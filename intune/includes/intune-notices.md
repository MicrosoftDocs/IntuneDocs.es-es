---
title: archivo include
description: archivo include
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 1073a38da8a5b2467b1ff8c97b32b93f92e34e4c
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454126"
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
