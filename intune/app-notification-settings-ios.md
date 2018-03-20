---
title: "Creación de notificaciones de la aplicación para dispositivos iOS: Microsoft Intune - Azure | Microsoft Docs"
description: "Agregue o cree notificaciones de la aplicación para dispositivos iOS en Microsoft Intune. Elija las aplicaciones a las que enviar notificaciones, configure las opciones de notificación en la pantalla de bloqueo, habilite el sonido, elija el tipo de alerta y agregue un distintivo."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 018a04bd674e4f270ed2e356c08825ab1d5878da
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2018
---
# <a name="configure-app-notifications-settings-on-ios-devices-in-intune"></a>Configuración de las notificaciones de la aplicación en dispositivos iOS en Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Configure cómo envían notificaciones las aplicaciones instaladas en un dispositivo iOS. Esta configuración admite dispositivos supervisados que ejecuten iOS 9.3 y versiones posteriores.

## <a name="add-the-app-notification"></a>Agregar la notificación de la aplicación

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. En el perfil de iOS o macOS, seleccione **Características del dispositivo**. En [Características del dispositivo iOS o macOS](device-features-configure.md) se enumeran los pasos para crear un perfil.
3. Seleccione **Notificaciones de la aplicación (solo supervisado)** y, después, haga clic en **Agregar**: ![Agregar notificación de la aplicación en el perfil de iOS o macOS en Intune](./media/ios-macos-app-notifications.png).
4. Introduzca las siguientes propiedades:

  - **Identificador de lote de aplicaciones**: escriba el **identificador de lote de aplicaciones** de la aplicación que quiere configurar. En **Referencia de id. de lote de aplicaciones iOS integradas** (en este artículo) se proporciona ayuda.
  - **Nombre de la aplicación**: escriba el nombre de la aplicación que quiera configurar. Este nombre no se muestra en el dispositivo y se usa para ayudarle a identificar la aplicación en la lista.
  - **Publicador**: escriba el publicador de la aplicación que quiera configurar. El nombre del publicador no se muestra en el dispositivo y se usa solo para ayudarle a identificar la aplicación en la lista.
  - **Notificaciones**: habilite o deshabilite el envío de notificaciones de la aplicación al dispositivo. Si deshabilita esta configuración, también se deshabilitan las siguientes.
    - **Mostrar en Centro de notificaciones**: habilite esta opción para permitir que la aplicación muestre notificaciones en el centro de notificaciones del dispositivo.
    - **Mostrar en pantalla de bloqueo**: habilite esta opción para ver las notificaciones de la aplicación en la pantalla de bloqueo del dispositivo.
    - **Alert type** (Tipo de alerta): seleccione el tipo de notificación que desea cuando el dispositivo se desbloquea:
      - **None** (Ninguna): no se muestra ninguna notificación.
      - **Banner** (Mensaje emergente): un mensaje emergente que muestra la notificación aparece brevemente.
      - **Modal** (Modal): se muestra la notificación y el usuario debe descartarla manualmente antes de poder continuar usando el dispositivo.
    - **Distintivo en el icono de la aplicación**: habilite esta opción para agregar un distintivo en el icono de aplicación para indicar que la aplicación ha enviado una notificación.
    - **Sonidos**: habilite esta opción para reproducir un sonido cuando se entrega una notificación.

5. Siga agregando las aplicaciones que necesita. Cuando termine de agregar aplicaciones, haga clic en **Aceptar**.
6. Haga clic en **Crear** para guardar el perfil.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referencia de identificador de lote para aplicaciones iOS integradas

En la lista siguiente se muestra el identificador de lote de algunas aplicaciones iOS integradas comunes. Para encontrar el identificador de lote de otras aplicaciones se recomienda ponerse en contacto con el proveedor de software.

|||
|-|-|
|Nombre de la aplicación|Identificador de lote|
|Tienda de aplicaciones|com.apple.AppStore|
|Calculadora|com.apple.calculator|
|Calendario|com.apple.mobilecal|
|Cámara|com.apple.camera|
|Reloj|com.apple.mobiletimer|
|Compass|com.apple.compass|
|Contactos|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Buscar amigos|com.apple.mobileme.fmf1|
|Buscar mi iPhone|com.apple.mobileme.fmip1|
|Centro de juegos|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Mantenimiento|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|Asignaciones|com.apple.Maps|
|Mensajes|com.apple.MobileSMS|
|Música|com.apple.Music|
|Noticias|com.apple.news|
|Notas|com.apple.mobilenotes|
|Números|com.apple.Numbers|
|Páginas|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Fotos|com.apple.mobileslideshow|
|Podcasts|com.apple.podcasts|
|Recordatorios|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Configuración|com.apple.Preferences|
|Acciones|com.apple.stocks|
|Sugerencias|com.apple.tips|
|Vídeos|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|Inspección|com.apple.Bridge|
|Clima|com.apple.weather|

## <a name="next-steps"></a>Pasos siguientes

Asigne el perfil de dispositivo a los grupos que elija. En [Cómo asignar perfiles de dispositivo](device-profile-assign.md) se enumeran los pasos.