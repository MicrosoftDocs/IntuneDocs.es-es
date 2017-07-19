---
title: "Configuración de filtro de contenido web de Intune para dispositivos iOS"
titleSuffix: Intune on Azure
description: "Obtenga información sobre la configuración que puede usar para permitir y bloquear el acceso a sitios web desde dispositivos iOS\"."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 7/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16aa0f3c-8977-4495-9fbe-ca30ad278c9e
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1fb2ce8ed9db6ff808cac2ee8ff46ee865dbdf35
ms.sourcegitcommit: c9b3a95bf529b6cb2a2bdacbc49127dfa0c233e5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2017
---
# <a name="web-content-filter-settings-for-ios-devices"></a>Configuración de filtro de contenido web para dispositivos iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use estos valores para configurar las direcciones URL que los usuarios finales de los exploradores web pueden o no visitar en dispositivos iOS. Hay dos métodos que puede usar para configurar direcciones URL:

- **Configurar direcciones URL**: use el filtro web integrado de Apple que busca términos para adultos, como lenguaje obsceno o sexualmente explícito. Esta función evalúa cada página web a medida que se carga e intenta identificar y bloquear contenido inadecuado. También puede configurar direcciones URL que el filtro no revisa, o bien direcciones URL para que estén bloqueadas, independientemente de la configuración del filtro.

- **Solo sitios web específicos** (solo para el explorador web Safari): estas direcciones URL se agregan a los marcadores del explorador Safari. El usuario **solo** puede visitar estos sitios; no puede tener acceso a ningún otro sitio. Use esta opción solo si conoce la lista exacta de direcciones URL a las que pueden acceder los usuarios.
Si no especifica ninguna dirección URL, los usuarios finales no pueden acceder a ningún sitio web, excepto microsoft.com, microsoft.net y apple.com.



## <a name="get-started"></a>Introducción

1. En la hoja Características del dispositivo, pulse **Filtro de contenido web (solo supervisado)**.
2. En la hoja **Filtro de contenido web**, elija el **tipo de filtro** desde donde desea configurar:
    - **No configurado**: no se realiza ningún filtrado.
    - **Configurar direcciones URL**
    - **Solo sitios web específicos**
3. Después, según el tipo de filtro que use, use uno de los siguientes procedimientos:


## <a name="configure-urls"></a>Configurar direcciones URL

1. En la hoja **Filtro de contenido web**, seleccione una de las siguientes opciones si es necesario:
    - **Direcciones URL permitidas**: en la hoja **Direcciones URL permitidas**, escriba las direcciones URL que desea permitir (omitiendo el filtro web de Apple) y elija Entrar después de cada una.
    - **Direcciones URL bloqueadas**: en la hoja **Direcciones URL bloqueadas**, escriba las direcciones URL que desea bloquear (independientemente de la configuración de filtro web de Apple) y elija Entrar después de cada una.
2. Cuando haya terminado, haga clic en **Aceptar**.


## <a name="specific-websites-only"></a>Solo sitios web específicos

1. En la hoja **Filtro de contenido web**, configure las siguientes opciones para cada sitio web que quiera permitir:
    - **Dirección URL**: escriba la dirección URL del sitio web que desea permitir, por ejemplo, **http://www.contoso.com**.
    - **Ruta de acceso de marcador**: escriba la ruta de acceso al lugar donde desea almacenar el marcador, por ejemplo, **/Contoso/Business Apps**. Si no agrega una ruta de acceso, el marcador se agregará a la carpeta predeterminada de marcadores del dispositivo.
    - **Título**: escriba un título descriptivo para el marcador.
2. Haga clic en **Agregar** después de escribir la información de cada sitio web.
3. Cuando haya terminado, haga clic en **Aceptar**.

>[!IMPORTANT] 
> Intune permite automáticamente las siguientes direcciones URL.
> - www.microsoft.com
> - www.microsoft.net
> - www.apple.com

## <a name="finish-up"></a>Finalizar

Elija **Aceptar** para volver a la hoja **Crear perfil** y, luego, elija **Crear**.

## <a name="next-steps"></a>Pasos siguientes

Ahora puede asignar el perfil de dispositivo a los grupos que elija. Para obtener más información, vea [Asignación de perfiles de dispositivo](device-profile-assign.md).
