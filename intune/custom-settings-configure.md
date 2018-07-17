---
title: Uso de una configuración de dispositivo personalizada en Microsoft Intune - Azure | Microsoft Docs
description: Agregue o cree un perfil para usar una configuración personalizada para dispositivos iOS, Android y Windows mediante Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d917d2449e75b89db00d453b72940a93efb03321
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905009"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Crear un perfil con una configuración personalizada en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Es posible que Intune no tenga toda la configuración integrada que necesita o quiere. O bien, puede que quiera usar un valor disponible en otros perfiles de dispositivo. Para agregar estos valores, cree un perfil de dispositivo y configúrelo con los valores personalizados del dispositivo.

En este artículo, se enumeran los pasos básicos para crear un perfil con una configuración personalizada. También se incluyen vínculos para profundizar más en la creación de configuraciones personalizadas con las diferentes plataformas.

## <a name="custom-settings-on-different-platforms"></a>Configuración personalizada en distintas plataformas
La configuración personalizada se puede realizar de forma diferente en cada plataforma. Por ejemplo, para controlar características en dispositivos Android y Windows, puede especificar valores de identificador uniforme de recursos de Open Mobile Alliance (OMA-URI). Para dispositivos Apple, puede importar un archivo creado con [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo**, **Perfiles** y, luego, **Crear perfil**.
4. Escriba un **Nombre** y una **Descripción** para el perfil personalizado.
5. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar la configuración personalizada. Puede usar cualquiera de las plataformas siguientes:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**

6. En la lista desplegable de **tipos de perfil**, elija **Personalizado**.
7. En función de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. En los siguientes vínculos, se proporcionan más detalles sobre la configuración personalizada para cada plataforma:

    - [Configuración de Android](custom-settings-android.md)
    - [Configuración de iOS](custom-settings-ios.md)
    - [Configuración de macOS](custom-settings-macos.md)
    - [Configuración de Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
    - [Configuración de Windows 10](custom-settings-windows-10.md)
    - [Configuración de Windows Holographic for Business](custom-settings-windows-holographic.md)
    - [Configuración de perfil de trabajo de Android](custom-settings-android-for-work.md)

8. Cuando termine, seleccione **Crear**.

El perfil se crea y aparece en la lista de perfiles. Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).
