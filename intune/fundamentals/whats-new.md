---
title: Novedades de Microsoft Intune (Azure) | Microsoft Docs
titleSuffix: ''
description: Descubra las novedades del portal de Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/08/2019
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
ms.openlocfilehash: 37ed7bfd204289c963b8134252d9d76f2379ecba
ms.sourcegitcommit: 768d581cb8bcc5fdcb8ade95d402b11223ab226c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73882489"
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune

Conozca las novedades semanales de Microsoft Intune. También puede encontrar [notificaciones importantes](#notices), [versiones anteriores](whats-new-archive.md) e información sobre [cómo se publican las actualizaciones del servicio de Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728).

> [!Note]
> El lanzamiento de cada [actualización mensual](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) puede tardar hasta tres días y se realizará en el orden siguiente:
>
> - Día 1: Asia Pacífico (APAC)
> - Día 2: Europa, Oriente Medio y África (EMEA)
> - Día 3: América del Norte
>
> Algunas características pueden lanzarse a lo largo de varias semanas y pueden no estar disponibles para todos los clientes durante la primera semana.
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

## <a name="week-of-november-4-2019"></a>Semana del 4 de noviembre de 2019

### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Las líneas de base de seguridad se admiten en Microsoft Azure Government<!-- 4062552 -->

Las instancias de Intune que se hospedan en *Microsoft Azure Government* ahora pueden usar [líneas base de seguridad](../protect/security-baselines.md) para ayudarle a proteger sus usuarios y dispositivos.

## <a name="week-of-october-28-2019"></a>Semana del 28 de octubre de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Diseño de la lista de comprobación mejorado en la aplicación Portal de empresa para Android<!-- 5550857 -->  
La lista de comprobación de configuración de la aplicación Portal de empresa para Android se ha actualizado con un diseño ligero y nuevos iconos. Los cambios se alinean con las actualizaciones recientes realizadas en la aplicación Portal de empresa para iOS. Para una comparación en paralelo de los cambios, consulte [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md). Para ver los pasos de inscripción actualizados, consulte [Inscripción con el perfil de trabajo Android](/intune-user-help/enroll-device-android-work-profile) e [Inscripción de su dispositivo Android](/intune-user-help/enroll-device-android-company-portal).  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Aplicaciones Win32 en dispositivos de modo Windows 10 S<!-- 3747604 --> 
Puede instalar y ejecutar aplicaciones Win32 en dispositivos administrados en modo Windows 10 S. Para ello, puede crear una o varias directivas complementarias para el modo S mediante las herramientas de PowerShell de Control de aplicaciones de Windows Defender (WDAC). Firme las directivas complementarias con el portal de firma de Device Guard y, después, cargue y distribuya las directivas mediante Intune. En Intune, encontrará esta funcionalidad seleccionando **Aplicaciones cliente** > **Directivas complementarias de Windows 10 S**. Para más información, consulte [Habilitación de aplicaciones Win32 en modo S](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Establecimiento de la disponibilidad de las aplicaciones Win32 basada en una fecha y hora<!-- 3510685 -->
Como administrador, puede configurar la hora de inicio y la hora de la fecha límite para una aplicación Win32 necesaria. A la hora de inicio, la extensión de administración de Intune iniciará la descarga del contenido de la aplicación y lo almacenará en caché. La aplicación se instalará a la hora de la fecha límite. Para las aplicaciones disponibles, la hora de inicio determinará cuando la aplicación está visible en Portal de empresa. Para más información, consulte [Administración de aplicaciones Win32 de Intune](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Reinicio necesario del dispositivo basado en el período de gracia después de la instalación de la aplicación Win32<!-- 3136567 -->
Puede requerir que un dispositivo se reinicie después de que una aplicación Win32 se instale correctamente. Para más información, consulte [Administración de aplicaciones Win32: Configuración de los detalles de instalación de la aplicación](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details).

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Modo oscuro para el Portal de empresa de iOS<!-- 4911422 -->
El modo oscuro está disponible para el Portal de empresa de iOS. Los usuarios pueden descargar aplicaciones de empresa, administrar sus dispositivos y obtener soporte técnico de TI en la combinación de colores de su elección en función de la configuración del dispositivo. El Portal de empresa de iOS hará coincidir automáticamente la configuración del dispositivo del usuario final con el modo oscuro o claro. Para más información, consulte [Introducción al modo oscuro en el Portal de empresa de Microsoft Intune para iOS](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453). Para más información sobre el Portal de empresa de iOS, consulte [Configuración de la aplicación Portal de empresa de Microsoft Intune](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Versión mínima de la aplicación aplicada por el Portal de empresa de Android<!-- 2378776 -->
Con la opción **Min Company Portal version** (Versión mínima del Portal de empresa) de una directiva de protección de aplicaciones, puede especificar una versión definida mínima determinada del Portal de empresa que se aplique a un dispositivos de usuario final. Esta configuración de inicio condicional permite **bloquear el acceso**, **borrar datos** o **advertir** como posibles acciones cuando no se cumple el valor. Los posibles formatos de este valor siguen el patrón *[Principal].[Secundaria]* , *[Principal].[Secundaria].[Compilación]* o *[Principal].[Secundaria].[Compilación].[Revisión]* .

La opción **Min Company Portal version** (Versión mínima del Portal de empresa), si está configurada, afectará a cualquier usuario final que obtenga la versión 5.0.4560.0 del Portal de empresa y todas sus versiones futuras. Esta configuración no afectará a los usuarios que usen una versión del Portal de empresa anterior a la versión con la que se publique esta característica. Los usuarios finales que usen actualizaciones automáticas de aplicaciones en su dispositivo probablemente no verán ningún cuadro de diálogo de esta característica, dado que es posible que estén en la versión más reciente del Portal de empresa. Esta opción es solo para Android con la protección de aplicaciones para dispositivos inscritos y no inscritos. Para más información, consulte [Configuración de directivas de protección de aplicaciones de Android: inicio condicional](~/apps/app-protection-policy-settings-android.md#conditional-launch).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Administración de dispositivos de Microsoft 365

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Introducción al nodo Seguridad del punto de conexión en Administración de dispositivos de Microsoft 365<!-- 5630102 -->

El nodo **Seguridad del punto de conexión** está ahora disponible con carácter general en el área de trabajo de especialistas de Administración de dispositivos de Microsoft 365 en https://devicemanagement.microsoft.com, que agrupa las funcionalidades para proteger los puntos de conexión como:

- Líneas de base de seguridad:  grupo preconfigurado de valores de configuración que le ayudan a aplicar un grupo conocido de valores de configuración y valores predeterminados que recomienda Microsoft.

- Tareas de seguridad: aproveche las ventajas de la administración de amenazas y vulnerabilidades (TVM) de Microsoft Defender ATP y use Intune para corregir las debilidades del punto de conexión.

- ATP de Microsoft Defender: integración de Microsoft Defender Advanced Threat Protection (ATP) para ayudar a evitar infracciones de seguridad en dispositivos móviles.

Esta configuración seguirá siendo accesible desde otros nodos aplicables, como los dispositivos, y el estado configurado actual será el mismo, sin importar dónde tenga acceso a estas funcionalidades y las habilite.

Para más información sobre estas mejoras, consulte la [entrada de blog sobre el éxito de clientes de Intune](https://aka.ms/Endpoint_security_node) en el sitio web de la comunidad tecnológica de Microsoft.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune admite iOS 11 y posterior<!-- 4665324  -->

La inscripción en Intune y el Portal de empresa ahora admiten las versiones de iOS 11 y posteriores. No se admiten versiones anteriores.

### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Línea de base de Microsoft Edge (versión preliminar)<!--  3787164  -->

Hemos agregado una versión preliminar de la línea de base de seguridad para la [configuración de Microsoft Edge](../protect/security-baseline-settings-edge.md). 

<!-- ########################## -->
## <a name="week-of-october-21-2019"></a>Semana del 21 de octubre de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Administración de dispositivos de Microsoft 365

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Experiencia de administración mejorada en Administración de dispositivos de Microsoft 365<!-- 5551239 -->

Existe ahora una experiencia de administración actualizada y optimizada que está disponible con carácter general en el área de trabajo de especialistas de Administración de dispositivos de Microsoft 365 en [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com), por ejemplo:

- **Navegación actualizada**: encontrará una navegación de primer nivel simplificada que agrupa las características de manera lógica.
- **Nuevos filtros de plataforma**: puede seleccionar una sola plataforma, que muestra solo las directivas y las aplicaciones de la plataforma seleccionada, en las páginas Dispositivos y Aplicaciones.
- **Nueva página principal**: vea rápidamente el estado del servicio, el estado de su inquilino, noticias, etc., en la nueva página principal.

Para más información sobre estas mejoras, consulte la [entrada de blog de Enterprise Mobility + Security](https://go.microsoft.com/fwlink/?linkid=2109094) en el sitio web de la comunidad tecnológica de Microsoft.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Incorporación de aplicaciones de Mobile Threat Defense a dispositivos no inscritos<!-- 3005337 -->
Puede crear una directiva de protección de aplicaciones de Intune que puede bloquear o borrar de forma selectiva los datos corporativos de los usuarios en función del estado de un dispositivo. El estado del dispositivo se determina mediante la solución Mobile Threat Defense (MTD) seleccionada. Esta funcionalidad existe en la actualidad con los dispositivos inscritos en Intune como una configuración de cumplimiento de dispositivos. Con esta nueva característica, ampliamos la detección de amenazas de un proveedor de Mobile Threat Defense para que funcione en dispositivos no inscritos. En Android, esta característica requiere la versión más reciente de Portal de empresa. En iOS, esta característica se podrá usar cuando las aplicaciones integren el SDK de Intune más reciente (v 12.0.15 +). Se actualizará el tema Novedades cuando la primera aplicación adopte el SDK de Intune más reciente. El resto de aplicaciones irán estando disponibles de manera gradual. Para más información, consulte [Creación de una directiva de protección de aplicaciones de Mobile Threat Defense con Intune](~/protect/mtd-app-protection-policy.md).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices---2266073----"></a>Nuevo perfil de interfaz de configuración de firmware de dispositivo para dispositivos con Windows 10 y versiones posteriores<!-- 2266073  -->

En Windows 10 y versiones posteriores, puede crear un perfil de configuración de dispositivo para controlar la configuración y las características (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** como plataforma). En esta actualización, existe un nuevo tipo de perfil de interfaz de configuración de firmware de dispositivo que permite a Intune administrar la configuración de UEFI (BIOS).

Para más información sobre esta característica, vea [Uso de perfiles de DFCI en dispositivos Windows en Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

Se aplica a:
- Windows 10 RS5 (1809) y versiones más recientes en firmware compatible

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Cambiar a mostrar solo la página Estado de inscripción en los dispositivos aprovisionados mediante la configuración rápida (OOBE)<!--3959566-->
Ahora puede elegir mostrar solo la página Estado de inscripción en los dispositivos aprovisionados mediante OOBE de Autopilot.

Para ver el nuevo control de alternancia, elija **Intune** > **Inscripción de dispositivos** > **Inscripción de Windows** > **página Estado de inscripción** > **Crear perfil** > **Configuración** > **Mostrar solo la página en los dispositivos aprovisionados por la configuración rápida (OOBE)** .


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>Semana del 14 de octubre de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Notificación de aplicaciones de Google Play disponibles para perfiles de trabajo de Android<!-- 3041956   -->
En las instalaciones de aplicaciones disponibles en dispositivos dedicados, totalmente administrados y de perfil de trabajo de Android Enterprise, puede ver el estado de instalación de la aplicación, así como la versión instalada de aplicaciones administradas de Google Play. Para obtener más información, vea [Supervisión de las directivas de protección de aplicaciones](~/apps/app-protection-policies-monitor.md), [Administrar dispositivos de perfil de trabajo Android con Intune](~/enrollment/android-enterprise-overview.md) y [Tipo de aplicación de Google Play administrado](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Microsoft Edge versión 77 y posteriores para Windows 10 y macOS (versión preliminar pública)<!-- 3872025, 4678761  -->
Microsoft Edge versión 77 y posteriores ya está disponible para implementarlo en equipos que ejecutan Windows 10 y macOS. 

La versión preliminar pública ofrece los canales **Dev** y **Beta** para Windows 10 y un canal **Beta** para macOS. La implementación solo está en inglés (EN), pero los usuarios finales pueden cambiar el idioma para mostrar en el explorador, en **Configuración** > **Idiomas**. Microsoft Edge es una aplicación Win32 que se instala en el contexto del sistema y en arquitecturas similares (aplicación x86 en sistemas operativos x86 y aplicación x64 en sistemas operativos x64). Además, las actualizaciones automáticas del explorador están **Activadas** de forma predeterminada, y Microsoft Edge no se puede desinstalar. Para más información, vea [Adición de Microsoft Edge para Windows 10 a Microsoft Intune](~/apps/apps-windows-edge.md) y la [documentación de Microsoft Edge](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>Actualización de la interfaz de usuario de protección de aplicaciones y de la interfaz de usuario de aprovisionamiento de aplicaciones de iOS<!-- 4102027, 4102029   -->
La interfaz de usuario para crear y editar directivas de protección de aplicaciones y perfiles de aprovisionamiento de aplicaciones de iOS en Intune se ha actualizado. Los cambios de la UI son:
- Una experiencia más sencilla, dado el uso de un formato de tipo asistente condensado dentro de una hoja. 
- Una actualización del flujo de creación para incluir asignaciones.
- Una página de resumen de todos los elementos establecidos al ver las propiedades, antes de crear una nueva directiva o al editar una propiedad. Además, al editar las propiedades, el resumen solo mostrará una lista de elementos de la categoría de propiedades que se están editando.

Para más información, vea [Creación y asignación de directivas de protección de aplicaciones](~/apps/app-protection-policies.md) y [Uso de perfiles de aprovisionamiento de aplicaciones para iOS](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Escenarios guiados de Intune<!-- 4850318, 4831296, 3610611  -->
Ahora, Intune proporciona escenarios guiados que ayudan a realizar una tarea concreta o un conjunto de tareas en Intune. Un escenario guiado es una serie personalizada de pasos (flujo de trabajo) en torno a un caso de uso completo. Los escenarios más habituales se definen en función del rol que un administrador, un usuario o un dispositivo desempeñan en la organización. Estos flujos de trabajo suelen requerir una colección de perfiles, opciones, aplicaciones y controles de seguridad cuidadosamente organizados para proporcionar la mejor experiencia de usuario y seguridad. Estos son los nuevos escenarios guiados:
- [Implementación de Microsoft Edge para dispositivos móviles](~/fundamentals/guided-scenarios-edge.md)
- [Aplicaciones móviles seguras de Microsoft Office](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Escritorio moderno administrado en la nube](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

Para más información, vea [Introducción a los escenarios guiados de Intune](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>Variable de configuración de aplicaciones adicional disponible<!-- 4969237   -->
Al crear una directiva de configuración de aplicaciones, puede incluir la variable de configuración `AAD Device ID` como parte de los valores de configuración. En Intune, seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones** > **Agregar**. Especifique los detalles de la directiva de configuración y seleccione **Opciones de configuración** para ver la hoja **Opciones de configuración**. Para más información, vea la sección [Uso del diseñador de configuración en Adición de directivas de configuración de aplicaciones para dispositivos Android Enterprise administrados](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>Creación de grupos de objetos de administración denominados conjuntos de directivas<!-- 3762880  -->
Los conjuntos de directivas permiten crear una agrupación de referencias a entidades de administración ya existentes que se deben identificar, establecer como destino y supervisar como una sola unidad conceptual. Los conjuntos de directivas no reemplazan los conceptos ni los objetos existentes. Puede seguir asignando objetos individuales en Intune y hacer referencia a objetos individuales como parte de un conjunto de directivas. Por lo tanto, cualquier cambio que se realice en esos objetos individuales se verá reflejado en el conjunto de directivas.  En Intune, deberá seleccionar **Conjuntos de directivas** > **Crear** para crear un conjunto de directivas desde cero. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Actualización de la interfaz de usuario para crear y editar anillos de actualización de Windows 10<!-- 4099089         -->
Hemos actualizado la experiencia de interfaz de usuario para [crear y editar anillos de actualización de Windows 10](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) para Intune. Los cambios en la interfaz de usuario son los siguientes:  
- Formato de tipo asistente condensado en una sola hoja de la consola, bastante alejado de la dispersión de la hoja anterior cuando se configuraban anillos de actualización.   
- El flujo de trabajo revisado incluye las asignaciones antes de completar la configuración inicial del anillo.
- Una página de resumen que se puede usar para revisar todas las configuraciones realizadas antes de guardar e implementar un anillo de actualización nuevo. Al editar un anillo de actualización, en el resumen solo muestra la lista de elementos establecidos en la categoría de las propiedades que se hayan editado.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>Actualización de la interfaz de usuario para crear y editar una directiva de actualización de software de iOS<!-- 4099090       --> 
Hemos actualizado la experiencia de interfaz de usuario para [crear](../protect/software-updates-ios.md#configure-the-policy) y [editar](../protect/software-updates-ios.md#edit-a-policy) directivas de actualización de software de iOS para Intune.  Los cambios en la interfaz de usuario son los siguientes:  
- Formato de tipo asistente condensado en una sola hoja de la consola, bastante alejado de la dispersión de la hoja anterior cuando se configuraban directivas de actualización.   
- El flujo de trabajo revisado incluye las asignaciones antes de completar la configuración inicial de la directiva.
- Una página de resumen que se puede usar para revisar todas las configuraciones realizadas antes de guardar e implementar una directiva nueva. Al editar una directiva, en el resumen solo muestra la lista de elementos establecidos en la categoría de las propiedades que se hayan editado.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>La configuración Reinicio establecido se ha quitado de los anillos de Windows Update<!--  4464404   WNReady   -->
Como ya anunciamos en su día, ahora los anillos de actualización de Windows 10 de Intune [admiten la configuración de fechas límite](../protect/windows-update-settings.md) y ya no admiten *Reinicio establecido*. Las opciones de *Reinicio establecido* ya no están disponibles cuando al configurar o administrar anillos de actualización en Intune.  

Este cambio viene de la mano de algunos [cambios recientes en el Servicio de actualización de Windows](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) y en los dispositivos que ejecutan Windows 10 1903 o versiones posteriores, las *fechas límite* reemplazan las configuraciones de *Reinicio establecido*.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Imposibilidad de instalar aplicaciones desde orígenes desconocidos en dispositivos de perfil de trabajo de Android Enterprise<!-- 4760025   -->
En los dispositivos de perfil de trabajo de Android Enterprise, los usuarios no pueden instalar aplicaciones procedentes de orígenes desconocidos en ninguna circunstancia. En esta actualización hay una nueva configuración, **Impedir la instalación de aplicaciones de orígenes desconocidos en el perfil personal**. Esta opción impide de forma predeterminada que los usuarios carguen aplicaciones de orígenes desconocidos en el perfil personal del dispositivo.

Para ver los valores que se pueden configurar, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](../configuration/device-restrictions-android-for-work.md).

Se aplica a:
- Perfil de trabajo de Android Enterprise

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Creación de un proxy HTTP global en los dispositivos de propietario de dispositivos de Android Enterprise<!-- 4816339   -->
En los dispositivos de Android Enterprise, se puede configurar un proxy HTTP global para cumplir los estándares de exploración web de la organización (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** como plataforma > **Propietario del dispositivo > Restricciones de dispositivos** como tipo de perfil > **Conectividad**). Una vez configurado, todo el tráfico HTTP usará este proxy.

Para configurar esta característica y ver los valores que se pueden configurar, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](../configuration/device-restrictions-android-for-work.md).

Se aplica a:
- Propietario del dispositivo Android Enterprise

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>La opción Conectar automáticamente se ha quitado de los perfiles de Wi-Fi del administrador de dispositivos Android y Android Enterprise<!-- 5021055   -->
En los dispositivos de administrador de dispositivos Android y Android Enterprise, puede crear un perfil de Wi-Fi para configurar diferentes opciones (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Administrador de dispositivos Android** o **Android Enterprise** como plataforma > **Wi-Fi** como tipo de perfil). En esta actualización, la opción **Conectar automáticamente** se ha quitado, ya que [no es compatible con Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Si utiliza esta configuración en un perfil de Wi-Fi, posiblemente haya notado que **Conectar automáticamente** no funciona. No es necesario realizar ninguna acción, pero tenga en cuenta que esta configuración se ha quitado en la interfaz de usuario de Intune.

Para ver la configuración actual, vaya a [Configuración de Wi-Fi de Android](../configuration/wi-fi-settings-android.md) y [Configuración de Wi-Fi de Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

Se aplica a:
- Administrador de dispositivos Android 
- Android Enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>Nuevos valores de configuración de dispositivo para dispositivos iOS e iPadOS supervisados<!-- 5199328   -->
En los dispositivos iOS e iPad se puede crear un perfil para restringir las características y la configuración de esos dispositivos (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS/iPadOS** como plataforma > **Restricciones de dispositivos** como tipo de perfil). En esta actualización, hay nuevas opciones de configuración que puede controlar: 
- El acceso a la unidad de red en la aplicación de archivos  
- El acceso a la unidad USB en la aplicación de archivos 
- La posibilidad tener Wi-Fi siempre activado 

Para ver estas opciones, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md).

Se aplica a:
- iOS 13.0 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Especificar qué versiones de sistema operativo del dispositivo Android se inscriben con el perfil de trabajo o la inscripción del administrador de dispositivos<!-- 4350697   -->
Con las restricciones del tipo de dispositivo de Intune, puede usar la versión del sistema operativo del dispositivo para especificar qué dispositivos de usuario usarán la inscripción de perfil de trabajo de Android Enterprise o la inscripción de administrador de dispositivos Android.  Para obtener más información, consulte [Establecer restricciones de inscripción](../enrollment/enrollment-restrictions-set.md).

#### <a name="windows-autopilot-deployment-reports---3856172---"></a>Informes de implementación de Windows Autopilot<!-- 3856172 -->
Un nuevo informe detalla cada dispositivo implementado mediante Windows Autopilot. Para más información, vea [Informe de implementaciones de Autopilot](../enrollment/enrollment-autopilot.md#autopilot-deployments-report). Estamos en proceso de implementar esta característica para todos los clientes, y se espera que el proceso finalice al término de la semana próxima.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Administración de dispositivos

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Nuevas restricciones para cambiar el nombre de los dispositivos Windows<!-- 3478938  -->
Al cambiar el nombre de un dispositivo Windows, se deben seguir reglas nuevas:
- 15 caracteres o menos (debe ser menor o igual que 63 bytes, sin incluir el valor NULL final).
- No puede ser una cadena nula o vacía.
- Caracteres ASCII permitidos: letras (a-z, A-Z), números (0-9) y guiones.
- Caracteres Unicode permitidos: caracteres >=0x80, debe tener un formato UTF8 válido, debe ser asignable mediante IDN (es decir, el proceso RtlIdnToNameprepUnicode debe finalizar correctamente. Consulte el documento RFC 3492).
- El nombre no debe contener números exclusivamente.
- El nombre no debe contener espacios.
- Caracteres no permitidos: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 Para más información, vea [Cambio de nombre de un dispositivo en Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>Nuevo informe de Android en la página de información general de dispositivos<!-- 4924364 -->
Un nuevo informe en la página de información general de dispositivos muestra la cantidad de dispositivos Android inscritos en cada solución de administración de dispositivos. Este gráfico muestra la cantidad de dispositivos inscritos de perfil de trabajo, totalmente administrados, dedicados y de administrador de dispositivos. Para ver el informe, elija **Intune** > **Dispositivos** > **Información general**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>Certificados PKCS para macOS<!-- 1333650       -->
Ahora puede [usar certificados PKCS con macOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). Puede seleccionar el certificado PKCS como un tipo de perfil para macOS e implementar certificados de usuario y de dispositivo que tengan [campos de firmante y de nombre alternativo del firmante personalizados](../protect/certficates-pfx-configure.md#subject-name-format-for-macos).  

El certificado PKCS para macOS también admite una nueva opción, _Permitir el acceso de todas las aplicaciones_. Con ella, puede permitir el acceso de todas las aplicaciones asociadas a la clave privada del certificado.  Para más información sobre esta opción, vea la documentación de Apple en https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>Credenciales derivadas para aprovisionar dispositivos móviles iOS con certificados<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune admite el uso de [credenciales derivadas](../protect/derived-credentials.md) como método de autenticación y para el cifrado y la firma S/MIME de dispositivos iOS. Las credenciales derivadas son una implementación de la norma *800-157 del National Institute of Standards and Technology (NIST)* relativa a la implementación de certificados en dispositivos.  

Las credenciales derivadas se basan en el uso de una tarjeta de verificación de identidad personal (PIV) o una tarjeta de acceso común (CAC), como una tarjeta inteligente. Para obtener una credencial derivada para un dispositivo móvil, los usuarios comienzan en la aplicación Portal de empresa y siguen un flujo de trabajo de inscripción que es único para el proveedor que usen.  Un requisito común a todos los proveedores es usar una tarjeta inteligente en un equipo para autenticarse en el proveedor de las credenciales derivadas. Tras ello, dicho proveedor emite un certificado para el dispositivo que viene derivado de la tarjeta inteligente del usuario.  

Intune admite los siguientes proveedores de credenciales derivadas:
- DISA Purebred
- Entrust Datacard
- Intercede

Las credenciales derivadas se usan como método de autenticación de los perfiles de configuración de dispositivos de VPN, Wi-Fi y correo electrónico. También se pueden usar para la autenticación de aplicaciones y el cifrado y la firma S/MIME.  

Para más información sobre la norma, vea el documento sobre [credenciales PIV derivadas](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) en www.nccoe.nist.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Uso de Graph API para especificar un nombre principal de usuario local como una variable para certificados SCEP<!--  5437939        -->  
Cuando use [Graph API de Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0), puede especificar onPremisesUserPrincipalName como variable del nombre alternativo del firmante (SAN) de los certificados SCEP.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Semana del 23 de septiembre de 2019

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>Inscripción de usuario de iOS en versión preliminar<!-- 4817900 -->
La versión iOS 13.1 de Apple incluye Inscripción de usuario, una nueva forma de administración ligera para dispositivos iOS. Se puede usar en lugar de Inscripción de dispositivos o de Inscripción de dispositivo automatizada (anteriormente Programa de inscripción de dispositivos) para dispositivos de propiedad personal. La versión preliminar de Intune es compatible con este conjunto de características, ya que permite:

- Realizar la inscripción de usuarios de destino en grupos de usuarios.
- Ofrecer a los usuarios finales la posibilidad de seleccionar entre la inscripción de usuarios más ligera o la inscripción de dispositivos más segura cuando inscriban sus dispositivos.

A partir del 24/9/2019 con la versión 13.1 de iOS, estaremos en el proceso de implementar estas actualizaciones para todos los clientes y se espera que finalicen al final de la semana próxima.
Se aplica a:

iOS 13.1 y versiones posteriores

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Compatibilidad de Intune con dispositivos iPadOS e iOS 13.1<!--5439574-->
Intune admite ahora la administración de dispositivos iPadOS e iOS 13.1. Para más información, vea [esta entrada de blog](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>Semana del 16 de septiembre de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Administración de aplicaciones 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>Aplicaciones de LOB privadas de Google Play administrado<!-- 1464182  -->
Ahora, Intune permite a los administradores de TI publicar aplicaciones de LOB de Android privadas en Google Play administrado a través de un iframe incrustado en la consola de Intune.  Anteriormente, los administradores de TI tenían que publicar aplicaciones de LOB directamente en la consola de publicación de Google Play, lo cual requería varios pasos y llevaba mucho tiempo. Esta nueva característica permite publicar fácilmente aplicaciones de LOB siguiendo solo unos pocos pasos, sin necesidad de salir de la consola de Intune.  Los administradores ya no tendrán que registrarse manualmente como desarrolladores en Google, y tampoco será necesario abonar la tasa de registro de Google de 25 $.  Cualquiera de los escenarios de administración de Android Enterprise en que se use Google Play administrado pueden beneficiarse de esta característica (dispositivos con perfil de trabajo, dedicados, totalmente administrados y no inscritos). En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. Luego, en la lista **Tipo de aplicación**, seleccione **Google Play administrado**. Para obtener más información sobre las aplicaciones de Google Play administrado, consulte [Incorporación de aplicaciones de Google Play administrado a dispositivos Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Experiencia en el Portal de empresa de Windows<!-- 1473353, 3598357 -->
El Portal de empresa de Windows se está actualizando. Podrá usar varios filtros en la página Aplicaciones del Portal de empresa de Windows. La página Detalles del dispositivo también se está actualizando con una experiencia de usuario mejorada. Estamos en proceso de implementar estas actualizaciones para todos los clientes, que se espera que finalicen al final de la semana próxima.

#### <a name="macos-support-for-web-apps---3174427---"></a>Compatibilidad de macOS con aplicaciones web<!-- 3174427 -->
Las aplicaciones web, que le permiten agregar un acceso directo a una dirección URL en la web, se pueden instalar en el Dock mediante el Portal de empresa de macOS. Los usuarios finales pueden tener acceso a la acción de **instalación** desde la página de detalles de la aplicación para una aplicación web en el Portal de empresa de MacOS. Para más información sobre el tipo de aplicación de **vínculo web**, consulte [Incorporación de aplicaciones a Microsoft Intune](../apps/apps-add.md) y [Agregar aplicaciones web a Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps---3173501----"></a>Compatibilidad de macOS con las aplicaciones de VPP<!-- 3173501  -->
Las aplicaciones macOS, compradas con Apple Business Manager, se muestran en la consola cuando se sincronizan los tokens de VPP de Apple en Intune. Puede asignar, revocar y reasignar licencias basadas en dispositivos y usuarios para grupos mediante la consola de Intune. Microsoft Intune le ayuda a administrar las aplicaciones de VPP compradas para su uso en su empresa:

- Informes sobre la información de licencia desde la tienda de aplicaciones.
- Realizando un seguimiento de cuántas licencias ha usado.
- Le ayudamos a impedir la instalación de más copias de la aplicación que las que tiene.

Para más información, consulte [Administración de aplicaciones y libros comprados por volumen con Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support---2871756----"></a>Compatibilidad con iframe de Google Play administrado<!-- 2871756  -->
Intune ahora proporciona compatibilidad para agregar y administrar vínculos web directamente en la consola de Intune a través del iframe de Google Play administrado.  Esto permite a los administradores de TI enviar una dirección URL y un gráfico de iconos y, a continuación, implementar esos vínculos en dispositivos como aplicaciones Android normales. Cualquiera de los escenarios de administración de Android Enterprise en que se use Google Play administrado pueden beneficiarse de esta característica (dispositivos con perfil de trabajo, dedicados, totalmente administrados y no inscritos). En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. Luego, en la lista **Tipo de aplicación**, seleccione **Google Play administrado**. Para obtener más información sobre las aplicaciones de Google Play administrado, consulte [Incorporación de aplicaciones de Google Play administrado a dispositivos Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Instalación silenciosa de aplicaciones de LOB de Android en dispositivos Zebra<!-- 4252734  -->
Al instalar aplicaciones de línea de negocio (LOB) de Android en [dispositivos Zebra](../configuration/android-zebra-mx-overview.md), en lugar de que se le solicite la descarga e instalación de la aplicación de LOB, podrá instalar la aplicación de forma silenciosa. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. En el panel **Agregar aplicación**, seleccione **Aplicación de línea de negocio**. Para obtener más información, consulte [Incorporación de una aplicación de línea de negocio de Android a Microsoft Intune](../apps/lob-apps-android.md).

Actualmente, una vez descargada la aplicación de LOB, aparecerá una notificación informando de la **descarga correcta** en el dispositivo del usuario. La notificación solo se puede descartar pulsando **Borrar todo** en el sombreado de la notificación. Este problema se corregirá en una próxima versión y la instalación será totalmente silenciosa sin ningún indicador visual.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Operaciones de lectura y escritura de Graph API para aplicaciones de Intune<!-- 5031704  -->
Las aplicaciones pueden llamar a Graph API de Intune con operaciones de lectura y escritura mediante la identidad de la aplicación y sin credenciales de usuario. Para obtener más información sobre cómo obtener acceso a Microsoft Graph API para Intune, consulte [Trabajar con Intune en Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Cifrado y uso compartido de datos protegidos para el SDK de aplicaciones de Intune para iOS<!-- 3586942  -->
El SDK de aplicaciones de Intune para iOS usará claves de cifrado de 256 bits cuando el cifrado esté habilitado mediante las directivas de protección de aplicaciones. Todas las aplicaciones deberán tener una versión de SDK 8.1.1 para permitir el uso compartido de datos.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Compatibilidad con perfiles VPN de IKEv2 para iOS<!-- 1943438   -->
En esta actualización, puede crear perfiles VPN para el cliente VPN nativo de iOS mediante el protocolo IKEv2. IKEv2 es un nuevo tipo de conexión en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **VPN** para tipo de perfil > **Tipo de conexión**.

Estos perfiles de VPN configuran el cliente de VPN nativo, por lo que no se instalan ni insertan aplicaciones cliente de VPN en los dispositivos administrados. Esta característica exige que los dispositivos estén inscritos en Intune (inscripción de MDM).

Para ver la configuración VPN actual que puede establecer, vaya a [Configuración de VPN en dispositivos iOS](../configuration/vpn-settings-ios.md).

Se aplica a:
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>Las características del dispositivo, las restricciones de dispositivos y los perfiles de extensión de la configuración de iOS y macOS se muestran mediante el tipo de inscripción.<!-- 4886161   -->

En Intune, puede crear perfiles para dispositivos iOS y macOS (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **iOS** o **macOS** como plataforma > **Características del dispositivo**, **Restricciones de dispositivos** o **Extensiones** para tipo de perfil). 

En esta actualización, la configuración disponible en el portal de Intune se clasifica por el tipo de inscripción al que se aplica:

- iOS
  - Inscripción de usuarios
  - Inscripción de dispositivos
  - Inscripción de dispositivo automatizada (supervisado)
  - Todos los tipos de inscripción

- macOS
  - Aprobada por el usuario
  - Inscripción de dispositivos
  - Inscripción de dispositivo automatizada
  - Todos los tipos de inscripción

Se aplica a:
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>Nueva configuración del control de voz para dispositivos iOS supervisados que se ejecutan en pantalla completa<!-- 4892835   -->
En Intune, puede crear directivas para ejecutar dispositivos iOS supervisados como una pantalla completa, o un dispositivo dedicado (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **Pantalla completa**).

En esta actualización, hay nuevas opciones de configuración que puede controlar:
- **Control de voz**: Habilita el control de voz en el dispositivo mientras se encuentra en pantalla completa.
- **Modificación del control de voz**: Permite a los usuarios cambiar el ajuste del control de voz del dispositivo mientras se encuentra en pantalla completa.

Para ver la configuración actual, vaya a los [parámetros de pantalla completa de iOS](../configuration/device-restrictions-ios.md#kiosk).

Se aplica a:
- iOS 13.0 y versiones posteriores

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Uso del inicio de sesión único para aplicaciones y sitios web en los dispositivos iOS y macOS<!-- 4893175   -->
En esta actualización, hay algunos nuevos ajustes para el inicio de sesión único para dispositivos iOS y macOS (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **iOS** o **macOS** como plataforma > **Características del dispositivo** para tipo de perfil).

Use estas opciones para configurar una experiencia de inicio de sesión único, especialmente para aplicaciones y sitios web que usan la autenticación Kerberos. Puede elegir entre una extensión de aplicación de inicio de sesión único de credencial genérica y la extensión integrada de Kerberos de Apple.

Para ver las características de dispositivo actuales que puede configurar, vaya a las [características de dispositivo de iOS](../configuration/ios-device-features-settings.md) y [Características de dispositivo de macOS](../configuration/macos-device-features-settings.md).

Se aplica a:
- iOS 13.0 y versiones más recientes
- macOS 10.15 y versiones más recientes

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Asociación de dominios a aplicaciones en dispositivos macOS 10.15 y versiones posteriores<!-- 4898079   -->
En los dispositivos macOS, puede configurar diferentes características e incorporar estas características a los dispositivos mediante una directiva (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **macOS** para plataforma > **Características de dispositivo** para tipo de perfil). En esta actualización, puede asociar dominios a sus aplicaciones. Esta característica ayuda a compartir credenciales con sitios web relacionados con la aplicación, y se puede usar con la extensión de inicio de sesión único de Apple, vínculos universales y relleno automático de contraseñas. 

Para ver los parámetros actuales que puede configurar, vaya a [Configuración de características de dispositivos macOS en Intune](../configuration/macos-device-features-settings.md).

Se aplica a:
- macOS 10.15 y versiones más recientes

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Uso de "iTunes" y "apps" en la dirección URL de iTunes App Store al mostrar u ocultar aplicaciones en dispositivos iOS supervisados<!-- 4928474   --> 
En Intune, puede crear directivas para mostrar u ocultar aplicaciones en los dispositivos iOS supervisados (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **Mostrar u ocultar aplicaciones**). 

Puede especificar la dirección URL de iTunes App Store, como `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. En esta actualización, se pueden usar `apps` y `itunes` en la dirección URL, como:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Para obtener más información acerca de esta configuración, consulte [Mostrar u ocultar aplicaciones](../configuration/device-restrictions-ios.md#show-or-hide-apps).

Se aplica a:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Los valores de tipo de contraseña de la directiva de cumplimiento de Windows 10 son más claros y coinciden con CSP.<!-- 5138985 -->
En los dispositivos Windows 10, puede crear una directiva de cumplimiento que requiera características de contraseña específicas (**Cumplimiento de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10 y versiones posteriores** para plataforma > **Seguridad del sistema**). En esta actualización:
- Los valores de **Tipo de contraseña** son más claros y se han actualizado para coincidir con [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- El valor de **Expiración de contraseña (días)** se ha actualizado para permitir valores entre 1 y 730 días. 

Para obtener más información sobre la configuración del cumplimiento de Windows 10, consulte [Configuración de Windows 10 y versiones posteriores para marcar dispositivos como compatibles o no compatibles con Intune](../protect/compliance-policy-create-windows.md). 

Se aplica a:
- Windows 10 y versiones posteriores

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Actualización de la interfaz de usuario para configurar el acceso local de Microsoft Exchange<!-- 4092920 -->  
Hemos actualizado la consola en la que [configura el acceso local a Microsoft Exchange](../protect/conditional-access-exchange-create.md). Todas las configuraciones para el acceso local de Exchange están ahora disponibles en el mismo panel de la consola donde *habilita el control de acceso local de Exchange*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Permiso o restricción para la adición de widgets de aplicaciones a la pantalla principal en dispositivos de perfil de trabajo de Android Enterprise<!-- 1109650  --> 
En dispositivos Android Enterprise, puede configurar características en el perfil de trabajo (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para plataforma > **Solo perfil de trabajo > Restricciones de dispositivos** para tipo de perfil). En esta actualización, puede permitir que los usuarios agreguen widgets expuestos por las aplicaciones del perfil de trabajo a la pantalla principal del dispositivo.

Para ver los valores que puede configurar, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](../configuration/device-restrictions-android-for-work.md).

Se aplica a:
- Perfil de trabajo de Android Enterprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Los nuevos inquilinos desaparecerán de forma predeterminada de la administración del administrador de dispositivos de Android.<!-- 4869790   -->
Las funcionalidades del administrador de dispositivos de Android se han sustituido por Android Enterprise. Por lo tanto, se recomienda usar Android Enterprise para nuevas inscripciones. En una actualización futura, los nuevos inquilinos deberán completar los siguientes requisitos previos en la inscripción de Android para usar la administración del administrador de dispositivos: Vaya a **Intune** > **Inscripción de dispositivos** > **Inscripción de Android** > **Personal and corporate-owned devices with device administration privileges**(Dispositivos personales y corporativos con privilegios de administración de dispositivos) > **Use el administrador de dispositivos para administrar los dispositivos**.

Los inquilinos existentes no experimentarán cambio alguno en sus entornos.

Para obtener más información sobre el administrador de dispositivos Android en Intune, consulte [Inscripción del administrador de dispositivos Android](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>Lista de dispositivos DEP asociados a un perfil<!-- 5012045 idmiss -->
Ahora puede ver una lista paginada de los dispositivos del Programa de inscripción de dispositivos (DEP) automatizados de Apple que están asociados a un perfil. Puede buscar en la lista desde cualquier página. Para ver la lista, vaya a **Intune** > **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > elija un token > **Perfiles** > elija un perfil > **Dispositivos asignados** (bajo **Supervisar**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Administración de dispositivos

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>Más compatibilidad con dispositivos Android totalmente administrados<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Hemos agregado la siguiente compatibilidad con dispositivos Android totalmente administrados:

- Los certificados SCEP para dispositivos Android totalmente administrados están disponibles para la autenticación de certificados en dispositivos administrados como propietario del dispositivo. Los certificados SCEP ya se admiten en los dispositivos con perfil de trabajo.  Con los certificados SCEP para el propietario del dispositivo, podrá: <!-- 5227935 -->
    - crear un perfil de SCEP en la sección correspondiente de Android Enterprise
    - vincular certificados SCEP con el perfil de Wi-Fi del propietario del dispositivo para la autenticación
    - vincular certificados SCEP con los perfiles VPM del propietario del dispositivo para la autenticación
    - vincular certificados SCEP con los perfiles de correo electrónico del propietario del dispositivo para la autenticación (a través de AppConfig)
- Las aplicaciones del sistema son compatibles con dispositivos de Android Enterprise. En Intune, agregue una aplicación del sistema Android Enterprise seleccionando **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación**, seleccione **Aplicación del sistema Android Enterprise**. Para más información, vea [Agregar aplicaciones del sistema Android Enterprise a Microsoft Intune](../apps/apps-ae-system.md). <!-- 4062195 -->
- En **Cumplimiento de dispositivos** > **Android Enterprise** > **Propietario del dispositivo**, puede crear una directiva de cumplimiento que cumpla con el nivel de atestación de Google SafetyNet.   <!-- 4631425 -->
- En dispositivos Android Enterprise totalmente administrados, se admiten los proveedores de Mobile Threat Defense. En **Cumplimiento de dispositivos** > **Android Enterprise** > **Propietario del dispositivo**, puede elegir un nivel de amenaza aceptable. <!-- 4631440 --> En [Configuración de Android Enterprise para marcar dispositivos como compatibles o no compatibles con Intune](../protect/compliance-policy-create-android-for-work.md#device-owner) se muestra la configuración actual.
- En los dispositivos Android Enterprise totalmente administrados, la aplicación Microsoft Launcher ahora se puede configurar a través de directivas de configuración de aplicaciones para permitir una experiencia de usuario final estandarizada en el dispositivo totalmente administrado. La aplicación Microsoft Launcher se puede usar para personalizar el dispositivo Android. Usando la aplicación con una cuenta Microsoft o una cuenta profesional o educativa, puede acceder a su calendario, documentos y actividades recientes en la fuente personalizada. <!-- 5334044 -->

Con esta actualización, nos complace anunciar que la compatibilidad de Intune con Android Enterprise totalmente administrado ya está disponible con carácter general.

Se aplica a:

- Dispositivos totalmente administrados de Android Enterprise

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>Envío de notificaciones personalizadas a un solo dispositivo<!-- 4928910 -->
Ahora puede seleccionar un solo dispositivo y, a continuación, usar una acción de dispositivo remoto para [enviar una notificación personalizada solo a ese dispositivo](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>Las acciones de borrado y restablecimiento de código de acceso no están disponibles para los dispositivos iOS inscritos mediante la inscripción de usuarios.<!-- 4950491 -->
La inscripción de usuarios es un nuevo tipo de inscripción de dispositivos de Apple. Al inscribir dispositivos mediante la inscripción de usuarios, las acciones remotas de borrado y restablecimiento de código de acceso no estarán disponibles para dichos dispositivos.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Compatibilidad de Intune con dispositivos iOS 13 y macOS Catalina<!-- 4665317 -->
Intune admite ahora la administración de dispositivos iOS 13 y macOS Catalina.
Para más información, vea la [entrada de blog sobre la compatibilidad de Microsoft Intune con iOS 13 y iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>Compatibilidad de BitLocker con la rotación de contraseñas de recuperación controlada por el cliente<!--  3444125 -->
Use la configuración de Endpoint Protection de Intune para configurar la [rotación de contraseñas de recuperación controlada por el cliente](../protect/endpoint-protection-windows-10.md#windows-encryption) para BitLocker en dispositivos que ejecutan la versión 1909 de Windows o una posterior.

Esta configuración inicia una actualización de la contraseña de recuperación controlada por el cliente después de la recuperación de la unidad del sistema operativo (mediante bootmgr o WinRE) y un desbloqueo de la contraseña de recuperación en una unidad de datos fija. Esta opción actualiza la contraseña de recuperación específica que se usó, y otras contraseñas no usadas en el volumen permanecen sin cambios. Para obtener más información, consulte la documentación de CSP de BitLocker para [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Protección contra alteraciones para el antivirus de Windows Defender<!-- 4705448        -->
Use Intune para administrar la *Protección contra alteraciones* para el antivirus de Windows Defender. Encontrará el [ajuste para la Protección contra alteraciones](../protect/endpoint-protection-windows-10.md#windows-defender-security-center) en el grupo del centro de seguridad de Microsoft Defender al usar perfiles de configuración de dispositivos para Windows 10 Endpoint Protection. Puede establecer la Protección contra alteraciones en *Habilitado* para activar las restricciones de la Protección contra alteraciones, en *Deshabilitado* para desactivarlas o bien en *No configurado* para dejar la configuración actual de los dispositivos.  

Para obtener más información acerca de la Protección contra alteraciones, vea [Evitar cambios de la configuración de seguridad con Protección contra alteraciones](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) en la documentación de Windows.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>La configuración avanzada del Firewall de Windows Defender ya está disponible con carácter general.<!--  5317392       -->  
Las [reglas de firewall personalizadas de Windows Defender para Endpoint Protection](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), que se configuran como parte de un perfil de configuración de dispositivos, ya están disponibles con carácter general en tanto que versión preliminar pública.  Puede usar estas reglas para especificar un comportamiento entrante y saliente en las aplicaciones, las direcciones de red y los puertos. Estas reglas se publicaron en julio como una versión preliminar pública. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>Las etiquetas de ámbito ahora son compatibles con las directivas de términos de uso.<!-- 2358863 idmiss -->
Ahora puede asignar [etiquetas de ámbito](scope-tags.md) a las directivas de términos de uso. Para ello, vaya a **Intune** > **Inscripción de dispositivos** > **Términos y condiciones** > elija un elemento de la lista > **Propiedades** > **Etiquetas de ámbito** > elija una etiqueta de ámbito.

## <a name="week-of-september-9-2019"></a>Semana del 9 de septiembre de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Actualizaciones a la aplicación de Microsoft Intune<!-- 4997846 -->
La aplicación de Microsoft Intune para Android se ha actualizado con las siguientes mejoras:
- Se ha actualizado y mejorado el diseño para incluir la navegación inferior para las acciones más importantes.
- Se ha agregado una página adicional que muestra el perfil del usuario.
- Se ha agregado la muestra de notificaciones interactivas en la aplicación para el usuario, como la necesidad de actualizar la configuración del dispositivo.
- Se ha agregado la muestra de notificaciones push personalizadas, alineando la aplicación con la compatibilidad agregada recientemente en la aplicación Portal de empresa para iOS y Android. Para más información, consulte [Envío de notificaciones personalizadas en Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>Para dispositivos iOS, personalice la pantalla de privacidad del proceso de inscripción del Portal de empresa.<!-- 4394993 -->
Con Markdown, puede personalizar la pantalla de privacidad del Portal de empresa que los usuarios finales ven durante la inscripción de iOS. En concreto, podrá personalizar la lista de elementos que la organización no puede ver o realizar en el dispositivo. Para más información, consulte [Configuración de la aplicación Portal de empresa de Intune](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Semana del 2 de septiembre de 2019

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Actualización de la interfaz de usuario de Intune: panel Estado del inquilino<!-- 5273210  -->
La interfaz de usuario para el panel Estado del inquilino se actualizó para alinearla con los estilos de interfaz de usuario de Azure. Para más información, consulte [Estado del inquilino](../tenant-status.md).

## <a name="week-of-august-26-2019"></a>Semana del 26 de agosto de 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Configuración de Microsoft Edge mediante plantillas administrativas para Windows 10 y versiones más recientes<!-- 5228061 -->

En los dispositivos Windows 10 y más recientes, puede crear plantillas administrativas para configurar las opciones de directiva de grupo en Intune. En esta actualización, puede configurar las opciones que se aplican a la versión 77 y posteriores de Microsoft Edge.

Para más información sobre las plantillas administrativas, vea [Usar plantillas de Windows 10 para configurar opciones de directiva de grupo en Intune](../configuration/administrative-templates-windows.md).

Se aplica a:

- Windows 10 y versiones más recientes (Windows RS4+)

## <a name="week-of-august-12-2019"></a>Semana del 12 de agosto de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>Control del comportamiento de desinstalación de aplicaciones iOS en anulación de la inscripción de dispositivos<!-- 3504144   -->
Los administradores pueden administrar si una aplicación se quita de un dispositivo o se conserva en este cuando se anula la inscripción de dicho dispositivo en el nivel de grupo de usuarios o dispositivos. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Categorización de aplicaciones de Microsoft Store para Empresas<!-- 3926922 -->
Puede categorizar las aplicaciones de la Tienda Microsoft para Empresas. Para ello, elija aplicaciones  > **cliente** > de **Intune** **aplicaciones** > seleccione una aplicación de Microsoft Store para empresas  > **categoría**de **información**de la aplicación. En el menú desplegable, asigne una categoría.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Notificaciones personalizadas para usuarios de aplicaciones de Microsoft Intune<!-- 4843354  -->
La aplicación de Microsoft Intune para Android ahora admite la visualización de notificaciones de envío personalizadas y se alinea con la compatibilidad agregada recientemente en las aplicaciones de Portal de empresa para iOS y Android. Para más información, consulte [Envío de notificaciones personalizadas en Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>Nuevas características para dispositivos dedicados de Android Enterprise en el modo de varias aplicaciones<!-- 3755304 3041943 3041946   -->

En Intune, puede controlar las características y las configuraciones en una experiencia de estilo de quiosco en dispositivos dedicados (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Solo el propietario del dispositivo, Restricciones de dispositivos** para el tipo de perfil).

En esta actualización, se agregan las siguientes características:

- **Dispositivos dedicados** > **Varias aplicaciones:** el **botón Inicio virtual** se puede mostrar al avanzar en el dispositivo o flotar en la pantalla para que los usuarios puedan moverla.
- **Dispositivos dedicados** > **Varias aplicaciones:** **Acceso a la linterna** permite a los usuarios usar la linterna. 
- **Dispositivos dedicados** > **Varias aplicaciones:** **Control del volumen de elementos multimedia**  permite a los usuarios controlar el volumen multimedia del dispositivo con un control deslizante. 
- **Dispositivos dedicados** > **Varias aplicaciones:**  **habilite un protector de pantalla**, cargue una imagen personalizada y controle cuándo se muestra el protector.

Para ver la configuración actual, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Se aplica a:

- Dispositivos Android Enterprise dedicados

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Nueva aplicación y perfiles de configuración para dispositivos Android Enterprise totalmente administrados<!-- 3574215 3574238 3574235 3574232   -->
Mediante el uso de perfiles, puede configurar las opciones que aplican la configuración de VPN, correo electrónico y Wi-Fi al propietario de dispositivos (totalmente administrados) Android Enterprise. En esta actualización, puede:

- Use las [directivas de configuración de aplicaciones](../apps/app-configuration-policies-use-android.md) para implementar la configuración de correo electrónico de Outlook, Gmail y Nine Work.
- Use los perfiles de configuración de dispositivos para implementar la [configuración de certificados raíz de confianza](../protect/certificates-configure.md).
- Use los perfiles de configuración de dispositivos para implementar la configuración de [VPN](../configuration/vpn-settings-android-enterprise.md) y [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md).

> [!IMPORTANT]
> Con esta característica, los usuarios se autentican con su nombre de usuario y contraseña para los perfiles de VPN, Wi-Fi y correo electrónico. Actualmente, la autenticación basada en certificados no está disponible.

Se aplica a:  
- Propietario del dispositivo Android Enterprise (totalmente administrado)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>Control de las aplicaciones, los archivos, los documentos y las carpetas que se abren cuando los usuarios inician sesión en dispositivos macOS<!--3914202   -->
Puede habilitar y configurar características de dispositivos macOS (**Configuración del dispositivos** > **Perfiles** > **Crear perfil** > **macOS** para la plataforma >**Características del dispositivo**  para el tipo de perfil). 

En esta actualización, hay una nueva configuración de elementos de inicio de sesión para controlar qué aplicaciones, archivos, documentos y carpetas se abren cuando un usuario inicia sesión en el dispositivo inscrito. 

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](../configuration/macos-device-features-settings.md).

Se aplica a:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Las fechas límite reemplazan la configuración del reinicio establecido de los anillos de Windows Update<!-- 4464404        -->
Para estar en consonancia con [los cambios recientes en el servicio de Windows](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing), los anillos de actualización de Windows 10 de Intune ahora [admiten la configuración de fechas límite](../protect/windows-update-settings.md). Las *fechas límite* determinan cuándo un dispositivo instala las actualizaciones de características y seguridad.  En los dispositivos que ejecutan Windows 10 1903 o una versión posterior, las *fechas límite* sustituyen a las configuraciones del *reinicio establecido*.  En el futuro, las *fechas límite* reemplazarán también al *reinicio establecido* de las versiones anteriores de Windows 10.  

Cuando no se configuran *fechas límite*, los dispositivos seguirán usando la configuración de *Reinicio establecido*, pero Intune dejará de admitir la configuración de Reinicio establecido en una actualización futura.  

Planee el uso de *fechas límite* para todos los dispositivos Windows 10. Una vez que haya establecido la configuración de las *fechas límite*, puede cambiar las configuraciones de Intune para que el *reinicio establecido* sea Sin configurar. Cuando se establece en Sin configurar, Intune deja de administrar esa configuración en los dispositivos, pero no quita las últimas configuraciones de la configuración del dispositivo. Por lo tanto, las últimas configuraciones que se establecieron para el *reinicio establecido* permanecen activas y en uso en los dispositivos hasta que dichas configuraciones se modifican mediante un método distinto de Intune. Más adelante, cuando la versión de los dispositivos de Windows cambia o cuando la compatibilidad de Intune con las *fechas límite* se expande a la versión de Windows de los dispositivos, el dispositivo comenzará a usar la nueva configuración, que ya está en su lugar.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>Compatibilidad con varias instancias de Microsoft Intune Certificate Connector<!--   4704642      -->
Intune ahora admite la instalación y el uso de varias instancias de [Microsoft Intune Certificate Connectors para operaciones PKCS](../protect/certficates-pfx-configure.md). Este cambio admite el equilibrio de carga y la alta disponibilidad del conector. Cada instancia de conector puede procesar solicitudes de certificado desde Intune.  Si un conector no está disponible, otros conectores continúan procesando las solicitudes.

Para usar varios conectores, no es necesario actualizar a la versión más reciente del software del conector.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>Nuevas configuraciones y cambios en la configuración existente para restringir características en dispositivos iOS y macOS<!-- 4867699 4867709   -->
Puede crear perfiles para restringir configuraciones en dispositivos que ejecutan iOS y macOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** o **macOS** para el tipo de plataforma > **Restricciones de dispositivos**). En esta actualización se incluyen las características siguientes:

- En**macOS** > **Restricciones de dispositivos** > **Nube y almacenamiento** use la nueva configuración **Handoff** para impedir que los usuarios empiecen a trabajar en un dispositivo macOS y sigan trabajando en otro dispositivo macOS o iOS.

  Para ver la configuración actual, vaya a [Configuración de dispositivos macOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-macos.md).

- En **iOS** > **Restricciones de dispositivos**, hay algunos cambios:

  - **Aplicaciones integradas** > **Buscar mi iPhone (solo supervisado)** : nueva configuración que bloquea esta característica en la característica Buscar mi aplicación. 
  - **Aplicaciones integradas** > **Find My Friends (solo supervisado)** : nueva configuración que bloquea esta característica en la característica Buscar mi aplicación. 
  - **Inalámbrica** > **Modificación del estado de Wi-Fi (solo supervisado)** : nueva configuración que impide que los usuarios activen o desactiven la conexión Wi-Fi en el dispositivo.
  - **Teclado y diccionario** > **QuickPath (solo supervisado)** : nueva configuración que bloquea la característica QuickPath.
  - **Nube y almacenamiento**: **Continuación de la actividad** pasa a llamarse **Handoff**.

  Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md).

Se aplica a:  
- macOS 10.15 y versiones más recientes
- iOS 13 y versiones más recientes

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Algunas restricciones de dispositivos iOS no supervisadas se supervisarán solo con la versión iOS 13.0<!-- 4867809   -->
En esta actualización, algunas configuraciones se aplican a los dispositivos solo supervisados con la versión iOS 13.0. Si esta configuración se definen y asignan a dispositivos no supervisados antes de la versión de iOS 13.0, dicha configuración se seguirá aplicando a esos dispositivos no supervisados. También se aplican después de que los dispositivos se actualicen a iOS 13.0. Estas restricciones se quitan de los dispositivos no supervisados de los que se realiza una copia de seguridad y se restauran.

Estas opciones incluyen:

- Tienda de aplicaciones, presentación de documentos, juegos
  - Tienda de aplicaciones
  - Música, podcasts o contenido de noticias explícitos de iTunes
  - Incorporación de amigos a Game Center
  - Juego multijugador
- Aplicaciones integradas
  - Cámara
    - FaceTime
  - Safari
    - Autorrellenar
- Nube y almacenamiento
  - Copia de seguridad en iCloud
  - Bloquear la sincronización de documentos de iCloud
  - Bloquear la sincronización de Keychain en iCloud

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md).

Se aplica a:  
- iOS 13.0 y versiones más recientes

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>Estado de dispositivo mejorado para el cifrado de FileVault de macOS<!-- 4944983         -->
Hemos actualizado varios [mensajes de estado de dispositivo](../protect/encryption-monitor.md#device-encryption-status) para el cifrado de FileVault en dispositivos macOS.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>Algunas configuraciones de examen del Antivirus de Windows Defender en el informe muestran un estado de error<!-- 5119229 -->
En Intune, puede crear directivas para usar el Antivirus de Windows Defender para examinar los dispositivos Windows 10 (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para la plataforma > **Restricciones del dispositivo** para el tipo de perfil > **Antivirus de Windows Defender**). Los informes **Hora a la que se realizará un examen rápido diario** y **Tipo de examen del sistema para realizar** muestran un estado de error, cuando es realmente un estado correcto. 

En esta actualización se ha corregido este comportamiento. Por lo tanto las configuraciones **Hora a la que se realizará un examen rápido diario** y **Tipo de examen del sistema para realizar** muestran un estado correcto cuando los exámenes se completan correctamente y muestran un estado de error cuando la configuración no se puede aplicar.

Para más información sobre la configuración de Windows Defender Antivirus consulte [Configuración de dispositivos con Windows 10 y versiones posteriores para permitir o restringir características mediante Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="default-scope-tags---3702875----"></a>Etiquetas de ámbito predeterminadas<!-- 3702875  -->
Ahora hay disponible una nueva etiqueta de ámbito predeterminada integrada. Todos los objetos de Intune no etiquetados que admiten etiquetas de ámbito se asignan automáticamente a la etiqueta de ámbito predeterminada. La etiqueta de ámbito **predeterminada** se agrega a todas las asignaciones de roles existentes para mantener la paridad con la experiencia de administración hoy en día. Si no desea que un administrador vea los objetos de Intune con la etiqueta de ámbito predeterminada, quítela de la asignación de roles. Esta característica es similar a la característica de ámbitos de seguridad de System Center Configuration Manager. Para más información, consulte [Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito para TI distribuida](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Soporte técnico del administrador de dispositivos de inscripción de Android<!-- 4869749   -->
La opción de inscripción del administrador de dispositivos Android se ha agregado a la página Inscripción de Android (**Intune** > **Inscripción de dispositivos** > **Inscripción de Android** ). El administrador de dispositivos Android seguirá estando habilitado de forma predeterminada para todos los inquilinos.  Para más información, consulte [Inscripción del administrador de dispositivos Android](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Omisión de más pantallas en el Asistente de configuración <!--4877451  -->
Puede establecer perfiles de Programa de inscripción de dispositivos para omitir las siguientes pantallas del Asistente de configuración:
- Para iOS
    - Apariencia
    - Express Language (Idioma rápido)
    - Idioma preferido
    - Device to Device Migration (Migración entre dispositivos)
- Para macOS
    - Tiempo de pantalla
    - Configuración de Touch ID

Para más información sobre la personalización del Asistente de configuración, consulte [Creación de un perfil de inscripción de Apple](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) y [Creación de un perfil de inscripción de Apple para macOS](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Incorporación de una columna de usuario al proceso de carga de CSV del dispositivo AutoPilot<!-- 3823054 -->
Ahora puede agregar una columna de usuario a la carga CSV para Dispositivos Autopilot. Esto le permite asignar usuarios en masa en el momento de importar el archivo CSV. Para más información, consulte [Inscripción de dispositivos Windows en Intune con Windows Autopilot](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Administración de dispositivos

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Configuración del límite de tiempo de limpieza automática de dispositivos en treinta días<!--4231059  -->
Puede establecer el límite de tiempo de limpieza automática de dispositivos en un plazo de 30 días (en lugar del límite anterior de noventa días) después del último inicio de sesión. Para ello, vaya a **Intune** > **configuración** > de**dispositivos** > **limpiar reglas**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Número de compilación incluido en la página Hardware del dispositivo Android<!-- 4461910   -->
Una nueva entrada en la página Hardware de cada dispositivo Android incluye el número de compilación del sistema operativo del dispositivo. Para más información, consulte [Ver detalles del dispositivo en Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Semana del 5 de agosto de 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies es un OEM admitido para OEMConfig en dispositivos Android Enterprise<!-- 4843713 -->

En Intune, puede crear perfiles de configuración de dispositivo y aplicar la configuración a los dispositivos Android Enterprise mediante OEMConfig (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **OEMConfig** para el tipo de perfil).

En esta actualización, Zebra Technologies es un fabricante de equipos originales (OEM) admitido para OEMConfig. Para obtener más información sobre OEMConfig, consulte [Uso y administración de dispositivos Android Enterprise con OEMConfig](../configuration/android-oem-configuration-overview.md).

Se aplica a:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Semana del 22 de julio de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Notificaciones personalizadas para usuarios y grupos<!-- 16766574          -->
Envíe notificaciones de inserción personalizadas desde la aplicación del Portal de empresa a los usuarios en dispositivos iOS y Android que administra con Intune. Estas notificaciones de inserción móviles son altamente personalizables con texto libre y se pueden usar con cualquier fin. Puede dirigirlas a diferentes grupos de usuarios de su organización. Para obtener más información, consulte [Notificaciones personalizadas](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>Aplicación de controlador de directiva de dispositivo de Google<!-- 3041950  -->
La aplicación de Pantalla principal administrada ahora proporciona acceso a la aplicación de directiva de dispositivo Android de Google. La aplicación de Pantalla principal administrada es un iniciador personalizado que se usa para dispositivos inscritos en Intune, como dispositivos dedicados de Android Enterprise (AE) que usan el modo de pantalla completa de varias aplicaciones. Puede acceder a la aplicación de directiva de dispositivo Android o guiar a los usuarios a esta aplicación, con fines de soporte técnico y depuración. Esta capacidad de inicio está disponible en el momento en que el dispositivo se inscribe y se bloquea en la Pantalla principal administrada. No se necesitan instalaciones adicionales para usar esta funcionalidad.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Configuración de protección de Outlook para dispositivos iOS y Android<!-- 3212619 -->
Ahora puede configurar los valores de configuración de protección generales de datos y aplicaciones para Outlook para iOS y Android mediante controles de administración de Intune simples sin inscripción de dispositivos. Los valores de configuración generales de aplicaciones proporcionan paridad con la configuración que pueden habilitar los administradores al administrar Outlook para iOS y Android en dispositivos inscritos. Para obtener más información sobre la configuración de Outlook, consulte [Implementación de Outlook para iOS y opciones de configuración de aplicación de Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Uso de "reglas de aplicabilidad" al crear perfiles de configuración de dispositivo Windows 10 <!-- 2549910 eeready   idstaged -->

Puede crear perfiles de configuración de dispositivo Windows 10 (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Windows 10** para la plataforma > **Reglas de aplicabilidad**). En esta actualización, puede crear una **regla de aplicabilidad** para que el perfil solo se aplique a una edición o una versión en concreto. Por ejemplo, cree un perfil que permita algunas opciones de configuración de BitLocker. Una vez que agregue el perfil, use una regla de aplicabilidad para que este solo se aplique a los dispositivos que ejecuten Windows 10 Enterprise.

Para agregar una regla de aplicabilidad, consulte [Reglas de aplicabilidad](../configuration/device-profile-create.md#applicability-rules).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>Uso de tokens para agregar información específica del dispositivo en perfiles personalizados para dispositivos iOS y macOS<!-- 3330008  -->
Puede usar perfiles personalizados en dispositivos iOS y macOS para configurar opciones y características no integradas en Intune (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** o **macOS** para la plataforma > **Personalizado** para el tipo de perfil). En esta actualización, puede agregar tokens a sus archivos `.mobileconfig` para agregar información específica del dispositivo. Por ejemplo, puede agregar `Serial Number: {{serialnumber}}` a su archivo de configuración para mostrar el número de serie del dispositivo.

Para crear un perfil personalizado, consulte [Configuración personalizada de iOS](../configuration/custom-settings-ios.md) o [Configuración personalizada de macOS](../configuration/custom-settings-macos.md).

Se aplica a:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Nuevo diseñador de configuraciones al crear un perfil OEMConfig para Android Enterprise<!-- 3712769   -->
En Intune, puede crear un perfil de configuración de dispositivo que use una aplicación OEMConfig (Configuración del dispositivo > Perfiles > Crear perfil > Android Enterprise para la plataforma > OEMConfig para el tipo de perfil). Al hacerlo, se abre un editor JSON con una plantilla y valores que debe cambiar. 

Esta actualización incluye un diseñador de configuraciones con una experiencia de usuario mejorada que muestra detalles insertados en la aplicación entre los que se incluyen títulos, descripciones, etc. El editor JSON sigue estando disponible y muestra cualquier cambio que realiza en el diseñador de aplicaciones.

Para ver la configuración actual, vaya a [Uso y administración de dispositivos Android Enterprise con OEMConfig](../configuration/android-oem-configuration-overview.md).

Se aplica a: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Interfaz de usuario actualizada para configurar Windows Hello<!-- 4089576            -->
Hemos actualizado la consola donde [configura Intune para usar Windows Hello para empresas](../protect/windows-hello.md). Ya están disponibles todas las opciones de configuración en el mismo panel de la consola donde habilita compatibilidad con Windows Hello.

#### <a name="intune-powershell-sdk---4924113---"></a>SDK de PowerShell de Intune<!-- 4924113 --> 
El SDK de PowerShell de Intune, que proporciona compatibilidad con la API de Intune a través de Microsoft Graph, se ha actualizado a la versión 6.1907.1.0. Ahora, el SDK admite lo siguiente:
- Funciona con Azure Automation.
- Admite operaciones de lectura de autenticación de solo aplicación. 
- Admite nombres abreviados descriptivos como alias.
- Se ajusta a las convenciones de nomenclatura de PowerShell. De forma específica, se ha cambiado el nombre del parámetro `PSCredential` (en el cmdlet `Connect-MSGraph`) por `Credential`.
- Admite la especificación manual del valor del encabezado `Content-Type` al usar el cmdlet `Invoke-MSGraphRequest`.

Para obtener más información, consulte [SDK de PowerShell para Graph API de Microsoft Intune](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Actualizaciones de las restricciones de inscripción<!-- 2871968 -->
Las restricciones de inscripción para nuevos inquilinos se han actualizado para que se permitan los perfiles de trabajo de Android Enterprise de forma predeterminada. Los inquilinos existentes no experimentarán cambio alguno. Para usar los perfiles de trabajo de Android Enterprise, aún deberá [conectar su cuenta de Intune a su cuenta de Google Play administrada](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Actualizaciones de interfaz de usuario de las restricciones de inscripción y la inscripción de Apple<!--4089575, 4089579  -->
Los dos procesos siguientes usan una interfaz de usuario de estilo de asistente:
- Inscripción de dispositivos de Apple. Para obtener más información, consulte [Inscripción automática de dispositivos iOS con el Programa de inscripción de dispositivos de Apple](../enrollment/device-enrollment-program-enroll-ios.md).
- Creación de restricciones de inscripción. Para obtener más información, consulte [Establecer restricciones de inscripción](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>Control de la configuración previa de identificadores de dispositivos corporativos para dispositivos Android Q<!-- 4711509  idmiss -->
En Android Q (v10), Google no permitirá a los agentes MDM de dispositivos Android (administrador de dispositivos) administrados heredados recopilar información del identificador de dispositivo.  Intune tiene una característica que permite a los administradores de TI [configurar de forma previa una lista de números de serie del dispositivo](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) para etiquetar automáticamente estos dispositivos como propiedad corporativa. Esta característica no funcionará para los dispositivos Android Q que administre el administrador de dispositivos.  Independientemente de si se carga el número de serie o IMEI del dispositivo, siempre se considerará personal durante la inscripción de Intune.  Puede cambiar manualmente la propiedad a corporativa tras la inscripción.  Esto solo afecta a las nuevas inscripciones, no a los dispositivos inscritos existentes.  Los dispositivos Android administrados con perfiles de trabajo no se ven afectados por este cambio y continuarán funcionando como lo hacen en la actualidad.  Además, los dispositivos Android Q inscritos como administrador de dispositivos ya no podrán informar sobre el número de serie o IMEI en la consola de Intune como propiedades del dispositivo.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Los iconos han cambiado para las inscripciones de Android Enterprise (perfil de trabajo, dispositivos dedicados y dispositivos completamente administrados)<!-- 4977730 -->
Los iconos de los perfiles de inscripción de Android Enterprise han cambiado. Para ver los nuevos iconos, vaya a **Intune** > **Inscripción** > **Inscripción de Android** > busque en **Perfiles de inscripción**.


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Cambio en la recopilación de datos de diagnóstico de Windows<!-- 4113859 -->
El valor predeterminado de la recopilación de datos de diagnóstico ha cambiado para los dispositivos con la versión 1903 de Windows 10 y posteriores. A partir de Windows 10 1903, la recopilación de datos de diagnóstico se habilita de forma predeterminada. Los datos de diagnóstico de Windows son datos técnicos vitales de dispositivos Windows sobre el dispositivo y el rendimiento de Windows y el software relacionado. Para obtener más información, consulte [Configurar los datos de diagnóstico de Windows en la organización](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Los dispositivos Autopilot también participan en la telemetría "completa" a menos que se establezca lo contrario en el perfil de Autopilot con [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Administración de dispositivos

#### <a name="improve-device-location---3855417----"></a>Mejora de la ubicación del dispositivo<!-- 3855417  -->
Puede acercar las coordenadas exactas de un dispositivo mediante la acción **Buscar dispositivo**. Para obtener más información sobre cómo buscar dispositivos iOS perdidos, consulte [Búsqueda de dispositivos iOS perdidos](../remote-actions/device-locate.md).

### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Configuración avanzada del Firewall de Windows Defender (versión preliminar pública)<!--  1311949     -->  
Use Intune para administrar las [reglas de firewall personalizadas como parte de un perfil de configuración de dispositivo](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) para Endpoint Protection en Windows 10. Las reglas pueden especificar un comportamiento entrante y saliente en las aplicaciones, las direcciones de red y los puertos. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Interfaz de usuario actualizada para administrar líneas de base de seguridad<!-- 4091125     -->
Hemos actualizado la [experiencia de creación y edición](../protect/security-baselines.md#create-the-profile) en la consola de Intune para nuestras líneas de base de seguridad. Los cambios son:

Un formato de estilo de asistente que se ha comprimido en una sola hoja. en una hoja. Este nuevo diseño elimina la expansión de la hoja que requiere que los profesionales de TI exploren en profundidad varios paneles independientes.  
Ahora puede crear asignaciones como parte de la experiencia de creación y edición, en lugar de tener que volver posteriormente para asignar líneas de base. Hemos agregado un resumen de la configuración que puede ver antes de crear una nueva línea de base y al editar una existente. Al editar, en el resumen solo se muestra la lista de elementos establecidos en la primera categoría de propiedades editadas.

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Semana del 15 de julio de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Iconos Managed Home Screen y Configuración administrada<!-- 4918107 -->
El icono de la aplicación Managed Home Screen y el icono **Configuración administrada** se han actualizado. La aplicación Managed Home Screen solo la usan dispositivos inscritos en Intune, como dispositivos dedicados de Android Enterprise (AE) y que se ejecutan en modo de pantalla completa con varias aplicaciones. Para obtener más información sobre la aplicación de Pantalla principal administrada, consulte [Configuración de la aplicación Managed Home Screen de Microsoft para Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Directiva de dispositivos Android en dispositivos dedicados de Android Enterprise<!-- 4918136 -->
Puede obtener acceso a la aplicación Directiva de dispositivos Android en la pantalla de depuración de la aplicación Managed Home Screen. La aplicación Managed Home Screen solo la usan dispositivos inscritos en Intune, como dispositivos dedicados de Android Enterprise (AE) y que se ejecutan en modo de pantalla completa con varias aplicaciones. Para obtener más información, consulte [Configuración de la aplicación Managed Home Screen de Microsoft para Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>Actualizaciones del Portal de empresa de iOS<!-- 3902931 -->
El nombre de la empresa reemplazará el texto "i.manage.microsoft.com" actual en los mensajes de administración de aplicaciones iOS. Por ejemplo, los usuarios verán el nombre de la empresa en lugar de "i.manage.microsoft.com" cuando intenten instalar una aplicación iOS desde el portal de empresa o cuando permitan la administración de la aplicación. Esto se implantará para todos los clientes en los próximos días.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>Administración de FileVault para macOS<!--  3858502 + 4557986 + 1210104  -->
Puede usar Intune para [administrar el cifrado de claves de FileVault para dispositivos macOS](../protect/encrypt-devices.md). Para cifrar los dispositivos, debe usar un perfil de configuración de dispositivos de Endpoint Protection.

Nuestra compatibilidad con FileVault incluye el cifrado de dispositivos descifrados, la custodia de la clave de recuperación personal de un dispositivo, la rotación automática o manual de claves de cifrado personales y la recuperación de clave para sus dispositivos corporativos. Los usuarios finales también pueden utilizar el sitio web del Portal de empresa para obtener la clave de recuperación personal para sus dispositivos cifrados.

También hemos expandido el informe de cifrado para incluir [información sobre FileVault](../protect/encryption-monitor.md) con información para BitLocker, de modo que puede ver todos los detalles del cifrado del dispositivo en un solo lugar.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>El restablecimiento de Windows Autopilot quita el usuario primario del dispositivo<!-- 4156123 -->
Al usarse el restablecimiento de Autopilot en un dispositivo, se quitará el usuario primario del dispositivo. El próximo usuario que inicie sesión tras el restablecimiento se establecerá como usuario primario. Esta característica se implantará para todos los clientes en los próximos días.

## <a name="week-of-july-8-2019"></a>Semana del 8 de julio de 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Nueva configuración de Office, Windows y OneDrive en las plantillas administrativas de Windows 10 <!-- 3510695 -->

Puede crear plantillas administrativas en Intune que imiten la administración de directivas de grupo locales (**Administración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y posterior** para la plataforma > **Plantilla administrativa** para el tipo de perfil).

En esta actualización se incluyen más opciones de configuración de Office, Windows y OneDrive que pueden agregar a sus plantillas. Con esta nueva configuración, ahora puede configurar más de 2500 opciones totalmente basadas en la nube.

Para obtener más información sobre esta característica, consulte [Usar plantillas de Windows 10 para configurar opciones de directiva de grupo en Intune](../configuration/administrative-templates-windows.md).

Se aplica a: Windows 10 y versiones posteriores

## <a name="week-of-july-1-2019"></a>Semana del 1 de julio de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>AAD y APP en los dispositivos Android Enterprise<!-- 3574267 -->
Ahora, al incorporar dispositivos Android Enterprise totalmente administrados, los usuarios se registrarán en Azure Active Directory (AAD) durante la configuración inicial de su nuevo dispositivo o el restablecimiento de fábrica del dispositivo. Anteriormente, en el caso de un dispositivo totalmente administrado, una vez completada la configuración, el usuario tenía que iniciar manualmente la aplicación de Microsoft Intune para iniciar el registro de AAD. Ahora, cuando el usuario tiene acceso a la página principal del dispositivo tras la configuración inicial, el dispositivo se inscribe y registra.

Además de las actualizaciones de AAD, las directivas de protección de aplicaciones (APP) de Intune se admiten ahora en dispositivos Android Enterprise totalmente administrados. Esta funcionalidad estará disponible a medida que la implementemos. Para obtener más información, consulte [Incorporación de aplicaciones de Google Play administrado a dispositivos Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Semana del 24 de junio de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>Configuración del explorador que se puede vincular a datos organizativos<!-- 3145939 -->
Ahora, las directivas de protección de aplicaciones (APP) de Intune en dispositivos iOS y Android permiten transferir vínculos web Org a un explorador determinado más allá de Intune Managed Browser o Microsoft Edge.  Consulte [¿Qué son las directivas de protección de aplicaciones?](../apps/app-protection-policy.md) para obtener más información sobre APP.

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>En la página Todas las aplicaciones se identifican las aplicaciones de Microsoft Store para Empresas en línea o sin conexión<!--4089647 -->
En la página **Todas las aplicaciones** ahora se incluye el etiquetado para identificar las aplicaciones de Microsoft Store para Empresas (MSFB) como aplicaciones en línea o sin conexión. Ahora, en cada aplicación MSFB se incluye un sufijo para **En línea** o **Sin conexión**. En la página de detalles de la aplicación también se incluye información sobre **Tipo de licencia** y **Supports device context installation** (Admite la instalación de contexto de dispositivo) (solo aplicaciones con licencia sin conexión).

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Aplicación del Portal de empresa en los dispositivos compartidos de Windows<!--4393553 -->
Ahora, los usuarios pueden tener acceso a la aplicación del Portal de empresa en los dispositivos compartidos de Windows. Los usuarios finales verán una etiqueta **Compartida** en el icono de dispositivo. Esto se aplica a la versión 10.3.45609.0 y posteriores de la aplicación del Portal de empresa de Windows.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>Ver todas las aplicaciones instaladas desde la página web del Portal de empresa<!-- 4224326 -->
La nueva página **Aplicaciones instaladas** del sitio web del Portal de empresa muestra todas las aplicaciones administradas (requeridas y disponibles) que están instaladas en los dispositivos de un usuario. Además del tipo de asignación, los usuarios pueden ver el editor de la aplicación, la fecha de publicación y el estado de instalación actual. Si todavía no hay ninguna aplicación requerida o disponible para los usuarios, estos verán un mensaje en el que se explica que no hay ninguna aplicación de la empresa instalada. Para ver la página nueva en la Web, vaya al [sitio web del Portal de empresa](https://portal.manage.microsoft.com) y haga clic en **Aplicaciones instaladas**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>La vista nueva permite que los usuarios de las aplicaciones vean todas las aplicaciones administradas instaladas en el dispositivo<!-- 2352913 -->  
La aplicación Portal de empresa para Windows ahora muestra todas las aplicaciones administradas (tanto las requeridas como las disponibles) que están instaladas en el dispositivo de un usuario. Los usuarios también pueden ver las instalaciones de aplicaciones intentadas y pendientes, además de sus estados actuales. Si todavía no hay ninguna aplicación requerida o disponible para los usuarios, estos verán un mensaje en el que se explica que no hay ninguna aplicación de la empresa instalada. Para ver la vista nueva, vaya al panel de navegación del Portal de empresa y seleccione **Aplicaciones** > **Aplicaciones instaladas**.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Configuración de las extensiones de kernel en dispositivos macOS<!-- 2043024 -->
En dispositivos macOS, puede crear un perfil de configuración de dispositivos (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > elija **macOS** como plataforma). Esta actualización incluye un nuevo grupo de opciones de configuración que permite configurar y usar las extensiones de kernel en los dispositivos. Puede agregar extensiones específicas o permitir todas las extensiones de un asociado o desarrollador específico.

Para obtener más información sobre esta característica, consulte los artículos sobre [información general de las extensiones de kernel](../configuration/kernel-extensions-overview-macos.md) y la [configuración de las extensiones de kernel](../configuration/kernel-extensions-settings-macos.md).

Se aplica a: macOS 10.13.2 y versiones posteriores

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>La opción Permitir solo aplicaciones de la Tienda para dispositivos Windows 10 incluye más opciones de configuración<!-- 2697002 -->
Al crear un perfil de restricciones de dispositivos para dispositivos Windows, se puede usar la opción **Permitir solo aplicaciones de la Tienda** de modo que los usuarios solo instalen aplicaciones de la Tienda Windows (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Restricciones de dispositivos** para tipo de perfil). En esta actualización, este valor se amplía para admitir más opciones.

Para ver la nueva configuración, vaya al artículo sobre la [configuración de dispositivos con Windows 10 y versiones posteriores para permitir o restringir características](../configuration/device-restrictions-windows-10.md#app-store).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>Implementación de varios perfiles de dispositivo de extensiones de movilidad de Zebra en un dispositivo, el mismo grupo de usuarios o el mismo grupo de dispositivos<!-- 4089955 -->
En Intune, puede usar extensiones de movilidad (MX) de Zebra en un perfil de configuración de dispositivo para personalizar la configuración de dispositivos Zebra que no se integran en Intune. Actualmente, puede implementar un perfil en un único dispositivo. En esta actualización, puede implementar varios perfiles en:
- Mismo grupo de usuarios
- Mismo grupo de dispositivos
- Dispositivo único

En [Usar y administrar dispositivos Zebra con extensiones de movilidad de Zebra en Microsoft Intune](../configuration/android-zebra-mx-overview.md) se muestra cómo usar MX en Intune.

Se aplica a: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>Algunas opciones de configuración de pantalla completa en dispositivos iOS se establecen mediante "Bloquear", en sustitución de "Permitir"<!-- 4404075  -->
Al crear un perfil de restricciones de dispositivos en dispositivos iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **Pantalla completa**), se establecen el **Bloqueo automático**, el **Cambio de timbre**, la **Rotación de pantalla**, el **Botón de suspensión de pantalla** y los **Botones de volumen**.

En esta actualización, los valores son **Bloquear** (bloquea la característica) o **Sin configurar** (permite la característica). Para ver la configuración, vaya a [Configuración de dispositivos iOS para permitir o restringir características ](../configuration/device-restrictions-ios.md#kiosk).

Se aplica a iOS.

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>Uso de Face ID para la autenticación de contraseña en dispositivos iOS<!-- 4490704 -->
Al crear un perfil de restricciones de dispositivos para dispositivos iOS, puede usar una huella digital para una contraseña. En esta actualización, la configuración de contraseña de huella digital también permite el reconocimiento facial (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma > **Restricciones de dispositivos** para el tipo de perfil > **Contraseña**). Como resultado, han cambiado las opciones de configuración siguientes:

- **Desbloqueo con huella digital** es ahora **Desbloqueo de Touch ID y Face ID**.
- **Modificación de huella digital (solo con supervisión)** es ahora **Modificación de Touch ID y Face ID (solo con supervisión)** .

Face ID está disponible en iOS 11.0 y versiones posteriores. Para ver la configuración, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md#password).

Se aplica a iOS.

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>La restricción de características de juegos y aplicaciones de la tienda en dispositivos iOS depende ahora de la región de clasificación<!-- 4593948 -->
En dispositivos iOS, puede permitir o restringir características relacionadas con los juegos, la tienda de aplicaciones y la visualización de documentos (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **App Store, presentación de documentos, juegos**). También puede elegir la región de clasificación, por ejemplo, Estados Unidos.

En esta actualización, la característica **Aplicaciones** pasa a ser un elemento secundario de **Región de clasificación** y a depender de **Región de clasificación**. Para ver la configuración, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Se aplica a iOS.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Compatibilidad de Windows Autopilot con Unión a Azure AD híbrido<!-- 4809146-->
Ahora, Windows Autopilot para los dispositivos existentes admite Unión a Azure AD híbrido (además de la compatibilidad con Unión a Azure AD existente). Se aplica a dispositivos con la versión 1809 de Windows 10 y posteriores. Para obtener más información, consulte [Windows Autopilot para dispositivos existentes](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

### <a name="device-management"></a>Administración de dispositivos

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Consulta del nivel de revisión de seguridad para dispositivos Android<!-- 4461911 -->
Ahora puede consultar el nivel de revisión de seguridad para dispositivos Android. Para ello, seleccione **Intune** > **Dispositivos** > **Todos los dispositivos** > seleccione un dispositivo > **Hardware**.
El nivel de revisión se muestra en la sección **Sistema operativo**.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Asignación de etiquetas de ámbito a todos los dispositivos administrados de un grupo de seguridad<!-- 3173810 -->
Ahora puede asignar etiquetas de ámbito a un grupo de seguridad y todos los dispositivos del grupo de seguridad también se asociarán a esas etiquetas de ámbito. La etiqueta de ámbito también se asigna a todos los dispositivos de estos grupos. Las etiquetas de ámbito establecidas con esta característica sobrescriben a las establecidas con el flujo de etiquetas de ámbito de dispositivo actual. Para obtener más información, consulte el artículo sobre el [uso de RBAC y las etiquetas de ámbito para TI distribuida](scope-tags.md).

### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="use-keyword-search-with-security-baselines------"></a>Uso de la búsqueda de palabras clave con Líneas de base de seguridad<!--  -->
Al crear o editar [perfiles de línea de base de seguridad](../protect/security-baselines.md#create-the-profile), puede especificar las palabras clave en la nueva barra de *búsqueda* para filtrar los grupos disponibles de opciones de configuración a aquellos que incluyen sus criterios de búsqueda.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>La característica Líneas de base de seguridad ya está disponible con carácter general<!-- 3785395 -->
La característica **Líneas de base de seguridad** está fuera de la versión preliminar y ya está disponible con carácter general (GA).  Esto significa que la característica está lista para usarse en producción. Sin embargo, las plantillas de línea de base individuales pueden permanecer en versión preliminar y se evalúan y publican con carácter general según su propia programación.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>La plantilla Línea de base de seguridad MDM ya está disponible con carácter general<!-- 3794072, 4217151,  3534649 -->
La plantilla Línea de base de seguridad MDM se ha sacado de la versión preliminar y ya está disponible con carácter general (GA). La plantilla con disponibilidad general se identifica como **Línea de base de seguridad MDM de mayo de 2019**.  Se trata de una nueva plantilla y no de una actualización de la versión preliminar.  Como nueva plantilla, deberá revisar la [configuración que contiene](../protect/security-baseline-settings-mdm.md) y, a continuación, crear nuevos perfiles para implementar la plantilla en su dispositivo. Otras plantillas de línea de base de seguridad pueden permanecer en versión preliminar. Para ver una lista de líneas de base disponibles, consulte [Líneas de base de seguridad disponibles](../protect/security-baselines.md#available-security-baselines).  

Además de ser una nueva plantilla, *Línea de base de seguridad MDM de mayo de 2019* incluye las dos opciones de configuración que hemos anunciado recientemente en nuestro artículo En desarrollo:  
- Above Lock (Por encima de la pantalla de bloqueo): la voz activa las aplicaciones de una pantalla bloqueada  
- DeviceGuard: use la seguridad basada en la virtualización (VBS) la próxima vez que reinicie los dispositivos.  

*Línea de base de seguridad MDM de mayo de 2019* también incluye la incorporación de varias opciones de configuración nuevas, la eliminación de otras y una revisión del valor predeterminado de una configuración. Para ver una lista detallada de los cambios realizados de la versión preliminar a la disponibilidad general, consulte los **cambios en la nueva plantilla**.

#### <a name="security-baseline-versioning---3194322---"></a>Control de versiones de líneas de base de seguridad<!-- 3194322 -->
Líneas de base de seguridad para el control de versiones del soporte técnico de Intune. Con este soporte técnico, a medida que se publican nuevas versiones de cada línea de base de seguridad, puede actualizar sus perfiles de línea de base de seguridad para usar la versión de línea de base más reciente sin tener que volver a crear e implementar una nueva línea de base desde cero. Además, en la consola de Intune puede ver información sobre cada una de las líneas de base, como, por ejemplo, el número de perfiles individuales que tiene y que usan la línea de base, cuántas de las diferentes versiones de línea de base usan sus perfiles y de qué fecha data la versión más reciente de una línea de base de seguridad específica.  Para obtener más información, consulte **Líneas de base de seguridad**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>Se ha movido la opción Utilice las claves de seguridad para el inicio de sesión<!-- 4501151 -->
La opción de configuración del dispositivo para la protección de identidad llamada **Utilice las claves de seguridad para el inicio de sesión** ya no se encuentra como configuración secundaria de *Configurar Windows Hello para empresas*. Ahora se trata de una opción de nivel superior que está siempre disponible, incluso si no habilita el uso de Windows Hello para empresas. Para obtener más información, consulte [Protección de identidad](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>Nuevos permisos para administradores de grupos asignados<!-- 4504437   -->
Ahora, el rol de administrador de la escuela integrado de Intune tiene permisos de creación, lectura, actualización y eliminación (CRUD) para Aplicaciones administradas. Esta actualización significa que si se le asigna como administrador de grupos en Intune for Education, ahora puede crear, ver, actualizar y eliminar el certificado push MDM de iOS, los tokens de servidor de MDM de iOS y los tokens de VPP de iOS, junto con [todos los permisos existentes que tenga](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Para tomar alguna de estas medidas, vaya a **Configuración de inquilinos** > **Administración de dispositivos iOS**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Las aplicaciones pueden usar Graph API para llamar a operaciones de lectura sin credenciales de usuario<!-- 4655885 -->
Las aplicaciones pueden llamar a operaciones de lectura de Graph API de Intune con la identidad de la aplicación y sin credenciales de usuario. Para obtener más información sobre cómo obtener acceso a Microsoft Graph API para Intune, consulte [Trabajar con Intune en Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Aplicación de etiquetas de ámbito a las aplicaciones de Microsoft Store para Empresas<!-- 4392555 -->
Ahora puede aplicar etiquetas de ámbito a las aplicaciones de Microsoft Store para Empresas. Para obtener más información sobre las etiquetas de ámbito, consulte [Uso del control de acceso basado en roles y de las etiquetas de ámbito para la TI distribuida](scope-tags.md).

## <a name="week-of-june-17-2019"></a>Semana del 17 de junio de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="new-features-in-microsoft-intune-app"></a>Características nuevas de la aplicación Microsoft Intune
Agregamos características nuevas a la aplicación Microsoft Intune (versión preliminar) para Android. Los usuarios de dispositivos Android totalmente administrados ahora pueden:  

* Ver y administrar los dispositivos inscritos mediante la aplicación Portal de empresa de Intune o Microsoft Intune.
* Ponerse en contacto con su organización para obtener soporte técnico.
* Enviar comentarios a Microsoft.
* Consultar los términos y condiciones, si la organización los estableció.

## <a name="week-of-june-10-2019"></a>Semana del 10 de junio de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>Aplicaciones de ejemplo nuevas que muestran la integración del SDK de Intune disponible en GitHub<!-- 2653471 -->
La cuenta de GitHub msintuneappsdk agregó aplicaciones de ejemplo nuevas para iOS (Swift), Android, Xamarin.iOS, Xamarin Forms y Xamarin.Android. Estas aplicaciones están pensadas para complementar la documentación existente y ofrecen demostraciones sobre cómo integrar el SDK de la aplicación Intune en sus propias aplicaciones móviles. Si es desarrollador de aplicaciones y necesita más orientación sobre el SDK de Intune, consulte estos ejemplos vinculados:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App): una aplicación de mensajería instantánea nativa de iOS (Swift) que usa la Biblioteca de autenticación de Azure Active Directory (ADAL) para la autenticación intermediada.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App): una aplicación de listas de tareas pendientes nativa de Android que usa ADAL para la autenticación intermediada.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps): una aplicación de listas de tareas pendientes de Xamarin.Android que usa ADAL para la autenticación intermediada. Este repositorio también tiene la aplicación Xamarin.Forms.
- [Aplicación de ejemplo de Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios): una aplicación de ejemplo esencial de Xamarin.iOS.

## <a name="week-of-may-27-2019"></a>Semana del 27 de mayo de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Informes de aplicaciones potencialmente peligrosas en dispositivos Android<!-- 4223162 -->
Intune ahora proporciona más datos sobre informes de aplicaciones potencialmente peligrosas en dispositivos Android. 

## <a name="week-of-may-20-2019"></a>Semana del 20 de mayo de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="windows-company-portal-app---3316993---"></a>Aplicación Portal de empresa de Windows<!-- 3316993 -->
La aplicación Portal de empresa de Windows ahora tiene una nueva página denominada **Dispositivos**. La página **Dispositivos** ahora mostrará a los usuarios finales los dispositivos inscritos. Los usuarios verán este cambio en Portal de empresa cuando usen la versión 10.3.4291.0 o una posterior. Para obtener información sobre cómo configurar Portal de empresa, vea [Configuración de la aplicación Portal de empresa de Microsoft Intune](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nombre del atributo OrderID del dispositivo de Autopilot cambiado a Etiqueta de grupo <!-- 4659453 -->

Para hacer que sea más intuitivo, el nombre del atributo **OrderID** en los dispositivos de Autopilot se ha cambiado a **Etiqueta de grupo**. Al usar archivos CSV para cargar información de dispositivos de Autopilot, debe usar Etiqueta de grupo como encabezado de columna, en lugar de OrderID.  

## <a name="week-of-may-13-2019"></a>Semana del 13 de mayo de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Método de autenticación de actualizaciones de directivas de Intune e instalación de aplicaciones de Portal de empresa<!-- 1927359  -->
En los dispositivos ya inscritos mediante el Asistente de configuración a través de uno de los métodos de inscripción de dispositivos corporativos de Apple, Intune ya no será compatible con el Portal de empresa cuando los usuarios finales de la tienda de aplicaciones lo instalen manualmente. Este cambio solo es pertinente cuando se realiza la autenticación con el Asistente de configuración de Apple durante la inscripción. Este cambio solo afecta a los dispositivos iOS inscritos a través de:  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Programa de inscripción de dispositivos (DEP) de Apple

Si los usuarios instalan la aplicación Portal de empresa desde la tienda de aplicaciones y luego intentan inscribir estos dispositivos a través de ella, recibirán un error. Se espera que estos dispositivos solo usen la aplicación Portal de empresa cuando Intune lo inserta, automáticamente, durante la inscripción. Se actualizarán los perfiles de inscripción de Intune en Azure Portal para que pueda especificar cómo los dispositivos se autentican y si reciben la aplicación Portal de empresa. Si quiere que los usuarios de dispositivos DEP tengan la aplicación Portal de empresa, deberá especificar sus preferencias en un perfil de inscripción. 

Además, se va a quitar la pantalla **Identificar el dispositivo** de la aplicación Portal de empresa de iOS. Por lo tanto, los administradores que quieren habilitar el acceso condicional o implementar aplicaciones de la empresa deben actualizar el perfil de inscripción de DEP. Este requisito solo se aplica si la inscripción de DEP se autentica con el Asistente para la configuración. En ese caso, debe insertar la aplicación Portal de empresa en el dispositivo. Para ello, elija **Intune** > **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > elija un token > **Perfiles** > elija un perfil > **Propiedades** > establezca **Instalar Portal de empresa** en **Sí**.

Para instalar la aplicación Portal de empresa en dispositivos DEP ya inscritos, deberá ir a Intune > Aplicaciones cliente e insertarla como una aplicación administrada con directivas de configuración de aplicación. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>Configurar cómo los usuarios finales actualizan una aplicación de línea de negocio (LOB) con una directiva de protección de aplicaciones<!-- 3568384 -->
Ahora puede configurar dónde los usuarios finales pueden obtener una versión actualizada de una aplicación de línea de negocio (LOB). Los usuarios finales verán esta característica en el cuadro de diálogo de inicio condicional **Versión mínima de la aplicación**, que le pedirá a los usuarios finales que actualicen a una versión mínima de la aplicación de LOB. Debe proporcionar estos detalles de actualización como parte de la directiva de protección de aplicaciones (APP) de LOB. Esta característica está disponible en iOS y en Android. En iOS, esta característica requiere que la aplicación esté integrada (o encapsulada con la herramienta de encapsulado) con el SDK de Intune para iOS v. 10.0.7 o superior. En Android, esta característica requeriría la versión más reciente de la aplicación Portal de empresa. Para configurar cómo un usuario final actualiza una aplicación de LOB, la aplicación necesita que se le envíe una directiva de configuración de aplicación administrada con la clave `com.microsoft.intune.myappstore`. El valor enviado definirá desde qué tienda descargará la aplicación el usuario final. Si la aplicación se implementa a través de Portal de empresa, el valor debe ser `CompanyPortal`. En el caso de cualquier otra tienda, debe escribir una dirección URL completa.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Scripts de PowerShell de extensión de administración de Intune<!-- 3734186  -->
Puede configurar los scripts de PowerShell para que se ejecuten con los privilegios de administración del usuario en el dispositivo. Para más información, consulte [Uso de scripts de PowerShell para dispositivos Windows 10 en Intune](../apps/intune-management-extension.md) y [Administración de aplicaciones Win32](../apps/app-management.md).

#### <a name="android-enterprise-app-management---4459905---"></a>Administración de aplicaciones de Android Enterprise<!-- 4459905 -->
Para facilitar a los administradores de TI la configuración y el uso de la administración de Android Enterprise, Intune agregará automáticamente cuatro aplicaciones comunes relacionadas con Android Enterprise a la consola de administración de Intune. Las cuatro aplicaciones de Android Enterprise son las siguientes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : se usa para escenarios totalmente administrados de Android Enterprise.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : ayuda a iniciar sesión en las cuentas si se usa la verificación de dos fases.
- **[Portal de empresa de Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : se usa para las directivas de protección de aplicación y escenarios de perfil de trabajo de Android Enterprise.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise): se usa para los escenarios de pantalla completa o dedicados de Android Enterprise.

Anteriormente, los administradores de TI tenían que buscar y aprobar manualmente estas aplicaciones en la [Tienda de Google Play administrada](https://play.google.com/store/apps) como parte de la configuración. Este cambio elimina los pasos que antes eran manuales para facilitar y agilizar el uso de la administración de Android Enterprise por parte de los clientes.

Los administradores verán que estas cuatro aplicaciones se agregan automáticamente a la lista de aplicaciones de Intune en el momento en que conecten por primera vez a su inquilino de Intune con Google Play administrado. Para más información, consulte [Conexión de una cuenta de Intune a una cuenta de Google Play administrado](../enrollment/connect-intune-android-enterprise.md). Para los inquilinos que ya han conectado a su inquilino o que ya utilizan Android Enterprise, no hay nada que los administradores tengan que hacer. Estas cuatro aplicaciones aparecerán automáticamente dentro de los siete días siguientes a la finalización de la implementación del servicio en mayo de 2019.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>Conector de certificados PFX actualizado para Microsoft Intune<!-- 1533038 -->
Hemos publicado una actualización del [Conector de certificado PFX para Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) que resuelve un problema por el que los certificados PFX existentes se siguen reprocesando, lo que provoca que el conector deje de procesar nuevas solicitudes.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Tareas de seguridad de Intune para ATP de Defender (en versión preliminar pública)<!-- 3208597 -->
En la versión preliminar pública, puede usar Intune para administrar las [tareas de seguridad para Protección contra amenazas avanzada (ATP) de Microsoft Defender](../protect/atp-manage-vulnerabilities.md). Esta integración con ATP agrega un enfoque basado en riesgos para detectar vulnerabilidades y errores de configuración de puntos de conexión, establecer su prioridad y corregirlos, a la vez que reduce el tiempo entre la detección y la mitigación.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>Buscar un conjunto de chips TPM en una directiva de cumplimiento de dispositivos Windows 10<!-- 3617671   idstaged-->
Muchos dispositivos Windows 10 y posteriores tienen conjuntos de chips del Módulo de plataforma segura (TPM). Esta actualización incluye una nueva configuración de cumplimiento que comprueba la versión del chip TPM en el dispositivo.

[La configuración de directivas de cumplimiento de Windows 10 y versiones posteriores](../protect/compliance-policy-create-windows.md#device-security) describe esta configuración.

Se aplica a: Windows 10 y versiones posteriores

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>Impedir que los usuarios finales modifiquen su punto de acceso personal y deshabilitar el registro del servidor Siri en dispositivos iOS<!-- 4097904   -->  
Crear un perfil de restricciones de dispositivo en el dispositivo iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma y **Restricciones de dispositivo** para el tipo de perfil). Esta actualización incluye nuevas opciones que puede configurar:

- **Aplicaciones integradas**: registro del servidor para los comandos de Siri
- **Inalámbrica**: modificación por el usuario del punto de acceso personal (solo con supervisión)

Para ver esta configuración, vaya a la [configuración de aplicaciones integradas para iOS](../configuration/device-restrictions-ios.md#built-in-apps) y [configuración inalámbrica para iOS](../configuration/device-restrictions-ios.md#wireless).

Se aplica a iOS 12.2 y versiones más recientes.

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>Nueva configuración de restricción de dispositivos de aplicaciones en el aula para dispositivos macOS<!-- 4097905   --> 
Puede crear un perfil de configuración de dispositivos para dispositivos MacOS (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **macOS** como plataforma >**Restricciones del dispositivo** para tipo de perfil). Esta actualización incluye una nueva configuración de aplicaciones en el aula, la opción para bloquear capturas de pantalla y la opción para deshabilitar la Fototeca de iCloud.

Para ver la configuración actual, vaya a [Configuración de dispositivos macOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-macos.md).

Se aplica a: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Se cambia el nombre de la configuración Contraseña para acceder a la tienda de aplicaciones de iOS<!-- 4557891  -->
El nombre de la configuración **Contraseña para acceder a la tienda de aplicaciones** se cambia a **Require iTunes Store password for all purchases** (Requerir contraseña de iTunes Store para todas las compras) (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma > **Restricciones de dispositivos** para el tipo de perfil > **Tienda de aplicaciones, presentación de documentos y juegos**).

Para ver la configuración disponible, vaya a [Tienda de aplicaciones, presentación de documentos, juegos de iOS](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Se aplica a iOS.

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Línea de base de Protección contra amenazas avanzada de Microsoft Defender (versión preliminar)<!--  3754134 -->
Agregamos una versión preliminar de línea de base de seguridad para la configuración [Protección contra amenazas avanzada de Microsoft Defender](../protect/security-baseline-settings-defender-atp.md). Esta línea de base está disponible cuando el entorno cumple con los requisitos previos para usar [Protección contra amenazas avanzada de Windows Defender](../protect/advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>La página Estado de inscripción (ESP) de Windows ya está disponible con carácter general<!-- 3605348 -->
La página Estado de inscripción dejó de estar en versión preliminar. Para más información, consulte [Configurar una página de estado de inscripción](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Actualización de la interfaz de usuario de Intune: creación de un perfil de inscripción de Autopilot<!-- 4593669 -->
La interfaz de usuario para crear un perfil de inscripción de Autopilot se actualizó para alinearla con los estilos de interfaz de usuario de Azure. Para obtener más información, consulte cómo [crear un perfil de inscripción de Autopilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). Más adelante, se actualizarán más escenarios de Intune a este nuevo estilo de interfaz de usuario.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>Habilitar Restablecimiento de Autopilot para todos los dispositivos Windows<!-- 4225665 -->
Restablecimiento de Autopilot ahora funciona para todos los dispositivos Windows, incluso para los que no están configurados para usar la página Estado de inscripción. Si no se configuró una página de estado de inscripción para el dispositivo durante la inscripción de dispositivo inicial, el dispositivo irá directamente al escritorio después de iniciar sesión. Puede tardar hasta ocho horas en sincronizar y aparecer como compatible en Intune. Para más información, consulte el artículo sobre cómo [restablecer dispositivos con Restablecimiento de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>No se requiere un formato IMEI exacto al buscar en todos los dispositivos<!--30407680 -->
No será necesario que incluya espacios en los números IMEI cuando busca en **Todos los dispositivos**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>Reflejo de la eliminación de un dispositivo del portal de Apple en el portal de Intune<!--2489996 -->
Si se elimina un dispositivo de los portales del Programa de inscripción de dispositivos de Apple o de Apple Business Manager, el dispositivo se eliminará automáticamente de Intune durante la siguiente sincronización.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>La página de estado de inscripción ahora realiza un seguimiento de las aplicaciones de Win32<!-- 2714451 -->
Esto solo se aplica a dispositivos que ejecutan Windows 10 versión 1903 y posteriores. Para más información, consulte [Configurar una página de estado de inscripción](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Administración de dispositivos

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Restablecimiento y borrado de dispositivos de forma masiva mediante Graph API<!-- 3295288 -->
Ahora podrá restablecer y borrar hasta 100 dispositivos de forma masiva mediante Graph API.

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>El informe de cifrado dejó de estar en versión preliminar pública<!-- 4587546      -->
El [informe sobre BitLocker y el cifrado de dispositivo](../protect/encryption-monitor.md) está disponible con carácter general y ya no forma parte de la versión preliminar pública.

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Configuración de biometría y firma de Outlook para dispositivos iOS y Android<!-- 4050557 -->
Ahora puede especificar si la firma predeterminada está habilitada en Outlook en dispositivos iOS y Android. Además, puede elegir permitir que los usuarios cambien la configuración de biometría en Outlook en iOS.

## <a name="week-of-may-6-2019"></a>Semana del 6 de mayo de 2019

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>Compatibilidad del control de acceso de red (NAC) con F5 Access para dispositivos iOS<!-- 4500808 -->

F5 ha publicado una actualización para BIG-IP 13 que permite la funcionalidad NAC para F5 Access para iOS en Intune. Para usar esta característica,:

- Actualice BIG-IP a 13.1.1.5. No se admite BIG-IP 14.
- Integre BIG-IP con Intune para NAC. Los pasos se describen en [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html) (Información general: Configuración de APM para comprobaciones de posición del dispositivo con sistemas de administración de puntos de conexión).
- Active la opción **Habilitar el control de acceso a la red (NAC)** del perfil de VPN en Intune.

Para ver las opciones disponibles, vaya a [Configuración de VPN en dispositivos iOS](../configuration/vpn-settings-ios.md).

Se aplica a iOS.

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>Conector de certificados PFX actualizado para Microsoft Intune<!-- doc-vso 1521237  -->  
Se ha publicado una actualización para el [Conector de certificados PFX para Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) que reduce el intervalo de sondeo de 5 minutos a 30 segundos.




## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
