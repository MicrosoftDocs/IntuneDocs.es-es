---
title: Solución de problemas comunes de Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Solucione los problemas comunes de los Microsoft Intune Exchange Connector local.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: de365312a7d293527c3c83fbbd84ab55de41d530
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547669"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>Resolver problemas comunes con Intune Exchange Connector
 
Este artículo puede ayudar al administrador de Intune a resolver problemas comunes con el funcionamiento de Intune Exchange Connector.

Antes de empezar a solucionar problemas, consulte [solución de problemas del conector de Exchange local de Intune](troubleshoot-exchange-connector.md) para obtener información básica sobre el conector. Revise también los problemas comunes de la configuración del conector.

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>Un dispositivo Exchange ActiveSync no se detecta desde Exchange

Cuando no se detecta un dispositivo de Exchange ActiveSync desde Exchange, [supervise la actividad de Exchange Connector](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) para ver si el conector de Exchange se está sincronizando con el servidor de Exchange. Si no se ha producido ninguna sincronización desde que se unió el dispositivo, recopile los registros de sincronización y asócielo a una solicitud de soporte técnico. Si una sincronización completa o una sincronización rápida ha finalizado correctamente desde que se unió el dispositivo, compruebe los siguientes problemas:

- Asegúrese de que los usuarios tengan una licencia de Intune. De lo contrario, Exchange Connector no detectará sus dispositivos.

- Si la dirección SMTP principal del usuario es diferente de su nombre principal de usuario (UPN) en Azure Active Directory (Azure AD), el conector de Exchange no detectará los dispositivos para ese usuario. Corrija la dirección SMTP principal para resolver el problema.

- Si tiene servidores de buzones de Exchange 2010 y Exchange 2013 en su entorno, se recomienda que el conector de Exchange apunte a un servidor de acceso de cliente (CAS) de Exchange 2013. En caso contrario, si el conector de Exchange se ha configurado para comunicarse con un CAS de Exchange 2010, no detectará ningún dispositivo de usuario en Exchange 2013.

- En entornos de Exchange online dedicado, debe señalar el conector de Exchange a una CA de Exchange 2013 (no a una CA de Exchange 2010) en el entorno dedicado durante la configuración inicial. El conector solo se comunicará con una CA de Exchange 2013 cuando ejecute cmdlets de PowerShell.

## <a name="problems-with-the-notification-email-message"></a>Problemas con el mensaje de correo electrónico de notificación

Para admitir el acceso condicional para los buzones locales en dispositivos que no ejecutan Android Knox, asegúrese de que la inscripción de Intune comienza en el mensaje de correo electrónico "Introducción ahora" que envía Intune Exchange Connector. Al iniciar la inscripción desde el mensaje se garantiza que el dispositivo reciba un ActiveSyncID único en todas las plataformas (Exchange, Azure AD, Intune).

Es posible que un usuario no reciba el mensaje de correo electrónico de notificación porque:

- La cuenta de notificación se configuró incorrectamente.
- Error de detección automática de la cuenta de notificación.
- Error en la solicitud de servicios Web de Exchange (EWS) para enviar el mensaje de correo electrónico.

Revise las siguientes secciones para solucionar problemas de notificación de correo electrónico.

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>Compruebe la cuenta de notificación que recupera la configuración de detección automática.

1. Asegúrese de que el servicio de detección automática y EWS están configurados en los servicios de acceso de cliente de Exchange. Para obtener más información, consulte [servicios de acceso de cliente](https://docs.microsoft.com/Exchange/architecture/client-access/client-access) y [servicio de detección automática en Exchange Server](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019).

2. Compruebe que la cuenta de notificación cumple los requisitos siguientes:

   - La cuenta tiene un buzón de correo activo que se hospeda en el servidor local de Exchange.

   - El UPN de la cuenta coincide con la dirección SMTP.

3. Detección automática requiere un servidor DNS que tenga un registro DNS para **Autodiscover.SMTPdomain.com** (por ejemplo, Autodiscover.contoso.com) que apunte al servidor de acceso de cliente de Exchange. Para comprobar el registro, especifique el FQDN en lugar de *Autodiscover.SMTPdomain.com* y siga estos pasos:

   1. En un símbolo del sistema, escriba *nslookup*.

   2. Escriba *Autodiscover.SMTPdomain.com*. La salida debe ser similar a la siguiente imagen: ![resultados de nslookup](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
      )

   También puede probar el servicio de detección automática desde Internet en https://testconnectivity.microsoft.com. O pruébelo desde un dominio local mediante la herramienta Microsoft Connectivity Analyzer. Para obtener más información, vea [Microsoft Connectivity Analyzer Tool](https://docs.microsoft.com/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80)).


### <a name="check-autodiscovery"></a>Comprobar detección automática

Si se produce un error en la detección automática, realice los pasos siguientes:

1. [Configure un registro DNS de detección automática válido](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150)).

2. Codifique de forma rígida la dirección URL de EWS en el archivo de configuración de Intune Exchange Connector:

   1. Determine la dirección URL de EWS. La dirección URL de EWS predeterminada para Exchange es `https://<mailServerFQDN>/ews/exchange.asmx`, pero su dirección URL puede ser diferente. Póngase en contacto con el administrador de Exchange para comprobar la dirección URL correcta para su entorno.

   2. Edite el archivo *OnPremisesExchangeConnectorServiceConfiguration.xml*. De forma predeterminada, el archivo se encuentra en *%ProgramData%\Microsoft\Windows Intune Exchange Connector* en el equipo que ejecuta el conector de Exchange. Abra el archivo en un editor de texto y, a continuación, cambie la siguiente línea para que refleje la dirección URL de EWS para su entorno: `<ExchangeWebServiceURL>https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`

3. Guarde el archivo y, después, reinicie el equipo o el servicio Microsoft Intune Exchange Connector.

>[!NOTE]
> En esta configuración, Intune Exchange Connector deja de usar detección automática y, en su lugar, se conecta directamente a la dirección URL de EWS.

## <a name="next-steps"></a>Pasos siguientes

Para obtener ayuda con errores específicos, pruebe a [resolver errores comunes para Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Para obtener soporte técnico o para obtener ayuda de la comunidad de Intune:

- Vea [obtener soporte técnico](../fundamentals/get-support.md) para usar la consola de Intune para solucionar el problema o para abrir un caso de soporte técnico con Microsoft.
- Publique su problema en los [foros de Microsoft Intune](https://social.technet.microsoft.com/Forums/home?forum=microsoftintuneprod).