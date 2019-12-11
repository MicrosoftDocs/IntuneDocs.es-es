---
title: Cómo obtienen sus aplicaciones los usuarios de iOS
description: Métodos para hacer que las aplicaciones iOS estén disponibles para los usuarios finales
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 06cc977ce8b0b892e1020436f89ada4a40bac3f2
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73413994"
---
# <a name="how-your-ios-users-get-their-apps"></a>Cómo obtienen sus aplicaciones los usuarios de iOS

Lea esta información para comprender cómo y dónde obtienen los usuarios finales las aplicaciones que se distribuyen a través de Microsoft Intune.

**Aplicaciones obligatorias**: son las aplicaciones que exige el administrador y que se instalan en el dispositivo con intervención mínima del usuario, según la plataforma.

**Aplicaciones disponibles**: son las aplicaciones que se proporcionan en la lista de aplicaciones de portal de empresa y que un usuario puede instalar si quiere.

**Aplicaciones administradas**: son aplicaciones que se pueden administrar mediante directivas y que se han "encapsulado" con Intune o se han creado con el kit de desarrollo de software (SDK) para aplicaciones de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de protección de aplicaciones pueden aplicarse a estas.

**Aplicaciones no administradas**: las aplicaciones que los usuarios pueden descargar desde el App Store de iOS que no están integradas con el SDK para aplicaciones de Intune. Intune no tiene ningún control sobre la distribución, la administración o el borrado selectivo de estas aplicaciones.  

Las restricciones de Apple prohíben que las aplicaciones de la tienda de aplicaciones de línea de negocio y administradas aparezcan en la aplicación Portal de empresa. Para solucionar este problema, los iconos de la aplicación Portal de empresa para iOS apuntan a los usuarios a distintas vistas de una única ubicación (el sitio web de Portal de empresa) para todas sus aplicaciones.

Los usuarios inscritos obtienen sus aplicaciones tocando en los iconos siguientes de la pantalla de aplicaciones de la aplicación del Portal de empresa:

- **Todas las aplicaciones** apunta a una lista de todas las aplicaciones en la pestaña TODO del [sitio web del Portal de empresa](https://portal.manage.microsoft.com).

- **Las aplicaciones destacadas** llevarán a los usuarios a la pestaña DESTACADOS del sitio web del Portal de empresa.

- **Categorías** apunta a la pestaña CATEGORÍAS del sitio web del Portal de empresa.

![Pantalla de aplicaciones del Portal de empresa de iOS](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

Para más información sobre cómo agregar aplicaciones, vea [Agregar una aplicación a Microsoft Intune](../apps/apps-add.md).

## <a name="see-also"></a>Consulte también

[Cómo obtienen sus aplicaciones los usuarios de Android](end-user-apps-android.md)

[Cómo obtienen sus aplicaciones los usuarios de Windows](end-user-apps-windows.md)
