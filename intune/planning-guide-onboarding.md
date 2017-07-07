---
title: "Proceso de la incorporación de Intune"
description: "Este artículo le ayuda con todos los detalles que necesita tener en cuenta a la hora de incorporar la solución solo en la nube de Intune en su entorno."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ade7caf544d71c062c0fa251d7a113facb700a36
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="intune-implementation"></a>Implementación de Intune

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Durante la fase de incorporación, implementará Intune en su entorno de producción. El proceso de implementación consistirá en la instalación y configuración de Intune y de las dependencias externas (si es necesario), basándose en sus [requisitos de casos de uso](planning-guide-requirements.md) que se revisaron en las secciones anteriores de esta guía.

En la siguiente sección se proporciona una información general del proceso de implementación de Intune que incluye requisitos y tareas de alto nivel.

>[!TIP]
> Vea [Recursos adicionales](planning-guide-resources.md) para obtener más información sobre el proceso de implementación de Intune.

## <a name="intune-requirements"></a>Requisitos de Intune

Los requisitos principales de Intune independiente se proporcionan a continuación:

-   Suscripción a Intune o EMS

-   Suscripción a Office 365 (para aplicaciones de Office y aplicaciones administradas de directivas de MAM)

-   Certificado de APNs de Apple (para habilitar la administración de plataforma de dispositivos iOS)

-   Azure AD Connect (para la sincronización de directorios)

-   Conector local de Intune para Exchange (para CA para Exchange local, si es necesario)

-   Conector de certificado de Intune (para la implementación de certificado SCEP, si es necesario)

>[!TIP]
> Puede encontrar más información sobre los requisitos de Intune independiente [aquí](/intune/supported-devices-browsers).

## <a name="intune-implementation-process"></a>Proceso de implementación de Intune

### <a name="overview-of-implementation-tasks"></a>Información general de las tareas de implementación

Aquí se muestra información general de cada tarea a la hora de implementar Intune.

#### <a name="task-1-add-intune-subscription"></a>Tarea 1: Agregar una suscripción de Intune

Como se identificó en la sección de requisitos anterior, se necesita una suscripción de Intune o EMS. Si su organización no tiene una suscripción de Intune o EMS, póngase en contacto con Microsoft o con el equipo de cuentas de Microsoft con respecto a su interés en comprar Enterprise Mobility + Security (EMS) o Intune.

-   Más información sobre [cómo comprar Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing).

#### <a name="task-2-add-office-365-subscription"></a>Tarea 2: Agregar una suscripción de Office 365

Este paso es opcional. Como se identificó en la sección de requisitos anterior, se necesita una suscripción de Office 365 si planea usar Exchange Online y administrar aplicaciones móviles de Office con una directiva de MAM. Si su organización no tiene una suscripción de Office 365, póngase en contacto con Microsoft o con el equipo de cuentas de Microsoft con respecto a su interés en comprar Office 365.

