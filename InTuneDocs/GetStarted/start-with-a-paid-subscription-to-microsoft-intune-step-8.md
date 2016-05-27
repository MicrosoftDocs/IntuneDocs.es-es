---
# required metadata

title: Inscripción de dispositivos móviles e instalación de una aplicación | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscripción de dispositivos móviles e instalación de una aplicación
Para configurar la administración de dispositivos móviles con Intune, primero debe establecer la entidad de administración de dispositivos móviles, habilitar la administración de plataformas de dispositivos e inscribir sus dispositivos con la aplicación del portal de empresa. Posteriormente, puede implementar la aplicación Microsoft Skype que publicó en el paso 6.

## Habilitar la administración de dispositivos e inscribir dispositivos

1.  **Convertir Intune en su entidad de administración de dispositivos móviles**
    En la [consola de administración de Intune](https://manage.microsoft.com/), elija **Administración** > **Administración de dispositivos móviles** y **Establecer entidad de MDM** en **Tareas**.  Elija **Sí** en el cuadro de diálogo Entidad de MDM.
    ![Consola de administración. Establecer MDM en Intune](./media/mdmAuthority.png)

2.  **Habilitación de MDM para su plataforma de dispositivo**
    Habilitación de la administración de dispositivos móviles para la plataforma de dispositivo que desea administrar. Los requisitos necesarios varían según la plataforma:

    -   **iOS y Mac OS X**: vea [Set up iOS and Mac management with Microsoft Intune](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) (Configurar la administración de iOS y Mac con Microsoft Intune)..

    -   **Windows Phone**: vea [Set up Windows Phone management with Microsoft Intune](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) (Configurar la administración de Windows Phone con Microsoft Intune)..

    -   **Android**: los dispositivos móviles Android permiten a los usuarios inscribirse mediante la aplicación de portal de empresa disponible en [Google Play](https://play.google.com/store/apps/details?id=com.skype.raider). No se requiere ninguna configuración adicional en Intune.

3.  **Inscribir dispositivos**:

    -   **Android**: instale la aplicación **Portal de empresa de Intune** de Microsoft Corporation, disponible en [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612), e inicie sesión con las credenciales de usuario de Intune agregadas anteriormente.

    -   **iOS y Mac OS X**: instale la aplicación **Portal de empresa de Microsoft Intune** de Microsoft Corporation, disponible en la Tienda de aplicaciones, e inicie sesión con las credenciales de usuario de Intune agregadas anteriormente. Consulte **Dispositivos inscritos** para agregar el dispositivo.

    -   **Windows Phone 8.1**: los usuarios deben instalar la aplicación **Portal de empresa** de Microsoft Corporation disponible en la Tienda de Windows Phone e iniciar sesión con las credenciales de usuario de Intune agregadas anteriormente.  Consulte **Dispositivos inscritos** para agregar el dispositivo.

    -   **Windows Phone 8.0**: los usuarios deben elegir **Configuración del sistema** &gt; **Aplicaciones de empresa** e iniciar sesión usando las credenciales de usuario de Intune agregadas anteriormente. La aplicación de portal de empresa se implementa en el teléfono.

    Si se le pide una **dirección de servidor**, escriba “manage.microsoft.com”.

## Instalar una aplicación en un dispositivo inscrito
En el [paso 6](start-with-a-paid-subscription-to-microsoft-intune-step-6.md) de esta guía de inicio rápido, publicó la aplicación Skype en el grupo de usuarios de Intune personalizado. Ahora instalará dicha aplicación en un dispositivo recién inscrito.

Abra el portal de empresa en el dispositivo móvil inscrito, seleccione **Aplicaciones** e instale **Microsoft Skype**..

Para más información sobre la administración de dispositivos móviles mediante [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], vea [Get ready to enroll devices in Microsoft Intune](/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) (Preparar la inscripción de dispositivos en Microsoft Intune)..


### Pasos siguientes
Enhorabuena. Acaba de completar el último paso de la *Guía de inicio rápido de Intune*. Ahora que ha finalizado la configuración inicial, puede habilitar funciones de MDM adicionales.

>[!div class="step-by-step"]

>[&larr; **Inscribir dispositivos**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**Tareas posteriores a la configuración** &rarr;](.\post-configuration-tasks.md)  


<!--HONumber=May16_HO1-->


