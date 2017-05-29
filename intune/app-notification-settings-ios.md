---
title: "Configuración de notificaciones de aplicación de Intune para dispositivos iOS"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Azure de Intune: conozca la configuración que puede usar para controlar las notificaciones de aplicaciones en dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c64167275a2628c6a3a4e899e00c25df4c10b06b
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="intune-app-notifications-settings-for-ios-devices"></a>Configuración de notificaciones de aplicación de Intune para dispositivos iOS

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Ahora configuraremos cómo las aplicaciones instaladas en un dispositivo envían notificaciones. Esta configuración admite dispositivos supervisados que ejecuten iOS 9.3 y versiones posteriores.

## <a name="configure-settings"></a>Configurar valores

1. En la hoja **Características del dispositivo**, elija **Notificaciones de aplicación (solo supervisadas)**.
2. En la hoja **Notificaciones de aplicación**, elija **Agregar** y, luego, configure los valores siguientes:
    - **App bundle ID** (Identificador del lote de aplicaciones): escriba el **Identificador del lote de aplicaciones** de la aplicación que quiere configurar. Consulte **Bundle ID reference for built-in iOS apps** (Referencia de identificador de lote para aplicaciones iOS integrada) más adelante en este tema para obtener ayuda.
    - **App name** (Nombre de la aplicación): escriba el nombre de la aplicación que desea configurar. Esto no es muestra en el dispositivo y se usa para ayudarle a identificar la aplicación en la lista.
    - **Publisher** (Publicador): escriba el publicador de la aplicación que desea configurar. Esto no es muestra en el dispositivo y se usa para ayudarle a identificar la aplicación en la lista.
    - **Notifications** (Notificaciones): habilite o deshabilite el envío de notificaciones de la aplicación al dispositivo. Si deshabilita esta configuración, también se deshabilitan las siguientes.
        - **Show in Notification Center** (Mostrar en centro de notificaciones): habilite esta opción para permitir que la aplicación muestre notificaciones en el centro de notificaciones del dispositivo.
        - **Show in Lock Screen** (Mostrar en pantalla de bloqueo): habilite esta opción para ver las notificaciones de la aplicación en la pantalla de bloqueo del dispositivo.
        - **Alert type** (Tipo de alerta): seleccione el tipo de notificación que desea cuando el dispositivo se desbloquea:
            - **None** (Ninguna): no se muestra ninguna notificación.
            - **Banner** (Mensaje emergente): un mensaje emergente que muestra la notificación aparece brevemente.
            - **Modal** (Modal): se muestra la notificación y el usuario debe descartarla manualmente antes de poder continuar usando el dispositivo.
        - **Badge on app icon** (Distintivo en el icono de aplicación): habilite esta opción para agregar un distintivo en el icono de aplicación para indicar que la aplicación envió una notificación.
        - **Sounds** (Sonidos): habilite esta opción para reproducir un sonido cuando se entrega una notificación.
3. Siga agregando las aplicaciones que necesita. Cuando termine, elija **Aceptar**.
4. Elija **Aceptar** hasta que vuelva a la hoja **Crear perfil** y, luego, elija **Crear**. 


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referencia de identificador de lote para aplicaciones iOS integradas

En esta lista se muestra el identificador de lote de algunas aplicaciones iOS comunes integradas. Póngase en contacto con el proveedor de software para encontrar el identificador de lote de otras aplicaciones. 

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
