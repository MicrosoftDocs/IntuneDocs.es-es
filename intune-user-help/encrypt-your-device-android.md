---
title: Cifrado de dispositivos Android para Intune | Microsoft Docs
description: Pasos para activar el cifrado de dispositivos Android cuando lo requiere Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2965d6a017d92bd4535a29a2257c0cac5e6deaf
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506367"
---
# <a name="encrypting-your-android-device"></a>Cifrado del dispositivo Android

El cifrado de dispositivos protege los archivos y las carpetas frente al acceso no autorizado si el dispositivo se pierde o se lo roban. Después de activar el cifrado del dispositivo, solo los usuarios con la contraseña o el PIN correctos podrán iniciar sesión en el dispositivo. 

Antes de poder acceder a los recursos de la escuela o del trabajo, es posible que su organización le obligue a cifrar el dispositivo Android. Algunos dispositivos Android más recientes están cifrados de forma predeterminada y listos para su configuración.  

## <a name="turn-on-encryption"></a>Activar el cifrado

Si Portal de empresa o la aplicación Microsoft Intune le pide que cifre el dispositivo, complete los pasos siguientes. 

> [!Note]
> Algunos dispositivos Android de Huawei, vivo y OPPO no se pueden cifrar. Descubra más [aquí](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1. Establecer un bloqueo de pantalla del dispositivo.  
    a. Vaya a **Configuración** > **Pantalla de bloqueo y seguridad** > **Tipo de bloqueo de pantalla**.  
    b. Seleccione **PIN**, **password**o **Pattern**.  
    c. Siga las instrucciones en pantalla para configurar el bloqueo de pantalla.  

2. Vuelva a la **pantalla de bloqueo y seguridad** y seleccione **Inicio seguro**.
3. Elija **requerir PIN cuando el dispositivo se active**  > **Aceptar**.
4. Escriba el PIN para confirmar y cifrar el dispositivo.
5. Abra la aplicación Portal de empresa o Microsoft Intune.
    * Usuarios de Portal de empresa: seleccione el dispositivo y pulse **Comprobar configuración del dispositivo**. 
    * Microsoft Intune usuarios: tendrá que esperar hasta que se actualice la página, pero cuando lo haga, el estado de cifrado debe cambiar a compatible.  

Los dispositivos que ejecutan Android 4,4 y versiones anteriores podrían no tener la opción de **Inicio seguro** . En ese caso, complete los pasos siguientes para cifrar el dispositivo.

1. Vaya a **configuración**  > **seguridad**  > **cifrar el dispositivo**. Las etiquetas en pantalla varían entre dispositivos Android. Si no ve la opción **cifrar dispositivo** , proteja:
    * **Cifrado** de **almacenamiento  >  Storage**
    * **Pantalla de bloqueo de**  >  **de almacenamiento y seguridad**  > **otra configuración de seguridad** 

2. Siga las instrucciones en pantalla. Durante el cifrado, es posible que el dispositivo se reinicie varias veces.
3. Abra la aplicación Portal de empresa o Microsoft Intune.
    * Usuarios de Portal de empresa: seleccione el dispositivo y pulse **Comprobar configuración del dispositivo**.  
    * Microsoft Intune usuarios: tendrá que esperar hasta que se actualice la página, pero cuando lo haga, el estado de cifrado debe cambiar a compatible.

## <a name="troubleshoot"></a>Solución de problemas  
**Problema**: ya cifró el dispositivo y

- El botón de cifrado está deshabilitado.
- Ve un mensaje en el que se indica que aún es necesario realizar el cifrado.
- Obtiene errores al intentar usar la aplicación Portal de empresa o Microsoft Intune.

**Opciones que puede probar**

- Asegúrese de que el dispositivo está cargado y conectado.  
- Asegúrese de que ha establecido un PIN o una contraseña en el dispositivo.  

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa (visite el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para obtener la información de contacto), o escriba al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">equipo de Microsoft Android</a>.  
