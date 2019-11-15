---
title: archivo include
description: archivo include
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/4/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: edef1f43caff97ab75aa3c58034ed4fc2dffd208
ms.sourcegitcommit: ae6f2e7812e7fd36f2393b8f4b6cd8de63777b2c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73612166"
---
Estos avisos proporcionan información importante que puede ayudarle a prepararse para las características y los cambios futuros de Intune.

### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>Plan de cambio: Experiencia actualizada al inscribir dispositivos dedicados de Android Enterprise en Intune<!--5198878-->
Con la versión de noviembre o 1911 de Intune, agregamos compatibilidad con la implementación de certificados de dispositivo SCEP en dispositivos Android Enterprise dedicados para permitir el acceso basado en certificados a los perfiles de Wi-Fi. Este cambio también implica algunos cambios secundarios en el flujo al inscribir dispositivos de Android Enterprise dedicados.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Si administra dispositivos dedicados de Android Enterprise en su entorno, comenzará a ver que la implementación de algunos cambios en noviembre.

- Para nuevas inscripciones de dispositivos dedicados de Android Enterprise: Los usuarios finales verán un conjunto diferente de pasos en los dispositivos durante la inscripción. La inscripción comenzará de la misma manera que hoy (con QR, NFC, Zero-Touch o identificador de dispositivo), pero después de la versión de servicio de noviembre, habrá un paso de instalación de la aplicación obligatorio.
- Para los dispositivos Android existentes inscritos como dispositivos dedicados: Intune comenzará a instalar automáticamente la aplicación de Microsoft Intune en dispositivos a partir de principios de noviembre. No es necesario hacer nada. La aplicación se descargará e instalará automáticamente en los dispositivos. 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
Debe planear la actualización de las instrucciones para el usuario final y dejar que el departamento de soporte técnico se entere de este cambio. Haga clic en Información adicional para obtener más información y capturas de pantallas. Actualizaremos esta página de novedades cuando se implante este cambio.

#### <a name="additional-information"></a>Información adicional
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>Plan de cambio: La configuración del "registro del lado servidor para comandos Siri" se quitará de la consola de Intune. <!-- 5468501-->

Tenemos previsto quitar la configuración del "registro del lado servidor para comandos Siri" de la consola de Intune con la actualización de noviembre del servicio de Intune. Este cambio se alinea con Apple, que ya ha quitado la configuración en su lado.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Cuando la actualización de noviembre o 1911 se implemente aproximadamente a mediados de noviembre, verá que esta configuración se ha quitado del menú Restricciones de dispositivos (aplicaciones integradas) para los perfiles de configuración de iOS, en la consola de Intune. Puede aparecer en las directivas y en el perfil de administración del dispositivo de destino, pero la configuración no tiene ningún efecto en el dispositivo. No se prevé mucho impacto en la funcionalidad, ya que actualmente no funciona en los dispositivos, aunque la vea en el perfil de administración.

Puede elegir una de las dos vías:
- Si desea eliminar esta configuración de las directivas, puede ir al perfil que tiene esta configuración, realizar una edición secundaria y guardar la directiva. La directiva volverá a calcularse en el back-end y la configuración se eliminará de la directiva.
- Si decide no realizar esta acción, los usuarios finales verán esta configuración en el perfil de administración del dispositivo, pero la configuración no tendrá ningún efecto.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
Puede realizar una acción según la sección anterior o dejar la directiva tal cual. Cuando se realice este cambio, actualizaremos nuestra página de novedades y la documentación correspondiente.

### <a name="end-of-support-for-legacy-pc-management"></a>Fin de la compatibilidad con la administración heredada de equipos

La administración heredada de equipos dejará de ser compatible el 15 de octubre de 2020. Actualice los dispositivos a Windows 10 y vuelva a inscribirlos como dispositivos MDM para administrarlos por Intune.

