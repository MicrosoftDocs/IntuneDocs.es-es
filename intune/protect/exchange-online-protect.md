---
title: Exchange sin administración de dispositivos
titleSuffix: Microsoft Intune
description: Use Microsoft Intune para permitir que los empleados tengan acceso al correo electrónico de Office 365 Exchange Online sin necesidad de configurar un sistema de administración de dispositivos.
keywords: Acceso al correo electrónico de Office 365 Exchange
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2017
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.topic: archived
ms.technology: ''
ms.assetid: 88a0d3b9-2622-403b-8374-1396afd8066e
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ac670fd5e17462688fdfcde1b047e1071a49353a
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515210"
---
# <a name="protect-office-365-exchange-online-without-requiring-device-management"></a>Proteger Office 365 Exchange Online sin requerir la administración de dispositivos

Si quiere permitir que los empleados accedan a su correo electrónico del trabajo evitando la incomodidad de tener que configurar un sistema de administración de dispositivos, ahora puede hacerlo. Puede conceder acceso a Office 365 Exchange Online a través de Intune. Para completar los pasos necesarios, confirme que tiene licencias para Microsoft 365 o Azure Active Directory (Premium) e Intune. Los empleados necesitan tener un [dispositivo iOS/iPadOS o Android compatible](../fundamentals/supported-devices-browsers.md). 

Si decide configurar un sistema de administración de dispositivos, también puede hacerlo. Este tipo de protección de aplicaciones funciona independientemente de la administración de dispositivos. 

## <a name="action-plan"></a>Plan de acción

1. [Obtenga información sobre el acceso condicional](conditional-access.md). 
2. [Obtenga información sobre el acceso condicional basado en la aplicación](app-based-conditional-access-intune.md).
3. [Configure directivas de acceso condicional basado en la aplicación para Exchange Online](app-based-conditional-access-intune-create.md).
4. [Bloquee las aplicaciones que no se pueden administrar](app-modern-authentication-block.md), específicamente las que no usan Azure Active Directory Authentication Library (ADAL).
5. [Configure directivas de acceso condicional basado en la aplicación para SharePoint Online](app-based-conditional-access-intune-create.md) (opcional). Estas directivas bloquean el acceso a los datos de la empresa desde las aplicaciones que no pueden administrarse ni protegerse. También limitan el acceso a través de SharePoint para dispositivos móviles. 

## <a name="what-to-tell-employees-and-students"></a>Qué decir a los empleados o estudiantes

* Pida a los empleados o alumnos que descarguen e instalen Microsoft Outlook o Microsoft SharePoint para iOS/iPadOS desde App Store de Apple o para Android desde Google Play Store. 
* Si bloquea el acceso a las aplicaciones que no usan la autenticación moderna, informe de esta restricción a los empleados o estudiantes. 

## <a name="next-steps"></a>Pasos siguientes

Ha usado el acceso condicional basado en la aplicación para aumentar la seguridad de los datos de la empresa. Como parte de los pasos siguientes, puede obtener más información sobre otras maneras de aumentar la protección de los datos de su empresa, como, por ejemplo: 

* Configurar el [acceso condicional basado en el cumplimiento, el riesgo y la ubicación del dispositivo, así como los atributos de usuario en Active Directory y Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).  
* Configurar directivas de protección de aplicaciones para ayudar a proteger los datos de su empresa de la pérdida de datos de forma intencionada o involuntaria. 
* Aprovechar Azure Information Protection para proteger los datos de la empresa fuera de su red. 

¿Necesita ayuda para habilitar este u otros escenarios de EMS u Office 365? Si tiene al menos 150 licencias para Microsoft 365, Enterprise Mobility + Security o Azure Active Directory Premium, aproveche las [ventajas de FastTrack](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 
