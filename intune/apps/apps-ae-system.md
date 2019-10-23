---
title: Incorporación de aplicaciones del sistema Android Enterprise a Microsoft Intune
titleSuffix: ''
description: Más información sobre cómo agregar aplicaciones del sistema Android Enterprise a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
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
ms.openlocfilehash: 11618d844fe7c4e190295ad06111ae0944deda95
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507280"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Incorporación de aplicaciones del sistema Android Enterprise a Microsoft Intune

Antes de asignar una aplicación a un dispositivo o a un grupo de usuarios, primero debe agregar la aplicación a Microsoft Intune. Las aplicaciones del sistema son compatibles con dispositivos de Android Enterprise. Puede habilitar una aplicación del sistema en [dispositivos dedicados de Android Enterprise](../enrollment/android-kiosk-enroll.md) o [dispositivos totalmente administrados](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Agregar la aplicación

Para agregar una aplicación del sistema Android Enterprise a Intune desde Azure Portal haga lo siguiente:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. En el panel **Intune**, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**.
3. En el panel **Agregar aplicación**, en **Otros** tipos disponibles, seleccione **Aplicación del sistema Android Enterprise**.
4. Para configurar la información de la aplicación, seleccione **Configurar** y luego proporcione la siguiente información:
    - **Nombre de la aplicación**: escriba el nombre de la aplicación.
    - **Publicador**: Escriba el nombre del publicador de la aplicación.  
    - **Nombre del paquete**: escriba un nombre de paquete. Intune validará si el nombre del paquete es válido.
5. Seleccione **Aceptar**.
6. Seleccione **Agregar**.

> [!NOTE]
> Tendrá que contactar con el OEM del dispositivo para que le indique cómo averiguar el nombre del paquete de la aplicación que desea habilitar o deshabilitar.

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione. 

Las aplicaciones del sistema Android Enterprise habilitarán o deshabilitarán las aplicaciones que ya forman parte de la plataforma. Para habilitar una aplicación, asigne la aplicación del sistema como **Requerida**. Para deshabilitar una aplicación, asigne la aplicación del sistema como **Desinstalar**. Las aplicaciones del sistema no se pueden asignar como disponibles para un usuario.


## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
