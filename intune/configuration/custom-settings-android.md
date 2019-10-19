---
title: 'Agregar una configuración personalizada para dispositivos Android en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o cree un perfil personalizado para dispositivos Android para crear un perfil de Wi-Fi con una clave precompartida, cree un perfil de VPN por aplicación o bien permita o bloquee aplicaciones para dispositivos Samsung Knox Standard en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17f0b30d0a8c706a7fdff1c7da722eeccdf097eb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495791"
---
# <a name="use-custom-settings-for-android-devices-in-microsoft-intune"></a>Uso de una configuración personalizada para dispositivos Android en Microsoft Intune

Con Microsoft Intune, puede agregar o crear una configuración personalizada para los dispositivos Android mediante un "perfil personalizado". Los perfiles personalizados son una característica de Intune diseñada para agregar una configuración de dispositivo y características que no están integradas Intune.

Los perfiles personalizados de Android usan la configuración OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) para configurar diferentes características en dispositivos Android. Esta configuración la suelen usar los fabricantes de dispositivos móviles para controlar estas características.

Si usa un perfil personalizado, puede configurar y asignar los siguientes valores de Android. Las opciones siguientes no están integradas en Intune:

- [Crear un perfil de Wi-Fi con una clave precompartida](/intune/wi-fi-profile-shared-key)
- [Creación de un perfil de VPN por aplicación](/intune/android-pulse-secure-per-app-vpn)
- [Uso de directivas personalizadas para permitir y bloquear aplicaciones para dispositivos Samsung Knox Standard](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Solo se pueden configurar los valores enumerados mediante un perfil personalizado. Los dispositivos Android no exponen una lista completa de opciones de OMA-URI que pueda configurar. Si quiere ver más valores, vote por ellos en el [sitio de Uservoice de Intune](https://microsoftintune.uservoice.com/forums/291681-ideas).

En este artículo se muestra cómo crear un perfil personalizado para dispositivos Android.

## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre para el perfil, como `android custom profile`.
    - **Descripción**: escriba una descripción para el perfil
    - **Plataforma**: elija **Android**.
    - **Tipo de perfil**: elija **Personalizado**.

4. En **Configuración OMA-URI personalizada**, seleccione **Agregar**. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre único para la configuración OMA-URI, de modo que pueda encontrarla fácilmente.
    - **Descripción**: escriba una descripción con información general sobre la configuración y otros detalles importantes.
    - **OMA-URI**: escriba la configuración OMA-URI que quiere usar.
    - **Tipo de datos**: elija el tipo de datos que se usará para esta configuración OMA-URI. Las opciones son:

      - String
      - Cadena (archivo XML)
      - Fecha y hora
      - Integer
      - Punto flotante
      - Boolean
      - Base64 (archivo)

    - **Valor**: escriba el valor de datos que quiere asociar con la configuración OMA-URI especificada. El valor depende del tipo de datos que ha seleccionado. Por ejemplo, si elige **Fecha y hora**, debe seleccionar el valor en un selector de fecha.

    Después de agregar algunos valores de configuración, puede seleccionar **Exportar**. Haga clic en **Exportar** para crear una lista de todos los valores agregados en un archivo de valores separados por comas (.csv).

5. Haga clic en **Aceptar** para guardar los cambios. Continúe agregando más valores según sea necesario. 
6. Cuando termine, seleccione **Aceptar** > **Crear** para crear el perfil de Intune. Una vez que se haya completado, el perfil se mostrará en la lista **Configuración del dispositivo - Perfiles**.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md).

Vea cómo [crear el perfil en dispositivos Android Enterprise](custom-settings-android-for-work.md).
