---
title: "Edición anticipada | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d0b3a883bb307fb06cb8d16500798086f328314a
ms.openlocfilehash: eeebf8b6b3bc5c7c35386eb20c96097af1f6769c
ms.lasthandoff: 02/14/2017


---


# <a name="the-early-edition-for-microsoft-intune---february-2017"></a>La edición anticipada de Microsoft Intune: febrero de 2017

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme al NDA en una base extremadamente limitada y está vinculada a cambios. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Póngase en contacto con su persona conocida de Intune/PM si tiene alguna pregunta o problema.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

> [!Note]
> Los siguientes cambios están en fase de desarrollo de Intune. Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="modernizing-the-company-portal-website---753980--"></a>Renovación del sitio web del portal de empresa<!--753980-->
A partir de febrero, el diseño del sitio web del portal de empresa se alineará con otros productos y servicios de Microsoft mediante una nueva combinación de colores de contraste, ilustraciones dinámicas y un "menú hamburguesa", ![pequeña imagen del menú hamburguesa que se agrega ahora a la esquina superior izquierda del sitio web del portal de empresa](./media/CP_hamburger_menu.png) que contendrá los detalles de contacto del departamento de soporte técnico e información sobre los dispositivos administrados existentes. La página de inicio se reorganizará para destacar las aplicaciones que están disponibles para los usuarios, con carruseles para aplicaciones destacadas y actualizadas recientemente. Puede encontrar imágenes de antes y después disponibles en la [página de actualizaciones de la interfaz de usuario](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Nueva experiencia guiada del Portal de empresa de Windows 10<!--713927-->
A partir de marzo, el Portal de empresa para Windows 10 incluirá la experiencia de un tutorial de Intune guiado para dispositivos que no se han identificado ni inscrito. La nueva experiencia proporciona instrucciones paso a paso, personalizadas para la compilación de Windows 10 del usuario, que guían a los usuarios por la realización del registro en AAD (necesario para la identificación de las características de acceso condicional) y la inscripción de MDM (necesaria para características de administración de dispositivos). La experiencia guiada será accesible desde la página principal del Portal de empresa y es opcional; los usuarios pueden seguir usando la aplicación aunque no realicen la inscripción ni el registro, pero puede que experimenten funcionalidad limitada.

###

## <a name="notices"></a>Notificaciones

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>La migración de grupo no requiere actualizaciones a grupos ni directivas para dispositivos iOS <!--898837-->
Para cada grupo de dispositivos de Intune previamente asignado mediante un perfil de inscripción de dispositivos corporativos, se creará un grupo de dispositivos dinámico correspondiente en AAD según el nombre del perfil de inscripción de dispositivos corporativos, durante la migración a grupos de dispositivos de Azure Active Directory. Esto garantizará que, según se inscriban dispositivos, estos se agrupen de forma automática y reciban las mismas directivas y aplicaciones que el grupo de Intune original.

Una vez que un inquilino empieza el proceso de migración para agrupar y seleccionar el destino, Intune creará de forma automática un grupo dinámico de AAD para que se corresponda con un grupo de Intune destinado mediante un perfil de inscripción de dispositivos corporativos. Si el administrador de Intune elimina el grupo de destino de Intune, no se eliminará el grupo de AAD dinámico correspondiente. Se borrarán los miembros del grupo y la consulta dinámica, pero el propio grupo permanecerá hasta que el administrador de TI lo quite a través del portal de AAD.

De forma similar, si el administrador de TI cambia qué grupo de Intune es el destino de un perfil de inscripción de dispositivos corporativos, Intune crea un nuevo grupo dinámico que refleje la nueva asignación de perfil, pero no quitará el grupo dinámico creado para la asignación anterior.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Nueva dirección del servidor MDM para dispositivos Windows <!--893007-->
Se producirá un error en la inscripción del dispositivo si los usuarios de Windows y Windows Phone especifican __manage.microsoft.com__ como la dirección del servidor MDM (si se le pide). La dirección del servidor MDM cambia de __manage.microsoft.com__ a __enrollment.manage.microsoft.com__. Notifique al usuario que use __enrollment.manage.microsoft.com__ como la dirección del servidor MDM si se le pide durante la inscripción de un dispositivo Windows o Windows Phone. Esta actualización necesitará que cualquier CNAME en el DNS que redirija __EnterpriseEnrollment.contoso.com__ a __manage.microsoft.com__ se reemplace por un CNAME en el DNS que redirija __EnterpriseEnrollment.contoso.com__ a __EnterpriseEnrollment-s.manage.microsoft.com__. Para obtener información adicional sobre este cambio, visite [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nueva experiencia del usuario en la aplicación del portal de empresa para Android <!--621622-->
A partir de marzo, la aplicación del portal de empresa para Android seguirá las [directrices de Material Design](https://material.io/guidelines/material-design/introduction.html) para crear una apariencia más moderna. Esta experiencia del usuario mejorada incluye:

* __Colores__: los encabezados de pestaña pueden colorearse según la paleta de colores personalizada.
* __Interfaz__: los botones Aplicaciones destacadas y Todas las aplicaciones se han actualizado en la pestaña Aplicaciones. El botón Buscar ahora es un botón de acción flotante.
* __Navegación__: Todas las aplicaciones muestra una vista con pestañas de Destacadas, Todas y Categorías para navegar más fácilmente.
* __Servicio__: las pestañas Mis dispositivos y Contactar con TI han mejorado la legibilidad.

Puede encontrar imágenes de antes y después en la [página de actualizaciones de la interfaz de usuario](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Asociación de varias herramientas de administración con la Tienda Windows para empresas<!--926135-->
Si usa más de una herramienta de administración para implementar las aplicaciones de la Tienda Windows para empresas, anteriormente solo podía asociar una de ellas con la Tienda Windows para empresas. Ahora puede asociar varias herramientas de administración con la tienda, por ejemplo, Intune y Configuration Manager. Para más información, consulte [Administrar las aplicaciones adquiridas a través de la Tienda Windows para empresas con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Versión preliminar pública de la nueva experiencia de administración de Intune en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune).

Si tiene alguna pregunta sobre la programación de la migración de su inquilino, póngase en contacto con nuestro equipo de migración en [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="february-2017"></a>Febrero de 2017

#### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidad para restringir la inscripción de dispositivos móviles <!--747600, 795782-->
Intune está agregando nuevas restricciones de inscripción que controlan qué plataformas de dispositivos móviles pueden inscribir. Intune separa las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows y Windows Mobile.

* La restricción la inscripción de dispositivos móviles no restringe la inscripción del cliente de PC.  
* Solo para iOS y Android, hay una opción adicional para bloquear la inscripción de dispositivos de propiedad personal.

Intune marca todos los dispositivos nuevos como personal a menos que el administrador de TI tome la medida de marcarlos como propiedad de la empresa, como se explica en [este artículo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

#### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas las acciones en los dispositivos administrados <!--677150-->
Un nuevo informe __Acciones de dispositivo__ muestra quién ha realizado acciones remotas como el restablecimiento de fábrica en dispositivos y, además, muestra el estado de esa acción.

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Los dispositivos no administrados puedan acceder a aplicaciones asignadas <!--664691-->
Como parte de los cambios de diseño en el sitio web del portal de empresa, los usuarios de iOS y Android podrán instalar aplicaciones asignadas a ellos como "disponibles sin inscripción" en sus dispositivos no administrados. Con sus credenciales de Intune, los usuarios podrán iniciar sesión en el sitio web del portal de empresa y ver la lista de aplicaciones asignadas. Los paquetes de aplicación de las aplicaciones "disponibles sin inscripción" se encuentran disponibles para descargar a través del sitio web del portal de empresa. Las aplicaciones que requieren la inscripción para la instalación no se ven afectadas por este cambio, ya que se les pedirá a los usuarios que inscriban su dispositivo si quieren instalar esas aplicaciones.

#### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->
Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.
Consulte [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Cómo agregar una aplicación a Intune).

#### <a name="display-device-categories---814654--"></a>Mostrar categorías de dispositivos <!--814654-->
Ahora puede ver la categoría del dispositivo como una columna en la lista de dispositivos. También puede editar la categoría desde la sección de propiedades de la hoja de propiedades del dispositivo.

### <a name="january-2017"></a>Enero de 2017

#### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->
Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.

#### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748803--"></a>Asignar aplicaciones de línea de negocio en dispositivos inscritos y no inscritos <!--748803-->
Ahora puede asignar aplicaciones de línea de negocio desde la tienda a usuarios tengan o no inscritos sus dispositivos con Intune. Si el dispositivo de los usuarios no está inscrito con Intune, deben ir al sitio web del portal de empresa para instalarlo, en lugar de a la aplicación de portal de empresa.

### <a name="december-2016"></a>Diciembre de 2016

#### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integración de la administración de gastos de telecomunicaciones en la versión preliminar pública del portal de Azure<!--747605-->
Ahora estamos comenzando a realizar la integración de la versión preliminar con los servicios de administración de gastos de telecomunicaciones (TEM) dentro del portal de Azure. Puede usar Intune para exigir límites sobre el uso de datos nacionales y móviles. Comenzaremos estas integraciones con [Saaswedo](http://www.saaswedo.com). Para habilitar esta característica en su inquilino de prueba, [póngase en contacto con el soporte técnico de Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md) para obtener más información sobre los desarrollos recientes.

