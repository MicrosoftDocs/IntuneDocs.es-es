---
title: "Crear un diseño de Intune | Microsoft Docs"
description: "Este artículo le ayuda a crear un diseño para una implementación y diseño solo en la nube de Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6df87e20011f20b99b91d88e669c67bb97ad2277
ms.openlocfilehash: 1768b98cdcb18b5489d9a30b8c1f455f5de58418
ms.lasthandoff: 03/13/2017


---

# <a name="create-an-intune-design"></a>Crear un diseño de Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

La sección de la guía debe usarse en paralelo con otros temas de la sección 2. Este diseño se basará en la información que ha recopilado y en las decisiones que ha tomado al completar las secciones anteriores de esta guía. En esta sección de diseño, nos centraremos en Intune independiente, que es un servicio basado en la nube de Microsoft.

Aunque existen requisitos mínimos de infraestructura local, trabaje en un plan de diseño para asegurarse de que tendrá la solución de administración de dispositivos móviles correcta que cumpla sus metas, objetivos y requisitos.

Además, es normal tener cambios de diseño durante la implementación y fases de pruebas, por lo que asegúrese de documentar estos cambios y el razonamiento subyacente a medida que se produzcan. Trataremos las siguientes áreas:

-   El entorno actual

-   Las opciones de implementación de Intune

-   Los requisitos de identidad para las dependencias externas

-   Consideraciones de la plataforma de dispositivos

-   Requisitos que se van a proporcionar  

Revisemos cada una de estas áreas con más detalle. 

## <a name="record-your-environment"></a>Registrar el entorno

El primer paso antes de crear su diseño es registrar el entorno actual. El entorno actual puede influir en las decisiones de diseño y debe documentarse y hacerse referencia al tomar otras decisiones de diseño de Intune. A continuación se muestran algunos ejemplos de cómo registrar el entorno actual:

-   **Identidad en la nube**

    -   ¿Usa DirSync o Azure Active Directory (AAD) Connect?

    -   ¿Su entorno está federado?

    -   ¿Está habilitada la autenticación multifactor?

-   **Entorno del correo electrónico**

    -   ¿Se está usando Exchange, local o en la nube?

    -   ¿Se encuentra en el medio de un proyecto para migrar Exchange a la nube?

-   **Solución MDM actual**

    -   ¿Está usando actualmente otras soluciones MDM?

    -   ¿Qué soluciones MDM está usando para los escenarios de casos de uso BYOD y de la empresa?

    -   ¿Qué características está usando (por ejemplo, configuración de dispositivos de aplicaciones, configuraciones Wi-Fi, etc.)?

    -   ¿Qué plataformas de dispositivos se admiten?

    -   ¿Qué grupos y cuántos usuarios están usando la solución MDM?

-   **Solución de certificado**

    -   ¿Ha implementado una solución de certificado?

    -   ¿Qué tipo de certificado usa?

-   **Administración de sistemas**

    -   ¿Cómo está administrando su PC y el entorno del servidor?

    -   ¿Está usándose System Center Configuration Manager? ¿Está usando una plataforma de administración de sistemas de terceros?

-   **Solución de VPN**

    -   ¿Cuál es su solución de VPN?

    -   ¿Se usa para escenarios de casos de uso BYOD y de la empresa?

Asegúrese de anotar cualquier proyecto o cualquier otro plan que podría realizar cambios en su entorno al registrar el entorno MDM actual. A continuación se muestra un ejemplo de una manera de registrar el entorno actual para ayudar en la creación de su diseño de Intune:

| **Área de solución** | **Entorno actual** | **Comentarios** |
|:---:|:---:|:---:|
| **Identidad** | Azure AD, Azure AD Connect, no federado, no MFA | Proyecto para habilitar MFA a finales de año |                 
| **Entorno del correo electrónico** | Exchange Online, Exchange local | Migrando actualmente de Exchange local a Exchange Online. 75 % de buzones migrados. El último 25 % se migrará antes de que comience el piloto de Intune. |                
| **SharePoint** | SharePoint local | Ningún plan para moverse a SharePoint Online |  
| **MDM actual** | Exchange ActiveSync |  |
| **Solución de certificado** | Microsoft Server 2012 R2, Servicios de certificado de AD | Solo se usa PKI en servidores de sitio web |
| **Administración de sistemas** | System Center Configuration Manager CB 1606 | Le gustaría investigar una solución híbrida de Intune |
| **Solución de VPN** | Cisco AnyConnect |  |

