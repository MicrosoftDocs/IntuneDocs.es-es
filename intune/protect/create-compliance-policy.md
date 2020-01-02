---
title: Creación de directivas de cumplimiento de dispositivos en Microsoft Intune - Azure | Microsoft Docs
description: Creación de directivas de cumplimiento de dispositivos, información general de los estados y los niveles de gravedad, uso del estado En período de gracia, trabajar con el acceso condicional, control de los dispositivos sin una directiva asignada y diferencias de cumplimiento en Azure Portal y el portal clásico en Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba6b8fb66d25af3833e55eebc12e8b6df2fb5ba5
ms.sourcegitcommit: 66e284fe092e19c1da72b4b770e45bf25ac7910c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74860237"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Creación de una directiva de cumplimiento en Microsoft Intune

Las directivas de cumplimiento de dispositivos son una característica clave cuando se usa Intune para proteger los recursos de su organización. En Intune, puede crear reglas y opciones de configuración que los dispositivos deben cumplir para que se consideren conformes, por ejemplo, una versión de SO mínima. Si el dispositivo no las cumple, puede bloquear el acceso a datos y recursos mediante el [acceso condicional](conditional-access.md).

También puede realizar acciones en caso de incumplimiento, como enviar un correo electrónico de notificación al usuario. Para información general sobre lo que hacen las directivas de cumplimiento y cómo se usan, consulte [Introducción al cumplimiento de dispositivos](device-compliance-get-started.md).

En este artículo:

- Se enumeran los requisitos previos y los pasos para crear una directiva de cumplimiento.
- Se muestra cómo asignar la directiva a los grupos de dispositivos y usuarios.
- Se describen características adicionales, como las etiquetas de ámbito para "filtrar" las directivas, y los pasos que puede realizar en los dispositivos que no cumplen con las reglamentaciones.
- Se enumeran los tiempos de ciclo de actualización de sincronización cuando los dispositivos reciben actualizaciones de directiva.

## <a name="before-you-begin"></a>Antes de comenzar

Para usar las directivas de cumplimiento de dispositivos, asegúrese de lo siguiente:

- Use las siguientes suscripciones:

  - Intune
  - Si usa el acceso condicional, necesita la edición Azure Active Directory (AD) Premium. [Precios de Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) muestra lo que obtiene con las distintas ediciones. El cumplimiento de Intune no requiere Azure AD.

- Use una plataforma compatible:

  - Administrador de dispositivos Android
  - Android Enterprise
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - Windows Phone 8,1

- Inscriba dispositivos en Intune (necesario para ver el estado de cumplimiento)

- Inscriba dispositivos en un usuario o realice la inscripción sin un usuario primario. Los dispositivos inscritos en varios usuarios no se admiten.

## <a name="create-the-policy"></a>Creación de la directiva

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Directivas de cumplimiento** > **Crear directiva**.

3. Especifique las siguientes propiedades:

   - **Nombre**: escriba un nombre descriptivo para la directiva. Asígnele un nombre a las directivas para que pueda identificarlas de manera sencilla más adelante. Por ejemplo, un buen nombre de directiva es **Marcar los dispositivos iOS liberados como no compatibles**.

   - **Descripción**: escriba una descripción para la directiva. Esta configuración es opcional pero recomendada.

   - **Plataforma**: seleccione la plataforma de los dispositivos. Las opciones son:
     - **Administrador de dispositivos Android**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 y versiones posteriores**
     - **Windows 10 y versiones posteriores**

     En *Android Enterprise*, debe seleccionar un **Tipo de perfil**:
     - **Propietario del dispositivo**
     - **Perfil de trabajo**

   - **Configuración**: En los artículos siguientes se muestran y describen los valores de cada plataforma:
     - [Administrador de dispositivos Android](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1, Windows 8.1 y versiones posteriores](compliance-policy-create-windows-8-1.md)
     - [Windows 10 y versiones posteriores](compliance-policy-create-windows.md)  

   - **Ubicaciones** *(administrador de dispositivos Android)* : En la directiva, puede forzar el cumplimiento según la ubicación del dispositivo. Elija entre las ubicaciones existentes. ¿Aún no tiene una ubicación? En [Usar ubicaciones (límite de red) en Intune](use-network-locations.md) se ofrecen algunas instrucciones.  

   - **Acciones en caso de incumplimiento**: En el caso de los dispositivos que no cumplen con las directivas de cumplimiento, puede agregar una secuencia de acciones para aplicar de manera automática. Puede cambiar la programación cuando el dispositivo se marca como no conforme, por ejemplo, después de un día. También puede configurar una segunda acción que envía un correo electrónico al usuario cuando el dispositivo es no conforme.

     En [Adición de acciones en caso de incumplimiento](actions-for-noncompliance.md) se proporciona más información, por ejemplo, cómo crear un correo electrónico para notificar a los usuarios.

     Por ejemplo, se usa la característica Ubicaciones y se agrega una ubicación en una directiva de cumplimiento. La acción predeterminada en caso de incumplimiento se aplica cuando se selecciona al menos una ubicación. Si el dispositivo no está conectado a las ubicaciones seleccionadas, se considera de inmediato como no conforme. Puede dar a los usuarios un período de gracia, por ejemplo, un día.

   - **Ámbito (etiquetas)** : Las etiquetas de ámbito son una excelente manera de filtrar las directivas por grupos específicos, como `US-NC IT Team` o `JohnGlenn_ITDepartment`. Una vez que agrega la configuración, también puede agregar una etiqueta de ámbito a las directivas de cumplimiento. [Uso de etiquetas de ámbito para filtrar directivas](../fundamentals/scope-tags.md) es un recurso útil.

