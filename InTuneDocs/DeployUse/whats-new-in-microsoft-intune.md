---
title: Novedades | Microsoft Intune
description: Conozca las novedades de este mes y las versiones anteriores de Microsoft Intune
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c636efee82331d6feac75153b872526f7af7c882
ms.openlocfilehash: 814312b0ac6055ffff2efad2ddbdaa8664f84fde


---

# Novedades de Microsoft Intune
Novedades en esta versión de Microsoft Intune. También puede comprobar los próximos cambios que pueda planear, así como información sobre las versiones anteriores.

Todas estas funciones se admitirán finalmente para las implementaciones de los clientes híbridos (Configuration Manager con Intune). Para obtener más información sobre las nuevas funciones híbridas, consulte nuestra [página Novedades](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

>[!IMPORTANT] 
>Entrada de blog: Garantía de que los dispositivos móviles están actualizados con Microsoft Intune<br>
>A la luz de los ataques de malware "Trident" recientes en dispositivos iOS, hemos publicado una nueva entrada de blog, [Garantía de que los dispositivos móviles están actualizados con Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) para conocer las distintas formas en las que Intune puede ayudar a proteger y mantener actualizados sus dispositivos.

## Septiembre de 2016

## Actualizaciones del Portal de empresa
### Android

**Adición de "Notificaciones" en el Portal de empresa para Android**

Se ha agregado un nuevo icono Notificaciones al Portal de empresa para Android en la página principal. Al seleccionar este icono se obtiene acceso a la página Notificaciones, que muestra a todos los usuarios todos los elementos que requieren atención en la aplicación del Portal de empresa, como la falta de conformidad del dispositivo, la actualización de la inscripción o la activación de la inscripción. La aplicación del Portal de empresa de iOS ya tiene esta experiencia en notificaciones. Tener la nueva página Notificaciones significa que el usuario no verá la página Configuración de acceso de la empresa cada vez que inicien o reanuden el Portal de empresa siempre que el dispositivo ya esté inscrito. Si crea su propia guía de usuario final, es posible que quiera actualizar la documentación para reflejar este cambio. Busque las capturas de pantalla actualizadas [aquí](https://aka.ms/androidcpupdate).  
<!---TFS 1095560--->

### Windows
**Botón de comentarios agregado a la aplicación de Portal de empresa de Windows Phone 8.1**

La aplicación de Portal de empresa de Windows Phone 8.1 permite a los usuarios finales pueden enviar comentarios acerca de la aplicación mediante un nuevo botón "Enviar comentarios". Para buscar el botón, los usuarios seleccionan el menú de "tres puntos" en la parte inferior derecha de la pantalla de la aplicación de Portal de empresa y, a continuación, seleccionan **Enviar comentarios**. Los comentarios recopilados y anónimos ayudarán a Microsoft a mejorar la experiencia de la aplicación del Portal de empresa para los usuarios.
<!---TFS 1317806--->

## Agosto de 2016
## Administración de aplicaciones
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### Aplicaciones ocultas y visibles para iOS 9.3
Para dispositivos supervisados con iOS 9.3 o posterior, puede usar la lista de aplicaciones ocultas y visibles en la directiva de configuración general de iOS para:
- Especificar una lista de aplicaciones que se ocultará a los usuarios. Los usuarios no pueden ver o iniciar estas aplicaciones.
- Especificar una lista de aplicaciones que los usuarios pueden ver e iniciar. No se pueden ver o iniciar otras aplicaciones.

Las aplicaciones que puede especificar incluyen las dos aplicaciones que ha implementado y las aplicaciones de iOS incorporadas como Mensajes y Notas. Para más información, va [Configuración de directivas de iOS en Microsoft Intune]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
### Directiva de aplicaciones permitidas y bloqueadas para dispositivos Samsung KNOX
Ahora puede configurar una directiva personalizada para dispositivos Samsung KNOX que le permite crear uno de los siguientes elementos:
- Una lista de aplicaciones para las que se ha bloqueado la ejecución en el dispositivo. Aunque esté instalada, una aplicación definida en la lista bloqueada no puede activarse en el dispositivo.
- Una lista de aplicaciones que los usuarios del dispositivo pueden instalar desde la tienda de Google Play. No se pueden instalar otras aplicaciones de la tienda.

Esta configuración solo pueden usarla dispositivos que ejecutan Samsung KNOX.
Para más información, vea [Uso de directivas personalizadas para permitir y bloquear aplicaciones para dispositivos Samsung KNOX]( custom-policy-to-allow-and-block-samsung-knox-apps.md).
<!---TFS 1311629 checked --->
### Nuevas aplicaciones compatibles con directivas de administración de aplicaciones móviles (MAM)
La aplicación de Yammer para [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) y [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) ahora es compatible con [directivas de administración de aplicaciones móviles (MAM) de Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), independientemente de que el dispositivo esté inscrito.

Para obtener una lista completa de aplicaciones compatibles MAM, vea el sitio de [partners de aplicaciones de Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### Aplicaciones del visor de Intune
Con el lanzamiento de la nueva aplicación para uso compartido de RMS, estamos quitando las siguientes aplicaciones del visor de Intune, a partir de agosto de 2016:
- Visor de AV de Intune
- Visor de PDF de Intune
- Visor de imágenes de Intune para Android de Google Play

En lugar de utilizar las aplicaciones de visor de Intune, se recomienda usar la nueva [aplicación de administración de derechos (uso compartido de RMS) para Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), que le permite implementar una aplicación en lugar de tres aplicaciones independientes para ver de forma segura archivos corporativos en dispositivos Android. Cuando ya no se admita la aplicación del visor de Intune, se quitará de la Tienda de Google y no estará disponible para su uso futuro.

## Administración de dispositivos
### Compatibilidad con Android 7.0
Intune proporciona compatibilidad desde el principio para el próximo sistema operativo Android 7.0 para dispositivos móviles.
<!---TFS 1262053--->
### Eliminación de Google de la capacidad de restablecimiento del código de acceso remoto en dispositivos Android 7.0
Google está quitando la capacidad de los administradores de TI y usuarios finales de restablecer el código de acceso de dispositivos Android 7.0 de forma remota. Anteriormente, los administradores de TI podían restablecer remotamente la el código de acceso de un usuario y los usuarios finales podrían restablecer sus códigos de acceso desde el sitio web de Portal de empresa.



## Actualizaciones del Portal de empresa
### sitio web del Portal de empresa
- **Vínculo de comentarios del Portal de empresa a Microsoft** <br/>
El sitio web de Portal de empresa permite a los usuarios finales seleccionar un nuevo vínculo "Comentarios", en la parte inferior de la página, para enviar comentarios a Microsoft acerca de su experiencia con el sitio. Los comentarios recopilados y anónimos ayudarán a Microsoft a mejorar la experiencia del sitio web del Portal de empresa para usuarios.
<!--- TFS 1313657 checked--->

### iOS
- **Versión mínima del explorador administrado de iOS a 8.0**<br/>
La aplicación del explorador administrado de Microsoft Intune para iOS se actualizó para admitir los dispositivos que ejecutan iOS 8.0 o posterior. Aunque los dispositivos iOS 7.1 pueden seguir usando la aplicación del explorador administrado existente, asegúrese de que los usuarios actualizan a iOS 8.0 o superior para acceder a las nuevas funciones de explorador administrado y aprovecharlas al máximo.  
<!---TFS 1313253 checked--->

## Próximas novedades

### Compatibilidad con iOS 10
Intune será totalmente compatible con iOS 10. La versión pública de iOS 10 proporcionará más información.

### Transición de grupos de Intune a Azure Active Directory a partir de septiembre de 2016
Intune está creando una nueva experiencia de administración de grupos que usa grupos de seguridad de Azure Active Directory (AAD) como grupos de usuarios y dispositivos en Intune. Estos grupos se usarán para toda la administración de grupos, implementación de directivas e implementación de perfiles **cuando presentemos el nuevo portal de administración de Intune basados en Azure**.

Esta nueva experiencia evitará que tenga que duplicar grupos entre servicios, **le permitirá obtener acceso a algunas nuevas funciones de grupo de Azure Active Directory Premium (AADP)**, y proporcionará extensibilidad con PowerShell y Graph. Esto también unificará la experiencia de administración de grupo a través de la administración de movilidad empresarial.

Para habilitar el movimiento a grupos de seguridad, la experiencia en la **consola de administración actual** experimentará algunas modificaciones. **Estos cambios y el uso de grupos de seguridad AAD se registrarán en la documentación de Intune**.

Los clientes nuevos en Intune verán **algunos de los cambios del grupo de seguridad antes de que lo puedan hacer los inquilinos actuales**.

Además de los cambios en la administración de grupos, **la siguiente funcionalidad dejará de utilizarse**:
- Excluir miembros o grupos al crear un nuevo grupo
- Grupos **Usuarios sin agrupar** y **Dispositivos sin agrupar**
- **Administrar grupos de** en el rol de administrador de servicio
- Alertas personalizadas basadas en grupos de reglas de notificación
- Dinamizar los grupos en informes
<!--- TFS 1295329--->

### Adición de "Notificaciones" en el Portal de empresa para Android
Vamos a lanzar una actualización en el Portal de empresa para Android en septiembre que incluirá un nuevo icono **Notificaciones** en la página principal. Al seleccionar este icono se obtendrá acceso a la página **Notificaciones**, que mostrará a todos los usuarios todos los elementos que requieren atención en la aplicación del Portal de empresa, como la falta de conformidad del dispositivo, la actualización de la inscripción o la activación de la inscripción. Si también utiliza la aplicación del Portal de empresa de iOS, ya verá la experiencia de notificaciones. Con la introducción de la página **Notificaciones**, no verá la página **Configuración de acceso de la empresa** cada vez que inicie o reanude el Portal de empresa para Android siempre que el dispositivo esté ya inscrito. Sabemos que muchos de vosotros habéis creado una guía de usuario final y que valoráis el aviso avanzado cuando la guía o las capturas de pantallas tienen que actualizarse. Actualice la documentación para reflejar el cambio siguiente en la experiencia. Busque las capturas de pantalla actualizadas aquí: https://aka.ms/androidcpupdate.  

### Mejoras en cómo los usuarios finales de iOS obtienen sus aplicaciones
Los siguientes cambios se realizan en septiembre en los iconos de aplicaciones en la aplicación del Portal de empresa para iOS para indicar a los usuarios distintas vistas en una única ubicación, el sitio web del Portal de empresa, para todas sus aplicaciones. Actualmente, las restricciones de Apple prohíben que las aplicaciones de tienda de aplicaciones administradas y de línea de negocio se muestren en la aplicación del Portal de empresa y requieren que los usuarios visiten diferentes vistas para buscar todas las aplicaciones.

- El icono **Aplicaciones de empresa** apunta actualmente a una lista de todas las aplicaciones en la pestaña TODOS del sitio web del Portal de empresa y seguirá funcionando de la misma forma. El nombre del icono cambiará a **Todas las aplicaciones**.
- El icono **Otras aplicaciones** actualmente apunta a una vista, dentro de la aplicación de Portal de empresa, que enumera todas las aplicaciones que Apple permite mostrar a la aplicación de Portal de empresa. El nombre del icono cambiará a **Aplicaciones destacadas** y si selecciona en el icono, se dirigirá a los usuarios a la pestaña DESTACADAS del sitio web del Portal de empresa.
-  El icono **Categorías** apunta actualmente a una vista, dentro de la aplicación del Portal de empresa, que incluye las categorías de aplicaciones. El nombre de icono no cambiará, pero ahora apuntará a la pestaña CATEGORÍAS del sitio web del Portal de empresa. Puede encontrar las capturas de pantalla actualizadas [aquí](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

### Guía básica de nube
Manténgase informado sobre los próximos desarrollos de Intune con la [Guía básica de la plataforma en la nube](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Degradación del servicio
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Cambios en la compatibilidad de la aplicación de Portal de empresa de iOS**<br/>
En septiembre, todos los usuarios de la aplicación de Portal de empresa de Microsoft Intune para iOS tendrán que utilizar la versión más reciente. Los nuevos usuarios solo podrán descargar la versión más reciente y será necesario actualizar para los usuarios actuales. La versión más reciente requiere iOS 8.0 o posterior, de modo que los dispositivos que ejecutan versiones anteriores de iOS no podrán usar el Portal de empresa o inscribirse hasta que actualicen su dispositivo a iOS 8.0 o posterior y, a continuación, actualicen la aplicación de Portal de empresa a la versión más reciente. Los dispositivos inscritos que ejecutan versiones anteriores a iOS 8.0 seguirán administrándose y apareciendo en la consola de administración de Intune.  

- **Versión mínima del explorador administrado de iOS a 8.0**<br/>
En agosto, Intune lanzará una aplicación de Microsoft Intune Managed Browser actualizada para iOS que solo admitirán los dispositivos con iOS 8.0 o posterior. Aunque los dispositivos iOS 7.1 podrán seguir usando la aplicación del explorador administrado existente, asegúrese de que los usuarios actualizan a iOS 8.0 o superior para acceder a las nuevas funciones de explorador administrado y aprovecharlas al máximo.  
<!---TFS 1313253--->

- **Las aplicaciones de Portal de empresa para Windows 8 y Windows Phone 8 están en desuso** <br/>
A partir de octubre de 2016, Microsoft Intune descartará el soporte técnico para aplicaciones del Portal de empresa para Windows 8 y Windows Phone 8. Microsoft Intune también descartará el soporte técnico para la plataforma de Windows Phone 8. Como consecuencia, no podrá inscribir o actualizar dispositivos de Windows Phone 8. Puede seguir administrando dispositivos de Windows Phone 8 y Windows 8 ya inscritos. Actualice dispositivos Windows Phone 8 y Windows 8 a Windows 8.1 y Windows Phone 8.1 y use las aplicaciones del Portal de empresa de Windows 8.1 y Windows Phone 8.1 correspondientes para seguir distribuyendo aplicaciones a estos dispositivos sin interrupciones.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->



## Versiones anteriores de Intune
Si desea ver lo que se ha publicado en Intune durante los últimos seis meses, vea el artículo [Versiones anteriores de Intune](previous-intune-releases.md).

### Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de la plataforma en la nube](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Sep16_HO2-->


