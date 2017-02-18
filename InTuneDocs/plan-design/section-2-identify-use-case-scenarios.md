---
title: Identificar escenarios de casos de uso de Intune | Microsoft Docs
description: "Este artículo ayuda a identificar los escenarios de casos de subuso y de casos de uso de Intune para una implementación solo en la nube de Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: c834b0282b8f9b47566ab1da2125d993ba8febdf


---

# <a name="identify-intune-use-case-scenarios"></a>Identificar escenarios de casos de uso de Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Los escenarios de casos de uso de la administración de dispositivos móviles describen el tipo de usuario o el rol y la propiedad de su dispositivo (por ejemplo, de la empresa o personal). Los escenarios de casos de uso son útiles porque le permiten segmentar a sus usuarios en grupos manejables. Identificar los escenarios de casos de uso es una parte importante del proceso de planeación para obtener una implementación correcta de Intune.

Vamos a tratar algunos ejemplos para ayudar a su organización a identificar escenarios de casos de uso de Intune, así como grupos de la organización y plataformas de dispositivos móviles asociadas a cada caso de uso.

## <a name="use-case-scenarios"></a>Escenarios de casos de uso

Puede comenzar haciendo referencia a los objetivos y metas de la implementación de Intune de la organización para ayudar a identificar los escenarios de casos de uso principales para su implementación. Dentro del ámbito de su plan de implementación de Intune, necesitará responder a las siguientes preguntas:

-   ¿Está planeando admitir dispositivos propiedad de la empresa?

-   ¿Está planeando admitir dispositivos de propiedad personal (BYOD)?

### <a name="sub-use-case-scenarios"></a>Escenarios de casos de subuso

Después de identificar los escenarios de casos de uso principales, necesitará determinar si cada escenario de casos de uso también incluye casos de subuso. Por ejemplo, una organización puede tener requisitos identificados para admitir un escenario de casos de uso corporativos que incluye casos de subuso adicionales:

-   Trabajador de la información

-   Ejecutivos

-   Pantalla completa

Aquí se muestran algunos ejemplos de escenarios de casos de uso y de casos de subuso. Puede usar la tabla siguiente para especificar los casos de uso de la organización y los escenarios de casos de subuso:

| **Casos de uso** | **Casos de subuso** |
|:---:|:---:|
| Corporativos | Trabajador de la información |              
| Corporativos | Ejecutivos |           
| Corporativos | Pantalla completa |
| BYOD | Trabajador de la información |           
| BYOD | Ejecutivos |

## <a name="identify-organizational-groups-associated-with-use-case-scenarios"></a>Identificar grupos de la organización asociados con escenarios de casos de uso

Ahora necesita identificar los grupos de la organización que están asociados con cada escenario de caso de uso y de caso de subuso. Estos son algunos ejemplos de grupos de la organización asociados con escenarios de casos de uso y de casos de subuso que pueden usarse como una plantilla para especificar la información de la organización:

| **Casos de uso** | **Casos de subuso** | **Grupos de la organización** |
|:---:|:---:|:---:|
| Corporativos | Trabajador de la información | Recursos humanos, finanzas |               
| Corporativos | Ejecutivo | Recursos humanos, finanzas |            
| Corporativos | Pantalla completa | Venta directa |
| BYOD | Trabajador de la información | Marketing, ventas |            
| BYOD | Ejecutivo | Marketing, ventas |

## <a name="identify-mobile-device-platforms-for-use-case-scenarios"></a>Identificar plataformas de dispositivos móviles para escenarios de casos de uso

Aquí identificará las plataformas de dispositivos móviles asociadas con cada escenario de casos de uso. Por ejemplo, su escenario de caso de uso corporativo puede admitir plataformas de dispositivos iOS y Android Samsung KNOX, y su directiva de BYOD puede incluir compatibilidad para plataformas de dispositivos móviles adicionales como Android (no Samsung KNOX) y Windows 10 Mobile. Este es un ejemplo de las plataformas de dispositivos móviles asociadas con cada escenario de casos de uso. Puede usar la tabla siguiente para especificar las plataformas de dispositivos de la organización asociadas con sus escenarios de casos de uso:

| **Casos de uso** | **Casos de subuso** | **Grupos** | **Plataformas de dispositivos** |   
|:---:|:---:|:---:|:---:|
| Corporativos | Trabajador de la información | Recursos humanos, finanzas | iOS |                                                           
| Corporativos | Ejecutivos | Recursos humanos, finanzas | iOS |                                                           
| Corporativos | Pantalla completa | Venta directa | Android |
| BYOD | Trabajador de la información | Marketing, ventas | iOS |                                                           
| BYOD | Ejecutivos | Marketing, ventas | iOS |

## <a name="next-section"></a>Sección siguiente

En la sección siguiente se proporcionan instrucciones sobre [cómo identificar los requisitos de Intune para cada escenario de caso de uso](section-3-determine-use-case-requirements.md).



<!--HONumber=Dec16_HO5-->


