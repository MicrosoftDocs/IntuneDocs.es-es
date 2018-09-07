---
title: Configuración del correo electrónico para dispositivos iOS en Microsoft Intune - Azure | Microsoft Docs
description: Cree un perfil de correo electrónico de configuración de dispositivos que use servidores de Exchange y recupere los atributos de Azure Active Directory. También puede habilitar SSL, autenticar a los usuarios con certificados o con el nombre de usuario y contraseña, y sincronizar el correo electrónico en dispositivos iOS con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d27e90655e54051d73989202d2bc849a66208f5
ms.sourcegitcommit: 488be75cbee88455b33c68a3ec2acb864d461bf8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "41910809"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>Configuración del perfil de correo electrónico para dispositivos iOS - Intune

Use la configuración del perfil de correo electrónico para configurar los dispositivos que funcionan con iOS.

> [!IMPORTANT]
> Hemos aplicado algunas mejoras a la característica S/MIME descrita en este artículo. Como resultado, la característica S/MIME se ha quitado temporalmente en Intune. Cuando esta característica se publique, quitaremos esta nota.

## <a name="email-settings"></a>Configuración de correo electrónico

- **Servidor de correo electrónico**: indique el nombre de host del servidor Exchange.
- **Nombre de la cuenta**: indique el nombre para mostrar en la cuenta de correo electrónico. Este nombre se muestra en los dispositivos de los usuarios.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (AAD). Intune genera dinámicamente el nombre de usuario que usa este perfil. Las opciones son:
  - **Nombre principal de usuario**: obtiene el nombre, como `user1` o `user1@contoso.com`.
  - **Dirección SMTP principal**: obtiene el nombre en formato de dirección de correo electrónico, como `user1@contoso.com`.
  - **Nombre de la cuenta sAM**: requiere el dominio, como `domain\user1`.

    Indique también:  
    - **Origen del nombre de dominio de usuario**: elija **AAD** (Azure Active Directory) o **Personalizar**.

      Si quiere obtener los atributos de **AAD**, escriba:
      - **Atributo de nombre de dominio de usuario de AAD**: elija si quiere obtener el atributo **Nombre de dominio completo** o **Nombre de NetBIOS** del usuario

      Si quiere usar los atributos **Personalizados**, escriba:
      - **Nombre de dominio personalizado que quiere usar**: escriba un valor que Intune use como nombre de dominio, como `contoso.com` o `contoso`.

- **Atributo Dirección de correo electrónico de AAD**: elija cómo se genera la dirección de correo electrónico para el usuario. Seleccione **Nombre principal de usuario** (`user1@contoso.com` o `user1`) para usar el nombre principal completo como dirección de correo electrónico o **Dirección SMTP principal** (`user1@contoso.com`) para usar la dirección SMTP principal para iniciar sesión en Exchange.
- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico. La autenticación multifactor de Azure no es compatible.
  - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS creados anteriormente, que se usará para autenticar la conexión de Exchange.
- **SSL**: **Habilitar** para usar la comunicación de Capa de sockets seguros (SSL) al enviar y recibir correos electrónicos y comunicarse con el servidor Exchange.
- **S/MIME**: **Habilitar S/MIME** para enviar correo electrónico saliente mediante firma S/MIME. Cuando se habilita, también se puede cifrar el correo electrónico para los destinatarios que pueden recibir correo electrónico cifrado, y descifrar el correo electrónico recibido de los remitentes.
  - Si seleccionó **Certificado**, seleccione un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange y cifrar los intercambios de correo electrónico.
- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar. También puede seleccionar **Ilimitado** para sincronizar todo el correo electrónico disponible.
- **Permitir a los mensajes moverse a otras cuentas de correo electrónico**: **Habilitar** permite a los usuarios mover los mensajes de correo electrónico entre distintas cuentas que tengan configuradas en sus dispositivos.
- **Permitir el envío de correo electrónico desde aplicaciones de terceros**: **Habilitar** permite que el usuario seleccione este perfil como la cuenta predeterminada para enviar correo electrónico, y permite que las aplicaciones de terceros abran los mensajes en la aplicación de correo electrónico nativa, por ejemplo, para adjuntar archivos a un correo electrónico.
- **Sincronizar direcciones de correo electrónico usadas recientemente**: **Habilitar** permite a los usuarios sincronizar con el servidor la lista de direcciones de correo electrónico que se han usado recientemente en el dispositivo.

## <a name="next-steps"></a>Pasos siguientes
[Configuración de las opciones de correo electrónico en Intune](email-settings-configure.md)
