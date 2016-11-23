---
title: Administrar dispositivos corporativos | Microsoft Intune
description: "Inscriba dispositivos corporativos de muchas maneras, según el tipo de dispositivo, cómo se haya adquirido y las necesidades de la organización."
keywords: 
author: staciebarker
ms.author: stabar
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
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: 7577cbab528d88635e8551bf8de1ffd49becaa84


---

# <a name="enroll-corporateowned-devices-by-using-intune"></a>Inscripción de dispositivos corporativos mediante Intune

Puede inscribir dispositivos corporativos o propiedad de la organización para administrarlos con Intune de muchas maneras, en función del tipo de dispositivo, cómo se haya adquirido y las necesidades de la organización. También puede instalar la aplicación de Portal de empresa para inscribir y administrar dispositivos corporativos, como en un escenario "traiga su propio dispositivo" (BYOD).

## <a name="enroll-corporateowned-ios-devices"></a>Inscribir dispositivos iOS de empresa

Los métodos de inscripción de dispositivos corporativos son una buena opción para escenarios "elija su propio dispositivo" (CYOD). En un entorno CYOD, la organización paga por un dispositivo que el usuario selecciona, y es ella la que administra el dispositivo.

Si ofrece a los usuarios dispositivos iOS para que elijan, puede preconfigurar la inscripción para que el dispositivo se administre con Intune desde el mismo momento en que el usuario lo enciende por primera vez. Intune permite la inscripción mediante el [Programa de inscripción de dispositivos (DEP) de Apple](ios-device-enrollment-program-in-microsoft-intune.md) o con la herramienta Apple Configurator en un equipo Mac para inscripción [directa](ios-direct-enrollment-in-microsoft-intune.md) o con el [Asistente de configuración](ios-setup-assistant-enrollment-in-microsoft-intune.md).

Aprenda a [inscribir dispositivos iOS corporativos](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

## <a name="create-a-device-enrollment-manager-account"></a>Creación de una cuenta de administrador de inscripción de dispositivos

Puede crear una cuenta de administrador (DEM) de inscripción de dispositivos de usuario único en Intune para administrar un gran número de dispositivos móviles para su organización. Después de crear una cuenta DEM, un administrador de cuentas designado puede inscribir más de los 15 dispositivos que puede inscribir un usuario estándar.

Puede usar una cuenta DEM para inscribir solo dispositivos que no use un usuario específico. Estos tipos de dispositivos son buenos para aplicaciones de punto de venta o de utilidad, por ejemplo, pero inadecuados para usuarios que necesitan acceso al correo electrónico o a los recursos de empresa.

Más información sobre cómo [inscribir dispositivos corporativos mediante una cuenta DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

## <a name="enroll-corporateowned-windows-10-enterprise-devices"></a>Inscripción de dispositivos Windows 10 Enterprise corporativos

Si usa Azure Active Directory Premium o Microsoft Enterprise Mobility Suite en su organización, puede [inscribir dispositivos Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview). Cuando un usuario agrega una cuenta profesional o educativa a un dispositivo, el dispositivo se marca automáticamente como "corporativo".

## <a name="import-imei-numbers"></a>Importación de los números IMEI

Muchos fabricantes de dispositivos móviles usan un número único conocido como identidad de equipo de móvil internacional (IMEI) en sus dispositivos. Puede importar los números IMEI de dispositivos que posea su organización. Cuando el dispositivo pasa a administrarlo Intune, se etiqueta como un dispositivo corporativo.

Más información sobre cómo [etiquetar dispositivos corporativos mediante números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).

## <a name="identify-a-device-as-corporateowned"></a>Identificación de un dispositivo como corporativo

En una lista de dispositivos, el valor de **Propiedad** es **Corporativo**. Un dispositivo corporativo tiene una de estas características:

 - El dispositivo se [inscribió mediante una cuenta DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).
 - El dispositivo se inscribió mediante [DEP de Apple](ios-device-enrollment-program-in-microsoft-intune.md) o [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md).
 - El fabricante del dispositivo [declaró con anterioridad el dispositivo mediante números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).
 - El dispositivo está registrado en [Azure Active Directory o Enterprise Mobility Suite como un dispositivo Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview).



<!--HONumber=Nov16_HO2-->


