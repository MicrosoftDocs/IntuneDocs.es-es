---
title: Asignación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Use Azure Portal para asignar perfiles de dispositivo y directivas a los usuarios y a los dispositivos. Aprenda a excluir grupos de una asignación de perfil en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 344ffdfefd8b354c9d2ab31f2d08c2a25456f970
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724118"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Asignación de perfiles de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede crear un perfil e incluir toda la configuración que escribió. El paso siguiente es implementar o "asignar el perfil" a los grupos de dispositivos o usuarios de Azure Active Directory (Azure AD). Cuando se asigna, los usuarios y dispositivos reciben su perfil y se aplica la configuración que escribió.

En este artículo se muestra cómo asignar un perfil y se incluye información sobre el uso de las etiquetas de ámbito en los perfiles.

## <a name="assign-a-device-profile"></a>Asignar un perfil de dispositivo

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles**. Se muestran todos los perfiles.
3. Seleccione el perfil que quiere asignar > **Asignaciones**.
4. Elija **Incluir** grupos o **Excluir** grupos y, luego, seleccione los grupos. Al seleccionar los grupos, se elige un grupo de Azure AD. Para seleccionar varios grupos, mantenga presionada la tecla **Ctrl** y seleccione los grupos.

    ![Captura de pantalla de las opciones para incluir o excluir grupos de una asignación de perfil](./media/device-profile-assign/group-include-exclude.png)

5. Guarde los cambios mediante **Guardar**.

### <a name="evaluate-how-many-users-are-targeted"></a>Evaluación de cuántos usuarios se rigen por una directiva

Cuando asigna el perfil, también puede **evaluar** cuántos usuarios se verán afectados. Esta característica calcula los usuarios, no los dispositivos.

1. En Intune, seleccione **Configuración del dispositivo** > **Perfiles**.
2. Seleccione un perfil > **Asignaciones** > **Evaluar**. Un mensaje muestra a cuántos usuarios se aplica este perfil.

Si el botón **Evaluar** está atenuado, asegúrese de que el perfil se asignó a uno o más grupos.

## <a name="use-scope-tags-or-applicability-rules"></a>Uso de etiquetas de ámbito o reglas de aplicabilidad

Cuando crea o actualiza un perfil, puede agregar también etiquetas de ámbito al perfil.

Las **etiquetas de ámbito** son una excelente forma de asignar y filtrar directivas a grupos específicos, como Recursos Humanos o todos los empleados de Carolina del Norte en EE. UU. En el artículo sobre [el uso de RBAC y las etiquetas de ámbito para TI distribuida](../fundamentals/scope-tags.md) tiene más información.

En los dispositivos Windows 10, puede agregar reglas **de aplicabilidad** para que el perfil solo se aplique a una versión específica del sistema operativo o a una edición específica de Windows. En el artículo sobre [reglas de aplicabilidad](device-profile-create.md#applicability-rules) se incluye más información.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de una asignación de perfil

Los perfiles de configuración de dispositivo de Intune permiten excluir grupos de una asignación de directiva.

Intune no contempla las relaciones entre grupos de usuarios y dispositivos. Es posible que la inclusión de grupos de usuarios a la vez que se excluyen grupos de dispositivos no genere los resultados que espera. En los escenarios de grupo de usuarios a grupo de usuarios y de grupo de dispositivos a grupo de dispositivos, la exclusión tiene prioridad sobre la inclusión.

Por ejemplo, se asigna un perfil de dispositivo al grupo de usuarios **Todos los usuarios corporativos**, pero se excluye a los miembros del grupo de usuarios **Personal de administración sénior**. Puesto que ambos grupos son grupos de usuarios, todos los miembros del **Personal de administración sénior** se excluyen de la directiva, aunque sean miembros del grupo de inclusión **Todos los usuarios corporativos**.

La inclusión tiene prioridad sobre la exclusión cuando se utilizan grupos mixtos, como grupo de usuarios a grupo de dispositivos o grupo de dispositivos a grupo de usuarios.

Por ejemplo, quiere asignar un perfil de dispositivo a todos los dispositivos de la organización, excepto los de pantalla completa. Incluye el grupo **Todos los usuarios**, pero excluye al grupo **Todos los dispositivos**. En este caso, todos los usuarios y sus dispositivos obtienen la directiva, incluso si el dispositivo del usuario se encuentre en el grupo **Todos los dispositivos**.

La exclusión solo considera a los miembros directos del grupo. No incluye los dispositivos asociados con un usuario. En cambio, los dispositivos que no tienen un usuario no obtienen la directiva. Este comportamiento se produce porque los dispositivos sin usuarios no tienen ninguna relación con el grupo **Todos los usuarios**.

Si incluye **Todos los dispositivos** y excluye **Todos los usuarios**, todos los dispositivos reciben la directiva. En este escenario, la intención es excluir aquellos dispositivos que tienen un usuario asociado de esta directiva. En cambio, no se excluyen los dispositivos porque la exclusión solo compara miembros de grupo directos.

## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de perfiles de dispositivo](device-profile-monitor.md) para instrucciones sobre cómo supervisar los perfiles y los dispositivos que los ejecutan.
