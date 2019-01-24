---
title: Configuración del correo electrónico de Android y Android Enterprise en Microsoft Intune (Azure) | Microsoft Docs
description: Cree un perfil de correo electrónico de configuración de dispositivos que use servidores de Exchange y recupere los atributos de Azure Active Directory. Habilite SSL o SMIME, autentique a los usuarios con certificados o con el nombre de usuario/contraseña y sincronice el correo electrónico y las programaciones en Android y en dispositivos de perfil de trabajo Android con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: b96363d679a6f09327bf9a1b46421e786d1956a8
ms.sourcegitcommit: 912aee714432c4a1e8efeee253ca2be4f972adaa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316889"
---
# <a name="android-and-android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Configuración del dispositivo Android y Android Enterprise para configurar el correo electrónico, la autenticación y la sincronización en Intune

En este artículo se enumeran y describen los diferentes valores de configuración del correo electrónico que puede controlar en los dispositivos Android y Android Enterprise. Como parte de su solución de administración de dispositivos móviles (MDM), use estos valores de configuración para configurar un servidor de correo electrónico, usar SSL para cifrar correos electrónicos y mucho más.

Como administrador de Intune, puede crear y asignar configuraciones de correo electrónico a los siguientes dispositivos Android:

- Android Samsung Knox Standard
- Android Enterprise

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](email-settings-configure.md).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Servidor de correo electrónico**: escriba el nombre de host del servidor de Exchange.
- **Nombre de la cuenta**: indique el nombre para mostrar en la cuenta de correo electrónico. Este nombre se muestra en los dispositivos de los usuarios.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (AAD). Intune genera dinámicamente el nombre de usuario que usa este perfil. Las opciones son:
  - **Nombre principal de usuario**: obtiene el nombre, como `user1` o `user1@contoso.com`
  - **Nombre de usuario**: obtiene solo el nombre, como `user1`.
  - **Nombre de cuenta sAM**: requiere el dominio, como `domain\user1`. El nombre de la cuenta sAM solo puede usarse con dispositivos Android. No se admite Android Enterprise.

    Indique también:  
    - **Origen de nombre de dominio del usuario**: elija **AAD** (Azure Active Directory) o **Personalizar**.

      Si quiere obtener los atributos de **AAD**, escriba:
      - **Atributo de nombre de dominio del usuario de ADD**: elija si quiere obtener el atributo **Nombre de dominio completo** o **Nombre de NetBIOS** del usuario

      Si quiere usar los atributos **Personalizados**, escriba:
      - **Nombre de dominio personalizado que se usará**: escriba un valor que Intune use como nombre de dominio, como `contoso.com` o `contoso`.

- **Atributo de dirección de correo electrónico de AAD**: elija el modo en que se genera la dirección de correo electrónico para el usuario. Seleccione **Nombre principal de usuario** (`user1@contoso.com` o `user1`) para usar el nombre principal completo como dirección de correo electrónico o **Dirección SMTP principal** (`user1@contoso.com`) para usar la dirección SMTP principal para iniciar sesión en Exchange.

- **Método de autenticación**: Seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.
  - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.

### <a name="security-settings"></a>Configuración de seguridad

- **SSL**: Usa la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **S/MIME**: Enviar correo electrónico saliente mediante cifrado S/MIME.
  - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.

### <a name="synchronization-settings"></a>Configuración de sincronización

- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar o seleccione **Sin límite** para sincronizar todo el correo electrónico disponible.
- **Programación de sincronización**: seleccione una programación para que los dispositivos sincronicen datos de Exchange Server. También puede seleccionar **Cuando llegan los mensajes**, en cuyo caso los datos se sincronizan tan pronto como llegan, o **Manual**, donde el usuario del dispositivo debe iniciar la sincronización.

### <a name="content-sync-settings"></a>Configuración de la sincronización de contenido

- **Tipo de contenido para sincronizar**: Seleccione los tipos de contenido que quiere sincronizar en los dispositivos. **No configurado** deshabilita esta opción. Cuando se establece en **No configurado**, si un usuario final permite la sincronización en el dispositivo, la sincronización se deshabilitará de nuevo cuando el dispositivo se sincronice con Intune, como refuerza la directiva. 

  Puede sincronizar este contenido: 
  - **Contactos**
  - **Calendarioio**
  - **Tareas**

## <a name="android-enterprise"></a>Android Enterprise

- **Aplicación de correo electrónico**: seleccione **Gmail** o **Nine Work**.
- **Servidor de correo electrónico**: el nombre de host del servidor de Exchange.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo de Active Directory (AD) o Azure AD que se usará para generar el nombre de usuario de este perfil de correo electrónico. Seleccione la **dirección SMTP principal**, como user1@contoso.com, o el **nombre principal de usuario**, como user1@contoso.com.
- **Atributo de dirección de correo electrónico de AAD**: Modo en que se genera la dirección de correo electrónico para el usuario en cada dispositivo. Seleccione **Nombre principal de usuario** para usar el nombre principal completo como dirección de correo electrónico, o **Nombre de usuario**.
- **Método de autenticación**: Seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico.
  - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS que haya creado anteriormente para autenticar la conexión de Exchange.
- **SSL**: Usa la comunicación de Capa de sockets seguros (SSL) al enviar correos electrónicos, recibir correos electrónicos y comunicarse con el servidor Exchange.
- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar o seleccione **Sin límite** para sincronizar todo el correo electrónico disponible.
- **Tipo de contenido para sincronizar** (solo Nine Work): Seleccione los tipos de contenido que quiere sincronizar en los dispositivos. **No configurado** deshabilita esta opción. Cuando se establece en **No configurado**, si un usuario final permite la sincronización en el dispositivo, la sincronización se deshabilitará de nuevo cuando el dispositivo se sincronice con Intune, como refuerza la directiva. 

  Puede sincronizar este contenido: 
  - **Contactos**
  - **Calendarioio**
  - **Tareas**

## <a name="next-steps"></a>Pasos siguientes
[Configuración de las opciones de correo electrónico en Intune](email-settings-configure.md)
