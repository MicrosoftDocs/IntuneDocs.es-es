---
title: "Configuración básica de Intune | Microsoft Docs"
description: "El propósito de este artículo es indicar los pasos necesarios para configurar Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: b01b68b7587cb91f24285cdffafeab43296886e6
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-basic-setup"></a>Fase 1: Configuración básica

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Después de evaluar el entorno, ha llegado la hora de configurar Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Dependencias externas para una implementación de Intune

### <a name="identity"></a>Identidad

Intune exige Azure Active Directory (AAD) como proveedor de agrupaciones de identidades y de usuarios.

-   Más información sobre los [requisitos de identidad](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview).

-   Más información sobre los [requisitos de sincronización de directorios](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements).

-   Más información sobre los [requisitos de Multi-factor Authentication](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements).

-   Más información sobre la [planeación de grupos de usuarios y dispositivos](https://docs.microsoft.com/intune/deploy-use/plan-your-user-and-device-groups).

-   Más información sobre [cómo crear grupos de usuarios y dispositivos](https://docs.microsoft.com/en-us/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

Si su organización ya está usando Office 365, es importante que Intune use el mismo entorno de Azure Active Directory.

### <a name="pki-optional"></a>PKI (opcional)

Si piensa usar autenticación basada en certificados para perfiles de VPN, Wi-Fi o correo electrónico con Intune, tendrá que asegurarse de que tiene una [infraestructura PKI específica](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles) lista para crear e implementar perfiles de certificado.

A continuación se ofrece más información sobre la configuración de certificados en Intune.

-   [Cómo configurar la infraestructura de certificados para SCEP](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep).

-   [Cómo configurar la infraestructura de certificados para PFX](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-pfx).

-   [Cómo configurar perfiles de certificado de Intune](archivo:///C:/intune/deploy-use/https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles).

-   [Cómo configurar directivas de acceso de recursos](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

## <a name="task-list-for-an-intune-setup"></a>Lista de tareas para una configuración de Intune

### <a name="task-1-intune-subscription"></a>Tarea 1: Suscripción a Intune

Para poder migrar a Intune, necesita primero una suscripción a Intune.

-   Puede visitar [esta página](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0), que le ofrece instrucciones sobre cómo:

    -   Crear una suscripción a Intune vinculada a un nuevo inquilino de AAD.

    -   Vincular la suscripción a Intune iniciando sesión en un inquilino existente de AAD.

### <a name="task-2-assign-intune-user-licenses"></a>Tarea 2: asignar licencias de usuario de Intune

-   Aprenda a [asignar licencias de usuario de Intune](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).

-   Si ha creado un inquilino de Azure Active Directory, aprenda a [crear otros usuarios o a sincronizar un usuario desde su Active Directory (AD) local.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Tarea 3: Establecer Intune como entidad de MDM

Intune puede administrarse mediante el Portal de Azure o la consola de rama actual de Configuration Manager. Salvo que tenga que integrar Intune con una implementación de la rama actual de Configuration Manager, se recomienda administrar Intune desde el [Portal Azure](https://portal.azure.com).

Establezca **Intune** como entidad de MDM para habilitar el Portal de Intune Azure. El uso de otra entidad de MDM permite a Intune transferir la administración de MDM a consolas de administración de Microsoft alternativas. Estos casos no son frecuentes.

> [!IMPORTANT]
> Si va a transferir la administración de dispositivos móviles a Intune por primera vez, debe establecer Intune como entidad de MDM.

-   Aprenda a [establecer la entidad de administración de dispositivos móviles](https://docs.microsoft.com/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority).

## <a name="next-step"></a>Paso siguiente

[Fase 1: Configurar las directivas de administración de dispositivos y aplicaciones](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-device-and-app-management-policies)

