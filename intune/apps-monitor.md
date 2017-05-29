---
title: "Supervisión de información de aplicación y asignaciones | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: después de haber asignado una aplicación a usuarios o dispositivos, use esta información para que le ayude a supervisar su estado."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7c39c904cd2a7bd20525d9072067c6e484b4437a
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Supervisión de información de aplicación y asignaciones con Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Intune proporciona diversas maneras en las cuales puede supervisar las propiedades de las aplicaciones que administra, así como el estado de la asignación.

1. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
2. En la hoja de lista de aplicaciones, elija la aplicación para la que desea información. Verá la hoja> **Estado de instalación de dispositivos** de <*nombre de la aplicación*: ![hoja Estado de instalación de aplicaciones.](./media/monitor-apps.png)

Luego, lleve a cabo una de las siguientes acciones para más información sobre las aplicaciones y sus asignaciones.

## <a name="general"></a>General

- **Información general**: proporciona información general básica de la aplicación, además de información sobre el estado de cualquiera de las asignaciones de esa aplicación. Puede elegir uno de los gráficos para abrir las hojas **Estado de instalación de dispositivos** o **Estado de instalación del usuario** para información más detallada.

## <a name="manage"></a>Administrar

- **Propiedades**: veamos y cambiemos la información sobre la aplicación seleccionada. Para más información sobre las propiedades de las aplicaciones, consulte [Incorporación de una aplicación a Microsoft Intune](apps-add.md).
- **Asignaciones**: proporciona información sobre las asignaciones de esta aplicación. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

## <a name="monitor"></a>Supervisión

- **Estado de instalación de dispositivos**: proporciona información detallada sobre cada dispositivo al que asignó la aplicación seleccionada, incluido el nombre del dispositivo, el sistema operativo, la fecha en que se insertó el último dispositivo en Intune y el estado de instalación de la aplicación.
- **Estado de instalación del usuario**: proporciona información detallada del usuario al que asignó la aplicación seleccionada, incluida la cantidad de instalaciones de la aplicación que tiene el usuario en todos los dispositivos e información sobre cualquier error de instalación.
