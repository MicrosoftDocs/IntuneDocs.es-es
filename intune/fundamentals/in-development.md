---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7c4e5ed45455dda941fb0c61c989c12c57135d
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999330"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>En desarrollo para Microsoft Intune: octubre de 2019

Para ayudarle con la preparación y planeación, en esta página se enumeran las actualizaciones y características de la interfaz de usuario de Intune que están en desarrollo, pero que aún no se han publicado. Además:

- Si prevemos que tendrá que tomar medidas antes de realizar un cambio, haremos una publicación complementaria en el Centro de mensajes de Office.
- Cuando se publique una característica en producción, ya sea como versión preliminar o disponible de forma general, su descripción se quitará de esta página y se moverá a la [página Novedades](whats-new.md).
- Esta página y la [página Novedades](whats-new.md) se actualizan periódicamente. Compruebe si hay actualizaciones adicionales.
- Consulte el [plan de desarrollo de M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para conocer los plazos de tiempo y los productos estratégicos.

> [!Note]
> Estos elementos reflejan las expectativas actuales de Microsoft sobre las funcionalidades de Intune que se publicarán en una versión futura. Las fechas y las características individuales pueden cambiar. No todos los elementos que están en desarrollo tienen una descripción de la característica en esta página.

**Fuente RSS**: para recibir notificaciones cuando esta página se actualice, copie y pegue la dirección URL siguiente en el lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Administración de aplicaciones

### <a name="additional-app-configuration-variable-available----4969237----"></a>Variable de configuración de aplicación adicional disponible <!-- 4969237  -->
Al crear una directiva de configuración de aplicaciones, podrá incluir la variable de configuración `AAD Device ID` como parte de las opciones de configuración. En Intune, seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones** > **Agregar**. Escriba los detalles de la Directiva de configuración y seleccione **configuración para ver** la hoja **Opciones de configuración** .

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>Modo oscuro para iOS Portal de empresa <!-- 4911422  -->
El modo oscuro está planeado para el Portal de empresa de iOS. Descargue aplicaciones de la empresa, administre sus dispositivos y obtenga soporte técnico en la combinación de colores que prefiera. Para más información sobre el Portal de empresa de iOS, consulte [Configuración de la aplicación Portal de empresa de Microsoft Intune](../apps/company-portal-app.md).

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Impedir la instalación de aplicaciones desde orígenes desconocidos en dispositivos empresariales Android <!-- 4760025  -->
En el caso de un dispositivo de Perfil de trabajo de Android Enterprise, nunca es posible que los usuarios finales instalen aplicaciones de orígenes desconocidos en el perfil de trabajo. También podrá extender esta restricción también al perfil personal de la. Si habilita esta restricción, los usuarios finales de los dispositivos de Perfil de trabajo empresarial de Android también se evitarán de las aplicaciones de carga de prueba de los orígenes desconocidos en el lado personal de su dispositivo. 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>Actualizar la interfaz de usuario de protección de aplicaciones y la interfaz de usuario de aprovisionamiento de aplicaciones de iOS <!-- 4102027, 4102029  -->
La interfaz de usuario para crear y editar las directivas de protección de aplicaciones y los perfiles de aprovisionamiento de aplicaciones de iOS en Intune se actualizarán. Los cambios de la UI son:
- Una experiencia simplificada mediante el uso de un formato de estilo de asistente condensado dentro de una hoja. 
- Una actualización del flujo de creación para incluir asignaciones.
- Página resumida de todos los elementos que se establecen al ver las propiedades, antes de crear una nueva Directiva o al editar una propiedad. Además, al editar las propiedades, el Resumen solo mostrará una lista de elementos de la categoría de propiedades que se van a editar.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Crear grupos de objetos de administración denominados conjuntos de directivas <!-- 3762880  -->
Los conjuntos de directivas permiten crear una agrupación de referencias a entidades de administración ya existentes que deben identificarse, dirigirse y supervisarse como una sola unidad conceptual. Los conjuntos de directivas no reemplazan los conceptos ni los objetos existentes. Un administrador puede seguir asignando objetos individuales como lo hacen hoy. Un conjunto de directivas hace referencia a los objetos individuales. Por lo tanto, cualquier cambio que se realice en esos objetos individuales se reflejará en el conjunto de directivas.  En Intune, seleccionará **conjuntos de directivas** > **crear** para crear un nuevo conjunto de directivas. 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Aplicaciones Win32 en dispositivos de modo Windows 10 S <!-- 3747604  --> 
Podrá instalar y ejecutar aplicaciones Win32 en dispositivos administrados en modo Windows 10 S. Podrá crear una o varias directivas complementarias para el modo S mediante las herramientas de PowerShell de Windows Defender Application control (WDAC). Firme las directivas complementarias con el portal de firma de Device Guard y, después, cargue y distribuya las directivas a través de Intune. En Intune, encontrará esta funcionalidad seleccionando **aplicaciones cliente** > **directivas complementarias de Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Establecer la disponibilidad de la aplicación en función de una fecha y hora <!-- 3510685  -->
Como administrador, podrá configurar la hora de inicio y la hora de la fecha límite para una aplicación requerida. A la hora de inicio, la extensión de administración de Intune iniciará la descarga del contenido de la aplicación y la almacenará en caché. La aplicación se instalará en el momento de la fecha límite. En el caso de las aplicaciones disponibles, la hora de inicio se determinará cuando la aplicación esté visible en Portal de empresa. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones**. Después, seleccione una aplicación específica de la lista o haga clic en **Agregar** para agregar una nueva aplicación. En la hoja de la aplicación, seleccione **asignaciones** > **Agregar grupo**. Establezca el **tipo de asignación** en **requerido** y, a continuación, seleccione **grupos incluidos**. Establezca **que esta aplicación sea necesaria para todos los usuarios** en **sí** y seleccione **Editar** para modificar las opciones de **experiencia del usuario final** . En la hoja **experiencia del usuario final** , establezca la **hora disponible del software** según sea necesario. Para más información sobre cómo agregar aplicaciones, consulte[Incorporación de aplicaciones a Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Requerir que las aplicaciones Win32 se reinicien <!-- 3136567  -->
Podrá requerir que se reinicie una aplicación Win32 después de una instalación correcta. Además, podrá elegir la cantidad de tiempo (el período de gracia) antes de que se produzca el reinicio.

### <a name="company-portal-app-on-windows----1808082----"></a>Portal de empresa aplicación en Windows <!-- 1808082  -->
La aplicación Portal de empresa en dispositivos Windows se actualizará para mostrar las notificaciones del sistema a los usuarios, incluso cuando se cierre la aplicación. La actualización solo mostrará las notificaciones de las aplicaciones disponibles cuando el estado de la instalación sea completado o erróneo. La aplicación Portal de empresa no mostrará notificaciones de las aplicaciones necesarias.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Portal de empresa mensajes de estado de instalación de aplicaciones <!-- 2514416  -->
La aplicación Portal de empresa mostrará mensajes de estado de instalación de aplicaciones adicionales a los usuarios finales. Las condiciones siguientes se aplicarán a las nuevas características de dependencia de Win32:
- No se pudo instalar la aplicación. No se cumplieron las dependencias definidas por el administrador.
- La aplicación se instaló correctamente, pero requiere un reinicio.
- La aplicación está en proceso de instalación, pero requiere un reinicio para continuar.

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Asignación de la versión beta de Microsoft Edge para macOS <!-- 4678761  -->
Podrá agregar y asignar la versión más reciente de Microsoft Edge beta a Intune para dispositivos macOS. En Intune, seleccione **aplicaciones cliente** > **aplicaciones** > **Agregar aplicación** > **Microsoft Edge-MacOS**. A continuación, asigne la versión beta de Microsoft Edge a los grupos deseados. Microsoft AutoUpdate (MAU) mantiene Microsoft Edge actualizado. Para obtener más información sobre Microsoft Edge, consulte [Administración del acceso web con Microsoft Edge con Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar el contenido de notificación de aplicación para las cuentas de la organización <!-- 2576686 -->
Las directivas de protección de aplicaciones (APP) de Intune en dispositivos iOS y Android le permitirán controlar el contenido de las notificaciones de la aplicación para las cuentas de la organización. Esta característica requerirá la compatibilidad de las aplicaciones y es posible que no esté disponible para todas las aplicaciones habilitadas para la aplicación. Consulte [¿Qué son las directivas de protección de aplicaciones?](../apps/app-protection-policy.md) para obtener más información sobre APP.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Notificación de aplicaciones de Google Play disponibles para perfiles de trabajo de Android <!-- 3041956  -->
En las instalaciones de aplicaciones disponibles en dispositivos de perfil de trabajo de Android, puede ver el estado de instalación de la aplicación y la versión instalada de aplicaciones administradas de Google Play. Para obtener más información, vea [Supervisión de las directivas de protección de aplicaciones](../apps/app-protection-policies-monitor.md), [Administrar dispositivos de perfil de trabajo Android con Intune](../enrollment/android-enterprise-overview.md) y [Tipo de aplicación de Google Play administrado](../apps/apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración de los dispositivos


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>Nuevas opciones de configuración de dispositivos para dispositivos iOS y iPados supervisados <!-- 5199328  -->
En dispositivos iOS y iPad, puede crear un perfil para restringir las características y la configuración en los dispositivos (**configuración de dispositivo** > **perfiles** > **crear perfil** > **iOS/iPad** para el dispositivo de > de plataforma  **restricciones** para el tipo de perfil). Habrá nuevas opciones de configuración que puede controlar: 
- Acceder a la unidad de red en la aplicación archivos  
- Acceso a la unidad USB en la aplicación archivos 
- Wi-Fi siempre activado 

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md).

Se aplica a:
- iOS 13.0 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>La opción conectar automáticamente se quita en perfiles de Wi-Fi en Android y Android Enterprise <!-- 5021055  -->
En los dispositivos Android y Android Enterprise, puede crear un perfil de Wi-Fi para configurar diferentes opciones (**configuración de dispositivo** > **perfiles** > **crear perfil** > **Android** o **Android Enterprise** para la plataforma > **Wi-Fi** para el tipo de perfil). Se quitará el valor **conectar automáticamente** , ya que [no es compatible con Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Si utiliza esta configuración en un perfil de Wi-Fi, es posible que observe que la conexión no funcionará **automáticamente** . No es necesario realizar ninguna acción, pero tenga en cuenta que esta configuración se quita en la interfaz de usuario de Intune.

Para ver la configuración actual, vaya a configuración de [Wi-Fi de Android](../configuration/wi-fi-settings-android.md) o [configuración de Wi-Fi de Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

Se aplica a:
- Android
- Android Enterprise

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>Creación de un proxy HTTP global en dispositivos de propietario de dispositivos empresariales Android <!-- 4816339  -->
En dispositivos Android Enterprise, puede configurar un proxy HTTP global para cumplir los estándares de exploración Web de su organización (**configuración de dispositivo** >  **perfiles** > **crear perfil** > **Android Enterprise** para Plataforma > **propietario del dispositivo > restricciones de dispositivo** para el tipo de perfil > **Conectividad**). Una vez configurado, todo el tráfico HTTP usará este proxy.

Se aplica a:
- Propietario del dispositivo Android Enterprise

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>Nuevo perfil de interfaz de configuración de firmware de dispositivo para dispositivos con Windows 10 y versiones posteriores <!-- 2266073  -->
En Windows 10 y versiones posteriores, puede crear un perfil de configuración de dispositivo para controlar la configuración y las características (**configuración de dispositivo** > **perfiles** > **crear perfil** > **Windows 10 y versiones posteriores** para la plataforma). Habrá un nuevo tipo de Perfil de interfaz de configuración de firmware de dispositivo que permite a Intune administrar la configuración de UEFI (BIOS).

Para ver una visión general de todos los valores de configuración actuales que puede configurar, consulte [Aplicar características y configuraciones en los dispositivos con perfiles de dispositivo en Microsoft Intune](../configuration/device-profiles.md).

Se aplica a:
- Windows 10 RS5 (1809) y versiones más recientes en dispositivos seleccionados

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>Certificados PKCS para macOS  <!-- 1333650                -->
Agregaremos soporte completo para los certificados PKCS en los dispositivos que ejecutan macOS. Los usuarios podrán implementar certificados de usuario y de dispositivo con los campos de nombre alternativo del sujeto y del asunto de personalización. También tendremos un nuevo valor para permitir el acceso de todas las aplicaciones, lo que permite que todas las aplicaciones asociadas tengan acceso a la clave privada. Para obtener más detalles sobre esta configuración, visite la siguiente documentación de Apple: https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>Credenciales derivadas para aprovisionar dispositivos móviles con certificados      <!--  1736036, 1736037, 1772050      --> 
Agregaremos compatibilidad con las credenciales derivadas, que admiten el estándar *National Institute of Standards and Technology (NIST) 800-157* para la implementación de certificados en los dispositivos.  Las credenciales derivadas se basan en el uso de una tarjeta de comprobación de identidad personal (PIV) o tarjeta de acceso común (CAC), como una tarjeta inteligente. Los usuarios se autentican con su tarjeta inteligente en un equipo y, a continuación, envían una solicitud de certificado para su dispositivo administrado siguiendo el proceso que requiere el proveedor de credenciales derivado.   

El proceso para usar las credenciales derivadas para obtener un certificado es diferente del uso de perfiles de certificado SCEP o PKCS, pero el resultado final es el mismo: dispositivos móviles con certificados para la autenticación que se pueden usar para la autenticación de aplicaciones, VPN, Wi-Fi o correo electrónico. File.   

Para obtener más información, vea [credenciales de PIV derivadas](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) en www.nccoe.NIST.gov.

La versión inicial de las credenciales derivadas será compatible con Entrust Datacard, intervenir y DISA purebred en iOS. En versiones posteriores se admitirán plataformas adicionales y proveedores de credenciales derivadas.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscripción de dispositivos

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>Especificar las versiones del sistema operativo del dispositivo Android que se inscriben con el perfil de trabajo o la inscripción del administrador de dispositivos <!-- 4350697 -->
Con las restricciones de tipo de dispositivo de Intune, podrá usar la versión del sistema operativo del dispositivo para especificar qué dispositivos de usuario usarán la inscripción de Perfil de trabajo de Android Enterprise o la inscripción de administrador de dispositivos Android. Para ello, vaya a **Intune** > **inscripción de dispositivo** > **restricciones de inscripción** > **crear restricción** > **restricción de tipo de dispositivo** > **configuración de plataforma**.

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>Editar el valor de nombre de dispositivo para dispositivos AutoPilot <!-- 4816775 -->
Podrá editar el valor de nombre de dispositivo para los dispositivos AutoPilot Azure AD Unidos. Para ello, vaya a **Intune** > **inscripción de dispositivos** > **inscripción de Windows** > **dispositivos** **Windows autopilot** >  > elija el dispositivo > cambiar el valor de nombre de dispositivo en el panel derecho > **Guardar** .

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Para dispositivos iOS, personalice la pantalla de privacidad del proceso de inscripción del Portal de empresa. <!-- 4394993  -->
Con Markdown, podrá personalizar la pantalla de privacidad del Portal de empresa que los usuarios finales ven durante la inscripción de iOS. En concreto, podrá personalizar la lista de elementos que la organización no puede ver o realizar en el dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Administración de dispositivos


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>Editar valor de etiqueta de grupo para dispositivos AutoPilot<!-- 4816775 -->
Podrá editar el valor de la etiqueta de grupo para dispositivos AutoPilot. Para ello, vaya a **Intune** > **inscripción de dispositivos** > **inscripción de Windows** > **dispositivos** **Windows autopilot** >  > elija el dispositivo > cambiar el valor de la etiqueta de grupo en el panel derecho > **Guardar** .

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Actualización de la interfaz de usuario para crear y editar anillos de actualización de Windows 10  <!-- 4099089          -->   
Vamos a implementar una experiencia de interfaz de usuario de creación y edición actualizada para los anillos de actualización de Windows 10 para Intune.  Los cambios en la interfaz de usuario incluirán:  
- Simplifique la experiencia existente con un formato de estilo de asistente condensado dentro de una hoja. Esta actualización de la interfaz de usuario se desplazará con la expansión de la hoja que requiere que los profesionales de ti exploren los recorridos profundos de la hoja.   
- Revise el flujo de creación para incluir asignaciones.  
- La adición de una página resumida de todos los elementos que se establecen al ver las propiedades, antes de crear un nuevo anillo de actualización, y al editar una propiedad. Al editar, en el resumen solo se mostrará la lista de elementos establecidos en la primera categoría de propiedades editadas.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>Actualización de la interfaz de usuario para crear y editar actualizaciones de software de iOS  <!-- 4099090        -->   
Vamos a implementar una experiencia de interfaz de usuario de creación y edición actualizada para las actualizaciones de software de iOS en Intune. Los cambios en la interfaz de usuario incluirán:
- Simplifique la experiencia existente con un formato de estilo de asistente condensado dentro de una hoja. Esta actualización de la interfaz de usuario se desplazará con la expansión de la hoja que requiere que los profesionales de ti exploren los recorridos profundos de la hoja.  
- La creación del flujo de la Directiva de actualización de software de iOS se actualizará para incluir asignaciones. 
- La Directiva de actualización de software de iOS incluirá una página resumida de todo lo que se establece al ver las propiedades, antes de crear una nueva Directiva y al editar una propiedad. Al editar, en el resumen solo se mostrará la lista de elementos establecidos en la primera categoría de propiedades editadas.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Dirigirse a los grupos de usuarios de macOS para requerir la administración de Jamf <!-- 4061739 -->
Podrá dirigirse a grupos específicos de usuarios para requerir que los dispositivos macOS estén administrados por Jamf. Este destino le permitirá aplicar la integración de cumplimiento de Jamf a un subconjunto de dispositivos macOS mientras que otros dispositivos siguen siendo administrados por Intune. También le permite migrar gradualmente los dispositivos de los usuarios de un MDM a otro.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Nuevas restricciones para cambiar el nombre de dispositivos Windows <!-- 3478938 -->
Los nombres de los dispositivos deberán seguir estas reglas:
- 15 caracteres o menos (debe ser menor o igual que 63 bytes, sin incluir el valor nulo final)
- Cadena no nula o vacía
- ASCII permitido: Letras (a-z, A-Z), números (0-9) y guiones
- Unicode permitido: los caracteres > = 0x80, deben ser UTF8 válidos, debe ser IDN-asignable (RtlIdnToNameprepUnicode se realiza correctamente; consulte RFC 3492).
- Los nombres no deben contener solo números o empezar por un número.
- No hay espacios en el nombre
- Caracteres no permitidos: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Implementar actualizaciones de software en dispositivos macOS <!-- 3194876 -->
Podrá implementar actualizaciones de software en grupos de dispositivos macOS. Esta característica incluye el archivo crítico, el firmware, el archivo de configuración y otras actualizaciones. Podrá enviar actualizaciones en la siguiente protección del dispositivo o seleccionar una programación semanal para implementar actualizaciones dentro o fuera de las ventanas que establezca. Esta característica le ayuda cuando desea actualizar dispositivos fuera de las horas de trabajo estándar o cuando el Departamento de soporte técnico está totalmente personal. También obtendrá un informe detallado de todos los dispositivos macOS con actualizaciones implementadas. Puede profundizar en el informe en función de cada dispositivo para ver los Estados de las actualizaciones determinadas.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>Página de información general sobre nuevos informes de Android en dispositivos <!-- 2984353  -->
Vamos a agregar un nuevo informe a la página de información general de dispositivos que muestra el número de dispositivos Android inscritos en cada solución de administración de dispositivos. Este gráfico mostrará el perfil de trabajo, los recuentos de dispositivos inscritos completamente administrados, dedicados y del administrador de dispositivos. Para ver el informe, elija **Intune** > **dispositivos** > **Introducción**.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Informes de implementación de Windows Autopilot <!-- 3856172  -->
Un nuevo informe detallará cada dispositivo implementado a través de Windows AutoPilot. Estos datos estarán disponibles durante 30 días después de la implementación. Para ver el informe, vaya a **Intune** > **inscripción de dispositivos** > **supervisar** **implementaciones de AutoPilot** > .

### <a name="updated-support-experience-------5012398------"></a>Experiencia de soporte actualizada   <!--  5012398    -->
Como parte de las mejoras continuas, actualizaremos la experiencia de soporte técnico en la consola de Intune.  Vamos a mejorar la búsqueda en la consola y los comentarios de los problemas comunes y a optimizar el flujo de trabajo para ponerse en contacto con el soporte técnico.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.




