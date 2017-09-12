---
title: "Cómo asignar perfiles de dispositivo con Intune"
titlesuffix: Azure portal
description: Cuando haya creado un perfil de dispositivo de Intune, use este tema para aprender a asignarlo a los dispositivos.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36b967ac740cc2f39d631c17556f73abb9f2f785
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-assign-microsoft-intune-device-profiles"></a>Asignación de perfiles de dispositivo de Microsoft Intune

## <a name="assign-a-device-profile"></a>Asignar un perfil de dispositivo

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
1. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
2. En la hoja de lista de perfiles, elija el perfil que quiere administrar y, luego, en la hoja <*nombre del perfil*> **Informes**, elija **Administrar** > **Asignaciones**.
3. En la siguiente hoja, elija **Incluir** (para incluir grupos) o **Excluir** (para excluir grupos) y luego **Seleccionar grupos**.
![Incluir y excluir grupos de una asignación de perfil.](./media/group-include-exclude.png)
4. En la hoja **Seleccionar grupos**, elija los grupos de Azure AD que quiere incluir en la asignación o excluir de ella. Para seleccionar varios, grupos, mantenga presionada la tecla **CTRL**.
4. Cuando haya terminado, en la hoja **Seleccionar grupos**, elija **Seleccionar**.



## <a name="how-to-exclude-groups-from-a-device-profile-assignment"></a>Cómo excluir grupos de una asignación de perfil de dispositivo

Los perfiles de configuración de dispositivo de Intune permiten excluir grupos de una asignación de directiva. Por ejemplo, puede asignar un perfil de dispositivo al grupo **Todos los usuarios corporativos**, pero excluir a todos los miembros del grupo **Personal de administración sénior**.

Al excluir grupos de una asignación, excluya solo grupos de usuarios o dispositivos, no una combinación de grupos. Intune no tiene en cuenta ninguna asociación de usuario a dispositivo al excluir grupos. La inclusión de grupos de usuarios a la vez que se excluyen grupos de dispositivos no es probable que genere los resultados que necesita. Si se usan grupos mixtos o hay otros conflictos, la inclusión tiene prioridad sobre la exclusión.

Por ejemplo, quiere asignar un perfil de dispositivo a todos los dispositivos de la organización, excepto los de pantalla completa. Incluye el grupo **Todos los usuarios**, pero excluye al grupo **Todos los dispositivos**.

En este caso, todos los usuarios y sus dispositivos obtienen la directiva, aunque el dispositivo del usuario forme parte del grupo **Todos los dispositivos**. 

La exclusión solo evalúa a los miembros directos de los grupos y no incluye a los dispositivos que están asociados a un usuario. Pero los dispositivos que no tienen un usuario no obtienen la directiva porque no tienen ninguna asociación al grupo **Todos los usuarios**. 

Si incluye **Todos los dispositivos** pero excluye **Todos los usuarios**, todos los dispositivos reciben la directiva. En este caso, la intención es excluir aquellos dispositivos que tienen un usuario asociado desde esta directiva. Pero no se consigue porque la característica de exclusión solo compara miembros de grupo directos. 

>[!Tip]
>Las exclusiones no están disponibles actualmente para las directivas de cumplimiento ni la asignación de aplicaciones. Para excluir miembros de una asignación, puede usar las opciones de asignación Disponible y No aplicable. Por ejemplo, asigne una aplicación a **Todos los usuarios corporativos** con la opción **Disponible** y a **Personal de administración sénior** con la opción **No aplicable**. La aplicación se asigna a todos los usuarios *excepto* a los del grupo **Personal de administración sénior**. Si asigna la aplicación a **Todos los usuarios corporativos** con la opción **Obligatorio**, los usuarios del grupo **Personal de administración sénior** no se excluyen.
 
    
## <a name="next-steps"></a>Pasos siguientes
Consulte [Supervisión de perfiles de dispositivo](device-profile-monitor.md) para obtener información que le ayude a supervisar las asignaciones de perfil de dispositivo.
