---
# required metadata

title: Novedades de archivo | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


## Septiembre de 2015
### Actualizaciones de administración de dispositivos y aplicaciones móviles
**Todas las características de administración de iOS de Intune ahora admiten iOS 9**
Para conocer los detalles sobre las funcionalidades de administración de iOS 9, consulte [esta publicación de blog](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx)..

**Nueva directiva de configuración de aplicaciones móviles para iOS**
Use la nueva directiva de configuración de aplicaciones móviles para proporcionar automáticamente la configuración que una aplicación de iOS podría necesitar al ejecutarse. Por ejemplo, podría proporcionar un puerto de red o un nombre de usuario. Para conocer los detalles, consulte [Configurar aplicaciones con directivas de configuración de aplicaciones móviles en Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx)..

**Administración de aplicaciones más sencilla para los usuarios de iOS 9**
 En esta versión, puede hacer que las aplicaciones ya implementadas se administren mediante Intune en el caso de los usuarios de iOS 9. En cuanto a las versiones anteriores de iOS, cuando implemente una aplicación y en el dispositivo ya esté instalada una versión no administrada de la aplicación, tendrá que solicitar al usuario que desinstale manualmente la aplicación para que Intune pueda instalar la aplicación administrada.

 Sin embargo, a partir de esta versión de Intune, es posible solicitar a los usuarios de dispositivos iOS 9 que permitan que Intune se ocupe de la administración de la aplicación y aplique las directivas de administración pertinentes de la aplicación móvil.

 **Administración de Windows 10** Use la nueva [directiva de configuración general de Windows 10](https://technet.microsoft.com/library/mt404697.aspx) para configurar la contraseña, el dispositivo, el explorador y otras opciones de los dispositivos inscritos que ejecutan Windows 10 y Windows 10 Mobile.

 **Crear e implementar aplicaciones en dispositivos de Windows 10 inscritos** El nuevo tipo de instalador de software, Windows Installer mediante MDM (&#42;.msi), le permite crear e implementar aplicaciones de Windows Installer en dispositivos inscritos que ejecutan Windows 10. Para conocer los detalles, consulte [Get started with app deployment in Microsoft Intune (Introducción a la implementación de aplicaciones en Microsoft Intune)](https://technet.microsoft.com/library/dn646955.aspx)..

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
* **Se cambió el nombre a una serie de directivas de Intune** para que sean más coherentes en todo el producto y más fáciles de buscar. Para ver una lista de todas las directivas de Intune disponibles, consulte [Use policies to manage computers and mobile devices with Microsoft Intune (Usar directivas para administrar equipos y dispositivos móviles con Microsoft Intune)](https://technet.microsoft.com/library/dn743712.aspx)..
* Los **perfiles de certificado PKCS #12 (.PFX)** están disponibles para Android 4.0 y versiones posteriores, así como para Windows 10 (escritorio y móvil) y versiones posteriores. No es necesario un servidor NDES para usar .PFX. Aprenda cómo usar perfiles de certificados .PFX en [Habilitar el acceso a los recursos de empresa mediante perfiles de certificados con Microsoft Intune](http://technet.microsoft.com/library/dn818904.aspx).
* **La configuración de los límites corporativos para dispositivos móviles y de escritorio de Windows 10** habilita la configuración de VPN granular, como se describe en [Ayudar a los usuarios a conectarse a su trabajo con perfiles de VPN con Microsoft Intune](https://technet.microsoft.com/library/dn818905.aspx).
* **La aplicación OneDrive para Android ahora admite varias identidades**. Esta y otras actualizaciones a las directivas de administración de aplicaciones móviles se describen en la [lista de aplicaciones de Microsoft que puede administrar](https://technet.microsoft.com/library/dn708489.aspx)..
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


<!--HONumber=May16_HO1-->


