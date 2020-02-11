---
title: Incorporación de aplicaciones del sistema Android Enterprise a Microsoft Intune
titleSuffix: ''
description: Más información sobre cómo agregar aplicaciones del sistema Android Enterprise a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755262"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Incorporación de aplicaciones del sistema Android Enterprise a Microsoft Intune

Antes de asignar una aplicación a un dispositivo o a un grupo de usuarios, primero debe agregar la aplicación a Microsoft Intune. Las aplicaciones del sistema son compatibles con dispositivos de Android Enterprise. Puede habilitar una aplicación del sistema en [dispositivos dedicados de Android Enterprise](../enrollment/android-kiosk-enroll.md) o [dispositivos totalmente administrados](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Agregar la aplicación

Para agregar una aplicación del sistema Android Enterprise a Intune desde Azure Portal haga lo siguiente:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en **Otros** tipos disponibles, seleccione **Aplicación del sistema Android Enterprise**.
4. Haga clic en **Seleccionar**. Se muestran los pasos para **Agregar aplicación**.
En la página **Información de la aplicación**, agregue los detalles de la aplicación:
    - **Nombre de la aplicación**: escriba el nombre de la aplicación.
    - **Publicador**: Escriba el nombre del publicador de la aplicación.  
    - **Nombre del paquete**: escriba un nombre de paquete. Intune validará si el nombre del paquete es válido.
5. Haga clic en **Siguiente** para mostrar la página **Etiquetas de ámbito**.
8. Si quiere, haga clic en **Seleccionar etiquetas de ámbito** para agregar etiquetas de ámbito para la aplicación. Para más información, consulte [Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito para TI distribuida](~/fundamentals/scope-tags.md).
9. Haga clic en **Siguiente** para abrir la página **Asignaciones**.
10. Seleccione las asignaciones de grupo para la aplicación. Para más información, consulte [Agregar grupos para organizar usuarios y dispositivos](~/fundamentals/groups-add.md). 
11. Elija **Siguiente** para mostrar la página **Revisar y crear**. Revise los valores y la configuración que especificó para la aplicación.
12. Cuando haya terminado, haga clic en **Crear** para agregar la aplicación a Intune.

Se muestra la hoja **Información general** de la aplicación que creó.

> [!NOTE]
> Tendrá que contactar con el OEM del dispositivo para que le indique cómo averiguar el nombre del paquete de la aplicación que desea habilitar o deshabilitar.

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione. 

Las aplicaciones del sistema Android Enterprise habilitarán o deshabilitarán las aplicaciones que ya forman parte de la plataforma. Para habilitar una aplicación, asigne la aplicación del sistema como **Requerida**. Para deshabilitar una aplicación, asigne la aplicación del sistema como **Desinstalar**. Las aplicaciones del sistema no se pueden asignar como disponibles para un usuario.


## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
