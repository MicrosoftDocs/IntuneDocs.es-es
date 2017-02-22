---
title: "Novedades de la versión preliminar de Microsoft Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: descubra las novedades de la versión preliminar de Intune Azure"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/02/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e405363f9d0a89b1589b01d18ee8d2861b07ec60
ms.openlocfilehash: 70007f5501fba37964a0a54807c0e0f565510a74


---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Novedades de la versión preliminar de Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


A medida que avance la versión preliminar pública y se agreguen más características, proporcionaremos información sobre ellas aquí.

<!--## February 2017-->

<!--### Custom app categories <!--748805
You can now create, edit, and assign categories for apps you add to Intune. Currently, categories can only be specified in English.
See [How to add an app to Intune](/intune-azure/manage-apps/add-apps).-->

<!--### Display device categories <!--814654
You can now view the device category as a column in the device list. You can also edit the category from the properties section of the device properties blade.-->

## <a name="january-2017"></a>Enero de 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Asignar aplicaciones de línea de negocio en dispositivos inscritos y no inscritos <!--748823-->
Ahora puede asignar aplicaciones de línea de negocio desde la tienda a usuarios tengan o no inscritos sus dispositivos con Intune. Si el dispositivo de los usuarios no está inscrito con Intune, deben ir al sitio web del portal de empresa para instalarlo, en lugar de a la aplicación de portal de empresa. [¿Qué es la administración de aplicaciones?](/intune-azure/manage-apps/what-is-app-management)

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Resolver el problema en el que los dispositivos iOS están inactivos o la consola de administración no puede comunicarse con ellos
Cuando los dispositivos de los usuarios pierden el contacto con Intune, puede proporcionarles nuevos pasos de solución de problemas para ayudarles a volver a obtener acceso a los recursos de la empresa. Vea [Los dispositivos están inactivos o la consola de administración no puede comunicarse con ellos](/intune-azure/enroll-devices/troubleshoot-device-enrollment#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>Diciembre de 2016 (versión inicial)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integración de la administración de gastos de telecomunicaciones en la versión preliminar pública del portal de Azure<!--747605-->
Ahora estamos comenzando a realizar la integración de la versión preliminar con los servicios de administración de gastos de telecomunicaciones (TEM) dentro del portal de Azure. Puede usar Intune para exigir límites sobre el uso de datos nacionales y móviles. Comenzaremos estas integraciones con [Saaswedo](http://www.saaswedo.com). Para habilitar esta característica en su inquilino de prueba, [póngase en contacto con el soporte técnico de Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

- Implementación y administración de aplicaciones de la tienda en dispositivos iOS, Android y Windows
- Implementación y administración de aplicaciones de línea de negocio (LOB) en dispositivos iOS, Android y Windows
- Implementación y administración de aplicaciones compradas por volumen en dispositivos iOS y Windows
- Implementación y administración de aplicaciones web para dispositivos Android, iOS y Windows
- Perfiles de configuración de aplicaciones administrados por iOS
- Configuración de directivas de protección de aplicaciones e implementación de aplicaciones de línea de negocio en dispositivos no inscritos en Intune
- Perfiles de VPN, VPN por aplicación, Wi-Fi, correo electrónico y perfiles de certificado
- Directivas de cumplimiento
- Acceso condicional para Azure AD
- Acceso condicional para Exchange local
- Inscripción de dispositivos
- Control de acceso basado en roles

## <a name="deprecated-features-in-the-azure-portal"></a>Características en desuso en el portal de Azure

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Compatibilidad con la revisión fila a fila de identificadores de hardware
El portal de Azure no admite la revisión fila a fila de identificadores de hardware para números IMEI y números de serie de Apple. En la consola de Intune clásica, puede importar detalles de un archivo de valores separados por comas (.csv) y sobrescribir los detalles existentes para identificadores de hardware individuales. El portal de Azure presenta una única opción optimizada que sobrescribe automáticamente los detalles de todos los identificadores de hardware u omite nuevos detalles de identificadores existentes.

#### <a name="how-this-affects-you"></a>Cómo afecta esto
En el portal de Azure, no podrá decidir, fila a fila, qué dispositivos de identidad de equipo móvil internacional (IMEI) se actualizarán. La consola de Intune clásica seguirá admitiendo esta funcionalidad.

#### <a name="how-to-get-ready-for-this-change"></a>Cómo prepararse para este cambio
Vamos a proporcionar esta información de antemano; así, en caso de que le afecte, pueda informar a sus administradores de soporte técnico de este cambio. Este cambio coincidirá con el paso al portal de Azure, previsto para la primera mitad de 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Compatibilidad con perfiles de Inscripción de dispositivos corporativos en DEP de Apple
El portal de Azure no admite el perfil de inscripción de dispositivos corporativos "predeterminado" para los números de serie de dispositivo del Programa de inscripción de dispositivos de Apple (DEP). Esta funcionalidad, disponible en la consola de Intune clásica, está en desuso para evitar que se asignen perfiles involuntariamente. En el portal de Azure, los números de serie sincronizados desde una cuenta de DEP de Apple inicialmente no tendrán asignado ningún perfil de inscripción de dispositivos corporativos.

#### <a name="how-this-affects-you"></a>Cómo afecta esto
En el portal de Azure, no podrá establecer una directiva de perfil predeterminada en todos los dispositivos Apple. La consola de Intune clásica seguirá admitiendo esta funcionalidad.

#### <a name="how-to-get-ready-for-this-change"></a>Cómo prepararse para este cambio
Vamos a proporcionar esta información de antemano; así, en caso de que le afecte, pueda informar a sus administradores de soporte técnico de este cambio. Este cambio coincidirá con el movimiento al portal de Azure, previsto para la primera mitad de 2017.



<!--HONumber=Feb17_HO1-->


