---
title: 'Restablecimiento de dispositivos Windows 10 con Microsoft Intune: Azure | Microsoft Docs'
description: Use Empezar de cero para quitar o desinstalar aplicaciones en equipos con Windows 10 con Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b66cd00f734cab3ca85f6d87f056f8c482a377d
ms.sourcegitcommit: 2811df0f851ca6b08f6ae8c926fb2e6971c41690
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2018
ms.locfileid: "40252746"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Uso de Empezar de cero para restablecer dispositivos Windows 10 con Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Comienzo de cero** quita las aplicaciones que están instaladas en un equipo que ejecuta Windows 10, versión 1703 o posterior. Comienzo de cero ayuda a eliminar las aplicaciones preinstaladas (OEM) que normalmente se instalan con un nuevo equipo.  

1. Inicie sesión en [Azure Portal](https://portal.azure.com) y vaya a > **Microsoft Intune** > **Dispositivos** > **Todos los dispositivos**.
2. En la lista de dispositivos que administra, elija un dispositivo de escritorio de Windows 10.
3. Haga clic en **Comienzo de cero**. 
4. Seleccione **Conservar los datos de usuario en este dispositivo** para:
   * Mantener el dispositivo unido a Azure AD
    * Mantener el dispositivo inscrito en la administración de dispositivos móviles 
    * Mantener el contenido de la carpeta Inicio del usuario del dispositivo y quitar las aplicaciones y la configuración  
  > [!IMPORTANT]
 > Si no se conservan los datos de usuario, se restaurará el dispositivo a su estado de fábrica. Se quitará su suscripción de Azure AD y la administración de dispositivos móviles. 
 
5. Haga clic en **Aceptar**.   
6. Para ver el estado de esta acción, vuelva a **Dispositivos** y haga clic en **Acciones de dispositivo**.  
