---
title: "Elegir cómo inscribir dispositivos móviles | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 06/06/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
translationtype: Human Translation
ms.sourcegitcommit: f1dc713099c982d6e32c87b814dd3f55b1656eda
ms.openlocfilehash: 5668a4d8a6cce15446201926b03d71ede174a299


---

# Elegir cómo inscribir dispositivos móviles

La inscripción de dispositivos móviles es un proceso en el que los smartphones, las tabletas y los equipos se incorporan a la administración de Microsoft Intune. Como administrador, su tarea consiste en averiguar cuál es la mejor forma de inscribir dispositivos a partir de los siguientes aspectos:

 -  Propiedad (personal o de la empresa)
 -  Uso (compartido o personal)
 -  Plataforma (iOS, Android, Windows Phone, PC Windows o PC Mac): seleccionada mediante el método de inscripción

Las respuestas a las siguientes preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos bajo su administración.

## **¿Los empleados traen sus propios dispositivos o se los proporciona la organización?**

  **Los dispositivos propiedad de los usuarios**, también conocidos por la inscripción "Bring your own device" (BYOD), permiten a los usuarios inscribir sus dispositivos para tener acceso a recursos de la empresa como el correo electrónico, aplicaciones de la empresa, datos de la empresa y soporte técnico. **Los dispositivos propiedad de la empresa** (COD) los proporciona la organización a sus empleados para resolver una necesidad empresarial.
  > [!div class="button"]
  [Inscripción BYOD >](#byod-device-enrollment)   [Inscripción COD >](#cod-device-enrollment)

### Inscripción de dispositivos BYOD

La inscripción BYOD requiere que los usuarios instalen la aplicación del Portal de empresa de Intune en sus dispositivos. Después pueden iniciar la aplicación e inscribirse al proporcionar sus credenciales profesionales o educativas. El Intune proporcionado encuentra una licencia para esas credenciales, el dispositivo se agrega a la consola de administración de Intune y recibe la directiva de Intune, lo que le concede acceso a recursos de la empresa.

**Seleccionar el tipo de dispositivo:**
> [!div class="button"]
[Android](..deploy-use/set-up-android-management-with-microsoft-intune) [iOS y Mac](..deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile y Window Phone](..deploy-use/set-up-windows-phone-management-with-microsoft-intune) [equipos PC Windows](..deploy-use/set-up-windows-device-management-with-microsoft-intune)


### Inscripción de dispositivos COD

Los dispositivos propiedad de la empresa (COD) se pueden inscribir para admitir un usuario dedicado o compartido entre muchos usuarios.  **Los dispositivos compartidos** no tienen un único usuario y no suelen estar configurados para obtener acceso al correo electrónico. Ejemplos de esto son los dispositivos de pantalla completa o los dispositivos orientados a tareas que los usuarios eligen de un grupo cuando lo necesitan y, luego, lo devuelven. Los métodos de inscripción recomendados dependerán de la plataforma de los dispositivos. **Los dispositivos dedicados** están destinados a usuarios individuales, deben someterse a un seguimiento como activos de la empresa y, al mismo tiempo, dejar que los usuarios puedan tener acceso a los datos y al correo como si se tratara de dispositivos personalizados. Los métodos de inscripción recomendados dependerán de la plataforma de los dispositivos. [Siguiente pregunta...](Are your company-owned devices shared or do they have dedicated users?)

## **¿Los dispositivos propiedad de la empresa son compartidos o se destinan a usuarios dedicados?**

> [!div class="button"]
[Compartido >](#Shared-company-owned-devices)   [Dedicado >](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)


### Dispositivos compartidos propiedad de la empresa

Estos dispositivos no tienen un único usuario y no suelen estar configurados para obtener acceso al correo electrónico. Ejemplos de esto son los dispositivos de pantalla completa o los dispositivos orientados a tareas que los usuarios eligen de un grupo cuando lo necesitan y, luego, lo devuelven. Los métodos de inscripción recomendados dependerán de la plataforma de los dispositivos.

  - **Dispositivos Windows y Android:**: un *administrador de inscripción de dispositivos* es una cuenta de Intune que se usa para inscribir varios dispositivos compartidos con la aplicación de portal de empresa.
  > [!div class="button"]
  [Windows >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#shared-ios-device-enrollment)

### Inscripción de dispositivos iOS compartidos

El método preferido para inscribir dispositivos iOS compartidos propiedad de la empresa depende de cómo adquiera y administre estos dispositivos:

  - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando esos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con ese perfil de DEP.
  - **Apple Configurator en un equipo Mac (Mac):** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración. Si prefiere no restablecer la configuración de fábrica de los dispositivos, use la inscripción directa.
  - **Ninguno de los anteriores:** si no puede o no quiere usar los métodos de inscripción de DEP o con Apple Configurator de Apple, use el Administrador de inscripción de dispositivos de Intune.

  **Elija:**
    > [!div class="button"]
     [Inscripción de DEP >](../deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Mac >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Inscripción directa >](../deploy-use/ios-direct-enrollment-in-microsoft-intune)  

  > [!div class="button"]
    [Inscripción de DEM >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

**Usuarios individuales:** los dispositivos propiedad de la empresa destinados a usuarios individuales deben someterse a un seguimiento como activos de la empresa y, al mismo tiempo, dejar que los usuarios puedan tener acceso a los datos y al correo como si se tratara de dispositivos personales. Los métodos de inscripción recomendados dependerán de la plataforma de los dispositivos.

  - **Dispositivos Windows y Android:** si se importan los números de identidad de equipo móvil internacional (IMEI) de los dispositivos propiedad de la empresa, estos se podrán etiquetar como dispositivos propiedad de la empresa en Intune. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos personales instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos.
  > [!div class="button"]
  [Etiquetar con IMEI >](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **Dispositivos iOS:** los dispositivos iOS compartidos se pueden administrar de tres maneras.  **¿Cómo se inscriben los dispositivos iOS compartidos?**

    - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando esos dispositivos se enciendan por primera vez, descargan el perfil de DEP y se inscriben de acuerdo a ese perfil.
    > [!div class="button"]
    [Inscripción de DEP](../deploy-use/ios-device-enrollment-program-in-microsoft-intune).

    - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración.

    Si prefiere no restablecer la configuración de fábrica de los dispositivos, use la inscripción directa.
    Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración.
    > [!div class="button"][iOS Setup Assistant enrollment](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"][iOS direct enrollment](../deploy-use/ios-direct-enrollment-in-microsoft-intune).

    - **Ninguno de los anteriores:** si no puede o no quiere usar los métodos de inscripción de DEP o con Apple Configurator de Apple, importe los números de identidad de equipo móvil internacional (IMEI) de los dispositivos propiedad de la empresa para poder etiquetarlos como dispositivos propiedad de la empresa en Intune. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos personales instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos.
    > [!div class="button"][Tag devices with IMEI numbers](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Jun16_HO5-->


