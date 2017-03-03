---
title: Determinar los requisitos de los escenarios de casos de uso de Intune | Microsoft Docs
description: "Este artículo ayuda a determinar los requisitos de los escenarios de casos de subuso y de casos de uso de Intune para una implementación solo en la nube de Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: 91b25fe35c6a1f8a554d543ca005cc3b482f22d7


---

# <a name="determine-intune-use-case-scenario-requirements"></a>Determinar los requisitos de los escenarios de casos de uso de Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

En esta sección se determinarán los requisitos de cada grupo de la organización dentro de cada escenario de caso de uso. Durante este proceso podrá preparar mejor las otras áreas de planeación de la implementación de Intune como la arquitectura y el diseño, la incorporación y la implementación. También puede ayudar a identificar posibles carencias y desafíos relacionados con su proyecto de implementación de Intune.

Puede tener diferentes conjuntos de requisitos para cada uno de sus escenarios de casos de subuso o uso, y sus grupos asociados de la organización y plataformas de dispositivos móviles. Por ejemplo, los requisitos de los escenarios de casos de uso corporativos pueden necesitar dispositivos para inscribirse en Intune con un conjunto más restrictivo de configuración de dispositivos (por ejemplo, un número PIN de 6 caracteres, deshabilitar la copia de seguridad en la nube), en comparación con el escenario de casos de uso de "Bring your own device" (BYOD), donde necesita menos opciones de configuración restrictivas (por ejemplo, un número PIN de 4 caracteres, permitir la copia de seguridad en la nube).

También puede tener grupos de la organización para el escenario de casos de uso corporativos que tengan diferentes conjuntos de requisitos (por ejemplo, configuración de PIN, perfil de VPN o Wi-Fi, aplicaciones implementadas). Además, sus requisitos pueden determinarse mediante las funciones de la plataforma de dispositivos móviles (por ejemplo, lector de huellas dactilares, perfil de correo electrónico).

Estos son algunos ejemplos de requisitos de casos de uso de la organización, que muestran diferentes conjuntos de requisitos para cada escenario de casos de subuso o uso, grupo de la organización y plataforma de dispositivos móviles. También puede usar la tabla siguiente para especificar los requisitos de los casos de uso de la organización:

| **Casos de uso** | **Casos de subuso** | **Grupos** | **Plataformas de sistema operativo del dispositivo** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| Corporativos | Trabajador de la información | Recursos humanos, finanzas | iOS | Correo electrónico seguro, configuración de dispositivo, perfiles, aplicaciones |                                                          
| Corporativos | Ejecutivos | Recursos humanos, finanzas | iOS | Correo electrónico seguro, configuración de dispositivo, perfiles, aplicaciones |                                                         
| Corporativos | Pantalla completa | Venta directa | Android | Configuración de dispositivo, perfiles, aplicaciones |
| BYOD | Trabajador de la información | Marketing, ventas | iOS | Correo electrónico seguro, configuración de dispositivo, perfiles, aplicaciones |                                                         
| BYOD | Ejecutivos | Marketing, ventas | iOS | Correo electrónico seguro, configuración de dispositivo, perfiles, aplicaciones |

## <a name="examples-of-requirements"></a>Ejemplos de requisitos

Estos son algunos ejemplos más que pueden usarse en la columna "Requisitos" a la que se hace referencia en la tabla anterior:

- **Correo electrónico seguro**
    - Acceso condicional para Exchange Online o local
    - Directivas de protección de aplicaciones de Outlook
<br></br>
- **Configuración del dispositivo**
    - Configuración de PIN con cuatro, seis caracteres
    - Restringir la copia de seguridad en la nube
<br></br>
- **Perfiles**
    - Wi-Fi
    - VPN
    - Correo electrónico (Windows 10 Mobile)
<br></br>
- **Aplicaciones**
    - Office 365 con directivas de protección de aplicaciones
    - Línea de negocio (LOB) con directivas de protección de aplicaciones

## <a name="next-section"></a>Sección siguiente

En la sección siguiente se proporcionan instrucciones sobre [cómo desarrollar un plan de implementación de Intune](section-4-develop-a-rollout-plan.md).



<!--HONumber=Dec16_HO5-->


