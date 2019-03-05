---
title: 'Configuración de Windows Hello para empresas en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte una lista de todas las opciones de configuración de PIN, biometría y protección contra suplantación de identidad en un perfil de protección de identidad para usar y configurar Windows Hello para empresas en dispositivos Windows 10 en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5eb4097ab2bedf032270b1d4230d81f7b326fbf1
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228585"
---
# <a name="windows-10-and-newer-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Configuración de dispositivos Windows 10 (y versiones posteriores) para habilitar Windows Hello para empresas en Intune

En este artículo se enumeran y describen las opciones de configuración de Windows Hello para empresas que puede controlar en los dispositivos Windows 10 en Intune. Como parte de su solución de administración de dispositivos móviles (MDM), use estas opciones de configuración para usar un PIN o una huella digital para iniciar sesión y mucho más.

Como administrador de Intune, puede crear y asignar estas opciones de configuración a los dispositivos Windows 10 y versiones posteriores.

Para más información sobre los perfiles de Windows Hello para empresas en Intune, consulte la [configuración de protección de identidad](identity-protection-configure.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello para empresas

- **Configurar Windows Hello para empresas**: para usar esta característica y configurar sus opciones, elija **Habilitar**.
- **Longitud de PIN mínima**: escriba la longitud de PIN mínima que desea permitir en los dispositivos. La longitud de PIN predeterminada es de seis caracteres. La longitud de PIN mínima es de cuatro (4) caracteres.
- **Longitud máxima del PIN**: escriba la longitud máxima de PIN que desea permitir en los dispositivos. La longitud de PIN predeterminada es de seis (6) caracteres. La longitud de PIN máxima es de 127 caracteres.  
- **Letras minúsculas en el PIN**: puede exigir un PIN más seguro solicitando a los usuarios finales que incluyan letras minúsculas. Las opciones son:

  - **No se permite** (opción predeterminada): esta opción impide que los usuarios usen minúsculas en el PIN. Este comportamiento también se produce si el valor de configuración no está configurado.
  - **Permitido**: esta opción permite a los usuarios usar letras minúsculas en el PIN, pero no es necesario.
  - **Requerido**: los usuarios deben incluir al menos una letra minúscula en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.

- **Letras mayúsculas en el PIN**: puede exigir un PIN más seguro solicitando a los usuarios finales que incluyan letras mayúsculas. Las opciones son:

  - **No se permite** (opción predeterminada): esta opción impide que los usuarios usen mayúsculas en el PIN. Este comportamiento también se produce si el valor de configuración no está configurado.
  - **Permitido**: esta opción permite a los usuarios usar letras mayúsculas en el PIN, pero no es necesario.
  - **Requerido**: los usuarios deben incluir al menos una letra mayúscula en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.

- **Caracteres especiales en el PIN**: puede exigir un PIN más seguro solicitando a los usuarios finales que incluyan caracteres especiales. Las opciones son:

  - **No se permite** (opción predeterminada): esta opción impide que los usuarios usen caracteres especiales en el PIN. Este comportamiento también se produce si el valor de configuración no está configurado.
    Entre los caracteres especiales se incluyen los siguientes: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **Permitido**: esta opción permite a los usuarios usar letras mayúsculas en el PIN, pero no es necesario.
  - **Requerido**: los usuarios deben incluir al menos una letra mayúscula en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.

- **Expiración del PIN (días)**: Se recomienda especificar un período de expiración del PIN, transcurrido el cual hay que cambiarlo. El valor predeterminado es 41 días.

- **Recordar historial de PIN**: Restringe la reutilización de los PIN usados anteriormente. De forma predeterminada, no se pueden volver a usar los últimos cinco PIN.  
- **Habilitar la recuperación del PIN**: permite al usuario cambiar el PIN mediante el servicio de recuperación de PIN de Windows Hello para empresas.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **Usar un Módulo de plataforma segura (TPM)**: Un chip de TPM ofrece una capa adicional de seguridad de datos. Elija uno de los siguientes valores:  
  - **Habilitar**: Solo los dispositivos que tengan un TPM accesible pueden aprovisionar Windows Hello para empresas.
  - **No configurado**: Todos los dispositivos pueden aprovisionar Windows Hello para empresas, incluso cuando no hay ningún TPM utilizable. En primer lugar, los dispositivos intentarán usar un TPM, pero si no hay ninguno disponible, los dispositivos pueden usar el cifrado de software.  

- **Permitir autenticación biométrica**: Habilita la autenticación biométrica, como el reconocimiento facial o la huella digital, como alternativa a un PIN para Windows Hello para empresas. Los usuarios todavía deben configurar un PIN de trabajo por si produce un error en la autenticación biométrica. Elija de entre las siguientes opciones:

  - **Habilitar**: Windows Hello para empresas permite la autenticación biométrica.
  - **Sin configurar** (valor predeterminado): Windows Hello para empresas impide la autenticación biométrica (en todos los tipos de cuenta).

- **Usar tecnología mejorada de suplantación de identidad cuando esté disponible**: elija si se usan las características de protección contra la suplantación de identidad de Windows Hello en los dispositivos que las admiten. Por ejemplo, detecte una fotografía de una cara en lugar de un rostro real.

  - **Habilitar**: Windows requiere que, cuando se admita, todos los usuarios usen tecnología contra la suplantación de identidad para las características faciales.  
  - **Sin configurar** (valor predeterminado): Windows respeta las configuraciones de suplantación de identidad en el dispositivo.

- **Certificado para recursos locales**: 

  - **Habilitar**: Permite que Windows Hello para empresas use certificados para autenticarse en los recursos locales.
  - **Sin configurar** (valor predeterminado): Impide que Windows Hello para empresas use certificados para autenticarse en los recursos locales.  

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
