---
title: 'Configuración del correo electrónico para dispositivos iOS/iPadOS en Microsoft Intune: Azure | Microsoft Docs'
description: Vea una lista de todas las opciones de correo electrónico que se pueden configurar y agregar en dispositivos iOS y iPadOS en Microsoft Intune, como el uso de servidores de Exchange y la obtención de atributos de Azure Active Directory. También puede habilitar SSL, autenticar usuarios con certificados o con nombre de usuario y contraseña, y sincronizar el correo electrónico en dispositivos iOS/iPadOS con perfiles de configuración de dispositivo de Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ea06c50b1da237d4a822e80a8085b3b51913cec
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512813"
---
# <a name="add-e-mail-settings-for-ios-and-ipados-devices-in-microsoft-intune"></a>Incorporación de la configuración de correo electrónico para dispositivos iOS y iPadOS en Microsoft Intune

En Microsoft Intune, puede crear y configurar el correo electrónico para conectarse a un servidor de correo electrónico, elegir cómo se autentican los usuarios, usar S/MIME para el cifrado, etc.

En este artículo se enumeran y describen todas las configuraciones de correo electrónico disponibles para los dispositivos con iOS/iPadOS. Puede crear un perfil de configuración de dispositivo para insertar o implementar esas configuraciones de correo electrónico en los dispositivos iOS/iPadOS.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](../email-settings-configure.md).

