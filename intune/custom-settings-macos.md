---
title: "Configuración personalizada de Intune para dispositivos macOS"
titleSuffix: Azure portal
description: "Conozca la configuración que puede usar en un perfil personalizado de macOS."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d52b6aac830ff01ee5c05ebc51f923102bf3eef2
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="custom-settings-for-macos-devices-in-microsoft-intune"></a>Opciones de configuración personalizadas para dispositivos macOS en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use el perfil personalizado de macOS de Microsoft Intune para asignar la configuración que ha creado mediante la herramienta [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) en dispositivos macOS. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. Luego, puede importar este perfil de configuración en un perfil personalizado de macOS de Intune y asignar la configuración a los usuarios y dispositivos de su organización.

Esta funcionalidad permite asignar la configuración de macOS que no se puede configurar con otros tipos de perfiles de Intune.


1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
2. En la hoja **Create Profile** (Crear perfil), especifique lo siguiente:

- **Nombre del perfil de configuración personalizado**: proporcione un nombre para la directiva que se mostrará en el dispositivo y en los informes de estado de Intune.
- **Archivo del perfil de configuración**: vaya al perfil de configuración que ha creado mediante Apple Configurator.
Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de macOS en los dispositivos a los que asigna la directiva personalizada de macOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **Referencia de perfiles de configuración** y la **Referencia del protocolo de administración de dispositivos móviles** en el sitio web de [Apple Developer](https://developer.apple.com/).

El archivo importado se mostrará en el área de **contenido del archivo** de la hoja.
