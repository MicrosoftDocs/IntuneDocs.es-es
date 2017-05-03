---
title: "Configuración de Intune AirPlay para dispositivos iOS"
titleSuffix: Intune Azure preview
description: "Obtenga información sobre cómo puede usar Intune para conectar automáticamente dispositivos iOS a dispositivos AirPlay compatibles."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: f1f7aa6a0b441b51f20d104c4353a1542a9e01ad
ms.lasthandoff: 04/19/2017


---

# <a name="intune-airplay-settings-for-ios-devices"></a>Configuración de Intune AirPlay para dispositivos iOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use esta configuración para conectar los dispositivos iOS que administra con dispositivos AirPlay compatibles (como Apple TV) en la red.
Con esta funcionalidad, puede:

- **Configurar una lista de dispositivos y contraseñas**: aprovisione dispositivos con el nombre y contraseña de dispositivos AirPlay para permitirles conectarse automáticamente cuando estén dentro del alcance. Si suministra una contraseña, no será necesario que los usuarios finales suministren una cuando se conecten.
- **Configurar destinos permitidos**: configure una lista de dispositivos AirPlay (por identificador de dispositivo). Los usuarios finales solo podrán ver y conectarse a los dispositivos de la lista (solo para dispositivos supervisados).

## <a name="get-started"></a>Introducción

1. En la hoja **Características del dispositivo**, elija **AirPlay**.
2. En la hoja **AirPlay**, elija una de las acciones siguientes o ambas:

## <a name="configure-a-device-and-password-list"></a>Configuración de una lista de dispositivos y contraseñas

1. En la hoja **Contraseñas**, escriba el **nombre del dispositivo** y la **contraseña** de un dispositivo AirPlay, por ejemplo, **Contoso Apple TV**.
2. Después de escribir los detalles del dispositivo, haga clic en **Agregar**. El dispositivo aparecerá en la lista **Nombre de dispositivos**.
3. Siga agregando dispositivos. Cuando termine, elija **Aceptar**.


## <a name="configure-allowed-destinations"></a>Configuración de destinos permitidos

1. En la hoja **Destinos permitidos (solo supervisados)*, escriba el **identificador** de un dispositivo AirPlay, por ejemplo, 52:46:CD:51:83:4C.
2. Después de escribir el identificador del dispositivo, haga clic en **Agregar**. El identificador aparecerá en la lista de **identificadores de dispositivos**.
3. Siga agregando dispositivos. Cuando termine, elija **Aceptar**.

También puede importar dispositivos y contraseñas, además de destinos permitidos desde un archivo de valores separados por comas (csv).



