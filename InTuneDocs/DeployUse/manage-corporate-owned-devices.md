---
# required metadata

title: Administrar dispositivos corporativos | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscribir dispositivos corporativos con Microsoft Intune
Los dispositivos corporativos (COD) o de la organización se pueden administrar mediante Intune de varias maneras en función del dispositivo, de cómo se adquirió y de las necesidades de la organización.

## Dispositivos iOS corporativos
Estos métodos de inscripción son apropiados para escenarios de tipo “Elija su propio dispositivo” (CYOD), en los que la organización adquiere los dispositivos para los usuarios, pero desea conservar la administración de esos dispositivos. Si su organización ha adquirido dispositivos iOS, puede configurar previamente la inscripción para que el dispositivo se administre desde el momento mismo en que lo enciende el usuario. Intune permite inscribir dispositivos mediante el [programa de inscripción de dispositivos (DEP) de Apple](ios-device-enrollment-program-in-microsoft-intune.md) o la herramienta Apple Configurator en un equipo Mac, en inscripción [directa](ios-direct-enrollment-in-microsoft-intune.md) o con el [Asistente de configuración](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Inscribir dispositivos iOS de empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Administrador de inscripción de dispositivos
Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario denominada cuenta de administrador de inscripción de dispositivos. Después de crear una cuenta de administrador de inscripción de dispositivos, el administrador puede usar esa cuenta para inscribir más dispositivos que los cinco permitidos para usuarios normales de forma predeterminada. La inscripción de dispositivos con un administrador de inscripción de dispositivos solo funciona con dispositivos que no son utilizados por un usuario específico. Estos dispositivos son buenos para aplicaciones de punto de venta o de utilidad, por ejemplo, pero inadecuados para usuarios que necesitan acceso a recursos de empresa o de correo electrónico.

[Inscribir dispositivos propiedad de la empresa con el administrador de inscripción de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## Identidad de equipo móvil internacional (IMEI)
Los números de identidad de equipo móvil internacional (IMEI) son una propiedad común de los dispositivos de muchos fabricantes de dispositivos móviles. Los administradores de Intune pueden importar los números IMEI para los dispositivos propiedad de la compañía. Cuando el dispositivo pasa a ser administrado por Intune, se puede etiquetar como un dispositivo corporativo y se le puede aplicar la directiva adecuada.

[Especificar dispositivos corporativos con números de identidad de equipo móvil internacional (IMEI)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

## Información general de los métodos de inscripción de dispositivos corporativos

En la tabla siguiente se muestran los métodos de inscripción de dispositivos corporativos y sus ventajas.

**Métodos de inscripción de iOS**

| **Método** |  **[Restablecer](#Reset)** |   **[Afinidad](#Affinity)**   |   **[Bloqueado](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | No|    Sí |   No |
|**[DEM](#DEM)**|   No |No |No  |
|**[DEP](#DEP)**|   Sí |   Opt. |   Opt.|
|**[USB-SA](#USB-SA)**| Sí |   Opt. |   No|
|**[USB-Direct](#USB-Direct)**| No |    No  | No|

**Métodos de inscripción de Windows y Android**

| **Método** |  **[Eliminación de datos](#Wipe)** | **[User](#User)**   |   **[Bloqueado](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | No|    Sí |   No |
|**[DEM](#DEM)**|   No |No |No  |

**Métodos de inscripción de dispositivos corporativos**

### BYOD
“Bring Your Own Device”. Los usuarios instalan la aplicación Portal de empresa e inscriben su dispositivo. Cuando se inscribe un dispositivo con el Portal de empresa, se unirá al lugar de trabajo. La inscripción de dispositivos de iOS con el Portal de empresa requiere un identificador de Apple. BYOD no requiere configuración adicional para dispositivos corporativos. Vea los pasos para [configurar la administración de dispositivos](get-ready-to-enroll-devices-in-microsoft-intune#set-up-device-management.md).

### DEM
Administrador de inscripción de dispositivos. El administrador crea cuentas de DEM. Después, los administradores pueden instalar el Portal de empresa e inscribir muchos dispositivos sin usuario. Obtenga más información sobre [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Volver a la tabla](#overview-of corporate-owned-device-enrollment-methods))

### DEP
Programa de inscripción de dispositivos de Apple. El administrador crea e implementa directivas "de forma inalámbrica" para dispositivos iOS adquiridos y administrados con DEP. El dispositivo se inscribe cuando el usuario ejecuta el Asistente para la configuración de iOS. Este método admite el modo **iOS supervisado**, que a su vez permite lo siguiente:
  - Inscripción bloqueada
  - Acceso condicional
  - Detección de jailbreak
  - Administración de aplicaciones móviles

Obtenga más información sobre [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Volver a la tabla](#overview-of corporate-owned-device-enrollment-methods))

### USB-SA
Inscripción con el Asistente para la configuración, conectados por USB. El administrador crea una directiva de Intune y la exporta a Apple Configurator. Los dispositivos conectados por USB se preparan con directiva de Intune. El administrador debe inscribir manualmente cada dispositivo. Los usuarios reciben sus dispositivos y ejecutan el Asistente para la configuración, con lo que inscriben el dispositivo. Este método admite el modo **iOS supervisado**, que a su vez permite lo siguiente:
  - Inscripción bloqueada
  - Acceso condicional
  - Detección de jailbreak
  - Administración de aplicaciones móviles

Obtenga más información sobre la [inscripción con el Asistente para la configuración con Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Volver a la tabla](#overview-of corporate-owned-device-enrollment-methods))

### USB-Direct
Inscripción directa. El administrador crea una directiva de Intune y la exporta a Apple Configurator. Los dispositivos conectados por USB se inscriben directamente, sin necesidad de un restablecimiento de fábrica. El administrador debe inscribir manualmente cada dispositivo. Los dispositivos se administran como dispositivos sin usuario. No se bloquean ni se supervisan y no son compatibles con el acceso condicional, la detección de jailbreak ni la administración de aplicaciones móviles. Obtenga más información sobre la [inscripción directa con Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Volver a la tabla](#overview-of corporate-owned-device-enrollment-methods))

**Comportamiento de los dispositivos móviles corporativos**

### Restablecer
Especifica si el registro del dispositivo requiere el restablecimiento de fábrica del dispositivo, la eliminación de todos los datos y la restauración a su estado original.
([Volver a la tabla](#overview-of corporate-owned-device-enrollment-methods))

### Afinidad
Especifica si el método de inscripción permite la "afinidad de usuario", que conecta un dispositivo con un usuario específico. Los dispositivos "Opt." se pueden inscribir con o sin afinidad de usuario. La afinidad de usuario es necesaria para admitir lo siguiente:
  - Aplicaciones de administración de aplicaciones móviles (MAM)
  - Acceso condicional al correo electrónico y los datos de la empresa
  - Aplicación Portal de empresa

([Volver a la tabla](#overview-of corporate-owned-device-enrollment-methods)) ([Volver a la tabla](#overview-of corporate-owned-device-enrollment-methods))

### Bloqueo
Especifica si el dispositivo puede bloquearse para impedir que el usuario quite la directiva de Intune, con lo que quitaría el dispositivo de la administración. En el caso de los dispositivos iOS, el bloqueo del dispositivo requiere que se encuentre en modo Supervisado.
([Volver a la tabla](#overview-of corporate-owned-device-enrollment-methods)) ([Volver a la tabla](#overview-of corporate-owned-device-enrollment-methods))


<!--HONumber=Jun16_HO1-->


