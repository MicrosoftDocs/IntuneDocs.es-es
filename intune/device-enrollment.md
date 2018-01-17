---
title: "¿Qué es la inscripción de dispositivos de Microsoft Intune?"
titlesuffix: Azure portal
description: "Aprenda sobre la inscripción de dispositivos iOS, Android y Windows."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 12/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dc0105bb786d8b1e569b11898b0d3757feba406a
ms.sourcegitcommit: a55a7119a15836b6941fdd5b32b9076139093693
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="what-is-device-enrollment"></a>¿Qué es la inscripción de dispositivos?
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune permite administrar los dispositivos y las aplicaciones de sus recursos y su acceso a los datos de la empresa. Para usar esta administración de dispositivos móviles (MDM), primero es necesario inscribir los dispositivos en el servicio de Intune. Al inscribir un dispositivo, se emite un certificado MDM. Dicho certificado se usa para la comunicación con el servicio de Intune.

Como puede observar en las tablas siguientes, hay varias formas de inscribir los dispositivos de sus recursos. Cada método depende de la propiedad del dispositivo (personal o corporativo), el tipo de dispositivo (iOS, Windows o Android) y los requisitos de administración (restablecimiento, afinidad o bloqueo).

## <a name="ios-enrollment-methods"></a>Métodos de inscripción de iOS

