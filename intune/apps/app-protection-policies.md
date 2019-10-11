---
title: Crear e implementar directivas de protección de aplicaciones
titleSuffix: Microsoft Intune
description: En este tema se describe cómo crear y asignar directivas de protección de aplicaciones (APP) de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4958a35f3a83fecffacf26421e4c1d797f45ddaa
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940394"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Creación y asignación de directivas de protección de aplicaciones

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Descubra cómo crear directivas de protección de aplicaciones de Microsoft Intune y asignarlas a los usuarios. En este tema también se describe cómo realizar cambios en las directivas existentes.

## <a name="before-you-begin"></a>Antes de comenzar

Las directivas de protección de aplicaciones se pueden aplicar a aplicaciones que se ejecutan en dispositivos que podrían estar o no administrados por Intune. Para obtener una descripción más detallada de cómo funcionan las directivas de protección de aplicaciones y los escenarios admitidos por las directivas de protección de aplicaciones de Intune, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

Si desea acceder a una lista de aplicaciones compatibles con MAM, vea la [lista de aplicaciones de MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Para obtener información acerca de cómo agregar aplicaciones de línea de negocio (LOB) de su organización a Microsoft Intune para prepararse para las directivas de protección de aplicaciones, consulte [Incorporación de aplicaciones a Microsoft Intune](apps-add.md).

## <a name="create-an-app-protection-policy"></a>Crear directivas de protección de aplicaciones
1. En el portal de Intune, vaya a **Aplicaciones cliente** > **Directivas de protección de aplicaciones**. Al seleccionar esa opción, se abrirán los detalles de **Directivas de protección de aplicaciones**, donde creará nuevas directivas y editará las existentes.
2. Seleccione **Crear directiva**.

   ![Captura de pantalla de la hoja "Agregar directiva"](./media/app-protection-policies/app-protection-add-policy.png)

3. Especifique un nombre para la directiva, agregue una descripción breve y seleccione el tipo de plataforma para la directiva. Puede crear más de una directiva para cada plataforma.

4. Seleccione **Aplicaciones** para abrir la hoja **Aplicaciones**, donde se muestra una lista de las aplicaciones disponibles. Seleccione una o varias aplicaciones de la lista que quiera asociar a la directiva que está creando. Seleccione al menos una aplicación para crear una directiva.  

5. Una vez que haya seleccionado las aplicaciones, elija **Seleccionar** para guardar la selección.

6. En la hoja **Agregar una directiva**, seleccione **Configurar los valores obligatorios** para abrir **Configuración**.

   Hay tres categorías de configuraciones de directiva:
   - **Protección de datos**: este grupo incluye los controles de prevención de pérdida de datos (DLP), como restricciones para cortar, copiar, pegar y guardar como. Esta configuración determina cómo los usuarios interactúan con los datos en las aplicaciones.
   - **Requisitos de acceso**: este grupo contiene las opciones de PIN por aplicación que determinan cómo el usuario final tiene acceso a las aplicaciones en un contexto de trabajo.  
   - **Inicio condicional** : este grupo contiene configuraciones como la configuración mínima del sistema operativo, la detección de dispositivos liberados o modificados y períodos de gracia sin conexión.

   Para comenzar, la configuración de directiva tiene valores predeterminados. Si los valores predeterminados cumplen sus requisitos, no resulta necesario realizar ningún cambio.

   > [!TIP]
   > Esta configuración de directiva se aplica solo al usar aplicaciones en el contexto de trabajo. Cuando los usuarios finales usen la aplicación para realizar una tarea personal, no se verán afectados por estas directivas. Tenga en cuenta que cuando se crea un nuevo archivo se considera un archivo personal. 

7. Seleccione **Aceptar** para guardar esta configuración. De esta forma, volverá a la hoja **Agregar directiva**.
8. Seleccione **Crear** para crear la directiva y guardar la configuración.

Las directivas creadas no se implementan para los usuarios hasta que no se haga de forma explícita. Para implementar una directiva, consulte [Implementar una directiva para los usuarios](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Implementar una directiva para los usuarios

1. En el panel **Directivas de protección de aplicaciones**, seleccione una directiva.

2. En el panel ***Intune App Protection**, seleccione **Asignaciones** para abrir el panel **Intune App Protection: Asignaciones**. En la pestaña *Incluir*, seleccione **Seleccionar grupos para incluir**. 

   ![Captura de pantalla del panel Asignaciones con el menú Seleccionar grupos para incluir](./media/app-protection-policies/app-protection-policy-add-users.png)

3. Se muestra una lista de todos los grupos de seguridad en su entorno de **Azure Active Directory**. Seleccione los grupos de usuarios a los que quiera aplicar esta directiva y, después, elija **Seleccionar**. 

    ![Captura de pantalla del panel Agregar grupo de usuarios con la lista de usuarios de Azure AD](./media/app-protection-policies/azure-ad-user-group-list.png)

4. Después de incluir y excluir grupos, seleccione **Guardar** para guardar la configuración e implementar la directiva en los usuarios. Si seleccione **Descartar** antes de guardar la configuración, se descartarán todos los cambios realizados en las pestañas *Incluir* y *Excluir*.   
 
     ![Captura de pantalla que muestra las opciones Guardar y Descartar](./media/app-protection-policies/save-assignment.png)
  
De esta forma, habrá creado una directiva y la habrá implementado en los usuarios.

La directiva solo afecta a los usuarios con licencias asignadas de Microsoft Intune. Los usuarios del grupo de seguridad seleccionado que no tengan asignada una licencia de Intune no se verán afectados.

>[!IMPORTANT]
> Si usa Intune con Administrador de configuración para administrar los dispositivos, la directiva solo se aplicará a los usuarios que estén directamente en el grupo seleccionado. Los miembros de grupos secundarios anidados en el grupo seleccionado no se verán afectados.

Los usuarios finales pueden descargar las aplicaciones desde App Store o Google Play. Para obtener más información, vea:
* [What to expect when your Android app is managed by app protection policies](../fundamentals/end-user-mam-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [What to expect when your iOS app is managed by app protection policies](../fundamentals/end-user-mam-apps-ios.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)

## <a name="change-existing-policies"></a>Cambiar las directivas existentes
Puede editar una directiva existente y aplicarla a los usuarios objetivo. Sin embargo, al cambiar las directivas existentes, los usuarios que ya han iniciado sesión en las aplicaciones no verán los cambios durante un período de ocho horas.

Para ver el efecto de los cambios inmediatamente, el usuario final debe cerrar sesión en la aplicación y volver a iniciarla.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para cambiar la lista de aplicaciones asociadas con la directiva

1. En el panel **Directivas de protección de aplicaciones**, seleccione la directiva que desea modificar.

2. En el panel *Intune App Protection*, seleccione **Aplicaciones de destino** para abrir la lista de aplicaciones.

3. Quite o agregue aplicaciones de la lista y luego seleccione el icono **Guardar** para guardar los cambios.

### <a name="to-change-the-list-of-user-groups"></a>Para cambiar la lista de grupos de usuarios


1. En el panel **Directivas de protección de aplicaciones**, seleccione la directiva que desea modificar.

2. En el panel *Intune App Protection*, seleccione **Asignaciones** para abrir el panel **Intune App Protection: Asignaciones** que muestra la lista de los grupos de usuarios actuales que tienen esta directiva.

3. Para agregar un nuevo grupo de usuarios a la directiva, en la pestaña *Incluir*, elija **Seleccionar grupos para incluir** y seleccione el grupo de usuarios. Elija **Seleccionar** para agregar el grupo. 

4. Para excluir un grupo de usuarios, en la pestaña *Excluir*, elija **Seleccionar grupos para excluir** y seleccione el grupo de usuarios. Elija **Seleccionar** para quitar el grupo de usuarios.  

5. Para eliminar los grupos que se agregaron anteriormente, ya sea en la pestaña *Incluir* o en la pestaña *Excluir*, seleccione los puntos suspensivos (...) y seleccione **Eliminar**. 

5. Una vez que estén listos los cambios en las asignaciones, seleccione **Guardar** para guardar la configuración e implementar la directiva en el nuevo conjunto de usuarios. Si seleccione **Descartar** antes de guardar la configuración, se descartarán todos los cambios realizados en las pestañas *Incluir* y *Excluir*.

### <a name="to-change-policy-settings"></a>Para cambiar la configuración de directiva

1. En el panel **Directivas de protección de aplicaciones**, seleccione la directiva que desea modificar.

2. En el panel *Intune App Protection*, seleccione **Propiedades** para abrir la lista de áreas de configuración que puede modificar. 

3. Seleccione el área de configuración con el valor que desea modificar, como **Reubicación de datos** o **Requisitos de acceso**. A continuación, cambie la configuración con los nuevos valores.

4. Seleccione el icono **Guardar** para guardar los cambios. Repita el proceso para seleccionar un área de configuración y modificarla y, a continuación, guarde los cambios, hasta que se completen todos los cambios. A continuación, puede cerrar el panel *Intune App Protection: Propiedades*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Destinar directivas de protección de aplicaciones en función del estado de administración del dispositivo
En muchas organizaciones es habitual permitir que los usuarios finales puedan usar los dispositivos administrados de administración de dispositivos móviles (MDM) de Intune (como los dispositivos propiedad de las empresas) y los dispositivos no administrados que únicamente están protegidos con directivas de protección de aplicaciones de Intune. Los dispositivos no administrados a menudo se conocen como Bring Your Own Devices (BYOD).

Dado que las directivas de protección de aplicaciones de Intune están destinadas a la identidad de un usuario, la configuración de protección de un usuario puede aplicarse tanto a los dispositivos inscritos (administrados con MDM) como a los dispositivos no inscritos (sin MDM). Por lo tanto, puede destinar una directiva de protección de aplicaciones de Intune a dispositivos iOS y Android inscritos y no inscritos de Intune. Puede tener una directiva de protección para los dispositivos no administrados a la que se apliquen unos controles de prevención de pérdida de datos (DLP) estrictos y una directiva de protección independiente para los dispositivos administrados con MDM en la que los controles DLP pueden ser un poco menos restrictivos. Para obtener más información sobre cómo funciona en dispositivos personales Android Enterprise, consulte [Directivas de protección de aplicaciones y perfiles de trabajo](android-deployment-scenarios-app-protection-work-profiles.md).

Para crear estas directivas, vaya a **Aplicaciones cliente** > **Directivas de protección de aplicaciones** en la consola de Intune y haga clic en **Crear directiva**. También puede editar una directiva de protección de aplicaciones existente. Para que la directiva de protección de aplicaciones se aplique a los dispositivos administrados y a los no administrados, confirme que la opción **Destinar a todos los tipos de aplicaciones** esté establecida en **Sí**, que es el valor predeterminado. Si quiere efectuar una asignación granular según el estado de administración, establezca **Destinar a todos los tipos de aplicaciones** en **No**. 

![Captura de pantalla de la hoja Agregar una directiva con la opción Destinar a todos los tipos de aplicaciones](./media/app-protection-policies/app-protection-policies-target-all.png)

### <a name="app-types"></a>Tipos de aplicación

- **Aplicaciones en dispositivos no administrados**: Dispositivos no administrados son aquellos en los que no se ha detectado la administración MDM de Intune. Esto incluye a los proveedores de MDM de terceros.
- **Aplicaciones en dispositivos administrados por Intune**: MDM de Intune administra los dispositivos administrados.
- **Aplicaciones del perfil del trabajo Android**: Se trata de dispositivos administrados que se han inscrito como dispositivos del perfil de trabajo de Android Enterprise.

> Nota: Los dispositivos Android le pedirán que instale la aplicación Portal de empresa de Intune independientemente del tipo de aplicación que se elija. Por ejemplo, si selecciona "Aplicaciones en dispositivos administrados por Intune", se le seguirá solicitando a los usuarios con dispositivos Android no administrados.

Para iOS, se requieren ajustes adicionales en la configuración de la aplicación para dirigir la configuración de la directiva de protección de aplicaciones (APP) a las aplicaciones en dispositivos inscritos en Intune:

- **IntuneMAMUPN** debe configurarse para todas las aplicaciones administradas de MDM. Para más información, vea [Administración de transferencias de datos entre aplicaciones iOS en Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** debe configurarse para todas las aplicaciones administradas de MDM de LOB y de terceros. **IntuneMAMDeviceID** debe configurarse en el token de identificador de dispositivo. Por ejemplo, `key=IntuneMAMDeviceID, value={{deviceID}}`. Para obtener más información, vea [Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados](app-configuration-policies-use-ios.md).
- Si solo está configurado **IntuneMAMDeviceID**, la aplicación Intune considerará el dispositivo como no administrado.

> [!NOTE]
> Para obtener información específica de compatibilidad con iOS sobre las directivas de protección de aplicaciones según el estado de administración de los dispositivos, vea [MAM protection policies targeted based on management state](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-) (Directivas de protección MAM destinadas según el estado de administración).

## <a name="policy-settings"></a>Configuraciones de directiva
Para ver una lista completa de las configuraciones de directivas para iOS y Android, seleccione uno de los siguientes vínculos:

- [Directivas de iOS](app-protection-policy-settings-ios.md)
- [Directivas de Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Pasos siguientes
[Supervisar el estado del cumplimiento y del usuario](app-protection-policies-monitor.md)

## <a name="see-also"></a>Consulte también
* [What to expect when your Android app is managed by app protection policies](../fundamentals/end-user-mam-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [What to expect when your iOS app is managed by app protection policies](../fundamentals/end-user-mam-apps-ios.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)
