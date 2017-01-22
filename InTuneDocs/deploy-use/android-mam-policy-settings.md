---
title: "Opciones de configuración de directiva de MAM de Android | Microsoft Docs"
description: "En este tema se describe la configuración de directiva de administración de aplicaciones móviles para dispositivos Android."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 28a1bf4c7c2200901761a53394064d920b56dad6
ms.openlocfilehash: 058527911594614865ae44ba9de7ab0887fa60b2


---

# <a name="android-mobile-app-management-policy-settings-in-microsoft-intune"></a>Opciones de configuración de directiva de administración de aplicaciones móviles de Android en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

La configuración de directiva que se describe en este tema puede [configurarse](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) para una directiva de administración de aplicaciones móviles (MAM) en la hoja **Configuración** de Azure Portal.
Existen dos categorías de configuración de directiva: configuración de acceso y configuración de reubicación de datos. En este tema, el término _**aplicaciones administradas por directivas**_ hace referencia a las aplicaciones que están configuradas con directivas de MAM.


##  <a name="data-relocation-settings"></a>Configuración de reubicación de datos

| Configuración | Cómo se usa | Valores predeterminados |
|------|------|------|
| **Impedir copias de seguridad de Android** | Pulse **Sí** para impedir que esta aplicación realice copias de seguridad de datos profesionales o educativos en el [Servicio de copia de seguridad de Android](https://developer.android.com/google/backup/index.html). Pulse **No** para permitir que esta aplicación realice copias de seguridad de datos profesionales o educativos.| Sí |
| **Permitir que la aplicación transfiera datos a otras aplicaciones** | Especifique qué aplicaciones pueden recibir datos de esta aplicación: <ul><li> **Aplicaciones administradas por directivas**: permite las transferencias solo para otras aplicaciones administradas por directivas.</li> <li>**Todas las aplicaciones**: permite la transferencia a cualquier aplicación. </li> <li>**Ninguna**: no permite la transferencia de datos a ninguna aplicación, incluidas otras aplicaciones administradas por directivas.</li></ul> | Todas las aplicaciones |
| **Permitir que la aplicación reciba datos de otras aplicaciones** | Especifique qué aplicaciones pueden transferir datos a esta aplicación: <ul><li>**Aplicaciones administradas por directivas**: permite las transferencias solo desde otras aplicaciones administradas por directivas.</li><li>**Todas las aplicaciones**: permite la transferencia de datos desde cualquier aplicación.</li><li>**Ninguna**: no permite la transferencia de datos desde ninguna aplicación, incluidas otras aplicaciones administradas por directivas. | Todas las aplicaciones |
| **Impedir "Guardar como"** | Pulse **Sí** para deshabilitar el uso de la opción Guardar como en esta aplicación. Elija **No** si quiere permitir el uso de Guardar como. | No |
| **Restringir cortar, copiar y pegar con otras aplicaciones** | Especifique cuándo pueden usarse las acciones de cortar, copiar y pegar con esta aplicación. Elija de entre las siguientes opciones: <ul><li>**Bloqueado**: no permite las acciones de cortar, copiar y pegar entre esta aplicación y cualquier otra.</li><li>**Aplicaciones administradas por directivas**: permite las acciones de cortar, copiar y pegar entre esta aplicación y otras aplicaciones administradas por directivas.</li><li>**Aplicaciones administradas por directivas con pegar**: permite cortar o copiar entre esta aplicación y otras aplicaciones administradas por directivas. Permite que los datos de cualquier aplicación se peguen en esta aplicación.</li><li>**Cualquier aplicación**: no se aplican restricciones a las acciones de cortar, copiar y pegar para y desde esta aplicación. | Cualquier aplicación |
|**Restringir contenido web para mostrar en Managed Browser** | Pulse **Sí** para aplicar los vínculos web en la aplicación que se va a abrir en la aplicación Managed Browser. <br><br> En el caso de los dispositivos que no estén inscritos en Intune, los vínculos web en aplicaciones administradas por directivas solo se pueden abrir en la aplicación Managed Browser. <br><br> Si usa Intune para administrar los dispositivos, vea [Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md). | No |
| **Cifrar datos de aplicación** | Pulse **Sí** para habilitar el cifrado de datos profesionales o educativos en esta aplicación. Intune usa un esquema de cifrado de OpenSSL junto con el sistema del almacén de claves Android para cifrar los datos de la aplicación de manera segura. Los datos se cifran de forma sincrónica durante las tareas de E/S de archivo. El contenido del almacenamiento del dispositivo estará siempre cifrado. <br><br> El método de cifrado **no** está certificado mediante FIPS 140-2.  | Sí |
| **Deshabilitar la sincronización de contactos** | Pulse **Sí** para impedir que la aplicación guarde datos en la aplicación nativa Contactos del dispositivo. Si pulsa **No**, la aplicación puede guardar datos en la aplicación Contactos nativa del dispositivo. <br><br>Cuando realiza un borrado selectivo para quitar los datos profesionales o educativos de la aplicación, se quitan los contactos sincronizados directamente desde la aplicación a la aplicación nativa Contactos. No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. Actualmente esto se aplica únicamente para la aplicación Microsoft Outlook. | No |
| **Deshabilitar la impresión** | Pulse **Sí** para impedir que la aplicación imprima datos profesionales o educativos. | No |


  >[!NOTE]
  >El método de cifrado de la opción de configuración **Cifrar datos de aplicación** **no** está certificado mediante FIPS 140-2.




##  <a name="access-settings"></a>Configuración de acceso

| Configuración | Cómo se usa | Valores predeterminados |
|------|------|------|
| **Requerir PIN para acceder** | Pulse **Sí** para requerir un PIN para usar esta aplicación. Se pedirá al usuario que configure este PIN la primera vez que ejecute la aplicación en un contexto profesional o educativo. Valor predeterminado = **Sí**.<br><br> Configure las siguientes opciones para la intensidad del PIN: <ul><li>**Número de intentos antes del restablecimiento del PIN**: especifique el número de veces que el usuario tiene que escribir correctamente el PIN antes de que deba restablecerlo. Valor predeterminado = **5**.</li><li> **Permitir el PIN simple**: pulse **Sí** para permitir que los usuarios usen secuencias de PIN simples como 1234 o 1111. Pulse **No** para impedir que usen secuencias simples. Valor predeterminado = **Sí**. </li><li> **Longitud del PIN**: especifique el número mínimo de dígitos en una secuencia de PIN. Valor predeterminado = **4**. </li><li> **Permitir desbloqueo mediante huellas digitales en lugar de mediante PIN (Android 6.0+)**: pulse **Sí** para permitir que el usuario use la [autenticación con huella digital](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) en lugar de un PIN para el acceso a la aplicación. Valor predeterminado = **Sí**.<br><br> En dispositivos Android, puede permitir que el usuario demuestre su identidad con la [autenticación con huella digital de Android](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) en lugar de usar un PIN. Cuando el usuario intenta usar esta aplicación con su cuenta profesional o educativa, se le solicita que indique su identidad mediante huella digital en lugar de escribir un PIN. </li></ul>| Requerir PIN: Sí <br><br> Intentos de restablecimiento del PIN: 5 <br><br> Permitir PIN simple: Sí <br><br> Longitud del PIN: 4 <br><br> Permitir huella digital: Sí |
| **Requerir credenciales corporativas en acceso** | Pulse **Sí** para requerir que el usuario inicie sesión con su cuenta profesional o educativa en lugar de escribir un PIN para el acceso a la aplicación. Si se establece en **Sí**, se reemplazarán los requisitos de introducción de un PIN o un Touch ID.  | No |
| **Bloquear la ejecución de aplicaciones administradas en dispositivos descodificados o descifrados** |  Pulse **Sí** para impedir que esta aplicación se ejecute en dispositivos descodificados o descifrados. El usuario seguirá siendo capaz de usar esta aplicación para las tareas personales, pero tendrá que usar un dispositivo distinto para tener acceso a los datos profesionales o educativos de esta aplicación. | Sí |
| **Volver a comprobar los requisitos de acceso después de (minutos)** | Configure las siguientes opciones: <ul><li>**Tiempo de espera**: especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación. Valor predeterminado = **30** minutos.</li><li>**Período de gracia sin conexión**: si el dispositivo está desconectado, especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación. Valor predeterminado = **720** minutos (12 horas).</li></ul>| Tiempo de espera: 30 <br><br> Sin conexión: 720 |
| **Intervalo sin conexión antes de que se borren los datos de la aplicación (días)** | Los datos profesionales o educativos de esta aplicación pueden borrarse si un dispositivo ha estado sin conexión durante más de un período determinado. Especifique el número de días que un dispositivo puede estar sin conexión antes de que se eliminen los datos profesionales o educativos del dispositivo. <br><br> | 90 días |
| **Bloquear captura de pantalla y Asistente para Android (Android 6.0+)** | Pulse **Sí** para bloquear las características de captura de pantalla y **Asistente para Android** del dispositivo cuando se usa esta aplicación. Al pulsar **Sí** también se desenfocará la imagen de vista previa de las últimas aplicaciones si se usa esta aplicación con una cuenta profesional o educativa. | No |



<!--HONumber=Dec16_HO3-->


