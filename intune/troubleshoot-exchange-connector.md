---
title: Solucionar problemas de Exchange Connector
titleSuffix: Microsoft Intune
description: Solucione los problemas relacionados con Intune On-Premises Exchange Connector.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/18/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea3ae66a32353b4aa6c782b13e6a587ee1f4464e
ms.sourcegitcommit: 1d4aec7b79c70d35ec3fc29df6ff9c6a1403412e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68491819"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>Solucionar problemas de Intune On-Premises Exchange Connector

En este artículo se describe cómo solucionar los problemas relacionados con Intune On-Premises Exchange Connector.

## <a name="steps-for-checking-the-connector-configuration"></a>Pasos para comprobar la configuración de Connector 

Compruebe la [instalación de Intune On-Premises Exchange Connector](exchange-connector-install.md) para asegurarse de que el conector está configurado correctamente. A continuación se muestran algunos problemas comunes. Después de realizar las correcciones, vea si se ha resuelto el problema.

- En el cuadro de diálogo de Microsoft Intune Exchange Connector, asegúrese de que ha especificado una cuenta de usuario que tiene los permisos adecuados para ejecutar los [cmdlets de Windows PowerShell Exchange requeridos](exchange-connector-install.md#exchange-cmdlet-requirements).
- Habilite las notificaciones y especifique una cuenta de notificación.
- Al configurar Exchange Connector, especifique un servidor de acceso de cliente (CAS) que sea lo más cercano posible al servidor que hospeda Exchange Connector. La latencia de comunicación entre las entidades de certificación y Exchange Connector podría provocar retrasos de detección del dispositivo, especialmente cuando se utiliza Exchange Online dedicado.
- El acceso de un usuario con un dispositivo recién inscrito podría retrasarse hasta que el conector de Exchange se sincronice con el CAS de Exchange. Una sincronización completa se lleva a cabo una vez al día y una sincronización diferencial (rápida) se realiza varias veces al día.  También puede [forzar manualmente una sincronización rápida o una sincronización completa](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) para minimizar los retrasos.
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Dispositivo Exchange ActiveSync no detectado desde Exchange
[Supervise la actividad de Exchange Connector](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support) para ver si se está sincronizando con el servidor de Exchange. Si se ha realizado una sincronización completa o una sincronización rápida correctamente desde que se unió el dispositivo, puede buscar otros posibles problemas, que se enumeran a continuación. Si no ha realizado ninguna sincronización, recopile los registros de sincronización y adjúntelos a una solicitud de soporte técnico.

- Asegúrese de que los usuarios tienen una licencia de Intune, de lo contrario, Exchange Connector no detectará sus dispositivos.
- Si la dirección SMTP principal de un usuario es diferente de su UPN en Azure Active Directory (Azure AD), Exchange Connector no detectará los dispositivos para ese usuario. Corrija la dirección SMTP principal para resolver el problema.
- Si tiene servidores de buzones de Exchange 2010 y Exchange 2013 en su entorno, se recomienda que apunte Exchange Connector a un CAS de Exchange 2013. En caso contrario, si Exchange Connector se ha configurado para comunicarse con un CAS de Exchange 2010, Exchange Connector no detectará ningún dispositivo de usuarios de Exchange 2013. 
- Para entornos de Exchange Online dedicado, debe dirigir Exchange Connector a un CAS de Exchange 2013 (no de Exchange 2010) en el entorno dedicado durante la instalación inicial, ya que el conector se comunicará únicamente con este CAS al ejecutar los cmdlets de Powershell.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Uso de Powershell para obtener más datos acerca de problemas de Exchange Connector
- Para obtener una lista de todos los dispositivos móviles para un buzón, use`Get-ActiveSyncDeviceStatistics -mailbox mbx`
- Para obtener una lista de direcciones SMTP para un buzón, use`Get-Mailbox -Identity user | select emailaddresses | fl`
- Para información detallada sobre el estado del acceso de un dispositivo, use `Get-CASMailbox <upn> | fl`.

## <a name="next-steps"></a>Pasos siguientes
Si esta información no le es de ayuda, también puede [obtener soporte técnico de Microsoft Intune](get-support.md).
