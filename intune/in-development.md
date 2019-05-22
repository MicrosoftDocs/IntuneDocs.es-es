---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3645d07fe9a703f182e05bc9a7f9fbb93c413ddc
ms.sourcegitcommit: dfcf80a91792715404dc021c8684866c8b0a27e1
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65816244"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>En desarrollo para Microsoft Intune: mayo de 2019

Para ayudarle con la preparación y planeación, en esta página se enumeran las actualizaciones y características de la interfaz de usuario de Intune que están en desarrollo, pero que aún no se han publicado. Además:

- Si prevemos que tendrá que tomar medidas antes de realizar un cambio, haremos una publicación complementaria en el Centro de mensajes de Office.
- Cuando se publique una característica en producción, ya sea como versión preliminar o disponible de forma general, su descripción se quitará de esta página y se moverá a la [página Novedades](whats-new.md).
- Esta página y la [página Novedades](whats-new.md) se actualizan periódicamente. Compruebe si hay actualizaciones adicionales.
- Consulte el [plan de desarrollo de M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para conocer los plazos de tiempo y los productos estratégicos.

> [!Note]
> Estos elementos reflejan las expectativas actuales de Microsoft sobre las funcionalidades de Intune que se publicarán en una versión futura. Las fechas y las características individuales pueden cambiar. No todos los elementos que están en desarrollo tienen una descripción de la característica en esta página.

**Fuente RSS**: para recibir notificaciones cuando esta página se actualice, copie y pegue la dirección URL siguiente en el lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure


<!-- 1905 start-->


### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Compatibilidad con la línea de base para la búsqueda de palabras clave  <!-- 3082036         -->
Al crear o editar un perfil de línea de base de seguridad, pronto se podrá usar la *búsqueda* para filtrar la configuración que se muestra en la consola.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Restablecimiento y borrado de dispositivos de forma masiva mediante Graph API <!-- 3295288 -->
Podrá restablecer y borrar hasta 100 dispositivos de forma masiva mediante Graph API.

<!-- 1904 start-->

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Los usuarios del dispositivo pueden ver todas las aplicaciones administradas que han instalado o han intentado instalar <!-- 2352913 -->
En Portal de empresa para Windows se mostrará una lista de todas las aplicaciones administradas, tanto las requeridas como las disponibles, que están instaladas en el dispositivo de un usuario. Los usuarios podrán ver las instalaciones de aplicaciones intentadas y pendientes, así como sus estados actuales. Si su organización no hace que las aplicaciones sean obligatorias o estén disponibles, los usuarios verán un mensaje en el que se explica que no se ha instalado ninguna aplicación de empresa. Los usuarios también podrán ordenar o filtrar sus aplicaciones por estado de instalación.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Uso de "reglas de aplicabilidad" al crear perfiles de configuración de dispositivo Windows 10 <!-- 2549910 -->
Puede crear perfiles de configuración de dispositivo Windows 10 (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10** como plataforma). Podrá crear una **regla de aplicabilidad** para que el perfil solo se aplique a una edición o una versión en concreto. Por ejemplo, cree un perfil que permita algunas opciones de configuración de BitLocker. Una vez que agregue el perfil, use una regla de aplicabilidad para que este solo se aplique a los dispositivos que ejecuten Windows 10 Enterprise.

Se aplica a: 
- Windows 10 y versiones posteriores



## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


