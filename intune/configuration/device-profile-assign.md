---
title: Asignación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Use el centro de administración de Microsoft Endpoint Manager para asignar perfiles de dispositivo y directivas a usuarios y dispositivos. Aprenda a excluir grupos de una asignación de perfil en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 252af3c7447b59ee6aaeb4cb05bed0579ae8af4c
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206710"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Asignación de perfiles de dispositivo en Microsoft Intune

Puede crear un perfil e incluir toda la configuración que escribió. El paso siguiente es implementar o "asignar el perfil" a los grupos de dispositivos o usuarios de Azure Active Directory (Azure AD). Cuando se asigna, los usuarios y dispositivos reciben su perfil y se aplica la configuración que escribió.

En este artículo se muestra cómo asignar un perfil y se incluye información sobre el uso de las etiquetas de ámbito en los perfiles.

> [!NOTE]  
> Cuando se quita un perfil o deja de estar asignado a un dispositivo, la configuración puede mantener el valor existente. La configuración no se revierte a un valor predeterminado. Para cambiar la configuración a un valor diferente, cree un perfil y asígnelo.

## <a name="before-you-begin"></a>Antes de comenzar

Asegúrese de que tiene el rol adecuado para asignar perfiles. Para más información, vea [Control de acceso basado en rol (RBAC) con Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="assign-a-device-profile"></a>Asignar un perfil de dispositivo

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración**. Se muestran todos los perfiles.
3. Seleccione el perfil que quiere asignar > **Asignaciones**.
4. Elija **Incluir** grupos o **Excluir** grupos y, luego, seleccione los grupos. Al seleccionar los grupos, se elige un grupo de Azure AD. Para seleccionar varios grupos, mantenga presionada la tecla **Ctrl** y seleccione los grupos.

    ![Captura de pantalla de las opciones para incluir o excluir grupos de una asignación de perfil](./media/device-profile-assign/group-include-exclude.png)

5. Guarde los cambios mediante **Guardar**.

### <a name="evaluate-how-many-users-are-targeted"></a>Evaluación de cuántos usuarios se rigen por una directiva

Cuando asigna el perfil, también puede **evaluar** cuántos usuarios se verán afectados. Esta característica calcula los usuarios, no los dispositivos.

1. En el Centro de administración, seleccione **Dispositivos** > **Perfiles de configuración**.
2. Seleccione un perfil > **Asignaciones** > **Evaluar**. Un mensaje muestra a cuántos usuarios se aplica este perfil.

Si el botón **Evaluar** está atenuado, asegúrese de que el perfil se asignó a uno o más grupos.

## <a name="use-scope-tags-or-applicability-rules"></a>Uso de etiquetas de ámbito o reglas de aplicabilidad

Cuando crea o actualiza un perfil, puede agregar también etiquetas de ámbito al perfil.

Las **etiquetas de ámbito** son una excelente manera de filtrar los perfiles por grupos específicos, como `US-NC IT Team` o `JohnGlenn_ITDepartment`. En el artículo sobre [el uso de RBAC y las etiquetas de ámbito para TI distribuida](../fundamentals/scope-tags.md) tiene más información.

En los dispositivos Windows 10, puede agregar reglas **de aplicabilidad** para que el perfil solo se aplique a una versión específica del sistema operativo o a una edición específica de Windows. En el artículo sobre [reglas de aplicabilidad](device-profile-create.md#applicability-rules) se incluye más información.

## <a name="user-groups-vs-device-groups"></a>Grupos de usuarios y grupos de dispositivos

Muchos usuarios se preguntan cuándo usar grupos de usuarios y cuándo grupos de dispositivos. La respuesta depende del objetivo. Esta es una guía para ayudarle a comenzar.

### <a name="device-groups"></a>Grupos de dispositivos

Si quiere aplicar la configuración de un dispositivo, con independencia de quién haya iniciado sesión, asigne los perfiles a un grupo de dispositivos. La configuración que se aplica a grupos de dispositivos siempre va con el dispositivo, no con el usuario.

Por ejemplo:

- Los grupos de dispositivos son útiles para administrar dispositivos que no tienen un usuario dedicado. Este sería el caso de dispositivos que imprimen entradas, examinan inventario, se comparten entre los trabajadores por turnos o se asignan a un almacén específico. Coloque estos dispositivos en un grupo de dispositivos y asigne sus perfiles a este grupo.

- Se crea un [perfil Device Firmware Configuration Interface (DFCI) de Intune](device-firmware-configuration-interface-windows.md) que actualiza la configuración en el BIOS. Por ejemplo, puede configurar este perfil para deshabilitar la cámara del dispositivo o bloquear las opciones de arranque a fin de impedir que los usuarios arranquen otro sistema operativo. Este perfil es un buen escenario para asignar a un grupo de dispositivos.

- En algunos dispositivos Windows específicos, siempre le interesará controlar algunos valores de configuración de Microsoft Edge, con independencia de quién use el dispositivo. Por ejemplo, si quiere bloquear todas las descargas, limite todas las cookies a la sesión de exploración actual y elimine el historial de exploración. En este escenario, coloque estos dispositivos Windows específicos en un grupo de dispositivos. Luego, cree una [plantilla administrativa en Intune](administrative-templates-windows.md), agregue esta configuración de dispositivo y, luego, asigne este perfil al grupo dispositivos.

En resumen, use grupos de dispositivos cuando no le preocupe quién haya iniciado sesión en el dispositivo, o si alguien ha iniciado sesión. Le interesa que la configuración esté siempre en el dispositivo.

### <a name="user-groups"></a>Grupos de usuarios

La configuración del perfil que se aplica a los grupos de usuarios siempre acompaña al usuario y va con él cuando inicia sesión en sus muchos dispositivos. Es normal que los usuarios tengan muchos dispositivos, como un equipo Surface Pro para trabajar o un dispositivo iOS personal. Además, es normal que una persona acceda al correo electrónico y a otros recursos de la organización desde estos dispositivos.

Por ejemplo:

- Quiere colocar un icono del departamento de soporte técnico en todos los dispositivos de todos los usuarios. En este escenario, coloque estos usuarios en un grupo de usuarios y asígnele el perfil de icono del departamento de soporte técnico.
- Un usuario recibe un nuevo dispositivo propiedad de la organización. El usuario inicia sesión en el dispositivo con su cuenta de dominio. El dispositivo se registra automáticamente en Azure AD y se administra automáticamente en Intune. Este perfil es un buen escenario para asignar a un grupo de usuarios.
- Cada vez que un usuario inicia sesión en un dispositivo, querrá controlar las características de las aplicaciones, como OneDrive u Office. En este escenario, asigne su configuración de perfil de OneDrive u Office a un grupo de usuarios.

  Por ejemplo, quiere bloquear los controles ActiveX que no son de confianza en las aplicaciones de Office. Puede crear una [plantilla administrativa en Intune](administrative-templates-windows.md), configurar esta opción y, luego, asignar este perfil a un grupo de usuarios.

En resumen, use grupos de usuarios cuando quiera que la configuración y las reglas vayan siempre con el usuario, sea cual sea el dispositivo que usen.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de una asignación de perfil

Los perfiles de configuración de dispositivos de Intune permiten incluir y excluir grupos de la asignación de perfiles.

Como procedimiento recomendado, cree y asigne perfiles específicamente para sus grupos de usuarios. Además, cree y asigne perfiles diferentes específicamente para los grupos de dispositivos. Para más información sobre los grupos, consulte [Agregar grupos para organizar usuarios y dispositivos](../fundamentals/groups-add.md).

Cuando asigne los perfiles, use la tabla siguiente al incluir y excluir grupos. Una marca de verificación significa que se admite la asignación:

![Las opciones admitidas incluyen o excluyen grupos de una asignación de perfil](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>Qué debe saber

- La exclusión tiene prioridad sobre la inclusión en los siguientes escenarios de tipos de grupos:

  - Inclusión y exclusión de grupos de usuarios
  - Inclusión y exclusión de grupos de dispositivos

  Por ejemplo, se asigna un perfil de dispositivo al grupo de usuarios **Todos los usuarios corporativos**, pero se excluye a los miembros del grupo de usuarios **Personal de administración sénior**. Puesto que ambos grupos son grupos de usuarios, **Todos los usuarios corporativos** excepto el **Personal de administración ejecutiva** obtienen el perfil.

- Intune no evalúa las relaciones entre grupos de usuarios y dispositivos. Si asigna perfiles a grupos mixtos, es posible que los resultados no sean los deseados o esperados.

  Por ejemplo, puede asignar un perfil de dispositivo al grupo de usuarios **Todos los usuarios**, pero excluir un grupo de dispositivos **Todos los dispositivos personales**. En esta asignación de perfil de grupo mixto, **Todos los usuarios** obtienen el perfil. La exclusión no se aplica.

  Como resultado, no se recomienda asignar perfiles a grupos mixtos.

## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de perfiles de dispositivo](device-profile-monitor.md) para instrucciones sobre cómo supervisar los perfiles y los dispositivos que los ejecutan.
