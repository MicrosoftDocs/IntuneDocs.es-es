---
title: Administrar dispositivos corporativos | Microsoft Docs
description: "Inscriba dispositivos corporativos de muchas maneras, según el tipo de dispositivo, cómo se haya adquirido y las necesidades de la organización."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 521a37044d6721fe905db7740329688ba2c24b35
ms.openlocfilehash: ae077d80e05b33d625285d796917f4f6c153ca3f
ms.lasthandoff: 01/31/2017


---

# <a name="enroll-corporate-owned-devices-by-using-intune"></a>Inscripción de dispositivos corporativos mediante Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Puede inscribir dispositivos corporativos o propiedad de la organización para administrarlos con Intune de muchas maneras, en función del tipo de dispositivo, cómo se haya adquirido y las necesidades de la organización. También puede instalar la aplicación de Portal de empresa para inscribir y administrar dispositivos corporativos, como en un escenario "traiga su propio dispositivo" (BYOD).

De manera predeterminada, los dispositivos de todas las plataformas pueden inscribirse en Intune. Para bloquear la inscripción de dispositivos, inicie sesión en el [portal de administración de Microsoft Intune](http://manage.microsoft.com) con sus credenciales de administrador. Elija **Administrador** > **Administración de dispositivos móviles** > **Reglas de inscripción** y después desactive las casillas correspondientes de las plataformas que quiera bloquear.

## <a name="enroll-corporate-owned-ios-devices"></a>Inscribir dispositivos iOS de empresa

Los métodos de inscripción de dispositivos corporativos son una buena opción para escenarios "elija su propio dispositivo" (CYOD). En un entorno CYOD, la organización paga por un dispositivo que el usuario selecciona, y es ella la que administra el dispositivo.

Si ofrece a los usuarios dispositivos iOS para que elijan, puede preconfigurar la inscripción para que el dispositivo se administre con Intune desde el mismo momento en que el usuario lo enciende por primera vez. Intune permite la inscripción mediante el [Programa de inscripción de dispositivos (DEP) de Apple](ios-device-enrollment-program-in-microsoft-intune.md) o con la herramienta Apple Configurator en un equipo Mac para inscripción [directa](ios-direct-enrollment-in-microsoft-intune.md) o con el [Asistente de configuración](ios-setup-assistant-enrollment-in-microsoft-intune.md).

Aprenda a [inscribir dispositivos iOS corporativos](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

## <a name="create-a-device-enrollment-manager-account"></a>Creación de una cuenta de administrador de inscripción de dispositivos

Puede crear una cuenta de administrador (DEM) de inscripción de dispositivos de usuario único en Intune para administrar un gran número de dispositivos móviles para su organización. Después de crear una cuenta DEM, un administrador de cuentas designado puede inscribir más de los 15 dispositivos que puede inscribir un usuario estándar.

Puede usar una cuenta DEM para inscribir solo dispositivos que no use un usuario específico. Estos tipos de dispositivos son buenos para aplicaciones de punto de venta o de utilidad, por ejemplo, pero inadecuados para usuarios que necesitan acceso al correo electrónico o a los recursos de empresa.

Más información sobre cómo [inscribir dispositivos corporativos mediante una cuenta DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

## <a name="enroll-corporate-owned-windows-10-enterprise-devices"></a>Inscripción de dispositivos Windows 10 Enterprise corporativos

Si usa Azure Active Directory Premium o Microsoft Enterprise Mobility Suite en su organización, puede [inscribir dispositivos Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview). Cuando un usuario agrega una cuenta profesional o educativa a un dispositivo, el dispositivo se marca automáticamente como "corporativo".

## <a name="import-imei-numbers"></a>Importación de los números IMEI

Muchos fabricantes de dispositivos móviles usan un número único conocido como identidad de equipo de móvil internacional (IMEI) en sus dispositivos. Puede importar los números IMEI de dispositivos que posea su organización. Cuando el dispositivo pasa a administrarlo Intune, se etiqueta como un dispositivo corporativo.

Más información sobre cómo [etiquetar dispositivos corporativos mediante números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).

## <a name="identify-a-device-as-corporate-owned"></a>Identificación de un dispositivo como corporativo

Intune reconoce un dispositivo como "corporativo" cuando cumple alguna de las condiciones siguientes:

 - El dispositivo se [inscribió mediante una cuenta DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) (todas las plataformas).
 - El dispositivo se inscribió mediante [DEP de Apple](ios-device-enrollment-program-in-microsoft-intune.md) o [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) (solo iOS).
 - El fabricante del dispositivo [declaró con anterioridad el dispositivo mediante números IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) (todas las plataformas con números IMEI).
 - El dispositivo está registrado en [Azure Active Directory o Enterprise Mobility Suite como un dispositivo Windows 10 Enterprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview) (solo Windows 10).

Cuando un dispositivo se etiqueta como corporativo, verá **Corporativo** en la columna **Propiedad** para ese registro del dispositivo en la consola de administrador. 

