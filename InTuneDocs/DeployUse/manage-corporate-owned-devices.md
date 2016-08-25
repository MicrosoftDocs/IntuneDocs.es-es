---
title: Administrar dispositivos corporativos | Microsoft Intune
description: "Administre los dispositivos corporativos (COD) de varias maneras en función del dispositivo, de cómo se adquirió y de las necesidades de la organización."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ecfeb73efed4a47256275120c52de232c556adfe
ms.openlocfilehash: 58efadf2f9fc34a31070aff93e86083583630caa


---

# Inscribir dispositivos corporativos con Microsoft Intune
Los dispositivos corporativos (COD) o de la organización se pueden administrar mediante Intune de varias maneras en función del dispositivo, de cómo se adquirió y de las necesidades de la organización. Los dispositivos corporativos también pueden inscribirse y administrarse mediante la instalación de la aplicación del portal de empresa como en escenarios "traiga su propio dispositivo" (BYOD).

## Dispositivos iOS corporativos
Estos métodos de inscripción son apropiados para escenarios de tipo “Elija su propio dispositivo” (CYOD), en los que la organización adquiere los dispositivos para los usuarios, pero desea conservar la administración de esos dispositivos. Si su organización ha adquirido dispositivos iOS, puede configurar previamente la inscripción para que el dispositivo se administre desde el momento mismo en que lo enciende el usuario. Intune permite inscribir dispositivos mediante el [programa de inscripción de dispositivos (DEP) de Apple](ios-device-enrollment-program-in-microsoft-intune.md) o la herramienta Apple Configurator en un equipo Mac, en inscripción [directa](ios-direct-enrollment-in-microsoft-intune.md) o con el [Asistente de configuración](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Inscribir dispositivos iOS de empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Administrador de inscripción de dispositivos
Las organizaciones pueden usar Intune para administrar un gran número de dispositivos móviles con una sola cuenta de usuario denominada cuenta de administrador de inscripción de dispositivos. Después de crear una cuenta de administrador de inscripción de dispositivos, el administrador puede usar esa cuenta para inscribir más dispositivos que los cinco permitidos para usuarios normales de forma predeterminada. La inscripción de dispositivos con un administrador de inscripción de dispositivos solo funciona con dispositivos que no son utilizados por un usuario específico. Estos dispositivos son buenos para aplicaciones de punto de venta o de utilidad, por ejemplo, pero inadecuados para usuarios que necesitan acceso a recursos de empresa o de correo electrónico.

[Inscribir dispositivos propiedad de la empresa con el administrador de inscripción de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## Inscribir equipos de escritorio Windows 10 corporativos

Si su organización tiene Azure Active Directory Premium (AADP) o Enterprise Management Suite (EMS), puede [inscribir dispositivos Windows 10 para empresa](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview) y se etiquetarán automáticamente como "corporativos" cuando los usuarios agreguen su cuenta profesional o educativa.

## Identificar dispositivos como corporativos

Los dispositivos corporativos aparecen como **Organización**  en **Propiedad** en listas de dispositivos. Los dispositivos se pueden identificar como corporativos de las siguientes maneras:

 - [Inscrito con el administrador de inscripción de dispositivos (DEM)](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)
 - Inscrito con el [ programa de inscripción de dispositivos (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) de Apple o [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md)
 - [Declarar previamente dispositivos con números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)
 - [Registro de dispositivos Windows 10 en Azure Active Directory/Enterprise Management Suite](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)

### Identidad de equipo móvil internacional (IMEI)

Los números de identidad de equipo móvil internacional (IMEI) son una propiedad común de los dispositivos de muchos fabricantes de dispositivos móviles. Los administradores de Intune pueden importar los números IMEI para los dispositivos propiedad de la compañía. Cuando el dispositivo pasa a administrarlo Intune, se etiqueta como un dispositivo corporativo.

[Especificar dispositivos corporativos con números de identidad de equipo móvil internacional (IMEI)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)



<!--HONumber=Jul16_HO4-->


