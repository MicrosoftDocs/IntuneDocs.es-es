---
title: "Visualización del inventario de dispositivos de Intune"
titleSuffix: Intune on Azure
description: "Sepa cómo ver los dispositivos que administra con Intune y conocer su hardware y aplicaciones administradas."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3618c5ee0b4a7ff0e7b6a4d6ed58f77a2af0ba66
ms.sourcegitcommit: fb17b59f4aa2b994b149fcc6d32520f74b0de6a5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2017
---
# <a name="how-to-view-intune-device-inventory"></a>Visualización del inventario de dispositivos de Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La carga de trabajo **Dispositivos** le proporciona información sobre los dispositivos que administra, como sus funcionalidades de hardware y las aplicaciones instaladas en ellos. 

Para ver el inventario de dispositivos:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.

Ahora, seleccione una de las siguientes opciones:

- **Overview** (Información general): obtenga información sobre los dispositivos que ha inscrito y los sistemas operativos en los que se ejecuta cada dispositivo.
- **Administrar**: elija **Todos los dispositivos** para ver una lista de todos los dispositivos administrados.
    Seleccione uno de los dispositivos de la lista para abrir la hoja *nombre de dispositivo*> **Overview** (Información general) donde puede seleccionar una de estas opciones:
    - **Overview** (Información general): vea información general sobre el dispositivo, incluido su nombre, el propietario, si se trata de un dispositivo BYOD, cuándo se registró por última vez, y mucho más.
    ![Información general del dispositivo](./media/device-overview.png)
    - **Hardware**: vea información más detallada sobre el dispositivo, como el espacio libre de almacenamiento, el modelo, el fabricante y mucho más.
    ![Inventario de hardware de dispositivo administrado](./media/hardware-inventory.png)
    - **Aplicaciones detectadas**: muestra una lista de todas las aplicaciones instaladas en el dispositivo que encuentra Intune.
    ![Nodo de aplicaciones detectadas](./media/detected-applications.png)
    


    - **Cumplimiento de dispositivo**: muestra el estado de cumplimiento de todas las directivas de cumplimiento que se han asignado al dispositivo.
    - **Configuración de dispositivo**: muestra el estado de cumplimiento de todas las directivas de configuración de dispositivo que se han asignado al dispositivo.
- **Monitor** (Supervisar): seleccione **Acciones de dispositivo** para ver una lista de acciones de dispositivo que se han realizado en los dispositivos administrados y su estado actual.
- **Configuración** > **conector de TeamViewer**: configure la administración remota en dispositivos con el software de TeamViewer. Para obtener detalles, vea [Asistencia remota para dispositivos Android administrados con Intune](/intune/device-profile-android-teamviewer).

>[!NOTE]
> Intune solo recopila inventario de las aplicaciones de los dispositivos corporativos, no de los personales. En los equipos con Windows 10, solo recopila inventario de las aplicaciones modernas de los dispositivos corporativos. Intune no recopila información sobre las aplicaciones de Win32 del dispositivo.
