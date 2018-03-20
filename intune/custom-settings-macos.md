---
title: "Configuración personalizada de Microsoft Intune para dispositivos que ejecutan macOS"
titleSuffix: 
description: "Conozca la configuración que puede usar en un perfil personalizado de macOS."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5ccc9d48eb16ce155bbed2bbdf38793b8f3bdfda
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-macos"></a>Configuración de dispositivo personalizada de Microsoft Intune para dispositivos que ejecutan macOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use el perfil personalizado de macOS de Microsoft Intune para asignar la configuración que ha creado mediante la herramienta [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) en dispositivos macOS. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. Luego, puede importar este perfil de configuración en un perfil personalizado de macOS de Intune y asignar la configuración a los usuarios y dispositivos de su organización.

Esta funcionalidad permite asignar la configuración de macOS que no se puede configurar con otros tipos de perfiles de Intune.


1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
2. En el panel **Perfil de configuración personalizada**, configure cada una de las siguientes opciones:

- **Nombre del perfil de configuración personalizado**: proporcione un nombre para la directiva tal como se muestra en el dispositivo y en los informes de estado de Intune.
- **Archivo del perfil de configuración**: vaya al perfil de configuración que ha creado mediante Apple Configurator.
Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de macOS en los dispositivos a los que asigna la directiva personalizada de macOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **Referencia de perfiles de configuración** y la **Referencia del protocolo de administración de dispositivos móviles** en el sitio web de [Apple Developer](https://developer.apple.com/).

El archivo importado se muestra en el área **Contenido del archivo** del panel.
