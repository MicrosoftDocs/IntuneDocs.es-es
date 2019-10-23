---
title: Conector Mobile Threat Defense de Better Mobile con Intune
titleSuffix: Intune on Azure
description: Configure el conector Mobile Threat Defense de Better Mobile con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a52636a140778f6e78bfe081cda40b36ef2354f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509643"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>Conector Mobile Threat Defense de Better Mobile con Intune

Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Better Mobile, una solución de Mobile Threat Defense (MTD) integrada en Microsoft Intune. El riesgo se evalúa en función de la telemetría recopilada de los dispositivos que ejecutan la aplicación Better Mobile.

Se pueden configurar directivas de acceso condicional según la evaluación de riesgos de Better Mobile habilitada mediante las directivas de cumplimiento de dispositivos de Intune. Puede usar dichas directivas para permitir o bloquear dispositivos que no cumplan los requisitos y, así, evitar que accedan a recursos corporativos en función de las amenazas detectadas.

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>¿Cómo ayudan Intune y Better Mobile a proteger los recursos de la empresa?

La aplicación móvil Better Mobile se instala y se ejecuta en dispositivos móviles. Esta aplicación captura el sistema de archivos, la pila de red, el dispositivo y la telemetría de aplicaciones cuando está disponible, y luego envía los datos al servicio en la nube de Better Mobile para evaluar el riesgo del dispositivo para las amenazas móviles.

La directiva de cumplimiento de dispositivos de Intune incluye una regla para Mobile Threat Defense que se basa en la evaluación del riesgo de Better Mobile. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó. Si se detecta que el dispositivo no cumple con la directiva, se bloqueará el acceso de los usuarios a los recursos corporativos, como Exchange Online y SharePoint Online. Los usuarios también reciben los pasos de la aplicación Better Mobile instalada en sus dispositivos para resolver el problema y volver a obtener acceso a los recursos corporativos.

## <a name="sample-scenarios"></a>Escenarios de ejemplo

Estos son algunos casos más frecuentes.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Control del acceso basado en amenazas de aplicaciones malintencionadas

Cuando se detectan aplicaciones malintencionadas, como el malware, en los dispositivos, puede bloquear las siguientes acciones hasta resolver la amenaza:

- Conectarse al correo electrónico corporativo

- Sincronizar los archivos corporativos mediante la aplicación OneDrive para el trabajo

- Acceder a las aplicaciones de empresa

**Bloquear cuando se detectan aplicaciones malintencionadas:**

![Imagen que muestra las aplicaciones malintencionadas detectadas](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_blocked.png)

**Acceso concedido tras la corrección:**

![Aplicaciones malintencionadas detectadas y acceso concedido](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Control del acceso basado en amenazas a la red

Detecte amenazas para la red, por ejemplo, ataques de tipo **Man in the middle**, y proteja el acceso a las redes Wi-Fi según el riesgo del dispositivo.

**Bloquear el acceso de red a través de Wi-Fi:**

![Bloquear el acceso de red a través de Wi-Fi](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_blocked.png)

**Acceso concedido tras la corrección:**

![Imagen que muestra el acceso concedido tras la corrección](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Control del acceso a SharePoint Online basado en amenazas a la red

Detecte amenazas para la red, por ejemplo, ataques de tipo **Man in the middle**, y evite la sincronización de archivos corporativos según el riesgo del dispositivo.

**Bloqueo de SharePoint Online cuando se detectan amenazas a la red:**

![Bloqueo de SharePoint Online cuando se detectan amenazas a la red](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_blocked.png)

**Acceso concedido tras la corrección:**

![Acceso concedido tras la solución](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Plataformas compatibles

- **Android 4.1 y versiones posteriores**

- **iOS 8.0 y versiones posteriores**

## <a name="prerequisites"></a>Requisitos previos

- Azure Active Directory Premium

- Suscripción a Microsoft Intune

- Suscripción a Mobile Threat Defense de Better Mobile

  - Para obtener más información, vea el [sitio web de Better Mobile](https://www.better.mobi/).

## <a name="next-steps"></a>Pasos siguientes

- [Integrate Better Mobile with Intune](better-mobile-mtd-connector-integration.md) (Integración de Better Mobile con Intune)

- [Set up Better Mobile apps](mtd-apps-ios-app-configuration-policy-add-assign.md) (Configuración de aplicaciones de Better Mobile)

- [Create Better Mobile device compliance policy](mtd-device-compliance-policy-create.md) (Creación de la directiva de cumplimiento de dispositivos de Better Mobile)

- [Enable Better Mobile MTD connector](mtd-connector-enable.md) (Habilitación del conector de MTD de Better Mobile)
