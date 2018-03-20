---
title: "Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune"
titlesuffix: 
description: "Obtenga información sobre cómo usar Microsoft Intune para incluir y excluir asignaciones de aplicaciones."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dbe8669dc2bf448e0738147758d90ba6d2d69b06
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune

Con Intune, puede determinar quién tiene acceso a una aplicación mediante la asignación de los grupos que quiera incluir o excluir. Sin embargo, antes de asignar grupos a la aplicación, se debe establecer el tipo de asignación de una aplicación. El tipo de asignación hace que la aplicación esté disponible, sea obligatoria o se desinstale. 

Al centrarse en la disponibilidad de una aplicación, la inclusión y exclusión de asignaciones de aplicaciones en un grupo de usuarios o dispositivos se realiza mediante una combinación de asignaciones de grupo de inclusión y exclusión. Esta capacidad puede serle útil en el momento de hacer que la aplicación esté disponible mediante la inclusión de un grupo grande, para después restringir los usuarios seleccionados excluyendo un grupo más reducido. El grupo más pequeño podría ser un grupo de prueba o un grupo ejecutivo. 

Al excluir grupos de una asignación de aplicaciones, solo se deben excluir grupos de usuarios o de dispositivos, no una combinación de grupos. Al excluir grupos, Intune no tiene en cuenta la asociación usuarios y dispositivos. Es probable que si incluye grupos de usuarios y excluye grupos de dispositivos no obtenga los resultados que necesita, ya que la inclusión tiene prioridad sobre la exclusión. Por ejemplo, si orienta una aplicación de iOS a **Todos los usuarios** y excluye **Todos los iPad**, el resultado neto será que cualquier usuario de iPad tendrá acceso a la aplicación. Si, en cambio, orienta la aplicación de iOS a **Todos los dispositivos** y excluye **Todos los iPad**, la implementación se realizará correctamente.  

>[!NOTE]
>Al establecer una asignación de grupo para una aplicación, el tipo **No es aplicable** queda en desuso y se reemplazan por la funcionalidad de grupo de exclusión. 
>
>Intune ofrece los grupos creados previamente **Todos los usuarios** y **Todos los dispositivos** en la consola con las optimizaciones integradas para su comodidad. Es muy recomendable utilizar estos grupos para segmentar todos los usuarios y todos los dispositivos en lugar de usar cualquier grupo "Todos los usuarios" o "Todos los dispositivos" que haya podido crear.  

## <a name="including-and-excluding-groups-when-assigning-apps"></a>Incluir y excluir grupos al asignar aplicaciones 
Para asignar una aplicación a grupos mediante la asignación de inclusión y exclusión, siga estos pasos:
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Seleccione **Aplicaciones móviles** en la hoja Microsoft Intune.
4. Seleccione **Aplicaciones** en la hoja **Aplicaciones móviles**. Se muestra la lista de aplicaciones agregadas.
5. Seleccione la aplicación que quiera asignar. Se muestra un panel relacionado con la aplicación. 
6. Seleccione **Asignaciones** en la sección **Administrar**. 

    ![Asignaciones de aplicaciones de Intune](./media/apps-inc-exl-01.png)
7. Seleccione **Agregar grupo** para agregar los grupos de usuarios que están asignados a la aplicación. 
8. Seleccione un **tipo de asignación** entre los disponibles en el panel **Agregar grupo**.
9. Seleccione **Disponible con o sin inscripción** como tipo de asignación.

    ![Asignaciones de aplicaciones de Intune: agregar un grupo](./media/apps-inc-exl-02.png)
10. Seleccione **Grupos incluidos** para seleccionar el grupo de usuarios para los que quiera que esta aplicación esté disponible.

    >[!NOTE]
    >Al agregar un grupo, si ya se ha incluido otro a un tipo de asignación determinado, este se preseleccionará y no se podrá cambiar por otros tipos de asignación de inclusión. Por lo tanto, ese grupo que se ha usado, no se puede utilizar como un grupo incluido.

11. Seleccione **Sí** para que esta aplicación esté disponible para todos los usuarios.

    ![Asignaciones de aplicaciones de Intune: incluir grupos](./media/apps-inc-exl-03.png)
12. Haga clic en **Aceptar** para establecer el grupo que quiera incluir.
13. Seleccione **Grupos excluidos** para seleccionar los grupos de usuarios para los que quiera que esta aplicación no esté disponible. 
14. Seleccione los grupos que quiere excluir, para los que esta aplicación dejará de estar disponible.

    ![Asignaciones de la aplicaciones de Intune: excluir grupos](./media/apps-inc-exl-04.png)
15. Haga clic en **Seleccionar** para completar la selección de grupos.
16. Haga clic en **Aceptar** en la hoja **Agregar grupo**. Se muestra la aplicación **Asignaciones**.
17. Haga clic en **Guardar** para activar las asignaciones de grupo para la aplicación.

Al realizar asignaciones de grupos, los grupos que ya se han asignado o seleccionado se deshabilitan. Si quiere seleccionar un grupo que actualmente está deshabilitado, quítelo de aplicaciones asignadas. Puede modificar asignaciones desde la lista **Asignaciones** de la aplicación. Para ello, seleccione la fila que contenga la asignación específica que quiera cambiar. Además, puede quitar una asignación haciendo clic en el botón de puntos suspensivos (…) situado en el extremo de una fila y seleccionando **Eliminar**. Además, puede cambiar la vista de la lista **Asignaciones**. Para ello, elija agrupar por **Tipo de asignación** o por **Incluidos o excluidos**.

![Asignaciones de aplicaciones de Intune: completar](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>Pasos siguientes

- Para obtener más información sobre la inclusión y exclusión de asignaciones de grupos para aplicaciones, consulte el [Blog de Microsoft Intune](https://aka.ms/new_app_assignment_process).
- [Supervisión de la información de la aplicación y las asignaciones](apps-monitor.md)