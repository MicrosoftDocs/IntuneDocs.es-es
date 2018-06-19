---
title: Configuración del correo electrónico de Microsoft Intune para dispositivos iOS
titleSuffix: ''
description: Obtenga información sobre las opciones de configuración de Microsoft Intune que puede usar para configurar el correo electrónico en dispositivos que ejecutan iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fe791dce88878fdbde7c62e59452a53ac08ef06b
ms.sourcegitcommit: af0cc27b05bf0743f7d0970f5f3822f0aab346af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190492"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-ios"></a>Configuración de perfiles de correo electrónico en Microsoft Intune para dispositivos que ejecutan iOS 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se muestran las opciones de configuración de perfiles de correo electrónico que puede configurar para los dispositivos que ejecutan iOS.

## <a name="email-settings"></a>Configuración de correo electrónico

- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Nombre de la cuenta**: el nombre para mostrar de la cuenta de correo electrónico tal y como aparecerá para los usuarios en sus dispositivos.
- **Atributo de nombre de usuario de AAD**: es el atributo de Active Directory (AD) o Azure AD que se usa para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como **user1@contoso.com**, o el **nombre principal de usuario**, como **usuario1** o **user1@contoso.com**.
- **Atributo de dirección de correo electrónico de AAD**: cómo se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Dirección SMTP primaria** para usar la dirección SMTP primaria para iniciar sesión en Exchange o **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico.
- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico. (**Nota**: la autenticación multifactor de Azure no se admite).
    - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS creados anteriormente, que se usará para autenticar la conexión de Exchange.
- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **S/MIME**: envíe correo electrónico saliente mediante firma S/MIME.
    - Si seleccionó **Certificado**, seleccione un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.
- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Unlimited** (Sin límite) para sincronizar todos el correo electrónico disponible.
- **Permitir a los mensajes moverse a otras cuentas de correo electrónico**: esta opción permite a los usuarios mover mensajes de correo electrónico entre distintas cuentas que tengan configuradas en su dispositivo.
- **Permitir el envío de correo electrónico desde aplicaciones de terceros**: permite que el usuario seleccione este perfil como la cuenta predeterminada para enviar correo electrónico y permite que aplicaciones de terceros abran el correo electrónico en la aplicación de correo electrónico nativa, por ejemplo, para adjuntar archivos a un correo electrónico.
- **Sincronizar direcciones de correo electrónico usadas recientemente**: esta característica permite sincronizar la lista de direcciones de correo electrónico que se han usado recientemente en el dispositivo.
