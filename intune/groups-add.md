---
title: Agregar grupos para organizar usuarios y dispositivos
titleSuffix: Microsoft Intune
description: Agregue grupos para organizar usuarios y dispositivos por geografía, departamento o especificaciones de hardware.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 60f2368fc8c6d4f8e2713a8386ccdd7e5958ac6b
ms.sourcegitcommit: 063177c6c365fef3642edd7c455790958469aad9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412616"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Agregar grupos para organizar usuarios y dispositivos
Intune usa grupos de Azure Active Directory (AD) para administrar dispositivos y usuarios. Como administrador de Intune, puede configurar los grupos de modo que satisfagan sus necesidades organizativas. Cree grupos para organizar a los usuarios o dispositivos por ubicación geográfica, departamento o características de hardware. Use los grupos para administrar tareas a escala. Por ejemplo, puede establecer directivas para muchos usuarios o implementar aplicaciones para un conjunto de dispositivos.

Puede agregar los siguientes tipos de grupos:
- **Grupos asignados**: se agregan usuarios o dispositivos manualmente a un grupo estático
- **Grupos dinámicos**: (Con Azure Active Directory Premium) permiten crear de forma dinámica grupos de usuarios o dispositivos definidos con reglas simples o avanzadas

## <a name="add-a-new-group"></a>Agregar un grupo nuevo

Use los siguientes pasos para crear un grupo.
1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel de **Intune**, vaya a **Grupos** y luego elija **Nuevo grupo** en el panel **Todos los grupos**.
   ![Captura de pantalla de Azure Portal con la opción Nuevo grupo seleccionada](./media/groups-add-new.png)
4. En **Tipo de grupo**, elija una de las opciones siguientes:
    - **Seguridad**: Los grupos de seguridad son un buen recurso para rellenar grupos de usuarios. Puesto que los grupos de seguridad definen quién puede acceder a qué recursos, se pueden convertir perfectamente en grupos de usuarios de Intune. Los grupos de seguridad que se sincronizan de Active Directory a Azure Active Directory, o que se crean directamente en Azure Active Directory a través del Centro de administración de Microsoft 365 o Azure Portal, están disponibles al crear grupos de usuarios en Intune.
    - **Office 365**

5. Escriba un **nombre** y una **descripción** para el grupo nuevo. Estas propiedades solo aparecen en el portal de administración y no se muestran a los usuarios.

6. Elija **Tipo de pertenencia**:
   - **Asignado** para crear un grupo con miembros asignados de forma manual. Más información sobre [grupos asignados de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
   - **Usuario dinámico** para crear un grupo de usuarios definido con una **consulta dinámica**.
   - **Dispositivo dinámico** para crear un grupo de dispositivos definido con una **consulta dinámica**.

   ![Captura de pantalla de las propiedades del grupo de Intune](./media/groups-add-properties.png)

   Azure AD permite crear grupos dinámicos basados en reglas que definen la pertenencia. Más información para [crear grupos dinámicos basados en atributos](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

7. Puede seleccionar **¿Quiere habilitar las características de Office?** para dar acceso a los miembros del grupo de usuarios a aplicaciones compartidas de Office 365. Obtenga más información sobre [Grupos de Office 365](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).
8. Elija **Crear** para agregar el nuevo grupo.

## <a name="groups-and-policies"></a>Grupos y directivas

Al crear grupos, tenga en cuenta cómo aplicará las [directivas](device-compliance-get-started.md). Por ejemplo, puede tener directivas específicas del sistema operativo de un dispositivo o directivas específicas de diferentes roles de la organización, o de unidades organizativas que ya ha definido en Active Directory. Podría resultar útil disponer de grupos de dispositivos separados para iOS, Android y Windows, así como de un grupo de usuarios para cada rol organizativo.

Además, probablemente quiera crear una directiva predeterminada que se aplique a todos los grupos y dispositivos para establecer los requisitos de cumplimiento básicos de la organización. Luego puede crear directivas más específicas para las categorías más amplias de usuarios y dispositivos. Por ejemplo, puede crear directivas de correo electrónico para cada uno de los sistemas operativos de dispositivos.



## <a name="see-also"></a>Consulte también
- [Administración del acceso a los recursos con grupos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Grupos clásicos de Intune en Azure Portal](groups-get-started.md)
