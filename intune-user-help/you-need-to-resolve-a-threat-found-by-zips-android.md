---
title: Resolución de amenazas detectadas por Zimperium zIPS en Android
description: Obtenga información sobre cómo resolver las amenazas de seguridad y aplicaciones detectadas en el dispositivo Android.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 9ffbb656-93cd-4e0b-96c0-c5038cd2cf31
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d1a0583b18d34dbf8b942cf2a31656d3d61c1600
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72507777"
---
# <a name="resolve-a-threat-found-by-zimperium-zips"></a>Resolución de una amenaza detectada por Zimperium zIPS

Zimperium zIPS es un servicio de Mobile Threat Defender que identifica posibles amenazas en los dispositivos Android. Estas amenazas se notifican a la aplicación Portal de empresa y aparecen como problemas de no conformidad sin resolver. Si el dispositivo se identifica como no compatible, es posible que no pueda:

* Conectarse al correo electrónico corporativo
* Conectarse a la red Wi-Fi corporativa
* Conectarse a SharePoint Online
* Sincronizar los archivos corporativos con OneDrive
* Acceder a las aplicaciones de la empresa

En este artículo se describe cómo reconocer alertas de amenazas de Zimperium zIPS y qué hacer para resolverlas. 

## <a name="troubleshoot-virus-or-security-threat"></a>Solución de problemas de virus o amenazas de seguridad  
Cuando se detecta un virus o una amenaza de seguridad, Zimperium zIPS aplicará restricciones según las directivas de acceso de la organización. Las directivas de acceso de la empresa podrían impedirle acceder a la red, las aplicaciones y el correo electrónico del trabajo.  

Zimperium zIPS le pedirá que realice alguna acción para recuperar el acceso que ha perdido. Seleccione la amenaza y siga las instrucciones dentro de la aplicación para resolverla.

Como la aplicación se integra con el proveedor de MDM de la empresa, también verá una advertencia sobre el acceso restringido en la aplicación Portal de empresa. La advertencia le indica que abra Zimperium zIPS para solucionar el virus o la amenaza de seguridad.  

  ![Captura de pantalla de ejemplo de la página de dispositivo del Portal de empresa, en la que se muestra la advertencia de Zimperium zIPS.](./media/CP-lookout-virus-banner-1808.png)  

Seleccione el banner de advertencia que aparece debajo del dispositivo afectado. Zimperium zIPS se abrirá y le indicará cómo eliminar la amenaza.  

## <a name="resolve-an-app-threat"></a>Resolución de una amenaza de aplicación

Si instala una aplicación que se considera una amenaza para el dispositivo, recibirá una notificación en Zimperium zIPS. Si la aplicación afectada sigue en el dispositivo, no podrá acceder a los recursos de la empresa.  

Para resolverlo, seleccione la aplicación en la lista de amenazas de Zimperium zIPS. Después, siga las instrucciones en pantalla para quitar y desinstalar la aplicación.    

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980). 
