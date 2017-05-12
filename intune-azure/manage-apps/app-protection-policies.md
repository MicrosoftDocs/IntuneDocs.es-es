---
title: "Crear e implementar directivas de protección de aplicaciones"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo las directivas de protección de aplicaciones de Intune pueden ayudar a proteger los datos de empresa que usan las aplicaciones que administra."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 119c7172f8175d128c3e13d37bb9ec3c91719bcf
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017

---

# <a name="how-to-create-and-assign-app-protection-policies"></a>Creación y asignación de directivas de protección de aplicaciones

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

**Si no está en el servicio de Intune del programa de versión preliminar del portal Azure**, en este tema se explica [cómo crear directivas de protección de aplicaciones](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) en la consola de Intune clásica.

Las directivas de protección de aplicaciones se pueden aplicar a aplicaciones que se ejecutan en dispositivos que podrían estar o no administrados por Intune. Para obtener una descripción más detallada de cómo funcionan las directivas de protección de aplicaciones y los escenarios admitidos por las directivas de protección de aplicaciones de Intune, consulte [What is Microsoft Intune app protection policies](what-is-app-protection-policy.md) (¿Qué son las directivas de protección de aplicaciones de Microsoft Intune?).

##  <a name="create-an-app-protection-policy"></a>Crear directivas de protección de aplicaciones
1.  En la carga de trabajo **Mobile apps**, elija **Administrar** > **Directivas de protección de aplicaciones**.

2.  Se abre la hoja **App protection policies** (Directivas de protección de aplicaciones), donde creará nuevas directivas y editará las existentes. Elija **Agregar una directiva**.

  ![Captura de pantalla de la hoja Agregar directiva](../media/app-protection-add-policy.png)

3.  Escriba un nombre para la directiva, agregue una descripción breve y seleccione el tipo de plataforma para el que se creará la directiva (iOS o Android). Puede crear más de una directiva para cada plataforma.

4.  Seleccione **Aplicaciones** para abrir la hoja **Aplicaciones**, donde se muestra una lista de las aplicaciones disponibles. Seleccione una o más aplicaciones de la lista que quiera asociar a la directiva que está creando. Una vez seleccionadas las aplicaciones, elija **Seleccionar**, en la parte inferior de la hoja **Aplicaciones**, para guardar la selección.

    > [!IMPORTANT]
    > Debe seleccionar al menos una aplicación para crear una directiva.

5.  En la hoja **Agregar directiva**, elija **Configurar los valores obligatorios** para abrir la hoja de configuración de directivas.

    Existen dos categorías de configuración de directivas: **Reubicación de datos** y **Acceso**.  Las directivas de reubicación de datos son aplicables a la introducción y la extracción de datos de las aplicaciones, mientras que las directivas de acceso determinan el modo en el que el usuario final tiene acceso a las aplicaciones en un contexto de trabajo.
    Para comenzar, la configuración de directiva tiene valores predeterminados. No es necesario realizar ningún cambio si los valores predeterminados satisfacen sus necesidades.

    > [!TIP]
    > Esta configuración de directiva se aplica solo al usar aplicaciones en el contexto de trabajo.  Cuando el usuario final usa la aplicación para realizar una tarea personal, no se verá afectado por estas directivas.



6.  Seleccione **Aceptar** para guardar esta configuración. Ahora habrá regresado a la hoja **Agregar una directiva** . Seleccione **Crear** para crear la directiva y guardar la configuración.


Cuando termine de crear una directiva como se describe en el procedimiento anterior, no se implementará en ningún usuario. Para implementar una directiva, consulte la sección siguiente titulada "Implementar una directiva para los usuarios".

## <a name="deploy-a-policy-to-users"></a>Implementar una directiva para los usuarios

1.  En la hoja **Directiva**, seleccione **Grupos de usuarios**, que abre la hoja **Grupos de usuarios**. Seleccione **Agregar grupo de usuarios** en la hoja **Grupos de usuarios** para abrir la hoja **Agregar grupo de usuarios**.

  ![Captura de pantalla de la hoja Grupos de usuarios con la opción de menú Agregar grupo de usuarios resaltada](../media/app-protection-policy-add-users.png)

