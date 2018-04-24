---
title: Supervisión de información de aplicación y asignaciones
titlesuffix: Microsoft Intune
description: Después de haber asignado una aplicación a usuarios o dispositivos, use esta información para que le ayude a supervisar su estado.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 01b7972a6a4dbb641f4c656190324d8572f9010c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Supervisión de información de aplicación y asignaciones con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune proporciona diversas maneras en las cuales puede supervisar las propiedades de las aplicaciones que administra, así como el estado de la asignación.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en el grupo **Supervisión y administración**.
3. Elija **Aplicaciones móviles** y **Aplicaciones** en el grupo **Administrar**.
5. En la lista de aplicaciones, elija la aplicación que quiera supervisar. De este modo, verá la hoja de la aplicación con información general sobre el estado del dispositivo y del usuario.

## <a name="app-overview-blade"></a>Hoja de información general sobre las aplicaciones

Puede usar la hoja de la aplicación específica para revisar los detalles sobre el estado de una aplicación en su entorno.

### <a name="essentials"></a>Essentials
En la sección **Essentials** se incluye la siguiente información sobre la aplicación:

 | **Detalles de la aplicación**            | **Descripción**                                                      |
|------------------------|------------------------------------------------------------------|
| **Publicador**          | Editor de la aplicación.                                            |
| **Sistema operativo**   | Sistema operativo de la aplicación (Windows, iOS, Android, etc.). |
| **Creado**             | Fecha y hora de creación de esta revisión.                         |
| **Asignado**           | **Sí** o **No** si se ha asignado la aplicación.                  |

### <a name="device-and-user-status-graphs"></a>Gráficos de estado de dispositivo y usuario
El gráfico muestra el número de elementos con los siguientes estados:

| **Estado del dispositivo**       | **Descripción**                                       |
|-----------------------|-------------------------------------------------------|
| **Instalado**         | El número de aplicaciones instaladas.                         |
| **Sin instalar**     | El número de aplicaciones sin instalar.                     |
| **Error**            | El número de errores de instalación.                   |
| **Instalación pendiente**   | El número de aplicaciones en proceso de ser instaladas. |
| **No aplicable**           | Número de aplicaciones en las que el estado no es aplicable.            |

### <a name="device-install-status"></a>Estado de instalación del dispositivo

Si selecciona **Estado de instalación del dispositivo** en la sección **Supervisar**, aparecerá una lista de estados del dispositivo. En la tabla de detalles se incluyen las columnas siguientes:

| **Columna de dispositivo**      | **Descripción**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nombre del dispositivo**      | Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos.                                                                       |
| **Nombre de usuario**        | Nombre del usuario.                                                                                                                                                                                                                                      |
| **Plataforma**         | El sistema operativo del dispositivo (Windows, iOS, Android, etc.)                                                                                                                                                                                           |
| **Versión**          | El número de versión de la aplicación. En el caso de las aplicaciones de línea de negocio, se muestra el número de versión completa de la aplicación. El número de versión completo identifica una versión específica de la aplicación. El número aparece como _versión_(_compilación_). Por ejemplo, 2.2(2.2.17560800). |
| **Estado**           | El estado de la aplicación.                                                                                                                                                                                                                                     |
| **Detalles de estado**   | Los detalles del estado.                                                                                                                                                                                                                                     |
| **Última inserción en el repositorio**    | Fecha de la última sincronización de dispositivos con Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Estado de instalación del usuario

Si selecciona **Estado de instalación del usuario** en la sección **Supervisar**, aparecerá una lista de estados del usuario. En la tabla de detalles se incluyen las columnas siguientes:

| **Columna de usuario**     | **Descripción**                           |
|---------------------|-------------------------------------------|
| **Nombre**            | El nombre del usuario en Azure AD.         |
| **Nombre de usuario**       | El nombre único del usuario.              |
| **Instalaciones**   | Número de instalaciones de aplicaciones usadas por el usuario. |
| **Errores**        | Número de errores de instalación del usuario.     |
| **Sin instalar**   | Número de aplicaciones sin instalar por el usuario. |


## <a name="next-steps"></a>Pasos siguientes

- Para obtener más información sobre cómo trabajar con los datos de Intune, vea [Usar el almacenamiento de datos de Intune](reports-nav-create-intune-reports.md).
- Para más información sobre las directivas de configuración de aplicaciones, vea [Directivas de configuración de aplicaciones para Intune](app-configuration-policies-overview.md).