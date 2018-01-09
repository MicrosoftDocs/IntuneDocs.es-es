---
title: "Descarga de la directiva de configuración de la aplicación de iOS de Skycure para usarla con Intune"
titlesuffix: Azure portal
description: "Descarga de la directiva de configuración de la aplicación de iOS de Skycure para usarla con Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1bdc2ecf-32d0-4b6a-80b4-dbcdb9909010
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cbf26b44725f1fa08fbc6766f0560fe91d63d6ca
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/30/2017
---
# <a name="download-skycure-ios-app-configuration-policy"></a>Descarga de la directiva de configuración de la aplicación de iOS de Skycure

## <a name="before-you-begin"></a>Antes de comenzar

Debe iniciar sesión en la consola de administración de Skycure para llevar a cabo los siguientes pasos.

> [!TIP] 
> Si utiliza Microsoft Internet Explorer 11 o Edge, debe abrir la consola de administración de Skycure en modo privado.

## <a name="to-download-the-ios-app-configuration-policy"></a>Para descargar la directiva de configuración de la aplicación de iOS

1.  Vaya a la [consola de administración de Skycure](https://aad.skycure.com).

2.  Escriba las **credenciales de administrador de Skycure** y, a continuación, haga clic en **Continuar**.

    ![Inicio de sesión en la consola de administración de Skycure](./media/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > El nombre de usuario de administrador de Skycure es una cuenta de correo electrónico que debe ser una cuenta válida de usuario en Azure Active Directory, de lo contrario, el inicio de sesión no se realizará. Skycure usa Azure Active Directory para autenticar que el nombre de usuario del administrador use el Inicio de sesión único (SSO).

3.  Vaya a **Configuración** &gt; **Device Management Integrations** (Integraciones de administración de dispositivos)&gt; **EMM Integration Selection** (Selección de integración de EMM), elija **Microsoft Intune** y, a continuación, guarde la selección.

4.  Haga clic en el vínculo **Archivos de configuración de integración** y guarde el archivo \*.zip generado. El archivo .zip contiene el archivo **skycure\_configuration.plist**, que se utilizará para crear la directiva de configuración de aplicación de iOS en el portal clásico de Intune.

![Archivos de configuración de Integración de Skycure](./media/skycure-ios-app-2.png)

## <a name="next-steps"></a>Pasos siguientes

[Agregar y asignar aplicaciones de Skycure, la aplicación de Microsoft Authenticator y la directiva de configuración de iOS](mtd-apps-ios-app-configuration-policy-add-assign.md)
