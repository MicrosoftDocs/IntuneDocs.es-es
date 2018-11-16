---
title: Incorporación de una aplicación de línea de negocio de Windows a Microsoft Intune
titlesuffix: ''
description: Aprenda a agregar una aplicación de línea de negocio de Windows a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04c9c6b184fac2082649e8be8e60e6ac3f5a5669
ms.sourcegitcommit: 5d5448f6c365aeb01d6f2488bf122024b9616bec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2018
ms.locfileid: "51212434"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Incorporación de una aplicación de línea de negocio de Windows a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Una aplicación de línea de negocio (LOB) es aquella que se agrega desde un archivo de instalación de la aplicación. Este tipo de aplicación normalmente se escribe localmente. En los pasos siguientes se proporcionan instrucciones para ayudarle a agregar una aplicación de LOB de Windows a Microsoft Intune.

## <a name="step-1-specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En la carga de trabajo **Aplicaciones cliente**, seleccione **Administrar** > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En el panel **Agregar aplicación**, seleccione **Aplicación de línea de negocio**.

## <a name="step-2-configure-the-app-package-file"></a>Paso 2: Configuración del archivo de paquete de aplicaciones

1. En el panel **Agregar aplicación**, seleccione **Archivo del paquete de aplicaciones**.
2. En el panel **Archivo del paquete de aplicaciones**, seleccione el botón Examinar. A continuación, seleccione un archivo de instalación de Windows con la extensión **.msi**, **.appx** o **.appxbundle**.

    > [!NOTE]
    > Las extensiones de archivo de las aplicaciones de Windows incluyen **.msi**, **.appx**, **.appxbundle**, **.msix** y **.msixbundle**.  

1. Cuando haya terminado, seleccione **Aceptar**.


## <a name="step-3-configure-app-information"></a>Paso 3: Configuración de la información de la aplicación

1. En el panel **Agregar aplicación**, seleccione **Información de la aplicación**.
2. En el panel **Información de la aplicación**, configure la información siguiente. Algunos de los valores de este panel podrían rellenarse automáticamente.
    - **Nombre**: escriba el nombre de la aplicación tal como aparece en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo aparece una de las aplicaciones en el portal de empresa.
    - **Descripción:** escriba una descripción de la aplicación. La descripción aparece en el portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Omitir la versión de la aplicación**: establezca esta opción en **Sí** en el caso de que el desarrollador de la aplicación actualice automáticamente esta. Esta opción se aplica solo a las aplicaciones para móviles .msi.
    - **Categoría**: seleccione una o varias de las categorías de aplicaciones integradas, o seleccione una categoría que haya creado. Las categorías facilitan a los usuarios encontrar la aplicación cuando exploran el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre la aplicación. La dirección URL aparece en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre la aplicación. La dirección URL aparece en el portal de empresa.
    - **Argumentos de línea de comandos**: si lo desea, especifique los argumentos de línea de comandos que desea aplicar al archivo .msi cuando se ejecuta. Un ejemplo es **/q**.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación. Un ejemplo es **Departamento de Recursos Humanos**.
    - **Notas**: escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: cargue un icono que esté asociado a la aplicación. El icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3. Cuando haya terminado, seleccione **Aceptar**.

## <a name="step-4-finish-up"></a>Paso 4: Finalización

1. En el panel **Agregar aplicación**, compruebe que ha configurado correctamente la información de la aplicación.
2. Seleccione **Agregar** para cargar la aplicación en Intune.

## <a name="step-5-update-a-line-of-business-app"></a>Paso 5: Actualización de una aplicación de línea de negocio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configuración de una aplicación móvil MSI con auto-actualización para omitir el proceso de comprobación de versión

Puede configurar una aplicación móvil MSI con auto-actualización para que omita el proceso de comprobación de versión. 

Los desarrolladores de aplicaciones actualizan automáticamente algunas aplicaciones MSI basadas en el instalador. Para estas aplicaciones MSI que se actualizan automáticamente, puede configurar el valor **Omitir la versión de la aplicación** en el panel **Información de la aplicación**. Cuando cambia esta configuración a **Sí**, Microsoft Intune no aplica la versión de la aplicación instalada en el cliente Windows. 

Esta capacidad resulta útil para evitar que se produzca una condición de carrera. Por ejemplo, puede producirse una condición de carrera cuando la aplicación se actualiza automáticamente por el desarrollador de aplicaciones y se actualiza mediante Intune. Ambos podrían tratar de aplicar una versión de la aplicación en un cliente de Windows, lo que crea un conflicto.

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

- Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Consulte [Supervisión de información de aplicación y asignaciones con Microsoft Intune](apps-monitor.md).

- Obtenga más información sobre el contexto de la aplicación en Intune. Consulte [Información general sobre los ciclos de vida del dispositivo y la aplicación](introduction-device-app-lifecycles.md).
