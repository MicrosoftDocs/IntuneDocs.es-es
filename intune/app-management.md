---
title: ¿Qué es la administración de aplicaciones de Microsoft Intune?
titlesuffix: ''
description: Aprenda los conceptos básicos de la administración de aplicaciones con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 20e9d4799b9ea4329c8286f0b75ea2a7d555e07b
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253772"
---
# <a name="what-is-microsoft-intune-app-management"></a>¿Qué es la administración de aplicaciones de Microsoft Intune?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador de TI, puede usar Microsoft Intune para administrar las aplicaciones móviles que usan los trabajadores de su empresa. Esta funcionalidad se suma a la administración de dispositivos y la protección de datos. Una de las prioridades de un administrador es garantizar que los usuarios finales tengan acceso a las aplicaciones que necesitan para hacer su trabajo. Este objetivo puede ser difícil por las siguientes causas:
- La amplia variedad de plataformas de dispositivo y tipos de aplicaciones.
- La necesidad de administrar aplicaciones de los dispositivos de la empresa y de los dispositivos personales de los usuarios.
- Debe asegurarse de que la red y los datos permanecen seguros.

Aparte de todo esto, puede que quiera asignar y administrar aplicaciones en dispositivos que no están inscritos en Intune.

Intune ofrece diversas funcionalidades para ayudarle a conseguir las aplicaciones que necesita en los dispositivos en los que desea que se ejecuten. En la tabla siguiente se ofrece un resumen de las capacidades de administración de aplicaciones: 

## <a name="app-management-capabilities-by-platform"></a>Funcionalidades de administración de aplicaciones por plataforma

|  | Android | iOS | macOS | Windows 10 | Windows Phone 8,1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| Agregar y asignar aplicaciones a dispositivos y usuarios | Sí | Sí | Sí | Sí | Sí |
| Asignar aplicaciones a dispositivos no inscritos en Intune | Sí | Sí | No | No | No |
| Usar directivas de configuración de aplicaciones para controlar el comportamiento de inicio de las aplicaciones | No | Sí | No | No | No |
| Usar directivas de aprovisionamiento de aplicaciones móviles para renovar aplicaciones caducadas | No | Sí | No | No | No |
| Proteger los datos de empresa de las aplicaciones con directivas de protección de aplicaciones | Sí | Sí | No | No1 | No |
| Quitar solo los datos corporativos de una aplicación instalada (eliminación selectiva de aplicaciones) | Sí | Sí | No | Sí | Sí |
| Supervisar las asignaciones de aplicaciones | Sí | Sí | Sí | Sí | Sí |
| Asignar y realizar el seguimiento de aplicaciones compradas por volumen desde una tienda de aplicaciones | No | No | No | Sí | No |
| Instalación obligatoria de aplicaciones en dispositivos (requerido)2 | Sí | Sí | Sí | Sí | Sí |
| Instalación opcional en dispositivos desde el Portal de empresa (instalación disponible) | Sí | Sí | Sí | Sí | Sí |
| Instalación de un acceso directo a una aplicación en Web (vínculo web) | Sí | Sí | Sí | Sí | Sí |
| Aplicaciones internas (línea de negocio) | Sí | Sí | Sí | Sí | No |
| Aplicaciones de una tienda | Sí | Sí | No | Sí | Sí |
| Actualizar aplicaciones | Sí | Sí | No | Sí | Sí |

<sup>1</sup> Considere el uso de [Windows Information Protection](windows-information-protection-configure.md) para proteger aplicaciones en dispositivos que ejecutan Windows 10.

<sup>2</sup> Se aplica solo a dispositivos administrados por Intune.

## <a name="get-started"></a>Introducción

Puede encontrar la mayoría de la información relacionada con las aplicaciones en la carga de trabajo **Aplicaciones cliente**, a la que puede acceder haciendo lo siguiente:

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**.  
    Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Microsoft Intune**, seleccione **Aplicaciones cliente**.

    ![Panel de carga de trabajo "Mobile apps"](./media/apps-workload.png)

Las cuatro secciones siguientes describen las opciones disponibles en el panel **Aplicaciones cliente**.

### <a name="manage"></a>Administrar
- **Aplicaciones**: seleccione esta opción para agregar, ver, asignar y supervisar las aplicaciones que usan los trabajadores. Para obtener más información, vea:
    - [Agregar aplicaciones](apps-add.md).
    - [Asignar aplicaciones](apps-deploy.md).
    - [Supervisar aplicaciones](apps-monitor.md).
- **Directivas de configuración de aplicaciones**: seleccione esta opción para proporcionar valores de configuración que podrían ser necesarios cuando el usuario ejecuta una aplicación. Para obtener más información, vea:
    - [Directivas de configuración de aplicaciones para Intune](app-configuration-policies-overview.md).
        - [Directivas de configuración de aplicaciones iOS](app-configuration-policies-use-ios.md).
        - [Directivas de configuración de aplicaciones Android](app-configuration-policies-use-android.md).
