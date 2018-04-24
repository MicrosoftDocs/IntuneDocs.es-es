---
title: Adición de aplicaciones de línea de negocio de Android a Microsoft Intune
titlesuffix: ''
description: Obtenga información sobre cómo agregar aplicaciones de línea de negocio (LOB) de Android a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0297cb0b399d487f548bf6fdd9fb74946bbcb7b1
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-android-line-of-business-lob-apps-to-microsoft-intune"></a>Adición de aplicaciones de línea de negocio (LOB) de Android a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Una aplicación de línea de negocio (LOB) es aquella que se agrega a Intune desde un archivo de instalación de la aplicación. Estos tipos de aplicaciones normalmente se han escrito internamente. Intune instala la aplicación de LOB en el dispositivo del usuario. 

> [!Note]
> Para obtener más información sobre las aplicaciones de línea de negocio (LOB) desde Google Play for Work Store, consulte [Working with a line-of-business app from the Google Play for Work store](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-google-play-for-work-store) (Trabajar con una aplicación de línea de negocio desde Google Play for Work Store). 

## <a name="step-1---specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En el panel **Agregar aplicación**, elija **Aplicación de línea de negocio**.

## <a name="step-2---configure-the-app-package-file"></a>Paso 2: Configuración del archivo de paquete de aplicaciones

1. En el panel **Agregar aplicación**, elija **Archivo del paquete de aplicaciones**.
2. En el panel **Archivo del paquete de aplicaciones**, elija el botón Examinar y seleccione un archivo de instalación Android con la extensión **.apk**.
3. Cuando termine, elija **Aceptar**.


## <a name="step-3---configure-app-information"></a>Paso 3: Configuración de la información de la aplicación

1. En el panel **Agregar aplicación**, elija el archivo **Paquete de la aplicación**.
2. En el panel **Información de la aplicación**, agregue los datos de su aplicación. Dependiendo de la aplicación que haya elegido, algunos de los valores de este panel pueden haberse rellenado automáticamente:
    - **Nombre**: Escriba el nombre de la aplicación que se mostrará en el Portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción**: Escriba la descripción de la aplicación que se mostrará a los usuarios en el Portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Sistema operativo mínimo**: en la lista, elija la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Ignorar la versión de la aplicación:** seleccione **Sí**, si el desarrollador de la aplicación se actualiza automáticamente.
    - **Categoría**: seleccione una o más de las categorías de aplicaciones integradas, o una categoría que haya creado. Esto facilita que los usuarios puedan encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente,, escriba un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Logotipo**: cargue un icono que esté asociado a la aplicación. Es el icono que se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3. Cuando termine, elija **Aceptar**.

## <a name="step-4---finish-up"></a>Paso 4: Finalización

1. En el panel **Agregar aplicación**, compruebe los datos de su aplicación.
2. Elija **Agregar** para cargar la aplicación en Intune.

La aplicación que ha creado se muestra en la lista de aplicaciones donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

## <a name="step-5---update-a-line-of-business-app"></a>Paso 5: Actualización de una aplicación de línea de negocio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> Para que el servicio de Intune implemente correctamente un archivo APK nuevo en el dispositivo, se debe incrementar la cadena android:versionCode en el archivo AndroidManifest.xml del paquete APK.

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

- Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Para más información, vea [Supervisión de información de aplicación y asignaciones](apps-monitor.md).

- Obtenga más información sobre el contexto de la aplicación en Intune. Para más información, vea [Información general sobre los ciclos de vida del dispositivo y la aplicación](introduction-device-app-lifecycles.md).
