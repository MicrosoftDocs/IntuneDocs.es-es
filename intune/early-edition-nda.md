---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0f6447f4a5cfb2638278a59414e83f744adb8c81
ms.sourcegitcommit: ed97b68f08c1a8469f0b45bc1c839a0b5f5c71e0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "45978270"
---
# <a name="the-early-edition-for-microsoft-intune---september-2018"></a>La edición anticipada de Microsoft Intune: septiembre de 2018

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

<!-- 1809 start -->

### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices-----1248496----"></a>Acceso a la cuenta de usuario de aplicaciones de Intune en dispositivos iOS y Android administrados <!-- ! 1248496  -->

Como administrador de Microsoft Intune, podrá controlar qué cuentas de usuario se agregan a las aplicaciones de Microsoft Office en dispositivos administrados. Podrá limitar el acceso solo a las cuentas de usuario de la organización permitidas y bloquear cuentas personales en los dispositivos inscritos. 

### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10----1333668---"></a>Creación de sufijos DNS en los perfiles de configuración de VPN en dispositivos que ejecutan Windows 10 <!-- 1333668 -->
Cuando se crea un perfil de configuración del dispositivo VPN (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **VPN** para tipo de perfil), se escriben algunos valores de DNS. También se pueden escribir varios **sufijos DNS** en Intune. Al usar los sufijos DNS, puede buscar un recurso de red mediante su nombre corto, en lugar del nombre de dominio completo (FQDN). Esta actualización también le permite cambiar el orden de los sufijos DNS en Intune.
[Configuración de VPN de Windows 10](vpn-settings-windows-10.md#dns-settings) muestra la configuración de DNS actual.
Se aplica a dispositivos Windows 10

### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Compatibilidad con VPN siempre activa para perfiles de trabajo empresarial de Android <!-- 1333705 -->
Podrá usar conexiones VPN siempre activas en dispositivos empresariales Android con perfiles de trabajo administrados. Las conexiones VPN siempre activas permanecen conectadas o se vuelven a conectar inmediatamente cuando el usuario desbloquea el dispositivo, cuando se reinicia el dispositivo o cuando cambia la red inalámbrica. También puede poner la conexión en modo “bloqueo”, que bloquea todo el tráfico de red hasta que la conexión VPN esté activa.
La configuración de VPN siempre activa estará en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android empresarial** para plataforma > **Restricciones de dispositivo** en **Solo perfiles de trabajo** para Tipo de perfil > configuración de **Conectividad**. 

### <a name="outlook-for-ios-and-android-app-configuration-policy---1828527---"></a>Directiva de configuración de aplicación de Outlook para iOS y Android <!--1828527 -->
Podrá crear una directiva de configuración de Outlook para iOS y Android. Se agregarán opciones de configuración adicionales a medida que se habiliten para Outlook para iOS y Android.

###  <a name="windows-line-of-business-lob-app-file-extensions----1884873---"></a>Extensiones de los archivos de aplicaciones de línea de negocio (LOB) de Windows <!-- 1884873 -->
Las extensiones de archivo de las aplicaciones de LOB de Windows incluirán las extensiones *.msi*, *.appx*, *.appxbundle*, *.msix* y *.msixbundle*. Podrá agregar una aplicación en Microsoft Intune seleccionando **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. Se mostrará el panel **Agregar aplicación** que le permitirá seleccionar el **Tipo de aplicación**. En el caso de las aplicaciones de LOB de Windows, seleccione la aplicación de **Línea de negocio** como el tipo de aplicación, elija el **Archivo de paquete de aplicación** y después especifique un archivo de instalación con la extensión adecuada.

### <a name="remotely-lock-noncompliant-devices----2064495---"></a>Bloquear dispositivos no compatibles de forma remota <!-- 2064495 -->
Cuando un dispositivo no cumple los requisitos, podrá crear una acción en la directiva de cumplimiento que bloquea el dispositivo de forma remota. En Intune > **Cumplimiento del dispositivo** cree una nueva directiva o seleccione una directiva existente. Seleccione **Acciones en caso de incumplimiento** > **Agregar** y elija bloquear de forma remota el dispositivo.
Compatible con: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 y versiones posteriores 

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Configuración de transferencia de datos de la aplicación de Intune en dispositivos iOS inscritos en MDM <!-- 2244713 -->
Podrá controlar por separado la configuración de transferencia de datos de la aplicación de Intune en dispositivos iOS inscritos en MDM y la especificación de la identidad del usuario inscrito. Los administradores que no usen el IntuneMAMUPN no observarán un cambio de comportamiento. Cuando esta función esté disponible, los administradores que usan el IntuneMAMUPN para controlar el comportamiento de la transferencia de datos en los dispositivos inscritos deben revisar la nueva configuración y actualizar la configuración de APP según sea necesario.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usar una clave precompartida en un perfil de Wi-Fi de Windows 10 <!-- 2662938 -->
Podrá usar una clave precompartida (PSK) con el protocolo de seguridad WPA o WPA2-Personal para autenticar un perfil de configuración de Wi-Fi para Windows 10.
Actualmente, debe importar un perfil de Wi-Fi o crear un perfil personalizado para usar una clave precompartida. [Configuración de Wi-Fi para Windows 10](wi-fi-settings-windows.md) muestra la configuración actual. 

### <a name="app-protection-policy-app-settings-for-web-data----2662995-eeready---"></a>Configuración de directiva de protección de la aplicación (APP) de datos web <!-- 2662995 eeready -->
La configuración de directiva APP de contenido web en dispositivos iOS y Android se actualizará para controlar mejor los vínculos web http y https, así como la transferencia de datos a través de vínculos universales de iOS y vínculos de aplicación de Android.  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>La frecuencia de sincronización de dispositivos Autopilot se aumenta a cada 12 horas <!-- 2753673 -->
Los dispositivos Autopilot se sincronizarán cada 12 horas en lugar de cada 24 horas.

### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Aplicar perfil de Autopilot para dispositivos Windows 10 inscritos que aún no están registrados para Autopilot <!-- 1558983 -->
Puede aplicar perfiles de Autopilot para dispositivos Windows 10 inscritos que aún no se han registrado para Autopilot. En el perfil de Autopilot, elija la opción **Convertir todos los dispositivos de destino a Autopilot** para registrar automáticamente los dispositivos que no se han registrado para Autopilot con los servicios de implementación de Autopilot. Permita un plazo de 48 horas para que se procese el registro. Cuando se anule la inscripción del dispositivo y este se restablezca, Autopilot lo aprovisionará. 

### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564--"></a>Crear y asignar varios perfiles de la página Estado de inscripción a grupos de Azure AD <!-- 2526564-->
Podrá crear y asignar varios perfiles de la página Estado de inscripción a grupos de usuarios de Azure AD.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Actualizaciones de la página de aterrizaje de Intune y cambio del nombre del nodo <!--2867309 -->
Las actualizaciones a la página de aterrizaje de Intune incluirán iconos de supervisión nuevos y modificados y gráficos para una mejor visualización de datos. El nodo **Aplicaciones móviles** cambiará a **Aplicaciones cliente**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Aumento de acceso de usuario final mediante la aplicación Portal de empresa <!-- 772203 -->
Los usuarios finales podrán acceder a las acciones de cuenta clave, como restablecer la contraseña y su perfil de Azure AD, desde la aplicación Portal de empresa.

### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emitir certificados SCEP para los dispositivos sin usuario <!-- 1744554 -->
Actualmente, los certificados se emiten a los usuarios. Podrá emitir certificados SCEP a los dispositivos, incluidos los dispositivos sin usuario como quioscos (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Certificado SCEP** para perfil). Otras actualizaciones incluyen:
- La propiedad **Asunto** en un perfil SCEP pasará a ser un cuadro de texto personalizado y puede incluir nuevas variables. 
- La propiedad **Nombre alternativo del firmante (SAN)** en un perfil SCEP ahora es un formato de tabla y puede incluir nuevas variables. En la tabla un administrador puede agregar un atributo y rellenar el valor en un cuadro de texto personalizado. La SAN será compatible con los siguientes atributos: 
  - DNS
  - Dirección de correo electrónico
  - UPN Estas nuevas variables se pueden agregar con texto estático en un cuadro de texto de valor personalizado. Por ejemplo, el atributo DNS puede agregarse como `DNS = {{AzureADDeviceId}}.domain.com`.
  > [!NOTE]
  > Las llaves, los puntos y coma y los símbolos de barra vertical “ { } ; | ” no funcionará en el texto estático de la SAN. Las llaves solo deben rodear una de las nuevas variables de certificado de dispositivo que debe aceptar `Subject` o `Subject alternative name`. Nuevas variables de certificado de dispositivo:  
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



<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP de Apple usado por otro MDM <!-- 1488946 -->
Intune detectará y mostrará los detalles si un token de programa de compras por volumen (VPP) de Apple lo está usando Intune y otro MDM.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>Se muestran el número de versión y el número de compilación de iOS <!-- 1892471 -->
En **Cumplimiento del dispositivo** > **Cumplimiento del dispositivo**, se muestra la versión del sistema operativo iOS. En una actualización futura, también se mostrará el número de compilación.
Cuando se publican las actualizaciones de seguridad, Apple normalmente deja el número de versión como está, pero actualiza el número de compilación. Al mostrar el número de compilación, puede comprobar fácilmente si se instala una actualización de vulnerabilidad.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos retirados en el panel de cumplimiento del dispositivos <!-- 1981119 -->
En una actualización futura, los dispositivos retirados se quitarán del panel de cumplimiento del dispositivo. Esto cambiará los números de cumplimiento.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Cambio en el proceso de actualización para conectores locales <!-- 2277554 -->
Según los comentarios de clientes, se cambiará la manera en que se realizan las actualizaciones en los conectores locales. Después de instalar inicialmente un conector local, las actualizaciones se producirán automáticamente. Este cambio se iniciará con el nuevo conector de certificado PFX para Microsoft Intune y posteriormente se implementará en otros tipos de conectores locales. 

### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224-eeready---"></a>Mejoras de perfil de quiosco multimedia de Windows 10 y versiones posteriores en Azure Portal <!-- 2748224 eeready -->
Se mejorará el perfil de configuración de dispositivo de quiosco multimedia de Windows 10 (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Versión preliminar de quiosco** para tipo de perfil): 
- Actualmente, puede crear varios perfiles de quiosco multimedia en el mismo dispositivo. Con esta actualización, Intune admitirá un solo perfil de quiosco multimedia por dispositivo. Si necesita varios perfiles de quiosco multimedia en un único dispositivo, puede usar un URI personalizado.
-En un perfil de **Quiosco con varias aplicaciones**, puede seleccionar el tamaño del icono de la aplicación y el orden del **Diseño del menú inicio** en la cuadrícula de la aplicación. Si prefiere una mayor personalización, puede cargar un archivo XML.
- La configuración del explorador de quiosco multimedia pasará a estar en la configuración de **Quiosco**. Actualmente, la configuración **Explorador web del quiosco** tiene su propia categoría en Azure Portal.
Se aplica a: Windows 10 y versiones posteriores

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Mejora de la experiencia en la aplicación Portal de empresa para usuarios administradores de inscripciones de dispositivos <!-- 675800 -->
Cuando un administrador de inscripciones de dispositivos (DEM) inicia sesión en la aplicación Portal de empresa para Windows, la aplicación solo mostrará el dispositivo actual en ejecución de DEM. Esta mejora reduce los tiempos de espera que se han producido anteriormente cuando la aplicación ha intentado cargar todos los dispositivos inscritos en DEM.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Comprobar cumplimiento de Configuration Manager <!-- 2192052 -->
Una actualización futura incluirá una nueva configuración de conformidad de System Center Configuration Manager (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10**). Configuration Manager envía señales a la conformidad de Intune. Mediante la configuración de Intune, puede exigir que todas las señales de Configuration Manager devuelvan “conforme”.

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En Configuration Manager, este requisito tiene el estado “Instalado”. Si algún programa del dispositivo se encuentra en estado desconocido, el dispositivo no será conforme en Intune.

Se aplica a Windows 10 y versiones posteriores

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas sobre tokens de VPP que expiran próximamente o licencias del Portal de empresa a punto de agotarse <!-- 2237572 -->
Si usa el Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante la inscripción de DEP, Intune le avisará cuando el token de VPP esté a punto de expirar y las licencias del Portal de empresa se estén agotando.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Configuración de seguridad adicional de Windows Installer <!-- 2282430 -->
Podrá dejar que los usuarios controlen las instalaciones de aplicaciones. Si lo permite, las instalaciones que antes se detendrían debido a una infracción de seguridad podrán seguir funcionando. Podrá indicar a Windows Installer que use permisos elevados cuando instale un programa en un sistema. Además, podrá habilitar elementos protegidos por WIP (Windows Information Protection) para indexarlos y almacenar los metadatos relativos a estos elementos en una ubicación sin cifrar. Cuando la directiva está deshabilitada, los elementos protegidos por WIP no se indexarán ni se mostrarán en los resultados de Cortana o del explorador de archivos. La funcionalidad de estas opciones estará deshabilitada de forma predeterminada. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Configuración de la directiva de protección de aplicaciones para el bloqueo de teclados de terceros en iOS <!-- 1248481 -->
En dispositivos iOS, los administradores de Intune podrán bloquear el uso de teclados de terceros al acceder a datos de la organización en aplicaciones protegidas mediante directiva. Cuando la directiva de protección de aplicación (APP) esté configurada para bloquear teclados de terceros, el usuario del dispositivo recibirá un mensaje la primera vez que interactúe con datos corporativos usando un teclado de terceros. Se bloquearán todas las demás opciones, que no afecten al teclado nativo, y los usuarios de los dispositivos no podrán verlas. Los usuarios de los dispositivos verán el mensaje del cuadro de diálogo una vez. 

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Paquetes de idioma de Office 365 Pro Plus <!-- 1833450 -->
Como administrador de Intune, podrá implementar idiomas adicionales para las aplicaciones Office 365 Pro Plus administradas mediante Intune. La lista de idiomas disponibles incluye el **Tipo** de paquete de idioma (núcleo, parcial y corrección). En el portal de Azure, seleccione **Microsoft Intune** > **Aplicaciones móviles** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación** de la hoja **Agregar aplicación**, seleccione **Windows 10** en **Conjunto de aplicaciones de Office 365**. Seleccione **Idiomas** en la hoja **Configuración del conjunto de aplicaciones**.

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>Requerir identificación que no sea biométrica después de tiempo de espera especificado <!-- 1506985 --> 

Al exigir un número de identificación personal no biométrico después de transcurrir un tiempo de espera especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más detallado sobre el acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones móviles** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos.

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Actualización de la experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android <!--1631531 -->

La experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android se actualizará de acuerdo con los procedimientos recomendados para las aplicaciones Android. En los próximos meses actualizaremos la aplicación Portal de empresa para Android para dividir el elemento de menú **Ayuda y comentarios** en los elementos de menú independientes **Ayuda** y **Enviar comentarios**. En la página **Ayuda** se incluirá una sección **Preguntas más frecuentes** y un botón **Soporte por correo electrónico** para permitir a los usuarios finales cargar registros a Microsoft y enviar al equipo de soporte técnico de la empresa un correo electrónico en el que se describa el problema. **Enviar comentarios** llevará al usuario a través de un proceso estándar de envío de comentarios de Microsoft, en el que se le pedirá elegir entre "Me gusta algo", "No me gusta algo" o "Tengo una idea".



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.



