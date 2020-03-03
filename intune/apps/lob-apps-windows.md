---
title: Incorporación de una aplicación de línea de negocio de Windows a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar aplicaciones de línea de negocio (LOB) de Windows mediante Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ceb4d2354ca073cf05f526df7638aebf8f16d5b7
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569496"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Incorporación de una aplicación de línea de negocio de Windows a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Una aplicación de línea de negocio (LOB) es aquella que se agrega desde un archivo de instalación de la aplicación. Este tipo de aplicación normalmente se escribe localmente. En los pasos siguientes se proporcionan instrucciones para ayudarle a agregar una aplicación de LOB de Windows a Microsoft Intune.

> [!IMPORTANT]
> Al implementar aplicaciones Win32 con un archivo de instalación con la extensión .msi (empaquetado en un archivo .intunewin con la Herramienta de preparación de contenido) considere la posibilidad de usar la [extensión de administración de Intune](../apps/intune-management-extension.md). Si mezcla la instalación de aplicaciones de Win32 y aplicaciones de línea de negocio durante la inscripción de AutoPilot, puede producirse un error en la instalación de la aplicación.  

## <a name="select-the-app-type"></a>Selección del tipo de aplicación

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en los **Otros** tipos de aplicaciones, seleccione **Aplicación de línea de negocio**.
4. Haga clic en **Seleccionar**. Se muestran los pasos para **Agregar aplicación**.

## <a name="step-1---app-information"></a>Paso 1: Información de la aplicación

### <a name="select-the-app-package-file"></a>Selección del archivo de paquete de aplicaciones

1. En el panel **Agregar aplicación**, haga clic en **Select app package file** (Seleccionar el archivo de paquete de aplicaciones). 
2. En el panel **Archivo del paquete de aplicaciones**, seleccione el botón Examinar. A continuación, seleccione un archivo de instalación de Windows con la extensión **.msi**, **.appx** o **.appxbundle**.
   Se mostrarán los detalles de la aplicación.

    > [!NOTE]
    > Las extensiones de archivo de las aplicaciones de Windows incluyen **.msi**, **.appx**, **.appxbundle**, **.msix** y **.msixbundle**.  

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

## <a name="update-a-line-of-business-app"></a>Actualización de una aplicación de línea de negocio

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > Para que el servicio Intune implemente correctamente un archivo APPX nuevo en el dispositivo, se debe incrementar la cadena `Version` en el archivo AppxManifest.xml del paquete APPX.

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configuración de una aplicación móvil MSI con auto-actualización para omitir el proceso de comprobación de versión

Puede configurar una aplicación móvil MSI con auto-actualización para que omita el proceso de comprobación de versión.

Algunas aplicaciones basadas en el instalador MSI se actualizan automáticamente por medio de una acción del desarrollador de aplicaciones o a través de otro método de actualización. Para estas aplicaciones MSI que se actualizan automáticamente, puede configurar el valor **Omitir la versión de la aplicación** en el panel **Información de la aplicación**. Cuando cambia esta configuración a **Sí**, Microsoft Intune no aplica la versión de la aplicación instalada en el cliente Windows.

Esta capacidad resulta útil para evitar que se produzca una condición de carrera. Por ejemplo, puede producirse una condición de carrera cuando la aplicación se actualiza automáticamente por el desarrollador de aplicaciones y se actualiza mediante Intune. Ambos podrían tratar de aplicar una versión de la aplicación en un cliente de Windows, lo que crea un conflicto.

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

- Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Consulte [Supervisión de información de aplicación y asignaciones con Microsoft Intune](apps-monitor.md).

- Obtenga más información sobre el contexto de la aplicación en Intune. Consulte [Información general sobre el ciclo de vida de la aplicación en Microsoft Intune](app-lifecycle.md).

- Más información sobre las aplicaciones Win32. Consulte [Administración de aplicaciones Win32](~/apps/apps-win32-app-management.md).
