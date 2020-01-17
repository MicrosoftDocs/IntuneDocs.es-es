---
title: 'Agregar una configuración personalizada para dispositivos Android en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o cree un perfil personalizado para dispositivos Android para crear un perfil de Wi-Fi con una clave precompartida, cree un perfil de VPN por aplicación o bien permita o bloquee aplicaciones para dispositivos Samsung Knox Standard en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
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
ms.openlocfilehash: 8137a806598facd540781702b1c2c359e89d6bda
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206795"
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

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil es el **perfil personalizado de Android**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: Seleccione **Android**.
    - **Tipo de perfil**: seleccione **personalizado**.

4. En **Configuración OMA-URI personalizada**, seleccione **Agregar**. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre único para la configuración OMA-URI, de modo que pueda encontrarla fácilmente.
    - **Descripción**: escriba una descripción con información general sobre la configuración y otros detalles importantes.
    - **OMA-URI**: escriba la configuración OMA-URI que quiere usar.
    - **Tipo de datos**: seleccione el tipo de datos que se va a usar para esta configuración OMA-URI. Las opciones son:

      - String
      - Cadena (archivo XML)
      - Fecha y hora
      - Integer
      - Punto flotante
      - Boolean
      - Base64 (archivo)

    - **Valor**: escriba el valor de datos que quiere asociar con la configuración OMA-URI especificada. El valor depende del tipo de datos que ha seleccionado. Por ejemplo, si selecciona **Fecha y hora**, seleccione el valor en un selector de fecha.

    Después de agregar algunos valores de configuración, puede seleccionar **Exportar**. Haga clic en **Exportar** para crear una lista de todos los valores agregados en un archivo de valores separados por comas (.csv).

5. Haga clic en **Aceptar** para guardar los cambios. Continúe agregando más valores según sea necesario.
6. Cuando termine, seleccione **Aceptar** > **Crear** para crear el perfil de Intune. Una vez hecho, el perfil aparece en la lista **Dispositivos - Perfiles de configuración**.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](../device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Cree un [perfil personalizado en dispositivos empresariales Android](custom-settings-android-for-work.md).
