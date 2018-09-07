---
title: Adición de aplicaciones de línea de negocio de macOS a Microsoft Intune
titlesuffix: ''
description: Aprenda a agregar aplicaciones de línea de negocio (LOB) de macOS a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d527b36876adf29c12d3577f7dcd09416b4d5a37
ms.sourcegitcommit: 40b1d82df99f09a75a17065cdd0e84d8038f460a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "40255467"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Adición de aplicaciones de línea de negocio (LOB) de macOS a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use la información de este artículo para agregar aplicaciones de línea de negocio de macOS a Microsoft Intune. Debe descargar una herramienta externa para procesar previamente los archivos *.pkg* antes de poder cargar el archivo de línea de negocio en Microsoft Intune. El procesamiento previo de los archivos *.pkg* debe realizarse en un dispositivo macOS.

> [!NOTE]
> Si bien los usuarios de dispositivos macOS pueden quitar algunas de las aplicaciones macOS integradas, como Bolsa y Mapas, no pueden usar Intune para volver a implementar esas aplicaciones. Si los usuarios finales eliminan estas aplicaciones, deben ir a la tienda de aplicaciones y reinstalarlas manualmente.

## <a name="before-your-start"></a>Antes de empezar

Debe descargar una herramienta externa para procesar previamente los archivos *.pkg* antes de poder cargar el archivo de línea de negocio en Microsoft Intune. El procesamiento previo de los archivos *.pkg* debe realizarse en un dispositivo macOS. Use la herramienta de ajuste de aplicaciones de Intune para Mac para permitir que Microsoft Intune administre las aplicaciones Mac.

> [!IMPORTANT]
> Solo los archivos *.pkg* se pueden usar para cargar aplicaciones de línea de negocio de macOS en Microsoft Intune. No se admite la conversión de otros formatos, como convertir de *.dmg* a *.pkg*.

1. Descargue y ejecute la [herramienta de ajuste de aplicaciones de Intune para Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac).

    > [!NOTE]
    > La **herramienta de ajuste de aplicaciones de Intune para Mac** se debe ejecutar en una máquina macOS.

2. Use el comando `IntuneAppUtil` dentro de la **herramienta de ajuste de aplicaciones de Intune para Mac** para encapsular el archivo de aplicación de línea de negocio *.pkg* desde un archivo *.intunemac*.<br>

    Comandos de ejemplo para usar en la herramienta de ajuste de aplicaciones de Microsoft Intune para macOS:
    
    - `IntuneAppUtil -h`<br>
    Este comando muestra información de uso de la herramienta.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Este comando encapsula el archivo de aplicación de línea de negocio *.pkg* en un archivo *.intunemac*.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Este comando extrae los parámetros detectados y la versión del archivo *.intunemac* creado.

## <a name="step-1---specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En el panel **Agregar aplicación**, elija **Aplicación de línea de negocio**.

## <a name="step-2---configure-the-app-package-file"></a>Paso 2: Configuración del archivo de paquete de aplicaciones

1. En el panel **Agregar aplicación**, elija **Archivo del paquete de aplicaciones**.
2. En el panel **Archivo del paquete de aplicaciones**, elija el botón Examinar y seleccione un archivo de instalación de macOS con la extensión *.intunemac*.
3. Cuando termine, elija **Aceptar**.


## <a name="step-3---configure-app-information"></a>Paso 3: Configuración de la información de la aplicación

1. En el panel **Agregar aplicación**, elija **Información de la aplicación**.
2. En el panel **Información de la aplicación**, agregue los datos de su aplicación. Dependiendo de la aplicación que haya elegido, algunos de los valores de este panel pueden haberse rellenado automáticamente:
    - **Nombre**: Escriba el nombre de la aplicación que se mostrará en el Portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción**: Escriba una descripción para la aplicación que se mostrará a los usuarios en el Portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Sistema operativo mínimo**: en la lista, elija la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
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

1. En el panel **Agregar aplicación**, compruebe que los detalles de la aplicación son correctos.
2. Elija **Agregar** para cargar la aplicación en Intune.

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

> [!NOTE]
> Si el archivo *.pkg* contiene varias aplicaciones o instaladores de aplicaciones, Microsoft Intune solo notifica que la *aplicación* se instaló correctamente cuando todas las aplicaciones instaladas se detectan en el dispositivo.

## <a name="step-5---update-a-line-of-business-app"></a>Paso 5: Actualización de una aplicación de línea de negocio

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Para que el servicio de Intune implemente correctamente un nuevo archivo *.pkg* en el dispositivo, debe aumentar el valor de `version` y la cadena `CFBundleVersion` del paquete en el archivo *packageinfo* de su paquete *.pkg*.

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

- Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Para más información, vea [Supervisión de información de aplicación y asignaciones](apps-monitor.md).

- Obtenga más información sobre el contexto de la aplicación en Intune. Para más información, vea [Información general sobre los ciclos de vida del dispositivo y la aplicación](introduction-device-app-lifecycles.md).