2.  Se mostrará una lista de grupos de usuarios en la hoja **Agregar grupo de usuarios** . Esta es una lista de todos los grupos de seguridad de su **Azure Active Directory**. Seleccione los grupos de usuarios a los que quiera aplicar esta directiva y, después, elija **Seleccionar**. Al **** hacerlo, la directiva se implementa en los usuarios.
  ![Captura de pantalla de la hoja Agregar grupo de usuarios que muestra la lista de usuarios de Azure Active Directory](../media/azure-ad-user-group-list.png)

Ahora ha creado una directiva y la ha implementado en los usuarios.

La directiva solo se aplica a los usuarios que tengan asignadas licencias de Microsoft Intune. No se aplica a los usuarios pertenecientes al grupo de seguridad seleccionado que no tengan asignada una licencia de Microsoft Intune.

>[!IMPORTANT]
> Si usa Intune con Administrador de configuración para administrar los dispositivos iOS y Android, la directiva solo se aplica a los usuarios directamente en el grupo seleccionado. No se ven afectados los miembros de los grupos secundarios anidados en el grupo seleccionado.

Los usuarios finales pueden descargar las aplicaciones desde App Store o Google Play. Para obtener más información, vea:
* [What to expect when your Android app is managed by app protection policies](app-protection-enabled-android-apps.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [What to expect when your iOS app is managed by app protection policies](app-protection-enabled-ios-apps.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)

##  <a name="change-existing-policies"></a>Cambiar las directivas existentes
Puede editar una directiva existente y aplicarla a los usuarios objetivo. Con todo, al cambiar las directivas existentes, los usuarios que ya han iniciado sesión en las aplicaciones no verán los cambios durante un período de 8 horas.

Para ver el efecto de los cambios inmediatamente, el usuario final tendrá que salir de la aplicación y volver a iniciar sesión.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para cambiar la lista de aplicaciones asociadas con la directiva

1.  En la hoja **Directiva de aplicaciones**, elija la directiva que quiera cambiar. De este modo se abrirá una hoja específica de la directiva que acaba de seleccionar.

2.  En la hoja de la directiva, seleccione **Aplicaciones de destino** para abrir la lista de aplicaciones.

3.  Quite o agregue aplicaciones de la lista y seleccione el icono **Guardar** para guardar los cambios.

### <a name="to-change-the-list-of-user-groups"></a>Para cambiar la lista de grupos de usuarios

1.  En la hoja **Directiva de aplicaciones**, elija la directiva que quiera cambiar. De este modo se abrirá la hoja específica de la directiva que ha seleccionado.

2.  En la hoja de la directiva, seleccione **Grupos de usuarios** para abrir la hoja **Grupo de usuarios** en la que se muestra la lista de grupos de usuarios actuales regidos por esta directiva.

3.  Para agregar un nuevo grupo de usuarios a la directiva, elija **Agregar grupo de usuarios** y seleccione el grupo de usuarios en cuestión. Elija **Seleccionar** para implementar la directiva en el grupo seleccionado.

4.  Para eliminar un grupo de usuarios, resalte el grupo que quiere quitar. Después, elija el botón de puntos suspensivos (…) y seleccione **Eliminar** para quitar el grupo de usuarios.
  ![Captura de pantalla que muestra la opción Eliminar](../media/app-protection-policy-delete-user.png)

### <a name="to-change-policy-settings"></a>Para cambiar la configuración de directiva

1.  En la hoja **Directiva de aplicaciones**, elija la directiva que quiera cambiar. De este modo se abrirá una hoja específica de la directiva que acaba de seleccionar.


2.  Seleccione **Configuración de directiva** para abrir la hoja **Configuración de directiva**.

3.  Cambie la configuración y elija el icono **Guardar** para guardar los cambios.

## <a name="policy-settings"></a>Configuraciones de directiva
Para ver una lista completa de las configuraciones de directiva para iOS y Android, seleccione una opción a continuación:

> [!div class="op_single_selector"]
- [Directivas de iOS](ios-app-protection-policy-settings.md)
- [Directivas de Android](android-app-protection-policy-settings.md)

## <a name="next-steps"></a>Pasos siguientes
[Supervisar el estado del cumplimiento y del usuario](monitor-app-protection-policies-with-microsoft-intune.md)

### <a name="see-also"></a>Consulte también
* [What to expect when your Android app is managed by app protection policies](app-protection-enabled-android-apps.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [What to expect when your iOS app is managed by app protection policies](app-protection-enabled-ios-apps.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)

