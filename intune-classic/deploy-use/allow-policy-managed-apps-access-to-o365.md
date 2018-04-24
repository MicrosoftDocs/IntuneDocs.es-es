---
title: Acceso condicional basado en aplicación a Office 365
description: Comprenda los conceptos de cómo el acceso condicional para MAM puede ayudar a controlar qué aplicaciones tienen acceso a los servicios de Office 365.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/05/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1f9446da0f553dca29bbfd96b99711c895cd8533
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="allow-only-mobile-apps-that-support-intune-app-protection-policies-to-access-office-365-services"></a>Permitir solo aplicaciones móviles que admitan directivas de protección de aplicaciones de Intune para obtener acceso a servicios de Office 365

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

[Las directivas de protección de aplicaciones de Intune](protect-apps-and-data-with-microsoft-intune.md) ayudan a proteger los datos de la empresa en dispositivos inscritos para administración en Intune. También puede usar directivas de protección de aplicaciones en **dispositivos que poseen los empleados que no están inscritos para administración en Intune**.  En este caso, aunque no administre el dispositivo, deberá asegurarse de que los datos y los recursos de la empresa están protegidos. Al usar el acceso condicional basado en la aplicación con MAM, puede crear una directiva que permita que solo las aplicaciones móviles que admiten directivas de protección de aplicaciones de Intune tengan acceso a servicios de Office 365 como Exchange Online.

Por ejemplo, al permitir que solo la **aplicación Microsoft Outlook** acceda a Exchange Online, puede **bloquear las aplicaciones de correo integradas en iOS y Android**, que no tienen protección de datos desde las directivas MAM de Intune para obtener correo electrónico desde **Exchange Online**. O bien puede bloquear el acceso de aplicaciones móviles que no tienen compatibilidad con MAM de Intune a **SharePoint Online**.

El diagrama siguiente muestra el flujo que usan las directivas de acceso condicional basado en la aplicación para determinar cuándo permitir o bloquear el acceso: ![Diagrama que muestra los diversos criterios incluidos para determinar si permitir o bloquear el acceso](../media/mam-ca-decision-flow_simple.png).

Descripción de las abreviaturas usadas en los diagramas:
* **CP**: aplicación de Portal de empresa
* **AA**: Autenticador de Azure
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>Requisitos previos
**Antes** de crear una directiva de acceso condicional basado en la aplicación, debe tener una **suscripción premium de Enterprise Mobility + Security o de Azure Active Directory** y los usuarios deben tener la licencia de EMS o Azure AD. Para obtener más detalles, vea la [página de precios de Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) o la [página de precios de Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).


## <a name="supported-apps"></a>Aplicaciones compatibles
**Exchange Online**:
* **Microsoft Outlook** para Android e iOS.

**SharePoint Online**
* Microsoft Word para iOS y Android
* Microsoft Excel para iOS y Android
* Microsoft PowerPoint para iOS y Android
* Microsoft OneDrive para la Empresa para iOS y Android
* Microsoft OneNote para iOS

>[!IMPORTANT]
>En el caso de los dispositivos Android, el registro de dispositivo inicial se debe hacer iniciando sesión en la aplicación OneDrive o Outlook. La aplicación OneNote para Android todavía no es compatible con MAM sin inscripción.

Para información sobre la experiencia del usuario con una aplicación que tiene directivas de acceso condicional basado en la aplicación, consulte [¿Qué se puede esperar al usar una aplicación con acceso condicional basado en la aplicación?](use-apps-with-mam-ca.md).


## <a name="next-steps"></a>Pasos siguientes
[Creación de una directiva de Exchange Online para aplicaciones MAM](mam-ca-for-exchange-online.md)

[Creación de una directiva de SharePoint Online para aplicaciones MAM](mam-ca-for-sharepoint-online.md)

[Bloqueo de aplicaciones que no usan la autenticación moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Vea también

[Protección de datos de aplicaciones con directivas de protección de aplicaciones](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
