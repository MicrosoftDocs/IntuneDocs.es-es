---
title: Edición anticipada - Microsoft Intune
titlesuffix: ''
description: Edición anticipada de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19994745a232a362d6bba0f09ed3934e492a17ed
ms.sourcegitcommit: 2f431f122ce3ee6b5d0cdb04a0b748d00f83e295
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265679"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>La edición anticipada de Microsoft Intune: febrero de 2019

> [!Note]
> Notificación de acuerdo de confidencialidad: Los siguientes cambios están en fase de desarrollo de Intune. Esta información se comparte en el acuerdo de confidencialidad de forma muy limitada. No publique esta información en redes sociales ni sitios web públicos, como Twitter, UserVoice, Reddit, etc. 

La **edición anticipada** proporciona una lista de características, compartidas en el acuerdo de confidencialidad, que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No publique en un tweet, divulgue en UserVoice ni comparta de otra manera esta información fuera de su empresa. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>Los scripts de PowerShell se pueden ejecutar en un host de 64 bits en dispositivos de 64 bits <!-- 1862675  -->
Al agregar un script de PowerShell a un perfil de configuración de dispositivo, el script siempre se ejecuta en 32 bits, incluso en sistemas operativos de 64 bits. Con esta actualización, un administrador puede ejecutar el script en un host de PowerShell de 64 bits en dispositivos de 64 bits (**Configuración del dispositivo** > **Scripts de PowerShell** >  **Agregar** > **Configurar** > **Ejecutar script en el host de PowerShell de 64 bits**).
Para obtener más detalles sobre el uso de PowerShell, vea [Scripts de PowerShell en Intune](intune-management-extension.md).
Se aplica a: Windows 10 y versiones posteriores

