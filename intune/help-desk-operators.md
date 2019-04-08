---
title: Portal de solución de problemas del departamento de soporte técnico
titleSuffix: Microsoft Intune
description: El personal del departamento de soporte técnico usa el portal de solución de problemas para solucionar los problemas técnicos de los usuarios.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: df5b20be667159689aaaee9a790c0a4c5b5864fd
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798405"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Uso del portal de solución de problemas para ayudar a los usuarios de su empresa

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

El portal de solución de problemas permite que los operadores del departamento de soporte técnico y los administradores de Intune vean la información de usuario para solucionar las solicitudes de ayuda del usuario. Las organizaciones que disponen de un departamento de soporte técnico pueden asignar el **Operador del departamento de soporte técnico** a un grupo de usuarios. El rol de operador del departamento de soporte técnico puede usar el panel **Solución de problemas**.

En el panel **Solución de problemas** también se muestran los problemas de inscripción del usuario. Los detalles del problema y los pasos de corrección sugeridos pueden ayudar a los administradores y a los operadores del departamento de soporte técnico a solucionar los problemas. Ciertos problemas de inscripción no se capturan, y es posible que no se sugieran correcciones para algunos errores.

Para conocer los pasos sobre cómo agregar un rol de operador del departamento de soporte técnico, consulte [Control de administración basada en roles (RBAC) con Intune](/intune/role-based-access-control)

Cuando un usuario se pone en contacto con el soporte técnico por un problema técnico con Intune, el operador del departamento de soporte técnico introduce el nombre del usuario. Intune muestra datos útiles que pueden ayudar a resolver muchos problemas de nivel 1, incluidos los siguientes:

- Estado del usuario
- Assignments
- Problemas de cumplimiento
- El dispositivo no responde
- El dispositivo no obtiene una configuración Wi-Fi o VPN
- Error de instalación de la aplicación

## <a name="to-review-troubleshooting-details"></a>Para ver los detalles de solución de problemas, siga estos pasos:

En el panel de solución de problemas, elija la opción **Seleccionar usuario** para ver la información del usuario. La información de usuario puede ayudarle a comprender el estado actual de los usuarios y sus dispositivos.  

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Solucionar problema**.
4. Haga clic en **Seleccionar** para seleccionar un usuario para solucionar problemas.
5. Seleccione un usuario escribiendo su nombre o dirección de correo electrónico. Haga clic en **Seleccionar**. La información de solución de problemas del usuario se muestra en el panel de solución de problemas. En la tabla siguiente se explica la información proporcionada.

> [!Note]  
> También puede acceder al panel de **solución de problemas** visitando la página [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) desde el explorador.

## <a name="areas-of-troubleshooting-dashboard"></a>Áreas del panel de solución de problemas

Puede usar el panel **Solución de problemas** para consultar la información de usuario.

![](/intune/media/troubleshooting-dash.png)

| Área | Nombre | Descripción |
| ---  | ---  | ---         |
| 1.   | Estado de la cuenta  | Muestra el estado del inquilino actual de Intune como **Activo** o **Inactivo**.       |
| 2.   | Selección de usuarios  | El nombre del usuario seleccionado actualmente. Haga clic en **Cambiar usuario** para elegir un usuario nuevo.       |
| 3.   | Estado del usuario  | Muestra el estado de la licencia de Intune del usuario, el número de dispositivos, la compatibilidad de cada dispositivo, el número de aplicaciones y la compatibilidad de las aplicaciones.       |
| 4.   | Información de usuario  | Use la lista para seleccionar los detalles que vaya a consultar en el panel. <br>Puede seleccionar: <ul><li>Aplicaciones cliente<li>Directivas de cumplimiento<li> Directivas de configuración<li>Directivas de protección de aplicaciones <li>Restricciones de inscripción</ul>      |
| 5.   | Pertenencia a grupos  | Muestra los grupos actuales de los que es miembro el usuario seleccionado.       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

## <a name="enrollment-failure-reference"></a>Referencia de errores de inscripción

La tabla Errores de inscripción enumera los intentos de inscripción que no han tenido éxito. Los dispositivo enumerados en la tabla siguiente pueden haberse inscrito correctamente en un intento posterior. Puede que no se muestren todos los intentos con error. La información de mitigación no está disponible para todos los errores.

| Columna de tabla | Descripción |
|-------------|----------|
| Inicio de inscripción | La hora en la que el usuario comenzó la inscripción. |
| Sistema operativo | El sistema operativo del dispositivo. |
| Versión del sistema operativo | Versión del sistema operativo del dispositivo. |
| Error | El motivo del error. |

### <a name="failure-details"></a>Detalles del error

