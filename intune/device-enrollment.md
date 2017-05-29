---
title: "¿Qué es la inscripción de dispositivos de Microsoft Intune?"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda sobre la inscripción de dispositivos iOS, Android y Windows."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 57bad4be991b61fe5212d340ab8d89cb6af3b0f7
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="what-is-device-enrollment"></a>¿Qué es la inscripción de dispositivos?
[!INCLUDE[azure_preview](./includes/azure_preview.md)]

En este tema se describe qué es la inscripción y las diferentes formas de inscribir dispositivos móviles en la administración de Intune.

Los dispositivos se inscriben en Intune para poder administrarlos. En la documentación de Intune esta funcionalidad se conoce como administración de dispositivos móviles (MDM). Cuando los dispositivos se inscriben en Intune, se les emite un certificado MDM que los dispositivos usan para comunicarse con el servicio de Intune.

La forma en que inscriba a los dispositivos depende del tipo de dispositivo, la propiedad y el nivel de administración que sea necesario. La inscripción BYOD ("Bring your own device") permite a los usuarios inscribir sus teléfonos, tabletas o equipos personales. La inscripción de dispositivos corporativos (COD) permite escenarios de administración como la inscripción automática, los dispositivos compartidos o los requisitos de inscripción previamente autorizada.

Si usa Exchange ActiveSync, ya sea local u hospedado en la nube, puede habilitar la administración de Intune sencilla sin inscripción (en breve habrá más información disponible). Puede administrar PC con Windows como dispositivos móviles, que es el método recomendado que se describe a continuación.


## <a name="overview-of-device-enrollment-methods"></a>Información general de los métodos de inscripción de dispositivos

En la tabla siguiente se muestran los métodos de inscripción de Intune, así como las funciones admitidas y los requisitos de cada método. A continuación se describen las funciones y los requisitos. En la tabla se emplean los términos siguientes:

- **Borrar**: indica si el dispositivo debe borrarse antes de que los usuarios lo inscriban. El término "borrado" significa el restablecimiento de fábrica del dispositivo, lo que elimina todos los datos. Para más información, consulte [Use full or selective wipe on devices](devices-wipe.md) (Uso de borrado completo o selectivo en los dispositivos).
- **Afinidad**: los dispositivos se asocian a los usuarios. Es necesaria para la administración de aplicaciones móviles (MAM) y el acceso condicional a los datos de la empresa. Para obtener más información, vea [Inscribir dispositivos iOS de empresa en Microsoft Intune](device-enrollment-program-enroll-ios.md).
- **Bloqueo**: indica si se impide que los usuarios anulen la inscripción de la administración de sus dispositivos. Los usuarios pueden anular la inscripción de sus dispositivos en todas las plataformas mediante el uso de su aplicación del portal de empresa. No pueden usar los menús del sistema operativo nativo para anular la inscripción.


**Métodos de inscripción de iOS**

