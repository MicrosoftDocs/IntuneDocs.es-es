---
# required metadata

title: Elegir cómo inscribir dispositivos móviles | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: damionw
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Elegir cómo inscribir dispositivos móviles

La inscripción de dispositivos móviles es un proceso en el que los smartphones, las tabletas y los equipos se incorporan a la administración de Microsoft Intune. Como administrador, su tarea consiste en averiguar cuál es la mejor forma de inscribir dispositivos a partir de los siguientes aspectos:

 -  Propiedad (personal o de la empresa)
 -  Uso (compartido o personal)
 -  Plataforma (iOS, Android, Windows Phone, PC Windows o PC Mac)

Las respuestas a las siguientes preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos bajo su administración.

## ¿Los empleados traen sus propios dispositivos o se los proporciona la organización?

  **Dispositivos propiedad de los usuarios** (Bring your own device o "BYOD"): los usuarios pueden instalar la aplicación de portal de empresa de Intune en sus dispositivos y, luego, inscribirlos para obtener acceso a recursos de la empresa, como el correo electrónico, aplicaciones de empresa, datos de la compañía y soporte técnico.  
  > [!div class="button"]   [Inscripción BYOD >](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)

  **Dispositivos propiedad de la empresa:** los dispositivos propiedad de la empresa (COD) se pueden inscribir de diversas formas, según cuáles sean las necesidades de la organización y los tipos de dispositivos administrados. Siguiente pregunta...

## ¿Los dispositivos propiedad de la empresa son compartidos o se destinan a determinados usuarios?

**Dispositivos propiedad de la empresa compartidos:** estos dispositivos no tienen un único usuario y no suelen estar configurados para obtener acceso al correo electrónico. Ejemplos de esto son los dispositivos de pantalla completa o los dispositivos orientados a tareas que los usuarios eligen de un grupo cuando lo necesitan y, luego, lo devuelven. Los métodos de inscripción recomendados dependerán de la plataforma de los dispositivos.

  - **Dispositivos Windows y Android:**: un *administrador de inscripción de dispositivos* es una cuenta de Intune que se usa para inscribir varios dispositivos compartidos con la aplicación de portal de empresa.
  > [!div class="button"]   [Administrador de inscripción de dispositivos >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Dispositivos iOS:** los dispositivos iOS compartidos se pueden administrar de tres maneras.  **¿Cómo se inscriben los dispositivos iOS compartidos?**

    - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando esos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con ese perfil de DEP.
    > [!div class="button"]     [Inscripción de DEP >](../deploy-use/ios-device-enrollment-program-in-microsoft-intune)

    - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración. Si prefiere no restablecer la configuración de fábrica de los dispositivos, use la inscripción directa.

    > [!div class="button"]     [Inscripción con el Asistente de configuración >](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) o [Inscripción directa >](../deploy-use/ios-direct-enrollment-in-microsoft-intune)

    - **Ninguno de los anteriores:** si no puede o no quiere usar los métodos de inscripción de DEP o con Apple Configurator de Apple, use el Administrador de inscripción de dispositivos de Intune.
    > [!div class="button"]     [Inscripción con DEM >](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

**Usuarios individuales:** los dispositivos propiedad de la empresa destinados a usuarios individuales deben someterse a un seguimiento como activos de la empresa y, al mismo tiempo, dejar que los usuarios puedan tener acceso a los datos y al correo como si se tratara de dispositivos personales. Los métodos de inscripción recomendados dependerán de la plataforma de los dispositivos.

  - **Dispositivos Windows y Android:** si se importan los números de identidad de equipo móvil internacional (IMEI) de los dispositivos propiedad de la empresa, estos se podrán etiquetar como dispositivos propiedad de la empresa en Intune. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos personales instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos.
  > [!div class="button"]   [Etiquetar con IMEI >](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **Dispositivos iOS:** los dispositivos iOS compartidos se pueden administrar de tres maneras.  **¿Cómo se inscriben los dispositivos iOS compartidos?**

    - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando esos dispositivos se enciendan por primera vez, descargan el perfil de DEP y se inscriben de acuerdo a ese perfil.
    > [!div class="button"]     [Inscripción con DEP](../deploy-use/ios-device-enrollment-program-in-microsoft-intune)

    - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración.

    Si prefiere no restablecer la configuración de fábrica de los dispositivos, use la inscripción directa.
    Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración.
    > [!div class="button"] [Inscripción con el Asistente de configuración de iOS](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"][Inscripción directa de iOS](../deploy-use/ios-direct-enrollment-in-microsoft-intune).

    - **Ninguno de los anteriores:** si no puede o no quiere usar los métodos de inscripción de DEP o con Apple Configurator de Apple, importe los números de identidad de equipo móvil internacional (IMEI) de los dispositivos propiedad de la empresa para poder etiquetarlos como dispositivos propiedad de la empresa en Intune. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos personales instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos. > [!div class="button"][Etiquetar dispositivos con números IMEI](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)


<!--HONumber=Jun16_HO1-->


