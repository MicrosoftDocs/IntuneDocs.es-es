---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2f21df636ab429969429c6dbdf540daaa67a8f88
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576773"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>Edición anticipada para Microsoft Intune: noviembre de 2018

> [!Note]
> Notificación del acuerdo de confidencialidad: Los siguientes cambios están en fase de desarrollo para Intune. Esta información se comparte en el acuerdo de confidencialidad de forma muy limitada. No publique esta información en redes sociales ni sitios web públicos, como Twitter, UserVoice, Reddit, etc. 

La **edición anticipada** proporciona una lista de características, compartidas en el acuerdo de confidencialidad, que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No publique en un tweet, divulgue en UserVoice ni comparta de otra manera esta información fuera de su empresa. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Desinstalación de aplicaciones en dispositivos iOS supervisados corporativos <!-- 1281677 -->
Podrá eliminar cualquier aplicación en dispositivos iOS corporativos supervisados. Puede quitar cualquier aplicación estableciendo como destino grupos de usuarios o dispositivos con un tipo de asignación **Desinstalar**. Para dispositivos iOS personales o no supervisados, podrá quitar solo las aplicaciones que se instalaron mediante Intune.

### <a name="track-installation-of-office-proplus---2620217--"></a>Seguimiento de la instalación de Office ProPlus <!--2620217-->
Podrá realizar un seguimiento del progreso de instalación de [Office ProPlus](apps-add-office365.md) en la [página de estado de la inscripción](windows-enrollment-status.md).

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>Compatibilidad del programa de inscripción de dispositivos macOS para cuentas de Apple School Manager <!--3006133-->
Intune permitirá usar el programa de inscripción de dispositivos en dispositivos macOS para las cuentas de Apple School Manager.

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Detener temporalmente el modo quiosco en dispositivos Android para realizar cambios <!-- 3041935 -->
Al usar dispositivos Android en modo quiosco con varias aplicaciones, puede que un administrador de TI deba realizar cambios en el dispositivo. Un modo quiosco con varias aplicaciones que permitirá a un administrador de TI detener temporalmente el modo quiosco mediante un PIN, así como obtener acceso a todo el dispositivo.
Para ver la configuración actual de quiosco, consulte la [configuración de quiosco de Android](android-kiosk-settings.md).

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Establecer un fondo personalizado en la aplicación Managed Home Screen <!-- 3041945 -->
Se va a agregar una configuración que permitirá personalizar la apariencia del fondo de la aplicación Managed Home Screen en dispositivos Android Enterprise en modo quiosco con varias aplicaciones.  Para configurar el **fondo de dirección URL personalizado**, vaya a Intune en Azure Portal > Configuración del dispositivo. Seleccione un perfil de configuración del dispositivo actual o cree uno para editar su configuración de quiosco.

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Habilitar el botón de inicio virtual en dispositivos de quiosco de Android Enterprise  <!-- 3042021 -->
Una nueva configuración permitirá a los usuarios pulsar un botón de tecla programable en su dispositivo para cambiar entre la aplicación Managed Home Screen y otras aplicaciones asignadas en su dispositivo de quiosco con varias aplicaciones asignadas. Esta configuración es especialmente útil en escenarios donde una aplicación de quiosco del usuario no responde correctamente al botón "Atrás". Podrá configurar esta opción para dispositivos Android corporativos de un solo uso. Para habilitar o deshabilitar el **botón de inicio virtual**, vaya a Intune en Azure Portal > Configuración del dispositivo. Seleccione un perfil de configuración del dispositivo actual o cree uno para editar su configuración de quiosco.

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Guardar y aplicar asignaciones de la directiva de protección de la aplicación <!-- 3104570 -->
Podrá controlar mejor las asignaciones de la directiva de protección de la aplicación. Al guardar y aplicar las asignaciones de la directiva de protección de la aplicación, esta directiva solo afectará directamente a los usuarios previstos.

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nueva configuración del explorador Microsoft Edge en Windows 10 y versiones posteriores <!-- 3174639 -->
Se agregará una nueva opción para ayudar a controlar y administrar el explorador Microsoft Edge en los dispositivos. Para obtener una lista de las configuraciones actuales, vea la [restricción de dispositivos para Windows 10 y versiones posteriores](device-restrictions-windows-10.md#microsoft-edge-browser).

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Seleccionar las aplicaciones de las que se realiza un seguimiento en la página de estado de la inscripción <!-- 2531007 -->
Podrá elegir de qué aplicaciones se realizará un seguimiento en la página de estado de la inscripción.

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Actualización de la interfaz de usuario de las directivas de protección de aplicaciones de Intune <!-- 3251427 -->

Las directivas de protección de aplicaciones de Intune permiten configurar varias opciones de protección de datos para aplicaciones protegidas de Intune, como Microsoft Outlook y Word. Se van a cambiar las etiquetas de configuración y de los botones para facilitar la comprensión. Los controles **Sí**/**No** se cambiarán principalmente por los controles **Bloquear**/**Permitir** y **Deshabilitar**/**Habilitar**, mientras que las etiquetas también se actualizarán para mayor claridad. También se cambiará el formato de la configuración, de tal forma que la opción de configuración y su etiqueta estarán una al lado de la otra en el control, para facilitar la navegación. La configuración predeterminada y el número de opciones se conservarán, pero este cambio permitirá al usuario entender, navegar y utilizar la configuración con más facilidad para aplicar las directivas de protección de aplicaciones seleccionadas.



<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Uso de la configuración recomendada por Microsoft con líneas de base de seguridad <!-- 2055484 -->
Intune se integra con otros servicios centrados en la seguridad, incluidos ATP de Windows Defender y Office 365 ATP. Los clientes solicitan una estrategia común y un conjunto coherente de flujos de trabajo de seguridad integrales entre los servicios de Microsoft 365. Nuestro objetivo es alinear las estrategias para crear soluciones que actúen de puente entre las operaciones de seguridad y las tareas de administración comunes. En Intune, este objetivo se pretende lograr mediante la publicación de un conjunto de "Líneas de base de seguridad" recomendadas de Microsoft (**Intune** > **Líneas de base de seguridad**).  Un administrador podrá crear directivas de seguridad directamente a partir de estas líneas de base y, después, implementarlas en sus usuarios. También se pueden personalizar los procedimientos recomendados para satisfacer las necesidades de la organización. Intune garantiza que los dispositivos cumplan estas líneas de base y notifica a los administradores los usuarios o dispositivos que no están en cumplimiento.

### <a name="scope-tags-for-apps---1081941---"></a>Etiquetas de ámbito para las aplicaciones <!--1081941 -->
Podrá crear etiquetas de ámbito para limitar el acceso a los recursos de Intune. Agregue una etiqueta de ámbito a una asignación de roles y luego agregue dicha etiqueta a un perfil de configuración. El rol solo tendrá acceso a los recursos con perfiles de configuración que tengan etiquetas de ámbito coincidentes (o no tengan ninguna etiqueta de ámbito).
Para crear una etiqueta de ámbito, elija **Roles de Intune** > **Ámbito (etiquetas)** > **Crear**.
Para agregar una etiqueta de ámbito a una asignación de rol, elija **Roles de Intune** > **Todos los roles** > **Policy and profile manager (Administrador de directivas y perfiles)** > **Asignaciones** > **Ámbito (etiquetas)**.
Para agregar una etiqueta de ámbito a un perfil de configuración, elija **Configuración del dispositivo** > **Perfiles** > elija un perfil > **Propiedades** > **Ámbito (etiquetas)**.

### <a name="tenant-health-dashboard----1124854---"></a>Panel de estado del inquilino <!-- 1124854 -->
En la página Estado del inquilino de Intune se proporciona información de estado del inquilino en un solo lugar. La página se divide en cuatro secciones:  
- **Detalles del inquilino**: contiene información como la autoridad de MDM, el total de los dispositivos inscritos en el inquilino y el número de licencias. En esta sección también se proporciona la versión actual del servicio para el inquilino.
- **Estado del conector**: contiene información de los conectores configurados, como PCV de Apple, Microsoft Store para Empresas y los conectores de certificados. En función de su estado actual, los conectores se marcan como *Correcto*, *Advertencia* o *Incorrecto*.
- **Service Health para Intune**: contiene los incidentes activos o las interrupciones para el inquilino. La información de esta sección se recupera directamente del Centro de mensajes de Office ([https://portal.office.com](https://portal.office.com)).
- **Noticias de Intune**: contiene mensajes activos para el inquilino, que incluyen elementos como las notificaciones que el inquilino ha recibido sobre las características de Intune más recientes. La información de esta sección se recupera directamente del Centro de mensajes de Office ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Directivas de WIP implementadas sin la inscripción del usuario <!-- 1434452 -->
Las directivas de Windows Information Protection (WIP) se podrán implementar sin requerir que los usuarios de MDM inscriban sus dispositivos Windows 10. Esta configuración permite a las empresas proteger sus documentos corporativos en función de la configuración de WIP, mientras que permite a los usuarios mantener la administración de sus propios dispositivos Windows. Una vez que los documentos están protegidos con una directiva de WIP, un administrador de Intune puede borrar de forma selectiva los datos protegidos. Mediante la selección del usuario y dispositivo, y el envío de una solicitud de borrado, todos los datos protegidos mediante la directiva de WIP quedarán inservibles. En Intune en Azure Portal, seleccione **Aplicación móvil** > **Borrado selectivo de aplicaciones**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Configuración de directiva de protección de la aplicación (APP) de datos web <!-- 2662995 -->
La configuración de directiva APP de contenido web en dispositivos iOS y Android se actualizará para controlar mejor los vínculos web http y https, así como la transferencia de datos a través de vínculos universales de iOS y vínculos de aplicación de Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP de Apple usado por otro MDM <!-- 1488946 -->
Intune detectará y mostrará los detalles si un token de programa de compras por volumen (VPP) de Apple lo está usando Intune y otro MDM.

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-available-in-compliance-policies----1892471---"></a>Los números de versión y los números de compilación de iOS y macOS están disponibles en las directivas de cumplimiento <!-- 1892471 -->
En **Conformidad de dispositivos** > **Conformidad de dispositivos** se muestran las versiones de los sistemas operativos iOS y macOS, que se pueden usar en las directivas de cumplimiento. En una actualización futura también se podrá configurar el número de compilación en ambas plataformas.

Cuando se publican las actualizaciones de seguridad, Apple normalmente deja el número de versión como está, pero actualiza el número de compilación. Si usa el número de compilación en una directiva de cumplimiento, puede comprobar fácilmente si hay instalada una actualización de vulnerabilidad.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos retirados en el panel de cumplimiento del dispositivos <!-- 1981119 -->
En una actualización futura, los dispositivos retirados se quitarán del panel de cumplimiento del dispositivo. Esto cambiará los números de cumplimiento.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Cambio en el proceso de actualización para conectores locales <!-- 2277554 -->
Según los comentarios de clientes, se cambiará la manera en que se realizan las actualizaciones en los conectores locales. Después de instalar inicialmente un conector local, las actualizaciones se producirán automáticamente. Este cambio se iniciará con el nuevo conector de certificado PFX para Microsoft Intune y posteriormente se implementará en otros tipos de conectores locales. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Comprobar cumplimiento de Configuration Manager <!-- 2192052 -->
Una actualización futura incluirá una nueva configuración de conformidad de System Center Configuration Manager (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10**). Configuration Manager envía señales a la conformidad de Intune. Mediante la configuración de Intune, puede exigir que todas las señales de Configuration Manager devuelvan “conforme”.

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En Configuration Manager, este requisito tiene el estado “Instalado”. Si algún programa del dispositivo se encuentra en estado desconocido, el dispositivo no será conforme en Intune.

Se aplica a Windows 10 y versiones posteriores

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas sobre tokens de VPP que expiran próximamente o licencias del Portal de empresa a punto de agotarse <!-- 2237572 -->
Si usa el Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante la inscripción de DEP, Intune le avisará cuando el token de VPP esté a punto de expirar y las licencias del Portal de empresa se estén agotando.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.



