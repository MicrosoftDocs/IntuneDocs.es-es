---
title: "¿Qué es la administración de aplicaciones?"
titlesuffix: Azure portal
description: "Use este tema para conocer los aspectos básicos sobre la administración de aplicaciones con Microsoft Intune."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 01/08/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0ea0c9a406d6ddb78cd016a7b594d077d7181952
ms.sourcegitcommit: 12b2111839e648f85374c1c0db4288f08e0ef85d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="what-is-microsoft-intune-app-management"></a>¿Qué es la administración de aplicaciones de Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Como administrador de TI, es responsable de asegurarse de que los usuarios finales tengan acceso a las aplicaciones que necesitan para cumplir con su trabajo. Esto puede ser difícil por las siguientes causas:
- La amplia variedad de plataformas de dispositivo y tipos de aplicaciones.
- La necesidad de administrar aplicaciones de los dispositivos de la empresa y de los propios dispositivos de los usuarios.
- Debe asegurarse de que la red y los datos permanecen seguros.

Aparte de todo esto, puede que quiera asignar y administrar aplicaciones en dispositivos que no están inscritos en Intune.

Intune ofrece diversas funcionalidades para ayudarle a conseguir las aplicaciones que necesita y en los dispositivos de su elección.

## <a name="app-management-capabilities-by-platform"></a>Funcionalidades de administración de aplicaciones por plataforma

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8,1|Windows 10|
|Agregar y asignar aplicaciones a dispositivos y usuarios|Sí|Sí|Sí|Sí|
|Asignar aplicaciones a dispositivos no inscritos en Intune|Sí|Sí|No|No|
|Usar directivas de configuración de aplicaciones para controlar el comportamiento de inicio de las aplicaciones|No|Sí|No|No|
|Usar directivas de aprovisionamiento de aplicaciones móviles para renovar aplicaciones caducadas|No|Sí|No|No|
|Proteger los datos de empresa de las aplicaciones con directivas de protección de aplicaciones|Sí|Sí|No|No<sup>1</sup>|
|Quitar solo los datos corporativos de una aplicación instalada (eliminación selectiva de aplicaciones)|Sí|Sí|Sí|Sí|
|Supervisar las asignaciones de aplicaciones|Sí|Sí|Sí|Sí|
|Asignar y realizar el seguimiento de aplicaciones compradas por volumen desde una tienda de aplicaciones|No|No|No|Sí|
|Instalación obligatoria de aplicaciones en dispositivos (requerido)<sup>2</sup>|Sí|Sí|Sí|Sí|
|Instalación opcional en dispositivos desde el Portal de empresa (instalación disponible)|Sí|Sí|Sí|Sí|
|Instalar un acceso directo a una aplicación en Web (clip de web)|Sí|Sí|Sí|Sí|
|Aplicaciones internas (línea de negocio)|Sí|Sí|No|No|
|Aplicaciones de una tienda|Sí|Sí|Sí|Sí|
|Actualizar aplicaciones|Sí|Sí|Sí|Sí|

<sup>1</sup> Considere el uso de [Windows Information Protection](windows-information-protection-configure.md) para proteger aplicaciones en dispositivos que ejecutan Windows 10.

<sup>1</sup>Se aplica solo a dispositivos administrados por Intune.

## <a name="how-to-get-started"></a>Cómo empezar

Puede encontrar la mayoría de las tareas relacionadas con las aplicaciones en la carga de trabajo **Mobile Apps** a la que puede acceder de la manera siguiente:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.

    ![La carga de trabajo Mobile Apps](./media/apps-workload.png)

### <a name="manage"></a>Administrar
- **Aplicaciones**: en este nodo puede agregar, asignar y supervisar la mayoría de las aplicaciones.
    - [Agregar aplicaciones](apps-add.md)
    - [Asignar aplicaciones](apps-deploy.md)
    - [Supervisión de aplicaciones](apps-monitor.md)
- **Directivas de configuración de aplicaciones**: estas directivas le permiten suministrar valores de configuración que podrían ser necesarios cuando un usuario ejecuta una aplicación.
    - [Directivas de configuración de aplicaciones iOS](app-configuration-policies-use-ios.md)
    - [Directivas de configuración de aplicaciones Android](app-configuration-policies-use-android.md)
