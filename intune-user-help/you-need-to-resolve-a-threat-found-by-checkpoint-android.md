---
title: Resolución de amenazas detectadas por SandBlast Mobile Protect para Android | Microsoft Docs
description: Obtenga información sobre cómo resolver una amenaza detectada por SandBlast Mobile Protect para Android.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 449c34ec-2d94-4c7f-8691-a5200efee3cb
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fdf06339435d0605c6ac84d82dc2ab6c643b2df
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55839029"
---
# <a name="resolve-a-threat-found-by-sandblast-mobile-protect"></a>Resolver una amenaza detectada por SandBlast Mobile Protect

La aplicación SandBlast Mobile Protect es un servicio de Mobile Threat Defender que identifica posibles amenazas en los dispositivos Android. Informa de las amenazas que después puede ver desde la aplicación de Portal de empresa. Las amenazas aparecen en la aplicación como problemas de no conformidad sin resolver. Mientras estas amenazas estén presentes, es posible que no pueda:   

* Conectarse al correo electrónico corporativo
* Conectarse a la red Wi-Fi corporativa
* Conectarse a SharePoint Online
* Sincronizar los archivos corporativos con OneDrive
* Acceder a las aplicaciones de la empresa

En este artículo se describe cómo reconocer alertas de amenazas de Sandblast Mobile Protect y qué hacer para resolverlas.  

## <a name="troubleshoot-virus-or-security-threat"></a>Solución de problemas de virus o amenazas de seguridad  
Si se detecta un virus o una amenaza de seguridad, la aplicación SandBlast Mobile Protect actuará según las directivas de acceso de la organización. Las directivas de acceso de la empresa podrían impedirle acceder a la red, las aplicaciones y el correo electrónico del trabajo.  

![Captura de pantalla de ejemplo de un mensaje de alerta de la aplicación SEP Mobile.](./media/skycure-list-of-potential-issues-android.png)  

Pero SandBlast Mobile Protect también le pedirá que realice alguna acción para recuperar el acceso que ha perdido. Seleccione la amenaza y siga las instrucciones dentro de la aplicación para resolverla.

Como la aplicación se integra con el proveedor de MDM de la empresa, también verá una advertencia sobre el acceso restringido en la aplicación Portal de empresa. La advertencia le indica que abra Sandblast Mobile Protect para solucionar el virus o la amenaza de seguridad.

  ![Captura de pantalla de ejemplo de la página de dispositivo del Portal de empresa, en la que se muestra la advertencia de SandBlast Mobile Protect.](./media/CP-lookout-virus-banner-1808.png)  

## <a name="troubleshoot-an-app-threat"></a>Solución de una amenaza de aplicación  

Si instala una aplicación que se considera una amenaza para el dispositivo, recibirá una notificación en SandBlast Mobile Protect. Si la aplicación afectada sigue en el dispositivo, no podrá acceder a los recursos de la empresa.  

Para resolverlo, seleccione la aplicación en la lista de amenazas de SandBlast Mobile Protect. Después, siga las instrucciones para quitar y desinstalar la aplicación.     

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
