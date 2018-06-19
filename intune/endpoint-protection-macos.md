---
title: 'Agregar Endpoint Protection de macOS en Microsoft Intune: Azure | Microsoft Docs'
description: En los dispositivos macOS, use el equipo selector para determinar dónde se pueden instalar las aplicaciones, incluidas las de Mac App Store. Además, habilite o configure un firewall para permitir aplicaciones concretas, bloquear otras, usar el modo sigiloso e incluso bloquear determinados tipos de conexiones entrantes mediante Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 49194d49658042802cbc1148276445008ee1b09f
ms.sourcegitcommit: c3ae3c3dc46b62d9191813d25a196874ba4927be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
ms.locfileid: "30254560"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Configuración de Endpoint Protection de macOS en Intune

En este artículo se muestran las opciones de Endpoint Protection que se pueden configurar para los dispositivos con macOS. Estas opciones incluyen la configuración de equipo selector y firewall en estos dispositivos y pueden definirse con un perfil de dispositivo en Microsoft Intune.

## <a name="gatekeeper"></a>Equipo selector

- **Allow apps downloaded from these locations** (Permitir aplicaciones descargadas desde estas ubicaciones): limita aplicaciones en función de desde dónde se descarguen. El fin es proteger los dispositivos frente al malware y permitir únicamente aplicaciones de orígenes de confianza. Opciones para permitir: 
  - **Mac App Store**
  - **Mac App Store y desarrolladores identificados**
  - **Cualquier ubicación**

- **User can override Gatekeeper** (El usuario puede invalidar el equipo selector): evita que los usuarios invaliden el valor del equipo selector y que presionen Control+clic para instalar una aplicación. Si está habilitado, los usuarios pueden presionar Control+clic en cualquier aplicación e instalarla.

## <a name="firewall"></a>Firewall

Use el firewall para controlar conexiones por aplicación en lugar de por puerto. La configuración por aplicación permite aprovechar las ventajas de la protección del firewall con más facilidad. También ayuda a evitar que aplicaciones no deseadas tomen el control de los puertos de red que están abiertos para las aplicaciones legítimas.

- **Use el firewall para proteger a los dispositivos frente al acceso de red no autorizado mediante el control de las conexiones por aplicación.**
  - **Firewall**: habilite el firewall para configurar la administración de las conexiones entrantes en el entorno.
  - **Conexiones entrantes**: bloquee todas las conexiones entrantes excepto las necesarias para los servicios básicos de Internet, como DHCP, Bonjour e IPSec. Esta característica también bloquea todos los servicios de uso compartido, como Uso compartido de archivos y Pantalla compartida. Si usa servicios de uso compartido, mantenga este valor como **No configurado**.

- **Permita o bloquee conexiones entrantes de aplicaciones concretas.**
  - **Aplicaciones permitidas**: seleccione las aplicaciones a las que de forma explícita se permite recibir conexiones entrantes.
  - **Aplicaciones bloqueadas**: seleccione las aplicaciones que deben bloquear conexiones entrantes.
  - **Modo sigiloso**: habilite el modo sigiloso para evitar que el equipo responda a solicitudes de sondeo. El dispositivo sigue respondiendo a las solicitudes entrantes de las aplicaciones autorizadas. Las solicitudes inesperadas, como ICMP (ping), se ignoran.
