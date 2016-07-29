---
title: Planear los grupos de usuarios y dispositivos | Microsoft Intune
description: Planee grupos para satisfacer las necesidades organizativas.
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ms.reviewer: lpatha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: bb3e96ad4276819ad46ab2a5e1a8deb931bd421a


---

# Planear los grupos de usuarios y dispositivos
Los grupos de Intune ofrecen una gran flexibilidad para administrar los dispositivos y usuarios. Puede configurar grupos para satisfacer sus necesidades organizativas por:

- ubicación geográfica
- department
- características de hardware
- sistema operativo
- si el dispositivo es propiedad del usuario o la empresa


## Funcionamiento de los grupos de Intune


La vista predeterminada del nodo Grupos de la consola de administración de Intune es:

![Captura de pantalla de la vista predeterminada del nodo Grupos de la consola de Intune](/intune/media/Intune_Planning_Groups_Default_small.png)

Las directivas se implementan en grupos, por lo que la jerarquía de grupo es una de las consideraciones de diseño clave. También es importante saber que el grupo primario de un grupo no se puede cambiar una vez creado el grupo, por lo que el diseño de los grupos es sumamente importante desde el momento que se empieza a usar el servicio Intune. Aquí se describen algunas de las prácticas recomendadas para diseñar una jerarquía de grupo según sus necesidades organizativas.

## Reglas de pertenencia a grupos

1. Un grupo puede contener o bien usuarios o bien dispositivos, pero no ambos.

    * **Grupos de dispositivos:** aquí se incluyen equipos y dispositivos móviles. Para poder agregar un equipo a un grupo, debe inscribirse. Para poder agregar un dispositivo móvil a un grupo, su entorno debe configurarse para admitir dispositivos móviles, y los dispositivos deben inscribirse, o detectarse desde Exchange ActiveSync.

    * **Grupos de usuarios:** un grupo puede contener usuarios de grupos de seguridad, que son grupos que se sincronizan desde Active Directory. Si no utiliza la sincronización de Active Directory, puede crear estos grupos manualmente.

2. Un dispositivo o un usuario pueden pertenecer a más de un grupo.

3. Un grupo puede incluir y excluir miembros según las siguientes reglas de pertenencia:

    * **Criterios de pertenencia:** son reglas dinámicas que ejecuta Intune para incluir o excluir miembros. Estos criterios usan **grupos de seguridad** y otra información sincronizada desde la instancia local de Active Directory (AD). Cuando el grupo de seguridad o los datos cambian, cambia la pertenencia al grupo al sincronizar con AD.

    * **Pertenencia directa:** son reglas estáticas que agregan o excluyen miembros explícitamente. La lista de pertenencia es estática.

4. No se necesitan los Servicios de dominio de Active Directory (AD DS) para crear grupos de usuarios o grupos de dispositivos que incluyan usuarios o equipos, pero para que los grupos de dispositivos incluyan dispositivos móviles, su entorno debe configurarse para admitir dispositivos móviles.

    Además, los dispositivos deben detectarse y agregarse a Intune.

## Reglas de relación entre grupos

1. Cada grupo que se cree debe tener un grupo primario, y no se puede cambiar el grupo primario de un grupo una vez creado el grupo.

2. Cuando se agregan usuarios o dispositivos a un grupo secundario:

    * Los grupos secundarios siempre son subconjuntos del grupo primario.

    * Los nuevos miembros que se agreguen a un grupo secundario se agregan automáticamente al grupo primario del grupo.

    * No se puede agregar un miembro a un grupo secundario si ese miembro está excluido del grupo primario.

3. La pertenencia a un grupo primario define la disponibilidad de la pertenencia al grupo secundario.

4. Cuando se elimina un grupo primario, se eliminan todos los grupos secundarios.

5. Es posible implementar contenido y directivas en un grupo primario a la vez que se excluye la implementación en los grupos secundarios.

6. Puede agregar un usuario o un dispositivo específico a un grupo secundario que no sea miembro del grupo primario. Si lo hace, el nuevo miembro del grupo se agregará al grupo primario.

    Sin embargo, no puede agregar un miembro a un grupo secundario que está excluido del grupo primario.

7. La pertenencia a grupos es recursiva. Por ejemplo:

    * **Nuria** es miembro de un único grupo, el grupo de seguridad **Usuarios de portátil** .

    * El grupo **Usuarios de portátil** es miembro del grupo de seguridad **Usuarios aprobados** .

    * Se crea un grupo en Intune que usa una consulta de pertenencia dinámica que incluye a los miembros del grupo **Usuarios aprobados**. El resultado es que su grupo de usuarios de Intune incluye a **Nuria**.

