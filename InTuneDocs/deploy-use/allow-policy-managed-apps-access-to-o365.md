---
title: "Acceso condicional basado en aplicación con Office 365 | Microsoft Docs"
description: "Comprenda los conceptos de cómo el acceso condicional para MAM puede ayudar a controlar qué aplicaciones tienen acceso a los servicios de Office 365."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 2babdeaaf10e9a58716d299cbde0babe45967fb1


---

# <a name="allow-only-mobile-apps-that-support-intune-mam-policies-to-access-office-365-services"></a>Permitir solo aplicaciones móviles que admitan directivas MAM de Intune para acceder a servicios de Office 365

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[Las directivas de administración de aplicaciones móviles (MAM) de Intune](protect-apps-and-data-with-microsoft-intune.md) ayudan a proteger los datos de su compañía en dispositivos inscritos para administración de Intune. También puede utilizar directivas MAM en **dispositivos que poseen los empleados que no están inscritos para la administración de Intune**.  En este caso, aunque no administre el dispositivo, deberá asegurarse de que los datos y los recursos de la empresa están protegidos. Al usar el acceso condicional para MAM (CA MAM), puede crear una directiva que permita que solo las aplicaciones móviles que admiten directivas MAM de Intune tengan acceso a servicios de Office 365 como Exchange Online.

Por ejemplo, al permitir que solo la **aplicación Microsoft Outlook** acceda a Exchange Online, puede **bloquear las aplicaciones de correo integradas en iOS y Android**, que no tienen protección de datos desde las directivas MAM de Intune para obtener correo electrónico desde **Exchange Online**.

El diagrama siguiente muestra el flujo que usan las directivas de CA de MAM para determinar cuándo permitir o bloquear el acceso: ![Diagrama que muestra los diversos criterios incluidos para determinar si permitir o bloquear el acceso ](../media/mam-ca-decision-flow_simple.png).

Descripción de las abreviaturas usadas en los diagramas:
* **CP**: aplicación de Portal de empresa
* **AA**: Autenticador de Azure
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>Requisitos previos
**Antes** de configurar una directiva de acceso condicional de MAM, debe tener una **suscripción de Enterprise Mobility + Security o de Azure Active Directory Premium** y los usuarios deben tener la licencia de EMS o Azure AD. Para obtener más detalles, vea la [página de precios de Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) o la [página de precios de Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).


## <a name="supported-apps"></a>Aplicaciones compatibles
**Exchange Online**: **Microsoft Outlook** para Android e iOS.

Para aprender sobre la experiencia del usuario con una aplicación que tiene directivas de CA MAM, consulte [¿Qué se puede esperar al usar una aplicación con el acceso condicional de MAM?](use-apps-with-mam-ca.md).


## <a name="next-steps"></a>Pasos siguientes
[Creación de una directiva de Exchange Online para aplicaciones MAM](mam-ca-for-exchange-online.md)

[Bloqueo de aplicaciones que no usan la autenticación moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Consulte también

[Proteger datos de aplicaciones mediante las directivas de MAM](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


