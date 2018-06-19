---
title: Configuración de directivas de administración de aplicaciones y cumplimiento de dispositivos durante una migración a Intune
titlesuffix: Microsoft Intune
description: En este artículo se proporcionan los pasos necesarios para configurar directivas de aplicaciones y cumplimiento de dispositivos durante una migración de Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 13a9c0a036eb6ce6ea7e984419c9598194b35b68
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
ms.locfileid: "29926361"
---
# <a name="configure-device-compliance-and-app-management-policies-when-migrating-to-microsoft-intune"></a>Configurar directivas administración de aplicaciones y cumplimiento de los dispositivos al migrar a Microsoft Intune

El objetivo principal al migrar a Intune es que todos los dispositivos estén inscritos en Intune y cumplan con sus directivas. Las directivas de dispositivos no solo ayudan a administrar dispositivos de usuario único de propiedad corporativa, sino también dispositivos personales (BYOD) y compartidos, como pantallas completas, máquinas de punto de venta, tabletas compartidas entre varios alumnos en un aula o dispositivos sin usuario (solo iOS).

Puede que cada plataforma de dispositivo ofrezca una configuración diferente, pero las directivas de dispositivos de Intune funcionan con cada plataforma de dispositivo proporcionando las siguientes capacidades de administración de dispositivos móviles:

-   Regular el número de dispositivos que cada usuario inscribe.

-   Administrar la configuración de dispositivos (por ejemplo, cifrado de nivel de dispositivo, longitud de la contraseña, uso de la cámara).

-   Entregar aplicaciones, perfiles de correo electrónico y perfiles de VPN, entre otros.

-   Evaluar los criterios de nivel de dispositivo para las directivas de cumplimiento de seguridad.

> [!IMPORTANT]
> Las directivas de administración de dispositivos no se asignan directamente a usuarios o dispositivos individuales, sino que se asignan a grupos de usuarios. Las directivas pueden aplicarse directamente a un grupo de usuarios y, por lo tanto, al dispositivo del usuario. También pueden aplicarse a un grupo de dispositivos y, por lo tanto, a los miembros del grupo.

## <a name="task-list-for-device-compliance-policies"></a>Lista de tareas para directivas de cumplimiento de dispositivos

### <a name="task-1-add-device-groups-optional"></a>Tarea 1: Agregar grupos de dispositivos (opcional)

Puede crear grupos de dispositivos cuando tenga que realizar tareas administrativas en función de la identidad del dispositivo y no de la identidad del usuario.

Los grupos de dispositivos resultan prácticos para administrar dispositivos que no tienen usuarios dedicados, como dispositivos de pantalla completa, dispositivos compartidos entre trabajadores por turnos o dispositivos asignados a una ubicación concreta.

Si configura grupos de dispositivos antes de la inscripción de dispositivos, puede usar las categorías de dispositivos para unir dispositivos automáticamente a los grupos tras la inscripción. Después, recibirán las directivas de sus dispositivos de grupo automáticamente. [Introducción a los grupos](groups-get-started.md)

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Tarea 2: Usar perfiles de acceso a recursos (certificados de Wi-Fi, VPN y correo electrónico)

Los perfiles de acceso a recursos proporcionan configuraciones de acceso y certificados para dispositivos inscritos. Si está usando autenticación basada en certificados, [configure los certificados](certificates-configure.md).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Tarea 3: Crear e implementar una directiva de configuración de dispositivos

Tiene que crear un perfil de configuración de dispositivos para aplicar la configuración de nivel de dispositivo, como, por ejemplo: deshabilitar la cámara, la tienda de aplicaciones, configurar el modo de aplicación sencilla y la pantalla principal, entre otros. Aprenda sobre los [perfiles de dispositivo](device-profiles.md).

####  <a name="directly-import-ios-configuration-profiles-optional"></a>Importar directamente los perfiles de configuración de iOS (opcional)

-   **Perfiles de iOS de Apple Configurator (iOS 7.1 y versiones posteriores):** si la solución MDM existente usa perfiles de Apple Configurator (archivos .mobileconfig), Intune puede importarlos directamente como directivas de configuración personalizadas.

-   **Directivas de configuración de aplicaciones móviles de iOS:** si la solución MDM existente usa directivas de configuración de aplicaciones móviles de iOS, Intune puede importarlas directamente siempre que cumplan con el formato XML especificado por Apple para listas de propiedades.

- Obtenga información sobre cómo agregar una directiva personalizada de [iOS](custom-settings-ios.md).

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Tarea 4: Crear e implementar directivas de cumplimiento de dispositivos (opcional)

Las directivas de cumplimiento de dispositivos evalúan la configuración orientada a la seguridad y ofrecen informes que muestran si los dispositivos son compatibles con los estándares corporativos o no. Dicha configuración incluye:

-   Longitud del PIN

-   Estado de liberado

-   Versión del sistema operativo

Vea otros recursos de configuración de cumplimiento de dispositivos:

-   Más información sobre las [directivas de cumplimiento de dispositivos](device-compliance.md).

-   Aprenda a [crear una directiva de cumplimiento de dispositivos](device-compliance-get-started.md).

### <a name="task-5-publish-and-deploy-apps"></a>Tarea 5: Publicar e implementar aplicaciones

Cuando use la MDM de Intune, puede proporcionar aplicaciones requiriendo su instalación automática o poniéndolas a disposición de los usuarios en el portal de empresa.

-   [Cómo agregar aplicaciones](apps-add.md).

-   [Cómo implementar aplicaciones](apps-deploy.md).

### <a name="task-6-enable-device-enrollment"></a>Tarea 6: Permitir la inscripción de dispositivos

La inscripción de dispositivos es necesaria para administrar el dispositivo. Aprenda a [prepararse para inscribir dispositivos de propiedad corporativa y personales de usuario](device-enrollment.md).

## <a name="next-steps"></a>Pasos siguientes

[Configuración de directivas de protección de aplicaciones (opcional)](migration-guide-app-protection-policies.md).
