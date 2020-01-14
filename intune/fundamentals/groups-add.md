---
title: Agregar grupos para organizar usuarios y dispositivos
titleSuffix: Microsoft Intune
description: Agregue grupos para organizar usuarios y dispositivos por geografía, departamento o especificaciones de hardware.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe37ac412d01d3032685a0e66827d20e13b0db64
ms.sourcegitcommit: 42183c87b137710b8529049f8710d47127e99900
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75303073"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Agregar grupos para organizar usuarios y dispositivos

Intune usa grupos de Azure Active Directory (AD) para administrar dispositivos y usuarios. Como administrador de Intune, puede configurar los grupos de modo que satisfagan sus necesidades organizativas. Cree grupos para organizar a los usuarios o dispositivos por ubicación geográfica, departamento o características de hardware. Use los grupos para administrar tareas a escala. Por ejemplo, puede establecer directivas para muchos usuarios o implementar aplicaciones para un conjunto de dispositivos.

Puede agregar los siguientes tipos de grupos:

- **Grupos asignados**: agregue manualmente usuarios o dispositivos a un grupo estático. 
- **Grupos dinámicos** (requiere Azure AD Premium): agregue automáticamente usuarios o dispositivos a grupos de usuarios o grupos de dispositivos en función de una expresión que cree.

  Por ejemplo, cuando se agrega un usuario con el título de administrador, el usuario se agrega automáticamente a un grupo de usuarios **Todos los administradores**. O bien, cuando un dispositivo tiene el tipo de sistema operativo para dispositivos iOS, el dispositivo se agrega automáticamente a un grupo de dispositivos **Todos los dispositivos iOS**.

## <a name="add-a-new-group"></a>Agregar un grupo nuevo

Use los siguientes pasos para crear un grupo.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Grupos** > **Nuevo grupo**:

   ![Captura de pantalla de Azure Portal con la opción Nuevo grupo seleccionada](./media/groups-add/groups-add-new.png)

3. En **Tipo de grupo**, elija una de las opciones siguientes:

    - **Seguridad**: los grupos de seguridad definen quién puede acceder a los recursos, y se recomiendan para los grupos de Intune. Por ejemplo, puede crear grupos para usuarios, como **Todos los empleados de Charlotte** o **Trabajadores remotos**. O bien, puede crear grupos para dispositivos, como **Todos los dispositivos iOS** o **Todos los dispositivos de alumnos de Windows 10**.

        > [!TIP]
        > Los usuarios y los grupos creados también pueden verse en el [Centro de administración de Microsoft 365](https://admin.microsoft.com), el centro de administración de Azure Active Directory y [Microsoft Intune en Azure Portal](https://go.microsoft.com/fwlink/?linkid=2090973). En el inquilino de la organización, puede crear y administrar grupos en todas estas áreas.
        >
        > Si su rol principal es la administración de dispositivos, se recomienda usar el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

    - **Office 365**: estos grupos están diseñados para controlar el acceso a los recursos de Office 365 y compartirlos. Por ejemplo, puede crear un grupo de Office 365 para compartir una bandeja de entrada o un calendario de Outlook. Para más información, consulte [Más información sobre los grupos de Office 365](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

4. Escriba los valores para **Nombre del grupo** y **Descripción del grupo** del nuevo grupo. Sea concreto e incluya información que permita a que otros usuarios saber para qué sirve el grupo.

    Por ejemplo, escriba **Todos los dispositivos de los alumnos de Windows 10** como nombre del grupo y **Todos los dispositivos de Windows 10 que usan los alumnos de secundaria de Contoso de los niveles 9-12** como descripción del grupo.

5. Especifique el valor de **Tipo de pertenencia**. Las opciones son:

    - **Asignados**: los administradores asignan manualmente usuarios o dispositivos a este grupo y quitan manualmente usuarios o dispositivos.
    - **Usuario dinámico**: los administradores crean reglas de pertenencia para agregar y quitar miembros automáticamente.
    - **Dispositivo dinámico**: los administradores crean reglas de grupo dinámicas para agregar y quitar dispositivos automáticamente.

        ![Captura de pantalla de las propiedades del grupo de Intune](./media/groups-add/groups-add-properties.png)

    Para más información sobre estos tipos de pertenencia y la creación de expresiones dinámicas, consulte:

    - [Creación de un grupo básico e incorporación de miembros con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Reglas de pertenencia dinámica a grupos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > En este centro de administración, al crear usuarios o grupos, es posible que no vea la personalización de marca de **Azure Active Directory**. Sin embargo, eso es lo que está usando.

6. Elija **Crear** para agregar el nuevo grupo. El grupo se muestra en la lista.

> [!TIP]
> Tenga en cuenta algunos de los otros grupos de dispositivos y usuarios dinámicos que puede crear, por ejemplo:
>
> - Todos los estudiantes de secundaria de Contoso
> - Todos los dispositivos Android Enterprise
> - Todos los dispositivos iOS 11 y anteriores
> - Marketing
> - Recursos humanos
> - Todos los empleados de Charlotte
> - Todos los empleados de WA

## <a name="groups-and-policies"></a>Grupos y directivas

El acceso a los recursos de su organización está controlado por los usuarios y grupos que se creen.

Al crear grupos, tenga en cuenta cómo se aplicarán las [directivas de cumplimiento](../protect/device-compliance-get-started.md) y los [perfiles de configuración](../configuration/device-profiles.md). Por ejemplo, puede tener:

- Directivas que son específicas de un sistema operativo de dispositivo.
- Directivas que son específicas de los distintos roles de su organización.
- Directivas que son específicas de las unidades organizativas definidas en Active Directory.

Para crear los requisitos básicos de cumplimiento de la organización, puede crear una directiva predeterminada que se aplique a todos los grupos y dispositivos. Luego, puede crear directivas más específicas para las categorías más amplias de usuarios y dispositivos. Por ejemplo, puede crear directivas de correo electrónico para cada uno de los sistemas operativos de dispositivos.

Para instrucciones y recomendaciones sobre los perfiles de configuración, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](../configuration/device-profile-assign.md#user-groups-vs-device-groups) y [Recomendaciones de perfiles](../configuration/device-profile-create.md#recommendations).

## <a name="see-also"></a>Vea también

- [Control de acceso basado en rol (RBAC) con Microsoft Intune](role-based-access-control.md)
- [Administración del acceso a recursos y aplicaciones con grupos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
