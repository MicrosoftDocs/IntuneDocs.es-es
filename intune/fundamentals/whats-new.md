---
title: Novedades de Microsoft Intune (Azure) | Microsoft Docs
titleSuffix: ''
description: Descubra las novedades del portal de Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f46b8c7f0f57ab7831d6487495946aa9326b2d5
ms.sourcegitcommit: 24487f078349795922dc497c952e8358cf767a1a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76977791"
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune

Conozca las novedades semanales de Microsoft Intune. También puede encontrar [notificaciones importantes](#notices), [versiones anteriores](whats-new-archive.md) e información sobre [cómo se publican las actualizaciones del servicio de Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> El lanzamiento de cada [actualización mensual](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) puede tardar hasta tres días y se realizará en el orden siguiente:
>
> - Día 1: Asia Pacífico (APAC)
> - Día 2: Europa, Oriente Medio y África (EMEA)
> - Día 3: América del Norte
> - Día 4+: Intune for Government
>
> Es posible que algunas características se implementen durante varias semanas y que no estén disponibles para todos los clientes la primera semana.
>
> Revise la [página En desarrollo](in-development.md) para ver una lista de las características que aparecerán en una versión próxima.

**Fuente RSS**: reciba notificaciones cuando esta página se actualice copiando y pegando la siguiente dirección URL en su lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-february-03-2020"></a>Semana del 3 de febrero de 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="company-portal-app-improved-performance---6178652---"></a>Rendimiento mejorado de la aplicación Portal de empresa<!-- 6178652 -->
La aplicación Portal de empresa se ha actualizado para admitir un rendimiento mejorado en los dispositivos que usan procesadores ARM64, como Surface Pro X. Anteriormente, el Portal de empresa operaba en un modo ARM32 emulado. Ahora, la aplicación Portal de empresa se compila de forma nativa para ARM64. Para más información sobre la aplicación Portal de empresa, consulte [Configuración de la aplicación Portal de empresa de Microsoft Intune](~/apps/company-portal-app.md).

<!-- ########################## -->
## <a name="week-of-january-27-2020"></a>Semana del 27 de enero de 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="new-setting-to-remove-specific-windows-built-in-apps---6184390---"></a>Nueva configuración para quitar aplicaciones integradas de Windows específicas<!-- 6184390 -->
Una nueva configuración de directiva de configuración de dispositivos de Windows 10 permite quitar las siguientes aplicaciones integradas de Windows:

- Visor de realidad mixta
- MSN El Tiempo
- Instalador de aplicación
- Recomendaciones de Microsoft
- Mi Office
- Microsoft Solitaire Collection 
- Planes móviles
- Centro de opiniones 
- Xbox 
- Groove Música
- Mail
- Calendario

En el Centro de administración del Administrador de puntos de conexión de Microsoft, seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**. Seleccione **Windows 10 y versiones posteriores** como **Plataforma**. Seleccione **Restricciones de dispositivo** como **Tipo de perfil**. Seleccione **App Store** en el panel **Restricciones de dispositivos**. En la parte inferior del panel junto a **Quitar aplicaciones integradas**, seleccione **Quitar**. Para más información sobre las aplicaciones integradas, consulte[Incorporación de aplicaciones integradas a Microsoft Intune](~/apps/apps-add-built-in.md).

#### <a name="intune-support-for-additional-microsoft-edge-version-77-deployment-channel-for-macos---5983950----"></a>Compatibilidad de Intune con el canal de implementación adicional de Microsoft Edge versión 77 para macOS<!-- 5983950  -->
Microsoft Intune ahora admite el canal de implementación **estable** para la aplicación Microsoft Edge para macOS. El canal **estable** es el canal recomendado para la implementación de Microsoft Edge en general en entornos empresariales. Se actualiza cada seis semanas y cada versión incorpora mejoras del canal **beta**. Además de canales **estable** y **beta**, Intune admite un canal de **desarrollo**. La versión preliminar pública ofrece los canales estable y de desarrollo para la versión 77 y posteriores de Microsoft Edge para macOS. Las actualizaciones automáticas del explorador están activadas de forma predeterminada. Para obtener más información, consulte [Adición de Microsoft Edge a dispositivos macOS con Microsoft Intune](~/apps/apps-edge-macos.md).

#### <a name="retirement-of-intune-managed-browser--5728447---"></a>Retirada de Intune Managed Browser<!--5728447 -->
Se va a retirar Intune Managed Browser. Use Microsoft Edge para la experiencia de explorador de Intune protegida. Para más información, vea la entrada correspondiente a "[Realizar acciones: uso de Microsoft Edge para la experiencia de explorador de Intune protegida](~/fundamentals/whats-new.md#take-action-use-microsoft-edge-for-your-protected-intune-browser-experience)" en la sección [Notificaciones](~/fundamentals/whats-new.md#notices) más adelante.

<!-- ########################## -->
## <a name="week-of-january-20-2020-2001-service-release"></a>Semana del 20 de enero de 2020 (versión del servicio 2001)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="user-experience-change-when-adding-apps-to-intune---4705829-----"></a>Cambio en la experiencia del usuario al agregar aplicaciones a Intune<!-- 4705829   -->
Verá una nueva experiencia de usuario al agregar aplicaciones a través de Intune. Esta experiencia proporciona la misma configuración y los mismos detalles que ha usado anteriormente, pero la nueva experiencia emplea un proceso similar a un asistente antes de agregar una aplicación a Intune. Esta nueva experiencia también proporciona una página de revisión antes de agregar la aplicación. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**. Para más información, vea [Agregar aplicaciones a Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----5622282-----"></a>Requisito de reinicio de las aplicaciones Win32 <!-- 5622282   -->
Puede requerir que una aplicación Win 32 se reinicie después de una instalación correcta. Además, puede elegir el tiempo (el período de gracia) que transcurrirá antes de que se produzca el reinicio.

#### <a name="user-experience-change-when-configuring-apps-in-intune---4207990-----"></a>Cambio en la experiencia del usuario al configurar aplicaciones en Intune<!-- 4207990   -->
Verá una nueva experiencia de usuario al crear directivas de configuración de aplicaciones en Intune. Esta experiencia proporciona la misma configuración y los mismos detalles que ha usado anteriormente, pero la nueva experiencia emplea un proceso similar a un asistente antes de agregar una directiva a Intune. En el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Aplicaciones** > **Directivas de configuración de aplicaciones** > **Agregar**. Para obtener más información, vea [Directivas de configuración de aplicaciones para Microsoft Intune](~/apps/app-configuration-policies-overview.md). 

#### <a name="intune-support-for-additional-microsoft-edge-for-windows-10-deployment-channel---5861774---"></a>Compatibilidad de Intune con el canal de implementación adicional de Microsoft Edge para Windows 10<!-- 5861774 -->
Microsoft Intune ahora admite el canal de implementación adicional **estable** para la aplicación Microsoft Edge (versión 77 y posteriores) para Windows 10. El canal **estable** es el canal recomendado para la implementación de Microsoft Edge para Windows 10 en general en entornos empresariales. Este canal se actualiza cada seis semanas y cada versión incorpora mejoras del canal **beta**. Además de canales **estable** y **beta**, Intune admite un canal de **desarrollo**. Para obtener más información, vea [Microsoft Edge para Windows 10 - Configuración de aplicaciones](~/apps/apps-windows-edge.md#configure-app-settings).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuración del dispositivo

#### <a name="improved-user-interface-experience-when-configuring-exchange-activesync-on-premises-connector-ui---5695492-----"></a>Mejor experiencia de interfaz de usuario al configurar la interfaz de usuario del conector local de Exchange ActiveSync<!-- 5695492   -->
Hemos actualizado para experiencia para [configurar el conector local de Exchange ActiveSync](../protect/exchange-connector-install.md). La experiencia actualizada usa un solo panel para configurar, editar y resumir los detalles de los conectores locales. 

#### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-----"></a>Adición de configuración de proxy automática a perfiles de Wi-Fi para perfiles de trabajo de Android Enterprise<!-- 4490822   -->
En los dispositivos de perfil de trabajo de Android Enterprise, puede crear perfiles de Wi-Fi. Al elegir el tipo Wi-Fi Enterprise, también puede especificar el tipo de protocolo de autenticación extensible (EAP) que se usa en la red Wi-Fi.

Ahora, al elegir el tipo de empresa, también puede especificar la configuración de proxy automática, incluida una dirección URL del servidor proxy, como `proxy.contoso.com`.

Para ver la configuración de Wi-Fi actual que puede establecer, vaya a [Incorporación de la configuración de Wi-Fi en Microsoft Intune para dispositivos que ejecutan Android Enterprise y el Quiosco de Android](../configuration/wi-fi-settings-android-enterprise.md).

Se aplica a:
- Perfil de trabajo de Android Enterprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="block-android-enrollments-by-device-manufacturer--5197392----"></a>Bloqueo de las inscripciones de Android por el fabricante del dispositivo<!--5197392  -->
Puede bloquear la inscripción de dispositivos en función del fabricante del dispositivo. Esto se aplica al administrador de dispositivos Android y los dispositivos de perfil de trabajo de Android Enterprise. Para ver las restricciones a la implementación, vaya al [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Dispositivos** > **Restricciones de inscripción**.

#### <a name="improvements-to-the-iosipados-create-enrollment-type-profile-ui---6055005---"></a>Mejoras en la interfaz de usuario para Crear un perfil de tipo de inscripción en iOS/iPadOS<!-- 6055005 -->
Para la inscripción de usuarios de iOS/iPadOS, se ha simplificado la página **Crear un perfil de tipo de inscripción** **Configuración** para mejorar el proceso de elección del **Tipo de inscripción** manteniendo la misma funcionalidad. Para ver la nueva interfaz de usuario, vaya a la página [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tipos de inscripción** > **Crear perfil** > **Configuración**. Para obtener más información, consulte [Creación de un perfil de inscripción de usuario en Intune](../enrollment/ios-user-enrollment.md#create-a-user-enrollment-profile-in-intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Administración de dispositivos

#### <a name="new-information-in-device-details---4471759-5604099----"></a>Nueva información en los detalles del dispositivo<!-- 4471759 5604099  -->
La siguiente información está ahora en la página de **información general** para dispositivos:
- Capacidad de memoria (cantidad de memoria física en el dispositivo)
- Capacidad de almacenamiento (cantidad de almacenamiento físico en el dispositivo) 
- Arquitectura de CPU


#### <a name="ios-bypass-activation-lock-remote-action-renamed-to-disable-activation-lock---5904591----"></a>Cambio de nombre de la acción remota Omisión del bloqueo de activación de iOS a Deshabilitación del bloqueo de activación <!--5904591  -->
Se ha cambiado el nombre de la acción remota **Omisión del bloqueo de activación** a **Deshabilitación del bloqueo de activación**. Para obtener más información, consulte [Deshabilitación del bloqueo de activación de iOS con Intune](../remote-actions/device-activation-lock-bypass.md).

#### <a name="windows-10-feature-update-deployment-support-for-autopilot-devices---5948137-----"></a>Compatibilidad con la implementación de actualizaciones de características de Windows 10 para dispositivos AutoPilot<!-- 5948137   -->
Intune ahora admite dispositivos registrados con AutoPilot mediante [implementaciones de actualizaciones de características de Windows 10](../protect/windows-update-for-business-configure.md#windows-10-feature-updates).

Las directivas de actualización de características de Windows 10 no se pueden aplicar durante la configuración rápida (OOBE) de Autopilot y solo se aplican en el primer análisis de Windows Update una vez que el dispositivo haya finalizado el aprovisionamiento (que suele ser un día).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="windows-autopilot-deployment-reports-preview----3856172-----"></a>Informes de implementación de Windows Autopilot (versión preliminar) <!-- 3856172   -->
Un nuevo informe detalla cada dispositivo implementado mediante Windows Autopilot. Para más información, vea [Informe de implementaciones de Autopilot](../enrollment/enrollment-autopilot.md#autopilot-deployments-report).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Control de acceso basado en roles.

#### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-----"></a>Nuevo rol de Administrador de seguridad de los puntos de conexión integrado en Intune<!--4253397   -->
Hay un nuevo rol integrado de Intune disponible: el administrador de seguridad de los puntos de conexión. Este nuevo rol concede a los administradores acceso completo al nodo del administrador de puntos de conexión en Intune y acceso de solo lectura a otras áreas. El rol es una expansión del rol "Administrador de seguridad" de Azure AD. Si actualmente solo tiene administradores globales como roles, no es necesario realizar ningún cambio. Si usa roles y desea la granularidad que proporciona el Administrador de seguridad de puntos de conexión, asigne ese rol cuando esté disponible. Para más información acerca de roles integrados, vea [Control de acceso basado en rol](role-based-access-control.md).

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>Semana del 6 de enero de 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>Compatibilidad de S/MIME con Microsoft Outlook para iOS<!-- 2669398 -->
Intune admite la entrega de certificados de cifrado y firma S/MIME que se pueden usar con Outlook para iOS en dispositivos iOS. Para más información, consulte [Etiquetado de sensibilidad y protección en Outlook para iOS y Android](https://aka.ms/omsmime).

#### <a name="cache-win32-app-content-using-microsoft-connected-cache-server---6030314---"></a>Almacenamiento en caché del contenido de la aplicación Win32 mediante el servidor de caché con conexión de Microsoft<!-- 6030314 -->
Puede instalar un servidor de caché con conexión de Microsoft en los puntos de distribución de Configuration Manager para almacenar en caché el contenido de la aplicación Win32 de Intune. Para más información, consulte [Caché con conexión de Microsoft en Configuration Manager - Compatibilidad con aplicaciones Win32 de Intune](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Control de acceso basado en roles.

#### <a name="windows-10-administrative-templates-admx-profiles-now-support-scope-tags---5137390---"></a>Los perfiles de plantillas administrativas de Windows 10 (ADMX) ahora admiten etiquetas de ámbito <!--5137390 -->
Ahora puede asignar etiquetas de ámbito a los perfiles de plantilla administrativa (ADMX). Para ello, vaya a **Intune** > **Dispositivos** > **Perfiles de configuración** > elija un perfil de plantillas administrativas en la lista > **Propiedades** > **Etiquetas de ámbito**. Para más información sobre las etiquetas de ámbito, vea [Asignar etiquetas de ámbito a otros objetos](../fundamentals/scope-tags.md#assign-scope-tags-to-other-objects).

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>Semana del 30 de diciembre de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Recuperación de una clave de recuperación personal desde dispositivos macOS con cifrado de MEM<!-- 4851745 -->
Los usuarios finales pueden recuperar su clave de recuperación personal (clave de FileVault) mediante la aplicación Portal de empresa de iOS. El dispositivo que tiene la clave de recuperación personal se debe inscribir en Intune y cifrar con FileVault a través de Intune. Con la aplicación Portal de empresa de iOS, un usuario final puede recuperar su clave de recuperación personal en su dispositivo macOS cifrado haciendo clic en **Obtener clave de recuperación**. También puede recuperar la clave de recuperación en Intune si selecciona **Dispositivos** > *el dispositivos macOS cifrado e inscrito* > **Obtener clave de recuperación**. Para más información sobre FileVault, consulte [Cifrado de FileVault para macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

#### <a name="ios-and-ipados-user-licensed-vpp-apps---5619268---"></a>Aplicaciones de VPP con licencia de usuario de iOS y iPadOS<!-- 5619268 -->
En el caso de los dispositivos iOS y iPadOS inscritos por el usuario, los usuarios finales ya no verán las aplicaciones de VPP con licencia de dispositivo recién creadas implementadas como disponibles. Sin embargo, los usuarios finales seguirán viendo todas las aplicaciones de VPP con licencia de usuario en el Portal de empresa. Para más información relacionada con las aplicaciones VPP, vea [Administración de aplicaciones de iOS y macOS compradas a través del Programa de Compras por Volumen de Apple con Microsoft Intune](~/apps/vpp-apps-ios.md).

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>Semana del 23 de diciembre de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>Aviso: La compatibilidad de Windows 10 1703 (RS2) finalizará <!-- 5026679 -->
A partir del 9 de octubre de 2018, finalizó la compatibilidad de Windows 10 1703 (RS2) con la plataforma de Microsoft para las ediciones Home, Pro y Pro for Workstations. En el caso de las ediciones Windows 10 Enterprise y Education, la compatibilidad de Windows 10 1703 (RS2) con la plataforma finalizó el 8 de octubre de 2019. A partir del 26 de diciembre de 2019, actualizaremos la versión mínima de la aplicación Portal de empresa de Windows a Windows 10 1709 (RS3). Los equipos que ejecutan versiones anteriores a 1709 dejarán de recibir las versiones actualizadas de la aplicación desde Microsoft Store. Comunicamos anteriormente este cambio a los clientes que administran versiones anteriores de Windows 10 a través del centro de mensajes. Para más información, consulte [Hoja de datos del ciclo de vida de Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>Semana del 16 de diciembre de 2019

### <a name="device-configuration"></a>Configuración del dispositivo

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Actualizaciones de Plantillas administrativas para dispositivos Windows 10 <!-- 5941568 -->

Puede usar plantillas ADMX en Microsoft Intune para controlar y administrar la configuración de Microsoft Edge, Office y Windows. Las Plantillas administrativas en Intune realizaron estas actualizaciones en la configuración de las directivas:

- Se agregó compatibilidad con las versiones 78 y 79 de Microsoft Edge.
- Incluye los archivos ADMX del 11 de noviembre de 2019 en [Archivos de Plantillas administrativas (ADMX/ADML) y la Herramienta de personalización de Office para Office 365 ProPlus, Office 2019 y Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

Para más información sobre las plantillas ADMX en Intune, consulte [Usar plantillas de Windows 10 para configurar opciones de directiva de grupo en Microsoft Intune](../configuration/administrative-templates-windows.md).

Se aplica a:

- Windows 10 y versiones posteriores

## <a name="week-of-december-9-2019-1912-service-release"></a>Semana del 9 de diciembre de 2019 (versión del servicio 1912)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>Migración a Microsoft Edge para escenarios de exploración administrados<!-- 5173762 -->
A medida que se acerca la retirada de Intune Managed Browser, se han realizado cambios en las directivas de protección de aplicaciones para simplificar los pasos necesarios para trasladar a los usuarios a Edge. Se han actualizado las opciones de la configuración de directiva de protección de aplicaciones **Restringir la transferencia de contenido web con otras aplicaciones** para que sea una de las siguientes:

- Cualquier aplicación
- Intune Managed Browser
- Microsoft Edge
- Explorador no administrado 

Al seleccionar **Microsoft Edge**, los usuarios finales verán que la mensajería de acceso condicional les notifica que Microsoft Edge es necesario para escenarios de exploración administrados. Se les pedirá que descarguen e inicien sesión en Microsoft Edge con sus cuentas de AAD, si todavía no lo han hecho.  Este será el equivalente a tener como destino las aplicaciones habilitadas para MAM con la configuración de la aplicación `com.microsoft.intune.useEdge` establecida en **true**. Las directivas de protección de aplicaciones existentes en las que se usaba la opción **Exploradores administrados por directivas** ahora tendrán **Intune Managed Browser** seleccionado y no verá ningún cambio de comportamiento. Esto significa que los usuarios verán mensajes para usar Microsoft Edge si ha establecido la opción de configuración de la aplicación **useEdge** en **true**. Animamos a todos los clientes que aprovechan los escenarios de exploración administrados para actualizar sus directivas de protección de aplicaciones con **Restringir la transferencia de contenido web con otras aplicaciones** para asegurarse de que los usuarios vean las instrucciones adecuadas para realizar la transición a Microsoft Edge, con independencia de la aplicación desde la que inicien los vínculos. 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>Configuración del contenido de las notificaciones de una aplicación para las cuentas de organización<!-- 2576686  -->
Las directivas de protección de aplicaciones (APP) de Intune en dispositivos iOS y Android permiten controlar el contenido de las notificaciones de una aplicación para las cuentas de organización. Puede seleccionar una opción (Permitir, Bloquear datos de la organización o Bloqueado) para especificar cómo se muestran las notificaciones para las cuentas de organización para la aplicación seleccionada. Esta característica requiere compatibilidad con las aplicaciones y puede que no esté disponible para todas las aplicaciones habilitadas para APP. Outlook para iOS versión 4.15.0 (o posterior) y Outlook para Android 4.83.0 (o posterior) serán compatibles con esta configuración. La configuración está disponible en la consola, pero la funcionalidad entrará en vigor después del 16 de diciembre de 2019. Consulte [¿Qué son las directivas de protección de aplicaciones?](../apps/app-protection-policy.md) para obtener más información sobre APP.

#### <a name="microsoft-app-icons-update--4677605----"></a>Actualización de los iconos de las aplicaciones de Microsoft<!--4677605  -->
Se han actualizado los iconos que se usan para las aplicaciones de Microsoft en el panel de la aplicación objetivo para las directivas de protección de aplicaciones y las directivas de configuración de aplicaciones.

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>Requerir el uso de teclados aprobados en Android<!--4761794  -->
Como parte de una directiva de protección de aplicaciones, puede especificar la configuración [**Teclados aprobados**](../apps/app-protection-policy-settings-android.md#data-protection) para administrar los teclados Android que se pueden usar con aplicaciones Android administradas. Cuando un usuario abra la aplicación administrada y aún no use un teclado aprobado para esa aplicación, se le pedirá que cambie a uno de los teclados aprobados que ya están instalados en el dispositivo. Si es necesario, verá un vínculo para descargar un teclado aprobado en Google Play Store, que puede instalar y configurar. El usuario solo puede editar campos de texto en una aplicación administrada cuando su teclado activo no sea uno de los teclados aprobados.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuración del dispositivo

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>Experiencia de inicio de sesión único actualizada para aplicaciones y sitios web en dispositivos iOS, iPadOS y macOS<!-- 4999578  -->
Intune agregó una configuración de inicio de sesión único (SSO) para dispositivos iOS, iPadOS y macOS. Ahora puede configurar las extensiones de aplicación de SSO de redireccionamiento escritas por su organización o por el proveedor de identidades. Use estas opciones para configurar una experiencia de inicio de sesión único sin problemas para aplicaciones y sitios web que usan métodos de autenticación modernos, como OAuth y SAML2. 

Estas nuevas opciones expanden la configuración anterior de las extensiones de aplicación SSO y la extensión Kerberos integrada de Apple (**Dispositivos** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS/iPadOS** o **macOS** para el tipo de plataforma > **Características del dispositivo** para el tipo de perfil). 

Para ver todas las opciones de la extensión de aplicación SSO que puede configurar, vaya a [SSO en iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) y [SSO en macOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Se aplica a:

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352------"></a>Actualizamos dos opciones de restricción de dispositivos para dispositivos iOS e iPados para corregir su comportamiento<!-- 5701352    -->
En los dispositivos iOS, puede crear los perfiles de restricción de dispositivos **Permitir actualizaciones móviles de PKI** y **Bloqueo del modo restringido de USB** (**Dispositivos** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS/iPadOS** para la plataforma > **Restricciones de dispositivos** para el tipo de perfil). Antes de esta versión, la configuración de la interfaz de usuario y las descripciones de las siguientes opciones no eran correctas, algo que ahora se corrigió. A partir de esta versión, el comportamiento de la configuración es el siguiente:

**Bloquear actualizaciones móviles de PKI**: **Bloquear** impide que los usuarios reciban actualizaciones de software, a menos que el dispositivo esté conectado a un equipo. **No configurado** (valor predeterminado): permite que un dispositivo reciba actualizaciones de software sin estar conectado a un equipo.
- Anteriormente, esta configuración le permitía configurarla como: **Permitir**, que permite a los usuarios recibir actualizaciones de software sin tener que conectar los dispositivos a un equipo.
**Permitir accesorios USB con el dispositivo bloqueado**: **Permitir** permite que los accesorios USB intercambien datos con un dispositivo que ha estado bloqueado durante más de una hora. **No configurado** (valor predeterminado) no actualiza el modo restringido de USB en el dispositivo y los accesorios USB no podrán transferir datos del dispositivo si están bloqueados durante más de una hora.
- Anteriormente, esta configuración le permitía configurarla como: **Bloquear** para deshabilitar el modo restringido de USB en los dispositivos supervisados.

Para más información sobre los valores que puede configurar, consulte [Configuración de dispositivos iOS e iPadOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md).

Esta característica se aplica a:

- OS/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfiles de configuración de dispositivos de red cableada para dispositivos macOS<!-- 3508686  -->
   > [!NOTE]
   > Esta característica se ha retrasado, pero se publicará pronto.

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>Impedir que los usuarios configuren las credenciales de certificado en el almacén de claves administrado en dispositivos propietarios de dispositivos Android Enterprise<!-- 3311998 -->
En dispositivos propietarios de dispositivos Android Enterprise, puede establecer una nueva configuración que impide que los usuarios configuren sus credenciales de certificado en el almacén de claves administrado (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Solo el propietario del dispositivo > Restricciones de dispositivos** para el tipo de perfil > **Users + Accounts** [Usuarios y cuentas]).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Administración de dispositivos

#### <a name="protected-wipe-action-now-available--51150000---"></a>La acción de borrado protegido ya está disponible<!--51150000 -->
Ahora tiene la opción de usar la acción Borrar dispositivo para realizar el borrado protegido de un dispositivo. Los borradores protegidos equivalen a los borrados estándar, salvo que no se pueden eludir apagando el dispositivo. Un borrado protegido seguirá intentando restablecer el dispositivo hasta que se complete de forma correcta. En algunas configuraciones, esta acción puede hacer que el dispositivo no se pueda reiniciar. Para más información, consulte [Retirada o borrado de los dispositivos](../remote-actions/devices-wipe.md).

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>Dirección MAC de Ethernet de un dispositivo agregada a la página Información general del dispositivo<!--5562275 -->
Ahora puede ver la dirección MAC de Ethernet de un dispositivo en la página de detalles del dispositivo (**Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Información general**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>Experiencia mejorada en un dispositivo compartido cuando se habilitan las directivas de acceso condicional basadas en el dispositivo<!-- 1734096  -->
Mejoramos la experiencia en un dispositivo compartido con varios usuarios a los que se les aplica la directiva de acceso condicional basada en los dispositivos mediante la comprobación de la evaluación de cumplimiento más reciente para el usuario al aplicar la directiva. Para más información, consulte estos artículos de información general:
- [Información general de Azure sobre el Acceso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Información general sobre el cumplimiento de los dispositivos de Intune](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>Uso de perfiles de certificado PKCS para aprovisionar dispositivos con certificados<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
Ahora puede usar perfiles de certificado PKCS para emitir certificados a *dispositivos* que ejecuten Android for Work, iOS y Windows, cuando estén asociados a perfiles como los de Wi-Fi y VPN. Anteriormente, estas tres plataformas solo admitían certificados basados en el usuario, con la compatibilidad basada en dispositivos limitada a macOS.

> [!NOTE]
> No se admiten los perfiles de certificado PKCS con perfiles Wi-FI. En su lugar, use perfiles de certificado SCEP cuando use un [tipo EAP](../configuration/wi-fi-settings-windows.md#enterprise-profile).

Para usar un certificado basado en dispositivos, al [crear un perfil de certificado PKCS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile) para las plataformas admitidas, seleccione **Configuración**. Ahora verá el valor de **Tipo de certificado**, que admite las opciones de dispositivo o usuario.



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="centralized-audit-logs--5603185-5697164---"></a>Registros de auditoría centralizados<!--5603185, 5697164 -->
Una nueva experiencia de registros de auditoría centralizados ahora recopila los registros de auditoría de todas las categorías en una sola página. Puede filtrar los registros para obtener los datos que está buscando. Para ver los registros de auditoría, vaya a **Administración de inquilinos** > **Registros de auditoría**. 

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>Información de etiqueta de ámbito incluida en los detalles de la actividad de registro de auditoría<!--5763534 -->
Los detalles de la actividad de registro de auditoría ahora incluyen información de etiqueta de ámbito (para los objetos de Intune que admiten etiquetas de ámbito). Para más información sobre los registros de auditoría, consulte [Uso de registros de auditoría para realizar un seguimiento de los eventos y supervisarlos](monitor-audit-logs.md).


<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>Semana del 2 de diciembre de 2019

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>Nueva licencia de administración conjunta de Microsoft Endpoint Configuration Manager<!--5027281-->
Los clientes de Configuration Manager con Software Assurance pueden obtener la administración conjunta de Intune para equipos con Windows 10 sin tener que comprar una licencia de Intune adicional para la administración conjunta. Los clientes ya no necesitan asignar licencias de Intune y EMS individuales a los usuarios finales para la administración conjunta de Windows 10.
- Los dispositivos administrados por Configuration Manager e inscritos en la administración conjunta tienen casi los mismos derechos que los equipos administrados por MDM de Intune independiente. Pero después de restablecerlos, no se pueden volver a aprovisionar con Autopilot.
- Los dispositivos Windows 10 inscritos en Intune mediante otros medios requieren licencias completas de Intune.
- Los dispositivos de otras plataformas siguen requiriendo licencias de Intune completas.

Para más información, vea [Términos de Licencia](https://www.microsoft.com/en-us/Licensing/product-licensing/products).


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>Semana del 18 de noviembre de 2019 (versión del servicio 1911)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>Actualización de la interfaz de usuario al borrar datos de la aplicación de forma selectiva<!-- 4102028 -->
La interfaz de usuario para borrar selectivamente los datos de la aplicación en Intune se ha actualizado. Los cambios de la UI son:
- Una experiencia más sencilla, dado el uso de un formato de tipo asistente condensado dentro de un panel.
- Una actualización del flujo de creación para incluir asignaciones.
- Una página de resumen de todos los elementos establecidos al ver las propiedades, antes de crear una nueva directiva o al editar una propiedad. Además, al editar las propiedades, el resumen solo mostrará una lista de elementos de la categoría de propiedades que se están editando.

Para obtener más información, consulte [Borrado solo de datos corporativos de aplicaciones administradas por Intune](~/apps/apps-selective-wipe.md).

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>Compatibilidad con el teclado de terceros de iOS y iPadOS<!-- 4922950 -->
En marzo de 2019, anunciamos el fin del la compatibilidad del parámetro de la directiva de protección de aplicaciones de iOS "Teclados de terceros". La característica está de vuelta en Intune con compatibilidad tanto con iOS como con iPadOS. Para habilitar esta configuración, visite la pestaña **Protección de datos** de una directiva de protección de aplicaciones iOS/iPadOS nueva o existente y busque la opción **Teclados de terceros** en **Transferencia de datos**.

El comportamiento de esta configuración de directiva difiere ligeramente de la implementación anterior. En las aplicaciones de varias identidades que usan la versión de SDK 12.0.16 y versiones posteriores que son el destino de directivas de protección de aplicaciones con esta opción configurada en **Bloquear**, los usuarios finales no podrán elegir los teclados de terceros en sus cuentas personales y de organización. Las aplicaciones que usan versiones de SDK 12.0.12 y anteriores seguirán mostrando el comportamiento documentado en la entrada de blog que lleva por título [Problema conocido: Los teclados de terceros no se bloquean en iOS para cuentas personales](https://aka.ms/3rdparty_iOS_Intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuración del dispositivo

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Requerimiento de administración de Jamf a grupos de usuarios de macOS<!-- 4061739  --> 
Puede dirigirse a grupos específicos de usuarios cuyos [dispositivos macOS serán administrados por Jamf](../protect/conditional-access-integrate-jamf.md). Esto le permite aplicar la integración de cumplimiento de Jamf a un subconjunto de dispositivos macOS mientras que otros dispositivos se administran mediante Intune. Si ya usa la integración de Jamf, la integración se destinará a todos los usuarios de manera predeterminada.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>Nueva configuración de Exchange ActiveSync al crear un perfil de configuración de dispositivo de correo electrónico en dispositivos iOS<!-- 4892824   --> 
En dispositivos iOS/iPadOS, puede configurar la conectividad del correo electrónico en un perfil de configuración de dispositivos (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **iOS/iPadOS** como plataforma > **Correo electrónico** para tipo de perfil). 

Hay nuevas opciones de configuración de Exchange ActiveSync disponibles, entre las que se incluyen:
- **Datos de Exchange para sincronizar**: elija los servicios de Exchange que se sincronizarán (o cuya sincronización se bloqueará) con el calendario, los contactos, los recordatorios, las notas y el correo electrónico.
- **Permitir a los usuarios cambiar la configuración de sincronización**: permita (o impida) a los usuarios cambiar la configuración de sincronización para estos servicios en sus dispositivos.  

Para obtener más información sobre esta configuración, vaya a [Incorporación de la configuración de correo electrónico para dispositivos iOS en Microsoft Intune](../configuration/email-settings-ios.md). 

Se aplica a:

- iOS 13.0 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Evitación de que los usuarios agreguen cuentas personales de Google a dispositivos Android Enterprise dedicados y totalmente administrados<!-- 5353228   -->
En los dispositivos Android Enterprise dedicados y totalmente administrados, hay una nueva opción que impide que los usuarios creen cuentas de Google personales (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Android Enterprise** para plataforma > **Solo el propietario del dispositivo > Restricciones de dispositivos** para tipo de perfil > **configuración de Usuarios y cuentas** > **Cuentas personales de Google**).

Para ver los valores que puede configurar, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](../configuration/device-restrictions-android-for-work.md).

Se aplica a:

- Dispositivos totalmente administrados de Android Enterprise
- Dispositivos Android Enterprise dedicados

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>Eliminación del parámetro de registro del servidor para los comandos de Siri en el perfil de restricciones de dispositivos de iOS/iPadOS <!-- 5468501   -->
En dispositivos iOS y iPadOS, el parámetro **Registro del servidor para los comandos de Siri** se ha quitado de la consola de administración del Administrador de puntos de conexión de Microsoft (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **iOS/iPadOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **Aplicaciones integradas**). 

Esta configuración no tiene ningún efecto en los dispositivos. Para quitar el parámetro de los perfiles existentes, abra el perfil, realice cualquier cambio y, a continuación, guarde el perfil. El perfil se actualiza y la configuración se elimina de los dispositivos.

Para ver todos los valores que puede configurar, vea [Configuración de dispositivos iOS y iPadOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md).

Se aplica a:

- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Actualizaciones de características de Windows 10 (versión preliminar pública)<!-- 2384877 -->
Ahora puede implementar [actualizaciones de características de Windows 10](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) en dispositivos Windows 10. Las actualizaciones de características de Windows 10 son una nueva directiva de actualización de software que establece la versión de Windows 10 que desea que se instale y permanezca en los dispositivos. Puede usar este nuevo tipo de directiva junto con los anillos de actualización de Windows 10 existentes.

Los dispositivos que reciben la directiva de actualizaciones de características de Windows 10 instalarán la versión especificada de Windows y, a continuación, permanecerán con esa versión hasta que se edite o se quite la directiva. Los dispositivos que ejecutan una versión posterior de Windows permanecen en su versión actual. Los dispositivos que se encuentran en una versión específica de Windows pueden seguir instalando actualizaciones de calidad y seguridad para esa versión desde los anillos de actualización de Windows 10.

Este nuevo tipo de directiva comienza a implementarse en los inquilinos esta semana. Si esta directiva todavía no está disponible para el inquilino, lo estará pronto.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>Adición y cambio de información clave en archivos PLIST para aplicaciones macOS<!-- 4736278 -->
En los dispositivos macOS, ahora puede crear un perfil de configuración de dispositivos que cargue un archivo de lista de propiedades (. plist) asociado a una aplicación o el dispositivo (**Dispositivos** > **Perfiles de configuración** > **Crear perfil** > **macOS** para la plataforma > **Archivo de preferencias** para el tipo de perfil).

Solo algunas aplicaciones admiten preferencias administradas, y es posible que estas aplicaciones no le permitan administrar toda la configuración. Asegúrese de cargar un archivo de lista de propiedades que configure los valores del canal del dispositivo, no la configuración del canal del usuario.

Para obtener más información sobre esta característica, consulte [Adición de un archivo de lista de propiedades a dispositivos macOS mediante Microsoft Intune](../configuration/preference-file-settings-macos.md).

Se aplica a:

- dispositivos macOS con 10.7 y versiones más recientes

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Administración de dispositivos

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Edición del valor de nombre de dispositivo para dispositivos Autopilot<!-- 2640074 -->
Puede editar el valor del nombre de dispositivo para los dispositivos Autopilot unidos a Azure AD.  Para obtener más información, consulte [Edición de atributos de dispositivo Autopilot](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Edición del valor de etiqueta de grupo para dispositivos Autopilot<!-- 4816775   -->
Puede editar el valor Etiqueta de grupo para dispositivos Autopilot. Para obtener más información, consulte [Edición de atributos de dispositivo Autopilot](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="updated-support-experience---5012398---"></a>Experiencia de soporte técnico actualizada<!-- 5012398 -->

A partir de hoy, se está implantando en los inquilinos una experiencia actualizada y simplificada en la consola para [obtener ayuda y soporte técnico para Intune](get-support.md). Si esta experiencia todavía no está disponible para usted, lo estará pronto.

Se ha mejorado la búsqueda en la consola, los comentarios de incidencias comunes y el flujo de trabajo que se usa para ponerse en contacto con el servicio de soporte técnico. Al abrir una incidencia de soporte técnico, verá estimaciones en tiempo real de cuándo pueda esperar una devolución de llamada o una respuesta por correo electrónico; los clientes de soporte técnico Premier y Unified pueden especificar fácilmente la gravedad de su incidencia con el fin de obtener soporte técnico más rápido.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>Mejora de la experiencia de informes de Intune (versión preliminar pública) <!-- 3791418 -->
Intune ahora proporciona una experiencia de informes mejorada, con nuevos tipos de informes, una mejor organización de informes, vistas más centradas y una funcionalidad de informes más eficiente, así como datos más coherentes y precisos. Los nuevos tipos de informe se centran en lo siguientes aspectos:
- **Operativo**: proporciona registros nuevos con un enfoque de estado negativo. 
- **Organizativo**: proporciona un resumen más amplio del estado general.
- **Histórico**: proporciona patrones y tendencias a lo largo de un período de tiempo.
- **Especialista**: le permite usar datos sin procesar para crear sus propios informes personalizados.

El primer conjunto de informes nuevos se centra en el cumplimiento de los dispositivos. Para obtener más información, vea [Blog:marco de creación de informes de Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) e [Informes de Intune](~/fundamentals/reports.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Control de acceso basado en roles.

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>Duplicación de roles personalizados o integrados <!-- 1081938   -->
Ahora puede copiar tanto roles integrados como roles personalizados. Para obtener más información, vea [Copia de un rol](../fundamentals/create-custom-role.md#copy-a-role).

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>Nuevos permisos para el rol de administrador escolar <!-- 5621805  -->  
Se han agregado dos nuevos permisos, **Asignar perfil** y **Sincronizar dispositivo**, al rol de administrador escolar > **Permisos** > **Programas de inscripción**. El permiso de sincronizar perfil permite a los administradores de grupos sincronizar dispositivos Windows Autopilot. El permiso de asignar perfil les permite eliminar perfiles de inscripción de Apple iniciados por el usuario. También les concede permiso para administrar las asignaciones de dispositivos Autopilot y las asignaciones del perfil de implementación de Autopilot. Para obtener una lista de todos los permisos de administrador de grupo y administrador escolar, consulte [Asignación de un grupo de administración](https://docs.microsoft.com/intune-education/group-admin-delegate). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>Seguridad

#### <a name="bitlocker-key-rotation---2564951----"></a>Rotación de clave de BitLocker<!-- 2564951  -->
Puede usar una acción de dispositivo de Intune para [rotar de forma remota las claves de recuperación de BitLocker](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) para dispositivos administrados que ejecutan la versión 1909 o posterior de Windows. Para que se puedan rotar las claves de recuperación, los dispositivos deben configurarse para admitir la rotación de claves de recuperación.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>Actualizaciones en la inscripción de dispositivos dedicada para admitir la implementación de certificados de dispositivos SCEP <!-- 5198878  -->
Intune ahora admite la implementación de certificados de dispositivos SCEP en dispositivos Android Enterprise dedicados para permitir el acceso basado en certificados a los perfiles de Wi-Fi. La aplicación Microsoft Intune debe estar presente en el dispositivo para que funcione la implementación. Como resultado, hemos actualizado la experiencia de inscripción para dispositivos Android Enterprise dedicados. Las nuevas inscripciones siguen empezando de la misma manera (con QR, NFC, sin interacción o con identificador de dispositivo) pero ahora tienen un paso que requiere que los usuarios instalen la aplicación Intune. Los dispositivos existentes comenzarán a instalar la aplicación automáticamente de manera gradual.

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>Registros de auditoría de Intune para colaboración de negocio a negocio<!--5670211 -->
La colaboración de negocio a negocio (B2B) le permite compartir de forma segura las aplicaciones y los servicios de la empresa con usuarios invitados de cualquier otra organización, manteniendo al mismo tiempo el control sobre sus propios datos corporativos. Intune ahora admite registros de auditoría para usuarios invitados de B2B. Por ejemplo, cuando los usuarios invitados realizan cambios, Intune podrá capturar estos datos a través de registros de auditoría. Para obtener más información, consulte [¿Qué es el acceso de usuarios invitados en Azure Active Directory B2B?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>Semana del 11 de noviembre de 2019  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Experiencia mejorada de inscripción de macOS en el Portal de empresa <!-- 5074349  -->  
La experiencia de inscripción del Portal de empresa para macOS cuenta con un proceso de inscripción más sencillo que es más coherente con la experiencia de inscripción en el Portal de empresa para iOS. Los usuarios del dispositivo ahora ven lo siguiente:  

* Una interfaz de usuario más elegante.  
* Una lista de comprobación de inscripción mejorada.  
* Instrucciones más claras sobre cómo inscribir sus dispositivos.  
* Mejores opciones de solución de problemas.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Aplicaciones web iniciadas desde la aplicación del Portal de empresa de Windows<!-- 5030972 -->
Los usuarios finales ahora pueden iniciar aplicaciones web directamente desde la aplicación Portal de empresa de Windows. Los usuarios finales pueden seleccionar la aplicación web y, a continuación, elegir la opción **Abrir en el explorador**. La dirección URL web publicada se abre directamente en un explorador web. Esta funcionalidad se implementará durante la próxima semana. Para más información sobre las aplicaciones web, consulte[Agregar aplicaciones web a Microsoft Intune](~/apps/web-app.md).  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>Nueva columna de tipo de asignación en el Portal de empresa para Windows 10 <!-- 5459950  -->
Se ha cambiado el nombre de la columna Portal de empresa > **Aplicaciones instaladas** > **Tipo de asignación** a **Requerida por la organización**.  En esa columna, los usuarios verán un valor de **Sí** o **No** para indicar si una aplicación es obligatoria o es opcional para su organización. La razón de estos cambios es la confusión que despertaba en los usuarios de los dispositivos el concepto de aplicaciones disponibles. Los usuarios pueden obtener más información sobre cómo instalar aplicaciones en el Portal de empresa en [Instalar y compartir aplicaciones en el dispositivo](/intune-user-help/install-apps-cpapp-windows). Para obtener más información sobre cómo configurar la aplicación Portal de empresa para sus usuarios, vea [Configuración de la aplicación Portal de empresa de Microsoft Intune](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>Semana del 4 de noviembre de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Las líneas de base de seguridad se admiten en Microsoft Azure Government<!-- 4062552 -->

Las instancias de Intune que se hospedan en *Microsoft Azure Government* ahora pueden usar [líneas base de seguridad](../protect/security-baselines.md) para ayudarle a proteger sus usuarios y dispositivos.

## <a name="whats-new-archive"></a>Archivo de novedades
Para ver los meses anteriores, consulte el [archivo de novedades](whats-new-archive.md).

## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
