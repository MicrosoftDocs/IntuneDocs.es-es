---
title: Adición de aplicaciones de línea de negocio de macOS a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar aplicaciones de línea de negocio (LOB) de macOS a Microsoft Intune.
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
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7aa6af751e5ab3e1e3cdff6b1d2e3d6693f65df
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755177"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Adición de aplicaciones de línea de negocio (LOB) de macOS a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Use la información de este artículo para agregar aplicaciones de línea de negocio de macOS a Microsoft Intune. Debe descargar una herramienta externa para procesar previamente los archivos *.pkg* antes de poder cargar el archivo de línea de negocio en Microsoft Intune. El procesamiento previo de los archivos *.pkg* debe realizarse en un dispositivo macOS.

> [!NOTE]
> A partir de la versión de macOS Catalina 10.15, antes de agregar las aplicaciones a Intune, asegúrese de que las aplicaciones de LOB de macOS están validadas. Si los desarrolladores de las aplicaciones de LOB no validaron sus aplicaciones, estas no podrán ejecutarse en los dispositivos macOS de los usuarios. Para obtener más información sobre cómo comprobar si una aplicación está validada, visite [Validación de aplicaciones macOS para prepararse para macOS Catalina](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579).

> [!NOTE]
> Si bien los usuarios de dispositivos macOS pueden quitar algunas de las aplicaciones macOS integradas, como Bolsa y Mapas, no pueden usar Intune para volver a implementar esas aplicaciones. Si los usuarios finales eliminan estas aplicaciones, deben ir a la tienda de aplicaciones y reinstalarlas manualmente.

## <a name="before-your-start"></a>Antes de empezar

Debe descargar una herramienta externa, marcar la herramienta descargada como ejecutable y procesar previamente los archivos *.pkg* con la herramienta antes de que pueda cargar el archivo de línea de negocio en Microsoft Intune. El procesamiento previo de los archivos *.pkg* debe realizarse en un dispositivo macOS. Use la herramienta de ajuste de aplicaciones de Intune para Mac para permitir que Microsoft Intune administre las aplicaciones Mac.

> [!IMPORTANT]
> El archivo *.pkg* primero se debe firmar con el certificado "Instalador de id. de desarrollador", que se obtiene de una cuenta de desarrollador de Apple. Solo los archivos *.pkg* se pueden usar para cargar aplicaciones de línea de negocio de macOS en Microsoft Intune. No se admite la conversión de otros formatos, como convertir de *.dmg* a *.pkg*.
>

1. Descargue la [herramienta de encapsulado de aplicaciones de Intune para Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac).

    > [!NOTE]
    > La **herramienta de ajuste de aplicaciones de Intune para Mac** se debe ejecutar en una máquina macOS. 

2. Marque la herramienta descargada como ejecutable:
   - Inicie la aplicación terminal.
   - Cambie el directorio por la ubicación donde se encuentra `IntuneAppUtil`.
   - Ejecute el comando siguiente para que la herramienta sea ejecutable:<br> 
       `chmod +x IntuneAppUtil`

3. Use el comando `IntuneAppUtil` dentro de la **herramienta de ajuste de aplicaciones de Intune para Mac** para encapsular el archivo de aplicación de línea de negocio *.pkg* desde un archivo *.intunemac*.<br>

    Comandos de ejemplo para usar en la herramienta de ajuste de aplicaciones de Microsoft Intune para macOS:
    > [!IMPORTANT]
    > Asegúrese de que el argumento `<source_file>` no contenga espacios antes de ejecutar los comandos `IntuneAppUtil`.

    - `IntuneAppUtil -h`<br>
    Este comando muestra información de uso de la herramienta.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Este comando encapsula el archivo de aplicación de línea de negocio *.pkg* en un archivo *.intunemac*.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Este comando extrae los parámetros detectados y la versión del archivo *.intunemac* creado.

## <a name="select-the-app-type"></a>Selección del tipo de aplicación

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en los **Otros** tipos de aplicaciones, seleccione **Aplicación de línea de negocio**.
4. Haga clic en **Seleccionar**. Se muestran los pasos para **Agregar aplicación**.

## <a name="step-1---app-information"></a>Paso 1: Información de la aplicación

### <a name="select-the-app-package-file"></a>Selección del archivo de paquete de aplicaciones

1. En el panel **Agregar aplicación**, haga clic en **Select app package file** (Seleccionar el archivo de paquete de aplicaciones). 
2. En el panel **Archivo del paquete de aplicaciones**, seleccione el botón Examinar. Después, seleccione un archivo de instalación de macOS con la extensión *.intunemac*.
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

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

> [!NOTE]
> Si el archivo *.pkg* contiene varias aplicaciones o instaladores de aplicaciones, Microsoft Intune solo notifica que la *aplicación* se instaló correctamente cuando todas las aplicaciones instaladas se detectan en el dispositivo.

## <a name="update-a-line-of-business-app"></a>Actualización de una aplicación de línea de negocio

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Para que el servicio de Intune implemente correctamente un nuevo archivo *.pkg* en el dispositivo, debe aumentar el valor de `version` y la cadena `CFBundleVersion` del paquete en el archivo *packageinfo* de su paquete *.pkg*.

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado aparece en la lista de aplicaciones. Ahora puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

- Obtenga más información sobre los métodos disponibles para supervisar las propiedades y la asignación de la aplicación. Para más información, vea [Supervisión de información de aplicación y asignaciones](apps-monitor.md).

- Obtenga más información sobre el contexto de la aplicación en Intune. Para más información, vea [Información general sobre los ciclos de vida del dispositivo y la aplicación](../fundamentals/device-lifecycle.md).
