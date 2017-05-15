---
title: "Portal de solución de problemas del departamento de soporte técnico | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "El personal del departamento de soporte técnico usa el portal de solución de problemas para resolver problemas técnicos de los usuarios"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 4916b66e1f2eeabb42401645dbece28dad28eb19
ms.contentlocale: es-es
ms.lasthandoff: 04/26/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Ayuda a los usuarios con el portal de solución de problemas en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

El portal de solución de problemas permite a los operadores del departamento de soporte técnico y a los administradores de Intune ver usuarios y sus dispositivos, y realizar tareas para resolver problemas técnicos de Intune.

## <a name="add-help-desk-operators"></a>Incorporación de operadores del departamento de soporte técnico
Un administrador de Intune puede asignar permiso de operador del departamento de soporte técnico a los usuarios. Después, los usuarios del departamento de soporte técnico pueden ver el portal de Intune pero no ver o realizar tareas administrativas fuera de la carga de trabajo de solución de problemas.

1. Como administrador de Intune, inicie sesión en [Azure Portal](https:portal.azure.com), seleccione **Más servicios** > **Supervisión y administración** > **Intune**.
2. En la hoja de navegación izquierda, seleccione **Roles de Intune**.
3. En la carga de trabajo **Roles de Intune**, seleccione **Help Desk Operator**  (Operador del departamento de soporte técnico) y luego seleccione **Asignar**.
4. En **Nombre de asignación** (obligatorio), un **Descripción de la asignación** (opcional) y luego asignar **Miembros (grupos)** y **Ámbito (grupos)**.
5. Los miembros del rol Operador del departamento de soporte técnico ahora pueden usar el portal de solución de problemas.

Para más información sobre los roles de Intune, consulte [Roles de Intune (RBAC) para Microsoft Intune](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control).

## <a name="access-the-troubleshooting-portal"></a>Acceso al portal de solución de problemas

El personal del departamento de soporte técnico y los administradores de Intune pueden acceder al portal de solución de problemas de dos maneras:
- En [Azure Portal](https://portal.azure.com), seleccione **Más servicios** > **Supervisión y administración** > **Intune** y luego, en la hoja de navegación izquierda, seleccione **Solucionar problemas**. Otras cargas de trabajo están visibles en la hoja de navegación izquierda, pero no están disponibles.

![Captura de pantalla de la carga de trabajo Solución de problemas de Intune con el vínculo Seleccionar usuario](media/help-desk-user.png)
- Abra [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) en un explorador web. Solamente está visible el portal de solución de problemas.

## <a name="use-the-troubleshooting-portal"></a>Uso del portal de solución de problemas

En el portal de solución de problemas, puede elegir **Seleccionar usuario** para ver la información de un usuario. La información de usuario puede ayudarle a comprender el estado actual de los usuarios y sus dispositivos. El portal de solución de problemas muestra los siguientes detalles de usuario y dispositivo de Intune:
- Información de cuenta de usuario
- Pertenencia a un grupo de usuarios
- Detalles del dispositivo

Los usuarios del departamento de soporte técnico también pueden realizar tareas remotas en dispositivos, como **Bloqueo remoto**.

