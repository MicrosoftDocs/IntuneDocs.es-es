---
title: Migrar grupos a Azure Active Directory | Microsoft Intune
description: "Migración de grupos de Intune a Azure AD"
keywords: 
author: nbigman
manager: angerobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
translationtype: Human Translation
ms.sourcegitcommit: d92c9ffe42b36770a32c28941de3c402aec9dd68
ms.openlocfilehash: 08bcc258f64e6385ae6fa648ddb8f2b5fe68942e


---

## La nueva experiencia de administración de grupos
    
Teniendo en cuenta los comentarios de tener una experiencia de agrupación y destino en Enterprise Mobility + Security, estamos convirtiendo los grupos de Intune en grupos de seguridad basados en Azure Active Directory. Esto unificará la administración de grupos en Intune y Azure Active Directory (Azure AD). La nueva experiencia le evitará tener que duplicar grupos entre servicios y le proporcionará extensibilidad mediante PowerShell y Graph. 

### ¿Cómo y cuándo migraré a la nueva experiencia de grupos?
Los clientes actuales migrarán en un período no anterior a diciembre de 2016. Recibirá un aviso antes de la migración de sus grupos. Si tiene alguna duda con respecto a la migración, póngase en contacto con nuestro equipo de migración en [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### ¿Qué características nuevas tendré disponibles?
Aquí se muestra la presentación de la nueva funcionalidad: 
 
-    Grupos de seguridad de Azure AD se admitirá en Intune para todos los tipos de implementaciones. 
-    Grupos de seguridad de Azure AD admitirá la agrupación de dispositivos con los usuarios.
-    Grupos de seguridad de Azure AD admitirá los grupos dinámicos con los atributos de dispositivos de Intune. Por ejemplo, podrá agrupar de manera dinámica dispositivos basándose en la plataforma, como iOS. De esta manera, cuando un nuevo dispositivo iOS se inscriba en su organización, automáticamente se agregará al grupo dinámico de dispositivos iOS.
-    Experiencias de administración compartidas para la administración de grupos en Azure AD e Intune.
- El *rol de administrador de servicios de Intune* se agregará a Azure AD para permitir que los administradores de servicios de Intune realicen tareas de administración de grupos en Azure AD.

 
### ¿Qué funcionalidad de Intune no estará disponible?
Aunque la experiencia de grupo mejorará, algunas funcionalidades de Intune no estarán disponibles después de la migración.

#### Funcionalidad de administración de grupos

-   No podrá excluir miembros ni grupos cuando cree un grupo nuevo. En cambio, los grupos dinámicos de Azure AD le permitirán usar atributos para crear reglas avanzadas para excluir miembros en función de criterios. Por ejemplo, podría crear una regla avanzada que incluya a todas las personas del departamento de ventas en un grupo de seguridad, pero no a los usuarios que tengan la palabra "Assistant" (Asistente) en el nombre de su puesto, con esta regla avanzada: `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`. Para obtener más información, consulte [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
-   No serán compatibles con los grupos **Usuarios sin agrupar** y **Dispositivos sin agrupar**. Esos grupos no se migrarán.

#### Funcionalidad dependiente del grupo

-   El rol de administrador de servicios no tendrá permisos de **Administrar grupos**.
-   No podrá agrupar dispositivos de Exchange ActiveSync.  Su grupo **Todos los dispositivos administrados de EAS** se convertirá de un grupo a una vista de informe.
-  Dinamizar con grupos en informes no estará disponible.
-  Grupo personalizado de destino de reglas de notificación no estará disponible.

### ¿Qué debería hacer para prepararme para este cambio?
 Tenemos algunas recomendaciones que le facilitarán la transición:
 
- Elimine cualquier grupo innecesario o no deseado de Intune antes de la migración.
- Evalúe el uso que hace de la exclusión en los grupos y considere cómo volver a diseñar los grupos de modo que no necesite usar la exclusión o que pueda usar reglas avanzadas para lograr el mismo propósito.
-  Si tiene administradores que no tienen permisos para crear grupos en Azure AD, solicite a su administrador de Azure AD agregarlos al rol **Administrador de servicios de Intune** de Azure AD.

También puede obtener más información sobre los grupos de seguridad de Azure AD:
-  Para ver una introducción, lea [Administración del acceso a los recursos con grupos de Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
-  Para obtener información sobre cómo crear y administrar grupos de Azure AD, consulte [Administración de grupos en Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/).
-  Para obtener más información sobre las reglas avanzadas para grupos de seguridad, consulte [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).

> [!NOTE]
Puede que observe que la documentación sobre grupos de seguridad de Azure AD no incluye la creación de grupos de dispositivos. Esta funcionalidad se habilitará en Azure AD antes de que empiece la migración de grupos de Intune.

## Detalles de la migración
A continuación se detalla la manera en que los grupos de Intune se migrarán a grupos de seguridad de Azure AD.

### Migración de grupos existentes

| El grupo de Intune se convierte en…|…Un grupo de seguridad de Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Grupos de usuarios estáticos a los que se aplica la directiva de Intune|Grupos de seguridad estáticos de Azure AD que contienen los mismos usuarios|
|Grupos de usuarios dinámicos a los que se aplica la directiva de Intune|Grupos de seguridad estáticos de Azure AD con una jerarquía de grupos de seguridad de Azure AD|
|Grupos de dispositivos estáticos a los que se aplica la directiva de Intune|Grupos de seguridad estáticos de Azure AD con dispositivos|
|Grupos de dispositivos dinámicos con atributos de dispositivo a los que se aplica la directiva de Intune|Grupos de seguridad dinámicos de Azure AD con atributos de dispositivo|
|Grupo con una condición de inclusión|Grupo de seguridad estático independiente de Azure AD que contendrá un grupo y los miembros estáticos o dinámicos que la condición de inclusión permitiera en Intune|
|Grupo con una condición de exclusión|No se migrará. Las condiciones de exclusión no se admiten durante la creación de grupos estáticos en Azure AD. Se puede usar una condición de exclusión al crear un grupo dinámico en Azure AD.|
|Grupos predeterminados **Todos los usuarios**, **Usuarios sin agrupar**, **Todos los dispositivos**, **Dispositivos sin agrupar**, **Todos los equipos**, **Todos los dispositivos móviles**, **Todos los dispositivos administrados de MDM** y **Todos los dispositivos administrados de EAS** que se usan en la directiva de Intune  |Grupos de seguridad de Azure AD. El cliente deberá crear los grupos predeterminados que no están en uso cuando los necesite mediante grupos dinámicos.|

### Cambios en las vistas jerárquicas
La vista jerárquica de los grupos en relaciones de tipo primario-secundario en Intune era una relación de superconjuntos y subconjuntos, mientras que en Azure AD no es el caso. Un elemento secundario puede tener miembros que el elemento primario no tenía. Los grupos también pueden tener una naturaleza cíclica en Azure AD; es decir, un grupo primario puede ser un elemento secundario de un grupo secundario.

### Conversión de atributos durante la migración
Los atributos son propiedades de dispositivos que se pueden usar para definir grupos. En esta tabla se describe cómo se migrarán estos criterios a grupos de seguridad de Azure AD.

| Atributo de Intune|Atributo de Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Atributo de unidad organizativa (UO) para grupos de dispositivos|Atributo de UO para grupos dinámicos. Valores de atributo que se ponen a disposición del administrador perteneciente a cada inquilino agregándolo como uno de los componentes de inquilino para la visualización.|
|Atributo de nombre de dominio para grupos de dispositivos|Atributo de nombre de dominio para grupos dinámicos. Valores de atributo que se ponen a disposición del administrador perteneciente a cada inquilino agregándolo como uno de los componentes de inquilino para la visualización.|
|Grupo de seguridad como atributo de grupos de usuarios|Los grupos no pueden ser atributos en consultas dinámicas de Azure AD. Los grupos dinámicos solo pueden contener atributos específicos de dispositivo o de usuario.|
|Atributo de administrador para grupos de usuarios|Regla avanzada para el atributo *manager* en grupos dinámicos|
|Todos los usuarios del grupo de usuarios primario|Grupo estático con ese grupo como miembro|
|Todos los dispositivos móviles del grupo de dispositivos primario|Grupo estático con ese grupo como miembro|
|Todos los dispositivos móviles administrados por la administración directa de Microsoft Intune|Atributo de tipo de administración con "MDM" como valor del grupo dinámico|
|Todos los dispositivos móviles administrados por EAS|Los dispositivos de EAS no se pueden agrupar en Azure AD. Su grupo **Todos los dispositivos administrados de EAS** se convertirá de un grupo a una vista de informe.|
|Grupos anidados dentro de grupos estáticos |Grupos anidados dentro de grupos estáticos|
|Grupos anidados dentro de grupos dinámicos|Grupo dinámico con un nivel de anidamiento|


## Migración de directivas
Mientras se lleva a cabo la migración de grupos, puede seguir administrando las directivas en la consola de Intune. Habrá un vínculo en la consola de Intune que le llevará a la consola de administración de Azure, donde administrará los grupos. Las directivas se seguirán implementando en los grupos de seguridad de Azure AD migrados equivalentes a los grupos de Intune antiguos.

Cuando toda la funcionalidad de Intune se haya migrado al Portal de administración de Azure (aproximadamente el primer trimestre de 2017), administrará allí las directivas y los grupos.

     
### Consulte también
[Administración del acceso a los recursos con grupos de Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)

[Administrar grupos en Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)

[Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)



<!--HONumber=Oct16_HO2-->


