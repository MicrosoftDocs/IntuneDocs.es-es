---
title: 'Configuración de características de dispositivos macOS en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte todas las opciones para configurar los dispositivos macOS para AirPrint en Microsoft Intune. Consulte también los pasos para obtener la dirección IP, la ruta de acceso y la configuración de puertos de un servidor de AirPrint en la red. Use esta configuración en un perfil de configuración de dispositivo para configurar dispositivos macOS para usar servidores de AirPrint en la red.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db89dd2cce679597533d2861a43a7a2fd82abd14
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850580"
---
# <a name="macos-device-feature-settings-in-intune"></a>Configuración de características de dispositivos macOS en Intune

Intune incluye algunas opciones de configuración integradas para permitir a los usuarios de macOS imprimir en impresoras AirPrint en la red. En este artículo se enumeran estas opciones de configuración y se describe lo que hace cada una de ellas. También muestra los pasos para obtener la dirección IP, la ruta de acceso y el puerto de las impresoras AirPrint mediante la aplicación Terminal (emulador).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo macOS](device-features-configure.md).

## <a name="airprint-settings"></a>Configuración de AirPrint

1. En **Configuración**, seleccione **AirPrint**. Especifique las siguientes propiedades del servidor AirPrint:

    - **Dirección IP**: escriba la dirección IPv4 o IPv6 de la impresora. Si usa nombres de host para identificar las impresoras, puede obtener la dirección IP haciendo ping a la impresora en la aplicación Terminal. En la sección [Obtención de la dirección IP y la ruta de acceso](#get-the-ip-address-and-path) (en este artículo) se proporcionan más detalles.
    - **Ruta de acceso**: escriba la ruta de acceso de la impresora. La ruta de acceso suele ser `ipp/print` para las impresoras de la red. En la sección [Obtención de la dirección IP y la ruta de acceso](#get-the-ip-address-and-path) (en este artículo) se proporcionan más detalles.
    - **Puerto**: escriba el puerto de escucha del destino de AirPrint. Si se deja esta propiedad en blanco, AirPrint usa el puerto predeterminado. Disponible en iOS 11.0 y versiones posteriores.
    - **TLS**: elija **Habilitar** para proteger las conexiones AirPrint con Seguridad de la capa de transporte (TLS). Disponible en iOS 11.0 y versiones posteriores.

2. Seleccione **Agregar**. El servidor AirPrint se agrega a la lista. Puede agregar varios servidores AirPrint.

    También puede **importar** un archivo separado por comas (.csv) que incluya una lista de impresoras AirPrint. Además, después de agregar impresoras AirPrint en Intune, puede **Exportar** esta lista.

3. Cuando termine, seleccione **Aceptar** para guardar la lista.

## <a name="get-the-ip-address-and-path"></a>Obtención de la dirección IP y la ruta de acceso

Para agregar servidores AirPrinter, necesita la dirección IP de la impresora, la ruta de acceso de recursos y el puerto. Los pasos siguientes muestran cómo obtener esta información.

1. En un equipo Mac conectado a la misma red local (subred) que las impresoras AirPrint, abra **Terminal** (en **/Aplicaciones/Utilidades**).
2. En la aplicación Terminal, escriba `ippfind` y seleccione Entrar.

    Anote la información de la impresora. Por ejemplo, puede devolver algo parecido a `ipp://myprinter.local.:631/ipp/port1`. La primera parte es el nombre de la impresora. La última parte (`ipp/port1`) es la ruta de acceso del recurso.

3. En Terminal, escriba `ping myprinter.local` y seleccione Entrar.

   Anote la dirección IP. Por ejemplo, puede devolver algo parecido a `PING myprinter.local (10.50.25.21)`.

4. Use los valores de dirección IP y de ruta de acceso del recurso. En este ejemplo, la dirección IP es `10.50.25.21` y la ruta de acceso del recurso es `/ipp/port1`.

## <a name="next-steps"></a>Pasos siguientes

- Vea toda la configuración para dispositivos [iOS](ios-device-features-settings.md).
- Asigne este perfil a grupos; consulte la [asignación de perfiles de dispositivo](device-profile-assign.md).
