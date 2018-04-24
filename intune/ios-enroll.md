---
title: Elegir cómo inscribir los dispositivos iOS en Intune
titlesuffix: Microsoft Intune
description: Configure la inscripción de dispositivos iOS en Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 01523dc4c887214794d4600219ce0b77549b4734
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-ios-devices-in-intune"></a>Inscripción de dispositivos iOS en Intune

Intune permite la administración de dispositivos móviles (MDM) de iPads y iPhones para conceder acceso a los usuarios al correo electrónico y las aplicaciones de la empresa.

Como administrador de Intune, puede habilitar la inscripción para dispositivos iOS. Puede permitir que los usuarios inscriban dispositivos propios, lo que se conoce como la inscripción "Bring Your Own Device" (BYOD). También puede habilitar la inscripción de dispositivos de la empresa.

## <a name="prerequisites-for-ios-enrollment"></a>Requisitos previos para la inscripción de iOS
Antes de que pueda habilitar dispositivos iOS, complete estos pasos:
- [Configurar Intune](setup-steps.md): estos pasos configurar la infraestructura de Intune. En concreto, la inscripción de dispositivos requiere que [establezca su autoridad de MDM](mdm-authority-set.md).
- [Obtención de un certificado push MDM de Apple](apple-mdm-push-certificate-get.md): Apple requiere un certificado para habilitar la administración de dispositivos iOS y macOS.

## <a name="user-owned-ios-devices-byod"></a>Dispositivos iOS corporativos (BYOD)

Puede permitir que los usuarios inscriban sus dispositivos personales para la administración de Intune. Esto se conoce como "Bring Your Own Device" o BYOD. Tras completar los requisitos previos y asignar licencias a los usuarios, estos podrán descargar la aplicación Portal de empresa de Intune del App Store y seguir las instrucciones de inscripción.

## <a name="company-owned-ios-devices"></a>Dispositivos iOS propiedad de la empresa
Para las organizaciones que adquieran dispositivos para sus usuarios, Intune admite los métodos de inscripción de dispositivos de empresa siguientes para iOS:

- Programa de inscripción de dispositivos (DEP) de Apple
- Apple School Manager
- Inscripción de Apple Configurator mediante el Asistente de configuración
- Inscripción directa de Apple Configurator

También puede inscribir dispositivos iOS de empresa con una cuenta de [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programa de inscripción de dispositivos
Las organizaciones pueden adquirir dispositivos iOS a través del Programa de inscripción de dispositivos (DEP) de Apple. DEP permite implementar un perfil de inscripción "de forma inalámbrica" que traiga los dispositivos a la administración. Más información sobre el [Programa de inscripción de dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager es un programa de compra e inscripción de dispositivos para centros escolares. Al igual que DEP, puede implementar un perfil para inscribir dispositivos en la administración. Más información sobre [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Puede inscribir dispositivos iOS con Apple Configuration en un equipo Mac. Para preparar los dispositivos, se conectan mediante USB y se instala un perfil de inscripción. Puede inscribir dispositivos con Apple Configuration de dos maneras:
- Inscripción con el Asistente de configuración: este proceso restablece el dispositivo a la configuración de fábrica, lo prepara para ejecutar el Asistente de configuración e instala las directivas de la empresa para el nuevo usuario del dispositivo.
- Inscripción directa: este proceso no restablece los valores de fábrica del dispositivo e inscribe el dispositivo con una directiva predefinida. Este método está destinado a los dispositivos sin afinidad de usuario.

Más información sobre [Inscripción de Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).

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

6. En la siguiente pantalla, el usuario debe confirmar el número de serie del nuevo dispositivo. El usuario puede pulsar el vínculo **Confirme el número de serie** que iniciará las instrucciones para usar la aplicación de configuración para comprobar el número de serie. El usuario debe especificar los últimos cuatro caracteres del número de serie en la aplicación del portal de empresa.

   Este paso comprueba que el dispositivo es el dispositivo de empresa inscrito en Intune. Si el número de serie del dispositivo no coincide, significa que se ha seleccionado el dispositivo equivocado. El usuario debe volver a la pantalla anterior y seleccionar un dispositivo diferente.

7. Después de comprobar el número de serie, la aplicación del portal de empresa redirige al sitio web del portal de empresa para finalizar la inscripción Luego, el sitio web le pide al usuario que vuelva a la aplicación.

8. La inscripción ya se ha completado. El usuario puede usar ahora este dispositivo con el conjunto completo de funcionalidades.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Acerca de los dispositivos administrados de propiedad corporativa sin afinidad de usuario

Los dispositivos configurados sin afinidad de usuario no admiten el portal de empresa y no se debe instalar en ellos la aplicación. El Portal de empresa está diseñado para usuarios que tienen credenciales corporativas y que necesitan acceso a recursos corporativos personalizados (por ejemplo, correo electrónico). Los dispositivos inscritos sin afinidad de usuario no están diseñados para tener un inicio de sesión de usuario dedicado. Los quioscos multimedia, los puntos de venta (PDV) y los dispositivos de utilidad compartida son casos de uso típicos de dispositivos inscritos sin afinidad de usuario.

En caso de que la afinidad de usuario sea un requisito, asegúrese de que el perfil de inscripción del dispositivo tenga seleccionada la **afinidad de usuario** antes de inscribirlo. Para cambiar el estado de afinidad en un dispositivo, debe cancelar su inscripción y realizarla de nuevo.

