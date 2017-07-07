---
title: Conector Mobile Threat Defense de Skycure
description: "Proteja el acceso a los recursos de la empresa en función del riesgo del dispositivo, la red y la aplicación con el conector de Mobile Threat Defense de Skycure e Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7a004e6c-604a-448c-bfb8-cfda63749f5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d0b401babf356e44479229c3bea27c956926a6f9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="skycure-mobile-threat-defense-connector"></a>Conector de Mobile Threat Defense de Skycure

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Puede controlar el acceso desde dispositivos móviles a recursos corporativos en función de la evaluación de riesgos efectuada por Skycure, una solución de defensa contra amenazas móviles integrada con Microsoft Intune. El riesgo se evalúa según la telemetría recopilada de dispositivos que ejecutan Skycure, que incluye:

-   Defensa física

-   Defensa de red

-   Defensa de aplicaciones

-   Defensa de vulnerabilidades

Se pueden configurar directivas de acceso condicional según la evaluación de riesgos de Skycure habilitada mediante las directivas de cumplimiento de dispositivos de Intune, que puede usar para permitir o bloquear dispositivos que no cumplan los requisitos para que no accedan a recursos corporativos en función de las amenazas detectadas.

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>¿Cómo ayudan Intune y Skycure a proteger los recursos de la empresa?

La aplicación móvil de Skycure para Android o iOS capta el sistema de archivos, la pila de red y la telemetría de aplicaciones y dispositivos cuando está disponible. Después lo envía al servicio en la nube de Skycure para evaluar el riesgo del dispositivo frente a las amenazas móviles.

La directiva de cumplimiento de dispositivos de Intune incluye una regla para Mobile Threat Defense de Skycure que se basa en la evaluación del riesgo de Skycure. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó.

Si se detecta que el dispositivo no cumple con la directiva, se bloquea el acceso a recursos como Exchange Online y SharePoint Online. Los usuarios de dispositivos bloqueados reciben los pasos de la aplicación móvil de Skycure para resolver el problema y volver a obtener acceso a los recursos corporativos.

Intune admite dos modos de integración con Skycure:

-   **Configuración básica**, que es un modo de solo lectura que permite la visibilidad de Skycure para dispositivos en Intune.

-   **Integración completa**, que permite a Skycure informar de riesgos para dispositivos y detalles del incidente de seguridad a Intune.

## <a name="sample-scenarios"></a>Escenarios de ejemplo

Estos son algunos escenarios frecuentes:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Control del acceso basado en amenazas de aplicaciones malintencionadas

Cuando se detectan aplicaciones malintencionadas, como malware, en los dispositivos, puede bloquearlos de la siguiente manera hasta que la amenaza se resuelva:

-   Conectarse al correo electrónico corporativo

-   Sincronizar los archivos corporativos mediante la aplicación OneDrive para el trabajo

-   Acceder a las aplicaciones de empresa

**Bloquear cuando se detectan aplicaciones malintencionadas:**

![Aplicaciones malintencionadas detectadas](../media/mtp/skycure-arch-1.png)

**Acceso concedido tras la solución:**

![Aplicaciones malintencionadas detectadas y acceso concedido](../media/mtp/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Control del acceso basado en amenazas a la red

Detecte amenazas para la red, como **ataques de tipo Man-in-the-middle**, y proteja el acceso a las redes Wi-Fi según el riesgo del dispositivo.

**Bloquear el acceso de red a través de Wi-Fi:**

![Bloquear el acceso de red a través de Wi-Fi](../media/mtp/skycure-arch-3.png)

**Acceso concedido tras la solución:**

![Acceso concedido tras la solución](../media/mtp/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Control del acceso a SharePoint Online basado en amenazas a la red

Detecte amenazas para la red, como **ataques de tipo Man-in-the-middle**, y evite la sincronización de archivos corporativos según el riesgo del dispositivo.

**Bloqueo de SharePoint Online cuando se detectan amenazas a la red:**

![Bloqueo de SharePoint Online cuando se detectan amenazas a la red](../media/mtp/skycure-arch-5.png)

**Acceso concedido tras la solución:**

![Acceso concedido tras la solución](../media/mtp/skycure-arch-6.png)

## <a name="supported-platforms"></a>Plataformas compatibles

-   **Android 4.1 y versiones posteriores**

-   **iOS 8 y versiones posteriores**

## <a name="pre-requisites"></a>Requisitos previos

-   Azure Active Directory Premium

-   Suscripción a Microsoft Intune

-   Suscripción a Mobile Threat Defense de Skycure

Para obtener más información, consulte el [sitio web de Skycure](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Pasos siguientes

Estos son los pasos que debe realizar para integrar Intune con Skycure:

1.  [Configuración de Skycure para utilizar el inicio de sesión único (SSO) de Azure Active Directory](/intune-classic/deploy-use/configure-skycure-to-use-azure-active-directory-single-sign-on)

2.  [Descarga de la directiva de configuración de la aplicación de iOS de Skycure](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)

3.  [Adición de aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)

4.  [Implementación de aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)

5.  [Configuración de la integración de Skycure con Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

6.  [Habilitación de Mobile Threat Defense de Skycure en Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

7.  [Creación de la directiva de cumplimiento de Mobile Threat Defense de Skycure en Intune](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
