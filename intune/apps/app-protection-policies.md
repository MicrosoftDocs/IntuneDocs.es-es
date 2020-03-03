---
title: Crear e implementar directivas de protección de aplicaciones
titleSuffix: Microsoft Intune
description: En este tema se describe cómo crear y asignar directivas de protección de aplicaciones (APP) de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: 7d1a55f758be50c342a5c8851106f0c37e6aec50
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513731"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Creación y asignación de directivas de protección de aplicaciones

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Aprenda a crear directivas de protección de aplicaciones de Microsoft Intune y asignarlas a los usuarios de la organización. En este tema también se describe cómo realizar cambios en las directivas existentes.

## <a name="before-you-begin"></a>Antes de comenzar

Las directivas de protección de aplicaciones se pueden aplicar a aplicaciones que se ejecutan en dispositivos que podrían estar o no administrados por Intune. Para obtener una descripción más detallada de cómo funcionan las directivas de protección de aplicaciones y los escenarios admitidos por las directivas de protección de aplicaciones de Intune, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

Si desea acceder a una lista de aplicaciones compatibles con MAM, vea la [lista de aplicaciones de MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Para obtener información acerca de cómo agregar aplicaciones de línea de negocio (LOB) de su organización a Microsoft Intune para prepararse para las directivas de protección de aplicaciones, consulte [Incorporación de aplicaciones a Microsoft Intune](apps-add.md).

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>Directivas de protección de aplicaciones para aplicaciones de iOS/iPadOS y Android

Cuando se crea una directiva de protección de aplicaciones para aplicaciones de iOS/iPadOS y Android, se lleva a cabo un moderno flujo de proceso de Intune que da como resultado una directiva de protección de aplicaciones nueva.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>Crear una directiva de protección de aplicaciones para aplicaciones de iOS/iPadOS o Android
1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. En el portal de Intune, elija **Aplicaciones** > **Directivas de protección de aplicaciones**. Al seleccionar esa opción, se abrirán los detalles de **Directivas de protección de aplicaciones**, donde creará nuevas directivas y editará las existentes.
3. Seleccione **Crear directiva** y, luego, **iOS/iPadOS** o **Android**. Se abre el panel **Crear directiva**.
4. En la página **Datos básicos**, agregue los siguientes valores:

    | Valor | Descripción |
    |--------------|------------------------------------------------|
    | Nombre | Nombre de esta directiva de protección de aplicaciones |
    | Descripción | [Opcional] Descripción de esta directiva de protección de aplicaciones |


    El valor de **Plataforma** se establece en función de la elección anterior.

    ![Captura de pantalla de la pestaña Datos básicos del panel Crear directiva](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. Haga clic en **Siguiente** para abrir la página **Aplicaciones**.<br>
    La página **Aplicaciones** permite elegir cómo se quiere aplicar esta directiva a las aplicaciones en distintos dispositivos. Debe agregar al menos una aplicación.<p>
    
    | Valor/opción | Descripción |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Destinar a todos los tipos de aplicaciones | Use esta opción para destinar la directiva a las aplicaciones en dispositivos que se encuentren en cualquier estado de administración. Elija **No** para destinar a aplicaciones en tipos de dispositivos específicos. Para más información, consulte [Destinar directivas de protección de aplicaciones en función del estado de administración del dispositivo](#target-app-protection-policies-based-on-device-management-state). |
    |     Tipos de dispositivo | Use esta opción para especificar si esta directiva se aplica a dispositivos administrados por MDM o a dispositivos no administrados. En el caso de las directivas de aplicaciones iOS/iPadOS, elija entre **Dispositivos no administrados** y **Dispositivos administrados**. En el caso de las directivas de aplicaciones de Android, elija entre **Dispositivos no administrados**, **Administrador de dispositivos Android** y **Android Enterprise**.  |
    | Aplicaciones públicas | Haga clic en **Seleccionar aplicaciones públicas** para elegir las aplicaciones de destino. |
    | Aplicaciones personalizadas | Haga clic en **Seleccionar aplicaciones personalizadas** para seleccionar aplicaciones personalizadas de destino en función de un identificador de paquete. |
    
    Las aplicaciones que se seleccionen aparecerán en la lista de aplicaciones públicas y personalizadas. 
6. Haga clic en **Siguiente** para abrir la página **Protección de datos**.<br>
    Esta página proporciona opciones de controles de prevención de pérdida de datos (DLP), incluidas restricciones para cortar, copiar, pegar y guardar como. Estas opciones determinan cómo van a interactuar los usuarios con los datos de las aplicaciones donde esta directiva de protección de aplicaciones está en vigor.

    **Configuración de la protección de datos**:<br>
    - **Protección de datos de iOS/iPadOS**: para más información, vea la sección [Protección de datos en Configuración de directivas de protección de aplicaciones de iOS/iPadOS](~/apps/app-protection-policy-settings-ios.md#data-protection).
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

9. Haga clic en **Siguiente** para abrir la página **Asignaciones**.<br>
   La página **Asignaciones** permite asignar la directiva de protección de aplicaciones a grupos de usuarios.

10. Haga clic en **Siguiente: Revisar + crear** para revisar los valores y la configuración especificados para esta directiva de protección de aplicaciones.

11. Cuando termine, haga clic en **Crear** para crear la directiva de protección de aplicaciones en Intune. 

    > [!TIP]
    > Esta configuración de directiva se aplica solo al usar aplicaciones en el contexto de trabajo. Cuando los usuarios finales usen la aplicación para realizar una tarea personal, no se verán afectados por estas directivas. Tenga en cuenta que cuando se crea un nuevo archivo se considera un archivo personal. 

Los usuarios finales pueden descargar las aplicaciones desde App Store o Google Play. Para obtener más información, vea:
* [What to expect when your Android app is managed by app protection policies](../fundamentals/end-user-mam-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [Qué esperar cuando la aplicación iOS/iPadOS se administra con directivas de protección de aplicaciones](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>Cambiar las directivas existentes
Puede editar una directiva existente y aplicarla a los usuarios objetivo. Sin embargo, al cambiar las directivas existentes, los usuarios que ya han iniciado sesión en las aplicaciones no verán los cambios durante un período de ocho horas.

Para ver el efecto de los cambios inmediatamente, el usuario final debe cerrar sesión en la aplicación y volver a iniciarla.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Para cambiar la lista de aplicaciones asociadas con la directiva

1. En el panel **Directivas de protección de aplicaciones**, seleccione la directiva que desea modificar.

2. En el panel *Intune App Protection*, seleccione **Propiedades**.

3. Junto a la sección titulada *Aplicaciones*, seleccione **Editar**.

4. La página **Aplicaciones** permite elegir cómo se quiere aplicar esta directiva a las aplicaciones en distintos dispositivos. Debe agregar al menos una aplicación.<p>
    
    | Valor/opción | Descripción |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Destinar a todos los tipos de aplicaciones | Use esta opción para destinar la directiva a las aplicaciones en dispositivos que se encuentren en cualquier estado de administración. Elija **No** para destinar a aplicaciones en tipos de dispositivos específicos. Para más información, consulte [Destinar directivas de protección de aplicaciones en función del estado de administración del dispositivo](#target-app-protection-policies-based-on-device-management-state). |
    |     Tipos de dispositivo | Use esta opción para especificar si esta directiva se aplica a dispositivos administrados por MDM o a dispositivos no administrados. En el caso de las directivas de aplicaciones iOS/iPadOS, elija entre **Dispositivos no administrados** y **Dispositivos administrados**. En el caso de las directivas de aplicaciones de Android, elija entre **Dispositivos no administrados**, **Administrador de dispositivos Android** y **Android Enterprise**.  |
    | Aplicaciones públicas | Haga clic en **Seleccionar aplicaciones públicas** para elegir las aplicaciones de destino. |
    | Aplicaciones personalizadas | Haga clic en **Seleccionar aplicaciones personalizadas** para seleccionar aplicaciones personalizadas de destino en función de un identificador de paquete. |

    Las aplicaciones que se seleccionen aparecerán en la lista de aplicaciones públicas y personalizadas. 

5. Haga clic en **Revisar y crear** para revisar las aplicaciones seleccionadas para esta directiva.

6. Cuando termine, haga clic en **Guardar** para actualizar la directiva de protección de aplicaciones.
 
#### <a name="to-change-the-list-of-user-groups"></a>Para cambiar la lista de grupos de usuarios

1. En el panel **Directivas de protección de aplicaciones**, seleccione la directiva que desea modificar.

2. En el panel *Intune App Protection*, seleccione **Propiedades**.

3. Junto a la sección titulada *Asignaciones*, seleccione **Editar**.

4. Para agregar un nuevo grupo de usuarios a la directiva, en la pestaña *Incluir*, elija **Seleccionar grupos para incluir** y seleccione el grupo de usuarios. Elija **Seleccionar** para agregar el grupo. 

5. Para excluir un grupo de usuarios, en la pestaña *Excluir*, elija **Seleccionar grupos para excluir** y seleccione el grupo de usuarios. Elija **Seleccionar** para quitar el grupo de usuarios.  

6. Para eliminar los grupos que se agregaron anteriormente, ya sea en la pestaña *Incluir* o en la pestaña *Excluir*, seleccione los puntos suspensivos (...) y seleccione **Eliminar**.

7. Haga clic en **Revisar y crear** para revisar los grupos de usuarios seleccionados para esta directiva.

8. Una vez que estén listos los cambios en las asignaciones, seleccione **Guardar** para guardar la configuración e implementar la directiva en el nuevo conjunto de usuarios. Si seleccione **Cancelar** antes de guardar la configuración, se descartarán todos los cambios realizados en las pestañas *Incluir* y *Excluir*.

### <a name="to-change-policy-settings"></a>Para cambiar la configuración de directiva

1. En el panel **Directivas de protección de aplicaciones**, seleccione la directiva que desea modificar.

2. En el panel *Intune App Protection*, seleccione **Propiedades**.

3. Junto a la sección correspondiente a la configuración que quiere cambiar, seleccione **Editar**. A continuación, cambie la configuración con los nuevos valores.

7. Haga clic en **Revisar y crear** para revisar la configuración actualizada de esta directiva.

4. Seleccione **Guardar** para guardar los cambios. Repita el proceso para seleccionar un área de configuración y modificarla y, a continuación, guarde los cambios, hasta que se completen todos los cambios. A continuación, puede cerrar el panel *Intune App Protection: Propiedades*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Destinar directivas de protección de aplicaciones en función del estado de administración del dispositivo
En muchas organizaciones es habitual permitir que los usuarios finales puedan usar los dispositivos administrados de administración de dispositivos móviles (MDM) de Intune (como los dispositivos propiedad de las empresas) y los dispositivos no administrados que únicamente están protegidos con directivas de protección de aplicaciones de Intune. Los dispositivos no administrados a menudo se conocen como Bring Your Own Devices (BYOD).

Dado que las directivas de protección de aplicaciones de Intune están destinadas a la identidad de un usuario, la configuración de protección de un usuario puede aplicarse tanto a los dispositivos inscritos (administrados con MDM) como a los dispositivos no inscritos (sin MDM). Por lo tanto, puede destinar una directiva de protección de aplicaciones de Intune a dispositivos iOS/iPadOS y Android inscritos y no inscritos de Intune. Puede tener una directiva de protección para los dispositivos no administrados a la que se apliquen unos controles de prevención de pérdida de datos (DLP) estrictos y una directiva de protección independiente para los dispositivos administrados con MDM en la que los controles DLP pueden ser un poco menos restrictivos. Para más información sobre cómo funciona esto en dispositivos de Android Enterprise personales, vea [Directivas de protección de aplicaciones y perfiles de trabajo](android-deployment-scenarios-app-protection-work-profiles.md).

Para crear estas directivas, vaya a **Aplicaciones cliente** > **Directivas de protección de aplicaciones** en la consola de Intune y haga clic en **Crear directiva**. También puede editar una directiva de protección de aplicaciones existente. Para que la directiva de protección de aplicaciones se aplique a los dispositivos tanto administrados como no administrados, vaya a la página **Aplicaciones** y confirme que la opción **Destinar a todos los tipos de aplicaciones** está establecida en el valor predeterminado, **Sí**. Si quiere efectuar una asignación granular según el estado de administración, establezca **Destinar a todos los tipos de aplicaciones** en **No**. 

### <a name="device-types"></a>Tipos de dispositivo

- **No administrado**: Dispositivos no administrados son aquellos en los que no se ha detectado la administración MDM de Intune. Esto incluye dispositivos administrados por proveedores de terceros de MDM.
- **Dispositivos administrados por Intune**: MDM de Intune administra los dispositivos administrados.
- **Administrador de dispositivos Android**: Dispositivos administrados por Intune mediante la API de administración de dispositivos Android.
- **Android Enterprise**: Dispositivos administrados por Intune mediante perfiles de trabajo de Android Enterprise o administración completa de dispositivos de Android Enterprise.

> [!NOTE]
> Los dispositivos Android le pedirán que instale la aplicación Portal de empresa de Intune independientemente del tipo de dispositivo que se elija. Por ejemplo, si selecciona "Android Enterprise", se le seguirá solicitando a los usuarios con dispositivos Android no administrados.

Para iOS/iPadOS, se requieren ajustes adicionales en la configuración de la aplicación para dirigir la configuración de la directiva de protección de aplicaciones (APP) a las aplicaciones de dispositivos inscritos en Intune:

- **IntuneMAMUPN** debe configurarse para todas las aplicaciones administradas de MDM. Para más información, vea [Administración de transferencias de datos entre aplicaciones iOS/iPadOS en Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** debe configurarse para todas las aplicaciones administradas por MDM de línea de negocio y de terceros. **IntuneMAMDeviceID** debe configurarse en el token de identificador de dispositivo. Por ejemplo, `key=IntuneMAMDeviceID, value={{deviceID}}`. Para más información, vea [Agregar directivas de configuración de aplicaciones para dispositivos iOS/iPadOS administrados](app-configuration-policies-use-ios.md).
- Si solo está configurado **IntuneMAMDeviceID**, la aplicación Intune considerará el dispositivo como no administrado.

> [!NOTE]
> Para obtener información específica de compatibilidad con iOS/iPadOS sobre las directivas de protección de aplicaciones según el estado de administración de los dispositivos, vea [Directivas de protección MAM destinadas según el estado de administración](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state).

## <a name="policy-settings"></a>Configuración de la directiva
Para ver una lista completa de las configuraciones de directivas para iOS/iPadOS y Android, seleccione uno de los siguientes vínculos:

- [Directivas de iOS/iPadOS](app-protection-policy-settings-ios.md)
- [Directivas de Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Pasos siguientes
[Supervisar el estado del cumplimiento y del usuario](app-protection-policies-monitor.md)

## <a name="see-also"></a>Vea también
* [What to expect when your Android app is managed by app protection policies](../fundamentals/end-user-mam-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [Qué esperar cuando la aplicación iOS/iPadOS se administra con directivas de protección de aplicaciones](../fundamentals/end-user-mam-apps-ios.md)
