---
title: "Configuración personalizada de Intune para dispositivos iOS | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: conozca la configuración que puede usar en un perfil personalizado de iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6da8caa8-65c2-4f47-842f-9570dcb1ac22
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: cfccdbf34437c5ab23cefba5307c53c60573ddb0


---

# <a name="intune-custom-settings-for-ios-devices-in-intune-azure-preview"></a>Configuración personalizada de Intune para dispositivos iOS en la versión preliminar de Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use el perfil personalizado de iOS de Microsoft Intune para implementar la configuración que ha creado mediante la [herramienta Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) en dispositivos iOS. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. A continuación, puede importar este perfil de configuración en un perfil personalizado de iOS de Intune y asignar la configuración a usuarios y dispositivos de su organización.

Esta funcionalidad permite implementar la configuración de iOS que no se puede configurar con otros tipos de perfiles de Intune.


1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](how-to-configure-custom-settings.md) para comenzar.
2. En la hoja **Create Profile** (Crear perfil), especifique lo siguiente:

- **Nombre del perfil de configuración personalizado**: proporcione un nombre para la directiva que se mostrará en el dispositivo y en los informes de estado de Intune.
- **Archivo del perfil de configuración**: vaya al perfil de configuración que ha creado mediante Apple Configurator.
Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de iOS en los dispositivos en los que implementa la directiva personalizada de iOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **Referencia de perfiles de configuración** y la **Referencia del protocolo de administración de dispositivos móviles** en el sitio web de [Apple Developer](https://developer.apple.com/).

El archivo importado se mostrará en el área de **contenido del archivo** de la hoja.



<!--HONumber=Feb17_HO1-->


