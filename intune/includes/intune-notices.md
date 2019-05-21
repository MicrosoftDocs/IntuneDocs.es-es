---
title: archivo include
description: archivo include
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: ffcef5b4d78856709f8563ee1f667ec7e5d993b3
ms.sourcegitcommit: d2e04a38e024b0f5afb0ca202823227de9da3ad1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65732600"
---
Estos avisos proporcionan información importante que puede ayudarle a prepararse para las características y los cambios futuros de Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Cambio en el flujo de trabajo de inscripción con el Portal de empresa de Intune en dispositivos iOS corporativos que se autentican con el Asistente de configuración <!-- 1927359 -->
Hay un próximo cambio en el flujo de trabajo para la inscripción de dispositivos iOS a través de uno de los métodos de inscripción de dispositivos corporativos de Apple: Apple Configurator, Apple Business Manager, Apple School Manager o el Programa de inscripción de dispositivos de Apple, cuando se usa el Asistente de configuración para la autenticación. Este cambio se aplica solo a los dispositivos inscritos con afinidad de usuario.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Cuando este cambio se implemente, se actualizarán los perfiles de inscripción de Intune en Azure Portal para que pueda especificar cómo se autentican los dispositivos y si reciben la aplicación Portal de empresa. Habrá un flujo de trabajo mejorado para inscribir dispositivos iOS a través de los métodos enumerados anteriormente. 

- Al inscribir nuevos dispositivos y autenticarse con el Asistente de configuración, podrá elegir si desea implementar automáticamente la aplicación Portal de empresa o no. Los usuarios finales ya no verán la pantalla de identificación ni de confirmación del dispositivo en la pantalla de inscripción.  
- En los dispositivos ya inscritos mediante el Asistente de configuración a través de uno de los métodos de inscripción de dispositivos corporativos de Apple, debe tomar medidas si desea habilitar el acceso condicional. Tendrá que [configurar una directiva de configuración de aplicación](https://aka.ms/enrollment_setup_assistant) con un archivo xml específico para insertar el Portal de empresa en estos dispositivos.  Si opta por insertar el Portal de empresa de este modo, los usuarios finales ya no verán la pantalla de identificación ni de confirmación del dispositivo en la pantalla de inscripción. 
- Una vez implantado este cambio, si no ha implementado el Portal de empresa con el perfil de configuración de la aplicación mencionado anteriormente y si los usuarios finales descargan la aplicación del Portal de empresa desde el App Store, estos podrán iniciar sesión, pero recibirán un mensaje de error. No podrán usar la aplicación para el acceso condicional. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Si planea usar el flujo de trabajo modificado, tendrá que actualizar las orientaciones para el usuario final para indicar que:

- Los usuarios finales ya no verán las dos pantallas mencionadas anteriormente en el flujo de inscripción. 
- Deben iniciar sesión en el Portal de empresa cuando se implemente automáticamente, y no descargarlo del App Store. 

Puede optar por crear ahora una directiva de configuración de la aplicación si fuera necesario, en preparación para este cambio. Cuando se implemente este nuevo flujo de trabajo, podrá ver los perfiles de inscripción actualizados en la consola. También le informaremos de esta implementación a través del Centro de mensajes. Luego, deberá tomar medidas para que sus usuarios finales puedan inscribirse a través del Programa de inscripción de dispositivos de Apple al autenticarse con el Asistente de configuración, y puede usar el Portal de empresa para el acceso condicional.

#### <a name="additional-information"></a>Información adicional 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Actualización de la aplicación del Portal de empresa de Android a la versión más reciente <!--4536963-->
Intune publica actualizaciones periódicamente de la aplicación del Portal de empresa de Android. En noviembre de 2018 publicamos una actualización del Portal de empresa, que incluía un conmutador de back-end, en preparación para el cambio de Google de su plataforma de notificación existente a Firebase Cloud Messaging (FCM). Cuando Google retire su plataforma de notificación existente y se traslade a FCM, los usuarios finales deberán haber actualizado la aplicación del Portal de empresa al menos a la versión de noviembre de 2018 para seguir comunicándose con Google Play Store.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Nuestra telemetría indica que tiene dispositivos con una versión anterior a 5.0.4269.0 del Portal de empresa. Si no está instalada esta versión o una versión posterior de la aplicación del Portal de empresa, las acciones del dispositivo iniciadas por profesionales de TI, como el borrado, el restablecimiento de la contraseña, las instalaciones de aplicaciones requeridas y disponibles y la inscripción de certificados pueden no funcionar según lo previsto. Si sus dispositivos están inscritos en MDM en Intune, puede ver las versiones y los usuarios del portal de empresa en Aplicaciones cliente - Aplicaciones detectadas. La selección de versiones anteriores del Portal de empresa le permitirá ver qué usuarios finales tienen los dispositivos que no han actualizado el Portal de empresa.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Pida a los usuarios finales de dispositivos Android que no hayan actualizado el Portal de empresa que lo hagan mediante Google Play. Ponga en conocimiento del departamento de soporte técnico aquellos casos en que un usuario no haya mantenido la actualización automática de la aplicación del Portal de empresa. Consulte el vínculo de información adicional para obtener más información sobre los cambios y la plataforma FCM de Google.

#### <a name="additional-information"></a>Información adicional
https://firebase.google.com/docs/cloud-messaging/