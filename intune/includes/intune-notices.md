---
title: archivo include
description: archivo include
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fab8f2be48a30f6ad058b3eeb6874a44ff04e6ac
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744316"
---
Estos avisos proporcionan información importante que puede ayudarle a prepararse para las características y los cambios futuros de Intune. 

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

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>Plan de cambio: Intune admitirá iOS 11 y versiones posteriores a partir de septiembre <!-- 4665342-->
Esperamos que Apple lance iOS 13 en septiembre. La inscripción de Intune, el Portal de empresa y el explorador administrado pasarán a admitir iOS 11 y versiones posteriores poco después del lanzamiento de iOS 13.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Puesto que iOS 11.0 y las versiones posteriores admiten las aplicaciones móviles de O365, puede ser que esto no le afecte. Es probable que ya haya actualizado la versión de su sistema operativo o de sus dispositivos. Con todo, si posee o quiere inscribir alguno de los siguientes dispositivos, debe saber que no admiten sistemas operativos posteriores a iOS 10. Estos dispositivos deben actualizarse a un dispositivo que admita iOS 11 o versiones posteriores:

- iPhone 5
- iPhone 5c
- iPad (4.ª generación)

A partir de julio, los dispositivos inscritos en MDM con iOS 10 y el Portal de empresa recibirán un aviso para actualizar el sistema operativo o el dispositivo. Si usa directivas de protección de aplicaciones (APP, por sus siglas en inglés), también puede establecer la configuración de acceso "Requerir sistema operativo iOS mínimo (solo es una advertencia)".

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Compruebe los informes de Intune para ver qué dispositivos o usuarios pueden verse afectados. Vaya a **Dispositivos** > **Todos los dispositivos** y filtre por sistema operativo. Puede agregar columnas adicionales para ayudar a identificar qué usuarios de su organización tienen dispositivos que ejecutan iOS 10. Pida a los usuarios finales que actualicen sus dispositivos a una versión del sistema operativo compatible antes de septiembre.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Plan de cambio: Compatibilidad con la versión 8.1.1 y versiones posteriores de Intune App SDK para iOS <!-- 3586942-->
A partir de septiembre de 2019, Intune pasará a admitir aplicaciones de iOS con Intune App SDK 8.1.1 y versiones posteriores. Ya no se admitirán las aplicaciones creadas con versiones del SDK inferiores a 8.1.1. Este cambio entrará en vigor con el lanzamiento de iOS 13 por parte de Apple, que está previsto para septiembre y se ha anunciado en MC181399.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Con la integración de Intune App SDK o el ajuste de aplicaciones, puede proteger los datos corporativos de aplicaciones y usuarios no aprobados mediante el cifrado de datos. El SDK de aplicaciones de Intune para iOS usará las claves de cifrado de 256 bits de forma predeterminada cuando el cifrado esté habilitado mediante las directivas de protección de aplicaciones (APP). Después de este cambio, las aplicaciones de iOS en versiones de SDK anteriores a la 8.1.1, que utilizan claves de cifrado de 128 bits, ya no podrán compartir datos con las aplicaciones integradas con SDK 8.1.1 o con claves de 256 bits. Todas las aplicaciones de iOS deberán tener una versión de SDK de 8.1.1 o posterior para permitir el uso compartido de datos.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
Compruebe sus aplicaciones de Microsoft, de terceros y de línea de negocio (LOB). Debe asegurarse de que todas sus aplicaciones protegidas con la aplicación de Intune usan la versión 8.1.1 del SDK o una versión posterior.

- Para aplicaciones de LOB: Es posible que deba volver a publicar las aplicaciones integradas con la versión 8.1.1 del SDK o con una versión posterior. Le recomendamos que utilice la versión más reciente del SDK. Para información sobre cómo preparar las aplicaciones de LOB para las directivas de protección de aplicaciones, vea [Preparar aplicaciones de línea de negocio para las directivas de protección de aplicaciones](../apps-prepare-mobile-application-management.md).
- Para las aplicaciones de terceros o de Microsoft: Asegúrese de que está implementando la versión más reciente de estas aplicaciones a los usuarios.

También debe actualizar la documentación o las instrucciones para desarrolladores, si procede, para que incluyan este cambio en el soporte técnico para el SDK.

#### <a name="additional-information"></a>Información adicional
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management
