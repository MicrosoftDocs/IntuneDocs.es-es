---
title: Uso compartido y seguridad de datos en Intune
description: Obtenga más información sobre cómo se protegen y comparten los datos personales en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 631d76aca2c393be3c81cb8b6f532605664f4ce4
ms.sourcegitcommit: 119962948045079022aa48f968dde3e961d7cd0c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031643"
---
# <a name="data-security-and-sharing-in-intune"></a>Uso compartido y seguridad de datos en Intune


## <a name="data-security"></a>Seguridad de los datos

Microsoft Intune es un componente clave de la oferta de servicio en la nube de Microsoft Enterprise Mobility + Security Suite. Para admitir la [estrategia de gobernanza de datos](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx), todos los servicios en la nube de Microsoft se desarrollan con metodologías de [Microsoft Privacy](https://www.microsoft.com/en-us/trustcenter/privacy) y [Microsoft Security](https://www.microsoft.com/en-us/trustcenter/security/).  

Microsoft Intune sigue las mismas medidas técnicas y organizativas que toman los equipos de servicio de Microsoft Azure para protegerse contra los procesos de vulneración de datos.

Para obtener más información, vea el [Portal de confianza de servicios](https://www.microsoft.com/en-us/TrustCenter/stp).

Intune usa técnicas de minimización de datos, como

- aggregation
- recopilación de datos opcional para algunas características
- datos menos precisos o confidenciales

Intune también usa técnicas como la seguridad JiT y RBAC para incidentes de soporte técnico para garantizar la protección de datos de forma predeterminada. 

### <a name="data-breach-reporting"></a>Informes de vulneración de datos

Cuando se identifica un incidente de seguridad notificable a los clientes (CRSI), los clientes reciben una notificación al respecto. Este proceso incluye trabajar con el equipo de Microsoft O365 para comunicar la notificación de vulneración a los clientes de Microsoft O365 que usan Intune.

## <a name="data-sharing"></a>Uso compartido de datos

Cuando los administradores de inquilinos activan ciertas funcionalidades (por ejemplo, el Programa de inscripción de dispositivos de Apple), Microsoft Intune obtiene consentimiento del administrador para compartir datos con las terceras partes adecuadas. En tal caso, Intune podría compartir los datos personales con:

- Terceros que actúen como agentes de Microsoft.
- Terceros que no actúen como agentes de Microsoft, pero solo cuando los administradores de inquilinos concedan permiso a Intune explícitamente para ello.

Todos los terceros que actúen como agentes de Microsoft se incluyen en la [lista de subcontratistas de servicios en línea](https://aka.ms/Online_Serv_Subcontractor_List).

El uso compartido de datos con estas entidades se realiza para ayudar al cliente y ofrecer soporte técnico, el mantenimiento del servicio y otras operaciones.

Los datos personales de Intune que se mantienen un el servicio de terceros se rigen mediante un contrato del inquilino con dichos terceros. También concede permiso a Intune que transmitir los datos al servicio de terceros.  

Para obtener más información sobre los datos compartidos con terceros determinados, consulte los artículos siguientes:
- [Data que Intune manda a Apple](data-intune-sends-to-apple.md)
- [Datos que Intune manda a Google](data-intune-sends-to-google.md)
- [Datos que Apple manda a Intune](data-apple-sends-to-intune.md)
- [Datos que Google manda a Intune](data-google-sends-to-intune.md)
- [Datos que Jamf Pro manda a Intune](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>Uso compartido de datos de System Center Configuration Manager

Microsoft Intune no comparte ningún dato con System Center Configuration Manager. System Center Configuration Manager es un producto local implementado, administrado y operado directamente por el cliente. Los datos de uso y diagnóstico recopilados por Configuration Manager solo son para mejorar la experiencia de instalación, la calidad y la seguridad de las versiones futuras.

Para obtener más información, vea [Diagnostics and usage data for SCCM](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data) (Diagnósticos y datos de uso para SCCM). 


## <a name="next-steps"></a>Pasos siguientes

Consulte cómo [visualizar y corregir](privacy-data-view-correct.md) los datos personales en Intune.
