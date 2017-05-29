---
title: "Configurar directivas de administración de aplicaciones y cumplimiento de dispositivos durante una migración de Intune | Microsoft Docs"
description: "El propósito de este artículo es indicar los pasos necesarios para configurar directivas de aplicaciones y cumplimiento de dispositivos durante una migración de Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 50a8929ef31e0a322e9460f82af3ed821ade69cf
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-configure-device-compliance-and-app-management-policies"></a>Fase 1: Configurar las directivas de administración de aplicaciones y cumplimiento de dispositivos

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

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

El [portal clásico de Intune](https://manage.microsoft.com/) le ofrece la posibilidad de crear grupos de dispositivos cuando tenga que realizar diversas tareas administrativas basadas en la identidad del dispositivo y no en la identidad del usuario.

Los grupos de dispositivos resultan prácticos para administrar dispositivos sin usuarios dedicados, como dispositivos de pantalla completa, o dispositivos compartidos entre trabajadores por turnos o asignados a una ubicación concreta.

Si configura grupos de dispositivos antes de la inscripción de dispositivos, puede aprovechar las categorías de dispositivos para agrupar dispositivos automáticamente tras la inscripción y recibir las directivas de dispositivos del grupo automáticamente.

-   Aprenda a [agregar grupos de dispositivos](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5).

-   Aprenda a [configurar categorías de dispositivos](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Tarea 2: Usar perfiles de acceso a recursos (certificados de Wi-Fi, VPN y correo electrónico)

Los perfiles de acceso a recursos aprovisionan configuraciones de acceso y certificados para dispositivos inscritos.

Como ya se explicó en la sección Evaluar los requisitos de MDM, si usa autenticación basada en certificados, debe tener una [infraestructura PKI específica](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles) para implementar certificados de VPN, Wi-Fi y correo electrónico.

#### <a name="direct-import-of-resource-access-profiles-optional"></a>Importación directa de perfiles de acceso a recursos (opcional)

Si la solución MDM existente ofrece un mecanismo de exportación de perfiles de correo electrónico, Wi-Fi y VPN a formato XML, tal vez pueda aprovechar el archivo XML y tan solo importarlo a Intune mediante OMA-URI para crear perfiles personalizados de dispositivos iOS, Android y Windows.

-   Obtenga información sobre cómo agregar una directiva personalizada para dispositivos [iOS](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Tarea 3: Crear e implementar una directiva de configuración de dispositivos

Tiene que crear un perfil de configuración de dispositivos para aplicar la configuración de nivel de dispositivo, como, por ejemplo: deshabilitar la cámara, la tienda de aplicaciones, configurar el modo de aplicación sencilla, la pantalla principal, etc.

- Más información sobre [perfiles de configuración de dispositivos](https://docs.microsoft.com/intune/device-profile-create).

####  <a name="direct-import-of-ios-configuration-profiles-optional"></a>Importación directa de perfiles de configuración de iOS (opcional)

-   **Perfiles de iOS de Apple Configurator (iOS 7.1 y versiones posteriores):** si la solución MDM existente usa perfiles de Apple Configurator (archivos .mobileconfig), Intune puede importarlos directamente como directivas de configuración personalizadas.

-   **Directivas de configuración de aplicaciones móviles de iOS:** si la solución MDM existente usa directivas de configuración de aplicaciones móviles de iOS, Intune puede importarlas directamente siempre que cumplan con el formato XML especificado por Apple para listas de propiedades.

- Aprenda a agregar una directiva personalizada de [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune#custom-policy-settings).

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

La inscripción establece la administración aprovisionando control sobre el dispositivo.

-   Aprenda a [prepararse para inscribir dispositivos de propiedad corporativa y personales de usuario](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune).

-   Aprenda a [inscribir dispositivos de propiedad corporativa](/intune-classic/deploy-use/manage-corporate-owned-devices).

Si necesita inscribir dispositivos sin usuarios o compartidos, puede usar una cuenta de administrador de inscripción de dispositivos (DEM).

## <a name="next-steps"></a>Pasos siguientes 

Fase 1: Configurar directivas de protección de aplicaciones (opcional)

