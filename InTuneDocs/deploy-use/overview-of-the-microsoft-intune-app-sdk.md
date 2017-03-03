---
title: "Información general sobre el SDK para aplicaciones de Microsoft Intune | Microsoft Docs"
description: "El SDK para aplicaciones de Intune está disponible para las plataformas iOS y Android y, gracias a él, podrá habilitar las características de administración de aplicaciones móviles con Microsoft Intune."
keywords: 
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f46f13e9dbf03fa2b3e2ec7339cad927ea0b38e0
ms.openlocfilehash: 99f3aa3c8640dd41133584b3e1cb056dfd493efa


---

# <a name="overview-of-the-microsoft-intune-app-sdk"></a>Información general sobre el SDK para aplicaciones de Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

El SDK para aplicaciones de Intune está disponible para las plataformas iOS y Android y, gracias a él, podrá habilitar las características de administración de aplicaciones móviles con Microsoft Intune. Además, se esfuerza por reducir la cantidad de cambios de código que el desarrollador tiene que realizar.

Encontrará que puede habilitar la mayoría de las características del SDK sin necesidad de cambiar el comportamiento de la aplicación. Para obtener una experiencia de administrador de TI y de usuario final mejorada, puede usar nuestras API para personalizar el comportamiento de la aplicación para aquellas características que requieren la participación de la aplicación.

Una vez que haya habilitado la aplicación, los administradores de TI podrán implementar directivas en aplicaciones administradas por Intune y aprovechar estas características para proteger los datos de su empresa.

## <a name="features"></a>Funciones
### <a name="control-users-ability-to-move-corporate-documents"></a>Controlar la capacidad de los usuarios para mover documentos de empresa
Los administradores de TI pueden controlar la reubicación de los archivos de documentos de empresa en las aplicaciones administradas por Intune. Por ejemplo, pueden implementar una directiva que impida a las aplicaciones de copia de seguridad de archivos realizar copias de seguridad de datos corporativos en la nube.  

### <a name="configure-clipboard-restrictions"></a>Configurar las restricciones del portapapeles
Los administradores de TI pueden configurar el comportamiento del portapapeles en aplicaciones administradas por Intune. Por ejemplo, pueden implementar una directiva para que los usuarios finales no puedan usar el portapapeles para cortar o copiar contenidos desde una aplicación administrada por Intune y pegarlos en una aplicación no administrada.

### <a name="enforce-encryption-on-saved-data"></a>Aplicar el cifrado en los datos guardados
Los administradores de TI pueden aplicar una directiva que garantice el cifrado de los datos guardados en el dispositivo por parte de la aplicación.

### <a name="remotely-wipe-corporate-data"></a>Borrado remoto de datos corporativos
Los administradores de TI pueden borrar remotamente los datos de empresa de una aplicación administrada por Intune cuando se anula la inscripción del dispositivo en Microsoft Intune. Esta función está basada en identidades y eliminará tan solo los archivos relacionados con la identidad corporativa del usuario final. Para ello, la característica requiere la participación de la aplicación. La aplicación puede especificar la identidad para la que debe producirse el borrado en función de la configuración de usuario. Si esta configuración especificada por el usuario no se encuentra en la aplicación, el comportamiento predeterminado será borrar el directorio de la aplicación y notificar al usuario final de que se ha quitado el acceso a los recursos de la empresa.

### <a name="enforce-the-use-of-a-managed-browser"></a>Exigir el uso de un explorador administrado
Los administradores de TI pueden exigir el uso de un explorador administrado cuando los usuarios abren vínculos desde aplicaciones administradas por Intune. Cuando los usuarios finales usan el navegador administrado de Microsoft Intune, ayuda a garantizar que de los vínculos que aparecen en los mensajes de correo electrónico en un cliente de correo electrónico administrado por Intune se guardan dentro del dominio de las aplicaciones administradas por Intune.

### <a name="enforce-a-pin-policy"></a>Aplicar una directiva de PIN
Los administradores de TI pueden aplicar una directiva de PIN cuando se inicia una aplicación administrada por Intune. Esta directiva ayuda a garantizar que los usuarios finales que inscribieron sus dispositivos con Microsoft Intune sean las mismas personas que están iniciando las aplicaciones. Cuando los usuarios finales configuran su PIN, el SDK para aplicaciones de Intune usa Azure Active Directory para comprobar las credenciales con las credenciales de inscripción de dispositivos.

### <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>Solicitar a los usuarios que introduzcan las credenciales para poder iniciar aplicaciones
Los administradores de TI pueden solicitar a los usuarios finales que especifiquen sus credenciales para poder iniciar una aplicación administrada por Intune. El SDK de la aplicación de Intune usa Azure Active Directory para proporcionar una experiencia de inicio de sesión único. Esto significa que las credenciales, una vez escritas, se reutilizan para inicios de sesión posteriores. El SDK también admite la autenticación de las soluciones de administración de identidades [federadas con Azure Active Directory](/active-directory/active-directory-aadconnect-federation-compatibility).

### <a name="check-device-health-and-compliance"></a>Comprobar el cumplimiento y el estado del dispositivo
Los administradores de TI pueden comprobar el estado del dispositivo y su cumplimiento de las directivas de empresa antes de que los usuarios finales accedan a las aplicaciones administradas por Intune. En la plataforma iOS, esta directiva comprueba si se ha liberado el dispositivo. En la plataforma Android, esta directiva comprueba si se ha modificado el dispositivo.  



<!--HONumber=Dec16_HO3-->