-   Más información sobre [cómo comprar Office 365](https://products.office.com/business/compare-office-365-for-business-plans).

#### <a name="task-3-add-users-groups-in-azure-ad"></a>Tarea 3: Agregar grupos de usuarios en Azure AD

Puede que necesite agregar usuarios o grupos de seguridad en AD o AAD basándose en sus escenarios de casos de uso de implementación de Intune y en los requisitos. Debe revisar sus usuarios y grupos de seguridad actuales en Active Directory o Azure Active Directory, y determinar si satisfacen completamente sus necesidades. Los usuarios y los grupos de seguridad nuevos se agregan normalmente en Active Directory y se sincronizan en Azure Active Directory mediante Azure AD Directory Connect.

-   Más información sobre [cómo agregar usuarios o grupos en Intune](users-permissions-add.md).

#### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>Tarea 4: Asignar licencias de usuario de Office 365 e Intune

Todos los usuarios que están destinados a la implementación de Office 365 y EMS o Intune necesitarán tener una licencia asignada. La asignación de licencia de Office 365 y EMS o Intune puede realizarse en el Portal del Centro de administración de Office 365.

-   Más información sobre [cómo asignar licencias de Intune](licenses-assign.md).

#### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>Tarea 5: Establecer la entidad de administración de dispositivos móviles en Intune

Antes de que pueda comenzar la instalación, configuración, administración e inscripción de dispositivos con Intune, debe establecer la entidad de administración de dispositivos en Intune. El establecimiento de la tarea de la entidad de administración de dispositivos se completa en el Portal de administración de Intune, en el área de trabajo Administración.

-   Más información sobre [cómo establecer la entidad de administración de dispositivos](/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority).

#### <a name="task-6-enable-device-platforms"></a>Tarea 6: Habilitar plataformas de dispositivos

De manera predeterminada, en la consola de administración de Intune, la mayoría de las plataformas de dispositivos están habilitadas, excepto para los dispositivos de Apple (iOS y Mac). Antes de que los dispositivos iOS puedan inscribirse y administrarse en Intune, la plataforma de dispositivos debe habilitarse. Habilitar la plataforma de dispositivos iOS consta de un proceso de tres pasos: crear y descargar el certificado APNs y cargar el certificado APNs en Intune.

-   Más información sobre [cómo funciona la instalación de la administración de dispositivos iOS y Mac](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).

#### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>Tarea 7: Agregar e implementar directivas de términos y condiciones

Microsoft Intune admite la adición e implementación de directivas de términos y condiciones. La adición e implementación de directivas de términos y condiciones se completa en el Portal de administración de Intune, en el área de trabajo Directiva. Agregue directivas de términos y condiciones según corresponda e impleméntelas en los grupos de destino basándose en los requisitos y casos de uso de la implementación de Intune.

-   Más información sobre [cómo agregar e implementar directivas de términos y condiciones](/intune-classic/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune).

#### <a name="task-8-add-and-deploy-configuration-policies"></a>Tarea 8: Agregar e implementar directivas de configuración

Microsoft Intune admite la adición e implementación de dos tipos de directivas de configuración, general y personalizada. La adición e implementación de directivas de configuración se completa en el Portal de administración de Intune, en el área de trabajo Directiva. Agregue directivas de configuración según corresponda e impleméntelas en los grupos de destino basándose en los requisitos y casos de uso de la implementación de Intune.

-   Más información sobre [cómo agregar e implementar directivas de configuración](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

#### <a name="task-9-add-and-deploy-resource-profiles"></a>Tarea 9: Agregar e implementar perfiles de recursos

Microsoft Intune admite los perfiles de VPN, Wi-Fi y correo electrónico. La adición e implementación de perfiles se completa en el Portal de administración de Intune, en el área de trabajo Directiva. Agregue perfiles de VPN, Wi-Fi y correo electrónico según corresponda e impleméntelos en los grupos de destino basándose en los requisitos y casos de uso de la implementación de Intune.

-   Más información sobre cómo [habilitar el acceso a los recursos de la empresa con Intune](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

#### <a name="task-10-add-and-deploy-apps"></a>Tarea 10: Agregar e implementar aplicaciones

Microsoft Intune admite la implementación de aplicaciones de almacén público, LOB y web. Además, se admite la administración de aplicaciones que tienen el SDK de Intune integrado asociándolas con directivas de MAM. La adición e implementación de aplicaciones se completa en el Portal de administración de Intune, en el área de trabajo Aplicación. La adición de directivas de MAM se completa en el Portal de administración de Intune, en el área de trabajo Directiva. Agregue aplicaciones según corresponda e impleméntelas en los grupos de destino basándose en los requisitos y casos de uso de la implementación de Intune.

-   Más información sobre cómo [agregar e implementar aplicaciones](/intune-classic/deploy-use/deploy-apps).

#### <a name="task-11-add-and-deploy-compliance-policies"></a>Tarea 11: Agregar e implementar directivas de cumplimiento

Microsoft Intune admite las directivas de cumplimiento. La adición e implementación de directivas de cumplimiento se completa en el Portal de administración de Intune, en el área de trabajo Directiva. Agregue directivas de cumplimiento según corresponda e impleméntelas en los grupos de destino basándose en los requisitos y casos de uso de la implementación de Intune.

-   Más información sobre las [directivas de cumplimiento](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

#### <a name="task-12-enable-conditional-access-policies"></a>Tarea 12: Habilitar las directivas de acceso condicional

Microsoft Intune admite el acceso condicional para Exchange Online y local, SharePoint Online, Skype Empresarial Online y Dynamics CRM Online. Habilite directivas de acceso condicional en el Portal de administración de Intune, en el área de trabajo Directiva. Habilite y configure el acceso condicional según corresponda basándose en los [requisitos y casos de uso de la implementación de Intune](planning-guide-requirements.md).

-   Más información sobre el [acceso condicional](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

#### <a name="task-13-enroll-devices"></a>Tarea 13: Inscripción de dispositivos

Intune admite las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows Escritorio y Windows Mobile. Inscriba plataformas de dispositivos móviles según corresponda basándose en los requisitos y casos de uso de la implementación de Intune.

-   Más información sobre [cómo inscribir dispositivos](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune).

>[!TIP]
> Consulte este [módulo de la sesión de Intune de la Academia virtual de Microsoft](https://mva.microsoft.com/training-courses/deploying-microsoft-enterprise-mobility-suite-16408?l=PPWNoZxvD_1404778676) para obtener más información sobre el proceso de implementación de Intune.

## <a name="next-section"></a>Sección siguiente

En la sección siguiente se proporcionan instrucciones sobre las [pruebas y validación de la implementación de Intune](planning-guide-test-validation.md).
