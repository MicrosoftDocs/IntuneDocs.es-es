---
title: "Restricciones de dispositivos de Intune para Windows 10 Team | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda sobre las restricciones de dispositivos disponibles para dispositivos Windows 10 Team."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: ab9c879763ce1ed02a52a57e66fdc06fa970c2a4
ms.lasthandoff: 02/16/2017


---

# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos Windows 10 Team en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

- **Reactivar pantalla cuando hay alguien en la sala**: permite que el dispositivo se active automáticamente cuando su sensor detecta alguien en la sala.
- **PIN para proyección inalámbrica**: especifica si debe escribir un PIN para poder usar las funcionalidades de proyección inalámbrica del dispositivo.
- **Proyección inalámbrica de Miracast**: habilite esta opción si quiere permitir que el dispositivo Windows 10 Team use los dispositivos habilitados para Miracast para proyectar.
- **Información sobre la reunión en la pantalla de inicio de sesión**: habilite esta opción para elegir la información que se mostrará en el icono de reuniones de la pantalla de bienvenida. Puede:
    - **Mostrar solo el organizador y la hora**
    - **Mostrar el organizador, la hora y el asunto (asunto oculto para reuniones privadas)**
- **URL de imagen de fondo de pantalla de inicio de sesión**: habilite esta opción para mostrar un fondo personalizado en la pantalla de **bienvenida** de los dispositivos Windows 10 Team desde la dirección URL que especifique.<br>La imagen debe estar en formato PNG y la dirección URL debe comenzar con **https://**.
- **Ventana de mantenimiento para actualizaciones**: configura la ventana de cuándo pueden tener lugar actualizaciones en el dispositivo. Puede configurar la hora de inicio de la ventana y la duración (de 1 a 5 horas).
- **Azure Operational Insights**: parte del conjunto de aplicaciones Microsoft Operations Manager, recopila, almacena y analiza datos de archivos de registro de dispositivos con Windows 10 Team.<br>Para conectarse a Visión operativa de Azure, se debe especificar un **Id. de área de trabajo** y una **Clave de área de trabajo**.

