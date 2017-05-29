---
title: "Cómo usar Windows Hello para empresas"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a crear una directiva para controlar el uso de Windows Hello para empresas en dispositivos administrados."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 541be8b8-8668-41be-afce-3f3e08c12191
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4d375a40283a5f3c1e9b7302d659739d4ca3d508
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="use-windows-hello-for-business"></a>Uso de Windows Hello para empresas


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Microsoft Intune se integra en Windows Hello para empresas (anteriormente denominado Microsoft Passport for Work), un método alternativo de inicio de sesión que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual.

Hello para empresas permite usar un *gesto de usuario* para iniciar sesión en lugar de una contraseña. Un gesto de usuario podría ser una autenticación biométrica de PIN simple, como Windows Hello, o un dispositivo externo como un lector de huellas digitales.

Intune se integra con Hello para empresas de dos maneras:

-   Puede usar una directiva de Intune para controlar los gestos que se pueden y no se pueden usar para iniciar sesión.

<!--- -   You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> En las versiones de escritorio y móvil de Windows 10 anteriores a la Actualización de aniversario, era posible establecer dos PIN diferentes para autenticarse en los recursos:
- El **PIN de dispositivo** se usaba para desbloquear el dispositivo y conectarse a recursos de nube.
- El **PIN de trabajo** se usaba para acceder a recursos de Azure AD en los dispositivos personales del usuario (BYOD).

>En la Actualización de aniversario, estos dos PIN se combinaron en un solo PIN de dispositivo.
Las directivas de configuración de Intune que establezca para controlar el PIN de dispositivo y las directivas de Windows Hello para empresas que configure serán las que establecerán ahora este nuevo valor de PIN.
Si ha establecido que ambos tipos de directivas controlarán el PIN, la directiva de Windows Hello para empresas se aplicará en dispositivos de escritorio y móviles de Windows 10.
Para garantizar que se resuelven los conflictos de directivas y que la directiva de PIN se aplica correctamente, actualice su directiva de Windows Hello para empresas de modo que coincida con la configuración de la directiva de configuración y pídales a los usuarios que sincronicen sus dispositivos en la aplicación del portal de empresa.



## <a name="create-a-windows-hello-for-business-policy"></a>Crear una directiva de Windows Hello para empresas

1.  En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2.  En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Administrar** > **Windows Hello para empresas**.

3.  En la hoja que se abre, elija la configuración **predeterminada**.

4.  En la hoja **All Users** (Todos los usuarios), haga clic en **Propiedades** y luego escriba un **nombre** y una **descripción** opcional para la configuración de Windows Hello para empresas.

5. En la hoja **All Users** (Todos los usuarios), haga clic en **Configuración** y luego elija entre las siguientes opciones para **configurar Windows Hello para empresas**:

    - **Deshabilitado**. Si no quiere usar Windows Hello para empresas, seleccione esta opción. De esta manera, todas las demás configuraciones en pantalla se deshabilitan.
    - **Habilitado**. Seleccione esta opción si quiere configurar Windows Hello para empresas.
    - **No configurado**. Seleccione esta opción si no quiere usar Intune para controlar la configuración de Windows Hello para empresas. No se cambiará ninguna de las opciones de configuración de Windows Hello para empresas en los dispositivos Windows 10. Todas las demás configuraciones de la hoja no están disponibles.

6.  Si ha seleccionado **Habilitado** en el paso anterior, configure las opciones necesarias que se aplicarán a todos los dispositivos Windows 10 y Windows 10 Mobile inscritos.

 - **Usar un Módulo de plataforma segura (TPM)**. Un chip de TPM ofrece una capa adicional de seguridad de datos.<br>Elija uno de los siguientes valores:

     - **Requerido** (valor predeterminado). Solo los dispositivos que tengan un TPM accesible pueden aprovisionar Windows Hello para empresas.
     - **Preferido**. Los dispositivos intentan primero usar un TPM. Si no está disponible, pueden usar el cifrado de software.

 - **Requerir longitud mínima de PIN**/**Requerir longitud máxima de PIN**. Configura los dispositivos para que usen las longitudes de PIN mínima y máxima que se especifiquen, lo cual garantiza un inicio de sesión seguro. La longitud de PIN predeterminada es de 6 caracteres, pero se puede aplicar una longitud mínima de 4 caracteres. La longitud de PIN máxima es de 127 caracteres.

 - **Requerir minúsculas en el PIN**/**Requerir mayúsculas en el PIN**/**Requerir caracteres especiales en el PIN**. Si quiere aplicar un PIN más seguro, puede requerir el uso de letras mayúsculas, letras minúsculas y caracteres especiales en el PIN. Elija de entre las siguientes opciones:

     - **Permitido**. Los usuarios pueden usar el tipo de carácter en el PIN, pero no es obligatorio.
    
     - **Requerido**. Los usuarios deben incluir al menos uno de los tipos de carácter en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.

     - **No permitido** (valor predeterminado). Los usuarios no deben usar estos tipos de caracteres en el PIN. (Este es también el comportamiento si no se configura esta opción).<br>Entre los caracteres especiales se incluyen los siguientes: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

 - **Expiración del PIN (días)**. Se recomienda especificar un período de expiración del PIN, transcurrido el cual hay que cambiarlo. El valor predeterminado es 41 días.

 - **Recordar historial de PIN**. Restringe la reutilización de los PIN usados anteriormente. De forma predeterminada, no se pueden volver a usar los últimos cinco PIN.

 - **Permitir autenticación biométrica**. Habilita la autenticación biométrica, como el reconocimiento facial o la huella digital, como alternativa a un PIN para Windows Hello para empresas. Los usuarios todavía deben configurar un PIN de trabajo por si produce un error en la autenticación biométrica. Elija de entre las siguientes opciones:

     - **Sí**. Windows Hello para empresas permite la autenticación biométrica.
     - **No**. Windows Hello para empresas impide la autenticación biométrica (en todos los tipos de cuenta).

 - **Usar tecnología mejorada contra la suplantación de identidad, cuando esté disponible**. Establece si se van a usar las características contra la suplantación de identidad de Windows Hello en los dispositivos que lo permitan (por ejemplo, cuando se detecte una fotografía de un rostro en lugar de un rostro real).<br>Si esta opción se establece en **Sí**, Windows requiere que todos los usuarios usen tecnología contra la suplantación de identidad para características faciales cuando se admitan.

 - **Usar inicio de sesión por teléfono**. Si esta opción se establece en **Sí**, los usuarios pueden usar una cuenta de Passport remota para que actúe como dispositivo complementario portátil para la autenticación del equipo de escritorio. El equipo de escritorio debe estar unido a Azure Active Directory y el dispositivo complementario debe configurarse con un PIN de Windows Hello para empresas.


## <a name="further-information"></a>Más información
Para obtener más información sobre Microsoft Passport, vea [la guía](https://technet.microsoft.com/library/mt589441.aspx) en la documentación de Windows 10.

