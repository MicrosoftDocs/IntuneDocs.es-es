---
title: "Supervisar la implementación de aplicaciones | Microsoft Docs"
description: "Obtenga información acerca de cómo supervisar las aplicaciones implementadas con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5daad56d-71c8-455b-8a55-f8b33e279a8a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 808268faa797d8576f5fb693d9940d97d17abf21
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---


# <a name="monitor-app-deployments-in-microsoft-intune"></a>Supervisar la implementación de aplicaciones en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="monitor-an-app-deployment"></a>Supervisar la implementación de una aplicación
En la consola de administración de Intune puede ver las aplicaciones que administra y el estado de las implementaciones. <!---App status is displayed in real-time. You don't have to wait for the device to check-in before you can see this.--->

### <a name="to-view-apps-that-you-manage-and-their-status"></a>Para ver las aplicaciones que administra y su estado
En el área de trabajo **Aplicaciones**, elija el nodo **Aplicaciones** y, después, seleccione **Aplicaciones**.

Aparece la lista de aplicaciones que administra. Puede elegir cualquier aplicación para ver el estado de la instalación en el panel inferior de las ventanas de la consola. Elija este estado para ver más detalles. Por ejemplo, si se muestra el estado **1 usuario tiene este software disponible**, puede elegir el mensaje para ver el nombre del usuario.

> [!TIP]
> Puede usar la lista desplegable **Filtros** para mostrar solo las aplicaciones que cumplen los criterios que especifique, como las aplicaciones que no se han podido instalar o las aplicaciones que se han implementado correctamente.
>
> ![Ejemplo de filtros de aplicación](./media/app-filters.png)

Además, el área de trabajo **Panel** muestra información general sobre el estado de las aplicaciones. Si hace clic en cualquier parte de la información general, accederá a la lista de aplicaciones.

## <a name="to-view-more-detailed-information-about-an-app"></a>Para ver información más detallada sobre una aplicación
En la lista de aplicaciones, seleccione cualquier aplicación y elija **Ver propiedades**.

En la página **Propiedades del software** de la aplicación, elija una de estas pestañas: **General** (para ver información general sobre la aplicación y su estado de instalación), **Dispositivos** (para ver los dispositivos que han instalado correctamente una implementación dirigida de la aplicación) y **Usuarios**para ver los usuarios en cuyos dispositivos se ha instalado correctamente una implementación dirigida de la aplicación).

Al igual que antes, puede usar la lista desplegable **Filtros** para configurar los valores mostrados en cada una de las pestañas.

