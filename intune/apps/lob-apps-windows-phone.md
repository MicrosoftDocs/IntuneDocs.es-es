---
title: Incorporación de una aplicación de línea de negocio de Windows Phone a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar aplicaciones de línea de negocio (LOB) de Windows Phone mediante Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 328bafc2a55191c203263911ceaac9b520eb07f5
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755160"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>Incorporación de una aplicación de línea de negocio de Windows Phone a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Use la información de este artículo para agregar un aplicación de línea de negocio (LOB) de Windows Phone a Microsoft Intune. Una aplicación de línea de negocio es aquella que se agrega a Intune desde un archivo de instalación de la aplicación. Este tipo de aplicación normalmente se escribe localmente. Intune instala la aplicación de línea de negocio en el dispositivo del usuario. 

## <a name="select-the-app-type"></a>Selección del tipo de aplicación

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en los **Otros** tipos de aplicaciones, seleccione **Aplicación de línea de negocio**.
4. Haga clic en **Seleccionar**. Se muestran los pasos para **Agregar aplicación**.

## <a name="step-1---app-information"></a>Paso 1: Información de la aplicación

### <a name="select-the-app-package-file"></a>Selección del archivo de paquete de aplicaciones

1. En el panel **Agregar aplicación**, haga clic en **Select app package file** (Seleccionar el archivo de paquete de aplicaciones). 
2. En el panel **Archivo del paquete de aplicaciones**, seleccione el botón Examinar. A continuación, seleccione un archivo de instalación de Windows Phone con la extensión **.xap**.
   Se mostrarán los detalles de la aplicación.
3. Cuando haya terminado, seleccione **Aceptar** en el panel **Archivo del paquete de aplicaciones** para agregar la aplicación.

### <a name="set-app-information"></a>Establecimiento de la información de la aplicación

1. En la página **Información de la aplicación**, agregue los datos de su aplicación. Dependiendo de la aplicación que haya elegido, algunos de los valores de este panel podrían rellenarse automáticamente.
    - **Nombre**: escriba el nombre de la aplicación tal como aparece en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo aparece una de las aplicaciones en el portal de empresa.
    - **Descripción**: escriba una descripción de la aplicación. La descripción aparece en el portal de empresa.
    - **Publicador**: Escriba el nombre del publicador de la aplicación.
    - **Versión mínima del sistema operativo**: en la lista, elija la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Categoría**: seleccione una o varias de las categorías de aplicaciones integradas o seleccione una categoría que haya creado. Las categorías facilitan a los usuarios encontrar la aplicación cuando exploran el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: Muestra la aplicación de forma destacada en la página principal del portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL aparece en el portal de empresa.
    - **Dirección URL de privacidad**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL aparece en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación. Un ejemplo es **Departamento de Recursos Humanos**.
    - **Notas**: escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: cargue un icono que esté asociado a la aplicación. Este icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
2. Haga clic en **Siguiente** para mostrar la página **Etiquetas de ámbito**.

## <a name="step-2---select-scope-tags-optional"></a>Paso 2: Selección de Etiquetas de ámbito (opcional)
Puede usar las etiquetas de ámbito para determinar quién puede ver información de la aplicación cliente en Intune. Para obtener más información sobre las etiquetas de ámbito, consulte [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Uso del control de acceso basado en roles y de las etiquetas de ámbito para la TI distribuida).

1. Si quiere, haga clic en **Seleccionar etiquetas de ámbito** para agregar etiquetas de ámbito para la aplicación. 
2. Haga clic en **Siguiente** para abrir la página **Asignaciones**.

## <a name="step-3---assignments"></a>Paso 3: Asignaciones

1. Seleccione las asignaciones de grupo **Requerido**, **Disponible para dispositivos inscritos** o **Desinstalar** para la aplicación. Para más información, consulte [Agregar grupos para organizar usuarios y dispositivos](~/fundamentals/groups-add.md) y [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).
2. Elija **Siguiente** para mostrar la página **Revisar y crear**. 

## <a name="step-4---review--create"></a>Paso 4: Revisión y creación

1. Revise los valores y la configuración que especificó para la aplicación.
2. Cuando haya terminado, haga clic en **Crear** para agregar la aplicación a Intune.

    Se muestra la hoja **Información general** correspondiente a la aplicación de línea de negocio.

La aplicación que ha creado ahora aparece en la lista de aplicaciones. En la lista, puede asignar las aplicaciones a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

- Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Consulte [Supervisión de información de aplicación y asignaciones con Microsoft Intune](apps-monitor.md).

- Obtenga más información sobre el contexto de la aplicación en Intune. Consulte [Información general sobre los ciclos de vida del dispositivo y la aplicación](../fundamentals/device-lifecycle.md).
