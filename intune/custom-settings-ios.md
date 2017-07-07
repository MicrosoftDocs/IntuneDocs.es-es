---
title: "Configuración personalizada de Intune para dispositivos iOS"
titleSuffix: Intune on Azure
description: "Conozca la configuración que puede usar en un perfil personalizado de iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6da8caa8-65c2-4f47-842f-9570dcb1ac22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b169fe74063b618f947f5d3d6809e0e49a5136e3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="microsoft-intune-custom-settings-for-ios-devices"></a>Configuración personalizada de Microsoft Intune para dispositivos iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use el perfil personalizado de iOS de Microsoft Intune para asignar la configuración que ha creado mediante la [herramienta Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) en dispositivos iOS. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. A continuación, puede importar este perfil de configuración en un perfil personalizado de iOS de Intune y asignar la configuración a usuarios y dispositivos de su organización.

Esta funcionalidad permite asignar la configuración de iOS que no se puede configurar con otros tipos de perfiles de Intune.


1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
2. En la hoja **Create Profile** (Crear perfil), especifique lo siguiente:

- **Nombre del perfil de configuración personalizado**: proporcione un nombre para la directiva que se mostrará en el dispositivo y en los informes de estado de Intune.
- **Archivo del perfil de configuración**: vaya al perfil de configuración que ha creado mediante Apple Configurator.
Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de iOS en los dispositivos a los que asigna la directiva personalizada de iOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **Referencia de perfiles de configuración** y la **Referencia del protocolo de administración de dispositivos móviles** en el sitio web de [Apple Developer](https://developer.apple.com/).

El archivo importado se mostrará en el área de **contenido del archivo** de la hoja.
