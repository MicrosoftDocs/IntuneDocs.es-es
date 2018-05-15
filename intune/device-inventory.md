---
title: Ver los detalles de un dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Vea los detalles del dispositivo, incluidos los sistemas operativos, el espacio de almacenamiento, el fabricante y el modelo. Obtenga una lista de las aplicaciones instaladas, compruebe las directivas de cumplimiento y configure TeamViewer con Microsoft Intune en Azure. El procedimiento es similar a ver el inventario de los dispositivos que administra.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f66c0695c7e3d1f4bb7a5ca3abceeb13f6af41f2
ms.sourcegitcommit: 3c4ea8d6809a63042705b5ed4f25ba80f522070e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="see-device-details-in-intune"></a>Ver detalles del dispositivo en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La característica **Dispositivos** proporciona detalles adicionales sobre los dispositivos que administra, incluido el hardware, y sobre las aplicaciones instaladas.

En este artículo se explica cómo se pueden ver todos los dispositivos y sus propiedades en el portal de Azure.

## <a name="view-the-device-details"></a>Ver los detalles del dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** > **Todos los dispositivos** > seleccione uno de los dispositivos que aparecen para que se muestren los detalles correspondientes:

   - En **Información general** se muestra el nombre del dispositivo y algunas propiedades clave del dispositivo. También se indica si es un dispositivo Bring Your Own Device (BYOD), cuándo se registró, etc. Seleccione **Más** para llevar a cabo las siguientes acciones:
     - Eliminar datos de la compañía
     - Eliminar el dispositivo
     - Bloquear el dispositivo de forma remota
     - Borrar
     - Iniciar una sesión de asistencia remota
   - Use **Propiedades** para asignar una [categoría de dispositivo que cree](device-group-mapping.md) y cambie la propiedad del dispositivo a un dispositivo personal o a un dispositivo de empresa.
   - En **Hardware** se incluye mucha información sobre el dispositivo (identificador del dispositivo, sistema operativo y versión, espacio de almacenamiento, modelo y fabricante, opciones de acceso condicional, etc.).
   - **Aplicaciones detectadas**: muestra todas las aplicaciones que Intune encuentra instaladas en el dispositivo, así como las versiones de las aplicaciones. También puede **exportar** la lista de aplicaciones a un archivo .csv.
   - En **Conformidad de dispositivos** figuran todas las directivas de cumplimiento asignadas y se indica si el dispositivo es compatible o no.
   - En **Configuración del dispositivo** se muestran todas las directivas de configuración de dispositivos asignadas al dispositivo. También se indica si la directiva se ha aplicado correctamente o no.

Intune solo recopila listas de aplicaciones en dispositivos corporativos. Las aplicaciones no se comprueban en los dispositivos personales. En equipos con Windows 10, solo se muestran las aplicaciones modernas en los dispositivos corporativos. Intune no recopila información sobre las aplicaciones Win32 del dispositivo. En función del operador que usen los dispositivos, puede que no se recopilen todas las aplicaciones.

|Plataforma|Para dispositivos personales|Para dispositivos de la compañía|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (sin el cliente de Configuration Manager)|Solo aplicaciones administradas|Solo aplicaciones administradas|
|Windows 8.1 (sin el cliente de Configuration Manager)|Solo aplicaciones administradas|Solo aplicaciones administradas|  
|Windows Phone 8|Solo aplicaciones administradas|Solo aplicaciones administradas|  
|Windows RT|Solo aplicaciones administradas|Solo aplicaciones administradas|  
|iOS|Solo aplicaciones administradas|Todas las aplicaciones instaladas en el dispositivo|
|macOS|Todas las aplicaciones instaladas en el dispositivo|Todas las aplicaciones instaladas en el dispositivo|  
|Android|Solo aplicaciones administradas|Todas las aplicaciones instaladas en el dispositivo|  

## <a name="next-steps"></a>Pasos siguientes
Vea qué más puede hacer para [administrar sus dispositivos](device-management.md) con Intune.