> [!NOTE]
> Estas configuraciones están disponibles con todos los tipos de inscripción. Para más información sobre los tipos de inscripción, consulte [Inscripción en iOS/iPadOS](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>Configuración de la cuenta de Exchange ActiveSync

- **Servidor de correo electrónico**: escriba el nombre de host del servidor de Exchange.
- **Nombre de la cuenta**: indique el nombre para mostrar en la cuenta de correo electrónico. Este nombre se muestra en los dispositivos de los usuarios.
- **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (AAD). Intune genera dinámicamente el nombre de usuario que usa este perfil. Las opciones son:
  - **Nombre principal de usuario**: obtiene el nombre, como `user1` o `user1@contoso.com`
  - **Dirección SMTP principal**: obtiene el nombre en formato de dirección de correo electrónico, como `user1@contoso.com`.
  - **Nombre de cuenta sAM**: requiere el dominio, como `domain\user1`. Indique también:  
    - **Origen de nombre de dominio del usuario**: elija **AAD** (Azure Active Directory) o **Personalizar**.
      - **AAD**: obtener los atributos de Azure AD. Indique también:
        - **Atributo de nombre de dominio del usuario de ADD**: elija si quiere obtener el atributo **Nombre de dominio completo** (`contoso.com`) o **Nombre NetBIOS** (`contoso`) del usuario.

      - **Personalizado**: obtenga los atributos de un nombre de dominio personalizado. Indique también:
        - **Nombre de dominio personalizado que se usará**: escriba un valor que Intune use como nombre de dominio, como `contoso.com` o `contoso`.

- **Atributo de dirección de correo electrónico de AAD**: elija el modo en que se genera la dirección de correo electrónico para el usuario. Las opciones son:
  - **Nombre principal de usuario**: use el nombre principal completo como dirección de correo electrónico, por ejemplo, `user1@contoso.com` o `user1`.
  - **Dirección SMTP principal**: use la dirección SMTP principal para iniciar sesión en Exchange, por ejemplo, `user1@contoso.com`.
- **Método de autenticación**: elija cómo se autentican los usuarios en el servidor de correo electrónico. Las opciones son:
  - **Certificado**: seleccione un perfil de certificado PKCS o SCEP de cliente que haya creado anteriormente para autenticar la conexión de Exchange. Esta opción proporciona a los usuarios la experiencia más segura y completa.
  - **Nombre de usuario y contraseña**: se pide a los usuarios que escriban su nombre de usuario y contraseña.
  - **Credencial derivada**: use un certificado que se derive de la tarjeta inteligente de un usuario. Para más información, consulte [Uso de credenciales derivadas en Microsoft Intune](../protect/derived-credentials.md).

  >[!NOTE]
  > La autenticación multifactor de Azure no es compatible.
  
- **SSL**: **Habilitar** usa la comunicación de Capa de sockets seguros (SSL) al enviar y recibir correos electrónicos y al comunicarse con el servidor de Exchange.
- **OAuth**: **Habilitar** usa la comunicación Open Authorization (OAuth) al enviar y recibir correos electrónicos y al comunicarse con Exchange. Si su servidor OAuth usa la autenticación de certificado, elija **Certificado** como **método de autenticación** e incluya el certificado con el perfil. Si no, elija **Nombre de usuario y contraseña** como **método de autenticación**. Al utilizar OAuth, no olvide:

  - Comprobar que su solución de correo electrónico es compatible con OAuth antes de fijar este perfil como destino para sus usuarios. Office 365 Exchange Online es compatible con OAuth. Exchange local y otras soluciones de asociados o de terceros podrían no ser compatibles con OAuth. Exchange local se puede configurar para la autenticación moderna (consulte la entrada de blog [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) [Anuncio de la autenticación moderna híbrida para Exchange local]).

    Si el perfil de correo electrónico usa OAuth y el servicio de correo electrónico no lo admite, la opción **Vuelva a escribir la contraseña** aparecerá como dañada. Por ejemplo, no ocurrirá nada cuando el usuario seleccione **Vuelva a escribir la contraseña** en la configuración de los dispositivos de Apple.

  - Cuando OAuth está habilitado, los usuarios finales tienen una experiencia de inicio de sesión de "autenticación moderna" diferente en el correo electrónico que admite la autenticación multifactor (MFA). 

  - Algunas organizaciones deshabilitan la capacidad del usuario final de tener [acceso a las aplicaciones de autoservicio](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). En este escenario, el inicio de sesión de autenticación moderna puede fallar hasta que un administrador cree la aplicación de empresa "Cuentas de iOS" y conceda acceso a la aplicación en Azure AD a los usuarios.

    La acción predeterminada consiste en agregar una aplicación con la característica **Agregar aplicación** del [Panel de acceso a aplicaciones](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction)**sin la aprobación de la empresa**. Para obtener más información, consulte [Asignación de usuarios a las aplicaciones](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Al habilitar OAuth ocurre lo siguiente:  
  > 1. Se emite un perfil nuevo para los dispositivos que ya estén seleccionados como destino.
  > 2. A los usuarios finales se les vuelve a pedir que escriban sus credenciales.

## <a name="exchange-activesync-profile-configuration"></a>Configuración del perfil de Exchange ActiveSync

> [!IMPORTANT]
> La configuración de estas opciones implementa un nuevo perfil en el dispositivo, incluso cuando se actualiza un perfil de correo electrónico existente para incluir estas opciones. A los usuarios se les pide que escriban la contraseña de su cuenta de Exchange ActiveSync. Esta configuración surte efecto cuando se escribe la contraseña.

- **Datos de Exchange para sincronizar**: cuando se use Exchange ActiveSync, elija los servicios de Exchange que se sincronizan en el dispositivo: Calendario, Contactos, Recordatorios, Notas y Correo electrónico. Las opciones son:
  - **Todos los datos** (valor predeterminado): la sincronización está habilitada para todos los servicios.
  - **Solo Correo electrónico**: la sincronización está habilitada solo para Correo electrónico. La sincronización está deshabilitada para los demás servicios.
  - **Solo Calendario**: la sincronización solo está habilitada para Calendario. La sincronización está deshabilitada para los demás servicios.
  - **Solo Calendario y Contactos**: la sincronización solo está habilitada para Calendario y Contactos. La sincronización está deshabilitada para los demás servicios.
  - **Solo Contactos**: la sincronización está habilitada solo para Contactos. La sincronización está deshabilitada para los demás servicios.

  Esta característica se aplica a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Permitir a los usuarios cambiar la configuración de sincronización**: elija si los usuarios pueden cambiar la configuración de Exchange ActiveSync en los servicios de Exchange del dispositivo: Calendario, Contactos, Recordatorios, Notas y Correo electrónico. Las opciones son:

  - **Sí** (valor predeterminado): los usuarios pueden cambiar el comportamiento de sincronización de todos los servicios. Si elige **Sí**, se permiten los cambios en *todos* los servicios.
  - **No**: los usuarios no pueden cambiar la configuración de sincronización de todos los servicios. La elección de **No** bloquea los cambios en *todos* los servicios.

  > [!TIP]
  > Si configuró la opción **Datos de Exchange para sincronizar** para sincronizar solo algunos servicios, se recomienda seleccionar **No** para esta opción. Al elegir **No** se impide que los usuarios cambien el servicio de Exchange que está sincronizado.

  Esta característica se aplica a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

## <a name="exchange-activesync-email-settings"></a>Configuración del correo electrónico de Exchange ActiveSync

- **S/MIME**: S/MIME usa certificados de correo electrónico que proporcionan seguridad adicional a las comunicaciones de correo electrónico mediante firma, cifrado y descifrado. Cuando se usa S/MIME con un mensaje de correo electrónico, se confirma la autenticidad del remitente y la integridad y la confidencialidad del mensaje.

  Las opciones son:

  - **Deshabilitar S/MIME** (valor predeterminado): no usa un certificado de correo electrónico S/MIME para firmar, cifrar o descifrar los correos electrónicos.
  - **Habilitar S/MIME**: permite a los usuarios firmar o cifrar el correo electrónico en la aplicación de correo nativa de iOS/iPadOS. Indique también:

    - **Firma S/MIME habilitada**: **Deshabilitar** (valor predeterminado) no permite que los usuarios firmen digitalmente el mensaje. La opción **Habilitar** permite a los usuarios firmar digitalmente el correo electrónico saliente de la cuenta especificada. La firma ayuda a los usuarios que reciben mensajes a estar seguros de que el mensaje procede del remitente específico y no de alguien que pretende ser el remitente.
      - **Permitir que el usuario cambie la configuración**: **Habilitar** permite a los usuarios cambiar las opciones de firma. **Deshabilitar** (valor predeterminado) impide que los usuarios cambien la firma y les obliga a usar la firma configurada.
      - **Tipo de certificado de firma**. Las opciones son:
        - **No configurado**: Intune no cambia ni actualiza esta configuración.
        - **Ninguno**: como administrador, no se fuerza un certificado específico. Seleccione esta opción para que los usuarios puedan elegir su propio certificado.
        - **Credencial derivada**: use un certificado que se derive de la tarjeta inteligente de un usuario. Para más información, consulte [Uso de credenciales derivadas en Microsoft Intune](../protect/derived-credentials.md).
        - **Certificados**: se selecciona un perfil de certificado PKCS o SCEP existente que se usa para firmar los mensajes de correo electrónico.
      - **Permitir que el usuario cambie la configuración**: **Habilitar** permite a los usuarios cambiar el certificado de firma. La opción **Deshabilitar** (predeterminada) evita que los usuarios cambien el certificado de firma y los obliga a usar el certificado configurado.

        Esta característica se aplica a:  
        - iOS 12 y versiones más recientes
        - IPadOS 12 y versiones más recientes

    - **Cifrar de forma predeterminada**: **Habilitar** cifra todos los mensajes como comportamiento predeterminado. La opción **Deshabilitar** (predeterminada) no cifra todos los mensajes como comportamiento predeterminado.
      - **Permitir al usuario cambiar la configuración**: elija **Habilitar** para permitir que los usuarios cambien el comportamiento de cifrado predeterminado. La opción **Deshabilitar** evita que los usuarios cambien el comportamiento predeterminado de cifrado y los obliga a usar el cifrado configurado.

        Esta característica se aplica a:  
        - iOS 12 y versiones más recientes
        - IPadOS 12 y versiones más recientes

    - **Forzar cifrado por mensaje**: el cifrado por mensaje permite a los usuarios elegir qué mensajes se cifran antes de enviarse.

      La opción **Habilitar** muestra la opción de cifrado por mensaje al crear un nuevo correo electrónico. Luego los usuarios pueden optar por activar o no el cifrado por mensaje. Si la opción **Cifrar de forma predeterminada** está también habilitada, la habilitación del cifrado por mensaje permite a los usuarios anular el cifrado por mensaje.

      La opción **Deshabilitar** (predeterminada) evita que aparezca la opción de cifrado por mensaje. Si la opción **Cifrar de forma predeterminada** está también deshabilitada, la habilitación del cifrado por mensaje permite a los usuarios optar por el cifrado por mensaje.

      - **Tipo de certificado de cifrado**. Las opciones son:
        - **No configurado**: Intune no cambia ni actualiza esta configuración.
        - **Ninguno**: como administrador, no se fuerza un certificado específico. Seleccione esta opción para que los usuarios puedan elegir su propio certificado.
        - **Credencial derivada**: use un certificado que se derive de la tarjeta inteligente de un usuario. Para más información, consulte [Uso de credenciales derivadas en Microsoft Intune](../protect/derived-credentials.md).
        - **Certificados**: se selecciona un perfil de certificado PKCS o SCEP existente que se usa para firmar los mensajes de correo electrónico.
      - **Permitir al usuario cambiar la configuración**: elija **Habilitar** para permitir que los usuarios cambien el certificado de cifrado. La opción **Deshabilitar** (predeterminada) evita que los usuarios cambien el certificado de cifrado y los obliga a usar el certificado configurado.

        Esta característica se aplica a:  
        - iOS 12 y versiones más recientes
        - IPadOS 12 y versiones más recientes

- **Cantidad de correo electrónico para sincronizar**: elija el número de días de correo electrónico que quiere sincronizar. También puede seleccionar **Ilimitado** para sincronizar todo el correo electrónico disponible.
- **Permitir que los mensajes se muevan a otras cuentas de correo electrónico**: **Habilitar** (valor predeterminado) permite a los usuarios mover los mensajes de correo electrónico entre las distintas cuentas que han configurado en sus dispositivos.
- **Permitir que el correo electrónico se envíe desde aplicaciones de terceros**: **Habilitar** (valor predeterminado) permite a los usuarios seleccionar este perfil como cuenta predeterminada para enviar correo electrónico. Permite que otras aplicaciones de terceros puedan abrir el correo en la aplicación de correo electrónico nativa (por ejemplo, para adjuntar archivos a los mensajes).
- **Sincronizar direcciones de correo electrónico usadas recientemente**: **Habilitar** (valor predeterminado) permite a los usuarios sincronizar con el servidor la lista de direcciones de correo electrónico que se han usado recientemente en el dispositivo.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](../device-profile-assign.md) y [supervise el estado](../device-profile-monitor.md).

Configure los valores de correo electrónico en dispositivos [Android](../email-settings-android.md), [Android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md) y [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
