---
title: 'Configuración del correo electrónico Android en Microsoft Intune: Azure | Microsoft Docs'
description: Cree un perfil de correo electrónico de configuración de dispositivos que use servidores de Exchange y recupere los atributos de Azure Active Directory. Habilite SSL o SMIME, autentique a los usuarios con certificados o con el nombre de usuario y contraseña y sincronice el correo electrónico y las programaciones en dispositivos Android Samsung Knox con Microsoft Intune.
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5611fb75ebf8106e70c1735458ee8b33fec16f7d
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838400"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Configuración del dispositivo Android para configurar el correo electrónico, la autenticación y la sincronización en Intune

En este artículo se enumeran y describen los diferentes valores de configuración del correo electrónico que puede controlar en los dispositivos Android Samsung Knox en Intune. Como parte de su solución de administración de dispositivos móviles (MDM), use estos valores de configuración para configurar un servidor de correo electrónico, usar SSL para cifrar correos electrónicos y mucho más.

Como administrador de Intune, puede crear y asignar configuraciones de correo electrónico a dispositivos Android Samsung Knox Standard.

Para más información sobre los perfiles de correo electrónico en Intune, consulte la [configuración de correo electrónico](email-settings-configure.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Servidor de correo electrónico**: escriba el nombre de host del servidor de Exchange. Por ejemplo, escriba `outlook.office365.com`.
- **Nombre de la cuenta**: indique el nombre para mostrar en la cuenta de correo electrónico. Este nombre se muestra en los dispositivos de los usuarios.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (Azure AD). Intune genera dinámicamente el nombre de usuario que usa este perfil. Las opciones son:
  - **Nombre principal de usuario**: obtiene el nombre, como `user1` o `user1@contoso.com`
  - **Nombre de usuario**: obtiene solo el nombre, como `user1`.
  - **Nombre de cuenta sAM**: requiere el dominio, como `domain\user1`. El nombre de la cuenta sAM solo se usa con dispositivos Android.

    Indique también:  
    - **Origen de nombre de dominio del usuario**: elija **AAD** (Azure Active Directory) o **Personalizar**.

      Si quiere obtener los atributos de **AAD**, escriba:
      - **Atributo de nombre de dominio del usuario de ADD**: elija si quiere obtener el atributo **Nombre de dominio completo** o **Nombre de NetBIOS** del usuario

      Si quiere usar los atributos **Personalizados**, escriba:
      - **Nombre de dominio personalizado que se usará**: escriba un valor que Intune use como nombre de dominio, como `contoso.com` o `contoso`.

- **Atributo de dirección de correo electrónico de AAD**: este nombre es el atributo de correo electrónico que Intune obtiene de Azure AD. Intune genera dinámicamente la dirección de correo electrónico que este perfil usa. Las opciones son:
  - **Nombre principal de usuario**:  usa el nombre principal completo, como `user1@contoso.com` o `user1`, como dirección de correo electrónico.
  - **Dirección SMTP principal**: use la dirección SMTP principal, como `user1@contoso.com`, para iniciar sesión en Exchange.

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
  - **Contactos**: elija **Habilitar** para permitir que los usuarios finales sincronicen contactos con sus dispositivos.
  - **Calendario**: elija **Habilitar** para permitir que los usuarios finales sincronicen el calendario con sus dispositivos.
  - **Tareas**: elija **Habilitar** para permitir que los usuarios finales sincronicen todas las tareas con sus dispositivos.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de correo electrónico para [Android Enterprise (perfil de trabajo)](email-settings-android-enterprise.md), [iOS](email-settings-ios.md), [Windows 10 y versiones posteriores](email-settings-windows-10.md) y [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
