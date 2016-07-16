---
title: "Creación de grupos para organizar usuarios y dispositivos | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: 00ac59ffe219109dd48c47e59de9ecf588f07344


---


# Creación de grupos para organizar usuarios y dispositivos
Los grupos de Intune ofrecen una gran flexibilidad para administrar dispositivos y usuarios. Puede configurar los grupos para que se adapten a las necesidades de su organización (por ejemplo, por ubicación geográfica, departamento o características del hardware) y usarlos para realizar una amplia variedad de tareas administrativas, desde implementar directivas para un conjunto de usuarios hasta implementar aplicaciones en un conjunto de dispositivos.

Los grupos de usuarios y de dispositivos se crean en el área de trabajo GRUPOS de la consola de administración de Intune.

![Área de trabajo Grupos de la consola de administración](./media/groups.png)


> [!TIP]
> Para más información sobre el uso de grupos, consulte [Crear grupos para administrar usuarios y dispositivos en Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).


## Creación de un grupo de dispositivos
Use los grupos de dispositivos para implementar aplicaciones y actualizaciones, y configurar otras características. Por ejemplo, configure un grupo "Mis dispositivos" siguiendo estos pasos:

1.  En la [consola de administración de Intune](https://manage.microsoft.com/), seleccione **Grupos** > **Información general** > **Crear grupo**.

2.  En **Nombre del grupo**, escriba "Mis dispositivos" y, en la lista de grupos principales, seleccione **Todos los dispositivos** y luego **Siguiente**.

3.  En la página **Definir criterios de pertenencia** , seleccione **Todos los dispositivos** para indicar que el grupo incluye tanto dispositivos móviles como equipos.

4.  En la página **Definir pertenencia directa**, elija **Siguiente**. Si previamente creó un grupo que no incluía todos los dispositivos y quería agregar dispositivos específicos al nuevo grupo, puede hacerlo aquí.

5.  En la página **Resumen**, revise las acciones que se van a realizar y luego seleccione **Finalizar**.

Puede encontrar el grupo recién creado en la lista **Grupos**, en el área de trabajo **Grupos** en **Todos los dispositivos**. Aquí también puede editar o eliminar el grupo.

## Creación de un grupo de usuarios
Use grupos de usuarios para implementar las directivas de software y dispositivos. Por ejemplo, configure un grupo "Usuarios de Intune" siguiendo estos pasos:

1.  En la [consola de administración de Intune](https://manage.microsoft.com/), seleccione **Grupos** > **Información general** > **Crear grupo**.

2.  En **Nombre del grupo**, escriba "Usuarios de Intune" y, en la lista de grupos principales, seleccione **Todos los usuarios** y luego **Siguiente**.

3.  En la página **Definir criterios de pertenencia** , establezca **Iniciar pertenencia a grupos con** en **Todos los usuarios del grupo primario**.

4.  Al lado de **Excluir los miembros de estos grupos de seguridad**, elija **Examinar** y, después, seleccione **Administrador de la empresa**. Esta exclusión le permite administrar el grupo de Usuarios de Intune sin que se vea afectada la cuenta de Administrador de empresa (también conocido como administrador de inquilinos).

5.  En la página **Definir pertenencia directa**, elija **Siguiente**. Aquí no tiene que hacer nada, ya que desea que el grupo Usuarios de Intune incluya a todos los usuarios salvo el administrador de la empresa.

6.  En la página **Resumen**, revise las acciones que se van a realizar y luego seleccione **Finalizar**.

Encontrará el grupo recién creado en la lista **Grupos** del área de trabajo **Grupos** en **Todos los usuarios**. Aquí también puede editar o eliminar el grupo.



### Pasos siguientes
Enhorabuena. Acaba de completar el paso 5 de la *Guía de inicio rápido de Intune*.

>[!div class="step-by-step"]

>[&larr; **Administrar licencias de Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md) [**Crear directivas y aplicaciones** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  



<!--HONumber=Jun16_HO4-->


