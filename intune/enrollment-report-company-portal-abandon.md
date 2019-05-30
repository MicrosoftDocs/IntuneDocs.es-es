---
title: Informe de inscripciones de usuario incompletas en Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre el informe de inscripciones de usuario incompletas.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 546694409e6f87d85c5ef934b5d084b0955e0bf7
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041865"
---
# <a name="incomplete-user-enrollments-report"></a>Informe de inscripciones de usuario incompletas

Este informe indica en qué parte del proceso de inscripción del Portal de empresa los usuarios no completan el proceso de inscripción.

Para ver el informe, elija **Intune** > **Inscripción de dispositivos** > **Inscripciones de usuario incompletas**.

Con esta información, puede actualizar los documentos de incorporación para ayudar a los usuarios a completar la inscripción. Por ejemplo, si muchos usuarios están abandonando el proceso en la sección Términos de uso, podría investigar esta área y hacer que sea más intuitiva para los usuarios.

## <a name="what-is-an-incomplete-enrollment"></a>¿Qué es una inscripción incompleta?

Una inscripción incompleta es cuando un usuario realiza una de estas acciones:

-   Elige explícitamente una acción para detener la inscripción.
-   Cierra Portal de empresa durante la inscripción.
-   Dedica más de 30 minutos entre las secciones de inscripción.

Si un usuario decide detener la inscripción y reiniciar varias veces, se muestra como varios intentos y varias inscripciones incompletas. Si un usuario espera 30 minutos entre las distintas pantallas de inscripción, se considera varias inscripciones incompletas.

## <a name="what-does-the-report-show"></a>¿Qué muestra el informe?

Los informes incluyen datos de dispositivos iOS y Android.

Los informes muestran datos de las dos últimas semanas, pero puede filtrar el informe para que muestre cualquier período de hasta 30 días en el pasado.

Puede filtrar el intervalo de fechas, el sistema operativo y la sección inscripción si elige **Filtrar**.

### <a name="number-and-percentage-tiles"></a>Iconos de número y porcentaje

En la parte superior del informe, puede ver el número y el porcentaje de inscripciones abandonadas en relación con todas las inscripciones.

-   Inscripciones iniciadas: número de inscripciones que se han intentado.
-   Inscripciones incompletas: número de inscripciones intentadas que no dieron lugar a la inscripción completa de un dispositivo compatible.
-   Tasa de inscripciones incompletas: porcentaje de intentos de inscripción que se abandonaron (inscripciones abandonadas/inscripciones iniciadas).

### <a name="line-graph"></a>Gráfico de líneas

El gráfico de líneas muestra las inscripciones incompletas para cada una de las cuatro secciones de inscripción principales:

-   Lista de comprobación de configuración
-   Pantallas de la plataforma
-   Términos de uso
-   Cumplimiento y activación

### <a name="user-abandonment-actions"></a>Acciones de abandono del usuario

En estas tablas se muestra la lista de acciones del usuario que se consideran una inscripción incompleta. Para ver ejemplos de las pantallas de inscripción, puede ver los vídeos de inscripción de [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) y [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment). 


#### <a name="setup-checklist-section"></a>Sección de lista de comprobación de configuración

| Nombre de acción | Pantalla o flujo | Plataforma | Acción |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Mensaje para abrir página en Portal de empresa | iOS/Android | **Cancelar** |
| EnrollmentWrapUp | Pantalla Inscribiendo el dispositivo hasta finalizar **Cargando los recursos de la empresa** | iOS/Android | Tardó > 30 minutos |
| DeviceCategory | Selección de categoría de dispositivo (si está configurado por el administrador) hasta que haga clic en **Listo** | iOS/Android | Tardó > 30 minutos |
| PreEnrollmentWizard | Se mostró la pantalla de configuración de acceso cuando se había empezado la inscripción, pero volvió a configuración de acceso | iOS/Android| **Posponer** |
| PreEnrollmentWizard | Pantalla de configuración de acceso hasta hacer clic en **Siguiente** en la pantalla **¿Cuál es el siguiente paso?** | iOS/Android | Tardó > 30 minutos |

#### <a name="platform-screens-section"></a>Sección de pantallas de la plataforma

| Nombre de acción | Pantalla o flujo | Plataforma | Acción |
| ---- |---- |---- |---- |
| iOSProfileLaunch | Mensaje para mostrar un perfil de configuración | iOS | **Omitir** |
| iOSProfileLaunch | Pantalla de instalación del perfil | iOS | **Cancelar** |
| iOSProfileLaunch | Mensaje para confiar en la fuente del perfil para inscribir el dispositivo | iOS | **Cancelar** |
| iOSProfileLaunch | Pantalla de instalación del perfil hasta que se instala el perfil | iOS | Tardó > 30 minutos |
| AndroidPermissions | Pantalla de activación de administrador del dispositivo | Android | **Cancelar** |
| AndroidPermissions | Desde el mensaje pidiendo aprobación para realizar y administrar llamadas telefónicas hasta **Activar** el administrador de dispositivos | Android | Tardó > 30 minutos |
| KnoxActivation | Activación del agente KLMS (solo Samsung) | Android| **Cancelar** |
| KnoxActivation | Activación del agente KLMS hasta **Confirmar** | Android | Tardó > 30 minutos|

#### <a name="terms-of-use-section"></a>Sección Términos de uso

| Nombre de acción | Pantalla o flujo | Plataforma | Acción |
| ---- |---- |---- |---- |
| TermsofUse | Términos de uso (si está configurado por el administrador) | iOS/Android | **Rechazar todo** |
| TermsofUse | Términos de uso hasta **Aceptar todo** | iOS/Android | Tardó > 30 minutos |

#### <a name="complianceactivation-section"></a>Sección Cumplimiento y activación

| Nombre de acción | Pantalla o flujo | Plataforma | Acción |
| ---- |---- |---- |---- |
| Cumplimiento | La sección Cumplimiento del dispositivo (si está configurado por el administrador) se muestra en un color distinto de verde en la inscripción posterior de configuración de acceso| iOS/Android | **Posponer** |
| Cumplimiento | La sección Cumplimiento del dispositivo se muestra en un color distinto de verde hasta que se actualiza para mostrarse en verde | iOS/Android | Tardó > 30 minutos |
| Activación | La sección Activación de la inscripción (si está configurado por el administrador) se muestra en un color distinto de verde en la configuración de acceso | iOS/Android | **Posponer** |
| Cumplimiento | La sección Activación de dispositivo se muestra en un color distinto de verde hasta que se actualiza para mostrarse en verde | iOS/Android | Tardó > 30 minutos |

## <a name="next-steps"></a>Pasos siguientes

Después de comprobar las tasas de inscripciones incompletas, puede revisar las [opciones de inscripción](enrollment-options.md) para ver si puede realizar cambios para mejorar la inscripción.
