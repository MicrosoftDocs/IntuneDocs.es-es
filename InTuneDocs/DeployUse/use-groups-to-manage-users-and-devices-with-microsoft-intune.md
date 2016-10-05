---
title: Usar grupos para administrar usuarios y dispositivos | Microsoft Intune
description: "Cree y administre grupos mediante el área de trabajo Grupos."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: lpatha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8c474810f8d3c7db4784c38c45c85c83b647860b
ms.openlocfilehash: fa0c235d3ab5f9dde04f8345e7e28fdd00603e58


---
# Usar grupos para administrar usuarios y dispositivos en Microsoft Intune

Este tema describe cómo crear grupos en Intune. También proporciona información acerca de cómo va a cambiar la administración de grupos durante los próximos meses. 

>[!IMPORTANT]
>
>Si abre el área de trabajo Grupos en el portal de Intune y ve un vínculo al portal de Azure Active Directory (Azure AD), ya está usando el *nuevo* enfoque de grupos de seguridad de Azure AD para la administración de grupos en Intune, que se describe en [Aviso de próximas mejoras en la experiencia de administración para grupos](#notice-of-upcoming-improvements-to-the-admin-experience-for-groups). Haga clic en el vínculo al portal de Azure AD para crear y administrar los grupos. Para más información sobre cómo trabajar con grupos de seguridad de Azure AD, vea [Administración del acceso a los recursos con grupos de Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
>
>Si no ve el vínculo al portal de Azure AD, todavía está usando el enfoque *actual* para la administración de grupos, que se describe en [Crear grupos para administrar usuarios y dispositivos en Microsoft Intune](#Create-groups-to-manage-users-and-devices-with-Microsoft-Intune) en este tema.


## Aviso de próximas mejoras en la experiencia de administración para grupos

Los usuarios nos han informado de que quieren disponer de una experiencia de agrupación y destinos común para todos los componentes de Enterprise Mobility + Security y los hemos escuchado. Conforme a los comentarios, los grupos de Intune pronto se convertirán en grupos de seguridad basados en Azure Active Directory. Este cambio unificará la administración de grupos en Intune y Azure Active Directory (Azure AD). Con esta nueva experiencia, no habrá que duplicar grupos entre servicios. También proporcionará extensibilidad en las opciones para usar Windows PowerShell y Microsoft Graph.

### ¿Cómo me afecta esto ahora?
Este cambio no le afecta por ahora. Pero estas son las próximas novedades:

-   En septiembre de 2016, las nuevas cuentas que se aprovisionen después del lanzamiento del servicio mensual usarán los grupos de seguridad de Azure AD en lugar de los grupos de usuarios de Intune.   
-   En octubre de 2016, las nuevas cuentas que se aprovisionen después del lanzamiento del servicio mensual administrarán los grupos basados en dispositivos y usuarios en el portal de Azure AD. No habrá ningún impacto en los clientes existentes.
-   En noviembre de 2016, el equipo del producto de Intune iniciará la migración de los clientes existentes a la nueva experiencia de administración de grupos basada en Azure AD. Todos los grupos de dispositivos y usuarios que existan en Intune en la actualidad se migrarán a los grupos de seguridad de Azure AD. La migración se realizará por lotes a partir de noviembre de 2016. Las migraciones no se iniciarán hasta que se pueda minimizar cualquier impacto en su trabajo diario y se espere que no tengan ningún efecto en sus usuarios. También se le avisará antes de migrar su cuenta.


### ¿Cómo y cuándo migraré a la nueva experiencia de grupos?
Los clientes actuales de Intune se migrarán a lo largo de un período de tiempo. Se está terminando la programación de esa migración y se actualizará este tema en unas semanas para proporcionar más detalles. Se le avisará antes de la migración. Si tiene alguna duda con respecto a la migración, póngase en contacto con nuestro equipo de migración en <intunegrps@microsoft.com>.

### ¿Qué pasa con mis grupos de dispositivos y usuarios existentes?
 Los grupos de usuarios y de dispositivos que haya creado en Intune se migrarán a grupos de seguridad de Azure AD. Los grupos predeterminados de Intune, como el grupo Todos los usuarios, solo se migrarán si los está usando en implementaciones en el momento de la migración. La migración puede ser más compleja para algunos grupos. Le avisaremos si tiene que realizar algún paso adicional para la migración de su organización.

### ¿Qué características nuevas tendré disponibles?
Esta es la nueva funcionalidad que se presentará con esta migración de Intune a Azure Active Directory:

-    Los grupos de seguridad de Azure AD se admitirán en Intune para todos los tipos de implementaciones.
-    Los grupos de seguridad de Azure AD admitirán la agrupación de dispositivos y usuarios.
-    Los grupos de seguridad de Azure AD admitirán grupos dinámicos con atributos de dispositivos de Intune. Por ejemplo, podrá agrupar de manera dinámica dispositivos por plataforma, como iOS. Cuando un nuevo dispositivo iOS se inscriba en la organización, automáticamente se agregará al grupo dinámico de dispositivos iOS.
-    Tendrá una experiencia de administración compartida para la administración de grupos en Azure AD e Intune.
- El rol de administrador de servicios de Intune se agregará a Azure AD para permitir que los administradores de servicios de Intune realicen tareas de administración de grupos en Azure AD.

### ¿Qué funcionalidad de Intune no estará disponible?
Aunque se mejorará la experiencia de los grupos, habrá alguna funcionalidad de Intune que no estará disponible una vez que la organización migre de los grupos de Intune a los grupos de seguridad de Azure AD.

#### Funcionalidad de administración de grupos

-   Después de migrar, no podrá excluir miembros ni grupos cuando cree un grupo nuevo. Pero con los grupos dinámicos de Azure AD puede usar atributos para crear reglas avanzadas que le permitan excluir miembros de un grupo según los criterios que defina.
-   Los grupos Usuarios sin agrupar y Dispositivos sin agrupar no se admitirán. No se migrarán esos grupos de Intune a Azure AD.


#### Funcionalidad dependiente del grupo

-   El rol de administrador de servicios no tendrá permisos de **Administrar grupos**.
-   No podrá agrupar dispositivos de Exchange ActiveSync. El grupo Todos los dispositivos administrados de EAS se convertirá de un grupo a una vista de informe.
-  Dinamizar con grupos en informes no estará disponible.
-  Grupo personalizado de destino de reglas de notificación no estará disponible.

### ¿Qué debería hacer para prepararme para este cambio?
 Tenemos algunas recomendaciones que le facilitarán la transición:

- Elimine cualquier grupo innecesario o no deseado de Intune antes de la migración.
- Evalúe el uso de la exclusión de grupos y considere la posibilidad de volver a diseñar los grupos de forma que no necesite usar la exclusión.
-  Si tiene administradores que no tienen permisos para crear grupos en Azure AD, solicite al administrador de Azure AD que los agregue al rol Administrador de servicios de Intune de Azure AD.


## Crear grupos para administrar usuarios y dispositivos en Microsoft Intune

En esta sección se describe cómo crear grupos de Intune en la consola de administración de Intune.

Puede crear y administrar grupos en el área de trabajo **Grupos** de la consola de administración de Microsoft Intune. La página **Información general de grupos** muestra resúmenes de estado que le pueden ayudar a identificar y clasificar por orden de prioridad los asuntos que requieren su atención. Los resúmenes de estado cubren estas áreas:

-   Alertas
-   Actualizaciones de software
-   Endpoint Protection
-   Directiva
-   Administración de software

La jerarquía de grupo, además, muestra resúmenes de estado que ayudan a identificar y resolver los problemas de los miembros de un grupo seleccionado.

## Crear grupos

> [!TIP]
> Al crear grupos, tenga en cuenta cómo aplicará las directivas. Por ejemplo, puede tener directivas específicas del sistema operativo de un dispositivo o directivas específicas de diferentes roles de la organización, o de unidades organizativas que ya ha definido en Active Directory. Podría resultar útil disponer de grupos de dispositivos separados para iOS, Android y Windows, así como de un grupo de usuarios para cada rol organizativo.
>
> Además, probablemente quiera crear una directiva predeterminada que se aplique a todos los grupos y dispositivos para establecer los requisitos de cumplimiento básicos de la organización. Luego puede crear directivas más específicas para las categorías más amplias de usuarios y dispositivos. Por ejemplo, puede crear directivas de correo electrónico para cada uno de los sistemas operativos de dispositivos.
>
> Preste atención al asignar nombres a las directivas a fin de poder identificarlas fácilmente en el futuro. Por ejemplo, un nombre descriptivo idóneo para una directiva sería **Directiva de correo electrónico de WP para toda la compañía**.
>
> Cada vez que cree una directiva restrictiva, es recomendable que se lo comunique a los usuarios. Después de crear las directivas y los grupos más generales, preste atención a la creación de grupos más pequeños para poder reducir las comunicaciones innecesarias.

### Para crear un grupo de dispositivos

1.  En la consola de administración de Intune, seleccione **Grupos** &gt; **Información general** &gt; **Crear grupo**.

2.  Especifique un nombre y una descripción (opcional) para el grupo y luego seleccione un grupo de dispositivos como grupo primario. Seleccione **Siguiente**.

3.  En la página **Definir criterios de pertenencia**, seleccione el tipo de dispositivos que se van a incluir en el grupo. Es posible que haya otras opciones de configuración de grupos adicionales, dependiendo de los tipos de dispositivos que decida incluir:

    -   **Equipo**. Seleccione si se van a incluir todos los miembros del grupo primario, las unidades organizativas que quiere incluir o excluir y los dominios que quiere incluir o excluir. Puede obtener información de unidades organizativas y dominios de un equipo desde el inventario.

    -   **Móvil**. Seleccione si se van a incluir los dispositivos móviles administrados por Intune, los administrados por Exchange ActiveSync o ambos.

    -   **Todos los dispositivos**. Esta opción incluye todos los dispositivos sin exclusiones basadas en ningún criterio.

4.  En la página **Definir pertenencia directa**, elija **Examinar** para seleccionar dispositivos individuales que quiera incluir o excluir. Si selecciona dispositivos que no están en el grupo primario especificado, Intune los agrega automáticamente a él.

5.  En la página **Resumen**, revise las opciones seleccionadas y elija **Finalizar**.

El grupo recién creado aparece en la lista **Grupos** del área de trabajo **Grupos**, en el grupo primario. Ahí también puede editar o eliminar el grupo.

### Para crear un grupo de usuarios

1.  En la consola de administración de Intune, seleccione **Grupos** &gt; **Información general** &gt; **Crear grupo**.

2.  Especifique un nombre y una descripción (opcional) para el grupo y luego seleccione un grupo de usuarios como grupo primario. Seleccione **Siguiente**.

3.  En la página **Definir criterios de pertenencia**, seleccione si se va a incluir a todos los miembros del grupo primario o si va a empezar con un grupo vacío. Luego, incluya o excluya miembros en función de los grupos de seguridad de usuarios que configure manualmente en el [Centro de administración de Office 365](http://go.microsoft.com/fwlink/?LinkId=698854) o que sincronice desde Active Directory. Si cambia la pertenencia de un grupo de seguridad, también puede cambiar la pertenencia de los grupos de usuarios basados en ese grupo de seguridad.

    > [!IMPORTANT]
    > En la actualidad, si el grupo incluye miembros de grupos de seguridad o de administradores concretos y se excluye a miembros de algunos grupos, se quitarán los miembros que se incluyeron en un principio. Para crear un grupo que tenga tanto los miembros incluidos como los excluidos, primero se recomienda crear un grupo primario que tenga los miembros incluidos. Luego, cree un grupo secundario para ese grupo primario. En el nuevo grupo secundario, enumere los miembros excluidos. Luego, use ese grupo secundario para administrar la distribución de directivas, perfiles y aplicaciones de Intune.

    > [!NOTE]
    > En el portal de Azure, puede crear grupos basados en los administradores de los que dependen los usuarios. Este tipo de grupo es dinámico y cambiará a medida que se agreguen o se quiten empleados del equipo de un administrador en Azure Active Directory. El procedimiento para crear un grupo de Azure basado en el nombre del administrador se describe en [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/), en la sección **Para configurar un grupo como un grupo de "Administrador"**.

4.  En la página **Definir pertenencia directa**, elija **Examinar** para seleccionar usuarios individuales que quiera incluir o excluir. Si selecciona usuarios que no están en el grupo primario especificado, estos se agregan automáticamente a él. La opción para agregar un usuario de forma manual se encuentra en la parte inferior del cuadro de diálogo **Seleccionar miembros**. Esto resulta útil si quiere agregar un usuario que todavía no tiene un dispositivo inscrito.

5.  En la página **Resumen**, revise las opciones seleccionadas y elija **Finalizar**.

El grupo recién creado aparece en la lista **Grupos** del área de trabajo **Grupos**, en el grupo primario. Ahí también puede editar o eliminar el grupo.

> [!TIP]
> Los grupos de seguridad son un buen recurso para rellenar grupos de usuarios. Puesto que los grupos de seguridad definen quién puede acceder a qué recursos, se pueden convertir perfectamente en grupos de usuarios de Intune. Los grupos de seguridad que se sincronizan desde Active Directory a Azure Active Directory, o que se crean directamente en Azure Active Directory a través del Centro de administración de Office 365 o el portal de Azure, están disponibles al crear grupos de usuarios en Intune.

## Filtrar vistas de administrador por rol
En las vistas de grupo filtradas, puede personalizar lo que un administrador de TI puede ver según su rol. También puede restringir los grupos que cada administrador de TI puede administrar. Esto puede resultar útil cuando:

-   Quiere que los administradores de TI puedan implementar elementos únicamente para dispositivos y usuarios concretos
-   Quiere que los administradores de TI vean solo los grupos que son relevantes para ellos

Puede configurar vistas de grupo filtradas para los administradores de servicios en la consola de administración de Intune. Para más información, consulte [What to know before you start Microsoft Intune (Información necesaria antes de iniciar Microsoft Intune)](/intune/get-started/what-to-know-before-you-start-microsoft-intune).

Después de configurar vistas de grupo filtradas para un administrador de servicios, cuando este implementa directivas o software, o ejecuta informes, solo puede ver y seleccionar los grupos que usted ha especificado. El administrador tampoco ve información de estado en estas páginas de la consola de administración:

-   **Información general del sistema**
-   **Información general de grupos**
-   **Información general de Endpoint Protection**
-   **Información general de alertas**
-   **Información general de software**
-   **Información general de directivas**

### Para crear una vista de grupo filtrada

1.  En la consola de administración de Intune, seleccione **Administración** &gt; **Administración de administradores** &gt; **Administradores de servicios**.

2.  Seleccione el administrador de servicios para el que quiere crear una vista de grupo filtrada y, luego, **Administrar grupos**.

3.  En el cuadro de diálogo **Seleccione los grupos que serán visibles para este administrador de servicios**, agregue los grupos a los que podrá acceder el administrador de servicios y, después, seleccione **Aceptar**.

Después de configurar las vistas de grupo filtradas, los administradores de TI podrán ver y seleccionar solo los grupos que haya indicado.

## Administrar tus grupos
Después de crear los grupos, puede seguir administrándolos según las necesidades de la organización.

Puede editar el grupo para cambiar su nombre o descripción, o quién pertenece a él.

Puede eliminar un grupo que ya no satisfaga las necesidades de la organización. Al eliminar un grupo no se eliminan los usuarios que pertenecen a este.

## Pasos siguientes
Después de configurar los grupos y las directivas, compruebe las implicaciones prácticas del diseño revisando **Valor previsto** y **Estado**.

### Para comprobar el diseño

1. Seleccione cualquier dispositivo de un grupo de dispositivos y examine las categorías de información de la parte superior de la página.
2. Seleccione **Directiva**. Verá algo parecido a esta captura de pantalla de configuración de directiva de un dispositivo Android.

![Ejemplo de directiva de configuración de Android](../media/Intune-Device-Policy-v.2.jpg)

Cada directiva tiene un **Valor previsto** y un **Estado**. El valor previsto es lo que tenía pensado lograr al asignar la directiva. El estado es lo que logra cuando todas las directivas aplicables al dispositivo, así como las restricciones y los requisitos del hardware y el sistema operativo, se tienen en cuenta conjuntamente. En esta captura de pantalla se pueden ver dos ejemplos claros:

-   **Permitir contraseñas sencillas** está establecido en **Sí**, como se muestra en la columna **Valor previsto** , pero su **Estado** es **No aplicable**. Esto es porque no se admiten contraseñas sencillas para dispositivos Android.
-   De forma similar, el elemento de directiva expandido **Configuración de correo electrónico para dispositivos iOS** no se aplica a este dispositivo porque es un dispositivo Android.

> [!NOTE]
> Recuerde que cuando dos directivas con distintos niveles de restricción se aplican al mismo dispositivo o usuario, la directiva más restrictiva se aplica en la práctica.



<!--HONumber=Sep16_HO2-->


