---
title: "Cómo obtienen sus aplicaciones los usuarios de Android | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3bcf89636f9da8fd8bfa5cc52391742a9ce9f92
ms.openlocfilehash: 25571ce1b214c927f3dc2ea3968d00970621e474


---


# Cómo obtienen sus aplicaciones los usuarios de Android
Lea esta información para comprender cómo y dónde obtienen los usuarios finales las aplicaciones que se distribuyen a través de Microsoft Intune. 

**Aplicaciones obligatorias**: son las aplicaciones que exige el administrador y que se instalan en el dispositivo con intervención mínima del usuario, según la plataforma.
 
- **Dispositivos Samsung Knox**: si implementa una aplicación requerida en dispositivos Samsung Knox, se instala automáticamente y de manera silenciosa en su dispositivo.
- **Dispositivos nativos (no de Samsung Knox)**: si implementa una aplicación requerida en dispositivos que no son de Samsung Knox, se instala automáticamente en los dispositivos de los usuarios. En su lugar, a los usuarios se les solicita que instalen la aplicación. Después de que acepten los mensajes, la aplicación se descarga y, después, los usuarios reciben una notificación que indica que necesitan instalarla. 

**Aplicaciones disponibles**: son las aplicaciones que se proporcionan en la lista de aplicaciones de portal de empresa y que un usuario puede instalar si quiere.

**Aplicaciones administradas**: son aplicaciones que se pueden administrar mediante directivas y que están “encapsuladas” con Intune o se han creado con el kit de desarrollo de software (SDK) de administración de aplicaciones móviles (MAM) de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de aplicación pueden aplicarse a estas.

**Aplicaciones no administradas**: son aplicaciones que se pueden administrar mediante directivas y que no están encapsuladas con Intune o no incorporan el SDK de MAM de Intune. Las directivas de aplicación no pueden aplicarse a estas aplicaciones.

###Consulte también
[Agregar aplicaciones con Microsoft Intune](/intune/deploy-use/add-apps)
[Cómo los usuarios de iOS obtienen sus aplicaciones](how-your-ios-users-get-their-apps.md)
[Cómo los usuarios de Windows obtienen sus aplicaciones](how-your-windows-users-get-their-apps.md)


<!--HONumber=Jul16_HO1-->


