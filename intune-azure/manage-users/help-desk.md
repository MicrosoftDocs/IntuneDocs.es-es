---
title: "Portal de solución de problemas del departamento de soporte técnico | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "El personal del departamento de soporte técnico usa el portal de solución de problemas para solucionar los problemas técnicos de los usuarios"
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
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 8cf12e434518c9f06c105a22f3b7aef2613fcdb0
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Ayude a los usuarios con el portal de solución de problemas en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

El portal de solución de problemas permite que los operadores del departamento de soporte técnico y los administradores de Intune vean a los usuarios y sus dispositivos y, además, realicen tareas para solucionar problemas técnicos de Intune.

## <a name="add-help-desk-operators"></a>Incorporación de operadores del departamento de soporte técnico
Un administrador de Intune puede asignar permiso de operador del departamento de soporte técnico a los usuarios. Luego, los usuarios del departamento de soporte técnico pueden ver el portal de Intune pero no pueden ver ni realizar tareas administrativas fuera de la carga de trabajo de la solución de problemas.

1. Como administrador de Intune, inicie sesión en [Azure Portal](https:portal.azure.com), seleccione **Más servicios** > **Supervisión y administración** > **Intune**.
2. En la hoja de navegación de la izquierda, seleccione **Roles de Intune**.
3. En la carga de trabajo **Roles de Intune**, seleccione **Operador del departamento de soporte técnico** y, luego, seleccione **Asignar**.
4. Escriba un **nombre de la asignación** (obligatorio), una **descripción de la asignación** (opcional) y, luego, asigne los **miembros (grupos)** y el **ámbito (grupos)**.
5. Los miembros del rol Operador del departamento de soporte técnico ahora pueden usar el portal de solución de problemas.

Para más información sobre los roles de Intune, consulte [Roles de Intune (RBAC)](../access-control/role-based-access-control.md).

## <a name="access-the-troubleshooting-portal"></a>Acceso al portal de solución de problemas

El personal del departamento de soporte técnico y los administradores de Intune pueden acceder al portal de solución de problemas de dos formas:
- En [Azure Portal](https://portal.azure.com), seleccione **Más servicios** > **Supervisión y administración** > **Intune** y, luego, en la hoja de navegación de la izquierda, seleccione **Solución de problemas**. Otras cargas de trabajo están visibles en la hoja de navegación izquierda, pero no están disponibles.

![Captura de pantalla de la carga de trabajo Solución de problemas de Intune con el vínculo Seleccionar usuario](media/help-desk-user.png)
- Abra [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) en un explorador web. Está visible solo el portal de solución de problemas.

## <a name="use-the-troubleshooting-portal"></a>Uso del portal de solución de problemas

En el portal de solución de problemas, puede seleccionar **Seleccionar usuario** para ver la información de usuarios. La información de usuario puede ayudarle a comprender el estado actual de los usuarios y sus dispositivos. El portal de solución de problemas muestra los siguientes detalles de dispositivos y usuarios de Intune:
- Información de cuenta de usuario
- Pertenencia a grupos de usuarios
- Detalles del dispositivo

Los usuarios del departamento de soporte técnico realizan tareas remotas en dispositivos como **Bloqueo remoto**.

