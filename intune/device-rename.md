---
title: 'Cambio de nombre de un dispositivo Windows con Microsoft Intune: Azure | Microsoft Docs'
description: Cambie el nombre de un dispositivo Windows con Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dfdc3641d583fc045346034ee8543feff1e7cbf
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "59567106"
---
# <a name="rename-a-windows-device-in-intune"></a>Cambio de nombre de un dispositivo Windows en Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La acción **Cambiar el nombre del dispositivo** le permite cambiar el nombre de un dispositivo Windows de propiedad de la empresa que está inscrito en Intune. El nombre del dispositivo se cambia en Intune y en el dispositivo. 

Esta característica no es compatible actualmente con el cambio de nombre de dispositivos Windows híbridos con Azure AD.

## <a name="rename-a-device"></a>Cambiar el nombre de un dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Elija **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Elija **Dispositivos** > **Todos los dispositivos** > elija un dispositivo Windows > **Más** > **Cambiar el nombre del dispositivo**.
4. En la hoja **Cambio de nombre de un dispositivo**, escriba el nombre nuevo en el cuadro de texto. Puede usar letras, números y guiones. El nombre debe incluir al menos una letra o guion.
5. Si quiere reiniciar el dispositivo después de cambiarle el nombre, elija **Sí** junto a **Restart after rename** (Reiniciar tras cambio de nombre).
6. Elija **Cambiar nombre**.



## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción **Cambiar nombre** del dispositivo, revise la página de **Información general** del dispositivo.
