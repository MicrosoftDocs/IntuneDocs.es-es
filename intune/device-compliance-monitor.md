---
title: Supervisión del cumplimiento del dispositivo
titlesuffix: Microsoft Intune
description: Aprenda a supervisar el cumplimiento de los dispositivos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0fec00b18bd63986a537549715af84cd44539fbb
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31830423"
---
# <a name="monitor-device-compliance-in-intune"></a>Supervisión del cumplimiento de dispositivos en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Puede ver el resumen del estado de sus **perfiles de cumplimiento** en la hoja **Overview** (Información general).
Puede hacer clic de manera interactiva por los gráficos para profundizar en los detalles. Si tiene varios perfiles de cumplimiento configurados, puede ver el estado de las directivas en la hoja de directivas de **Administrar** > **Informes**.

##  <a name="device-compliance"></a>Cumplimiento de dispositivos

La vista resumida del informe de cumplimiento de dispositivos muestra información agregada sobre el número de dispositivos que se notifican con uno de los siguientes estados:

- **Compatible**: el dispositivo se ha evaluado recientemente y cumple la configuración del perfil de cumplimiento que ha especificado.
- **Noncompliant** (No conforme): el dispositivo se ha evaluado y se ha determinado que no es compatible.  Si ha habido un período de gracia especificado en el perfil, este expiró y el dispositivo se ha colocado en estado No compatible.
- **Período de gracia**: el dispositivo se ha evaluado y se ha determinado que no es compatible. Sin embargo, se sigue aplicando el período de gracia antes de que el dispositivo se marque como no compatible.

Puede profundizar en cada sección para ver más detalles sobre los dispositivos y usuarios individuales.

## <a name="setting-compliance"></a>Configuración de cumplimiento

El informe de configuración de cumplimiento proporciona detalles sobre cada uno de los valores de cumplimiento, por ejemplo:

- Número de dispositivos que no cumplen la configuración.
- La plataforma a la que se aplica la configuración.

Puede profundizar en cada una de las opciones de configuración para ver más información sobre los perfiles en los que se han habilitado estas opciones y el valor de cada opción.
