---
title: Crear el diseño de Microsoft Intune
titleSuffix: Microsoft Intune
description: Este artículo le ayuda a crear un diseño para una implementación y diseño solo en la nube de Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 24f15cb179dfc2b12b642f5f196d04dce58d4377
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505197"
---
# <a name="create-a-design"></a>Creación de un diseño

El diseño de Intune se basa en la información que recopile y en las decisiones que tome al completar otras [secciones anteriores de esta guía](../planning-guide.md). Le ayuda a reunir lo siguiente:

- El entorno actual

- Las opciones de implementación de Intune

- Los requisitos de identidad para las dependencias externas

- Consideraciones de la plataforma de dispositivos

- Requisitos que se van a proporcionar  

Aunque existen requisitos mínimos de infraestructura local, es útil que disponga de un plan de diseño para asegurarse de que va a tener la solución de administración de dispositivos móviles correcta que cumpla sus metas, objetivos y requisitos.

Revisemos cada una de estas áreas con más detalle. 

## <a name="record-your-current-environment"></a>Registro del entorno actual
Además, es habitual realizar cambios de diseño durante las fases de implementación y prueba. Use el plan de diseño para documentar estos cambios y la lógica subyacente a medida que se produzcan.

El entorno actual puede influir en las decisiones de diseño, y debe documentarse y hacerse referencia a él al tomar otras decisiones de diseño de Intune. A continuación se muestran algunos ejemplos de cómo registrar el entorno actual:

- **Identidad en la nube**

  - ¿Usa DirSync o Azure Active Directory (Azure AD) Connect?

  - ¿Su entorno está federado?

  - ¿Está habilitada la autenticación multifactor (MFA)?

- **Entorno del correo electrónico**

  - ¿Usa Exchange? ¿Es local o en la nube?

  - ¿Se encuentra en el medio de un proyecto para migrar Exchange a la nube?

- **Solución actual de administración de dispositivos móviles (MDM)**

  - ¿Está usando actualmente otras soluciones MDM?

  - ¿Qué soluciones MDM está usando para los escenarios de casos de uso BYOD y de la empresa?

  - ¿Qué características está usando (por ejemplo, configuración de dispositivos de aplicaciones, configuraciones Wi-Fi)?

  - ¿Qué plataformas de dispositivos se admiten?

  - ¿Qué grupos y cuántos usuarios están usando la solución MDM?

- **Solución de certificado**

  - ¿Ha implementado una solución de certificado?

  - ¿Qué tipo de certificado usa?

- **Administración de sistemas**

  - ¿Cómo está administrando su PC y el entorno del servidor?

  - ¿Usa System Center Configuration Manager? ¿Está usando una plataforma de administración de sistemas de terceros?

- **Solución de VPN**

  - ¿Cuál es su solución de VPN?

  - ¿Lo usa para escenarios de casos de uso BYOD y de la empresa?

Asegúrese de anotar cualquier proyecto o cualquier otro plan que podría afectar al entorno al registrar el entorno MDM actual. A continuación se muestra un ejemplo de una manera de registrar el entorno actual al crear el diseño de Intune:

| **Área de solución** | **Entorno actual** | **Comentarios** |
|---|---|---|
| **Identidad** | Azure AD, Azure AD Connect, no federado, no MFA | Proyecto para habilitar MFA a finales de año |                 
| **Entorno del correo electrónico** | Exchange Online, Exchange local | Migrando actualmente de Exchange local a Exchange Online. 75 % de buzones migrados. El último 25 % se migrará antes de que comience el piloto de Intune. |                
| **SharePoint** | SharePoint local | Ningún plan para moverse a SharePoint Online |  
| **MDM actual** | Exchange ActiveSync |  |
| **Solución de certificado** | Microsoft Server 2012 R2, Servicios de certificado de AD | Solo se usa PKI en servidores de sitio web |
| **Administración de sistemas** | System Center Configuration Manager CB 1606 | Le gustaría investigar una solución híbrida de Intune |
| **Solución de VPN** | Cisco AnyConnect |  |


Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para desarrollar el plan de diseño de Intune.

