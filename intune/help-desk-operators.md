---
title: Portal de solución de problemas del departamento de soporte técnico
titlesuffix: Microsoft Intune
description: El personal del departamento de soporte técnico usa el portal de solución de problemas para solucionar los problemas técnicos de los usuarios.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 37483f0fa33db109510ee537772a7bdead79e4f3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203559"
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
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
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

## <a name="client-apps-reference"></a>Referencia de aplicaciones cliente

Las aplicaciones que ejecutan los dispositivos:
- administrados por Intune y Azure Active Directory; 
- propiedad de usuarios administrados por Intune y Azure Active Directory (AD).

### <a name="properties"></a>Propiedades

Las propiedades de las aplicaciones cliente.

| Propiedad      | Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre          | El nombre de la aplicación.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Sistema operativo            | El sistema operativo instalado en el dispositivo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Tipo          | Puede elegir un tipo de asignación para cada aplicación.  <br> **Disponible**: los usuarios instalan la aplicación desde el sitio web o la aplicación del Portal de empresa.  <br> **No aplicable**: la aplicación no está instalada ni se muestra en el Portal de empresa. <br> **Desinstalar**: la aplicación se ha desinstalado de dispositivos de los grupos seleccionados.  <br> **Available with or without enrollment** (Disponible con o sin inscripción): asignar esta aplicación a grupos de usuarios cuyos dispositivos no se hayan inscrito en Intune. |
| Última modificación | El nombre del tipo de dispositivo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### <a name="devices"></a>Dispositivos

Dispositivos administrados por Intune o por usuarios administrados por Intune o Azure AD.

| Propiedad           | Descripción                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nombre del dispositivo        | El nombre del tipo de dispositivo.                                                                                                     |
| Administrado por         | La marca de tiempo en que se modificó la directiva.                                                                                              |
| Tipo de combinación de Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Propiedad          | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**).                                               |
| Compatibilidad con Intune   | El nombre del tipo de dispositivo.                                                                                                     |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Instalación de la aplicación | Indica si una aplicación se ha instalado correcta o incorrectamente en el dispositivo. |
| Sistema operativo                 | El sistema operativo instalado en el dispositivo.                                                                                       |
| Versión del sistema operativo         | El número de versión del sistema operativo del dispositivo.                                                                                  |
| Última inserción en el repositorio      | El nombre del tipo de dispositivo.                                                                                                     |

### <a name="app-protection-status"></a>Estado de protección de la aplicación

Las aplicaciones móviles que se integran con tecnologías de Enterprise Mobility Solution (EMS) disponen de una directiva de protección de aplicaciones, Estas directivas proporcionan una protección básica para los datos corporativos al descargarse en aplicaciones móviles, incluidas las de Office. 

| Propiedad    | Descripción                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Estado      | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**). |
| Nombre de la aplicación    | El nombre de la aplicación.                                                           |
| Nombre del dispositivo | El nombre del tipo de dispositivo.                                                       |
| Tipo de dispositivo | El nombre del tipo de dispositivo.                                                       |
| Directivas    | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**). |
| Última sincronización   | La marca de tiempo de la última vez que el dispositivo se sincronizó con Intune.                   |

## <a name="app-protection-policies-reference"></a>Referencia de las directivas de protección de aplicaciones

Las aplicaciones móviles que se integran con tecnologías de Enterprise Mobility Solution (EMS) disponen de una directiva de protección de aplicaciones. Estas directivas proporcionan una protección básica para los datos corporativos al descargarse en aplicaciones móviles, incluidas las de Office. 

### <a name="properties"></a>Propiedades

En la tabla se resume el estado de las directivas de protección de aplicaciones para dispositivos administrados por Intune.

| Propiedad    | Descripción                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nombre        | El nombre de la aplicación.                                                                                                        |
| Implementado    | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Plataforma    | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**).                                               |
| Inscripción  | El nombre del tipo de dispositivo.                                                                                                     |
| Última actualización | La marca de tiempo en que se modificó la directiva.                                                                                              |

### <a name="devices"></a>Dispositivos

Dispositivos administrados por Intune o por usuarios administrados por Intune o Azure AD.

| Propiedad           | Texto                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nombre del dispositivo        | El nombre del tipo de dispositivo.                                                                                                     |
| Administrado por         | La marca de tiempo en que se modificó la directiva.                                                                                              |
| Tipo de combinación de Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Propiedad          | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**).                                               |
| Compatibilidad con Intune   | El nombre del tipo de dispositivo.                                                                                                     |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Sistema operativo                 | El sistema operativo instalado en el dispositivo.                                                                                       |
| Versión del sistema operativo         | El número de versión del sistema operativo del dispositivo.                                                                                  |
| Última inserción en el repositorio      | El nombre del tipo de dispositivo.                                                                                                     |

