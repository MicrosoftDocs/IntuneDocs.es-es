---
title: "Inscripción de dispositivos iOS de empresa | Microsoft Intune"
description: "Inscripción de dispositivos iOS de empresa mediante el Programa de inscripción de dispositivos (DEP) de Apple o Apple Configurator"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 09/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bee93334e7b868ef6c827fba9efc3318c8419527
ms.openlocfilehash: b295ee11d566fbfbe84513c045f3a76dfd51cda4


---

# Inscribir dispositivos iOS de empresa en Microsoft Intune
Microsoft Intune permite inscribir dispositivos iOS de propiedad corporativa con el Programa de inscripción de dispositivos (DEP) de Apple o la herramienta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) que se ejecuta en un equipo Mac.

**Requisito previo:** se requiere un [certificado de Apple Push Notification Service](set-up-ios-and-mac-management-with-microsoft-intune.md).

Puede inscribir dispositivos iOS de empresa de tres maneras: mediante Apple Configurator, DEP o el Portal de empresa.

## Usar Apple Configurator

Puede inscribir dispositivos iOS mediante la exportación de un perfil de inscripción corporativa y, después, mediante la conexión de esos dispositivos móviles a un equipo Mac que ejecuta Apple Configurator. Apple Configurator admite dos formas de inscripción:

- **Inscripción con el Asistente de configuración**: restablece la configuración de fábrica del dispositivo y lo prepara para que el nuevo usuario del dispositivo lo configure. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para preconfigurar la inscripción. Después, los dispositivos se entregan a los usuarios, que ejecutan el proceso del Asistente de configuración. Mediante este proceso se configura el dispositivo con sus credenciales profesionales o educativas y se completa el proceso de inscripción. Para obtener más información, consulte [Inscribir dispositivos iOS con Apple Configurator y el Asistente de configuración](ios-setup-assistant-enrollment-in-microsoft-intune.md).

- **Inscripción directa**: crea un archivo compatible con Apple Configurator para su uso durante la preparación del dispositivo. No se restablece la configuración de fábrica del dispositivo inscrito, pero no tiene ninguna afiliación de usuario. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para inscribir el dispositivo. Para obtener más información, consulte [Inscribir directamente dispositivos iOS mediante Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md).

## Usar el Programa de inscripción de dispositivos (DEP)
DEP implementa un perfil de inscripción "de forma inalámbrica" en los dispositivos que se adquieren a través de DEP. Cuando un usuario ejecuta el Asistente de configuración en el dispositivo, el dispositivo se inscribe en Intune.  Los usuarios no pueden anular la inscripción de dispositivos inscritos a través de DEP. Para obtener más información, consulte [Inscribir dispositivos iOS de la empresa mediante el Programa de inscripción de dispositivos](ios-device-enrollment-program-in-microsoft-intune.md).

## Usar el portal de empresa en dispositivos inscritos mediante DEP o Apple Configurator

Los dispositivos configurados con afinidad de usuario pueden instalar y ejecutar la aplicación del portal de empresa para descargar aplicaciones y administrar dispositivos. Después de recibir sus dispositivos, los usuarios deben realizar una serie de pasos adicionales para completar el Asistente de configuración e instalar la aplicación del portal de empresa.

La afinidad de usuario es necesaria para admitir lo siguiente:
  - Aplicaciones de administración de aplicaciones móviles (MAM)
  - Acceso condicional al correo electrónico y los datos de la empresa
  - Aplicación de portal de empresa

**Inscripción de dispositivos iOS de empresa con afinidad de usuario**
1. Cuando los usuarios encienden su dispositivo, se les pide que completen el Asistente de configuración. Durante la instalación, se pide a los usuarios sus credenciales. Deben usar las credenciales (es decir, el nombre único personal o UPN) que están asociadas con su suscripción en Intune.

2. Durante la instalación, se pide a los usuarios un id. de Apple. Deben proporcionar un identificador de Apple para que el dispositivo instale el portal de empresa. También pueden proporcionar el identificador desde el menú de configuración de iOS una vez finalizada la instalación.

3. Tras completar la instalación, el dispositivo iOS debe instalar la aplicación del portal de empresa desde la Tienda de aplicaciones.

4. El usuario puede ahora iniciar sesión en el portal de empresa con el UPN que usó al configurar el dispositivo.

5. Después de iniciar sesión, se pide al usuario que inscriba el dispositivo. El primer paso es identificar su dispositivo. La aplicación presenta una lista de dispositivos iOS que ya se han inscrito en la empresa y que se han asignado a la cuenta de Intune del usuario. Debe elegir el dispositivo que corresponda.

  Si este dispositivo no está inscrito en la empresa, debe elegir **nuevo dispositivo** para continuar con el flujo de inscripción estándar.

6. En la siguiente pantalla, el usuario debe confirmar el número de serie del nuevo dispositivo. El usuario puede pulsar el vínculo **Confirme el número de serie** para iniciar la aplicación de configuración para comprobar el número de serie. El usuario debe especificar los últimos cuatro caracteres del número de serie en la aplicación del portal de empresa.

  Este paso comprueba que el dispositivo es el dispositivo de empresa inscrito en Intune. Si el número de serie del dispositivo no coincide, significa que se ha seleccionado el dispositivo equivocado. El usuario debe volver a la pantalla anterior y seleccionar un dispositivo diferente.

7. Después de comprobar el número de serie, la aplicación del portal de empresa redirige al sitio web del portal de empresa para finalizar la inscripción. Luego, el sitio web le pide al usuario que vuelva a la aplicación.

8. La inscripción ya se ha completado. El usuario puede usar ahora este dispositivo con el conjunto completo de funcionalidades.

### Acerca de los dispositivos administrados de propiedad corporativa sin afinidad de usuario

Los dispositivos configurados sin afinidad de usuario no admiten el portal de empresa y no se debe instalar en ellos la aplicación. El Portal de empresa está diseñado para usuarios que tienen credenciales corporativas y que necesitan acceso a recursos corporativos personalizados (por ejemplo, correo electrónico). Los dispositivos inscritos sin afinidad de usuario no están diseñados para tener un inicio de sesión de usuario dedicado. Los quioscos multimedia, los puntos de venta (PDV) y los dispositivos de utilidad compartida son casos de uso típicos de dispositivos inscritos sin afinidad de usuario.

En caso de que la afinidad de usuario sea un requisito, asegúrese de que el perfil de inscripción del dispositivo tenga seleccionada la **afinidad de usuario** antes de inscribirlo. Para cambiar el estado de afinidad en un dispositivo, debe cancelar su inscripción y realizarla de nuevo.



### Consulte también
[Preparar la inscripción de dispositivos en Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Sep16_HO3-->


