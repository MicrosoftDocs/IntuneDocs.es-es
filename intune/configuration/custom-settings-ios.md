---
title: 'Incorporación de una configuración personalizada a dispositivos iOS/iPadOS en Microsoft Intune: Azure | Microsoft Docs'
titleSuffix: ''
description: Exporte una configuración de iOS/iPadOS con las herramientas Apple Configurator o Apple Profile Manager y, después, importe dicha configuración en Microsoft Intune. Esta configuración puede crear, usar y controlar características y configuraciones personalizadas de dispositivos iOS/iPadOS. Después, este perfil personalizado puede asignarse o distribuirse en dispositivos iOS/iPadOS de la organización para crear una línea base o estándar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a5dbb56a20d778a0fffc9abde1bc6ce80eb0add
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513119"
---
# <a name="use-custom-settings-for-ios-and-ipados-devices-in-microsoft-intune"></a>Uso de una configuración personalizada para dispositivos iOS y iPadOS en Microsoft Intune

Con Microsoft Intune, puede agregar o crear una configuración personalizada para los dispositivos iOS/iPadOS mediante "perfiles personalizados". Los perfiles personalizados son una característica de Intune diseñada para agregar una configuración de dispositivo y características que no están integradas Intune.

Cuando se usan dispositivos iOS/iPadOS, hay dos maneras de obtener una configuración personalizada en Intune:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

Puede usar estas herramientas para exportar configuraciones a un perfil de configuración. En Intune, importe este archivo y, después, asigne el perfil a los usuarios y los dispositivos iOS/iPadOS. Una vez asignada, las configuraciones se distribuye. También crean una base de referencia o estándar para iOS/iPad en su organización.

En este artículo se proporcionan instrucciones sobre el uso de Apple Configurator y Apple Profile Manager, y se describen las propiedades que se pueden configurar.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree el perfil](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Aspectos que debe saber

- Cuando use **Apple Configurator** para crear el perfil de configuración, asegúrese de que la configuración que exporta sea compatible con la versión de iOS/iPadOS de los dispositivos. Para obtener información sobre la resolución de configuraciones incompatibles, busque **Configuration Profile Reference** (Referencia de perfiles de configuración) y **Mobile Device Management Protocol Reference** (Referencia del protocolo de administración de dispositivos móviles) en el sitio web de [Apple Developer](https://developer.apple.com/).

- Cuando use **Apple Profile Manager**, no olvide hacer lo siguiente:

  - Habilite la [administración de dispositivos móviles](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) en Profile Manager.
  - Agregue [dispositivos iOS/iPadOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) en Profile Manager.
  - Después de agregar un dispositivo en Profile Manager, vaya a **Under the Library** (En la biblioteca)  > **Dispositivos** > seleccione el dispositivo > **Configuración**. Especifique la configuración general para el dispositivo.

    Descargue y guarde este archivo, ya que lo usará en el perfil de Intune.

  - Asegúrese de que la configuración que exporte desde Apple Profile Manager sea compatible con la versión de iOS/iPadOS de los dispositivos. Para obtener información sobre la resolución de configuraciones incompatibles, busque **Configuration Profile Reference** (Referencia de perfiles de configuración) y **Mobile Device Management Protocol Reference** (Referencia del protocolo de administración de dispositivos móviles) en el sitio web de [Apple Developer](https://developer.apple.com/).

## <a name="custom-configuration-profile-settings"></a>Ajustes de perfiles de configuración personalizados

- **Nombre del perfil de configuración personalizado**: Especifique un nombre para la directiva. Este nombre se muestra en el dispositivo y en el estado de Intune.
- **Archivo del perfil de configuración**: vaya al perfil de configuración que ha creado mediante Apple Configurator o Apple Profile Manager. El tamaño máximo de archivo es de 1 millón de bytes (justo por debajo de 1 MB). El archivo importado se muestra en el área **Contenido del archivo**.

  También puede agregar tokens de dispositivo a los archivos de configuración personalizados. Los tokens de dispositivo se usan para agregar información específica del dispositivo. Por ejemplo, para que se muestre el número de serie, escriba `{{serialnumber}}`. En el dispositivo, el texto se muestra de forma similar `123456789ABC`, lo que es único para cada dispositivo. Al especificar variables, no olvide usar llaves: `{{ }}`. En los [tokens de configuración de aplicación](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) podrá ver una lista de las variables que puede usar. También puede usar `deviceid` o cualquier otro valor específico del dispositivo.

  > [!NOTE]
  > Las variables no se validan en la interfaz de usuario y distinguen mayúsculas de minúsculas. Como resultado, es posible que vea perfiles guardados con entradas incorrectas. Por ejemplo, si escribe `{{DeviceID}}` en lugar de `{{deviceid}}`, se muestra la cadena literal en lugar del identificador del dispositivo. Asegúrese de especificar la información correcta.

Seleccione **Aceptar** > **Crear** para guardar los cambios. El perfil se crea y se muestra en la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md).

Vea cómo [crear el perfil en dispositivos macOS](custom-settings-macos.md). 
