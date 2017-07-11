---
title: "Preparación de Intune para la administración de dispositivos móviles"
description: "El propósito de este artículo es ayudar a los lectores a evaluar sus requisitos empresariales y técnicos antes de migrar a Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 65e3bb4b6a4e6e8dcfa1dd16738ae47758f4fb9b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="phase-1-prepare-intune-for-mobile-device-management-mdm"></a>Fase 1: Preparar Intune para la administración de dispositivos móviles (MDM)

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Antes de profundizar en los detalles de configuración de Intune, revisemos los requisitos de administración de dispositivos móviles de la organización. Puede que resulte útil ejecutar informes de usuarios activos del proveedor de MDM actual para identificar los grupos de usuarios críticos. Luego puede empezar a solucionar las preguntas que aparecen en la sección [Evaluar los requisitos de MDM](migration-guide-prepare.md#assess-mdm-requirements).

## <a name="assess-mdm-requirements"></a>Evaluar los requisitos de MDM

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>¿Qué tipos de dispositivos tiene que administrar?

-   ¿Qué [plataformas](/intune-classic/get-started/supported-mobile-devices-and-computers) tiene que admitir?

-   ¿Son corporativos o BYOD los dispositivos que tiene que admitir?

-   ¿Qué tipo de conectividad se usa? ¿Wi-Fi, móvil, VPN?

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>¿Qué tienen que hacer sus usuarios en dispositivos administrados?

-   ¿Necesita aprovisionar aplicaciones a los usuarios finales?

-   ¿Usa aplicaciones de línea de negocio personalizadas? ¿O solo necesita aplicaciones de la tienda pública?

-   ¿Tiene que aprovisionar cuentas de correo electrónico?

### <a name="what-kinds-of-users"></a>¿Qué tipos de usuarios?

-   ¿Cuántos usuarios van a usar un solo dispositivo?

-   ¿Qué Términos de uso necesita?

    -   Asegúrese de involucrar en esto al departamento legal desde el principio.

    -   ¿Qué localización se requiere?

-   ¿Están los usuarios familiarizados con la tecnología y el entorno de TI en general?

### <a name="what-is-your-device-security-policy"></a>¿Cuál es su directiva de seguridad de dispositivos?

-   ¿Necesita cifrado de nivel de dispositivo?

-   ¿Longitudes de código PIN o código de acceso de dispositivo?

-   ¿Tiene que deshabilitar características del dispositivo o restringir determinados comportamientos del dispositivo?

    -   Puede controlar diversas opciones de configuración específicas de la plataforma con perfiles de configuración de dispositivo, por ejemplo: deshabilitar la cámara, bloquear en modo de aplicación sencilla.
<br></br>
-   ¿Qué tipos de autenticación debe admitir?

    -   Si necesita autenticación basada en certificados, ¿qué tipos de certificados deben aprovisionarse?

        -   Intune puede aprovisionar certificados con perfiles de acceso a recursos en dispositivos inscritos.
<br></br>
    -   ¿Qué tipo de infraestructura de clave pública (PKI) tiene que admitir?
<br></br>
-   ¿Tiene que admitir red privada virtual (VPN) en el nivel de aplicación o de dispositivo?

    -   Intune puede aprovisionar configuraciones de VPN para proveedores de VPN de terceros.
<br></br>
-   ¿Se pueden hacer excepciones temporales para que determinados requisitos eviten el tiempo de inactividad? ¿O deben los dispositivos con acceso cumplir siempre todos los requisitos de seguridad?

## <a name="additional-information"></a>Información adicional

-   Para obtener ejemplos más detallados, revise estos [casos prácticos](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune) desde diferentes sectores para ver cómo las organizaciones evalúan sus requisitos de administración de dispositivos móviles.

## <a name="next-steps"></a>Pasos siguientes

[Configuración básica](migration-guide-setup.md)