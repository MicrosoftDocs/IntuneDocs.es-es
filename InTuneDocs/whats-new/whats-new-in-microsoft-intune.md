---
title: Novedades | Microsoft Docs
description: Conozca las novedades de las versiones anteriores y de este mes de Microsoft Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: cb1679deda0ba325ee3bd7288713f12317489006
ms.openlocfilehash: 37d44dc2752815ef7abf47e5d4a658a126892a86
ms.lasthandoff: 02/18/2017


---
# <a name="whats-new-in-microsoft-intune---february-2017"></a>Novedades de Microsoft Intune: febrero de 2017
Conozca las novedades de esta versión de Microsoft Intune. También podrá obtener información sobre los próximos cambios para los que debe prepararse y sobre las versiones anteriores.

> [!Note]
> Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="modernizing-the-company-portal-website---753980--"></a>Renovación del sitio web del portal de empresa<!--753980-->
El sitio web del portal de empresa admitirá aplicaciones destinadas a aquellos usuarios que no tienen dispositivos administrados. El sitio web se alineará con otros productos y servicios de Microsoft mediante una nueva combinación de colores de contraste, ilustraciones dinámicas y un "menú hamburguesa", ![pequeña imagen del menú hamburguesa que se agrega ahora a la esquina superior izquierda del sitio web del portal de empresa](./media/CP_hamburger_menu.png) que contendrá los detalles de contacto del departamento de soporte técnico e información sobre los dispositivos administrados existentes. La página de inicio se reorganizará para destacar las aplicaciones que están disponibles para los usuarios, con carruseles para aplicaciones destacadas y actualizadas recientemente. Puede encontrar imágenes de antes y después disponibles en la [página de actualizaciones de la interfaz de usuario](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Nueva experiencia guiada del Portal de empresa de Windows 10<!--713927-->
A partir de marzo, el Portal de empresa para Windows 10 incluirá la experiencia de un tutorial de Intune guiado para dispositivos que no se han identificado ni inscrito. La nueva experiencia proporciona instrucciones paso a paso, personalizadas para la compilación de Windows 10 del usuario, que guían a los usuarios por la realización del registro en AAD (necesario para la identificación de las características de acceso condicional) y la inscripción de MDM (necesaria para características de administración de dispositivos). La experiencia guiada será accesible desde la página principal del Portal de empresa y es opcional; los usuarios pueden seguir usando la aplicación aunque no realicen la inscripción ni el registro, pero puede que experimenten funcionalidad limitada.

## <a name="notices"></a>Notificaciones

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>La migración de grupo no requiere actualizaciones a grupos ni directivas para dispositivos iOS <!--898837-->
Para cada grupo de dispositivos de Intune previamente asignado mediante un perfil de inscripción de dispositivos corporativos, se creará un grupo de dispositivos dinámico correspondiente en AAD según el nombre del perfil de inscripción de dispositivos corporativos, durante la migración a grupos de dispositivos de Azure Active Directory. Esto garantizará que, según se inscriban dispositivos, estos se agrupen de manera automática y reciban las mismas directivas y aplicaciones que el grupo de Intune original.

Una vez que un inquilino empieza el proceso de migración para agrupar y seleccionar el destino, Intune creará de forma automática un grupo dinámico de AAD para que se corresponda con un grupo de Intune destinado mediante un perfil de inscripción de dispositivos corporativos. Si el administrador de Intune elimina el grupo de destino de Intune, no se eliminará el grupo de AAD dinámico correspondiente. Se borrarán los miembros del grupo y la consulta dinámica, pero el propio grupo permanecerá hasta que el administrador de TI lo quite a través del portal de AAD.

De forma similar, si el administrador de TI cambia qué grupo de Intune es el destino de un perfil de inscripción de dispositivos corporativos, Intune crea un nuevo grupo dinámico que refleje la nueva asignación de perfil, pero no quitará el grupo dinámico creado para la asignación anterior.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Restablecer la administración de dispositivos de escritorio Windows predeterminada mediante la configuración de Windows <!--663050-->
El comportamiento predeterminado para inscribir equipos de escritorio de Windows 10 está cambiando. Las nuevas inscripciones seguirán el típico flujo de inscripción del agente MDM en lugar del agente de PC. El sitio web de portal de empresa proporcionará a los usuarios de escritorio de Windows 10 las instrucciones de inscripción que les guiarán a través del proceso de agregar equipos de escritorio de Windows 10 como dispositivos móviles. Esto no afectará a los PC inscritos en estos momentos, y su organización todavía puede administrar equipos de escritorio de Windows 10 con el agente de PC [si lo prefiere](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Mejorar la asistencia de la administración de aplicaciones móviles para el borrado selectivo <!--581242-->
A los usuarios finales se les proporcionarán instrucciones adicionales sobre cómo recuperar el acceso a los datos profesionales o educativos si estos se quitaron automáticamente debido a la directiva "Intervalo sin conexión antes de que se borren los datos de la aplicación".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Los vínculos de portal de empresa para iOS se abren dentro de la aplicación <!--665954-->
Los vínculos dentro de la aplicación de portal de empresa para iOS, incluidos los de documentación y aplicaciones, se abrirán directamente en la aplicación de portal de empresa con una vista desde la aplicación de Safari. Esta actualización se enviará por separado desde la actualización del servicio en enero.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Nueva dirección del servidor MDM para dispositivos Windows <!--893007-->
Se producirá un error en la inscripción del dispositivo si los usuarios de Windows y Windows Phone especifican __manage.microsoft.com__ como la dirección del servidor MDM (si se le pide). La dirección del servidor MDM cambia de __manage.microsoft.com__ a __enrollment.manage.microsoft.com__. Notifique al usuario que use __enrollment.manage.microsoft.com__ como la dirección del servidor MDM si se le pide durante la inscripción de un dispositivo Windows o Windows Phone. No se requieren cambios para la configuración de CNAME. Para obtener información adicional sobre este cambio, visite [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nueva experiencia del usuario en la aplicación del portal de empresa para Android <!--621622-->
A partir de marzo, la aplicación del portal de empresa para Android seguirá las [directrices de Material Design](https://material.io/guidelines/material-design/introduction.html) para crear una apariencia más moderna. Esta experiencia del usuario mejorada incluye:

* __Colores__: los encabezados de pestaña pueden colorearse según la paleta de colores personalizada.
* __Interfaz__: los botones Aplicaciones destacadas y Todas las aplicaciones se han actualizado en la pestaña Aplicaciones. El botón Buscar ahora es un botón de acción flotante.
* __Navegación__: Todas las aplicaciones muestra una vista con pestañas de Destacadas, Todas y Categorías para navegar más fácilmente.
* __Servicio__: las pestañas Mis dispositivos y Contactar con TI han mejorado la legibilidad.

Puede encontrar imágenes de antes y después en la [página de actualizaciones de la interfaz de usuario](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Asociación de varias herramientas de administración con la Tienda Windows para empresas<!--926135-->
Si usa más de una herramienta de administración para implementar las aplicaciones de la Tienda Windows para empresas, anteriormente solo podía asociar una de ellas con la Tienda Windows para empresas. Ahora puede asociar varias herramientas de administración con la tienda, por ejemplo, Intune y Configuration Manager. Para más información, consulte [Administrar las aplicaciones adquiridas a través de la Tienda Windows para empresas con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novedades en la versión preliminar pública de la experiencia de administración en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](https://docs.microsoft.com/intune-azure/introduction/whats-new).

Si tiene alguna pregunta sobre la programación de la migración de su inquilino, póngase en contacto con nuestro equipo de migración en [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

Puede encontrar las novedades en la vista previa de Intune en Azure [aquí](https://docs.microsoft.com/intune-azure/introduction/whats-new).

### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades en la vista previa de Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Novedades de la interfaz de usuario del portal de empresa](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Archivo de novedades](whats-new-archive.md)

