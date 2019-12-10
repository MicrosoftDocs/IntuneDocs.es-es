---
title: Incorporación de una aplicación de línea de negocio de iOS a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar una aplicación de línea de negocio (LOB) de iOS a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e1d3c6a427dcbd4a7946c5f3e180de56e8cb955
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563522"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Incorporación de una aplicación de línea de negocio de iOS a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Use la información de este artículo para agregar una aplicación de línea de negocio (LOB) de iOS a Microsoft Intune. Una aplicación de línea de negocio (LOB) es aquella que se agrega a Intune desde un archivo de instalación de la aplicación IPA. Este tipo de aplicación normalmente se escribe localmente. En primer lugar, debe unirse al programa iOS Developer Enterprise Program. Para más información sobre cómo hacerlo, consulte el [sitio web de Apple](https://developer.apple.com/programs/ios/enterprise/).

>[!NOTE]
>Los usuarios de dispositivos iOS pueden quitar algunas de las aplicaciones iOS integradas, como Bolsa y Mapas. No puede usar Intune para volver a implementar esas aplicaciones. Si los usuarios eliminan estas aplicaciones, deben ir a la tienda de aplicaciones y reinstalarlas manualmente.
>
>Las aplicaciones LOB de iOS tienen un límite de tamaño máximo de 4 GB por aplicación.

## <a name="step-1-specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Agregar aplicación**, seleccione **Aplicación de línea de negocio** para **Tipo de aplicación**.

## <a name="step-2-configure-the-app-package-file"></a>Paso 2: Configuración del archivo de paquete de aplicaciones

1. En el panel **Agregar aplicación**, seleccione **Archivo del paquete de aplicaciones**.
2. En el panel **Archivo del paquete de aplicaciones**, seleccione el botón Examinar. Luego, seleccione un archivo de instalación de iOS con la extensión **.ipa**.
3. Cuando haya terminado, seleccione **Aceptar**.


## <a name="step-3-configure-app-information"></a>Paso 3: Configuración de información de la aplicación

1. En el panel **Agregar aplicación**, seleccione **Información de la aplicación**.
2. En el panel **Información de la aplicación**, agregue los datos de su aplicación. Dependiendo de la aplicación que haya elegido, algunos de los valores de este panel podrían rellenarse automáticamente.
    - **Nombre**: escriba el nombre de la aplicación tal como aparece en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo aparece una de las aplicaciones en el portal de empresa.
    - **Descripción**: Escriba una descripción de la aplicación. La descripción aparece en el portal de empresa.
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
3. Cuando haya terminado, seleccione **Aceptar**.

## <a name="step-4-finish-up"></a>Paso 4: Finalizar

1. En el panel **Agregar aplicación**, compruebe que los detalles de la aplicación son correctos.
2. Seleccione **Agregar** para cargar la aplicación en Intune.

La aplicación que ha creado ahora aparece en la lista de aplicaciones. En la lista, puede asignar las aplicaciones a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

> [!NOTE]
> Los perfiles de aprovisionamiento para las aplicaciones LOB de iOS tienen un aviso de 30 días antes de que caduquen.

## <a name="step-5-update-a-line-of-business-app"></a>Paso 5: Actualización de una aplicación de línea de negocio

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

La actualización de la aplicación de línea de negocio se instalará automáticamente.

> [!NOTE]
> Para que el servicio de Intune implemente correctamente un archivo IPA nuevo en el dispositivo, se debe incrementar la cadena `CFBundleVersion` en el archivo Info.plist del paquete IPA.

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

- Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Consulte [Supervisión de información de aplicación y asignaciones con Microsoft Intune](apps-monitor.md).

- Obtenga más información sobre el contexto de la aplicación en Intune. Consulte [Información general sobre los ciclos de vida del dispositivo y la aplicación](../fundamentals/device-lifecycle.md).
