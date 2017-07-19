---
title: "Introducción a Intune en Azure Portal"
titleSuffix: Intune on Azure
description: "Conozca los conceptos básicos sobre Intune en Azure Portal y cómo puede ayudarle a administrar sus dispositivos\"."
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 06/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7549f3277c23c3951090502f2babfe7c47b0a201
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Introducción a Microsoft Intune en Azure Portal


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune ahora está en Azure Portal, lo que significa que los flujos de trabajo y la funcionalidad que conoce han cambiado.
El nuevo portal le ofrece una funcionalidad nueva y actualizada en Azure Portal, donde puede administrar los dispositivos móviles, los equipos y las aplicaciones de su organización.

> [!IMPORTANT]
> **¿Aún no puede ver el nuevo portal?**<br>
> Los inquilinos existentes se están migrando a la nueva experiencia. Se muestra una notificación en el Centro de mensajes de Office antes de la migración de su inquilino.
>
> Las cuentas de Intune creadas antes de enero de 2017 requieren una migración única antes de que los flujos de trabajo de inscripción de Apple estén disponibles en Azure. Todavía no se anuncia la programación de la migración. Si la cuenta existente no puede acceder a Azure Portal, se recomienda crear una cuenta de prueba.
>
> Revise la lista de posibles bloqueadores https://blogs.technet.microsoft.com/intunesupport/2017/05/17/intune-migration-blockers-for-grouping-targeting/


Puede encontrar información sobre el nuevo portal en esta biblioteca, la que se actualiza continuamente. Si tiene sugerencias que le gustaría ver, deje sus comentarios en la sección de comentarios sobre el tema. Queremos saber su opinión.

Algunos de los aspectos destacables de la nueva experiencia son:

- Consola integrada para todos los componentes de Enterprise Mobility + Security (EMS)
- Consola basada en HTML basada en estándares web
- Soporte técnico de la API de Microsoft Graph para automatizar muchas acciones
- Grupos de Azure Active Directory (AD) para proporcionar compatibilidad entre todas las aplicaciones de Azure
- Compatibilidad con la mayoría de los exploradores web más modernos

Si busca documentación sobre la consola de Intune clásica, vea [la biblioteca de documentación de Intune](https://docs.microsoft.com/intune-classic/).

## <a name="before-you-start"></a>Antes de empezar

Para usar Intune en el portal de Azure, debe tener una cuenta de administrador y de inquilino de Intune. [Regístrese para obtener una cuenta](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) si todavía no tiene una.

## <a name="supported-web-browsers-for-the-azure-portal"></a>Exploradores web admitidos en el portal de Azure

El portal de Azure funciona en la mayoría de equipos PC, Mac y tabletas más modernos. No es compatible con teléfonos móviles.
Actualmente, se admiten los siguientes exploradores:

- Microsoft Edge (última versión)
- Microsoft Internet Explorer 11
- Safari (solo en Mac, última versión)
- Chrome (última versión)
- Firefox (última versión)

Para obtener la información más reciente sobre los exploradores admitidos, vea [Azure Portal](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices).

## <a name="whats-in-this-library"></a>¿Qué hay en esta biblioteca?

La documentación refleja el diseño del portal de Intune para que resulte más fácil encontrar la información que necesita.

![Cargas de trabajo del portal de Azure](./media/azure-portal-workloads.png)

### <a name="introduction-and-get-started"></a>Introducción y empezar a trabajar
En esta sección se encuentra [información de introducción](introduction-intune.md) que le permite comenzar a usar Intune.
### <a name="plan-and-design"></a>Planeamiento y diseño
Información para ayudarlo a [planear y diseñar](/intune-classic/plan-design/introduction) su entorno Intune.
### <a name="device-enrollment"></a>Inscripción de dispositivos
[Cómo administrar sus dispositivos con Intune](device-enrollment.md).
### <a name="device-compliance"></a>Cumplimiento de dispositivos
[Defina un nivel de cumplimiento para sus dispositivos y, luego, notifique los dispositivos que no son conformes](device-compliance.md).
### <a name="device-configuration"></a>Configuración de los dispositivos
[Obtenga información sobre los perfiles que puede usar para configurar opciones y características en los dispositivos que administra](device-profiles.md).
### <a name="devices"></a>Dispositivos
[Conozca los dispositivos que administra con inventarios e informes](device-management.md).
### <a name="mobile-apps"></a>Aplicaciones móviles
[Cómo publicar, administrar, configurar y proteger las aplicaciones](app-management.md).
### <a name="conditional-access"></a>Acceso condicional
[Restrinja el acceso a los servicios de Exchange en función de las condiciones que especifique](conditional-access.md).
### <a name="on-premises-access"></a>Acceso local
[Configure el acceso a Exchange ActiveSync y a Exchange local](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)
### <a name="users"></a>Usuarios
[Obtenga información sobre los usuarios de dispositivos que administra y clasifique recursos en grupos](user-management.md).
### <a name="groups"></a>Grupos
[Obtenga información acerca de cómo usar grupos de Azure Active Directory con Intune](groups-get-started.md)
### <a name="intune-roles"></a>Roles de Intune
[Controle quién puede realizar diversas acciones de Intune y a quién se aplican esas acciones](role-based-access-control.md). Puede usar los roles integrados que abarcan algunos escenarios de Intune comunes, o crear los suyos propios.
### <a name="software-updates"></a>Actualizaciones de software
[Obtenga información acerca de cómo configurar las actualizaciones de software para dispositivos Windows 10](windows-update-for-business-configure.md).



## <a name="whats-new"></a>Novedades

[Conozca las novedades de Intune](whats-new.md).
