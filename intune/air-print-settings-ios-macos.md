---
title: "Configuración de Intune AirPrint para dispositivos iOS y macOS"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Azure de Intune: aprenda a usar Intune para ayudar a conectar automáticamente dispositivos iOS y macOS a impresoras AirPrint compatibles."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 55486693e2f5678ceeb20dd3a0ef3c52553871d2
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="airprint-settings-for-ios-and-macos-devices"></a>Configuración de AirPrint para dispositivos iOS y macOS

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Use estas opciones para configurar los dispositivos iOS o macOS para conectarse automáticamente a impresoras AirPrint compatibles en la red. Necesitará la ruta de acceso a recursos y la dirección IP de las impresoras para continuar.

## <a name="find-airprint-printer-information"></a>Búsqueda de información sobre impresoras AirPrint

Use este procedimiento para agregar información de AirPrint a la carga de AirPrint para que los usuarios de dispositivos iOS puedan imprimir en impresoras AirPrint conocidas.

1. En un equipo Mac conectado a la misma red local (subred) que las impresoras AirPrint, abra Terminal (en **/Applications/Utilities**)
2. En Terminal, escriba **ippfind** y presiona Entrar.
3. Anote cualquier información relacionada con impresoras que devuelva el comando, por ejemplo: **ipp://myprinter.local.:631/ipp/port1**. La primera parte de la información es el nombre de la impresora y la última parte, la ruta de acceso a recursos.
4. En Terminal, escriba **ping myprinter.local** y, luego, presione Entrar.
5. Anote la información sobre direcciones IP que devuelva el comando, por ejemplo, **PING myprinter.local (10.50.25.21)**.
6. Por último, use la dirección IP y la ruta de acceso a recursos en la configuración de carga de AirPrint. Una dirección IP de ejemplo sería **10.50.25.21** y una ruta de acceso a recursos de ejemplo podría ser **/ipp/port1**.

## <a name="configure-an-airprint-profile"></a>Configuración de un perfil de AirPrint

1. En la hoja **Características del dispositivo**, elija **AirPrint**.
2. Para agregar un destino de AirPrint en la hoja **AirPrint**, escriba su **dirección IP** y su **ruta de acceso a recursos** y, luego, haga clic en **Agregar**.
3. Siga agregando los destinos que necesita. Cuando termine, elija **Aceptar**.

También puede importar una lista de impresoras de un archivo de valores separados por comas (.csv) o exportar la lista.

