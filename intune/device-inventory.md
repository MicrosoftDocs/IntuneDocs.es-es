---
title: Ver los dispositivos con Microsoft Intune - Azure |Microsoft Docs
description: Vea los detalles del dispositivo, incluidos los sistemas operativos, el espacio de almacenamiento, el fabricante y el modelo. Obtenga una lista de las aplicaciones instaladas, compruebe las directivas de cumplimiento y configure TeamViewer con Microsoft Intune en Azure. El procedimiento es similar a ver el inventario de los dispositivos que administra.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: eaaf3e9807a8eab66c24f4d1bb3c3c5ea9f4cfe0
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="see-device-details-in-intune"></a>Ver detalles del dispositivo en Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La característica **Dispositivos** proporciona detalles adicionales sobre los dispositivos que administra, incluido el hardware, y sobre las aplicaciones instaladas. 

En este artículo se explica cómo se pueden ver todos los dispositivos y sus propiedades en el portal de Azure.

## <a name="view-your-device-details"></a>Ver los detalles del dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos**. En dispositivos, tiene varias opciones:

   - **Información general**: obtenga información sobre los dispositivos que ha inscrito y el sistema operativo en el que se ejecuta cada dispositivo.
   - **Administrar**: para ver una lista de todos los dispositivos que administra, seleccione **Todos los dispositivos** o **Dispositivos Azure AD**.
    Seleccione uno de los dispositivos de la lista. Con este paso se abre la <*Información general de*> **nombre del dispositivo**, donde puede seleccionar lo siguiente:
     - **Información general**: consulte el nombre del dispositivo, el propietario, si es un dispositivo "Bring Your Own Device" (BYOD), cuándo se registró por última vez y más detalles.
     - **Hardware**: vea el espacio de almacenamiento libre, el modelo y fabricante, y más detalles sobre el dispositivo.
     - **Aplicaciones detectadas**: vea una lista de todas las aplicaciones instaladas en el dispositivo que encuentra Intune.
     - **Cumplimiento del dispositivo**: muestra el estado de todas las directivas de cumplimiento que se han asignado al dispositivo.
     - **Configuración de dispositivo**: muestra el estado de cumplimiento de todas las directivas de configuración de dispositivo que se han asignado al dispositivo.
   - **Supervisión**: seleccione **Acciones de dispositivo** para ver una lista de las acciones que se realizan en dispositivo que administra y su estado actual. **Registros de auditoría** muestra el estado de diferentes tareas.
   - **Configuración** > **Conector de TeamViewer**: configure la administración remota en dispositivos con el software TeamViewer. Para obtener detalles, vea [Asistencia remota para dispositivos Android administrados con Intune](device-profile-android-teamviewer.md).

Intune solo recopila listas de aplicaciones en dispositivos corporativos. Las aplicaciones no se comprueban en los dispositivos personales. En equipos con Windows 10, solo se muestran las aplicaciones modernas en los dispositivos corporativos. Intune no recopila información sobre las aplicaciones Win32 del dispositivo. En función del operador que usen los dispositivos, puede que no se recopilen todas las aplicaciones.

## <a name="next-steps"></a>Pasos siguientes
Vea qué más puede hacer para [administrar sus dispositivos](device-management.md) con Intune.