4. Cuando termine, seleccione **Aceptar** > **Crear** para guardar los cambios. La directiva se crea y se muestra en la lista. A continuación, asigne la directiva a los grupos.

## <a name="assign-the-policy"></a>Asignación de la directiva

Una vez que se crea una directiva, el paso siguiente es asignar la directiva a los grupos:

1. Elija una directiva que haya creado. Las directivas existentes están en **Dispositivos** > **Directivas de cumplimiento** > **Directivas**.

2. Seleccione la *directiva* > **Asignaciones**. Puede incluir o excluir grupos de seguridad de Azure Active Directory (AD).

3. Elija **Grupos seleccionados** para ver los grupos de seguridad de Azure AD. Seleccione los grupos a los que quiere aplicar esta directiva > Elija **Guardar** para implementar la directiva.

Los usuarios o dispositivos de destino de la directiva se evalúan para comprobar su compatibilidad cuando se registran en Intune.

### <a name="evaluate-how-many-users-are-targeted"></a>Evaluación de cuántos usuarios se rigen por una directiva

Cuando asigna la directiva, también puede **evaluar** cuántos usuarios se verán afectados. Esta característica calcula los usuarios, no los dispositivos.

1. En Intune, seleccione **Dispositivos** > **Directivas de cumplimiento** > **Directivas**.

2. Seleccione una *directiva* > **Asignaciones** > **Evaluar**. Un mensaje muestra a cuántos usuarios se aplica esta directiva.

Si el botón **Evaluar** está atenuado, asegúrese de que la directiva se asignó a uno o más grupos.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>Tiempos de ciclo de actualización

Intune usa distintos ciclos de actualización para comprobar las actualizaciones de las directivas de cumplimiento. Si el dispositivo se inscribió recientemente, la inserción en el repositorio se ejecuta con más frecuencia. En el artículo sobre [ciclos de actualización de directivas y perfiles](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) se indican los tiempos de actualización estimados.

En cualquier momento, los usuarios pueden abrir la aplicación Portal de empresa de Intune y sincronizar el dispositivo para comprobar de inmediato las actualizaciones del perfil.

### <a name="assign-an-ingraceperiod-status"></a>Asignar un estado En período de gracia

El estado En período de gracia de una directiva de cumplimiento es un valor. Este valor se determina mediante la combinación del período de gracia de un dispositivo y el estado real del dispositivo para esa directiva de cumplimiento.

En concreto, si un dispositivo tiene un estado No conforme para una directiva de cumplimiento asignada y si se dan los casos siguientes:

- El dispositivo no tiene asignado ningún período de gracia, de modo que el valor asignado para la directiva de cumplimiento es No conforme.
- El dispositivo tiene un período de gracia que ha expirado, de modo que el valor asignado para la directiva de cumplimiento es No conforme.
- El dispositivo tiene un período de gracia futuro, de modo que el valor asignado para la directiva de cumplimiento es En período de gracia

En la siguiente tabla se resumen estos aspectos:

|Estado de cumplimiento real|Valor del período de gracia asignado|Estado de cumplimiento efectivo|
|---------|---------|---------|
|No conforme |Ningún periodo de gracia asignado |No conforme |
|No conforme |Fecha de ayer|No conforme|
|No conforme |Fecha de mañana|En período de gracia|

Para obtener más información sobre la supervisión de las directivas de cumplimiento de dispositivos, vea [Supervisión de las directivas de cumplimiento de dispositivos Intune](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Asignar un estado de directiva de cumplimiento resultante

Si un dispositivo tiene varias directivas de cumplimiento y distintos estados de cumplimiento para dos o más de dichas directivas, se asigna un único estado de cumplimiento resultante. Esta asignación se basa en un nivel de gravedad conceptual que se asigna a cada estado de cumplimiento. Cada estado de cumplimiento tiene el nivel de gravedad siguiente:

|Estado  |Gravedad  |
|---------|---------|
|Unknown     |1|
|No aplicable     |2|
|Conforme|3|
|En período de gracia|4|
|No conforme|5|
|Error|6|

Si un dispositivo tiene varias directivas de cumplimiento, se le asignará el nivel de gravedad más alto de todas las directivas.

Por ejemplo, un dispositivo tiene 3 directivas de cumplimiento asignadas: la primera, con el estado Desconocido (gravedad 1); la segunda, con el estado Conforme (gravedad 3) y, la tercera, con el estado InGracePeriod (gravedad 4). El estado InGracePeriod tiene el nivel de gravedad más alto. Por lo tanto, las tres directivas tienen el estado de cumplimiento InGracePeriod.

## <a name="next-steps"></a>Pasos siguientes

[Supervise las directivas](compliance-policy-monitor.md).
