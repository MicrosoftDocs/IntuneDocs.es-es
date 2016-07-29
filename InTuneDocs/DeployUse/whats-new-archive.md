---
title: Novedades de archivo | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 458ee268d0c6a8fa6cbe6cc23ad07f0e45eff3e5


---
## Diciembre de 2015
### Cambios y actualizaciones del Portal de empresa de Microsoft
Los siguientes cambios se realizaron en el Portal de empresa en esta versión.

**Aplicación Portal de empresa de Android**

Los siguientes cambios se realizaron para cumplir con los nuevos requisitos de Google. En dispositivos con Android 6.0 y versiones posteriores, se muestran dos nuevos mensajes a los usuarios:
* ¿Permitir que Portal de empresa realice y administre llamadas telefónicas?
* ¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?

Consulte la tabla siguiente para conocer los detalles sobre estos dos mensajes.



Texto del mensaje  |¿Permitir que Portal de empresa realice y administre llamadas telefónicas?  
---------|---------
Significado del mensaje     |  Permite que el número de teléfono y el IMEI del dispositivo del usuario se envíen al servicio Intune y que aparezcan en la consola de administración de la página de hardware.   </br></br>**NOTA: La aplicación Portal de empresa nunca hace ni administra llamadas telefónicas.** Google controla el texto del mensaje y no se puede cambiar. </br></br>Para ver la página **Hardware**, vaya a **Grupos** > **Todos los dispositivos móviles** > **Dispositivos**. Seleccione el dispositivo del usuario y vaya a **Ver propiedades** > **Hardware**.    
Cuándo y dónde aparece el mensaje  | El mensaje aparece cuando los usuarios inician sesión en la aplicación Portal de empresa por primera vez para inscribir su dispositivo.|         
Qué sucede si los usuarios permiten el acceso  |  El número de teléfono y el IMEI del dispositivo aparecerán en la página de hardware de la consola de administración. |         
Qué sucede si los usuarios deniegan el acceso     | Podrán seguir usando la aplicación Portal de empresa e inscribir sus dispositivos, pero el número de teléfono y el IMEI de los dispositivos de los usuarios aparecerán en blanco en la página de hardware de la consola de administración.       </br></br> La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para que el mensaje no se vuelva a mostrar.</br></br>Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios inicien sesión en la aplicación Portal de empresa después de la inscripción.</br></br>Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración**  >  **Aplicaciones**  >  **Portal de empresa**  >  **Permisos**  >  **Teléfono** y activar el permiso.
Más información     |  Para los usuarios: [Iniciar sesión en el Portal de empresa](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp).  </br></br>Para los profesionales de TI: La información de esta tabla también está disponible en [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs).   

Texto del mensaje  |¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?  
---------|---------
Significado del mensaje     |  Habilita el dispositivo para escribir registros de datos en la tarjeta SD del dispositivo, que permite mover los registros con un cable USB.   </br></br>**NOTA: La aplicación Portal de empresa nunca accede a las fotos, a los elementos multimedia ni a los archivos de los usuarios.** Google controla el texto del mensaje y no se puede cambiar.     
Cuándo y dónde aparece el mensaje  | El mensaje aparece cuando los usuarios pulsan en **Enviar datos** para enviar registros de datos a su administrador de TI.|         
Qué sucede si los usuarios permiten el acceso  |  Los registros se copiarán en la tarjeta SD. |         
Qué sucede si los usuarios deniegan el acceso     | Aun así pueden enviar registros de datos, pero los registros no se copiarán en la tarjeta SD del dispositivo.       </br></br> La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para que el mensaje no se vuelva a mostrar.</br></br>Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios intenten enviar registros.</br></br>Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración**  >  **Aplicaciones**  >  **Portal de empresa**  >  **Permisos**  >  **Almacenamiento** y activar el permiso.
Más información     |  Para los usuarios: [Enviar los registros de datos de diagnóstico al administrador de TI mediante correo electrónico](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs).  </br></br>Para los profesionales de TI: La información de esta tabla también está disponible en [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs).   


**Aplicación Portal de empresa de iOS**
* Los usuarios ahora pueden usar Microsoft Outlook u otras aplicaciones de correo electrónico para enviar registros de diagnóstico al administrador de TI. Anteriormente, se puede usar solo la aplicación nativa.
* Se mejoró la compatibilidad para dispositivos de empresa y el programa de inscripción de dispositivos (DEP) de Apple. Para conocer más detalles, consulte [Usar un dispositivo iOS con Intune](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device).
* En la lista de dispositivos inscritos del usuario, aparece una marca de verificación verde junto al dispositivo que está usando actualmente el usuario. Antes de que se añadiera esta marca de verificación, los usuarios no podrían saber qué dispositivo inscrito estaban usando.

