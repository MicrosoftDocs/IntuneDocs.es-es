---
title: Configuración de directivas de protección de aplicaciones de Android
titleSuffix: Microsoft Intune
description: En este tema, se describe la configuración de directivas de protección de aplicaciones para dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9e9ef9f5-1215-4df1-b690-6b21a5a631f8
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf2a8e55963dd3da98e20f5700a464d00c3c62a9
ms.sourcegitcommit: 4bf23327af734a9811d555fbd566c31239e2acd6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "72999463"
---
# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Configuración de directivas de protección de aplicaciones Android en Microsoft Intune
En este artículo se describe la configuración de directivas de protección de aplicaciones para dispositivos Android. La configuración de directivas que se describe puede [realizarse](app-protection-policies.md) para una directiva de protección de aplicaciones en la hoja **Configuración** de Azure Portal.
Hay tres categorías de configuración de directiva: configuración de protección de datos, requisitos de acceso e inicio condicional. En este artículo, el término *aplicaciones administradas por directivas* hace referencia a las aplicaciones que están configuradas con directivas de protección de aplicaciones.

> [!IMPORTANT]
> Es necesario que el Portal de empresa de Intune esté instalado en el dispositivo para recibir las directivas de protección de aplicación para dispositivos Android. Para más información, consulte los [requisitos de las aplicaciones de acceso al Portal de empresa de Intune](../fundamentals/end-user-mam-apps-android.md).

