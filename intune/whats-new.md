---
title: Novedades de Microsoft Intune (Azure) | Microsoft Docs
titlesuffix: ''
description: Descubra las novedades del portal de Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: d7fd8c7f6f2c3dd5e6e8af323ccbb41a1ab779df
ms.sourcegitcommit: 814d1d473de2de2e735efab826b1091de2b093f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025243"
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Conozca las novedades semanales de Microsoft Intune. También podrá obtener información sobre los [próximos cambios](#whats-coming), [notificaciones importantes](#notices) sobre el servicio e información sobre las [versiones anteriores](whats-new-archive.md). Algunas características pueden lanzarse a lo largo de varias semanas y pueden no estar disponibles para todos los clientes durante la primera semana.

> [!Note]
> Para obtener más información sobre la nueva funcionalidad de administración híbrida de dispositivos móviles (MDM), consulte la [página Novedades de MDM híbrida](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     
## <a name="week-of-october-29-2018"></a>Semana del 29 de octubre de 2018


### <a name="app-management"></a>Administración de aplicaciones

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Requerir PIN que no sea biométrico después de un tiempo de expiración especificado <!-- 1506985 -->
Al exigir un número de identificación personal no biométrico después de transcurrir un tiempo de expiración especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más exhaustivo del acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos. Para obtener información sobre la configuración del acceso, vea la [configuración para iOS](app-protection-policy-settings-ios.md#access-settings) y la [configuración para Android](app-protection-policy-settings-android.md#access-settings).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Configuración de transferencia de datos de la aplicación de Intune en dispositivos iOS inscritos en MDM <!-- 2244713 -->
Podrá controlar por separado la configuración de la transferencia de datos de la aplicación de Intune en dispositivos iOS inscritos en MDM y la especificación de la identidad del usuario inscrito, que se conoce también como nombre principal de usuario (UPN). Los administradores que no usen el IntuneMAMUPN no observarán un cambio de comportamiento. Cuando esta función esté disponible, los administradores que usan el IntuneMAMUPN para controlar el comportamiento de la transferencia de datos en los dispositivos inscritos deben revisar la nueva configuración y actualizar la configuración de APP según sea necesario.

#### <a name="windows-10-win32-apps----2617325---"></a>Aplicaciones Win32 de Windows 10 <!-- 2617325 -->
Puede configurar las aplicaciones Win32 para instalarlas en el contexto de usuario para usuarios individuales, en comparación con la instalación de la aplicación para todos los usuarios del dispositivo.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Aplicaciones Win32 de Windows y scripts de PowerShell <!-- 2617330 -->
Los usuarios finales ya no tienen que iniciar sesión en el dispositivo para instalar las aplicaciones Win32 o ejecutar scripts de PowerShell. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Solución de problemas de instalación de la aplicación cliente <!-- 1363711 -->
Puede solucionar los problemas para que las aplicaciones cliente se instalen correctamente si consulta la columna etiquetada como **Instalación de la aplicación** en la hoja **Solución de problemas**. Para ver la hoja **Solución de problemas**, en el portal de Intune, seleccione **Solución de problemas** en **Ayuda y soporte técnico**.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693-wnready---"></a>Compatibilidad del control de acceso a la red en clientes VPN de iOS <!-- 1333693 wnready -->
Con esta actualización, hay una nueva configuración para habilitar el control de acceso de red (NAC) al crear un perfil de configuración de VPN de Cisco AnyConnect, F5 Access y Citrix SSO para iOS. Esta configuración permite que el identificador de NAC del dispositivo se incluya en el perfil de VPN. Actualmente, no existe ningún cliente de VPN ni solución de asociados de NAC que admita este nuevo identificador de NAC, pero le mantendremos informado en nuestra [entrada de blog de soporte técnico](ttps://aka.ms/iOS12_and_vpn) cuando estén disponibles.

Para usar NAC, deberá:
1. Optar por permitir que Intune incluya los identificadores de dispositivo en perfiles de VPN
2. Actualizar el software/firmware del proveedor de NAC con instrucciones directas de dicho proveedor

Para obtener información sobre esta configuración en un perfil de VPN para iOS, vea [Configuración de VPN en Microsoft Intune para dispositivos que ejecutan iOS](vpn-settings-ios.md). Para obtener más información sobre el control de acceso de red, vea [Integración del control de acceso de red (NAC) con Intune](network-access-control-integrate.md). 

Se aplica a iOS.

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Eliminar un perfil de correo electrónico de un dispositivo, incluso cuando hay un solo perfil de este tipo <!-- 1818139 -->
Antes no se podía quitar un perfil de correo electrónico de un dispositivo *si* era el único perfil de correo electrónico. Con esta actualización, se ha cambiado este comportamiento y ahora se puede quitar un perfil de correo electrónico aunque sea el único perfil de este tipo del dispositivo. Vea [Configuración del correo electrónico en Microsoft Intune](email-settings-configure.md) para obtener más información.

#### <a name="powershell-scripts-and-aad----2309469---"></a>Scripts de PowerShell y AAD <!-- 2309469 -->
Los scripts de PowerShell en Intune pueden estar dirigidos a grupos de seguridad de dispositivos de AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nueva configuración predeterminada "Tipo de contraseña requerida" para Android, Android Enterprise <!-- 2649963 -->
Al crear una directiva de cumplimiento (**Intune** > **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Android** o **Android Enterprise** para Plataforma > Seguridad del sistema), el valor predeterminado de **Tipo de contraseña requerida** cambiará:

De: Valor predeterminado del dispositivo A: Al menos numérica

Se aplica a: Android, Android Enterprise

Para ver esta configuración, vaya a [Android](compliance-policy-create-android.md) y [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usar una clave precompartida en un perfil de Wi-Fi de Windows 10 <!-- 2662938 -->
Con esta actualización, puede usar una clave precompartida (PSK) con el protocolo de seguridad WPA o WPA2-Personal para autenticar un perfil de configuración de Wi-Fi para Windows 10. También puede especificar la configuración de costo para una red de uso medido para la actualización del 10 de octubre de 2018 en dispositivos Windows 10.

Actualmente, debe importar un perfil de Wi-Fi o crear un perfil personalizado para usar una clave precompartida. [Configuración de Wi-Fi para Windows 10](wi-fi-settings-windows.md) muestra la configuración actual. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Eliminar certificados PKCS y SCEP de los dispositivos <!-- 3218390 -->
En algunos casos, los certificados PKCS y SCEP se conservaban en los dispositivos incluso si se quitaba una directiva de un grupo, se eliminaba una configuración o una implementación de cumplimiento, o bien un administrador actualizaba un perfil SCEP o PKCS existente. Esta actualización cambia el comportamiento. Hay algunos casos en los que los certificados PKCS y SCEP se quitan de los dispositivos y otros casos en los que dichos certificados se conservan. Vea [Eliminación de certificados SCEP y PKCS en Microsoft Intune](remove-certificates.md) para conocer estos casos.

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Usar un equipo selector para cumplimiento en dispositivos macOS <!-- 2504381 -->
Esta actualización incluye el equipo selector de macOS para evaluar el cumplimiento de los dispositivos. Para configurar la directiva del equipo selector, vea [Incorporación de una directiva de cumplimiento de dispositivos macOS con Intune](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="enrollment-abandonment-report----1382924---"></a>Informe de abandono de la inscripción <!-- 1382924 -->
Un nuevo informe en el que se proporciona información detallada sobre las inscripciones abandonadas está disponible en **Inscripción de dispositivos** > **Supervisión**. Para obtener más información, vea [Company portal abandonment report](enrollment-report-company-portal-abandon.md) (Informe de abandono del portal de empresa).

#### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Asignación de perfiles de AutoPilot al grupo virtual Todos los dispositivos<!--2715522 -->
Podrá asignar perfiles de AutoPilot al grupo virtual Todos los dispositivos. Para ello, elija **Inscripción de dispositivos** > **Inscripción Windows** > **Perfiles de implementación** > elija un perfil > **Tareas** > bajo **Asignar a** elija **Todos los dispositivos**. Para más información sobre los perfiles de Autopilot, vea [Inscribir dispositivos Windows con Windows Autopilot](enrollment-autopilot.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nuevos característica de términos de uso de Azure Active Directory <!-- 2870393 -->
Azure Active Directory tiene una característica de términos de uso que puede usar en lugar de los términos y condiciones existentes de Intune. La característica de términos de uso de Azure AD proporciona más flexibilidad sobre qué términos se van a mostrar y cuándo, mejor compatibilidad de localización, mayor control sobre cómo se representan los términos y creación de informes mejorada. La característica de términos de uso de Azure AD requiere Azure Active Directory Premium P1, que también forma parte del conjunto de aplicaciones Enterprise Mobility + Security E3. Para más información, vea el artículo [Administrar los términos y condiciones de acceso de los usuarios de su empresa](terms-and-conditions-create.md).

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Compatibilidad con AutoPilot para dispositivos híbridos unidos a Azure Active Directory (versión preliminar) <!-- 1048100-->
Ahora puede configurar dispositivos híbridos unidos a Azure Active Directory mediante AutoPilot. Los dispositivos deben estar unidos a la red de la organización para usar la característica de AutoPilot híbrida. Para más información, vea [Implementar dispositivos unidos a Azure AD híbrido mediante Intune y Windows Autopilot (versión preliminar)](windows-autopilot-hybrid.md).
Esta característica se implementará en toda la base de usuarios durante los próximos días. Por tanto, es posible que no pueda seguir estos pasos hasta que se implemente en su cuenta.

### <a name="android-device-owner-mode-support---3188762--"></a>Compatibilidad con el modo de propietario del dispositivo Android <!--3188762-->
Para Samsung Knox Mobile Enrollment, Intune ahora admite la inscripción de dispositivos en el modo de administración de propietario del dispositivo Android. Los usuarios en redes Wi-Fi o de telefonía móvil se pueden inscribir con unas pocas pulsaciones al encender sus dispositivos por primera vez. Para más información, vea [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Inscripción automática de dispositivos Android mediante Samsung Knox Mobile Enrollment).

### <a name="device-management"></a>Administración de dispositivos

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Agrupación de dispositivos inscritos en Windows Autopilot por identificador de correlación <!-- 2075110 -->
Intune ahora admite la agrupación de dispositivos Windows mediante un identificador de correlación cuando se inscriban mediante [AutoPilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) con Configuration Manager. El identificador de correlación es un parámetro del archivo de configuración de AutoPilot. Intune establecerá de forma automática el [atributo enrollmentProfileName de dispositivo de Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) para que sea igual a "OfflineAutopilotprofile-<correlator ID>". Esto permite la creación de grupos dinámicos de Azure AD arbitrarios en función del identificador de correlación a través del atributo enrollmentprofileName para las inscripciones de AutoPilot sin conexión. Para más información vea [Windows Autopilot para dispositivos existentes](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

### <a name="intune-app-protection-policies----2984657---"></a>Directivas de protección de aplicaciones de Intune <!-- 2984657 -->
Las directivas de protección de aplicaciones de Intune permiten configurar varias opciones de protección de datos para aplicaciones protegidas de Intune, como Microsoft Outlook y Microsoft Word. Se ha cambiado la apariencia de estas opciones para [iOS](app-protection-policy-settings-ios.md) y [Android](app-protection-policy-settings-android.md) a fin de facilitar su detección de forma individual. Hay tres categorías de configuraciones de directiva:
- **Reubicación de datos** : este grupo incluye los controles de prevención de pérdida de datos (DLP), como restricciones para cortar, copiar, pegar y guardar como. Esta configuración determina cómo los usuarios interactúan con los datos en las aplicaciones.
- **Requisitos de acceso**: este grupo contiene las opciones de PIN por aplicación que determinan cómo el usuario final tiene acceso a las aplicaciones en un contexto de trabajo.  
- **Inicio condicional** : este grupo contiene configuraciones como la configuración mínima del sistema operativo, la detección de dispositivos liberados o modificados y períodos de gracia sin conexión.  
  
No cambia la funcionalidad de la configuración, pero será más fácil encontrarla cuando se trabaja en el flujo de creación de la directiva. 

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune admitirá un tamaño de paquete máximo de 8 GB para las aplicaciones de línea de negocio <!-- 1727158 -->
Intune aumentó el tamaño de paquete máximo a 8 GB para las aplicaciones de línea de negocio (LOB). Para más información, vea [Agregar aplicaciones a Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Adición de una imagen de marca personalizada para la aplicación Portal de empresa <!-- 1916266 -->
Como administrador de Microsoft Intune, puede cargar una imagen de marca personalizada que se mostrará como imagen de fondo en la página de perfil del usuario en la aplicación Portal de empresa de iOS. Para obtener más información sobre cómo configurar la aplicación Portal de empresa, vea [How to configure the Microsoft Intune Company Portal app](company-portal-app.md) (Cómo configurar la aplicación Portal de empresa de Microsoft Intune).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune mantendrá el idioma de Office localizado al actualizar Office en los equipos de los usuarios finales <!-- 2971030 -->
Cuando Intune instala Office en los equipos de los usuarios finales, estos recibirán automáticamente los mismos paquetes de idioma que tenían con las instalaciones de Office .MSI anteriores. Para más información, vea [Asignación de aplicaciones de Office 365 a dispositivos Windows 10 con Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nueva experiencia de soporte técnico de Intune en el portal de administración de dispositivos de Microsoft 365 <!-- 3076965 -->
Se va a lanzar una nueva experiencia de ayuda y soporte técnico para Intune en el [portal de administración de dispositivos de Microsoft 365]( http://devicemanagement.microsoft.com). La nueva experiencia le permite describir el problema con sus propias palabras y recibir información sobre solución de problemas y contenido de corrección basado en la Web. Estas soluciones se ofrecen mediante un algoritmo de aprendizaje automático con reglas, basado en las consultas de los usuarios.  

Además de instrucciones específicas del problema, también puede utilizar el nuevo flujo de trabajo de creación de casos para abrir una incidencia de soporte técnico por teléfono o correo electrónico.  

Los clientes que forman parte del lanzamiento, esta nueva experiencia reemplaza la actual experiencia de ayuda y soporte técnico de un conjunto estático de opciones previamente seleccionadas que se basan en el área de la consola en la que se encuentra cuando abre la sección Ayuda y soporte técnico.  

*Esta nueva experiencia de ayuda y soporte técnico se va a lanzar para algunos pero no todos los inquilinos y está disponible en el portal de administración de dispositivos. Los participantes de esta nueva experiencia se seleccionan aleatoriamente entre los inquilinos de Intune disponibles. Se agregarán nuevos inquilinos a medida que se expanda el lanzamiento.*  

Para más información, vea [Nueva experiencia de ayuda y soporte técnico](get-support.md#new-help-and-support-experience) en Cómo obtener asistencia para Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----wnready-951068---"></a>Módulo de PowerShell para Intune: versión preliminar disponible <!-- wnready 951068 -->
Ya hay disponible en [GitHub]( https://aka.ms/intunepowershell) una versión preliminar de un nuevo módulo de PowerShell, que proporciona compatibilidad con la API de Intune a través de Microsoft Graph. Para obtener más información sobre cómo usar este módulo, consulte el archivo Léame en esa ubicación. 


## <a name="week-of-october-15-2018"></a>Semana del 15 de octubre de 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Solicitud de PIN al cambiar los identificadores de huella digital o cara en un dispositivo <!-- 2637704  -->
Se pide un PIN a los usuarios después de realizar cambios biométricos en su dispositivo iOS. Esto incluye cambios en las huellas digitales o los identificadores de cara registrados. El tiempo de la solicitud depende de la configuración del tiempo de espera de *Recheck access requirements after (minutes)* (Volver a comprobar los requisitos de acceso después de [minutos]).  Cuando no se establece ningún PIN, se solicita al usuario que establezca uno. 
 
Esta característica solo está disponible para iOS y requiere la participación de aplicaciones que integran Intune APP SDK para iOS, versión 9.0.1 o posterior. La integración del SDK es necesaria para que se pueda aplicar el comportamiento en las aplicaciones de destino. Esta integración ocurre de manera gradual y depende de los equipos de la aplicación específica. Algunas de las aplicaciones que participan son WXP, Outlook, Managed Browser y Yammer.


## <a name="week-of-october-1-2018"></a>Semana del 1 de octubre de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Acceso a las propiedades de perfil principales mediante la aplicación del Portal de empresa <!-- 772203 -->
Los usuarios finales pueden acceder ahora a las propiedades y acciones de cuenta principales, como el restablecimiento de contraseña, desde la aplicación del Portal de empresa. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Configuración de la directiva de protección de aplicaciones para el bloqueo de teclados de terceros en iOS <!-- 1248481 -->
En dispositivos iOS, los administradores de Intune pueden bloquear el uso de teclados de terceros al acceder a datos de la organización en aplicaciones protegidas mediante directivas. Cuando la directiva de protección de aplicaciones (APP) está configurada para bloquear teclados de terceros, el usuario del dispositivo recibe un mensaje la primera vez que interactúa con los datos corporativos al usar un teclado de terceros. Todas las demás opciones, que no afecten al teclado nativo, se bloquean y los usuarios de los dispositivos no podrán verlas. Los usuarios de los dispositivos verán el mensaje del cuadro de diálogo una vez. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Acceso a la cuenta de usuario de aplicaciones de Intune en dispositivos iOS y Android administrados <!-- 1248496 -->
Como administrador de Microsoft Intune, puede controlar qué cuentas de usuario se agregan a las aplicaciones de Microsoft Office en dispositivos administrados. Puede limitar el acceso solo a las cuentas de usuario de la organización permitidas y bloquear las cuentas personales en los dispositivos inscritos. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Directiva de configuración de aplicaciones iOS y Android para Outlook <!--1828527 -->
Ahora, puede crear una directiva de configuración de aplicaciones de Outlook iOS y Android para usuarios locales que aprovechan la autenticación básica con el protocolo ActiveSync. Se agregarán opciones de configuración adicionales a medida que se habiliten en Outlook para iOS y Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Paquetes de idioma de Office 365 Pro Plus <!-- 1833450 -->
Como administrador de Intune, podrá implementar idiomas adicionales para las aplicaciones Office 365 Pro Plus administradas mediante Intune. La lista de idiomas disponibles incluye el **Tipo** de paquete de idioma (núcleo, parcial y corrección). En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación** de la hoja **Agregar aplicación**, seleccione **Windows 10** en **Conjunto de aplicaciones de Office 365**. Seleccione **Idiomas** en la hoja **Configuración del conjunto de aplicaciones**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Extensiones de los archivos de aplicaciones de línea de negocio (LOB) de Windows <!-- 1884873 -->
Ahora, las extensiones de archivo de las aplicaciones de LOB de Windows incluirán las extensiones *.msi*, *.appx*, *.appxbundle*, *.msix* y *.msixbundle*. Puede agregar una aplicación en Microsoft Intune seleccionando **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. Se mostrará el panel **Agregar aplicación**, que permite seleccionar el **tipo de aplicación**. En el caso de las aplicaciones de LOB de Windows, seleccione la aplicación de **línea de negocio** como el tipo de aplicación, elija el **archivo de paquete de aplicación** y, después, especifique un archivo de instalación con la extensión adecuada.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Implementación de aplicaciones Windows 10 con Intune<!-- 2309001 -->
Aprovechando la compatibilidad actual con aplicaciones de línea de negocio (LOB) y Microsoft Store para aplicaciones empresariales, los administradores pueden usar Intune para implementar la mayoría de las aplicaciones existentes de su organización a los usuarios finales en dispositivos Windows 10. Los administradores pueden agregar, instalar y desinstalar aplicaciones para los usuarios de Windows 10 en una variedad de formatos, como archivos MSI, Setup.exe o MSP. Intune evaluará las reglas de requisitos antes de realizar la descarga y la instalación, y notificará a los usuarios finales del estado o los requisitos de reinicio a través del Centro de actividades de Windows 10. Esta función desbloqueará de manera eficaz las organizaciones interesadas en el desplazamiento de esta carga de trabajo a Intune y la nube. Esta característica está actualmente en versión preliminar pública y esperamos poder agregarle nuevas funciones importantes en los próximos meses. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menú de contenido de aplicaciones y dispositivos de usuario final <!-- 2771453 -->
Los usuarios finales ahora pueden usar el menú contextual de aplicaciones y dispositivos para desencadenar acciones comunes, como cambiar el nombre de un dispositivo o comprobar su cumplimiento. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Métodos abreviados de teclado del Portal de empresa de Windows <!-- 2771518 -->
Ahora, los usuarios finales podrán desencadenar acciones de aplicación y dispositivo en el Portal de empresa de Windows mediante métodos abreviados de teclado (aceleradores).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Creación de sufijos DNS en los perfiles de configuración de VPN en dispositivos que ejecutan Windows 10<!-- 1333668 -->
Cuando se crea un perfil de configuración del dispositivo VPN (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **VPN** para tipo de perfil), se escriben algunos valores de DNS. Con esta actualización, también puede especificar varios **sufijos DNS** en Intune. Al usar los sufijos DNS, puede buscar un recurso de red mediante su nombre corto, en lugar del nombre de dominio completo (FQDN). Esta actualización también le permite cambiar el orden de los sufijos DNS en Intune.
[Configuración de VPN de Windows 10](vpn-settings-windows-10.md#dns-settings) muestra la configuración de DNS actual.
Se aplica a dispositivos Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Compatibilidad con VPN siempre activa para perfiles de trabajo empresarial de Android <!-- 1333705 -->
En esta actualización, puede usar conexiones VPN siempre activas en dispositivos empresariales Android con perfiles de trabajo administrados. Las conexiones VPN siempre activas permanecen conectadas o se vuelven a conectar inmediatamente cuando el usuario desbloquea el dispositivo, cuando se reinicia el dispositivo o cuando cambia la red inalámbrica. También puede poner la conexión en modo “bloqueo”, que bloquea todo el tráfico de red hasta que la conexión VPN esté activa.
Puede habilitar la VPN siempre activa en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android empresarial** para plataforma > **Restricciones de dispositivo** > **Conectividad**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emitir certificados SCEP para los dispositivos sin usuario <!-- 1744554 -->
Actualmente, los certificados se emiten a los usuarios. Con esta actualización, se pueden emitir certificados SCEP para los dispositivos, incluidos los dispositivos sin usuario, como los quioscos multimedia (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Certificado SCEP** para perfil). Otras actualizaciones incluyen:
- La propiedad **Asunto** en un perfil SCEP pasará a ser un cuadro de texto personalizado y puede incluir nuevas variables. 
- La propiedad **Nombre alternativo del firmante (SAN)** en un perfil SCEP ahora es un formato de tabla y puede incluir nuevas variables. En la tabla un administrador puede agregar un atributo y rellenar el valor en un cuadro de texto personalizado. La SAN será compatible con los siguientes atributos: 
  - DNS
  - Dirección de correo electrónico
  - UPN

  Estas nuevas variables se pueden agregar con texto estático en un cuadro de texto de valor personalizado. Por ejemplo, el atributo DNS puede agregarse como `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Las llaves, los puntos y coma y los símbolos de barra vertical “ { } ; | ” no funcionará en el texto estático de la SAN. Las llaves solo deben rodear una de las nuevas variables de certificado de dispositivo que debe aceptar `Subject` o `Subject alternative name`. 

Nuevas variables de certificado de dispositivo:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` solo funciona para Windows y dispositivos unidos a dominios. 
>  -  Al especificar las propiedades del dispositivo como el IMEI, el número de serie y el nombre de dominio completo en el asunto o SAN para un certificado de dispositivo, tenga en cuenta que una persona con acceso al dispositivo podría suplantar estas propiedades. 

[Crear un perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile) enumera las variables actuales al crear un perfil de configuración de SCEP. 

Se aplica a: Windows 10 y versiones posteriores y iOS, compatible con Wi-Fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Bloquear dispositivos no compatibles de forma remota <!-- 2064495 -->
Cuando un dispositivo no cumple los requisitos, puede crear una acción en la directiva de cumplimiento que bloquee el dispositivo de forma remota. En Intune > **Cumplimiento del dispositivo**, cree una nueva directiva o seleccione una directiva existente > **Propiedades**. Seleccione **Acciones en caso de incumplimiento** > **Agregar** y elija bloquear de forma remota el dispositivo.
Compatible con: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 y versiones posteriores 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Mejoras de perfil de quiosco multimedia de Windows 10 y versiones posteriores en Azure Portal <!-- 2748224 -->
Esta actualización incluye las siguientes mejoras para el perfil de configuración de dispositivo de quiosco multimedia de Windows 10 (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Versión preliminar de quiosco** para tipo de perfil): 
- Actualmente, puede crear varios perfiles de quiosco multimedia en el mismo dispositivo. Con esta actualización, Intune admitirá un solo perfil de quiosco multimedia por dispositivo. Si necesita varios perfiles de quiosco multimedia en un único dispositivo, puede usar un URI personalizado.
- En un perfil de **Quiosco con varias aplicaciones**, puede seleccionar el tamaño del icono de la aplicación y el orden del **Diseño del menú inicio** en la cuadrícula de la aplicación. Si prefiere una mayor personalización, puede cargar un archivo XML.
- La configuración del explorador de quiosco multimedia pasará a estar en la configuración de **Quiosco**. Actualmente, la configuración **Explorador web del quiosco** tiene su propia categoría en Azure Portal.
Se aplica a: Windows 10 y versiones posteriores




### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Aplicar perfil de Autopilot para dispositivos Windows 10 inscritos que aún no están registrados para Autopilot <!-- 1558983 -->
Puede aplicar perfiles de Autopilot para dispositivos Windows 10 inscritos que aún no se han registrado para Autopilot. En el perfil de Autopilot, elija la opción **Convertir todos los dispositivos de destino a Autopilot** para registrar automáticamente los dispositivos que no se han registrado para Autopilot con los servicios de implementación de Autopilot. Permita un plazo de 48 horas para que se procese el registro. Cuando se anule la inscripción del dispositivo y este se restablezca, Autopilot lo aprovisionará.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Crear y asignar varios perfiles de la página Estado de inscripción a grupos de Azure AD <!-- 2526564 -->
Ya puede [crear y asignar](windows-enrollment-status.md) varios perfiles de la página Estado de inscripción a grupos de Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migración desde el Programa de inscripción de dispositivos a Apple Business Manager en Intune <!--2748613-->
Apple Business Manager (ABM) funciona en Intune, así que puede actualizar su cuenta desde el Programa de inscripción de dispositivos (DEP) a ABM. El proceso en Intune es el mismo. Para actualizar la cuenta de Apple de DEP a ABN, vaya a [ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Pestañas de estado de alerta e inscripción en la página de información general de inscripción de dispositivos <!--2748656-->
Ahora, las alertas y los errores de inscripción aparecen en pestañas distintas en la página de información general de inscripción de dispositivos.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Restricción de aplicaciones y bloqueo del acceso a los recursos de la compañía dispositivos Android <!-- 2451462  -->  
En **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Android**  >  **Seguridad del sistema**, hay un nuevo valor en la sección *Seguridad del dispositivo* que se llama **Aplicaciones restringidas**. El valor **Aplicaciones restringidas** usa una directiva de cumplimiento para bloquear el acceso a recursos de la compañía si ciertas aplicaciones están instaladas en el dispositivo. El dispositivo se considera no compatible hasta que las aplicaciones restringidas se quitan del dispositivo.
Se aplica a: 
- Android




## <a name="week-of-september-24-2018"></a>Semana del 24 de septiembre de 2018

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Centro de Administración de dispositivos de Microsoft 365 <!-- 3078424 -->
Una de las promesas de Microsoft 365 es la simplificación de la administración. Con los años, hemos ido integrando servicios de Microsoft 365 back-end para entregar escenarios de extremo a extremo, como el acceso condicional de Intune y Azure AD. El nuevo [Centro de administración de Microsoft 365](http://devicemanagement.microsoft.com) consolida, simplifica e integra la experiencia de administración. El área de trabajo especialista en administración de dispositivos proporciona fácil acceso a todas las tareas y la información relacionadas con la administración de dispositivos y aplicaciones que necesita su organización. Esperamos que esto se convierta en el área de trabajo principal en la nube para los equipos informáticos de usuario final de empresa.

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Compatibilidad con más entidades de certificación de terceros (CA) <!-- 3093107 -->
Si usa el protocolo de inscripción de certificados Simple (SCEP), ya puede emitir nuevos certificados y renovarlos en dispositivos móviles con Windows, iOS, Android y macOS.

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune cambia a compatibilidad con iOS 10 y versiones posteriores <!-- 2454656 -->  
Ahora la inscripción de Intune, el Portal de empresa y el explorador administrado incluyen dispositivos iOS que tengan solo la versión iOS 10 y posteriores. Para comprobar si hay dispositivos o usuarios que se vean afectados en la organización, vaya a Intune en Azure Portal > **Dispositivos** > **Todos los dispositivos**. Filtre por sistema operativo y, después, haga clic en **Columnas** para mostrar los detalles de la versión de sistema operativo. Pida a los usuarios que actualicen sus dispositivos a una versión del sistema operativo que sea compatible.  

Si posee o quiere inscribir alguno de los siguientes dispositivos, debe estar al tanto de que solo admiten iOS 9 y versiones anteriores.  Para seguir accediendo al Portal de empresa de Intune, debe actualizar estos dispositivos a dispositivos compatibles con iOS 10 o versiones posteriores:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3ª generación) 
* iPad (1ª generación)  

## <a name="week-of-september-17-2018"></a>Semana del 17 de septiembre de 2018

### <a name="app-management"></a>Administración de aplicaciones

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Quitar la duplicación de los iconos de estado de protección de la aplicación <!-- 3083391 -->
Los iconos **Estado del usuario para iOS** y **Estado del usuario para Android** estaban presentes en las páginas **Aplicaciones cliente: Información general** y **Aplicaciones cliente: Estado de protección de la aplicación**. Se han quitado los iconos de estado de la página **Aplicaciones cliente: Información general** para evitar la duplicación. 

## <a name="week-of-august-27-2018"></a>Semana del 27 de agosto de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Compatibilidad de túnel de paquete para perfiles de VPN por aplicación de iOS para los tipos de conexión Pulse Secure y personalizados <!-- 1520957 -->
Al usar perfiles de VPN por aplicación de iOS, puede elegir entre usar tunelización de capa de aplicación (app-proxy) o tunelización de nivel de paquete (packet-tunnel). Estas opciones están disponibles con los tipos de conexión siguientes:
- VPN personalizada
- Pulse Secure. Si no está seguro de qué valor usar, consulte la documentación de su proveedor de VPN.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Retraso cuando las actualizaciones de software de iOS se muestran en el dispositivo <!-- 1949583 -->
En Intune > **Actualizaciones de software** > **Directivas de actualización para iOS**, puede configurar los días y las horas en los que no desea que los dispositivos instalen ninguna actualización. En una actualización futura, podrá retrasar entre 1 y 90 días el momento en el que una actualización de software se muestra de forma visible en el dispositivo. 
[Configurar directivas de actualización de iOS en Microsoft Intune](software-updates-ios.md) enumera la configuración actual.

#### <a name="office-365-proplus-version----2213968---"></a>Versión de Office 365 ProPlus <!-- 2213968 -->
Al asignar las aplicaciones de Office 365 ProPlus a dispositivos Windows 10 mediante Intune, podrá seleccionar la versión de Office. En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones** > **Agregar aplicación**. Después, seleccione **Conjunto de aplicaciones Office 365 ProPlus (Windows 10)** en la lista desplegable **Tipo**. Seleccione **Configuración del conjunto de aplicaciones** para mostrar la hoja asociada. Establezca **Canal de actualización** en un valor, como **Mensualmente**. Si lo desea, quite otra versión de Office (msi) de los dispositivos del usuario final seleccionando **Sí**. Seleccione **Específico** para instalar una versión específica de Office del canal seleccionado en los dispositivos del usuario final. En este momento, en **Versión específica**, puede seleccionar la versión de Office que desee usar. Las versiones disponibles cambiarán con el tiempo. Por lo tanto, al crear una nueva implementación, las versiones disponibles pueden ser más recientes y no tener determinadas versiones anteriores disponibles. Las implementaciones actuales seguirán implementando la versión anterior, pero la lista de versiones se actualizará continuamente por canal. Para más información, vea [Información general de los canales de actualización para Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Compatibilidad con la configuración de DNS de registro para VPN de Windows 10 <!-- 2282852 -->
Con esta actualización, puede configurar perfiles de VPN de Windows 10 para registrar dinámicamente las direcciones IP asignadas a la interfaz VPN con el DNS interno, sin necesidad de usar perfiles personalizados.
Para obtener información sobre la configuración de perfil de VPN actual disponible, vea [Configuración de VPN de Windows 10](vpn-settings-windows-10.md). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>El instalador de Portal de empresa para macOS ahora incluye el número de versión en el nombre de archivo del instalador <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759-wnready---"></a>Actualizaciones de aplicaciones automáticas de iOS <!-- 2729759 wnready -->
Las actualizaciones de aplicaciones automáticas funcionan para las aplicaciones con licencia de dispositivo y usuario para la versión 11.0 de iOS y versiones posteriores.




### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello está dirigido a usuarios y dispositivos <!-- 1106609 -->
Cuando crea una directiva [Windows Hello para empresas](windows-hello.md), se aplica a todos los usuarios dentro de la organización (inquilinos). Con esta actualización, la directiva también se puede aplicar a determinados usuarios o específicos mediante una directiva de configuración de dispositivo (**Configuración del dispositivo** > **Perfiles**  >  **Crear perfil** > **Identity Protection** > **Windows Hello para empresas**).
En Intune en Azure Portal, la configuración de Windows Hello ahora existe tanto en **Inscripción del dispositivo** como en **Configuración del dispositivo**. **Inscripción del dispositivo** tiene como destino toda la organización (inquilinos) y es compatible con Windows AutoPilot (OOBE). **Configuración del dispositivo** tiene como destino los dispositivos y usuarios mediante una directiva que se aplica durante la inserción en el repositorio.
Esta característica se aplica a:  
- Windows 10 y versiones posteriores
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler es una conexión disponible para los perfiles VPN en iOS <!-- 1769858 -->
Cuando crea un perfil de configuración de dispositivo de VPN para iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > plataforma **iOS** > tipo de perfil **VPN**), hay varios tipos de conexión, incluidos Cisco, Citrix, etc. Esta actualización agrega Zscaler como un tipo de conexión. 
[Configuración de VPN para dispositivos que ejecutan iOS](vpn-settings-ios.md) enumera los tipos de conexión disponibles.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>Modo FIPS para perfiles de Wi-Fi de empresa para Windows 10 <!-- 1879077 -->
Ahora puede habilitar el modo Estándar federal de procesamiento de información (FIPS) para los perfiles de Wi-Fi de empresa para Windows 10 en Intune en Azure Portal. Asegúrese de que el modo FIPS está habilitado en la infraestructura de Wi-Fi si lo habilita en los perfiles de Wi-Fi.
En [Configuración de Wi-Fi para dispositivos Windows 10 y versiones posteriores en Intune](wi-fi-settings-windows.md) se muestra cómo crear un perfil de Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Control del modo S en Windows 10 y dispositivos posteriores: versión preliminar pública <!-- 1958649 -->
Con esta actualización de características, puede crear un perfil de configuración de dispositivo que haga cambiar el modo S de un dispositivo Windows 10 o evitar que los usuarios cambien el modo S del dispositivo. Esta característica está en Intune > **Configuración del dispositivo** > **Perfiles** >  **Windows 10 y versiones posteriores** > **Edition upgrade and mode switch (Actualización de edición y conmutación de modo)**.
En [Presentamos Windows 10 en modo S](https://www.microsoft.com/windows/s-mode) se proporciona más información sobre el modo S.
Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Paquete de configuración de ATP de Windows Defender agregado automáticamente al perfil de configuración <!-- 2144658 -->
Cuando se usa la [Protección contra amenazas avanzada y la incorporación](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) de dispositivos en Intune, antes era necesario descargar un paquete de configuración y agregarlo al perfil de configuración. Con esta actualización, Intune obtiene de forma automática el paquete del Centro de seguridad avanzada de Windows Defender y lo agrega al perfil.
Se aplica a Windows 10 y versiones posteriores.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Requerir que los usuarios se conecten durante la instalación del dispositivo <!--2311457-->
Ahora puede establecer los perfiles de dispositivo para requerir que el dispositivo se conecte a una red antes de continuar más allá de la página Red durante la instalación de Windows 10. Aunque esta característica está en versión preliminar, se requiere una compilación 1809 de Windows Insider o una versión posterior para usar esta configuración.
Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Restricción de aplicaciones y bloqueo del acceso a los recursos de la empresa en dispositivos iOS y Android Enterprise <!-- 2451462 -->
En **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **iOS** > **Seguridad del sistema**, hay una nueva opción **Aplicaciones restringidas**. Esta nueva opción usa una directiva de cumplimiento para bloquear el acceso a recursos de la compañía si ciertas aplicaciones están instaladas en el dispositivo. El dispositivo se considera no compatible hasta que las aplicaciones restringidas se quitan del dispositivo.
Se aplica a iOS.

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Actualizaciones de compatibilidad con VPN moderna para iOS <!-- 2459928, 1819876, and 2650856 -->
Esta actualización agrega compatibilidad con los siguientes clientes VPN de iOS: 
- F5 Access (versión 3.0.1 y versiones posteriores)
- SSO de Citrix
- GlobalProtect de Palo Alto Networks versión 5.0 y versiones posteriores. También en esta actualización:
- El nombre del tipo de conexión de **F5 Access** existente se cambia a **F5 Access Legacy** para iOS.
- El nombre del tipo de conexión de **GlobalProtect de Palo Alto Networks** existente se cambia a **GlobalProtect de Palo Alto Networks (legacy)** para iOS.
Los perfiles existentes con estos tipos de conexión siguen funcionando con su correspondiente cliente heredado de VPN. Si usa Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN o GlobalProtect de Legacy Palo Alto Networks versión 4.1 y versiones anteriores con iOS, debe cambiar a las nuevas aplicaciones. Hágalo tan pronto como sea posible para garantizar que el acceso VPN esté disponible para dispositivos iOS a medida que se actualicen a iOS 12.
Para obtener más información sobre iOS 12 y los perfiles de VPN, vea el [blog del equipo de soporte técnico de Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Exportación de las directivas de cumplimiento del Portal de Azure clásico para volver a crearlas en Intune en Azure Portal <!-- 2469637 -->
Las directivas de cumplimiento creadas en el Portal de Azure clásico dejarán de utilizarse. Puede revisar y eliminar todas las directivas de cumplimiento existentes, pero no podrá actualizarlas. Si tiene que migrar las directivas de cumplimiento a Intune en Azure Portal, puede exportarlas como un archivo separado por comas (archivo *.csv*). Después, use los detalles del archivo para volver a crear estas directivas en Intune en Azure Portal.

> [!IMPORTANT]
> Cuando se retire el Portal de Azure clásico, ya no podrá acceder ni ver las directivas de cumplimiento. Por tanto, asegúrese de exportar las directivas y volverlas a crear en Azure Portal antes de la retirada del Portal de Azure clásico.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile: nuevo socio de Mobile Threat Defense <!-- 22662717 -->
Puede controlar el acceso desde dispositivos móviles a los recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Better Mobile, una solución de Mobile Threat Defense integrada en Microsoft Intune.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Bloqueo del Portal de empresa en el modo de aplicación única hasta el inicio de sesión del usuario <!--1067692 --> 
Ahora tiene la opción de ejecutar Portal de empresa en el modo de aplicación única si autentica un usuario a través de Portal de empresa en lugar del Asistente para configuración durante la inscripción de DEP. Esta opción bloquea el dispositivo inmediatamente después de completar el Asistente para configuración, de manera que un usuario debe iniciar sesión para acceder al dispositivo. Este proceso garantiza que el dispositivo completa la incorporación y no está huérfano en un estado sin ningún usuario asociado.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Asignación de un usuario y un nombre descriptivo a un dispositivo AutoPilot <!--1346521 -->
Ahora puede [asignar un usuario a un único dispositivo Autopilot ](enrollment-autopilot.md). Los administradores también podrán proporcionar nombres descriptivos para saludar a los usuarios al configurar sus dispositivos con AutoPilot.
Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Use licencias de dispositivo de VPP para tener en servicio el Portal de empresa durante la inscripción de DEP <!-- 1608345 -->
Ahora puede usar licencias de dispositivo del Programa de compras por volumen (VPP) para aprovisionar previamente Portal de empresa durante las inscripciones en el Programa de inscripción de dispositivos (DEP). Para ello, al [crear o editar un perfil de inscripción](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), especifique el token de VPP que quiera usar para instalar Portal de empresa. Asegúrese de que el token no expire y que dispone de suficientes licencias para la aplicación de Portal de empresa. En los casos en los que el token expire o se agoten las licencias, Intune instalará el Portal de empresa del App Store (se solicitará un identificador de Apple).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmación requerida para eliminar el token de VPP que se usa para tener en servicio el Portal de empresa <!-- 2237634 -->
Ahora se solicita confirmación para eliminar un token del Programa de Compras por Volumen (VPP) si se usa para preaprovisionar el Portal de empresa durante la inscripción de DEP.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloqueo de inscripciones de dispositivos personales Windows <!-- 1849498 -->
Puede [bloquear la inscripción de dispositivos personales Windows](enrollment-restrictions-set.md#set-device-type-restrictions) con la [administración de dispositivos móviles](windows-enroll.md) en Intune. Los dispositivos inscritos con el [agente de PC de Intune](manage-windows-pcs-with-microsoft-intune.md) no se puede bloquear con esta característica. Esta característica se desplegará gradualmente durante las próximas semanas, por lo que quizá no la vea de inmediato en la interfaz de usuario.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Especificación de patrones de nombre de equipo en un perfil de AutoPilot <!--1849855-->
Puede [especificar una plantilla de nombre de equipo](enrollment-autopilot.md#create-an-autopilot-deployment-profile) para generar y establecer el [nombre de equipo](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante la inscripción de AutoPilot. Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Para los perfiles de Windows AutoPilot, oculte las opciones de cambio de cuenta en las páginas de inicio de sesión de la compañía y de error de dominio <!--1901669 -->
Hay [nuevas opciones de perfil de Windows AutoPilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile) para que los administradores oculten las opciones de cambio de cuenta en las páginas de inicio de sesión de la empresa y de error de dominio. La ocultación de estas opciones requiere que se configure la personalización de marca de empresa en Azure Active Directory. Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).



### <a name="device-management"></a>Administración de dispositivos

#### <a name="delete-jamf-devices----2653306--"></a>Eliminación de dispositivos Jamf <!-- 2653306-->
Puede eliminar los dispositivos administrados por JAMF desde **Dispositivos** > seleccione el dispositivo de Jamf > **Eliminar**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Cambio de terminología a "retirar" y "borrar" <!-- 2175759 -->
Para mantener la coherencia con Graph API, en la documentación y la interfaz de usuario de Intune se han cambiado los términos siguientes:
- **Eliminar datos de la compañía** se cambiará por "retirar".
- **Restablecimiento de fábrica** cambiará a **borrar**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Cuadro de diálogo de confirmación si el administrador intenta eliminar el certificado push MDM <!-- 297909500-->
Si alguien intenta eliminar un certificado push MDM de Apple, en un cuadro de diálogo de confirmación se muestra el número de dispositivos iOS y macOS relacionados. Si se elimina el certificado, será necesario volver a inscribir estos dispositivos.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Configuración de seguridad adicional de Windows Installer <!-- 2282430 -->
Puede dejar que los usuarios controlen las instalaciones de aplicaciones. Si lo permite, las instalaciones que antes se detendrían debido a una infracción de seguridad podrán seguir funcionando. Puede indicar a Windows Installer que use permisos elevados cuando instale un programa en un sistema. Además, los elementos protegidos por WIP (Windows Information Protection) se pueden indexar y los metadatos relativos a estos elementos se pueden almacenar en una ubicación sin cifrar. Cuando la directiva está deshabilitada, los elementos protegidos por WIP no se indexan y no se muestran en los resultados de Cortana o del explorador de archivos. La funcionalidad de estas opciones está deshabilitada de forma predeterminada. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968 -->
Tras escuchar las opiniones de los clientes, se han agregado características nuevas al sitio web de Portal de empresa. Experimentará una mejora considerable en las funciones y la facilidad de uso actual de los dispositivos. Se ha aplicado un nuevo diseño moderno y dinámico a las áreas del sitio, como los detalles del dispositivo, los comentarios, el soporte técnico y la descripción general del dispositivo. También verá:

- Flujos de trabajo simplificados en todas las plataformas del dispositivo
- Flujos mejorados para la identificación y la inscripción de dispositivos
- Mensajes de error más útiles
- Lenguaje más descriptivo y menos terminología técnica
- Capacidad de compartir vínculos directos a aplicaciones
- Rendimiento mejorado de los catálogos de aplicaciones de gran tamaño
- Mayor accesibilidad para todos los usuarios  

Se ha actualizado la [documentación del sitio web de Portal de empresa de Intune](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) para reflejar estos cambios. Para ver un ejemplo de las mejoras de la aplicación, vea [Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Detección de jailbreak mejorada en informes de cumplimiento<!-- 2198738 -->
Ahora la configuración de detección de jailbreak mejorada aparece en todos los informes de cumplimiento en la consola de administración.

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="scope-tags-for-policies---1081974---"></a>Etiquetas de ámbito para las directivas <!--1081974 -->
Puede crear [etiquetas de ámbito](scope-tags.md) para limitar el acceso a los recursos de Intune. Agregue una etiqueta de ámbito a una asignación de roles y luego agregue dicha etiqueta a un perfil de configuración. El rol solo tendrá acceso a los recursos con perfiles de configuración que tengan etiquetas de ámbito coincidentes (o no tengan ninguna etiqueta de ámbito).

## <a name="week-of-august-14-2018"></a>Semana del 14 de agosto de 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Compatibilidad de macOS para el Programa de inscripción de dispositivos de Apple <!-- 747651 -->
Intune ahora admite la inscripción de dispositivos macOS el Programa de inscripción de dispositivos de Apple (DEP). Para obtener más información, vea [Inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos de Apple](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Semana del 23 de julio de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Compatibilidad con aplicaciones de línea de negocio (LOB) para macOS <!-- 1895847 -->
Microsoft Intune permite implementar aplicaciones de LOB macOS como **Required** (Obligatoria) o como **Available with enrollment** (Disponible con inscripción). Los usuarios finales pueden obtener las aplicaciones implementadas como **Available** (Disponible) a través del Portal de empresa para macOS o del [sitio web del Portal de empresa](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Compatibilidad con aplicaciones integradas de iOS para pantalla completa <!-- 2051098 -->
Además de las aplicaciones de la Tienda y las aplicaciones administradas, ahora puede seleccionar una aplicación integrada (como Safari) que se ejecuta en pantalla completa en un dispositivo iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Editar implementaciones de aplicaciones de Office 365 Pro Plus <!-- 2150145 -->
Como administrador de Microsoft Intune, tiene más capacidad para editar las implementaciones de aplicaciones de Office 365 Pro Plus. Además, ya no tiene que eliminar las implementaciones para cambiar las propiedades del conjunto. En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Aplicaciones**. En la lista de aplicaciones, seleccione su conjunto de aplicaciones Office 365 ProPlus.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>El SDK para aplicaciones de Intune para Android actualizado ya está disponible <!-- 2744271-->

Hay disponible una versión actualizada del SDK para aplicaciones de Intune para Android compatible con la versión de Android P. Si es desarrollador de aplicaciones y usa el SDK de Intune para Android, debe instalar la versión actualizada del SDK para aplicaciones de Intune a fin de garantizar que la funcionalidad de Intune dentro de las aplicaciones Android seguirá funcionando según lo esperado en dispositivos de Android P. En esta versión del SDK para aplicaciones de Intune se proporciona un complemento integrado que lleva a cabo las actualizaciones del SDK. No es necesario que reescriba ningún código existente que ya esté integrado. Para detalles, consulte el artículo sobre el [SDK de Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Si usa el anterior estilo de distintivo para Intune, se recomienda usar el icono de maletín. Para detalles de personalización de la marca, consulte [este repositorio de GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Uso de S/MIME para cifrar y firmar varios dispositivos de un usuario <!-- 1333642 -->
Esta actualización incluye cifrado de correo electrónico S/MIME mediante un nuevo perfil de certificado importado (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > seleccione la plataforma > tipo de perfil **Certificado PKCS importado**). En Intune, puede importar los certificados en formato PFX. Después, Intune puede entregar esos mismos certificados a varios dispositivos inscritos por un solo usuario. Esto también incluye lo siguiente:

- El perfil de correo electrónico de iOS nativo permite habilitar el cifrado S/MIME mediante certificados importados en formato PFX.
- La aplicación de correo nativo de los dispositivos Windows Phone 10 usa automáticamente el certificado S/MIME.
- Los certificados privados se pueden entregar en varias plataformas. Aun así, no todas las aplicaciones de correo electrónico son compatibles con S/MIME.
- En otras plataformas, podría tener que configurar manualmente la aplicación de correo electrónico para habilitar S/MIME.  
- Las aplicaciones de correo electrónico que admiten el cifrado S/MIME pueden controlar la recuperación de certificados para el cifrado de correo electrónico S/MIME de una manera que no es compatible con un servicio MDM, por ejemplo, si los lee desde el almacén de certificados del publicador.

Compatible con: Windows, Windows Phone 10, macOS, iOS y Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Crear directiva de cumplimiento de dispositivos usando la configuración de firewall en dispositivos macOS <!-- 1497640 -->
Cuando se crea una directiva de cumplimiento de macOS (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Plataforma: macOS** > **Seguridad del sistema**), hay nuevas opciones de **Firewall** disponibles: 

- **Firewall**: configure cómo se administran las conexiones entrantes en el entorno.
- **Conexiones entrantes**: **bloquee** todas las conexiones entrantes excepto las necesarias para los servicios básicos de Internet, como DHCP, Bonjour e IPSec. Esta opción también bloquea todos los servicios de uso compartido.
- **Modo sigiloso**: **habilite** el modo sigiloso para evitar que el dispositivo responda a solicitudes de sondeo. El dispositivo sigue respondiendo a las solicitudes entrantes de las aplicaciones autorizadas.

Se aplica a: macOS 10.12 y versiones posteriores

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nuevo perfil de configuración de dispositivos Wi-Fi para Windows 10 y versiones posteriores <!-- 1879077 -->
Actualmente, puede importar y exportar perfiles de Wi-Fi mediante archivos XML. Con esta actualización, puede crear un perfil de configuración de dispositivo Wi-Fi directamente en Intune, igual que en otras plataformas.

Para crear el perfil, abra **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** > **Wi-Fi**. 

Se aplica a Windows 10 y versiones posteriores.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>La característica Quiosco (obsoleto) aparece atenuada y no se puede cambiar <!-- 2149998 -->
La [característica Quiosco](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** > **Restricciones de dispositivos**) está obsoleta y se sustituye por la [configuración de Quiosco para Windows 10 y versiones posteriores](kiosk-settings.md). Con esta actualización, la característica **Quiosco (obsoleto)** está atenuada y la interfaz de usuario no se puede modificar ni actualizar. 

Para habilitar el modo quiosco, vea [Configuración de quiosco para Windows 10 (y versiones posteriores)](kiosk-settings.md).

Se aplica a Windows 10 y versiones posteriores, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API para usar entidades de certificación de terceros <!-- 2184013 -->
En esta actualización, hay una API de Java que permite que las entidades de certificación de terceros se integren con Intune y SCEP. Después, los usuarios pueden agregar el certificado SCEP a un perfil y aplicarlo a los dispositivos mediante MDM.

Actualmente, Intune admite [solicitudes SCEP mediante Servicios de certificados de Active Directory](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Alternar para mostrar u ocultar el botón Finalizar sesión en un explorador de Quiosco <!-- 2455253 -->
Ahora puede configurar si los exploradores de Quiosco muestran o no el botón Finalizar sesión. Puede ver el control en **Configuración del dispositivo** > **Quiosco (versión preliminar)** > **Kiosk Web Browser**. Si está activado, cuando un usuario hace clic en el botón, la aplicación solicita confirmación para finalizar la sesión. Cuando se confirma, el explorador borra todos los datos de exploración y vuelve a la dirección URL predeterminada.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Creación de un perfil de configuración de red de telefonía móvil eSIM <!-- 2564077 -->
En **Configuración del dispositivo**, puede crear un perfil de red de telefonía móvil eSIM. Puede importar un archivo que contenga códigos de activación de red de telefonía móvil proporcionados por el operador de telefonía móvil. Después, puede implementar estos perfiles en sus dispositivos Windows 10 habilitados para eSIM LTE, como Surface Pro LTE y otros dispositivos compatibles con eSIM.

Compruebe si sus [dispositivos admiten perfiles de eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Se aplica a Windows 10 y versiones posteriores. 




### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Marcado automático de dispositivos Android inscritos mediante Samsung Knox Mobile Enrollment como "corporativos". <!-- 2404851 -->
De forma predeterminada, los dispositivos Android inscritos mediante Samsung Knox Mobile Enrollment ahora se marcan como **corporativos** en **Propiedad del dispositivo**. No es necesario identificar manualmente los dispositivos corporativos mediante IMEI o números de serie antes de realizar la inscripción mediante Knox Mobile Enrollment.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eliminación en masa de dispositivos en la hoja de dispositivos <!-- 1793693 -->

Ahora puede eliminar varios dispositivos a la vez en la hoja de dispositivos. Elija **Dispositivos** > **Todos los dispositivos** > seleccione los dispositivos que quiere eliminar > **Eliminar**. En el caso de los dispositivos que no se puedan eliminar, se mostrará una alerta.

## <a name="week-of-july-16-2018"></a>Semana del 16 de julio de 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Más oportunidades de sincronización en la aplicación Portal de empresa para Windows  
La aplicación Portal de empresa para Windows ahora permite iniciar una sincronización directamente desde la barra de tareas de Windows y el menú Inicio. Esta característica es especialmente útil si la única tarea es sincronizar los dispositivos y obtener acceso a los recursos corporativos. Para acceder a la nueva característica, haga clic con el botón derecho en el icono de Portal de empresa que está anclado a la barra de tareas o el menú Inicio. En las opciones de menú (también denominada lista de accesos directos), seleccione **Sincronizar este dispositivo**. El Portal de empresa se abrirá en la página **Configuración** e iniciará la sincronización. Para comprobar la nueva funcionalidad, vea [Novedades de la interfaz de usuario](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nuevas experiencias de navegación en la aplicación Portal de empresa para Windows  

Ahora al examinar o buscar aplicaciones en la aplicación Portal de empresa para Windows, puede alternar entre la vista **Iconos** existente y la vista **Detalles** recién agregada. En la nueva vista se muestran detalles de la aplicación, como el nombre, el editor, la fecha de publicación y el estado de la instalación.  

La vista **Instaladas** de la página **Aplicaciones** permite ver detalles sobre las instalaciones de aplicaciones completadas y en curso. Para ver el aspecto de la vista nueva, vea [Novedades de la interfaz de usuario](whats-new-app-ui.md).  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Mejora de la experiencia en la aplicación Portal de empresa para administradores de inscripciones de dispositivos  
Cuando un administrador de inscripciones de dispositivos (DEM) inicia sesión en la aplicación Portal de empresa para Windows, ahora la aplicación solo mostrará el dispositivo en ejecución actual de DEM. Esta mejora reducirá los tiempos de espera que se producían anteriormente cuando la aplicación intentaba mostrar todos los dispositivos inscritos en DEM.  


## <a name="week-of-july-9-2018"></a>Semana del 9 de julio de 2018

### <a name="app-management"></a>Administración de aplicaciones

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloqueo del acceso a aplicaciones según proveedores y modelos de dispositivos no aprobados <!-- 1425689 ! -->
El administrador de TI de Intune puede aplicar una lista específica de fabricantes de dispositivos Android o modelos de iOS a través de las directivas de Intune App Protection. El administrador de TI puede brindar una lista de fabricantes separados por punto y coma para las directivas Android y los modelos de dispositivo para las directivas iOS. Las directivas de Intune App Protection solo son para Android e iOS. Se pueden realizar dos acciones independientes en esta lista especificada:
- Bloquear el acceso a la aplicación en dispositivos no especificados.
- O bien, borrar de manera selectiva los datos corporativos en dispositivos no especificados. 

El usuario no podrá acceder a la aplicación de destino si no se cumplen los requisitos que establece la directiva. En función de la configuración, se podrá bloquear al usuario o borrar de manera selectiva sus datos corporativos dentro de la aplicación. En dispositivos iOS, esta característica requiere el uso de ciertas aplicaciones (como WXP, Outlook, Managed Browser o Yammer) para integrar Intune APP SDK para que esta característica se aplique en las aplicaciones de destino. Esta integración se produce de manera gradual y depende de los equipos de la aplicación específica. En Android, esta característica requiere la versión más reciente de Portal de empresa. 

En dispositivos de usuario final, el cliente de Intune actúa en función de una coincidencia simple de las cadenas especificadas en la hoja de Intune para directivas de protección de aplicaciones. Esto depende por completo del valor que informa el dispositivo. Por lo tanto, se recomienda que el administrador de TI se asegure de que el comportamiento previsto sea preciso. Para ello, pruebe esta configuración en función de una variedad de fabricantes de dispositivos y de modelos dirigidos a un grupo de usuarios pequeño. En Microsoft Intune, seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** para ver y agregar directivas de protección de aplicaciones. Para obtener más información sobre las directivas de protección de aplicaciones, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) y [Borrar los datos de forma selectiva mediante acciones de acceso de la directiva de protección de aplicaciones en Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Acceso a la compilación de versión preliminar del Portal de empresa de macOS <!-- 1734766 -->
Con Microsoft AutoUpdate, puede registrarse para recibir antes las compilaciones si se une al programa Insider. El registro le permite usar el Portal de empresa actualizado antes de que esté disponible para los usuarios finales. Para obtener más información, vea el [blog de Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Semana del 2 de julio de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Supervisar el estado de configuración de aplicaciones iOS por dispositivo <!-- 880037 -->
Como administrador de Microsoft Intune, puede supervisar el estado de configuración de aplicaciones iOS para cada dispositivo administrado. Desde **Microsoft Intune** en Azure Portal, seleccione **Dispositivos** > **Todos los dispositivos**. En la lista de dispositivos administrados, seleccione un dispositivo específico para mostrar una hoja para el dispositivo. En la hoja del dispositivo, seleccione **Configuración de aplicaciones**.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Acceso a acciones para las directivas de protección de aplicaciones <!-- 1483510 -->
Puede configurar directivas de protección de aplicaciones para borrar, bloquear o advertir de forma expresa los dispositivos que no cumplan directivas. La acción *borrado* quita los datos corporativos de su empresa de un dispositivo. Si se lleva a cabo esta acción, el usuario del dispositivo recibe una notificación sobre el motivo del borrado y los pasos para corregirlo. En el caso de algunas configuraciones, como la versión mínima de SO, podrá aplicar varias acciones, como el bloqueo o el borrado. Cabe reseñar que estas acciones se desencadenan cuando la aplicación se inicia.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Borrado selectivo de datos de aplicaciones de la organización <!-- 1507030 -->
Ahora, los administradores pueden configurar un borrado selectivo de los datos de la organización como una nueva acción cuando no se cumplan las condiciones de Configuración de acceso de las Directivas de protección de aplicaciones (APP).  Mediante esta característica, los administradores podrán proteger y eliminar automáticamente datos confidenciales de la organización en las aplicaciones, en función de criterios configurados previamente.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Revocar una aplicación iOS adquirida a través de PCV <!-- 1777384 -->
Como administrador de Microsoft Intune, puede revocar todas las licencias de una determinada aplicación iOS adquirida a través del Programa de Compras por Volumen de Apple (VPP). Puede notificar a los usuarios cuando una aplicación con licencia de usuario ya no esté asignada a ellos. Revocar una licencia de aplicación no desinstalará la aplicación VPP desde el dispositivo. Para desinstalar una aplicación VPP, debe cambiar la acción de asignación a **Desinstalar**. El número de licencias reclamadas se indicará en el nodo **Aplicaciones con licencia** en la carga de trabajo **Aplicación** de Intune. Para más información relacionada con las aplicaciones iOS de PCV, vea [How to manage iOS apps purchased through a volume-purchase program with Microsoft Intune](vpp-apps-ios.md) (Administración de aplicaciones iOS adquiridas a través de un Programa de Compra de Licencias por Volumen con Microsoft Intune).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Actualizaciones en los mensajes de no conformidad en la aplicación Portal de empresa <!-- 1832222 -->
Hemos revisado los mensajes que ven los usuarios cuando un dispositivo no es conforme. Estos mensajes conservan su significado original, pero se han actualizado con un lenguaje más descriptivo y menos jerga técnica. También se han actualizado los vínculos a la documentación y los pasos de corrección para mantenerlos actualizados.
Los textos siguientes son un ejemplo de las mejoras que verá en los mensajes:
- **Antes**: *Este dispositivo no ha contactado con el servicio de Intune en el período de tiempo especificado que requiere el administrador de TI. Para resolver este problema, abra la aplicación de Portal de empresa en el dispositivo y haga clic en el botón Comprobar cumplimiento.*
- **Después**:  *Hace tiempo que el dispositivo no se registra en la organización. Para volver a establecer una conexión, abra la aplicación de Portal de empresa en el dispositivo y pulse en Comprobar configuración del dispositivo.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Revocar licencias de aplicaciones iOS de PCV<!-- 1863797 -->
Como administrador, puede recuperar la licencia de una aplicación iOS de VPP asignada a un usuario o un dispositivo. Al desinstalar una aplicación iOS de PCV, también podrá recuperar la licencia de la aplicación. Antes de desinstalar la aplicación, hay que quitar el usuario o el dispositivo del grupo al que se destina la aplicación. Al quitarlos, se evita que la aplicación vuelva a instalarse. Tras completar estos pasos, puede optar por asignar la licencia de la aplicación a otro usuario o dispositivo. Para más información sobre las licencias de aplicaciones iOS de PCV, vea [Manage iOS volume-purchased apps in Microsoft Intune](vpp-apps-ios.md) (Administración de aplicaciones iOS compradas por volumen en Microsoft Intune).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Selección de las categorías de dispositivos mediante el valor de configuración Obtener acceso a trabajo o escuela <!-- 1058963 eenotready --> 
Si ha habilitado la [asignación de grupos de dispositivos](https://docs.microsoft.com/intune/device-group-mapping), ahora se pedirá a los usuarios de Windows 10 que seleccionen una categoría de dispositivo después de la inscripción a través del botón **Conectar** en **Configuración** > **Cuentas** > **Obtener acceso a trabajo o escuela**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Usar sAMAccountName como nombre de usuario de cuenta para perfiles de correo electrónico <!-- 1500307 -->
Puede usar el nombre local **sAMAccountName** como nombre de usuario de cuenta de los perfiles de correo electrónico para Android, iOS y Windows 10. También puede obtener el dominio de los atributos `domain` o `ntdomain` en Azure Active Directory (Azure AD). O si lo prefiere, podrá especificar un dominio estático personalizado.

Para usar esta característica, debe sincronizar el atributo `sAMAccountName` desde el entorno de Active Directory local con Azure AD.

Se aplica a [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 y versiones posteriores](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Ver perfiles de configuración de dispositivos en conflicto <!-- 1556983 -->
En **Configuración del dispositivo**, se muestra una lista de los perfiles existentes. Con esta actualización, se agrega una nueva columna que proporciona información detallada sobre los perfiles que tienen un conflicto. Puede seleccionar una fila en conflicto para ver la configuración y el perfil que tiene el conflicto. 

Obtenga más información sobre cómo [administrar perfiles de configuración](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Nuevo estado para dispositivos en la conformidad de dispositivos <!-- 2308882 -->
En **Conformidad de dispositivos** > **Directivas** > seleccione una directiva > **Información general**, se han agregado los estados nuevos siguientes:
- Correcto
- error
- Conflicto
- pendiente
- No aplicable: una imagen que también muestra el número de dispositivos de una plataforma diferente. Por ejemplo, si está buscando un perfil de iOS, el nuevo icono muestra el número de dispositivos que no son de iOS que también están asignados a este perfil. Vea [Directivas de cumplimiento de dispositivos](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Conformidad de dispositivos compatible con soluciones antivirus de terceros <!-- 2325484 -->
Cuando cree una directiva de cumplimiento de dispositivos (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Plataforma: Windows 10 y versiones posteriores** > **Configuración** > **Seguridad del sistema**), existen nuevas opciones disponibles de **[Seguridad del dispositivo](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)**: 
- **Antivirus**: cuando se establece en **Requerir**, puede comprobar la conformidad a través de soluciones antivirus registradas con Centro de seguridad de Windows, como Symantec y Windows Defender. 
- **Antispyware**: cuando se establece en **Requerir**, puede comprobar la conformidad a través de soluciones antispyware registradas con Windows Security Center, como Symantec y Windows Defender. 

Se aplica a: Windows 10 y versiones posteriores 

### <a name="device-enrollment"></a>Inscripción de dispositivos

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Dispositivos sin columna de perfiles en la lista de tokens del programa de inscripción <!-- 1853904 -->
En la lista de tokens del programa de inscripción hay una nueva columna que muestra el número de dispositivos sin un perfil asignado. Esto ayuda a los administradores a asignar perfiles a estos dispositivos antes de entregarlos a los usuarios. Para ver la nueva columna, vaya a **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción**.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Cambio de nombre en Google para Android for Work y Play for Work <!--842873 -->
Intune ha actualizado el término "Android for Work" para reflejar los cambios de personalización de marca de Google. Ya no se usan los términos "Android for Work" ni "Play for Work". Se usa otra terminología en función del contexto:
- "Android Enterprise" hace referencia a la pila de administración general de Android moderna.
- "Perfil de trabajo" o "Propietario de perfil" hacen referencia a dispositivos BYOD administrados con perfiles de trabajo.
- "Google Play administrada" hace referencia a la tienda de aplicaciones de Google.

#### <a name="rules-for-removing-devices----1609459---"></a>Reglas para quitar dispositivos <!-- 1609459 -->
Hay disponibles nuevas reglas que permiten quitar automáticamente dispositivos que no se hayan protegido durante un número de días que establezca. Para ver la nueva regla, vaya al panel **Intune**, seleccione **Dispositivos** y, luego, **Reglas de limpieza de dispositivos**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Compatibilidad con dispositivos Android de un solo uso y propiedad corporativa <!-- 1630973 -->

Ahora, Intune admite dispositivos Android de estilo quiosco, que estén bloqueados y con una elevada administración. De este modo, los administradores pueden bloquear aún más el uso de un dispositivo para restringir su uso a una sola aplicación o un pequeño conjunto de aplicaciones, impidiendo así que los usuarios habiliten otras aplicaciones o realicen otras acciones en el dispositivo. Para configurar el quiosco de Android, vaya a Intune > **Inscripción de dispositivos** > **Inscripción de Android** > **Inscripciones de dispositivos de tareas y quiosco**. Para obtener más información, vea [Set up enrollment of Android enterprise kiosk devices](android-kiosk-enroll.md) (Configurar la inscripción de dispositivos de quiosco de Android Enterprise).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Revisión por fila de los identificadores de dispositivos corporativos duplicados cargados <!-- 2203794-->
Ahora, al cargar identificadores corporativos, Intune facilita una lista de cualquier dispositivo duplicado y ofrece la posibilidad de reemplazar o conservar la información existente. El informe se mostrará si hay duplicados después de elegir **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar identificadores**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Agregar manualmente identificadores de dispositivos corporativos <!-- 2203803 -->
Ahora puede agregar manualmente identificadores de dispositivos corporativos. Elija **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar**. 

## <a name="week-of-june-25-2018"></a>Semana del 25 de junio de 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo, nuevo colaborador de Mobile Threat Defense <!-- 1169249 -->

Puede controlar el acceso desde dispositivos móviles a recursos corporativos en función de la evaluación de riesgos efectuada por Pradeo, una solución de Mobile Threat Defense integrada con Microsoft Intune.

## <a name="week-of-june-18-2018"></a>Semana del 18 de junio de 2018

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Compatibilidad móvil de Edge para directivas de Intune App Protection <!-- 1817882 -->

El navegador Microsoft Edge para dispositivos móviles ahora admite las directivas de protección de aplicaciones definidas en Intune.

## <a name="week-of-june-11-2018"></a>Semana del 11 de junio de 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Uso del modo FIPS con el conector de certificado NDES <!-- 1333688 -->
Al instalar el conector de certificado NDES en un equipo con el modo Estándar federal de procesamiento de información (FIPS) habilitado, la emisión y revocación de certificados no funciona según lo previsto. Con esta actualización, con el conector de certificado NDES se incluye la compatibilidad con FIPS. 

Esta actualización también incluye:

- El conector de certificado NDES requiere .NET 4.5 Framework, que se incluye automáticamente con Windows Server 2016 y Windows Server 2012 R2. Anteriormente, .NET 3.5 Framework era la versión mínima requerida.
- Con el conector de certificado NDES se incluye la compatibilidad con TLS 1.2. Por tanto, si el servidor con el conector de certificado NDES instalado es compatible con TLS 1.2, entonces se usará TLS 1.2. Si el servidor no admite TLS 1.2, entonces se usará TLS 1.1. Actualmente, se usa TLS 1.1 para la autenticación entre los dispositivos y el servidor.

Para obtener más información, vea [Configuración y uso de certificados SCEP](certificates-scep-configure.md) y [Configuración y uso de certificados PKCS](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Semana del 4 de junio de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Recuperación del identificador de modelo de usuario de la aplicación (AUMID) asociado para aplicaciones de Microsoft Store para Empresas en pantalla completa <!-- 1560077 ! -->
Intune ya puede recuperar los identificadores de modelo de usuario de la aplicación (AUMID) para aplicaciones de Microsoft Store para Empresas (WSfB) con el fin de mejorar la configuración del perfil de quiosco.

Para más información sobre las aplicaciones de Microsoft Store para Empresas, consulte el artículo sobre la [administración de aplicaciones de Microsoft Store para Empresas](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Nueva página de personalización de marca del Portal de empresa <!-- 1916370 -->
La página de personalización de marca del Portal de empresa tiene un nuevo diseño, mensajes e información sobre herramientas.


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Compatibilidad con perfiles de VPN de Palo Alto Networks GlobalProtect <!-- 1333680 ! -->
Con esta actualización, puede elegir Palo Alto Networks GlobalProtect como un tipo de conexión VPN para perfiles de VPN en Intune (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Tipo de perfil** > **VPN**). En esta versión, se admiten las siguientes plataformas: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adiciones a la configuración de opciones de seguridad del dispositivo local <!-- 1403702 -->
Ya puede configurar opciones adicionales de seguridad del dispositivo local para dispositivos con Windows 10. Las opciones adicionales están disponibles en las áreas Cliente de redes de Microsoft, Servidor de red Microsoft, Acceso y seguridad de red e Inicio de sesión interactivo. Encuentre estos valores en la categoría de Endpoint Protection cuando cree una directiva de configuración de dispositivo de Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Habilitación de la pantalla completa en dispositivos Windows 10 <!-- 1560072 ! -->
En los dispositivos Windows 10, puede crear un perfil de configuración y habilitar la pantalla completa (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Windows 10** > **Restricciones de dispositivos** > **Quiosco**). En esta actualización, la configuración **Quiosco (versión preliminar)** cambia de nombre a **Quiosco (obsoleto)**. Ya no se recomienda usar **Quiosco (obsoleto)**, pero seguirá funcionando hasta la actualización de julio. El nuevo tipo de perfil **Quiosco** reemplaza a **Quiosco (obsoleto)** (**Crear perfil** > **Windows 10** > **Quiosco (versión preliminar)**), que contendrá los valores para configurar Quioscos en Windows 10 RS4 y versiones posteriores.

Se aplica a Windows 10 y versiones posteriores.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Vuelve el gráfico de usuario del perfil del dispositivo <!-- 2160133 -->
Si bien mejoraba el valor numérico que aparece en el gráfico del perfil del dispositivo (**Configuración de dispositivos** > **Perfiles** > seleccione un perfil existente > **Información general**), el gráfico de usuario se quitó de manera temporal.

Con esta actualización, dicho gráfico vuelve y aparece en Azure Portal.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>Compatibilidad con la inscripción de Windows Autopilot sin autenticación de usuario <!-- 1165118 wnready -->
Intune admite la inscripción de Windows Autopilot sin autenticación de usuario. Se trata de una nueva opción en el perfil de implementación de Windows Autopilot "Modo de implementación Autopilot" establecido en "Self-Deploying" (Autoimplementable).  El dispositivo debe ejecutar Windows 10 Insider Preview, compilación 17672 o posterior, y poseer un chip de TPM 2.0 para completar correctamente este tipo de inscripción. Puesto que no se requiere ninguna autenticación de usuario, solo puede asignar esta opción a dispositivos sobre los que tenga control físico.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nueva configuración de idioma y región al realizar la configuración rápida de Autopilot <!-- 1821766 -->
Hay disponible una nueva configuración para establecer el idioma y la región de los perfiles de Autopilot durante la configuración rápida. Para ver la nueva configuración, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Implementación perfiles** > **Crear perfil** > **Modo de implementación** = **Self-deploying (Autoimplementable)** > **Valores predeterminados configurados**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nuevo valor para configurar el teclado del dispositivo <!-- 1821768 -->
Habrá disponible un valor nuevo para configurar el teclado de los perfiles de Autopilot durante la configuración rápida. Para ver la nueva configuración, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Implementación perfiles** > **Crear perfil** > **Modo de implementación** = **Self-deploying (Autoimplementable)** > **Valores predeterminados configurados**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Los perfiles AutoPilot se migran a un destinatario de grupo <!-- 1877935 -->
Se pueden asignar perfiles de implementación de AutoPilot a grupos de Azure AD que contengan dispositivos AutoPilot.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="set-compliance-by-device-location----851881----"></a>Establecimiento del cumplimiento por ubicación del dispositivo <!-- 851881 ! -->
En algunas situaciones, es posible que desee restringir el acceso a los recursos corporativos a una ubicación específica, definida por una conexión de red. Ya puede crear una directiva de cumplimiento (**Cumplimiento de dispositivos** > **Ubicaciones**) en función de la dirección IP del dispositivo. Si el dispositivo sale del intervalo IP, no podrá acceder a los recursos corporativos.

Se aplica a: dispositivos Android 6.0 y versiones posteriores, con la aplicación Portal de empresa actualizada

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitar aplicaciones y experiencias de consumidor en dispositivos Windows 10 Enterprise RS4 Autopilot<!-- 1621980 -->
Puede evitar la instalación de aplicaciones y experiencias de consumidor en los dispositivos Windows 10 Enterprise RS4 Autopilot. Para ver esta característica, vaya a **Intune** > **Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Plataforma** = **Windows 10 o versiones posteriores** > **Tipo de perfil** = **Restricciones de dispositivo** > **Configurar** > **Windows Spotlight** > **Características de consumidor**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Desinstalar las últimas actualizaciones de software de Windows 10 <!-- 1732948 -->
En caso de que detecte un problema importante en las máquinas con Windows 10, puede optar por desinstalar (revertir) la última actualización de características o la última actualización de calidad. La desinstalación de una actualización de característica o de calidad solo está disponible para el canal de servicio en el que se encuentra el dispositivo. La desinstalación desencadenará una directiva para restaurar la actualización anterior en las máquinas con Windows 10. Para las actualizaciones de características concretamente, puede limitar el tiempo de 2 a 60 días durante el cual se puede aplicar una desinstalación de la versión más reciente. Para configurar las opciones de desinstalación de actualización de software, seleccione **Actualizaciones de software** en la hoja **Microsoft Intune** en el portal de Azure. Después, seleccione **Anillos de actualización de Windows 10** en la hoja **Actualizaciones de software**. Elija después la opción **Desinstalar** en la sección **Información general**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Buscar IMEI y número de serie en todos los dispositivos <!-- 1793685 -->
Ya puede buscar IMEI y los números de serie en la hoja Todos los dispositivos (correo electrónico, UPN, nombre de dispositivo y nombre de la administración siguen estando disponibles). En Intune, elija **Dispositivos** > **Todos los dispositivos** y escriba la búsqueda en el cuadro de búsqueda.

#### <a name="management-name-field-will-be-editable----1875989---"></a>El campo de nombre de administración se podrá editar <!-- 1875989 -->
Ya puede editar el campo de nombre de administración en la hoja **Propiedades** de un dispositivo. Para editar este campo, elija **Dispositivos** > **Todos los dispositivos** > elija el dispositivo > **Propiedades**. Puede usar el campo de nombre de administración para identificar un dispositivo de manera única.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nuevo filtro Todos los dispositivos: categoría de dispositivo <!-- 1878520 -->
Ya puede filtrar la lista **Todos los dispositivos** por categoría de dispositivo. Para ello, elija **Dispositivos** > **Todos los dispositivos** > **Filtro** > **Categoría de dispositivo**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Use TeamViewer para compartir la pantalla de dispositivos iOS y MacOS <!-- 1985547 -->
Los administradores podrán conectarse a [TeamViewer](device-profile-android-teamviewer.md) e iniciar una sesión de uso compartido de pantalla con dispositivos iOS y macOS. Los usuarios de iPhone, iPad y macOS pueden compartir sus pantallas en vivo con cualquier otro dispositivo móvil o de escritorio. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Compatibilidad con múltiples instancias de Exchange Connector <!-- 2070451 -->
Ya no estará limitado a una instancia de Microsoft Intune Exchange Connector por inquilino. Intune admite varias instancias de Exchange Connector para que pueda configurar el acceso condicional de Intune con varias organizaciones de Exchange local.

Con un conector de Exchange local de Intune, se puede controlar el acceso de los dispositivos a los buzones de Exchange locales en función de si un dispositivo está inscrito en Intune y cumple con las directivas de cumplimiento de dispositivos de Intune. Para configurar un conector, descargue el conector de Exchange local de Intune desde Azure Portal e instálelo en un servidor en la organización de Exchange. En el panel de Microsoft Intune, elija **Acceso local** y, después, en **Instalación**, elija **Conector de Exchange ActiveSync**. Descargue el conector de Exchange local e instálelo en un servidor en la organización de Exchange. Ahora que ya no está limitado a un conector de Exchange por inquilino, si tiene otras organizaciones de Exchange, puede seguir el mismo proceso para descargar e instalar un conector para cada organización de Exchange adicional.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Nuevos detalles de hardware de dispositivo: CCID <!-- 2156657 -->
La información de dispositivo de interfaz de tarjeta de chip (CCID) ya se incluye para cada dispositivo. Para verla, elija **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Hardware**> compruebe en **Detalles de red**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Asignación de todos los usuarios y dispositivos como grupos de ámbito <!-- 2196803 -->
Podrá asignar todos los usuarios, todos los dispositivos y todos los usuarios y dispositivos en los grupos de ámbito. Para ello, elija **Roles de Intune** > **Todos los roles** > **Policy and profile manager (Administrador de directivas y perfiles)** > **Asignaciones**  > elija una asignación > **Ámbito (grupos)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>La información de UDID ahora se incluye para dispositivos iOS y macOS <!-- 2219806 wnready-->
Para ver el identificador único de dispositivo (UDID) para dispositivos iOS y macOS, vaya a **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Hardware**. UDID solo está disponible para dispositivos corporativos, tal y como se configura en **Dispositivos** > **Todos los dispositivos** > dispositivo > **Propiedades** > **Propiedad del dispositivo**.

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Solución de problemas mejorada para la instalación de aplicaciones <!-- 928990 -->
En algunas ocasiones, las instalaciones de aplicaciones en los dispositivos administrados por MDM de Microsoft Intune pueden presentar errores. Cuando esto ocurre, puede ser complicado entender el motivo del error o cómo solucionarlo. Incluimos una Versión preliminar pública de las características de solución de problemas de las aplicaciones. Verá un nodo nuevo bajo cada dispositivo individual denominado **Aplicaciones administradas**. En él aparecen las aplicaciones que se han entregado a través de MDM de Intune. Dentro del nodo, verá una lista de los estados de instalación de las aplicaciones. Si selecciona una aplicación individual, aparecerá la vista de solución de problemas de esa aplicación específica. En la vista de solución de problemas, verá el ciclo de vida completo de la aplicación, como cuándo se creó y modificó la aplicación, el momento en que se estableció su destino y cuándo se entregó a un dispositivo. Además, si la instalación de la aplicación no se realizó correctamente, verá el código de error y un mensaje útil sobre la causa del mismo. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Directivas de protección de aplicaciones de Intune y Microsoft Edge <!-- 1818968 -->
El explorador Microsoft Edge para dispositivos móviles (iOS y Android) ahora admite las directivas de protección de aplicaciones Microsoft Intune. Intune protegerá a los usuarios de dispositivos iOS y Android que inicien sesión con sus cuentas corporativas de Azure AD en la aplicación Edge. En dispositivos iOS, la directiva **Require managed browser for web content** (Requerir explorador administrado para contenido web) permitirá a los usuarios abrir vínculos en Edge cuando esté administrado.

## <a name="week-of-may-14-2018"></a>Semana del 14 de mayo de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Exigencia de instalación de perfiles de directivas, aplicaciones, certificados y red <!-- 1553555 -->

Los administradores pueden evitar que los usuarios finales accedan al escritorio de Windows 10 RS4 hasta que Intune instale los perfiles de red y certificado, las aplicaciones y las directivas durante el aprovisionamiento de dispositivos AutoPilot. Para obtener más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Configurar las directivas de protección de aplicaciones <!-- 2144597 Part 2 -->

En Azure Portal, en lugar de dirigirse a la hoja del servicio Intune App Protection, solo tiene que ir a Intune. Ahora hay una única ubicación para las directivas de protección de aplicaciones en Intune. Tenga en cuenta que todas las directivas de protección de aplicaciones se encuentran en la hoja **Aplicación móvil** de Intune, en **Directivas de protección de aplicaciones**. Esta integración ayuda a simplificar la administración en la nube. Recuerde que todas las directivas de protección de aplicaciones ya están en Intune y que puede modificar cualquiera de las directivas configuradas anteriormente. Las directivas de protección de aplicaciones (APP) y acceso condicional (CA) de Intune se encuentran ahora en **Acceso condicional**, que se encuentra en la sección **Administrar** de la hoja **Microsoft Intune** o en la sección **Seguridad** de la hoja **Azure Active Directory**. Para obtener más información sobre cómo modificar directivas de acceso condicional, vea [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obtener más información, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Semana del 7 de mayo de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Compatibilidad con Samsung Knox Mobile Enrollment <!--1112863-->

Al usar Intune con Samsung Knox Mobile Enrollment (KME), puede inscribir un gran número de dispositivos Android propiedad de la empresa. Los usuarios en redes Wi-Fi o de telefonía móvil se pueden inscribir con unas pocas pulsaciones al encender sus dispositivos por primera vez. Con la aplicación de implementación Knox, los dispositivos se pueden inscribir mediante Bluetooth o NFC. Para más información, vea [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Inscripción automática de dispositivos Android mediante Samsung Knox Mobile Enrollment).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Solicitar ayuda en el Portal de empresa para Windows 10 <!-- 1874137 -->

El Portal de empresa para Windows 10 ahora enviará registros de aplicaciones directamente a Microsoft cuando el usuario inicie el flujo de trabajo para obtener ayuda con un problema. Esto permitirá que sea más fácil solucionar los problemas que se envían a Microsoft.

## <a name="week-of-april-23-2018"></a>Semana del 23 de abril de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Compatibilidad de código de acceso con el PIN de MAM en Android<!-- 1438086 -->

Los administradores de Intune pueden establecer un requisito de inicio de aplicación para exigir un código de acceso en lugar de un PIN numérico de MAM. Si se configura, se le pide al usuario que establezca y use un código de acceso cuando se le solicite antes de obtener acceso a aplicaciones habilitadas para MAM. Un código de acceso se define como un PIN numérico con al menos un carácter especial o un carácter alfabético en mayúsculas/minúsculas. Intune admite un código de acceso de forma similar al PIN numérico existente... puede establecer una longitud mínima y permite la repetición de caracteres y secuencias en la consola de administración. Esta característica requiere la versión más reciente del Portal de empresa en Android. Esta característica ya está disponible para iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Compatibilidad con aplicaciones de línea de negocio (LOB) para macOS <!-- 1473977 -->
Microsoft Intune proporciona la capacidad de instalar aplicaciones LOB de macOS desde Azure Portal. Se puede agregar una aplicación LOB de macOS a Intune una vez procesada por la herramienta disponible en GitHub. En Azure Portal, seleccione **Aplicaciones cliente** en la hoja **Intune**. En la hoja **Aplicaciones cliente**, elija **Aplicaciones** > **Agregar**. En la hoja **Agregar aplicación**, seleccione **Aplicación de línea de negocio**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Todos los usuarios y todos los grupos de dispositivos integrados para la asignación de aplicaciones de perfil de trabajo de Android Enterprise <!-- 1813073 -->
Puede aprovechar los grupos integrados **Todos los usuarios** y **Todos los dispositivos** para la asignación de aplicaciones de perfil de trabajo de Android Enterprise. Para obtener más información, vea [Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune volverá a instalar las aplicaciones necesarias desinstaladas por los usuarios <!-- 1947010 -->
Si un usuario final desinstala una aplicación requerida, Intune la reinstala de forma automática antes de que transcurran 24 horas en lugar de esperar al ciclo de reevaluación de siete días.

### <a name="device-configuration"></a>Configuración de los dispositivos

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>El gráfico de perfiles de dispositivos y la lista de estado muestran todos los dispositivos de un grupo <!-- 1449153 -->
Al configurar un perfil de dispositivo (**Configuración del dispositivo** > **Perfiles**), elija el perfil del dispositivo, por ejemplo, iOS. Este perfil se asigna a un grupo que incluye los dispositivos iOS y los dispositivos que no son iOS. El recuento del gráfico muestra que el perfil se aplica a dispositivos iOS *y* no iOS (**Configuración del dispositivo** > **Perfiles** > seleccionar un perfil existente > **Información general**). Cuando se selecciona el gráfico en la pestaña **Información general**, el **Estado del dispositivo** enumera todos los dispositivos del grupo, en lugar de solo los dispositivos iOS. 

Con esta actualización, el gráfico (**Configuración del dispositivo** > **Perfiles** > seleccionar un perfil existente > **Información general**) solo muestra el recuento del perfil de dispositivo determinado. Por ejemplo, si el perfil de dispositivo de configuración se aplica a dispositivos iOS, el gráfico muestra solo el número de dispositivos iOS. Al seleccionar el gráfico y abrir **Estado del dispositivo**, solo se muestran los dispositivos iOS.

Mientras se realiza esta actualización, se quita temporalmente el gráfico de usuario. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>VPN de Always On para Windows 10 <!--1333666 -->

Actualmente, [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) puede usarse en dispositivos Windows 10 mediante un perfil de red privada virtual (VPN) personalizado creado con OMA-URI.

Con esta actualización, los administradores pueden habilitar Always On para perfiles de VPN de Windows 10 directamente en Intune en Azure Portal. Los perfiles VPN de Always On se conectarán automáticamente cuando:

- Los usuarios inicien sesión en sus dispositivos
- La red del dispositivo cambie
- La pantalla del dispositivo se vuelva a activar después de haberse desactivado

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nueva configuración de impresora para perfiles de educación <!-- 1308900 -->

Para los perfiles de educación, hay nueva configuración disponible en la categoría **Impresoras**: **Impresoras**, **Impresora predeterminada**, **Agregar nuevas impresoras**.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Mostrar el identificador de llamada en el perfil personal: perfil de trabajo de Android Enterprise <!--1098984 -->
Al usar un perfil personal en un dispositivo, es posible que los usuarios finales no vean los detalles del identificador del autor de la llamada de un contacto de trabajo. 

Con esta actualización, hay una nueva opción en **Android Enterprise** > **Restricciones de dispositivos** > **Configuración del perfil de trabajo**:
- Mostrar el identificador de llamada de contacto profesional en el perfil personal

Cuando se habilita (sin configurar), se muestran los detalles del autor de la llamada del contacto en el perfil personal. Cuando se bloquea, no se muestra el número del autor de la llamada del contacto en el perfil personal. 

Se aplica a: dispositivos de perfil de trabajo Android con la versión de SO Android 6.0 y versiones más recientes

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nueva configuración de Credential Guard de Windows Defender agregada a la configuración de Endpoint Protection <!--1102252 --><!--from 1802 and 1804-->

Con esta actualización, [Credential Guard de Windows Defender](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuración de dispositivos** > **Perfiles** > **Endpoint Protection**) incluye la siguiente configuración: 

- **Credential Guard de Windows Defender**: activa Credential Guard con seguridad basada en virtualización. Habilitar esta característica ayuda a proteger las credenciales en el siguiente reinicio cuando las opciones **///Platform Security Level with Secure Boot** (Nivel de seguridad de plataforma con arranque seguro) y **///Virtualization Based Security** (Seguridad basada en virtualización) are están ambas habilitadas. Las opciones son:
  - **Deshabilitado**: si Credential Guard se activó anteriormente con la opción **Habilitar sin bloqueo**", entonces Credential Guard se desactiva de forma remota.

  - **Habilitar con bloqueo UEFI**: garantiza que Credential Guard no se puede deshabilitar mediante una clave de Registro o por medio de directiva de grupo. Para deshabilitar Credential Guard después de usar esta opción, debe establecer la directiva de grupo en "Deshabilitado". A continuación, quite la funcionalidad de seguridad de cada equipo, con un usuario físicamente presente. Estos pasos borrar la configuración almacenada en UEFI. Mientras se conserve la configuración de UEFI, Credential Guard estará habilitado.

  - **habilitar sin bloqueo**: permite deshabilitar Credential Guard de forma remota mediante la directiva de grupo. Los dispositivos que usen esta configuración deben ejecutar al menos Windows 10 (versión 1511).

Las siguientes tecnologías dependientes se habilitan automáticamente al configurar Credential Guard: 

  - **Enable Virtualization-based Security (VBS)** (Habilitar la seguridad basada en la virtualización [VBS]): activa la seguridad basada en la virtualización (VBS) en el siguiente reinicio. La seguridad basada en la virtualización emplea el hipervisor de Windows para proporcionar compatibilidad con servicios de seguridad, y requiere arranque seguro.
  - **Secure Boot with Direct Memory Access (DMA)**: activa VBS con arranque seguro y acceso directo a memoria. La protección de DMA requiere compatibilidad con el hardware y solo se habilita en los dispositivos configurados correctamente. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Usar un nombre de firmante personalizado en certificado SCEP <!-- 2064190 -->
Puede usar el nombre común **OnPremisesSamAccountName** de un sujeto personalizado en un perfil de certificado SCEP. Por ejemplo, puede usar `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Bloqueo de la cámara y capturas de pantalla en los perfiles de trabajo de Android Enterprise <!-- 1098977 -->
Hay dos nuevas propiedades disponibles para bloquear al configurar restricciones de dispositivo para dispositivos Android: 
- Cámara: bloquea el acceso a todas las cámaras en el dispositivo
- Captura de pantalla: bloquea la captura de pantalla y además evita que el contenido se muestre en los dispositivos de pantalla que no tengan una salida de vídeo segura

Se aplica a los perfiles de trabajo de Android Enterprise.


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nuevos pasos de inscripción para los usuarios en dispositivos con macOS High Sierra 10.13.2+ <!--1734567 -->
macOS high Sierra 10.13.2 presentó el concepto de inscripción de inscripción de MDM "aprobada por el usuario". Las inscripciones aprobadas permiten a Intune administrar algunas configuraciones dependientes de la seguridad. Para obtener más información, vea la documentación de soporte técnico de Apple aquí: https://support.apple.com/HT208019.

Los dispositivos inscritos mediante el Portal de empresa de macOS se consideran "No aprobados por el usuario", a menos que el usuario final abra las preferencias del sistema y los apruebe de forma manual. Así, el Portal de empresa de macOS ahora insta a los usuarios de macOS 10.13.2 y versiones posteriores a aprobar manualmente su inscripción al final del proceso de inscripción. La consola de administración de Intune indicará si un dispositivo inscrito está aprobado por el usuario.



### <a name="device-management"></a>Administración de dispositivos

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>Protección contra amenazas avanzada (ATP) e Intune están totalmente integrados <!-- 1629303 -->

[Protección contra amenazas avanzada (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) muestra el nivel de riesgo de los dispositivos Windows 10. En el Centro de seguridad de Windows Defender (portal de ATP), puede crear una conexión a Microsoft Intune. Una vez creada, se usa una directiva de cumplimiento de Intune para determinar un nivel de amenaza aceptable. Si se supera el nivel de amenaza, una directiva de acceso condicional de Azure Active Directory (AD) puede bloquear el acceso a diferentes aplicaciones dentro de su organización.

Esta característica permite que ATP examine archivos, detecte amenazas y notifique cualquier riesgo en los dispositivos Windows 10.

Consulte [Habilitación de ATP con acceso condicional en Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Compatibilidad con dispositivos sin usuario <!-- 1637553 -->
Intune ofrece la posibilidad de evaluar el cumplimiento en dispositivos sin usuario, como Microsoft Surface Hub. La directiva de cumplimiento puede tener como destino dispositivos concretos. Así, es posible determinar el cumplimiento (y no cumplimiento) de dispositivos sin un usuario asociado.

#### <a name="delete-autopilot-devices----1713650---"></a>Eliminar dispositivos Autopilot <!-- 1713650 -->
Los administradores de Intune pueden [eliminar dispositivos Autopilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Experiencia de eliminación de dispositivos mejorada <!--1832333 -->
Ya no se le pide que quite los datos de la empresa o que restablezca el dispositivo a los valores de fábrica para [eliminar un dispositivo de Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Para ver la nueva experiencia, inicie sesión en Intune y seleccione **Dispositivos** > **Todos los dispositivos** > el nombre del dispositivo > **Eliminar**.

Si todavía quiere confirmar el borrado o eliminación, puede usar la ruta de ciclo de vida de dispositivo estándar al usar **Eliminar datos de la compañía** y **Restablecimiento de fábrica** antes de **Eliminar**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Reproducir sonidos en iOS en modo Perdido <!-- 1947769 -->
Cuando los dispositivos iOS supervisados están en el [modo perdido](device-lost-mode.md) de administración de dispositivos móviles (MDM), puede [reproducir un sonido](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Dispositivos** > **Todos los dispositivos** > seleccionar un dispositivo iOS > **Información general** > **Más**). El sonido sigue reproduciéndose hasta que el dispositivo se quita del modo Perdido o un usuario deshabilita el sonido en el dispositivo. Se aplica a dispositivos iOS 9.3 y versiones más recientes.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloquear o permitir resultados web en búsquedas realizadas en un dispositivo de Intune <!--1972804-->

Ahora, los administradores pueden bloquear los resultados web en las búsquedas realizadas en un dispositivo.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Mensajes de error mejorados para errores de carga del certificado push MDM de Apple <!-- 2172331 -->

El mensaje de error explica que se debe usar el mismo identificador de Apple al renovar un certificado MDM existente.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Probar el Portal de empresa para macOS en máquinas virtuales <!-- 2216679 -->

Se han publicado instrucciones para ayudar a los administradores de TI a probar la aplicación de Portal de empresa para macOS en máquinas virtuales en Parallels Desktop y VMware Fusion. Encuentre más información en [Inscribir máquinas virtuales macOS para realizar pruebas](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Interfaz de usuario

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Mejora de iconos de dispositivos en el Portal de empresa de Windows 10 <!--2213364 -->

Se han actualizado los iconos para hacerlos más accesibles para los usuarios con deficiencia visual y para que funcionen mejor con las herramientas de lectura de pantalla.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Enviar informes de diagnóstico en la aplicación Portal de empresa para macOS <!-- 2216677 -->
La aplicación Portal de empresa para dispositivos macOS se actualizó para mejorar la forma en que los usuarios notifican errores relacionados con Intune. Desde la aplicación Portal de empresa, los empleados pueden:

- Cargar informes de diagnóstico directamente para el equipo de desarrollo de Microsoft.
- Enviar por correo electrónico un Id. de incidente al equipo de soporte técnico de TI de la empresa.

Para más información, consulte [Envío de errores de macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune se adapta al sistema de diseño fluido de la aplicación Portal de empresa de Windows 10 <!-- 1195010 WNready -->
La aplicación Portal de empresa de Windows 10 se ha actualizado con la [vista de navegación del sistema de diseño fluido](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). En la parte lateral de la aplicación, verá una lista estática vertical de todas las páginas de nivel superior. Haga clic en cualquier vínculo para ver y cambiar entre páginas rápidamente. Esta es la primera de varias actualizaciones que verá como parte de nuestros esfuerzos para crear una experiencia más adaptable, empática y familiar en Intune. Para ver el aspecto actualizado, vaya a [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Semana del 16 de abril de 2018

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Usar el cliente de Cisco AnyConnect para iOS <!-- 1333708 -->

Cuando se crea un nuevo perfil de VPN para iOS, ahora hay dos opciones: **Cisco AnyConnect** y **Cisco Legacy AnyConnect**. Los perfiles de Cisco AnyConnect admiten las versiones 4.0.7x y más recientes. Los perfiles de VPN existentes de Cisco AnyConnect para iOS se etiquetan como **Cisco Legacy AnyConnect**, y siguen funcionando con Cisco AnyConnect 4.0.5x y versiones posteriores, como lo hacen en la actualidad.

> [!NOTE]
> Este cambio sólo se aplica a iOS. Sigue habiendo una única opción de Cisco AnyConnect para perfiles de trabajo de Android y Android Enterprise y las plataformas macOS.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Ahora, los dispositivos macOS inscritos en Jamf se pueden registrar en Intune <!-- 2370684 -->

Las versiones 1.3 y 1.4 del portal de empresa de macOS no registraban correctamente los dispositivos Jamf en Intune. La versión 1.4.2 del portal de macOS corrige este problema.


## <a name="week-of-april-9-2018"></a>Semana del 9 de abril de 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Experiencia de ayuda actualizada en la aplicación Portal de empresa para Android <!-- 1631531 -->

Se ha actualizado la experiencia de ayuda en la aplicación Portal de empresa para Android de acuerdo con los procedimientos recomendados para la plataforma Android. Ahora, cuando los usuarios detectan un problema en la aplicación, pueden pulsar en **Menú** > **Ayuda** y:
- Cargar registros de diagnóstico en Microsoft.
- Enviar un mensaje de correo electrónico que describe el problema y un Id. de incidente a un miembro del equipo de soporte técnico de la empresa.  

Para ver la experiencia de ayuda actualizada, vaya a [Send logs using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) (Enviar registros por correo electrónico) y [Send errors to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (Enviar errores a Microsoft).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nuevo gráfico de tendencias sobre errores de inscripción y tabla de motivos de error <!-- 1471783 -->

En la página de información general de inscripción, puede ver la tendencia de los errores de inscripción y los cinco motivos de error principales. Al hacer clic en el gráfico o la tabla, puede explorar los detalles para obtener consejos de resolución de problemas y sugerencias de corrección.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Actualización de la ubicación en la que se configuran las directivas de protección de aplicaciones <!-- 2144597 -->

En Azure Portal, dentro del servicio Microsoft Intune, se le va a redirigir de forma temporal desde la hoja del servicio **Intune App Protection** a la hoja **Aplicación móvil**. Tenga en cuenta que todas las directivas de protección de aplicaciones ya se encuentran en la hoja **Aplicación móvil** de Intune, en Configuración de aplicaciones. En lugar de ir a Intune App Protection, simplemente irá a Intune. En abril de 2018, se suspenderá el redireccionamiento y se quitará por completo la hoja del servicio **Intune App Protection**, para que haya una sola ubicación para las directivas de protección de aplicaciones en Intune. 

**¿Cómo me afecta esto a mí?**
Este cambio afectará tanto a los clientes de Intune independientes como a los clientes híbridos (Intune con Configuration Manager). Esta integración le ayudará a simplificar la administración en la nube.

**¿Qué he de hacer para prepararme para este cambio?**
Etiquete **Intune** como favorito en lugar de la hoja del servicio **Intune App Protection** y familiarícese con el flujo de trabajo de directivas de protección de aplicaciones de la hoja **Aplicación móvil** de Intune. Se proporciona el redireccionamiento durante un breve período de tiempo y, después, se elimina la hoja **Intune App Protection**. Recuerde que todas las directivas de protección de aplicaciones ya están en Intune y que puede modificar las directivas de acceso condicional. Para obtener más información sobre cómo modificar directivas de acceso condicional, vea [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obtener más información, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Semana del 2 de abril de 2018

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Actualización de la experiencia del usuario en la aplicación del Portal de empresa para iOS <!--1412866 -->
Se ha lanzado una actualización importante de la experiencia de usuario para la aplicación Portal de empresa para iOS. La actualización incorpora un rediseño visual completo con una apariencia modernizada. Se ha mantenido la funcionalidad de la aplicación, pero se han mejorado la facilidad de uso y la accesibilidad.  

También verá:
- Compatibilidad con iPhone X.
- Inicio de la aplicación y carga de respuestas más rápidos, para ahorrar tiempo a los usuarios.
- Barras de progreso adicionales para proporcionar a los usuarios la información de estado más reciente.
- Mejoras en la forma en que los usuarios cargan registros, de modo que, si hay algún problema, resulte más fácil informar.  

Para ver el aspecto actualizado, vaya a [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Protección de los datos locales de Exchange mediante APP y CA de Intune <!-- 1056954 -->
Ahora puede usar directivas de protección de aplicaciones (APP) y acceso condicional (CA) de Intune para proteger el acceso a datos locales de Exchange con Outlook Mobile. Para agregar o modificar una directiva de protección de aplicaciones en Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Directivas de protección de aplicaciones**. Antes de usar esta característica, asegúrese de cumplir los [requisitos de Outlook para iOS y Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="notices"></a>Notificaciones

### <a name="plan-for-change-intune-will-move-to-support-macos-1012-and-higher-in-december---2970975--"></a>Plan de cambio: Intune pasará a ser compatible con macOS 10.12 y versiones superiores en diciembre <!--2970975--> 

Apple acaba de lanzar macOS 10.14. En consecuencia, Intune pasará a ser compatible con macOS 10.12 y versiones superiores en diciembre de 2018. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?

A partir de diciembre, los usuarios finales de dispositivos con macOS 10.11 y anteriores no podrán usar el Portal de empresa para inscribirse en Intune. Deberán actualizar el dispositivo a la versión macOS 10.12 o posterior. También tendrán que actualizar la aplicación Portal de empresa a la versión más reciente para continuar recibiendo soporte técnico y nuevas características. 

Actualmente, macOS 10.12 y las versiones posteriores son compatibles con: 
- MacBook (finales de 2009 o posterior). 
- iMac (finales de 2009 o posterior).
- MacBook Air (finales de 2010 o posterior).  
- MacBook Pro (finales de 2010 o posterior). 
- MacBook Mini (finales de 2010 o posterior). 
- Mac Pro (finales de 2010 o posterior). 

Después de diciembre, los usuarios finales que tengan dispositivos distintos de los mencionados anteriormente no podrán tener acceso a la versión más reciente de la aplicación Portal de empresa para macOS. Los dispositivos inscritos que ejecuten versiones no compatibles anteriores a la macOS 10.12 seguirán administrándose y apareciendo en la Consola de administración de Intune.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?

- Pida a los usuarios finales que actualicen sus dispositivos a una versión del sistema operativo compatible antes de diciembre de 2018. 
- Consulte los informes de Intune en la consola de Intune en Azure para ver qué dispositivos o usuarios pueden verse afectados. Vaya a Dispositivos > Todos los dispositivos y filtre por el sistema operativo. Puede agregar columnas adicionales para ayudar a identificar qué usuarios de su organización tiene dispositivos que ejecutan macOS 10.11. 
- Si usa administración de dispositivos móviles (MDM) híbrida, vaya a Activos y Compatibilidad > Dispositivos en la consola de Configuration Manager; haga clic con el botón derecho en las columnas para agregar las columnas de Sistema operativo y Versión de cliente, y ordene por sistema operativo. Tenga en cuenta que la MDM híbrida está en desuso, y debe cambiar a Intune en Azure tan pronto como sea posible. 
 
#### <a name="additional-information"></a>Información adicional
Para más información, vea [Inscribir un dispositivo macOS en Intune con la aplicación Portal de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp).
 

### <a name="plan-for-change-new-intune-support-experience-for-premier-customers"></a>Plan de cambio: nueva experiencia de soporte técnico de Intune para clientes Premier 
Como cliente Premier de Microsoft, puede usar actualmente el portal de Microsoft Premier Online (MPO, premier.microsoft.com) e Intune en Azure (portal.azure.com) para crear solicitudes de soporte técnico de Intune. A partir del 3 de diciembre de 2018, y para continuar mejorando la experiencia de soporte técnico Premier, podrá crear solicitudes de soporte técnico solo en Intune en Azure.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Después del 3 de diciembre, no se podrán crear solicitudes de soporte técnico en MPO.  Si lo intenta, verá un símbolo del sistema que le obligará a dirigirse a Intune en Azure. En este caso, puede crear una solicitud que se enrutará al Soporte técnico de Microsoft especialista en Intune, para que diagnostiquen y resuelvan el problema de manera conveniente. Las solicitudes de soporte técnico creadas en el portal MPO no pueden verse en Azure Portal. Por lo tanto, no cree más solicitudes de soporte técnico en MPO.  

Si usa administración de dispositivos móviles híbrida (MDM híbrida) o administración conjunta, puede seguir utilizando MPO para crear solicitudes de soporte técnico para Configuration Manager. No obstante, para crear solicitudes relacionadas con Intune, debe usar Azure Portal. Le recordamos que la MDM híbrida está en desuso y que debe planear el cambio a Intune en Azure tan pronto como sea posible. Para más información, vea [Move from Hybrid Mobile Device Management to Intune on Azure](https://aka.ms/hybrid_notification) (Pasar de la administración híbrida de dispositivos móviles (MDM) a Intune en Azure).

Tenga en cuenta que solo los usuarios con roles de administrador global, administrador de servicios de Intune y administrador de soporte técnico de servicio pueden crear incidencias de soporte técnico en Azure Portal.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
- Deje de usar MPO y utilice Intune en Azure para crear y administrar todas las solicitudes de soporte técnico de Intune.  
- Avise al departamento de soporte técnico y actualice la documentación si es necesario.
- Si tiene usuarios sin los roles de administrador global o administrador de servicios de Intune que están creando solicitudes de soporte técnico en MPO, asígneles el rol de administrador de soporte técnico de servicio en Azure Active Directory. De este modo podrán seguir creando incidencias de soporte técnico en Azure Portal.
- Haga clic en Información adicional para obtener más información y vínculos útiles.

#### <a name="additional-information"></a>Información adicional
Para más información, vea la [entrada de blog del equipo de soporte técnico de Microsoft Intune](https://aka.ms/IntuneSupport_MPO_to_Azure).


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Acción necesaria: actualización de la restricción de dispositivos Android o configuración de contraseña de directiva de cumplimiento en Intune
Intune ya no dispondrá del tipo de contraseña "predeterminada del dispositivo" para dispositivos Android 4.4 y versiones superiores. Debido a las diferencias entre las plataformas de Android y la configuración predeterminada del dispositivo, este suele tratar esta directiva como opcional. Para que no se produzcan confusiones al aplicar esta configuración en Android, se eliminará de la interfaz de usuario en una versión posterior. 
#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
- Si quiere que sea obligatorio indicar una contraseña en los dispositivos, le recomendamos que edite los perfiles de plataforma de Android para definir el tipo de contraseña necesario, en vez de usar la opción predeterminada del dispositivo.
- Si quiere que el usuario final decida si crear una contraseña o no, seleccione el botón "Sin configurar". Cuando se quite esta opción de la interfaz de usuario, si todavía está activada, recibirá una solicitud para elegir una opción distinta a la predeterminada del dispositivo al editar el perfil.
¿Qué necesito hacer para prepararme para este cambio?
Revise la configuración de contraseña en las directivas de cumplimiento y restricción de dispositivos Android y dispositivos empresariales Android. Figuran en las directivas Seguridad del sistema para cumplimiento y en las restricciones Contraseña de dispositivo o Configuración de perfil de trabajo para el dispositivo. En la información adicional encontrará un vínculo para obtener más información y capturas de pantalla sobre cómo configurar dichas opciones.
#### <a name="additional-information"></a>Información adicional
https://aka.ms/PasswordSettings 

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>Plan de cambio: opción Change Password at Next Auth (Cambiar contraseña en la siguiente autenticación) agregada a Intune<!-- 1873216 -->
En la versión de servicio de septiembre, Intune planea integrar la opción **Change Password at Next Auth** (Cambiar la contraseña en la siguiente autenticación) que Apple lanzó recientemente para dispositivos que ejecutan la versión 10.13 de macOS y versiones más recientes de este sistema operativo. Antes de esta opción de configuración, los proveedores de MDM no podían comprobar que el código de paso del dispositivo se cambiaba para que fuera compatible. Las directivas de configuración y cumplimiento de Intune solo validan eso la siguiente vez que se cambia una contraseña del dispositivo, que está marcada como compatible. Cuando se agregue esta nueva característica de Apple, los usuarios de macOS recibirán una solicitud para actualizar su contraseña, aunque esta fuera compatible.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Esto afecta a los entornos con una directiva de dispositivos macOS que usan Intune o MDM híbrida. Ahora que Apple tiene la opción **Change Password at New Auth** (Cambiar contraseña en la siguiente autenticación), Intune puede exigir a los usuarios que actualicen su contraseña cuando se inserta una directiva de contraseña. Si bloquea los recursos de la empresa hasta que el dispositivo se marca como compatible, se puede bloquear a los usuarios finales para que no puedan acceder a los recursos de la empresa, como pueden ser el correo electrónico o los sitios de SharePoint, hasta que restablezcan su contraseña. En el futuro, todas las actualizaciones a las directivas de contraseña de configuración y cumplimiento exigirán a los usuarios de destino que actualicen sus contraseñas.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Hágaselo saber a su departamento de soporte técnico. Si no desea aplicar esta directiva de dispositivo de macOS, se recomienda anular la asignación de la directiva de macOS existente o eliminar dicha directiva. La investigación en los clientes sugiere que la mayoría de los clientes no se ven afectados por este cambio. La mayoría de los usuarios finales actualizan su contraseña después de recibir una solicitud para inscribirse con una contraseña o restablecen su contraseña para que siga siendo compatible.

### <a name="plan-for-change-intune-moving-to-tls-12"></a>Previsión de cambio: traspaso de Intune a TLS 1.2
A partir del 31 de octubre de 2018, Intune admitirá la versión 1.2 del protocolo de Seguridad de la capa de transporte (TLS) para proporcionar el mejor cifrado y garantizar que nuestro servicio sea más seguro de forma predeterminada, y para adaptarse a otros servicios de Microsoft, como Microsoft Office 365. Office comunicó este cambio en MC128929.

El Portal de empresa será compatible con TLS 1.2 a partir del 31 de octubre de 2018.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
A partir del 31 de octubre de 2018, Intune ya no será compatible con las versiones 1.0 o 1.1 del protocolo TLS. Todas las combinaciones de cliente y servidor, y de explorador y servidor deben usar la versión 1.2 de TLS para garantizar una conexión sin problemas a Intune. Tenga en cuenta que este cambio afectará a los dispositivos de usuario final que ya no son compatibles con Intune, pero que todavía reciben la directiva a través de Intune, y que no pueden usar la versión 1.2 de TLS. Esto incluye los dispositivos que ejecutan Android 4.3 y versiones anteriores. Para obtener una lista de exploradores y dispositivos afectados, vea la información adicional a continuación.

Después del 31 de octubre de 2018, si experimenta algún problema relacionado con el uso de una versión antigua de TLS, será necesario que actualice a TLS 1.2 o a un dispositivo que admita TLS 1.2 como parte de la resolución.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Se recomienda que quite las dependencias de TLS 1.0 y 1.1 de manera anticipada en sus entornos y deshabilite TLS 1.0 y 1.1 en el nivel de sistema operativo, en los casos en los que sea posible. Comience ya a planear la migración a TLS 1.2. Compruebe la siguiente entrada de blog de soporte técnico para obtener la lista de dispositivos que no son compatibles actualmente con Intune, pero que es posible que todavía reciban directivas, y que no podrán comunicarse con la versión 1.2 de TLS. Es posible que deba notificar a los usuarios finales de que perderán el acceso a los recursos corporativos.

**Información adicional**: [Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/) (Traspaso de Intune a TLS 1.2 para el cifrado)


### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Plan de cambio: use Intune en Azure ahora para la administración de MDM<!-- 1227338 -->
Hace más de un año anunciamos una [versión preliminar pública de Intune en Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) y hace seis meses seguimos con la [disponibilidad general de la nueva experiencia de administración](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) para Intune. A partir del 31 de agosto de 2018, se desactivará la administración de dispositivos móviles (MDM) en la consola de Silverlight clásica para los clientes que usan Intune de forma independiente. En su lugar, puede usar [Intune en Azure](https://aka.ms/Intune_on_Azure) para cubrir sus necesidades de MDM. Si todavía usa la consola clásica de MDM, deje de hacerlo y familiarícese con Intune en Azure. No se espera que este cambio afecte de ningún modo a los usuarios finales. La administración de PC clásica permanecerá en Silverlight. Puede obtener más información sobre este cambio y cómo le afecta [aquí](https://aka.ms/Intune_on_Azure_mdm).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->
Apple ha anunciado que se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS. Se mantendrá el [Blog de soporte técnico de Intune](https://aka.ms/compportalats) con detalles.



## <a name="see-also"></a>Vea también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/cloud-platform/roadmap)
* [Novedades de la interfaz de usuario del portal de empresa](whats-new-app-ui.md)
* [Novedades de los meses anteriores](whats-new-archive.md)
