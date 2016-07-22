---
title: Ventajas del SDK para aplicaciones de Intune | Microsoft Intune
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: 3abf566831348de11f718370d6267e3ff4355bfb


---

# Información general del SDK para aplicaciones de Intune
El SDK para aplicaciones de Intune está disponible para las plataformas iOS y Android y, gracias a él, podrá habilitar las características de administración de aplicaciones móviles con Microsoft Intune. Además, nos esforzamos por reducir la cantidad de cambios de código necesarios para el desarrollador. Encontrará que puede habilitar la mayoría de las características del SDK sin necesidad de cambiar el comportamiento de la aplicación. Para obtener una experiencia de administrador de TI y de usuario final mejorada, puede usar nuestras API para personalizar el comportamiento de la aplicación para aquellas características que requieren la participación de la aplicación. Una vez que haya habilitado la aplicación, los administradores de TI podrán implementar directivas en aplicaciones administradas por Intune y aprovechar estas características para proteger los datos de su empresa.

## Funciones habituales

### Controlar la capacidad de los usuarios para mover documentos de empresa
Los administradores de TI pueden controlar la reubicación de los archivos de documentos de empresa en las aplicaciones administradas por Intune. Por ejemplo, pueden implementar una directiva que impida a las aplicaciones de copia de seguridad de archivos realizar copias de seguridad de datos corporativos en la nube.

### Configurar las restricciones del portapapeles
Los administradores de TI pueden configurar el comportamiento del portapapeles en aplicaciones administradas por Intune. Por ejemplo, pueden implementar una directiva para que los usuarios finales no puedan usar el portapapeles para cortar o copiar contenidos desde una aplicación administrada por Intune y pegarlos en una aplicación no administrada.

### Configurar restricciones de captura de pantalla
Los administradores de TI pueden impedir que los usuarios hagan capturas de pantalla si se muestra una aplicación administrada por Intune. La aplicación de esta restricción impide la captura y publicación de contenido empresarial confidencial. Esta característica solo está disponible para dispositivos Android.

### Aplicar el cifrado en los datos guardados
Los administradores de TI pueden aplicar una directiva que garantice el cifrado de los datos guardados en el dispositivo por parte de la aplicación.

### Borrado remoto de datos corporativos
Los administradores de TI pueden borrar remotamente los datos de empresa de una aplicación administrada por Intune cuando se anula la inscripción del dispositivo en Microsoft Intune. Esta característica está basada en identidades y eliminará tan solo los archivos relacionados con la identidad corporativa del usuario final. Para ello, la característica requiere la participación de la aplicación. La aplicación puede especificar la identidad para la que debe producirse el borrado en función de la configuración de usuario. Si esta configuración especificada por el usuario no se encuentra en la aplicación, el comportamiento predeterminado será borrar el directorio de la aplicación y notificar al usuario final de que se ha quitado el acceso a los recursos de la empresa.

### Exigir el uso de un explorador administrado
Los administradores de TI pueden exigir el uso de un explorador administrado cuando se abren vínculos desde aplicaciones administradas por Intune. El uso del explorador administrado por Microsoft Intune ayuda a garantizar la conservación de los vínculos que aparecen en los mensajes de correo electrónico (los cuales se encuentran en un cliente de correo electrónico administrado por Intune) dentro del dominio de las aplicaciones administradas por Intune.

### Aplicar una directiva de PIN
Los administradores de TI pueden aplicar una directiva de PIN cuando se inicia una aplicación administrada por Intune. Esta directiva ayuda a garantizar que los usuarios finales que inscribieron sus dispositivos con Microsoft Intune sean las mismas personas que están iniciando las aplicaciones. Cuando los usuarios finales configuran su PIN, el SDK para aplicaciones de Intune usa Azure Active Directory para comprobar las credenciales de los usuarios finales con las credenciales de inscripción de dispositivos.

### Solicitar a los usuarios que introduzcan las credenciales para poder iniciar aplicaciones
Los administradores de TI pueden solicitar a los usuarios que especifiquen sus credenciales para poder iniciar una aplicación administrada por Intune. El SDK de la aplicación de Intune usa Azure Active Directory para proporcionar una experiencia de inicio de sesión única, en la que las credenciales, una vez introducidas, se reutilizan para los inicios de sesión posteriores. Asimismo, se admite la autenticación de las soluciones de administración de identidades [federadas con Azure Active Directory](https://msdn.microsoft.com/library/azure/jj679342.aspx).

### Comprobar el cumplimiento y el estado del dispositivo
Los administradores de TI pueden comprobar el estado del dispositivo y su cumplimiento de las directivas de empresa antes de que los usuarios finales accedan a las aplicaciones administradas por Intune. En la plataforma iOS, esta directiva comprueba si se ha liberado el dispositivo. En la plataforma Android, esta directiva comprueba si se ha modificado el dispositivo.

## Funcionalidades de vista previa
El SDK para aplicaciones de Microsoft Intune incluye varias características que se encuentran en "vista previa". Puede empezar a efectuar la integración con API de vista previa, pero solo con fines de prueba. Tenga en cuenta que estas vistas previas se agregan a escenarios existentes en lugar de reemplazar escenarios existentes.

### Compatibilidad con varias identidades del SDK para aplicaciones de Microsoft Intune
Compatibilidad con varias identidades es una funcionalidad que permite la coexistencia de cuentas administradas por directiva (corporativas) y cuentas (personales) no administradas en una sola aplicación.

### Ejemplo de un escenario de varias identidades
Muchos usuarios configuran las cuentas de correo electrónico profesionales y personales en la aplicación de Outlook para iOS y Android. Cuando un usuario accede a datos en su cuenta corporativa, el administrador de TI debe estar seguro de que se aplicará la administración de directivas MAM. Sin embargo, cuando un usuario accede a una cuenta de correo electrónico personal, esos datos deben estar fuera del control del administrador de TI. Microsoft Intune consigue esto mediante la orientación de la directiva de administración a la cuenta corporativa solo en la aplicación. Esta funcionalidad de varias identidades ayuda a solucionar el problema de la protección de datos al que se enfrentan las organizaciones con dispositivos y aplicaciones que admiten cuentas personales y profesionales.

### Cómo admitir varias identidades
Las API de vista previa le permiten especificar un Nombre principal de usuario (UPN) con operaciones de datos específicos, como las operaciones del portapapeles y las operaciones de archivos. El SDK para aplicaciones de Microsoft Intune usa el UPN para hacer coincidir la llamada realizada al UPN usado para inscribir el dispositivo con el servicio Microsoft Intune. Si los UPN coinciden, la llamada se tratará como una llamada de "datos corporativos" y se protegerán los datos; si los UPN no coinciden, la llamada se tratará como una llamada de "datos personales" y los datos no se protegerán.

### Administración de aplicaciones sin la inscripción de dispositivos
Muchos usuarios con dispositivos personales desean ver y usar datos corporativos sin inscribir sus dispositivos personales en un producto de administración de dispositivos móviles (MDM). Debido a que la inscripción en MDM requiere el control global del dispositivo, los usuarios dudan a la hora de conceder ese control global de sus propios dispositivos personales a su empresa.

La administración de aplicaciones sin la inscripción de dispositivos permite al servicio Microsoft Intune implementar la directiva MAM en una aplicación directamente, sin tener que depender de que un canal MDM implemente la directiva. Dado que no se necesita ningún canal MDM, no se necesita la inscripción de MDM.




<!--HONumber=Jul16_HO3-->


