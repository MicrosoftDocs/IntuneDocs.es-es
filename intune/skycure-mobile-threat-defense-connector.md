---
title: Conector de Skycure con Intune
titlesuffix: Azure portal
description: "Integración del conector de Skycure con Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c8be5d271bfff84ec440b25724ca2101ec7f224d
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2018
---
# <a name="skycure-mobile-threat-defense-connector"></a>Conector de Mobile Threat Defense de Skycure

Puede controlar el acceso desde dispositivos móviles a recursos corporativos en función de la evaluación de riesgos efectuada por Skycure, una solución de defensa contra amenazas móviles integrada con Microsoft Intune. El riesgo se evalúa según la telemetría recopilada de dispositivos que ejecutan Skycure, que incluye:

-   Defensa física

-   Defensa de red

-   Defensa de aplicaciones

-   Defensa de vulnerabilidades

Se pueden configurar directivas de acceso condicional según la evaluación de riesgos de Skycure habilitada mediante las directivas de cumplimiento de dispositivos de Intune. Puede usar dichas directivas para permitir o bloquear dispositivos que no cumplan los requisitos y, así, evitar que accedan a recursos corporativos en función de las amenazas detectadas.

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>¿Cómo ayudan Intune y Skycure a proteger los recursos de la empresa?

La aplicación móvil de Skycure para Android o iOS capta el sistema de archivos, la pila de red y la telemetría de aplicaciones y dispositivos cuando está disponible. Después lo envía al servicio en la nube de Skycure para evaluar el riesgo del dispositivo frente a las amenazas móviles.

La directiva de cumplimiento de dispositivos de Intune incluye una regla para Mobile Threat Defense de Skycure que se basa en la evaluación del riesgo de Skycure. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó.

Si se detecta que el dispositivo no es conforme, se bloqueará el acceso a recursos como Exchange Online y SharePoint Online. Los usuarios de dispositivos bloqueados reciben los pasos de la aplicación móvil de Skycure para resolver el problema y volver a obtener acceso a los recursos corporativos.

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

![Aplicaciones malintencionadas detectadas](./media/skycure-arch-1.png)

**Acceso concedido tras la corrección:**

![Aplicaciones malintencionadas detectadas y acceso concedido](./media/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Control del acceso basado en amenazas a la red

Detecte amenazas para la red, como **ataques de tipo Man-in-the-middle**, y proteja el acceso a las redes Wi-Fi según el riesgo del dispositivo.

**Bloquear el acceso de red a través de Wi-Fi:**

![Bloquear el acceso de red a través de Wi-Fi](./media/skycure-arch-3.png)

**Acceso concedido tras la corrección:**

![Acceso concedido tras la solución](./media/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Control del acceso a SharePoint Online basado en amenazas a la red

Detecte amenazas para la red, como **ataques de tipo Man-in-the-middle**, y evite la sincronización de archivos corporativos según el riesgo del dispositivo.

**Bloqueo de SharePoint Online cuando se detectan amenazas a la red:**

![Bloqueo de SharePoint Online cuando se detectan amenazas a la red](./media/skycure-arch-5.png)

**Acceso concedido tras la corrección:**

![Acceso concedido tras la solución](./media/skycure-arch-6.png)

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

- [Configuración de la integración de Skycure con Intune](skycure-mtd-connector-integration.md)

- [Agregar y asignar aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Creación de la directiva de cumplimiento de dispositivos de Skycure con Intune](mtd-device-compliance-policy-create.md)

- [Habilitación del conector MTD de Skycure en Intune](mtd-connector-enable.md)
