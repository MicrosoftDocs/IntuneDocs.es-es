---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 62028232e4d6c9ab20a05480811978234ed0a3c1
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---may-2018"></a>La edición anticipada de Microsoft Intune: mayo de 2018

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
Pronto podrá configurar directivas de protección de aplicaciones para borrar, bloquear o advertir de manera explícita los dispositivos que no cumplen las directivas. La acción más reciente, *borrado*, quita los datos corporativos de su empresa de un dispositivo. Si se lleva a cabo esta acción, el usuario del dispositivo recibe una notificación sobre el motivo del borrado y los pasos para corregirlo. En el caso de algunas configuraciones, como la versión mínima de SO, podrá aplicar varias acciones, como el bloqueo o el borrado.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Nueva información de inventario para los dispositivos Windows <!-- 1333569 eeready -->

En los dispositivos Windows, la información de inventario siguiente estará disponible por dispositivo en la pestaña **Hardware** (**Grupos** > **Todos los dispositivos móviles** > **Dispositivos** > elija el dispositivo del usuario > **Ver propiedades** > **Hardware**):
- TPM
- Antivirus
- Antiespía
- Firewall
- UAC
- Batería
- Nombre de dominio

Para más información sobre cómo el CSP recupera estos datos, consulte las entradas de DeviceGuard en el artículo sobre el [CSP de DeviceStatus](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp).

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune y el explorador Microsoft Edge <!-- 1818969 -->
El explorador Microsoft Edge para dispositivos móviles (iOS y Android) ahora admite las directivas de protección de aplicaciones Intune. Intune protegerá a los usuarios que inicien sesión con sus cuentas corporativas de Azure AD en la aplicación de explorador Edge. 

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
Podrá asignar todos los usuarios, todos los dispositivos y todos los usuarios y dispositivos en los grupos de ámbito.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Los perfiles AutoPilot se migran a un destinatario de grupo <!-- 1877935 -->
Actualmente, los perfiles de implementación AutoPilot pueden asignarse a dispositivos seleccionados. Una vez que se libere esta característica, tendrá que hacer lo siguiente para asignar estos perfiles:
- Crear grupos (Azure AD) que contengan dispositivos AutoPilot
- Asigne los perfiles deseados a un grupo de Azure AD. El perfil AutoPilot ahora se asigna a los dispositivos AutoPilot de ese grupo.

### <a name="management-name-field-will-be-editable----1875989---"></a>El campo de nombre de administración se podrá editar <!-- 1875989 -->
Podrá editar el campo de nombre de administración en la hoja **Propiedades** de un dispositivo. Para editar este campo, elija **Dispositivos** > **Todos los dispositivos** > elija el dispositivo > **Propiedades**. Puede usar el campo de nombre de administración para identificar un dispositivo de manera única.

<!-- 1804 start -->


### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adiciones a la configuración de opciones de seguridad del dispositivo local <!-- 1403702 -->
Puede configurar opciones adicionales de seguridad del dispositivo local para dispositivos Windows 10. Las opciones adicionales están disponibles en las áreas de Cliente de redes de Microsoft, Servidor de red Microsoft, acceso y seguridad de red e inicio de sesión interactivo. Encuentre estos valores en la categoría de Endpoint Protection cuando cree una directiva de configuración de dispositivo de Windows 10.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Exigencia de instalación de perfiles de directivas, aplicaciones, certificados y red <!-- 1553555 -->
Los administradores pueden evitar que los usuarios finales accedan al escritorio de Windows 10 RS4 hasta que Intune instale los perfiles de directivas, aplicaciones, certificados y red durante el aprovisionamiento de dispositivos AutoPilot.

### <a name="rules-for-removing-devices----1609459---"></a>Reglas para quitar dispositivos <!-- 1609459 -->
Hay disponibles nuevas reglas que permiten quitar automáticamente dispositivos que no se hayan protegido durante un número de días que establezca. Para ver la nueva regla, vaya al panel **Intune**, seleccione **Dispositivos** y **Device removal rules** (Reglas de eliminación de dispositivos).

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitar aplicaciones y experiencias de consumidor en dispositivos Windows 10 Enterprise RS4 Autopilot<!-- 1621980 -->
Puede evitar la instalación de aplicaciones y experiencias de consumidor en los dispositivos Windows 10 Enterprise RS4 Autopilot. Para ver esta característica, vaya a **Intune** > **Inscripción de dispositivos** > **Inscripción de Windows** > **Perfiles de Windows AutoPilot** > **Crear nuevo** > **Configuración de inscripción**. 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Compatibilidad con múltiples instancias de Exchange Connector <!-- 2070451 -->

