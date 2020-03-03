---
title: Conector de Symantec con Microsoft Intune
titleSuffix: Microsoft Intune
description: Aprenda a integrar Intune con Symantec Endpoint Protection Mobile para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 884d7f5d4710b44c302598b3c34e704beace240a
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515278"
---
# <a name="symantec-endpoint-protection-mobile-connector"></a>Conector de Symantec Endpoint Protection Mobile

Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Symantec Endpoint Protection Mobile (SEP Mobile), una solución de defensa contra amenazas móviles integrada en Microsoft Intune. El riesgo se evalúa según la telemetría recopilada de dispositivos que ejecutan SEP Mobile, lo que incluye:

- Defensa física

- Defensa de red

- Defensa de aplicaciones

- Defensa de vulnerabilidades

Puede habilitar la evaluación de riesgos de SEP Mobile mediante directivas de cumplimiento de dispositivos y luego usar directivas de acceso condicional para permitir o bloquear el acceso a los dispositivos no conformes a los recursos corporativos en función de las amenazas detectadas.

## <a name="how-do-intune-and-sep-mobile-help-protect-your-company-resources"></a>¿Cómo ayudan Intune y SEP Mobile a proteger los recursos de la empresa?

La aplicación de SEP Mobile para Android o iOS/iPadOS captura la telemetría del sistema de archivos, de la pila de red y de las aplicaciones y dispositivos cuando está disponible, y la envía al servicio en la nube de Symantec para evaluar el riesgo del dispositivo frente a las amenazas móviles.

La directiva de cumplimiento de dispositivos de Intune incluye una regla para SEP Mobile, que se basa en la evaluación del riesgo de SEP Mobile. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó.

Si se detecta que el dispositivo no es conforme, se bloqueará el acceso a recursos como Exchange Online y SharePoint Online. Los usuarios de dispositivos bloqueados reciben instrucciones de la aplicación de SEP Mobile para resolver el problema y volver a obtener acceso a los recursos corporativos.

Intune admite dos modos de integración con SEP Mobile:

- **Configuración básica**, que es un modo de solo lectura que permite la visibilidad de SEP Mobile para dispositivos en Intune.

- **Integración completa**, que permite que SEP Mobile notifique la información de riesgos e incidentes de seguridad de los dispositivos a Intune.

## <a name="sample-scenarios"></a>Escenarios de ejemplo

Estos son algunos escenarios frecuentes:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Control del acceso basado en amenazas de aplicaciones malintencionadas

Cuando se detectan aplicaciones malintencionadas, como malware, en los dispositivos, puede bloquearlos de la siguiente manera hasta que la amenaza se resuelva:

- Conectarse al correo electrónico corporativo

- Sincronizar los archivos corporativos mediante la aplicación OneDrive para el trabajo

- Acceder a las aplicaciones de empresa

**Bloquear cuando se detectan aplicaciones malintencionadas:**

![Imagen conceptual de aplicaciones malintencionadas detectadas](./media/skycure-mobile-threat-defense-connector/symantec-arch-1.png)

**Acceso concedido tras la corrección:**

![Imagen de Acceso concedido tras la corrección después de detectar aplicaciones malintencionadas](./media/skycure-mobile-threat-defense-connector/symantec-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Controlar el acceso basándose en amenazas en la red

Detecte amenazas para la red, como **ataques de tipo Man-in-the-middle**, y proteja el acceso a las redes Wi-Fi según el riesgo del dispositivo.

**Bloquear el acceso de red a través de Wi-Fi:**

![Bloquear el acceso de red a través de Wi-Fi](./media/skycure-mobile-threat-defense-connector/symantec-arch-3.png)

**Acceso concedido tras la corrección:**

![Acceso concedido tras la solución](./media/skycure-mobile-threat-defense-connector/symantec-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar el acceso a SharePoint Online basándose en amenazas en la red

Detecte amenazas para la red, como **ataques de tipo Man-in-the-middle**, y evite la sincronización de archivos corporativos según el riesgo del dispositivo.

**Bloqueo de SharePoint Online cuando se detectan amenazas a la red:**

![Bloqueo de SharePoint Online cuando se detectan amenazas a la red](./media/skycure-mobile-threat-defense-connector/symantec-arch-5.png)

**Acceso concedido tras la corrección:**

![Acceso concedido tras la solución](./media/skycure-mobile-threat-defense-connector/symantec-arch-6.png)

## <a name="supported-platforms"></a>Plataformas compatibles

- **Android 4.1 y versiones posteriores**

- **iOS 8 y versiones posteriores**

## <a name="pre-requisites"></a>Requisitos previos

- Azure Active Directory Premium

- Suscripción a Microsoft Intune

- Suscripción a Symantec Endpoint Protection Mobile

Para más información, visite el [sitio web de Symantec](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Pasos siguientes

Estos son los pasos que debe realizar para integrar Intune con SEP Mobile:

- [Configurar la integración de SEP Mobile con Intune](skycure-mtd-connector-integration.md)

- [Agregar y asignar aplicaciones de SEP Mobile, Microsoft Authenticator y la directiva de configuración de aplicaciones iOS/iPadOS](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Crear una directiva de cumplimiento de dispositivos de SEP Mobile con Intune](mtd-device-compliance-policy-create.md)

- [Habilitar el conector de MTD para SEP Mobile en Intune](mtd-connector-enable.md)
