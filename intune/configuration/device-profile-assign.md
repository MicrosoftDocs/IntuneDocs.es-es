---
title: Asignación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Use Azure Portal para asignar perfiles de dispositivo y directivas a los usuarios y a los dispositivos. Aprenda a excluir grupos de una asignación de perfil en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
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
ms.openlocfilehash: ae8bc7d5797a2ba6404331166e9d955bbb2fadf9
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059589"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Asignación de perfiles de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede crear un perfil e incluir toda la configuración que escribió. El paso siguiente es implementar o "asignar el perfil" a los grupos de dispositivos o usuarios de Azure Active Directory (Azure AD). Cuando se asigna, los usuarios y dispositivos reciben su perfil y se aplica la configuración que escribió.

En este artículo se muestra cómo asignar un perfil y se incluye información sobre el uso de las etiquetas de ámbito en los perfiles.

> [!NOTE]  
> Cuando se quita una directiva o deja de estar asignada a un dispositivo, el parámetro puede mantener el valor existente. La configuración no se revierte a un valor predeterminado. Para cambiar el parámetro a un valor diferente, cree una nueva directiva y asígnela.

## <a name="before-you-begin"></a>Antes de comenzar

Asegúrese de que tiene el rol adecuado para asignar directivas. Para más información, vea [Control de acceso basado en rol (RBAC) con Microsoft Intune](../fundamentals/role-based-access-control.md).

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

Las **etiquetas de ámbito** son una excelente forma de asignar y filtrar directivas a grupos específicos, como Recursos Humanos o todos los empleados de Carolina del Norte en EE. UU. En el artículo sobre [el uso de RBAC y las etiquetas de ámbito para TI distribuida](../fundamentals/scope-tags.md) tiene más información.

En los dispositivos Windows 10, puede agregar reglas **de aplicabilidad** para que el perfil solo se aplique a una versión específica del sistema operativo o a una edición específica de Windows. En el artículo sobre [reglas de aplicabilidad](device-profile-create.md#applicability-rules) se incluye más información.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de una asignación de perfil

Los perfiles de configuración de dispositivos de Intune permiten incluir y excluir grupos de una asignación de directiva.

Como procedimiento recomendado, cree y asigne directivas específicamente para sus grupos de usuarios. Además, cree y asigne directivas diferentes específicamente para los grupos de dispositivos. Para más información sobre los grupos, consulte [Agregar grupos para organizar usuarios y dispositivos](../fundamentals/groups-add.md).

Cuando asigne directivas, use la tabla siguiente al incluir y excluir grupos. Una marca de verificación significa que se admite la asignación:

![Las opciones admitidas incluyen o excluyen grupos de una asignación de perfil](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>Qué debe saber

- La exclusión tiene prioridad sobre la inclusión en los siguientes escenarios de tipos de grupos:

  - Inclusión y exclusión de grupos de usuarios
  - Inclusión y exclusión de grupos de dispositivos

  Por ejemplo, se asigna un perfil de dispositivo al grupo de usuarios **Todos los usuarios corporativos**, pero se excluye a los miembros del grupo de usuarios **Personal de administración sénior**. Puesto que ambos grupos son grupos de usuarios, **todos los usuarios corporativos** excepto el **personal de administración ejecutiva** obtienen la directiva.

- Intune no evalúa las relaciones entre grupos de usuarios y dispositivos. Si asigna directivas a grupos mixtos, es posible que los resultados no sean los deseados o esperados.

  Por ejemplo, puede asignar un perfil de dispositivo al grupo de usuarios **Todos los usuarios**, pero excluir un grupo de dispositivos **Todos los dispositivos personales**. En esta asignación de directiva de grupo mixta, **Todos los usuarios** obtienen la directiva. La exclusión no se aplica.

  Como resultado, no se recomienda asignar directivas a grupos mixtos.

## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de perfiles de dispositivo](device-profile-monitor.md) para instrucciones sobre cómo supervisar los perfiles y los dispositivos que los ejecutan.
