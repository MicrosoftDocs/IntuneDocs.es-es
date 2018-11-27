---
title: Configuración de Intune AirPlay para dispositivos iOS
titlesuffix: Microsoft Intune
description: Sepa cómo puede usar Microsoft Intune para conectar automáticamente dispositivos iOS a dispositivos AirPlay compatibles.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: efeb7895bcd83883e7fcaaca93c3d19d19a0bb5c
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184138"
---
# <a name="intune-airplay-settings-for-ios-devices"></a>Configuración de Intune AirPlay para dispositivos iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use esta configuración para conectar los dispositivos iOS que administra con dispositivos AirPlay compatibles (como Apple TV) en la red.
Con esta funcionalidad, puede:

- **Configurar una lista de dispositivos y contraseñas**: se permite a los usuarios conectarse automáticamente a dispositivos AirPlay que se encuentran dentro del alcance. Aprovisiónelos con el nombre y la contraseña de dispositivos AirPlay, para que no tengan que proporcionarlos cuando se conecten.
- **Configurar destinos permitidos**: configure una lista de dispositivos AirPlay (por identificador de dispositivo). Los usuarios finales solo pueden ver y conectarse a los dispositivos de la lista (solo para dispositivos supervisados).

## <a name="get-started"></a>Introducción

1. Desde [Intune en Azure Portal](https://portal.azure.com), vaya a [**Características del dispositivo** en el área de configuración de dispositivos](device-features-configure.md). 
1. En el panel **Características del dispositivo**, elija **AirPlay**.
2. En el panel **AirPlay**, elija una de las acciones siguientes o ambas:

## <a name="configure-a-device-and-password-list"></a>Configuración de una lista de dispositivos y contraseñas

1. En el panel **Contraseñas**, escriba el **Nombre del dispositivo** y la **Contraseña** de un dispositivo AirPlay, por ejemplo, **Contoso Apple TV**.
2. Después de escribir los detalles del dispositivo, haga clic en **Agregar**. El dispositivo aparece en la lista **Nombre de dispositivos**.
3. Siga agregando dispositivos. Cuando termine, elija **Aceptar**.


## <a name="configure-allowed-destinations"></a>Configuración de destinos permitidos

1. En el panel **Allowed destinations (supervised only)** [Destinos permitidos (solo supervisados)], escriba el **identificador** de un dispositivo AirPlay, por ejemplo, 52:46:CD:51:83:4C.
2. Después de escribir el identificador del dispositivo, haga clic en **Agregar**. El identificador aparece en la lista de **identificadores de dispositivos**.
3. Siga agregando dispositivos. Cuando termine, elija **Aceptar**.

También puede importar dispositivos y contraseñas, además de destinos permitidos desde un archivo de valores separados por comas (csv).


## <a name="next-steps"></a>Pasos siguientes

Ahora puede asignar el perfil de dispositivo a los grupos que elija. Para obtener más información, vea [Asignación de perfiles de dispositivo](device-profile-assign.md).

