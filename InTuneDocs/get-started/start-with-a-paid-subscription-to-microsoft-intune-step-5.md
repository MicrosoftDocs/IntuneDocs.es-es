---
title: "Creación de grupos para organizar usuarios y dispositivos | Microsoft Docs"
description: "Crear usuarios y grupos para la suscripción de Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: 446156265047994f0a15890d7699991d032c0bd5


---


# <a name="create-groups-to-organize-users-and-devices"></a>Creación de grupos para organizar usuarios y dispositivos

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Los grupos de Intune ofrecen una gran flexibilidad para administrar dispositivos y usuarios. Puede configurar los grupos para que se adapten a las necesidades de su organización (por ejemplo, por ubicación geográfica, departamento o características del hardware) y usarlos para realizar una amplia variedad de tareas administrativas, desde implementar directivas para un conjunto de usuarios hasta implementar aplicaciones en un conjunto de dispositivos.

## <a name="group-management-moving-to-azure-ad"></a>Movimiento de la administración de grupos a Azure AD

**A partir de noviembre de 2016**, se usarán nuevas cuentas para administrar grupos de usuarios y dispositivos en el portal de Azure Acitve Directory (AD). En diciembre de 2016, el equipo del producto de Intune comenzará la migración de los clientes existentes a la nueva experiencia de administración de grupos basada en Azure AD. Los grupos de dispositivos y usuarios se migrarán a los grupos de seguridad de Azure AD. Las migraciones no se iniciarán hasta que se pueda minimizar cualquier impacto en su trabajo diario y se espere que no tengan ningún efecto en sus usuarios. También se le avisará antes de migrar su cuenta.


>[!IMPORTANT]
>
>Si abre el área de trabajo Grupos en el portal de Intune y ve que los **grupos de usuarios de Intune se administran ahora como grupos de Azure Active Directory** con un vínculo al portal de Azure Active Directory, significa que ya está usando el *nuevo* enfoque de grupos de seguridad de Azure AD para administrar grupos en Intune. Para aprender a crear grupos, consulte [Administración de grupos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
>
>Si no ve el vínculo al portal de Azure AD, significa que aún utiliza el portal de Intune para la administración de grupos.

## <a name="group-management-in-the-intune-portal"></a>Administración de grupos en el portal de Intune

Los grupos de usuarios y de dispositivos se crean en el área de trabajo GRUPOS de la consola de administración de Intune.

![Área de trabajo Grupos de la consola de administración](./media/groups.png)


> [!TIP]
> Para más información sobre el uso de grupos, consulte [Crear grupos para administrar usuarios y dispositivos en Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).


## <a name="create-a-device-group"></a>Creación de un grupo de dispositivos
Use los grupos de dispositivos para implementar aplicaciones y actualizaciones, y configurar otras características. Por ejemplo, configure un grupo "Mis dispositivos" siguiendo estos pasos:

1.  En la [consola de administración de Intune](https://manage.microsoft.com/), seleccione **Grupos** > **Información general** > **Crear grupo**.

2.  En **Nombre del grupo**, escriba "Mis dispositivos" y, en la lista de grupos principales, seleccione **Todos los dispositivos** y luego **Siguiente**.

3.  En la página **Definir criterios de pertenencia** , seleccione **Todos los dispositivos** para indicar que el grupo incluye tanto dispositivos móviles como equipos.

4.  En la página **Definir pertenencia directa**, elija **Siguiente**. Si previamente creó un grupo que no incluía todos los dispositivos y quería agregar dispositivos específicos al nuevo grupo, puede hacerlo aquí.

5.  En la página **Resumen**, revise las acciones que se van a realizar y luego seleccione **Finalizar**.

Puede encontrar el grupo recién creado en la lista **Grupos**, en el área de trabajo **Grupos** en **Todos los dispositivos**. Aquí también puede editar o eliminar el grupo.

## <a name="create-a-user-group"></a>Creación de un grupo de usuarios
Use grupos de usuarios para implementar las directivas de software y dispositivos. Por ejemplo, configure un grupo "Usuarios de Intune" siguiendo estos pasos:

1.  En la [consola de administración de Intune](https://manage.microsoft.com/), seleccione **Grupos** > **Información general** > **Crear grupo**.

2.  En **Nombre del grupo**, escriba "Usuarios de Intune" y, en la lista de grupos principales, seleccione **Todos los usuarios** y luego **Siguiente**.

3.  En la página **Definir criterios de pertenencia** , establezca **Iniciar pertenencia a grupos con** en **Todos los usuarios del grupo primario**.

4.  Al lado de **Excluir los miembros de estos grupos de seguridad**, elija **Examinar** y, después, seleccione **Administrador de la empresa**. Esta exclusión le permite administrar el grupo de Usuarios de Intune sin que se vea afectada la cuenta de Administrador de empresa (también conocido como administrador de inquilinos).

5.  En la página **Definir pertenencia directa**, elija **Siguiente**. Aquí no tiene que hacer nada, ya que desea que el grupo Usuarios de Intune incluya a todos los usuarios salvo el administrador de la empresa.

6.  En la página **Resumen**, revise las acciones que se van a realizar y, después, elija **Finalizar**.

Encontrará el grupo recién creado en la lista **Grupos** del área de trabajo **Grupos** en **Todos los usuarios**. Aquí también puede editar o eliminar el grupo.

>[!div class="step-by-step"]

>[&larr; **Administrar licencias de Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md) [**Crear directivas y aplicaciones** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  



<!--HONumber=Jan17_HO2-->


