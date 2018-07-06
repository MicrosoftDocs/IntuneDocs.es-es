---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0500194f5afaba11f37b84bbdf606e6167632a71
ms.sourcegitcommit: afa2e84d5cadf5542ecabc26e61dc71919992a22
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37340189"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Edición anticipada de Microsoft Intune: julio de 2018

> [!Note]
> Notificación del acuerdo de confidencialidad: Los siguientes cambios están en fase de desarrollo de Intune. Esta información se comparte en el acuerdo de confidencialidad de forma muy limitada. No publique esta información en redes sociales ni sitios web públicos, como Twitter, UserVoice, Reddit, etc. 

La **edición anticipada** proporciona una lista de características, compartidas en el acuerdo de confidencialidad, que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No publique en un tweet, divulgue en UserVoice ni comparta de otra manera esta información fuera de su empresa. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

<!-- 1807 start -->

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Códigos de acceso para restablecer el dispositivo desde la aplicación Portal de empresa para Windows 10 <!-- 2101282 --> 
Los empleados pronto podrán restablecer el PIN o el código de acceso de su dispositivo directamente desde la aplicación Portal de empresa para Windows 10. Esta funcionalidad estará disponible en los dispositivos remotos y locales administrados por Intune que admiten el restablecimiento de la contraseña. Según el tipo de dispositivo, una solicitud realizada para un dispositivo remoto eliminará el código de acceso actual del dispositivo o creará una contraseña temporal. Si un usuario solicita el restablecimiento para un dispositivo local, se le redirigirá a la aplicación de configuración del dispositivo.

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Uso de S/MIME para cifrar y firmar varios dispositivos de un usuario <!-- 1333642 -->
Una actualización futura incluirá un cifrado de correo electrónico S/MIME mediante un nuevo perfil de certificado importado (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > seleccione la plataforma > **Certificado PKCS importado** tipo de perfil). En Intune, puede importar los certificados en formato PFX. Después, Intune puede entregar esos mismos certificados a varios dispositivos inscritos por un solo usuario. Esto también incluye lo siguiente:

- El perfil de correo electrónico de iOS nativo permite habilitar el cifrado S/MIME mediante certificados importados en formato PFX.
- La aplicación de correo nativo de los dispositivos Windows Phone 10 usa automáticamente el certificado S/MIME.
- Los certificados privados se pueden entregar en varias plataformas. Aun así, no todas las aplicaciones de correo electrónico son compatibles con S/MIME.
- En otras plataformas, podría tener que configurar manualmente la aplicación de correo electrónico para habilitar S/MIME.  
- Las aplicaciones de correo electrónico que admiten el cifrado S/MIME pueden controlar la recuperación de certificados para el cifrado de correo electrónico S/MIME de una manera que no es compatible con un servicio MDM, por ejemplo, si los lee desde el almacén de certificados del publicador.

Compatible con: Windows, Windows Phone 10, macOS, iOS y Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Use licencias de dispositivo de VPP para tener en servicio el Portal de empresa durante la inscripción de DEP <!-- 1608345 -->
Podrá usar licencias de dispositivo del Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante las inscripciones en el Programa de inscripción de dispositivos (DEP). Para ello, al crear o editar un perfil de inscripción, especifique el token de VPP que quiera usar para instalar el Portal de empresa. Asegúrese de que el token no expire y que dispone de suficientes licencias para la aplicación de Portal de empresa. En los casos en los que el token expire o se agoten las licencias, Intune instalará el Portal de empresa del App Store (se solicitará un identificador de Apple).

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eliminación en masa de dispositivos en la hoja de dispositivos <!-- 1793693 -->
Puede eliminar varios dispositivos a la vez en la hoja de dispositivos. Elija **Dispositivos** > **Todos los dispositivos** > seleccione los dispositivos que quiere eliminar > **Eliminar**. En el caso de los dispositivos que no se puedan eliminar, se mostrará una alerta.

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nuevo perfil de configuración de dispositivos Wi-Fi para Windows 10 y versiones posteriores <!-- 1879077 -->
Actualmente, puede importar y exportar perfiles de Wi-Fi mediante archivos XML. Puede crear un perfil de configuración de dispositivo Wi-Fi directamente en Intune, igual que en otras plataformas.

