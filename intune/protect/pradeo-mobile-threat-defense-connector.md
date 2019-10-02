---
title: Conector Mobile Threat Defense de Pradeo con Intune
titleSuffix: Intune on Azure
description: Aprenda a integrar Intune con el conector Mobile Threat Defense de Pradeo para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1e881886a060646af700fa7affe4b65b5685087
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726900"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>Conector Mobile Threat Defense de Pradeo con Intune

Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Pradeo, una solución de defensa contra amenazas móviles (MTD) integrada en Microsoft Intune. El riesgo se evalúa en función de la telemetría recopilada de los dispositivos que ejecutan la aplicación Pradeo.

Se pueden configurar directivas de acceso condicional según la evaluación de riesgos de Pradeo habilitada mediante las directivas de cumplimiento de dispositivos de Intune. Puede usar dichas directivas para permitir o bloquear dispositivos que no cumplan los requisitos y, de este modo, evitar que estos accedan a recursos corporativos en función de las amenazas detectadas.

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>¿Cómo ayudan Intune y Pradeo a proteger los recursos de la empresa?

La aplicación Pradeo para iOS y Android capta el sistema de archivos, la pila de red, el dispositivo y la telemetría de aplicaciones, cuando está disponible y, después, envía los datos de telemetría al servicio en la nube de Pradeo para evaluar el riesgo del dispositivo frente a las amenazas móviles.

La directiva de cumplimiento de dispositivos de Intune incluye una regla para Mobile Threat Defense de Pradeo que se basa en la evaluación del riesgo de Pradeo. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó. Si se detecta que el dispositivo no cumple con la directiva, se bloqueará el acceso de los usuarios a los recursos corporativos, como Exchange Online y SharePoint Online. Los usuarios también reciben los pasos de la aplicación Pradeo instalada en sus dispositivos para resolver el problema y volver a obtener acceso a los recursos corporativos.

## <a name="sample-scenarios"></a>Escenarios de ejemplo

Estos son algunos casos más frecuentes.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Control del acceso basado en amenazas de aplicaciones malintencionadas

Cuando se detectan aplicaciones malintencionadas, como el malware, en los dispositivos, puede bloquear las siguientes acciones hasta resolver la amenaza:

- Conectarse al correo electrónico corporativo

- Sincronizar los archivos corporativos mediante la aplicación OneDrive para el trabajo

- Acceder a las aplicaciones de empresa

**Bloquear cuando se detectan aplicaciones malintencionadas:**

![Imagen conceptual de aplicaciones malintencionadas detectadas](./media/pradeo-mobile-threat-defense-connector/pradeo_maliciousapps_blocked.png)

**Acceso concedido tras la corrección:**

![Aplicaciones malintencionadas detectadas y acceso concedido](./media/pradeo-mobile-threat-defense-connector/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Control del acceso basado en amenazas a la red

Detecte amenazas para la red, por ejemplo, ataques de tipo **Man in the middle**, y proteja el acceso a las redes Wi-Fi según el riesgo del dispositivo.

**Bloquear el acceso de red a través de Wi-Fi:**

![Bloquear el acceso de red a través de Wi-Fi](./media/pradeo-mobile-threat-defense-connector/pradeo_network_wifi_blocked.png)

**Acceso concedido tras la corrección:**

![Imagen conceptual de acceso concedido tras la corrección](./media/pradeo-mobile-threat-defense-connector/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Control del acceso a SharePoint Online basado en amenazas a la red

Detecte amenazas para la red, por ejemplo, ataques de tipo **Man in the middle**, y evite la sincronización de archivos corporativos según el riesgo del dispositivo.

**Bloqueo de SharePoint Online cuando se detectan amenazas a la red:**

![Bloqueo de SharePoint Online cuando se detectan amenazas a la red](./media/pradeo-mobile-threat-defense-connector/pradeo_network_spo_blocked.png)

**Acceso concedido tras la corrección:**

![Imagen conceptual de acceso concedido tras la corrección para el ejemplo de SharePoint](./media/pradeo-mobile-threat-defense-connector/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Plataformas compatibles

- **Android 4.0.3 y versiones posteriores**

- **iOS 7 y versiones posteriores**

## <a name="prerequisites"></a>Requisitos previos

- Azure Active Directory Premium

- Suscripción a Microsoft Intune

- Pradeo Security para la suscripción a Mobile Threat Defense

  - Para obtener más información, vea el [sitio web de Pradeo](https://www.pradeo.com/en-US/mobile-threat-protection).

## <a name="next-steps"></a>Pasos siguientes

- [Integración de Pradeo con Intune](pradeo-mtd-connector-integration.md)

- [Configuración de las aplicaciones de Pradeo](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Creación de una directiva de cumplimiento de dispositivos de Pradeo](mtd-device-compliance-policy-create.md)

- [Activación del conector MTD de Pradeo](mtd-connector-enable.md)
