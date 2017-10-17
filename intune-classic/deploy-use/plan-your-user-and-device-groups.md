---
title: Planear los grupos de usuarios y dispositivos
description: Planee grupos para satisfacer las necesidades organizativas.
keywords: 
author: sanchusa
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lpatha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5c1f06cc59ff81483d9e54b23435af720d919155
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="plan-your-user-and-device-groups"></a>Planear los grupos de usuarios y dispositivos

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Los grupos de Intune ofrecen una gran flexibilidad cuando está administrando dispositivos y usuarios. Puede configurar grupos para satisfacer sus necesidades organizativas por:

- ubicación geográfica
- department
- características de hardware
- sistema operativo
- si el dispositivo es propiedad del usuario o la empresa


## <a name="how-intune-groups-work"></a>Funcionamiento de los grupos de Intune


Esta es la vista predeterminada del nodo **Grupos** de la consola de administración de Intune:

![Captura de pantalla de la vista predeterminada del nodo Grupos de la consola de Intune](../media/Intune_Planning_Groups_Default_small.png)

Las directivas se implementan en grupos, por lo que la jerarquía de grupo es una de las consideraciones de diseño clave. Es importante saber que no puede cambiar un grupo primario de un grupo después de que haya creado el grupo. La manera en que diseña los grupos es muy importante desde el momento en que empieza a usar el servicio de Intune. Aquí se describen algunos de los procedimientos recomendados para diseñar una jerarquía de grupo según sus necesidades organizativas.

## <a name="group-membership-rules"></a>Reglas de pertenencia a grupos

- Un grupo puede contener o bien usuarios o bien dispositivos, pero no ambos.

    * **Grupos de dispositivos**. Esto incluye equipos y dispositivos móviles. Para poder agregar un equipo a un grupo, debe inscribirse. Antes de que pueda agregar un dispositivo móvil a un grupo, su entorno debe configurarse para admitir dispositivos móviles y los dispositivos deben inscribirse o detectarse en Exchange ActiveSync.

    * **Grupos de usuarios**. Un grupo puede tener usuarios de grupos de seguridad. Sincronización de los grupos de seguridad con su instancia de Active Directory. Si no sincroniza con Active Directory, puede crear estos grupos manualmente.

- Un dispositivo o un usuario pueden pertenecer a más de un grupo.

- Un grupo puede incluir y excluir miembros según las siguientes reglas de pertenencia:

    * **Criterios de pertenencia**. Estos son reglas dinámicas que Intune ejecuta para incluir o excluir miembros. Estos criterios usan grupos de seguridad y otra información sincronizada con la instancia local de Active Directory. Cuando el grupo de seguridad o los datos cambian, cambia la pertenencia al grupo al sincronizar con Active Directory.

    * **Pertenencia directa**. son reglas estáticas que agregan o excluyen miembros explícitamente. La lista de pertenencia es estática.

-   Active Directory Domain Services (AD DS) no es necesario cuando crea grupos de usuarios o grupos de dispositivos que incluyen usuarios o equipos. Pero, para los grupos de dispositivos que incluyen dispositivos móviles, el entorno debe configurarse para admitirlos.

    Además, los dispositivos deben detectarse y agregarse a Intune.

## <a name="group-relationship-rules"></a>Reglas de relación entre grupos

- Cada grupo que crea debe tener un grupo primario. No puede cambiar un grupo primario de un grupo después de que haya creado el grupo.

- Cuando se agregan usuarios o dispositivos a un grupo secundario:

    * El grupo secundario siempre es un subconjunto del grupo primario.

    * Los nuevos miembros que se agreguen a un grupo secundario se agregan automáticamente al grupo primario del grupo.

    * No se puede agregar un miembro a un grupo secundario si ese miembro está excluido del grupo primario.

- La pertenencia a un grupo primario define la disponibilidad de la pertenencia al grupo secundario.

- Cuando se elimina un grupo primario, se eliminan todos los grupos secundarios.

- Puede implementar contenido y directivas en un grupo primario, pero excluye la implementación en los grupos secundarios.

- Puede agregar un usuario o un dispositivo específico a un grupo secundario si el usuario o el dispositivo todavía no es un miembro del grupo primario. Si hace esto, el miembro nuevo del grupo secundario se agregará al grupo primario.

    En cambio, no puede agregar un miembro a un grupo secundario si este está excluido del grupo primario.

- La pertenencia a grupos es recursiva. Por ejemplo:

    * **Nuria** es miembro de un único grupo, el grupo de seguridad **Usuarios de portátil** .

    * El grupo **Usuarios de portátil** es miembro del grupo de seguridad **Usuarios aprobados** .

    * Se crea un grupo en Intune que usa una consulta de pertenencia dinámica que incluye a los miembros del grupo **Usuarios aprobados**. El resultado es que su grupo de usuarios de Intune incluye a **Nuria**.

