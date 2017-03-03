---
title: "Configuración del correo electrónico de Intune para dispositivos iOS | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda sobre la configuración de Intune que puede usar para configurar conexiones de correo electrónico en dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9f0fa6af-3669-439a-bd0d-75d8b1a0b135
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 186630903a606842406ff1d76115c1fa7d1c962e
ms.lasthandoff: 02/16/2017


---

# <a name="email-profile-settings-for-ios-devices-in-microsoft-intune"></a>Configuración del perfil de correo electrónico para dispositivos iOS en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Nombre de la cuenta**: el nombre para mostrar de la cuenta de correo electrónico tal y como aparecerá para los usuarios en sus dispositivos.
- **Atributo de nombre de usuario de AAD**: es el atributo de Active Directory (AD) o Azure AD que se usará para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como **user1@contoso.com**, o el **nombre principal de usuario**, como **usuario1** o **user1@contoso.com**.
- **Atributo de dirección de correo electrónico de AAD**: cómo se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Dirección SMTP primaria** para usar la dirección SMTP primaria para iniciar sesión en Exchange o **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico.
- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.
    - Si seleccionó **Certificado**, seleccione un cliente SCEP o un perfil de certificado PKCS creados anteriormente, que se usará para autenticar la conexión de Exchange.
- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **S/MIME**: envíe correo electrónico saliente mediante cifrado S/MIME.
    - Si seleccionó **Certificado**, seleccione un cliente SCEP o un perfil de certificado PKCS creados anteriormente, que se usará para autenticar la conexión de Exchange.
- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Unlimited** (Sin límite) para sincronizar todos el correo electrónico disponible.
- **Permitir a los mensajes moverse a otras cuentas de correo electrónico**: esta opción permite a los usuarios mover mensajes de correo electrónico entre distintas cuentas que tengan configuradas en su dispositivo.
- **Permitir el envío de correo electrónico desde aplicaciones de terceros**: permite que el usuario seleccione este perfil como la cuenta predeterminada para enviar correo electrónico, y permite que aplicaciones de terceros abran el correo electrónico en la aplicación de correo electrónico nativa, por ejemplo, para adjuntar archivos a un correo electrónico.
- **Sincronizar direcciones de correo electrónico usadas recientemente**: esta característica permite sincronizar la lista de direcciones de correo electrónico que se han usado recientemente en el dispositivo.

