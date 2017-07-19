---
title: "Portal de solución de problemas del departamento de soporte técnico"
titleSuffix: Intune on Azure
description: "El personal del departamento de soporte técnico usa el portal de solución de problemas para solucionar los problemas técnicos de los usuarios"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 7a61c3703cd1016ef63c8baa371c3a21dca127fc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Ayude a los usuarios con el portal de solución de problemas en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

El portal de solución de problemas permite que los operadores del departamento de soporte técnico y los administradores de Intune vean la información de usuario para solucionar las solicitudes de ayuda del usuario. Las organizaciones que incluyen los operadores del departamento de soporte técnico en su personal pueden asignar el **operador del departamento de soporte técnico** a un grupo de usuarios, que pueden usar después la hoja de solución de problemas para ayudar a los usuarios.

Por ejemplo, cuando un usuario se pone en contacto con el soporte técnico por un problema técnico con Intune, el operador del departamento de soporte técnico escribe el nombre del usuario. Intune muestra la información pertinente que puede ayudar a resolver muchos problemas de nivel 1 como el estado del usuario, errores en la instalación de aplicaciones o problemas de cumplimiento. Los problemas que se tratan pueden incluir:
- El dispositivo no responde
-   El dispositivo no obtiene una configuración Wi-Fi o VPN
-   Error de instalación de la aplicación


## <a name="add-help-desk-operators"></a>Incorporación de operadores del departamento de soporte técnico
Un administrador de Intune puede asignar permiso de operador del departamento de soporte técnico a los usuarios de dos maneras:
- Asignar el rol **Operador del departamento de soporte técnico** integrado
- Crear y asignar un rol personalizado

## <a name="assign-help-desk-operator-role"></a>Asignar el rol de operador del departamento de soporte técnico
Como administrador de Intune, puede asignar el rol Operador del departamento de soporte técnico a un grupo de usuarios. Los miembros de ese grupo pueden usar el portal de administración. Cada operador del departamento de soporte técnico debe tener una licencia de Intune para tener acceso al portal de Intune. Obtenga información sobre cómo [asignar licencias de Intune](licenses-assign.md).

1. Como administrador de Intune, inicie sesión en el portal de Intune y seleccione **Roles de Intune**.
2. En la carga de trabajo **Roles de Intune**, seleccione **Operador del departamento de soporte técnico** > **Asignaciones** y, luego, seleccione **Asignar**.
  ![Captura de pantalla del portal de Intune que muestra los roles de Intune resaltados y una lista de roles integrados incluido el Operador del departamento de soporte técnico con Asignaciones resaltado y un cuadro rojo alrededor de Asignar](./media/help-desk-user-assign.png)
3. Escriba un **nombre de la asignación** (obligatorio), una **descripción de la asignación** (opcional) y, luego, asigne los **miembros (grupos)** y el **ámbito (grupos)**.
4. Los miembros del rol Operador del departamento de soporte técnico ahora pueden usar el portal de solución de problemas.

Para más información sobre los roles de Intune, consulte [Roles de Intune (RBAC)](role-based-access-control.md).

## <a name="create-a-custom-role-for-troubleshooting"></a>Crear un rol personalizado para la solución de problemas
Como administrador de Intune, puede crear un rol personalizado que permita a los usuarios usar el portal de solución de problemas con permisos que se adapten a las necesidades de su organización. Para más información sobre los roles de Intune, consulte [Roles de Intune (RBAC)](role-based-access-control.md).

![Captura de pantalla del portal de Intune que muestra los roles de Intune resaltados y una lista de roles integrados incluido el Operador del departamento de soporte técnico](./media/help-desk-user-add.png)

Para usar la consola de Intune para obtener una vista del departamento de soporte técnico, un rol del departamento de soporte técnico personalizado debe tener los permisos siguientes:
- MobileApps: Lectura
- ManagedApps: Lectura
- ManagedDevices: Lectura
- Organización: Lectura

## <a name="access-the-troubleshooting-portal"></a>Acceso al portal de solución de problemas

El personal del departamento de soporte técnico y los administradores de Intune pueden acceder al portal de solución de problemas de dos formas:
- Abra [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) en un explorador web.
- En el portal de Intune, vaya a **Ayuda y soporte técnico** > **Solucionar problemas**.

![Captura de pantalla de la carga de trabajo Solución de problemas de Intune con el vínculo Seleccionar usuario](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>Uso del portal de solución de problemas

En el portal de solución de problemas, puede elegir la opción **Seleccionar usuario** para ver la información de usuarios. La información de usuario puede ayudarle a comprender el estado actual de los usuarios y sus dispositivos. En el portal de solución de problemas se muestran los siguientes detalles:
- **Estado del inquilino**
- **Estado del usuario**
- **Dispositivos** y acciones de dispositivo
- **Pertenencia a grupos**
- **Estado de protección de la aplicación**
