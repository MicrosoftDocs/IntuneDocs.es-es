---
title: archivo include
description: archivo include
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 041f37e56e85b0ac26a4dd7a9dbbdb49bc0ebd9e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166339"
---
Estos avisos proporcionan información importante que puede ayudarle a prepararse para las características y los cambios futuros de Intune. 


### <a name="decreasing-support-for-android-device-administrator"></a>Reducción de la compatibilidad con el administrador de dispositivos Android 
El administrador de dispositivos Android (que a veces se conoce como administración de Android "heredada" y publicada con Android 2.2) es una manera de administrar dispositivos Android. Sin embargo, ahora hay una funcionalidad de administración mejorada disponible con [Android Enterprise](../connect-intune-android-enterprise.md) (publicada con Android 5.0). Con el fin de realizar la transición a la administración de dispositivos moderna, más completa y segura, Google va a reducir la compatibilidad con el administrador de dispositivos en las nuevas versiones de Android.

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

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665324--"></a>Plan de cambio: Intune admitirá iOS 11 y versiones posteriores a partir de septiembre <!-- 4665324-->
Esperamos que Apple lance iOS 13 en septiembre. La inscripción de Intune, el Portal de empresa y el explorador administrado pasarán a admitir iOS 11 y versiones posteriores poco después del lanzamiento de iOS 13.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Puesto que iOS 11.0 y las versiones posteriores admiten las aplicaciones móviles de O365, puede ser que esto no le afecte. Es probable que ya haya actualizado la versión de su sistema operativo o de sus dispositivos. Con todo, si posee o quiere inscribir alguno de los siguientes dispositivos, debe saber que no admiten sistemas operativos posteriores a iOS 10. Estos dispositivos deben actualizarse a un dispositivo que admita iOS 11 o versiones posteriores:

- iPhone 5
- iPhone 5c
- iPad (4.ª generación)

Si usa directivas de protección de aplicaciones (APP, por sus siglas en inglés), también puede establecer la configuración de acceso "Requerir sistema operativo iOS mínimo (solo es una advertencia)".

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Compruebe los informes de Intune para ver qué dispositivos o usuarios pueden verse afectados. Vaya a **Dispositivos** > **Todos los dispositivos** y filtre por sistema operativo. Puede agregar columnas adicionales para ayudar a identificar qué usuarios de su organización tienen dispositivos que ejecutan iOS 10. Pida a los usuarios finales que actualicen sus dispositivos a una versión del sistema operativo compatible antes de septiembre.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Plan de cambio: Compatibilidad con la versión 8.1.1 y versiones posteriores de Intune App SDK para iOS <!-- 3586942-->
A partir de septiembre de 2019, Intune pasará a admitir aplicaciones de iOS con Intune App SDK 8.1.1 y versiones posteriores. Ya no se admitirán las aplicaciones creadas con versiones del SDK inferiores a 8.1.1. Este cambio entrará en vigor con el lanzamiento de iOS 13 por parte de Apple, que está previsto para septiembre y se ha anunciado en MC181399.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Con la integración de Intune App SDK o el ajuste de aplicaciones, puede proteger los datos corporativos de aplicaciones y usuarios no aprobados mediante el cifrado de datos. El SDK de aplicaciones de Intune para iOS usará las claves de cifrado de 256 bits de forma predeterminada cuando el cifrado esté habilitado mediante las directivas de protección de aplicaciones (APP). Después de este cambio, las aplicaciones de iOS en versiones de SDK anteriores a la 8.1.1, que utilizan claves de cifrado de 128 bits, ya no podrán compartir datos con las aplicaciones integradas con SDK 8.1.1 o con claves de 256 bits. Todas las aplicaciones de iOS deberán tener una versión de SDK de 8.1.1 o posterior para permitir el uso compartido de datos.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
Compruebe sus aplicaciones de Microsoft, de terceros y de línea de negocio (LOB). Asegúrese de que todas sus aplicaciones protegidas con la aplicación de Intune usan la versión 8.1.1 del SDK o una posterior.

- Para aplicaciones de LOB: Es posible que deba volver a publicar las aplicaciones integradas con la versión 8.1.1 del SDK o con una versión posterior. Le recomendamos que utilice la versión más reciente del SDK. Para información sobre cómo preparar las aplicaciones de LOB para las directivas de protección de aplicaciones, consulte [Preparar aplicaciones de línea de negocio para las directivas de protección de aplicaciones](../apps-prepare-mobile-application-management.md).
- Para las aplicaciones de terceros o de Microsoft: Asegúrese de que está implementando la versión más reciente de estas aplicaciones a los usuarios.

También debe actualizar la documentación o las instrucciones para desarrolladores, si procede, para que incluyan este cambio en el soporte técnico para el SDK.

#### <a name="additional-information"></a>Información adicional
[Preparar aplicaciones de línea de negocio para las directivas de protección de aplicaciones](../apps-prepare-mobile-application-management.md)

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
