---
title: "Proteger el correo electrónico y Office 365"
description: "En este tema se describe cómo puede utilizar acceso condicional para permitir que únicamente los dispositivos que cumplan los requisitos puedan tener acceso al correo electrónico y los datos de la empresa en SharePoint Online y otros servicios."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab45292734c39d3eaf4a5f0403cbff6e77d9d7e6
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="protect-access-to-email-office-365-and-other-services-with-microsoft-intune"></a>Proteger el acceso al correo electrónico, a Office 365 y a otros servicios con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Puede proteger el acceso a su correo electrónico de empresa, a servicios de Office 365 como **Exchange local**, **Exchange Online**, **Exchange Online dedicado**, **SharePoint Online**, **Skype Empresarial Online**, y a otros servicios mediante el acceso condicional de Enterprise Mobility + Security (EMS). Esta característica le permite asegurarse de que el acceso al correo electrónico de la empresa y a los servicios de Office 365 está restringido a los dispositivos compatibles con las reglas de acceso condicional que establece en la consola de administración de Intune o en el Portal de Azure clásico.
## <a name="how-does-conditional-access-work"></a>¿Cómo funciona el acceso condicional?
Puede usar la configuración de la directiva de cumplimiento para evaluar el cumplimiento del dispositivo. La directiva de acceso condicional usa la evaluación para restringir o permitir el acceso a un servicio específico. Cuando usa una directiva de acceso condicional en combinación con una directiva de cumplimiento de dispositivos, solo podrán tener acceso al servicio los dispositivos compatibles. La directiva de cumplimiento y de acceso condicional se implementan en el usuario. Cualquier dispositivo que utilice el usuario para tener acceso a los servicios se somete a comprobaciones para verificar que cumple con las directivas.

> [!IMPORTANT]
> Tenga en cuenta que el usuario que usa el dispositivo debe tener implementada una directiva de cumplimiento para que se pueda evaluar el cumplimiento del dispositivo.
> Si no se implementa ninguna directiva de cumplimiento en el usuario, el dispositivo se considera conforme y no se aplicarán restricciones de acceso.

Cuando los dispositivos no cumplen las condiciones establecidas en las directivas, se indica al usuario final el proceso que debe seguir para inscribir el dispositivo y corregir el problema que impide que cumpla los requisitos.

Flujo típico de acceso condicional:

![Diagrama que muestra los puntos de decisión usados para determinar si un dispositivo puede tener acceso a un servicio o si se bloquea](../media/ConditionalAccess4.png)

## <a name="setup-considerations"></a>Consideraciones sobre la configuración

### <a name="licensing"></a>Licencias

Microsoft Intune y Azure Active Directory (Azure AD) Premium funcionan sin problemas conjuntamente para proporcionar varias capas de control a través del acceso condicional de EMS. Si quiere implementar directivas de acceso condicional con Intune, se le solicitará que tenga licencia para ambos productos.

Las **licencias de Azure AD Premium** pueden comprarse como un servicio independiente o pueden comprarse (junto con Intune) como parte de un contrato Enterprise. Si ha implementado directivas de acceso condicional con Intune, asegúrese de que ha obtenido las **licencias de EMS** o de Azure AD Premium correctas.

- Más información sobre la [página de precios de Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) o la [página de precios de Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

Además, asegúrese de que a los usuarios que planea que van a aplicar directivas de acceso condicional se les hayan [asignado licencias de EMS o de Azure AD Premium](/intune/licenses-assign).

### <a name="device-compliance-settings"></a>Configuración de cumplimiento de dispositivos

Para configurar el acceso condicional, configure una directiva de cumplimiento del dispositivo y una directiva de acceso condicional. La directiva de cumplimiento incluye opciones como el código de acceso, el cifrado y si el dispositivo está liberado o no. El dispositivo debe cumplir estas reglas para que se considere conforme.

- Obtenga más información sobre la [directiva de cumplimiento de dispositivos y su funcionamiento](introduction-to-device-compliance-policies-in-microsoft-intune.md).

### <a name="conditional-access-policy"></a>Directiva de acceso condicional

Puede establecer una directiva de acceso condicional para proteger el acceso en función de lo siguiente:
- El estado de cumplimiento del dispositivo.
- La plataforma en la que se ejecuta el dispositivo.
- El tipo de aplicaciones que se usan para tener acceso a los servicios.

A diferencia de otras directivas de Intune, no se implementan directivas de acceso condicional. En su lugar, después de configurar la directiva y seleccionar los usuarios que deben tenerla, la directiva se aplica a todos los usuarios de destino. Cuando un usuario es destinatario de una directiva, cada dispositivo que use debe ser conforme con el fin de que obtengan acceso a los recursos.


## <a name="next-steps"></a>Pasos siguientes


2. [Crear una directiva de cumplimiento de dispositivos](create-a-device-compliance-policy-in-microsoft-intune.md).

2.  Crear una directiva de acceso condicional para uno de los siguientes productos o servicios de la nube de Microsoft:

  - [Crear una directiva de acceso condicional para Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Crear una directiva de acceso condicional para Exchange local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Crear una directiva de acceso condicional para el nuevo entorno de Exchange Online dedicado](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Crear una directiva de acceso condicional para Exchange Online dedicado heredado](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Crear una directiva de acceso condicional para SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Crear una directiva de acceso condicional para Skype Empresarial Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [Crear una directiva de acceso condicional para Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
