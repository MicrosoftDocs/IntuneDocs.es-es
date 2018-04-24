---
title: Configuración del correo electrónico de Microsoft Intune para dispositivos que ejecutan Android y Android for Work
titleSuffix: ''
description: Obtenga información sobre las opciones de configuración de Microsoft Intune que puede usar para configurar el correo electrónico en dispositivos que ejecutan Android y Android for Work.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 10bea7ace3fe03db66fa6f8a83a94679dfdc071c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>Configuración de perfiles de correo electrónico en Microsoft Intune para dispositivos que ejecutan Android y Android for Work

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se muestran las opciones de configuración de perfiles de correo electrónico que puede configurar para los dispositivos que ejecutan Android.

Como administrador de Intune, puede crear y asignar configuraciones de correo electrónico a los siguientes dispositivos Android:
- [Android Samsung Knox Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>Configuración del correo electrónico de Android Samsung Knox Standard
- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Nombre de la cuenta**: el nombre para mostrar de la cuenta de correo electrónico tal y como aparecerá para los usuarios en sus dispositivos.
- **Atributo de nombre de usuario de AAD**: es el atributo de Active Directory (AD) o Azure AD que se usará para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como user1@contoso.com, o el **nombre principal de usuario**, como user1@contoso.com.
- **Atributo de dirección de correo electrónico de AAD**: cómo se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Dirección SMTP primaria** para usar la dirección SMTP primaria para iniciar sesión en Exchange o use **Nombre principal de usuario** para utilizar el nombre principal completo como dirección de correo electrónico.
- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.
    - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.

### <a name="security-settings"></a>Configuración de seguridad

- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **S/MIME**: envíe correo electrónico saliente mediante cifrado S/MIME.
    - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.

### <a name="synchronization-settings"></a>Configuración de sincronización

- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Unlimited** (Sin límite) para sincronizar todos el correo electrónico disponible.
- **Programación de sincronización**: seleccione la programación según la cual los dispositivos sincronizarán datos de Exchange Server. También puede seleccionar **Cuando llegan los mensajes**, en cuyo caso los datos se sincronizan tan pronto como llegan, o **Manual**, donde el usuario del dispositivo debe iniciar la sincronización.

### <a name="content-sync-settings"></a>Configuración de la sincronización de contenido

- **Tipo de contenido para sincronizar**: seleccione los tipos de contenido que quiere sincronizar con los dispositivos:
    - **Contactos**
    - **Calendarioio**
    - **Tareas**

## <a name="android-for-work-email-settings"></a>Configuración del correo electrónico de Android for Work

- **Aplicación de correo electrónico**: seleccione **Gmail** o **Nine Work**.
- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo de Active Directory (AD) o Azure AD que se usa para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como user1@contoso.com, o el **nombre principal de usuario**, como user1@contoso.com.
- **Atributo de dirección de correo electrónico de AAD**: cómo se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico, o **Nombre de usuario**.
- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.
    - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.
- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Unlimited** (Sin límite) para sincronizar todos el correo electrónico disponible.
- **Tipo de contenido para sincronizar** (solo Nine Work): seleccione los tipos de contenido que quiere sincronizar con los dispositivos:
    - **Contactos**
    - **Calendarioio**
    - **Tareas**
