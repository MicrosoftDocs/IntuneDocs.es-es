---
title: Restricciones de dispositivos de Intune para Windows 10 Team
titleSuffix: Intune on Azure
description: Aprenda sobre las restricciones de dispositivos disponibles para dispositivos Windows 10 Team.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: abb5e181430b267ca2267bb7209687177ae5fde2
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos Windows 10 Team en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="apps-and-experience"></a>Aplicaciones y experiencia

- **Reactivar pantalla cuando hay alguien en la sala**: permite que el dispositivo se active automáticamente cuando su sensor detecta alguien en la sala.
- **Información sobre la reunión en la pantalla de inicio de sesión**: habilite esta opción para elegir la información que se muestra en el icono de reuniones de la pantalla de bienvenida. Puede:
    - **Mostrar solo el organizador y la hora**
    - **Mostrar el organizador, la hora y el asunto (asunto oculto para reuniones privadas)**
- **URL de imagen de fondo de pantalla de inicio de sesión**: habilite esta opción para mostrar un fondo personalizado en la pantalla de **bienvenida** de los dispositivos Windows 10 Team desde la dirección URL que especifique.<br>La imagen debe estar en formato PNG y la dirección URL debe comenzar con **https://**.

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights**: parte del conjunto de aplicaciones Microsoft Operations Manager, Azure Operational Insights recopila, almacena y analiza datos de archivos de registro de dispositivos con Windows 10 Team.
Para conectarse a Visión operativa de Azure, se debe especificar un **Id. de área de trabajo** y una **Clave de área de trabajo**.

## <a name="maintenance"></a>Mantenimiento

- **Ventana de mantenimiento para actualizaciones**: configura la ventana de cuándo pueden tener lugar actualizaciones en el dispositivo. Puede configurar la **hora de inicio** de la ventana y la **duración en horas** (de 1 a 5 horas).

## <a name="wireless-projection"></a>Proyección inalámbrica

- **PIN para proyección inalámbrica**: especifica si debe escribir un PIN para poder usar las funcionalidades de proyección inalámbrica del dispositivo.
- **Proyección inalámbrica de Miracast**: seleccione esta opción si quiere permitir que el dispositivo Windows 10 Team use los dispositivos habilitados para Miracast para proyectar.
- **Canal de proyección inalámbrica de Miracast**: seleccione el canal de Miracast que se usará para establecer la conexión.


## <a name="next-steps"></a>Pasos siguientes

Use la información descrita en [Configuración de restricciones de dispositivos en Microsoft Intune](device-restrictions-configure.md) para guardar y asignar el perfil a los usuarios y dispositivos.
