---
title: Crear e implementar directivas de protección de aplicaciones
titleSuffix: Microsoft Intune
description: En este tema se describe cómo crear y asignar directivas de protección de aplicaciones (APP) de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8e105dae43c4e7139c8e44a8c6535baebe31cc4
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585470"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Creación y asignación de directivas de protección de aplicaciones

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Aprenda a crear directivas de protección de aplicaciones de Microsoft Intune y asignarlas a los usuarios de la organización. En este tema también se describe cómo realizar cambios en las directivas existentes.

## <a name="before-you-begin"></a>Antes de comenzar

Las directivas de protección de aplicaciones se pueden aplicar a aplicaciones que se ejecutan en dispositivos que podrían estar o no administrados por Intune. Para obtener una descripción más detallada de cómo funcionan las directivas de protección de aplicaciones y los escenarios admitidos por las directivas de protección de aplicaciones de Intune, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

Si desea acceder a una lista de aplicaciones compatibles con MAM, vea la [lista de aplicaciones de MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Para obtener información acerca de cómo agregar aplicaciones de línea de negocio (LOB) de su organización a Microsoft Intune para prepararse para las directivas de protección de aplicaciones, consulte [Incorporación de aplicaciones a Microsoft Intune](apps-add.md).

Actualmente, el flujo de proceso para crear una directiva de protección de aplicaciones difiere en función de la plataforma:
- Directivas de protección de aplicaciones para aplicaciones de iOS/iPadOS y Android
- Directivas de protección de aplicaciones para aplicaciones de Windows 10

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>Directivas de protección de aplicaciones para aplicaciones de iOS/iPadOS y Android

Cuando se crea una directiva de protección de aplicaciones para aplicaciones de iOS/iPadOS y Android, se lleva a cabo un moderno flujo de proceso de Intune que da como resultado una directiva de protección de aplicaciones nueva.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>Crear una directiva de protección de aplicaciones para aplicaciones de iOS/iPadOS o Android
1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. En el portal de Intune, seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones**. Al seleccionar esa opción, se abrirán los detalles de **Directivas de protección de aplicaciones**, donde creará nuevas directivas y editará las existentes.
3. Seleccione **Crear directiva** y, luego, **iOS/iPadOS** o **Android**. Se abre la hoja **Crear directiva**.
4. En la página **Datos básicos**, agregue los siguientes valores:

    | Valor | Descripción |
    |--------------|------------------------------------------------|
    | Nombre | Nombre de esta directiva de protección de aplicaciones |
    | Descripción | [Opcional] Descripción de esta directiva de protección de aplicaciones |


    El valor de **Plataforma** se establece en función de la elección anterior.

    ![Captura de pantalla de la pestaña Datos básicos de la hoja Crear directiva](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. Haga clic en **Siguiente** para abrir la página **Aplicaciones**.<br>
    La página **Aplicaciones** permite elegir cómo se quiere aplicar esta directiva a las aplicaciones en distintos dispositivos. Debe agregar al menos una aplicación.<p>
    
    | Valor/opción | Descripción |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Destinar a todos los tipos de aplicaciones | Use esta opción para destinar la directiva a las aplicaciones en dispositivos que se encuentren en cualquier estado de administración. Elija **No** para destinar a aplicaciones en tipos de dispositivos específicos. |
    |     Tipos de dispositivo | Use esta opción para especificar si esta directiva se aplica a dispositivos administrados por MDM o a dispositivos no administrados. En el caso de las directivas de aplicaciones de iOS, elija entre **Dispositivos no administrados** y **Dispositivos administrados**. En el caso de las directivas de aplicaciones de Android, elija entre **Dispositivos no administrados**, **Administrador de dispositivos Android** y **Android Enterprise**.  |
    | Aplicaciones públicas | Haga clic en **Seleccionar aplicaciones públicas** para elegir las aplicaciones de destino. |
    | Aplicaciones personalizadas | Haga clic en **Seleccionar aplicaciones personalizadas** para seleccionar aplicaciones personalizadas de destino en función de un identificador de paquete. |
    
    Las aplicaciones que se seleccionen aparecerán en la lista de aplicaciones públicas y personalizadas. 
6. Haga clic en **Siguiente** para abrir la página **Protección de datos**.<br>
    Esta página proporciona opciones de controles de prevención de pérdida de datos (DLP), incluidas restricciones para cortar, copiar, pegar y guardar como. Estas opciones determinan cómo van a interactuar los usuarios con los datos de las aplicaciones donde esta directiva de protección de aplicaciones está en vigor.

    **Configuración de la protección de datos**:<br>
    - **Protección de datos de iOS/iPadOS**: para más información, vea la sección [Protección de datos en Configuración de directivas de protección de aplicaciones de iOS](~/apps/app-protection-policy-settings-ios.md#data-protection).
    - **Protección de datos de Android**: para más información, vea la sección [Protección de datos en Configuración de directivas de protección de aplicaciones de Android](~/apps/app-protection-policy-settings-android.md#data-protection).

7. Haga clic en **Siguiente** para abrir la página **Requisitos de acceso**.<br>
    En esta página se proporcionan opciones que permiten configurar los requisitos de PIN y credenciales que los usuarios deben cumplir para obtener acceso a las aplicaciones en un contexto de trabajo. 
 
    **Configuración de los requisitos de acceso**:<br>
    - **Requisitos de acceso de iOS/iPadOS**: para más información, vea la sección [Requisitos de acceso en Configuración de directivas de protección de aplicaciones de iOS/iPadOS](~/apps/app-protection-policy-settings-ios.md#access-requirements).
    - **Requisitos de acceso de Android**: para más información, vea la sección [Requisitos de acceso en Configuración de directivas de protección de aplicaciones de Android](~/apps/app-protection-policy-settings-android.md#access-requirements).

8. Haga clic en **Siguiente** para abrir la página **Inicio condicional**.<br>
    Esta página proporciona opciones para establecer los requisitos de seguridad del inicio de sesión de la directiva de protección de acceso. Seleccione **Configuración** y escriba el **Valor** que los usuarios deben cumplir para iniciar sesión en la aplicación de empresa. Luego, seleccione la **Acción** que quiera llevar a cabo si los usuarios no cumplen los requisitos. En algunos casos, se pueden configurar varias acciones para una sola configuración.

    **Configuración del inicio condicional**:<br>
    - **Configuración del inicio condicional de iOS/iPadOS**: para más información, vea la sección [Inicio condicional en Configuración de directivas de protección de aplicaciones de iOS/iPadOS](~/apps/app-protection-policy-settings-ios.md#conditional-launch).
    - **Configuración del inicio condicional de Android**: para más información, vea la sección [Inicio condicional en Configuración de directivas de protección de aplicaciones de Android](~/apps/app-protection-policy-settings-android.md#conditional-launch).

7. Haga clic en **Siguiente** para abrir la página **Asignaciones**.<br>
   La página **Asignaciones** permite asignar la directiva de protección de aplicaciones a grupos de usuarios. 
8. Haga clic en **Siguiente: Revisar + crear** para revisar los valores y la configuración especificados para esta directiva de protección de aplicaciones.
9. Cuando termine, haga clic en **Crear** para crear la directiva de protección de aplicaciones en Intune. 

## <a name="app-protection-policies-for-windows-10-apps"></a>Directivas de protección de aplicaciones para aplicaciones de Windows 10

Al crear una directiva de protección de aplicaciones para aplicaciones de Windows 10, llevará a cabo un flujo de proceso clásico de Intune.

### <a name="create-a-windows-10-app-protection-policy"></a>Creación de una directiva de protección de aplicaciones de Windows 10
1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. En el portal de Intune, seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones**. Al seleccionar esa opción, se abrirán los detalles de **Directivas de protección de aplicaciones**, donde creará nuevas directivas y editará las existentes.
3. Seleccione **Crear directiva**.

    <img alt="Screenshot of the 'Create policy' blade for Windows 10" src="~/apps/media/app-protection-policies/app-protection-add-policy.png" width="350">

4. Especifique un nombre para la directiva, agregue una descripción breve y seleccione el tipo de plataforma para la directiva. Puede crear más de una directiva para cada plataforma.

4. Puede optar por **Destinar a todos los tipos de aplicaciones**. Esta opción permite destinar la directiva a las aplicaciones en dispositivos que se encuentren en cualquier estado de administración. En la resolución de un conflicto entre directivas, esta configuración se reemplazará si un usuario tiene una directiva destinada a un estado de administración específico. Para obtener más información, vea [Target app protection policies based on device management state](~/apps/app-protection-policies.md#target-app-protection-policies-based-on-device-management-state) (Destinar directivas de protección de aplicaciones en función del estado de administración del dispositivo).

5. Seleccione **Aplicaciones** para abrir la hoja **Aplicaciones**, donde se muestra una lista de las aplicaciones disponibles. Seleccione una o varias aplicaciones de la lista que quiera asociar a la directiva que está creando. Seleccione al menos una aplicación para crear una directiva.  

6. Una vez que haya seleccionado las aplicaciones, elija **Seleccionar** para guardar la selección.

7. En la hoja **Agregar una directiva**, seleccione **Configurar los valores obligatorios** para abrir **Configuración**.

   Hay tres categorías de configuraciones de directiva:
   - **Protección de datos**: este grupo incluye los controles de prevención de pérdida de datos (DLP), como restricciones para cortar, copiar, pegar y guardar como. Esta configuración determina cómo los usuarios interactúan con los datos en las aplicaciones.
   - **Requisitos de acceso**: este grupo contiene las opciones de PIN por aplicación que determinan cómo el usuario final tiene acceso a las aplicaciones en un contexto de trabajo.  
   - **Inicio condicional** : este grupo contiene configuraciones como la configuración mínima del sistema operativo, la detección de dispositivos liberados o modificados y períodos de gracia sin conexión.

   Para comenzar, la configuración de directiva tiene valores predeterminados. Si los valores predeterminados cumplen sus requisitos, no resulta necesario realizar ningún cambio.

   > [!TIP]
   > Esta configuración de directiva se aplica solo al usar aplicaciones en el contexto de trabajo. Cuando los usuarios finales usen la aplicación para realizar una tarea personal, no se verán afectados por estas directivas. Tenga en cuenta que cuando se crea un nuevo archivo se considera un archivo personal. 

8. Seleccione **Aceptar** para guardar esta configuración. De esta forma, volverá a la hoja **Agregar directiva**.
9. Seleccione **Crear** para crear la directiva y guardar la configuración.

Las nuevas directivas de Windows 10 que cree no se asignan a ningún usuario hasta que no lo haga de forma expresa. Para asignar una directiva de Windows 10, vea [Asignación de una directiva de Windows 10 a usuarios](~/apps/app-protection-policies.md#assign-a-windows-10-policy-to-users)

### <a name="assign-a-windows-10-policy-to-users"></a>Asignación de una directiva de Windows 10 a usuarios 

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

### <a name="change-existing-windows-10-policies"></a>Cambio de las directivas de Windows 10 existentes
Puede editar una directiva existente y aplicarla a los usuarios objetivo. Sin embargo, al cambiar las directivas existentes, los usuarios que ya han iniciado sesión en las aplicaciones no verán los cambios durante un período de ocho horas.

Para ver el efecto de los cambios inmediatamente, el usuario final debe cerrar sesión en la aplicación y volver a iniciarla.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para cambiar la lista de aplicaciones asociadas con la directiva

1. En el panel **Directivas de protección de aplicaciones**, seleccione la directiva que desea modificar.

2. En el panel *Intune App Protection*, seleccione **Aplicaciones de destino** para abrir la lista de aplicaciones.

3. Quite o agregue aplicaciones de la lista y luego seleccione el icono **Guardar** para guardar los cambios.

#### <a name="to-change-the-list-of-user-groups"></a>Para cambiar la lista de grupos de usuarios

1. En el panel **Directivas de protección de aplicaciones**, seleccione la directiva que desea modificar.

2. En el panel *Intune App Protection*, seleccione **Asignaciones** para abrir el panel **Intune App Protection: Asignaciones** que muestra la lista de los grupos de usuarios actuales que tienen esta directiva.

3. Para agregar un nuevo grupo de usuarios a la directiva, en la pestaña *Incluir*, elija **Seleccionar grupos para incluir** y seleccione el grupo de usuarios. Elija **Seleccionar** para agregar el grupo. 

4. Para excluir un grupo de usuarios, en la pestaña *Excluir*, elija **Seleccionar grupos para excluir** y seleccione el grupo de usuarios. Elija **Seleccionar** para quitar el grupo de usuarios.  

5. Para eliminar los grupos que se agregaron anteriormente, ya sea en la pestaña *Incluir* o en la pestaña *Excluir*, seleccione los puntos suspensivos (...) y seleccione **Eliminar**. 

5. Una vez que estén listos los cambios en las asignaciones, seleccione **Guardar** para guardar la configuración e implementar la directiva en el nuevo conjunto de usuarios. Si seleccione **Descartar** antes de guardar la configuración, se descartarán todos los cambios realizados en las pestañas *Incluir* y *Excluir*.

### <a name="to-change-windows-10-policy-settings"></a>Para cambiar la configuración de una directiva de Windows 10

1. En el panel **Directivas de protección de aplicaciones**, seleccione la directiva que desea modificar.

2. En el panel *Intune App Protection*, seleccione **Propiedades** para abrir la lista de áreas de configuración que puede modificar. 

3. Seleccione el área de configuración con el valor que desea modificar, como **Reubicación de datos** o **Requisitos de acceso**. A continuación, cambie la configuración con los nuevos valores.

4. Seleccione el icono **Guardar** para guardar los cambios. Repita el proceso para seleccionar un área de configuración y modificarla y, a continuación, guarde los cambios, hasta que se completen todos los cambios. A continuación, puede cerrar el panel *Intune App Protection: Propiedades*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Destinar directivas de protección de aplicaciones en función del estado de administración del dispositivo
En muchas organizaciones es habitual permitir que los usuarios finales puedan usar los dispositivos administrados de administración de dispositivos móviles (MDM) de Intune (como los dispositivos propiedad de las empresas) y los dispositivos no administrados que únicamente están protegidos con directivas de protección de aplicaciones de Intune. Los dispositivos no administrados a menudo se conocen como Bring Your Own Devices (BYOD).

Dado que las directivas de protección de aplicaciones de Intune están destinadas a la identidad de un usuario, la configuración de protección de un usuario puede aplicarse tanto a los dispositivos inscritos (administrados con MDM) como a los dispositivos no inscritos (sin MDM). Por lo tanto, puede destinar una directiva de protección de aplicaciones de Intune a dispositivos iOS y Android inscritos y no inscritos de Intune. Puede tener una directiva de protección para los dispositivos no administrados a la que se apliquen unos controles de prevención de pérdida de datos (DLP) estrictos y una directiva de protección independiente para los dispositivos administrados con MDM en la que los controles DLP pueden ser un poco menos restrictivos. Para más información sobre cómo funciona esto en dispositivos de Android Enterprise personales, vea [Directivas de protección de aplicaciones y perfiles de trabajo](android-deployment-scenarios-app-protection-work-profiles.md).

Para crear estas directivas, vaya a **Aplicaciones cliente** > **Directivas de protección de aplicaciones** en la consola de Intune y haga clic en **Crear directiva**. También puede editar una directiva de protección de aplicaciones existente. Para que la directiva de protección de aplicaciones se aplique a los dispositivos tanto administrados como no administrados, vaya a la página **Aplicaciones** y confirme que la opción **Destinar a todos los tipos de aplicaciones** está establecida en el valor predeterminado, **Sí**. Si quiere efectuar una asignación granular según el estado de administración, establezca **Destinar a todos los tipos de aplicaciones** en **No**. 

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
