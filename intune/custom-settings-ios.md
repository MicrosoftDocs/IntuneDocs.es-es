---
title: "Configuración personalizada de Microsoft Intune para dispositivos que ejecutan iOS"
titleSuffix: Azure portal
description: "Conozca la configuración que puede usar en un perfil personalizado de iOS."
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
ms.openlocfilehash: 40e34a2e22c9349cad63d813b892863e0e8a2933
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-ios"></a>Configuración de dispositivo personalizada de Microsoft Intune para dispositivos que ejecutan iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use el perfil personalizado de iOS de Microsoft Intune para asignar la configuración que ha creado mediante la [herramienta Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) en dispositivos iOS. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. A continuación, puede importar este perfil de configuración en un perfil personalizado de iOS de Intune y asignar la configuración a usuarios y dispositivos de su organización.

Esta funcionalidad permite asignar la configuración de iOS que no se puede configurar con otros tipos de perfiles de Intune.


1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
2. En el panel **Perfil de configuración personalizada**, configure cada una de las siguientes opciones:

- **Nombre del perfil de configuración personalizado**: proporcione un nombre para la directiva tal como se muestra en el dispositivo y en los informes de estado de Intune.
- **Archivo del perfil de configuración**: vaya al perfil de configuración que ha creado mediante Apple Configurator.
Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de iOS en los dispositivos a los que asigna la directiva personalizada de iOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **Referencia de perfiles de configuración** y la **Referencia del protocolo de administración de dispositivos móviles** en el sitio web de [Apple Developer](https://developer.apple.com/).

El archivo importado se muestra en el área **Contenido del archivo** del panel.
