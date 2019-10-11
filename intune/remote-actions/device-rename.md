---
title: 'Cambio de nombre de un dispositivo con Microsoft Intune: Azure | Microsoft Docs'
description: Cambie el nombre de un dispositivo mediante Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35fae5ea1b3294772db4f4db51179892e08ed5d1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728512"
---
# <a name="rename-a-device-in-intune"></a>Cambio de nombre de un dispositivo en Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La acción **Cambiar el nombre del dispositivo** le permite cambiar el nombre de un dispositivo que está inscrito en Intune. El nombre del dispositivo se cambia en Intune y en el dispositivo.

Puede cambiar el nombre de los tipos de dispositivos siguientes:
- Windows de propiedad corporativa 
- iOS supervisado
- MacOS 10 de propiedad corporativa

Esta característica no es compatible actualmente con el cambio de nombre de dispositivos Windows híbridos con Azure AD.

## <a name="rename-a-device"></a>Cambiar el nombre de un dispositivo

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Elija **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Más** > **Cambiar el nombre del dispositivo**.
4. En la hoja **Cambio de nombre de un dispositivo**, escriba el nombre nuevo en el cuadro de texto. Puede usar letras, números y guiones. El nombre debe incluir al menos una letra o guion.
5. Si quiere reiniciar el dispositivo después de cambiarle el nombre, elija **Sí** junto a **Restart after rename** (Reiniciar tras cambio de nombre).
6. Elija **Cambiar nombre**.



## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción **Cambiar nombre** del dispositivo, revise la página de **Información general** del dispositivo.
