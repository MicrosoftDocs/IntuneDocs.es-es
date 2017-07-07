---
title: "Configuración de directivas de administración de aplicaciones y cumplimiento de dispositivos durante una migración a Intune"
description: "El propósito de este artículo es indicar los pasos necesarios para configurar directivas de aplicaciones y cumplimiento de dispositivos durante una migración de Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5e848dda6643a28141a8f5f1d0bdc01f2bd9d390
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="configure-device-compliance-and-app-management-policies"></a>Configuración de directivas de administración de aplicaciones y cumplimiento de dispositivos

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

El objetivo principal al migrar a Intune es que todos los dispositivos estén inscritos y cumplan con sus directivas. Las directivas de dispositivos no solo ayudan a administrar dispositivos de usuario único de propiedad corporativa, sino también dispositivos personales (BYOD) y compartidos, tales como pantallas completas, máquinas de punto de venta, tabletas compartidas entre varios alumnos en un aula o dispositivos sin usuario (solo iOS).

Puede que cada plataforma de dispositivo ofrezca una configuración diferente, pero las directivas de dispositivos de Intune funcionan con cada plataforma de dispositivo proporcionando las siguientes capacidades de administración de dispositivos móviles:

-   Regular el número de dispositivos que cada usuario inscribe.

-   Administrar la configuración de dispositivos (p. ej., cifrado de nivel de dispositivo, longitud de la contraseña, uso de la cámara).

-   Entregar aplicaciones, perfiles de correo electrónico, perfiles de VPN, etc.

-   Evaluar los criterios de nivel de dispositivo para las directivas de cumplimiento de seguridad.

> [!IMPORTANT]
> Las directivas de administración de dispositivos no se asignan directamente a usuarios o dispositivos individuales, sino que se asignan a grupos de usuarios. Las directivas pueden aplicarse directamente a un grupo de usuarios y, por lo tanto, al dispositivo del usuario. También pueden aplicarse a un grupo de dispositivos y, por lo tanto, a los miembros del grupo.

## <a name="task-list-for-device-compliance-policies"></a>Lista de tareas para directivas de cumplimiento de dispositivos

### <a name="task-1-add-device-groups-optional"></a>Tarea 1: Agregar grupos de dispositivos (opcional)

Puede crear grupos de dispositivos cuando tenga que realizar diversas tareas administrativas en función de la identidad del dispositivo y no de la identidad del usuario.

Los grupos de dispositivos resultan prácticos para administrar dispositivos sin usuarios dedicados, como dispositivos de pantalla completa, o dispositivos compartidos entre trabajadores por turnos o asignados a una ubicación concreta.

Si configura grupos de dispositivos antes de la inscripción de dispositivos, puede aprovechar las categorías de dispositivos para agrupar dispositivos automáticamente tras la inscripción y recibir las directivas de dispositivos del grupo automáticamente. [Introducción a los grupos](/intune/groups-get-started)

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Tarea 2: Usar perfiles de acceso a recursos (certificados de Wi-Fi, VPN y correo electrónico)

Los perfiles de acceso a recursos aprovisionan configuraciones de acceso y certificados para dispositivos inscritos.

Como se explicó anteriormente en la sección de evaluación de los requisitos de MDM, si va a usar la autenticación basada en certificados, [configure certificados](/intune/certificates-configure).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Tarea 3: Crear e implementar una directiva de configuración de dispositivos

Tiene que crear un perfil de configuración de dispositivos para aplicar la configuración de nivel de dispositivo, como, por ejemplo: deshabilitar la cámara, la tienda de aplicaciones, configurar el modo de aplicación sencilla, la pantalla principal, etc.

- Aprenda sobre los [perfiles de dispositivo](/intune/device-profiles).

####  <a name="direct-import-of-ios-configuration-profiles-optional"></a>Importación directa de perfiles de configuración de iOS (opcional)

-   **Perfiles de iOS de Apple Configurator (iOS 7.1 y versiones posteriores):** si la solución MDM existente usa perfiles de Apple Configurator (archivos .mobileconfig), Intune puede importarlos directamente como directivas de configuración personalizadas.

-   **Directivas de configuración de aplicaciones móviles de iOS:** si la solución MDM existente usa directivas de configuración de aplicaciones móviles de iOS, Intune puede importarlas directamente siempre que cumplan con el formato XML especificado por Apple para listas de propiedades.

- Aprenda a agregar una directiva personalizada de [iOS](/intune/custom-settings-ios).

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Tarea 4: Crear e implementar directivas de cumplimiento de dispositivos (opcional)

Las directivas de cumplimiento de dispositivos evalúan la configuración orientada a la seguridad y ofrecen informes que muestran si los dispositivos son compatibles con los estándares corporativos o no. Las directivas de cumplimiento de dispositivos evalúan factores orientados a la seguridad tales como:

-   Longitud del PIN

-   Estado de liberado

-   Versión del SO

Vea otros recursos de configuración de cumplimiento de dispositivos:

-   Más información sobre las [directivas de cumplimiento de dispositivos](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

-   Aprenda a [crear una directiva de cumplimiento de dispositivos](/intune-classic/deploy-use/create-a-device-compliance-policy-in-microsoft-intune).

### <a name="task-5-publish-and-deploy-apps"></a>Tarea 5: Publicar e implementar aplicaciones

Cuando use la MDM de Intune, puede aprovisionar aplicaciones requiriendo su instalación automática o poniéndolas a disposición de los usuarios en el Portal de empresa.

-   Aprenda a [agregar aplicaciones](/intune-classic/deploy-use/add-apps).

-   Aprenda a [implementar aplicaciones](/intune-classic/deploy-use/deploy-apps).

### <a name="task-6-enable-device-enrollment"></a>Tarea 6: Permitir la inscripción de dispositivos

La inscripción establece la administración aprovisionando control sobre el dispositivo. Aprenda a [prepararse para inscribir dispositivos de propiedad corporativa y personales de usuario](/intune/device-enrollment).

## <a name="next-steps"></a>Pasos siguientes 

[Configure App Protection Policies (optional)](migration-guide-app-protection-policies.md) (Configuración de directivas de protección de aplicaciones [opcional])
