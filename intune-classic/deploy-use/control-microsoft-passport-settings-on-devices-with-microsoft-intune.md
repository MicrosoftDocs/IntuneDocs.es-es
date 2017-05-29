---
title: "Controlar la configuración de Windows Hello para empresas en dispositivos | Microsoft Docs"
description: "Obtenga información sobre cómo se integra Intune en Windows Hello para empresas, un método alternativo de inicio de sesión que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 09/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 9a223f7fb1fd0736541da0d6a15ad5285241577a
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="control-windows-hello-for-business-settings-on-devices-with-microsoft-intune"></a>Controlar la configuración de Windows Hello para empresas en dispositivos que tienen Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune se integra en Windows Hello para empresas (anteriormente denominado Microsoft Passport for Work), un método alternativo de inicio de sesión que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual.

Hello para empresas permite usar un *gesto de usuario* para iniciar sesión en lugar de una contraseña. Un gesto de usuario podría ser una autenticación biométrica de PIN simple, como Windows Hello, o un dispositivo externo como un lector de huellas digitales.

Intune se integra con Hello para empresas de dos maneras:

-   Puede usar una directiva de Intune para controlar los gestos que se pueden y no se pueden usar para iniciar sesión.

-   Puede almacenar certificados de autenticación en el proveedor de almacenamiento de claves (KSP) de Windows Hello para empresas. Para obtener más información, consulte [Secure resource access with certificate profiles in Microsoft Intune (Proteger el acceso a los recursos con perfiles de certificado en Microsoft Intune)](secure-resource-access-with-certificate-profiles.md).

> [!IMPORTANT]
> En las versiones de escritorio y móvil de Windows 10 anteriores a la Actualización de aniversario, era posible establecer dos PIN diferentes para autenticarse en los recursos:
- El **PIN de dispositivo** se usaba para desbloquear el dispositivo y conectarse a recursos de nube.
- El **PIN de trabajo** se usaba para acceder a recursos de Azure AD en los dispositivos personales del usuario (BYOD).

>En la Actualización de aniversario, estos dos PIN se combinaron en un solo PIN de dispositivo.
Las directivas de configuración de Intune que establezca para controlar el PIN de dispositivo y las directivas de Windows Hello para empresas que configure serán las que establecerán ahora este nuevo valor de PIN.
Si ha establecido que ambos tipos de directivas controlarán el PIN, la directiva de Windows Hello para empresas se aplicará en dispositivos de escritorio y móviles de Windows 10.
Para garantizar que se resuelven los conflictos de directivas y que la directiva de PIN se aplica correctamente, actualice su directiva de Windows Hello para empresas de modo que coincida con la configuración de la directiva de configuración y pídales a los usuarios que sincronicen sus dispositivos en la aplicación del portal de empresa.



## <a name="create-a-windows-hello-for-business-policy"></a>Crear una directiva de Windows Hello para empresas

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows** &gt; **Windows Hello para empresas** para abrir la página de Windows Hello para empresas.

    ![Página de Windows Hello para empresas](../media/passport.png)

2.  Elija una de las siguientes opciones:
    - **Deshabilitar Windows Hello para empresas en los dispositivos inscritos**. Si no quiere usar Windows Hello para empresas, seleccione esta opción. De esta manera, todas las demás configuraciones en pantalla se deshabilitan.
    - **Habilitar Windows Hello para empresas en los dispositivos inscritos**. Seleccione esta opción si quiere configurar Windows Hello para empresas.
    - **No configurado**. Seleccione esta opción si no quiere usar Intune para controlar la configuración de Windows Hello para empresas. No se cambiará ninguna de las opciones de configuración de Windows Hello para empresas en los dispositivos Windows 10. Todas las demás configuraciones en pantalla se deshabilitan.
3.  Si ha seleccionado **Habilitar Windows Hello para empresas en los dispositivos inscritos**, configure las opciones necesarias que se deben aplicar a todos los dispositivos Windows 10 y Windows 10 Mobile inscritos.
4.  Cuando termine, elija **Guardar**.


## <a name="settings-for-the-windows-hello-for-business-policy"></a>Configuración de la directiva de Windows Hello para empresas

- **Usar un Módulo de plataforma segura (TPM)**. Un chip de TPM ofrece una capa adicional de seguridad de datos.<br>Elija uno de los siguientes valores:
    - **Requerido** (valor predeterminado). Solo los dispositivos que tengan un TPM accesible pueden aprovisionar Windows Hello para empresas.
    - **Preferido**. Los dispositivos intentan primero usar un TPM. Si no está disponible, pueden usar el cifrado de software.
- **Requerir longitud mínima de PIN**/**Requerir longitud máxima de PIN**. Configura los dispositivos para que usen las longitudes de PIN mínima y máxima que se especifiquen, lo cual garantiza un inicio de sesión seguro. La longitud de PIN predeterminada es de 6 caracteres, pero se puede aplicar una longitud mínima de 4 caracteres. La longitud de PIN máxima es de 127 caracteres.
- **Requerir minúsculas en el PIN**/**Requerir mayúsculas en el PIN**/**Requerir caracteres especiales en el PIN**. Si quiere aplicar un PIN más seguro, puede requerir el uso de letras mayúsculas, letras minúsculas y caracteres especiales en el PIN. Elija de entre las siguientes opciones:
    - **Permitido**. Los usuarios pueden usar el tipo de carácter en el PIN, pero no es obligatorio.
    - **Requerido**. Los usuarios deben incluir al menos uno de los tipos de carácter en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.
    - **No permitido** (valor predeterminado). Los usuarios no deben usar estos tipos de caracteres en el PIN. (Este es también el comportamiento si no se configura esta opción).<br>Entre los caracteres especiales se incluyen los siguientes: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **Expiración del PIN (días)**. Se recomienda especificar un período de expiración del PIN, transcurrido el cual hay que cambiarlo. El valor predeterminado es 41 días.
- **Recordar historial de PIN**. Restringe la reutilización de los PIN usados anteriormente. De forma predeterminada, no se pueden volver a usar los últimos cinco PIN.
- **Permitir autenticación biométrica**. Habilita la autenticación biométrica, como el reconocimiento facial o la huella digital, como alternativa a un PIN para Windows Hello para empresas. Los usuarios todavía deben configurar un PIN de trabajo por si produce un error en la autenticación biométrica. Elija de entre las siguientes opciones:
    - **Sí**. Windows Hello para empresas permite la autenticación biométrica.
    - **No**. Windows Hello para empresas impide la autenticación biométrica (en todos los tipos de cuenta).
- **Usar tecnología mejorada contra la suplantación de identidad, cuando esté disponible**. Establece si se van a usar las características contra la suplantación de identidad de Windows Hello en los dispositivos que lo permitan (por ejemplo, cuando se detecte una fotografía de un rostro en lugar de un rostro real).<br>Si esta opción se establece en **Sí**, Windows requiere que todos los usuarios usen tecnología contra la suplantación de identidad para características faciales cuando se admitan.
- **Usar inicio de sesión por teléfono**. Si esta opción se establece en **Sí**, los usuarios pueden usar una cuenta de Passport remota para que actúe como dispositivo complementario portátil para la autenticación del equipo de escritorio. El equipo de escritorio debe estar unido a Azure Active Directory y el dispositivo complementario debe configurarse con un PIN de Windows Hello para empresas.

## <a name="further-information"></a>Más información
Para obtener más información sobre Microsoft Passport, vea [la guía](https://technet.microsoft.com/library/mt589441.aspx) en la documentación de Windows 10.

