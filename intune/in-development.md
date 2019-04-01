---
title: En el desarrollo - Microsoft Intune
titlesuffix: ''
description: En el desarrollo de las características de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c377a8558b1f318b4ddad735b6368a291e34516
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756826"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>En el desarrollo de Microsoft Intune: marzo de 2019

Para ayudar a su nivel de preparación y planeación, esta página listas Intune UI actualizaciones y características que están en desarrollo, pero aún no se ha liberado. Además:

- Si se prevé que deberá tomar medidas antes de realizar un cambio, publicaremos una entrada de centro de mensajes de Office gratuita.
- Cuando se inicia una característica en producción, ya sea como una vista previa o en disponibilidad general, se moverá la descripción de la característica fuera de esta página y en el [página Novedades](whats-new.md).
- Esta página y el [página Novedades](whats-new.md) se actualizan periódicamente. Compruebe si hay actualizaciones adicionales.
- Hacer referencia a la [guía básica de M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para entregas estratégicas y las escalas de tiempo.

> [!Note]
> Estos elementos reflejan las expectativas actuales de Microsoft sobre las capacidades de Intune que entran en una versión futura. Pueden cambiar las fechas y las características individuales. No todos los elementos de desarrollo tienen una descripción de la característica en esta página.

**Fuente RSS**: para recibir notificaciones cuando esta página se actualice, copie y pegue la dirección URL siguiente en el lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure


<!-- 1903 start-->

### <a name="encryption-report-----2351538---"></a>Informe de cifrado  <!-- 2351538 -->
Podrá usar un nuevo informe de cifrado para ver los detalles sobre el estado de cifrado de los dispositivos. Detalles disponibles incluirá una versión TPM de dispositivos, preparación de cifrado y estado, informes de errores y mucho más.  

### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-----2351547----"></a>Tener acceso a las claves de recuperación de BitLocker desde el portal de Intune  <!-- 2351547  -->
Estamos agregando un nuevo punto de entrada en los dispositivos, donde puede ver detalles de Azure Active Directory (AAD) sobre el identificador de clave de BitLocker y las claves de recuperación de BitLocker.

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>Etiquetas de ámbito para las directivas de configuración de aplicaciones <!--2371891 -->
Podrá agregar una etiqueta de ámbito a una directiva de configuración de aplicación para que sólo las personas con los roles también asignados la etiqueta de ámbito que tengan acceso a la directiva de configuración de la aplicación. La directiva de configuración de aplicación solo puede ser destinada a o asociada con las aplicaciones asignadas a la misma etiqueta de ámbito.

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Asignación de perfiles de AutoPilot al grupo virtual Todos los dispositivos <!--2715522 -->
Podrá asignar perfiles de AutoPilot al grupo virtual Todos los dispositivos. Para ello, elija **Inscripción de dispositivos** > **Inscripción Windows** > **Perfiles de implementación** > elija un perfil > **Tareas** > bajo **Asignar a** elija **Todos los dispositivos**. Para más información sobre los perfiles de Autopilot, vea [Inscribir dispositivos Windows con Windows Autopilot](enrollment-autopilot.md).

### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523----"></a>Instalar aplicaciones disponibles para el uso de la aplicación de Portal de empresa después de inscripción masiva de Windows <!-- 2751523  -->
Dispositivos Windows inscritos en Intune mediante [inscripción masiva de Windows](windows-bulk-enroll.md) (paquetes de aprovisionamiento) podrán usar la aplicación de Portal de empresa para instalar aplicaciones disponibles. Para obtener más información acerca de la aplicación de Portal de empresa, consulte [agregar manualmente el Portal de empresa de Windows 10](store-apps-company-portal-app.md) y [cómo configurar la aplicación de Portal de empresa de Microsoft Intune](company-portal-app.md).

### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430---"></a>Etiquetas de ámbito para los perfiles de aprovisionamiento de aplicaciones de iOS <!--2934430 -->
Podrá agregar una etiqueta de ámbito a un perfil de aprovisionamiento de aplicaciones de iOS para que sólo las personas con los roles también asignados la etiqueta de ámbito que tengan acceso a la aplicación de iOS que el perfil de aprovisionamiento. 

### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477----"></a>Herramienta de implementación de Office (ODT) XML para la implementación de Office ProPlus <!-- 3192477  -->
Podrá proporcionar herramientas de implementación de Office (ODT) XML al crear una instancia de Office Pro Plus en la consola de administración de Intune. Esto permite mayor capacidad de personalización si las opciones de Intune UI existentes no satisfacen sus necesidades. 

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>Impedir que los usuarios buscar actualizaciones de Windows    <!-- 3316758    -->
Estamos agregando un nuevo Windows anillo de actualización de configuración que puede usar que impide que los usuarios buscar actualizaciones de Windows. Esta opción no estará disponible en el portal, pero puede configurarse mediante el uso de Graph API de Intune.

### <a name="windows-update-notifications-----3316782---"></a>Notificaciones de actualización de Windows  <!-- 3316782 -->
Estamos agregando compatibilidad para las configuraciones de anillo de actualización de Windows por lo que podrá configurar las notificaciones de actualización de Windows que ven los usuarios. Esta opción no estará disponible en el portal, pero puede configurarse mediante el uso de Graph API de Intune.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Cambios realizados en la inscripción de Portal de empresa para los usuarios de dispositivos iOS 12 <!--3448635 -->  
Portal de empresa para iOS va a actualizar las pantallas de inscripción de la aplicación y los pasos para alinearse con los cambios de inscripción de MDM que publicó en Apple iOS 12.2. El flujo de trabajo actualizado ahora le pedirá a los usuarios:

- Permitir Safari abrir el sitio Web de Portal de empresa (a través de Safari) y descargar el perfil de administración antes de volver a la aplicación de Portal de empresa. 
- Abra la aplicación de configuración para instalar el perfil de administración en su dispositivo.
- Vuelva a la aplicación de Portal de empresa para realizar la inscripción.  

Para obtener más información acerca de cómo puede prepararse para estos cambios, consulte el [post de la comunidad tecnológica de Microsoft](https://techcommunity.microsoft.com/). Mientras tanto, para admitir nuevas inscripciones de iOS en el Portal de empresa, hemos actualizado los pasos descritos en [inscribir dispositivos de iOS en Intune](https://docs.microsoft.com/en-us/intune/ios-enroll). Estos cambios de docs serán dinámicos después de Apple iOS versión 12.2 de versiones. 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>Compatibilidad con conectores adicionales en la página de estado del inquilino <!-- 3617202     -->
Mostrará información de estado de los conectores adicionales, incluidos en la página de estado del inquilino *protección contra amenazas avanzada de Windows Defender* (ATP) y otros conectores de Mobile Threat Defense.

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>Intune de conceder acceso de lectura solo a algunos roles de Azure Active Directory <!-- 3637917 -->
Se deberá conceder que los siguientes roles de Azure AD solo acceso de lectura de Intune. Los permisos concedidos con roles de Azure AD sustituyen a los permisos concedidos con control de acceso basado en roles (RBAC) de Intune.

Acceso de lectura solo a los datos de auditoría de Intune:

- Administrador de cumplimiento
- Administrador de datos de cumplimiento

Acceso de solo lectura a todos los datos de Intune:

- Administrador de seguridad
- Operador de seguridad
- Lector de seguridad
- Lector global

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>Facilitar el acceso a la configuración de diagnóstico   <!-- 3804627   -->
Vamos a agregar una nueva opción para el **registros de auditoría** hoja en cada en cada carga de trabajo de registro de auditoría en la consola de Intune que puede usar para abrir directamente el *configuración de diagnóstico* página.

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>Crear y usar perfiles de configuración de dispositivo en dispositivos Android Zebra en Intune <!-- 3895244  -->
Intune admitirá la configuración de dispositivos Android cebra. En concreto, podrá: 

- Crear un perfil de configuración de dispositivo y aplicar la configuración para dispositivos Android cebra mediante perfiles de movilidad extensiones (MX) generados por StageNow (**configuración del dispositivo** > **perfiles**  >  **Crear perfil** > **Android** para la plataforma).

Se aplica a:  
- Android

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Implementación de aplicaciones de Microsoft Store para Empresas con licencias en línea <!-- 1672660  -->
Podrá asignar las aplicaciones de Microsoft Store para Empresas con licencias en línea necesarias en el contexto del dispositivo. Implementar una aplicación de Microsoft Store para Empresas de esta forma permitirá que la aplicación se instale para todos los usuarios en el dispositivo. Esto solo es aplicable para dispositivos de escritorio de Windows 10 RS4+. La opción para instalar en el contexto del dispositivo está disponible en la página de asignación de aplicaciones del cliente para las aplicaciones con licencia en línea de MSFB.

## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