> [!TIP]
> Al crear los grupos, tenga en cuenta cómo aplicará la directiva. Por ejemplo, puede tener directivas específicas para sistemas operativos de dispositivos o directivas específicas para diferentes roles o unidades organizativas que ya ha definido en el servicio de Active Directory. A algunos administradores les parece útil la creación de grupos de dispositivos específicos de iOS, Android y Windows. Esto se suma a la creación de grupos de usuarios para cada rol organizativo.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your organization. Then, you create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful when you name your policies, so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy, you'll want to communicate it to your users. After you create the more general groups and policies, pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## <a name="built-in-groups"></a>Grupos integrados
Intune proporciona nueve grupos integrados que no puede editar ni eliminar: <!--maybe a screen shot would be best?-->

-   **Todos los usuarios**
    -   Usuarios no agrupados
-   **Todos los dispositivos**
    -   Todos los equipos
    -   Todos los dispositivos móviles
        -   Todos los dispositivos administrados directamente
        -   Todos los dispositivos administrados por Exchange ActiveSync
    -   Todos los dispositivos propiedad de la empresa
    -   Dispositivos no agrupados

> [!NOTE]
> Su lema tendría que ser: *sencillez*. Si la organización no tiene necesidades específicas, como las descritas en las siguientes secciones, no se complique y continúe con la estructura de grupos y las directivas predeterminadas. Esto hará que el servicio sea más manejable a largo plazo. El mantenimiento será más sencillo si puede tratar a sus usuarios de la misma manera. Si existe una diferenciación mínima por grupo, tendrá menos directivas que mantener.


### <a name="all-users-and-devices-in-your-organization"></a>Todos los usuarios y dispositivos de su organización
Defina un grupo primario para todos los usuarios y dispositivos de su organización. Probablemente tenga directivas que se aplicarán a todos. Puede usar los grupos predeterminados **Todos los usuarios** y **Todos los dispositivos** de Intune para este fin. Los subgrupos que organizan los dispositivos por características específicas, como un grupo para BYOD (Bring Your Own Device) y uno para dispositivos corporativos (CO), pueden ser los grupos secundarios de los grupos primarios **Todos los usuarios** y **Todos los dispositivos**.

## <a name="customize-groups-for-your-organization"></a>Personalización de los grupos de la organización

### <a name="byod-and-corporate-owned-devices"></a>BYOD y dispositivos corporativos
Si la organización permite a los empleados usar sus propios dispositivos, proporciona dispositivos corporativos o una combinación de ambos, se recomienda aplicar directivas independientes para estas categorías de dispositivos.

En el caso de BYOD o una combinación de ambos, asegúrese de planear directivas que no infrinjan los reglamentos de privacidad locales. Cree un grupo primario para todos los usuarios que traerán sus propios dispositivos. Puede usar este grupo para aplicar las directivas aplicables a todos los usuarios de esta categoría.

![Crear un grupo primario de BYOD](../media/Intune_Planning_Groups_BYOD_small.png)

De forma similar, puede crear un grupo para los usuarios de dispositivos corporativos de la organización:

