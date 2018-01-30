---
title: "Visualización del inventario de dispositivos de Intune"
titlesuffix: Azure portal
description: "Sepa cómo ver los dispositivos que administra con Intune y conocer su hardware y aplicaciones administradas."
keywords: 
author: arob98
ms.author: angrobe
nmanager: dougeby
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39351e76c2510f7411c64d4bc3e3275bc051c63e
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
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
    - **Hardware**: vea información más detallada sobre el dispositivo, como el espacio libre de almacenamiento, el modelo, el fabricante y mucho más.
    - **Aplicaciones detectadas**: muestra una lista de todas las aplicaciones instaladas en el dispositivo que encuentra Intune.
    - **Cumplimiento de dispositivo**: muestra el estado de cumplimiento de todas las directivas de cumplimiento que se han asignado al dispositivo.
    - **Configuración de dispositivo**: muestra el estado de cumplimiento de todas las directivas de configuración de dispositivo que se han asignado al dispositivo.
- **Monitor** (Supervisar): seleccione **Acciones de dispositivo** para ver una lista de acciones de dispositivo que se han realizado en los dispositivos administrados y su estado actual.
- **Configuración** > **conector de TeamViewer**: configure la administración remota en dispositivos con el software de TeamViewer. Para obtener detalles, vea [Asistencia remota para dispositivos Android administrados con Intune](/intune/device-profile-android-teamviewer).

Intune solo recopila inventario de las aplicaciones de los dispositivos corporativos, no de los personales. En los equipos con Windows 10, solo recopila inventario de las aplicaciones modernas de los dispositivos corporativos. Intune no recopila información sobre las aplicaciones de Win32 del dispositivo. Es posible que no se recopilen todos los elementos del inventario, según el operador que utilice con los dispositivos.
