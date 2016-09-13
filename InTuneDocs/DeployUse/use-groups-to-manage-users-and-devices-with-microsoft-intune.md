---
title: Usar grupos para administrar usuarios y dispositivos | Microsoft Intune
description: "Cree y administre grupos mediante el área de trabajo Grupos."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 06/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: lpatha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7c680c43b8c9120755ec3c652cf7ec1cbcc3472
ms.openlocfilehash: b13e2ff2f4822d71ef8cff9d835e32b99cb3e4ab


---
# Usar grupos para administrar usuarios y dispositivos en Microsoft Intune

Este tema describe cómo crear grupos en Intune. También proporciona información acerca de cómo va a cambiar la administración de grupos durante los próximos meses. Para obtener información sobre el enfoque *actual* de la administración de grupo, consulte [Crear grupos para administrar usuarios y dispositivos con Microsoft Intune](#Create-groups-to-manage-users-and-devices-with-Microsoft-Intune) en este tema.

## Aviso sobre las próximas mejoras en la experiencia de administración de grupos

Teniendo en cuenta los comentarios de tener una experiencia de agrupación y destino en Enterprise Mobility + Security, estamos convirtiendo los grupos de Intune en grupos de seguridad basados en Azure Active Directory. Esto unificará la administración de grupos en Intune y Azure Active Directory (Azure AD). La nueva experiencia le evitará tener que duplicar grupos entre servicios y le proporcionará extensibilidad mediante PowerShell y Graph. 

### ¿Cómo me afecta esto ahora?
Este cambio no le afectará ahora, pero le podemos especificar las novedades:

-   En septiembre, las nuevas cuentas que se hayan aprovisionado después del lanzamiento del servicio mensual usarán los grupos de seguridad de Azure AD en lugar de los grupos de usuarios de Intune.   
-   En octubre, las nuevas cuentas que se hayan aprovisionado después del lanzamiento del servicio mensual administrarán los grupos basados en dispositivos y usuarios en el Portal de Azure AD. No afecta a los clientes existentes.
-   En noviembre, el equipo del producto de Intune iniciará la migración de los clientes existentes a la nueva experiencia de administración de grupos basada en Azure AD. Todos los grupos de dispositivos y usuarios de Intune se migrarán a los grupos de seguridad de Azure AD. La migración se realizará en lotes a partir de noviembre. No iniciaremos las migraciones hasta que podamos minimizar cualquier impacto en su trabajo diario y esperamos que no se produzca ningún impacto en el usuario final. También le avisaremos antes de la migración de su cuenta.


### ¿Cómo y cuándo migraré a la nueva experiencia de grupos?
Los clientes actuales se migrarán en un período de tiempo. Estamos terminando la programación de esa migración y actualizaremos este tema en unas semanas para proporcionar más detalles. Obtendrá un aviso antes de la migración. Si tiene alguna duda con respecto a la migración, póngase en contacto con nuestro equipo de migración en [intunegrps@microsoft.com](intunegrps@microsoft.com).

### ¿Qué pasa con mis grupos de dispositivos y usuarios existentes?
 Los grupos de dispositivos y usuarios que ha creado se migrarán a los grupos de seguridad de Azure AD. Los grupos predeterminados de Intune, como el grupo Todos los usuarios, solo se migrarán si los está usando en implementaciones en el momento de la migración. La migración puede ser más compleja para algunos grupos y le notificaremos si se necesitan pasos adicionales para realizarla.

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

-   No podrá excluir miembros ni grupos cuando cree un grupo nuevo. En cambio, los grupos dinámicos de Azure AD le permitirán usar atributos para crear reglas avanzadas para excluir miembros basándose en criterios.
-   No serán compatibles con los grupos **Usuarios sin agrupar** y **Dispositivos sin agrupar**. Esos grupos no se migrarán.


#### Funcionalidad dependiente del grupo

-   El rol de administrador de servicios no tendrá permisos de **Administrar grupos**.
-   No podrá agrupar dispositivos de Exchange ActiveSync.  Su grupo **Todos los dispositivos administrados de EAS** se convertirá de un grupo a una vista de informe.
-  Dinamizar con grupos en informes no estará disponible.
-  Grupo personalizado de destino de reglas de notificación no estará disponible.

### ¿Qué debería hacer para prepararme para este cambio?
 Tenemos algunas recomendaciones que le facilitarán la transición:

- Elimine cualquier grupo innecesario o no deseado de Intune antes de la migración.
- Evalúe el uso de la exclusión de grupos y considere la posibilidad de volver a diseñar los grupos de forma que no necesite usar la exclusión.
-  Si tiene administradores que no tienen permisos para crear grupos en Azure AD, solicite a su administrador de Azure AD agregarlos al rol **Administrador de servicios de Intune** de Azure AD.


## Crear grupos para administrar usuarios y dispositivos en Microsoft Intune

En esta sección se describe cómo crear grupos de Intune en la consola de administración de Intune.

Para crear y administrar grupos use el área de trabajo **Grupos** de la consola de administración de Microsoft Intune. La página **Información general de grupos** contiene resúmenes de estado que le ayudan a identificar y clasificar por orden de prioridad los asuntos que requieren su atención en relación con:

-   Alertas
-   Actualizaciones de software
-   Endpoint Protection
-   Directiva
-   Administración de software

Además, la jerarquía de grupo se muestra con resúmenes de estado que ayudan a identificar y resolver los problemas de los miembros de un grupo seleccionado.


> [!TIP]
> Al crear los grupos, tenga en cuenta cómo se aplicará la directiva. Por ejemplo, puede tener directivas específicas para sistemas operativos de dispositivos y directivas específicas para diferentes roles de la organización o para las unidades organizativas que ha definido en Active Directory. Algunos usuarios consideran útil disponer de grupos de dispositivos específicos de iOS, Android y Windows, así como de grupos de usuarios para cada rol organizativo.
>
> Probablemente deseará crear una directiva predeterminada que se aplique a todos los grupos y dispositivos, para establecer los requisitos de cumplimiento básicos de la compañía. A continuación, cree directivas más específicas para las categorías más amplias de usuarios y dispositivos como, por ejemplo, directivas de correo electrónico para el sistema operativo de cada dispositivo.
>
> Preste atención al asignar nombres a las directivas a fin de poder identificarlas fácilmente en el futuro. Por ejemplo, un nombre de directiva descriptivo ideal sería **Directiva de correo electrónico de WP para toda la compañía**.
>
> Cada vez que cree una directiva restrictiva deseará comunicarla a los usuarios. Por lo tanto, después de crear directivas y grupos más generales, preste atención a la creación de grupos más pequeños para poder reducir las comunicaciones innecesarias.


## Creación de un grupo de dispositivos

1.  En la consola de administración de Intune, haga clic en **Grupos** &gt; **Información general** &gt; **Crear grupo**.

2.  Especifique un nombre y una descripción opcional para el grupo y seleccione un grupo de dispositivos como grupo primario. Seleccione **Siguiente**.

3.  En la página **Definir criterios de pertenencia** , seleccione el tipo de dispositivos que va a incluir el grupo. Las opciones adicionales de configuración del grupo dependen del tipo de dispositivos que seleccione:

    -   **Equipo:** especifique si se deben incluir todos los miembros del grupo principal, las unidades organizativas (OU) que quiera incluir o excluir y los dominios que quiera incluir o excluir. La información sobre unidades organizativas y dominios de los equipos se obtiene del inventario.

    -   **Móvil:** especifique si se deben incluir solo los dispositivos móviles administrados por Intune, los administrados por Exchange ActiveSync o ambos.

    -   **Todos los dispositivos:** esta opción incluye todos los dispositivos sin exclusiones en función de criterios.

4.  En la página **Definir pertenencia directa** , puede incluir o excluir los dispositivos individuales que especifique si pulsa **Examinar**. Si utiliza esta opción para seleccionar dispositivos que no están en el grupo primario especificado, estos dispositivos se agregan automáticamente al grupo primario.


5.  En la página **Resumen**, revise las acciones que se van a realizar. Seleccione **Finalizar**.

Encontrará el grupo recién creado en la lista **Grupos** del área de trabajo **Grupos** en el grupo primario. Aquí también puede editar o eliminar el grupo.

## Creación de un grupo de usuarios

1.  En la consola de administración de Intune, haga clic en **Grupos** &gt; **Información general** &gt; **Crear grupo**.

2.  Especifique un nombre y una descripción opcional para el grupo y seleccione un grupo de usuarios como grupo primario. Seleccione **Siguiente**.

3.  En la página **Definir criterios de pertenencia** , especifique si desea incluir todos los miembros del grupo primario o empezar con un grupo vacío.  Una vez hecho esto, incluya o excluya los miembros en función de los **grupos de seguridad** de usuarios que configure manualmente en el [Centro de administración de Office 365](http://go.microsoft.com/fwlink/?LinkId=698854) o que se sincronicen desde su servicio local de Active Directory. Si cambia la pertenencia de un grupo de seguridad, también puede cambiar la pertenencia de los grupos de usuarios basados en ese grupo de seguridad.

    > [!IMPORTANT]
    > Tenga en cuenta que si el grupo incluye miembros de grupos de seguridad o administrador específicos y que si usted excluye a miembros de grupos específicos, se quitarán los miembros que incluyó en un principio. Para crear un grupo que tenga tanto los miembros incluidos como los excluidos, le recomendamos que cree un grupo principal con los miembros incluidos y que, a continuación, cree un grupo secundario en el principal para enumerar ahí los miembros excluidos. A continuación, puede usar ese grupo secundario como le sea conveniente para distribuir directivas, perfiles y aplicaciones de Intune.

    > [!NOTE]
    > En el Portal de administración de Azure puede crear un grupo en función del administrador al cual los usuarios envían sus notificaciones. El grupo será dinámico y cambiará a medida que se agreguen o se quiten empleados del equipo del administrador en Azure Active Directory. El procedimiento para crear un grupo de Azure basado en un administrador se describe en [Uso de atributos para crear reglas avanzadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/) en la sección denominada **Configurar un grupo como "Administrador"**.


4.  En la página **Definir pertenencia directa** , puede incluir o excluir los usuarios individuales que especifique si pulsa **Examinar**. Si utiliza esta opción para seleccionar usuarios que no están en el grupo primario especificado, estos dispositivos se agregan automáticamente al grupo primario. En la parte inferior del cuadro de diálogo **Seleccionar miembros** encontrará la opción para agregar un usuario manualmente. Esto resulta útil si quiere agregar un usuario que todavía no tiene un dispositivo inscrito.


5.  En la página **Resumen**, revise las acciones que se van a realizar. Seleccione **Finalizar**.

Encontrará el grupo recién creado en la lista **Grupos** del área de trabajo **Grupos** en el grupo primario. Aquí también puede editar o eliminar el grupo.

> [!TIP]
> Los grupos de seguridad son un excelente recurso para rellenar los grupos de usuarios. Puesto que los grupos de seguridad definen quién tiene acceso a qué recursos, se pueden convertir perfectamente en grupos de usuarios de Intune. Los grupos de seguridad que se sincronicen desde Active Directory en Azure Active Directory, o que se creen directamente en Azure Active Directory a través del Centro de administración de Office 365 o el portal de administración de Azure, estarán a su disposición para crear grupos de usuarios en Intune.

## Personalizar las vistas de los roles de administrador
Las vistas de grupo filtradas permiten personalizar la vista que pueden ver los administradores según su rol y restringir los grupos que cada administrador de TI puede administrar. Esto puede resultar útil cuando:

-   Los administradores de TI solo deben poder implementar elementos para dispositivos y usuarios específicos.

-   Quiere mostrar solo los grupos relevantes a cada administrador de TI.

Puede configurar vistas de grupo filtradas para los administradores de servicios en la consola de administrador de Intune. Para más información, consulte [What to know before you start Microsoft Intune (Información necesaria antes de iniciar Microsoft Intune)](/intune/get-started/what-to-know-before-you-start-microsoft-intune).

Después de configurar vistas de grupo filtradas para un administrador de servicios, el administrador:

-   Solo puede ver y seleccionar los grupos especificados al implementar directivas o software, o al usar informes

-   No recibe información del estado de las siguientes páginas de la consola de administración:

    -   **Información general del sistema**

    -   **Información general de grupos**

    -   **Información general de Endpoint Protection**

    -   **Información general de alertas**

    -   **Información general de software**

    -   **Información general de directivas**

### Configurar vistas de grupo filtradas

1.  En la consola de administración de Intune, seleccione **Administración** &gt; **Administración de administradores** &gt; **Administradores de servicios**.

2.  Seleccione el administrador de servicios para el que desea filtrar los grupos y haga clic en **Administrar grupos**.

3.  En el cuadro de diálogo **Seleccione los grupos que serán visibles para este administrador de servicios** , agregue los grupos a los que el administrador de servicios seleccionado podrán tener acceso y, después, haga clic en **Aceptar**.

Después de configurar las vistas de grupo filtradas, los administradores de TI podrán ver y seleccionar solo los grupos especificados.

## Administrar tus grupos
Después de crear los grupos seguirá administrándolos según las necesidades de su organización.

Puede editar el grupo para cambiar su nombre y descripción, así como los miembros que pertenecen al grupo.

Puede eliminar un grupo que ya no satisfaga las necesidades de la organización. Al eliminar un grupo no se eliminan los usuarios que pertenecen a este.

## Pasos siguientes

### Comprobar el diseño
Después de configurar los grupos y las directivas, compruebe las implicaciones prácticas del diseño revisando el **Valor previsto** y el **Estado**.

1. Seleccione cualquier dispositivo de un grupo de dispositivos y examine las categorías de información en la parte superior de la pantalla.
2. Seleccione **Directiva** . Verá algo parecido a esta captura de pantalla de configuración de directiva de un dispositivo Android.

![Ejemplo de directiva de configuración de iOS](../media/Intune-Device-Policy-v.2.jpg)

Cada directiva tiene un **Valor previsto** y un **Estado**. El valor previsto es lo que tenía pensado lograr al asignar la directiva. El estado es lo que se logra realmente cuando todas las directivas aplicables al dispositivo, así como las restricciones y los requisitos del hardware y el sistema operativo, se consideran conjuntamente.  En la captura de pantalla se pueden ver dos ejemplos claros:

-   **Permitir contraseñas sencillas** está establecido en **Sí**, como se muestra en la columna **Valor previsto** , pero su **Estado** es **No aplicable**. Esto es porque no se admiten contraseñas sencillas para dispositivos Android.

-   De forma similar, el elemento de directiva expandido**Configuración de correo electrónico para dispositivos iOS** no se aplica a este dispositivo, ya que es un dispositivo Android.

> [!NOTE]
> Recuerde que cuando dos directivas con distintos niveles de restricción se aplican al mismo dispositivo o usuario, la directiva más restrictiva se aplica en la práctica.



<!--HONumber=Aug16_HO4-->