## <a name="choose-an-intune-deployment-option"></a>Elegir una opción de implementación de Intune

Intune ofrece dos opciones de implementación: independiente e híbrida. Necesitará decidir cuál se adapta a los requisitos de su empresa. Independiente se refiere al servicio de Intune que se ejecuta en la nube, híbrida se refiere a la integración de Intune con System Center Configuration Manager.

- Más información sobre cómo [elegir entre Microsoft Intune independiente y la administración de dispositivos móviles híbrida con System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)

## <a name="intune-tenant-location"></a>Ubicación del inquilino de Intune

Si su organización tiene una presencia global, asegúrese de planear dónde se encontrará su inquilino al suscribirse al servicio. El país se define cuando se registra en una suscripción de Intune la primera vez, y se asignan las regiones del mundo que se muestran a continuación:

-   América del Norte

-   Europa, Oriente Medio y África

-   Asia y Pacífico

>[!IMPORTANT]
> No es posible cambiar el país o la ubicación del inquilino posteriormente.

## <a name="external-dependencies"></a>Dependencias externas

Las dependencias externas son servicios y productos que son independientes de Intune pero son un requisito de este o pueden integrarse en él. Es importante identificar los requisitos de cualquier dependencia externa y cómo se configurará. A continuación se muestran algunos ejemplos de dependencias externas comunes.

-   Identidad

-   Grupos de usuarios y dispositivos

-   PKI

Vamos a explorar con más detalle estas dependencias externas comunes a continuación.

### <a name="identity"></a>Identidad

Identidad es la manera en que se identifica a los usuarios que pertenecen a la organización y que se inscriben en un dispositivo. Intune requiere Azure Active Directory (Azure AD) como el proveedor de identidades de usuario. Si ya usa este servicio, ya podrá aprovechar su identidad existente en la nube. Además, Azure AD Connect es la herramienta recomendada para sincronizar sus identidades de usuario locales con los servicios en la nube de Microsoft. Si su organización ya está usando Office 365, es importante que Intune use el mismo entorno de Azure Active Directory.

Puede encontrar más información sobre los requisitos de identidad de Intune a continuación.

-   Más información sobre los [requisitos de identidad](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview).

-   Más información sobre los [requisitos de sincronización de directorios](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements).

-   Más información sobre los [requisitos de Multi-factor Authentication](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements).

### <a name="user-and-device-groups"></a>Grupos de usuarios y dispositivos

Grupos de usuarios y dispositivos determina el destino de una implementación. Esto puede incluir el destino de la implementación de directivas, aplicaciones y perfiles. La nube de Intune solo admite grupos de usuarios y dispositivos; necesitará determinar qué grupos de usuarios y dispositivos se requerirán. Se recomienda que todos los grupos se creen en Active Directory local y, después, se sincronicen en Azure Active Directory. Puede encontrar más información sobre la creación y planeación de grupos de usuarios y dispositivos a continuación.

