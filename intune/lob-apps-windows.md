---
title: Adición de aplicaciones de línea de negocio de Windows a Microsoft Intune
titlesuffix: ''
description: Descubra cómo agregar aplicaciones de línea de negocio (LOB) de Windows a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa11c29a50006053b6e9b52516a595683d6f4cfd
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>Adición de aplicaciones de línea de negocio (LOB) de Windows a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Una aplicación de línea de negocio (LOB) es aquella que se agrega desde un archivo de instalación de la aplicación. Estos tipos de aplicaciones normalmente se han escrito internamente. En los pasos siguientes se proporcionan instrucciones para ayudarle a agregar una aplicación de LOB de Windows a Microsoft Intune.

## <a name="step-1---specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En el panel **Agregar aplicación**, elija **Aplicación de línea de negocio**.

## <a name="step-2---configure-the-app-package-file"></a>Paso 2: Configuración del archivo de paquete de aplicaciones

1. En el panel **Agregar aplicación**, elija el archivo **Paquete de la aplicación**.
2. En el panel del archivo **Paquete de la aplicación**, elija el botón Examinar y seleccione un archivo de instalación de Windows con la extensión **.msi**, **.appx** o **.appxbundle**.
3. Cuando termine, elija **Aceptar**.


## <a name="step-3---configure-app-information"></a>Paso 3: Configuración de la información de la aplicación

1. En el panel **Agregar aplicación**, elija el archivo **Paquete de la aplicación**.
2. En el panel **Información de la aplicación**, configure la información siguiente (algunos de los valores de este panel podrían rellenarse de forma automática):
    - **Nombre**: escriba el nombre de la aplicación tal como se muestra en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se muestra a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción:** escriba una descripción de la aplicación. La descripción se muestra a los usuarios en el portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Ignorar la versión de la aplicación:** seleccione **Sí**, si el desarrollador de la aplicación se actualiza automáticamente.
    - **Categoría**: seleccione una o más de las categorías de aplicaciones integradas, o una categoría que haya creado. La categorización de aplicaciones facilita a los usuarios encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre la aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre la aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Argumentos de línea de comandos**: si lo desea, especifique los argumentos de línea de comandos que desea aplicar al archivo .msi cuando se ejecuta, como **/q**.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente,, escriba un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Logotipo**: cargue un icono que esté asociado a la aplicación. El icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3. Cuando termine, elija **Aceptar**.

## <a name="step-4---finish-up"></a>Paso 4: Finalización

1. En el panel **Agregar aplicación**, compruebe que haya configurado correctamente la información de la aplicación.
2. Elija **Agregar** para cargar la aplicación en Intune.

## <a name="step-5---update-a-line-of-business-app"></a>Paso 5: Actualización de una aplicación de línea de negocio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configuring-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configuración de una aplicación móvil MSI con auto-actualización para omitir el proceso de comprobación de versión

Puede configurar una aplicación móvil MSI con auto-actualización para que omita el proceso de comprobación de versión. Los desarrolladores de aplicaciones actualizan automáticamente algunas aplicaciones MSI basadas en el instalador. Para estas aplicaciones MSI que se actualizan automáticamente, puede configurar el valor **Omitir la versión de la aplicación** en la hoja **Información de la aplicación**. Cuando se cambia esta configuración a **Sí**, Microsoft Intune no aplica la versión de la aplicación instalada en el cliente de Windows. Esta capacidad resulta útil para evitar que se produzca una condición de carrera. Por ejemplo, este tipo de condición de carrera podría producirse cuando la aplicación que el desarrollador de aplicaciones actualiza automáticamente también la estuviera actualizando Intune. Ambos podrían tratar de aplicar una versión de la aplicación en un cliente de Windows, lo que podría crear un conflicto.

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

- Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Para más información, vea [Supervisión de información de aplicación y asignaciones](apps-monitor.md).

- Obtenga más información sobre el contexto de la aplicación en Intune. Para más información, vea [Información general sobre los ciclos de vida del dispositivo y la aplicación](introduction-device-app-lifecycles.md).