| **Método** |  **Se requiere reinicio** |    [**Afinidad de usuario**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) |   **Bloqueado** | **Detalles** |
|:---:|:---:|:---:|:---:|:---:|
| | Los dispositivos se restablecen de fábrica durante la inscripción. |  Se asocia cada dispositivo a un usuario.| Los usuarios no pueden anular la inscripción de los dispositivos.  | |
|**[BYOD](#bring-your-own-device)** | No|   Sí |   No | [Más información](./apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No  | [Más información](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**|   Sí |   Opcional |  Opcional|[Más información](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Sí |   Opcional |  No| [Más información](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| No |    No  | No|[Más información](./apple-configurator-direct-enroll-ios.md)|

## <a name="windows-enrollment-methods"></a>Métodos de inscripción de Windows

| **Método** |  **Se requiere reinicio** |    **Afinidad de usuario**   |   **Bloqueado** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | No |  Sí |   No | [Más información](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No  |[Más información](device-enrollment-manager-enroll.md)|
|**Inscripción automática** | No |Sí |No | [Más información](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Inscripción masiva** |No |No |No | [Más información](./windows-bulk-enroll.md) |

## <a name="android-enrollment-methods"></a>Métodos de inscripción de Android

| **Método** |  **Se requiere reinicio** |    **Afinidad de usuario**   |   **Bloqueado** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | No|   Sí |   No | [Más información](./android-enroll.md)|
|**[DEM](#device-enrollment-manager)**| No |No |No  |[Más información](./device-enrollment-manager-enroll.md)|
|**Android for Work**| No | Sí | No| [Más información](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="bring-your-own-device"></a>Bring Your Own Device
Entre los dispositivos Bring Your Own Device (BYOD) se incluyen teléfonos, tabletas y equipos personales. Los usuarios instalan y ejecutan la aplicación Portal de empresa para inscribir sus dispositivos BYOD. Este programa permite a los usuarios acceder a los recursos de la compañía, como el correo electrónico.

## <a name="corporate-owned-device"></a>Dispositivo de propiedad corporativa
Entre los dispositivos de propiedad corporativa (COD) se incluyen teléfonos, tabletas y equipos propiedad de la empresa facilitados a los recursos. La inscripción de COD permite escenarios como la inscripción automática, el uso compartido de dispositivos o los requisitos de inscripción autorizada previamente. Una forma habitual de inscribir dispositivos COD es utilizar el administrador de inscripción de dispositivos (DEM) por parte de un administrador. Los dispositivos iOS se pueden inscribir directamente mediante las herramientas del Programa de inscripción de dispositivos (DEP) proporcionadas por Apple. Los dispositivos con un número IMEI también se pueden identificar y etiquetar como de propiedad corporativa.

### <a name="device-enrollment-manager"></a>Administrador de inscripción de dispositivos
El administrador de inscripción de dispositivos (DEM) es una cuenta especial de usuario que se usa para inscribir y administrar varios dispositivos de la empresa. Los administradores pueden instalar el portal de empresa e inscribir muchos dispositivos sin usuario. Obtenga más información sobre [DEM](./device-enrollment-manager-enroll.md).

### <a name="apple-device-enrollment-program"></a>Programa de inscripción de dispositivos de Apple
La administración del Programa de inscripción de dispositivos (DEP) de Apple permite crear e implementar directivas "de forma inalámbrica" para dispositivos iOS que se han adquirido y administrado con DEP. El dispositivo se inscribe cuando los usuarios lo activan por primera vez y ejecutan el asistente de configuración de iOS. Este método admite el modo supervisado de iOS, que permite configurar un dispositivo con una funcionalidad específica.

Más información sobre la inscripción de DEP de iOS:

- [Elegir cómo inscribir los dispositivos iOS](ios-enroll.md)
- [Enroll iOS devices using Device Enrollment Program](https://docs.microsoft.com/intune/device-restrictions-ios#device-enrollment-program) (Inscripción de dispositivos iOS mediante el Programa de inscripción de dispositivos)

### <a name="usb-sa"></a>USB-SA
Los administradores de TI usan Apple Configurator a través de USB para preparar manualmente cada dispositivo corporativo para la inscripción mediante el Asistente de configuración. El administrador de TI crea un perfil de inscripción y lo exporta a Apple Configurator. Cuando los usuarios reciben sus dispositivos, se les solicita que ejecuten el Asistente de configuración para inscribirlos. Este método admite el modo **supervisado de iOS**, que a su vez permite las siguientes características:
  - Inscripción bloqueada
  - Modo de pantalla completa y otras configuraciones y restricciones avanzadas

Más información sobre la inscripción de iOS con Apple Configurator con el Asistente de configuración:

- [Decide how to enroll iOS devices](enrollment-method-choose-ios.md) (Decidir cómo inscribir dispositivos iOS)
- [Enroll iOS devices with Configurator and Setup Assistant](apple-configurator-setup-assistant-enroll-ios.md) (Inscripción de dispositivos iOS con el Asistente de configuración y Apple Configurator)

### <a name="usb-direct"></a>USB-Direct
Para realizar una inscripción directa, el administrador debe inscribir cada dispositivo manualmente creando una directiva de inscripción y exportándola a Apple Configurator. Los dispositivos corporativos conectados por USB se inscriben directamente, sin necesidad de un restablecimiento de fábrica. Los dispositivos se administran como dispositivos sin usuario. No se bloquean ni se supervisan y no son compatibles con el acceso condicional, la detección de jailbreak ni la administración de aplicaciones móviles.

Para más información sobre la inscripción de dispositivos iOS, consulte:

- [Decide how to enroll iOS devices](enrollment-method-choose-ios.md) (Decidir cómo inscribir dispositivos iOS)
- [Enroll iOS devices with Configurator and direct enrollment](apple-configurator-direct-enroll-ios.md) (Inscripción de dispositivos iOS con Apple Configurator y la inscripción directa)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Administración de dispositivos móviles con Exchange ActiveSync e Intune
Los dispositivos móviles que no estén inscritos, pero que se conecten a Exchange ActiveSync (EAS), se pueden administrar mediante Intune a través de la directiva de MDM de EAS. Intune usa Exchange Connector para comunicarse con EAS, tanto localmente como hospedado en la nube. Más información disponible próximamente.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpieza de dispositivos móviles tras la expiración del certificado MDM

El certificado MDM se renueva automáticamente cuando los dispositivos móviles se comunican con el servicio de Intune. Si se borran los dispositivos móviles o estos no pueden comunicarse con el servicio de Intune durante un tiempo, el certificado MDM no se renueva. El dispositivo se quita del portal de Azure 180 días después de que expire el certificado MDM.