## <a name="data-protection"></a>Protección de datos 
### <a name="data-transfer"></a>Transferencia de datos
| Setting | Cómo se usa | Valor predeterminado |
|------|------|------|
| **Hacer copia de seguridad de los datos de la organización en los servicios correspondientes de Android** | Seleccione **Bloquear** para impedir que esta aplicación haga una copia de seguridad de los datos profesionales o educativos en [Android Backup Service](https://developer.android.com/google/backup/index.html) (Servicio de copia de seguridad de Android).<br><br> Seleccione **Permitir** para permitir que esta aplicación haga una copia de seguridad de los datos profesionales o educativos.| **Permitir** |
| **Enviar datos de la organización a otras aplicaciones** | Especifique qué aplicaciones pueden recibir datos de esta aplicación: <ul><li> **Aplicaciones administradas por directivas**: permite las transferencias solo para otras aplicaciones administradas por directivas.</li> <li>**Todas las aplicaciones**: permite la transferencia a cualquier aplicación. </li> <li>**Ninguna**: no permite la transferencia de datos a ninguna aplicación, incluidas otras aplicaciones administradas por directivas.</li></ul> <p>Hay aplicaciones y servicios exentos a los que Intune puede permitir la transferencia de datos de forma predeterminada. Además, puede crear sus propias excepciones si necesita permitir que los datos se transfieran a una aplicación que no admita las directivas de protección de aplicaciones de Intune. Para obtener más información, vea [Exenciones de transferencia de datos](app-protection-policy-settings-android.md#data-transfer-exemptions).<p>Esta directiva también se puede aplicar a los vínculos de las aplicaciones Android.  Los vínculos web generales se administran mediante la configuración de directiva **Abrir vínculos a aplicaciones en Intune Managed Browser**.<p><div class="NOTE"><p>Nota</p><p>Intune no admite actualmente la característica Android Instant Apps. Intune bloqueará todas las conexiones de datos con origen o destino a la aplicación. Para obtener más información, vea [Android Instant Apps](https://developer.android.com/topic/instant-apps/index.html) en la documentación para desarrolladores de Android.</p><p>Si **Enviar datos de la organización a otras aplicaciones** se ha configurado en **Todas las aplicaciones**, todavía se pueden transferir datos de texto a través de la funcionalidad de uso compartido del sistema operativo al Portapapeles.</p></div> | **Todas las aplicaciones** | 
|<ul><ui>**Seleccionar las aplicaciones que quedan exentas** | Esta opción está disponible si selecciona *Aplicaciones administradas por directivas* en la opción anterior. | |
| **Recibir datos de otras aplicaciones** | Especifique qué aplicaciones pueden transferir datos a esta aplicación: <ul><li>**Aplicaciones administradas por directivas**: permite las transferencias solo desde otras aplicaciones administradas por directivas.</li><li>**Todas las aplicaciones**: permite la transferencia de datos desde cualquier aplicación.</li><li>**Ninguna**: no permite la transferencia de datos desde ninguna aplicación, incluidas otras aplicaciones administradas por directivas. </li></ul> <p>Hay aplicaciones y servicios exentos desde los que Intune puede permitir la transferencia de datos. Consulte [Exenciones de transferencia de datos](app-protection-policy-settings-android.md#data-transfer-exemptions) para ver una lista completa de aplicaciones y servicios. | **Todas las aplicaciones** |
| **Guardar copias de los datos de la organización** | Elija **Bloquear** para deshabilitar el uso de la opción Guardar como en esta aplicación. Elija **Permitir** si quiere permitir el uso de Guardar como. **Nota:** *Esta opción es compatible con Microsoft Excel, OneNote, PowerPoint y Word. También puede admitirse en aplicaciones de LOB y de terceros.*| **Permitir** |  
|<ul><ui>**Permitir al usuario guardar copias en los servicios seleccionados** |Los usuarios pueden guardar en los servicios seleccionados (OneDrive para la Empresa, SharePoint y el almacenamiento local). El resto de servicios se bloquearán.  | **0 seleccionados** |
| **Restringir cortar, copiar y pegar entre otras aplicaciones** | Especifique cuándo pueden usarse las acciones de cortar, copiar y pegar con esta aplicación. Elija de entre las siguientes opciones: <ul><li>**Bloqueado**:  no permite las acciones de cortar, copiar y pegar entre esta aplicación y cualquier otra.</li><li>**Aplicaciones administradas por directivas**: permite las acciones de cortar, copiar y pegar entre esta aplicación y otras aplicaciones administradas por directivas.</li><li>**Aplicaciones administradas por directivas con pegar**: permite cortar o copiar entre esta aplicación y otras aplicaciones administradas por directivas. Permite que los datos de cualquier aplicación se peguen en esta aplicación.</li><li>**Cualquier aplicación**: no se aplican restricciones a las acciones de cortar, copiar y pegar en esta aplicación y desde ella. | **Cualquier aplicación** |
| <ul><ui>**Límite de caracteres para cortar y copiar en cualquier aplicación** | Especifique el número de caracteres que se pueden cortar o copiar de las cuentas y los datos de la organización.  Esto permitirá compartir el número especificado de caracteres en cualquier aplicación, independientemente de la opción "Restringir cortar, copiar y pegar con otras aplicaciones".<p>Valor predeterminado = 0<p>**Nota**: se necesita Portal de empresa de Intune, versión 5.0.4364.0 o posterior.  | **0** |
| **Captura de pantalla y Asistente de Google** | Seleccione **Deshabilitar** para bloquear las características de captura de pantalla y **Asistente de Google** del dispositivo cuando se usa esta aplicación. Al elegir **Deshabilitar** también se desenfocará la imagen de vista previa de las últimas aplicaciones si se usa esta aplicación con una cuenta profesional o educativa.| **Habilitar** |

  
### <a name="encryption"></a>Cifrado
| Setting | Cómo se usa | Valor predeterminado |
|------|------|------|
| **Cifrar datos de la organización** | Elija **Requerir** para habilitar el cifrado de datos profesionales o educativos en esta aplicación. Intune usa un esquema de cifrado AES de 256 bits de OpenSSL junto con el sistema del almacén de claves Android para cifrar los datos de la aplicación de manera segura. Los datos se cifran de forma sincrónica durante las tareas de E/S de archivo. El contenido del almacenamiento del dispositivo estará siempre cifrado. Los archivos nuevos se cifrarán con claves de 256 bits. Los archivos cifrados de 128 bits existentes se someterán a un intento de migración a las claves de 256 bits, pero el proceso no está garantizado. Los archivos cifrados con claves de 128 bits seguirán siendo legibles. <br><br> El método de cifrado es compatible con FIPS 140-2.     |  **Requerir**|  
| <ul><ui>**Cifrar datos de la organización en los dispositivos inscritos** | Seleccione **Requerir** para aplicar el cifrado de datos de la organización con el cifrado de la capa de aplicaciones de Intune en todos los dispositivos. Seleccione **No se requiere** para no aplicar el cifrado de datos de la organización con el cifrado de la capa de aplicaciones de Intune en los dispositivos inscritos.| **Requerir** |


### <a name="functionality"></a>Funcionalidad
| Setting | Cómo se usa | Valor predeterminado |
|------|------|------|
| **Sincronizar la aplicación con la aplicación de contactos nativa** | Elija **Deshabilitar** para impedir que la aplicación guarde datos en la aplicación de contactos nativa del dispositivo. Si elije **Habilitar**, la aplicación puede guardar datos en la aplicación de contactos nativa del dispositivo. <br><br>Cuando realiza un borrado selectivo para quitar los datos profesionales o educativos de la aplicación, se quitan los contactos sincronizados directamente desde la aplicación a la aplicación nativa Contactos. No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. Actualmente esto se aplica únicamente para la aplicación Microsoft Outlook. | **Habilitar** |
| **Impresión de datos de la organización** | Elija **Deshabilitar** para impedir que la aplicación imprima datos profesionales o educativos. Si deja esta opción **habilitada**, el valor predeterminado, los usuarios podrán exportar e imprimir todos los datos de la organización. | **Habilitar** |
|**Compartir contenido web con exploradores administrados por directivas** | Especifique cómo se debe abrir el contenido web (vínculos http/https) en las aplicaciones administradas por directivas. Elija de entre las siguientes opciones:<ul><li>**Requerir**: permite que el contenido web se abra solo en exploradores administrados por directivas.</li><li>**Explorador no administrado**: permite que el contenido web se abra solo en el explorador no administrado definido por la configuración de **identificador de explorador no administrado**. No se administrará el contenido web en el explorador de destino.<br>**Nota**: Se necesita Portal de empresa de Intune, versión 5.0.4415.0 o posterior.</li><li>**No configurado**: permite los vínculos web en cualquier aplicación. </li></ul><br><br> Si usa Intune para administrar los dispositivos, vea [Administración del acceso a Internet mediante un explorador protegido por directivas de Microsoft Intune](app-configuration-managed-browser.md).<br><br>**Exploradores administrados por directivas**<br>Si implementa varios exploradores administrados por directivas, solo se iniciará uno.  El orden de inicio será Intune Managed Browser y luego Microsoft Edge.  En Android, los usuarios finales pueden elegir otras aplicaciones administradas por directivas compatibles con los vínculos http/https en el caso de que no tengan instalado ni Intune Managed Browser ni Microsoft Edge.<p>Si se necesita un explorador administrado por directivas pero no está instalado, se pedirá a los usuarios finales que instalen Intune Managed Browser.<p>Si se necesita un explorador administrado por directivas, los vínculos de aplicaciones Android se administran con la opción de directiva **Permitir a la aplicación transferir datos a otras aplicaciones**.<p>**Inscripción de dispositivos de Intune**<br>Si usa Intune para administrar sus dispositivos, consulte Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune. <p>**Microsoft Edge administrado por directivas**<br>El explorador Microsoft Edge para dispositivos móviles (iOS y Android) admite las directivas de protección de aplicaciones de Intune. Los usuarios que inicien sesión con sus cuentas corporativas de Azure AD en la aplicación del explorador Microsoft Edge estarán protegidos por Intune. El explorador Microsoft Edge integra el SDK de MAM y admite todas sus directivas de protección de datos, con la excepción de evitar:<br><ul><li>**Guardar como**: el explorador Microsoft Edge no permite que los usuarios agreguen conexiones directas en la aplicación a los proveedores de almacenamiento en nube (como, por ejemplo, OneDrive).</li><li>**Sincronización de contactos**: el explorador Microsoft Edge no guarda datos en las listas de contactos nativos.</li></ul><br>**Nota:** *El SDK de la aplicación no puede determinar si una aplicación de destino es un explorador. En los dispositivos Android se permiten otras aplicaciones de exploradores administrados compatibles con http/https.* | **No configurado**. |
|<ul><ui>**Identificador de explorador no administrado** | Escriba el identificador de aplicación de un solo explorador. Se abrirá contenido web (vínculos http o https) de aplicaciones administradas por directivas en el explorador especificado.  No se administrará el contenido web en el explorador de destino. | **En blanco** |
|<ul><ui>**Nombre del explorador no administrado** | Escriba el nombre de aplicación del explorador asociado al **identificador de explorador no administrado**. Los usuarios podrán ver este nombre si no se instala el explorador especificado.  | **En blanco** |


## <a name="data-transfer-exemptions"></a>Exenciones de transferencia de datos

  La directiva de protección de aplicaciones de Intune puede permitir la transferencia de datos desde y hacia algunas aplicaciones y servicios de plataforma. Por ejemplo, todas las aplicaciones administradas de Intune en Android deben poder transferir datos desde y hacia la función Texto a voz de Google, de forma que se pueda leer en voz alta el texto que aparezca en la pantalla del dispositivo móvil. Esta lista está sujeta a cambios y refleja los servicios y las aplicaciones que se consideran útiles para una productividad segura.

### <a name="full-exemptions"></a>Exenciones completas

  En estas aplicaciones y servicios se permite totalmente la transferencia de datos desde y hacia aplicaciones administradas por Intune.

  |Nombre de aplicación/servicio | Descripción |
  | ------ | ---- |
  | com.android.phone | Aplicación de teléfono nativa
  | com.android.vending | Google Play Store |
  | com.android.documentsui | Selector de documentos de Android|
  | com.google.android.webview | [WebView](https://developer.android.com/reference/android/webkit/WebView.html), necesario para muchas aplicaciones, incluido Outlook |
  | com.android.webview |[WebView](https://developer.android.com/reference/android/webkit/WebView.html), necesario para muchas aplicaciones, incluido Outlook|
  | com.google.android.tts | Texto a voz de Google |
  | com.android.providers.settings | Configuración del sistema Android |
  | com.android.settings | Configuración del sistema Android |
  | com.azure.authenticator | Aplicación Azure Authenticator, necesaria para una autenticación correcta en muchos escenarios |
  | com.microsoft.windowsintune.companyportal | Intune Portal de empresa|

### <a name="conditional-exemptions"></a>Exenciones condicionales
  En estas aplicaciones y servicios solo se permite la transferencia de datos desde y hacia aplicaciones administradas por Intune en determinadas condiciones.

  |Nombre de aplicación/servicio | Descripción | Condición de exención|
  | ------ | ---- | --- |
  | com.android.chrome | Explorador Google Chrome | Chrome se utiliza para algunos componentes de WebView en Android 7.0 y versiones posteriores, y nunca está oculto. No obstante, el flujo de datos desde y hacia la aplicación siempre está restringido.  |
  | com.skype.raider | Skype | La aplicación Skype solo se permite para determinadas acciones que dan lugar a una llamada telefónica. |
  | com.android.providers.media | Proveedor de contenido multimedia de Android | El proveedor de contenido multimedia solo se permite para la selección de tono. |
  | com.google.android.gms; com.google.android.gsf | Paquetes de Servicios de Google Play | Estos paquetes se permiten para acciones de Google Cloud Messaging, como las notificaciones de inserción. |
  | com.google.android.apps.maps | Google Maps | Se permiten direcciones para la navegación |

Para obtener más información, consulte [Data transfer policy exceptions for apps](app-protection-policies-exception.md) (Excepciones de la directiva de transferencia de datos para aplicaciones).

## <a name="access-requirements"></a>Requisitos de acceso

| Setting | Cómo se usa |  
|------|------| 
| **Requerir PIN para acceder** | Seleccione **Sí** para exigir un PIN para usar esta aplicación. Se pedirá al usuario que configure este PIN la primera vez que ejecute la aplicación en un contexto profesional o educativo. <br><br> Valor predeterminado = **Sí**.<br><br> Configure las siguientes opciones para la intensidad del PIN: <br> <ul><li>**Seleccionar tipo**: establezca un requisito de PIN numérico o de tipo contraseña antes de acceder a una aplicación con directivas de protección de aplicaciones aplicadas. Los requisitos numéricos solo implican números, mientras que una contraseña se puede definir con al menos 1 letra **o** 1 carácter especial. <br><br> Valor predeterminado = **Numérico**<br><br> **Nota:** Entre los caracteres especiales permitidos se incluyen los caracteres especiales y los símbolos del teclado en inglés de Android.</li></ul><ul><li> **Permitir el PIN simple:** seleccione **Sí** para permitir que los usuarios usen secuencias de PIN simples como *1234*, *1111*, *abcd* o *aaaa*. Seleccione **No** para impedir que usen secuencias simples. Las secuencias simples se comprueban en ventanas deslizantes de tres caracteres. Si **No** está configurado, 1235 o 1112 no se aceptarán como PIN establecido por el usuario final, pero se permitirá 1122. <br><br>Valor predeterminado = **Sí**. <br><br>**Nota:** Si se configura un PIN de tipo código de acceso y la opción Permitir el PIN simple está establecida en Sí, el usuario necesitará como mínimo una letra **o** un carácter especial en su PIN. Si se configura un PIN de tipo contraseña y la opción Permitir el PIN simple está establecida en No, el usuario necesitará como mínimo un número **y** una letra **y** un carácter especial en su PIN. </li> <br> <li>  **Longitud del PIN:** especifique el número mínimo de dígitos en una secuencia de PIN. <br><br>Valor predeterminado = **4** </li> <br> <li> **Permitir huella digital en lugar de PIN (Android 6.0 y posteriores)** : pulse **Sí** para permitir que el usuario use la [autenticación con huella digital](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) en lugar de un PIN para el acceso a la aplicación. <br><br>Valor predeterminado = **Sí**. <br><br>**Nota:** Esta característica admite controles genéricos para biometría en dispositivos Android. *No se admite* la configuración de biometría específica del OEM, como Samsung Pass. <br><br>En Android, puede permitir que el usuario demuestre su identidad con la [autenticación con huella digital de Android](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) en lugar de usar un PIN. Cuando el usuario intenta usar esta aplicación con su cuenta profesional o educativa, se le pide que confirme su identidad mediante huella digital en lugar de escribir un PIN. <br><br> Los dispositivos inscritos en el perfil de trabajo Android requieren el registro de una huella digital independiente para aplicar la directiva **Permitir desbloqueo mediante huellas digitales en lugar de mediante PIN**. Esta directiva surte efecto únicamente en las aplicaciones administradas de directiva instaladas en el perfil de trabajo Android. La huella digital independiente debe estar registrada con el dispositivo después de crear el perfil de trabajo Android por medio de la inscripción en el Portal de empresa. Para obtener más información sobre las huellas digitales con perfiles de trabajo Android, vea [Bloquear el perfil de trabajo](https://support.google.com/work/android/answer/7029958).<br><br><ul><li>**Invalidar la huella digital con el PIN después del tiempo de espera**: para usar esta configuración, seleccione **Sí** y, después, configure un tiempo de espera de inactividad. <br><br>Valor predeterminado = **Sí**. </li></ul> <br> <ul><li>**Tiempo de espera (minutos de inactividad)** : especifique un tiempo en minutos transcurrido el cual un código de acceso o un PIN numérico (como se configuró) invalidarán el uso de una huella digital. Este valor de tiempo de espera debe ser mayor que el valor especificado en "Volver a comprobar los requisitos de acceso tras (minutos de inactividad)".<br><br>Valor predeterminado = **30**  </li></ul></li></ul><br><ul><li>**Deshabilitar el PIN de aplicación cuando se administra el PIN del dispositivo**: seleccione **Sí** para deshabilitar el PIN de aplicación cuando se detecta un bloqueo de dispositivo en un dispositivo inscrito con Portal de empresa configurado. <br><br> Valor predeterminado = **No**. </li></ul> | 
| **Requerir credenciales corporativas en acceso** | Pulse **Sí** para requerir que el usuario inicie sesión con su cuenta profesional o educativa en lugar de escribir un PIN para el acceso a la aplicación. Cuando se establece en **Sí** y están activados el PIN o las solicitudes biométricas, se muestran tanto las credenciales corporativas como el PIN o las solicitudes biométricas. <br><br>Valor predeterminado: **No** |
| **Volver a comprobar los requisitos de acceso después de (minutos)** | Establezca la siguiente configuración: <ul><li>**Tiempo de espera**: número de minutos antes de que se vuelvan a comprobar los requisitos de acceso (definidos anteriormente en la directiva). Por ejemplo, si un administrador activa el PIN y bloquea los dispositivos liberados en la directiva, cuando un usuario abre una aplicación administrada por Intune, debe escribir un PIN y usar la aplicación en un dispositivo que no esté liberado. Al usar esta configuración, el usuario no tendría que escribir un PIN ni someterse a otra comprobación de detección de raíz en ninguna aplicación administrada por Intune durante un período igual al valor configurado.  <br><br>Este formato de la configuración de directiva admite un número entero positivo. <br><br> Valor predeterminado = **30 minutos**. <br><br> **Nota:** En el caso de Android, el PIN es el mismo para todas las aplicaciones administradas de Intune. El temporizador del PIN se restablece una vez que la aplicación deja de estar en segundo plano en el dispositivo. Durante el período de tiempo de expiración definido en esta opción de configuración, el usuario no tendría que escribir el PIN en ninguna aplicación administrada con Intune que lo comparta. <br><br></li> |
| **Bloquear captura de pantalla y asistente de Android** | Seleccione **Sí** para bloquear las características de captura de pantalla y **Asistente para Android** del dispositivo cuando se usa esta aplicación. Al pulsar **Sí** también se desenfocará la imagen de vista previa de las últimas aplicaciones si se usa esta aplicación con una cuenta profesional o educativa. <br><br>Valor predeterminado: **No** |

> [!NOTE]  
> Para obtener más información sobre cómo funcionan diferentes opciones de protección de aplicaciones en Intune configuradas en la sección Acceso para el mismo conjunto de aplicaciones y usuarios en Android, vea [Preguntas más frecuentes sobre MAM](mam-faq.md) y [Borrar los datos de forma selectiva mediante acciones de acceso de la directiva de protección de aplicaciones en Intune](app-protection-policies-access-actions.md).


## <a name="conditional-launch"></a>Inicio condicional
Configure opciones de inicio condicionales para establecer los requisitos de seguridad del inicio de sesión para la directiva de protección de acceso. 

De forma predeterminada, se proporcionan varias opciones de configuración con acciones y valores preconfigurados. Puede eliminar algunas opciones de configuración, como la *Versión mínima del sistema operativo*. También puede seleccionar una configuración adicional en la lista desplegable **Seleccionar una**. 

| Setting | Cómo se usa |  
|---------|------------| 
| **N.º máximo de intentos de PIN** | Especifique el número de intentos que tiene el usuario para escribir correctamente el PIN antes de que se lleve a cabo la acción configurada. Este formato de la configuración de directiva admite un número entero positivo. Las *acciones* incluyen: <br><ul><li>**Restablecer PIN**: el usuario debe restablecer el PIN.</li></ul> <ul><li>**Borrar datos**: la cuenta de usuario que está asociada con la aplicación se borra del dispositivo.  </li></ul> </li></ul> Valor predeterminado = **5** |
| **Período de gracia sin conexión** | Número de minutos que las aplicaciones MAM se pueden ejecutar sin conexión. Especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación. Las *acciones* incluyen: <br><ul><li>**Bloquear el acceso (minutos)** : número de minutos que las aplicaciones MAM se pueden ejecutar sin conexión. Especifique el tiempo (en minutos) que debe transcurrir antes de que se vuelvan a comprobar los requisitos de acceso de la aplicación. Cuando expira este período, la aplicación necesita la autenticación del usuario a Azure Active Directory (Azure AD) para poder seguir ejecutándose. <br><br>Este formato de la configuración de directiva admite un número entero positivo. <br><br>Valor predeterminado = **720** minutos (12 horas) </li></ul> <ul><li>**Borrar datos (días)** : después de estos días (definidos por el administrador) de ejecución sin conexión, la aplicación necesitará que el usuario se conecte a la red y vuelva a autenticarse. Si el usuario se autentica correctamente, puede seguir teniendo acceso a sus datos y el intervalo sin conexión se restablecerá.  Si el usuario no puede autenticarse, la aplicación realizará un borrado selectivo de los datos y la cuenta de los usuarios. Para obtener más información, vea [Borrado solo de datos corporativos de aplicaciones administradas por Intune](apps-selective-wipe.md).</li></ul> Este formato de la configuración de directiva admite un número entero positivo. <br><br>  Valor predeterminado = **90** días </li></ul> <br><br>  Esta entrada puede aparecer varias veces y cada instancia admite una acción diferente. |   
| **Dispositivos con jailbreak o rooting** |No se puede establecer ningún valor para esta configuración. Las *acciones* incluyen: <br><ul><li>**Bloquear acceso**: impida que esta aplicación se ejecute en dispositivos con jailbreak o rooting. El usuario sigue siendo capaz de usar esta aplicación para tareas personales, pero tendrá que usar otro dispositivo para acceder a los datos profesionales o educativos de esta aplicación.</li></ul> <ul><li>**Borrar datos**: la cuenta de usuario que está asociada con la aplicación se borra del dispositivo.  </li></ul> |
| **Versión mínima del sistema operativo** | Especifique un sistema operativo mínimo Android que es obligatorio para usar esta aplicación. Las *acciones* incluyen: <br><ul><li>**Advertir**: el usuario verá una notificación si la versión de Android del dispositivo no cumple el requisito. Se puede descartar esta notificación.  </li></ul> <ul><li>**Bloquear acceso**: se bloqueará el acceso al usuario si la versión de Android del dispositivo no cumple el requisito.</li></ul> <ul><li>**Borrar datos**: la cuenta de usuario que está asociada con la aplicación se borra del dispositivo.  </li></ul> </li></ul>Este formato de configuración de directiva admite major.minor, major.minor.build, major.minor.build.revision. |
| **Versión mínima de la aplicación** | Especifique un valor de sistema operativo mínimo. Las *acciones* incluyen: <br><ul><li>**Advertir**: el usuario ve una notificación si la versión de la aplicación del dispositivo no cumple el requisito. Se puede descartar esta notificación.</li></ul> <ul><li>**Bloquear acceso**: se bloquea el acceso al usuario si la versión de la aplicación del dispositivo no cumple el requisito. </li></ul> <ul><li>**Borrar datos**: la cuenta de usuario que está asociada con la aplicación se borra del dispositivo. </li></ul> </li></ul> Como las aplicaciones a menudo tienen esquemas de control de versiones distintos entre sí, cree una directiva con una versión de aplicación mínima destinada a una aplicación (por ejemplo, *directiva de versión de Outlook*).<br><br> Esta entrada puede aparecer varias veces y cada instancia admite una acción diferente.<br><br> Este formato de configuración de directiva admite major.minor, major.minor.build, major.minor.build.revision.<br><br> Además, puede configurar **dónde** los usuarios finales pueden obtener una versión actualizada de una aplicación de línea de negocio (LOB). Los usuarios finales la verán en el cuadro de diálogo de inicio condicional **Versión mínima de la aplicación**, que le pedirá a los usuarios finales que actualicen a una versión mínima de la aplicación de LOB. En Android, esta característica usa la aplicación Portal de empresa. Para configurar dónde un usuario final debería actualizar una aplicación de LOB, la aplicación necesita que se le envíe una [directiva de configuración de aplicación](app-configuration-policies-managed-app.md) administrada con la clave `com.microsoft.intune.myappstore`. El valor enviado definirá desde qué tienda descargará la aplicación el usuario final. Si la aplicación se implementa a través de Portal de empresa, el valor debe ser `CompanyPortal`. En el caso de cualquier otra tienda, debe escribir una dirección URL completa. |
| **Versión mínima de la revisión** | Exige que los dispositivos tengan una revisión de seguridad de Android mínima publicada por Google.  <br><ul><li>**Advertir**: el usuario verá una notificación si la versión de Android del dispositivo no cumple el requisito. Se puede descartar esta notificación.  </li></ul> <ul><li>**Bloquear acceso**: se bloqueará el acceso al usuario si la versión de Android del dispositivo no cumple el requisito.</li></ul> <ul><li>**Borrar datos**: la cuenta de usuario que está asociada con la aplicación se borra del dispositivo.  </li></ul></li></ul> Esta configuración de directiva es compatible con el formato de fecha *AAAA-MM-DD*. |
| **Fabricantes de dispositivos** | Especifique una lista de fabricantes separada por puntos y comas. Evite los espacios en las listas de varios valores. Estos valores no distinguen entre mayúsculas y minúsculas. Las *acciones* incluyen: <br><ul><li>**Permitir especificados (bloquear no especificados)** : solo los dispositivos que coincidan con el fabricante especificado pueden usar la aplicación. El resto de dispositivos se bloquean. </li></ul> <ul><li>**Permitir especificados (borrar no especificados)** : la cuenta de usuario que está asociada con la aplicación se borra del dispositivo. </li></ul> Para más información sobre el uso de esta configuración, consulte [Acciones de inicio condicional](app-protection-policies-access-actions.md#android-policy-settings). |
| **Atestación de dispositivo SafetyNet** | Las directivas de protección de aplicaciones admiten algunas de las API de Google Play Protect. En concreto, este valor configura la atestación de SafetyNet de Google en dispositivos de usuarios finales. Especifique **Integridad básica** o **Integridad básica y dispositivos certificados**. **Integridad básica** muestra información sobre la integridad general del dispositivo. Por ejemplo, dispositivos manipulados por rooting, emuladores, dispositivos virtuales y cualquier otro dispositivo con signos de error de integridad básica por manipulación. **Integridad básica y dispositivos certificados** ofrece información sobre la compatibilidad del dispositivo con los servicios de Google. Solo superan esta comprobación aquellos dispositivos que no se han manipulado y están certificados por Google. Las *acciones* incluyen: <br><ul><li>**Advertir**: el usuario ve una notificación si el dispositivo no supera el examen de atestación de SafetyNet de Google según el valor configurado. Se puede descartar esta notificación. </li></ul><ul><li>**Bloquear acceso**: se bloquea el acceso al usuario si el dispositivo no supera el examen de atestación de SafetyNet de Google según el valor configurado. </li></ul> <ul><li>**Borrar datos**: la cuenta de usuario que está asociada con la aplicación se borra del dispositivo. </li></ul> </li></ul> Para ver las preguntas más frecuentes relacionadas con esta configuración, vea [Preguntas más frecuentes sobre MAM y la protección de la aplicación](mam-faq.md#app-experience-on-android). |
| **Requerir examen de amenazas en las aplicaciones** | Las directivas de protección de aplicaciones admiten algunas de las API de Google Play Protect. En concreto, este valor garantiza que el examen de verificación de aplicaciones de Google está activado para los dispositivos de usuarios finales. Si se ha configurado, se bloqueará el acceso al usuario hasta que se active el examen de aplicaciones de Google en su dispositivo Android. Las *acciones* incluyen: <br><ul><li>**Advertir**: se muestra una notificación al usuario si el examen de verificación de aplicaciones de Google no está activado en el dispositivo. Se puede descartar esta notificación. </li></ul><ul><li>**Bloquear acceso**: se bloquea el acceso al usuario si el examen de verificación de aplicaciones de Google no está activado en el dispositivo. </li></ul></li></ul> Los resultados del examen de verificación de aplicaciones de Google se muestran en el informe **Aplicaciones potencialmente dañinas** en la consola. |
| **Versión mínima del Portal de empresa** | Con la opción **Min Company Portal version** (Versión mínima del Portal de empresa), puede especificar una versión definida mínima específica del Portal de empresa que se aplique en un dispositivo de usuario final. Esta configuración de inicio condicional permite establecer valores para **bloquear el acceso**, **borrar datos** y **advertir** como posibles acciones cuando no se cumple cada uno de los valores. Los posibles formatos de este valor siguen el patrón *[Principal].[Secundaria]* , *[Principal].[Secundaria].[Compilación]* o *[Principal].[Secundaria].[Compilación].[Revisión]* . Dado que es posible que algunos usuarios finales no prefieran una actualización forzada de las aplicaciones en el momento, la opción "advertir" puede ser muy adecuada al configurar este valor. Lo bueno de Google Play Store es que solo envía la diferencia de bytes de las actualizaciones de aplicaciones, pero aún así puede seguir siendo una gran cantidad de datos que quizás el usuario no quiera utilizar si está trabajando con datos en el momento de la actualización. Forzar una actualización y, por tanto, descargar una aplicación actualizada podría dar lugar a cargos por datos inesperados en el momento de la actualización. Para más información, consulte [Configuración de directivas de Android](~/apps/app-protection-policies-access-actions.md#android-policy-settings). |
| **Nivel máximo de amenazas de dispositivo permitido** | Las directivas de protección de aplicaciones pueden aprovechar el conector de MTD de Intune. Especifique un nivel de amenaza máximo aceptable para usar esta aplicación. Las amenazas vienen determinadas por la aplicación de proveedor de Mobile Threat Defense (MTD) que se haya seleccionado en el dispositivo del usuario final. Especifique *Protegido*, *Bajo*, *Medio* o *Alto*. El nivel *Protegido* no requiere ninguna amenaza en el dispositivo y es el valor configurable más restrictivo, mientras que *Alto* requiere básicamente una conexión activa de Intune a MTD. Las *acciones* incluyen: <br><ul><li>**Bloquear acceso**: se impedirá el acceso del usuario si el nivel de amenaza determinado por la aplicación de proveedor de Mobile Threat Defense (MTD) seleccionada en el dispositivo del usuario final no cumple este requisito.</li></ul> <ul><li>**Borrar datos**: la cuenta de usuario que está asociada con la aplicación se borra del dispositivo.</li></ul>Para más información sobre el uso de esta opción, consulte [Habilitación del conector Mobile Threat Defense en Intune para dispositivos no inscritos](~/protect/mtd-enable-unenrolled-devices.md). |