---
title: Supervisión de información y asignaciones de aplicaciones
titleSuffix: Microsoft Intune
description: Después de haber asignado una aplicación a usuarios o dispositivos, use esta información para ayudarle a supervisar el estado de dicha aplicación.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b3cba546be350f47c1a57f47b8eddf85323dc74
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567236"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Supervisión de información y asignaciones de aplicaciones con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune ofrece varias formas de supervisar las propiedades de las aplicaciones administra y de administrar el estado de asignación de estas.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el menú **Intune**, seleccione **Aplicaciones cliente**.
4. En la sección **Administrar** del menú, seleccione **Aplicaciones**.
5. En la lista de aplicaciones, seleccione una aplicación para supervisar. Verá el panel de la aplicación, que incluye información general sobre el estado del dispositivo y del usuario.

> [!NOTE]
> Las aplicaciones de Google Play Store que se implementan como **Disponible** y las aplicaciones de LOB de Android implementadas como **Disponible con o sin inscripción** no informan de su estado de instalación.

## <a name="app-overview-pane"></a>Panel de información general de la aplicación

En el panel de la aplicación, puede revisar los detalles sobre el estado de una aplicación en su entorno.

### <a name="essentials"></a>Essentials
En la sección **Essentials** se incluye la siguiente información sobre la aplicación:

 | **Detalles de la aplicación**            | **Descripción**                                                      |
|------------------------|------------------------------------------------------------------|
| **Publicador**          | El editor de la aplicación.                                            |
| **Sistema operativo**   | El sistema operativo de aplicación (Windows, iOS, Android, etc.). |
| **Creado**             | Fecha y hora de creación de esta revisión. <b>**Nota**: este valor de fecha se actualiza cuando un administrador de TI cambia los metadatos de una aplicación, como al cambiar la categoría o la descripción de una aplicación.                        |
| **Asignado**           | Si la aplicación se ha asignado (**Sí** o **No**).                  |

### <a name="device-and-user-status-graphs"></a>Gráficos de estado de dispositivo y usuario
El gráfico muestra el número de elementos con el siguiente estado:

| **Estado del dispositivo**       | **Descripción**                                       |
|-----------------------|-------------------------------------------------------|
| **Instalado**         | El número de aplicaciones instaladas.                         |
| **Sin instalar**     | El número de aplicaciones sin instalar.                     |
| **Error**            | El número de errores de instalación.                   |
| **Instalación pendiente**   | El número de aplicaciones en proceso de ser instaladas. |
| **No aplicable**           | El número de aplicaciones en las que el estado no es aplicable.            |

> [!NOTE]
> El número de aplicaciones detectadas puede no coincidir con el recuento del estado de instalación de la aplicación. Estas son las posibles incoherencias:
>    - Un cambio de orientación de una aplicación administrada instalada puede hacer que el recuento de instalación en la hoja de estado disminuya, pero se mantenga presente en las aplicaciones detectadas.
>    - Dirigir varias instancias de la misma aplicación a un inquilino dará lugar a recuentos diferentes debido a la posible superposición de usuarios o dispositivos. Cada instancia de la aplicación contará los usuarios que se superponen, pero las aplicaciones detectadas tendrán recuentos duplicados.
>    - Las aplicaciones detectadas y los estados de la aplicación se recopilan en intervalos de tiempo diferentes, lo que podría provocar una discrepancia en los recuentos de la aplicación.
> 
> Además, tenga en cuenta que las aplicaciones Android implementadas como **Disponible con o sin inscripción** solo informarán del estado de instalación de las aplicaciones en dispositivos inscritos. El estado de instalación de las aplicaciones no está disponible en los dispositivos no inscritos en Intune.

### <a name="device-install-status"></a>Estado de instalación del dispositivo

Si selecciona **Estado de instalación del dispositivo** en la sección **Supervisión** del menú, se muestra una lista de estados de dispositivo. En la tabla de detalles se incluyen las columnas siguientes:

| **Columna de dispositivo**      | **Descripción**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nombre del dispositivo**      | El nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no está disponible para ningún otro dispositivo.                                                                       |
| **Nombre de usuario**        | Nombre del usuario.                                                                                                                                                                                                                                      |
| **Plataforma**         | El sistema operativo del dispositivo (Windows, iOS, Android, etc.)                                                                                                                                                                                           |
| **Versión**          | El número de versión de la aplicación. En el caso de las aplicaciones de línea de negocio (LOB), se muestra el número de versión completo de la aplicación. El número de versión completo identifica una versión específica de la aplicación. El número aparece como _versión_(_compilación_). Por ejemplo, 2.2(2.2.17560800). En el caso de las aplicaciones de Store, no se muestra ninguna versión. |
| **Estado**           | El estado de la aplicación.                                                                                                                                                                                                                                     |
| **Detalles de estado**   | Los detalles del estado.                                                                                                                                                                                                                                     |
| **Última inserción en el repositorio**    | La fecha de la última sincronización de dispositivos con Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Estado de instalación del usuario

Si selecciona **Estado de instalación del usuario** en la sección **Supervisión** del menú, aparece una lista de estados del usuario. En la tabla de detalles se incluyen las columnas siguientes:

| **Columna de usuario**     | **Descripción**                           |
|---------------------|-------------------------------------------|
| **Nombre**            | El nombre del usuario en Azure Active Directory.         |
| **Nombre de usuario**       | El nombre único del usuario.              |
| **Instalaciones**   | El número de aplicaciones instaladas por el usuario. |
| **Errores**        | El número de errores de instalación de aplicaciones del usuario.     |
| **Sin instalar**   | El número de aplicaciones sin instalar por el usuario. |


## <a name="next-steps"></a>Pasos siguientes

- Para más información sobre cómo trabajar con los datos de Intune, consulte [Usar el almacenamiento de datos de Intune](reports-nav-create-intune-reports.md).
- Para más información sobre las directivas de configuración de aplicaciones, vea [Directivas de configuración de aplicaciones para Intune](app-configuration-policies-overview.md).
