---
title: "Inscribir dispositivos móviles de evaluación | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 9755499575118feecf33780ee29a70525f95508e
ms.openlocfilehash: f26b64015f483eb5b6a6efbaa6fe6730dde7dac9


---

# Inscribir dispositivos móviles de evaluación e instalar una aplicación
Para configurar la administración de dispositivos móviles con Intune, primero debe establecer la entidad de administración de dispositivos móviles, habilitar la administración de plataformas de dispositivos e inscribir sus dispositivos con la aplicación del Portal de empresa. Posteriormente, puede implementar la aplicación Microsoft Skype que publicó.

## Preparar el servicio para la administración de dispositivos

1.  **Convertir Intune en su entidad de administración de dispositivos móviles**

    En la [consola de administración de Intune](https://manage.microsoft.com/), elija **Administrador** &gt; **Administración de dispositivos móviles**. Elija **Tareas** > **Establecer entidad de MDM** y, después, elija **Sí** en el cuadro de diálogo **Entidad de MDM**.

2.  **Habilitación de MDM para su plataforma de dispositivo**

    Habilitación de la administración de dispositivos móviles para la plataforma de dispositivo que desea administrar. Los requisitos necesarios varían según la plataforma:

    -   **iOS y Mac OS X**: vea [Set up iOS and Mac management with Microsoft Intune (Configurar la administración de iOS y Mac con Microsoft Intune)](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune).

    -   **Android**: los dispositivos móviles de Android permiten a los usuarios inscribirse mediante la aplicación de Portal de empresa disponible en Google Play. No se requiere ninguna configuración adicional en Intune.

    -   **Windows Phone**: vea [Set up Windows Phone management with Microsoft Intune (Configurar la administración de Windows Phone con Microsoft Intune)](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune).

## Inscribir dispositivos de prueba

### iOS y Mac OS X
Instale la aplicación **Portal de empresa de Microsoft Intune** de Microsoft Corporation disponible en la Tienda de aplicaciones e inicie sesión con las credenciales de usuario de Intune agregadas anteriormente. Consulte **Dispositivos inscritos** para agregar el dispositivo.

### Android
Instale la aplicación **Portal de empresa de Intune** de Microsoft Corporation, disponible en [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) e inicie sesión con las credenciales de usuario de Intune agregadas anteriormente.

### Windows Phone 8,1
Los usuarios deben instalar la aplicación **Portal de empresa** de Microsoft Corporation disponible en la Tienda de Windows Phone e iniciar sesión con las credenciales de usuario de Intune agregadas anteriormente.  Consulte **Dispositivos inscritos** para agregar el dispositivo.

 ### Windows Phone 8.0
 Los usuarios deben hacer clic en **configuración del sistema** &gt; **aplicaciones de empresa** e iniciar sesión con las credenciales de usuario de Intune agregadas anteriormente. La aplicación Portal de empresa se implementa en el teléfono.

Si se le pide una **dirección de servidor**, escriba “manage.microsoft.com”.


## Instalar la aplicación implementada anteriormente
Abra el Portal de empresa en el dispositivo móvil, elija **Aplicaciones** y, luego, instale **Microsoft Skype**.

Para más información sobre la administración de dispositivos móviles mediante Intune, vea [Get ready to enroll devices in Microsoft Intune (Preparar la inscripción de dispositivos en Microsoft Intune)](/Intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune).

### Pasos siguientes
Enhorabuena. Acaba de completar el paso 5 del tutorial de *evaluación de Microsoft Intune*.

>[!div class="step-by-step"]

>[!div class="step-by-step"]  



<!--HONumber=Jun16_HO4-->