Para crear el perfil, abra **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** > **Wi-Fi**. 

Se aplica a Windows 10 y versiones posteriores.

###  <a name="windows-line-of-business-lob-apps-file-extension-rename----1884873---"></a>Cambio de nombre de la extensión de los archivos de aplicaciones de línea de negocio (LOB) de Windows <!-- 1884873 -->
El nombre de las extensiones de archivo para las aplicaciones de LOB de Windows cambiará de *.appx* y *.appxbundle* a *.msix* y *.msixbundle*. Puede agregar una aplicación en Microsoft Intune seleccionando **Aplicaciones móviles** > **Aplicaciones** > **Agregar**. Se mostrará el panel **Agregar aplicación**, que permite seleccionar el **tipo de aplicación**. En el caso de las aplicaciones de LOB de Windows, seleccione la aplicación de **línea de negocio** como el tipo de aplicación, elija el **archivo de paquete de aplicación** y, después, especifique un archivo de instalación con la extensión adecuada.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Paquete de configuración de ATP de Windows Defender agregado automáticamente al perfil de configuración <!-- 2144658 -->
Cuando se usa la [Protección contra amenazas avanzada y la incorporación](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) de dispositivos en Intune, se descarga un paquete de configuración y se agrega al perfil de configuración. En una actualización futura, Intune obtendrá automáticamente el paquete del Centro de seguridad avanzada de Windows Defender y lo agregará al perfil.

Se aplica a Windows 10 y versiones posteriores.

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>La característica Quiosco (obsoleto) aparece atenuada y no se puede cambiar <!-- 2149998 -->
La [característica Quiosco](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 and later (Windows 10 y versiones posteriores)** > **Restricciones de dispositivos**) estará obsoleta y se sustituirá por la [configuración de Quiosco para Windows 10 y versiones posteriores](kiosk-settings.md). La característica **Quiosco (obsoleto)** estará atenuada y la interfaz de usuario no se podrá modificar ni actualizar. 

Para habilitar el modo quiosco, vea [Configuración de quiosco para Windows 10 (y versiones posteriores)](kiosk-settings.md).

Se aplica a Windows 10 y versiones posteriores, Windows Holographic for Business

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API para usar entidades de certificación de terceros <!-- 2184013 -->
Habrá una API de Java que permitirá que las entidades de certificación de terceros se integren con Intune y SCEP. Después, los usuarios pueden agregar el certificado SCEP a un perfil y aplicarlo a los dispositivos mediante MDM.

Actualmente, Intune admite [solicitudes SCEP mediante Servicios de certificados de Active Directory](certificates-scep-configure.md).

### <a name="check-for-sccm-compliance----2192052---"></a>Comprobación de la conformidad de SCCM <!-- 2192052 -->
Una actualización futura incluirá una nueva configuración de conformidad de System Center Configuration Manager (SCCM) (**Conformidad de dispositivos** > **Directivas** > **Crear directiva**  > **Windows 10**). SCCM envía señales a la conformidad de Intune. Mediante la configuración de Intune, puede exigir que todas las señales de SCCM devuelvan "conforme".

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En SCCM, este requisito tiene el estado "Instalado". Si algún programa del dispositivo se encuentra en estado desconocido, el dispositivo no será conforme en Intune.

