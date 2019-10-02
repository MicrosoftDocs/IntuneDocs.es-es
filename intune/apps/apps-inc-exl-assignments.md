---
title: Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo usar Microsoft Intune para incluir y excluir asignaciones de aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c743b25ce2823c952b1e4b8ab764a48488c0ca5d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725106"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune

Con Intune, puede determinar quién tiene acceso a una aplicación mediante la asignación de grupos de usuarios que quiera incluir o excluir. Antes de asignar grupos a la aplicación, se debe establecer el tipo de asignación de una aplicación. El tipo de asignación hace que la aplicación esté disponible, sea obligatoria o se desinstale. 

Para establecer la disponibilidad de una aplicación, la inclusión y exclusión de asignaciones de aplicaciones en un grupo de usuarios o dispositivos se realiza mediante una combinación de asignaciones de grupo de inclusión y exclusión. Esta capacidad puede serle útil en el momento de hacer que la aplicación esté disponible mediante la inclusión de un grupo grande, para después restringir los usuarios seleccionados excluyendo un grupo más reducido. El grupo más pequeño podría ser un grupo de prueba o un grupo ejecutivo. 

Al excluir grupos de una asignación de aplicaciones, solo se deben excluir grupos de usuarios o grupos de dispositivos. No se puede excluir una combinación de grupos de usuarios y de dispositivos. 

Intune no tiene en cuenta la asociación de usuarios y dispositivos al excluir grupos. La inclusión de grupos de usuarios a la vez que se excluyen grupos de dispositivos no es probable que genere los resultados que necesita. La inclusión tiene prioridad sobre la exclusión. Por ejemplo, si una aplicación iOS tiene como destino **All Users** (Todos los usuarios) y excluye **All iPads** (Todos los iPad), el resultado neto será que cualquier usuario de iPad tendrá acceso a la aplicación. Si, en cambio, la aplicación iOS tiene como destino **All Devices** (Todos los dispositivos) y excluye **All iPads** (Todos los iPad), la implementación se realizará correctamente.  

> [!NOTE]
> Al establecer una asignación de grupo para una aplicación, el tipo **Not Applicable** (No es aplicable) queda en desuso y se reemplaza por la funcionalidad de exclusión de grupos. 
>
> Intune proporciona grupos **Todos los usuarios** y **Todos los dispositivos** ya creados en la consola. De forma práctica, los grupos llevan incorporadas optimizaciones. Es muy recomendable usar estos grupos para dirigirse a todos los usuarios y todos los dispositivos en lugar de a cualquier grupo "todos los usuarios" o "todos los dispositivos" que haya podido crear usted mismo.  
>
> Android Enterprise admite grupos incluidos y excluidos. Puede aprovechar los grupos integrados **Todos los usuarios** y **Todos los dispositivos** para la asignación de aplicaciones de Android Enterprise. 


## <a name="include-and-exclude-groups-when-assigning-apps"></a>Inclusión y exclusión de grupos al asignar aplicaciones 
Para asignar una aplicación a grupos mediante la asignación de inclusión y exclusión, siga estos pasos:
1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En el panel **Aplicaciones cliente**, seleccione **Aplicaciones**. Se muestra la lista de aplicaciones agregadas.
5. Seleccione la aplicación que quiera asignar. Un panel muestra información sobre la aplicación. 
6. En la sección **Administrar** del menú, seleccione **Asignaciones**. 

    ![Inclusión de las asignaciones de aplicaciones al asignar aplicaciones](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)
7. Seleccione **Agregar grupo** para agregar los grupos de usuarios que están asignados a la aplicación. 
8. Seleccione un **tipo de asignación** entre los disponibles en el panel **Agregar grupo**.
9. Seleccione **Available with or without enrollment** (Disponible con o sin inscripción) como tipo de asignación.

    ![Asignaciones de aplicaciones de Intune: agregar un grupo](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
10. Seleccione **Grupos incluidos** para seleccionar el grupo de usuarios para los que estará disponible esta aplicación.

    > [!NOTE]
    > Al agregar un grupo, si ningún otro grupo se ha incluido para un tipo de asignación específica, la aplicación se preselecciona y no se puede modificar para otros tipos de asignación de inclusión. El grupo que se ha usado no se puede utilizar como un grupo incluido.

11. Seleccione **Sí** para que esta aplicación esté disponible para todos los usuarios.

    ![Asignaciones de aplicaciones de Intune: incluir grupos](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
12. Haga clic en **Aceptar** para establecer el grupo que quiere incluir.
13. Seleccione **Grupos excluidos** para seleccionar los grupos de usuarios para los que no estará disponible esta aplicación. 
14. Seleccione los grupos para excluir. A continuación, esta aplicación deja de estar disponible para esos grupos.

    ![Asignaciones de la aplicaciones de Intune: excluir grupos](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
15. Haga clic en **Seleccionar** para completar la selección de grupos.
16. En el panel **Agregar grupo**, seleccione **Aceptar**. Aparece la lista de **asignaciones** de aplicaciones.
17. Haga clic en **Guardar** para activar las asignaciones de grupo para la aplicación.

Cuando se realizan asignaciones de grupos, los grupos que se han asignado ya no están disponibles para modificarse. Si quiere seleccionar un grupo que actualmente no está disponible, quite primero la aplicación de lista asignada de aplicaciones. 

Para editar las asignaciones, en la lista de **asignaciones** de aplicaciones, seleccione la fila que contiene la asignación específica que quiere cambiar. Otra forma de quitar una asignación es seleccionar los puntos suspensivos ( **…** ) al final de una fila y, luego, seleccionar **Quitar**. Para cambiar la vista de la lista **Asignaciones**, agrupe por **Tipo de asignación** o por **Incluidos o excluidos**.

![Asignaciones de aplicaciones de Intune: completar](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>Pasos siguientes

- Para más información sobre la inclusión y exclusión de asignaciones de aplicaciones para grupos, consulte el [blog de Microsoft Intune](https://aka.ms/new_app_assignment_process).
- Consulte [Supervisión de información y asignaciones de aplicaciones](apps-monitor.md).
