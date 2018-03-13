---
title: "Decisiones de tecnología para BYOD con EMS"
description: "Principales decisiones de tecnología para habilitar BYOD y proteger los datos corporativos con Microsoft Enterprise Mobility + Security."
keywords: 
author: dougeby
ms.author: pfetty
manager: angrobe
ms.date: 12/8/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.openlocfilehash: 3ee642f5c2e30023043cec4bf5286999d4397e2d
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2018
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>Decisiones de tecnología para habilitar BYOD con Microsoft Enterprise Mobility + Security (EMS)

Cuando desarrolle su estrategia para permitir que los empleados trabajen de forma remota en sus propios dispositivos (BYOD), tiene que tomar importantes decisiones en los escenarios para habilitar BYOD y proteger los datos corporativos. Por suerte, EMS ofrece todas las capacidades necesarias en un conjunto completo de soluciones.  

En este tema se analiza el caso de uso sencillo de habilitar el acceso BYOD al correo electrónico corporativo. Se centra en si es o no necesario administrar todo el dispositivo o solo las aplicaciones, ambas opciones totalmente válidas.

## <a name="assumptions"></a>Suposiciones
* Tiene conocimientos básicos de Azure Active Directory y Microsoft Intune
* Las cuentas de correo electrónico están hospedadas en Exchange Online

## <a name="common-reasons-to-manage-the-device-mdm"></a>Razones habituales para administrar el dispositivo (MDM)
Puede impulsar fácilmente a los usuarios a inscribir sus dispositivos en la administración de dispositivos si implementa una directiva de [acceso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) en Exchange Online. Estos son los motivos por los que es posible que quiera administrar los dispositivos personales:

**Wi-Fi/VPN**: si los usuarios necesitan un perfil de conectividad corporativo para ser productivos, se puede configurar sin problemas.

**Aplicaciones**: si los usuarios necesitan instalar un conjunto de aplicaciones en el dispositivo, se pueden entregar sin problemas. Esto incluye aplicaciones que se puedan exigir por motivos de seguridad, como Mobile Threat Defense.

**Cumplimiento**: algunas organizaciones deben cumplir directivas reglamentarias u otras que exijan controles de MDM concretos. Por ejemplo, necesita que MDM cifre todo el dispositivo o elabore un informe de todas las aplicaciones del dispositivo.

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>Razones habituales para administrar solo las aplicaciones (MAM)
MAM sin MDM es muy popular en organizaciones que admiten BYOD. Puede impulsar a los usuarios a acceder al correo electrónico desde Outlook Mobile (que admite las protecciones de MAM) si implementa una directiva de acceso condicional en Exchange Online. Estos son los motivos por los que es posible que quiera administrar únicamente las aplicaciones de los dispositivos personales:

**Experiencia de usuario**: la inscripción de MDM incluye muchos mensajes de advertencia (aplicados por la plataforma) que suelen dar lugar a que el usuario desista de acceder al correo electrónico en el dispositivo personal después de todo. MAM es mucho menos alarmante para los usuarios, ya que simplemente aparece un mensaje emergente una vez para informar de que se han aplicado las protecciones de MAM.

**Cumplimiento**: algunas organizaciones deben cumplir directivas que exigen menos capacidades de administración en dispositivos personales. Por ejemplo, MAM solo puede quitar datos corporativos de las aplicaciones, a diferencia de MDM, que puede quitar todos los datos del dispositivo.

![Imagen comparativa de la administración del dispositivo y las aplicaciones en dispositivos móviles](./media/byod-app-device-mgmt.png)

Más información sobre los [ciclos de vida del dispositivo y la aplicación](introduction-device-app-lifecycles.md).

## <a name="mdm-vs-mam-capability-comparison"></a>Comparación de capacidades de MDM y MAM
Como ya se ha mencionado, el acceso condicional puede llevar a un usuario a inscribir su dispositivo o a usar una aplicación administrada como Outlook Mobile. Se pueden aplicar muchas otras condiciones en cada caso, que incluyen:

* Qué usuario intenta acceder
* Si la ubicación es o no de confianza
*   Nivel de riesgo de inicio de sesión
* Plataforma de dispositivo

Aun así, suele haber riesgos concretos que preocupan a muchas organizaciones.  En la siguiente tabla se indican las preocupaciones comunes y la respuesta que ofrecen MDM y MAM.

| Preocupación   |   MDM  |   MAM  |
|------------|--------|--------|
|Acceso a datos no autorizado | Exigir pertenencia a grupo | Exigir pertenencia a grupo |
|Acceso a datos no autorizado | Exigir inscripción del dispositivo | Exigir aplicación protegida |
|Acceso a datos no autorizado | Exigir ubicación determinada | Exigir ubicación determinada |
| | | |
|Cuenta de usuario en peligro| Exigir MFA | Exigir MFA|
|Cuenta de usuario en peligro | Bloquear usuarios de alto riesgo | Bloquear usuarios de alto riesgo |
|Cuenta de usuario en peligro | PIN de dispositivo | PIN de aplicación |
| | | |
| Dispositivo o aplicación en peligro | Exigir un dispositivo conforme | Comprobación de jailbreak al iniciar la aplicación |
| Dispositivo o aplicación en peligro | Cifrar datos de dispositivo | Cifrar datos de aplicación |
| | | |
|Dispositivo extraviado o robado | Borrar todos los datos del dispositivo | Borrar todos los datos de la aplicación|
| | | |
| Uso compartido de datos accidental o guardado en ubicaciones inseguras | Restringir copias de seguridad de datos del dispositivo | Restringir el corte, la copia o el pegado|
| Uso compartido de datos accidental o guardado en ubicaciones inseguras | Restringir el guardado como | Restringir el guardado como |
|Uso compartido de datos accidental o guardado en ubicaciones inseguras | Deshabilitar la impresión | n/a|

## <a name="next-steps"></a>Pasos siguientes
Es hora de decidir si va a habilitar BYOD en la organización al centrarse en la administración del dispositivo, de la aplicación o en una combinación de ambas. Usted elige la forma de implementación, aquella que le asegure que las características de identidad y seguridad disponibles en Azure AD siempre van a estar disponibles.

Use la [guía de planeamiento](planning-guide.md) de Intune para el siguiente nivel de planeamiento.
