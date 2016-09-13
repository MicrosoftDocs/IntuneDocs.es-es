---
title: "Cómo obtienen sus aplicaciones los usuarios de iOS | Microsoft Intune"
description: "Métodos para hacer que las aplicaciones iOS estén disponibles para los usuarios finales"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9f1946c02c6267a22844106e8f72555ec5e9cabb
ms.openlocfilehash: 212dcd31697180dae61569dda13b56704a079bf4


---


# Cómo obtienen sus aplicaciones los usuarios de iOS

Lea esta información para comprender cómo y dónde obtienen los usuarios finales las aplicaciones que se distribuyen a través de Microsoft Intune.

**Aplicaciones obligatorias**: son las aplicaciones que exige el administrador y que se instalan en el dispositivo con intervención mínima del usuario, según la plataforma.

**Aplicaciones disponibles**: son las aplicaciones que se proporcionan en la lista de aplicaciones de portal de empresa y que un usuario puede instalar si quiere.

**Aplicaciones administradas**: son aplicaciones que se pueden administrar mediante directivas y que están “encapsuladas” con Intune o se han creado con el kit de desarrollo de software (SDK) de administración de aplicaciones móviles (MAM) de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de aplicación pueden aplicarse a estas.

**Aplicaciones no administradas**: son aplicaciones que se pueden administrar mediante directivas y que no están encapsuladas con Intune o no incorporan el SDK de MAM de Intune. Las directivas de aplicación no pueden aplicarse a estas aplicaciones.

Las restricciones de Apple prohíben que se muestren la línea de negocio y las aplicaciones de la tienda de aplicaciones administrada en la aplicación de portal de empresa de la tienda, lo que significa que los usuarios tienen que visitar vistas diferentes para encontrar todas sus aplicaciones. Las aplicaciones para cada icono que se muestran en la página Aplicaciones del portal de empresa están disponibles de la siguiente manera:

- El icono **Aplicaciones de empresa** apunta a una lista de todas las aplicaciones en la pestaña **TODOS** del [sitio web del portal de empresa](http://portal.manage.microsoft.com).

- El icono **Otras aplicaciones** apunta actualmente a una vista, dentro de la aplicación de portal de empresa, que enumera todas las aplicaciones que Apple permite mostrar a la aplicación de portal de empresa. Esto incluye todas las aplicaciones excepto las aplicaciones de la tienda de aplicaciones administradas y de la línea de negocio.

- El icono **Categorías** apunta actualmente a una vista, dentro del portal de empresa, que enumera las categorías de aplicaciones.

    ![ios-how-to-sync-device-with-intune](./media/ios-sync-comp-portal-apps.png)


###Consulte también
[Cómo obtienen sus aplicaciones los usuarios de Android](how-your-android-users-get-their-apps.md)</br>
[Cómo obtienen sus aplicaciones los usuarios de Windows](how-your-windows-users-get-their-apps.md)



<!--HONumber=Aug16_HO4-->