Se aplica a Windows 10 y versiones posteriores

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas sobre tokens de VPP que expiran próximamente o licencias del Portal de empresa a punto de agotarse <!-- 2237572 -->
Si usa el Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante la inscripción de DEP, Intune le avisará cuando el token de VPP esté a punto de expirar y las licencias del Portal de empresa se estén agotando.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmación requerida para eliminar el token de VPP que se usa para tener en servicio el Portal de empresa <!-- 2237634 -->
Se solicitará confirmación para eliminar un token del Programa de Compras por Volumen (VPP) si se usa para tener en servicio el Portal de empresa durante la inscripción de DEP.

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Marcado automático de dispositivos Android inscritos mediante Samsung Knox Mobile Enrollment como "corporativos" <!-- 2404851 -->
De forma predeterminada, los dispositivos Android inscritos mediante Samsung Knox Mobile Enrollment se marcarán como **corporativos** en **Propiedad del dispositivo**. No tendrá que identificar manualmente los dispositivos corporativos mediante IMEI o números de serie antes de realizar la inscripción mediante Knox Mobile Enrollment.

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Alternar para mostrar u ocultar el botón Finalizar sesión en un explorador de Quiosco <!-- 2455253 -->
Puede configurar si los exploradores de Quiosco muestran o no el botón Finalizar sesión. Puede ver el control en **Configuración del dispositivo** > **Quiosco (versión preliminar)** > **Kiosk Web Browser**. Si está activado, cuando un usuario hace clic en el botón, la aplicación solicita confirmación para finalizar la sesión. Cuando se confirma, el explorador borra todos los datos de exploración y vuelve a la dirección URL predeterminada.

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Creación de un perfil de configuración de red de telefonía móvil eSIM <!-- 2564077 -->
En **Configuración del dispositivo**, puede crear un perfil de red de telefonía móvil eSIM. Puede importar un archivo que contenga códigos de activación de red de telefonía móvil proporcionados por el operador de telefonía móvil. Después, puede implementar estos perfiles en sus dispositivos Windows 10 habilitados para eSIM LTE, como Surface Pro LTE y otros dispositivos compatibles con eSIM.

