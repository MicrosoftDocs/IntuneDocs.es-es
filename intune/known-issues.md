---
title: "Problemas conocidos de la versión preliminar de Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: lea acerca de los problemas conocidos de la versión preliminar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 36b35e5311f6262c545a266003fb72b2febb277c
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Problemas conocidos de la versión preliminar de Microsoft Intune


[!INCLUDE[azure_preview](./includes/azure_preview.md)]


Use este tema para aprender sobre los problemas conocidos de la versión preliminar de Intune.

Si quiere notificar un error que no aparece aquí, [abra una solicitud de soporte técnico](https://docs.microsoft.com/intune-classic/troubleshoot/get-support).

Si quiere solicitar que se agregue una nueva característica a Intune, considere la posibilidad de presentar un informe en nuestro sitio [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Los grupos creados por Intune durante la migración pueden afectar a la funcionalidad de otros productos de Microsoft

Al migrar de Intune clásico a Azure Portal, es posible que vea un nuevo grupo denominado **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421**. Tenga en cuenta que este grupo contiene todos los usuarios de Azure Active Directory, no solo los usuarios con licencia de Intune. Esto podría causar problemas con otros productos de Microsoft si espera que algunos usuarios nuevos o existentes no sean miembros de los grupos.

### <a name="altering-groups-created-by-intune-during-migration-will-delay-migration"></a>Modificar los grupos creados por Intune durante la migración retrasará la migración

Para preparar la migración, los grupos se copiarán de Intune a Azure AD. Los cambios posteriores que realice en el portal de Intune clásico se actualizarán en el grupo de Azure AD. Sin embargo, los cambios realizados en Azure AD no se volverán a sincronizar en la consola de Intune clásica. Esto puede provocar que se produzca un error en la migración de Azure Portal y que se retrase la migración.

### <a name="compliance-policies-from-intune-will-not-show-up-in-new-console"></a>Las directivas de cumplimiento de Intune no aparecerán en la nueva consola.

Las directivas de cumplimiento que creó en el portal de Intune clásico se migran, pero no se muestran en Azure Portal. Esto debe a un cambio de diseño en Azure Portal. Las directivas de cumplimiento creadas en el portal de Intune clásico siguen siendo aplicables, pero debe verlas y editarlas en el portal clásico.
Además, las nuevas directivas de cumplimiento en Azure Portal no estarán visibles en el portal clásico.
Para obtener más información, consulte [¿Qué es el cumplimiento del dispositivo?](device-compliance.md)




### <a name="administration-and-accounts"></a>Administración y cuentas

Los administradores globales (también denominados administradores de inquilinos) pueden seguir realizando tareas de administración cotidianas sin una licencia independiente de Intune o Enterprise Mobility Suite (EMS). Sin embargo, si los administradores globales quieren usar el servicio, por ejemplo para inscribir sus dispositivos, un dispositivo de la empresa o para usar el Portal de empresa de Intune, necesitarán una licencia de Intune o EMS igual que cualquier otro usuario.

### <a name="apple-enrollment-profile-migration"></a>Migración de perfiles de inscripción de Apple
En los próximos meses, Intune permitirá administrar las inscripciones de Apple Configurator y el programa de inscripciones de dispositivos de Apple mediante el nuevo Azure Portal. Si elimina el token del programa de inscripción de dispositivos de Apple y no carga uno actualizado, el original se restaurará en el nuevo Azure Portal como parte del proceso de migración de su cuenta de Intune. Para quitar este token y evitar la inscripción de DEP, simplemente elimine el token en Azure Portal. 

### <a name="rbac-for-apple-corporate-owned-device-enrollment"></a>RBAC para inscripción de dispositivos Apple de propiedad corporativa
Los roles de inquilino o administrador de dispositivos de Azure AD son necesarios para realizar tareas de incorporación de DEP de Apple y Apple Configurator a pesar de que los permisos de RBAC aparecen listados y están disponibles en el rol de usuario personalizado. La compatibilidad del rol RBAC con estas características se anunciarán en el futuro.

