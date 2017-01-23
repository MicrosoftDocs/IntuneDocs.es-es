---
title: "Proteger el acceso mediante la protección contra amenazas de dispositivo | Microsoft Docs"
description: "Proteja el acceso a recursos de la empresa en función del riesgo del dispositivo, la red y la aplicación."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9f34d54710f0ec662eecec85f7fa041061132a0d
ms.openlocfilehash: 184002a3a9f4af671a467ce9fe79fe0050bd00df


---

# <a name="protect-access-to-company-resource-based-on-device-network-and-application-risk"></a>Proteja el acceso al recurso de la empresa en función del riesgo del dispositivo, la red y la aplicación.

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Puede controlar el acceso de dispositivos móviles a recursos corporativos en función de la evaluación de riesgos efectuada por Lookout, una solución de protección contra amenazas de dispositivo integrada en Microsoft Intune. El riesgo se evalúa basándose en la telemetría recopilada de dispositivos mediante el servicio de Lookout que incluye:
- Vulnerabilidades del sistema operativo
- Aplicaciones malintencionadas instaladas
- Perfiles de red malintencionados

Puede configurar directivas de acceso condicional basándose en la evaluación de riesgo de Lookout habilitada mediante las directivas de cumplimiento de Intune. Con la configuración puede permitir o bloquear dispositivos no compatibles basándose en las amenazas detectadas.  

## <a name="what-problem-does-this-solve"></a>¿Qué problema soluciona esto?
Las empresas necesitan proteger datos confidenciales frente a amenazas emergentes que incluyen amenazas físicas, basadas en aplicaciones y basadas en redes, así como frente a vulnerabilidades del sistema operativo.

Históricamente, las empresas han sido proactivas a la hora de proteger PC de los ataques, mientras que los dispositivos móviles no estaban supervisados ni protegidos. Las plataformas móviles cuentan con protección integrada como el aislamiento de aplicaciones y las tiendas de aplicaciones de consumidor seguras, pero estas plataformas siguen siendo vulnerables a ataques sofisticados. Hoy en día, más empleados usan dispositivos para trabajar y necesitan acceso a información confidencial. Los dispositivos necesitan estar protegidos de los ataques sofisticados que cada vez son más frecuentes.

Intune le permite controlar el acceso a los recursos de la empresa según la evaluación de riesgos que proporcionan las soluciones de protección contra amenazas de dispositivo como Lookout.

## <a name="how-do-intune-and-lookout-device-threat-protection-help-protect-company-resources"></a>¿Cómo contribuyen la protección contra amenazas de dispositivo de Lookout e Intune a proteger los recursos de empresa?
La aplicación móvil Lookout, **Lookout for Work**, está instalada y se ejecuta en dispositivos móviles. Esta aplicación captura el sistema de archivos, la pila de red y la telemetría de aplicaciones y dispositivos cuando está disponible, después lo envía al servicio en la nube de Lookout para evaluar el riesgo del dispositivo para las amenazas móviles. Puede cambiar la clasificación del nivel de riesgo de las amenazas en la consola de Lookout para satisfacer sus requisitos.  

La directiva de cumplimiento en Intune incluye una regla para Lookout Mobile Threat Protection basándose en la evaluación del riesgo de Lookout. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó.

Si se detecta que el dispositivo no es compatible, puede bloquearse el acceso a recursos como Exchange Online y SharePoint Online. Los usuarios de dispositivos bloqueados reciben los pasos para resolver el problema y volver a obtener acceso. Las instrucciones se inician desde la aplicación Lookout for Work.

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
1.  [Configurar la suscripción con protección contra amenazas móviles de Lookout](set-up-your-subscription-with-lookout-mtp.md)
2.  [Habilitar la conexión de Lookout MTP en Intune](enable-lookout-mtp-connection-in-intune.md)
3.  [Configurar e implementar la aplicación Lookout for Work](configure-and-deploy-lookout-for-work-apps.md)
4.  [Configurar directiva de cumplimiento](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Solucionar problemas de integración de Lookout](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)



<!--HONumber=Jan17_HO1-->


