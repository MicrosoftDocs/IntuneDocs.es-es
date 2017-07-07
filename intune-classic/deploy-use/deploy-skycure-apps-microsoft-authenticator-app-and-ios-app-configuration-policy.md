---
title: "Implementación de aplicaciones de Skycure, de la aplicación Microsoft Authenticator y de la directiva de configuración de iOS"
description: "Implemente aplicaciones de Skycure, aplicación de Microsoft Authenticator y directiva de configuración de iOS en la consola clásica de Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45826fbc-6df5-41b2-8e80-d1353f904b43
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 60f4ab5a656a2e253d82971d7bea6b3a6c9eb25a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>Implementación de aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>Antes de comenzar

-   Los pasos que se indican a continuación, deben completarse en la [consola clásica de Intune](https://manage.microsoft.com/).

-   Utilice la misma cuenta de Azure AD configurada previamente en la consola de administración de Skycure, que debe ser la misma cuenta utilizada para iniciar sesión en la consola clásica de Intune.

-   Asegúrese de estar familiarizado con los siguientes procesos:

    -   [Implementar una aplicación con Intune](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)

    -   [Descargar directiva de configuración de aplicaciones iOS](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>Para implementar aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS

1.  En la consola clásica de Intune, elija **Aplicaciones** &gt; **Aplicaciones** para ver la lista de aplicaciones que puede administrar.

2.  Seleccione las siguientes aplicaciones:

    a.  Microsoft Authenticator

    b.  Aplicación de Skycure para Android

    c.  Aplicación de Skycure para iOS

       ![Consola clásica de Intune: todas las aplicaciones para implementar](../media/mtp/skycure-deploy-app-1.png)

3.  Elija **Manage Deployments** (Administrar implementaciones), seleccione el grupo de seguridad de Azure AD que tiene los usuarios Skycure y, a continuación, haga clic en **Siguiente**.

4.  En la página **Acción de implementación**, seleccione la opción **Required Install** (Instalación solicitada) en la lista desplegable **Aprobación** y, a continuación, haga clic en **Siguiente**.

    ![Consola clásica de Intune: acción de implementación](../media/mtp/skycure-deploy-app-2.png)

5.  En la página **Perfil de VPN**, seleccione la opción **Ninguna** de la lista desplegable **Directiva de VPN** y, a continuación, haga clic en **Siguiente**.

6.  En la página **Mobile App Configuration** (Configuración de aplicación móvil), seleccione la directiva de configuración de la aplicación de iOS que se creó anteriormente en la lista desplegable **Directiva de configuración de la aplicación** y, a continuación, haga clic en **Finalizar**.

    ![Consola clásica de Intune: configuración de la aplicación móvil](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>Pasos siguientes

[Configuración de la integración de Skycure con Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)
