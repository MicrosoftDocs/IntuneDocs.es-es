---
title: Configuración de filtro de contenido web de Microsoft Intune para dispositivos iOS
titlesuffix: ''
description: Obtenga información sobre la configuración de Microsoft Intune que puede usar para permitir y bloquear el acceso a sitios web desde dispositivos que ejecutan iOS.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c5e3dbdc339fd25289e1aed526bc03e4691c3812
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="web-content-filter-settings-for-ios-devices"></a>Configuración de filtro de contenido web para dispositivos iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestra la configuración de Microsoft Intune que puede usar para controlar el acceso a direcciones URL del explorador desde dispositivos que ejecutan iOS.

Hay dos métodos distintos para configurar las URL:

- **Configurar direcciones URL**: use el filtro web integrado de Apple que busca términos para adultos, como lenguaje obsceno o sexualmente explícito. Esta función evalúa cada página web a medida que se carga e intenta identificar y bloquear contenido inadecuado. También puede configurar direcciones URL que el filtro no revisa, o bien direcciones URL para que estén bloqueadas, independientemente de la configuración del filtro.

- **Solo sitios web específicos** (solo para el explorador web Safari): estas direcciones URL se agregan a los marcadores del explorador Safari. El usuario **solo** puede visitar estos sitios; no puede tener acceso a ningún otro sitio. Use esta opción solo si conoce la lista exacta de direcciones URL a las que pueden acceder los usuarios.
Si no especifica ninguna dirección URL, los usuarios finales no pueden acceder a ningún sitio web, excepto microsoft.com, microsoft.net y apple.com.

## <a name="get-started"></a>Introducción

1. En la página Características del dispositivo, elija **Filtro de contenido web (solo supervisados)**.
2. En la página **Filtro de contenido web**, elija el **Tipo de filtro** desde donde quiere configurar:
    - **No configurado**: no se realiza ningún filtrado.
    - **Configurar direcciones URL**
    - **Solo sitios web específicos**
3. Después, según el tipo de filtro que use, use uno de los siguientes procedimientos:


## <a name="configure-urls"></a>Configurar direcciones URL

1. En la página **Filtro de contenido web**, seleccione uno de los siguientes valores si es necesario:
   - **URL permitidas**: en la página **URL permitidas**, escriba las URL que quiere permitir (omitiendo el filtro web de Apple) y presione Entrar después de cada una.
     > [!NOTE]
     > Las direcciones URL que especifique aquí son las que no quiere que estén sujetas al filtro web de Apple. Estas direcciones URL no representan una lista de los únicos sitios web permitidos. Si eso es lo que quiere, use **Solo sitios web específicos**.

   - **URL bloqueadas**: en la página **URL bloqueadas**, escriba las URL que quiere bloquear (independientemente de la configuración de filtro web de Apple) y presione Entrar después de cada una.
2. Cuando haya terminado, haga clic en **Aceptar**.


## <a name="specific-websites-only"></a>Solo sitios web específicos

1. En el panel **Filtro de contenido web**, configure las siguientes opciones para cada sitio web que quiera permitir:
    - **Dirección URL**: escriba la dirección URL del sitio web que quiere permitir, por ejemplo, **http://www.contoso.com**.
    - **Ruta de acceso de marcador**: escriba la ruta de acceso al lugar donde desea almacenar el marcador, por ejemplo, **/Contoso/Business Apps**. Si no agrega una ruta de acceso, el marcador se agregará a la carpeta predeterminada de marcadores del dispositivo.
    - **Título**: escriba un título descriptivo para el marcador.
2. Haga clic en **Agregar** después de escribir la información de cada sitio web.
3. Cuando haya terminado, haga clic en **Aceptar**.

> [!IMPORTANT]
> Intune permite automáticamente las siguientes direcciones URL.
> - www.microsoft.com
> - www.microsoft.net
> - www.apple.com

## <a name="finish-up"></a>Finalizar

Elija **Aceptar** para volver al panel **Crear perfil** y, luego, seleccione **Crear**.

## <a name="next-steps"></a>Pasos siguientes

Ahora puede asignar el perfil de dispositivo a los grupos que elija. Para obtener más información, vea [Asignación de perfiles de dispositivo](device-profile-assign.md).
