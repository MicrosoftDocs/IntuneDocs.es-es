---
title: Ventajas del SDK para aplicaciones de Intune | Microsoft Docs
description: 
keywords: 
author: mtillman
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 613e293d9bd853d6de7cdc0d753cc8473afc180b
ms.openlocfilehash: e8f96499f006af590b6e7da295503696110dad4e


---

# <a name="intune-app-sdk-overview"></a>Información general del SDK para aplicaciones de Intune
El SDK para aplicaciones de Intune está disponible para las plataformas iOS y Android y, gracias a él, podrá habilitar las características de administración de aplicaciones móviles con Microsoft Intune. Su objetivo es minimizar la cantidad de cambios de código que debe realizar el desarrollador de la aplicación. Encontrará que puede habilitar la mayoría de las características del SDK sin necesidad de cambiar el comportamiento de la aplicación. Para obtener una experiencia de administrador de TI y de usuario final mejorada, puede usar nuestras API para personalizar el comportamiento de la aplicación para aquellas características que requieren la participación de la aplicación. 

Una vez que haya habilitado la aplicación, los administradores de TI podrán implementar directivas en aplicaciones administradas por Intune y aprovechar estas características para proteger los datos de su empresa.

## <a name="regular-features"></a>Funciones habituales

### <a name="control-users-ability-to-move-corporate-documents"></a>Controlar la capacidad de los usuarios para mover documentos de empresa
Los administradores de TI pueden controlar la reubicación de los archivos de documentos de empresa en las aplicaciones administradas por Intune. Por ejemplo, pueden implementar una directiva que impida a las aplicaciones de copia de seguridad de archivos realizar copias de seguridad de datos corporativos en la nube.

### <a name="configure-clipboard-restrictions"></a>Configurar las restricciones del portapapeles
Los administradores de TI pueden configurar el comportamiento del portapapeles en aplicaciones administradas por Intune. Por ejemplo, pueden implementar una directiva para que los usuarios finales no puedan usar el portapapeles para cortar o copiar contenidos desde una aplicación administrada por Intune y pegarlos en una aplicación personal no administrada.

### <a name="enforce-encryption-on-saved-data"></a>Aplicar el cifrado en los datos guardados
Los administradores de TI pueden aplicar una directiva que garantice el cifrado de los datos guardados en el dispositivo por parte de la aplicación.

### <a name="remotely-wipe-corporate-data"></a>Borrado remoto de datos corporativos
Los administradores de TI pueden borrar remotamente datos corporativos desde una aplicación administrada por Intune. Esta característica está basada en identidades y eliminará tan solo los archivos asociados con la identidad corporativa del usuario final. Para ello, la característica requiere la participación de la aplicación. La aplicación puede especificar la identidad para la que debe producirse el borrado en función de la configuración de usuario. Si esta configuración especificada por el usuario no se encuentra en la aplicación, el comportamiento predeterminado será borrar el directorio de la aplicación y notificar al usuario final que se ha quitado el acceso.

### <a name="enforce-the-use-of-a-managed-browser"></a>Exigir el uso de un explorador administrado
Los administradores de TI pueden exigir el uso de la aplicación Intune Managed Browser cuando se abren vínculos desde aplicaciones administradas por Intune. Esto garantiza que los vínculos que aparecen en un entorno corporativo se mantengan dentro del dominio de las aplicaciones administradas por Intune.

### <a name="enforce-a-pin-policy"></a>Aplicar una directiva de PIN
Los administradores de TI pueden aplicar una directiva de PIN cuando se inicia una aplicación administrada por Intune. Esto garantiza que el usuario que inicia la aplicación sea el mismo que en un principio inició sesión con una cuenta profesional o educativa inscrita. Cuando los usuarios finales configuran su PIN, el SDK de aplicaciones de Intune usa Azure Active Directory para comprobar las credenciales de los usuarios finales con la cuenta de Intune inscrita.

### <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>Solicitar a los usuarios que introduzcan las credenciales para poder iniciar aplicaciones
Los administradores de TI pueden solicitar a los usuarios que especifiquen sus credenciales para poder iniciar una aplicación administrada por Intune. El SDK de la aplicación de Intune usa Azure Active Directory para proporcionar una experiencia de inicio de sesión única, en la que las credenciales, una vez introducidas, se reutilizan para los inicios de sesión posteriores. Asimismo, se admite la autenticación de las soluciones de administración de identidades [federadas con Azure Active Directory](https://msdn.microsoft.com/library/azure/jj679342.aspx).

### <a name="check-device-health-and-compliance"></a>Comprobar el cumplimiento y el estado del dispositivo
Los administradores de TI pueden comprobar el estado del dispositivo y su cumplimiento de las directivas de empresa antes de que los usuarios finales accedan a las aplicaciones administradas por Intune. En la plataforma iOS, esta directiva comprueba si se ha liberado el dispositivo. En la plataforma Android, esta directiva comprueba si se ha modificado el dispositivo.

### <a name="sdk-multi-identity-support"></a>Compatibilidad con varias identidades del SDK
Compatibilidad con varias identidades es una funcionalidad que permite la coexistencia de cuentas administradas por directiva (corporativas) y cuentas (personales) no administradas en una sola aplicación.

Por ejemplo, muchos usuarios configuran las cuentas de correo electrónico profesionales y personales en la aplicación de Outlook para iOS y Android. Cuando un usuario accede a datos en su cuenta corporativa, el administrador de TI debe estar seguro de que se aplicará la administración de directivas MAM. Sin embargo, cuando un usuario accede a una cuenta de correo electrónico personal, esos datos deben estar fuera del control del administrador de TI. Microsoft Intune consigue esto mediante la orientación de la directiva de administración a la cuenta corporativa solo en la aplicación. Esta funcionalidad de varias identidades ayuda a solucionar el problema de la protección de datos al que se enfrentan las organizaciones con dispositivos y aplicaciones que admiten cuentas personales y profesionales.

* **Cómo admitir varias identidades**: las API del SDK de aplicaciones de Microsoft Intune le permiten especificar un nombre principal de usuario (UPN) con operaciones de datos específicos, como las operaciones del portapapeles y las operaciones de archivos. El SDK usa el UPN para hacer coincidir la llamada realizada al UPN usado para inscribir el dispositivo con el servicio Microsoft Intune. Si los UPN coinciden, la llamada se tratará como una llamada de "datos corporativos" y se protegerán los datos; si los UPN no coinciden, la llamada se tratará como una llamada de "datos personales" y los datos no se protegerán.

### <a name="app-management-without-device-enrollment"></a>Administración de aplicaciones sin la inscripción de dispositivos

>[!IMPORTANT]
>La administración de aplicaciones móviles de Intune sin la inscripción de dispositivos solo está disponible con el SDK de aplicaciones de Intune para iOS. 


Muchos usuarios con dispositivos personales desean ver y usar datos corporativos sin inscribir sus dispositivos personales en un producto de administración de dispositivos móviles (MDM). Debido a que la inscripción en MDM requiere el control global del dispositivo, los usuarios dudan a la hora de conceder ese control global de sus propios dispositivos personales a su empresa.

La administración de aplicaciones sin la inscripción de dispositivos permite al servicio Microsoft Intune implementar la directiva MAM en una aplicación directamente, sin tener que depender de que un canal MDM implemente la directiva. Dado que no se necesita ningún canal MDM, no se necesita la inscripción de MDM.



<!--HONumber=Dec16_HO2-->