-   Más información sobre la [planeación de grupos de usuarios y dispositivos](https://docs.microsoft.com/intune/deploy-use/plan-your-user-and-device-groups).

-   Más información sobre [cómo crear grupos de usuarios y dispositivos](https://docs.microsoft.com/en-us/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

### <a name="public-key-infrastructure-pki"></a>Infraestructura de clave pública (PKI)

Infraestructura de clave pública proporciona certificados a los dispositivos o usuarios para autenticarse de manera segura en un servicio. Intune admite una infraestructura de PKI de Microsoft. Los certificados de usuarios y dispositivos pueden emitirse en un dispositivo móvil para satisfacer los requisitos de autenticación basados en certificados. Antes de implementar los certificados, necesita determinar si estos son necesarios, si la infraestructura de red puede admitir la autenticación basada en certificados y si los certificados se usan actualmente en el entorno existente.

Si está planeando usar certificados con perfiles de VPN, Wi-Fi o correo electrónico con Intune, necesita asegurarse de que tiene una [infraestructura de PKI](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles) admitida y lista para crear e implementar perfiles de certificado.

Además, si se van a emitir certificados SCEP, necesita determinar qué servidor hospedará la característica del Servicio de inscripción de dispositivos de red (NDES) y cómo se producirá la comunicación.

Más información sobre la configuración de certificados en Intune:

-   [Cómo configurar la infraestructura de certificados para SCEP](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep).

-   [Cómo configurar la infraestructura de certificados para PFX](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-pfx).

-   [Cómo configurar perfiles de certificado de Intune](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles).

-   [Cómo configurar directivas de acceso de recursos](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

## <a name="device-platform-considerations"></a>Consideraciones de la plataforma de dispositivos

Necesita una visión más detallada de sus dispositivos para entender cómo funcionan correctamente.

-   Determinar las plataformas de dispositivos compatibles

-   Dispositivos

-   Propiedad del dispositivo

-   Inscripción masiva

Revisemos estas áreas con más detalle.

### <a name="determine-supported-device-platforms"></a>Determinar las plataformas de dispositivos compatibles

Necesita saber qué dispositivos estarán en el entorno y comprobar si son compatibles o no con Intune al crear su diseño. Intune admite plataformas de iOS, Android y Windows.

-   Más información sobre [los dispositivos compatibles con Intune](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers).

### <a name="devices"></a>Dispositivos

Intune administra dispositivos móviles para proteger los datos corporativos y permitir que los usuarios finales trabajen desde más ubicaciones. Intune admite varias plataformas de dispositivos, por lo que se recomienda documentar los dispositivos y las plataformas de sistema operativo que se admitirán en el diseño de su organización. Esto se ampliará en los dispositivos y plataformas que se crean en la sección (requisitos de casos de uso).

También se recomienda conocer las versiones para hacer referencia a la lista a la hora de comprobar las características de los dispositivos por versión y plataforma de sistema operativo. Aquí tenemos un ejemplo:

| **Plataforma de dispositivo** | **Versiones del sistema operativo** |
|:---:|:---:|
| iOS: iPhone | 9.0+ |                
| iOS: iPad | 8.0+ |               
| Android: Samsung KNOX Standard | 4.0+ |
| Tableta de Windows 10 | 10+ |

### <a name="device-ownership"></a>Propiedad del dispositivo

Intune admite la propiedad BYOD y la propiedad de la empresa. Un dispositivo se considera de propiedad de la empresa si está inscrito por un administrador de inscripción de dispositivos, o por un programa de inscripción de dispositivos. Como ejemplo, un dispositivo puede inscribirse mediante DEP de Apple, marcarse como corporativo, y colocarse en un grupo de dispositivos que recibe aplicaciones y directivas corporativas de destino.

Consulte la [Sección 3: Determinar los requisitos de los escenarios de casos de uso](section-3-determine-use-case-requirements.md) para obtener más información sobre los casos de uso BYOD y de la empresa.

### <a name="bulk-enrollment"></a>Inscripción masiva

Existen varias opciones de inscripción disponibles para la inscripción de un dispositivo en Intune para complementar la inscripción de autoservicio mediante el portal de empresa. La inscripción masiva puede realizarse de diferentes maneras dependiendo de la plataforma. Si se necesita la inscripción masiva, primero determine el método de inscripción masiva e incorpórelo a su diseño. Puede encontrar más información sobre los diferentes métodos de inscripción masiva a continuación.

-   Más información sobre la [inscripción masiva](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).

## <a name="feature-requirements"></a>Requisitos de características

En estas secciones, revisaremos las siguientes funciones y características que se adaptan a los requisitos de escenarios de casos de uso:

-   Directivas de términos y condiciones

-   Directivas de configuración

-   Perfiles de recursos

-   Aplicaciones

-   Directiva de cumplimiento

-   Acceso condicional

Revisemos cada una de estas áreas con más detalle.

### <a name="terms-and-conditions-policies"></a>Directivas de términos y condiciones

Los términos y condiciones pueden usarse para explicar directivas o condiciones que un usuario final debe aceptar antes de la inscripción. Intune admite la capacidad de agregar e implementar varias directivas de términos y condiciones a los grupos de usuarios. Necesita determinar si se necesitan las directivas de términos y condiciones. De ser así, determine quién será el responsable de proporcionar esta información en la organización.

-   Obtenga información sobre [cómo crear directivas de términos y condiciones](https://docs.microsoft.com/intune/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune) en Intune. A continuación se muestra un ejemplo de cómo documentar la directiva de términos y condiciones.

| **Nombre de los términos y condiciones** | **Caso de uso** | **Grupo de destino** |
|:---:|:---:|:---:|
| Términos y condiciones corporativos | Corporativos | Usuarios corporativos |                 
| Términos y condiciones BYOD | BYOD | Usuarios BYOD |                

### <a name="configuration-policies"></a>Directivas de configuración

Las directivas de configuración se usan para administrar las características y la configuración de seguridad en un dispositivo. Al diseñar las directivas de configuración, consulte la sección de los requisitos de casos de uso para determinar las configuraciones necesarias para los dispositivos de Intune. Documente qué configuración y cómo debe configurarse, también documente a qué usuarios o grupos de dispositivos se aplicarán.

Debe crear al menos una directiva de configuración por plataforma. Puede crear varias directivas de configuración por plataforma si es necesario. A continuación se muestra un ejemplo del diseño de cuatro directivas de configuración diferentes para plataformas y escenarios de casos de uso distintos.

| **Nombre de la directiva** | **Plataforma de dispositivo** | **Configuración** | **Grupo de destino** |   
|:---:|:---:|:---:|:---:|
| Corporativo: iOS | iOS | Se necesita PIN, longitud: 6, restringir copia de seguridad en la nube | Dispositivos corporativos |                                                           
| Corporativo: Android | Android | Se necesita PIN, longitud: 6, restringir copia de seguridad en la nube | Dispositivos corporativos |                                                           
| BYOD: iOS  | iOS | Se necesita PIN, longitud: 4 | Dispositivos BYOD |
| BYOD: Android  | Android | Se necesita PIN, longitud: 4 | Dispositivos BYOD |

### <a name="profiles"></a>Profiles

Los perfiles se usan para ayudar al usuario final a conectarse a los datos de la empresa. Intune admite muchos tipos de perfiles. Consulte los requisitos y los casos de uso para determinar cuándo se configurarán los [perfiles](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune). Todos los perfiles de dispositivos están clasificados por tipo de plataforma, y deben incluirse en la documentación de diseño.

-   Perfiles de certificado

-   Perfil de Wi-Fi

-   Perfil de VPN

-   Perfil de correo electrónico

Revisemos cada tipo de perfil con más detalle.

##### <a name="certificate-profiles"></a>Perfiles de certificado

Los perfiles de certificado permiten que Intune emita un certificado para un usuario o dispositivo. Intune admite lo siguiente:

-   Protocolo de inscripción de certificados simple (SCEP)

-   Certificado de raíz de confianza

-   Certificado PFX.

Se recomienda que documente qué grupo de usuarios necesita un certificado, cuántos perfiles de certificado se necesitarán y en qué grupos de usuarios se van a implementar.

>[!NOTE]
> Recuerde que se necesita el certificado de raíz de confianza para el certificado SCEP, de manera que asegúrese de que todos los usuarios destinados al certificado SCEP también reciben un certificado de raíz de confianza. Si se necesitan los certificados SCEP, diseñe y documente qué plantillas de certificado SCEP se van a necesitar.

Aquí se muestra un ejemplo de cómo puede documentar los certificados durante el diseño:

| **Tipo** | **Nombre de perfil** | **Plataforma de dispositivo** | **Casos de uso** |   
|:---:|:---:|:---:|:---:|
| CA raíz | CA raíz corporativo | Android, iOS, Windows Mobile | Corporativo, BYOD  |                                                           
| SCEP | Certificado de usuario | Android, iOS, Windows Mobile | Corporativo, BYOD |                                                           

##### <a name="wi-fi-profile"></a>Perfil de Wi-Fi

Los perfiles de Wi-Fi se usan para conectar automáticamente un dispositivo móvil a una red inalámbrica. Intune admite la implementación de perfiles de Wi-Fi en todas las plataformas compatibles.

-   Más información sobre [cómo Intune admite los perfiles de Wi-Fi](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune).

A continuación se muestra un ejemplo de un diseño de un perfil de Wi-Fi:

| **Tipo** | **Nombre de perfil** | **Plataforma de dispositivo** | **Casos de uso** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | Perfil de Wi-Fi de Asia | Android | Corporativo, región de Asia BYOD|                                                           
| Wi-Fi | Perfil de Wi-Fi de América del Norte | Android, iOS, Windows 10 Mobile | Corporativo, región de América del Norte BYOD |                                                           

##### <a name="vpn-profile"></a>Perfil de VPN

Los perfiles de VPN permiten que los usuarios accedan de manera segura a su red desde ubicaciones remotas. Intune admite los perfiles de VPN desde conexiones de VPN móviles nativas y proveedores de terceros.

-   Más información sobre los [perfiles de VPN y los proveedores admitidos por Intune](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune).

A continuación se muestra un ejemplo de la documentación del diseño de un perfil de VPN.

| **Tipo** | **Nombre de perfil** | **Plataforma de dispositivo** | **Casos de uso** |   
|:---:|:---:|:---:|:---:|
| VPN | Perfil de cualquier conexión de VPN Cisco | Android, iOS, Windows 10 Mobile | Corporativo, América del Norte y Alemania BYOD|                                                           
| VPN | Pulse Secure | Android | Corporativo, región de Asia BYOD |                                                           

##### <a name="email-profile"></a>Perfil de correo electrónico

Los perfiles de correo electrónico permiten que un cliente de correo se configure automáticamente con la información de conexión y la configuración del correo electrónico de instalación. Intune admite los perfiles de correo electrónico en algunos dispositivos.

-   Más información sobre los [perfiles de correo electrónico](https://docs.microsoft.com/en-us/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) y qué plataformas son compatibles.

A continuación se muestra un ejemplo de la documentación del diseño de perfiles de correo electrónico:

| **Tipo** | **Nombre de perfil** | **Plataforma de dispositivo** | **Casos de uso** |   
|:---:|:---:|:---:|:---:|
| Perfil de correo electrónico | Perfil de correo electrónico iOS | iOS | Corporativo: trabajador de la información BYOD |                                                           
| Perfil de correo electrónico | Perfil de correo electrónico Android KNOX | Android KNOX | BYOD |

### <a name="apps"></a>Aplicaciones

Intune admite la entrega de aplicaciones a los usuarios o dispositivos de varias maneras. El tipo de aplicación que se entrega puede ser aplicaciones de instalador de software, aplicaciones de una tienda de aplicaciones pública, vínculos externos o aplicaciones iOS administradas. Además de las implementaciones de aplicaciones individuales, las aplicaciones adquiridas por volumen pueden administrarse e implementarse mediante los programas de compra por volumen para iOS y Windows. A continuación se encuentra información sobre cómo Intune admite aplicaciones y programas de compra por volumen.

-   Más información sobre los [tipos de aplicaciones](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)

-   Más información sobre el [Programa de Compras por Volumen de iOS para empresas (PCV](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)).

-   Más información sobre la [Tienda Windows para empresas](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune).

#### <a name="app-type-requirements"></a>Requisitos del tipo de aplicación

Como las aplicaciones pueden implementarse en usuarios y dispositivos, se recomienda decidir qué aplicaciones administrará Intune. Mientras se recopila la lista, intente responder a las siguientes preguntas:

-   ¿Las aplicaciones requieren integración con servicios en la nube?

-   ¿Las aplicaciones estarán disponibles para los usuarios BYOD?

-   ¿Cuáles son las opciones de implementación disponibles de estas aplicaciones?

-   ¿Su empresa necesita proporcionar acceso a datos de aplicaciones de software como servicio (SaaS) para sus partners?

-   ¿Las aplicaciones requieren que se acceda a Internet desde los dispositivos de los usuarios?

-   ¿Las aplicaciones están disponibles públicamente en una tienda de aplicaciones o son aplicaciones de línea de negocio personalizadas?


>[!TIP]
> Consulte los [diferentes tipos de aplicaciones compatibles con Intune](https://docs.microsoft.com/intune/deploy-use/add-apps).

#### <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

Las directivas de protección de aplicaciones minimizan la pérdida de datos definiendo cómo administra la aplicación los datos corporativos. Intune admite las directivas de protección de aplicaciones para cualquier aplicación compilada para funcionar con la administración de aplicaciones móviles. Al diseñar la directiva de protección de aplicaciones, necesita determinar qué restricciones colocará en los datos corporativos de una aplicación determinada. Se recomienda que revise cómo funcionan las [directivas de protección de aplicaciones](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune). A continuación se muestra un ejemplo de cómo documentar las aplicaciones existentes y qué protección se necesita.

| **Aplicación** | **Finalidad** | **Plataformas** | **Caso de uso** | **Directiva de protección de aplicaciones** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Available | iOS | Corporativo: ejecutivos | No puede descodificarse, archivos cifrados |                                                         
| Word | Available | iOS, Android - Samsung Knox, no-Knox, Windows 10 Mobile | Corporativo, BYOD | No puede descodificarse, archivos cifrados |                                                         

#### <a name="compliance-policies"></a>Directivas de cumplimiento

Las directivas de cumplimiento determinan si un dispositivo se adapta a determinados requisitos. Intune usa directivas de cumplimiento para determinar si un dispositivo se considera compatible o no compatible. El estado de cumplimiento puede usarse para restringir el acceso a los recursos de la empresa. Si se requiere el acceso condicional, se recomienda diseñar una [directiva de cumplimiento de dispositivos](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune). Consulte los requisitos y los casos de uso para determinar cuántas directivas de cumplimiento de dispositivos son necesarias y qué grupos de usuarios son los grupos de usuarios de destino. Además, necesita determinar cuánto tiempo puede estar sin conexión un dispositivo sin realizar la comprobación antes de que se considere no compatible.

A continuación se muestra un ejemplo de cómo diseñar una directiva de cumplimiento:

| **Nombre de la directiva** | **Plataforma de dispositivo** | **Configuración** | **Grupo de destino** |   
|:---:|:---:|:---:|:---:|
| Directiva de cumplimiento | iOS, Android - Samsung Knox, no-Knox, Windows 10 Mobile | PIN: requerido, no puede descodificarse | Corporativo, BYOD |

#### <a name="conditional-access-policies"></a>Directivas de acceso condicional

El acceso condicional se usa para permitir solo los dispositivos compatibles para acceder a los recursos de la empresa. Intune trabaja con Enterprise Mobility + Security (EMS) al completo para controlar el acceso a los recursos de la empresa. Necesitará determinar si se necesita el acceso condicional y qué debe protegerse.

-   Más información sobre el [acceso condicional](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

Para el acceso en línea, determine qué plataformas y a qué grupos de usuarios se dirigirán las directivas de acceso condicional.

Además, necesita determinar si necesita instalar o configurar el conector de servicio a servicio de Intune para Exchange Online o Exchange local.

Más información sobre cómo instalar y configurar los conectores de servicio a servicio de Intune:

-   [Exchange Online](https://docs.microsoft.com/intune/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange local](https://docs.microsoft.com/intune/deploy-use/intune-on-premises-exchange-connector)

Aquí se muestra un ejemplo de cómo documentar las directivas de acceso condicional:

| **Servicio** | **Plataformas de la autenticación moderna** | **Autenticación básica** | **Casos de uso** |   
|:---:|:---:|:---:|:---:|
| Intercambio en línea | iOS, Android | Bloquear los dispositivos no compatibles de las plataformas que admite Intune | Corporativo, BYOD |
| SharePoint Online | iOS, Android |  | Corporativo, BYOD |

## <a name="next-section"></a>Sección siguiente

En la siguiente sección se proporcionan instrucciones sobre el [proceso de implementación de Intune](section-8-onboarding-process.md).

