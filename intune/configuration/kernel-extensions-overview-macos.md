---
title: Creación de un perfil de dispositivo de extensiones de kernel de macOS con Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Agregue o cree un perfil de dispositivo macOS y, a continuación, configure las extensiones de kernel para permitir que el usuario invalide, agregue un identificador de equipo y un paquete y un identificador de equipo en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bce6b99723c5eada8f8f29e875a1df1daa02751a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059354"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Agregar extensiones de kernel de macOS en Intune

En los dispositivos macOS, puede agregar características en el nivel de kernel. Estas características acceden a partes del sistema operativo a los que los programas normales no pueden tener acceso. Su organización puede tener necesidades o requisitos específicos que no están disponibles en una aplicación, una característica del dispositivo, etc. 

Para agregar extensiones de kernel que siempre se pueden cargar en los dispositivos, agregue "extensiones de kernel" (KEXT) en Microsoft Intune y, a continuación, implemente estas extensiones en los dispositivos.

Por ejemplo, tiene un programa antivirus que examina el dispositivo en busca de contenido malintencionado. Puede Agregar esta extensión de kernel del programa de detección de virus como una extensión de kernel permitida en Intune. A continuación, "asigne" la extensión a los dispositivos macOS.

Con esta característica, los administradores pueden permitir a los usuarios invalidar extensiones de kernel, agregar identificadores de equipo y agregar extensiones de kernel específicas en Intune.

Esta característica se aplica a:

- macOS 10.13.2 y versiones posteriores

Para usar esta característica, los dispositivos deben:

- Inscritos en Intune mediante el Programa de inscripción de dispositivos de Apple (DEP). La [inscripción automática de dispositivos MacOS](../enrollment/device-enrollment-program-enroll-macos.md) tiene más información.

  O BIEN

- Inscritos en Intune con "inscripción aprobada por el usuario" (término de Apple). [Preparar los cambios en las extensiones de kernel en MacOS High Sierra](https://support.apple.com/en-us/HT208019) (abre el sitio web de Apple) tiene más información.

Intune usa "perfiles de configuración" para crear y personalizar estas configuraciones para las necesidades de su organización. Después de agregar estas características en un perfil, puede insertar o implementar el perfil en dispositivos macOS de su organización.

En este artículo se muestra cómo crear un perfil de configuración de dispositivo con extensiones de kernel en Intune.

> [!TIP]
> Para obtener más información sobre las extensiones de kernel, consulte [información general](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) de la extensión de kernel (abre el sitio web de Apple).

## <a name="what-you-need-to-know"></a>Aspectos que debe saber

- Se pueden agregar extensiones de kernel heredadas sin firmar.
- Asegúrese de escribir el identificador de equipo y el identificador de paquete correctos de la extensión de kernel. Intune no valida los valores que especifique. Si escribe información incorrecta, la extensión no funcionará en el dispositivo.

> [!NOTE]
> Apple ha publicado información sobre la firma y la certificación para todo el software. En macOS 10.14.5 y versiones más recientes, las extensiones de kernel implementadas mediante Intune no tienen que cumplir la Directiva de certificación de Apple.
>
> Para obtener información sobre esta directiva de certificación y las actualizaciones o los cambios, consulte los siguientes recursos:
>
> - [Certificación de la aplicación antes de la distribución](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (abre el sitio web de Apple) 
> - [Preparar los cambios en las extensiones de kernel en MacOS High Sierra](https://support.apple.com/en-us/HT208019) (abre el sitio web de Apple)

## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **macOS**.
    - **Tipo de perfil**: seleccione **extensiones**.
    - **Configuración**: especifique la configuración que quiera definir. Para una lista de todas las configuraciones, y lo que hacen, consulte:

        - [macOS](kernel-extensions-settings-macos.md)

4. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y se muestra en la lista. Asegúrese de [asignar el perfil](../device-profile-assign.md) y [supervise su estado](../device-profile-monitor.md).

## <a name="next-steps"></a>Pasos siguientes

Una vez creado el perfil, está listo para asignarlo. Después, [asigne el perfil](../device-profile-assign.md) y [supervise el estado](../device-profile-monitor.md).