[Más información](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Reducción de la compatibilidad con el administrador de dispositivos Android 
El administrador de dispositivos Android (que a veces se conoce como "administración de Android heredada" y publicada con Android 2.2) es una manera de administrar dispositivos Android. Sin embargo, ahora hay una funcionalidad de administración mejorada disponible con [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (publicada con Android 5.0). Con el fin de realizar la transición a la administración de dispositivos moderna, más completa y segura, Google va a reducir la compatibilidad con el administrador de dispositivos en las nuevas versiones de Android.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Debido a estos cambios de Google, los usuarios de Intune se verán afectados de las siguientes maneras:  
- Intune solo podrá proporcionar compatibilidad con dispositivos Android administrados por el administrador de dispositivos que ejecuten Android 10 y versiones posteriores (también conocido como "Android Q") hasta el verano 2020. Es en esta fecha cuando se espera que se lance la versión principal de Android.   
- Los dispositivos administrados por el administrador de dispositivos que ejecutan Android 10 o posterior después del verano de 2020 ya no se podrán administrar por completo.       
- Los dispositivos Android administrados por el administrador de dispositivos que permanezcan en versiones de Android inferiores a Android 10 no se verán afectados y se podrán seguir administrando por completo con el administrador de dispositivos.    
- En todos los dispositivos Android 10 y versiones posteriores, Google ha restringido a los agentes de administración del administrador de dispositivos, como el Portal de empresa, el acceso a la información de identificación del dispositivo. Esta situación afecta a las siguientes características de Intune después de que un dispositivo se actualice a Android 10 o una versión posterior:  
    - El control de acceso a la red de VPN dejará de funcionar.   
    - La identificación de los dispositivos como propiedad de la empresa con el número IMEI o el número de serie no marcará automáticamente los dispositivos como propiedad de la empresa.  
    - El número IMEI y el número de serie ya no serán visibles para los administradores de TI en Intune. 
        > [!NOTE]
        > Esta situación solo afecta a los dispositivos administrados por el administrador de dispositivos en Android 10 y versiones posteriores; no a los administrados con Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Para evitar la reducción de la funcionalidad que tendrá lugar en el verano de 2020, siga estas recomendaciones:
- No incorpore nuevos dispositivos a la administración del administrador de dispositivos.
- Si está previsto que un dispositivo reciba una actualización de Android 10, mígrelo de la administración del administrador de dispositivos a la administración de Android Enterprise o a las directivas de protección de aplicaciones.

#### <a name="additional-information"></a>Información adicional
- [Guía de Google para la migración desde el administrador de dispositivos a Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentación de Google sobre el plan para dejar de usar la API del administrador de dispositivos](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Actualización de la aplicación del Portal de empresa de Android a la versión más reciente <!--4536963-->
Intune publica actualizaciones periódicamente de la aplicación del Portal de empresa de Android. En noviembre de 2018 publicamos una actualización del Portal de empresa, que incluía un conmutador de back-end, en preparación para el cambio de Google de su plataforma de notificación a Firebase Cloud Messaging (FCM). Cuando Google retire su plataforma de notificación existente y se traslade a FCM, los usuarios finales deberán haber actualizado la aplicación del Portal de empresa al menos a la versión de noviembre de 2018 para seguir comunicándose con Google Play Store.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Nuestra telemetría indica que tiene dispositivos con una versión anterior a 5.0.4269.0 del Portal de empresa. Si no está instalada esta versión o una versión posterior de la aplicación del Portal de empresa, las acciones del dispositivo iniciadas por profesionales de TI, como el borrado, el restablecimiento de la contraseña, las instalaciones de aplicaciones requeridas y disponibles y la inscripción de certificados pueden no funcionar según lo previsto. Si sus dispositivos están inscritos en MDM en Intune, puede ver las versiones y los usuarios del portal de empresa en Aplicaciones cliente - Aplicaciones detectadas. La selección de versiones anteriores de la aplicación del Portal de empresa le permitirá ver qué usuarios finales tienen los dispositivos que no han actualizado la aplicación del Portal de empresa.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Pida a los usuarios finales de dispositivos Android que no hayan actualizado la aplicación del Portal de empresa que lo hagan mediante Google Play. Ponga en conocimiento del departamento de soporte técnico aquellos casos en que un usuario no haya mantenido la actualización automática de la aplicación del Portal de empresa. Consulte el vínculo de *Información adicional* para obtener más información sobre los cambios y la plataforma FCM de Google.

#### <a name="additional-information"></a>Información adicional
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Nueva experiencia de pantalla completa en Intune <!--4593669-->
Estamos implementando una actualización de las experiencias de creación e implementación de interfaz de usuario en Intune en Azure Portal. Esta nueva experiencia simplificará los flujos de trabajo mediante el uso de un formato de estilo de asistente condensado en una hoja. Esta actualización eliminará la "expansión de la hoja" o cualquier flujo de creación y edición que implique que sea necesario explorar en profundidad los recorridos detallados de la hoja. Los flujos de trabajo de creación también se actualizarán para incluir asignaciones (excepto para asignación de aplicaciones).

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
La experiencia de pantalla completa se implementará en Intune tanto en portal.azure.com como en devicemanagement.microsoft.com durante los próximos meses. Esta actualización de la interfaz de usuario no afectará la funcionalidad de las directivas y perfiles existentes, pero sí verá un flujo de trabajo algo modificado. Por ejemplo, al crear directivas podrá establecer ciertas asignaciones como parte de este flujo en lugar de hacerlo después de crear la directiva. Consulte la entrada de blog en *Información adicional* para ver capturas de pantalla de cómo se verá la experiencia nueva en la consola.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
No es necesario realizar ninguna acción, pero puede considerar la posibilidad de actualizar las instrucciones para los profesionales de TI si es necesario. Actualizaremos la documentación al implementar esta experiencia en distintas hojas de Intune en Azure Portal.

#### <a name="additional-information"></a>Información adicional 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Plan de cambio: Intune App SDK y las directivas de protección de aplicaciones de Android van a ser compatibles con Android 5.0 y posterior en una próxima versión. <!--4911065 -->
Intune pasará a ser compatible con Android 5.x (Lollipop) y posterior en una próxima versión. Actualice las aplicaciones encapsuladas con la instancia de Intune App SDK más reciente y actualice los dispositivos.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Si no va a usar, ni tiene pensado usar, el SDK o la aplicación para Android, este cambio no le afectará. Si va a usar Intune App SDK, asegúrese de actualizarse a la versión más reciente y también actualice los dispositivos a Android 5.x y versiones posteriores. Si no realiza la actualización, las aplicaciones no recibirán actualizaciones y la calidad de su experiencia empeorará con el tiempo.

A continuación, encontrará una lista de dispositivos comunes inscritos en Intune que ejecutan Android versión 4.x. Si tiene uno de estos dispositivos, siga los pasos adecuados para asegurarse de que sea compatible con Android 5.0 o superior o de que se va a reemplazar por un dispositivo que admita la versión 5.0 o posterior de Android. Esta lista no incluye todos los dispositivos que puede ser necesario evaluar:

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Encapsule las aplicaciones con la versión más reciente de Intune App SDK. También puede establecer la configuración de inicio condicional "Requerir versión mínima del sistema operativo (solo advertencia)" para notificar a los usuarios finales los dispositivos personales que se van a actualizar.

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Plan de cambio de Intune: Se aproxima el final del soporte técnico de Windows 7<!-- 3042987 -->
Tal y como informamos en el mensaje MC148476, con fecha de septiembre de 2018, y de nuevo en el mensaje MC176794, de marzo de 2019, Windows 7 llegará al final del soporte técnico extendido el 14 de enero de 2020. En ese momento, Intune retirará la compatibilidad con los dispositivos que ejecutan Windows 7. Así podremos centrar nuestra inversión en respaldar las tecnologías más recientes y en ofrecer nuevas y excelentes experiencias de usuario final. Después de esa fecha, la asistencia técnica y las actualizaciones automáticas que ayudan a proteger los equipo con Windows 7 ya no estarán disponibles a través de Intune. Microsoft recomienda encarecidamente que actualice a Windows 10 antes de enero de 2020, para evitar que pueda necesitar servicios o soporte técnico que ya no estén disponibles. Obtenga más información sobre el ciclo de vida de soporte técnico de Windows [aquí](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Le hemos enviado este mensaje porque actualmente está administrando equipos con Windows 7 mediante el agente de software de PC de Intune heredado. Debido a que queda menos de un año antes de que finalice el ciclo de vida de soporte técnico extendido de Windows 7, recomendamos encarecidamente que su organización empiece a actualizar los equipos a Windows 10 lo antes posible.  

Las funcionalidades de administración de equipos se crean directamente en el sistema operativo Windows 10 y ya no es necesario instalar un agente cliente, como el cliente de software Intune para Windows 7. A partir de Windows 8.1, Microsoft utiliza la arquitectura de administración de dispositivos móviles (MDM) para aprovisionar, configurar, actualizar y administrar equipos con Windows. Una vez que haya configurado Intune, puede simplificar el proceso de inscripción de Windows [inscribiendo los equipos con Windows 10 en Intune](..\windows-enroll.md) a través del canal MDM. Recomendamos usar esta solución de administración de MDM "sin agente" para administrar los equipos con Windows 10.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Recomendamos que en su organización se tenga en cuenta inmediatamente este plan de acción:

- Planee y actualice la flota de Windows 7 a Windows 10 antes del 14 de enero de 2020.
- Explore la [compatibilidad con la implementación de Windows 10](https://docs.microsoft.com/windows/deployment/) para obtener más información sobre cómo actualizar la flota de equipos con Windows 7 a Windows 10.
- Revise la oferta de [Asesoría de aplicaciones de escritorio](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) a través de FastTrack, que ayudará a que se cumpla la promesa de Microsoft en cuanto a la compatibilidad de las aplicaciones.
- Realice la transición de los dispositivos administrados del cliente de software Intune heredado a la solución recomendada de Microsoft para administrar Windows 10 mediante la administración de MDM. Inscriba todos los nuevos equipos con Windows 10 mediante la administración de MDM para Intune en Azure Portal.

Vea la [entrada de blog publicada aquí](https://aka.ms/Windows7_Intune) para obtener más información.
