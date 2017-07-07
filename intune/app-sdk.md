---
title: Ventajas del SDK para aplicaciones de Intune
description: "El SDK para aplicaciones de Intune está disponible para las plataformas iOS y Android y, gracias a él, podrá habilitar las características de administración de aplicaciones móviles con Microsoft Intune."
keywords: 
author: mtillman
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8a9b0c398c4b6dd46823ceaaefd68ee193ab4502
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="intune-app-sdk-overview"></a>Información general del SDK para aplicaciones de Intune
El SDK de aplicaciones de Intune, disponible para iOS y Android, habilita su aplicación para las directivas de protección de aplicaciones de Intune. Su objetivo es minimizar la cantidad de cambios de código que debe realizar el desarrollador de la aplicación. Encontrará que puede habilitar la mayoría de las características del SDK sin necesidad de cambiar el comportamiento de la aplicación. Para obtener una experiencia de administrador de TI y de usuario final mejorada, puede usar nuestras API para personalizar el comportamiento de la aplicación para aquellas características que requieren la participación de la aplicación.

Una vez que haya habilitado su aplicación para las directivas de protección de aplicaciones, los administradores de TI pueden implementar estas directivas para proteger sus datos corporativos dentro de la aplicación.

## <a name="app-protection-features"></a>Características de protección de aplicaciones

A continuación se muestran ejemplos de características de protección de aplicaciones de Intune que pueden habilitarse con el SDK.

### <a name="control-users-ability-to-move-corporate-files"></a>Controlar la capacidad de los usuarios para mover archivos de empresa
Los administradores de TI pueden controlar dónde pueden moverse los datos profesionales o educativos en la aplicación. Por ejemplo, pueden implementar una directiva que impida a la aplicación realizar copias de seguridad de datos corporativos en la nube.

### <a name="configure-clipboard-restrictions"></a>Configurar las restricciones del portapapeles
Los administradores de TI pueden configurar el comportamiento del portapapeles en aplicaciones administradas por Intune. Por ejemplo, pueden implementar una directiva que impida que los usuarios finales corten o copien datos de la aplicación y los peguen en una aplicación personal no administrada.

### <a name="enforce-encryption-on-saved-data"></a>Aplicar el cifrado en los datos guardados
Los administradores de TI pueden aplicar una directiva que garantice el cifrado de los datos guardados en el dispositivo por parte de la aplicación.

### <a name="remotely-wipe-corporate-data"></a>Borrado remoto de datos corporativos
Los administradores de TI pueden borrar remotamente datos corporativos desde una aplicación administrada por Intune. Esta característica está basada en identidades y eliminará tan solo los archivos asociados con la identidad corporativa del usuario final. Para ello, la característica requiere la participación de la aplicación. La aplicación puede especificar la identidad para la que debe producirse el borrado en función de la configuración de usuario. Si esta configuración especificada por el usuario no se encuentra en la aplicación, el comportamiento predeterminado será borrar el directorio de la aplicación y notificar al usuario final que se ha quitado el acceso.

### <a name="enforce-the-use-of-a-managed-browser"></a>Exigir el uso de un explorador administrado
Los administradores de TI pueden forzar los vínculos web de la aplicación para que se abran con la [aplicación Managed Browser de Intune](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies). Esto garantiza que los vínculos que aparecen en un entorno corporativo se mantengan dentro del dominio de las aplicaciones administradas por Intune.

### <a name="enforce-a-pin-policy"></a>Aplicar una directiva de PIN
Los administradores de TI pueden solicitar al usuario final que escriba un PIN antes de tener acceso a los datos corporativos de la aplicación. Esto garantiza que el usuario que usa la aplicación sea el mismo que en un principio inició sesión con su cuenta profesional o educativa. Cuando los usuarios finales configuran su PIN, el SDK de aplicaciones de Intune usa Azure Active Directory para comprobar las credenciales de los usuarios finales con la cuenta de Intune inscrita.

### <a name="require-users-to-sign-in-with-work-or-school-account-for-app-access"></a>Requerir que los usuarios inicien sesión con su cuenta profesional o educativa para el acceso a la aplicación
Los administradores de TI pueden solicitar a los usuarios que inicien sesión con su cuenta profesional o educativa para tener acceso a la aplicación. El SDK de la aplicación de Intune usa Azure Active Directory para proporcionar una experiencia de inicio de sesión única, en la que las credenciales, una vez introducidas, se vuelven a usar para los inicios de sesión posteriores. Además, se admite la autenticación de las soluciones de administración de identidades federadas con Azure Active Directory.

### <a name="check-device-health-and-compliance"></a>Comprobar el cumplimiento y el estado del dispositivo
Los administradores de TI pueden comprobar el estado del dispositivo y su cumplimiento de las directivas de Intune antes de que los usuarios finales accedan a la aplicación. En iOS, esta directiva comprueba si se ha descodificado el dispositivo. En Android, esta directiva comprueba si se ha descifrado el dispositivo.

### <a name="multi-identity-support"></a>Compatibilidad con varias identidades
Compatibilidad con varias identidades es una característica del SDK que permite la coexistencia de cuentas administradas por directiva (corporativas) y cuentas (personales) no administradas en una sola aplicación.

Por ejemplo, muchos usuarios configuran las cuentas de correo electrónico profesionales y personales en las aplicaciones móviles de Office para iOS y Android. Cuando un usuario accede a los datos con su cuenta corporativa, el administrador de TI debe estar seguro de que se aplicará la directiva de protección de aplicaciones. Sin embargo, cuando un usuario accede a una cuenta de correo electrónico personal, esos datos deben estar fuera del control del administrador de TI. El SDK de aplicaciones de Intune consigue esto dirigiendo la directiva de protección de aplicaciones **solo** a la identidad corporativa de la aplicación.

Esta característica de varias identidades ayuda a solucionar el problema de la protección de datos al que se enfrentan las organizaciones con aplicaciones de almacenamiento que admiten cuentas personales y profesionales.
 
### <a name="app-protection-without-device-enrollment"></a>Protección de aplicaciones sin la inscripción de dispositivos

>[!IMPORTANT]
>La protección de aplicaciones de Intune sin la inscripción de dispositivos todavía no está disponible con el SDK de aplicaciones de Intune para Android. Está disponible con las herramientas de ajuste de aplicaciones de Intune, el SDK para iOS, el componente del SDK de Xamarin y el complemento de SDK Cordova.


Muchos usuarios con dispositivos personales quieren tener acceso a los datos corporativos sin inscribir sus dispositivos personales con un proveedor de administración de dispositivos móviles (MDM). Debido a que la inscripción en MDM requiere el control global del dispositivo, los usuarios dudan a menudo a la hora de conceder ese control de sus dispositivos personales a su empresa.

La protección de aplicaciones sin la inscripción de dispositivos permite al servicio de Microsoft Intune implementar la directiva de protección de aplicaciones en una aplicación directamente, sin tener que depender de que un canal de administración de dispositivos que implemente la directiva.
