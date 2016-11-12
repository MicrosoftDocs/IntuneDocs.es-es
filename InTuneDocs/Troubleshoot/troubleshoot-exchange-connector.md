---
title: Solucionar problemas de Exchange Connector | Microsoft Intune
description: Solucione los problemas relacionados con Intune Exchange Connector.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: f6b673d05e385ddfe6ef3d3e63cf857439b164de


---

# Solucionar problemas con Exchange Connector
En este tema se describe cómo solucionar problemas que pueden estar relacionados con Intune Exchange Connector.

## Pasos para comprobar la configuración de Connector 

Compruebe la configuración de Exchange Connector y, a continuación, vea si se ha resuelto el problema.

- Asegúrese de especificar una cuenta de notificación en la instalación inicial de Exchange Connector.
- La cuenta de servicio de Exchange Connector debe tener los permisos adecuados para ejecutar los cmdlets de PowerShell utilizados por Exchange Connector.
- Al configurar Exchange Connector, especifique un servidor de acceso de cliente (CAS) que sea lo más cercano posible al servidor que hospeda Exchange Connector. La latencia de comunicación entre las entidades de certificación y Exchange Connector podría provocar retrasos de detección del dispositivo, especialmente cuando se utiliza Office 365 dedicado.
- Tenga en cuenta que hay un lapso de tiempo entre sincronizaciones de Exchange Connector con CAS de Exchange. Una sincronización completa se lleva a cabo una vez al día y una sincronización diferencial (rápida) se realiza cada dos horas. Es probable que un usuario con un dispositivo recién inscrito experimente un retraso a al obtener acceso.
- 
## Dispositivo Exchange ActiveSync no detectado desde Exchange
Compruebe si Exchange Connector se está sincronizando con el servidor Exchange. Para ello, busque los registros de una sincronización completa o una sincronización diferencial. Consulte Registros de Exchange Connector. Si se han completado correctamente una sincronización completa o una sincronización diferencial desde que se unió el dispositivo, ha eliminado esto como origen del problema. Si no ha realizado ninguna sincronización, recopile los registros de sincronización y adjúntelos a su solicitud de soporte técnico.

- Si un usuario no tiene una licencia de Intune, Exchange Connector no detectará sus dispositivos.
- Si la dirección SMTP principal de un usuario es diferente de su UPN en AAD, Exchange Connector no detectará los dispositivos para ese usuario de Intune/AAD. Solucione la dirección SMTP principal.
- Si la directiva CAS con la que Exchange Connector se comunica durante un ciclo de detección es una directiva CAS de Exchange 2010 y dispone de servidores de buzón de Exchange 2010 y 2013, Exchange Connector no detectará los dispositivos de los usuarios de Exchange 2013. Para resolver este problema, configure Exchange Connector para que señale a una directiva CAS de Exchange 2013.  Aunque este problema se refiere principalmente a topologías dedicadas a O365, seguimos recomendando que apunte a una directiva CAS de Exchange 2013 en otras topologías como práctica recomendada.
- Para entornos de Exchange dedicados (O365 dedicado), debe dirigir Exchange Connector a una directiva CAS de Exchange 2013 (no 2010) en el entorno dedicado durante la instalación inicial, ya que se comunicará únicamente con esta directiva CAS al ejecutar los cmdlets de Powershell.


## Uso de Powershell para obtener más datos acerca de problemas de Exchange Connector
- Para obtener una lista de todos los dispositivos móviles para un buzón de correo, use Get-ActiveSyncDeviceStatistics -mailbox mbx
- Para obtener una lista de direcciones SMTP para un buzón de correo, use Get-Mailbox -Identity user | select emailaddresses | fl.
- Para obtener información detallada sobre el estado del acceso de un dispositivo, use Get-CASMailbox <upn> | fl

### Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).



<!--HONumber=Oct16_HO4-->


