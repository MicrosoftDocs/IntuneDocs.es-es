---
title: Configuración básica de Microsoft Intune
description: En este artículo se indican los pasos necesarios para configurar Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: a9f16c563ff0416092abe3812b3505c2f6d92587
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61512906"
---
# <a name="basic-setup"></a>Configuración básica

Después de evaluar el entorno, ha llegado la hora de configurar Microsoft Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Dependencias externas para una implementación de Intune

### <a name="identity"></a>Identidad

Intune exige Azure Active Directory (AAD) como proveedor de agrupaciones de identidades y de usuarios. Más información acerca de:

-  [¿Requisitos de identidad?](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

-   [Requisitos de sincronización de directorios](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

-   [Multi-Factor Authentication (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

-   [Planeación de grupos de usuarios y dispositivos](users-add.md)

-   [Creación de grupos de usuarios y dispositivos](groups-get-started.md)

Si su organización ya usa Office 365, Intune debe usar el mismo entorno de Azure Active Directory.

### <a name="pki-optional"></a>PKI (opcional)

Si piensa usar autenticación basada en certificados para perfiles de VPN, Wi-Fi o correo electrónico con Intune, tendrá que asegurarse de que tiene una [infraestructura PKI específica](certificates-configure.md) lista para crear e implementar perfiles de certificado. Obtenga más información sobre la configuración de certificados en Intune:

-   [Cómo configurar la infraestructura de certificados para SCEP](/intune/certificates-scep-configure).

-   [Cómo configurar la infraestructura de certificados para PFX](/intune/certficates-pfx-configure).


## <a name="task-list-for-an-intune-setup"></a>Lista de tareas para una configuración de Intune

### <a name="task-1-intune-subscription"></a>Tarea 1: Suscripción a Intune

Para poder migrar a Intune, necesita primero una suscripción a Intune.

-   Puede visitar [esta página](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0), que le ofrece instrucciones sobre cómo:

    -   Crear una suscripción a Intune vinculada a un nuevo inquilino de AAD.

    -   Vincular la suscripción a Intune iniciando sesión en un inquilino existente de AAD.

### <a name="task-2-assign-intune-user-licenses"></a>Tarea 2: Asignación de licencias de usuario de Intune

-   Aprenda a [asignar licencias de usuario de Intune](licenses-assign.md).

-   Si ha creado un inquilino de Azure Active Directory, aprenda a [crear otros usuarios o a sincronizar un usuario desde su Active Directory (AD) local.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Tarea 3: Establecer Intune como entidad de MDM

Intune puede administrarse mediante el portal de Azure o la consola de la rama actual de Configuration Manager. Salvo que tenga que integrar Intune con una implementación de la rama actual de Configuration Manager, le recomendamos que administre Intune desde [Azure Portal](https://portal.azure.com).

Establezca **Intune** como entidad de MDM para habilitar el portal de Intune Azure. El uso de otra entidad de MDM permite a Intune transferir la administración de MDM a consolas de administración de Microsoft alternativas. Estos casos no son frecuentes.

> [!IMPORTANT]
> Si va a transferir la administración de dispositivos móviles a Intune por primera vez, debe establecer Intune como entidad de MDM.

Aprenda a [establecer la entidad de administración de dispositivos móviles](mdm-authority-set.md).

## <a name="next-step"></a>Paso siguiente

Configure las [directivas de administración de dispositivos y aplicaciones](migration-guide-configure-policies.md).
