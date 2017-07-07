---
title: "Supervisión del cumplimiento de dispositivos"
titleSuffix: Intune on Azure
description: Aprenda a supervisar el cumplimiento de los dispositivos.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f18bfa7fb045dbad4ab785c2c8e1bc13fc439db
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-monitor-device-compliance-in-intune"></a>Supervisión del cumplimiento de dispositivos en Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Puede ver el resumen del estado de sus **perfiles de cumplimiento** en la hoja **Overview** (Información general).
Puede hacer clic de manera interactiva por los gráficos para profundizar en los detalles. Si ha configurado varios perfiles de cumplimiento, también puede ver el estado de cada directiva; para ello, vaya a la hoja de la directiva y elija **Informes** en la sección **Administrar**.  A continuación se enumeran los detalles de los informes disponibles.

##  <a name="device-compliance"></a>Cumplimiento de dispositivos

La vista resumida del informe de cumplimiento de dispositivos comienza mostrando la información agregada sobre el número de dispositivos que se notifican con uno de los siguientes estados:

- **Compliant** (Conforme): se ha evaluado recientemente el dispositivo y se ha determinado que es compatible con la configuración del perfil de cumplimiento especificada.
- **Noncompliant** (No conforme): el dispositivo se ha evaluado y se ha determinado que no es compatible.  Si ha habido un período de gracia especificado en el perfil, este expiró y el dispositivo se ha colocado en estado No compatible.
- **Período de gracia**: el dispositivo se ha evaluado y se ha determinado que no es compatible. Sin embargo, se sigue aplicando el período de gracia antes de que el dispositivo se marque realmente se marca como no compatible.

Puede profundizar en cada sección para ver más detalles sobre los dispositivos y usuarios individuales.

## <a name="setting-compliance"></a>Configuración de cumplimiento

El informe de configuración de cumplimiento proporciona detalles sobre cada uno de los valores de cumplimiento, por ejemplo:

- Número de dispositivos que no cumplen la configuración.
- La plataforma a la que se aplica la configuración.

Puede profundizar en cada una de las opciones de configuración para ver más información sobre los perfiles en los que se han habilitado estas opciones y el valor de cada opción.
