---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95ad588b084319cd8a0f5f5c5d92da0e892eed50
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745050"
---
# <a name="the-early-edition-for-microsoft-intune---june-2018"></a>Edición anticipada de Microsoft Intune: mayo de 2018

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No comparta esta información fuera de la compañía. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

> [!Note]
>Los siguientes cambios están en fase de desarrollo de Intune. Para obtener más información sobre las nuevas características híbridas, vea la [página sobre las novedades de implementaciones híbridas](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

<!-- 1806 start -->

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

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968 -->
Tras escuchar las opiniones de los clientes, estamos agregando nuevas características al sitio web de Portal de empresa. Podrá comprobar una mejora considerable en las funciones y la facilidad de uso actual de los dispositivos Android, iOS y Windows. Se aplicará un diseño moderno y receptivo a las áreas del sitio, como los detalles del dispositivo, los comentarios, el soporte técnico y la descripción general del dispositivo. También verá:

- Flujos de trabajo simplificados en todas las plataformas del dispositivo
- Flujos mejorados para la identificación y la inscripción de dispositivos
- Mensajes de error más útiles
- Lenguaje más descriptivo con menos jerga técnica
- Posibilidad de compartir vínculos directos a aplicaciones
- Mejor rendimiento de los catálogos de aplicaciones de gran tamaño
- Mayor accesibilidad para todos los usuarios

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Editar implementaciones de aplicaciones de Office 365 Pro Plus <!-- 2150145 -->
Como administrador de Microsoft Intune, tendrá más capacidad para editar las implementaciones de aplicaciones de Office 365 Pro Plus. En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones móviles** > **Aplicaciones**. En la lista de aplicaciones, seleccione su conjunto de aplicaciones Office 365 ProPlus.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Revisión por fila de los identificadores de dispositivos corporativos duplicados cargados <!-- 2203794 -->
Al cargar identificadores corporativos, Intune proporcionará una lista de cualquier dispositivo duplicado y ofrecerá la opción de reemplazar o conservar la información existente. El informe se mostrará si hay duplicados después de elegir **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar identificadores**. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Agregar manualmente identificadores de dispositivos corporativos <!-- 2203803 -->
Podrá agregar manualmente identificadores de dispositivos corporativos. Elija **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar**.

### <a name="new-status-for-devices-in-device-configuration----2308882---"></a>Nuevo estado para dispositivos en la configuración de dispositivos <!-- 2308882 -->
En **Configuración del dispositivo** > **Información general**, se agregarán estos nuevos estados:
- Correcto
- error
- Conflicto
- pendiente
- No aplicable: una imagen que también muestra el número de dispositivos de una plataforma diferente. Por ejemplo, si está buscando un perfil de iOS, el nuevo icono muestra el número de dispositivos que no son de iOS que también están asignados a este perfil. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Conformidad de dispositivos compatible con soluciones antivirus de terceros <!-- 2325484 -->
Cuando cree una nueva directiva de cumplimiento de dispositivos (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Plataforma: Windows 10 y versiones posteriores** > **Configuración** > **Seguridad del sistema**), habrá nuevas opciones disponibles de **Seguridad del dispositivo**: 
- **Antivirus**: cuando se establece en **Requerir**, puede comprobar la conformidad mediante soluciones antivirus registradas con Centro de seguridad de Windows, como Symantec. 
- **Antispyware**: cuando se establece en **Requerir**, puede comprobar la conformidad mediante soluciones antispyware registradas con Centro de seguridad de Windows, como Symantec. 

Se aplica a: Windows 10 y versiones posteriores 

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Compatibilidad con perfiles de VPN de Palo Alto Networks GlobalProtect <!-- 1333680 eeready ! -->

Con esta actualización, puede elegir Palo Alto Networks GlobalProtect como un tipo de conexión VPN para perfiles de VPN en Intune (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Tipo de perfil** > **VPN**). En esta versión, se admiten las siguientes plataformas: 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>Establecimiento del cumplimiento por ubicación del dispositivo <!-- 851881 ! -->
En algunas situaciones, es posible que desee restringir el acceso a los recursos corporativos a una ubicación específica, definida por una conexión de red. Podrá crear una directiva de cumplimiento (**Cumplimiento de dispositivos** > **Ubicaciones**) en función de la dirección IP del dispositivo. Si el dispositivo sale del intervalo IP, no podrá acceder a los recursos corporativos.

Se aplica a: dispositivos Android 6.0 y versiones posteriores, con la aplicación Portal de empresa actualizada

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

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Habilitación de la pantalla completa en dispositivos Windows 10 <!-- 1560072 ! -->
En los dispositivos Windows 10, puede crear un perfil de configuración y habilitar la pantalla completa (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Windows 10** > **Restricciones de dispositivos** > **Quiosco**). En esta actualización, la configuración **Quiosco (versión preliminar)** cambia de nombre a **Quiosco (obsoleto)**. Ya no se recomienda usar **Quiosco (obsoleto)**, pero seguirá funcionando hasta la actualización de julio. El nuevo tipo de perfil **Quiosco** reemplaza a **Quiosco (obsoleto)** (**Crear perfil** > **Windows 10** > **Quiosco (versión preliminar)**), que contendrá los valores para configurar Quioscos en Windows 10 RS4 y versiones posteriores.

Se aplica a Windows 10 y versiones posteriores.

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Recuperación del identificador de modelo de usuario de la aplicación (AUMID) asociado para aplicaciones de Microsoft Store para Empresas en pantalla completa <!-- 1560077 ! -->
Intune podrá recuperar los identificadores de modelo de usuario de la aplicación (AUMID) para aplicaciones de Microsoft Store para Empresas (WSfB) con el fin de mejorar la configuración del perfil de quiosco.

Para más información sobre las aplicaciones de Microsoft Store para Empresas, consulte el artículo sobre la [administración de aplicaciones de Microsoft Store para Empresas](windows-store-for-business.md).

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Acceso a acciones para las directivas de protección de aplicaciones <!-- 1483510 EEready -->
Pronto podrá configurar directivas de protección de aplicaciones para borrar, bloquear o advertir de manera explícita los dispositivos que no cumplen las directivas. La acción más reciente, *borrado*, quita los datos corporativos de su empresa de un dispositivo. Si se lleva a cabo esta acción, el usuario del dispositivo recibe una notificación sobre el motivo del borrado y los pasos para corregirlo. En el caso de algunas configuraciones, como la versión mínima de SO, podrá aplicar varias acciones, como el bloqueo o el borrado. Estas acciones se desencadenan cuando se inicia la aplicación.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Nueva información de inventario para los dispositivos Windows <!-- 1333569 eeready -->

En los dispositivos Windows, la información de inventario siguiente estará disponible por dispositivo en la pestaña **Hardware** (**Grupos** > **Todos los dispositivos móviles** > **Dispositivos** > elija el dispositivo del usuario > **Ver propiedades** > **Hardware**):
- TPM
- Antivirus
- Antiespía
- Firewall
- UAC
- Batería
- Nombre de dominio

Para más información sobre cómo el CSP recupera estos datos, vea las entradas de DeviceStatus en el artículo [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) (CSP de DeviceStatus).

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune y el explorador Microsoft Edge <!-- 1818969 -->
El explorador Microsoft Edge para dispositivos móviles (iOS y Android) ahora admite las directivas de protección de aplicaciones Intune. Los usuarios que inicien sesión con sus cuentas corporativas de Azure AD en la aplicación de explorador Edge estarán protegidas por Intune. 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nueva configuración de idioma y región al realizar la configuración rápida de Autopilot <!-- 1821766 -->
Habrá disponible una configuración nueva para establecer el idioma y la región de los perfiles de Autopilot durante la configuración rápida.

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nuevo valor para configurar el teclado del dispositivo <!-- 1821768 -->
Habrá disponible un valor nuevo para configurar el teclado de los perfiles de Autopilot durante la configuración rápida.

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Use TeamViewer para compartir la pantalla de dispositivos iOS y MacOS <!-- 1985547 -->
En este momento, puede usar TeamViewer para administrar de manera remota los [dispositivos Android y Windows administrados por Intune](device-profile-android-teamviewer.md).

Los administradores podrán conectarse a TeamViewer e iniciar una sesión de uso compartido de pantalla con dispositivos iOS y macOS. Los usuarios de iPhone, iPad y macOS pueden compartir sus pantallas en vivo con cualquier otro dispositivo móvil o de escritorio. 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Vuelve el gráfico de usuario del perfil del dispositivo <!-- 2160133 -->
Si bien mejoraba el valor numérico que aparece en el gráfico del perfil del dispositivo (**Configuración de dispositivos** > **Perfiles** > seleccione un perfil existente > **Información general**), el gráfico de usuario se quitó de manera temporal.

Con esta actualización, dicho gráfico vuelve y aparece en Azure Portal.

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Asignación de todos los usuarios y dispositivos como grupos de ámbito <!-- 2196803 -->
Podrá asignar todos los usuarios, todos los dispositivos y todos los usuarios y dispositivos en los grupos de ámbito. Para ello, elija **Roles de Intune** > **Todos los roles** > **Policy and profile manager (Administrador de directivas y perfiles)** > **Asignaciones**  > elija una asignación > **Ámbito (grupos)**.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Los perfiles AutoPilot se migran a un destinatario de grupo <!-- 1877935 -->
Actualmente, los perfiles de implementación AutoPilot pueden asignarse a dispositivos seleccionados. Una vez que se libere esta característica, tendrá que hacer lo siguiente para asignar estos perfiles:
- Crear grupos (Azure AD) que contengan dispositivos AutoPilot
- Asigne los perfiles deseados a un grupo de Azure AD. El perfil AutoPilot ahora se asigna a los dispositivos AutoPilot de ese grupo.

### <a name="management-name-field-will-be-editable----1875989---"></a>El campo de nombre de administración se podrá editar <!-- 1875989 -->
Podrá editar el campo de nombre de administración en la hoja **Propiedades** de un dispositivo. Para editar este campo, elija **Dispositivos** > **Todos los dispositivos** > elija el dispositivo > **Propiedades**. Puede usar el campo de nombre de administración para identificar un dispositivo de manera única.

<!-- 1804 start -->

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adiciones a la configuración de opciones de seguridad del dispositivo local <!-- 1403702 -->
Puede configurar opciones adicionales de seguridad del dispositivo local para dispositivos Windows 10. Las opciones adicionales están disponibles en las áreas de Cliente de redes de Microsoft, Servidor de red Microsoft, acceso y seguridad de red e inicio de sesión interactivo. Encuentre estos valores en la categoría de Endpoint Protection cuando cree una directiva de configuración de dispositivo de Windows 10.

### <a name="rules-for-removing-devices----1609459---"></a>Reglas para quitar dispositivos <!-- 1609459 -->
Hay disponibles nuevas reglas que permiten quitar automáticamente dispositivos que no se hayan protegido durante un número de días que establezca. Para ver la nueva regla, vaya al panel **Intune**, seleccione **Dispositivos** y **Device removal rules** (Reglas de eliminación de dispositivos).

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitar aplicaciones y experiencias de consumidor en dispositivos Windows 10 Enterprise RS4 Autopilot<!-- 1621980 -->
Puede evitar la instalación de aplicaciones y experiencias de consumidor en los dispositivos Windows 10 Enterprise RS4 Autopilot. Para ver esta característica, vaya a **Intune** > **Inscripción de dispositivos** > **Inscripción de Windows** > **Perfiles de Windows AutoPilot** > **Crear nuevo** > **Configuración de inscripción**. 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Compatibilidad con múltiples instancias de Exchange Connector <!-- 2070451 -->

La limitación de una instancia de Microsoft Intune Exchange Connector por inquilino ya no se aplica. Intune admitirá varias instancias de Exchange Connector para que pueda configurar el acceso condicional de Intune con varias organizaciones de Exchange local.

Con un conector de Exchange local de Intune, se puede controlar el acceso de los dispositivos a los buzones de Exchange locales en función de si un dispositivo está inscrito en Intune y cumple con las directivas de cumplimiento de dispositivos de Intune. Para configurar un conector, descargue el conector de Exchange local de Intune desde Azure Portal e instálelo en un servidor en la organización de Exchange. En el panel de Microsoft Intune, elija **Acceso local** y, después, en **Instalación**, elija **Conector de Exchange ActiveSync**. Descargue el conector de Exchange local e instálelo en un servidor en la organización de Exchange. Ahora que ya no está limitado a un conector de Exchange por inquilino, si tiene otras organizaciones de Exchange, puede seguir el mismo proceso para descargar e instalar un conector para cada organización de Exchange adicional.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidad de implementar aplicaciones de línea de negocio (LOB) requeridas en todos los usuarios en dispositivos Windows 10 Escritorio <!-- 1627835 RS4 -->
Los clientes podrán implementar aplicaciones de Windows 10 de línea de negocio requeridas para instalarlas en contextos de dispositivo. Esto permitirá que estas aplicaciones estén disponibles para todos los usuarios del dispositivo. Esto solo es aplicable a dispositivos Windows 10 Escritorio.

### <a name="company-portal-enrollment-improved----1874230--"></a>Mejora de la inscripción de Portal de empresa <!-- 1874230-->
Los usuarios que inscriban un dispositivo mediante el Portal de empresa en Windows 10, compilación 1703, y versiones posteriores podrán completar el primer paso de la inscripción sin salir de la aplicación.

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



