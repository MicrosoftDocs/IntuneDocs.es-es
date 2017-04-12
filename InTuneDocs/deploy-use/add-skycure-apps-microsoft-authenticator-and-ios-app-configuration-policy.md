---
title: "Adición de aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS | Microsoft Docs"
description: "Agregue aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS en la consola clásica de Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 018d26f4-4a75-4e27-bb04-54f54106cb2f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 86fd9d7212277f9524eb4d7f225df2c7beda1313
ms.openlocfilehash: 2910bcc6b4b34da8c50899cac21d7c9ec926e9ec
ms.lasthandoff: 03/21/2017


---

# <a name="add-skycure-apps-microsoft-authenticator-app-and-ios-configuration-policy"></a>Adición de aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Debe usar Intune para agregar e implementar las aplicaciones de Skycure para que los usuarios finales puedan recibir notificaciones cuando se identifique una amenaza en sus dispositivos móviles y para recibir orientación para solucionar tales amenazas.

Además, es necesario [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) para que Azure AD pueda comprobar las identidades de los usuarios y la directiva de configuración de aplicación de iOS que le indica a la aplicación de Skycure para iOS que debe usar Intune y el inicio de sesión único (SSO) de Azure AD para que los usuarios no tengan que escribir el nombre de usuario y la contraseña cada vez que inicien sesión en la aplicación de Skycure.

## <a name="before-you-begin"></a>Antes de comenzar

-   Los pasos que se indican a continuación, deben completarse en la [consola clásica de Intune](https://manage.microsoft.com/).

-   Utilice la misma cuenta de Azure AD configurada previamente en la consola de administración de Skycure, que debe ser la misma cuenta utilizada para iniciar sesión en la consola clásica de Intune.

-   Debe tener el archivo de integración de Skycure listo para usar. Este es el archivo .zip descargado previamente desde la consola de administración de Skycure que contiene el archivo **skycure\_configuration.plist** con los parámetros de la directiva de configuración de aplicación de iOS.

-   Asegúrese de estar familiarizado con los siguientes procesos:

    -   [Agregar una aplicación en Intune](https://docs.microsoft.com/intune/deploy-use/add-apps)

    -   [Descargar una directiva de configuración de aplicación de iOS en Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)

## <a name="to-add-the-skycure-app-for-android"></a>Para agregar la aplicación de Skycure para Android

1.  En la consola clásica de Intune, elija **Aplicaciones** &gt; **Agregar aplicaciones** para iniciar el Editor de software de Intune y, a continuación, haga clic en **Siguiente**.

2.  En la página **Instalación de software**, elija **Vínculo externo**. Luego pegue la [URL de Skycure para Android](https://play.google.com/store/apps/details?id=com.skycure.skycure) en **Specify the URL** (Especificar la URL).

    ![Editor de software de Intune: Especificar la URL](../media/mtp/skycure-add-apps-1.png)

3.  En la página **Descripción del software**, escriba el **Editor**, el **Nombre** y la **Descripción** y seleccione la opción **Display this as a featured app and highlight it in the company portal** (Mostrarla como una aplicación especial y destacarla en el portal de la empresa). A continuación, haga clic en **Siguiente**.

    ![Editor de software de Intune: Descripción del software](../media/mtp/skycure-add-apps-2.png)

4.  Haga clic en **Cargar** y, luego, en **Cerrar**.

## <a name="to-add-the-skycure-app-for-ios"></a>Para agregar la aplicación de Skycure para iOS

1.  En la consola clásica de Intune, elija **Aplicaciones** &gt; **Agregar aplicaciones** para iniciar el Editor de software de Intune y, a continuación, haga clic en **Siguiente**.

2.  En la página **Instalación de software**, elija **Managed iOS App from the App Store** (Aplicación para iOS administrada desde App Store). Luego pegue la [URL de Skycure para iOS](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) en **Specify the URL** (Especificar la URL).

    ![Editor de software de Intune: Aplicación para iOS administrada](../media/mtp/skycure-add-apps-3.png)

3.  En la página **Descripción del software**, escriba el **Editor**, el **Nombre** y la **Descripción** y seleccione la opción **Display this as a featured app and highlight it in the company portal** (Mostrarla como una aplicación especial y destacarla en el portal de la empresa). A continuación, haga clic en **Siguiente**.

    ![Editor de software de Intune: Opciones](../media/mtp/skycure-add-apps-4.png)

4.  En la página **Requisitos**, seleccione la opción **Cualquiera** en **Mobile Device Type** (Tipo de dispositivo móvil) y, a continuación, haga clic en **Siguiente**.

5.  Haga clic en **Cargar** y, luego, en **Cerrar**.

## <a name="to-add-the-microsoft-authenticator-app-for-ios"></a>Para agregar la aplicación de Microsoft Authenticator para iOS

1.  En la consola clásica de Intune, elija **Aplicaciones** &gt; **Agregar aplicaciones** para iniciar el Editor de software de Intune y, a continuación, haga clic en **Siguiente**.

2.  En la página **Instalación de software**, elija **Managed iOS App from the App Store** (Aplicación para iOS administrada desde App Store). Luego pegue la [URL de la aplicación de Microsoft Authenticator para iOS](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) en **Specify the URL** (Especificar la URL).

    ![Editor de software de Intune: Aplicación para iOS administrada 2](../media/mtp/skycure-add-apps-5.png)

3.  En la página **Descripción del software**, escriba el **Editor**, el **Nombre** y la **Descripción** y seleccione la opción **Display this as a featured app and highlight it in the company portal** (Mostrarla como una aplicación especial y destacarla en el portal de la empresa). A continuación, haga clic en **Siguiente**.

    ![Editor de software de Intune: Aplicación para iOS administrada 3](../media/mtp/skycure-add-apps-6.png)

4.  En la página **Requisitos**, seleccione la opción **Cualquiera** en **Mobile Device Type** (Tipo de dispositivo móvil) y, a continuación, haga clic en **Siguiente**.

5.  Haga clic en **Cargar** y, luego, en **Cerrar**.

## <a name="to-add-the-skycure-ios-app-configuration-policy"></a>Para agregar la directiva de configuración de la aplicación de iOS de Skycure

1.  En la consola clásica de Intune, elija **Directiva** &gt; **Información general &gt; Agregar directiva**.

2.  En la lista de directivas, expanda **iOS**, elija **Directiva de configuración de aplicaciones móviles (iOS 8.0 y posteriores)** y, a continuación, elija **Crear directiva**.

    ![Directiva de configuración de aplicaciones para iOS](../media/mtp/skycure-add-apps-7.png)

3.  En la sección **General** de la página **Crear directiva**, proporcione un nombre y una descripción opcional para la directiva de configuración de aplicaciones para iOS.

    a.  Abra el archivo **skycure\_configuration.plist** con un editor de texto, como el Bloc de notas, copie el contenido y péguelo en el cuerpo de **Directiva de configuración de aplicaciones móviles**. Elija **Validar** y, luego, **Guardar directiva**.

       ![Directiva de configuración de aplicaciones para iOS 2](../media/mtp/skycure-add-apps-8.png)

## <a name="next-steps"></a>Pasos siguientes

[Implementación de aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS](https://docs.microsoft.com/intune/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)

