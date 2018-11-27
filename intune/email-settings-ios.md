---
title: Configuración del correo electrónico para dispositivos iOS en Microsoft Intune - Azure | Microsoft Docs
description: Cree un perfil de correo electrónico de configuración de dispositivos que use servidores de Exchange y recupere los atributos de Azure Active Directory. También puede habilitar SSL, autenticar a los usuarios con certificados o con el nombre de usuario y contraseña, y sincronizar el correo electrónico en dispositivos iOS con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b3aa3e7a4cd79ab990afe7f02a1d6960bc66494a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180194"
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

- **Atributo Dirección de correo electrónico de AAD**: elija cómo se genera la dirección de correo electrónico para el usuario. Seleccione **Nombre principal de usuario** (`user1@contoso.com` o `user1`) para usar el nombre principal completo como dirección de correo electrónico. Seleccione **Dirección SMTP principal** (`user1@contoso.com`) para usar la dirección SMTP principal para iniciar sesión en Exchange.
- **Método de autenticación**: seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico. La autenticación multifactor de Azure no es compatible.
  - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS creados anteriormente, que se usará para autenticar la conexión de Exchange.
- **SSL**: la opción **Habilitar** usa la comunicación de Capa de sockets seguros (SSL) al enviar y recibir correos electrónicos y comunicarse con el servidor de Exchange.
- **OAuth**: la opción **Habilitar** usa la comunicación Open Authorization (OAuth) al enviar y recibir correos electrónicos y comunicarse con Exchange. Si su servidor OAuth usa la autenticación de certificado, elija **Certificado** como **método de autenticación** e incluya el certificado con el perfil. Si no, elija **Nombre de usuario y contraseña** como **método de autenticación**. Al utilizar OAuth, no olvide:

  - Comprobar que su solución de correo electrónico es compatible con OAuth antes de fijar este perfil como destino para sus usuarios. Office 365 Exchange Online es compatible con OAuth. Exchange local y otras soluciones de asociados o de terceros podrían no ser compatibles con OAuth. Exchange local se puede configurar para la autenticación moderna (consulte la entrada de blog [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) [Anuncio de la autenticación moderna híbrida para Exchange local]).

    Si el perfil de correo electrónico usa OAuth y el servicio de correo electrónico no lo admite, la opción **Vuelva a escribir la contraseña** aparecerá como dañada. Por ejemplo, no ocurrirá nada cuando el usuario seleccione **Vuelva a escribir la contraseña** en la configuración de los dispositivos de Apple.

  - Cuando OAuth está habilitado, los usuarios finales tienen una experiencia de inicio de sesión de "autenticación moderna" diferente en el correo electrónico que admite la autenticación multifactor (MFA). 

  - Algunas organizaciones deshabilitan la capacidad del usuario final de tener [acceso a las aplicaciones de autoservicio](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). En este escenario, el inicio de sesión de autenticación moderna puede fallar hasta que un administrador cree la aplicación de empresa "Cuentas de iOS" y conceda acceso a la aplicación en Azure AD a los usuarios.

    La acción predeterminada consiste en agregar una aplicación con la característica **Agregar aplicación** del [Panel de acceso a aplicaciones](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **sin la aprobación de la empresa**. Para obtener más información, consulte [Asignación de usuarios a las aplicaciones](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Al habilitar OAuth ocurre lo siguiente:  
  > 1. Se emite un perfil nuevo para los dispositivos que ya estén seleccionados como destino.
  > 2. A los usuarios finales se les vuelve a pedir que escriban sus credenciales.

- **S/MIME**: **Habilitar S/MIME** para enviar correo electrónico saliente mediante firma S/MIME. Cuando se habilita, también se puede cifrar el correo electrónico para los destinatarios que pueden recibir correo electrónico cifrado, y descifrar el correo electrónico recibido de los remitentes.
  - Si ha seleccionado **Certificado**, elija un perfil de certificado PKCS existente para autenticar la conexión de Exchange o cifrar los intercambios de correo electrónico.
- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar. También puede seleccionar **Ilimitado** para sincronizar todo el correo electrónico disponible.
- **Permitir a los mensajes moverse a otras cuentas de correo electrónico**: la opción **Habilitar** permite a los usuarios mover los mensajes de correo electrónico entre distintas cuentas que hayan configurado los usuarios en sus dispositivos.
- **Permitir que el correo electrónico se envíe desde aplicaciones de terceros**: la opción **Habilitar** permite a los usuarios seleccionar este perfil como cuenta predeterminada para enviar mensajes de correo electrónico. Permite que otras aplicaciones de terceros puedan abrir el correo en la aplicación de correo electrónico nativa (por ejemplo, para adjuntar archivos a los mensajes).
- **Sincronizar direcciones de correo electrónico usadas recientemente**: **Habilitar** permite a los usuarios sincronizar con el servidor la lista de direcciones de correo electrónico que se han usado recientemente en el dispositivo.

## <a name="next-steps"></a>Pasos siguientes
[Configuración de las opciones de correo electrónico en Intune](email-settings-configure.md)
