---
title: Novedades de Microsoft Intune en los meses anteriores
titlesuffix: Azure portal
description: "Revise los anuncios anteriores en la página de novedades de Intune"
keywords: 
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0d6513b570851473651fbfa38dbb4dc1b6c91036
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novedades de Microsoft Intune: meses anteriores

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="september-2017"></a>Septiembre de 2017

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informar a los usuarios finales de la información de dispositivo que puede verse para iOS <!--739894-->

Hemos agregado **Tipo de propiedad** a la pantalla Detalles del dispositivo en la aplicación del portal de empresa para iOS. Esto permitirá que los usuarios obtengan más información sobre la privacidad directamente en esta página de los documentos para el usuario final de Intune. También podrán encontrar esta información en la pantalla Acerca de.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que los usuarios finales accedan a la aplicación Portal de empresa para Android sin inscripción <!---1169910--->

Pronto los usuarios finales no tendrán que inscribir sus dispositivos para acceder a la aplicación Portal de empresa para Android. Los usuarios finales de las organizaciones que usen directivas de protección de aplicaciones dejarán de recibir mensajes para inscribir sus dispositivos cuando abran la aplicación Portal de empresa. Los usuarios finales también podrán instalar aplicaciones desde el Portal de empresa sin inscribir el dispositivo. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Expresión más fácil de entender para la aplicación de Portal de empresa para Android <!---1396349--->  

