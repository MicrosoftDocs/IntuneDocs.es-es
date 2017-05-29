---
title: "Configuración de directivas de protección de aplicaciones de iOS"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: en este tema se describe la configuración de directivas de protección de aplicaciones para dispositivos iOS."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ecb2b2561d287543fef36ecab471639d7fb1d9a5
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

#  <a name="ios-app-protection-policy-settings"></a>Configuración de directivas de protección de aplicaciones de iOS
[!INCLUDE[azure_preview](./includes/azure_preview.md)]

La configuración de directivas que se describe en este tema puede [realizarse](app-protection-policies.md) para una directiva de protección de aplicaciones en la hoja **Configuración** del portal de Azure.

Existen dos categorías de configuración de directiva: configuración de acceso y configuración de reubicación de datos. En este tema, el término ***aplicaciones administradas por directivas*** hace referencia a las aplicaciones que están configuradas con directivas de protección de aplicaciones.

##  <a name="data-relocation-settings"></a>Configuración de reubicación de datos

| Configuración | Cómo se usa | Valores predeterminados |
|------|------|------|
| **Impedir copias de seguridad de iTunes e iCloud** | Pulse **Sí** para evitar que esta aplicación realice una copia de seguridad de los datos profesionales o educativos en iTunes e iCloud. Pulse **No** para permitir que esta aplicación realice una copia de seguridad de los datos profesionales o educativos en iTunes e iCloud.| Sí |
| **Permitir que la aplicación transfiera datos a otras aplicaciones** | Especifique qué aplicaciones pueden recibir datos de esta aplicación: <ul><li> **Aplicaciones administradas por directivas**: permite las transferencias solo para otras aplicaciones administradas por directivas.</li> <li>**Todas las aplicaciones**: permite la transferencia a cualquier aplicación. </li> <li>**Ninguna**: no permite la transferencia de datos a ninguna aplicación, incluidas otras aplicaciones administradas por directivas.</li></ul> Además, si establece esta opción en **Aplicaciones administradas por directivas** o **Ninguno**, la característica de iOS 9 que permite que la búsqueda de Spotlight busque datos dentro de las aplicaciones se bloqueará. <br><br> Hay aplicaciones y servicios exentos a los que Intune puede permitir la transferencia de datos. Consulte [Exenciones de transferencia de datos](#data-transfer-exemptions) para ver una lista completa de aplicaciones y servicios. | Todas las aplicaciones |
| **Permitir que la aplicación reciba datos de otras aplicaciones** | Especifique qué aplicaciones pueden transferir datos a esta aplicación: <ul><li>**Aplicaciones administradas por directivas**: permite las transferencias solo desde otras aplicaciones administradas por directivas.</li><li>**Todas las aplicaciones**: permite la transferencia de datos desde cualquier aplicación.</li><li>**Ninguna**: no permite la transferencia de datos desde ninguna aplicación, incluidas otras aplicaciones administradas por directivas. </li></ul> <p>  Hay aplicaciones y servicios exentos desde los que Intune puede permitir la transferencia de datos. Consulte [Exenciones de transferencia de datos](#data-transfer-exemptions) para ver una lista completa de aplicaciones y servicios. | Todas las aplicaciones |
| **Impedir "Guardar como"** | Pulse **Sí** para deshabilitar el uso de la opción Guardar como en esta aplicación. Elija **No** si quiere permitir el uso de Guardar como. | No |
| **Restringir cortar, copiar y pegar con otras aplicaciones** | Especifique cuándo pueden usarse las acciones de cortar, copiar y pegar con esta aplicación. Elija de entre las siguientes opciones: <ul><li>**Bloqueado**: no permite las acciones de cortar, copiar y pegar entre esta aplicación y cualquier otra.</li><li>**Aplicaciones administradas por directivas**: permite las acciones de cortar, copiar y pegar entre esta aplicación y otras aplicaciones administradas por directivas.</li><li>**Aplicaciones administradas por directivas con pegar**: permite cortar o copiar entre esta aplicación y otras aplicaciones administradas por directivas. Permite que los datos de cualquier aplicación se peguen en esta aplicación.</li><li>**Cualquier aplicación**: no se aplican restricciones a las acciones de cortar, copiar y pegar para y desde esta aplicación. | Cualquier aplicación |
|**Restringir contenido web para mostrar en Managed Browser** | Pulse **Sí** para aplicar los vínculos web en la aplicación que se va a abrir en la aplicación Managed Browser. <br><br> En el caso de los dispositivos que no estén inscritos en Intune, los vínculos web en aplicaciones administradas por directivas solo se pueden abrir en la aplicación Managed Browser. <br><br> Si usa Intune para administrar los dispositivos, vea [Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies). | No |
| **Cifrar datos de aplicación** | Para las aplicaciones administradas por directivas, los datos están cifrados en reposo con el esquema de cifrado de nivel de dispositivo proporcionado por iOS. Cuando se requiere un PIN, los datos se cifran según la configuración de la directiva de protección de aplicaciones. <br><br> Vaya a la documentación oficial de Apple [aquí](https://support.apple.com/HT202739) para ver qué módulos de cifrado iOS están certificados mediante FIPS 140-2 o están pendientes de certificación mediante FIPS 140-2. <br><br> Especifique cuándo se cifran los datos profesionales o educativos en esta aplicación. Elija de entre las siguientes opciones: <ul><li>**Cuando el dispositivo esté bloqueado**: todos los datos de la aplicación que están asociados a esta directiva se cifran mientras el dispositivo está bloqueado.</li><li>**Cuando el dispositivo esté bloqueado y haya archivos abiertos**: todos los datos de la aplicación asociados a esta directiva se cifran mientras el dispositivo está bloqueado, excepto los datos de los archivos que están abiertos actualmente en la aplicación.</li><li>**Después de reiniciar el dispositivo**: todos los datos de la aplicación asociados a esta directiva se cifran al reiniciar el dispositivo, hasta que el dispositivo se desbloquea por primera vez.</li><li>**Usar la configuración del dispositivo**: los datos de la aplicación se cifran en función de la configuración predeterminada del dispositivo. </li></ul> Al habilitar esta configuración, puede que se solicite al usuario que configure y use un PIN para acceder a su dispositivo.  Si no hay ningún PIN de dispositivo y se requiere el cifrado, las aplicaciones no se abren y se le solicita al usuario que establezca un PIN con este mensaje: “Su organización ha solicitado que primero habilite un PIN de dispositivo para acceder a esta aplicación”. | Cuando el dispositivo está bloqueado |
| **Deshabilitar la sincronización de contactos** | Pulse **Sí** para impedir que la aplicación guarde datos en la aplicación nativa Contactos del dispositivo. Si pulsa **No**, la aplicación puede guardar datos en la aplicación Contactos nativa del dispositivo. <br><br>Cuando realiza un borrado selectivo para quitar los datos profesionales o educativos de la aplicación, se quitan los contactos sincronizados directamente desde la aplicación a la aplicación nativa Contactos. No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. Actualmente esto se aplica únicamente para la aplicación Microsoft Outlook. | No |
| **Deshabilitar la impresión** | Pulse **Sí** para impedir que la aplicación imprima datos profesionales o educativos. | No |


> [!NOTE]
> Ninguna de las opciones de configuración de reubicación de datos controla la característica de Administración abierta de Apple (Apple Managed Open In) en dispositivos iOS. Para usar Administración abierta de Apple (Apple Managed Open In), vea [Administrar la transferencia de datos entre aplicaciones iOS con Microsoft Intune](data-transfer-between-apps-manage-ios.md).

## <a name="data-transfer-exemptions"></a>Exenciones de transferencia de datos

La directiva de protección de aplicaciones de Intune puede permitir la transferencia de datos desde y hacia algunas aplicaciones y servicios de plataforma en determinados escenarios. Esta lista está sujeta a cambios y refleja los servicios y las aplicaciones que se consideran útiles para una productividad segura.

| Nombres de aplicación/servicio | Descripción |
| ---- | --- |
|tel; telprompt | Aplicación de teléfono nativa |
| skype | Skype |
| app-settings | Configuración del dispositivo |
| itms; itmss; itms-apps; itms-appss; itms-services | Tienda de aplicaciones |
| calshow | Calendario nativo |


## <a name="access-settings"></a>Configuración de acceso

| Configuración | Cómo se usa | Valores predeterminados |
|------|------|------|
| **Requerir PIN para acceder** | Pulse **Sí** para requerir un PIN para usar esta aplicación. Se pedirá al usuario que configure este PIN la primera vez que ejecute la aplicación en un contexto profesional o educativo. Valor predeterminado = **Sí**.<br><br> Configure las siguientes opciones para la intensidad del PIN: <ul><li>**Número de intentos antes del restablecimiento del PIN**: especifique el número de veces que el usuario tiene que escribir correctamente el PIN antes de que deba restablecerlo. Valor predeterminado = **5**.</li><li> **Permitir el PIN simple**: pulse **Sí** para permitir que los usuarios usen secuencias de PIN simples como 1234 o 1111. Pulse **No** para impedir que usen secuencias simples. Valor predeterminado = **Sí**. </li><li> **Longitud del PIN**: especifique el número mínimo de dígitos en una secuencia de PIN. Valor predeterminado = **4**. </li><li> **Permitir desbloqueo mediante huellas digitales en lugar de mediante PIN (iOS 8.0+)**: pulse **Sí** para permitir que el usuario use [Touch ID](https://support.apple.com/en-us/HT201371) en lugar de un PIN para el acceso a la aplicación. Valor predeterminado = **Sí**.</li></ul> En dispositivos iOS, puede permitir que el usuario demuestre su identidad con [Touch ID](https://support.apple.com/en-us/HT201371) en lugar de con un PIN. Cuando el usuario intenta usar esta aplicación con su cuenta profesional o educativa, se le solicita que indique su identidad mediante huella digital en lugar de escribir un PIN. </li></ul>| Requerir PIN: Sí <br><br> Intentos de restablecimiento del PIN: 5 <br><br> Permitir PIN simple: Sí <br><br> Longitud del PIN: 4 <br><br> Permitir huella digital: Sí |
| **Requerir credenciales corporativas en acceso** | Pulse **Sí** para requerir que el usuario inicie sesión con su cuenta profesional o educativa en lugar de escribir un PIN para el acceso a la aplicación. Si se establece en **Sí**, se reemplazarán los requisitos de introducción de un PIN o un Touch ID.  | No |
| **Bloquear la ejecución de aplicaciones administradas en dispositivos descodificados o descifrados** |  Pulse **Sí** para impedir que esta aplicación se ejecute en dispositivos descodificados o descifrados. El usuario seguirá siendo capaz de usar esta aplicación para las tareas personales, pero tendrá que usar un dispositivo distinto para tener acceso a los datos profesionales o educativos de esta aplicación. | Sí |
| **Volver a comprobar los requisitos de acceso después de (minutos)** | Configure las siguientes opciones: <ul><li>**Tiempo de espera**: especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación. Valor predeterminado = **30** minutos.</li><li>**Período de gracia sin conexión**: si el dispositivo está desconectado, especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación. Valor predeterminado = **720** minutos (12 horas).</li></ul>| Tiempo de espera: 30 <br><br> Sin conexión: 720 |
| **Intervalo sin conexión antes de que se borren los datos de la aplicación (días)** | Los datos profesionales o educativos de esta aplicación pueden borrarse si un dispositivo ha estado sin conexión durante más de un período determinado. Especifique el número de días que un dispositivo puede estar sin conexión antes de que se eliminen los datos profesionales o educativos del dispositivo. <br><br> | 90 días |
| **Requiere el sistema operativo mínimo iOS** | Pulse **Sí** para requerir un sistema operativo mínimo iOS para usar esta aplicación. Se bloqueará el acceso al usuario si la versión de iOS en el dispositivo no cumple el requisito. <br><br> | No |
| **Requiere el sistema operativo mínimo iOS (solo advertencia)** | Seleccione **Sí** para recomendar un sistema operativo mínimo iOS para usar esta aplicación. El usuario verá una notificación si la versión de iOS en el dispositivo no cumple el requisito. Se puede descartar esta notificación. <br><br> | No |
| **Requiere la versión mínima de la aplicación** | Seleccione **Sí** para requerir la versión mínima de la aplicación para usar esta aplicación. Se bloqueará el acceso al usuario si la versión de la aplicación en el dispositivo no cumple el requisito.<br><br>Al seleccionar aplicaciones de destino, tenga en cuenta que las aplicaciones a menudo tienen esquemas de versiones distintas entre sí.<br><br> | No |
| **Requiere la versión mínima de la aplicación (solo advertencia)** | Seleccione **Sí** para recomendar la versión mínima de la aplicación para usar esta aplicación. El usuario verá una notificación si la versión de la aplicación en el dispositivo no cumple el requisito. Se puede descartar esta notificación.<br><br>Al seleccionar aplicaciones de destino, tenga en cuenta que las aplicaciones a menudo tienen esquemas de versiones distintas entre sí.<br><br> | No |
| **Requiere una versión mínima del SDK de la directiva de protección de aplicaciones de Intune** | Elija **Sí** para requerir una versión mínima del SDK de la directiva de protección de aplicaciones de Intune en la aplicación que se usará. Se bloqueará el acceso al usuario si la versión del SDK de la directiva de protección de aplicaciones de Intune de la aplicación no cumple el requisito. <br> <br> Para obtener más información sobre el SDK de la directiva de protección de aplicaciones de Intune, vea [Información general del SDK para aplicaciones de Intune](/intune-classic/develop/intune-app-sdk). <br><br> | No |

##  <a name="add-ins-for-outlook-app"></a>Complementos para la aplicación Outlook

Outlook ha incorporado recientemente complementos de Outlook para iOS que le permiten integrar aplicaciones conocidas con el cliente de correo electrónico. Los complementos para Outlook están disponibles en la plataforma web y en Windows, Mac y Outlook para iOS. Dado que los complementos se administran mediante Microsoft Exchange, los usuarios podrán compartir datos y mensajes entre Outlook y aplicaciones de complementos sin administrar a no ser que en Exchange los complementos estén desactivado para el usuario.

Si quiere que los usuarios finales dejen de acceder a complementos de Outlook e instalarlos (esto afecta a todos los clientes de Outlook), asegúrese de que existen los siguientes cambios en los roles en el centro de administración de Exchange:

- Para evitar que los usuarios instalen complementos de la Tienda Office, quíteles el rol Mi Marketplace.
- Para evitar que los usuarios carguen complementos, quíteles el rol Mis aplicaciones personalizadas.
- Para evitar que los usuarios instalen todos los complementos, quíteles los roles Mis aplicaciones personalizadas y Mi Marketplace.

Estas instrucciones se aplican a Office 365, Exchange 2016, Exchange 2013 a través de Outlook en la web, Windows, Mac y dispositivos móviles.

- Más información sobre [complementos para Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Aprenda [cómo especificar los administradores y los usuarios que pueden instalar y administrar complementos para la aplicación Outlook](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).

