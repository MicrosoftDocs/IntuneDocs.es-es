---
title: 'Agregar Endpoint Protection de macOS en Microsoft Intune: Azure | Microsoft Docs'
description: En los dispositivos macOS, use el equipo selector para determinar dónde se pueden instalar las aplicaciones, incluidas las de Mac App Store. Además, habilite o configure un firewall para permitir aplicaciones concretas, bloquear otras, usar el modo sigiloso e incluso bloquear determinados tipos de conexiones entrantes mediante Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d110013c10f0330c0edbbf230c508009fb47b2a6
ms.sourcegitcommit: 11a31cd39b727f2254e2705b07d18924e103bd2e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341320"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Configuración de Endpoint Protection de macOS en Intune  

En este artículo se muestran las opciones de Endpoint Protection que se pueden configurar para los dispositivos con macOS. Estas opciones se configuran mediante un perfil de configuración de dispositivo macOS para [Endpoint Protection](endpoint-protection-configure.md) en Intune.  

## <a name="gatekeeper"></a>Equipo selector  

- **Permitir aplicaciones descargadas desde estas ubicaciones**  
  Limitar las aplicaciones que puede iniciar un dispositivo, en función de dónde se hayan descargado las aplicaciones. El fin es proteger los dispositivos frente al malware y permitir únicamente aplicaciones de orígenes de confianza.  

  - **No configurado**.  
  - **Mac App Store**  
  - **Mac App Store y desarrolladores identificados**  
  - **Cualquier ubicación**  

  **Valor predeterminado**: No configurado  

- **El usuario puede invalidar el equipo selector**  
  Impide que los usuarios invaliden el valor del equipo selector y que presionen Control+clic para instalar una aplicación. Si está habilitado, los usuarios pueden presionar Control+clic en cualquier aplicación e instalarla.  
 
  - **No configurado** : los usuarios pueden hacer clic en el control para instalar aplicaciones.  
  - **Bloquear** : impide que los usuarios usen el control-haga clic para instalar aplicaciones.  

  **Valor predeterminado**: No configurado  

## <a name="firewall"></a>Firewall  

Use el firewall para controlar conexiones por aplicación en lugar de por puerto. La configuración por aplicación permite aprovechar las ventajas de la protección del firewall con más facilidad. También ayuda a evitar que aplicaciones no deseadas tomen el control de los puertos de red que están abiertos para las aplicaciones legítimas.  

**General**
- **Firewall**  
  Habilite el firewall para configurar la administración de las conexiones entrantes en el entorno.  
  - **No configurado**.  
  - **Habilitar**  

  **Valor predeterminado**: No configurado  

- **Conexiones entrantes**  
  Bloquee todas las conexiones entrantes excepto las necesarias para los servicios básicos de Internet, como DHCP, Bonjour e IPSec. Esta característica también bloquea todos los servicios de uso compartido, como Uso compartido de archivos y Pantalla compartida. Si usa servicios de uso compartido, mantenga este valor como *No configurado*.  
  - **No configurado**.  
  - **Bloquear**  

  **Valor predeterminado**: No configurado  

**Permita o bloquee conexiones entrantes de aplicaciones concretas.**  

  - **Aplicaciones permitidas**  
    Seleccione las aplicaciones a las que de forma explícita se permite recibir conexiones entrantes.  

  - **Aplicaciones bloqueadas**  
    Seleccione las aplicaciones que deben bloquear conexiones entrantes.  

  - **Modo sigiloso**  
    Habilite el modo sigiloso para impedir que el equipo responda a solicitudes de sondeo. El dispositivo sigue respondiendo a las solicitudes entrantes de las aplicaciones autorizadas. Las solicitudes inesperadas, como ICMP (ping), se ignoran.  
    - **No configurado**.  
    - **Habilitar**  

    **Valor predeterminado**: No configurado  

## <a name="filevault"></a>FileVault  
Para obtener más información sobre la configuración de FileVault de Apple, consulte [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) en el contenido para desarrolladores de Apple. 

- **FileVault**  
  Puede *Habilitar* el cifrado de disco completo mediante XTS-AES 128 con FileVault en los dispositivos que ejecutan MacOS 10,13 y versiones posteriores.  
  - **No configurado**.  
  - **Habilitar**  

  **Valor predeterminado**: No configurado  

  - **Tipo de clave de recuperación**  
    Se crean claves de recuperación de *clave personal* para dispositivos. Configure las siguientes opciones para la clave personal.  

     - **Ubicación de la clave de recuperación personal** : especifique un mensaje breve para el usuario que explica cómo puede recuperar su clave de recuperación personal. Este texto se inserta en el mensaje que el usuario ve al habilitar FileVault.  
      
     - **Rotación de claves de recuperación personal** : especifique la frecuencia con la que se girará la clave de recuperación personal de un dispositivo. Puede seleccionar el valor predeterminado de **no configurado**, o un valor de **1** a **12** meses.  

  - **Diferir FileVault hasta cerrar sesión** 
    > [!NOTE]
    > La compatibilidad con FileVault está limitada hasta que la versión de julio complete el lanzamiento en unos días. Hasta que se complete la implementación, si configura FileVault, debe establecer *defer FileVault hasta* que se cierre la sesión en **Habilitar**.   

    FileVault no se habilitará hasta que el usuario cierra la sesión. Se le pedirá a un usuario local o a una cuenta móvil que habilite FileVault al cerrar sesión o el siguiente inicio de sesión.  
    - **No configurado**.  
    - **Habilitar**  
    
    **Valor predeterminado**: No configurado  



    - **Deshabilitar preguntar al cerrar sesión**  
      Evite el aviso al usuario que le solicita que habilite FileVault cuando cierre la sesión.  
      - **No configurado**.  
      - **Habilitar**  

      **Valor predeterminado**: No configurado  

    - **Número de veces que se permite omitir**  
      Establezca el número de veces que un usuario puede omitir las solicitudes para habilitar FileVault antes de que FileVault sea necesario para que el usuario inicie sesión.  

      - **No configurado** : el cifrado en el dispositivo es necesario antes de que se permita el siguiente inicio de sesión.  
      -  de **1** a **10** : permite que un usuario ignore el aviso de 1 a 10 veces antes de requerir el cifrado en el dispositivo.  
      - **Sin límite, preguntar siempre** : se solicita al usuario que habilite FileVault pero el cifrado nunca es necesario.  
 
      **Valor predeterminado**: No configurado  


