---
title: Conector Lookout Mobile Threat Defense | Microsoft Docs
description: "Proteja el acceso a recursos de la empresa en función del riesgo del dispositivo, la red y la aplicación con el conector Lookout Mobile Threat Defense e Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d42fa20a3bc6b6f4a74dd0872aae25cfb33067b9
ms.openlocfilehash: dfed1ece238210e8b98934d8add7dbb9b0f1c1fb
ms.lasthandoff: 03/21/2017


---

# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Conector Lookout Mobile Threat Defense con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Puede controlar el acceso del dispositivo móvil a recursos corporativos según la evaluación del riesgo que realice Lookout, una solución Mobile Threat Defense integrada con Microsoft Intune. El riesgo se evalúa basándose en la telemetría recopilada de dispositivos mediante el servicio de Lookout que incluye:
- Vulnerabilidades del sistema operativo
- Aplicaciones malintencionadas instaladas
- Perfiles de red malintencionados

Puede configurar directivas de acceso condicional basándose en la evaluación de riesgo de Lookout habilitada mediante las directivas de cumplimiento de Intune. Con la configuración puede permitir o bloquear dispositivos no compatibles basándose en las amenazas detectadas.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>¿Cómo contribuyen Mobile Threat Defense de Lookout e Intune a proteger los recursos de la empresa?
La aplicación móvil Lookout, **Lookout for Work**, está instalada y se ejecuta en dispositivos móviles. Esta aplicación captura el sistema de archivos, la pila de red y la telemetría de aplicaciones y dispositivos cuando está disponible, después lo envía al servicio en la nube de Lookout para evaluar el riesgo del dispositivo para las amenazas móviles. Puede cambiar la clasificación del nivel de riesgo de las amenazas en la consola de Lookout para satisfacer sus requisitos.  

La directiva de cumplimiento en Intune incluye una regla para Mobile Threat Protection de Lookout basada en la evaluación del riesgo de Lookout. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó.

Si se detecta que el dispositivo no cumple con la regla, se puede bloquear el acceso a recursos como Exchange Online y SharePoint Online. Los usuarios de dispositivos bloqueados reciben los pasos para resolver el problema y volver a obtener acceso. Las instrucciones se inician desde la aplicación Lookout for Work.

## <a name="supported-platforms"></a>Plataformas compatibles:
Las siguientes plataformas son compatibles con Lookout cuando se inscriben en Intune:
* **Android 4.1 y versiones posteriores**
* **iOS 8 y versiones posteriores** Para obtener información adicional sobre la compatibilidad de lenguaje y plataforma, visite el [sitio web de Lookout](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

## <a name="prerequisites"></a>Requisitos previos:
* Suscripción a Microsoft Intune
* Azure Active Directory
* Suscripción de empresa a Lookout Mobile Endpoint Security  

Para obtener más información, consulte [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security).

## <a name="sample-scenarios"></a>Escenarios de ejemplo
Estos son algunos escenarios frecuentes:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Control del acceso basado en amenazas de aplicaciones malintencionadas
Cuando las aplicaciones malintencionadas como malware se detectan en dispositivos, puede bloquear los dispositivos de la siguiente manera hasta que la amenaza se resuelva:
* Conectarse al correo electrónico corporativo
* Sincronizar los archivos corporativos mediante la aplicación OneDrive para el trabajo
* Acceder a las aplicaciones de empresa

**Bloqueo cuando se detectan aplicaciones malintencionadas:**
![diagrama en el que se muestra la directiva de acceso condicional bloqueando el acceso cuando se determina que el dispositivo no es compatible debido a que tiene aplicaciones malintencionadas](../media/mtp/malicious-apps-blocked.png).

**Acceso concedido tras la solución:**

![diagrama en el que se muestra la directiva de acceso condicional concediendo acceso cuando se determina que, tras la solución, el dispositivo es conforme](../media/mtp/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Control del acceso basado en amenazas a la red
Detecte amenazas para la red como ataques de tipo Man-in-the-middle y proteja el acceso a las redes Wi-Fi según el riesgo del dispositivo.

**Bloquear el acceso a la red a través de Wi-Fi:**
![diagrama en el que se muestra el acceso condicional bloqueando el acceso Wi-Fi en función de las amenazas de red](../media/mtp/network-wifi-blocked.png).

**Acceso concedido tras la solución:**

![diagrama en el que se muestra el acceso condicional permitiendo el acceso tras la corrección de la amenaza](../media/mtp/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Control del acceso a SharePoint Online basado en amenazas a la red

Detecte amenazas para la red como ataques de tipo Man-in-the-middle y evite la sincronización de archivos corporativos según el riesgo del dispositivo.

**Bloqueo de SharePoint Online cuando se detectan amenazas a la red:**

![diagrama en el que se muestra el acceso condicional bloqueando el acceso del dispositivo a SharePoint Online en función de la detección de amenazas](../media/mtp/network-spo-blocked.png)


**Acceso concedido tras la solución:**

![diagrama en el que se muestra el acceso condicional permitiendo el acceso tras la corrección de la amenaza de red](../media/mtp/network-spo-unblocked.png)

## <a name="next-steps"></a>Pasos siguientes
Estos son los principales pasos para implementar esta solución:
1.    [Configurar la suscripción a Lookout](device-threat-protection-subscription-setup.md)
2.    [Habilitar Mobile Threat Defense de Lookout en Intune](device-threat-protection-enable.md)
3.  [Configurar e implementar la aplicación Mobile Threat Defense de Lookout](device-threat-protection-apps.md)
4.    [Crear la directiva de cumplimiento de dispositivos de Lookout](device-threat-protection-policy.md)
5.    [Solucionar problemas de integración de Mobile Threat Defense de Lookout](http://docs.microsoft.com/intune/troubleshoot/device-threat-protection-troubleshooting)

