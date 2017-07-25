---
title: "Establecer restricciones de inscripción en Intune"
titleSuffix: Intune on Azure
description: "Restrinja las inscripciones por plataforma y establezca un límite de inscripciones de dispositivos en Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce779e8dad2c9813d5faf1f03bca9b33690508fe
ms.sourcegitcommit: b287025b1a0d09d41faf51cf98c34b676fa1d98e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2017
---
# <a name="add-groups-in-intune"></a>Agregar grupos en Intune
Intune usa grupos de Azure Active Directory (AD) para administrar dispositivos y usuarios. Como administrador de Intune, puede configurar los grupos de modo que satisfagan sus necesidades organizativas. Cree grupos para organizar a los usuarios o dispositivos por ubicación geográfica, departamento o características de hardware. Use los grupos para administrar tareas a escala. Por ejemplo, puede establecer directivas para muchos usuarios o implementar aplicaciones para un conjunto de dispositivos.

En este tema se explica cómo agregar grupos para su uso en Intune.

Puede agregar los siguientes tipos de grupos:
- **Grupos asignados**: se agregan usuarios o dispositivos manualmente a un grupo estático
- **Grupos dinámicos**: (Azure Active Directory Premium) permiten crear de forma dinámica grupos de usuarios o dispositivos definidos con reglas simples o avanzadas

## <a name="add-a-new-group"></a>Agregar un grupo nuevo

Use los siguientes pasos para crear un grupo.
1. En el portal de Intune, vaya a **Grupos** y luego elija **Nuevo grupo** en la hoja **Todos los grupos**.
  ![Captura de pantalla del portal de Intune con la opción Nuevo grupo seleccionada](./media/groups-add-new.png)
2. Especifique el **Nombre** y la **Descripción** del nuevo grupo. Estas propiedades solo aparecen en el portal de Intune y no se muestran a los usuarios.

3. Elija **Tipo de pertenencia**:
  - **Asignado** para crear un grupo con miembros asignados de forma manual. Más información sobre [grupos asignados de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
  - **Usuario dinámico** para crear un grupo de usuarios definido con una **consulta dinámica**.
  - **Dispositivo dinámico** para crear un grupo de dispositivos definido con una **consulta dinámica**.

  ![Captura de pantalla de las propiedades de los grupos de Intune con Nombre, Descripción, Tipo de pertenencia, ¿Quiere habilitar las características de Office? y Miembros](./media/groups-add-properties.png)

  Azure AD permite crear grupos dinámicos basados en reglas que definen la pertenencia. Más información para [crear grupos dinámicos basados en atributos](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

4. Puede seleccionar **¿Quiere habilitar las características de Office?** para dar acceso a los miembros del grupo de usuarios a aplicaciones compartidas de Office 365.
5. Elija **Crear** para agregar el nuevo grupo.

## <a name="see-also"></a>Consulte también
- [Administración del acceso a los recursos con grupos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Grupos clásicos de Intune en Azure Portal](groups-get-started.md)
