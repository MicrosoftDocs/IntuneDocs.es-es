---
title: Integración de Jamf Pro con Microsoft Intune para cumplimiento
titleSuffix: Microsoft Intune
description: Use directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para ayudar a integrar y proteger los dispositivos administrados por Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39d687c8c9b75182ba0e7d4020c6b840c753a231
ms.sourcegitcommit: a4c7339ec9ff5b1b846cb3cca887cf91b5cd4baa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627661"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integración de Jamf Pro con Intune para cumplimiento

Se aplica a: Intune en el portal de Azure

Si la organización usa [Jamf Pro](https://www.jamf.com) para administrar los dispositivos macOS, puede usar las directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory (Azure AD) para garantizar que los dispositivos de la organización son compatibles antes de que puedan acceder a los recursos empresariales. Este artículo le ayudará a configurar la integración de Jamf con Intune.

Cuando Jamf Pro se integra con Intune, puede sincronizar los datos de inventario de dispositivos macOS con Intune, a través de Azure AD. A continuación, el motor de cumplimiento de Intune analiza los datos de inventario para generar un informe. El análisis de Intune se combina con la información de la identidad de Azure AD del usuario del dispositivo para impulsar la aplicación a través del acceso condicional. Los dispositivos que son compatibles con las directivas de acceso condicional pueden obtener acceso a los recursos protegidos de la empresa.

Después de configurar la integración, [configure Jamf e Intune para aplicar el cumplimiento con el acceso condicional](conditional-access-assign-jamf.md) en los dispositivos administrados por Jamf.  


## <a name="prerequisites"></a>Requisitos previos

### <a name="products-and-services"></a>Productos y servicios
Necesitará lo siguiente para configurar el acceso condicional con Jamf Pro:

- Jamf Pro 10.1.0 o versiones posteriores
- [Aplicación Portal de empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS con OS X 10.11 Yosemite o versiones posteriores

### <a name="network-ports"></a>Puertos de red
<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
Los siguientes puertos deben ser accesibles para Jamf e Intune para integrarse correctamente: 
- **Intune**: Puerto 443
- **Apple**: puertos 2195, 2196 y 5223 (notificaciones push a Intune)
- **Jamf**: puertos 80 y 5223

Para permitir que APNS funcione correctamente en la red, también debe habilitar las conexiones salientes a los destinos siguientes, que también podrán ser orígenes de redireccionamiento:
- el bloque 17.0.0.0/8 de Apple a través de los puertos TCP 5223 y 443 desde todas las redes cliente.   
- los puertos 2195 y 2196 de los servidores Jamf Pro.  

Para obtener más información sobre estos puertos, vea los artículos siguientes:  
- [Ancho de banda y requisitos de configuración de red de Intune](../fundamentals/network-bandwidth-use.md).
- [Puertos de red usados por Jamf Pro](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro) en jamf.com.
- [Puertos TCP y UDP usados por los productos de software de Apple](https://support.apple.com/HT202944) en support.apple.com.


## <a name="connect-intune-to-jamf-pro"></a>Conexión de Intune a Jamf Pro

Para conectar Intune con Jamf Pro:

1. Cree una aplicación en Azure.
2. Habilite Intune para su integración con Jamf Pro.
3. Configure el acceso condicional en Jamf Pro.

## <a name="create-an-application-in-azure-active-directory"></a>Creación de una aplicación en Azure Active Directory

1. En [Azure Portal](https://portal.azure.com), vaya a **Azure Active Directory** > **Registros de aplicaciones** y seleccione **Nuevo registro**. 

2. En la página **Registrar una aplicación**, especifique estos detalles:
   - En la sección **Nombre**, escriba un nombre significativo para la aplicación, por ejemplo, **Acceso condicional de Jamf**.
   - Para la sección **Supported account types** (Tipos de cuenta admitidos), seleccione **Accounts in any organizational directory** (Cuentas en cualquier directorio organizativo). 
   - En **URI de redireccionamiento**, deje el valor predeterminado de Web y, luego, especifique la dirección URL de la instancia de Jamf Pro.  

3. Seleccione **Registrar** para crear la aplicación y abrir la página de **información general** de la aplicación nueva.  

4. En la página **Información general** de la aplicación, copie el valor de **Application (client) ID** (Identificador de aplicación [cliente]) y anótelo para usarlo más adelante. Lo necesitará en procedimientos posteriores.  

5. Seleccione **Certificates & secrets** (Certificados y secretos) en **Administrar**. Seleccione el botón **Nuevo secreto de cliente**. Escriba un valor en **Descripción**, seleccione cualquier opción para **Expira** y elija **Agregar**.

   > [!IMPORTANT]  
   > Antes de salir de la página, copie el valor del secreto de cliente y anótelo para usarlo más adelante. Lo necesitará en procedimientos posteriores. Este valor no vuelve a estar disponible sin volver a crear el registro de la aplicación.  

6. Seleccione **Permisos de API** en **Administrar**. Seleccione los permisos existentes y, luego, seleccione **Quitar permiso** para eliminar todos esos permisos. Quitar todos los permisos existentes es necesario, ya que agregará un nuevo permiso y la aplicación solo funciona si tiene un único permiso necesario.  

7. Para asignar un permiso nuevo, seleccione **Agregar un permiso**. En la página **Request API permissions** (Solicitar permisos de API), seleccione **Intune** y, luego, **Permisos de aplicación**. Active solo la casilla para **update_device_attributes**.  

   Seleccione **Agregar permiso** para guardar esta configuración.  

8. En la página **Permisos de API**, seleccione **Conceder consentimiento del administrador para _\<su inquilino>_** y, luego, seleccione **Sí**.  Una vez que la aplicación se haya registrado correctamente, los permisos de la API deben aparecer de la siguiente manera: ![Permisos correctos](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   El proceso de registro de la aplicación en Azure AD se completó.


    > [!NOTE]
    > Si el secreto de cliente expira, debe crear otro secreto de cliente en Azure y luego actualizar los datos de acceso condicional en Jamf Pro. Azure permite tener activo tanto el secreto anterior como la clave nueva para evitar las interrupciones del servicio.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Habilitación de Intune para su integración con Jamf Pro

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y vaya a **Microsoft Intune** > **Cumplimiento de dispositivos** > **Partner device management** (Administración de dispositivos de asociados).

2. Habilite el conector de cumplimiento para Jamf. Para ello, pegue el identificador de la aplicación que ha guardado en el procedimiento anterior en el campo **Jamf Azure Active Directory App ID** (Id. de aplicación de Azure Active Directory para Jamf).

3. Seleccione **Guardar**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar la integración de Microsoft Intune en Jamf Pro

1. En Jamf Pro, navegue a **Administración global** > **Acceso condicional**. Haga clic en el botón **Editar** de la pestaña **macOS Intune Integration** (Integración de Intune para macOS).

2. Active la casilla **Enable Intune Integration for macOS** (Habilitar la integración de Intune para macOS).

3. Proporcione la información necesaria sobre su inquilino de Azure, como la **ubicación**, el **nombre de dominio**, el **identificador de aplicación** y el valor del *secreto de cliente* que guardó cuando creó la aplicación en Azure AD.  

4. Seleccione **Guardar**. Jamf Pro probará la configuración y confirmará que sea correcta.

## <a name="set-up-compliance-policies-and-register-devices"></a>Configurar directivas de cumplimiento y registrar dispositivos

Después de configurar la integración entre Intune y Jamf, tiene que [aplicar directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md).


## <a name="disconnect-jamf-pro-and-intune"></a>Desconexión de Jamf Pro e Intune 

Si ya no usa Jamf Pro para administrar los equipos Mac de la organización y desea que los usuarios se administren mediante Intune, debe quitar la conexión entre Jamf Pro e Intune. Quite la conexión mediante la consola de Jamf Pro. 

1. En Jamf Pro, vaya a **Administración global** > **Acceso condicional**. En la pestaña **Integración de MacOS Intune**, seleccione **Editar**.
2. Desactive la casilla **Enable Intune Integration for macOS** (Habilitar la integración de Intune para macOS).
3. Seleccione **Guardar**. Jamf Pro envía la configuración a Intune y se terminará la integración.
4. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Vaya a **Microsoft Intune** > **Device Compliance**  > **Partner device management** (Cumplimiento del dispositivo > Administración de dispositivos de asociados) para comprobar que el estado es ahora **Terminated** (Terminado). 

   > [!NOTE]
   > Los dispositivos Mac de la organización se retirarán en la fecha (tres meses) que se muestra en la consola. 

## <a name="next-steps"></a>Pasos siguientes

- [Aplicación de directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md)
- [Datos que Jamf envía a Intune](data-jamf-sends-to-intune.md)