![Grupos de usuarios del mismo nivel para BYOD y dispositivos corporativos](../media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### <a name="groups-for-geographic-regions"></a>Grupos de regiones geográficas
Si la organización necesita directivas para regiones específicas, puede crear grupos basados en la región geográfica. Puede basarlos en grupos regionales que puede que haya creado en su instancia de Active Directory y sincronizarlos con su servicio de Azure Active Directory. También puede crear grupos regionales directamente en Azure Active Directory.

Las siguientes capturas de pantalla le muestran cómo crear grupos de Intune basados en grupos sincronizados con su instancia de Active Directory local. En estos ejemplos se supone que tiene un grupo de seguridad de Active Directory denominado **Grupo de usuarios de EE. UU.**

En primer lugar, proporcione información general.

![Captura de pantalla del área Editar grupo](../media/Intune_Planning_Groups_AD_General_small.png)

En **Criterios de pertenencia**, seleccione **Grupo de usuarios de EE. UU.**, sincronizado con Active Directory, como el grupo de seguridad para usar en reglas de pertenencia.

![Captura de pantalla del cuadro de diálogo Editar grupo](../media/Intune_Planning_Groups_AD_Criteria_small.png)

Revise las entradas y, después, elija **Finalizar** para crear el grupo.

![Captura de pantalla del cuadro de diálogo Editar grupo](../media/Intune_Planning_Groups_AD_Summary_small.png)

En nuestro ejemplo, también hemos creado un grupo denominado **MEA** para Oriente Medio y Asia.

> [!NOTE]
> Si la pertenencia al grupo no se rellena según la pertenencia a los grupos de seguridad, asegúrese de que ha asignado licencias de Intune a los miembros del grupo.

### <a name="groups-for-specific-hardware"></a>Grupos de hardware específico
Si la organización necesita directivas aplicables a tipos de hardware concretos, puede crear grupos basados en este requisito. Puede basar las directivas en grupos específicos que ya haya creado en su instancia de Active Directory local y, después, sincronizarlas con Azure Active Directory. También puede crear grupos directamente en Azure Active Directory. En este ejemplo, usamos el **Grupo de usuarios de EE. UU.** como grupo primario del grupo **Usuarios de equipos portátiles**.

![Cuadro de diálogo Seleccionar grupo de seguridad](../media/Intune_Planning_Groups_Laptop_small.png)

En este punto, la jerarquía del grupo debería tener un aspecto similar al de la siguiente captura de pantalla. Puede ver que ahora hay miembros en el grupo **Usuarios de equipos portátiles** de Intune. Las directivas que se apliquen a este grupo se aplicarán a los usuarios de equipos portátiles BYOD de la región de EE. UU.

![Presentación del grupo de usuarios de equipos portátiles](../media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### <a name="groups-for-specific-operating-systems"></a>Grupos de sistemas operativos específicos
Si la organización necesita directivas aplicables a sistemas operativos concretos, como Android, iOS o Windows, puede crear grupos basados en este requisito. Como en los ejemplos anteriores, puede basarlas en grupos específicos de sistema operativo que ya haya creado en su instancia de Active Directory local y sincronizarlas después con Azure Active Directory. También puede crearlos directamente en su instancia de Azure Active Directory.

Mediante el mismo método de los ejemplos anteriores, puede crear grupos basados en usuarios <!--devices?--> que usan plataformas de sistemas operativos concretos.

> [!NOTE]
> Si tiene usuarios que usan varios sistemas operativos o plataformas móviles y no tiene una manera automatizada para clasificar a los usuarios como usuarios de Android, iOS o Windows, considere la posibilidad de aplicar directivas en el nivel de dispositivo. Esto le proporcionará una mayor flexibilidad a la hora de aplicar directivas específicas de un sistema operativo.
>
> No puede aprovisionar grupos de manera dinámica basándose en el sistema operativo del dispositivo. En su lugar, realice esto mediante los grupos de seguridad de Active Directory o Azure Active Directory.

![Grupo de usuarios de equipos portátiles](../media/Intune_Planning_Groups_OS_Hierachy_small.png)

Después de que todos los grupos de usuarios se hayan rellenado en función de estos requisitos organizativos, la jerarquía de grupo debería tener un aspecto parecido a este:

![Vista de jerarquía de grupos](../media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Puede usar esta jerarquía para aplicar las directivas de la organización.

### <a name="device-groups"></a>Grupos de dispositivos
También puede crear grupos similares para dispositivos como se muestra a continuación, a partir de un amplio grupo que incluye todos los dispositivos propiedad de los empleados para el escenario de BYOD.

![Cuadro de diálogo Crear grupo](../media/Intune_Planning_Groups_Device_General_small.png)

Asegúrese de seleccionar **Todos los dispositivos (equipos y dispositivos móviles)** para que el grupo incluya todos los dispositivos BYOD:

![Página Definir criterios de pertenencia](../media/Intune_Planning_Groups_Device_Criteria_small.png)

Revise las entradas y, después, elija **Finalizar** para crear el grupo BYOD.

![Cuadro de diálogo Crear grupo](../media/Intune_Planning_Groups_Device_Summary_small.png)

Siga creando grupos de dispositivos, hasta que tenga una jerarquía de grupos de dispositivos similar a la jerarquía de grupos de usuarios. El nodo de grupo en la consola de Intune tendrá un aspecto similar al siguiente:

![Vista de jerarquía de grupos de Intune](../media/Intune_Groups_Hierarchy_Final_Small.png)

## <a name="group-hierarchies-and-naming-conventions"></a>Convenciones de nomenclatura y jerarquías de grupo
Para facilitar la administración de directivas, se recomienda asignar un nombre a cada directiva según el ámbito de aplicación, la plataforma y el propósito. Use un nombre estándar que siga la estructura del grupo que ha creado y preparado para aplicar las directivas.

Por ejemplo, para una directiva de Android que se aplica a todos los dispositivos corporativos, Android y móviles en el nivel regional de Estados Unidos, la directiva puede denominarse **CO_US_Mob_Android_General**.

![Crear directiva para Android](../media/Intune_planning_policy_android_small.png)

Cuando denomina a las directivas de esta manera, puede identificar rápidamente las directivas y su uso y ámbito previstos en el nodo **Directivas**, de la siguiente manera:

![Lista de directivas de Intune](../media/Intune_planning_policy_view_small.png)

## <a name="next-steps"></a>Pasos siguientes
[Crear grupos](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
