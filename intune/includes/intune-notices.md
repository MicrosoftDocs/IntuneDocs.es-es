---
title: archivo include
description: archivo include
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 8db05399c4a880d72d24cde885976309bf9a4fa7
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74549506"
---
Estos avisos proporcionan información importante que puede ayudarle a prepararse para las características y los cambios futuros de Intune.

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Actualizada la instrucción de soporte técnico para la aplicación móvil de Adobe Acrobat Reader para Intune<!--5746776-->
A finales de agosto, publicamos en MC188653 que la aplicación móvil de Adobe Acrobat Reader para Intune llegaría al final de su vida útil el 1 de diciembre de 2019 y que Adobe planeaba admitir las directivas de protección de aplicaciones de Intune dentro de su aplicación principal Acrobat Reader. Desde entonces, recibimos comentarios de los clientes solicitando más tiempo para permitir a los administradores de TI dirigirse a Adobe Acrobat Reader para Intune y a los usuarios finales empezar a utilizarlo. Dado el alto uso de Adobe Acrobat Reader para Intune en los dispositivos de los usuarios finales y su importancia en escenarios empresariales, queremos asegurarnos de que cualquier experiencia cumpla las necesidades de protección de las aplicaciones de su organización. 

Aunque seguimos recomendando establecer como destino la aplicación móvil de Acrobat Reader general en las directivas, ya que la aplicación móvil de Acrobat Reader es compatible con las directivas de protección de aplicaciones y ha integrado el SDK de Intune, se seguirá admitiendo la aplicación Adobe Acrobat Reader para Intune hasta el 31 de marzo de 2020. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Está recibiendo este mensaje porque nuestros informes señalan que una o más directivas de la organización tienen como destino la aplicación Adobe Acrobat Reader para Intune o bien ha recibido nuestra comunicación de EOL anterior. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Informe a los usuarios finales y el departamento de soporte técnico sobre este cambio. Puede usar la [funcionalidad de la información de soporte técnico del Portal de empresa](../apps/company-portal-app.md#support-information) para establecer un canal para preguntas relacionadas con Intune.

#### <a name="additional-information"></a>Información adicional
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Final del soporte técnico para Windows Phone 8.1<!--3544909-->
El soporte estándar de Microsoft para Windows Phone 8.1 finalizó en julio de 2017, y el soporte ampliado finalizó en junio de 2019. La aplicación Portal de empresa para Windows Phone 8.1 está en modo de mantenimiento desde octubre de 2017. Microsoft Intune pondrá ahora fin al soporte técnico el 20 de febrero de 2020 para Windows Phone 8.1.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Después del 20 de febrero de 2020 estos dispositivos no recibirán ninguna actualización de seguridad y no podrá inscribir ningún dispositivo nuevo. Los dispositivos Windows Phone 8.1 existentes permanecerán inscritos (directiva, aplicaciones e informes), pero tenga en cuenta que después de esa fecha no se podrán solucionar problemas de inscripciones existentes, ya que muchos componentes, como los certificados de terceros, ya no son compatibles con la plataforma. Intune detendrá las pruebas de compatibilidad con Intune y Windows Phone 8.1.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Puede comprobar los informes de Intune para ver qué dispositivos o usuarios pueden verse afectados. Vaya a Dispositivos > Todos los dispositivos y filtre por el sistema operativo. Puede agregar columnas adicionales para ayudar a identificar qué usuarios de su organización tienen dispositivos que ejecutan Windows Phone 8.1. Pida a los usuarios finales que actualicen sus dispositivos a una versión del sistema operativo compatible.

### <a name="update-your-intune-outlook-app-protection-policies-app--2576686--"></a>Actualización de las directivas de protección de aplicaciones (APP) de Outlook en Intune<!--2576686-->
Es posible que tenga que tomar medidas si ha recibido MC195618 en el centro de mensajes. Como se compartía en los identificadores de características de la hoja de ruta de Microsoft 365: 56325 y 56326, Intune y Outlook para iOS y Android están implementando la compatibilidad para limitar la información confidencial en las notificaciones de correo electrónico y los recordatorios de calendario. Como resultado de estas mejoras, Outlook para iOS y Android quitará la compatibilidad con varias claves de configuración de aplicaciones de protección de datos que actualmente está empleando para administrar las notificaciones.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Aunque las nuevas características aún no se han publicado, tan pronto estén disponibles las siguientes claves de configuración de aplicaciones dejarán de funcionar en Outlook para iOS y Android:
- com.microsoft.outlook.Mail.NotificationsEnabled
- com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed
- com.microsoft.outlook.Calendar.NotificationsEnabled
- com.microsoft.outlook.Calendar.NotificationsEnabled.UserChangeAllowed

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Le recomendamos que configure la opción de protección de datos de la directiva de Intune App Protection "Notificaciones de datos de la organización" en la opción "Bloquear datos de la organización" para prepararse ante esta nueva característica. A partir del 16 de diciembre de 2019, Outlook para iOS y Android aceptará la configuración de protección de datos "Notificaciones de datos de la organización" y ya no admitirá las claves mencionadas anteriormente. La configuración de este nuevo parámetro garantizará que los datos confidenciales no se filtren cuando las claves de configuración anteriores ya no se admitan. Además, Outlook proporciona granularidad adicional cuando la opción de protección de datos "Notificaciones de datos de la organización" esté establecida en "Bloquear datos de la organización" con una opción de configuración de aplicación adicional, "Notificaciones de calendario". La combinación de la configuración de la directiva de protección de aplicaciones y esta opción de configuración de las aplicaciones limita la información confidencial en las notificaciones de correo, a la vez que expone información confidencial en las notificaciones de calendario para que los usuarios puedan acceder a sus reuniones echando un vistazo rápido a la notificación o al centro de notificaciones.

#### <a name="additional-information"></a>Información adicional
Para obtener más información sobre la configuración de la aplicación y la configuración de Outlook, consulte:
- [Configuración de directivas de protección de aplicaciones de Android](../apps/app-protection-policy-settings-android.md)
- [Configuración de directivas de protección de aplicaciones de iOS](../apps/app-protection-policy-settings-ios.md)
- [Implementación de las opciones de configuración de la aplicación de Outlook para iOS y Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)


### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Plan de cambio de Intune: fin de la compatibilidad del Portal de empresa en la versión 1703 de Windows 10<!--5026679-->
La versión 1703 de Windows 10 (también conocida como Windows 10, RS2) se ha quedado sin servicio el 8 de octubre de 2019 para las ediciones Enterprise y EDU. Intune pondrá fin la compatibilidad con la aplicación de Portal de empresa correspondiente para RS2/RS1 a partir del 26 de diciembre de 2019.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
En adelante, no verá las nuevas características de la versión específica de la aplicación Portal de empresa, aunque seguiremos admitiendo esta versión de la aplicación Portal de empresa hasta el 26 de diciembre de 2019, incluida la provisión de las actualizaciones de seguridad a la aplicación Portal de empresa según se requiera. Sin embargo, como la versión 1703 de Windows 10 no recibirá ninguna actualización de seguridad una vez que se excluya del servicio, le recomendamos encarecidamente que actualice los dispositivos Windows a una versión más reciente de Windows y que se asegure de que tiene la aplicación Portal de empresa más reciente para que seguir recibiendo nuevas características y funcionalidad adicional.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Los pasos que debe adoptar dependerán de cómo esté configurado el entorno. Sin embargo, en general, debe identificar los dispositivos que tienen la versión anterior del sistema operativo o el Portal de empresa instalado y actualizarlos. Para configurar los anillos de actualización de Windows 10, inicie sesión en Intune-> actualizaciones de software - Anillos de actualización de Windows 10. La versión más reciente del Portal de empresa es 10.3.5601.0. Pida a los usuarios que la adquieran en Microsoft Store para mantenerse al día con versiones futuras. También puede usar Intune para instalar la versión más reciente en los dispositivos Windows a través de [Microsoft Store para Empresas](https://docs.microsoft.com/intune/windows-store-for-business).

#### <a name="additional-information"></a>Información adicional
[Adición manual de la aplicación Portal de empresa para Windows 10 con Microsoft Intune](https://docs.microsoft.com/intune/store-apps-company-portal-app)


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Realizar acción: uso de Microsoft Edge para la experiencia de explorador de Intune protegida<!--5728447-->
Como hemos venido anunciando en este último año, Microsoft Edge para dispositivos móviles admite el mismo conjunto de características de administración que Managed Browser, proporcionando al mismo tiempo una experiencia de usuario final mucho mejor. Para dar paso a las sólidas experiencias que proporciona Microsoft Edge, retiraremos Intune Managed Browser. A partir del 27 de enero de 2020, Intune ya no será compatible con Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto? 
A partir del 1 de febrero de 2020, Intune Managed Browser ya no estará disponible en Google Play Store o ni en la App Store de iOS. En este punto, aún podrá dirigir nuevas políticas de protección de aplicaciones a Intune Managed Browser, aunque los nuevos usuarios no podrán descargar la aplicación Intune Managed Browser. Además, en iOS, los nuevos clips de web que se inserten en el dispositivo inscrito en MDM se abrirán en Microsoft Edge en lugar de hacerlo en Intune Managed Browser.  

El 31 de marzo de 2020, Intune Managed Browser se quitará de la consola de Azure. Esto significa que ya no podrá crear nuevas directivas para Intune Managed Browser. Las directivas de Intune Managed Browser que tenga actualmente no se verán afectadas. Intune Managed Browser se mostrará en la consola como una aplicación LOB sin icono, y las directivas existentes se seguirán dirigiendo a la aplicación. En este punto, también se quitará la opción de redirigir el contenido web a Intune Managed Browser en la sección Protección de datos de las directivas de protección de aplicaciones.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio? 
Para garantizar una transición fluida de Intune Managed Browser a Microsoft Edge, se recomienda realizar los siguientes pasos de forma proactiva: 

1. Dirija la directiva de protección de aplicaciones (también conocida como MAM) y los parámetros de configuración de la aplicación a Microsoft Edge para iOS y Android. Puede reutilizar las directivas de Intune Managed Browser para Microsoft Edge destinando tales directivas también a Microsoft Edge.  
2. Asegúrese de que todas las aplicaciones protegidas por MAM del entorno tienen la opción de la directiva de protección de aplicaciones "Restringir la transferencia de contenido web con otras aplicaciones" establecida en "Exploradores administrados por directivas". 
3. Diríjase a todas las aplicaciones protegidas por MAM con el parámetro de configuración "com.microsoft.intune.useEdge" establecido en true. A partir del próximo mes, con la versión 1911, podrá llevar a cabo los pasos 2 y 3 simplemente configurando la opción "Restringir la transferencia de contenido web con otras aplicaciones" de manera que tenga "Microsoft Edge" seleccionado en la sección Protección de datos de las directivas de protección de aplicaciones. 

La compatibilidad con los clips de web en iOS y Android estará próximamente disponible. Cuando se publique esta versión, tendrá que cambiar el destino de los clips de web preexistentes para asegurarse de que se abren en Microsoft Edge en lugar de en Managed Browser. 

#### <a name="additional-information"></a>Información adicional
Visite nuestros documentos sobre [el uso de Microsoft Edge con directivas de protección de aplicaciones](../apps/manage-microsoft-edge.md) para obtener más información, o consulte nuestra [entrada de blog sobre soporte técnico](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).

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

### <a name="end-of-support-for-legacy-pc-management"></a>Fin de la compatibilidad con la administración heredada de equipos

La administración heredada de equipos dejará de ser compatible el 15 de octubre de 2020. Actualice los dispositivos a Windows 10 y vuelva a inscribirlos como dispositivos de administración de dispositivos móviles (MDM) para administrarlos por Intune.

[Más información](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Reducción de la compatibilidad con el administrador de dispositivos Android 
El administrador de dispositivos Android (que a veces se conoce como "administración de Android heredada" y publicada con Android 2.2) es una manera de administrar dispositivos Android. Sin embargo, ahora hay una funcionalidad de administración mejorada disponible con [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (publicada con Android 5.0). Con el fin de realizar la transición a la administración de dispositivos moderna, más completa y segura, Google va a reducir la compatibilidad con el administrador de dispositivos en las nuevas versiones de Android.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Debido a estos cambios de Google, los usuarios de Intune se verán afectados de las siguientes maneras:  
- Intune solo podrá proporcionar compatibilidad con dispositivos Android administrados por el administrador de dispositivos que ejecuten Android 10 y versiones posteriores (también conocido como "Android Q") hasta el verano 2020. Es en esta fecha cuando se espera que se lance la versión principal de Android.   
- Los dispositivos administrados por el administrador de dispositivos que ejecutan Android 10 o posterior después del verano de 2020 ya no se podrán administrar por completo.       
- Los dispositivos Android administrados por el administrador de dispositivos que permanezcan en versiones de Android inferiores a Android 10 no se verán afectados y se podrán seguir administrando por completo con el administrador de dispositivos.    
- En todos los dispositivos Android 10 y versiones posteriores, Google ha restringido a los agentes de administración del administrador de dispositivos, como el Portal de empresa, el acceso a la información de identificación del dispositivo. Esta restricción afecta a las siguientes características de Intune después de que un dispositivo se actualice a Android 10 o una versión posterior:  
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


