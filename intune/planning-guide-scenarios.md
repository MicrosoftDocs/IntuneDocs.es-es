---
title: Identificación de escenarios de casos de uso
titlesuffix: Microsoft Intune
description: Este artículo ayuda a identificar los escenarios de casos de subuso y de casos de uso de Intune para una implementación solo en la nube de Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: de72bc56bf1ec0e7f1555d889ae0684c1162fdb9
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841409"
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>Identificación de escenarios de casos de uso de administración de dispositivos móviles

Identificar los escenarios de casos de uso es una parte importante del proceso de planeación para obtener una implementación correcta de Intune. Estos escenarios son útiles porque permiten segmentar los usuarios en grupos administrables por tipo de usuario o rol y la propiedad del dispositivo del usuario (por ejemplo, profesional o personal).

Se van a tratar algunos ejemplos para ayudar a su organización a identificar escenarios de casos de uso de Intune, así como grupos de la organización y plataformas de dispositivos móviles asociadas a cada caso de uso.

## <a name="device-ownership"></a>Propiedad del dispositivo
Puede comenzar haciendo referencia a los objetivos y metas de la implementación de Intune de la organización para ayudar a identificar los escenarios de casos de uso principales para su implementación. Dentro del ámbito de su plan de implementación de Intune, responda a las siguientes preguntas:

-   ¿Está planeando admitir dispositivos propiedad de la empresa?

-   ¿Está planeando admitir dispositivos de propiedad personal (BYOD)?

No se trata de una u otra opción. Es posible que necesite admitir ambas formas de propiedad del dispositivo para cumplir los objetivos de la organización. Los casos de subuso permitirán aclarar dónde aplicar las diferentes directivas de administración de dispositivos.

### <a name="user-type-or-device-role"></a>Tipo de usuario o rol de dispositivo

Determine si cada escenario de caso de uso también incluye casos de subuso. Por ejemplo, la organización puede tener requisitos identificados para admitir un escenario de casos de uso corporativos que incluye casos de subuso adicionales basados en el tipo de usuario o en el rol de dispositivo, como:

-   Trabajador de la información

-   Ejecutivo

-   Pantalla completa

Aquí se muestran algunos ejemplos de escenarios de casos de uso y de casos de subuso:

| **Casos de uso** | **Casos de subuso** |
|:---:|:---:|
| Corporativos | Trabajador de la información |              
| Corporativos | Ejecutivos |           
| Corporativos | Pantalla completa |
| BYOD | Trabajador de la información |           
| BYOD | Ejecutivos |

Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para especificar los casos de uso y subuso de su organización.

## <a name="organizational-groups-for-your-scenarios"></a>Grupos de la organización para los escenarios

Ahora necesita identificar los grupos de la organización que están asociados con cada escenario de caso de uso y de caso de subuso. Por ejemplo:

| **Casos de uso** | **Casos de subuso** | **Grupos de la organización** |
|:---:|:---:|:---:|
| Corporativos | Trabajador de la información | Recursos humanos, finanzas |               
| Corporativos | Ejecutivo | Recursos humanos, finanzas |            
| Corporativos | Pantalla completa | Venta directa |
| BYOD | Trabajador de la información | Marketing, ventas |            
| BYOD | Ejecutivo | Marketing, ventas |


## <a name="mobile-device-platforms-for-your-scenarios"></a>Plataformas de dispositivos móviles para los escenarios

El siguiente paso consiste en identificar las plataformas de dispositivos móviles asociadas con cada escenario de casos de uso. Puede haber más de una.

Por ejemplo, su escenario de caso de uso corporativo puede admitir las plataformas de dispositivos iOS y Android Samsung Knox. La directiva BYOD puede incluir compatibilidad con plataformas de dispositivos móviles adicionales como Windows 10 Mobile y Android (no Samsung Knox). Según los ejemplos anteriores, se han asociado las plataformas de dispositivos móviles con cada escenario de caso de uso.

| **Casos de uso** | **Casos de subuso** | **Grupos** | **Plataformas de dispositivos** |   
|:---:|:---:|:---:|:---:|
| Corporativos | Trabajador de la información | Recursos humanos, finanzas | iOS |                                                           
| Corporativos | Ejecutivos | Recursos humanos, finanzas | iOS |                                                           
| Corporativos | Pantalla completa | Venta directa | Android |
| BYOD | Trabajador de la información | Marketing, ventas | iOS |                                                           
| BYOD | Ejecutivos | Marketing, ventas | iOS |

## <a name="next-steps"></a>Pasos siguientes

En la sección siguiente se proporcionan instrucciones sobre [cómo identificar los requisitos de Intune para cada escenario de caso de uso](planning-guide-requirements.md).
