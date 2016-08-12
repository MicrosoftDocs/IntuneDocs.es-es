---
title: Inscribir dispositivos | Microsoft Intune
description: "La administración de dispositivos móviles (MDM) hace uso de la inscripción para incluir dispositivos en la administración y permitir el acceso a los recursos."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7bea7ba4ef59c6b1400414b59456e19dc1c152fb
ms.openlocfilehash: 41c21da7c95ef15f817aa344aa5b2d6479b65922


---

# Inscribir dispositivos para administrarlos en Intune
La administración de dispositivos móviles (MDM) de Microsoft Intune hace uso de la inscripción para incluir dispositivos en la administración y permitir el acceso a los recursos. La forma en que los dispositivos se inscriben depende del tipo de dispositivo, de la propiedad de los mismos y del nivel de administración necesario. En los escenarios "Bring Your Own Device" (BYOD) y de dispositivos propiedad de la empresa se necesita un proceso de inscripción. Las organizaciones con Exchange ActiveSync (ya sea local u hospedado en la nube) permiten una administración más fluida, sin requisitos de inscripción. Los PC Windows también se pueden administrar con el software cliente de Intune.

###  Plataformas de dispositivos compatibles

Intune puede administrar las siguientes plataformas de dispositivo:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Establecer la entidad de administración de dispositivos móviles
La entidad de MDM define el servicio de administración que tiene permiso para administrar un conjunto de dispositivos. Las opciones para la entidad de MDM incluyen Intune y Configuration Manager con Intune. Si establece Configuration Manager como la entidad de administración, ningún otro servicio podrá usarse para la administración de dispositivos móviles.

>[!IMPORTANT]
> Considere detenidamente si quiere administrar los dispositivos móviles solo mediante Intune (servicio en línea) o mediante System Center Configuration Manager con Intune (solución de software local junto con el servicio en línea). Una vez que establezca la entidad de administración de dispositivos móviles, esta no se puede cambiar.

1.  En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), haga clic en **Administración** &gt; **Administración de dispositivos móviles**.

2.  En la lista **Tareas** , haga clic en **Configurar entidad de administración de dispositivos móviles**. Se abre el cuadro de diálogo **Establecer entidad de administración de dispositivos móviles** .

    ![Cuadro de diálogo Establecer entidad de MDM](../media/intune-mdm-authority.png)

3.  Intune solicita confirmación de que desea que Intune sea su entidad de MDM. Seleccione la casilla y elija **Sí** si quiere usar Microsoft Intune para administrar dispositivos móviles.

## Configurar el portal de empresa de Intune

El portal de empresa de Intune es el lugar donde los usuarios tienen acceso a los datos de la empresa y pueden realizar tareas habituales como, por ejemplo, inscribir dispositivos, instalar aplicaciones y buscar información de ayuda del departamento de TI.

> [!TIP]
> Al personalizar el portal de empresa, los valores de configuración se aplicarán tanto al sitio web como a las aplicaciones del portal de empresa.

