---
title: "Controlar la configuración de Microsoft Passport en dispositivos | Microsoft Intune"
description: "Obtenga información sobre cómo se integra Intune en Microsoft Passport for Work, un método alternativo de inicio de sesión que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 822264b7af87c0241e1d345544b8e9892f9e8c51
ms.openlocfilehash: c05929f3c4032bf8e252f4b2087b23dfdecf846b


---

# Controlar la configuración de Microsoft Passport en dispositivos mediante Microsoft Intune
Microsoft Intune se integra en Microsoft Passport for Work, un método alternativo de inicio de sesión que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual.

Passport permite usar un *gesto de usuario* para iniciar sesión en lugar de una contraseña. Un gesto de usuario podría ser una autenticación biométrica de PIN simple, como Windows Hello, o un dispositivo externo como un lector de huellas digitales.

>[!TIP]
>Microsoft Passport for Work ahora se conoce como Windows Hello para empresas. En la consola de Intune todavía no se refleja este cambio.

Intune se integra con Passport for Work de dos maneras:

-   Puede usar una directiva de Intune para controlar los gestos que se pueden y no se pueden usar para iniciar sesión.

-   Puede almacenar certificados de autenticación en el proveedor de almacenamiento de claves (KSP) de Passport for Work. Para obtener más información, consulte [Secure resource access with certificate profiles in Microsoft Intune (Proteger el acceso a los recursos con perfiles de certificado en Microsoft Intune)](secure-resource-access-with-certificate-profiles.md).

## Crear una directiva de Passport for Work

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows** &gt; **Passport for Work** para abrir la página de Passport for Work.

    ![Página de Passport for Work](../media/passport.png)

2.  Elija una de las siguientes opciones:
    - **Deshabilitar Passport for Work en los dispositivos inscritos**. Seleccione esta configuración si no quiere usar Passport for Work en dispositivos Windows 10. De esta manera, todas las demás configuraciones en pantalla se deshabilitan.
    - **Habilitar Passport for Work en los dispositivos inscritos**. Seleccione esta configuración si quiere configurar Passport for Work en todos los dispositivos Windows 10.
    - **No configurado**. Seleccione esta configuración si no quiere usar Intune para controlar la configuración de Passport for Work. No se cambiará ninguna de las opciones de configuración de Passport for Work en los dispositivos de Windows 10. Todas las demás configuraciones en pantalla se deshabilitan.
3.  Si ha seleccionado **Habilitar Passport for Work en los dispositivos inscritos**, configure las opciones necesarias que se deben aplicar a todos los dispositivos Windows 10 y Windows 10 Mobile inscritos.
4.  Cuando termine, elija **Guardar**.

## Passport for Work: Configuración de PIN


- **Requerir longitud mínima de PIN**/**Requerir longitud máxima de PIN**. Configura los dispositivos para que usen las longitudes de PIN mínima y máxima que se especifiquen, lo cual garantiza un inicio de sesión seguro. La longitud de PIN predeterminada es de 6 caracteres, pero se puede aplicar una longitud mínima de 4 caracteres. La longitud de PIN máxima es de 127 caracteres.
- **Requerir minúsculas en el PIN**/**Requerir mayúsculas en el PIN**/**Requerir caracteres especiales en el PIN**. Si quiere aplicar un PIN más seguro, puede requerir el uso de letras mayúsculas, letras minúsculas y caracteres especiales en el PIN. Elija de entre las siguientes opciones:
    - **Permitido**. Los usuarios pueden usar el tipo de carácter en el PIN, pero no es obligatorio.
    - **Requerido**. Los usuarios deben incluir al menos uno de los tipos de carácter en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.
    - **No permitido** (valor predeterminado). Los usuarios no deben usar estos tipos de caracteres en el PIN. (Este es también el comportamiento si no se configura esta opción).
    > [!TIP]
    > Los caracteres especiales incluyen: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **Expiración del PIN (días)**. Se recomienda especificar un período de expiración del PIN, transcurrido el cual hay que cambiarlo. El valor predeterminado es 41 días.
- **Recordar historial de PIN**. Restringe la reutilización de los PIN usados anteriormente. De forma predeterminada, no se pueden volver a usar los últimos cinco PIN.


## Passport for Work: Otras opciones

- **Usar un Módulo de plataforma segura (TPM)**. Un chip de TPM ofrece una capa adicional de seguridad de datos.<br>Elija uno de los siguientes valores:
    - **Requerido** (valor predeterminado). Solo los dispositivos con un TPM accesible pueden aprovisionar Passport for Work.
    - **Preferido**. Los dispositivos intentan primero usar un TPM. Si no está disponible, pueden usar el cifrado de software.
- **Permitir autenticación biométrica**. Habilita la autenticación biométrica, como el reconocimiento facial o la huella digital, como alternativa a un PIN para Passport for Work. Los usuarios todavía deben configurar un PIN de trabajo por si produce un error en la autenticación biométrica. Elija de entre las siguientes opciones:
    - **Sí**. Passport for Work permite la autenticación biométrica.
    - **No**. Passport for Work impide la autenticación biométrica (en todos los tipos de cuenta).
- **Usar tecnología mejorada contra la suplantación de identidad, cuando esté disponible**. Establece si se van a usar las características contra la suplantación de identidad de Windows Hello en los dispositivos que lo permitan (por ejemplo, cuando se detecte una fotografía de un rostro en lugar de un rostro real).<br>Si esta opción se establece en **Sí**, Windows requiere que todos los usuarios usen tecnología contra la suplantación de identidad para características faciales cuando se admitan.
- **Usar Remote Passport**. Si esta opción se establece en **Sí**, los usuarios pueden usar una cuenta de Passport remota para que actúe como dispositivo complementario portátil para la autenticación del equipo de escritorio. El equipo de escritorio debe estar unido a Azure Active Directory y el dispositivo complementario debe configurarse con un PIN de Passport for Work.

## Más información
Para obtener más información sobre Microsoft Passport, vea [la guía](https://technet.microsoft.com/library/mt589441.aspx) en la documentación de Windows 10.



<!--HONumber=Aug16_HO1-->