El proceso de inscripción para la aplicación de Portal de empresa para Android se ha simplificado con nuevo texto para que resulte más sencillo para los usuarios finales. Si tiene documentación de inscripción personalizada, deberá actualizarla para reflejar las pantallas nuevas. También puede encontrar imágenes de muestra en nuestra página [Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Adición de la aplicación de Portal de empresa de Windows 10 a la directiva de permiso de Windows Information Protection <!-- 677129 -->

La aplicación de Portal de empresa de Windows 10 se ha actualizado para admitir Windows Information Protection (WIP). La aplicación se puede agregar a la directiva de autorización de WIP. Con este cambio, la aplicación ya no tiene que agregarse a la lista **Excluir**.


## <a name="august-2017"></a>Agosto de 2017

### <a name="improvements-to-device-overview----1404453---"></a>Mejoras en la información general de dispositivos <!-- 1404453 -->  
La información general de dispositivos ahora muestra los que están inscritos, pero excluye a los que administra Exchange ActiveSync. Los dispositivos de Exchange ActiveSync no ofrecen las mismas opciones de administración que los inscritos. Para ver el número de dispositivos inscritos y el de dispositivos inscritos por plataforma en la sección Intune de Azure Portal, vaya a **Dispositivos** > **Información general**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Mejoras en el inventario de dispositivos recopilado mediante Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
En esta versión, hemos realizado las mejoras siguientes en la información del inventario que recopilan los dispositivos que administra:
 
-   En dispositivos Android, ahora puede agregar una columna al inventario de dispositivos que muestra el nivel de revisión más reciente de cada uno. Agregue la columna **Nivel de revisión de seguridad** a la lista de dispositivos para verlo.
-   Al filtrar la vista de dispositivos, podrá filtrarlos según su fecha de inscripción. Por ejemplo, puede mostrar solo los dispositivos que se hayan inscrito después de una fecha específica.
-   Hemos realizado mejoras en el filtro que usa el elemento **Ultima fecha de inserción**.
-   En la lista de dispositivos, ahora puede mostrar el número de teléfono de los dispositivos corporativos.
Además, puede usar el panel de filtros para buscar dispositivos por el número de teléfono.
 
Para obtener más información sobre el inventario de dispositivos, consulte [Visualización del inventario de dispositivos de Intune](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Compatibilidad del acceso condicional con dispositivos macOS 
<!-- 720172 -->
Ya puede establecer una directiva de acceso condicional que exija que los dispositivos Mac se inscriban en Intune y cumplan las directivas de cumplimiento de dispositivos. Por ejemplo, los usuarios pueden descargar la aplicación Portal de empresa de Intune para macOS e inscribir los dispositivos Mac en Intune. Intune evalúa si el dispositivo Mac es conforme o no con requisitos como el PIN, el cifrado, la versión del sistema operativo y la integridad del sistema.

- Obtenga más información sobre la [compatibilidad con el acceso condicional para dispositivos macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>La aplicación Portal de empresa para macOS está en versión preliminar pública <!---1484796--->
La aplicación Portal de empresa para macOS ya está disponible como parte de la versión preliminar pública para el acceso condicional en Enterprise Mobility + Security. Esta versión admite macOS 10.11 y versiones posteriores. Puede obtenerla en [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Nueva configuración de restricciones de dispositivos para Windows 10    
<!--1063965, 1308850  -->
En esta versión, hemos agregado nuevas opciones para el [perfil de restricción de dispositivos Windows 10](/intune/device-restrictions-windows-10) en las categorías siguientes:

-   SmartScreen de Windows Defender
-   Tienda de aplicaciones

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Actualizaciones en el perfil de dispositivo de Endpoint Protection de Windows 10 para la configuración de BitLocker
<!--1459533 -->    
En esta versión, hemos realizado las mejoras siguientes al funcionamiento de la configuración de BitLocker en un perfil de dispositivo de Endpoint Protection de Windows 10:
 
En **Configuración de BitLocker para unidades de sistema operativo**, en el ajuste **BitLocker con un chip TPM no compatible** BitLocker estaba permitido tras seleccionar **Bloquear**. Se ha corregido este problema para poder bloquear BitLocker cuando se selecciona.
En **Configuración de BitLocker para unidades de sistema operativo**, en el ajuste **Agente de recuperación de datos basada en certificado**, ya puede bloquear explícitamente el agente de recuperación de datos basada en certificado. De forma predeterminada, el agente está permitido.
En **Configuración de BitLocker para unidades de datos fijas**, en el ajuste **Agente de recuperación de datos**, ya puede bloquear explícitamente el agente de recuperación de datos.
Para obtener más información, vea [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Configuración de Endpoint Protection para Windows 10 y versiones posteriores).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nueva experiencia de sesión iniciada para los usuarios del portal de empresa de Android y para los usuarios de la directiva de protección de aplicaciones <!-- 621669 -->
Los usuarios finales pueden ahora examinar aplicaciones, administrar dispositivos y ver la información de contacto de TI mediante la aplicación del Portal de empresa de Android sin inscribir sus dispositivos Android. Además, si un usuario final ya usa una aplicación protegida mediante las directivas de Intune App Protection e inicia el portal de empresa de Android, el usuario final ya no recibirá una solicitud para inscribir el dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nueva configuración de la aplicación de portal de empresa para Android para alternar la optimización de la batería <!--1405990-->
La página **Configuración** de la aplicación Portal de empresa para Android tiene una nueva opción que permite a los usuarios desactivar fácilmente la optimización de la batería para las aplicaciones Portal de empresa y Microsoft Authenticator. El nombre de la aplicación que se muestra en la configuración variará dependiendo de qué aplicación administre la cuenta profesional. Recomendamos que los usuarios desactiven la optimización de la batería para obtener un rendimiento mejor de las aplicaciones de trabajo que sincronizan el correo electrónico y los datos. 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Compatibilidad con varias identidades en OneNote para iOS      <!-- 1234281 -->
Los usuarios finales ahora pueden usar cuentas diferentes (profesionales o educativas) en Microsoft OneNote para iOS. Las directivas de protección de aplicaciones se pueden aplicar a los datos corporativos en blocs de notas del trabajo sin que esto afecte a sus blocs de notas personales. Por ejemplo, una directiva puede permitir que un usuario busque información en blocs de notas del trabajo, pero impedir que copie datos corporativos desde un bloc de notas del trabajo a uno personal.
 
- Obtenga más información sobre las aplicaciones que admiten [protección de aplicaciones y varias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nueva configuración para permitir y bloquear aplicaciones en dispositivos Samsung Knox Standard
<!-- 1305423 822899-->  
En esta versión, se ha agregado una nueva [configuración de restricción de dispositivos](device-restrictions-android.md) que permite especificar las listas de aplicaciones siguientes:
 
- Aplicaciones que los usuarios pueden instalar
- Aplicaciones que los usuarios no pueden ejecutar
- Aplicaciones ocultas para el usuario en el dispositivo
 
Puede especificar la aplicación por dirección URL, nombre del paquete o desde la lista de aplicaciones que administra.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Nuevo vínculo de interfaz de usuario de la directiva de acceso condicional basado en la aplicación de Azure AD desde Intune
<!-- 1016201 -->
Los administradores de TI ahora pueden establecer directivas condicionales basadas en aplicaciones mediante la nueva interfaz de usuario de directivas de acceso condicional en la carga de trabajo de Azure AD. El acceso condicional basado en la aplicación de la sección de Intune App Protection en Azure Portal por el momento no se moverá y se aplicará en paralelo. También encontrará un práctico vínculo a la interfaz de usuario de la nueva directiva de acceso condicional en la carga de trabajo de Intune.

- Obtenga más información sobre el [acceso condicional basado en la aplicación en Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## <a name="july-2017"></a>Julio de 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restricción de la inscripción de dispositivos Android e iOS por versión del SO <!--- 1333256,  1245463 --->
Intune ya permite restringir la inscripción de Android e iOS por número de versión del sistema operativo. En **Restricción de tipo de dispositivo**, los administradores de TI ahora pueden establecer una configuración de plataforma para restringir la inscripción entre un valor del sistema operativo mínimo y máximo. Las versiones del sistema operativo Android se deben especificar como Principal.Secundaria.Compilación.Revisión, donde Secundaria, Compilación y Revisión son opcionales. Las versiones de iOS deben especificarse como Principal.Secundaria.Compilación, donde Compilación es opcional. Obtenga más información sobre las [restricciones de inscripción de dispositivos](enrollment-restrictions-set.md).

>[!NOTE]
>No se restringe la inscripción a través de los programas de inscripción de Apple o Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Restricción de la inscripción de dispositivos de propiedad personal macOS, iOS y Android <!--- 1333272,  1333275, 1245709 --->
Intune puede restringir la inscripción de dispositivos personales al incluir los números IMEI de los dispositivos corporativos en la lista aprobada. Intune ha ampliado esta funcionalidad para iOS, Android y macOS con números de serie del dispositivo. Al cargar los números de serie en Intune, puede declarar los dispositivos como de propiedad corporativa. Con las restricciones de inscripción puede bloquear los dispositivos de propiedad personal (BYOD), lo que permitiría la inscripción de dispositivos de propiedad corporativa únicamente. Obtenga más información sobre las [restricciones de inscripción de dispositivos](enrollment-restrictions-set.md).

Para importar números de serie, vaya a **Inscripción de dispositivos** > **Identificadores de dispositivo corporativos** y haga clic en **Agregar**; luego, cargue un archivo .CSV (sin encabezado, dos columnas para el número de serie y detalles como los números IMEI).  Para restringir dispositivos de propiedad personal, vaya a **Inscripción de dispositivos** > **Restricciones de inscripción**. En **Restricciones de tipo de dispositivo**, seleccione **Predeterminado** y luego **Configuraciones de plataforma**. Puede **Permitir** o **Bloquear** dispositivos de propiedad personal iOS, Android y macOS. 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nueva acción de dispositivo para forzar la sincronización de los dispositivos con Intune <!-- 711369 -->
En esta versión, se ha agregado una nueva acción de dispositivo que fuerza al dispositivo seleccionado a registrarse inmediatamente en Intune. Cuando un dispositivo se registra, recibe de inmediato las acciones o las directivas pendientes que se le han asignado.  Esta acción puede ayudarle a validar y a solucionar problemas de directivas que se le hayan asignado inmediatamente, sin tener que esperar al siguiente registro programado.
Para obtener detalles, vea [Synchronize device](device-sync.md) (Sincronizar dispositivos).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible <!-- 777100 -->
En el área de trabajo Actualizaciones de software hay disponible una nueva directiva que permite forzar a los dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible. Para obtener información detallada, consulte [Configure iOS update policies](/intune/software-updates-ios) (Configuración de directivas de actualización de iOS).

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile: nuevo socio de defensa contra amenazas móviles <!-- 954651, 1172027 -->
Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por SandBlast Mobile de Check Point, una solución de defensa contra amenazas móviles integrada en Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funcionamiento de la integración con Intune
El riesgo se evalúa según la telemetría recopilada de dispositivos que ejecutan SandBlast Mobile de Check Point. Puede configurar directivas de acceso condicional de EMS basadas en la evaluación de riesgos de SandBlast Mobile de Check Point habilitada mediante las directivas de cumplimiento de los dispositivos de Intune. Puede permitir o bloquear el acceso de dispositivos no compatibles a recursos corporativos en función de las amenazas detectadas.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Implementar una aplicación como disponible en la Tienda Microsoft para Empresas <!-- 748101 -->
Con esta versión, ahora los administradores pueden asignar la Tienda Microsoft para Empresas como disponible. Cuando se establece como disponible, los usuarios finales pueden instalar la aplicación desde la aplicación de Portal de empresa o un sitio web sin que se les redirija a Microsoft Store.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Actualizaciones de la interfaz de usuario en el sitio web del portal de empresa <!--1313244 part 1-->
Hemos realizado varias actualizaciones en la interfaz de usuario del [sitio web del portal de empresa](https://portal.manage.microsoft.com) para mejorar la experiencia del usuario final.

- __Mejoras en los iconos de aplicación__: Los iconos de aplicación ahora se muestran con un fondo generado automáticamente basándose en el color dominante del icono (si se puede detectar). Si procede, este fondo reemplaza el borde gris que antes era visible en los iconos de aplicación.

    En una próxima versión, el sitio web del Portal de empresa mostrará iconos grandes siempre que sea posible. Recomendamos que los administradores de TI publiquen aplicaciones con iconos de alta resolución, con un tamaño mínimo de 120 x 120 píxeles. 

- __Cambios de navegación__: Los elementos de barra de navegación se han movido al menú hamburguesa de la parte superior izquierda. Se ha quitado la página Categorías. Los usuarios ahora pueden filtrar el contenido por categoría durante la exploración.

- __Actualizaciones de aplicaciones destacadas__: Hemos agregado al sitio una página dedicada donde los usuarios pueden buscar aplicaciones que ha decidido presentar, y hemos realizado algunos ajustes a la interfaz de usuario de la sección Destacado en la página principal.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Compatibilidad de iBooks con el sitio web del Portal de empresa <!--1231841-->
Hemos agregado una página dedicada al sitio web del Portal de empresa que permite a los usuarios buscar y descargar iBooks. 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Detalles adicionales para la solución de problemas del departamento de soporte técnico <!---  Applies to 1263399, 1326964, 1341642 --->
Intune ha actualizado la visualización de información para la solución de problemas, y la ha agregado a la información que se proporciona a los administradores y al personal del departamento de soporte técnico. Ahora puede consultar la tabla **Asignaciones**, en la que se resumen todas las asignaciones para el usuario en función de la pertenencia al grupo. La lista incluye lo siguiente:
- Aplicaciones móviles
- Directivas de cumplimiento
- Perfiles de configuración
 
Además, en la tabla **Dispositivos** se incluyen ahora las columnas **Tipo de combinación de Azure AD** y **Conforme con Azure AD**. Para obtener más información, consulte [Help users troubleshoot problems (Ayudar a los usuarios a solucionar problemas)](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Almacenamiento de datos de Intune (versión preliminar pública)
El Almacenamiento de datos de Intune muestrea los datos a diario para proporcionar una vista histórica del inquilino. Puede tener acceso a los datos mediante un archivo de Power BI (PBIX), un vínculo de OData que es compatible con muchas herramientas de análisis o al interactuar con la API de REST. Para obtener más información, vea [Usar el Almacenamiento de datos de Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modos claro y oscuro disponibles para la aplicación Portal de empresa para Windows 10 <!---676547--->
Los usuarios finales podrán personalizar el modo de color de la aplicación Portal de empresa para Windows 10. El usuario puede realizar el cambio en la sección Configuración de la aplicación Portal de empresa. El cambio aparecerá una vez que el usuario haya reiniciado la aplicación. En Windows 10 versión 1607 y posteriores, el valor predeterminado del modo de la aplicación es la configuración del sistema. En Windows 10 versión 1511 y anteriores, el valor predeterminado del modo de la aplicación es el modo claro.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Permitir que los usuarios finales etiqueten su grupo de dispositivos en la aplicación Portal de empresa para Windows 10 <!---807046-->
Los usuarios finales ahora pueden seleccionar el grupo al que pertenece su dispositivo al etiquetarlo directamente desde la aplicación de portal de empresa para Windows 10.



## <a name="june-2017"></a>Junio de 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Nuevo acceso de administración basada en roles para los administradores de Intune <!-- 1099990 -->  
Se va a agregar un nuevo rol de administrador de acceso condicional para ver, crear, modificar y eliminar directivas de acceso condicional de Azure AD. Anteriormente, solo los administradores globales y de seguridad tenían este permiso. Se puede conceder a los administradores de Intune el permiso de este rol para que tengan acceso a las directivas de acceso condicional.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Etiquetado de los dispositivos corporativos con el número de serie<!-- 1215070 -->  
Intune ahora admite la carga de números de serie de iOS, macOS y Android como identificadores de dispositivos corporativos. No puede usar en este momento números de serie para impedir que los dispositivos personales se inscriban, ya que los números de serie no se comprueban durante la inscripción. Próximamente se podrán bloquear los dispositivos personales por el número de serie.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nuevas acciones remotas para los dispositivos iOS <!-- 854689 -->
En esta versión, hemos agregado dos nuevas acciones de dispositivo remoto para los dispositivos iPad compartidos que administran la aplicación Classroom de Apple:

-   [Cerrar sesión del usuario actual](device-logout-user.md): cierra la sesión del usuario actual de un dispositivo iOS que seleccione.
-   [Quitar usuario](device-remove-user.md): elimina un usuario que seleccione de la memoria caché local en un dispositivo iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Compatibilidad con dispositivos iPad compartidos con la aplicación Classroom de iOS<!-- 1044681 -->
En esta versión, hemos ampliado la compatibilidad con la administración de la aplicación Classroom en iOS, a fin de incluir a los estudiantes que se registran en dispositivos iPad compartidos con sus identificadores de Apple administrados.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Cambios en las aplicaciones integradas de Intune <!-- 1332306 -->
Anteriormente, Intune tenía numerosas aplicaciones integradas que se podían asignar rápidamente. Basándonos en los comentarios de los usuarios, hemos quitado esta lista y ya no se verán las aplicaciones integradas.
Sin embargo, si las aplicaciones integradas ya están asignadas, seguirán mostrándose en la lista de aplicaciones. Las aplicaciones podrán seguir asignándose según se necesite.
En una versión posterior, vamos a agregar un método sencillo para seleccionar y asignar aplicaciones integradas de Azure Portal.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Instalación más sencilla de aplicaciones de Office 365 <!--- 1121362 --->
El nuevo tipo de aplicación de **Office 365 ProPlus** facilita la asignación de aplicaciones de Office 365 ProPlus 2016 a dispositivos que administre con la versión más reciente de Windows 10. Además, también puede instalar Microsoft Project y Microsoft Visio si dispone de licencias para ellos. Las aplicaciones que quiera se agrupan y aparecen como una única aplicación en la lista de aplicaciones de la consola de Intune.
Para obtener más información, consulte el artículo sobre [cómo agregar aplicaciones de Office 365 para Windows 10](apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Compatibilidad con aplicaciones sin conexión desde la Tienda Microsoft para Empresas <!--- 777044 --->
Las aplicaciones sin conexión que ha adquirido en la Tienda Microsoft para Empresas ahora se sincronizarán con Azure Portal. Así, puede implementar estas aplicaciones en grupos de usuarios o grupos de dispositivos. Las aplicaciones sin conexión no se instalan desde la Tienda, sino mediante Intune.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft Teams ahora forma parte de la lista de CA basada en aplicación de aplicaciones aprobadas <!-- 1257019 -->
La aplicación Microsoft Teams para iOS y Android ahora forma parte de las aplicaciones aprobadas para las directivas de acceso condicional basado en la aplicación en Exchange y SharePoint Online. La aplicación puede configurarse para todos los inquilinos mediante la hoja Intune App Protection de Azure Portal en estos momentos mediante el acceso condicional basado en la aplicación.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Integración de App Proxy y Managed Browser <!-- 1287310 -->
Intune Managed Browser ahora puede integrarse con el servicio de Azure AD Application Proxy para permitir que los usuarios tengan acceso a los sitios web internos incluso cuando están trabajando en remoto. Los usuarios del explorador simplemente especifican la URL del sitio como lo harían normalmente y Managed Browser enruta la solicitud mediante la puerta de enlace web de Application Proxy. Para obtener más información, vea [Administrar el acceso a Internet mediante directivas de Managed Browser](app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nuevas opciones de configuración de aplicaciones para Intune Managed Browser<!-- 682951 -->
En esta versión, hemos agregado más configuraciones para la aplicación Intune Managed Browser para iOS y Android. Ahora puede usar una directiva de configuración de aplicaciones para configurar la página principal predeterminada y los marcadores para el explorador.
Para obtener más información, vea [Administrar el acceso a Internet mediante directivas de Managed Browser](app-configuration-managed-browser.md).

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Configuración de BitLocker para Windows 10 <!-- 951707 -->
Ahora puede configurar las opciones de BitLocker para dispositivos Windows 10 con un nuevo perfil de dispositivo de Intune. Por ejemplo, puede que necesite que los dispositivos estén cifrados, y también configurar más opciones que se apliquen cuando BitLocker esté activado.
Para obtener más información, vea [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Configuración de Endpoint Protection para Windows 10 y versiones posteriores).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Nueva configuración del perfil de restricción de dispositivo Windows 10<!--- 978527,  978550, 978569, 1050031, 1058611,  --->
En esta versión, hemos agregado nuevas opciones para el perfil de restricción de dispositivos Windows 10, en las categorías siguientes:

-  Windows Defender
-  Red de telefonía móvil y conectividad
-  Experiencia de pantalla bloqueada
-  Privacidad
-  Buscar
-  Contenido destacado de Windows
-  Explorador Edge

Para obtener más información sobre la configuración de Windows 10, vea [Configuración de restricciones de dispositivos Windows 10 y versiones posteriores](device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>La aplicación portal de empresa para Android ahora tiene una nueva experiencia de usuario final para las directivas de protección de aplicaciones <!--1305217-->
Basándonos en los comentarios de los clientes, hemos modificado la aplicación del portal de empresa para Android para mostrar un botón **Acceso al contenido de la empresa**. El objetivo es impedir que los usuarios finales pasen innecesariamente por el proceso de inscripción cuando solo necesitan tener acceso a las aplicaciones que admiten directivas de protección de aplicaciones, una característica de administración de aplicaciones móviles de Intune. Puede ver estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nueva acción de menú para quitar fácilmente Portal de empresa de Intune <!--1164569-->
Según los comentarios de los usuarios, se agregó una nueva acción de menú en la aplicación Portal de empresa de Intune para Android con el fin de iniciar su eliminación del dispositivo. Con esta acción se quita el dispositivo de administración de Intune para que la aplicación se pueda quitar del dispositivo por parte del usuario. Puede ver estos cambios en la página de [novedades en la UI de la aplicación](whats-new-app-ui.md) y en la [documentación para el usuario final de Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Mejoras en la sincronización de aplicaciones con Windows 10 Creators Update <!--676505-->
La aplicación Portal de empresa de Intune para Windows 10 ahora iniciará automáticamente una sincronización de las solicitudes de instalación de aplicaciones para dispositivos con Windows 10 Creators Update (versión 1703). De esta forma, se reducirá el problema de estancamiento de las instalaciones de aplicaciones durante el estado "Pending Sync" (Sincronización pendiente). Además, los usuarios podrán iniciar manualmente la sincronización desde dentro de la aplicación. Puede ver estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nueva experiencia guiada del Portal de empresa de Windows 10<!---1058938--->
La aplicación del Portal de empresa para Windows 10 incluirá la experiencia de un tutorial de Intune guiado para dispositivos que no se han identificado ni inscrito. La nueva experiencia proporciona instrucciones paso a paso que llevan al usuario por el registro en Azure Active Directory (que es necesario para las características de acceso condicional) y la inscripción en MDM (que es necesaria para las características de administración de dispositivos). La experiencia guiada será accesible desde la página principal del Portal de empresa. Los usuarios pueden seguir utilizando la aplicación si no completan el registro y la inscripción, pero experimentarán una funcionalidad limitada.

Esta actualización solo es visible en dispositivos que ejecuten la Actualización de aniversario de Windows 10 (compilación 1607) o superior. Puede ver estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Las consolas de administración de Microsoft Intune y Acceso condicional están disponibles con carácter general
Se anuncia la disponibilidad general de la nueva consola de administración tanto de Intune en Azure Portal como de Acceso condicional. A través de Intune en Azure Portal, ahora puede administrar todas las funcionalidades MAM y MDM de Intune en una experiencia de administración consolidada y aprovechar la agrupación y la selección de destino de Azure AD. Acceso condicional de Azure reúne las amplias funcionalidades de Azure AD e Intune en una consola unificada. Y, desde una experiencia administrativa, migrar a la plataforma Azure permite usar exploradores modernos.

Intune ya está visible sin la etiqueta de **versión preliminar** en Azure portal en portal.azure.com.

No es necesario que los clientes existentes tomen ninguna medida en este momento, a menos que se haya recibido un mensaje de una serie de estos en el centro de mensajes en el que se le solicite llevar a cabo una acción para que sea posible migrar sus grupos. Es posible que también haya recibido una notificación del centro de mensajes en el que se le informe que la migración está tardando más de lo debido producto de errores en nuestro lado. Seguimos trabajando con diligencia para migrar cualquier cliente afectado.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Mejoras de los iconos de aplicación en la aplicación Portal de empresa de Intune para iOS
Se actualizó el diseño de los iconos de aplicación en la página principal para reflejar el color de personalización de marca que estableció para Portal de empresa de Intune. Para más información, consulte las [novedades en la UI de la aplicación](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Ahora el selector de cuenta está disponible en la aplicación Portal de empresa de Intune para iOS
Los usuarios de dispositivos iOS pueden ver el nuevo selector de cuenta cuando inician sesión en Portal de empresa de Intune si usan su cuenta profesional o educativa para iniciar sesión en otras aplicaciones de Microsoft. Para más información, consulte las [novedades en la UI de la aplicación](whats-new-app-ui.md).

## <a name="may-2017"></a>Mayo de 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Cambio de la entidad de MDM sin anular la inscripción de dispositivos administrados <!--1103950-->
Ahora puede cambiar la entidad de MDM sin tener que ponerse en contacto con el Soporte técnico de Microsoft y sin necesidad de anular la inscripción ni de volver a inscribir los dispositivos administrados existentes. En la consola de Configuration Manager, puede [cambiar la entidad de MDM](/sccm/mdm/deploy-use/change-mdm-authority) de Configurar como Configuration Manager (híbrido) a Microsoft Intune (independiente), o viceversa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notificación mejorada para PIN de inicio en Samsung Knox <!--1087143-->
Si los usuarios finales necesitan establecer un PIN de inicio en dispositivos Samsung Knox a efectos de compatibilidad con el cifrado, cuando dichos usuarios pulsen en la notificación que aparece, se les remitirá al lugar exacto de la aplicación de configuración.  Anteriormente, la notificación remitía al usuario final a la pantalla de cambio de contraseña.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Compatibilidad de Apple School Manager (ASM) con iPad compartido <!-- 748864, 770395-->

Intune ahora admite el uso de Apple School Manager (ASM) en lugar del Programa de inscripción de dispositivos de Apple para permitir la inscripción inmediata de dispositivos iOS. Es necesario incorporar ASM para usar la aplicación Classroom para Shared iPads, así como habilitar la sincronización de datos de ASM en Azure Active Directory mediante Microsoft School Data Sync (SDS). Para más información, consulte el artículo sobre la [habilitación de la inscripción de dispositivos iOS con Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> Configurar iPad compartidos para que funcionen con la aplicación Classroom requiere configuraciones de dispositivos iOS para Education en Azure que todavía no están disponibles.  Esta funcionalidad se agregará pronto.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Asistencia remota para dispositivos Android con TeamViewer <!-- 675418 -->

Intune ahora puede usar el software [TeamViewer](https://www.teamviewer.com), que se compra de forma independiente, para permitirle ofrecer asistencia remota a los usuarios que ejecutan dispositivos Android. Para más información, consulte [Asistencia remota para dispositivos Android administrados con Intune](device-profile-android-teamviewer.md).

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Nuevas condiciones de las directivas de protección de aplicaciones para MAM <!-- 679864 -->

Ahora puede establecer un requisito para MAM sin inscripción de usuarios que exige las siguientes directivas:

- Versión mínima de la aplicación
- Versión mínima del sistema operativo
- Versión mínima del SDK para aplicaciones de Intune de la aplicación de destino (solo iOS)

Esta característica está disponible en iOS y Android. Intune admite el cumplimiento del requisito de versiones mínimas de la plataforma de SO, las aplicaciones y el SDK para aplicaciones de Intune. En iOS, las aplicaciones que tienen el SDK integrado también pueden establecer el cumplimiento de una versión mínima a nivel del SDK. El usuario no podrá acceder a la aplicación de destino si no se cumplen los requisitos mínimos a través de la directiva de protección de aplicaciones a los tres niveles distintos mencionados anteriormente. En este punto, el usuario puede quitar la cuenta (en aplicaciones con varias identidades), cerrar la aplicación o actualizar la versión del SO o de la aplicación.

También puede configurar valores adicionales para proporcionar una notificación sin bloqueo que recomienda una actualización del SO o de la aplicación. Puede cerrar esta notificación, y la aplicación puede usarse de la forma habitual.

Para más información, consulte [Configuración de directivas de protección de aplicaciones de iOS](app-protection-policy-settings-ios.md) y [Configuración de directivas de protección de aplicaciones de Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Configuración de aplicación para Android for Work <!-- 621621 -->
Algunas aplicaciones Android de la tienda admiten opciones de configuración administradas que permiten que un administrador de TI controle cómo se ejecuta la aplicación en el perfil de trabajo. Con Intune, ahora puede ver las configuraciones que son compatibles con una aplicación y configurarlas desde Azure Portal con un diseñador de configuración o un editor de JSON. Para más información, consulte el artículo sobre el [uso de configuraciones de aplicación para Android for Work](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Nueva funcionalidad de configuración de aplicación para MAM sin inscripción <!-- 677969 -->
Ahora puede crear directivas de configuración de aplicación a través de MAM sin canal de inscripción. Esta característica es equivalente a las directivas de configuración de aplicación disponibles en la configuración de aplicación de administración de dispositivos móviles (MDM). Si desea un ejemplo de configuración de aplicación con MAM sin inscripción, consulte [Administrar el acceso a Internet mediante directivas de Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Configuración de las listas de direcciones URL permitidas y bloqueadas para Managed Browser <!-- 682960 -->
Ahora puede configurar una lista de direcciones URL y dominios permitidos y bloqueados para Intune Manager Browser con los valores de configuración de aplicación en Azure Portal. Estos valores se pueden configurar independientemente de si se usa en un dispositivo administrado o no administrado. Para más información, consulte [Administrar el acceso a Internet mediante directivas de Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Vista de departamento de soporte técnico de directiva de protección de aplicaciones <!-- 1069473 -->
Los usuarios del departamento de soporte técnico de TI ahora pueden comprobar el estado de la licencia de usuario y el estado de las aplicaciones de directiva de protección de aplicaciones asignadas a los usuarios en la hoja Solución de problemas. Para información detallada, consulte [Solución de problemas](./help-desk-operators.md).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Control de las visitas a sitios web en dispositivos iOS <!-- 723832 -->
Ahora puede controlar qué sitios web pueden visitar los usuarios de dispositivos iOS mediante uno de los dos métodos siguientes:

- Agregar direcciones URL permitidas y bloqueadas mediante el filtro de contenido web integrado de Apple.

- Permitir que el explorador Safari acceda solo a sitios web especificados. Se crean marcadores en Safari para cada sitio que especifique.

Para más información, consulte [Configuración de filtro de contenido web para dispositivos iOS](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Configuración previa de permisos de dispositivo para aplicaciones de Android for Work <!-- 621614 -->
En el caso de las aplicaciones implementadas en perfiles de trabajo de dispositivos Android for Work, ahora puede configurar el estado de los permisos en cada aplicación.  De forma predeterminada, las aplicaciones de Android que requieren permisos de dispositivo como el acceso a la ubicación o la cámara del dispositivo solicitarán a los usuarios que acepten o denieguen permisos.  Por ejemplo, si una aplicación usa el micrófono del dispositivo, se solicita al usuario final que conceda a la aplicación el permiso para usar el micrófono. Esta característica le permite definir permisos en nombre del usuario final.  Ahora puede configurar permisos para a) denegar automáticamente sin notificar al usuario, b) aprobar automáticamente sin notificar al usuario, o c) pedirle al usuario que acepte o deniegue los permisos. Para más información, consulte [Configuración de restricciones de dispositivos Android for Work en Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Establecimiento de un PIN específico de la aplicación para dispositivos Android for Work <!-- 728976, 1102534 -->
Los dispositivos Android 7.0 y versiones posteriores con un perfil de trabajo administrado como un dispositivo Android for Work permiten que el administrador defina una directiva de código de acceso que solo se aplique a aplicaciones del perfil de trabajo.  Las opciones son:

- Definir una contraseña de código de acceso a nivel de dispositivo: se trata del código de acceso que el usuario debe usar para desbloquear todo el dispositivo.
- Definir una directiva de código de acceso solo a nivel de perfil de trabajo: a los usuarios se les pedirá que escriban un código de acceso cada vez que se abra cualquier aplicación del perfil de trabajo.
- Definir una directiva para el dispositivo y el perfil de trabajo: el administrador de TI tiene la opción de definir una directiva de código de acceso para el dispositivo y otra para el perfil de trabajo con diferentes intensidades (por ejemplo, un PIN de cuatro dígitos para desbloquear el dispositivo y uno de seis para abrir cualquier aplicación de trabajo).

Para más información, consulte [Configuración de restricciones de dispositivos Android for Work en Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Esta opción solo está disponible en Android 7.0 y versiones posteriores.  De forma predeterminada, el usuario final puede usar los dos PIN definidos por separado o de optar por combinar los dos en el más seguro de ellos.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Nuevas opciones de configuración para dispositivos Windows 10 <!-- 978585 -->
Agregamos una nueva [configuración de restricción de dispositivos Windows](device-restrictions-windows-10.md) que controla características como la proyección inalámbrica, la detección de dispositivos, la conmutación de tareas y los mensajes de error de tarjetas SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Actualizaciones de la configuración de certificados <!-- 918991 and 823198 -->
Cuando crea un perfil de certificado SCEP, en el **formato del nombre del sujeto**, la opción **Personalizar** está disponible para dispositivos iOS, Android y Windows. Antes de esta actualización, el campo **Personalizar** solo estaba disponible para dispositivos iOS. Para más información, consulte [Creación de un perfil de certificado SCEP] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile).

Cuando crea un perfil de certificado PKCS, en el **nombre alternativo del sujeto**, está disponible la opción **Atributo de Azure AD personalizado**. La opción **Departamento** está disponible cuando se selecciona **Atributo de Azure AD personalizado**. Para más información, consulte el artículo sobre la [creación de un perfil de certificado PKCS](certficates-pfx-configure.md#create-a-device-configuration-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configuración de varias aplicaciones que se pueden ejecutar cuando un dispositivo Android está en el modo de pantalla completa <!-- 662059 -->
Si un dispositivo Android está en el modo de pantalla completa, anteriormente solo podía configurar una aplicación que se podía ejecutar. Ahora puede configurar varias aplicaciones con el id. de la aplicación, la dirección URL de la tienda o seleccionando una aplicación Android que ya administra. Para más información, consulte [Configuración del modo de pantalla completa](device-restrictions-android.md#kiosk).



## <a name="april-2017"></a>Abril de 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Compatibilidad para administrar la aplicación Classroom de Apple
Ahora puede administrar la aplicación Classroom de iOS en dispositivos iPad. Configure la aplicación Classroom en el iPad de los profesores con los datos correctos de la clase y los estudiantes y, a continuación, configure los iPad de los estudiantes registrados en la clase, de modo que pueda controlarlos mediante la aplicación.
Para obtener más detalles, vea [Configuración de dispositivos iOS para el entorno educativo](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Compatibilidad con las opciones de configuración administradas para aplicaciones Android <!-- 621621 -->
Intune ahora puede configurar las aplicaciones Android de Play Store que admiten opciones de configuración administradas.  Esta característica permite al equipo de TI ver la lista de valores de configuración que admite una aplicación y proporciona una interfaz de usuario interactiva y de primera clase que les permite configurar dichos valores.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nueva directiva de Android para PIN complejos <!-- 722069 -->
Ahora puede establecer un tipo de [contraseña](device-restrictions-android.md#password) obligatoria de complejo numérico en un perfil de dispositivo Android para dispositivos que ejecutan Android 5.0 y versiones posteriores.  Use esta opción para impedir que los usuarios de los dispositivos creen un PIN que contenga números repetidos o consecutivos, como 1111 o 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Soporte adicional para dispositivos Android for Work
- **Administrar la configuración del perfil de trabajo y la contraseña** <!-- 612808 -->

  Esta nueva directiva de restricción de dispositivos Android for Work ahora permite administrar la configuración del perfil de trabajo y la contraseña en los dispositivos Android for Work que administre.

- **Permitir el uso compartido de datos entre perfiles profesionales y personales** <!-- 1045102 -->

Este perfil de restricción de dispositivos Android for Work ahora tiene opciones nuevas que le ayudarán a configurar el uso compartido de datos entre el perfil profesional y el perfil personal.

- **Restringir las acciones de copiar y pegar entre perfiles profesionales y personales** <!-- 1046094 -->

  Un perfil de dispositivo personalizado para dispositivos Android for Work ahora permite restringir si se permiten las acciones de copiar y pegar entre aplicaciones profesionales y personales.

Para más información, consulte [Restricciones de dispositivos para Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Asignar aplicaciones de LOB a dispositivos iOS y Android <!-- 1057568 -->
Ahora puede asignar aplicaciones de línea de negocio para [iOS](lob-apps-ios.md) (archivos .ipa) y [Android](lob-apps-android.md) (archivos .apk) a usuarios o dispositivos.


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nuevas directivas de dispositivo para iOS <!-- 723774, 723815, 723826, 723830 -->
- **Aplicaciones en la pantalla principal**: controla qué aplicaciones ven los usuarios en la [pantalla principal de sus dispositivos iOS](home-screen-settings-ios.md). Esta directiva cambia el diseño de la pantalla principal, pero no implementa ninguna aplicación.

- **Conexiones con dispositivos AirPrint**: controla a qué [dispositivos AirPrint](air-print-settings-ios-macos.md) (impresoras de red) se pueden conectar los usuarios finales de dispositivos iOS.

- **Conexiones con dispositivos AirPlay**: controla a qué [dispositivos AirPlay](airplay-settings-ios.md) (como Apple TV) se pueden conectar los usuarios finales de dispositivos iOS.

- **Mensaje personalizado de la pantalla de bloqueo**: configurar un mensaje personalizado que verán los usuarios en la pantalla de bloqueo de sus dispositivos iOS y que reemplaza al mensaje predeterminado de esa pantalla. Para más información, consulte [Activación del modo perdido en dispositivos iOS](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Restringir las notificaciones de inserción para aplicaciones iOS <!-- 723767 -->
En un perfil de restricción de dispositivos de Intune, ahora puede configurar los siguientes [ajustes de notificación](app-notification-settings-ios.md) para dispositivos iOS:

- Activar o desactivar completamente las notificaciones para una aplicación especificada.
- Activar o desactivar la notificación en el centro de notificaciones para una aplicación especificada.
- Especificar el tipo de alerta como **None** (Ninguna), **Banner** (Mensaje emergente) o **Modal Alert** (Alerta modal).
- Especificar si se permiten los distintivos para esta aplicación.
- Especificar si se permiten los sonidos de notificaciones.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurar aplicaciones iOS para que se ejecuten en el modo de aplicación única de forma autónoma <!-- 737837 -->
Puede usar un perfil de dispositivo de Intune para configurar dispositivos iOS de modo que ejecuten aplicaciones especificadas en [modo de aplicación única autónoma](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Cuando se configura este modo y se ejecuta la aplicación, el dispositivo se bloquea para que solo pueda ejecutar esa aplicación. Un ejemplo es cuando se configura una aplicación que permite a los usuarios hacer un examen en el dispositivo. Cuando se completan las acciones de la aplicación, o quita esta directiva, el dispositivo vuelve a su estado normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurar dominios de confianza para el correo electrónico y la exploración web en dispositivos iOS <!-- 723765 -->
Desde un perfil de restricción de dispositivos iOS, ahora puede configurar los [valores de dominio](device-restrictions-ios.md#domains) siguientes:

- **Dominios de correo electrónico sin marcar**: los correos electrónicos que el usuario envía o recibe y no coinciden con los dominios que especifique aquí se marcarán como que no son de confianza.

- **Dominios web administrados**: los documentos que se descargan de las direcciones URL que especifique aquí se considerarán administrados (solo en Safari).  

- **Dominios de relleno automático de contraseña de Safari**: los usuarios pueden guardar en Safari las contraseñas solo de las direcciones URL que coincidan con los patrones que especifique aquí. Para usar esta opción, el dispositivo debe estar en modo supervisado y no estar configurado para varios usuarios. (iOS 9.3 y versiones posteriores)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Aplicaciones de PCV disponibles en el Portal de empresa de iOS <!-- 748782 -->
Ahora puede asignar aplicaciones de compras por volumen (PCV) de iOS como instalaciones **Disponibles** para usuarios finales. Los usuarios finales necesitarán una cuenta de Apple Store para instalar la aplicación.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizar libros electrónicos de la tienda de compras por volumen de Apple <!-- 800878 -->
Ahora puede [sincronizar los libros](vpp-apps-ios.md) que haya adquirido a través de la tienda del Programa de Compras por Volumen de Apple con Intune y asignarlos a los usuarios.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Administración de varios usuarios para dispositivos Samsung Knox Standard <!-- 971988 -->
Intune es compatible ahora con dispositivos que ejecutan Samsung Knox Standard para la [administración de varios usuarios](android-enroll.md). Esto significa que los usuarios finales pueden iniciar y cerrar sesión en el dispositivo con sus credenciales de Azure Active Directory, y que el dispositivo se administra centralmente tanto si está en uso como si no.  Cuando los usuarios finales inician sesión, tienen acceso a las aplicaciones y se les aplican las directivas. Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Configuración adicional de restricción de dispositivos Windows <!-- 818566 -->
Hemos agregado compatibilidad con [opciones de configuración adicionales de restricción de dispositivos Windows](device-restrictions-windows-10.md), como la compatibilidad adicional con el explorador Edge, la personalización de la pantalla de bloqueo del dispositivo, las personalizaciones del menú Inicio, el papel tapiz del conjunto de búsqueda de Contenido destacado de Windows y la configuración de proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Compatibilidad con varios usuarios para Windows 10 Creators Update <!-- 822547 -->
Hemos agregado compatibilidad para la [administración de varios usuarios](windows-enroll.md) en dispositivos que ejecutan Windows 10 Creators Update y están unidos al dominio de Azure Active Directory. Esto significa que cuando varios usuarios estándar inicien sesión en el dispositivo con sus credenciales de Azure AD, recibirán las aplicaciones y las directivas que se hayan asignado a sus nombres de usuario. Actualmente, los usuarios no puede usar Portal de empresa para escenarios de autoservicio, como la instalación de aplicaciones.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start para equipos con Windows 10<!-- 1004830 -->
Ahora hay disponible una nueva [acción de dispositivo Fresh Start](device-fresh-start.md) para equipos Windows 10.  Cuando se lleva a cabo esta acción, se quitan las aplicaciones que hubiera instaladas en el equipo y este se actualiza automáticamente a la última versión de Windows. Esto puede servir para ayudar a quitar las aplicaciones de OEM preinstaladas que a menudo se entregan con los nuevos PC. Puede configurar si se conservan los datos de usuario cuando se lleva a cabo esta acción de dispositivo.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Rutas de actualización adicionales de Windows 10 <!-- 903672 -->
Ahora puede crear una [directiva de actualización de edición para actualizar los dispositivos](edition-upgrade-configure-windows-10.md) a las siguientes ediciones adicionales de Windows 10:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscripción masiva de dispositivos Windows 10 <!-- 747607 -->
Ahora puede unir grandes cantidades de dispositivos que ejecutan Windows 10 Creator Update a Azure Active Directory e Intune con Windows Configuration Designer (WCD). Para habilitar la [inscripción masiva de MDM](windows-bulk-enroll.md) para el inquilino de Azure AD, cree un paquete de aprovisionamiento que una dispositivos al inquilino de Azure AD a través de Windows Configuration Designer y aplique el paquete a los dispositivos corporativos que desea inscribir y administrar de forma masiva. Una vez que el paquete se aplica a los dispositivos, se unirán a Azure AD, se inscribirán en Intune y estarán listos para que los usuarios de Azure AD inicien sesión.  Los usuarios de Azure AD son usuarios estándar en estos dispositivos y reciben las aplicaciones requeridas y las directivas asignadas. En este momento, no se admiten los escenarios de autoservicio ni de portal de empresa.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nueva configuración de MAM para PIN y ubicaciones de almacenamiento administrado <!-- 581122, 736644 -->
Ahora hay disponibles dos nuevas opciones de configuración de aplicaciones que le ayudarán con los escenarios de administración de aplicaciones móviles (MAM):

- **Disable app PIN when device PIN is managed** (Deshabilitar el PIN de aplicación cuando se administra el PIN del dispositivo): detecta si hay un PIN de dispositivo en el dispositivo inscrito y, si es así, omite el PIN de aplicación desencadenado por las directivas de protección de aplicaciones. Esta configuración permitirá reducir el número de veces que se muestra una solicitud de PIN a los usuarios que abran una aplicación habilitada para MAM en un dispositivo inscrito. Esta característica está disponible para iOS y Android.

- **Seleccione en qué servicios de almacenamiento se puede guardar datos empresariales**: permite especificar en qué ubicaciones de almacenamiento quiere guardar los datos corporativos. Los usuarios pueden guardar en los servicios de ubicación de almacenamiento seleccionados, lo que implica que se bloquearán todos los demás servicios de ubicación de almacenamiento no indicados.

  Lista de servicios de ubicación de almacenamiento compatibles:

  - OneDrive
  - OneDrive para la Empresa/SharePoint Online
  - Almacenamiento local

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portal de solución de problemas del departamento de soporte técnico <!-- 907448 -->
El nuevo [portal de solución de problemas](help-desk-operators.md) permite que los operadores del departamento de soporte técnico y los administradores de Intune vean a los usuarios y sus dispositivos y, además, realicen tareas para solucionar problemas técnicos de Intune.

## <a name="march-2017"></a>Marzo de 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Compatibilidad con Modo Perdido de iOS <!--431695-->
En iOS 9.3 y dispositivos posteriores, Intune agrega compatibilidad con **Modo Perdido**. Ahora puede bloquear un dispositivo para evitar su uso, así como mostrar un mensaje y llamar al número de teléfono de la pantalla de bloqueo del dispositivo.

El usuario final no podrá desbloquear el dispositivo hasta que un administrador deshabilite Modo Perdido. Cuando está activado el Modo Perdido, puede usar la acción **Buscar dispositivo** para ver la ubicación geográfica del dispositivo en un mapa en la consola de Intune.

El dispositivo debe ser un dispositivo iOS de la empresa, inscrito mediante DEP, que esté en modo supervisado.

Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](device-management.md)

### <a name="improvements-to-device-actions-report---677150--"></a>Mejoras en los informes de las acciones del dispositivo <!--677150-->
Hemos realizado mejoras en el informe de las acciones del dispositivo para mejorar el rendimiento. Además, ahora puede filtrar el informe por estado. Por ejemplo, puede filtrar el informe para mostrar únicamente las acciones de dispositivo que se han completado".

### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->
Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.
Consulte [How to add an app to Intune](apps-add.md) (Cómo agregar una aplicación a Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Asignación de aplicaciones LOB a los usuarios con dispositivos no inscritos <!--748823-->
Ahora puede asignar aplicaciones de línea de negocio desde la tienda a usuarios tengan o no inscritos sus dispositivos con Intune. Si el dispositivo de los usuarios no está inscrito con Intune, deben ir al sitio web del Portal de empresa para instalarlo, en lugar de a la aplicación del Portal de empresa.

### <a name="new-compliance-reports---846671--"></a>Nuevos informes de cumplimiento <!--846671-->
Ahora dispone de informes de cumplimiento que proporcionan la posición de cumplimiento de los dispositivos de su empresa y le permiten solucionar rápidamente los problemas relacionados con el cumplimiento detectados por los usuarios. Puede ver información acerca de

- Estado de cumplimiento general de los dispositivos
- Estado de cumplimiento de una configuración individual
- Estado de cumplimiento de una directiva individual

También puede usar estos informes para profundizar en un dispositivo individual para ver la configuración específica y las directivas que afectan a dicho dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->
Para las cuentas de Intune creadas después de enero de 2017, Intune habilitó el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en Azure Portal. Anteriormente, la vista preliminar de inscripción de Apple solo era accesible desde los vínculos de Azure Portal. Las cuentas de Intune creadas antes de enero de 2017 requerirán una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero pronto habrá detalles disponibles. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a la versión preliminar.


## <a name="february-2017"></a>Febrero de 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidad para restringir la inscripción de dispositivos móviles <!--747600, 795782-->
Intune está agregando nuevas restricciones de inscripción que controlan qué plataformas de dispositivos móviles pueden inscribir. Intune separa las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows y Windows Mobile.

* La restricción la inscripción de dispositivos móviles no restringe la inscripción del cliente de PC.  
* Solo para iOS y Android, hay una opción adicional para bloquear la inscripción de dispositivos de propiedad personal.

Intune marca todos los dispositivos nuevos como personal a menos que el administrador de TI tome la medida de marcarlos como propiedad de la empresa, como se explica en [este artículo](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas las acciones en los dispositivos administrados <!--677150-->
Un nuevo informe __Acciones de dispositivo__ muestra quién ha realizado acciones remotas como el restablecimiento de fábrica en dispositivos y, además, muestra el estado de esa acción. Vea [¿Qué es la administración de dispositivos?](device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Los dispositivos no administrados puedan acceder a aplicaciones asignadas <!--664691-->
Como parte de los cambios de diseño en el sitio web del portal de empresa, los usuarios de iOS y Android podrán instalar aplicaciones asignadas a ellos como "disponibles sin inscripción" en sus dispositivos no administrados. Con sus credenciales de Intune, los usuarios podrán iniciar sesión en el sitio web del portal de empresa y ver la lista de aplicaciones asignadas. Los paquetes de aplicación de las aplicaciones "disponibles sin inscripción" se encuentran disponibles para descargar a través del sitio web del portal de empresa. Las aplicaciones que requieren la inscripción para la instalación no se ven afectadas por este cambio, ya que se les pedirá a los usuarios que inscriban su dispositivo si quieren instalar esas aplicaciones.

### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->
Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.
Consulte [How to add an app to Intune](apps-add.md) (Cómo agregar una aplicación a Intune).

### <a name="display-device-categories---814654--"></a>Mostrar categorías de dispositivos <!--814654-->
Ahora puede ver la categoría del dispositivo como una columna en la lista de dispositivos. También puede editar la categoría desde la sección de propiedades de la hoja de propiedades del dispositivo. Consulte [How to add an app to Intune](apps-add.md) (Cómo agregar una aplicación a Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configuración de Windows Update para empresas <!--776716-->

Windows como servicio es la nueva forma de proporcionar actualizaciones para Windows 10. A partir de Windows 10, todas las nuevas actualizaciones de calidad y características contienen las actualizaciones anteriores. Es decir, siempre que haya instalado la más reciente, sabrá que sus dispositivos Windows 10 están completamente actualizados. A diferencia de las versiones anteriores de Windows, ahora debe instalar la actualización completa en lugar de una parte.

Gracias a Windows Update para empresas, puede simplificar la administración de actualizaciones, ya que no tendrá que aprobar actualizaciones individuales para grupos de dispositivos. Todavía puede administrar los riesgos en sus entornos configurando una estrategia de implementación de actualizaciones; Windows Update se asegurará de que las actualizaciones se instalen en el momento oportuno. Microsoft Intune ofrece la posibilidad de configurar las actualizaciones en los dispositivos y de aplazar su instalación. Intune no almacena las actualizaciones, sino únicamente la asignación de las directivas de actualización. Los dispositivos acceden a Windows Update directamente para instalar las actualizaciones. Use Intune para configurar y administrar los **anillos de actualización de Windows 10**. Un anillo de actualización contiene un grupo de opciones que configuran cuándo y cómo se instalan las actualizaciones de Windows 10. Para obtener más información, consulte [Configuración de Windows Update para empresas](windows-update-for-business-configure.md).
