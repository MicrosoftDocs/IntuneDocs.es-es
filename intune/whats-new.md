---
title: Novedades de Microsoft Intune
titleSuffix: Intune on Azure
description: Descubra las novedades del portal de Intune Azure
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 77f433037e4e576b29cf5800e9666008300ce568
ms.sourcegitcommit: 3d1ec7a68977e6f5727821366ffd25657b459818
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/26/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Conozca las novedades semanales de Microsoft Intune. También podrá obtener información sobre los [próximos cambios](#whats-coming), [notificaciones importantes](#notices) sobre el servicio e información sobre las [versiones anteriores](whats-new-archive.md).

> [!Note]
> Muchas de estas características finalmente serán compatibles con las implementaciones híbridas con Configuration Manager. Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   


## <a name="week-of-august-21-2017"></a>Semana del 21 de agosto de 2017

### <a name="device-enrollment"></a>Inscripción de dispositivos
#### <a name="improvements-to-device-overview----1404453---"></a>Mejoras en la información general de dispositivos <!-- 1404453 -->  
La información general de dispositivos ahora muestra los que están inscritos, pero excluye a los que administra Exchange ActiveSync. Los dispositivos de Exchange ActiveSync no ofrecen las mismas opciones de administración que los inscritos. Para ver el número de dispositivos inscritos y el de dispositivos inscritos por plataforma en la sección Intune de Azure Portal, vaya a **Dispositivos** > **Información general**.

### <a name="device-management"></a>Administración de dispositivos
#### <a name="improvements-to-device-inventory-collected-by-intune"></a>Mejoras en el inventario de dispositivos recopilado mediante Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
En esta versión, hemos realizado las mejoras siguientes en la información del inventario que recopilan los dispositivos que administra:
 
-   En dispositivos Android, ahora puede agregar una columna al inventario de dispositivos que muestra el nivel de revisión más reciente de cada uno. Agregue la columna **Nivel de revisión de seguridad** a la lista de dispositivos para verlo.
-   Al filtrar la vista de dispositivos, podrá filtrarlos según su fecha de inscripción. Por ejemplo, puede mostrar solo los dispositivos que se hayan inscrito después de una fecha específica.
-   Hemos realizado mejoras en el filtro que usa el elemento **Ultima fecha de inserción**.
-   En la lista de dispositivos, ahora puede mostrar el número de teléfono de los dispositivos corporativos.
Además, puede usar el panel de filtros para buscar dispositivos por el número de teléfono.
 
Para obtener más información sobre el inventario de dispositivos, consulte [Visualización del inventario de dispositivos de Intune](device-inventory.md).

#### <a name="conditional-access-support-for-mac-devices"></a>Compatibilidad del acceso condicional con dispositivos Mac 
<!-- 720172 -->
Ya puede establecer una directiva de acceso condicional que exija que los dispositivos Mac se inscriban en Intune y cumplan las directivas de cumplimiento de dispositivos. Por ejemplo, los usuarios pueden descargar la aplicación Portal de empresa de Intune para macOS e inscribir los dispositivos Mac en Intune. Intune evalúa si el dispositivo Mac es conforme o no con requisitos como el PIN, el cifrado, la versión del sistema operativo y la integridad del sistema.

#### <a name="new-device-restriction-settings-for-windows-10"></a>Nueva configuración de restricciones de dispositivos para Windows 10    
<!--1063965, 1308850  -->
En esta versión, hemos agregado nuevas opciones para el [perfil de restricción de dispositivos Windows 10](/intune/device-restrictions-windows-10) en las categorías siguientes:

-   SmartScreen de Windows Defender
-   Tienda de aplicaciones

#### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Actualizaciones en el perfil de dispositivo de Endpoint Protection de Windows 10 para la configuración de BitLocker
<!--1459533 -->    
En esta versión, hemos realizado las mejoras siguientes al funcionamiento de la configuración de BitLocker en un perfil de dispositivo de Endpoint Protection de Windows 10:
 
En **Configuración de BitLocker para unidades de sistema operativo**, en el ajuste **BitLocker con un chip TPM no compatible** BitLocker estaba permitido tras seleccionar **Bloquear**. Se ha corregido este problema para poder bloquear BitLocker cuando se selecciona.
En **Configuración de BitLocker para unidades de sistema operativo**, en el ajuste **Agente de recuperación de datos basada en certificado**, ya puede bloquear explícitamente el agente de recuperación de datos basada en certificado. De forma predeterminada, el agente está permitido.
En **Configuración de BitLocker para unidades de datos fijas**, en el ajuste **Agente de recuperación de datos**, ya puede bloquear explícitamente el agente de recuperación de datos.
Para obtener más información, vea [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Configuración de Endpoint Protection para Windows 10 y versiones posteriores).


### <a name="app-management"></a>Administración de aplicaciones
#### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nueva experiencia de sesión iniciada para los usuarios del portal de empresa de Android y para los usuarios de la directiva de protección de aplicaciones <!-- 621669 -->
Los usuarios finales ya pueden examinar aplicaciones, administrar dispositivos y ver la información de contacto de TI con la aplicación Portal de empresa de Android sin inscribir sus dispositivos Android. Además, si un usuario final ya usa una aplicación protegida mediante las directivas de Intune App Protection e inicia el portal de empresa de Android, el usuario final ya no recibirá una solicitud para inscribir el dispositivo.

#### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Compatibilidad con varias identidades en OneNote para iOS      <!-- 1234281 -->
Los usuarios finales ahora pueden usar cuentas diferentes (profesionales o educativas) en Microsoft OneNote para iOS. Las directivas de protección de aplicaciones se pueden aplicar a los datos corporativos en blocs de notas del trabajo sin que esto afecte a sus blocs de notas personales. Por ejemplo, una directiva puede permitir que un usuario busque información en blocs de notas del trabajo, pero impedir que copie datos corporativos desde un bloc de notas del trabajo a uno personal.
 
- Obtenga más información sobre las aplicaciones que admiten [protección de aplicaciones y varias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.




## <a name="notices"></a>Notificaciones

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Actualización de direcciones IP para Intune <!-- 1175274 -->
Hay una [lista actualizada de nombres DNS y direcciones IP](/intune/network-bandwidth-use) disponibles para la configuración de proxy del firewall.

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Uso de Azure Active Directory para acceso condicional <!-- 967947 -->
El acceso condicional está disponible en la sección Azure Active Directory de la consola de Azure y proporciona un marco más eficaz y flexible para establecer directivas de aplicaciones en la nube como Office 365 Exchange Online y SharePoint Online.  Use la hoja **Acceso condicional en Azure Active Directory** para configurar directivas en lugar de la consola de Intune clásica. Es necesario volver a crear las directivas existentes de la consola de Intune clásica en la consola de Azure. Para obtener más información, consulte [Creación de directivas de acceso condicional de Azure AD](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->
Para las cuentas de Intune creadas después de enero de 2017, Intune habilitó el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en Azure Portal. Anteriormente, la vista previa de inscripción de Apple solo era accesible desde los vínculos al portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requieren una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a Azure Portal.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Roles de administración que se reemplazan en el Portal de Azure
Los roles de administración de aplicaciones móviles (MAM) existentes (colaborador, propietario y de solo lectura) usados en el portal clásico de Intune (Silverlight) se reemplazan por un conjunto completo de nuevos controles de administración basada en roles (RBAC) en el Portal de Intune Azure. Cuando haya migrado a Azure Portal, tendrá que reasignar estos nuevos roles de administración a los administradores. Para obtener más información sobre RBAC y los nuevos roles, vea [Roles de Intune (RBAC) para Microsoft Intune](/intune/role-based-access-control).



## <a name="whats-coming"></a>Próximas novedades

### <a name="end-of-support-for-ios-80----1164477---"></a>Fin de la compatibilidad con iOS 8.0 <!---1164477--->
Las aplicaciones administradas y la aplicación Portal de empresa para iOS exigirán iOS 9.0 y versiones posteriores para acceder a recursos de empresa. Los dispositivos que no estén actualizados antes de septiembre de este año ya no podrán acceder a esas aplicaciones ni al Portal de empresa. 

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Actualizaciones de la interfaz de usuario en el sitio web del portal de empresa <!--1313244 part 2-->
__Actualizaciones de aplicaciones destacadas__  
Hemos agregado una página dedicada al sitio donde los usuarios pueden buscar aplicaciones que ha decidido presentar, y hemos realizado algunos ajustes a la interfaz de usuario de la sección Destacado en la página principal. Puede ver el aspecto de estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fin de la compatibilidad con Android 4.3 y anterior <!---1171127, 1326920 --->
Las aplicaciones administradas y la aplicación Portal de empresa para Android exigirán Android 4.4 y versiones posteriores para acceder a recursos de empresa. Los dispositivos que no estén actualizados antes del comienzo de octubre ya no podrán acceder a esas aplicaciones ni al Portal de empresa. En diciembre, todos los dispositivos inscritos serán eliminados, lo que provocará su pérdida de acceso a los recursos de empresa. Si está usando directivas de protección de aplicaciones sin MDM, las aplicaciones no recibirán actualizaciones y la calidad de su experiencia empeorará con el tiempo.


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>Recordatorio sobre el soporte técnico para la plataforma: el soporte técnico estándar para Windows Phone 8.1 finalizó el 11 de julio de 2017
<!-- 1327781 -->
El 11 de julio de 2017, la plataforma Windows Phone 8.1 llegó a la finalización del soporte técnico estándar. La compatibilidad de los equipos Windows 8.1 no se verá afectada.

No hay ningún impacto inmediato en ningún dispositivo Windows Phone 8.1 administrado por el servicio Intune. Los dispositivos inscritos continuarán funcionando y todas las directivas, configuraciones y aplicaciones seguirán funcionando según lo previsto. Tenga en cuenta que no hay mejoras destinadas a la plataforma Windows Phone 8.1 en el servicio Intune ni para la aplicación Portal de empresa de Windows Phone 8.1.

Se recomienda que actualice los dispositivos Windows Phone 8.1 aptos a Windows 10 Mobile en cuanto pueda. 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Cambios en la compatibilidad de la aplicación de portal de empresa de iOS de Intune <!-- 1164474  -->
Próximamente, habrá una nueva versión de la aplicación de portal de empresa de Microsoft Intune para iOS que solo admitirá dispositivos que ejecuten iOS 9.0 o posterior. La versión del portal de empresa que admite iOS 8 todavía estará disponible durante un período de tiempo muy breve. En cambio, tenga en cuenta que si también usa aplicaciones iOS habilitadas para MAM, se admiten iOS 9.0 y versiones posteriores, por lo que querrá asegurarse de que sus usuarios finales actualicen al sistema operativo más reciente. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Le informamos de esto con antelación, incluso cuando no tenemos fechas específicas, para que tenga tiempo para planear. Asegúrese de que sus usuarios hayan actualizado a iOS 9 o versiones posteriores y, cuando se publique la aplicación Portal de empresa, solicite a sus usuarios finales que la actualicen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Anime a los usuarios a que actualicen a iOS 9.0 o posterior para aprovechar las nuevas características de Intune.  Anime a los usuarios a que instalen la última versión del portal de empresa y se aprovechen de las nuevas características que ofrecerá.

Vaya a Intune en Azure Portal y vea Dispositivos > Todos los dispositivos y filtre por la versión de iOS para ver cualquier dispositivo actual con sistemas operativos anteriores a iOS 9.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->
Apple ha anunciado que se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS.

Hay disponible una versión de la aplicación Portal de empresa para iOS a través del programa Apple TestFlight que aplica los nuevos requisitos de ATS. Si desea probarla para que pueda experimentar el cumplimiento de ATS, envíe un correo electrónico a <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con su nombre, apellidos, dirección de correo electrónico y nombre de la empresa. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades de la interfaz de usuario del portal de empresa](whats-new-app-ui.md)
* [Novedades de los meses anteriores](whats-new-archive.md)