Compruebe si sus [dispositivos admiten perfiles de eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Se aplica a Windows 10 y versiones posteriores. 




<!-- 1806 start -->

### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Ver perfiles de configuración de dispositivos en conflicto <!-- 1556983 -->
En **Configuración del dispositivo**, se muestra una lista de los perfiles existentes. Con esta actualización, se agrega una nueva columna que proporciona información detallada sobre los perfiles que tienen un conflicto. Puede seleccionar una fila en conflicto para ver la configuración y el perfil que tiene el conflicto. 

Más información en [Perfiles de configuración de dispositivos](device-profiles.md).

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>Compatibilidad con dispositivos Android de un solo uso y propiedad de la empresa <!-- 1630973 -->

Intune admitirá dispositivos Android de estilo quiosco, que estén bloqueados y con una elevada administración. De este modo, los administradores pueden bloquear aún más el uso de un dispositivo para restringir su uso a una sola aplicación o un pequeño conjunto de aplicaciones, impidiendo así que los usuarios habiliten otras aplicaciones o realicen otras acciones en el dispositivo.

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Compatibilidad de macOS para el Programa de inscripción de dispositivos de Apple <!-- 747651 -->

Intune admitirá la inscripción de dispositivos macOS el Programa de inscripción de dispositivos de Apple (DEP). Para ello:

1. En deploy.apple.com, asigne números de serie de macOS a un servidor MDM.
2. Importe los números de serie en Intune.
3. Cree un perfil de programa de inscripción específico para dispositivos Mac OS.

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Cambio de nombre en Google para Android for Work y Play for Work <!--842873 -->
Intune actualizará el término "Android for Work" para reflejar los cambios de personalización de marca de Google.  Ya no se usarán los términos "Android for Work" y "Play for Work". Se usará terminología diferente en función del contexto:

- "Android Enterprise" hace referencia a la pila de administración general de Android moderna.
- "Perfil de trabajo" o "Propietario de perfil" hacen referencia a dispositivos BYOD administrados con perfiles de trabajo.
- "Google Play administrada" hace referencia a la tienda de aplicaciones de Google.

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>Supervisar el estado de configuración de aplicaciones iOS por dispositivo <!-- 880037 eeready eestaged -->

Como administrador de Microsoft Intune, podrá supervisar el estado de configuración de aplicaciones iOS para cada dispositivo administrado. Desde **Microsoft Intune** en Azure Portal, seleccione **Dispositivos** > **Todos los dispositivos**. En la lista de dispositivos administrados, seleccione un dispositivo específico para mostrar una hoja para el dispositivo. En la hoja del dispositivo, seleccione **Configuración de aplicaciones**.  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Configuración de la directiva de protección de aplicaciones para el bloqueo de teclados de terceros en iOS <!-- 1248481 -->
En dispositivos iOS, los administradores de Intune podrán bloquear el uso de teclados de terceros al acceder a datos de la organización en aplicaciones protegidas mediante directiva. Cuando la directiva de protección de aplicación (APP) esté configurada para bloquear teclados de terceros, el usuario del dispositivo recibirá un mensaje la primera vez que interactúe con datos corporativos usando un teclado de terceros. Se bloquearán todas las demás opciones, que no afecten al teclado nativo, y los usuarios de los dispositivos no podrán verlas. Los usuarios de los dispositivos verán el mensaje del cuadro de diálogo una vez. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Crear directiva de cumplimiento de dispositivos usando la configuración de firewall en dispositivos macOS <!-- 1497640 -->
Cuando se crea una nueva directiva de cumplimiento en macOS (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Plataforma: macOS** > **Seguridad del sistema**), habrá nuevas opciones de **Firewall** disponibles: 
- **Firewall**: configure cómo se administran las conexiones entrantes en el entorno.
- **Conexiones entrantes**: **bloquee** todas las conexiones entrantes excepto las necesarias para los servicios básicos de Internet, como DHCP, Bonjour e IPSec. Esta opción también bloquea todos los servicios de uso compartido.
- **Modo sigiloso**: **habilite** el modo sigiloso para evitar que el dispositivo responda a solicitudes de sondeo. El dispositivo sigue respondiendo a las solicitudes entrantes de las aplicaciones autorizadas.

Se aplica a: macOS 10.12 y versiones posteriores

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Usar sAMAccountName como nombre de usuario de cuenta para perfiles de correo electrónico <!-- 1500307 -->

Podrá usar local el nombre **sAMAccountName** local como nombre de usuario de la cuenta para los perfiles de correo electrónico para Android, iOS y Windows 10. También podrá obtener el dominio del atributo `domain` o `ntdomain` en Azure Active Directory (Azure AD). O si lo prefiere, podrá especificar un dominio estático personalizado.

Para usar esta característica, debe sincronizar el atributo `sAMAccountName` desde el entorno de Active Directory local con Azure AD.

Se aplica a: Android, iOS, Windows 10 y versiones posteriores

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Exigir código de acceso no biométrico al transcurrir tiempo de espera y al iniciar la aplicación <!-- 1506985 -->

Al exigir un código de acceso no biométrico al iniciar la aplicación y después de transcurrir un tiempo de espera especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más detallado sobre el acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones móviles** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos.

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Borrado selectivo de datos de aplicaciones de la organización <!-- 1507030 -->
Los administradores podrán configurar un borrado selectivo de los datos de la organización como una nueva acción cuando no se cumplan las condiciones de Configuración de acceso de las Directivas de protección de aplicaciones (APP).  Mediante esta característica, los administradores podrán proteger y eliminar automáticamente datos confidenciales de la organización en las aplicaciones, en función de criterios configurados previamente.

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Revocar una aplicación iOS adquirida a través de PCV <!-- 1777384 -->
Como administrador de Microsoft Intune, podrá revocar la licencia de una determinada aplicación iOS adquirida a través del Programa de Compras por Volumen de Apple (PCV). Puede notificar a los usuarios cuando una aplicación ya no esté asignada a ellos. Revocar una licencia de aplicación no desinstalará la aplicación VPP desde el dispositivo. Para desinstalar una aplicación VPP, debe cambiar la acción de asignación a **Desinstalar**. El número de licencias reclamadas se indicará en el nodo **Aplicaciones con licencia** en la carga de trabajo **Aplicación** de Intune. Para más información relacionada con las aplicaciones iOS de PCV, vea [How to manage iOS apps purchased through a volume-purchase program with Microsoft Intune](vpp-apps-ios.md) (Administración de aplicaciones iOS adquiridas a través de un Programa de Compra de Licencias por Volumen con Microsoft Intune).

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Paquetes de idioma de Office 365 Pro Plus <!-- 1833450 -->
Como administrador de Intune, podrá implementar idiomas adicionales para las aplicaciones Office 365 Pro Plus administradas mediante Intune. La lista de idiomas disponibles incluye el **Tipo** de paquete de idioma (núcleo, parcial y corrección). En el portal de Azure, seleccione **Microsoft Intune** > **Aplicaciones móviles** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación** de la hoja **Agregar aplicación**, seleccione **Windows 10** en **Conjunto de aplicaciones de Office 365**. Seleccione **Idiomas** en la hoja **Configuración del conjunto de aplicaciones**.

### <a name="revoke-ios-vpp-app-license----1863797---"></a>Revocar licencias de aplicaciones iOS de PCV<!-- 1863797 -->
Como administrador, podrá recuperar la licencia de una aplicación iOS de PCV asignada a un usuario o un dispositivo. Al desinstalar una aplicación iOS de PCV, también podrá recuperar la licencia de la aplicación. Después, puede optar por asignar la licencia de la aplicación a otro usuario o dispositivo. Para más información sobre las licencias de aplicaciones iOS de PCV, vea [Manage iOS volume-purchased apps in Microsoft Intune](vpp-apps-ios.md) (Administración de aplicaciones iOS compradas por volumen en Microsoft Intune).

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Obtener una versión preliminar de una actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968 -->
Tras escuchar las opiniones de los clientes, estamos agregando nuevas características al sitio web de Portal de empresa y al catálogo de aplicaciones de iOS. Podrá comprobar una mejora considerable en las funciones y la facilidad de uso actual de los dispositivos Android, iOS y Windows. Se aplicará un diseño moderno y receptivo a las áreas del sitio, como los detalles del dispositivo, los comentarios, el soporte técnico y la descripción general del dispositivo. También verá:

- Flujos de trabajo simplificados en todas las plataformas del dispositivo
- Flujos mejorados para la identificación y la inscripción de dispositivos
- Mensajes de error más útiles
- Lenguaje más descriptivo con menos jerga técnica
- Posibilidad de compartir vínculos directos a aplicaciones
- Mejor rendimiento de los catálogos de aplicaciones de gran tamaño
- Mayor accesibilidad para todos los usuarios

Actualmente, la actualización está disponible en versión preliminar. Puede registrarse para unirse a la versión preliminar en http://aka.ms/webcpflighting.

### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Actualizaciones en los mensajes de no conformidad en la aplicación Portal de empresa <!-- 1832222 -->
Estamos revisando los mensajes que ven los usuarios cuando un dispositivo no es conforme. Los mensajes conservarán su significado original, pero se actualizarán con un lenguaje más descriptivo y menos jerga técnica. También estamos actualizando los vínculos a la documentación y los pasos de corrección para mantenerlos actualizados.  

Los textos siguientes son un ejemplo de las mejoras que verá en los mensajes:  

Antes: *Este dispositivo no ha contactado con el servicio de Intune en el período de tiempo especificado que requiere el administrador de TI. Para resolver este problema, abra la aplicación de Portal de empresa en el dispositivo y haga clic en el botón Comprobar cumplimiento.*  

Después: *Hace tiempo que el dispositivo no se registra en la organización. Para restablecer una conexión, abra la aplicación Portal de empresa en el dispositivo y pulse Comprobar configuración para el dispositivo*.  

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Editar implementaciones de aplicaciones de Office 365 Pro Plus <!-- 2150145 -->
Como administrador de Microsoft Intune, tendrá más capacidad para editar las implementaciones de aplicaciones de Office 365 Pro Plus. En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones móviles** > **Aplicaciones**. En la lista de aplicaciones, seleccione su conjunto de aplicaciones Office 365 ProPlus.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Revisión por fila de los identificadores de dispositivos corporativos duplicados cargados <!-- 2203794 -->
Al cargar identificadores corporativos, Intune proporcionará una lista de cualquier dispositivo duplicado y ofrecerá la opción de reemplazar o conservar la información existente. El informe se mostrará si hay duplicados después de elegir **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar identificadores**. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Agregar manualmente identificadores de dispositivos corporativos <!-- 2203803 -->
Podrá agregar manualmente identificadores de dispositivos corporativos. Elija **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar**.

### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Nuevo estado para dispositivos en la conformidad de dispositivos <!-- 2308882 -->
En **Conformidad de dispositivos** > **Directivas** > seleccione una directiva > **Información general**, se agregarán los estados nuevos siguientes:
- Correcto
- error
- Conflicto
- pendiente
- No aplicable

También se muestra una imagen con el número de dispositivos de una plataforma diferente. Por ejemplo, si está buscando un perfil de iOS, el nuevo icono muestra el número de dispositivos que no son de iOS que también están asignados a este perfil. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Conformidad de dispositivos compatible con soluciones antivirus de terceros <!-- 2325484 -->
Cuando cree una nueva directiva de cumplimiento de dispositivos (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Plataforma: Windows 10 y versiones posteriores** > **Configuración** > **Seguridad del sistema**), habrá nuevas opciones disponibles de **Seguridad del dispositivo**: 
- **Antivirus**: cuando se establece en **Requerir**, puede comprobar la conformidad mediante soluciones antivirus registradas con Centro de seguridad de Windows, como Symantec. 
- **Antispyware**: cuando se establece en **Requerir**, puede comprobar la conformidad mediante soluciones antispyware registradas con Centro de seguridad de Windows, como Symantec. 

Se aplica a: Windows 10 y versiones posteriores 

<!-- 1805 start -->

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Solución de problemas mejorada para la instalación de aplicaciones <!-- 928990 -->
En algunas ocasiones, las instalaciones de aplicaciones en los dispositivos administrados por MDM de Microsoft Intune pueden presentar errores. Cuando esto ocurre, puede ser complicado entender el motivo del error o cómo solucionarlo. Incluimos una Versión preliminar pública de las características de solución de problemas de las aplicaciones. Verá un nodo nuevo bajo cada dispositivo individual denominado **Aplicaciones administradas**. En él aparecen las aplicaciones que se han entregado a través de MDM de Intune. Dentro del nodo, verá una lista de los estados de instalación de las aplicaciones. Si selecciona una aplicación individual, aparecerá la vista de solución de problemas de esa aplicación específica. En la vista de solución de problemas, verá el ciclo de vida completo de la aplicación, como cuándo se creó y modificó la aplicación, el momento en que se estableció su destino y cuándo se entregó a un dispositivo. Además, si la instalación de la aplicación no se realizó correctamente, verá el código de error y un mensaje útil sobre la causa del mismo.

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Exigir código de acceso no biométrico al transcurrir tiempo de espera y al iniciar la aplicación en frío<!-- 1506985 --> 

Al exigir un código de acceso no biométrico al iniciar la aplicación en frío y después de transcurrir un tiempo de espera especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más detallado sobre el acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones móviles** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloqueo del acceso a aplicaciones según proveedores y modelos de dispositivos no aprobados <!-- 1425689 ! -->
El administración de TI de Intune podrá exigir una lista específica de fabricantes de dispositivos Android o modelos de iOS a través de las directivas de Intune App Protection. El administrador de TI puede brindar una lista de fabricantes separados por punto y coma para las directivas Android y los modelos de dispositivo para las directivas iOS. Las directivas de Intune App Protection solo son para Android e iOS. Podrá realizar dos acciones independientes en esta lista especificada:
- Bloquear el acceso a la aplicación en dispositivos no especificados.
- O bien, borrar de manera selectiva los datos corporativos en dispositivos no especificados. 

El usuario no podrá acceder a la aplicación de destino si no se cumplen los requisitos que establece la directiva. En función de la configuración, se podrá bloquear al usuario o borrar de manera selectiva sus datos corporativos dentro de la aplicación. En los dispositivos iOS, esta característica requiere la participación de las aplicaciones (es decir, WXP, Outlook, Managed Browser, Yammer) para integrar el SDK para aplicaciones de Intune para aplicar la configuración de versión mínima en las aplicaciones de destino. Esta integración se produce de manera gradual y depende de los equipos de la aplicación específica. En Android, esta característica requiere la versión más reciente de Portal de empresa. 

En los dispositivos del usuario final, el cliente de Intune tomaría medidas en función de una coincidencia simple de las cadenas que se especifican en la hoja Intune para las directivas de protección de aplicaciones. Esto depende por completo del valor que informa el dispositivo. Por lo tanto, se recomienda que el administrador de TI se asegure de que el comportamiento previsto sea preciso. Para ello, pruebe esta configuración en función de una variedad de fabricantes de dispositivos y de modelos dirigidos a un grupo de usuarios pequeño. En Microsoft Intune, seleccione **Aplicaciones móviles** > **Directivas de protección de aplicaciones** para ver y agregar directivas de protección de aplicaciones. Para más información sobre las directivas de protección de aplicaciones, consulte [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Acceso a acciones para las directivas de protección de aplicaciones <!-- 1483510 EEready -->
Pronto podrá configurar directivas de protección de aplicaciones para borrar, bloquear o advertir de manera explícita los dispositivos que no cumplen las directivas. La acción más reciente, *borrado*, quita los datos corporativos de su empresa de un dispositivo. Si se lleva a cabo esta acción, el usuario del dispositivo recibe una notificación sobre el motivo del borrado y los pasos para corregirlo. En el caso de algunas configuraciones, como la versión mínima de SO, podrá aplicar varias acciones, como el bloqueo o el borrado. Estas acciones se desencadenan cuando se inicia la aplicación.

<!-- 1804 start -->

### <a name="rules-for-removing-devices----1609459---"></a>Reglas para quitar dispositivos <!-- 1609459 -->
Hay disponibles nuevas reglas que permiten quitar automáticamente dispositivos que no se hayan protegido durante un número de días que establezca. Para ver la nueva regla, vaya al panel **Intune**, seleccione **Dispositivos** y **Device removal rules** (Reglas de eliminación de dispositivos).

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidad de implementar aplicaciones de línea de negocio (LOB) requeridas en todos los usuarios en dispositivos Windows 10 Escritorio <!-- 1627835 RS4 -->
Los clientes podrán implementar aplicaciones de Windows 10 de línea de negocio requeridas para instalarlas en contextos de dispositivo. Esto permitirá que estas aplicaciones estén disponibles para todos los usuarios del dispositivo. Esto solo es aplicable a dispositivos Windows 10 Escritorio.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Actualización de la experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android <!--1631531 -->

La experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android se actualizará de acuerdo con los procedimientos recomendados para las aplicaciones Android. En los próximos meses actualizaremos la aplicación Portal de empresa para Android para dividir el elemento de menú **Ayuda y comentarios** en los elementos de menú independientes **Ayuda** y **Enviar comentarios**. En la página **Ayuda** se incluirá una sección **Preguntas más frecuentes** y un botón **Soporte por correo electrónico** para permitir a los usuarios finales cargar registros a Microsoft y enviar al equipo de soporte técnico de la empresa un correo electrónico en el que se describa el problema. **Enviar comentarios** llevará al usuario a través de un proceso estándar de envío de comentarios de Microsoft, en el que se le pedirá elegir entre "Me gusta algo", "No me gusta algo" o "Tengo una idea".

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Directivas de protección de aplicaciones  <!-- 679615 -->
Las directivas de Intune App Protection ofrecerán la capacidad de crear directivas predeterminadas globales para habilitar rápidamente la protección en todos los usuarios de todo el inquilino.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.