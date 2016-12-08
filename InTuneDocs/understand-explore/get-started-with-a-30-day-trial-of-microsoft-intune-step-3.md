---
title: "Creación de grupos para organizar usuarios y dispositivos | Microsoft Intune"
description: "Cómo crear grupos de dispositivos y grupos de usuarios al registrarse para obtener una evaluación gratuita de 30 días de Microsoft Intune."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7162cad3-5c14-43f3-a760-833ffd7786b1
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: ab451a1213923ecd27dfc0b8ca353041e70435ed


---

# <a name="create-groups-to-organize-evaluation-subscription-users-and-devices"></a>Crear grupos para organizar los dispositivos y usuarios de la suscripción de evaluación
Los grupos de Intune ofrecen una gran flexibilidad para administrar dispositivos y usuarios. Puede configurar los grupos para que se adapten a las necesidades de su organización (por ejemplo, por ubicación geográfica, departamento o características de hardware) y usarlos para realizar diversas tareas administrativas a escala, desde la configuración de directivas para un conjunto de usuarios hasta la implementación de aplicaciones en un conjunto de dispositivos.

## <a name="create-a-device-group"></a>Creación de un grupo de dispositivos
Use los grupos de dispositivos para implementar software y actualizaciones y para establecer las directivas de configuración del Agente de Microsoft Intune y del Firewall de Windows. Por ejemplo, configure un grupo de "Mis dispositivos de prueba" siguiendo estos pasos:

1.  En la [consola de administración de Intune](https://manage.microsoft.com/), elija **Grupos** &gt; **Información general** &gt; **Crear grupo**.

2.  En el **Nombre de grupo**, escriba "Mis dispositivos de prueba" y, en la lista de grupos principales, seleccione **Todos los dispositivos** y, después, elija **Siguiente**.

3.  En la página **Definir criterios de pertenencia** , seleccione **Todos los dispositivos** para indicar que el grupo incluye tanto dispositivos móviles como equipos.

4.  En la página **Definir pertenencia directa**, elija **Siguiente**. Si previamente creó un grupo que no incluye todos los dispositivos y desea agregar determinados dispositivos al nuevo grupo, puede hacerlo aquí.

5.  En la página **Resumen**, revise las acciones que se van a realizar y, después, elija **Finalizar**.

Puede encontrar el grupo recién creado en la lista **Grupos** , del área de trabajo **Grupos** en **Todos los dispositivos**. Aquí también puede editar o eliminar el grupo.

## <a name="create-a-user-group"></a>Creación de un grupo de usuarios
Use grupos de usuarios para implementar las directivas de software y dispositivos. Por ejemplo, configure un grupo de "Mis usuarios de prueba" siguiendo estos pasos:

1.  En la [consola de administración de Intune](https://manage.microsoft.com/), elija **Grupos** &gt; **Información general** &gt; **Crear grupo**.

2.  En el **Nombre de grupo**, escriba "Mis usuarios de prueba" y, en la lista de grupos principales, seleccione **Todos los usuarios** y, después, haga clic en **Siguiente**.

3.  En la página **Definir criterios de pertenencia** , establezca **Iniciar pertenencia a grupos con** en **Todos los usuarios del grupo primario**.

4.  Al lado de **Excluir los miembros de estos grupos de seguridad**, elija **Examinar** y, después, seleccione **Administrador de la empresa**. Esta exclusión le permite administrar el grupo Mis usuarios de prueba sin que afecte a la cuenta del Administrador de la compañía (también conocido como Administrador de inquilinos).

5.  En la página **Definir pertenencia directa**, elija **Siguiente**. Aquí no tiene que hacer nada, ya que desea que el grupo Mi usuarios de prueba incluya a todos los usuarios, salvo el Administrador de empresa.

6.  En la página **Resumen**, revise las acciones que se van a realizar y, después, elija **Finalizar**.

Puede encontrar el grupo recién creado en la lista **Grupos** del área de trabajo **Grupos** en **Todos los usuarios**. Aquí también puede editar o eliminar el grupo.

Para obtener más información sobre el uso de los grupos, vea [Usar grupos para administrar usuarios y dispositivos en Microsoft Intune](/Intune/Deploy-Use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## <a name="next-steps"></a>Pasos siguientes
[Crear las directivas](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)  



<!--HONumber=Nov16_HO5-->