## <a name="choose-an-intune-deployment-option"></a>Elegir una opción de implementación de Intune

Intune ofrece dos opciones de implementación: independiente e híbrida. Independiente se refiere al servicio de Intune que se ejecuta en la nube, híbrida se refiere a la integración de Intune con System Center Configuration Manager. Esta guía está destinada principalmente al uso de la opción independiente. [Decida qué opción se adapta a los requisitos de su empresa](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

> [!Important]
>La incorporación de nuevos clientes MDM híbridos está en desuso. Para obtener más información, vea la entrada de blog [Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) (Transición de la administración de dispositivos móviles híbrida a Intune en Azure).


## <a name="intune-tenant-location"></a>Ubicación del inquilino de Intune

Si su organización tiene una presencia global, asegúrese de planear dónde se encontrará su inquilino al suscribirse al servicio. El país o región se define cuando se registra en una suscripción de Intune la primera vez, y se asignan los países o regiones del mundo que se muestran a continuación:

- América del Norte

- Europa, Oriente Medio y África

- Asia y Pacífico

>[!IMPORTANT]
> No es posible cambiar el país o región y la ubicación del inquilino posteriormente.

## <a name="external-dependencies"></a>Dependencias externas

Las dependencias externas son servicios y productos que son independientes de Intune, pero son un requisito de este o pueden integrarse en él. Es importante identificar los requisitos de cualquier dependencia externa y cómo se configurará. A continuación se muestran algunos ejemplos de dependencias externas comunes:

- Identidad

- Grupos de usuarios y dispositivos

- Infraestructura de clave pública (PKI)

Aquí veremos con más detalle estas dependencias externas comunes.

### <a name="identity"></a>Identidad

Identidad es la manera en que se identifica a los usuarios que pertenecen a la organización y que se inscriben en un dispositivo. Intune requiere Azure Active Directory (Azure AD) como el proveedor de identidades de usuario. Si ya usa este servicio, puede usar la identidad existente en la nube. Además, Azure AD Connect es la herramienta recomendada para sincronizar sus identidades de usuario locales con los servicios en la nube de Microsoft. Si su organización ya usa Office 365, es importante que Intune use el mismo entorno de Azure AD.

Obtenga más información sobre los siguientes requisitos de identidad de Intune:

- [Requisitos de identidad](https://docs.microsoft.com/azure/active-directory/understand-azure-identity-solutions).

- [Requisitos de sincronización de directorios](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

- [Requisitos de autenticación multifactor](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

### <a name="user-and-device-groups"></a>Grupos de usuarios y dispositivos

Los grupos de usuarios y dispositivos determinan el destino de una implementación, incluidas las directivas, las aplicaciones y los perfiles. Debe determinar qué grupos de usuarios y dispositivos serán necesarios.

Se recomienda que cree todos los grupos en Active Directory local y, después, sincronice con Azure AD. Obtenga más información sobre la planeación y la creación de grupos de usuarios y dispositivos:

- [Planear los grupos de usuarios y dispositivos](users-add.md).

- [Crear grupos de usuarios y dispositivos](groups-add.md).

### <a name="public-key-infrastructure-pki"></a>Infraestructura de clave pública (PKI)
La infraestructura de clave pública proporciona certificados a los dispositivos o usuarios para autenticarse de manera segura en un servicio. Intune admite una infraestructura de PKI de Microsoft. Los certificados de usuarios y dispositivos pueden emitirse en un dispositivo móvil para cumplir los requisitos de autenticación basados en certificados. Antes de usar los certificados, debe determinar si son necesarios, si la infraestructura de red puede admitir la autenticación basada en certificados y si los certificados se usan actualmente en el entorno existente.

Si está planeando usar certificados con perfiles de VPN, Wi-Fi o correo electrónico con Intune, asegúrese de que tiene una [infraestructura de PKI](../protect/certificates-configure.md) admitida y lista para crear e implementar perfiles de certificado.

Además, si se van a usar perfiles de certificado SCEP, debe determinar qué servidor hospedará la característica Servicio de inscripción de dispositivos de red (NDES) y cómo se producirá la comunicación.

Más información acerca de:

- [Cómo configurar perfiles de certificado de Intune](../protect/certificates-configure.md)

- [Cómo configurar la infraestructura de certificados para SCEP](../protect/certificates-scep-configure.md).

- [Cómo configurar la infraestructura de certificados para PFX](../protect/certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>Consideraciones de la plataforma de dispositivos

Examine con más detenimiento los siguientes aspectos de los dispositivos para entender cómo administrarlos correctamente.

- Plataformas de dispositivos compatibles

- Dispositivos

- Propiedad del dispositivo

- Inscripción masiva

Revisemos estas áreas con más detalle.

### <a name="determine-supported-device-platforms"></a>Determinar las plataformas de dispositivos compatibles

Necesita saber qué dispositivos estarán en el entorno y comprobar si son compatibles o no con Intune al crear su diseño. Intune admite plataformas de iOS, Android y Windows.

[Lista completa de dispositivos compatibles con Intune](supported-devices-browsers.md).

### <a name="devices"></a>Dispositivos

Intune administra dispositivos móviles para proteger los datos corporativos y permitir que los usuarios finales trabajen desde más ubicaciones. Intune admite numerosas plataformas de dispositivos, por lo que se recomienda documentar los dispositivos y las plataformas y versiones de sistema operativo que se admitirán en el diseño de la organización. Por ejemplo:

| **Plataforma de dispositivo** | **Versiones del sistema operativo** |
|:---:|:---:|
| iOS: iPhone | 10.0+ |                
| iOS: iPad | 10.0+ |               
| Android: Samsung KNOX Standard | 4.0+ |
| Tableta de Windows 10 | 10+ |


Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para desarrollar la lista de dispositivos.
### <a name="device-ownership"></a>Propiedad del dispositivo

Intune admite dispositivos de propiedad corporativa y personal. Un dispositivo se considera de propiedad corporativa si está inscrito por un administrador de inscripción de dispositivos o por un programa de inscripción de dispositivos. Por ejemplo, un dispositivo se inscribe mediante el Programa de Inscripción de Dispositivos (DEP) de Apple, se marca como corporativo y se coloca en un grupo de dispositivos que recibe aplicaciones y directivas corporativas de destino.

Consulte la [Sección 3: Determinación de los requisitos de los escenarios de casos de uso](planning-guide-requirements.md) para obtener más información sobre los casos de uso BYOD y de la empresa.

### <a name="bulk-enrollment"></a>Inscripción masiva

 Puede inscribir dispositivos masivamente de maneras diferentes según la plataforma. Si se necesita la inscripción masiva, primero [determine el método de inscripción masiva](../enrollment/device-enrollment.md) e incorpórelo a su diseño.

## <a name="feature-requirements"></a>Requisitos de características

En estas secciones, revisaremos las siguientes funciones y características que se adaptan a los requisitos de escenarios de casos de uso:

- Directivas de términos y condiciones

- Directivas de configuración

- Perfiles de recursos

- Aplicaciones

- Directiva de cumplimiento

- Acceso condicional

Revisemos cada una de estas áreas con más detalle.

### <a name="terms-and-conditions-policies"></a>Directivas de términos y condiciones

Puede usar los [términos y condiciones](../enrollment/terms-and-conditions-create.md) para explicar las directivas o las condiciones que un usuario final debe aceptar antes de la inscripción del dispositivo. Intune admite la capacidad de agregar e implementar varias directivas de términos y condiciones a los grupos de usuarios.

Necesita determinar si se necesitan las directivas de términos y condiciones. De ser así, determine quién será el responsable de proporcionar esta información en la organización. A continuación se muestra un ejemplo de cómo documentar la directiva de términos y condiciones.

| **Nombre de los términos y condiciones** | **Caso de uso** | **Grupo de destino** |
|:---:|:---:|:---:|
| Términos y condiciones corporativos | Corporativos | Usuarios corporativos |                 
| Términos y condiciones BYOD | BYOD | Usuarios BYOD |                


También puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para asignar los términos y las condiciones a los grupos de usuarios.

### <a name="configuration-policies"></a>Directivas de configuración

Use las directivas de configuración para administrar las características y la configuración de seguridad en un dispositivo. Al diseñar las directivas de configuración, consulte la sección de los requisitos de casos de uso para determinar las configuraciones necesarias para los dispositivos de Intune. Documente la configuración y cómo se debe establecer. Además, documente a qué grupos de usuarios o dispositivos se destinará.

Debe crear al menos una directiva de configuración por plataforma. Puede crear varias directivas de configuración por plataforma si es necesario. A continuación se muestra un ejemplo del diseño de cuatro directivas de configuración diferentes para plataformas y escenarios de casos de uso distintos.

| **Nombre de la directiva** | **Plataforma de dispositivo** | **Configuración** | **Grupo de destino** |   
|:---:|:---:|:---:|:---:|
| Corporativo: iOS | iOS | Se necesita PIN, longitud: 6, Restringir la copia de seguridad en la nube | Dispositivos corporativos |                                                           
| Corporativo: Android | Android | Se necesita PIN, longitud: 6, Restringir la copia de seguridad en la nube | Dispositivos corporativos |                                                           
| BYOD: iOS  | iOS | Se necesita PIN, longitud: 4 | Dispositivos BYOD |
| BYOD: Android  | Android | Se necesita PIN, longitud: 4 | Dispositivos BYOD |


Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar los requisitos de la directiva de configuración.

### <a name="profiles"></a>Profiles

Use perfiles para ayudar al usuario final a conectarse a los datos de la empresa. Intune admite muchos tipos de perfiles. Consulte los requisitos y los casos de uso para determinar cuándo se configurarán los perfiles. Todos los perfiles de dispositivo están clasificados por tipo de plataforma, y deben incluirse en la documentación de diseño.

- Perfiles de certificado

- Perfil de Wi-Fi

- Perfil de VPN

- Perfil de correo electrónico

Revisemos cada tipo de perfil con más detalle.

#### <a name="certificate-profiles"></a>Perfiles de certificado

Los perfiles de certificado permiten que Intune emita un certificado para un usuario o dispositivo. Intune admite lo siguiente:

- Protocolo de inscripción de certificados simple (SCEP)

- Certificado de raíz de confianza

- Certificado PFX.

Se recomienda que documente qué grupo de usuarios necesita un certificado, cuántos perfiles de certificado se necesitan y en qué grupos de usuarios se van a implementar.

>[!NOTE]
> Recuerde que se necesita el certificado raíz de confianza para el perfil de certificado SCEP, de manera que asegúrese de que todos los usuarios destinados al perfil de certificado SCEP también reciben un certificado raíz de confianza. Si necesita certificados SCEP, diseñe y documente qué plantillas de certificado SCEP se van a necesitar.

Aquí se muestra un ejemplo de cómo puede documentar los certificados durante el diseño:

| **Tipo** | **Nombre de perfil** | **Plataforma de dispositivo** | **Casos de uso** |   
|:---:|:---:|:---:|:---:|
| CA raíz | CA raíz corporativo | Android, iOS, Windows Mobile | Corporativo, BYOD  |                                                           
| SCEP | Certificado de usuario | Android, iOS, Windows Mobile | Corporativo, BYOD |                                                           


Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar los requisitos de los perfiles de certificado.

#### <a name="wi-fi-profile"></a>Perfil de Wi-Fi

Los perfiles de Wi-Fi se usan para conectar automáticamente un dispositivo móvil a una red inalámbrica. Intune admite la implementación de perfiles de Wi-Fi en todas las plataformas compatibles. Más información sobre [cómo Intune admite los perfiles de Wi-Fi](../configuration/wi-fi-settings-configure.md).

A continuación se muestra un ejemplo de un diseño de un perfil de Wi-Fi:

| **Tipo** | **Nombre del perfil** | **Plataforma de dispositivo** | **Casos de uso** | | Wi-Fi | Perfil de Wi-Fi de Asia | Android | Corporativo, región de Asia BYOD | | Wi-Fi | Perfil de Wi-Fi de América del Norte | Android, iOS, Windows 10 Mobile | Corporativo, región de América del Norte BYOD |

Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar los requisitos de los perfiles de Wi-Fi.

#### <a name="vpn-profile"></a>Perfil de VPN

Los perfiles de VPN permiten que los usuarios accedan de manera segura a su red desde ubicaciones remotas. Intune admite los perfiles de VPN desde conexiones de VPN móviles nativas y proveedores de terceros. Más información sobre los [perfiles de VPN y los proveedores admitidos por Intune](../configuration/vpn-settings-configure.md).

A continuación se muestra un ejemplo de la documentación del diseño de un perfil de VPN.

| **Tipo** | **Nombre de perfil** | **Plataforma de dispositivo** | **Casos de uso** |
|:---:|:---:|:---:|:---:|
| VPN | Perfil de cualquier conexión de VPN Cisco | Android, iOS, Windows 10 Mobile | Corporativo, América del Norte y Alemania BYOD|
| VPN | Pulse Secure | Android | Corporativo, región de Asia BYOD |

Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar los requisitos de los perfiles de VPN.

#### <a name="email-profile"></a>Perfil de correo electrónico

Los perfiles de correo electrónico permiten que un cliente de correo se configure automáticamente con la información de conexión y la configuración del correo electrónico. Intune admite los perfiles de correo electrónico en algunos dispositivos. Obtenga más información sobre los [perfiles de correo electrónico y qué plataformas son compatibles](../configuration/email-settings-configure.md).

A continuación se muestra un ejemplo de la documentación del diseño de perfiles de correo electrónico:

| **Tipo** | **Nombre de perfil** | **Plataforma de dispositivo** | **Casos de uso** |
|:---:|:---:|:---:|:---:|
| Perfil de correo electrónico | Perfil de correo electrónico iOS | iOS | Corporativo: trabajador de la información BYOD |
| Perfil de correo electrónico | Perfil de correo electrónico Android KNOX | Android KNOX | BYOD |

Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar los requisitos de los perfiles de correo electrónico.
### <a name="apps"></a>Aplicaciones

Puede usar Intune para proporcionar las aplicaciones a los usuarios o a los dispositivos de varias maneras. El tipo de aplicación incluye aplicaciones de instalador de software, aplicaciones de una tienda de aplicaciones pública, vínculos externos o aplicaciones iOS administradas. Además de las implementaciones de aplicaciones individuales, puede administrar e implementar las aplicaciones adquiridas por volumen mediante los programas de compra por volumen para iOS y Windows. Más información acerca de:

- [Tipos de aplicaciones que se pueden proporcionar](../apps/app-management.md)

- [Programa de Compras por Volumen (VPP) de iOS para empresas](../apps/vpp-apps-ios.md)

- [Tienda Microsoft para aplicaciones empresariales](../apps/windows-store-for-business.md)

#### <a name="app-type-requirements"></a>Requisitos del tipo de aplicación

Como las aplicaciones pueden implementarse en usuarios y dispositivos, se recomienda decidir qué aplicaciones administrará Intune. Mientras se recopila la lista, intente responder a las siguientes preguntas:

- ¿Las aplicaciones requieren integración con servicios en la nube?

- ¿Las aplicaciones estarán disponibles para los usuarios BYOD?

- ¿Cuáles son las opciones de implementación disponibles de estas aplicaciones?

- ¿Su empresa necesita proporcionar acceso a datos de aplicaciones de software como servicio (SaaS) para sus partners?

- ¿Las aplicaciones requieren que se acceda a Internet desde los dispositivos de los usuarios?

- ¿Las aplicaciones están disponibles públicamente en una tienda de aplicaciones o son aplicaciones de línea de negocio (LOB) personalizadas?


#### <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

Las directivas de protección de aplicaciones minimizan la pérdida de datos definiendo cómo administra la aplicación los datos corporativos. Intune admite las directivas de protección de aplicaciones para cualquier aplicación compilada para funcionar con la administración de aplicaciones móviles. Al diseñar la directiva de protección de aplicaciones, debe decidir qué restricciones colocará en los datos corporativos de una aplicación determinada. Se recomienda que revise cómo funcionan las [directivas de protección de aplicaciones](../apps/app-protection-policy.md). A continuación se muestra un ejemplo de cómo documentar las aplicaciones existentes y qué protección se necesita.

| **Aplicación** | **Finalidad** | **Plataformas** | **Caso de uso** | **Directiva de protección de aplicaciones** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Available | iOS | Corporativo: ejecutivos | No puede descodificarse, archivos cifrados |                                                         
| Word | Available | iOS, Android - Samsung Knox, no-Knox, Windows 10 Mobile | Corporativo, BYOD | No puede descodificarse, archivos cifrados |                                                         


Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar los requisitos de la directiva de protección de aplicaciones.
#### <a name="compliance-policies"></a>Directivas de cumplimiento

Las directivas de cumplimiento determinan si un dispositivo se adapta a determinados requisitos. Intune usa directivas de cumplimiento para determinar si un dispositivo se considera compatible o no compatible. El estado de cumplimiento puede usarse para restringir o permitir el acceso a los recursos de la empresa. Si se requiere el acceso condicional, se recomienda diseñar una [directiva de cumplimiento de dispositivos](../protect/device-compliance-get-started.md).

Consulte los requisitos y los casos de uso para determinar cuántas directivas de cumplimiento de dispositivos necesita y qué grupos de usuarios son los grupos de usuarios de destino. Además, debe decidir cuánto tiempo puede estar sin conexión un dispositivo sin registrarse antes de que se considere no compatible.

A continuación se muestra un ejemplo de cómo diseñar una directiva de cumplimiento:

| **Nombre de la directiva** | **Plataforma de dispositivo** | **Configuración** | **Grupo de destino** |
|:---:|:---:|:---:|:---:|
| Directiva de cumplimiento | iOS, Android - Samsung Knox, no-Knox, Windows 10 Mobile | PIN: requerido, no puede descodificarse | Corporativo, BYOD |


Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar los requisitos de la directiva de cumplimiento.
#### <a name="conditional-access-policies"></a>Directivas de acceso condicional

El acceso condicional se usa para permitir que solo los dispositivos compatibles tengan acceso al correo electrónico y a otros recursos de la empresa. Intune trabaja con Enterprise Mobility + Security (EMS) para controlar el acceso a los recursos de la empresa. Decida si necesita el acceso condicional y qué debe protegerse. Más información sobre el [acceso condicional](../protect/conditional-access.md).

Para el acceso en línea, decida a qué plataformas y a qué grupos de usuarios se dirigirán las directivas de acceso condicional. Determine también si necesita instalar o configurar el conector de Intune para Exchange local: 

- [Exchange local](../protect/exchange-connector-install.md)

Aquí se muestra un ejemplo de cómo documentar las directivas de acceso condicional:

| **Servicio** | **Plataformas de la autenticación moderna** | **Autenticación básica** | **Casos de uso** |
|:---:|:---:|:---:|:---:|
| Intercambio en línea | iOS, Android | Bloquear los dispositivos no compatibles de las plataformas que admite Intune | Corporativo, BYOD |
| SharePoint Online | iOS, Android |  | Corporativo, BYOD |

Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar los requisitos de la directiva de acceso condicional.

## <a name="next-steps"></a>Pasos siguientes

En la siguiente sección se proporcionan instrucciones sobre el [proceso de implementación de Intune](planning-guide-onboarding.md).
