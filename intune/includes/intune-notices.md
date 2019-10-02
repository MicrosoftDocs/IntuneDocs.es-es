---
title: archivo include
description: archivo include
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fa251a0edd943d566849b138af5cbab0be248a53
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726406"
---
Estos avisos proporcionan información importante que puede ayudarle a prepararse para las características y los cambios futuros de Intune. 


### <a name="decreasing-support-for-android-device-administrator"></a>Reducción de la compatibilidad con el administrador de dispositivos Android 
El administrador de dispositivos Android (que a veces se conoce como administración de Android "heredada" y publicada con Android 2.2) es una manera de administrar dispositivos Android. Sin embargo, ahora hay una funcionalidad de administración mejorada disponible con [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (publicada con Android 5.0). Con el fin de realizar la transición a la administración de dispositivos moderna, más completa y segura, Google va a reducir la compatibilidad con el administrador de dispositivos en las nuevas versiones de Android.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Debido a estos cambios de Google, los usuarios de Intune se verán afectados de las siguientes maneras: 
- Intune solo podrá proporcionar compatibilidad con dispositivos Android administrados por el administrador de dispositivos que ejecuten Android 10 y versiones posteriores (también conocido como Android Q) hasta el verano 2020. Es en esta fecha cuando se espera que se lance la versión principal de Android.  
- Los dispositivos administrados por el administrador de dispositivos que ejecutan Android 10 o posterior después del verano de 2020 ya no se podrán administrar por completo.    
- Los dispositivos Android administrados por el administrador de dispositivos que permanezcan en versiones de Android inferiores a Android 10 no se verán afectados y se podrán seguir administrando por completo con el administrador de dispositivos.  
- En todos los dispositivos Android 10 y versiones posteriores, Google ha restringido a los agentes de administración del administrador de dispositivos, como el Portal de empresa, el acceso a la información de identificación del dispositivo. Esta situación afecta a las siguientes características de Intune después de que un dispositivo se actualice a Android 10 o una versión posterior: 
    - El control de acceso a la red de VPN dejará de funcionar.  
    - La identificación de los dispositivos como propiedad de la empresa con el número IMEI o el número de serie no marcará automáticamente los dispositivos como propiedad de la empresa. 
    - El número IMEI y el número de serie ya no serán visibles para los administradores de TI en Intune. 
        > [!Note]
        > Esta situación solo afecta a los dispositivos administrados por el administrador de dispositivos en Android 10 y versiones posteriores; no a los administrados con Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Para evitar la reducción de la funcionalidad que tendrá lugar en el verano de 2020, siga estas recomendaciones:
- No incorpore nuevos dispositivos a la administración del administrador de dispositivos.
- Si está previsto que un dispositivo reciba una actualización de Android 10, mígrelo de la administración del administrador de dispositivos a la administración de Android Enterprise o a las directivas de protección de aplicaciones.

#### <a name="additional-information"></a>Información adicional
- [Guía de Google para la migración desde el administrador de dispositivos a Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentación de Google sobre el plan para dejar de usar la API del administrador de dispositivos](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Actualización de la aplicación del Portal de empresa de Android a la versión más reciente <!--4536963-->
Intune publica actualizaciones periódicamente de la aplicación del Portal de empresa de Android. En noviembre de 2018 publicamos una actualización del Portal de empresa, que incluía un conmutador de back-end, en preparación para el cambio de Google de su plataforma de notificación existente a Firebase Cloud Messaging (FCM). Cuando Google retire su plataforma de notificación existente y se traslade a FCM, los usuarios finales deberán haber actualizado la aplicación del Portal de empresa al menos a la versión de noviembre de 2018 para seguir comunicándose con Google Play Store.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Nuestra telemetría indica que tiene dispositivos con una versión anterior a 5.0.4269.0 del Portal de empresa. Si no está instalada esta versión o una versión posterior de la aplicación del Portal de empresa, las acciones del dispositivo iniciadas por profesionales de TI, como el borrado, el restablecimiento de la contraseña, las instalaciones de aplicaciones requeridas y disponibles y la inscripción de certificados pueden no funcionar según lo previsto. Si sus dispositivos están inscritos en MDM en Intune, puede ver las versiones y los usuarios del portal de empresa en Aplicaciones cliente - Aplicaciones detectadas. La selección de versiones anteriores del Portal de empresa le permitirá ver qué usuarios finales tienen los dispositivos que no han actualizado el Portal de empresa.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Pida a los usuarios finales de dispositivos Android que no hayan actualizado el Portal de empresa que lo hagan mediante Google Play. Ponga en conocimiento del departamento de soporte técnico aquellos casos en que un usuario no haya mantenido la actualización automática de la aplicación del Portal de empresa. Consulte el vínculo de información adicional para obtener más información sobre los cambios y la plataforma FCM de Google.

#### <a name="additional-information"></a>Información adicional
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Nueva experiencia de pantalla completa en Intune <!--4593669-->
Estamos implementando una actualización de las experiencias de creación e implementación de interfaz de usuario en Intune en Azure Portal. Esta nueva experiencia simplificará los flujos de trabajo existentes mediante el uso de un formato de estilo de asistente condensado en una hoja. Esta actualización eliminará la "expansión de la hoja" o cualquier flujo de creación y edición que implique que sea necesario explorar en profundidad los recorridos detallados de la hoja. Los flujos de trabajo de creación también se actualizarán para incluir asignaciones (excepto para Asignación de aplicaciones).

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
La experiencia de pantalla completa se implementará en Intune tanto en portal.azure.com como en devicemanagement.microsoft.com durante los próximos meses. Esta actualización de la interfaz de usuario no afectará la funcionalidad de las directivas y perfiles existentes, pero sí verá un flujo de trabajo algo modificado. Por ejemplo, al crear directivas podrá establecer ciertas asignaciones como parte de este flujo en lugar de hacerlo después de crear la directiva. Consulte la entrada de blog en Información adicional para ver capturas de pantalla de cómo se verá la experiencia nueva en la consola.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
No es necesario realizar ninguna acción, pero puede considerar la posibilidad de actualizar las instrucciones para los profesionales de TI si es necesario. Actualizaremos la documentación al implementar esta experiencia en distintas hojas de Intune en Azure Portal.

#### <a name="additional-information"></a>Información adicional 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>Plan de cambio: Nueva configuración de actualizaciones de Windows en Intune <!-- 4464404 -->
A partir de la versión de agosto del servicio de Intune o actualización 1908, estamos agregando una nueva "configuración de la fecha límite" que puede configurar en lugar de la configuración "Permitir al usuario que reinicie (reinicio establecido)". Planeamos deshabilitar la configuración del reinicio establecido en la interfaz de usuario en la actualización 1909 o en la actualización de septiembre y luego quitarlos completamente de la consola hacia finales de octubre.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Si administra dispositivos de Windows 10 en su entorno:

- Con la actualización de Intune de agosto o 1908, verá una nueva configuración de la fecha límite en la consola, además de la antigua configuración del reinicio establecido.
- Cuando se configuran estos dos valores, la configuración de la fecha límite sustituyen a los valores de la configuración del reinicio establecido.
- La configuración de la fecha límite reemplazará la opción "Permitir al usuario que reinicie (reinicio establecido) en la consola de la actualización 1910.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
Empiece a usar la configuración de la fecha límite en la actualización 1908 con los valores deseados. Una vez que lo haya hecho, puede configurar el valor de reinicio establecido en "Sin configurar" para preparar su retirada de la consola en octubre.

Actualice la documentación y cualquier script de automatización si es necesario.

Le mantendremos informado y enviaremos un recordatorio al centro de mensajes antes de quitar la configuración del reinicio establecido.

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>Plan de cambio: Intune App SDK y las directivas de protección de aplicaciones de Android van a pasar a ser compatible con Android 5.0 y versiones posteriores en octubre <!--4911065 -->
Intune pasará a ser compatible con Android 5.x (Lollipop) y versiones posteriores en octubre. Actualice las aplicaciones encapsuladas con la instancia de Intune App SDK más reciente y actualice los dispositivos.

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

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Plan de cambio de Intune: aproximación de la finalización del ciclo de vida de soporte técnico de Windows 7 <!-- 3042987 -->
Tal y como informamos en el mensaje MC148476, con fecha de septiembre de 2018, y de nuevo en el mensaje MC176794, de marzo de 2019, Windows 7 llegará al final del soporte técnico extendido el 14 de enero de 2020. En ese momento, Intune retirará la compatibilidad con los dispositivos que ejecutan Windows 7. Así podremos centrar nuestra inversión en respaldar las tecnologías más recientes y en ofrecer nuevas y excelentes experiencias de usuario final. Después de esa fecha, la asistencia técnica y las actualizaciones automáticas que ayudan a proteger los equipo con Windows 7 ya no estarán disponibles a través de Intune. Microsoft recomienda encarecidamente que actualice a Windows 10 antes de enero de 2020, para evitar que pueda necesitar servicios o soporte técnico que ya no estén disponibles. Obtenga más información sobre el ciclo de vida de soporte técnico de Windows [aquí](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Le hemos enviado este mensaje porque actualmente está administrando equipos con Windows 7 mediante el agente de software de PC de Intune heredado. Debido a que queda menos de un año antes de que finalice el ciclo de vida de soporte técnico extendido de Windows 7, recomendamos encarecidamente que su organización empiece a actualizar los equipos a Windows 10 lo antes posible. Las funcionalidades de administración de equipos se crean directamente en el sistema operativo Windows 10 y ya no es necesario instalar un agente cliente, como el cliente de software Intune para Windows 7. A partir de Windows 8.1, Microsoft utiliza la arquitectura de administración de dispositivos móviles (MDM) para aprovisionar, configurar, actualizar y administrar equipos con Windows. Una vez que haya configurado Intune, puede simplificar el proceso de inscripción de Windows [inscribiendo los equipos con Windows 10 en Intune](..\windows-enroll.md) a través del canal MDM. Recomendamos usar esta solución de administración de MDM "sin agente" para administrar los equipos con Windows 10.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Recomendamos que en su organización se tenga en cuenta inmediatamente este plan de acción:

- Planee y actualice la flota de Windows 7 a Windows 10 antes del 14 de enero de 2020.
- Explore la [compatibilidad con la implementación de Windows 10](https://docs.microsoft.com/windows/deployment/) para obtener más información sobre cómo actualizar la flota de equipos con Windows 7 a Windows 10.
- Revise la oferta de [Asesoría de aplicaciones de escritorio](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) a través de FastTrack, que ayudará a que se cumpla la promesa de Microsoft en cuanto a la compatibilidad de las aplicaciones.
- Realice la transición de los dispositivos administrados del cliente de software Intune heredado a la solución recomendada de Microsoft para administrar Windows 10 mediante la administración de MDM. Inscriba todos los nuevos equipos con Windows 10 mediante la administración de MDM para Intune en Azure Portal.
- Vea la [entrada de blog publicada aquí](https://aka.ms/Windows7_Intune) para obtener más información.
