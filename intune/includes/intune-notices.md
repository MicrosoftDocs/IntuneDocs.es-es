---
title: archivo include
description: Archivo de inclusión
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 373aeea9ab4fcbd075ac2ab18f205f3ddd191a39
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609269"
---
Estos avisos proporcionan información importante que puede ayudarle a prepararse para las características y los cambios futuros de Intune.

### <a name="microsoft-intune-support-for-windows-10-mobile-ending--3544938--"></a>Fin del soporte técnico de Microsoft Intune para Windows 10 Mobile<!--3544938-->
El soporte técnico estándar de Microsoft para Windows 10 Mobile finalizó en diciembre de 2019. Como se ha mencionado en esta declaración de soporte técnico, los usuarios de Windows 10 Mobile dejarán de recibir de Microsoft nuevas actualizaciones de seguridad, revisiones no relacionadas con la seguridad, opciones gratuitas de soporte técnico asistido o actualizaciones de contenido técnico en línea. En lo referente a todo el soporte técnico del sistema operativo Mobile, el 11 de mayor de 2020 Microsoft Intune finalizará el soporte técnico del Portal de empresa de la aplicación de Windows 10 Mobile y del sistema operativo Windows 10 Mobile.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Si tiene dispositivos Windows 10 Mobile implementados en su organización, desde ahora y el 11 de mayo de 2020 puede inscribir nuevos dispositivos, agregar o quitar directivas y aplicaciones o actualizar cualquier configuración de administración. Sin embargo, a partir del 11 de mayo, se detendrán las nuevas inscripciones y, finalmente, se eliminará la administración de Windows 10 Mobile de la interfaz de usuario de Intune. Los dispositivos ya no se registrarán en el servicio de Intune y se eliminarán los datos de directivas y dispositivos.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué debo hacer para prepararme para este cambio?
Puede comprobar los informes de Intune para ver qué dispositivos o usuarios pueden verse afectados. Vaya a **Dispositivos** > **Todos los dispositivos** y filtre por sistema operativo. Puede agregar columnas adicionales para ayudar a identificar qué usuarios de su organización tienen dispositivos que ejecutan Windows 10 Mobile. Solicite a los usuarios finales que actualicen sus dispositivos o que dejen de usar los dispositivos para el acceso corporativo.



### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>Plan de cambio: Cambio de la experiencia al inscribir dispositivos dedicados de Android Enterprise en Intune<!--6114580-->
Comunicamos que en la versión de noviembre agregábamos compatibilidad con la implementación de certificados de SCEP en dispositivos dedicados de Android Enterprise para permitir el acceso basado en certificados a los perfiles de Wi-Fi. Este cambio implicaba algunos cambios de flujo de inscripción secundarios para dispositivos dedicados de Android Enterprise. Con la próxima actualización del servicio de marzo o 2003, hay algunos cambios más que nos gustaría que conocieran.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Si administra dispositivos dedicados de Android Enterprise en su entorno, comenzará a ver la implementación de algunos cambios en noviembre.
- Para dispositivos Android dedicados existentes inscritos antes del 22 de noviembre de 2019 o de la actualización del servicio 1911: Estos dispositivos tienen instalada la aplicación de Microsoft Intune. Después de que los cambios de back-end se implementen en el servicio de Intune en marzo, los certificados de SCEP implementados en los dispositivos y asociados a los perfiles de Wi-Fi comenzarán a aplicarse.
- En el caso de dispositivos que se inscribieron después del 22 de noviembre de 2019 y antes de estas implementaciones de cambios de marzo: Estos dispositivos tienen instalada la aplicación de Microsoft Intune. Los certificados de SCEP implementados en dispositivos y asociados a perfiles de Wi-Fi seguirán aplicándose.
- En el caso de nuevas inscripciones de dispositivos dedicados de Android Enterprise después de las implementaciones de cambios de marzo: Los usuarios finales verán un conjunto diferente de pasos en los dispositivos durante la inscripción. La inscripción comenzará de la misma manera que hoy (con QR, NFC, Zero-Touch o un identificador de dispositivo), pero no habrá un paso de instalación de la aplicación obligatorio. En su lugar, la aplicación de Microsoft Intune se instalará automáticamente en los dispositivos. Además, los usuarios finales no tendrán que pulsar "Enable Intune Agent" (Habilitar agente de Intune) durante el flujo. Los certificados de SCEP asociados a perfiles de Wi-Fi se pueden implementar en estos dispositivos.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
Puede actualizar las instrucciones para el usuario final y comunicar este cambio al departamento de soporte técnico. Actualizaremos nuestra página Novedades y le notificaremos a través del centro de mensajes cuando este cambio empiece a implementarse.

