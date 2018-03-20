---
title: "Configuración de restricción de dispositivos de Microsoft Intune para Windows Holographic for Business"
titlesuffix: Azure portal
description: "Obtenga información sobre la configuración de Intune que se puede usar para controlar los valores de configuración y la funcionalidad en dispositivos que ejecutan Windows Holographic for Business."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 10bb5a2eac9e72ba5b09a9a6f02932e872328c75
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-windows-holographic-for-business-device-restriction-settings"></a>Configuración de restricciones de dispositivos Windows Holographic for Business de Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Se admiten las siguientes configuraciones de restricciones de dispositivos en dispositivos que ejecutan Windows Holographic for Business, como Microsoft HoloLens.

## <a name="general"></a>General

- **Cancelación manual de la suscripción**: permite al usuario eliminar manualmente la cuenta del área de trabajo desde el dispositivo.
- **Cortana**: habilita o deshabilita el asistente de voz de Cortana.
- **Geolocation** (Geolocalización): especifica si el dispositivo puede usar la información de servicios de ubicación.



## <a name="password"></a>Contraseña
-   **Contraseña**: exige que el usuario final escriba una contraseña para acceder al dispositivo.
    -   **Requerir contraseña cuando el dispositivo vuelve de un estado de inactividad**: especifica que el usuario debe escribir una contraseña para desbloquear el dispositivo.



## <a name="app-store"></a>Tienda de aplicaciones

-   **Actualizar automáticamente las aplicaciones de la tienda**: permite que las aplicaciones instaladas de Microsoft Store se actualicen automáticamente.
-   **Instalación de aplicaciones de confianza**: permite realizar una instalación de prueba de las aplicaciones firmadas con un certificado de confianza.
-   **Desbloqueo de desarrollador**: permite que un usuario final modifique la configuración de desarrollador de Windows, como permitir las aplicaciones con instalación de prueba.

## <a name="edge-browser"></a>Explorador Microsoft Edge

-   **Explorador de Microsoft Edge**: permite el uso del explorador web Edge en el dispositivo.
-   **Cookies**: permite que el explorador guarde cookies de Internet en el dispositivo.
-   **Ventanas emergentes**: bloquea las ventanas emergentes en el explorador (solo se aplica a Windows 10 Escritorio).
-   **Search suggestions** (Sugerencias de búsqueda): permite que el motor de búsqueda sugiera sitios a medida que se escriben las frases de búsqueda.
-   **Administrador de contraseñas**: habilita o deshabilita la característica de Administrador de contraseñas de Microsoft Edge.
- **Enviar encabezados de no seguimiento**: configura el explorador Microsoft Edge para que envíe encabezados de no seguimiento a sitios web que visitan los usuarios.

## <a name="windows-defender-smart-screen"></a>SmartScreen de Windows Defender

- **SmartScreen para Microsoft Edge**: permite a SmartScreen de Edge el acceso al sitio y las descargas de archivos.

## <a name="search"></a>Buscar
- **Ubicación de búsqueda**: especifica si la búsqueda puede usar la ubicación. Información de


## <a name="cloud-and-storage"></a>Nube y almacenamiento
-   **Cuenta Microsoft**: permite al usuario asociar una cuenta de Microsoft con el dispositivo.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

-   **Bluetooth**: controla si el usuario puede habilitar y configurar Bluetooth en el dispositivo.
-   **Detectabilidad de Bluetooth**: permite que otros dispositivos con Bluetooth habilitado detecten el dispositivo.
-   **Anuncios de Bluetooth**: permite que el dispositivo reciba anuncios a través de Bluetooth.

## <a name="control-panel-and-settings"></a>Panel de control y configuración

- **Modificación de la hora del sistema**: evita que el usuario final cambie la fecha y hora del dispositivo.

## <a name="reporting-and-telemetry"></a>Informes y telemetría

- **Compartir datos de uso**: seleccione el nivel de envío de datos de diagnóstico.