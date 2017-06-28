---
title: Inscribir dispositivos iOS de empresa
description: "Inscripción de dispositivos iOS de empresa mediante el Programa de inscripción de dispositivos (DEP) de Apple o Apple Configurator"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 42da9c874183287bc9485035ae39e94efbaa3e8b
ms.contentlocale: es-es
ms.lasthandoff: 06/08/2017


---

# <a name="enroll-corporate-owned-ios-devices-in-microsoft-intune"></a>Inscribir dispositivos iOS de empresa en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune permite inscribir dispositivos iOS de propiedad corporativa con el Programa de inscripción de dispositivos (DEP) de Apple o la herramienta [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017) que se ejecuta en un equipo Mac.

**Requisito previo:** un [certificado de Apple Push Notification Service](set-up-ios-and-mac-management-with-microsoft-intune.md)

Puede inscribir dispositivos iOS de empresa con uno de los siguientes tres métodos:

- Apple Configurator, mediante el Asistente de instalación o la inscripción directa
- Programa de inscripción de dispositivos
- Aplicación de portal de empresa

>[!NOTE]
>Los métodos de inscripción del Programa de inscripción de dispositivos y Apple Configurator no se pueden usar con el método [administrador de inscripción de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

De manera predeterminada, todos los dispositivos iOS pueden inscribirse en Intune. Para bloquear la inscripción de dispositivos propiedad de la empresa o personales, inicie sesión en el [portal de administración de Microsoft Intune](https://manage.microsoft.com) con sus credenciales de administrador. Elija **Administrador** > **Administración de dispositivos móviles** > **Reglas de inscripción** y después desactive las opciones aplicables.

## <a name="use-apple-configurator"></a>Usar Apple Configurator

Puede inscribir dispositivos iOS mediante la exportación de un perfil de inscripción corporativa y, después, mediante la conexión de esos dispositivos móviles a un equipo Mac que ejecuta Apple Configurator. Apple Configurator admite dos formas de inscripción:

- **Inscripción con el Asistente de configuración**: restablece la configuración de fábrica del dispositivo y lo prepara para que el nuevo usuario del dispositivo lo configure. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017) para preconfigurar la inscripción. Después, los dispositivos se entregan a los usuarios, que ejecutan el proceso del Asistente de configuración. Mediante este proceso se configura el dispositivo con sus credenciales profesionales o educativas y se completa el proceso de inscripción. Para obtener más información, consulte [Inscribir dispositivos iOS con Apple Configurator y el Asistente de configuración](ios-setup-assistant-enrollment-in-microsoft-intune.md).

- **Inscripción directa**: crea un archivo compatible con Apple Configurator para su uso durante la preparación del dispositivo. No se restablece la configuración de fábrica del dispositivo inscrito, pero no tiene ninguna afiliación de usuario. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017) para inscribir el dispositivo. Para obtener más información, consulte [Inscribir directamente dispositivos iOS mediante Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md).

## <a name="use-the-device-enrollment-program-dep"></a>Usar el Programa de inscripción de dispositivos (DEP)
DEP implementa un perfil de inscripción "de forma inalámbrica" en los dispositivos que se adquieren a través de DEP. Cuando un usuario ejecuta el Asistente de configuración en el dispositivo, el dispositivo se inscribe en Intune. Para obtener más información, consulte [Inscribir dispositivos iOS de la empresa mediante el Programa de inscripción de dispositivos](ios-device-enrollment-program-in-microsoft-intune.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Usar el portal de empresa en dispositivos inscritos mediante DEP o Apple Configurator

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

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Acerca de los dispositivos administrados de propiedad corporativa sin afinidad de usuario

Los dispositivos configurados sin afinidad de usuario no admiten el portal de empresa y no se debe instalar en ellos la aplicación. El Portal de empresa está diseñado para usuarios que tienen credenciales corporativas y que necesitan acceso a recursos corporativos personalizados (por ejemplo, correo electrónico). Los dispositivos inscritos sin afinidad de usuario no están diseñados para tener un inicio de sesión de usuario dedicado. Los quioscos multimedia, los puntos de venta (PDV) y los dispositivos de utilidad compartida son casos de uso típicos de dispositivos inscritos sin afinidad de usuario.

En caso de que la afinidad de usuario sea un requisito, asegúrese de que el perfil de inscripción del dispositivo tenga seleccionada la **afinidad de usuario** antes de inscribirlo. Para cambiar el estado de afinidad en un dispositivo, debe cancelar su inscripción y realizarla de nuevo.



### <a name="see-also"></a>Consulte también
[Requisitos previos para la inscripción de dispositivos en Microsoft Intune](prerequisites-for-enrollment.md)