#### <a name="additional-information"></a>Información adicional
[Compatibilidad con certificados de SCEP en dispositivos dedicados de Android Enterprise](https://aka.ms/Dedicated_devices_enrollment)

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Actualizada la instrucción de soporte técnico para la aplicación móvil de Adobe Acrobat Reader para Intune<!--5746776-->
A finales de agosto, publicamos en MC188653 que la aplicación móvil de Adobe Acrobat Reader para Intune llegaría al final de su vida útil el 1 de diciembre de 2019 y que Adobe planeaba admitir las directivas de protección de aplicaciones de Intune dentro de su aplicación principal Acrobat Reader. Desde entonces, recibimos comentarios de los clientes solicitando más tiempo para permitir a los administradores de TI dirigirse a Adobe Acrobat Reader para Intune y a los usuarios finales empezar a utilizarlo. Dado el alto uso de Adobe Acrobat Reader para Intune en los dispositivos de los usuarios finales y su importancia en escenarios empresariales, queremos asegurarnos de que cualquier experiencia cumpla las necesidades de protección de las aplicaciones de su organización. 

Aunque seguimos recomendando establecer como destino la aplicación móvil de Acrobat Reader general en las directivas, ya que la aplicación móvil de Acrobat Reader es compatible con las directivas de protección de aplicaciones y ha integrado el SDK de Intune, se seguirá admitiendo la aplicación Adobe Acrobat Reader para Intune hasta el 31 de marzo de 2020. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Está recibiendo este mensaje porque nuestros informes señalan que una o más directivas de la organización tienen como destino la aplicación Adobe Acrobat Reader para Intune o bien ha recibido nuestra comunicación de EOL anterior. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué debo hacer para prepararme para este cambio?
Informe a los usuarios finales y el departamento de soporte técnico sobre este cambio. Puede usar la [funcionalidad de la información de soporte técnico del Portal de empresa](../apps/company-portal-app.md#support-information) para establecer un canal para preguntas relacionadas con Intune.

#### <a name="additional-information"></a>Información adicional
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Realizar acción: uso de Microsoft Edge para la experiencia de explorador de Intune protegida<!--5728447-->
Como hemos venido anunciando en este último año, Microsoft Edge para dispositivos móviles admite el mismo conjunto de características de administración que Managed Browser, proporcionando al mismo tiempo una experiencia de usuario final mucho mejor. Para dar paso a las sólidas experiencias que proporciona Microsoft Edge, retiraremos Intune Managed Browser. A partir del 27 de enero de 2020, Intune ya no será compatible con Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto? 
A partir del 1 de febrero de 2020, Intune Managed Browser ya no estará disponible en Google Play Store o ni en la App Store de iOS. En este punto, aún podrá dirigir nuevas políticas de protección de aplicaciones a Intune Managed Browser, aunque los nuevos usuarios no podrán descargar la aplicación Intune Managed Browser. Además, en iOS, los nuevos clips de web que se inserten en el dispositivo inscrito en MDM se abrirán en Microsoft Edge en lugar de hacerlo en Intune Managed Browser.  

El 31 de marzo de 2020, Intune Managed Browser se quitará de la consola de Azure. Esto significa que ya no podrá crear nuevas directivas para Intune Managed Browser. Las directivas de Intune Managed Browser que tenga actualmente no se verán afectadas. Intune Managed Browser se mostrará en la consola como una aplicación LOB sin icono, y las directivas existentes se seguirán dirigiendo a la aplicación. En este punto, también se quitará la opción de redirigir el contenido web a Intune Managed Browser en la sección Protección de datos de las directivas de protección de aplicaciones.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué debo hacer para prepararme para este cambio? 
Para garantizar una transición fluida de Intune Managed Browser a Microsoft Edge, se recomienda realizar los siguientes pasos de forma proactiva: 

1. Dirija la directiva de protección de aplicaciones (también conocida como MAM) y los parámetros de configuración de la aplicación a Microsoft Edge para iOS y Android. Puede reutilizar las directivas de Intune Managed Browser para Microsoft Edge destinando tales directivas también a Microsoft Edge.  
2. Asegúrese de que todas las aplicaciones protegidas por MAM del entorno tienen la opción de la directiva de protección de aplicaciones "Restringir la transferencia de contenido web con otras aplicaciones" establecida en "Exploradores administrados por directivas". 
3. Diríjase a todas las aplicaciones protegidas por MAM con el parámetro de configuración "com.microsoft.intune.useEdge" establecido en true. A partir del próximo mes, con la versión 1911, podrá llevar a cabo los pasos 2 y 3 simplemente configurando la opción "Restringir la transferencia de contenido web con otras aplicaciones" de manera que tenga "Microsoft Edge" seleccionado en la sección Protección de datos de las directivas de protección de aplicaciones. 

La compatibilidad con los clips de web en iOS y Android estará próximamente disponible. Cuando se publique esta versión, tendrá que cambiar el destino de los clips de web preexistentes para asegurarse de que se abren en Microsoft Edge, en lugar de en Managed Browser. 

#### <a name="additional-information"></a>Información adicional
Consulte la documentación sobre el [uso de Microsoft Edge con directivas de protección de aplicaciones](../apps/manage-microsoft-edge.md) para obtener más información. También puede leer nuestra [entrada de blog sobre el soporte técnico](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


### <a name="end-of-support-for-legacy-pc-management"></a>Fin de la compatibilidad con la administración heredada de equipos

La administración heredada de equipos dejará de ser compatible el 15 de octubre de 2020. Actualice los dispositivos a Windows 10 y vuelva a inscribirlos como dispositivos de administración de dispositivos móviles (MDM) para administrarlos por Intune.

[Más información](https://go.microsoft.com/fwlink/?linkid=2107122).

### <a name="decreasing-support-for-android-device-administrator--5857738--"></a>Reducción de la compatibilidad con el administrador de dispositivos Android<!--5857738-->
El administrador de dispositivos Android (que a veces se conoce como "administración de Android heredada" y publicada con Android 2.2) es una manera de administrar dispositivos Android. Sin embargo, ahora hay una funcionalidad de administración mejorada disponible con [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (publicada con Android 5.0). Con el fin de realizar la transición a la administración de dispositivos moderna, más completa y segura, Google va a reducir la compatibilidad con el administrador de dispositivos en las nuevas versiones de Android.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Debido a estos cambios de Google, los usuarios de Intune se verán afectados de las siguientes maneras:  
- Intune solo podrá proporcionar compatibilidad completa con dispositivos Android administrados por el administrador de dispositivos que ejecuten Android 10 y versiones posteriores hasta el segundo trimestre de 2020. Los dispositivos administrados por el administrador de dispositivos que ejecuten Android 10 o versiones posteriores después de este periodo ya no se podrán administrar por completo. En concreto, los dispositivos afectados no recibirán nuevos requisitos de contraseña.
    - Los dispositivos Samsung Knox no se verán afectados en este período de tiempo porque el soporte extendido se proporciona a través de la integración de Intune con la plataforma Knox. Esto le proporciona más tiempo para planear la transición desde la administración del administrador de dispositivos.    
- Los dispositivos Android administrados por el administrador de dispositivos que permanezcan en versiones de Android inferiores a Android 10 no se verán afectados y se podrán seguir administrando por completo con el administrador de dispositivos.    
- En todos los dispositivos Android 10 y versiones posteriores, Google ha restringido a los agentes de administración del administrador de dispositivos, como el Portal de empresa, el acceso a la información de identificación del dispositivo. Esta restricción afecta a las siguientes características de Intune después de que un dispositivo se actualice a Android 10 o una versión posterior:  
    - El control de acceso a la red de VPN dejará de funcionar.   
    - La identificación de los dispositivos como propiedad de la empresa con el número IMEI o el número de serie no marcará automáticamente los dispositivos como propiedad de la empresa.  
    - El número IMEI y el número de serie ya no serán visibles para los administradores de TI en Intune. 
        > [!NOTE]
        > Esta situación solo afecta a los dispositivos administrados por el administrador de dispositivos en Android 10 y versiones posteriores; no a los administrados con Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué debo hacer para prepararme para este cambio?
Para evitar la reducción de la funcionalidad que tendrá lugar en el tercer trimestre de 2020, siga estas recomendaciones:
- No incorpore nuevos dispositivos a la administración del administrador de dispositivos.
- Si está previsto que un dispositivo reciba una actualización de Android 10, mígrelo de la administración del administrador de dispositivos a la administración de Android Enterprise o a las directivas de protección de aplicaciones.

#### <a name="additional-information"></a>Información adicional
- [Guía de Google para la migración desde el administrador de dispositivos a Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentación de Google sobre el plan para dejar de usar la API del administrador de dispositivos](https://developers.google.com/android/work/device-admin-deprecation)



