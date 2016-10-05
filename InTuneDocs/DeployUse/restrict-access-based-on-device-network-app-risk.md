---
title: "Restringir el acceso mediante la protección contra amenazas móviles | Microsoft Intune"
description: "Restrinja el acceso a recursos de la empresa en función del riesgo del dispositivo, la red y la aplicación."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c3cf5e6b32ad24d4972fd147331dda7d2d43e8c6
ms.openlocfilehash: d4eadb73aac14a375f41c434a4303a885bfbae64


---

# Restringir el acceso a recursos de la empresa en función del riesgo del dispositivo, la red y la aplicación
Puede controlar el acceso desde dispositivos móviles a recursos corporativos en función de la evaluación de riesgos efectuada por Lookout, una solución de protección contra amenazas móviles (MTP) integrada en Microsoft Intune. El riesgo se basa en la telemetría que recopila el servicio Lookout MTP de los dispositivos sobre vulnerabilidades del sistema operativo (SO), aplicaciones malintencionadas instaladas y perfiles de red. Según la evaluación de riesgos, se pueden configurar directivas de acceso condicional de Intune y permitir o bloquear los dispositivos definidos como no conformes debido a las amenazas detectadas en ellos.  De momento esto solo se admite en dispositivos **Android** con versiones **4.1 y posteriores** e inscritos en Microsoft Intune.  
## ¿Qué problema soluciona esto?
Las empresas y organizaciones necesitan proteger datos confidenciales frente a amenazas emergentes que incluyen amenazas físicas, basadas en aplicaciones y basadas en redes, así como frente a vulnerabilidades del sistema operativo.

Históricamente, las empresas y organizaciones han tenido un papel activo a la hora de proteger los equipos frente a ataques malintencionados. La movilidad es un área emergente que a menudo no se protege. Aunque las plataformas móviles cuentan con protección integrada del sistema operativo mediante técnicas como el aislamiento de aplicaciones y las tiendas de aplicaciones de consumidor seguras, estas plataformas siguen siendo vulnerables a ataques sofisticados. Como los empleados cada vez usan más los dispositivos móviles para trabajar y necesitan acceder a información que puede ser confidencial y valiosa, estos dispositivos tienen que protegerse frente a una serie de ataques sofisticados.

Intune ofrece la posibilidad de controlar el acceso a los recursos y los datos de la empresa según la evaluación de riesgos que proporcionan las soluciones MTP como Lookout.

## ¿Cómo contribuyen la protección contra amenazas móviles de Lookout e Intune a proteger los recursos de empresa?
La aplicación móvil de Lookout (Lookout for Work), que se ejecuta en dispositivos móviles, captura la telemetría del sistema de archivos, la pila de red y los dispositivos y las aplicaciones (si está disponible) y la envía al servicio de nube de protección contra amenazas móviles (MTP) de Lookout para calcular un riesgo de dispositivo agregado de amenazas móviles. También puede cambiar la clasificación de nivel de riesgo de las amenazas en la consola MTP para satisfacer sus requisitos.  
La directiva de cumplimiento normativo de Intune ahora incluye una nueva regla de protección contra amenazas móviles de Lookout que se basa en la evaluación de riesgos de Lookout MTP. Cuando esta regla está habilitada, Microsoft Intune evalúa la conformidad del dispositivo con la directiva habilitada.

Si se determina que el dispositivo no es conforme con la directiva de cumplimiento normativo, se puede bloquear el acceso a recursos como Exchange Online y SharePoint Online mediante directivas de acceso condicional. Cuando se bloquea el acceso, se proporciona a los usuarios finales un tutorial para ayudarles a resolver el problema y obtener acceso a los recursos de la empresa. Este tutorial se inicia a través de la aplicación Lookout for Work.

## Escenarios de ejemplo
Estos son algunos escenarios frecuentes:
### Amenaza de aplicaciones malintencionadas:
Cuando se detectan aplicaciones malintencionadas como malware en el dispositivo, puede evitar que estos dispositivos:
* Se conecten al correo electrónico corporativo antes de solucionar la amenaza.
* Sincronicen archivos corporativos mediante la aplicación OneDrive para el trabajo.
* Accedan a aplicaciones cruciales para la empresa.

**Acceso bloqueado cuando se detectan aplicaciones malintencionadas:**
![diagrama en el que se muestra la directiva de acceso condicional bloqueando el acceso cuando se determina que el dispositivo no es conforme debido a que tiene aplicaciones malintencionadas](../media/mtp/malicious-apps-blocked.png)

**Dispositivo desbloqueado que puede acceder a recursos de la empresa cuando se soluciona la amenaza:**

![diagrama en el que se muestra la directiva de acceso condicional concediendo acceso cuando se determina que, tras la solución, el dispositivo es conforme](../media/mtp/malicious-apps-unblocked.png)
### Amenaza para la red:
Detecte amenazas para la red como ataques de tipo Man-in-the-middle y restrinja el acceso a las redes Wi-Fi según el riesgo del dispositivo.

**Acceso bloqueado a la red a través de Wi-Fi:**
![diagrama en el que se muestra el acceso condicional bloqueando el acceso Wi-Fi en función de las amenazas de red](../media/mtp/network-wifi-blocked.png)

**Acceso concedido tras la solución:**

![diagrama en el que se muestra el acceso condicional permitiendo el acceso tras la corrección de la amenaza](../media/mtp/network-wifi-unblocked.png)
### Amenaza para la red (evita el acceso a SharePoint Online):

Detecte amenazas para la red como ataques de tipo Man-in-the-middle y evite la sincronización de archivos corporativos según el riesgo del dispositivo.

**Acceso bloqueado a SharePoint Online en función de amenazas de red detectadas en el dispositivo:**

![diagrama en el que se muestra el acceso condicional bloqueando el acceso del dispositivo a SharePoint Online en función de la detección de amenazas](../media/mtp/network-spo-blocked.png)


**Acceso concedido tras la solución:**

![diagrama en el que se muestra el acceso condicional permitiendo el acceso tras la corrección de la amenaza de red](../media/mtp/network-spo-unblocked.png)

## Pasos siguientes
Estos son los principales pasos para implementar esta solución:
1.  [Configurar la suscripción con protección contra amenazas móviles de Lookout](set-up-your-subscription-with-lookout-mtp.md)
2.  [Habilitar la conexión de Lookout MTP en Intune](enable-lookout-mtp-connection-in-intune.md)
3.  [Configurar e implementar la aplicación Lookout for Work](configure-and-deploy-lookout-for-work-apps.md)
4.  [Configurar directiva de cumplimiento](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Solucionar problemas de integración de Lookout](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)



<!--HONumber=Sep16_HO3-->


