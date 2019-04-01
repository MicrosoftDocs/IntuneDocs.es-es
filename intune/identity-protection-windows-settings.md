---
title: 'Configuración de Windows Hello para empresas en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte una lista de todas las opciones de configuración de PIN, biometría y protección contra suplantación de identidad en un perfil de protección de identidad para usar y configurar Windows Hello para empresas en dispositivos Windows 10 en Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 308a730737612f39863160952409ab92670f9153
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069374"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Configuración de dispositivos Windows 10 para habilitar Windows Hello para empresas en Intune

En este artículo se enumeran y describen las opciones de configuración de Windows Hello para empresas que puede controlar en los dispositivos Windows 10 en Intune. Como administrador de Intune, puede configurar y asignar a esta configuración para dispositivos Windows 10 como parte de la solución de administración (MDM) de dispositivos móviles. 

Puede encontrar información adicional acerca de estos valores en [configurar Windows Hello para la configuración de directiva empresarial](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings), en la documentación de WIndows Hello.


Para más información sobre los perfiles de Windows Hello para empresas en Intune, consulte la [configuración de protección de identidad](identity-protection-configure.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello para empresas

- **Configurar Windows Hello para empresas**: para usar esta característica y configurar sus opciones, elija **habilitar**.
- **Longitud de PIN mínima**: escriba la longitud de PIN mínima que quiere permitir en los dispositivos. La longitud de PIN predeterminada es de seis caracteres. La longitud de PIN mínima es de cuatro (4) caracteres.
- **Longitud máxima del PIN**: escriba la longitud de PIN máxima que quiere permitir en los dispositivos. La longitud de PIN predeterminada es de seis (6) caracteres. La longitud de PIN máxima es de 127 caracteres.  
- **Letras minúsculas en el PIN**: puede exigir un PIN más seguro si solicita a los usuarios finales que incluyan letras minúsculas. Las opciones son:

  - **No se permiten** (valor predeterminado): impedir que los usuarios usen minúsculas en el PIN. Este comportamiento también se produce si el valor de configuración no está configurado.
  - **Permitido**: esta opción permite a los usuarios usar letras minúsculas en el PIN, pero no es obligatorio.
  - **Requerido**: los usuarios deben incluir al menos una letra minúscula en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.

- **Letras mayúsculas en el PIN**: puede exigir un PIN más seguro si solicita a los usuarios finales que incluyan letras mayúsculas. Las opciones son:

  - **No se permiten** (valor predeterminado): impedir que los usuarios usen mayúsculas en el PIN. Este comportamiento también se produce si el valor de configuración no está configurado.
  - **Permitido**: esta opción permite a los usuarios utilizar letras mayúsculas en el PIN, pero no es obligatorio.
  - **Requerido**: los usuarios deben incluir al menos una letra mayúscula en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.

- **Caracteres especiales en el PIN**: puede exigir un PIN más seguro si solicita a los usuarios finales que incluyan caracteres especiales. Las opciones son:

  - **No se permiten** (valor predeterminado): impedir que los usuarios usar caracteres especiales en el PIN. Este comportamiento también se produce si el valor de configuración no está configurado.
    Entre los caracteres especiales se incluyen los siguientes: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **Permitido**: esta opción permite a los usuarios utilizar letras mayúsculas en el PIN, pero no es obligatorio.
  - **Requerido**: los usuarios deben incluir al menos una letra mayúscula en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.

- **Expiración de PIN (días):** un procedimiento recomendado consiste en especificar un período de caducidad para un PIN, transcurrido el cual los usuarios tendrán que cambiarlo. El valor predeterminado es 41 días.

- **Recordar historial de PIN**: restringe la reutilización de los PIN usados anteriormente. De forma predeterminada, no se pueden volver a usar los últimos cinco PIN.  
- **Habilitar la recuperación del PIN**: permite al usuario cambiar el PIN mediante el servicio de recuperación de PIN de Windows Hello para empresas.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **Usar un Módulo de plataforma segura (TPM)**: un chip de TPM ofrece una capa adicional de seguridad de datos. Elija uno de los siguientes valores:  
  - **Habilitar**: solo los dispositivos con un TPM accesible pueden aprovisionar Windows Hello para empresas.
  - **No configurado**: todos los dispositivos pueden aprovisionar Windows Hello para empresas, incluso cuando no hay ningún TPM utilizable. En primer lugar, los dispositivos intentarán usar un TPM, pero si no hay ninguno disponible, los dispositivos pueden usar el cifrado de software.  

- **Permitir autenticación biométrica**: habilita la autenticación biométrica (como el reconocimiento facial o la huella digital) como alternativa a un PIN para Windows Hello para empresas. Los usuarios todavía deben configurar un PIN de trabajo por si produce un error en la autenticación biométrica. Elija de entre las siguientes opciones:

  - **Habilitar**: Windows Hello para empresas permite la autenticación biométrica.
  - **No configurado** (valor predeterminado): Windows Hello para empresas impide la autenticación biométrica (para todos los tipos de cuenta).

- **Usar anti-spoofing mejorado, cuando esté disponible**: elija si la suplantación se usan características de Windows Hello en los dispositivos que lo admiten. Por ejemplo, detecte una fotografía de una cara en lugar de un rostro real.

  - **Habilitar**: Windows requiere que, cuando se admita, todos los usuarios utilicen tecnología contra la suplantación de identidad para las características faciales.  
  - **No configurado** (valor predeterminado): Windows respeta las configuraciones de la suplantación en el dispositivo.

- **Certificado para recursos locales**: 

  - **Habilitar**: permite que Windows Hello para empresas use certificados para autenticarse en los recursos locales.
  - **No configurado** (valor predeterminado): impide que Windows Hello para empresas use certificados para autenticarse en los recursos locales. En su lugar, los dispositivos usar el comportamiento predeterminado de *autenticación de clave de confianza local*. Para obtener más información, consulte [certificado de usuario para la autenticación local](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) en la documentación de Windows Hello.  
## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
