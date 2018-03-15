---
title: "Visualización del inventario de dispositivos de Intune"
titlesuffix: Azure portal
description: "Sepa cómo ver los dispositivos que administra con Intune y conocer su hardware y aplicaciones administradas."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 772e2b1380626384d618e653b90b31a1f421eb72
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-view-intune-device-inventory"></a>Visualización del inventario de dispositivos de Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La carga de trabajo **Dispositivos** le proporciona información sobre los dispositivos que administra, como sus funcionalidades de hardware y las aplicaciones instaladas en ellos. 

Para ver el inventario de dispositivos:

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services (Todos los servicios)** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Intune**, elija **Dispositivos**.

Ahora, seleccione una de las siguientes opciones:

- **Overview** (Información general): obtenga información sobre los dispositivos que ha inscrito y los sistemas operativos en los que se ejecuta cada dispositivo.
- **Administrar**: elija **Todos los dispositivos** para ver una lista de todos los dispositivos que administra.
    Seleccione uno de los dispositivos de la lista para abrir la hoja *nombre de dispositivo*> **Overview** (Información general) donde puede seleccionar una de estas opciones:
    - **Overview** (Información general): vea información general sobre el dispositivo, incluido su nombre, el propietario, si se trata de un dispositivo BYOD, cuándo se registró por última vez, y mucho más.
    - **Hardware**: vea información más detallada sobre el dispositivo, como el espacio libre de almacenamiento, el modelo, el fabricante y mucho más.
    - **Aplicaciones detectadas**: muestra una lista de todas las aplicaciones instaladas en el dispositivo que encuentra Intune.
    - **Cumplimiento de dispositivo**: muestra el estado de cumplimiento de todas las directivas de cumplimiento que se han asignado al dispositivo.
    - **Configuración de dispositivo**: muestra el estado de cumplimiento de todas las directivas de configuración de dispositivo que se han asignado al dispositivo.
- **Monitor**: seleccione **Acciones de dispositivo** para ver una lista de acciones de dispositivo que se han realizado en los dispositivos que administra y su estado actual.
- **Configuración** > **conector de TeamViewer**: configure la administración remota en dispositivos con el software de TeamViewer. Para obtener detalles, vea [Asistencia remota para dispositivos Android administrados con Intune](/intune/device-profile-android-teamviewer).

Intune solo recopila inventario de las aplicaciones de los dispositivos corporativos, no de los personales. En los equipos con Windows 10, solo recopila inventario de las aplicaciones modernas de los dispositivos corporativos. Intune no recopila información sobre las aplicaciones de Win32 del dispositivo. Es posible que no se recopilen todos los elementos del inventario, según el operador que utilice con los dispositivos.
