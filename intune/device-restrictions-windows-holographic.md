---
title: 'Restricciones de dispositivos de Windows Holographic for Business en Microsoft Intune: Azure | Microsoft Docs'
description: Conozca y configure las opciones de restricción de dispositivos de Microsoft Intune para Windows Holographic for Business, incluidas la cancelación de la suscripción, la geolocalización, las contraseñas, la instalación de aplicaciones desde App Store, las cookies y los elementos emergentes de Edge, Windows Defender, la búsqueda, la nube y el almacenamiento, la conectividad de Bluetooth, la hora del sistema y los datos de uso de Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9d7f54ce0e288025a4a7f0f45bf5b10de5323021
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321761"
---
# <a name="device-restriction-settings-for-windows-holographic-for-business-in-intune"></a>Configuración de restricción de dispositivos de Windows Holographic for Business en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

## <a name="kiosk---obsolete"></a>Quiosco (obsoleto)

Estos valores son de solo lectura y no se pueden cambiar. Para configurar la pantalla completa, vea [Configuración de quiosco](kiosk-settings.md#windows-holographic-for-business).

Normalmente, un dispositivo de pantalla completa ejecuta una aplicación específica. A los usuarios no se les permite el acceso a características o funciones del dispositivo que está fuera de la aplicación de pantalla completa.

- **Pantalla completa**: identifica el tipo de pantalla completa admitido por la directiva. Las opciones son:

  - **No configurado** (valor predeterminado): la directiva no habilita una pantalla completa. 
  - **Pantalla completa con una sola aplicación**: el perfil permite que el dispositivo solo ejecute una aplicación. Cuando el usuario inicia sesión, se inicia una aplicación concreta. Este modo también evita que el usuario abra nuevas aplicaciones o modifique la aplicación en ejecución.
  - **Pantalla completa con varias aplicaciones**: el perfil permite que el dispositivo ejecute varias aplicaciones. Solo las aplicaciones que agregue están disponibles para el usuario. La ventaja de una pantalla completa con varias aplicaciones, o de un dispositivo de propósito fijo, es proporcionar una experiencia fácil de entender para los usuarios, que solo tienen que acceder a las aplicaciones que necesitan. Además, se quitan de la vista las aplicaciones que no necesitan. 
  
    Al agregar aplicaciones para una experiencia de pantalla completa con varias aplicaciones, también se agrega un archivo de diseño de menú Inicio. El [archivo de diseño de menú Inicio](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune) incluye XML de ejemplo que se puede usar en Intune. 

#### <a name="single-app-kiosks"></a>Pantallas completas con una sola aplicación
Escriba los valores siguientes:

- **Cuenta de usuario**: especifique la cuenta de usuario local (en el dispositivo) o el inicio de sesión de cuenta de Azure AD asociado a la aplicación de pantalla completa. En el caso de las cuentas unidas a dominios de Azure AD, especifique la cuenta con el formato `domain\username@tenant.org`. 

    En el caso de las pantallas completas en entornos de uso público con inicio de sesión automático habilitado, se debe usar un tipo de usuario con los privilegios mínimos (por ejemplo, la cuenta de usuario estándar local). Para configurar una cuenta de Azure Active Directory (AD) para el modo de pantalla completa, use el formato `AzureAD\user@contoso.com`.

- **Identificador de modelo de usuario de la aplicación (AUMID)**: especifique el AUMID de la aplicación de pantalla completa. Para más información, vea [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Buscar el identificador de modelo de usuario de aplicación de una aplicación instalada).

## <a name="reporting-and-telemetry"></a>Informes y telemetría

- **Compartir datos de uso**: seleccione el nivel de envío de datos de diagnóstico.
