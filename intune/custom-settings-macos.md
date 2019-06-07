---
title: 'Agregar una configuración personalizada para dispositivos macOS en Microsoft Intune: Azure | Microsoft Docs'
titleSuffix: ''
description: Exporte una configuración de macOS desde las herramientas Apple Configurator o Apple Profile Manager y, después, importe dicha configuración en Microsoft Intune. Esta configuración puede crear, usar y controlar características y configuraciones personalizadas en dispositivos macOS. Después, este perfil personalizado puede asignarse o distribuirse en dispositivos macOS de la organización para crear una línea base o un estándar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa043e667bf12db9e30bfc56522c92d530a88c75
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373630"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>Usar una configuración personalizada para dispositivos macOS en Microsoft Intune

Con Microsoft Intune, puede agregar o crear una configuración personalizada para los dispositivos macOS mediante un "perfil personalizado". Los perfiles personalizados son una característica de Intune diseñada para agregar una configuración de dispositivo y características que no están integradas Intune.

Cuando se usan dispositivos macOS, hay dos maneras de obtener una configuración personalizada en Intune:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

Puede usar estas herramientas para exportar configuraciones a un perfil de configuración. En Intune, debe importar este archivo y, después, asignar el perfil a los usuarios y los dispositivos de macOS. Una vez asignado, la configuración se distribuye y también se crea una línea base o un estándar para macOS en la organización.

En este artículo se muestra cómo crear un perfil personalizado para dispositivos macOS. También se proporcionan indicaciones sobre el uso de Apple Configurator y Apple Profile Manager.

## <a name="before-you-begin"></a>Antes de comenzar

- Cuando use **Apple Configurator** para crear el perfil de configuración, asegúrese de que la configuración que exporta sea compatible con la versión de macOS de los dispositivos que usa. Para obtener información sobre la resolución de configuraciones incompatibles, busque **Configuration Profile Reference** (Referencia de perfiles de configuración) y **Mobile Device Management Protocol Reference** (Referencia del protocolo de administración de dispositivos móviles) en el sitio web de [Apple Developer](https://developer.apple.com/).

- Cuando use **Apple Profile Manager**, no olvide hacer lo siguiente:

  - Habilite la [administración de dispositivos móviles](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) en Profile Manager.
  - Agregue [dispositivos macOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) en Profile Manager.
  - Después de agregar un dispositivo en Profile Manager, vaya a **Under the Library** (En la biblioteca)  > **Dispositivos** > seleccione el dispositivo > **Configuración**. Especifique la configuración general, de seguridad, de privacidad, de directorio y de certificado del dispositivo.

    Descargue y guarde este archivo, ya que lo usará en el perfil de Intune. 

  - Asegúrese de que la configuración que exporte desde Apple Profile Manager sea compatible con la versión de macOS de los dispositivos que está usando. Para obtener información sobre la resolución de configuraciones incompatibles, busque **Configuration Profile Reference** (Referencia de perfiles de configuración) y **Mobile Device Management Protocol Reference** (Referencia del protocolo de administración de dispositivos móviles) en el sitio web de [Apple Developer](https://developer.apple.com/).

## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre para el perfil, como `macos custom profile`.
    - **Descripción**: escriba una descripción para el perfil
    - **Plataforma**: seleccione **macOS**.
    - **Tipo de perfil**: elija **Personalizado**.

4. En **Configuración personalizada**, escriba los valores siguientes:

    - **Nombre del perfil de configuración personalizado**: escriba un nombre para la directiva. Este nombre se muestra en el dispositivo y en el estado de Intune.
    - **Archivo del perfil de configuración**: vaya al perfil de configuración que ha creado mediante Apple Configurator o Apple Profile Manager. El archivo importado se muestra en el área **Contenido del archivo**.

5. Seleccione **Aceptar** > **Crear** para crear el perfil de Intune. Una vez que se haya completado, el perfil se mostrará en la lista **Configuración del dispositivo - Perfiles**.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md).

Vea cómo [crear el perfil en dispositivos iOS](custom-settings-ios.md).
