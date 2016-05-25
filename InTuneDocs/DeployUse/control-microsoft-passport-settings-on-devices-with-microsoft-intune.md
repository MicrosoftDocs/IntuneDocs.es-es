---
# required metadata

title: Controlar la configuración de Microsoft Passport en dispositivos mediante Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Controlar la configuración de Microsoft Passport en dispositivos mediante Microsoft Intune
Microsoft Intune se puede integrar con **Microsoft Passport for Work**, que es un método alternativo de inicio de sesión que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual.

Con Passport, se puede usar un **gesto de usuario** para iniciar sesión en lugar de una contraseña. Un gesto de usuario podría ser una autenticación biométrica de PIN simple, como Windows Hello, o un dispositivo externo como un lector de huellas digitales.

Intune se integra con Passport for Work de dos maneras:

-   Puede usar una directiva de Intune para controlar los gestos que se pueden y no se pueden usar para iniciar sesión.

-   Puede almacenar certificados de autenticación en el proveedor de almacenamiento de claves (KSP) de Passport for Work. Para obtener más información, vea [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..

## Para crear una directiva de Passport for Work

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows** &gt; **Passport for Work** para abrir la página de Passport for Work como se ilustra aquí.

    ![Página de Passport for Work](../media/passport.png)

2.  Elija una de las siguientes opciones:
    - **Deshabilitar Passport for Work en los dispositivos inscritos:** seleccione esta opción si no quiere usar Passport for Work en los dispositivos de Windows 10. Se deshabilitarán todas las demás opciones en pantalla.
    - **Habilitar Passport for Work en los dispositivos inscritos:** seleccione esta opción si quiere configurar Passport for Work en todos los dispositivos de Windows 10.
    - **No configurado:** seleccione esta opción si no quiere usar Intune para controlar la configuración de Passport for Work. No se cambiará ninguna de las opciones de configuración de Passport for Work en los dispositivos de Windows 10. Se deshabilitarán todas las demás opciones en pantalla.
3.  Si seleccionó **Habilitar Passport for Work en los dispositivos inscritos**, configure las opciones necesarias que se aplicarán a todos los dispositivos de Windows 10 y Windows 10 Mobile inscritos.
3.  Cuando termine, haga clic en **Guardar**..

## Passport for Work: Configuración de PIN

  
- **Requerir longitud mínima de PIN**/**Requerir longitud máxima de PIN:** configura los dispositivos para que usen las longitudes de PIN mínima y máxima que se especifiquen, lo que garantiza un inicio de sesión seguro. La longitud de PIN predeterminada es de 6 caracteres, pero se puede aplicar una longitud mínima de 4 caracteres. La longitud de PIN máxima es de 127 caracteres.
- **Requerir minúsculas en el PIN**/**Requerir mayúsculas en el PIN**/**Requerir caracteres especiales en el PIN:** también se puede lograr un PIN más seguro exigiendo el uso de mayúsculas y minúsculas y de caracteres especiales en el PIN. Elija de entre las siguientes opciones:
    - **Permitido:** los usuarios pueden usar el tipo de carácter en el PIN, pero no es obligatorio.
    - **Obligatorio:** los usuarios deben incluir al menos uno de los tipos de carácter en el PIN. Por ejemplo, una práctica habitual consiste en obligar a usar como mínimo una mayúscula y un carácter especial.
    - **No permitido** (valor predeterminado): los usuarios no deben usar estos tipos de caracteres en el PIN (este es el comportamiento si no se ha definido la configuración).
    > [!TIP]
    > Los caracteres especiales son lo siguientes: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **Expiración de PIN (días):** se recomienda especificar un período de caducidad para un PIN, transcurrido el cual hay que cambiarlo. El valor predeterminado es 41 días. 
- **Recordar historial de PIN:** use esta opción para restringir la reutilización de los PIN usados anteriormente. De forma predeterminada, no se pueden reutilizar los últimos cinco PIN.


## Passport for Work: Otras opciones

- **Usar un Módulo de plataforma segura (TPM):** un chip de Módulo de plataforma segura (TPM) ofrece una capa extra de seguridad de datos.<br>Elija uno de los siguientes valores:
    - **Obligatorio** (valor predeterminado): solo los dispositivos con un TPM accesible pueden aprovisionar Passport for Work.
    - **Preferido:** los dispositivos intentan primero usar un TPM. Si no está disponible, pueden usar el cifrado de software.
- **Permitir autenticación biométrica:** habilita la autenticación biométrica, como el reconocimiento facial o una huella digital, a modo de alternativa a un PIN para Passport for Work. Los usuarios todavía deben configurar un PIN de trabajo por si produce un error en la autenticación biométrica. Elija de entre las siguientes opciones:
    - **Sí:** Passport for Work permite la autenticación biométrica.
    - **No:** Passport for Work impide la autenticación biométrica (en todos los tipos de cuenta).
- **Usar tecnología mejorada contra la suplantación de identidad, cuando esté disponible:** establece si se van a usar las características contra la suplantación de identidad de Windows Hello en los dispositivos que lo permitan (por ejemplo, cuando se detecte una fotografía de una cara en lugar de una cara real).<br>Si establece en **Sí**, Windows requiere que todos los usuarios usen tecnología contra la suplantación de identidad (spoofing) para características faciales cuando se admitan.
- **Usar Remote Passport:** si esta opción se establece en **Sí**, los usuarios pueden usar una cuenta de Passport remota para que actúe como dispositivo complementario portátil para la autenticación del equipo de escritorio. El equipo de escritorio debe estar unido a Azure Active Directory y el dispositivo complementario debe configurarse con un PIN de Passport for Work.

## Más información
Para obtener más información sobre Microsoft Passport, vea [la guía](https://technet.microsoft.com/library/mt589441.aspx) en la documentación de Windows 10.




<!--HONumber=May16_HO1-->