- **Directivas de protección de aplicaciones**: seleccione esta opción para asociar valores de configuración con una aplicación y ayudar a proteger los datos de empresa que esta usa. Por ejemplo, podría restringir las funcionalidades de una aplicación para comunicarse con otras aplicaciones o podría pedir que el usuario escribiera un PIN para acceder a una aplicación de la empresa. Para obtener más información, vea:
    - [Directivas de protección de aplicaciones](app-protection-policies.md).
- **Borrado selectivo de aplicaciones**: seleccione esta opción para quitar solo los datos corporativos de un dispositivo de un usuario seleccionado. Para obtener más información, vea:
    - [Borrado selectivo de aplicaciones](apps-selective-wipe.md).
- **Perfiles de aprovisionamiento de aplicaciones de iOS**: las aplicaciones iOS incluyen un perfil y un código de aprovisionamiento que está firmado por un certificado. Cuando el certificado expira, ya no se puede ejecutar la aplicación. Intune proporciona las herramientas para asignar proactivamente una nueva directiva de perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima. Para obtener más información, vea:
    - [Perfiles de aprovisionamiento de aplicaciones de iOS](app-provisioning-profile-ios.md).

Para más información sobre esta sección, vea [Administración de aplicaciones](app-management.md).

### <a name="monitor"></a>Supervisión
- **Licencias de aplicaciones**: vea, asigne y supervise las aplicaciones compradas por volumen de las tiendas de aplicaciones. Para obtener más información, vea:
    - [Aplicaciones de programa compradas por volumen de iOS](vpp-apps-ios.md).
    - [Aplicaciones adquiridas por volumen de la Microsoft Store para Empresas](windows-store-for-business.md).
- **Aplicaciones detectadas**: vea todas las aplicaciones que asignó Intune y que están instaladas en un dispositivo. Para obtener más información, consulte [Monitor app information and assignments with Microsoft Intune](apps-monitor.md#device-and-user-status-graphs) (Supervisión de información de aplicación y asignaciones con Microsoft Intune).
- **Estado de instalación de la aplicación**: vea el estado de una asignación de aplicación que ha creado. Para obtener más información, consulte [Monitor app information and assignments with Microsoft Intune](apps-monitor.md#device-and-user-status-graphs) (Supervisión de información de aplicación y asignaciones con Microsoft Intune).
- **Estado de protección de la aplicación**: vea el estado de una directiva de protección de aplicaciones de un usuario que haya seleccionado.
- **Registros de auditoría**: vea la actividad relacionada con la aplicación de Intune desarrollada de todos los administradores de TI.

Para más información sobre esta sección, vea [Supervisión de aplicaciones](apps-monitor.md).

### <a name="set-up"></a>Configurar
- **Tokens de VPP de iOS**: aplique y vea sus licencias del programa de compras por volumen (PCV) de iOS. Para obtener más información, vea:
    - [Aplicaciones de iOS adquiridas por volumen](vpp-apps-ios.md)
- **Certificado de Windows Enterprise**: aplique o vea el estado de un certificado de firma de código que se utiliza para distribuir aplicaciones de línea de negocio en los dispositivos de Windows administrados.
- **Certificado de Symantec para Windows**: aplique o vea el estado de un certificado de firma de código de Symantec que se necesita para distribuir archivos appx de XAP y WP8.x a dispositivos Windows 10 Mobile.
- **Microsoft Store para Empresas**: configure la integración con la Microsoft Store para Empresas. Luego, puede sincronizar las aplicaciones adquiridas en Intune, asignarlas y realizar el seguimiento de su uso de licencias. Para obtener más información, vea:
    - [Aplicaciones adquiridas por volumen de la Microsoft Store para Empresas](windows-store-for-business.md).
- **Claves de instalación de prueba de Windows**: agregue una clave de instalación de prueba de Windows que puede usarse para instalar una aplicación directamente en dispositivos en lugar de publicar y descargar la aplicación desde la tienda Windows. Para obtener más información, vea:
    - [Instalación de prueba de una aplicación de Windows](app-sideload-windows.md).
- **Personalización de marca del Portal de empresa**: personalice el Portal de empresa para adaptarlo a su empresa. Para obtener más información, vea:
    - [Configuración del Portal de empresa](company-portal-app.md).
- **Categorías de aplicaciones**: agregue, ancle y elimine los nombres de categoría de las aplicaciones.
- **Perfil de trabajo Android**: apruebe y sincronice las aplicaciones que ha aprobado para su empresa. Para obtener más información, vea:
    - [Aplicaciones del perfil del trabajo Android](apps-add-android-for-work.md).

### <a name="help-and-support"></a>Ayuda y soporte técnico
- **Ayuda y soporte técnico**: solucione problemas, solicite soporte técnico o vea el estado de Intune. Para obtener más información, vea:
    - [Solución de problemas](help-desk-operators.md).

## <a name="next-steps"></a>Pasos siguientes

- [Agregar una aplicación a Microsoft Intune](apps-add.md)
