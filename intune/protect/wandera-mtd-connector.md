---
title: Configuración de la seguridad móvil de Wandera con Intune
titleSuffix: Intune on Azure
description: Procedimientos para configurar la seguridad móvil de Wandera con Microsoft Intune para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50973d883a3d31089e16dca5a9021643a821a3fb
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036624"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Conector Wandera Mobile Threat Defense con Intune  

Controle el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional en función de la evaluación de riesgos efectuada por Wandera. Wandera es una solución Mobile Threat Defense (MTD) que se integra con Microsoft Intune.  El riesgo se evalúa basándose en la telemetría recopilada de dispositivos mediante el servicio de Wandera que incluye:
- Vulnerabilidades del sistema operativo
- Aplicaciones malintencionadas instaladas
- Perfiles de red malintencionados
- Cryptojacking

Puede configurar directivas de *acceso condicional* basadas en la evaluación de riesgos de Wandera, habilitada mediante las directivas de cumplimiento de dispositivos de Intune. La directiva de evaluación de riesgos puede permitir o bloquear el acceso de dispositivos no compatibles a recursos corporativos en función de las amenazas detectadas.  


## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>¿Cómo contribuyen Wandera Mobile Threat Defense e Intune a proteger los recursos de la empresa?  

La aplicación móvil de Wandera se instala sin problemas con Microsoft Intune. Esta aplicación captura el sistema de archivos, la pila de red y la telemetría del dispositivo y de la aplicación (cuando están disponibles). Esta información se sincroniza con el servicio en la nube de Wandera para evaluar el riesgo del dispositivo de amenazas móviles. Estas clasificaciones de nivel de riesgo se pueden configurar para adaptarse a sus necesidades en la consola de Wandera, RADAR.

La directiva de cumplimiento de Intune incluye una regla para MTD basada en la evaluación de riesgos de Wandera. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó.

Para los dispositivos que no son compatibles, puede bloquearse el acceso a recursos como Office 365. Los usuarios de dispositivos bloqueados reciben instrucciones de la aplicación de Wandera para resolver el problema y volver a obtener acceso.

## <a name="supported-platforms"></a>Plataformas compatibles  

Las siguientes plataformas son compatibles con Wandera cuando se inscriben en Intune:

- Android 5.0 y versiones posteriores  
- iOS 10.2 y versiones posteriores  

Para obtener más información sobre la plataforma y el dispositivo, consulte el [sitio web de Wandera](https://www.wandera.com/classic-help-center/).

## <a name="prerequisites"></a>Requisitos previos  

- Suscripción a Microsoft Intune  
- Azure Active Directory  
- Wandera Mobile Threat Defense (anteriormente Wandera Secure)  

Para obtener más información, consulte la sección sobre [seguridad móvil de Wandera](https://www.wandera.com/mobile-security/).
 
## <a name="sample-scenarios"></a>Escenarios de ejemplo

Estos son los escenarios comunes cuando se usa Wandera MTD con Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Control del acceso basado en amenazas de aplicaciones malintencionadas  

Cuando las aplicaciones malintencionadas como malware se detectan en dispositivos, puede bloquear estos a partir de herramientas comunes hasta que la amenaza se resuelva. Los bloques comunes incluyen:  
- Conectarse al correo electrónico corporativo  
- Sincronizar los archivos corporativos mediante la aplicación OneDrive para el trabajo  
- Acceder a las aplicaciones de empresa  

**Bloquear cuando se detectan aplicaciones malintencionadas**:

![Imagen conceptual de aplicaciones malintencionadas detectadas](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**Acceso concedido tras la corrección**: 

![Imagen conceptual de acceso concedido tras la corrección](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>Controlar el acceso basándose en amenazas en la red  

Detecte amenazas para la red como ataques de tipo "Man in the middle" y proteja el acceso a las redes Wi-Fi según el riesgo del dispositivo.  

**Bloquear el acceso de red a través de Wi-Fi**:  

![Bloquear el acceso de red a través de Wi-Fi](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**Acceso concedido tras la corrección**:  

![Acceso concedido tras la corrección](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controlar el acceso a SharePoint Online basándose en amenazas en la red

Detecte amenazas en la red como ataques de tipo "Man in the middle" e impida la sincronización de archivos corporativos en función del riesgo del dispositivo.

**Bloqueo de SharePoint Online cuando se detectan amenazas de red**:  

![Bloqueo de SharePoint Online cuando se detectan amenazas a la red](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**Acceso concedido tras la corrección**:  

![Acceso concedido tras la corrección para el ejemplo de SharePoint](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>Pasos siguientes

- [Integrate Wandera with Intune](wandera-mtd-connector-integration.md) (Integración de Wandera con Intune)
- [Agregar y asignar aplicaciones de Mobile Threat Defense (MTD) con Intune](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Creación de directiva de cumplimiento de dispositivos de Mobile Threat Defense (MTD) con Intune](mtd-device-compliance-policy-create.md)
- [Habilitar el conector Mobile Threat Defense en Intune](mtd-connector-enable.md)