### <a name="rename-an-enrolled-windows-device----1911112----"></a>Cambio del nombre de un dispositivo Windows inscrito <!-- 1911112  -->
Podrá cambiar el nombre de un dispositivo Windows 10 inscrito (RS4 o posterior). Para ello, seleccione **Intune** > **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Cambiar el nombre del dispositivo**.

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>Asignación de certificados SCEP en un dispositivo macOS sin usuarios    <!-- 2340521   -->
Podrá asignar certificados de Protocolo de inscripción de certificados simple (SCEP) a un dispositivo macOS sin usuarios y asociar el certificado con perfiles Wi-Fi o de VPN. Esto amplía la compatibilidad existente que ya tenemos para [asignar certificados a dispositivos sin usuarios que ejecutan Windows, iOS y Android](certificates-scep-configure.md#create-a-scep-certificate-profile).

### <a name="intune-conditional-access-ui-update------2432313----"></a>Actualización de la interfaz de usuario de acceso condicional de Intune   <!-- 2432313  -->
Estamos realizando mejoras en la interfaz de usuario para el acceso condicional en la consola de Intune. Entre ellos se incluyen los siguientes:
- Reemplazar la hoja *Acceso condicional* de Intune con la hoja de Azure Active Directory. Esto garantiza que tendrá acceso a toda la gama de opciones y configuraciones para el acceso condicional que sigue siendo una tecnología de Azure AD.
- Se reubica el programa de instalación *Conector de servicio de Exchange* a lo que actualmente es la hoja *Acceso local*. También se va a cambiar el nombre de esa hoja por *Acceso de Exchange*. Este cambio se consolidará donde podrá configurar y supervisar los detalles relacionados con Exchange en línea y local.

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Intune aprovechará las API de Google Play Protect en dispositivos Android <!-- 2577355  -->
Algunos administradores de TI se enfrentan a un panorama BYOD donde los usuarios finales pueden acabar por obtener privilegios de usuario root o realizar jailbreaking en sus teléfonos móviles. Este comportamiento, aunque en ocasiones no sea malintencionado, tiene como resultado la omisión de muchas directivas de Intune que se establecen con el fin de proteger los datos de la organización en los dispositivos de los usuarios finales. Por tanto, Intune proporciona la detección de jailbreak y de obtención de permisos de usuario root para los dispositivos inscritos y no inscritos. Con esta versión, ahora Intune aprovechará las API de Google Play Protect para agregarlas a nuestras comprobaciones de detección de modificaciones existentes para los dispositivos no inscritos. Aunque Google no comparte la totalidad de las comprobaciones de detección de modificaciones que se producen, esperamos que estas API detecten los usuarios que han modificado sus dispositivos por cualquier motivo, desde la personalización del dispositivo a la obtención de las actualizaciones más recientes del sistema operativo en dispositivos más antiguos. Después, se puede bloquear el acceso de estos usuarios a los datos corporativos, o bien se pueden eliminar sus cuentas de empresa desde sus aplicaciones habilitadas para la directiva. Para obtener valor adicional, ahora los administradores de TI tendrán varias actualizaciones de informes en la hoja Protección de aplicaciones de Intune: en el informe "Usuarios marcados" se mostrarán los usuarios que se han detectado mediante el examen de la API SafetyNet de Google Play Protect, y en el informe "Aplicaciones potencialmente peligrosas" se mostrarán las aplicaciones que se hayan detectado mediante el examen de la API Verify Apps de Google. Esta característica está disponible en Android. 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>Información de aplicaciones Win32 disponible en la hoja Solucionar problemas <!-- 2617342    -->
Podrá recopilar archivos de registro de error de la instalación de una aplicación Win32 desde la aplicación hoja **Solucionar problemas** de Intune. Para obtener más información sobre la solución de problemas de instalación de aplicaciones, vea [Troubleshoot app installation issue](troubleshoot-app-install.md) (Solución de problemas de instalación de aplicaciones).

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>Las aplicaciones Kiosk Browser y Explorador Microsoft Edge se pueden ejecutar en dispositivos Windows 10 en modo de pantalla completa <!-- 2935135  -->
Puede usar los dispositivos Windows 10 en modo de pantalla completa para ejecutar una o varias aplicaciones. En esta actualización se incluyen varios cambios en el uso de las aplicaciones de explorador en modo de pantalla completa, incluidos los siguientes:

- Se agrega el explorador Microsoft Edge o Kiosk Browser para que se ejecuten como aplicaciones en el dispositivo de pantalla completa (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil**  >  **Windows 10 y versiones posteriores** para plataforma > **Pantalla completa** para el tipo de perfil).
- Se restringe Microsoft Edge para que se pueda (o no) ejecutar a pantalla completa (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil**  >  **Windows 10 y versiones posteriores** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **Explorador Microsoft Edge**). Cuando no se ejecuta en modo de pantalla completa, los usuarios finales pueden cambiar la configuración de Microsoft Edge.

Para obtener una lista de las configuraciones actuales, vea lo siguiente:

- [Configuración de dispositivos con Windows 10 y versiones posteriores para ejecutarse como una pantalla completa](kiosk-settings-windows.md)
- [Restricciones de dispositivos del explorador Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)

Se aplica a: Windows 10 y versiones posteriores

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Asignación automática de etiquetas de ámbito a los recursos creados por un administrador con ese ámbito <!-- 3173823  -->
Cuando un administrador crea un recurso, las etiquetas de ámbito asignadas al administrador se asignarán de forma automática a esos recursos nuevos.

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>Nueva configuración de restricción de dispositivos para dispositivos iOS y macOS <!-- 3448774 -->
Puede restringir algunas opciones y características de los dispositivos que ejecutan iOS y macOS (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil**  >  **iOS** o **macOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil). En esta actualización se agregan más características y configuraciones que puede controlar, incluida la configuración del tiempo de pantalla, el cambio de la configuración eSIM y planes de telefonía móvil, el retraso de la visibilidad del usuario de las actualizaciones de software, el bloqueo del almacenamiento de contenido en caché y muchas más.
Para ver la configuración y las características actuales que se pueden restringir, vea lo siguiente:
- [Configuración de restricciones de dispositivos iOS](device-restrictions-ios.md)
- [Configuración de restricciones de dispositivos macOS](device-restrictions-macos.md)

Se aplica a:
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>El informe Errores de inscripción se mueve a la hoja Inscripción de dispositivos <!-- 3560202 -->
El informe **Errores de inscripción** se moverá a la sección **Supervisar** de la hoja **Inscripción de dispositivos**. También se agregan dos columnas nuevas (Método de inscripción y Versión del sistema operativo).

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>Se cambia "Pantalla completa" por "Dispositivos dedicados" <!-- 3598402  -->
Para alinear con la terminología de Android, **Pantalla completa** se cambiará por **Dispositivos dedicados** en Perfiles de configuración de dispositivos, **Android Enterprise** >  **Propietario del dispositivo** > **Restricciones de dispositivos**.

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>Las opciones de Safari y Retrasar la visibilidad de las actualizaciones de software de iOS se van a cambiar a la interfaz de usuario de Intune <!-- 3640850, , 3803313  -->
Para los dispositivos iOS, puede establecer la configuración de Safari y configurar actualizaciones de software. En esta actualización, estas opciones se van a cambiar a otra partes de la interfaz de usuario de Intune:

- La configuración de Safari se va cambiar de **Safari** (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil**  >  **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil) a **Aplicaciones integradas**. 
- La opción **Delaying user software update visibility for supervised iOS devices** (Retrasar la visibilidad de las actualizaciones de software para los dispositivos iOS supervisados) (**Actualizaciones de software** > **Directivas de actualización para iOS**) se va a cambiar a **Restricciones de dispositivos** > **General**.

Para obtener una lista de las configuraciones actuales, vea [Restricciones de dispositivos iOS](device-restrictions-ios.md) y [Actualizaciones de software de iOS](software-updates-ios.md).

Se aplica a: 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>En los dispositivos iOS se ha cambiado el nombre de Habilitar restricciones en la configuración del dispositivo por Tiempo de uso <!-- 3699164  -->
Puede configurar **Habilitar restricciones en la configuración del dispositivo**  en dispositivos iOS supervisados (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **General**). En esta actualización, se ha cambiado el nombre de esta opción por **Tiempo de uso (solo con supervisión)**. El comportamiento es el mismo. De manera específica: 

- iOS 11.4.1 y versiones anteriores: **Bloquear** impide que los usuarios finales establezcan sus propias restricciones en la configuración del dispositivo. 
- iOS 12.0 y versiones posteriores: **Bloquear** impide que los usuarios finales establezcan su propio **Tiempo de uso** en la configuración del dispositivo, incluidas las restricciones de contenido y privacidad. En los dispositivos actualizados a iOS 12.0 ya no aparecerá la pestaña Restricciones en la configuración del dispositivo. Estas opciones se encuentran en **Tiempo de uso**. 

Para obtener una lista de las configuraciones actuales, vea [Restricciones de dispositivos iOS](device-restrictions-ios.md).

Se aplica a: 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>Detalles de estado de la aplicación para aplicaciones iOS <!-- 3761235  -->
Habrá nuevos mensajes de error de instalación de aplicaciones relacionados con lo siguiente:
- Error de las aplicaciones VPP cuando se instalan en un iPad compartido
- Error cuando la tienda de aplicaciones está deshabilitada
- No se puede encontrar la licencia VPP de la aplicación
- No se pueden instalar las aplicaciones del sistema con el proveedor de MDM
- No se pueden instalar aplicaciones cuando el dispositivo está en modo de pantalla completa o modo perdido
- No se puede instalar la aplicación cuando el usuario no ha iniciado sesión en la App Store

En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > "Nombre de la aplicación" > **Estado de instalación del dispositivo**. Los mensajes de error nuevos estarán disponibles en el estado **Detalles del estado**.

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Implementación de aplicaciones de Microsoft Store para Empresas con licencias en línea <!-- 1672660  -->
Podrá asignar las aplicaciones de Microsoft Store para Empresas con licencias en línea necesarias en el contexto del dispositivo. Implementar una aplicación de Microsoft Store para Empresas de esta forma permitirá que la aplicación se instale para todos los usuarios en el dispositivo. Esto solo es aplicable para dispositivos de escritorio de Windows 10 RS4+. La opción para instalar en el contexto del dispositivo está disponible en la página de asignación de aplicaciones del cliente para las aplicaciones con licencia en línea de MSFB.

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Implementación de aplicaciones APP-WE de Android Enterprise <!-- 1171203 -->
Para los dispositivos Android en un escenario de implementación de directiva de protección de aplicaciones sin inscripción (APP-WE) no inscrito, podrá usar Google Play administrado para implementar aplicaciones de la tienda y aplicaciones LOB en los usuarios. En concreto, el departamento de TI puede brindar a los usuarios finales un catálogo de aplicaciones y experiencia de instalación que ya no requiere que los usuarios finales flexibilicen la posición de seguridad de sus dispositivos al permitir instalaciones de orígenes desconocidos. Además, este escenario de implementación proporcionará una mejor experiencia del usuario final.

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Método de autenticación de actualizaciones de directivas de Intune e instalación de aplicaciones de Portal de empresa <!-- 1927359 -->
En los dispositivos ya inscritos mediante el Asistente de configuración a través de uno de los métodos de inscripción de dispositivos corporativos de Apple, Intune ya no será compatible con el Portal de empresa cuando los usuarios finales de la tienda de aplicaciones lo instalen manualmente. Este cambio solo es pertinente cuando se realiza la autenticación con el Asistente de configuración de Apple durante la inscripción. Este cambio solo afecta a los dispositivos iOS inscritos a través de:  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Programa de inscripción de dispositivos (DEP) de Apple

Si los usuarios instalan la aplicación Portal de empresa desde la tienda de aplicaciones y luego intentan inscribir estos dispositivos a través de ella, recibirán un error. Se espera que estos dispositivos solo usen Portal de empresa cuando Intune lo inserta, automáticamente, durante la inscripción. Se actualizarán los perfiles de inscripción de Intune en Azure Portal para que pueda especificar cómo los dispositivos se autentican y si reciben la aplicación Portal de empresa. Si quiere que los usuarios de dispositivos DEP tengan la aplicación Portal de empresa, deberá especificar sus preferencias en un perfil de inscripción. Además, pronto quedará obsoleta la pantalla **Identificar el dispositivo** de la aplicación Portal de empresa.  
Para instalar Portal de empresa en dispositivos DEP ya inscritos, deberá ir a Intune > Aplicaciones cliente e insertarla como aplicación administrada con las directivas de configuración de aplicaciones. En futuros documentos habrá disponible más información sobre cómo llevar a cabo estos pasos.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Las plantillas administrativas están en versión preliminar pública y se movieron a su propio perfil de configuración <!-- 3322847 -->
Las plantillas administrativas de Intune (**Configuración del dispositivo** > **Plantillas administrativas**) están actualmente en versión preliminar privada. Con esta actualización: las plantillas administrativas incluyen cerca de 300 valores de configuración que se pueden administrar en Intune. Anteriormente, estas configuraciones solo existían en el editor de directivas de grupo.
Las plantillas administrativas están disponibles en versión preliminar pública y se mueven desde **Configuración del dispositivo** > **Plantillas administrativas** a **Configuración del dispositivo** > **Perfiles** >**Crear perfil** > en **Plataforma**, elija **Windows 10 y versiones posteriores**, en **Tipo de perfil**, elija **Plantillas administrativas**.
Se habilita el informe; se aplica a: Windows 10 y versiones posteriores

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Modo oscuro del Portal de empresa de macOS para Intune <!-- 3300524 -->
El Portal de empresa de macOS para Intune ahora admite el Modo oscuro para macOS. Cuando habilita el Modo oscuro en un dispositivo macOS 10.14 o una versión posterior, el Portal de empresa ajustará su apariencia para que los colores reflejen ese modo.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Configuración de directiva de protección de la aplicación (APP) de datos web <!-- 2662995 -->
La configuración de directiva APP de contenido web en dispositivos iOS y Android se actualizará para controlar mejor los vínculos web http y https, así como la transferencia de datos a través de vínculos universales de iOS y vínculos de aplicación de Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP de Apple usado por otro MDM <!-- 1488946 -->
Intune detectará y mostrará los detalles si un token de programa de compras por volumen (VPP) de Apple lo está usando Intune y otro MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos retirados en el panel de cumplimiento del dispositivos <!-- 1981119 -->
En una actualización futura, los dispositivos retirados se quitarán del panel de cumplimiento del dispositivo. Esto cambiará los números de cumplimiento.

## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
