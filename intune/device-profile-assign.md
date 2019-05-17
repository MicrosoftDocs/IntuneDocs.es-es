---
title: Asignación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Use Azure Portal para asignar perfiles de dispositivo y directivas a los usuarios y a los dispositivos. Aprenda a excluir grupos de una asignación de perfil en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c950efdd95fd8d856ec677385712a022dead870
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570512"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Asignación de perfiles de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Puede crear un perfil e incluir toda la configuración que escribió. El paso siguiente es implementar o "asignar el perfil" a los grupos de dispositivos o usuarios de Azure Active Directory (Azure AD). Cuando se asigna, los usuarios y dispositivos reciben su perfil y se aplica la configuración que escribió.

En este artículo se muestra cómo asignar un perfil y se incluye información sobre el uso de las etiquetas de ámbito en los perfiles.

## <a name="assign-a-device-profile"></a>Asignar un perfil de dispositivo

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles**. Se muestran todos los perfiles.
3. Seleccione el perfil que quiere asignar > **Asignaciones**.
4. Elija **Incluir** grupos o **Excluir** grupos y, luego, seleccione los grupos. Al seleccionar los grupos, se elige un grupo de Azure AD. Para seleccionar varios grupos, mantenga presionada la tecla **Ctrl** y seleccione los grupos.

    ![Captura de pantalla de las opciones para incluir o excluir grupos de una asignación de perfil](./media/group-include-exclude.png)

5. Guarde los cambios mediante **Guardar**.

### <a name="evaluate-how-many-users-are-targeted"></a>Evaluación de cuántos usuarios se rigen por una directiva

Cuando asigna el perfil, también puede **evaluar** cuántos usuarios se verán afectados. Esta característica calcula los usuarios, no los dispositivos.

1. En Intune, seleccione **Configuración del dispositivo** > **Perfiles**.
2. Seleccione un perfil > **Asignaciones** > **Evaluar**. Un mensaje muestra a cuántos usuarios se aplica este perfil.

Si el botón **Evaluar** está atenuado, asegúrese de que el perfil se asignó a uno o más grupos.


## <a name="use-scope-tags"></a>Uso de etiquetas de ámbito

Cuando crea o actualiza un perfil, también puede agregar etiquetas de ámbito al perfil.

Las **etiquetas de ámbito** son una excelente forma de asignar y filtrar directivas a grupos específicos, como Recursos Humanos o todos los empleados de Carolina del Norte en EE. UU. En el artículo sobre [el uso de RBAC y las etiquetas de ámbito para TI distribuida](scope-tags.md) tiene más información.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de una asignación de perfil

Los perfiles de configuración de dispositivo de Intune permiten excluir grupos de una asignación de directiva. Por ejemplo, puede asignar un perfil de dispositivo al grupo **Todos los usuarios corporativos**, pero excluir a todos los miembros del grupo **Personal de administración sénior**.

Cuando excluye grupos, solo usuarios o solo grupos de dispositivos (no una combinación de grupos) de una asignación, Intune no observa las relaciones de usuario a dispositivo. Es posible que la inclusión de grupos de usuarios a la vez que se excluyen grupos de dispositivos no genere los resultados que espera. Si se usan grupos mixtos o hay otros conflictos, la inclusión tiene prioridad sobre la exclusión.

Por ejemplo, quiere asignar un perfil de dispositivo a todos los dispositivos de la organización, excepto los de pantalla completa. Incluye el grupo **Todos los usuarios**, pero excluye al grupo **Todos los dispositivos**. En este caso, todos los usuarios y sus dispositivos obtienen la directiva, incluso si el dispositivo del usuario se encuentre en el grupo **Todos los dispositivos**.

La exclusión solo considera a los miembros directos del grupo. No incluye los dispositivos asociados con un usuario. En cambio, los dispositivos que no tienen un usuario no obtienen la directiva. Esto ocurre porque esos dispositivos no tienen ninguna relación con el grupo **Todos los usuarios**.

Si incluye **Todos los dispositivos** y excluye **Todos los usuarios**, todos los dispositivos reciben la directiva. En este escenario, la intención es excluir aquellos dispositivos que tienen un usuario asociado de esta directiva. En cambio, no se excluyen los dispositivos porque la exclusión solo compara miembros de grupo directos.

## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de perfiles de dispositivo](device-profile-monitor.md) para instrucciones sobre cómo supervisar los perfiles y los dispositivos que los ejecutan.