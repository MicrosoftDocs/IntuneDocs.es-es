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
ms.sourcegitcommit: 52b9e786fe22b04081441db88a3629062fc85668
ms.openlocfilehash: a215d547507dcc460e83009cc6a04baf3fd8f4a4


---


# Cómo obtienen sus aplicaciones los usuarios de iOS

Lea esta información para comprender cómo y dónde obtienen los usuarios finales las aplicaciones que se distribuyen a través de Microsoft Intune.

**Aplicaciones obligatorias**: son las aplicaciones que exige el administrador y que se instalan en el dispositivo con intervención mínima del usuario, según la plataforma.

**Aplicaciones disponibles**: son las aplicaciones que se proporcionan en la lista de aplicaciones de portal de empresa y que un usuario puede instalar si quiere.

**Aplicaciones administradas**: son aplicaciones que se pueden administrar mediante directivas y que están “encapsuladas” con Intune o se han creado con el kit de desarrollo de software (SDK) de administración de aplicaciones móviles (MAM) de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de aplicación pueden aplicarse a estas.

**Aplicaciones no administradas**: son aplicaciones que se pueden administrar mediante directivas y que no están encapsuladas con Intune o no incorporan el SDK de MAM de Intune. Las directivas de aplicación no pueden aplicarse a estas aplicaciones.

Las restricciones de Apple prohíben que las aplicaciones de la tienda de aplicaciones de línea de negocio y administradas aparezcan en la aplicación Portal de empresa. Para solucionar este problema, los iconos de aplicaciones de la aplicación Portal de empresa para iOS apuntan a los usuarios a distintas vistas de una única ubicación (el sitio web de Portal de empresa) para todas sus aplicaciones, del siguiente modo:

- El icono **Aplicaciones de la empresa** anteriormente apuntaba a una lista de todas las aplicaciones de la pestaña TODAS del [sitio web de Portal de empresa](http://portal.manage.microsoft.com) y seguirá funcionando del mismo modo. El nombre del icono ha cambiado a **Todas las aplicaciones**.

- El icono **Otras aplicaciones** antes apuntaba a una vista, dentro de la aplicación Portal de empresa, que enumera todas las aplicaciones que Apple permite mostrar a la aplicación Portal de empresa. El nombre del icono ha cambiado a **Aplicaciones destacadas** y, si pulsa en él, se le dirigirá a la pestaña DESTACADAS del sitio web de Portal de empresa.

-  El icono **Categorías** anteriormente apuntaba a una vista, dentro de la aplicación Portal de empresa, que enumera las categorías de aplicaciones. El nombre del icono no ha cambiado, pero ahora apunta a la pestaña CATEGORÍAS del sitio web de Portal de empresa.
Puede encontrar las capturas de pantalla actualizadas [aquí](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).



###Consulte también
[Cómo obtienen sus aplicaciones los usuarios de Android](how-your-android-users-get-their-apps.md)</br>
[Cómo obtienen sus aplicaciones los usuarios de Windows](how-your-windows-users-get-their-apps.md)



<!--HONumber=Sep16_HO3-->


