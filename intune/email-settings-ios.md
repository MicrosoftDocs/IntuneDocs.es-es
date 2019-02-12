---
title: Configuración del correo electrónico para dispositivos iOS en Microsoft Intune - Azure | Microsoft Docs
description: Vea una lista de todas las opciones de correo electrónico que se pueden configurar y agregar en dispositivos iOS en Microsoft Intune, incluido el uso de servidores de Exchange y la obtención de atributos de Azure Active Directory. También puede habilitar SSL, autenticar usuarios con certificados o con nombre de usuario y contraseña, y sincronizar el correo electrónico en dispositivos iOS con perfiles de configuración de dispositivo de Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd1f24c7114e21239d19ca2e99fc05d125e675d9
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845797"
---
# <a name="email-profile-settings-for-ios-devices-in-intune"></a>Configuración del perfil de correo electrónico para dispositivos iOS en Intune

En Microsoft Intune, puede crear y configurar el correo electrónico para conectarse a un servidor de correo electrónico, elegir cómo se autentican los usuarios, usar S/MIME para el cifrado, etc.

En este artículo se enumeran y se describen todas las opciones de correo electrónico disponibles para los dispositivos con iOS. Puede crear un perfil de configuración de dispositivo para insertar o implementar esas opciones de correo electrónico en los dispositivos iOS.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](email-settings-configure.md#create-a-device-profile).

## <a name="email-settings"></a>Configuración de correo electrónico

- **Servidor de correo electrónico**: escriba el nombre de host del servidor de Exchange.
- **Nombre de la cuenta**: indique el nombre para mostrar en la cuenta de correo electrónico. Este nombre se muestra en los dispositivos de los usuarios.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (AAD). Intune genera dinámicamente el nombre de usuario que usa este perfil. Las opciones son:
  - **Nombre principal de usuario**: obtiene el nombre, como `user1` o `user1@contoso.com`
  - **Dirección SMTP principal**: obtiene el nombre en formato de dirección de correo electrónico, como `user1@contoso.com`.
  - **Nombre de cuenta sAM**: requiere el dominio, como `domain\user1`.

    Indique también:  
    - **Origen de nombre de dominio del usuario**: elija **AAD** (Azure Active Directory) o **Personalizar**.

      Si quiere obtener los atributos de **AAD**, escriba:
      - **Atributo de nombre de dominio del usuario de ADD**: elija si quiere obtener el atributo **Nombre de dominio completo** o **Nombre de NetBIOS** del usuario

      Si quiere usar los atributos **Personalizados**, escriba:
      - **Nombre de dominio personalizado que se usará**: escriba un valor que Intune use como nombre de dominio, como `contoso.com` o `contoso`.

- **Atributo de dirección de correo electrónico de AAD**: elija el modo en que se genera la dirección de correo electrónico para el usuario. Seleccione **Nombre principal de usuario** (`user1@contoso.com` o `user1`) para usar el nombre principal completo como dirección de correo electrónico. Seleccione **Dirección SMTP principal** (`user1@contoso.com`) para usar la dirección SMTP principal para iniciar sesión en Exchange.
- **Método de autenticación**: Seleccione **Nombre de usuario y contraseña** o **Certificados** como método de autenticación que usa el perfil de correo electrónico. La autenticación multifactor de Azure no es compatible.
  - Si seleccionó **Certificado**, seleccione un SCEP cliente o un perfil de certificado PKCS creados anteriormente, que se usará para autenticar la conexión de Exchange.
- **SSL**: **Habilitar** usa la comunicación de Capa de sockets seguros (SSL) al enviar y recibir correos electrónicos y al comunicarse con el servidor de Exchange.
- **OAuth**: **Habilitar** usa la comunicación Open Authorization (OAuth) al enviar y recibir correos electrónicos y al comunicarse con Exchange. Si su servidor OAuth usa la autenticación de certificado, elija **Certificado** como **método de autenticación** e incluya el certificado con el perfil. Si no, elija **Nombre de usuario y contraseña** como **método de autenticación**. Al utilizar OAuth, no olvide:

  - Comprobar que su solución de correo electrónico es compatible con OAuth antes de fijar este perfil como destino para sus usuarios. Office 365 Exchange Online es compatible con OAuth. Exchange local y otras soluciones de asociados o de terceros podrían no ser compatibles con OAuth. Exchange local se puede configurar para la autenticación moderna (consulte la entrada de blog [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) [Anuncio de la autenticación moderna híbrida para Exchange local]).

    Si el perfil de correo electrónico usa OAuth y el servicio de correo electrónico no lo admite, la opción **Vuelva a escribir la contraseña** aparecerá como dañada. Por ejemplo, no ocurrirá nada cuando el usuario seleccione **Vuelva a escribir la contraseña** en la configuración de los dispositivos de Apple.

  - Cuando OAuth está habilitado, los usuarios finales tienen una experiencia de inicio de sesión de "autenticación moderna" diferente en el correo electrónico que admite la autenticación multifactor (MFA). 

  - Algunas organizaciones deshabilitan la capacidad del usuario final de tener [acceso a las aplicaciones de autoservicio](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). En este escenario, el inicio de sesión de autenticación moderna puede fallar hasta que un administrador cree la aplicación de empresa "Cuentas de iOS" y conceda acceso a la aplicación en Azure AD a los usuarios.

    La acción predeterminada consiste en agregar una aplicación con la característica **Agregar aplicación** del [Panel de acceso a aplicaciones](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **sin la aprobación de la empresa**. Para obtener más información, consulte [Asignación de usuarios a las aplicaciones](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Al habilitar OAuth ocurre lo siguiente:  
  > 1. Se emite un perfil nuevo para los dispositivos que ya estén seleccionados como destino.
  > 2. A los usuarios finales se les vuelve a pedir que escriban sus credenciales.

- **S/MIME**: **Habilitar S/MIME** para permitir a los usuarios firmar o cifrar el correo electrónico en la aplicación de correo electrónico nativa de iOS. 

  Cuando se usa S/MIME con un mensaje de correo electrónico, se confirma la autenticidad del remitente y la integridad y la confidencialidad del mensaje.

  - **Firma S/MIME habilitada**: elija **Habilitar** para permitir a los usuarios firmar digitalmente el correo electrónico saliente de la cuenta especificada. La firma ayuda a los usuarios que reciben mensajes a estar seguros de que el mensaje procede del remitente específico y no de alguien que pretende ser el remitente. **Deshabilitar** no permite a los usuarios firmar digitalmente el mensaje.
    - **Permitir al usuario cambiar la configuración**: elija **Habilitar** para permitir a los usuarios cambiar el comportamiento de firma S/MIME. **Deshabilitar** evita que los usuarios cambien la opción de firma S/MIME configurada. Disponible en iOS 12 y versiones más recientes.

  - **Certificado de firma S/MIME**: se selecciona un perfil de certificado PKCS o SCEP existente que se usa para firmar los mensajes de correo electrónico.
    - **Permitir al usuario cambiar la configuración**: elija **Habilitar** para permitir a los usuarios cambiar el certificado de firma. **Deshabilitar** evita que los usuarios cambien el certificado de firma y los obliga a usar el certificado configurado. Disponible en iOS 12 y versiones más recientes.

  - **Cifrar de forma predeterminada**: **Habilitar** cifra todos los mensajes como comportamiento predeterminado. **Deshabilitar** no cifra todos los mensajes como comportamiento predeterminado.
    - **Permitir al usuario cambiar la configuración**: elija **Habilitar** para permitir a los usuarios cambiar el comportamiento de cifrado predeterminado. **Deshabilitar** evita que los usuarios cambien el comportamiento predeterminado de cifrado y los obliga a usar la opción configurada. Disponible en iOS 12 y versiones más recientes.

  - **Forzar cifrado por mensaje**: el cifrado por mensaje permite a los usuarios elegir qué mensajes se cifran antes de enviarse. Elija **Habilitar** para mostrar la opción de cifrado por mensaje al crear un nuevo correo electrónico. Luego los usuarios pueden optar por activar o no el cifrado por mensaje. **Deshabilitar** evita que aparezca la opción de cifrado por mensaje.

    Si la opción **Cifrar de forma predeterminada** está habilitada, la habilitación del cifrado por mensaje permite a los usuarios anular el cifrado por mensaje. Si la opción **Cifrar de forma predeterminada** está deshabilitada, la habilitación del cifrado por mensaje permite a los usuarios optar por el cifrado por mensaje.

  - **Certificado de cifrado S/MIME**: seleccione un perfil de certificado PKCS o SCEP existente que se usa para cifrar los mensajes de correo electrónico.
    - **Permitir al usuario cambiar la configuración**: elija **Habilitar** para permitir a los usuarios cambiar el certificado de cifrado. **Deshabilitar** evita que los usuarios cambien el certificado de cifrado y los obliga a usar el certificado configurado. Disponible en iOS 12 y versiones más recientes.
- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar. También puede seleccionar **Ilimitado** para sincronizar todo el correo electrónico disponible.
- **Permitir que los mensajes se muevan a otras cuentas de correo electrónico**: **Habilitar** permite a los usuarios mover los mensajes de correo electrónico entre las distintas cuentas que han configurado en sus dispositivos.
- **Permitir que el correo electrónico se envíe desde aplicaciones de terceros**: **Habilitar** permite a los usuarios seleccionar este perfil como cuenta predeterminada para enviar correo electrónico. Permite que otras aplicaciones de terceros puedan abrir el correo en la aplicación de correo electrónico nativa (por ejemplo, para adjuntar archivos a los mensajes).
- **Sincronizar direcciones de correo electrónico usadas recientemente**: **Habilitar** permite a los usuarios sincronizar la lista de direcciones de correo electrónico que se han usado recientemente en el dispositivo con el servidor.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Configure el correo electrónico en dispositivos [Android](email-settings-android.md), [Windows 10](email-settings-windows-10.md) y [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
