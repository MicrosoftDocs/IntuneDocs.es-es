---
title: Grupos clásicos de Intune en Azure Portal
titleSuffix: Microsoft Intune
description: Conozca las novedades de los grupos en Azure Portal de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/31/2019
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e912c14418d54321b0998dad3081f297ae81114d
ms.sourcegitcommit: 55323746ca3c1c66326f1453ba66ded9c1b73b0e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58867439"
---
# <a name="microsoft-intune-classic-groups-in-the-azure-portal"></a>Grupos clásicos de Microsoft Intune en Azure Portal

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Hemos escuchado sus comentarios y hemos realizado algunos cambios sobre cómo trabaja con los grupos en Microsoft Intune.
Si usa Intune desde el portal de Azure, los grupos de Intune se han migrado a grupos de seguridad de Azure Active Directory.

La ventaja es que ahora usa la misma experiencia de grupos en Enterprise Mobility + Security y en las aplicaciones de Azure AD. Además, puede usar PowerShell y Graph API para extender y personalizar esta nueva función.

Los grupos de seguridad de Azure AD admiten todos los tipos de implementaciones de Intune para los usuarios y los dispositivos. Además, puede usar los grupos dinámicos de Azure AD que se actualizan automáticamente basándose en los atributos que proporcione. Por ejemplo, puede crear un grupo de dispositivos que ejecute iOS 9. Cuando se inscriba un dispositivo que ejecuta iOS 9, el dispositivo se muestra automáticamente en el grupo dinámico.

## <a name="what-is-not-available"></a>¿Qué características no están disponibles?

Algunas de las funcionalidades de los grupos que podría haber usado anteriormente no están disponibles en Azure AD:

- Los grupos de Intune **Usuarios sin agrupar** y **Dispositivos sin agrupar** ya no están disponibles.
- La opción para **excluir miembros específicos** de un grupo no existe en el portal de Azure. En cambio, puede usar un grupo de seguridad de Azure AD con reglas avanzadas para replicar este comportamiento. Por ejemplo, para crear una regla avanzada que incluya a todas las personas del departamento de ventas en un grupo de seguridad, pero excluya a esos grupos que tengan la palabra "Assistant" (Asistente) en el nombre de su puesto, puede usar esta regla avanzada:

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- El grupo **Todos los dispositivos administrados por Exchange ActiveSync** de la consola de Intune clásica no se ha migrado a Azure AD. En cambio, todavía puede acceder a la información sobre dispositivos administrados de EAS desde Azure Portal.

## <a name="how-to-get-started"></a>Cómo empezar

- Lea los siguientes temas para obtener información sobre los grupos de seguridad de Azure AD y su funcionamiento:
    -  [Administración del acceso a los recursos con grupos de Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/).
    -  [Administración de grupos en Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
-  Asegúrese de que los administradores que necesiten crear grupos se agreguen al rol de Azure AD **Administrador del servicio de Intune**. El rol Administrador del servicio de Azure AD no tiene permisos de **Administrar grupo**.
-  Si los grupos de Intune han usado la opción **Excluir miembros específicos**, decida si puede volver a diseñar estos grupos sin exclusiones, o si necesita reglas avanzadas para satisfacer las necesidades empresariales.


## <a name="what-happened-to-intune-groups"></a>¿Qué ha sucedido con los grupos de Intune?
Cuando los grupos se migran de Azure Portal a Intune en Azure Portal, se aplican las siguientes reglas:

| Grupos de Intune|Grupos en Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Grupo de usuarios estáticos|Grupo de seguridad de Azure AD estático|
|Grupo de usuarios dinámicos|Grupos de seguridad estáticos de Azure AD con una jerarquía de grupos de seguridad de Azure AD|
|Grupo de dispositivos estáticos|Grupo de seguridad de Azure AD estático|
|Grupo de dispositivos dinámicos|Grupo de seguridad de Azure AD dinámico|
|Grupo con una condición de inclusión|Grupo de seguridad de Azure AD estático que contiene cualquier miembro dinámico o estático de la condición de inclusión de Intune|
|Grupo con una condición de exclusión|No se migra|
|Los grupos integrados:<br>- **Todos los usuarios**<br>- **Usuarios no agrupados**<br>- **Todos los dispositivos**<br>- **Dispositivos no agrupados**<br>- **Todos los equipos**<br>- **Todos los dispositivos móviles**<br>- **Todos los dispositivos administrados de MDM**<br>- **Todos los dispositivos administrados de EAS**|Grupos de seguridad de Azure AD|

## <a name="group-hierarchy"></a>Jerarquía de grupos

En la consola de Intune, todos los grupos tienen un grupo primario. Los grupos solo pueden contener miembros de su grupo primario. En Azure AD, los grupos secundarios pueden contener miembros que no se incluyen en su grupo primario.

## <a name="group-attributes"></a>Atributos de grupo
Los atributos son propiedades de dispositivos que se pueden usar para definir grupos. En esta tabla se describe cómo se migran estos criterios a grupos de seguridad de Azure AD.

| Atributo en Intune|Atributo en Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Atributo de unidad organizativa (UO) para grupos de dispositivos|Atributo de UO para grupos dinámicos.|
|Atributo de nombre de dominio para grupos de dispositivos|Atributo de nombre de dominio para grupos dinámicos.|
|Grupo de seguridad como atributo de grupos de usuarios|Los grupos no pueden ser atributos en consultas dinámicas de Azure AD. Los grupos dinámicos solo pueden contener atributos específicos de dispositivo o de usuario.|
|Atributo de administrador para grupos de usuarios|Regla avanzada para el atributo *manager* en grupos dinámicos|
|Todos los usuarios del grupo de usuarios primario|Grupo estático con ese grupo como miembro|
|Todos los dispositivos móviles del grupo de dispositivos primario|Grupo estático con ese grupo como miembro|
|Todos los dispositivos móviles administrados por Intune|Atributo de tipo de administración con "MDM" como valor del grupo dinámico|
|Grupos anidados dentro de grupos estáticos |Grupos anidados dentro de grupos estáticos|
|Grupos anidados dentro de grupos dinámicos|Grupo dinámico con un nivel de anidamiento|

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>¿Qué sucede con las directivas y las aplicaciones que ya ha implementado?

Las directivas y las aplicaciones siguen implementándose en grupos, como antes. En cambio, ahora administra estos grupos desde Azure Portal en lugar de usar la consola de Intune.
