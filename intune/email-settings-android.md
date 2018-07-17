---
title: Configuración del correo electrónico para Android y dispositivos de perfil de trabajo Android en Microsoft Intune - Azure | Microsoft Docs
description: Cree un perfil de correo electrónico de configuración de dispositivos que use servidores de Exchange y recupere los atributos de Azure Active Directory. También puede habilitar SSL o SMIME, autenticar a los usuarios con certificados o con el nombre de usuario/contraseña y sincronizar el correo electrónico y las programaciones en Android y en dispositivos de perfil de trabajo Android con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 136ccb6079b16c13098c1dbd6ca49e8254c14f89
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905774"
---
# <a name="email-profile-settings-for-devices-running-android-and-android-enterprise---intune"></a>Configuración de perfiles de correo electrónico para dispositivos que ejecutan Android y Android Enterprise - Intune

Use la configuración del perfil de correo electrónico para configurar los dispositivos que ejecuten Android.

Como administrador de Intune, puede crear y asignar configuraciones de correo electrónico a los siguientes dispositivos Android:

- Android Samsung Knox Standard
- Android Enterprise

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Servidor de correo electrónico**: indique el nombre de host del servidor Exchange.
- **Nombre de la cuenta**: indique el nombre para mostrar en la cuenta de correo electrónico. Este nombre se muestra en los dispositivos de los usuarios.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (AAD). Intune genera dinámicamente el nombre de usuario que usa este perfil. Las opciones son:
  - **Nombre principal de usuario**: obtiene el nombre, como `user1` o `user1@contoso.com`.
  - **Nombre de usuario**: obtiene solo el nombre, como `user1`.
  - **Nombre de la cuenta sAM**: requiere el dominio, como `domain\user1`. El nombre de la cuenta sAM solo puede usarse con dispositivos Android. No se admite Android Enterprise.

    Indique también:  
    - **Origen del nombre de dominio de usuario**: elija **AAD** (Azure Active Directory) o **Personalizar**.

      Si quiere obtener los atributos de **AAD**, escriba:
      - **Atributo de nombre de dominio de usuario de AAD**: elija si quiere obtener el atributo **Nombre de dominio completo** o **Nombre de NetBIOS** del usuario

      Si quiere usar los atributos **Personalizados**, escriba:
      - **Nombre de dominio personalizado que quiere usar**: escriba un valor que Intune use como nombre de dominio, como `contoso.com` o `contoso`.

- **Atributo Dirección de correo electrónico de AAD**: elija cómo se genera la dirección de correo electrónico para el usuario. Seleccione **Nombre principal de usuario** (`user1@contoso.com` o `user1`) para usar el nombre principal completo como dirección de correo electrónico o **Dirección SMTP principal** (`user1@contoso.com`) para usar la dirección SMTP principal para iniciar sesión en Exchange.

- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.
  - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.

### <a name="security-settings"></a>Configuración de seguridad

- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **S/MIME**: envíe correo electrónico saliente mediante cifrado S/MIME.
  - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.

### <a name="synchronization-settings"></a>Configuración de sincronización

- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Sin límite** para sincronizar todos el correo electrónico disponible.
- **Programación de sincronización**: seleccione una programación para que los dispositivos sincronicen datos de Exchange Server. También puede seleccionar **Cuando llegan los mensajes**, en cuyo caso los datos se sincronizan tan pronto como llegan, o **Manual**, donde el usuario del dispositivo debe iniciar la sincronización.

### <a name="content-sync-settings"></a>Configuración de la sincronización de contenido

- **Tipo de contenido para sincronizar**: seleccione los tipos de contenido que quiere sincronizar con los dispositivos:
  - **Contactos**
  - **Calendarioio**
  - **Tareas**

## <a name="android-enterprise"></a>Android Enterprise

- **Aplicación de correo electrónico**: seleccione **Gmail** o **Nine Work**.
- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo de Active Directory (AD) o Azure AD que se usa para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como user1@contoso.com, o el **nombre principal de usuario**, como user1@contoso.com.
- **Atributo de dirección de correo electrónico de AAD**: cómo se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico, o **Nombre de usuario**.
- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.
  - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.
- **SSL**: use la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar, o seleccione **Sin límite** para sincronizar todos el correo electrónico disponible.
- **Tipo de contenido para sincronizar** (solo Nine Work): seleccione los tipos de contenido que quiere sincronizar con los dispositivos:
  - **Contactos**
  - **Calendarioio**
  - **Tareas**

## <a name="next-steps"></a>Pasos siguientes
[Configuración de las opciones de correo electrónico en Intune](email-settings-configure.md)
