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
ms.sourcegitcommit: 37841027c7ae040163440a19f9e163fb4eb87233
ms.openlocfilehash: ad780fb3403f6caaee1218d785a5cad326c18df5


---


# Cómo obtienen sus aplicaciones los usuarios de iOS

Lea esta información para comprender cómo y dónde obtienen los usuarios finales las aplicaciones que se distribuyen a través de Microsoft Intune.

**Aplicaciones obligatorias**: son las aplicaciones que exige el administrador y que se instalan en el dispositivo con intervención mínima del usuario, según la plataforma.

**Aplicaciones disponibles**: son las aplicaciones que se proporcionan en la lista de aplicaciones de portal de empresa y que un usuario puede instalar si quiere.

**Aplicaciones administradas**: son aplicaciones que se pueden administrar mediante directivas y que están “encapsuladas” con Intune o se han creado con el kit de desarrollo de software (SDK) de administración de aplicaciones móviles (MAM) de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de aplicación pueden aplicarse a estas.

**Aplicaciones no administradas**: son aplicaciones que se pueden administrar mediante directivas y que no están encapsuladas con Intune o no incorporan el SDK de MAM de Intune. Las directivas de aplicación no pueden aplicarse a estas aplicaciones.

Las restricciones de Apple prohíben que las aplicaciones de la tienda de aplicaciones de línea de negocio y administradas aparezcan en la aplicación Portal de empresa. Para solucionar este problema, los iconos de la aplicación Portal de empresa para iOS apuntan a los usuarios a distintas vistas de una única ubicación (el sitio web de Portal de empresa) para todas sus aplicaciones.

- **Aplicaciones de la empresa** anteriormente apuntaba a una lista de todas las aplicaciones de la pestaña TODAS del [sitio web de Portal de empresa](http://portal.manage.microsoft.com), y seguirá funcionando del mismo modo. El nombre del icono ha cambiado a **Todas las aplicaciones**.

- **Otras aplicaciones** antes apuntaba a una vista, dentro de la aplicación de portal de empresa, que enumera todas las aplicaciones que Apple permite mostrar a la aplicación de portal de empresa. El nombre del icono ha cambiado a **Aplicaciones destacadas** y, si pulsa en él, se le dirigirá a la pestaña Destacadas del sitio web de portal de empresa.

-  **Categorías** anteriormente apuntaba a una vista, dentro de la aplicación de portal de empresa, que enumera las categorías de aplicaciones. El nombre del icono no ha cambiado, pero ahora apunta a la pestaña Categorías del sitio web de portal de empresa.
Puede encontrar capturas de pantalla actualizadas en [Mejoras en cómo los usuarios finales de iOS obtienen sus aplicaciones](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).



### Consulte también
[Cómo obtienen sus aplicaciones los usuarios de Android](how-your-android-users-get-their-apps.md)

[Cómo obtienen sus aplicaciones los usuarios de Windows](how-your-windows-users-get-their-apps.md)



<!--HONumber=Oct16_HO2-->