| **Método** |    **¿Se requiere borrado?** |    **Afinidad**    |    **Bloqueo** | **Detalles** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |    No | Más información disponible próximamente|
|**[DEM](#dem)**|    No |No |No    | [Más información](device-enrollment-program-enroll-ios.md).|
|**[DEP](#dep)**|    Sí |    Opcional |    Opcional|[Más información](device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**|    Sí |    Opcional |    No| [Más información](apple-configurator-setup-assistant-enroll-ios.md).|
|**[USB-Direct](#usb-direct)**|    No |    No    | No|[Más información](apple-configurator-direct-enroll-ios.md).|

**Métodos de inscripción de Windows**

| **Método** |    **¿Se requiere borrado?** |    **Afinidad**    |    **Bloqueo** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No |    Sí |    No | [Más información](windows-enroll.md).|
|**[DEM](#dem)**|    No |No |No    |[Más información](device-enrollment-manager-enroll.md).|

**Métodos de inscripción de Android**

| **Método** |    **¿Se requiere borrado?** |    **Afinidad**    |    **Bloqueo** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |    No | [Más información](android-enroll.md).|
|**[DEM](#dem)**|    No |No |No    |[Más información](device-enrollment-program-enroll-ios.md)|
|**Android for Work**| No | Sí | No| [Más información](android-enroll.md) |


## <a name="byod"></a>BYOD
Los usuarios "Bring your own device" instalan la aplicación Portal de empresa e inscriben su dispositivo. Esto permite a los usuarios conectarse a la red de la empresa y unirse al dominio o a Azure Active Directory. Para la mayoría de las plataformas, tiene que habilitar la inscripción BYOD en muchos escenarios COD. Puede bloquear la inscripción de los dispositivos Android e iOS de propiedad personal. Vea [Set device type restrictions](enrollment-restrictions-set.md#set-device-type-restrictions) (Establecer restricciones de tipos de dispositivo) para obtener instrucciones.

## <a name="corporate-owned-devices"></a>Dispositivos de propiedad corporativa
Los dispositivos corporativos (COD) se pueden administrar mediante el portal de Azure. Los dispositivos iOS se pueden inscribir directamente a través de las herramientas proporcionadas por Apple. Un administrador puede inscribir cualquier tipo de dispositivo mediante el administrador de inscripción de dispositivos. Los dispositivos con un número IMEI también se pueden identificar y etiquetar como de propiedad corporativa para, así, posibilitar escenarios de dispositivos propiedad de la empresa.

### <a name="dem"></a>DEM
El administrador de inscripción de dispositivos (DEM) es una cuenta especial de usuario que se usa para inscribir y administrar varios dispositivos de la empresa. Los administradores pueden instalar el portal de empresa e inscribir muchos dispositivos sin usuario. Obtenga más información sobre [DEM](device-enrollment-manager-enroll.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
La administración del Programa de inscripción de dispositivos (DEP) de Apple permite crear e implementar directivas "de forma inalámbrica" para dispositivos iOS que se han adquirido y administrado con DEP. El dispositivo se inscribe cuando los usuarios lo activan por primera vez y ejecutan el asistente de configuración de iOS. Este método admite el modo **iOS supervisado**, que a su vez permite lo siguiente:

  -    Inscripción bloqueada
  -    Modo de pantalla completa y otras configuraciones y restricciones avanzadas

Para más información sobre la inscripción de dispositivos iOS, consulte:

- [Elegir cómo inscribir los dispositivos iOS](enrollment-method-choose-ios.md)
- [Enroll iOS devices using Device Enrollment Program](device-enrollment-program-enroll-ios.md) (Inscripción de dispositivos iOS mediante el Programa de inscripción de dispositivos)
- [Volver a la tabla anterior](#overview-of-device-enrollment-methods)

### <a name="usb-sa"></a>USB-SA
Los administradores de TI usan Apple Configurator a través de la conexión USB para preparar manualmente cada dispositivo corporativo para la inscripción mediante el Asistente de configuración. El administrador de TI crea un perfil de inscripción y lo exporta a Apple Configurator. Cuando los usuarios reciben sus dispositivos, se les solicita que ejecuten el Asistente de configuración para inscribirlos. Este método admite el modo **iOS supervisado**, que a su vez permite lo siguiente:
  -    Inscripción bloqueada
  -    Modo de pantalla completa y otras configuraciones y restricciones avanzadas

Para más información sobre la inscripción de dispositivos iOS, consulte:

- [Decide how to enroll iOS devices](enrollment-method-choose-ios.md) (Decidir cómo inscribir dispositivos iOS)
- [Enroll iOS devices with Configurator and Setup Assistant](apple-configurator-setup-assistant-enroll-ios.md) (Inscripción de dispositivos iOS con el Asistente de configuración y Apple Configurator)

### <a name="usb-direct"></a>USB-Direct
Para realizar una inscripción directa, el administrador debe inscribir cada dispositivo manualmente creando una directiva de inscripción y exportándola a Apple Configurator. Los dispositivos corporativos conectados por USB se inscriben directamente, sin necesidad de un restablecimiento de fábrica. Los dispositivos se administran como dispositivos sin usuario. No se bloquean ni se supervisan y no son compatibles con el acceso condicional, la detección de jailbreak ni la administración de aplicaciones móviles.

Para más información sobre la inscripción de dispositivos iOS, consulte:

- [Decide how to enroll iOS devices](enrollment-method-choose-ios.md) (Decidir cómo inscribir dispositivos iOS)
- [Enroll iOS devices with Configurator and direct enrollment](apple-configurator-direct-enroll-ios.md) (Inscripción de dispositivos iOS con Apple Configurator y la inscripción directa)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Administración de dispositivos móviles con Exchange ActiveSync e Intune
Los dispositivos móviles que no estén inscritos, pero que se conecten a Exchange ActiveSync (EAS), se pueden administrar mediante Intune a través de la directiva de MDM de EAS. Intune usa Exchange Connector para comunicarse con EAS, tanto localmente como hospedado en la nube. Más información disponible próximamente.

## <a name="supported-device-platforms-and-browsers"></a>Exploradores y plataformas de dispositivos compatibles

Consulte [Dispositivos y exploradores admitidos para Intune](https://docs.microsoft.com/intune-classic/get-started/supported-mobile-devices-and-computers)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpieza de dispositivos móviles tras la expiración del certificado MDM

El certificado MDM se renueva automáticamente cuando los dispositivos móviles se comunican con el servicio de Intune. Si se borran los dispositivos móviles o estos no pueden comunicarse con el servicio de Intune durante un tiempo, el certificado MDM no se renovará. El dispositivo se quita del portal de Azure 180 días después de que expire el certificado MDM.

