---
title: "Crear e implementar directivas de protección de aplicaciones"
titleSuffix: Microsoft Intune
description: "Aprenda a crear y asignar directivas de protección de aplicaciones de Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cd92e787fd3c1abaa8b20ce1d75141b46ab17934
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Creación y asignación de directivas de protección de aplicaciones

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Descubra cómo crear directivas de protección de aplicaciones de Microsoft Intune y asignarlas a los usuarios. En este tema también se describe cómo realizar cambios en las directivas existentes.

## <a name="before-you-begin"></a>Antes de comenzar

Si desea obtener instrucciones en el portal clásico de Intune, vea [cómo crear directivas de protección de aplicaciones](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune).

Las directivas de protección de aplicaciones se pueden aplicar a aplicaciones que se ejecutan en dispositivos que podrían estar o no administrados por Intune. Para obtener una descripción más detallada de cómo funcionan las directivas de protección de aplicaciones y los escenarios admitidos por las directivas de protección de aplicaciones de Intune, consulte [What is Microsoft Intune app protection policies](app-protection-policy.md) (¿Qué son las directivas de protección de aplicaciones de Microsoft Intune?).

Si desea acceder a una lista de aplicaciones compatibles con MAM, vea la [lista de aplicaciones de MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

##  <a name="create-an-app-protection-policy"></a>Crear directivas de protección de aplicaciones
1.  En la carga de trabajo **Aplicaciones móviles**, seleccione **Directivas de protección de aplicaciones** en la sección **Administrar**. Al seleccionar esa opción, se abrirán los detalles de **Directivas de protección de aplicaciones**, donde creará nuevas directivas y editará las existentes. 
2. Elija **Agregar una directiva**. 

  ![Captura de pantalla de la hoja "Agregar directiva"](./media/app-protection-add-policy.png)

3.  Escriba un nombre para la directiva, agregue una descripción breve y seleccione el tipo de plataforma para la directiva. Si resulta necesario, puede crear más de una directiva para cada plataforma.

4.  Seleccione **Aplicaciones** para abrir la hoja **Aplicaciones**, donde se muestra una lista de las aplicaciones disponibles. Seleccione una o varias aplicaciones de la lista que quiera asociar a la directiva que está creando. 
5. Una vez que haya seleccionado las aplicaciones, elija **Seleccionar** para guardar la selección.

    > [!IMPORTANT]
    > Debe seleccionar al menos una aplicación para crear una directiva.

6.  Elija **Configurar los valores obligatorios** en la hoja **Agregar directiva** para abrir **Configuración**.

    Existen dos categorías de configuración de directivas: **Reubicación de datos** y **Acceso**.  Las directivas de reubicación de datos se aplican al movimiento de datos dentro y fuera de las aplicaciones. Las directivas de acceso determinan cómo accede el usuario final a las aplicaciones en un contexto de trabajo.
    Para comenzar, la configuración de directiva tiene valores predeterminados. Si los valores predeterminados cumplen sus requisitos, no resulta necesario realizar ningún cambio.

    > [!TIP]
    > Esta configuración de directiva se aplica solo al usar aplicaciones en el contexto de trabajo. Cuando los usuarios finales usen la aplicación para realizar una tarea personal, no se verán afectados por estas directivas.

7.  Seleccione **Aceptar** para guardar esta configuración. Esto le devolverá al panel **Agregar directiva**. Seleccione **Crear** para crear la directiva y guardar la configuración.
8. Seleccione **Aceptar** para guardar esta configuración. De esta forma, volverá a la hoja **Agregar directiva**. 
9. Seleccione **Crear** para crear la directiva y guardar la configuración.

Cuando termine de crear una directiva como se describe en el procedimiento anterior, no se implementará en ningún usuario. Para implementar una directiva, consulte [Implementar una directiva para los usuarios](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Implementar una directiva para los usuarios


1. En el panel **Directivas de protección de aplicaciones**, seleccione una directiva.

1. En el panel **Directiva**, elija **Asignaciones**, lo que abrirá el panel **Protección de aplicaciones de Intune - Asignaciones**. Elija **Seleccionar grupos para incluir** en el panel **Asignaciones** para abrir el panel **Seleccionar grupos para incluir**.

   ![Captura de pantalla del panel Asignaciones con la opción Seleccionar grupos para incluir resaltada](./media/app-protection-policy-add-users.png)

2.  Se mostrará una lista de grupos de usuarios en el panel **Add user group** (Agregar grupo de usuarios). En esta aparecen todos los grupos de seguridad de su **Azure Active Directory**. Seleccione los grupos de usuarios a los que quiera aplicar esta directiva y, después, elija **Seleccionar**. Al elegir **Seleccionar**, la directiva se implementa para los usuarios.
  
    ![Captura de pantalla del panel Add user group (Agregar grupo de usuarios) que muestra la lista de usuarios de Azure Active Directory](./media/azure-ad-user-group-list.png)

De esta forma, habrá creado una directiva y la habrá implementado en los usuarios.

La directiva solo afecta a los usuarios con licencias asignadas de Microsoft Intune. Los usuarios del grupo de seguridad seleccionado que no tengan asignada una licencia de Intune no se verán afectados.

>[!IMPORTANT]
> Si usa Intune con Administrador de configuración para administrar los dispositivos, la directiva solo se aplicará a los usuarios que estén directamente en el grupo seleccionado. Los miembros de grupos secundarios anidados en el grupo seleccionado no se verán afectados.

Los usuarios finales pueden descargar las aplicaciones desde App Store o Google Play. Para obtener más información, vea:
* [What to expect when your Android app is managed by app protection policies](app-protection-enabled-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [What to expect when your iOS app is managed by app protection policies](app-protection-enabled-apps-ios.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)

##  <a name="change-existing-policies"></a>Cambiar las directivas existentes
Puede editar una directiva existente y aplicarla a los usuarios objetivo. Sin embargo, al cambiar las directivas existentes, los usuarios que ya han iniciado sesión en las aplicaciones no verán los cambios durante un período de 8 horas.

Para ver el efecto de los cambios inmediatamente, el usuario final tendrá que salir de la aplicación y volver a iniciar sesión.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para cambiar la lista de aplicaciones asociadas con la directiva

1.  En el panel **Directivas de protección de aplicaciones**, elija la directiva que quiera cambiar para abrir un panel específico para dicha directiva seleccionada.

2.  En el panel de la directiva, elija **Aplicaciones destinatarias** para abrir la lista de aplicaciones.

3.  Quite o agregue aplicaciones de la lista y seleccione el icono **Guardar** para guardar los cambios.

### <a name="to-change-the-list-of-user-groups"></a>Para cambiar la lista de grupos de usuarios


1.  En el panel **Directivas de protección de aplicaciones**, elija la directiva que quiera cambiar para abrir el panel específico para dicha directiva seleccionada.

2.  En el panel de la directiva, elija **Asignaciones** para abrir el panel **Protección de aplicaciones de Intune - Asignaciones**, que muestra la lista de los grupos de usuarios actuales que tienen esta directiva.

3.  Para agregar un nuevo grupo de usuarios a la directiva, en la pestaña **Incluir**, elija **Seleccionar grupos para incluir** y seleccione el grupo de usuarios. Elija **Seleccionar** para implementar la directiva en el grupo seleccionado.

4.  Para eliminar un grupo de usuarios, en la pestaña **Excluir**, elija **Seleccionar grupos para excluir** y seleccione el grupo de usuarios. Elija **Seleccionar** para quitar el grupo de usuarios.

### <a name="to-change-policy-settings"></a>Para cambiar la configuración de directiva

1.  En el panel **Directivas de protección de aplicaciones**, elija la directiva que quiera cambiar para abrir un panel específico para dicha directiva seleccionada.

2.  Seleccione **Configuración de directiva** para abrir el panel **Configuración de directiva**.

3.  Cambie la configuración y elija el icono **Guardar** para guardar los cambios.

## <a name="policy-settings"></a>Configuraciones de directiva
Para ver una lista completa de las configuraciones de directivas para iOS y Android, seleccione uno de los siguientes vínculos:

- [Directivas de iOS](app-protection-policy-settings-ios.md)
- [Directivas de Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Pasos siguientes
[Supervisar el estado del cumplimiento y del usuario](app-protection-policies-monitor.md)

### <a name="see-also"></a>Vea también
* [What to expect when your Android app is managed by app protection policies](app-protection-enabled-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [What to expect when your iOS app is managed by app protection policies](app-protection-enabled-apps-ios.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)
