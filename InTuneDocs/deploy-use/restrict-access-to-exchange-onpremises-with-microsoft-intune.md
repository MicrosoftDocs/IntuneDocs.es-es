---
title: "Proteger el acceso de correo electrónico a Exchange local | Microsoft Docs"
description: "Proteja y controle el acceso al correo electrónico de empresa en Exchange local con el acceso condicional."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: 24d000f650cafffc0c998ef80ba52bd06b56afe2


---

# <a name="protect-email-access-to-exchange-on-premises-and-legacy-exchange-online-dedicated-with-intune"></a>Proteger el acceso de correo electrónico a Exchange local y Exchange Online dedicado heredado con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

> [!NOTE]
> Si tiene un entorno de Exchange Online dedicado y necesita averiguar si es la configuración nueva o heredada, póngase en contacto con su administrador de cuentas.


Para controlar el acceso de correo electrónico a Exchange local o al entorno heredado de Exchange Online dedicado, puede configurar el acceso condicional para Exchange local con Microsoft Intune.
Para más información sobre cómo funciona el acceso condicional, consulte el artículo [Proteger el acceso al correo electrónico y los servicios de O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

**Antes** de configurar el acceso condicional, debe comprobar lo siguiente:

-   Su versión de Exchange debe ser **Exchange 2010 o posterior**. Se admiten las matrices del servidor de acceso de cliente (CAS) de Exchange Server.

-   Debe usar **Exchange Connector local** que conecta [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] con Exchange local. Esto le permite administrar dispositivos a través de la consola de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Para obtener detalles sobre Connector, consulte [Intune on-premises Exchange connector (Intune Exchange Connector local)](intune-on-premises-exchange-connector.md).

    -   La versión de Exchange Connector local que tiene disponible en la consola de Intune es específica de su inquilino de Intune y no puede usarla con otro inquilino. Le recomendamos que también se asegure de que la versión de Exchange Connector del inquilino esté instalada **en un solo equipo**.

        Puede descargar el conector de la consola de administración de Intune. Para ver un tutorial sobre cómo configurar Exchange Connector local, consulte [Configure Exchange on-premises connector for on-premises or hosted Exchange (Configurar Exchange Connector local para Exchange local u hospedado)](intune-on-premises-exchange-connector.md).

    -   Puede instalar el conector en cualquier equipo siempre y cuando este pueda comunicarse con el servidor de Exchange.

    -   El conector es compatible con el **entorno de CAS de Exchange**. Técnicamente puede instalar el conector en el servidor de CAS de Exchange directamente si quiere. En cambio, no lo recomendamos porque aumenta la carga en el servidor. Cuando configure el conector, debe permitir que se comunique con uno de los servidores de CAS de Exchange.

-   Debe configurar **Exchange ActiveSync** con autenticación basada en certificados o con la entrada de credenciales de usuario.

Cuando configura directivas de acceso condicional y se aplican a un usuario, antes de que este pueda conectarse a su correo electrónico, el **dispositivo** que usa debe ser:

-  Un PC unido a un dominio o estar **inscrito** con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-  Debe estar **registrado en Azure Active Directory**. Además, el identificador de Exchange ActiveSync del cliente debe registrarse con Azure Active Directory.

  El servicio Registro de dispositivos de Azure Active Directory se activa automáticamente para los clientes de Intune y Office 365. Los clientes que ya hayan implementado el servicio Registro de dispositivos de ADFS no podrán ver los dispositivos registrados en la instancia local de Active Directory. **Esto no se aplica a equipos de Windows ni a dispositivos Windows Phone.**

-   Debe **cumplir** todas las directivas de cumplimiento de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] que se han implementado en el dispositivo.

En el diagrama siguiente se muestra el flujo que usan las directivas de acceso condicional de Exchange local para evaluar si se permitirá o se bloqueará el acceso a los dispositivos.

![Diagrama que muestra los puntos de decisión que determinan si un dispositivo puede tener acceso a Exchange local o si se bloquea](../media/ConditionalAccess8-2.png)

Si no se cumple una directiva de acceso condicional, el usuario ve uno de los mensajes siguientes cuando inicia sesión:

- Si el dispositivo no está inscrito con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o no está registrado en Azure Active Directory, se muestra un mensaje con instrucciones sobre cómo instalar la aplicación de portal de empresa, inscribir el dispositivo y activar el correo electrónico. Este proceso también asocia el identificador de Exchange ActiveSync del dispositivo con el registro del dispositivo en Azure Active Directory.

-   Si el dispositivo no es compatible, se muestra un mensaje que dirige al usuario a la aplicación de portal de empresa o al sitio web del portal de empresa de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], donde puede encontrar información sobre el problema y sobre cómo resolverlo.

## <a name="support-for-mobile-devices"></a>Compatibilidad con dispositivos móviles
No se admite lo siguiente:
-   Windows Phone 8.1 y versiones posteriores.

-   La aplicación de correo electrónico nativa de iOS.

-   Clientes de correo de Exchange ActiveSync, como Gmail en Android 4 o versiones posteriores.
- Clientes de correo de Exchange ActiveSync en **dispositivos Android for Work**: solo se admiten las aplicaciones **Gmail** y **Nine Work** en el **perfil de trabajo** en los dispositivos Android for Work. Para que el acceso condicional funcione con Android for Work, debe implementar un perfil de correo electrónico para la aplicación Gmail o Nine Work, y también implementar esas aplicaciones como una instalación obligatoria. 

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

> [!NOTE]
> La aplicación Microsoft Outlook para iOS y Android no es compatible.

## <a name="support-for-pcs"></a>Compatibilidad para equipos
Se admite lo siguiente:
-   La aplicación **Correo** en Windows 8.1 y versiones posteriores (cuando el PC se inscribe con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).