- **Directivas de protección de aplicaciones**: estas directivas permiten asociar valores de configuración con una aplicación con el fin de ayudar a proteger los datos de empresa que esta usa. Por ejemplo, podría restringir las funcionalidades de una aplicación para comunicarse con otras aplicaciones o pedir que el usuario escribiera un PIN para acceder a una aplicación de la empresa.
    - [Directivas de protección de aplicaciones](app-protection-policies.md)
- **Borrado selectivo de aplicaciones**: quita solamente los datos corporativos del dispositivo de usuario seleccionado.
    - [Borrado selectivo de aplicaciones](apps-selective-wipe.md)
- **Perfiles de aprovisionamiento de iOS**: las aplicaciones iOS incluyen un perfil y un código de aprovisionamiento que está firmado por un certificado. Cuando el certificado expira, ya no se puede ejecutar la aplicación. Intune proporciona las herramientas para asignar proactivamente una nueva directiva de perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima.
    - [Perfiles de aprovisionamiento de aplicaciones iOS](app-provisioning-profile-ios.md)

Para obtener más información, consulte [Administrar aplicaciones](app-management.md).

### <a name="monitor"></a>Supervisión
- **Licencias de aplicaciones**: vea, asigne y supervise las aplicaciones compradas por volumen de las tiendas de aplicaciones.
    - [Aplicaciones adquiridas por volumen de la Tienda Microsoft para Empresas](windows-store-for-business.md)
- **Aplicaciones detectadas**: muestra todas las aplicaciones que asignó Intune y que están instaladas en un dispositivo.
- **App Install Status** (Estado de instalación de aplicación): muestra el estado de una asignación de aplicación que ha creado.
- **App protection status** (Estado de protección de aplicación): muestra el estado de una directiva de protección de aplicaciones de un usuario seleccionado.
- **Registros de auditoría**: muestra la actividad relacionada con la aplicación de Intune desarrollada por todos los administradores de TI.

Para más información, consulte [Supervisión de aplicaciones](apps-monitor.md).

### <a name="setup"></a>Setup
- **Tokens de PCV de iOS**: aplique y vea sus licencias del programa de compras por volumen (PCV) de iOS.
    - [Aplicaciones de iOS adquiridas por volumen](vpp-apps-ios.md)
- **Certificado de empresa de Windows**: aplique o vea el estado de un certificado de firma de código utilizado para distribuir aplicaciones de línea de negocio en los dispositivos de Windows administrados. 
- **Certificado de Windows Symantec**: aplique o vea el estado de un certificado de firma de código de Symantec que se necesita para distribuir archivos appx de XAP y WP8.x a dispositivos Windows 10 Mobile. 
- **Tienda Microsoft para Empresas**: configure la integración con la Tienda Microsoft para Empresas. Luego, puede sincronizar las aplicaciones adquiridas en Intune, asignarlas y realizar el seguimiento de su uso de licencias.
    - [Aplicaciones adquiridas por volumen de la Tienda Microsoft para Empresas](windows-store-for-business.md)
- **Claves de instalación de prueba de Windows**: puede agregar una clave de instalación de prueba de Windows que puede usarse para instalar una aplicación directamente en dispositivos en lugar de publicar y descargar la aplicación desde la tienda Windows.
    - [Instalación de prueba de una aplicación de Windows](app-sideload-windows.md) 
- **Company Portal branding** (Personalización de marca del Portal de empresa): personalice el Portal de empresa para adaptarlo a su empresa.
    - [Configuración del Portal de empresa](company-portal-app.md)
- **Categorías de aplicaciones**: agregue, ancle y elimine los nombres de categoría de las aplicaciones.
- **Android for Work**: apruebe y sincronice las aplicaciones que ha aprobado para su empresa.
    - [Aplicaciones Android for Work](apps-add-android-for-work.md) 

### <a name="help-and-support"></a>Ayuda y soporte técnico
- **Ayuda y soporte técnico**: solucione problemas, solicite soporte técnico o vea el estado de Intune.
    - [Solución de problemas](help-desk-operators.md)