La limitación de una instancia de Microsoft Intune Exchange Connector por inquilino ya no se aplica. Intune admitirá varias instancias de Exchange Connector para que pueda configurar el acceso condicional de Intune con varias organizaciones de Exchange local.

Con un conector de Exchange local de Intune, se puede controlar el acceso de los dispositivos a los buzones de Exchange locales en función de si un dispositivo está inscrito en Intune y cumple con las directivas de cumplimiento de dispositivos de Intune. Para configurar un conector, descargue el conector de Exchange local de Intune desde Azure Portal e instálelo en un servidor en la organización de Exchange. En el panel de Microsoft Intune, elija **Acceso local** y, después, en **Instalación**, elija **Conector de Exchange ActiveSync**. Descargue el conector de Exchange local e instálelo en un servidor en la organización de Exchange. Ahora que ya no está limitado a un conector de Exchange por inquilino, si tiene otras organizaciones de Exchange, puede seguir el mismo proceso para descargar e instalar un conector para cada organización de Exchange adicional.

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>Disponibilidad próximamente de soporte técnico para el nuevo cliente Cisco AnyConnect para iOS <!-- 1333708 -->

Los nuevos perfiles de VPN creados para Cisco AnyConnect para iOS funcionarán con Cisco AnyConnect 4.0.7x y versiones posteriores. Los perfiles de VPN existentes de Cisco AnyConnect para iOS se etiquetarán como **Cisco Legacy AnyConnect** y continuarán funcionando con Cisco AnyConnect 4.0.5x como lo hacen en la actualidad.

> [!NOTE]
> Este cambio es solo para iOS; seguirá existiendo una sola opción de Cisco AnyConnect para Android, Android for Work y macOS.

#### <a name="more-information"></a>Más información

Debe crear un nuevo perfil de VPN de Cisco AnyConnect para iOS para admitir la nueva aplicación, ya que la nueva aplicación de Cisco AnyConnect y la aplicación de Cisco Legacy AnyConnect son independientes. Si administra el cliente AnyConnect en su entorno, también debe implementar la nueva aplicación de Cisco AnyConnect. Para completar una actualización, también debe eliminar el perfil de VPN de Cisco Legacy AnyConnect y quitar la aplicación de Cisco Legacy AnyConnect.

La integración del control de acceso de red (NAC) no funcionará para el nuevo cliente AnyConnect en la versión inicial. Estamos trabajando con Cisco para proporcionar una integración NAC en una futura versión de Intune.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidad de implementar aplicaciones de línea de negocio (LOB) requeridas en todos los usuarios en dispositivos Windows 10 Escritorio <!-- 1627835 RS4 -->
Los clientes podrán implementar aplicaciones de Windows 10 de línea de negocio requeridas para instalarlas en contextos de dispositivo. Esto permitirá que estas aplicaciones estén disponibles para todos los usuarios del dispositivo. Esto solo es aplicable a dispositivos Windows 10 Escritorio.

### <a name="company-portal-enrollment-improved----1874230--"></a>Mejora de la inscripción de Portal de empresa <!-- 1874230-->
Los usuarios que inscriban un dispositivo mediante el Portal de empresa en Windows 10, compilación 1703, y versiones posteriores podrán completar el primer paso de la inscripción sin salir de la aplicación.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Actualización de la experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android <!--1631531 -->

Actualizaremos la experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android de acuerdo con los procedimientos recomendados para las aplicaciones Android. En los próximos meses actualizaremos la aplicación Portal de empresa para Android para dividir el elemento de menú **Ayuda y comentarios** en los elementos de menú independientes **Ayuda** y **Enviar comentarios**. En la página **Ayuda** se incluirá una sección **Preguntas más frecuentes** y un botón **Soporte por correo electrónico** para permitir a los usuarios finales cargar registros a Microsoft y enviar al equipo de soporte técnico de la empresa un correo electrónico en el que se describa el problema. **Enviar comentarios** llevará al usuario a través de un proceso estándar de envío de comentarios de Microsoft, en el que se le pedirá elegir entre "Me gusta algo", "No me gusta algo" o "Tengo una idea".

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Directivas de protección de aplicaciones  <!-- 679615 -->
Las directivas de Intune App Protection ofrecerán la capacidad de crear directivas predeterminadas globales para habilitar rápidamente la protección en todos los usuarios de todo el inquilino.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