##  <a name="configure-a-conditional-access-policy"></a>Configurar una directiva de acceso condicional

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Directiva** > **Acceso condicional** > **Directiva de Exchange local**.
![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2.  Configure la directiva con la configuración que necesite: ![Captura de pantalla de la página de la directiva de Exchange local](../media/IntuneSA5bExchangeOnPremPolicy.png)

  - **Bloquear el acceso a Exchange local a las aplicaciones de correo electrónico si el dispositivo no cumple los requisitos o no está inscrito en Microsoft Intune**: al seleccionar esta opción, se bloqueará el acceso a los servicios de Exchange a los dispositivos que no están administrados por [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o que no son compatibles con una directiva de cumplimiento.

  - **Sustitución de la regla predeterminada. Permitir siempre que los dispositivos inscritos y compatibles accedan a Exchange**: cuando se selecciona esta opción, los dispositivos inscritos en Intune y que cumplen con las directivas de cumplimiento pueden tener acceso a Exchange.
  Esta regla invalida la **Regla predeterminada**, lo que significa que aunque configure la **Regla predeterminada** para poner el acceso en cuarentena o bloquearlo, los dispositivos inscritos y compatibles aún podrán acceder a Exchange.

  - **Grupos de destino**: seleccione los grupos de usuarios de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] que deben inscribir su dispositivo con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para poder acceder a Exchange.

  - **Grupos exentos**: seleccione los grupos de usuarios de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] exentos de la directiva de acceso condicional. Los usuarios de esta lista están exentos aunque estén incluidos también en la lista de **Grupos de destino**.

  - **Excepciones de plataforma**: pulse **Agregar regla** para configurar una regla que defina los niveles de acceso para las familias y los modelos de dispositivos móviles especificados. Dado que estos dispositivos pueden ser de cualquier tipo, también puede configurar tipos de dispositivo que no sean compatibles con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

  - **Regla predeterminada**: en el caso de un dispositivo que no esté cubierto por ninguna de las otras reglas, puede permitirle el acceso a Exchange, bloquearlo o ponerlo en cuarentena. Al establecer la regla para permitir el acceso a los dispositivos que están inscritos y que cumplen con las directivas, se concede acceso automático al correo electrónico a los dispositivos iOS, Windows y Samsung KNOX. El usuario no tiene que realizar ningún proceso para acceder a su correo electrónico.

        En los dispositivos Android que no ejecutan Samsung KNOX, los usuarios reciben un correo electrónico de cuarentena con un tutorial detallado que les ayudará a comprobar la inscripción y el cumplimiento para poder tener acceso al correo electrónico. Si establece la regla para bloquear el acceso o establecer una cuarentena para los dispositivos, todos los dispositivos se bloquean al obtener acceso a Exchange, independientemente de si están ya inscritos en Intune o no. Para evitar que los dispositivos inscritos y compatibles a las directivas se vean afectados por esta regla, active la casilla **Invalidación de regla predeterminada**.
>[!TIP]
>Si se pretende bloquear todos los dispositivos antes de conceder acceso al correo electrónico, elija las opciones de bloqueo de regla de acceso o la regla de cuarentena. La regla predeterminada se aplica a todos los tipos de dispositivo, por lo que los tipos de dispositivo que configure como excepciones de la plataforma que no sean compatibles con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] también se verán afectados.

  - **Notificación de usuario**: además del correo electrónico de notificación que envía Exchange, Intune envía un correo electrónico que incluye los pasos para desbloquear el dispositivo. Puede editar el mensaje predeterminado para personalizarlo según sus necesidades. En el caso de que el dispositivo del usuario se bloquee antes de que reciba el correo electrónico de notificación de Intune que contiene las instrucciones de corrección (este correo electrónico se envía al buzón de Exchange del usuario), puede usar un dispositivo desbloqueado u otro método para acceder a Exchange y ver el mensaje.

        This is especially true when the **Default Rule** is set to block or quarantine. In this case, the user has to go to their app store, download the Microsoft Company Portal app, and enroll their device. This is applicable to iOS, Windows, and Samsung KNOX devices. For devices that don't run Samsung KNOX, you need to send the quarantine email to an alternate email account. The user has to copy the email to their blocked device to complete the enrollment and compliance process.
  > [!NOTE]
  > Para que Exchange pueda enviar el correo electrónico de notificación, debe especificar la cuenta que se usa para enviarlo.
  >
  > Para obtener detalles, vea [Configure Exchange on-premises connector for on-premises or hosted Exchange (Configurar Exchange Connector local para Exchange local u hospedado)](intune-on-premises-exchange-connector.md).

3.  Cuando termine, elija **Guardar**.

-   No es necesario implementar la directiva de acceso condicional, ya que surte efecto inmediatamente.

-   Después de que un usuario configure un perfil de Exchange ActiveSync, puede tardar de una a tres horas en bloquear el dispositivo (si no está administrado por [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).

-   Si un usuario bloqueado luego inscribe el dispositivo con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y corrige la no conformidad, el acceso al correo electrónico se desbloqueará en dos minutos.

-   Si el usuario anula la inscripción de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], puede tardar de una a tres horas en desbloquear el dispositivo.

**Para ver algunos escenarios de ejemplo sobre la configuración de la directiva de acceso condicional para proteger el acceso a los dispositivos, vea [Proteger el acceso al correo electrónico con Microsoft Intune: escenarios de ejemplo](restrict-email-access-example-scenarios.md).**

## <a name="next-steps"></a>Pasos siguientes
-   [Proteger el acceso a SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

-   [Proteger el acceso a Skype Empresarial Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)



<!--HONumber=Jan17_HO2-->


