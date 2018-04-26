---
title: Portal de solución de problemas del departamento de soporte técnico
titlesuffix: Microsoft Intune
description: El personal del departamento de soporte técnico usa el portal de solución de problemas para solucionar los problemas técnicos de los usuarios.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 9ff0d6f662fca4cb223496d342de5d6378c05ceb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
- El dispositivo no
- El dispositivo no obtiene una configuración Wi-Fi o VPN
- Error de instalación de la aplicación

## <a name="to-review-troubleshooting-details"></a>Para ver los detalles de solución de problemas, siga estos pasos:

En el panel de solución de problemas, elija la opción **Seleccionar usuario** para ver la información del usuario. La información de usuario puede ayudarle a comprender el estado actual de los usuarios y sus dispositivos.  

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Solucionar problema**.
4. Haga clic en **Seleccionar** para seleccionar un usuario para solucionar problemas.
5. Seleccione un usuario escribiendo su nombre o dirección de correo electrónico. Haga clic en **Seleccionar**. La información de solución de problemas del usuario se muestra en el panel de solución de problemas. En las tablas siguientes se explica la información proporcionada.

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
| 4.   | Información de usuario  | Use la lista para seleccionar los detalles que vaya a consultar en el panel. <br>Puede seleccionar: <ul><li>Aplicaciones móviles<li>Directivas de protección de aplicaciones<li>Directivas de cumplimiento<li> Directivas de configuración</ul>      |
| 5.   | Pertenencia a grupos  | Yadda       |

## <a name="mobile-apps-reference"></a>Referencia de aplicaciones móviles

Las aplicaciones que se ejecutan en dispositivos o los dispositivos que pertenecen a los usuarios administrados por Intune y Azure Active Directory (AD).

### <a name="properties"></a>Propiedades

Las propiedades de las aplicaciones móviles.

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
| Propiedad          | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**.                                               |
| Compatibilidad con Intune   | El nombre del tipo de dispositivo.                                                                                                     |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Sistema operativo                 | El sistema operativo instalado en el dispositivo.                                                                                       |
| Versión del sistema operativo         | El número de versión del sistema operativo del dispositivo.                                                                                  |
| Última inserción en el repositorio      | El nombre del tipo de dispositivo.                                                                                                     |

### <a name="app-protection-status"></a>Estado de protección de la aplicación

Las aplicaciones móviles que se integran con tecnologías de Enterprise Mobility Solution (EMS) disponen de una directiva de protección de aplicaciones, que proporciona una protección básica para los datos corporativos al descargarse en aplicaciones móviles, incluidas las de Office. 

| Propiedad    | Descripción                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Estado      | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**. |
| Nombre de la aplicación    | El nombre de la aplicación.                                                           |
| Nombre del dispositivo | El nombre del tipo de dispositivo.                                                       |
| Tipo de dispositivo | El nombre del tipo de dispositivo.                                                       |
| Directivas    | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**. |
| Última sincronización   | La marca de tiempo de la última vez que el dispositivo se sincronizó con Intune.                   |

## <a name="app-protection-policies-reference"></a>Referencia de las directivas de protección de aplicaciones

Las aplicaciones móviles que se integran con tecnologías de EMS disponen de una directiva de protección de aplicaciones, que proporciona una protección básica para los datos corporativos al descargarse en aplicaciones móviles, incluidas las de Office. 

### <a name="properties"></a>Propiedades

En la tabla se resume el estado de las directivas de protección de aplicaciones para dispositivos administrados por Intune.

| Propiedad    | Descripción                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nombre        | El nombre de la aplicación.                                                                                                        |
| Implementado    | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Plataforma    | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**.                                               |
| Inscripción  | El nombre del tipo de dispositivo.                                                                                                     |
| Última actualización | La marca de tiempo en que se modificó la directiva.                                                                                              |

### <a name="devices"></a>Dispositivos

Dispositivos administrados por Intune o por usuarios administrados por Intune o Azure AD.

| Propiedad           | Texto                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nombre del dispositivo        | El nombre del tipo de dispositivo.                                                                                                     |
| Administrado por         | La marca de tiempo en que se modificó la directiva.                                                                                              |
| Tipo de combinación de Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Propiedad          | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**.                                               |
| Compatibilidad con Intune   | El nombre del tipo de dispositivo.                                                                                                     |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Sistema operativo                 | El sistema operativo instalado en el dispositivo.                                                                                       |
| Versión del sistema operativo         | El número de versión del sistema operativo del dispositivo.                                                                                  |
| Última inserción en el repositorio      | El nombre del tipo de dispositivo.                                                                                                     |

