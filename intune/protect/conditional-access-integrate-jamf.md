---
title: Integración de Jamf Pro con Microsoft Intune para cumplimiento
titleSuffix: Microsoft Intune
description: Use directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para ayudar a integrar y proteger los dispositivos administrados por Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9dab1025e283ed1591c22b03ed4e3a61d40a20c3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515091"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integración de Jamf Pro con Intune para cumplimiento

Si la organización usa [Jamf Pro](https://www.jamf.com) para administrar dispositivos macOS, puede utilizar directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory (Azure AD) para garantizar que los dispositivos de la organización sean compatibles antes de que puedan acceder a los recursos empresariales. Este artículo le ayudará a configurar la integración de Jamf con Intune.

Cuando Jamf Pro se integra con Intune, puede sincronizar los datos de inventario de dispositivos macOS con Intune, a través de Azure AD. A continuación, el motor de cumplimiento de Intune analiza los datos de inventario para generar un informe. El análisis de Intune se combina con la información de la identidad de Azure AD del usuario del dispositivo para impulsar la aplicación a través del acceso condicional. Los dispositivos que son compatibles con las directivas de acceso condicional pueden obtener acceso a los recursos protegidos de la empresa.

Después de configurar la integración, [configure Jamf e Intune para aplicar el cumplimiento con el acceso condicional](conditional-access-assign-jamf.md) en los dispositivos administrados por Jamf.

## <a name="prerequisites"></a>Requisitos previos

### <a name="products-and-services"></a>Productos y servicios

Necesitará lo siguiente para configurar el acceso condicional con Jamf Pro:

- Jamf Pro 10.1.0 o versiones posteriores
- [Aplicación Portal de empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS con OS X 10.12 Yosemite o versiones posteriores

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

### <a name="create-an-application-in-azure-active-directory"></a>Creación de una aplicación en Azure Active Directory

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

6. Seleccione **Permisos de API** en **Administrar**. 

7. En la página de permisos de API, para quitar todos los permisos de esta aplicación, seleccione el icono **...** situado junto a cada permiso existente. Tenga en cuenta que esto es obligatorio; la integración no se realizará correctamente si hay algún permiso adicional inesperado en el registro de esta aplicación.

8. A continuación, se agregarán permisos para actualizar los atributos del dispositivo. En la parte superior izquierda de la página **Permisos de API**, seleccione **Agregar un permiso** para agregar un permiso nuevo. 

9. En la página **Request API permissions** (Solicitar permisos de API), seleccione **Intune** y, luego, **Permisos de aplicación**. Active solo la casilla para **update_device_attributes** y guarde el permiso nuevo.

10. Después, para conceder consentimiento de administrador para esta aplicación, seleccione **Conceder consentimiento de administrador para _\<su inquilino>_** en la parte superior izquierda de la página **Permisos de API**. Es posible que tenga que volver a autenticar la cuenta en la nueva ventana y seguir las indicaciones para conceder acceso a la aplicación.  

11. Para actualizar la página, haga clic en el botón **Actualizar** de la parte superior de la página. Confirme que se ha concedido el consentimiento del administrador para el permiso **update_device_attributes**. 

12. Una vez que la aplicación se haya registrado correctamente, los permisos de API solo deben contener un permiso llamado **update_device_attributes** y deben aparecer de la siguiente manera:

   ![Permisos correctos](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   El proceso de registro de la aplicación en Azure AD se completó.

    > [!NOTE]
    > Si el secreto de cliente expira, debe crear otro secreto de cliente en Azure y luego actualizar los datos de acceso condicional en Jamf Pro. Azure permite tener activo tanto el secreto anterior como la clave nueva para evitar las interrupciones del servicio.

### <a name="enable-intune-to-integrate-with-jamf-pro"></a>Habilitación de Intune para su integración con Jamf Pro

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Administración de dispositivos de socio**.

3. Habilite el **conector de cumplimiento para Jamf**. Para ello, pegue el identificador de la aplicación que ha guardado en el procedimiento anterior en el campo para *especificar el identificador de aplicación de Azure Active Directory para Jamf*.

4. Seleccione **Guardar**.

### <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar la integración de Microsoft Intune en Jamf Pro

1. Active la conexión en la consola de Jamf Pro:

   1. Abra la consola de Jamf Pro y vaya a **Global Management** > **Conditional Access** (Administración global > Acceso condicional). Haga clic en el botón **Editar** de la pestaña **macOS Intune Integration** (Integración de Intune para macOS).
   2. Active la casilla **Enable Intune Integration for macOS** (Habilitar la integración de Intune para macOS).
   3. Proporcione la información necesaria sobre su inquilino de Azure, como la **ubicación**, el **nombre de dominio**, el **identificador de aplicación** y el valor del *secreto de cliente* que guardó cuando creó la aplicación en Azure AD.
   4. Seleccione **Guardar**. Jamf Pro probará la configuración y confirmará que sea correcta.

   Regrese a la página **Administración de dispositivos asociados** de Intune para completar la configuración.

2. En Intune, vaya a la página **Administración de dispositivos asociados**. En **Configuración del conector**, configure grupos para la asignación:

   - Seleccione **Incluir** y especifique los grupos de usuarios que serán el destino de la inscripción de macOS con Jamf.
   - Use **Excluir** para seleccionar grupos de usuarios que no se inscriben con Jamf, sino que inscribirán sus equipos Mac directamente con Intune.

   *Excluir* invalida a *Incluir*, lo que significa que cualquier dispositivo que se encuentre en ambos grupos se excluye de Jamf y se dirige hacia la inscripción en Intune.

   >[!NOTE]
   > Este método de incluir y excluir grupos de usuarios afecta a la experiencia de inscripción del usuario. Cualquier usuario con un equipo Mac que ya esté inscrito en Jamf o en Intune que luego se le dirija hacia la inscripción con el otro MDM deberá anular la inscripción en su dispositivo y volver a inscribirlo en el nuevo MDM para que la administración del dispositivo funcione correctamente.

3. Seleccione **Evaluar** para determinar el número de dispositivos que se inscribirán con Jamf, según las configuraciones de grupos.

4. Seleccione **Guardar** cuando esté listo para aplicar la configuración.

5. Para continuar, tendrá que usar [Implementar la aplicación Portal de empresa para macOS en Jamf Pro](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) para que los usuarios puedan registrar sus dispositivos en Intune.

## <a name="set-up-compliance-policies-and-register-devices"></a>Configurar directivas de cumplimiento y registrar dispositivos

Después de configurar la integración entre Intune y Jamf, tiene que [aplicar directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Desconexión de Jamf Pro e Intune

Si ya no usa Jamf Pro para administrar los equipos Mac de la organización y desea que los usuarios se administren mediante Intune, debe quitar la conexión entre Jamf Pro e Intune. Quite la conexión mediante la consola de Jamf Pro.

1. En Jamf Pro, vaya a **Administración global** > **Acceso condicional**. En la pestaña **Integración de MacOS Intune**, seleccione **Editar**.

2. Desactive la casilla **Enable Intune Integration for macOS** (Habilitar la integración de Intune para macOS).

3. Seleccione **Guardar**. Jamf Pro envía la configuración a Intune y se terminará la integración.

4. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Administración de dispositivos de socio** para comprobar que el estado es ahora **Finalizado**.

   > [!NOTE]
   > Los dispositivos Mac de la organización se retirarán en la fecha (tres meses) que se muestra en la consola.

## <a name="next-steps"></a>Pasos siguientes

- [Aplicación de directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md)
- [Datos que Jamf envía a Intune](data-jamf-sends-to-intune.md)