> [!TIP]
> Al crear los grupos, tenga en cuenta cómo se aplicará la directiva. Por ejemplo, puede tener directivas específicas para sistemas operativos de dispositivos y directivas específicas para diferentes roles de la organización o para las unidades organizativas que ha definido en Active Directory. Algunos usuarios consideran útil disponer de grupos de dispositivos específicos de iOS, Android y Windows, así como de grupos de usuarios para cada rol organizativo.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your company. Then create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful naming your policies so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy you'll want to communicate it to your users, so after you create the more general groups and policies pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## Grupos integrados
Intune proporciona nueve grupos integrados que no se pueden editar ni eliminar: <!--maybe a screen shot would be best?-->

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
> Su lema tendría que ser: *sencillez*. Si la organización no tiene necesidades específicas, como las descritas abajo, no se complique y continúe con la estructura de grupos y las directivas predeterminadas para facilitar la administración del servicio a largo plazo. El mantenimiento será más fácil si puede tratar a los usuarios de la misma manera con leves diferencias según el grupo, lo que hará que tenga que mantener menos directivas.


### Todos los usuarios y dispositivos de su organización
Defina un grupo primario para todos los usuarios y dispositivos de la organización, ya que probablemente tenga directivas que se aplicarán a todos. Puede usar los grupos predeterminados **Todos los usuarios** y **Todos los dispositivos** de Intune para este fin. Los subgrupos que organicen los dispositivos por características específicas, como un grupo para BYOD (Bring Your Own Device) y uno para dispositivos corporativos, pueden ser los grupos secundarios de los grupos primarios **Todos los usuarios** y **Todos los dispositivos**.

## Personalización de los grupos de la organización

### BYOD y dispositivos de propiedad corporativa
Si la organización permite a los empleados usar sus propios dispositivos en el trabajo (BYOD), proporciona dispositivos corporativos o una combinación de ambos, se recomienda aplicar directivas basadas en estas dos categorías de dispositivos.

En el caso de BYOD o una combinación de ambos, asegúrese de planear directivas que no infrinjan los reglamentos de privacidad locales. Cree un grupo primario para todos los usuarios que traerán sus propios dispositivos. Este grupo se podrá usar para aplicar las directivas aplicables a todos los usuarios de esta categoría.

![Captura de pantalla de creación de un grupo primario de BYOD](/intune/media/Intune_Planning_Groups_BYOD_small.png)

De forma similar, puede crear un grupo para los usuarios de dispositivos corporativos de la organización:

