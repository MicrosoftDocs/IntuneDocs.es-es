---
title: "¿Qué es la inscripción de dispositivos de Microsoft Intune?"
titlesuffix: Azure portal
description: "Aprenda sobre la inscripción de dispositivos iOS, Android y Windows."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/03/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bef73c81d285a6d320cd92b055ff2b5592a55af4
ms.sourcegitcommit: 001577b700f634da2fec0b44af2a378150d1f7ac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2017
---
# <a name="what-is-device-enrollment"></a>¿Qué es la inscripción de dispositivos?
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En este tema se describe qué es la inscripción y las diferentes formas de inscribir dispositivos móviles en la administración de Intune.

Los dispositivos se inscriben en Intune para poder administrarlos. En la documentación de Intune esta funcionalidad se conoce como administración de dispositivos móviles (MDM). Cuando los dispositivos se inscriben en Intune, se les emite un certificado MDM que los dispositivos usan para comunicarse con el servicio de Intune.

La forma en que inscriba a los dispositivos depende del tipo de dispositivo, la propiedad y el nivel de administración que sea necesario. La inscripción BYOD ("Bring your own device") permite a los usuarios inscribir sus teléfonos, tabletas o equipos personales. La inscripción de dispositivos corporativos (COD) permite escenarios de administración como la inscripción automática, los dispositivos compartidos o los requisitos de inscripción previamente autorizada.

Si usa Exchange ActiveSync, ya sea local u hospedado en la nube, puede habilitar la administración de Intune sencilla sin inscripción (en breve habrá más información disponible). Puede administrar PC con Windows como dispositivos móviles, que es el método recomendado que se describe a continuación.


## <a name="overview-of-device-enrollment-methods"></a>Información general de los métodos de inscripción de dispositivos

En la tabla siguiente se proporciona una visión general de los métodos de inscripción de Intune y se describen sus funcionalidades y requisitos.

**Leyenda**

- **Se requiere reinicio**: los dispositivos se restablecen de fábrica durante la inscripción.
- **Afinidad de usuario**: los dispositivos se asocian a los usuarios. Para obtener más información, vea [Inscribir dispositivos iOS de empresa en Microsoft Intune](device-enrollment-program-enroll-ios.md).
- **Bloqueado**: impide que los usuarios cancelen la inscripción de los dispositivos.

**Métodos de inscripción de iOS**

