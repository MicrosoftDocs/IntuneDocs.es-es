---
title: Crear perfil de dispositivo de extensiones del núcleo de macOS con Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Agregar o crear perfil de dispositivo de macOS y, a continuación, configurar las extensiones de kernel para permitir el reemplazo de usuario, agregue el identificador de equipo y un identificador de lote y el equipo en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403911"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Agregar extensiones de kernel de macOS en Intune

En los dispositivos macOS, puede agregar características en el nivel de kernel. Estas características, tener acceso a las partes del sistema operativo que no se pueden obtener acceso programas normales. La organización puede tener necesidades específicas o requisitos que no están disponibles en una aplicación, una característica de dispositivo y así sucesivamente. 

Para agregar extensiones de kernel que se permiten siempre que se cargue en los dispositivos, agregue "extensions kernel" (KEXT) en Microsoft Intune y, a continuación, implementar estas extensiones en los dispositivos.

Por ejemplo, tiene un programa antivirus que examina el dispositivo para el contenido malintencionado. Puede agregar esta extensión de kernel del programa de detección como una extensión de kernel permitidos en Intune de virus. A continuación, "asignar" la extensión a los dispositivos macOS.

Con esta característica, los administradores pueden permitir a los usuarios reemplazar las extensiones de kernel, agregue los identificadores de equipo y agregar extensiones específicas de kernel en Intune.

Esta característica se aplica a:

- macOS 10.13.2 y versiones posteriores

Para usar esta característica, los dispositivos deben estar:

- Inscritos en Intune mediante el programa de inscripción de dispositivos (DEP de Apple). [Inscribir automáticamente los dispositivos macOS](device-enrollment-program-enroll-macos.md) tiene más información.

  O BIEN

- Inscritos en Intune con "inscripción aprobado por el usuario" (término de Apple). [Prepararse para cambios a las extensiones de kernel en macOS High Sierra](https://support.apple.com/en-us/HT208019) (abre el sitio web de Apple) tiene más información.

Intune usa "perfiles de configuración" para crear y personalizar estas configuraciones para las necesidades de su organización. Después de agregar estas características en un perfil, puede insertar o implementar el perfil en dispositivos macOS de su organización.

Este artículo muestra cómo crear un perfil de configuración de dispositivo mediante extensiones de kernel en Intune.

> [!TIP]
> Para obtener más información acerca de las extensiones de kernel, vea [Introducción a la extensión de kernel](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (abre el sitio web de Apple).

## <a name="what-you-need-to-know"></a>Aspectos que debe saber

- Se pueden agregar extensiones de kernel heredado sin signo.
- Asegúrese de especificar el identificador de equipo correcto y agrupar el identificador de la extensión de kernel. Intune no valida los valores que especifique. Si escribe la información es incorrecta, la extensión no funcionará en el dispositivo.

> [!NOTE]
> Apple publicado información relacionada con la firma y Notarización para todo el software. En macOS 10.14.5 y kernel más reciente, las extensiones implementadas a través de Intune no tienen que cumple la directiva de Notarización de Apple.
>
> Para obtener información sobre esta directiva Notarización y las actualizaciones o cambios, consulte los siguientes recursos:
>
>  - [Notarizing la aplicación antes de la distribución](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (abre el sitio web de Apple) 
>  - [Prepararse para cambios a las extensiones de kernel en macOS High Sierra](https://support.apple.com/en-us/HT208019) (abre el sitio web de Apple)

## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **macOS**.
    - **Tipo de perfil**: seleccione **extensiones**.
    - **Configuración**: especifique la configuración que quiera definir. Para una lista de todas las configuraciones, y lo que hacen, consulte:

        - [macOS](kernel-extensions-settings-macos.md)

4. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y se muestra en la lista. Asegúrese de [asignar el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

## <a name="next-steps"></a>Pasos siguientes

Una vez creado el perfil, está listo para asignarlo. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
