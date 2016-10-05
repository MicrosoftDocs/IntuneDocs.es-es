---
title: Inscribir dispositivos | Microsoft Intune
description: "La administración de dispositivos móviles (MDM) hace uso de la inscripción para incluir dispositivos en la administración y permitir el acceso a los recursos."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6b182ebab1691c62e69cabaf4689ac7395ab31a
ms.openlocfilehash: 0995d3ced978f5213fdb0e9905f508b64a1e5c09


---

# Inscribir dispositivos para administrarlos en Intune
Puede inscribir dispositivos, incluidos equipos Windows, para habilitar la administración de dispositivos móviles (MDM) con Microsoft Intune. En este tema se describen diferentes maneras de inscribir dispositivos móviles en la administración de Intune. La forma de inscribir dispositivos depende del tipo de dispositivo, de la propiedad y del nivel de administración necesario. La inscripción BYOD ("Bring your own device") permite a los usuarios inscribir sus teléfonos, tabletas o equipos personales. La inscripción de dispositivos corporativos (COD) permite escenarios de administración como barrido remoto, dispositivos compartidos o afinidad de usuario para un dispositivo.

Si usa [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), ya sea local u hospedado en la nube, puede habilitar una administración de Intune sencilla sin inscripción. Los equipos Windows también se pueden administrar con el [software cliente de Intune](#manage-windows-pcs-with-intune).

## Información general de los métodos de inscripción de dispositivos

En la siguiente tabla se muestran los métodos de inscripción de Intune con sus funciones admitidas. Estas funciones incluyen:
- **Barrido**: restablecimiento de fábrica del dispositivo, quitando todos los datos. [Retirar dispositivos](retire-devices-from-microsoft-intune-management.md)
- **Afinidad**: los dispositivos se asocian a los usuarios. Es necesaria para la administración de aplicaciones móviles (MAM) y el acceso condicional a los datos de la empresa. [Afinidad de usuario](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)
- **Bloqueo**: evita que los usuarios quiten el dispositivo de la administración. Los dispositivos iOS necesitan el modo supervisado para el bloqueo. [Bloqueo remoto](retire-devices-from-microsoft-intune-management.md#block-access-a-device)

**Métodos de inscripción de iOS**

| **Método** |  **Eliminación de datos** |  **Afinidad**    |   **Bloqueo** | **Detalles** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |   No | [más](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   No |No |No  | [más](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Sí |   Opcional |  Opcional|[más](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Sí |   Opcional |  No| [más](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| No |    No  | No|[más](ios-direct-enrollment-in-microsoft-intune.md)|

**Métodos de inscripción de Windows y Android**

| **Método** |  **Eliminación de datos** |  **Afinidad**    |   **Bloqueo** | **Detalles**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | No|    Sí |   No | [más](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   No |No |No  |[más](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

Para ver una serie de preguntas que pueden ayudarle a decidir el método adecuado, consulte [Elegir cómo inscribir dispositivos móviles](/intune/get-started/choose-how-to-enroll-devices1).

## BYOD
Los usuarios "Bring your own device" instalan la aplicación Portal de empresa e inscriben su dispositivo. Esto les permite conectarse a la red de la empresa, uniéndose al dominio o a Azure Active Directory. La activación de la inscripción BYOD es un requisito previo para muchos escenarios COD en la mayoría de las plataformas. Consulte [Requisitos previos para la inscripción de dispositivos](prerequisites-for-enrollment.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

## Dispositivos de propiedad corporativa
Los dispositivos de propiedad corporativa se pueden administrar con la consola de Intune. Los dispositivos iOS se pueden inscribir directamente a través de las herramientas proporcionadas por Apple. Un administrador puede inscribir cualquier tipo de dispositivo mediante el administrador de inscripción de dispositivos. Los dispositivos con un número IMEI también se pueden identificar y etiquetar como de propiedad corporativa para, así, posibilitar escenarios de dispositivos propiedad de la empresa.

[Inscribir dispositivos de propiedad corporativa](manage-corporate-owned-devices.md)

### DEM
El administrador de inscripción de dispositivos es una cuenta especial de Intune que se usa para inscribir y administrar varios dispositivos de propiedad corporativa. Los administradores pueden instalar el portal de empresa e inscribir muchos dispositivos sin usuario. Obtenga más información sobre [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

### DEP
La administración del Programa de Inscripción de Dispositivos (DEP) de Apple permite crear e implementar directivas "por aire" para dispositivos iOS adquiridos y administrados con DEP. El dispositivo se inscribe cuando el usuario lo activa por primera vez y ejecuta el asistente de configuración de iOS. Este método admite el modo **iOS supervisado**, que a su vez permite lo siguiente:
  - Inscripción bloqueada
  - Acceso condicional
  - Detección de jailbreak
  - Administración de aplicaciones móviles

Obtenga más información sobre [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

### USB-SA
Inscripción con el Asistente para la configuración, conectados por USB. El administrador crea una directiva de Intune y la exporta a Apple Configurator. Los dispositivos propiedad de la empresa conectados por USB se preparan con la directiva de Intune. El administrador debe inscribir manualmente cada dispositivo. Los usuarios reciben sus dispositivos y ejecutan el Asistente para la configuración, con lo que inscriben el dispositivo. Este método admite el modo **iOS supervisado**, que a su vez permite lo siguiente:
  - Acceso condicional
  - Detección de jailbreak
  - Administración de aplicaciones móviles

Obtenga más información sobre la [inscripción con el Asistente para la configuración con Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

### USB-Direct
Inscripción directa. El administrador crea una directiva de Intune y la exporta a Apple Configurator. Los dispositivos propiedad de la empresa conectados por USB se inscriben directamente, sin necesidad de un restablecimiento de fábrica. El administrador debe inscribir manualmente cada dispositivo. Los dispositivos se administran como dispositivos sin usuario. No se bloquean ni se supervisan y no son compatibles con el acceso condicional, la detección de jailbreak ni la administración de aplicaciones móviles. Obtenga más información sobre la [inscripción directa con Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

## Administración de dispositivos móviles con Exchange ActiveSync e Intune
Los dispositivos móviles que no estén inscritos, pero que se conecten a Exchange ActiveSync (EAS), se pueden administrar mediante Intune a través de la directiva de MDM de EAS. Intune usa Exchange Connector para comunicarse con EAS, tanto localmente como hospedado en la nube.

[Administración de dispositivos móviles con Exchange ActiveSync e Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Administrar equipos Windows con Intune  
Microsoft Intune también se puede usar para administrar equipos Windows con el software cliente de Intune. Los PC administrados con el cliente de Intune pueden encargarse de lo siguiente:

 - Informar de los inventarios de software y hardware
 - Instalar aplicaciones de escritorio (por ejemplo, archivos .msi y .exe)
 - Configuración del firewall

Los equipos administrados con el software cliente de Intune no se pueden borrar, como tampoco pueden beneficiarse de muchas características de administración de Intune, por ejemplo, el acceso condicional, la configuración de VPN y Wi-Fi o la implementación de certificados y las configuraciones de correo electrónico.

[Administrar equipos Windows con Intune](manage-windows-pcs-with-microsoft-intune.md)

##  Plataformas de dispositivos compatibles

Intune puede administrar las siguientes plataformas de dispositivo:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Pasos siguientes
- [Requisitos previos para la inscripción de dispositivos](prerequisites-for-enrollment.md)
- [Administrar dispositivos propiedad de la empresa](manage-corporate-owned-devices.md)
- [Equipos y dispositivos móviles compatibles](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Sep16_HO3-->


