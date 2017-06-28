---
title: Inscribir dispositivos
description: "La administración de dispositivos móviles (MDM) hace uso de la inscripción para incluir dispositivos en la administración y permitir el acceso a los recursos."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: c7c4390629178256728c55e47f06bffae043a729
ms.contentlocale: es-es
ms.lasthandoff: 06/08/2017


---

# <a name="enroll-devices-for-management-in-intune"></a>Inscribir dispositivos para administrarlos en Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Puede inscribir dispositivos, incluidos equipos Windows, para habilitar la administración de dispositivos móviles (MDM) con Microsoft Intune. En este tema se describen diferentes maneras de inscribir dispositivos móviles en la administración de Intune. La forma en que inscriba los dispositivos depende del tipo de dispositivo, de la propiedad de los mismos y del nivel de administración que sea necesario. La inscripción BYOD ("Bring your own device") permite a los usuarios inscribir sus teléfonos, tabletas o equipos personales. La inscripción de dispositivos corporativos (COD) permite escenarios de administración como la inscripción automática, los dispositivos compartidos o los requisitos de inscripción previamente autorizada.

Si usa [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), ya sea local u hospedado en la nube, puede habilitar una administración de Intune sencilla sin inscripción. Los equipos Windows también se pueden administrar con el [software cliente de Intune](#manage-windows-pcs-with-intune).

De manera predeterminada, los dispositivos de todas las plataformas pueden inscribirse en Intune. Para bloquear la inscripción de dispositivos, inicie sesión en el [portal de administración de Microsoft Intune](https://manage.microsoft.com) con sus credenciales de administrador. Elija **Administrador** > **Administración de dispositivos móviles** > **Reglas de inscripción** y después desactive las casillas correspondientes de las plataformas que quiera bloquear.

## <a name="overview-of-device-enrollment-methods"></a>Información general de los métodos de inscripción de dispositivos

En la tabla siguiente se muestran los métodos de inscripción de Intune, así como las funciones admitidas y los requisitos de cada método. A continuación se describen las funciones y los requisitos.

- **Borrar**: indica si el dispositivo debe borrarse antes de que los usuarios lo inscriban. El término "borrado" significa el restablecimiento de fábrica del dispositivo, lo que elimina todos los datos. Para obtener más información, vea [Retirar dispositivos de la administración de Intune](retire-devices-from-microsoft-intune-management.md).
- **Afinidad**: los dispositivos se asocian a los usuarios. Es necesaria para la administración de aplicaciones móviles (MAM) y el acceso condicional a los datos de la empresa. Para obtener más información, vea [Inscribir dispositivos iOS de empresa en Microsoft Intune](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices).
- **Bloqueo**: indica si se evita que los usuarios anulen la inscripción de los dispositivos mediante menús nativos del sistema operativo. Los usuarios pueden anular la inscripción de sus dispositivos en todas las plataformas mediante el uso de su aplicación del portal de empresa.

**Métodos de inscripción de iOS**

| **Método** |  **¿Se requiere borrado?** |    **Afinidad**    |   **Bloqueo** | **Detalles** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |   No | [Más información](prerequisites-for-enrollment.md).|
|**[DEM](#dem)**|   No |No |No  | [Más información](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).|
|**[DEP](#dep)**|   Sí |   Opcional |  Opcional|[Más información](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Sí |   Opcional |  No| [Más información](ios-setup-assistant-enrollment-in-microsoft-intune.md).|
|**[USB-Direct](#usb-direct)**| No |    No  | No|[Más información](ios-direct-enrollment-in-microsoft-intune.md).|

**Métodos de inscripción de Windows**

| **Método** |  **¿Se requiere borrado?** |    **Afinidad**    |   **Bloqueo** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |   No | [Más información](prerequisites-for-enrollment.md).|
|**[DEM](#dem)**|   No |No |No  |[Más información](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).|

**Métodos de inscripción de Android**

| **Método** |  **¿Se requiere borrado?** |    **Afinidad**    |   **Bloqueo** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |   No | [Más información](prerequisites-for-enrollment.md).|
|**[DEM](#dem)**|   No |No |No  |[Más información](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Métodos de inscripción de Android for Work**

| **Método** |  **¿Se requiere borrado?** |    **Afinidad**    |   **Bloqueo** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |   No | [Más información](prerequisites-for-enrollment.md).|
|**[DEM](#dem)**|   No |No |No  |[Más información](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Métodos de inscripción de macOS**

| **Método** |  **¿Se requiere borrado?** |    **Afinidad**    |   **Bloqueo** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |   No | [Más información](prerequisites-for-enrollment.md).|


Para ver una serie de preguntas que pueden ayudarle a decidir el método adecuado, vea [Elegir cómo inscribir dispositivos móviles](/intune-classic/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD
Los usuarios "Bring your own device" instalan la aplicación Portal de empresa e inscriben su dispositivo. Esto permite a los usuarios conectarse a la red de la empresa y unirse al dominio o a Azure Active Directory. Para la mayoría de las plataformas, tiene que habilitar la inscripción BYOD en muchos escenarios COD. Para obtener más información, vea [Requisitos previos para la administración de dispositivos móviles en Intune](prerequisites-for-enrollment.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Dispositivos de propiedad corporativa
Los dispositivos corporativos (COD) se pueden administrar con la consola de Intune. Los dispositivos iOS se pueden inscribir directamente a través de las herramientas proporcionadas por Apple. Un administrador puede inscribir cualquier tipo de dispositivo mediante el administrador de inscripción de dispositivos. Los dispositivos con un número IMEI también se pueden identificar y etiquetar como de propiedad corporativa para, así, posibilitar escenarios de dispositivos propiedad de la empresa.

Para obtener más información, vea [Inscribir dispositivos corporativos con Microsoft Intune](manage-corporate-owned-devices.md).

### <a name="dem"></a>DEM
El administrador de inscripción de dispositivos es una cuenta especial de Intune que se usa para inscribir y administrar varios dispositivos corporativos. Los administradores pueden instalar el portal de empresa e inscribir muchos dispositivos sin usuario. Obtenga más información sobre [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
La administración del Programa de inscripción de dispositivos (DEP) de Apple permite crear e implementar directivas "de forma inalámbrica" para dispositivos iOS que se han adquirido y administrado con DEP. El dispositivo se inscribe cuando los usuarios lo activan por primera vez y ejecutan el asistente de configuración de iOS. Este método admite el modo **iOS supervisado**, que a su vez permite lo siguiente:
  - Inscripción bloqueada
  - Modo de pantalla completa y otras configuraciones y restricciones avanzadas

Obtenga más información sobre [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
Los administradores de TI usan Apple Configurator a través de la conexión USB para preparar manualmente cada dispositivo corporativo para la inscripción mediante el Asistente de configuración. El administrador de TI crea un perfil de inscripción y lo exporta a Apple Configurator. Cuando los usuarios reciben sus dispositivos, se les solicita que ejecuten el Asistente de configuración para inscribirlos. Este método admite el modo **iOS supervisado**, que a su vez permite lo siguiente:
  - Inscripción bloqueada
  - Modo de pantalla completa y otras configuraciones y restricciones avanzadas

Obtenga más información sobre la [inscripción con el Asistente para la configuración con Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

### <a name="usb-direct"></a>USB-Direct
Para realizar una inscripción directa, el administrador debe inscribir cada dispositivo manualmente creando una directiva de inscripción y exportándola a Apple Configurator. Los dispositivos corporativos conectados por USB se inscriben directamente, sin necesidad de un restablecimiento de fábrica. Los dispositivos se administran como dispositivos sin usuario. No se bloquean ni se supervisan y no son compatibles con el acceso condicional, la detección de jailbreak ni la administración de aplicaciones móviles.  Obtenga más información sobre la [inscripción directa con Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Administración de dispositivos móviles con Exchange ActiveSync e Intune
Los dispositivos móviles que no estén inscritos, pero que se conecten a Exchange ActiveSync (EAS), se pueden administrar mediante Intune a través de la directiva de MDM de EAS. Intune usa Exchange Connector para comunicarse con EAS, tanto localmente como hospedado en la nube. Para obtener más información, vea [Administración de dispositivos móviles con Exchange ActiveSync e Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).


## <a name="windows-pc-management-with-intune"></a>Administración de equipos con Windows con Intune  
Microsoft Intune también se puede usar para administrar equipos Windows con el software cliente de Intune. Los equipos que se administran con el cliente de Intune pueden:

 - Informar de los inventarios de software y hardware
 - Instalar aplicaciones de escritorio (por ejemplo, archivos .msi y .exe)
 - Administrar la configuración de firewall

Los equipos que se administran con el software cliente de Intune no pueden borrarse completamente, pero sí de manera selectiva. Los equipos administrados con el software cliente de Intune no se pueden beneficiar de muchas características de administración de Intune, por ejemplo, el acceso condicional, la configuración de VPN y Wi-Fi o la implementación de certificados y las configuraciones de correo electrónico. Para obtener más información, vea [Administración de PC con Windows con el software de cliente de PC de Intune](manage-windows-pcs-with-microsoft-intune.md).

## <a name="supported-device-platforms"></a>Plataformas de dispositivos compatibles

Intune puede administrar las siguientes plataformas de dispositivo:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## <a name="next-steps"></a>Pasos siguientes
- [Requisitos previos para la inscripción de dispositivos](prerequisites-for-enrollment.md)
- [Administración de dispositivos corporativos](manage-corporate-owned-devices.md)
- [Equipos y dispositivos móviles compatibles](/intune/supported-devices-browsers#intune-supported-devices)

