---
title: Cifre el dispositivo Android de Intune | Microsoft Docs
description: Pasos para activar cifrado de dispositivo Android cuando sea necesario mediante Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfc17c60412a1cfe90693216caa69ada3d2d2c9a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545258"
---
# <a name="encrypting-your-android-device"></a>Cifrado del dispositivo Android

Cifrado de dispositivo protege los archivos y carpetas frente al acceso no autorizado si el dispositivo se pierde o lo roban. Después de activar el cifrado de dispositivo, solo los usuarios con la contraseña correcta o el pin podrán iniciar sesión en su dispositivo. 

Antes de que puede tener acceso a los recursos de trabajo o educativos, su organización puede requerir que se cifre el dispositivo Android. Algunos dispositivos Android más reciente se cifran de forma predeterminada, del cuadro.  

## <a name="turn-on-encryption"></a>Activar el cifrado

Si el Portal de empresa o la aplicación de Microsoft Intune le pide que cifre el dispositivo, complete los pasos siguientes. 

> [!Note]
> No se puede cifrar ciertos dispositivos Android desde Huawei Vivo y OPPO. Descubra más [aquí](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1. Establecer un bloqueo de pantalla del dispositivo.  
    a. Vaya a **Configuración** > **Pantalla de bloqueo y seguridad** > **Tipo de bloqueo de pantalla**.  
    b. Seleccione **PIN**, **contraseña**, o **patrón**.  
    c. Siga las instrucciones en pantalla para configurar el bloqueo de pantalla.  

2. Vuelva a **pantalla de bloqueo y seguridad** y seleccione **inicio seguro**.
3. Elija **solicitar PIN al dispositivo se enciende** > **Aceptar**.
4. Escriba su PIN para confirmar y cifrado del dispositivo.
5. Abra la aplicación de portal de empresa de Microsoft Intune.
    * Usuarios de Portal de empresa: seleccione el dispositivo y pulse **Comprobar configuración del dispositivo**. 
    * Los usuarios de Microsoft Intune: tendrá que esperar hasta que la página se actualiza, pero cuando lo hace, su estado de cifrado debe cambiar a compatible.  

Dispositivos que ejecutan Android 4.4 y versiones anteriores podrían no tener el **inicio seguro** opción. En ese caso, complete los pasos siguientes para cifrar el dispositivo.

1. Vaya a **configuración** > **seguridad** > **cifrar dispositivo**. Etiquetas en la pantalla pueden variar entre los dispositivos Android. Si no ve el **cifrar dispositivo** opción, la protección:
    * **Almacenamiento** > **cifrado de almacenamiento**
    * **Almacenamiento** > **pantalla de bloqueo y seguridad** > **otras configuraciones de seguridad** 

2. Siga las instrucciones en pantalla. Durante el cifrado, es posible que el dispositivo se reinicie varias veces.
3. Abra la aplicación de portal de empresa de Microsoft Intune.
    * Usuarios de Portal de empresa: seleccione el dispositivo y pulse **Comprobar configuración del dispositivo**.  
    * Los usuarios de Microsoft Intune: tendrá que esperar hasta que la página se actualiza, pero cuando lo hace, su estado de cifrado debe cambiar a compatible.

## <a name="troubleshoot"></a>Solución de problemas  
**Problema**: el dispositivo ya se ha cifrado y

- El botón de cifrado está deshabilitado.
- Ve un mensaje en el que se indica que aún es necesario realizar el cifrado.
- Obtiene errores al intentar usar la aplicación de Portal de empresa o Microsoft Intune.

**Opciones que puede probar**

- Asegúrese de que el dispositivo está cargado y conectado.  
- Asegúrese de que ha establecido un PIN o una contraseña en el dispositivo.  

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa (visite el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para obtener la información de contacto), o escriba al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">equipo de Microsoft Android</a>.  