## <a name="compliance-policies-reference"></a>Referencia de las directivas de cumplimiento

Garantice que los dispositivos usados para acceder a las aplicaciones y a los datos de la empresa cumplan ciertas reglas, como el uso de un PIN para acceder al dispositivo y el cifrado de los datos almacenados en el dispositivo.

### <a name="properties"></a>Propiedades

Las propiedades de las directivas de cumplimiento.

| Propiedad      | Descripción                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Asignación    | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Nombre          | El nombre de la aplicación.                                                                                                        |
| Sistema operativo            | El sistema operativo instalado en el dispositivo.                                                                                       |
| Tipo de directiva   | El tipo de propiedad del dispositivo (**Empresa**, **Personal** y **Desconocido**).                                               |
| Última modificación | El nombre del tipo de dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivos

Dispositivos administrados por Intune o por usuarios administrados por Intune o Azure AD.

| Propiedad           | Descripción                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nombre del dispositivo        | El nombre del tipo de dispositivo.                                                                                                     |
| Administrado por         | La marca de tiempo en que se modificó la directiva.                                                                                              |
| Tipo de combinación de Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Propiedad          | El tipo de propiedad del dispositivo (**Empresa**, **Personal** y **Desconocido**).                                               |
| Compatibilidad con Intune   | El nombre del tipo de dispositivo.                                                                                                     |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Sistema operativo                 | El sistema operativo instalado en el dispositivo.                                                                                       |
| Versión del sistema operativo         | El número de versión del sistema operativo del dispositivo.                                                                                  |
| Última inserción en el repositorio      | El nombre del tipo de dispositivo.                                                                                                     |

### <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

Las aplicaciones móviles que se integran con tecnologías de EMS disponen de una directiva de protección de aplicaciones, Estas directivas proporcionan una protección básica para los datos corporativos al descargarse en aplicaciones móviles, incluidas las de Office. 

| Propiedad    | Descripción                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Estado      | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**). |
| Nombre de la aplicación    | El nombre de la aplicación.                                                           |
| Nombre del dispositivo | El nombre del tipo de dispositivo.                                                       |
| Tipo de dispositivo | El nombre del tipo de dispositivo.                                                       |
| Directivas    | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**). |
| Última sincronización   | La marca de tiempo de la última vez que el dispositivo se sincronizó con Intune.                   |

## <a name="configuration-policies-reference"></a>Referencia de las directivas de configuración

Las aplicaciones móviles con configuraciones específicas del proveedor disponen de una directiva de configuración de aplicaciones. 

### <a name="properties"></a>Propiedades

Las propiedades de las directivas de configuración.

| Propiedad      | Descripción                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Asignación    | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Nombre          | El nombre de la aplicación.                                                                                                        |
| Sistema operativo            | El sistema operativo instalado en el dispositivo.                                                                                       |
| Tipo de directiva   | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**).                                               |
| Última modificación | El nombre del tipo de dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivos

Dispositivos administrados por Intune o por usuarios administrados por Intune o Azure AD.

| Propiedad           | Descripción                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nombre del dispositivo        | El nombre del tipo de dispositivo.                                                                                                     |
| Administrado por         | La marca de tiempo en que se modificó la directiva.                                                                                              |
| Tipo de combinación de Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Propiedad          | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**).                                               |
| Compatibilidad con Intune   | El nombre del tipo de dispositivo.                                                                                                     |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Sistema operativo                 | El sistema operativo instalado en el dispositivo.                                                                                       |
| Versión del sistema operativo         | El número de versión del sistema operativo del dispositivo.                                                                                  |
| Última inserción en el repositorio      | El nombre del tipo de dispositivo.                                                                                                     |


### <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

Las aplicaciones móviles que se integran con tecnologías de EMS disponen de una directiva de protección de aplicaciones, Estas directivas proporcionan una protección básica para los datos corporativos al descargarse en aplicaciones móviles, incluidas las de Office. 

| Propiedad    | Descripción                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Estado      | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**). |
| Nombre de la aplicación    | El nombre de la aplicación.                                                           |
| Nombre del dispositivo | El nombre del tipo de dispositivo.                                                       |
| Tipo de dispositivo | El nombre del tipo de dispositivo.                                                       |
| Directivas    | El tipo de propiedad del dispositivo (**Empresa**, **Personal** o **Desconocido**). |
| Última sincronización   | La marca de tiempo de la última vez que el dispositivo se sincronizó con Intune.                   |

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
