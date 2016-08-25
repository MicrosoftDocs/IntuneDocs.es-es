---
title: "Inscripción de dispositivos iOS de empresa | Microsoft Intune"
description: "Inscripción de dispositivos iOS de empresa mediante el Programa de inscripción de dispositivos (DEP) de Apple o Apple Configurator"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9b7b8f6e5182e228458f5ea75e804a638f1e2a2b
ms.openlocfilehash: ca05e94e72269c11db24b667f1d113c794cd8b23


---

# Inscribir dispositivos iOS de empresa en Microsoft Intune
Microsoft Intune permite inscribir dispositivos iOS de propiedad corporativa con el programa de inscripción de dispositivos (DEP) de Apple o la herramienta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) que se ejecuta en un equipo Mac.

**Requisito previo:**  [Certificado del servicio de notificaciones push de Apple](set-up-ios-and-mac-management-with-microsoft-intune.md)

Puede inscribir dispositivos iOS de empresa de tres maneras:

-   **Apple Configurator**: los dispositivos iOS se pueden inscribir mediante la exportación de un perfil de inscripción corporativa y, después, mediante la conexión de esos dispositivos móviles a un equipo Mac que ejecuta Apple Configurator. Apple Configurator admite dos formas de inscripción:

    - **Inscripción con el asistente de configuración** : restablece la configuración de fábrica del dispositivo y lo prepara para que el nuevo usuario del dispositivo lo instale. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para preconfigurar la inscripción. Tras esto, los dispositivos se entregan a los usuarios, que ejecutan el proceso del asistente de instalación, configuran el dispositivo con sus credenciales profesionales o educativas y finalizan el proceso de inscripción. [Inscribir dispositivos iOS con Apple Configurator y el asistente de instalación](ios-setup-assistant-enrollment-in-microsoft-intune.md)

    - **Inscripción directa:** crea un archivo compatible con Apple Configurator para su uso durante la preparación del dispositivo. No se restablece la configuración de fábrica del dispositivo inscrito pero no tiene ninguna afiliación de usuario. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para inscribir el dispositivo. [Inscribir dispositivos iOS mediante inscripción directa de Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md)

-   **Programa de inscripción de dispositivos (DEP):** implementa un perfil de inscripción "de forma inalámbrica" en los dispositivos adquiridos a través del programa de inscripción de dispositivos de Apple. Cuando se ejecuta el asistente de instalación en el dispositivo, el dispositivo se inscribe en Intune.  Los usuarios no pueden anular la inscripción de dispositivos inscritos a través de DEP. [Inscribir dispositivos iOS del programa de inscripción de dispositivos](ios-device-enrollment-program-in-microsoft-intune.md)

## Usar Portal de empresa de DEP o dispositivos inscritos en Apple Configurator

Los dispositivos configurados con afinidad de usuario pueden instalar y ejecutar la aplicación del Portal de empresa para descargar aplicaciones y administrar dispositivos. Cuando los usuarios reciben sus dispositivos, deben realizar una serie de pasos adicionales para completar el Asistente para la instalación e instalar la aplicación del Portal de empresa.

Inscripción de dispositivos iOS de empresa con la afinidad de usuario
1. Cuando los usuarios encienden su dispositivo, se les pide que completen el Asistente de configuración. Durante la instalación, se pide a los usuarios sus credenciales. Deben usar las credenciales (es decir, el nombre único personal o UPN) asociadas con su suscripción en Intune.

2. Durante la instalación, se pide a los usuarios un id. de Apple. El id. de Apple es necesario para que el dispositivo instale el Portal de empresa. También se puede proporcionar el id. de Apple cuando finalice la instalación desde el menú de configuración de iOS.

3. Tras completar la instalación, el dispositivo iOS debe instalar la aplicación del Portal de empresa desde App Store, por ejemplo, aplicación del Portal de empresa.

4. El usuario puede ahora iniciar sesión en el Portal de empresa con el UPN cuando configure el dispositivo.

5. Después de iniciar sesión, se pide al usuario que inscriba el dispositivo. El primer paso es identificar su dispositivo. La aplicación presenta una lista de dispositivos iOS que ya se han inscrito en la empresa y que se han asignado a la cuenta de Intune del usuario final. Elija el dispositivo que corresponda.

  Si este dispositivo no está inscrito en la empresa, seleccione "nuevo dispositivo" para continuar con el flujo de inscripción estándar.

6. En la siguiente pantalla, el usuario debe confirmar la serie del nuevo dispositivo. El usuario puede pulsar en el vínculo "confirmar el número de serie" para iniciar la aplicación de configuración para comprobar el número de serie. El usuario debe especificar los últimos cuatro caracteres del número de serie en la aplicación del Portal de empresa.

  Este paso comprueba que el dispositivo es el dispositivo de empresa inscrito en Intune. Si el número de serie del dispositivo no coincide, significa que se ha seleccionado el dispositivo equivocado. Vuelva a la pantalla anterior y seleccione un dispositivo diferente.

7. Después de comprobar el número de serie, la aplicación del Portal de empresa redirige al sitio web del Portal de empresa para finalizar la inscripción y luego pide al usuario que vuelva a la aplicación.

8. La inscripción ya se ha completado. Ahora puede usar este dispositivo con el conjunto completo de funcionalidades.

### Acerca de los dispositivos administrados de propiedad corporativa sin afinidad de usuario

Los dispositivos configurados sin afinidad de usuario no admiten el Portal de empresa y no deben instalar la aplicación. El Portal de empresa está diseñado para usuarios que tienen credenciales corporativas y que necesitan acceso a recursos corporativos personalizados (por ejemplo, correo electrónico). Los dispositivos inscritos sin afinidad de usuario no están diseñados para tener un inicio de sesión de usuario dedicado. Los quioscos, puntos de venta (POS) y dispositivos de utilidad compartida son casos de uso típicos de dispositivos inscritos sin afinidad de usuario. En caso de que la afinidad de usuario sea un requisito, asegúrese de que el perfil de inscripción del dispositivo tenga seleccionada la afinidad de usuario antes de inscribirlo. Para cambiar el estado de afinidad en un dispositivo, debe cancelar su inscripción y realizarla de nuevo.



### Consulte también
[Preparar la inscripción de dispositivos en Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


