---
title: Integración de Jamf Pro con Microsoft Intune para cumplimiento | Microsoft Intune
description: Use directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para ayudar a proteger los dispositivos administrados por Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cc547926d95e3fa1bec54b4ea55f764b5701b3b7
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816827"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integración de Jamf Pro con Intune para cumplimiento

Se aplica a: Intune en el portal de Azure

Si la organización usa [Jamf Pro](https://www.jamf.com) para administrar los equipos Mac de los usuarios finales, puede usar las directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para garantizar que los dispositivos de la organización son compatibles.

## <a name="prerequisites"></a>Requisitos previos

Necesitará lo siguiente para configurar el acceso condicional con Jamf Pro:

- Jamf Pro 10.1.0 o versiones posteriores
- [Aplicación Portal de empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS con OS X 10.11 Yosemite o versiones posteriores

## <a name="connecting-intune-to-jamf-pro"></a>Conexión de Intune a Jamf Pro

Puede conectar Intune con Jamf Pro mediante la:

1. Creación de una aplicación nueva en Azure
2. Habilitación de Intune para su integración con Jamf Pro
3. Configuración del acceso condicional en Jamf Pro

## <a name="create-a-new-application-in-azure-active-directory"></a>Creación de una aplicación en Azure Active Directory

1. Abra **Azure Active Directory** > **Registros de aplicaciones**.
2. Haga clic en **+Nuevo registro de aplicaciones**.
3. Escriba un **nombre para mostrar**, como **Acceso condicional de Jamf**.
4. Seleccione **Web app / API** (API/aplicación web).
5. Especifique la **Dirección URL de inicio de sesión** con la dirección URL de la instancia de Jamf Pro.
6. Haga clic en **Crear aplicación**.
7. Guarde el **Id. de aplicación** recién creado, abra **Configuración** y vaya a **Acceso de API** > **Claves** para crear una clave de aplicación. Escriba una **Descripción**, cuánto hay que esperar antes de que **expire** y, después, guarde la clave de aplicación.

   > [!IMPORTANT]
   > La clave de aplicación solo aparece una vez durante este proceso. Asegúrese de guardarla donde pueda recuperarla fácilmente.

8. Abra **Configuración**, después vaya a **Acceso de API** > **Permisos necesarios** y elimine todos los permisos.

   > [!NOTE]
   > Agregue un permiso necesario nuevo. La aplicación solo puede funcionar correctamente si tiene el permiso necesario.

9. Seleccione **API de Microsoft Intune** y haga clic en **Seleccionar**.
10. Elija **Send device attributes to Microsoft Intune** (Enviar atributos de dispositivo a Microsoft Intune) y haga clic en **Seleccionar**.
11. Haga clic en el botón **Conceder permisos** después de guardar los permisos necesarios para la aplicación.

    > [!NOTE]
    > Si la clave de aplicación expira, debe crear una clave de aplicación nueva en Microsoft Azure y luego actualizar los datos del acceso condicional en Jamf Pro. Azure permite tener activa tanto la clave anterior como la clave nueva para evitar las interrupciones del servicio.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Habilitación de Intune para su integración con Jamf Pro

1. En el portal de Microsoft Azure, abra **Microsoft Intune** > **Cumplimiento de dispositivos** > **Administración de dispositivos de socios comerciales**.
2. Habilite el conector de cumplimiento para Jamf. Para ello, pegue el id. de aplicación en el campo **Jamf Azure Active Directory App ID** (Id. de aplicación de Azure Active Directory para Jamf).
3. Haga clic en **Guardar**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar la integración de Microsoft Intune en Jamf Pro

1. En Jamf Pro, navegue a **Administración global** > **Acceso condicional**. Haga clic en el botón **Editar** de la pestaña **Integración de Microsoft Intune**.
2. Active la casilla **Habilitar integración de Microsoft Intune**.
3. Proporcione la información necesaria sobre el inquilino de Azure, incluida la **ubicación**, el **nombre de dominio**, el **id. de aplicación** y la **clave de aplicación** que guardó de los pasos anteriores.
4. Haga clic en **Guardar**. Jamf Pro proporcionará la configuración y comprobará el éxito.

## <a name="set-up-compliance-policies-and-register-devices"></a>Configurar directivas de cumplimiento y registrar dispositivos

Cuando termine de configurar la integración entre Intune y Jamf, tiene que [aplicar directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md).

## <a name="information-shared-from-jamf-pro-to-intune"></a>Información compartida de Jamf Pro a Intune

Jamf Pro captura la información de inventario sobre los dispositivos macOS administrados. Jamf Pro informa lo siguiente a Intune:

* Id. de Azure AD del dispositivo
* Estado del inventario JAMF (el estado de inventario de un equipo registrado con Jamf Pro en las últimas 24 horas)
* Versión del SO
* Id. de Azure AD del usuario
* Cifrado (FileVault 2)
* Estado del equipo selector
* Contraseña: número mínimo de conjuntos de caracteres
* Expiración de contraseña (días)
* Tipo de contraseña: simple, alfanumérico o desconocido
* Evitar inicio de sesión automático
* Longitud necesaria del código de acceso
* Contraseña: número de contraseñas anteriores para impedir su reutilización
* Protección de la integridad del sistema
* Hora de última comprobación
* Tipo de arquitectura
* Ranuras de RAM disponibles
* Capacidad de la batería
* ROM de arranque
* Velocidad de bus
* Tamaño de caché
* Nombre del dispositivo
* Unión al dominio
* Id. de Jamf
* Dirección MAC
* Marca
* Modelo
* Identificador de modelo
* Velocidad de NIC
* Número de núcleos
* Número de procesadores
* Sistema operativo
* Plataforma
* Velocidad del procesador
* Tipo de procesador
* Dirección MAC secundaria
* Número de serie
* Versión de SMC
* RAM total
* UDID
* Correo electrónico del usuario

## <a name="next-steps"></a>Pasos siguientes

- [Aplicación de directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md)