## <a name="compliance-policies-reference"></a>Referencia de las directivas de cumplimiento

Garantiza que los dispositivos usados para acceder a las aplicaciones y a los datos de la empresa cumplan ciertas reglas, como el uso de un PIN para acceder al dispositivo y el cifrado de los datos almacenados en el dispositivo.

### <a name="properties"></a>Propiedades

Las propiedades de las directivas de cumplimiento.

| Propiedad      | Descripción                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Asignación    | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Nombre          | El nombre de la aplicación.                                                                                                        |
| Sistema operativo            | El sistema operativo instalado en el dispositivo.                                                                                       |
| Tipo de directiva   | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**.                                               |
| Última modificación | El nombre del tipo de dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivos

Dispositivos administrados por Intune o por usuarios administrados por Intune o Azure AD.

| Propiedad           | Descripción                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nombre del dispositivo        | El nombre del tipo de dispositivo.                                                                                                     |
| Administrado por         | La marca de tiempo en que se modificó la directiva.                                                                                              |
| Tipo de combinación de Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Propiedad          | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**.                                               |
| Compatibilidad con Intune   | El nombre del tipo de dispositivo.                                                                                                     |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Sistema operativo                 | El sistema operativo instalado en el dispositivo.                                                                                       |
| Versión del sistema operativo         | El número de versión del sistema operativo del dispositivo.                                                                                  |
| Última inserción en el repositorio      | El nombre del tipo de dispositivo.                                                                                                     |

### <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

Las aplicaciones móviles que se integran con tecnologías de EMS disponen de una directiva de protección de aplicaciones, que proporciona una protección básica para los datos corporativos al descargarse en aplicaciones móviles, incluidas las de Office. 

| Propiedad    | Descripción                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Estado      | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**. |
| Nombre de la aplicación    | El nombre de la aplicación.                                                           |
| Nombre del dispositivo | El nombre del tipo de dispositivo.                                                       |
| Tipo de dispositivo | El nombre del tipo de dispositivo.                                                       |
| Directivas    | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**. |
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
| Tipo de directiva   | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**.                                               |
| Última modificación | El nombre del tipo de dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivos

Dispositivos administrados por Intune o por usuarios administrados por Intune o Azure AD.

| Propiedad           | Descripción                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nombre del dispositivo        | El nombre del tipo de dispositivo.                                                                                                     |
| Administrado por         | La marca de tiempo en que se modificó la directiva.                                                                                              |
| Tipo de combinación de Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Propiedad          | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**.                                               |
| Compatibilidad con Intune   | El nombre del tipo de dispositivo.                                                                                                     |
| Compatibilidad con Azure AD | El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**. |
| Sistema operativo                 | El sistema operativo instalado en el dispositivo.                                                                                       |
| Versión del sistema operativo         | El número de versión del sistema operativo del dispositivo.                                                                                  |
| Última inserción en el repositorio      | El nombre del tipo de dispositivo.                                                                                                     |


### <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

Las aplicaciones móviles que se integran con tecnologías de EMS disponen de una directiva de protección de aplicaciones, que proporciona una protección básica para los datos corporativos al descargarse en aplicaciones móviles, incluidas las de Office. 

| Propiedad    | Descripción                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Estado      | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**. |
| Nombre de la aplicación    | El nombre de la aplicación.                                                           |
| Nombre del dispositivo | El nombre del tipo de dispositivo.                                                       |
| Tipo de dispositivo | El nombre del tipo de dispositivo.                                                       |
| Directivas    | El tipo de propiedad del dispositivo. Puede ser **Empresa**, **Personal** o **Desconocido**. |
| Última sincronización   | La marca de tiempo de la última vez que el dispositivo se sincronizó con Intune.                   |

## <a name="next-steps"></a>Pasos siguientes

Puede obtener más información sobre el control de administración basada en roles (RBAC) para definir los roles en su dispositivo de empresa, en la administración de aplicaciones móviles y en las tareas de protección de datos en [Control de administración basada en roles (RBAC) con Intune](/intune/role-based-access-control).

Obtenga información sobre los problemas conocidos de Microsoft Intune. Para obtener más información, consulte [Problemas conocidos de Microsoft Intune](/intune/known-issues).

Obtenga información sobre cómo crear una incidencia de soporte técnico y obtener ayuda cuando lo necesite. [Obtener soporte técnico](/intune/get-support).
