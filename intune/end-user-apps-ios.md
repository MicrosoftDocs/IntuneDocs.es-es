---
title: Cómo obtienen sus aplicaciones los usuarios de iOS
description: Métodos para hacer que las aplicaciones iOS estén disponibles para los usuarios finales
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/28/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7744d8422e774242e0883c8d77814c42fd71895f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31023162"
---
# <a name="how-your-ios-users-get-their-apps"></a>Cómo obtienen sus aplicaciones los usuarios de iOS

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Lea esta información para comprender cómo y dónde obtienen los usuarios finales las aplicaciones que se distribuyen a través de Microsoft Intune.

**Aplicaciones obligatorias**: son las aplicaciones que exige el administrador y que se instalan en el dispositivo con intervención mínima del usuario, según la plataforma.

**Aplicaciones disponibles**: son las aplicaciones que se proporcionan en la lista de aplicaciones de portal de empresa y que un usuario puede instalar si quiere.

**Aplicaciones administradas**: son aplicaciones que se pueden administrar mediante directivas y que se han "encapsulado" con Intune o se han creado con el kit de desarrollo de software (SDK) para aplicaciones de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de protección de aplicaciones pueden aplicarse a estas.

**Aplicaciones no administradas**: son aplicaciones que se pueden administrar mediante directivas y que no están encapsuladas con Intune o no incorporan el SDK de aplicaciones de Intune. Las directivas de aplicación no pueden aplicarse a estas aplicaciones.

Las restricciones de Apple prohíben que las aplicaciones de la tienda de aplicaciones de línea de negocio y administradas aparezcan en la aplicación Portal de empresa. Para solucionar este problema, los iconos de la aplicación Portal de empresa para iOS apuntan a los usuarios a distintas vistas de una única ubicación (el sitio web de Portal de empresa) para todas sus aplicaciones.

Los usuarios inscritos obtienen sus aplicaciones tocando en los iconos siguientes de la pantalla de aplicaciones de la aplicación del Portal de empresa:

- **Todas las aplicaciones** apunta a una lista de todas las aplicaciones en la pestaña TODO del [sitio web del Portal de empresa](https://portal.manage.microsoft.com).

- **Las aplicaciones destacadas** llevarán a los usuarios a la pestaña DESTACADOS del sitio web del Portal de empresa.

- **Categorías** apunta a la pestaña CATEGORÍAS del sitio web del Portal de empresa.


![Pantalla de aplicaciones del Portal de empresa de iOS](./media/ios-cp-app-main-apps-screen.png)

Para más información sobre cómo agregar aplicaciones, vea [Agregar una aplicación a Microsoft Intune](apps-add.md).

### <a name="see-also"></a>Vea también
[Cómo obtienen sus aplicaciones los usuarios de Android](end-user-apps-android.md)

[Cómo obtienen sus aplicaciones los usuarios de Windows](end-user-apps-windows.md)
