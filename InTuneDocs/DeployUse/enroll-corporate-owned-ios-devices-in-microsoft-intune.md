---
title: Inscribir dispositivos iOS de empresa | Microsoft Intune
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
ms.sourcegitcommit: d81ef697518745b258598124d6e73899bdd76a0f
ms.openlocfilehash: 00d7e73154bb293fec48b74b6f6454d67e5ef378


---

# Inscribir dispositivos iOS de empresa en Microsoft Intune
Microsoft Intune permite inscribir dispositivos iOS de empresa con el Programa de inscripción de dispositivos (DEP) de Apple o la herramienta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) en ejecución en un equipo Mac.

**Requisito previo:** es necesario un [certificado de Apple Push Notification Service](set-up-ios-and-mac-management-with-microsoft-intune.md).

Puede inscribir dispositivos iOS de empresa de tres maneras: mediante Apple Configurator, DEP o el portal de empresa.

## Usar Apple Configurator

Para inscribir dispositivos iOS, exporte un perfil de inscripción corporativa y, después, conecte estos dispositivos móviles a un equipo Mac que ejecute Apple Configurator. Apple Configurator admite dos formas de inscripción:

- **Inscripción con el asistente de configuración**: restablece la configuración de fábrica del dispositivo y lo prepara para que el nuevo usuario del dispositivo lo configure. Este método requiere que el administrador conecte el dispositivo iOS a través de USB a un equipo Mac que ejecute [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para preconfigurar la inscripción. Después, los dispositivos se entregan a sus usuarios, que ejecutan el proceso del Asistente de configuración. En este proceso, se configura el dispositivo con las credenciales profesionales o educativas y se completa el proceso de inscripción. Para obtener más información, consulte [Inscribir dispositivos iOS con Apple Configurator y el Asistente de configuración](ios-setup-assistant-enrollment-in-microsoft-intune.md).

- **Inscripción directa**: crea un archivo compatible con Apple Configurator para su uso durante la preparación del dispositivo. No se restablece la configuración de fábrica del dispositivo inscrito, pero no tiene ninguna afiliación de usuario. Este método requiere que el administrador conecte el dispositivo iOS a través de USB a un equipo Mac que ejecute [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para inscribir el dispositivo. Para obtener más información, consulte [Inscribir directamente dispositivos iOS mediante Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md).

## Usar el Programa de inscripción de dispositivos (DEP)
DEP implementa un perfil de inscripción "de forma inalámbrica" en los dispositivos que se adquieren a través de DEP. Cuando un usuario ejecuta el Asistente de configuración en el dispositivo, este se inscribe en Intune.  Los usuarios no pueden anular la inscripción de dispositivos inscritos a través de DEP. Para obtener más información, consulte [Inscribir dispositivos iOS de la empresa mediante el Programa de inscripción de dispositivos](ios-device-enrollment-program-in-microsoft-intune.md).

## Use el portal de empresa en dispositivos inscritos mediante DEP o mediante Apple Configurator

Los dispositivos que se configuran con afinidad de usuario pueden instalar y ejecutar la aplicación del portal de empresa para descargar aplicaciones y administrar dispositivos. Una vez que los usuarios han recibido sus dispositivos, deben realizar una serie de pasos adicionales para completar el Asistente de configuración e instalar la aplicación del portal de empresa.

**Cómo inscriben los usuarios dispositivos iOS de empresa con afinidad de usuario**
1. Cuando los usuarios encienden su dispositivo, se les pide que completen el Asistente de configuración. Durante la instalación, se pide a los usuarios sus credenciales. Deben usar las credenciales (es decir, el nombre único personal o UPN) asociadas con su suscripción en Intune.

2. Durante la instalación, se pide a los usuarios un id. de Apple. Deben proporcionar un identificador de Apple para que el dispositivo instale el portal de empresa. También pueden proporcionar el identificador desde el menú de configuración de iOS una vez finalizada la instalación.

3. Tras completar la instalación, el dispositivo iOS debe instalar la aplicación del portal de empresa desde App Store.

4. El usuario puede ahora iniciar sesión en el portal de empresa con el UPN que usó al configurar el dispositivo.

5. Después de iniciar sesión, se pide al usuario que inscriba el dispositivo. El primer paso es identificar su dispositivo. La aplicación presenta una lista de dispositivos iOS que ya se han inscrito en la empresa y que se han asignado a la cuenta de Intune del usuario. Debe elegir el dispositivo que corresponda.

  Si este dispositivo no está inscrito en la empresa, debe seleccionar **Nuevo dispositivo** para continuar con el flujo de inscripción estándar.

6. En la siguiente pantalla, el usuario debe confirmar el número de serie del dispositivo nuevo. El usuario puede pulsar el vínculo **Confirme el número de serie** para iniciar la aplicación de configuración para comprobar el número de serie. Después, el usuario debe especificar los últimos cuatro caracteres del número de serie en la aplicación del portal de empresa.

  Este paso comprueba que el dispositivo es el dispositivo de empresa inscrito en Intune. Si el número de serie del dispositivo no coincide, significa que se ha seleccionado el dispositivo equivocado. El usuario debe volver a la pantalla anterior y seleccionar un dispositivo diferente.

7. Después de comprobar el número de serie, la aplicación del portal de empresa redirige al sitio web del portal de empresa para finalizar la inscripción y luego pide al usuario que vuelva a la aplicación.

8. La inscripción ya se ha completado. Ahora el usuario puede usar este dispositivo con el conjunto completo de funcionalidades.

### Acerca de los dispositivos administrados de propiedad corporativa sin afinidad de usuario

Los dispositivos configurados sin afinidad de usuario no admiten el portal de empresa y no deben tener instalada la aplicación. El Portal de empresa está diseñado para usuarios que tienen credenciales corporativas y que necesitan acceso a recursos corporativos personalizados (por ejemplo, correo electrónico). Los dispositivos que se inscriben sin afinidad de usuario no están diseñados para tener un inicio de sesión de usuario dedicado. Los quioscos, los puntos de venta (POS) y los dispositivos de utilidad compartida son casos de uso típicos de dispositivos que se inscriben sin afinidad de usuario.

En caso de que la afinidad de usuario sea un requisito, asegúrese de que el perfil de inscripción del dispositivo tenga seleccionada la **afinidad de usuario** antes de inscribirlo. Para cambiar el estado de afinidad de un dispositivo, debe retirarlo y volver a inscribirlo.



### Consulte también
[Preparar la inscripción de dispositivos en Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Sep16_HO1-->


