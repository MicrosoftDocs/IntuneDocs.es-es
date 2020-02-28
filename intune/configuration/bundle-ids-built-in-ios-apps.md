---
title: 'Identificadores de lote para aplicaciones iOS/iPadOS integradas en Microsoft Intune: Azure | Microsoft Docs'
titleSuffix: ''
description: Vea una lista de los identificadores de lote para las aplicaciones iOS y iPadOS integradas. Use estos identificadores de lote para permitir explícitamente las aplicaciones en perfiles de configuración de dispositivo y directivas en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10c6ea8e3afd7bb1f5a583c0088c72fc155cb0f9
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513306"
---
# <a name="bundle-ids-for-built-in-ios-and-ipados-apps-you-can-use-in-intune"></a>Identificadores de lote para aplicaciones iOS y iPadOS integradas que se pueden usar en Intune

Al configurar características en dispositivos iOS/iPadOS, también puede agregar las aplicaciones integradas en estos mismos dispositivos. En este artículo se enumeran los identificadores de lote de algunas aplicaciones iOS/iPadOS comunes integradas. Póngase en contacto con el proveedor de software para encontrar el identificador de lote de otras aplicaciones. Consulte la lista de [identificadores de lote de iOS/iPadOS](https://support.apple.com/guide/mdm/ios-bundle-ids-mdm90f60c1ce/web) de Apple (se abre el sitio web de Apple).

## <a name="bundle-ids"></a>Identificador de lote

| Identificador de lote                   | Nombre de la aplicación     | Publicador |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | Tienda de aplicaciones    | Apple     |
| com.apple.calculator        | Calculadora   | Apple     |
| com.apple.mobilecal         | Calendario     | Apple     |
| com.apple.camera            | Cámara       | Apple     |
| com.apple.mobiletimer       | Reloj        | Apple     |
| com.apple.clips             | Imágenes        | Apple     |
| com.apple.compass           | Compass      | Apple     |
| com.apple.MobileAddressBook | Contactos     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Archivos        | Apple     |
| com.apple.mobileme.fmf1     | Buscar amigos | Apple     |
| com.apple.mobileme.fmip1    | Buscar mi iPhone  | Apple     |
| com.apple.gamecenter        | Centro de juegos  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Mantenimiento       | Apple     |
| com.apple.Home              | Inicio         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | Asignaciones         | Apple     |
| com.apple.measure           | Medida      | Apple     |
| com.apple.MobileSMS         | Mensajes     | Apple     |
| com.apple.Music             | Música        | Apple     |
| com.apple.news              | Noticias         | Apple     |
| com.apple.mobilenotes       | Notas        | Apple     |
| com.apple.Numbers           | Números      | Apple     |
| com.apple.Pages             | Páginas        | Apple     |
| com.apple.mobilephone       | Teléfono        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Fotos       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Recordatorios    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Configuración     | Apple     |
| com.apple.shortcuts         | Accesos directos    | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Acciones       | Apple     |
| com.apple.tips              | Sugerencias         | Apple     |
| com.apple.tv                | TV           | Apple     |
| com.apple.videos            | Vídeos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Inspección        | Apple     |
| com.apple.weather           | Clima      | Apple     |

## <a name="next-steps"></a>Pasos siguientes

Use estos identificadores de lote para configurar las [características del dispositivo](ios-device-features-settings.md) y [permitir o restringir algunas opciones de configuración](device-restrictions-ios.md) en dispositivos iOS/iPadOS.
