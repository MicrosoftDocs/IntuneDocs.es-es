---
title: "Supervisión de información de aplicación y asignaciones"
titlesuffix: Azure portal
description: "Después de haber asignado una aplicación a usuarios o dispositivos, use esta información para que le ayude a supervisar su estado."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3736b6d43f5cd3b6c75097a2ceabebffd75f0caa
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Supervisión de información de aplicación y asignaciones con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune proporciona diversas maneras en las cuales puede supervisar las propiedades de las aplicaciones que administra, así como el estado de la asignación.

1. Inicie sesión en Azure Portal.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** + **Intune**.
3. En la carga de trabajo **Aplicaciones móviles**, elija **Aplicaciones** en el grupo **Administrar**.
     
    ![Hoja de estado de instalación de aplicaciones.](./media/monitor-apps.png)
5. En la lista de la hoja de aplicaciones, elija una aplicación. Verá la hoja **Estado de instalación del dispositivo** de <*nombre de la aplicación*> .

El informe de estado de instalación del dispositivo contiene las columnas siguientes:

1.  **Nombre de dispositivo**: contiene el nombre del tipo de dispositivo.
2.  **Nombre de usuario**: se trata del nombre del usuario.
3.   **Plataforma**: es el sistema operativo instalado en el dispositivo.
4.  **Versión**: corresponde al número de versión de la aplicación.
5.   **Estado**: los posibles estados que pueden tener las aplicaciones son **Instalada**, **No instalada**, **Instalación pendiente** y **Error**.
6. **Detalles del estado**: descripción legible del estado de la aplicación en el dispositivo.
7. **Última inserción en el repositorio**: última vez que el dispositivo tuvo acceso a Intune.

Luego, lleve a cabo una de las siguientes acciones para más información sobre las aplicaciones y sus asignaciones.

## <a name="general"></a>General

- **Información general**: proporciona información general básica de la aplicación, además de información sobre el estado de cualquiera de las asignaciones de esa aplicación. Puede elegir uno de los gráficos para abrir las hojas **Estado de instalación de dispositivos** o **Estado de instalación del usuario** para información más detallada.

## <a name="manage"></a>Administrar

- **Propiedades**: veamos y cambiemos la información sobre la aplicación seleccionada. Para más información sobre las propiedades de las aplicaciones, consulte [Incorporación de una aplicación a Microsoft Intune](apps-add.md).
- **Asignaciones**: proporciona información sobre las asignaciones de esta aplicación. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

## <a name="monitor"></a>Supervisión

- **Estado de instalación de dispositivos**: proporciona información detallada sobre cada dispositivo al que asignó la aplicación seleccionada, incluido el nombre del dispositivo, el sistema operativo, la fecha en que se insertó el último dispositivo en Intune y el estado de instalación de la aplicación.
- **Estado de instalación del usuario**: proporciona información detallada del usuario al que ha asignado la aplicación seleccionada, incluida la cantidad de instalaciones de la aplicación que tiene el usuario en todos los dispositivos e información sobre cualquier error de instalación.