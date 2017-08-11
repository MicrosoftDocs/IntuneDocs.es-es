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
ms.openlocfilehash: 7aad054f0861522174faa01b979083a818c106af
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Ayude a los usuarios con el portal de solución de problemas en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

El portal de solución de problemas permite que los operadores del departamento de soporte técnico y los administradores de Intune vean la información de usuario para solucionar las solicitudes de ayuda del usuario. Las organizaciones que incluyen los operadores del departamento de soporte técnico en su personal pueden asignar el **operador del departamento de soporte técnico** a un grupo de usuarios, que pueden usar después la hoja de solución de problemas para ayudar a los usuarios.

Por ejemplo, cuando un usuario se pone en contacto con el soporte técnico por un problema técnico con Intune, el operador del departamento de soporte técnico escribe el nombre del usuario. Intune muestra datos útiles que pueden ayudar a resolver muchos problemas de nivel 1 incluidos:
- Estado del usuario
- Assignments
- Error de instalación de la aplicación
- Problemas de cumplimiento
- El dispositivo no responde
-   El dispositivo no obtiene una configuración Wi-Fi o VPN
-   Error de instalación de la aplicación


## <a name="add-help-desk-operators"></a>Incorporación de operadores del departamento de soporte técnico
Como administrador de Intune, puede asignar el rol Operador del departamento de soporte técnico a un grupo de usuarios. Los miembros de ese grupo pueden usar el portal de administración para solucionar los problemas de los usuarios. Cada operador del departamento de soporte técnico debe tener una licencia de Intune para tener acceso al portal de Intune. Obtenga información sobre cómo [asignar licencias de Intune](licenses-assign.md).

Para agregar usuarios al departamento de soporte técnico:
1. [Agregue un usuario a Intune](users-add.md) si es necesario
2. [Cree un grupo de departamento de soporte técnico](groups-add.md) y agregue usuarios al grupo
3. [Asigne el rol de operador del departamento de soporte técnico de RBAC](role-based-access-control.md#built-in-roles) o [cree un rol personalizado](role-based-access-control.md#custom-roles) con los permisos siguientes:
  - MobileApps: Lectura
  - ManagedApps: Lectura
  - ManagedDevices: Lectura
  - Organización: Lectura
  - DeviceCompliancePolices: Lectura
  - DeviceConfigurations: Lectura

  ![Captura de pantalla del portal de Intune que muestra los roles de Intune resaltados y una lista de roles integrados incluido el Operador del departamento de soporte técnico](./media/help-desk-user-add.png)

4. Para proporcionar a los operadores del departamento de soporte técnico permiso para ver el estado del servicio y abrir vales de soporte técnico para Intune, [conceda permisos de administración a los usuarios](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal) como un **administrador de servicios**. No conceda permiso de **Administrador de servicios de Intune** porque este rol de directorio tiene más derechos que los que necesitan los operadores del departamento de soporte técnico.

## <a name="access-the-troubleshooting-portal"></a>Acceso al portal de solución de problemas

El personal del departamento de soporte técnico y los administradores de Intune pueden acceder al portal de solución de problemas de dos formas:
- Abra [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) en un explorador web para ver solo el portal de solución de problemas.
  ![Captura de pantalla de la consola de solución de problemas](./media/help-desk-console.png)
- Inicie sesión en Azure Portal, seleccione **Más servicios** > **Supervisión y administración** > **Intune** y, después, vaya a **Ayuda y soporte técnico** > **Solucionar problemas**.

Haga clic en **Seleccionar usuario** para ver un usuario y los detalles de este.

![Captura de pantalla de la carga de trabajo Solución de problemas de Intune con el vínculo Seleccionar usuario](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>Uso del portal de solución de problemas

En el portal de solución de problemas, puede elegir la opción **Seleccionar usuario** para ver la información de usuarios. La información de usuario puede ayudarle a comprender el estado actual de los usuarios y sus dispositivos. En el portal de solución de problemas se muestran los siguientes detalles:
- **Estado de la cuenta**
- **Estado del usuario**
- **Dispositivos** con acciones de dispositivo
- **Pertenencia a grupos**
- **Estado de protección de la aplicación**
