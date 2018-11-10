---
title: 'Agregar una configuración personalizada para dispositivos iOS en Microsoft Intune: Azure | Microsoft Docs'
titleSuffix: ''
description: Exporte una configuración de iOS desde las herramientas Apple Configurator o Apple Profile Manager y, después, importe dicha configuración en Microsoft Intune. Esta configuración puede crear, usar y controlar características y configuraciones personalizadas en dispositivos iOS. Después, este perfil personalizado puede asignarse o distribuirse en dispositivos iOS de la organización para crear una línea base o un estándar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 348a1dbf7b969956bc1ddcfb0f32a994a84e29d4
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983115"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>Usar una configuración personalizada para dispositivos iOS en Microsoft Intune

Con Microsoft Intune, puede agregar o crear una configuración personalizada para los dispositivos iOS mediante "perfiles personalizados". Los perfiles personalizados son una característica de Intune diseñada para agregar una configuración de dispositivo y características que no están integradas Intune.

Cuando se usan dispositivos iOS, hay dos maneras de obtener una configuración personalizada en Intune:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

Puede usar estas herramientas para exportar configuraciones a un perfil de configuración. En Intune, debe importar este archivo y, después, asignar el perfil a los usuarios y los dispositivos de iOS. Una vez asignado, la configuración se distribuye y también se crea una línea base o un estándar para iOS en la organización.

En este artículo se muestra cómo crear un perfil personalizado para dispositivos iOS. También se proporcionan indicaciones sobre el uso de Apple Configurator y Apple Profile Manager.

## <a name="before-you-begin"></a>Antes de comenzar

- Cuando use **Apple Configurator** para crear el perfil de configuración, asegúrese de que la configuración que exporta sea compatible con la versión de iOS de los dispositivos que usa. Para obtener información sobre la resolución de configuraciones incompatibles, busque **Configuration Profile Reference** (Referencia de perfiles de configuración) y **Mobile Device Management Protocol Reference** (Referencia del protocolo de administración de dispositivos móviles) en el sitio web de [Apple Developer](https://developer.apple.com/).

- Cuando use **Apple Profile Manager**, no olvide hacer lo siguiente:

  - Habilite la [administración de dispositivos móviles](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) en Profile Manager.
  - Agregue [dispositivos iOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) en Profile Manager.
  - Después de agregar un dispositivo en Profile Manager, vaya a **Under the Library** (En la biblioteca)  > **Dispositivos** > seleccione el dispositivo > **Configuración**. Especifique la configuración general para el dispositivo.

    Descargue y guarde este archivo, ya que lo usará en el perfil de Intune.

  - Asegúrese de que la configuración que exporte desde Apple Profile Manager sea compatible con la versión de iOS de los dispositivos que está usando. Para obtener información sobre la resolución de configuraciones incompatibles, busque **Configuration Profile Reference** (Referencia de perfiles de configuración) y **Mobile Device Management Protocol Reference** (Referencia del protocolo de administración de dispositivos móviles) en el sitio web de [Apple Developer](https://developer.apple.com/).

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre para el perfil, como `ios custom profile`.
    - **Descripción**: escriba una descripción para el perfil
    - **Plataforma**: elija **iOS**.
    - **Tipo de perfil**: elija **Personalizado**.

4. En **Configuración personalizada**, escriba los valores siguientes:

    - **Nombre del perfil de configuración personalizado**: escriba un nombre para la directiva. Este nombre se muestra en el dispositivo y en el estado de Intune.
    - **Archivo del perfil de configuración**: vaya al perfil de configuración que ha creado mediante Apple Configurator o Apple Profile Manager. El archivo importado se muestra en el área **Contenido del archivo**.

5. Seleccione **Aceptar** > **Crear** para crear el perfil de Intune. Una vez que se haya completado, el perfil se mostrará en la lista **Configuración del dispositivo - Perfiles**.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md).

Vea cómo [crear el perfil en dispositivos macOS](custom-settings-macos.md). 