Con la personalización del Portal de empresa, es más fácil ofrecer una experiencia conocida y útil a los usuarios finales. Para proceder a la personalización, inicie sesión en la [consola de administración de Microsoft Intune](https://manage.microsoft.com) como administrador de inquilinos o de servicios, elija **Administración** &gt; **Portal de empresa** y configure el Portal de empresa.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

## Información general de los métodos de inscripción de dispositivos

En la siguiente tabla se muestran los métodos de inscripción de dispositivos corporativos y sus ventajas.

**Métodos de inscripción de iOS**

| **Método** |  **[Eliminación de datos](#Wipe)** | **[Afinidad](#Affinity)**   |   **[Bloqueado](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | No|    Sí |   No |
|**[DEM](#DEM)**|   No |No |No  |
|**[DEP](#DEP)**|   Sí |   Opt. |   Opt.|
|**[USB-SA](#USB-SA)**| Sí |   Opt. |   No|
|**[USB-Direct](#USB-Direct)**| No |    No  | No|

**Métodos de inscripción de Windows y Android**

| **Método** |  **[Eliminación de datos](#Wipe)** | **[Afinidad](#Affinity)**   |   **[Bloqueado](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | No|    Sí |   No |
|**[DEM](#DEM)**|   No |No |No  |

**Métodos de inscripción de dispositivos corporativos**

### BYOD
“Bring Your Own Device”. Los usuarios instalan la aplicación de portal de empresa e inscriben su dispositivo. Cuando se inscribe un dispositivo con el portal de empresa, se unirá al lugar de trabajo. La inscripción de dispositivos de iOS con el portal de empresa requiere un identificador de Apple. BYOD no requiere configuración adicional para dispositivos corporativos. Vea los pasos para [configurar la administración de dispositivos](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management). ([Volver a la tabla](#overview-of-device-enrollment-methods))

### DEM
Administrador de inscripción de dispositivos. El administrador crea cuentas de DEM para administrar dispositivos propiedad de la empresa. Después, los administradores pueden instalar el portal de empresa e inscribir muchos dispositivos sin usuario. Obtenga más información sobre [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Volver a la tabla](#overview-of-device-enrollment-methods))

### DEP
Programa de inscripción de dispositivos de Apple. El administrador crea e implementa directivas "de forma inalámbrica" para dispositivos iOS propiedad de la empresa adquiridos y administrados con DEP. El dispositivo se inscribe cuando el usuario ejecuta el Asistente para la configuración de iOS. Este método admite el modo **iOS supervisado**, que a su vez permite lo siguiente:
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

**Comportamiento de los dispositivos móviles corporativos**

### Eliminación de datos
Especifica si el registro del dispositivo requiere el restablecimiento de fábrica del dispositivo, la eliminación de todos los datos y la restauración a su estado original.
[Retirar dispositivos](retire-devices-from-microsoft-intune-management.md) ([Volver a la tabla](#overview-of-device-enrollment-methods))

### Afinidad
Especifica si el método de inscripción permite la "afinidad de usuario", que conecta un dispositivo con un usuario específico. Los dispositivos "Opt." se pueden inscribir con o sin afinidad de usuario. La afinidad de usuario es necesaria para admitir lo siguiente:
  - Aplicaciones de administración de aplicaciones móviles (MAM)
  - Acceso condicional al correo electrónico y los datos de la empresa
  - Aplicación de portal de empresa

[Afinidad de usuario](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices) ([Volver a la tabla](#overview-of-device-enrollment-methods))

### Bloqueo
Especifica si el dispositivo puede bloquearse para impedir que el usuario quite la directiva de Intune, con lo que quitaría el dispositivo de la administración. En el caso de los dispositivos iOS, el bloqueo del dispositivo requiere que se encuentre en modo Supervisado.
([Volver a la tabla](#overview-of-device-enrollment-methods))

## Permitir la inscripción de dispositivos  
 Con la inscripción, los usuarios pueden tener acceso a los recursos empresariales en sus dispositivos personales y el administrador puede asegurarse de que dichos dispositivos cumplen las directivas que protegen esos recursos. Se trata de la mejor manera de dar cabida a escenarios de tipo "Bring Your Own Device" con Intune. El administrador debe habilitar la inscripción en la consola de Intune, lo que podría conllevar la creación de una relación de confianza con el dispositivo y la asignación de licencias a los usuarios. Tras ello, el dispositivo se inscribe, cosa que los usuarios realizan normalmente especificando sus credenciales profesionales o educativas. Después, el dispositivo recibe la directiva de Intune y obtiene acceso a los recursos.

[Preparar la inscripción de dispositivos en Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)

## Inscribir dispositivos de propiedad corporativa
Los dispositivos de propiedad corporativa se pueden administrar con la consola de Intune. Los dispositivos iOS se pueden inscribir directamente a través de las herramientas proporcionadas por Apple. Un administrador puede inscribir cualquier tipo de dispositivo mediante el administrador de inscripción de dispositivos. Los dispositivos con un número IMEI también se pueden identificar y etiquetar como de propiedad corporativa para, así, posibilitar escenarios de dispositivos propiedad de la empresa.

[Inscribir dispositivos de propiedad corporativa](manage-corporate-owned-devices.md)

## Administración de dispositivos móviles con Exchange ActiveSync e Intune
Los dispositivos móviles que no estén inscritos, pero que se conecten a Exchange ActiveSync (EAS), se pueden administrar mediante Intune a través de la directiva de MDM de EAS. Intune usa Exchange Connector para comunicarse con EAS, tanto localmente como hospedado en la nube.

[Administración de dispositivos móviles con Exchange ActiveSync e Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Administrar equipos Windows con Intune  
Microsoft Intune también se puede usar para administrar PC Windows con el software cliente de PC Windows de Intune. Los PC administrados con el cliente de Intune pueden encargarse de lo siguiente:

 - Informar de los inventarios de software y hardware
 - Instalar aplicaciones de escritorio (por ejemplo, archivos .msi y .exe)
 - Configuración del firewall

Los equipos administrados con el software cliente de Intune no se pueden borrar ni retirar de forma selectiva de Intune, como tampoco pueden beneficiarse de muchas características de administración de Intune, por ejemplo, el acceso condicional, la configuración de VPN y Wi-Fi o la implementación de certificados y las configuraciones de correo electrónico.

[Administrar equipos Windows con Intune](manage-windows-pcs-with-microsoft-intune.md)



<!--HONumber=Aug16_HO2-->