Cuando se elige una fila de error, se proporcionan más detalles.

| Sección | Descripción |
|-------------|----------|
| Detalles del error | Una explicación más detallada del error. |
| Soluciones posibles | Pasos sugeridos para resolver el error. Puede que algunos errores no tengan solución. |
| Recursos (opcional) | Vínculos para obtener más información o áreas del portal en las que deben tomarse medidas. |

### <a name="enrollment-errors"></a>Errores de inscripción

| Error | Detalles |
|-------------|----------|
| Error o tiempo de espera de iOS | Tiempo de espera agotado entre el dispositivo e Intune debido a que el usuario tarda demasiado en realizar la inscripción. |
| Usuario no encontrado o sin licencia | El usuario no tiene una licencia o se ha quitado del servicio. |
| Dispositivo ya inscrito | Un usuario intentó inscribir un dispositivo mediante el Portal de empresa en un dispositivo que todavía está inscrito para otro usuario. |
| No incorporado a Intune | Se intentó una inscripción sin que la entidad de administración de dispositivos móviles (MDM) de Intune estuviese configurada. |
| Error de autorización de inscripción | Se intentó realizar la inscripción con una versión antigua del portal de empresa. |
| Dispositivo no compatible | El dispositivo no cumple los requisitos mínimos para la inscripción en Intune. |
| Las restricciones de inscripción no se cumplen | Esta inscripción se ha bloqueado debido a una restricción de inscripciones configurada por el administrador. |
| Versión de dispositivo demasiado baja | El administrador ha configurado una restricción de inscripción que exige una versión de dispositivo superior. |
| Versión de dispositivo demasiado alta | El administrador ha configurado una restricción de inscripción que exige una versión de dispositivo inferior. |
| El dispositivo no se puede inscribir como personal | El administrador ha configurado una restricción de inscripción para bloquear las inscripciones personales y el dispositivo con el error no se ha predefinido como corporativo. |
| Plataforma de dispositivo bloqueada | El administrador ha configurado una restricción de inscripción que bloquea la plataforma de este dispositivo. |
| El token en masa ha expirado | El token en masa del paquete de aprovisionamiento ha expirado. |
| No se encontraron los detalles o el dispositivo Autopilot | No se ha encontrado el dispositivo Autopilot al intentar inscribir. |
| El perfil de Autopilot no se ha encontrado o no se ha asignado | El dispositivo no tiene un perfil de Autopilot activo. |
| Método de inscripción de Autopilot no esperado | El dispositivo ha intentado inscribirse mediante un método no permitido. |
| El dispositivo Autopilot se ha eliminado | Se ha quitado de Autopilot el dispositivo que intentaba inscribirse para esta cuenta. |
| Se alcanzó el límite de dispositivos | Esta inscripción se ha bloqueado debido a una restricción en el límite de dispositivos configurada por el administrador. |
| Incorporación de Apple | Se ha bloqueado la inscripción de todos los dispositivos iOS debido a que falta o ha expirado el certificado de inserción de MDM de Apple en Intune. |
| Dispositivo no registrado previamente | El dispositivo no se ha registrado previamente como corporativo y todas las inscripciones personales han sido bloqueadas por el administrador. |
| Característica no compatible | Es probable que el usuario intentase realizar la inscripción a través de un método que no es compatible con la configuración de Intune. |

## <a name="collect-available-data-from-mobile-device"></a>Recopilación de los datos disponibles desde un dispositivo móvil

Use los siguientes recursos para ayudarle a recopilar los datos de servicio al solucionar problemas del dispositivo del usuario:
  - [Enviar errores de inscripción de iOS al administrador de TI](/intune-user-help/send-errors-to-your-it-admin-ios)
  - [Ayudar al equipo de soporte técnico de su empresa a solucionar los problemas del dispositivo mediante el registro detallado](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
  - [Enviar registros de Android al equipo de soporte técnico de su empresa mediante un cable USB](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Enviar registros de datos de diagnóstico al administrador de TI mediante correo electrónico](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
  - [Enviar errores de inscripción de Android al administrador de TI](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>Pasos siguientes

Puede obtener más información sobre el control de administración basada en roles (RBAC) para definir los roles en su dispositivo de empresa, en la administración de aplicaciones móviles y en las tareas de protección de datos en [Control de administración basada en roles (RBAC) con Intune](/intune/role-based-access-control).

Obtenga información sobre los problemas conocidos de Microsoft Intune. Para obtener más información, consulte [Problemas conocidos de Microsoft Intune](/intune/known-issues).

Obtenga información sobre cómo crear una incidencia de soporte técnico y obtener ayuda cuando lo necesite. [Obtener soporte técnico](/intune/get-support).