| **Método** |  **Se requiere reinicio** |    **Afinidad de usuario**   |   **Bloqueado** | **Detalles** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |   No | [Más información](./apple-mdm-push-certificate-get.md).|
|**[DEM](#dem)**|   No |No |No  | [Más información](./device-enrollment-program-enroll-ios.md).|
|**[DEP](#dep)**|   Sí |   Opcional |  Opcional|[Más información](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Sí |   Opcional |  No| [Más información](./apple-configurator-setup-assistant-enroll-ios.md).|
|**[USB-Direct](#usb-direct)**| No |    No  | No|[Más información](./apple-configurator-direct-enroll-ios.md).|

**Métodos de inscripción de Windows**

| **Método** |  **Se requiere reinicio** |    **Afinidad de usuario**   |   **Bloqueado** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No |   Sí |   No | [Más información](windows-enroll.md).|
|**[DEM](#dem)**|   No |No |No  |[Más información](device-enrollment-manager-enroll.md)|
|**Inscripción automática** | No |Sí |No | [Más información](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Inscripción masiva** |No |No |No | [Más información](./windows-bulk-enroll.md). |

**Métodos de inscripción de Android**

| **Método** |  **Se requiere reinicio** |    **Afinidad de usuario**   |   **Bloqueado** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |   No | [Más información](./android-enroll.md).|
|**[DEM](#dem)**|   No |No |No  |[Más información](./device-enrollment-program-enroll-ios.md)|
|**Android for Work**| No | Sí | No| [Más información](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="byod"></a>BYOD
Los usuarios "Bring your own device" instalan la aplicación del Portal de empresa e inscriben sus dispositivos. Este programa permite a los usuarios acceder a los recursos de la compañía, como el correo electrónico.

## <a name="corporate-owned-devices"></a>Dispositivos de propiedad corporativa
Los siguientes son escenarios de inscripción de dispositivos corporativos (COD). Los dispositivos iOS se pueden inscribir directamente a través de las herramientas proporcionadas por Apple. Un administrador puede inscribir cualquier tipo de dispositivo mediante el administrador de inscripción de dispositivos. Los dispositivos con un número IMEI también se pueden identificar y etiquetar como de propiedad corporativa para, así, posibilitar escenarios de dispositivos propiedad de la empresa.

### <a name="dem"></a>DEM
El administrador de inscripción de dispositivos (DEM) es una cuenta especial de usuario que se usa para inscribir y administrar varios dispositivos de la empresa. Los administradores pueden instalar el portal de empresa e inscribir muchos dispositivos sin usuario. Obtenga más información sobre [DEM](./device-enrollment-manager-enroll.md).

### <a name="dep"></a>DEP
La administración del Programa de inscripción de dispositivos (DEP) de Apple permite crear e implementar directivas "de forma inalámbrica" para dispositivos iOS que se han adquirido y administrado con DEP. El dispositivo se inscribe cuando los usuarios lo activan por primera vez y ejecutan el asistente de configuración de iOS. Este método admite el modo supervisado de iOS, que permite configurar un dispositivo con la siguiente funcionalidad:

- Bloqueo de aplicaciones (modo de aplicación única) 
- Proxy HTTP global 
- Bypass del bloqueo de activación 
- Modo de aplicación única autónoma 
- Filtro de contenido web 
- Establecer la pantalla de fondo y la pantalla de bloqueo 
- Inserción de aplicación silenciosa 
- VPN Always-On 
- Permitir la instalación de aplicaciones administradas de forma exclusiva 
- iBookstore 
- iMessages 
- Centro de juegos 
- AirDrop 
- AirPlay 
- Emparejamiento de host 
- Sincronización en la nube 
- Búsqueda en Spotlight 
- Handoff 
- Borrar dispositivo 
- Interfaz de usuario de restricciones 
- Instalación de perfiles de configuración por interfaz de usuario 
- Noticias 
- Métodos abreviados de teclado 
- Modificaciones de código de acceso 
- Cambios en los nombres de dispositivos 
- Cambios en los fondos de escritorio 
- Descargas de aplicaciones automáticas 
- Cambios en la confianza de las aplicaciones empresariales 
- Apple Music 
- Mail Drop 
- Emparejamiento con Apple Watch 

> [!NOTE]
> Apple ha confirmado que ciertas opciones de configuración se trasladarán al modo de solo supervisión en 2018. Le recomendamos que lo tenga en cuenta a la hora de usar estas opciones, en lugar de esperar a que Apple las migre al modo de solo supervisión:
> - Instalación de la aplicación
> - Eliminación de aplicaciones
> - FaceTime
> - Safari
> - iTunes
> - Contenido explícito
> - Documentos y datos de iCloud
> - Juego multijugador
> - Agregar amigos del centro de juegos

Más información sobre la inscripción de DEP de iOS:

- [Elegir cómo inscribir los dispositivos iOS](ios-enroll.md)
- [Enroll iOS devices using Device Enrollment Program](device-enrollment-program-enroll-ios.md) (Inscripción de dispositivos iOS mediante el Programa de inscripción de dispositivos)

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

El certificado MDM se renueva automáticamente cuando los dispositivos móviles se comunican con el servicio de Intune. Si se borran los dispositivos móviles o estos no pueden comunicarse con el servicio de Intune durante un tiempo, el certificado MDM no se renovará. El dispositivo se quita del portal de Azure 180 días después de que expire el certificado MDM.