![Captura de pantalla de grupos de usuarios del mismo nivel para BYOD y dispositivos corporativos](/intune/media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### Grupos de regiones geográficas
Si la organización necesita directivas para regiones específicas, puede crear grupos basados en la región geográfica. Se pueden basar en grupos regionales que ya pueda haber creado en Active Directory (AD) y sincronizarlos con Azure AD. También puede crearlos directamente en Azure AD.

Estas capturas de pantalla muestran cómo crear grupos de Intune basados en grupos sincronizados desde AD local. En este ejemplo se supone que tiene un grupo de seguridad de AD denominado **Grupo de usuarios de EE. UU.**.

1. En primer lugar, proporcione la información general.

![Captura de pantalla del área Editar grupo](/intune/media/Intune_Planning_Groups_AD_General_small.png)

En Criterios de pertenencia, seleccione **US Users Group**, sincronizado desde AD, como el grupo de seguridad para usar en Reglas de pertenencia.

![Cuadro de diálogo Editar grupo](/intune/media/Intune_Planning_Groups_AD_Criteria_small.png)

Revise el contenido y seleccione **Finalizar** para terminar de crear el grupo.

![Cuadro de diálogo Editar grupo](/intune/media/Intune_Planning_Groups_AD_Summary_small.png)

En nuestro ejemplo, también hemos creado un grupo de Oriente medio y Asia, MEA.

> [!NOTE]
> Si la pertenencia al grupo no se rellena según la pertenencia a grupos de seguridad, compruebe que licencias de Intune estén asignadas a esos miembros.

### Grupos de hardware específico
Si la organización necesita directivas aplicables a tipos de hardware concretos, puede crear grupos basados en este requisito. Se pueden basar en grupos específicos que ya haya creado en AD local y sincronizarlos con Azure AD. También puede crearlos directamente en Azure AD. En este ejemplo, usamos el **Grupo de usuarios de EE. UU.** como grupo primario del grupo **Usuarios de equipos portátiles**.

![Cuadro de diálogo Seleccionar grupo de seguridad](/intune/media/Intune_Planning_Groups_Laptop_small.png)

En este punto, la jerarquía de grupos debe aparecer como se muestra a continuación. Como puede ver, ahora hay miembros en el grupo **Usuarios de equipos portátiles** de Intune. Las directivas que se apliquen a este grupo se aplicarán ahora a los usuarios de equipos portátiles BYOD de la región de EE. UU.

![Presentación del grupo de usuarios de equipos portátiles](/intune/media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### Grupos de sistemas operativos específicos
Si la organización necesita directivas aplicables a sistemas operativos concretos, como Android, iOS o Windows, puede crear grupos basados en este requisito. Como en los ejemplos anteriores, se pueden basar en grupos específicos de SO que ya haya creado en AD local y sincronizarlos con Azure AD. También puede crearlos directamente en Azure AD.

Con el mismo método de los ejemplos anteriores, se pueden crear grupos basados en usuarios <!--devices?--> mediante plataformas específicas de sistema operativo.

> [!NOTE]
> Si tiene usuarios que usan varios sistemas operativos y plataformas móviles y no tiene una forma automatizada para clasificar a los usuarios como usuarios de Android, iOS o Windows, considere la posibilidad de aplicar directivas en el nivel de dispositivo, lo que le proporcionará una mayor flexibilidad a la hora de aplicar directivas específicas del sistema operativo.
>
> No puede aprovisionar grupos de manera dinámica basándose en el sistema operativo del dispositivo. Hágalo mediante los grupos de seguridad de AD o AAD.

![Presentación del grupo de usuarios de equipos portátiles](/intune/media/Intune_Planning_Groups_OS_Hierachy_small.png)

Una vez que todos los grupos de usuarios se hayan rellenado en función de estos requisitos organizativos, la jerarquía de grupo debería tener un aspecto parecido a este:

![Vista de jerarquía de grupos](/intune/media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Esta jerarquía puede usarse para aplicar las directivas de la organización adecuadamente.

### Grupos de dispositivos
También puede crear grupos similares para dispositivos como se muestra a continuación, a partir de un amplio grupo que incluye todos los dispositivos propiedad de los empleados para el escenario de BYOD:

![Cuadro de diálogo Crear grupo](/intune/media/Intune_Planning_Groups_Device_General_small.png)

Asegúrese de seleccionar **Todos los dispositivos (equipos y dispositivos móviles)** para que el grupo incluya todos los dispositivos BYOD:

![Página Definir criterios de pertenencia](/intune/media/Intune_Planning_Groups_Device_Criteria_small.png)

Revise el contenido y seleccione **Finalizar** para crear el grupo de BYOD.

![Cuadro de diálogo Crear grupo](/intune/media/Intune_Planning_Groups_Device_Summary_small.png)

Siga creando grupos de dispositivos, hasta que tenga una jerarquía de grupos de dispositivos similar a la jerarquía de grupos de usuarios. El nodo de grupo en la consola de Intune debería tener un aspecto similar al siguiente:

![Vista de jerarquía de grupos de Intune](/intune/media/Intune_Groups_Hierarchy_Final_Small.png)

## Convenciones de nomenclatura y jerarquías de grupo
Para facilitar la administración de directivas, se recomienda asignar un nombre a cada directiva según el ámbito de aplicación, la plataforma y el propósito. Este estándar de nomenclatura debe seguir la estructura del grupo que haya creado en la preparación para aplicar las directivas.

Por ejemplo, para una directiva de Android que se aplica a todos los dispositivos corporativos, a Android y a móviles en el nivel regional de Estados Unidos, la directiva puede denominarse **CO_US_Mob_Android_General**.

![Crear directiva para Android](/intune/media/Intune_planning_policy_android_small.png)

Este método de asignación de nombres a las directivas permite identificar rápidamente las directivas y su uso previsto, así como el ámbito, desde el nodo de directivas de la consola, de la siguiente manera:

![Lista de directivas de Intune](/intune/media/Intune_planning_policy_view_small.png)

## Pasos siguientes
[Crear grupos](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


