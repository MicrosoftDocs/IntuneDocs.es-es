---
title: Migrar grupos a Azure Active Directory | Microsoft Docs
description: "Migración de grupos de Intune a Azure AD"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 12/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 2296490a8c3984e79eeeb553d90591048ed46711
ms.lasthandoff: 04/14/2017


---

# <a name="a-new-way-of-using-groups-in-intune"></a>Una nueva manera de usar grupos en Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Hemos escuchado sus comentarios y estamos realizando algunos cambios sobre cómo trabaja con los grupos en Microsoft Intune.
Estamos en el proceso de migrar todos nuestros grupos de Intune de clientes a los grupos de seguridad de Azure Active Directory.

La ventaja es que ahora usará la misma experiencia de grupos en Enterprise Mobility + Security y en las aplicaciones de Azure AD. Además, podrá usar PowerShell y API Graph para extender y personalizar esta nueva función.

Los grupos de seguridad de Azure AD admiten todos los tipos de implementaciones de Intune para los usuarios y los dispositivos. Además, puede usar los grupos dinámicos de Azure AD que se actualizan automáticamente basándose en los atributos que proporcione. Por ejemplo, puede crear un grupo de dispositivos que ejecute iOS 9. Cuando un nuevo dispositivo que ejecute iOS 9 se inscriba, se agregará automáticamente al grupo dinámico.

## <a name="when-is-this-happening"></a>¿Cuándo va a suceder esto?

El proceso de migración se encuentra en curso ahora mismo. Se le notificará antes de que se realice su migración.
Si ya ha sido migrado, verá un mensaje similar a este cuando intente acceder a grupos desde la consola de Intune clásico:

![Mensaje para mostrar los grupos que se han migrado.](http://i.imgur.com/72KRaXj.png)

## <a name="what-wont-be-available"></a>¿Hay algo que no estará disponible?

Algunas características existentes de los grupos de Intune no están disponibles en Azure AD:

- Los grupos de Intune **Usuarios sin agrupar** y **Dispositivos sin agrupar** no se migrarán.
- La opción para **Excluir miembros específicos** de un grupo que existe actualmente en la consola de Intune no existe en Azure Portal. En cambio, puede usar un grupo de seguridad de Azure AD con reglas avanzadas para replicar este comportamiento. Por ejemplo, podría crear una regla avanzada que incluya a todas las personas del departamento de ventas en un grupo de seguridad, pero no a los usuarios que tengan la palabra "Assistant" (Asistente) en el nombre de su puesto, usando esta regla avanzada: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- El grupo **Todos los dispositivos administrados de Exchange ActiveSync** que está integrado en la consola de Intune no se migrará a Azure AD. En cambio, todavía puede acceder a la información sobre dispositivos administrados de EAS desde Azure Portal.
- No podrá filtrar los informes por grupos en la consola de Intune clásico.
<!--- - Custom group targeting of notification rules will not be available. ROB I took this out as I couldn't replicate the behavior. --->

## <a name="how-to-get-ready"></a>Cómo estar preparado

- Lea los siguientes temas de Azure AD para obtener información sobre los grupos de seguridad de Azure AD y su funcionamiento:
    -  [Administración del acceso a los recursos con grupos de Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/).
    -  [Administración de grupos en Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
- Considere la posibilidad de quitar cualquier grupo de Intune que ya no use antes de la migración.
-  Asegúrese de que cualquier administrador que necesite crear grupos se agregue al rol de Azure AD **Administrador del servicio de Intune**. Tenga en cuenta que el rol Administrador del servicio de Azure AD no tiene permisos de **Administrar grupo**.
-  Si usa grupos con la opción **Excluir miembros específicos**, considere si puede volver a diseñar estos grupos para que no necesiten exclusiones, o si puede usar reglas avanzadas en su consulta de Azure AD para conseguir el mismo resultado.


## <a name="what-happens-to-intune-groups"></a>¿Qué sucede con los grupos de Intune?

| Grupos de Intune|Grupo de Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Grupo de usuarios estáticos|Grupo de seguridad de Azure AD estático|
|Grupo de usuarios dinámicos|Grupos de seguridad estáticos de Azure AD con una jerarquía de grupos de seguridad de Azure AD|
|Grupo de dispositivos estáticos|Grupo de seguridad de Azure AD estático|
|Grupo de dispositivos dinámicos|Grupo de seguridad de Azure AD dinámico|
|Grupo con una condición de inclusión|El grupo de seguridad de Azure AD estático contiene cualquier miembro dinámico o estático de la condición de inclusión de Intune.|
|Grupo con una condición de exclusión|No se migra|
|Los grupos integrados, **Todos los usuarios**, **Usuarios sin agrupar**, **Todos los dispositivos**, **Dispositivos sin agrupar**, **Todos los equipos**, **Todos los dispositivos móviles**, **Todos los dispositivos administrados de MDM** y **Todos los dispositivos administrados de EAS**|Grupos de seguridad de Azure AD.|

En Intune, todos los grupos tienen que tener un grupo primario. Los grupos solo pueden contener miembros de su grupo primario. En Azure AD, los grupos secundarios pueden contener miembros que el grupo primario no tiene.

Los atributos son propiedades de dispositivos que se pueden usar para definir grupos. En esta tabla se describe cómo se migrarán estos criterios a grupos de seguridad de Azure AD.

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

## <a name="what-happens-to-policies-and-apps-youve-already-deployed"></a>¿Qué sucede con las directivas y las aplicaciones que ya ha implementado?

Las directivas y las aplicaciones siguen implementándose en grupos, como antes. En cambio, ahora administrará estos grupos desde Azure Portal en lugar de usar la consola de Intune clásico.
 