**Aplicación Portal de empresa de Windows**

Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso del portal de empresa para mejorar sus productos y servicios. Los usuarios finales pueden desactivar la recopilación de datos mediante la opción Datos de uso en su dispositivo, pero los administradores no tienen ningún control sobre la recopilación de datos y no pueden cambiar la configuración que el usuario final seleccione.



## Noviembre de 2015
### Administración de aplicaciones
Intune admite directivas de administración de aplicaciones móviles (MAM) que ayudan a evitar que los datos corporativos se filtren a las aplicaciones o los servicios de los consumidores. Históricamente, estas directivas solo se aplicarían en aplicaciones móviles que se ejecuten en dispositivos que también se inscribieron para la administración de dispositivos móviles (MDM) en Intune.

Con la actualización de este mes, Intune está ampliando sus funcionalidades MAM a nuevas clases de dispositivos. Además de los dispositivos inscritos en Intune, ahora puede aplicar directivas MAM en:
* dispositivos administrados por alguna otra solución de administración de dispositivos móviles (MDM);
* dispositivos que no estén inscritos en ningún sistema de administración de dispositivos, normalmente dispositivos bring your own device (BYO).

Puede encontrar más información sobre estas nuevas funcionalidades MAM en las siguientes entradas de blog:
* [Mejorar la productividad móvil administrada](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Anuncio de nuevas funcionalidades de movilidad empresarial de Microsoft](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

Además, a continuación se muestran algunos aspectos destacados e información adicional sobre las características MAM de Intune:
* Los datos corporativos se aíslan de los datos del consumidor en las aplicaciones habilitadas para Intune, incluidas las aplicaciones de Office Mobile, las aplicaciones de terceros que han adoptado el SDK de Intune o las aplicaciones de línea de negocio encapsuladas por Intune.
* Los datos de la empresa se pueden compartir (**cortar, copiar y pegar**) entre las aplicaciones de empresa, a la vez que se evita el uso compartido de datos de empresa en aplicaciones personales. Lea [Cómo protegen las directivas MAM los datos de las aplicaciones](https://technet.microsoft.com/library/mt627825.aspx) para conocer más detalles. Este escenario de ejemplo, [Experiencia del usuario final para aplicaciones asociadas con directivas de administración de aplicaciones móviles de Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx), se muestra cómo se evita el uso compartido de los datos de empresa en aplicaciones personales.
* Directivas de prevención de pérdida de datos clave como PIN por aplicación, controles guardar como y uso compartido de datos administrados entre aplicaciones. Lea [Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx) para ver una lista con todas las directivas.
* Word, Excel, PowerPoint, Outlook, OneNote y OneDrive para la Empresa tienen estas nuevas funcionalidades y se pueden administrar con y sin inscripción de dispositivos. Las funcionalidades de protección de pérdida de datos están integradas de forma nativa en las aplicaciones de Office estándares de Apple Store o Google Play Store, y no requieren instalación de prueba ni ajuste de la aplicación.
* Para conocer los primeros pasos, consulte [Introducción a las directivas de administración de aplicaciones móviles en el portal de Azure](https://technet.microsoft.com/library/mt627830.aspx). Para conocer cómo configurar e implementar directivas de administración de aplicaciones móviles, consulte [Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Cuando los usuarios finales se autentican en la aplicación con sus credenciales corporativas, las funcionalidades de protección de la pérdida de datos se configuran automáticamente. El tema [Experiencia del usuario final para aplicaciones asociadas con directivas de administración de aplicaciones móviles de Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx) tiene algunos escenarios de ejemplo para acceder a OneDrive en dispositivos iOS y Android.
* Funciona en dispositivos iOS y Android.

La lista de [Aplicaciones de Microsoft que puede utilizar con las directivas de administración de aplicaciones móviles de Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx) se ha actualizado para se muestren las aplicaciones más recientes.

### Administración de dispositivos
 **Administración de dispositivos Mac OS X** Con Intune, ahora puede inscribir y administrar dispositivos Mac OS X. Puede hacer lo siguiente con los dispositivos Mac OS X:
* Inscribir dispositivos para que los administre Intune. Consulte [Configurar la administración de iOS con Microsoft Intune](https://technet.microsoft.com/library/dn408185.aspx).
* Controlar la configuración de dispositivo mediante una directiva de configuración general. Consulte [Configuración de directivas de configuración de Mac OS X en Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx).
* Implementar la configuración de Mac OS X que ha creado con Apple Configurator. Consulte [Configuración de directivas personalizadas de Mac OS X en Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx).
* Recopilar el inventario de hardware y de software de los dispositivos Mac OS X. Consulte [Comprender el funcionamiento de sus dispositivos mediante el inventario en Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx).
* Ejecutar nuevos informes donde se muestren los detalles sobre los dispositivos de Mac OS X que administre. Consulte [Comprender las operaciones de Microsoft Intune mediante informes](https://technet.microsoft.com/library/dn646977.aspx).

**Nueva configuración del explorador Edge para dispositivos de Windows 10** Se ha agregado una nueva configuración a la directiva de configuración general de Windows 10 que permite administrar la configuración y las características del explorador Microsoft Edge. Consulte [Configuración de directivas de configuración de Windows 10 en Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx).

**Perfiles de correo electrónico** Se ha agregado una nueva directiva de perfiles de correo electrónico a los dispositivos de escritorio de Windows 10 y móviles de Windows 10. Consulte [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](https://technet.microsoft.com/library/dn646984.aspx).

**Nueva configuración de directivas de cumplimiento** La nueva configuración de directivas de sistema y seguridad siguiente se ha agregado a la lista de directivas de cumplimiento:
* Para asegurarse de que los dispositivos con Windows 8.1 o versiones posteriores que acceden a los recursos de empresa tengan instaladas las actualizaciones más recientes, use la configuración **Requerir actualizaciones automáticas**. También puede especificar el tipo de actualizaciones que se instalarán automáticamente: todas las actualizaciones marcadas como importantes o todas las marcadas como importantes o recomendadas. Para obtener la lista completa de configuraciones de directivas de cumplimiento, consulte [Administrar directivas de cumplimiento del dispositivo de Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx).
* La nueva configuración **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad** combinada con la configuración existente **Minutos de inactividad antes de que sea necesaria la contraseña** permite crear una configuración de cumplimiento que requiera que el usuario final escriba una contraseña para utilizar un dispositivo que ha estado inactivo durante un tiempo determinado.

**Nuevas opciones de directivas de acceso condicional** Puede aplicar directivas de acceso condicional a **todos los usuarios** en directivas de acceso condicional nuevas o existentes. Todos los usuarios con licencia para Intune y Office 365 deberán inscribir sus dispositivos y, si la plataforma de dispositivo no es compatible con Intune, el acceso se bloqueará para las aplicaciones de cliente que usen [inicio de sesión basado en la autenticación de Active Directory (autenticación moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/).

También puede especificar que la directiva de acceso condicional se aplique a **todas las plataformas**.  Cualquier aplicación cliente que use el [inicio de sesión basado en la autenticación de Active Directory (autenticación moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) está sujeta a la directiva de acceso condicional y, si la plataforma no es compatible con Intune, se bloqueará.

### Cambios y actualizaciones del Portal de empresa de Microsoft
Los siguientes cambios se realizaron en las aplicaciones de portal de empresa en esta versión:

* **Android**: una pantalla de inicio de sesión se ha agregado a la aplicación Portal de empresa de Android para ayudar a los usuarios a entender el propósito de la aplicación Portal de empresa. Esta pantalla está diseñada para reducir las descargas de la aplicación por parte de los usuarios cuyas empresas no son suscriptores de Intune.

* **iOS**: Intune ahora admite la inscripción de dispositivos Mac OS X mediante el [sitio web del Portal de empresa](https://portal.manage.microsoft.com). Para obtener instrucciones, consulte [Usar un dispositivo iOS con Intune](https://technet.microsoft.com/library/mt598622.aspx).

* **Sitio web del Portal de empresa**: Los usuarios que inscribieron su dispositivo en Intune ahora pueden restablecer su código de acceso mediante la opción **Restablecer código de acceso** del sitio web del Portal de empresa. Anteriormente, solo los administradores de TI podían restablecer los códigos de acceso de los usuarios. La opción Restablecer código de acceso no se admite en dispositivos Windows 8.1 y Windows RT, y la opción solo aparece cuando se inscriben los dispositivos en administración de dispositivos móviles (MDM) o en MDM con Exchange ActiveSync. Para obtener instrucciones de usuario, consulte [Restablecer el código de acceso](https://technet.microsoft.com/library/mt590895.aspx).

### Cambios en las licencias de administradores globales
En octubre, publicamos que los administradores globales (también denominados administradores de inquilinos) podrían seguir realizando tareas de administración cotidianas sin una licencia independiente de Intune o Enterprise Mobility Suite (EMS). Sin embargo, si los administradores globales quieren usar el servicio, por ejemplo para inscribir sus dispositivos, un dispositivo de la empresa o para usar el Portal de empresa de Intune, necesitarán una licencia de Intune o EMS igual que cualquier otro usuario. A continuación se muestran algunos detalles adicionales.
* El Portal de empresa de Intune es donde los usuarios finales pueden:
    * inscribir su dispositivo;
    * ver el estado de su dispositivo;
    * descargar el software que un administrador global ha implementado para la organización;
    * encontrar vínculos publicados por el administrador global sobre cómo ponerse en contacto con su departamento de TI.

    [Obtenga información sobre el Portal de empresa](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) y sobre las distintas [maneras de personalizar el Portal de empresa](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal).
* La persona que se registre para comprar Intune o EMS en nombre de una organización se convierte automáticamente en el primer administrador global de su inquilino. Este otoño, Intune comenzó a asignar automáticamente una licencia Intune o EMS a ese primer administrador global como parte de la transición al [Portal de Office 365](http://portal.office.com/) y la retirada del [Portal de cuentas de Intune](http://account.manage.microsoft.com/). Los administradores globales adicionales que se hayan agregado pueden seguir con la administración diaria sin una licencia independiente de Intune o EMS. Si se actúa como un usuario final e inscribe su dispositivo propio (o corporativo) o descarga software del Portal de empresa, se provocaría la necesidad de una licencia, como cualquier otro usuario.
* El cambio se introducirá progresivamente y comenzará en enero de 2016.
* Para los partners de Microsoft, este cambio no debería afectar a su capacidad para administrar el servicio en nombre de los clientes. Para los usuarios finales, un usuario deberá tener una licencia de Intune o EMS para inscribir un dispositivo y acceder o descargar software desde el Portal de empresa.

Si tiene alguna pregunta sobre este cambio, no dude en ponerse en contacto con el equipo de soporte técnico de Intune:
* [Canales de soporte técnico de Microsoft Intune](https://technet.microsoft.com/library/jj839713.aspx)
* [Soporte técnico de la Comunidad](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

Hay comentarios generales sobre Microsoft Intune, incluidos el envío de solicitudes de cambios de diseño (DCR) o errores, en la página de [Intune user voice](https://microsoftintune.uservoice.com/).


### Novedades de la documentación de Intune: noviembre de 2015
**Contenido nuevo**
* [Configuración de directivas de configuración de Mac OS X en Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx): cómo controlar la configuración de dispositivo y las características de dispositivos Mac OS X.
* [Configuración de directivas personalizadas de Mac OS X en Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx): cómo implementar configuraciones de dispositivos Mac OS X que creó mediante la herramienta Apple Configurator.
* [Configurar directivas de aplicaciones de prevención de pérdida de datos con Microsoft Intune](https://technet.microsoft.com/library/mt627825.aspx): contiene información sobre los escenarios que admiten las directivas de administración de aplicaciones móviles y cómo funciona la directiva a fin de proteger los datos.
* [Introducción a las directivas de administración de aplicaciones móviles en el portal de Azure](https://technet.microsoft.com/library/mt627830.aspx): lo que necesita para empezar a usar el Portal de vista previa de Azure para las directivas de administración de aplicaciones móviles.
* [Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx): contiene un tutorial paso a paso donde se explica cómo crear directivas de administración de aplicaciones móviles en el Portal de vista previa de Azure.
* [Supervisión de directivas de administración de aplicaciones móviles con Microsoft Intune](https://technet.microsoft.com/library/mt627824.aspx): se incluye información sobre cómo puede supervisar las directivas de administración de aplicaciones móviles mediante el Portal de vista previa de Azure.
* [Directivas de administración de aplicaciones móviles de Microsoft Intune y característica Open In de iOS](https://technet.microsoft.com/library/mt627821.aspx): información sobre cómo funcionan las directivas de administración de aplicaciones móviles con la característica Open In de iOS.
* [Experiencia del usuario final para aplicaciones asociadas con directivas de administración de aplicaciones móviles de Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx): se describe la experiencia del usuario final cuando se usan aplicaciones asociadas con directivas de administración de aplicaciones móviles.
* [Borrar los datos administrados de la aplicación de la empresa con Microsoft Intune](https://technet.microsoft.com/library/mt627826.aspx): cómo se pueden quitar datos de la aplicación de empresa.

**Contenido actualizado**
* [Configuración de directivas de configuración de Windows 10 en Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx): se han agregado nuevas características del explorador Edge.
* [Configurar la administración de iOS con Microsoft Intune](http://technet.microsoft.com/library/dn408185.aspx): se ha agregado información sobre cómo inscribir dispositivos Mac OS X.
* [Supervisar dispositivos móviles con Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx): se ha agregado información sobre el inventario recopilado a partir de dispositivos Mac OS X. Además, se ha actualizado el tema con la información más reciente de todas las plataformas de dispositivo.
* [Comprender las operaciones de Microsoft Intune mediante informes](https://technet.microsoft.com/library/dn646977.aspx): se ha agregado información sobre los dos nuevos informes que se usan para mostrar información sobre los dispositivos de Mac OS X administrados.
* [Administrar directivas de cumplimiento del dispositivo de Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx): se ha agregado información sobre las nuevas directivas de cumplimiento para requerir actualizaciones automáticas y el requisito de contraseña cuando un dispositivo vuelve de estado de inactividad.
* [Administrar acceso al correo electrónico con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx): se ha agregado información sobre la capacidad de aplicar la directiva de acceso condicional a todos los usuarios y plataformas.
* [Administrar el acceso a SharePoint Online con Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx): se ha agregado información sobre la capacidad de aplicar la directiva de acceso condicional a todos los usuarios y plataformas.

## Octubre de 2015

### Actualizaciones para el acceso condicional de Exchange local
**Ahora puede permitir el acceso al correo electrónico de Exchange Active Sync para dispositivos compatibles inscritos en Intune cuando la regla de Exchange global está establecida en bloquear o poner en cuarentena** Hasta ahora, para permitir el acceso al correo electrónico en dispositivos inscritos y compatibles, era necesario establecer la regla de Exchange global predeterminada en **Permitir**.

Con esta actualización de servicio, esta configuración ya no es un requisito necesario para el acceso condicional. Si su entorno de Exchange requiere que la regla global predeterminada se establezca en **Bloqueo/cuarentena**, solo debe marcar la casilla **Invalidación de la regla predeterminada** en la página de directivas de acceso condicional de Exchange local. En el tema [Administrar acceso al correo electrónico con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) se incluyen más detalles sobre las reglas y las notificaciones del usuario final resultantes.

**Nueva experiencia de cuarentena de un clic** Se ha simplificado la experiencia de cuarentena del correo electrónico para que pueda realizar la inscripción con un solo clic. Con esta actualización de servicio, los usuarios finales pueden hacer clic en un solo vínculo del correo electrónico de cuarentena para completar el proceso de inscripción dentro de la aplicación Portal de empresa.
### Actualizaciones de administración de dispositivos y aplicaciones móviles
**Android** Todas las características de administración de Intune ahora admiten Android 6.0 (Marshmallow) tal y como se describe en esta entrada de blog: [Microsoft Intune Provides Day 0 Support for Android Marshmallow](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx) (Microsoft Intune ofrece compatibilidad de día 0 para Android Marshmallow).

**iOS** Ya no podrá crear nuevas implementaciones de aplicaciones para dispositivos que ejecuten versiones anteriores a iOS 7.1. Cualquier implementación de aplicaciones que se realice en dispositivos que ejecuten una versión anterior a iOS 7.1, seguirá funcionando e Intune se encargará de administrarlas.

**Windows 10** Intune ahora admite la implementación de aplicaciones universales de Windows 10 mediante el tipo de instalador de software de **paquete de aplicaciones de Windows**. Para conocer los detalles y requisitos, vea [Get started with app deployment in Microsoft Intune (Introducción a la implementación de aplicaciones en Microsoft Intune)](http://technet.microsoft.com/en-US/library/dn646955.aspx).


### Cambios y actualizaciones para las aplicaciones del Portal de empresa de Microsoft
Los siguientes cambios se han realizado en las aplicaciones de portal de empresa en esta versión: **iOS** Los nuevos botones se han agregado a la aplicación de portal de empresa para facilitar a los usuarios el envío de registros de diagnóstico a sus administradores de TI:

|Nombre del botón|Dónde aparece|
|------------|---------------|
|Informe|Mensajes de alerta de error|
|Enviar informe de diagnóstico|Acerca de la pantalla de la aplicación Portal de empresa|



## Septiembre de 2015
### Actualizaciones de administración de dispositivos y aplicaciones móviles
**Todas las características de administración de iOS de Intune ahora son compatibles con iOS 9** Para obtener detalles sobre las capacidades de administración de iOS 9, consulte [esta entrada de blog](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx).

**Nueva directiva de configuración de aplicaciones móviles para iOS** Use la nueva directiva de configuración de aplicaciones móviles para proporcionar automáticamente aquellas opciones que una aplicación de iOS podría necesitar al ejecutarse. Por ejemplo, podría proporcionar un puerto de red o un nombre de usuario. Para conocer los detalles, consulte [Configurar aplicaciones con directivas de configuración de aplicaciones móviles en Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx).

**Administración de aplicaciones más fácil para los usuarios de iOS 9**
 En esta versión, puede hacer que aplicaciones ya implementadas se administren mediante Intune en el caso de los usuarios de iOS 9. En cuanto a las versiones anteriores de iOS, cuando implemente una aplicación y en el dispositivo ya esté instalada una versión no administrada de la aplicación, tendrá que solicitar al usuario que desinstale manualmente la aplicación para que Intune pueda instalar la aplicación administrada.

 Sin embargo, a partir de esta versión de Intune, es posible solicitar a los usuarios de dispositivos iOS 9 que permitan que Intune se ocupe de la administración de la aplicación y aplique las directivas de administración pertinentes de la aplicación móvil.

 **Administración de Windows 10** Use la nueva [directiva de configuración general de Windows 10](https://technet.microsoft.com/library/mt404697.aspx) para configurar la contraseña, el dispositivo, el explorador y otras opciones de los dispositivos inscritos que ejecutan Windows 10 y Windows 10 Mobile.

 **Crear e implementar aplicaciones en dispositivos de Windows 10 inscritos** El nuevo tipo de instalador de software, Windows Installer mediante MDM (&#42;.msi), le permite crear e implementar aplicaciones de Windows Installer en dispositivos inscritos que ejecutan Windows 10. Para conocer los detalles, consulte [Introducción a la implementación de aplicaciones en Microsoft Intune](https://technet.microsoft.com/library/dn646955.aspx).

### Cambios y actualizaciones para las aplicaciones del Portal de empresa de Microsoft
Los siguientes cambios se realizaron en las aplicaciones de portal de empresa en esta versión:

**iOS**
* Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso del portal de empresa para mejorar sus productos y servicios. Los usuarios finales pueden desactivar la recopilación de datos mediante la opción Datos de uso en su dispositivo, pero los administradores no tienen ningún control sobre la recopilación de datos y no pueden cambiar la configuración que el usuario final seleccione.
* Compatibilidad con la resolución de pantalla completa en iPhone 6 y 6 Plus
* Se han corregido errores para mejorar la seguridad

### Novedades de la documentación de Intune: septiembre de 2015
**Temas nuevos**

|Nombre|Detalles|
|----|--------|
|[Configuración de directivas de configuración de Windows 10 en Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx)|Se trata de una nueva directiva de configuración que le permite administrar la configuración y las características de los dispositivos que ejecutan Windows 10 y Windows 10 Mobile.
| [Configurar aplicaciones con directivas de configuración de aplicaciones móviles en Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx)|Este nuevo tipo de directiva le permite proporcionar automáticamente la configuración que podría ser necesaria cuando el usuario ejecuta una aplicación de iOS. |

**Temas actualizados**

|Nombre|Detalles|
|----|-------|
|[Usar directivas para administrar equipos y dispositivos móviles con Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx)|Se ha actualizado para incluir la información más reciente que le será de ayuda para entender y crear directivas.|

## Agosto de 2015
### Actualizaciones de administración de dispositivos y aplicaciones móviles
* Los**términos y condiciones** para la inscripción en Intune y el acceso a la compañía [se administran ahora mediante directivas](https://technet.microsoft.com/library/mt405893.aspx). Puede destinar conjuntos de términos y condiciones diferentes a grupos de usuarios que deben cumplir requisitos específicos. Por ejemplo, puede implementar términos y condiciones en distintos idiomas en grupos de usuarios delimitados geográficamente. También puede [editar los términos y condiciones](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) y especificar si desea incrementar los números de la versión, requiriendo así que los usuarios acepten los nuevos términos y condiciones para poder usar el portal de empresa.
* **Se cambió el nombre a una serie de directivas de Intune** para que sean más coherentes en todo el producto y más fáciles de buscar. Para ver una lista de todas las directivas de Intune disponibles, consulte [Uso de directivas para administrar equipos y dispositivos móviles con Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx).
* Los **perfiles de certificado PKCS #12 (.PFX)** están disponibles para Android 4.0 y versiones posteriores, así como para Windows 10 (escritorio y móvil) y versiones posteriores. No es necesario un servidor NDES para usar .PFX. Aprenda cómo usar perfiles de certificados .PFX en [Habilitar el acceso a los recursos de empresa mediante perfiles de certificados con Microsoft Intune](http://technet.microsoft.com/library/dn818904.aspx).
* **La configuración de los límites corporativos para dispositivos móviles y de escritorio de Windows 10** habilita la configuración de VPN granular, como se describe en [Ayudar a los usuarios a conectarse a su trabajo con perfiles de VPN con Microsoft Intune](https://technet.microsoft.com/library/dn818905.aspx).
* **La aplicación OneDrive para Android ahora admite varias identidades**. Esta y otras actualizaciones a las directivas de administración de aplicaciones móviles se describen en la [lista de aplicaciones de Microsoft que puede administrar](https://technet.microsoft.com/library/dn708489.aspx).
* **Bypass del bloqueo de activación de iOS**. Si los dispositivos iOS corporativos están protegidos con el bloqueo de activación, para poder borrarlos o volver a activarlos, debe escribir el identificador y la contraseña de Apple del usuario. Esto puede suponer un desafío cuando los usuarios dejan la empresa y devuelven un dispositivo corporativo sin desactivar el bloqueo de activación. Para obtener ayuda para resolver este problema, puede usar el [bypass del bloqueo de activación de Intune](https://technet.microsoft.com/library/mt414176.aspx).

### Acceso condicional para equipos
Ahora puede configurar directivas de acceso condicional para equipos. Esto permite a las aplicaciones de escritorio de Office tener acceso a los servicios de Exchange Online y SharePoint Online.
Para habilitar la directiva de acceso condicional para equipos, el equipo debe estar unido al dominio o ser compatible.
* Consulte la sección **Introducción** del tema [Administrar el acceso al correo electrónico y SharePoint con Microsoft Intune](http://technet.microsoft.com/library/dn818907) a fin de ver una lista completa de requisitos para habilitar el acceso condicional a los equipos.
* Consulte [Administrar acceso al correo electrónico con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) para conocer las opciones que puede establecer para habilitar el acceso condicional en el acceso al correo electrónico.
* Consulte [Administrar el acceso a SharePoint Online con Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx) para conocer las opciones que puede establecer para habilitar el acceso condicional en el acceso para SharePoint Online.

### Cambios y actualizaciones para las aplicaciones del Portal de empresa de Microsoft
Los siguientes cambios se realizaron en las aplicaciones de portal de empresa en esta versión:

**Android**

Los usuarios verán las instrucciones de inscripción de dispositivos después de iniciar sesión si todavía no han inscrito el dispositivo para su administración.

### Novedades de la documentación de Intune: agosto de 2015
**Temas nuevos**

|Título|Detalles|
|-----|-------|
|[Ayudar a proteger dispositivos iOS con el bypass del bloqueo de activación para Microsoft Intune](https://technet.microsoft.com/library/mt414176.aspx)|Obtenga información sobre cómo puede usar Intune para realizar el bypass del bloqueo de activación de iOS cuando un usuario abandona la empresa y devuelve un dispositivo bloqueado.|

**Temas actualizados**

|Título|Detalles|
|-----|-------|
|[Aplicaciones de Microsoft que puede utilizar con las directivas de administración de aplicaciones móviles de Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx)|Actualizado con la información más reciente sobre las aplicaciones que puede administrar con directivas de administración de aplicaciones móviles.
|[Usar directivas para administrar equipos y dispositivos móviles con Microsoft Intune](http://technet.microsoft.com/library/dn743712.aspx)|Actualizado con las directivas más recientes agregadas a Intune.|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Jul16_HO4-->


