---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d6a06326fbb60d910aef0411fc666b82a5f22078
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>La edición anticipada de Microsoft Intune: abril de 2018

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

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Los sitios web de Azure Active Directory pueden requerir la aplicación Intune Managed Browser y compatibilidad con el inicio de sesión único para Managed Browser (versión preliminar pública) <!-- 710595 -->   
Con Azure Active Directory (Azure AD), podrá restringir el acceso a sitios web en dispositivos móviles a la aplicación Intune Managed Browser. En Managed Browser, los datos del sitio web permanecen seguros y separados de los datos personales del usuario final. Además, Managed Browser admite funciones de inicio de sesión único para sitios protegidos por Azure AD. Al iniciar sesión en Managed Browser, o al usarlo en un dispositivo con otra aplicación administrada por Intune, se permite que Managed Browser tenga acceso a sitios corporativos protegidos por Azure AD sin necesidad de que el usuario escriba sus credenciales. Esta funcionalidad se aplica a sitios como Outlook Web Access (OWA) y SharePoint Online, así como a otros sitios corporativos, como los recursos de intranet a los que se tiene acceso a través de Azure App Proxy.




## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.


### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


