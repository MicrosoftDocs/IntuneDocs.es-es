---
title: "Descarga de la directiva de configuración de la aplicación de iOS de Skycure"
description: "Descargue la directiva de configuración de la aplicación de iOS de Skycure para usar con la aplicación de iOS de Skycure implementada para usuarios finales."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d211b876-4d3a-473c-999f-843c0a16cd22
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f452ca2305b83ee106827a7dca4b02a90910a289
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="download-skycure-ios-app-configuration-policy"></a>Descarga de la directiva de configuración de la aplicación de iOS de Skycure

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

##<a name="before-you-begin"></a>Antes de comenzar

Debe iniciar sesión en la consola de administración de Skycure para llevar a cabo los siguientes pasos.

> [!TIP] 
> Si utiliza Microsoft Internet Explorer 11 o Edge, debe abrir la consola de administración de Skycure en modo privado.

## <a name="to-download-the-ios-app-configuration-policy"></a>Para descargar la directiva de configuración de la aplicación de iOS

1.  Vaya a la [consola de administración de Skycure](https://aad.skycure.com).

2.  Escriba las **credenciales de administrador de Skycure** y, a continuación, haga clic en **Continuar**.

    ![Inicio de sesión en la consola de administración de Skycure](../media/mtp/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > El nombre de usuario de administrador de Skycure es una cuenta de correo electrónico que debe ser una cuenta válida de usuario en Azure Active Directory, de lo contrario, el inicio de sesión no se realizará. Skycure usa Azure Active Directory para autenticar que el nombre de usuario del administrador use el Inicio de sesión único (SSO).

3.  Vaya a **Configuración** &gt; **Device Management Integrations** (Integraciones de administración de dispositivos)&gt; **EMM Integration Selection** (Selección de integración de EMM), elija **Microsoft Intune** y, a continuación, guarde la selección.

2.  Haga clic en el vínculo **Archivos de configuración de integración** y guarde el archivo \*.zip generado. El archivo .zip contiene el archivo **skycure\_configuration.plist**, que se utilizará para crear la directiva de configuración de aplicación de iOS en el portal clásico de Intune.

![Archivos de configuración de Integración de Skycure](../media/mtp/skycure-ios-app-2.png)

## <a name="next-steps"></a>Pasos siguientes

[Adición de aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)
