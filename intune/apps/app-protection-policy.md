---
title: Introducción general a las directivas de protección de aplicaciones
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo las directivas de protección de aplicaciones de Microsoft Intune ayudan a proteger los datos de su empresa y evitan la pérdida de datos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2d8d50f7ac5d79d4d0081e7eee2169e9ff45d49
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512082"
---
# <a name="app-protection-policies-overview"></a>Introducción general a las directivas de protección de aplicaciones

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Las directivas de protección de aplicaciones (APP) que garantizan los datos de la organización siguen siendo seguras o se encuentran en una aplicación administrada. Una directiva puede ser una regla que se aplica cuando el usuario intenta obtener acceso o mover datos "corporativos" o un conjunto de acciones que están prohibidas o que se supervisan cuando el usuario está dentro de la aplicación. Una aplicación administrada es aquella que tiene las directivas de protección de aplicaciones aplicadas y puede administrarse mediante Intune.

Las directivas de protección de aplicaciones de Administración de aplicaciones móviles (MAM) le permiten administrar y proteger los datos de su organización dentro de una aplicación. Con **MAM sin inscripción** (MAM-WE), una aplicación profesional o educativa que contiene información confidencial puede administrarse en casi cualquier [dispositivo](app-management.md#app-management-capabilities-by-platform), incluidos los dispositivos personales en escenarios de **Bring Your Own Device** (BYOD). Muchas aplicaciones de productividad, como las aplicaciones de Microsoft Office, pueden administrarse mediante Intune MAM. Consulte la lista oficial de [aplicaciones protegidas de Microsoft Intune](apps-supported-intune-apps.md), disponible para uso público.

## <a name="how-you-can-protect-app-data"></a>Cómo puede proteger los datos de la aplicación
Los empleados usan dispositivos móviles para tareas personales y de trabajo. Mientras se asegura de que los empleados pueden ser productivos, puede evitar la pérdida de datos, ya sea intencional o involuntaria. También conviene proteger los datos de empresa que son accesibles desde dispositivos que no están administrados por usted.

Puede usar directivas de protección de aplicaciones de Intune **independientemente de cualquier otra solución de administración de dispositivos móviles (MDM)**. Esta independencia le ayuda a proteger los datos de su empresa con o sin inscripción de dispositivos en una solución de administración de dispositivos. Mediante la implementación de **directivas de nivel de aplicación**, puede restringir el acceso a los recursos de la empresa y mantener los datos dentro del ámbito del departamento de TI.

### <a name="app-protection-policies-on-devices"></a>Directivas de protección de aplicaciones en dispositivos

Se pueden configurar directivas de protección de aplicaciones para aplicaciones que se ejecutan en dispositivos:

- **Inscritos en Microsoft Intune:** estos dispositivos suelen ser propiedad de la empresa.

- **Inscritos en una solución de administración de dispositivos móviles (MDM) de terceros:** estos dispositivos suelen ser propiedad de la empresa.

  > [!NOTE]
  > Las directivas de administración de la aplicaciones móviles no deben usarse con soluciones de contenedor seguro ni de administración de aplicaciones móviles de terceros.

- **No inscritos en ninguna solución de administración de dispositivos móviles:** Estos dispositivos normalmente son dispositivos de empleados que no están administrados ni inscritos en Intune ni en ninguna otra solución MDM.

> [!IMPORTANT]
> Puede crear directivas de administración de aplicaciones móviles para aplicaciones móviles de Office que se conectan a servicios de Office 365. También puede proteger el acceso a los buzones locales de Exchange mediante la creación de directivas de protección de aplicaciones de Intune para Outlook para iOS/iPadOS y Android habilitadas con autenticación moderna híbrida. Antes de usar esta característica, asegúrese de cumplir los [requisitos de Outlook para iOS/iPadOS y Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Las directivas de protección de aplicaciones no son compatibles con otras aplicaciones que se conectan a los servicios de Exchange o SharePoint locales.

## <a name="benefits-of-using-app-protection-policies"></a>Ventajas del uso de directivas de protección de aplicaciones

Las ventajas más importantes del uso de directivas de protección de aplicaciones son las siguientes:

- **Protección de datos de su compañía a nivel de aplicación.** Puesto que la administración de aplicaciones móviles no requiere la administración de dispositivos, puede proteger los datos de la empresa en dispositivos administrados y no administrados. La administración se centra en la identidad del usuario, lo que elimina la necesidad de administrar dispositivos.

- **La productividad del usuario final no se ve afectada y no se aplican las directivas cuando se usa la aplicación en un contexto personal.** Las directivas se aplican solo en un contexto de trabajo, lo que le ofrece la capacidad de proteger los datos de la compañía sin tocar los datos personales.

- **Las directivas de protección de aplicaciones garantizan que las protecciones de la capa de aplicaciones estén establecidas.** Por ejemplo, puede:
  - Solicitar un PIN para abrir una aplicación en un contexto de trabajo 
  - Controlar el uso compartido de datos entre aplicaciones 
  - Impedir el almacenamiento de datos de la aplicación de empresa en una ubicación de almacenamiento personal

- **MDM, además de MAM, garantiza que el dispositivo esté protegido**. Por ejemplo, puede solicitar un PIN para acceder al dispositivo o puede implementar aplicaciones administradas en el dispositivo. También puede implementar aplicaciones en dispositivos a través de la solución MDM para proporcionarle más control sobre la administración de aplicaciones.

Hay otras ventajas derivadas del uso de MDM con directivas de protección de aplicaciones, y las empresas pueden usar estas directivas con o sin MDM al mismo tiempo. Por ejemplo, piense el caso de un empleado que utiliza tanto un teléfono proporcionado por la empresa como su propia tableta personal. El teléfono de la empresa está inscrito en MDM y está protegido por directivas de protección de aplicaciones, mientras que el dispositivo personal está protegido únicamente por directivas de protección de aplicaciones.

Si aplica una directiva de MAM al usuario sin establecer el estado del dispositivo, el usuario recibirá la directiva de MAM en el dispositivo BYOD y el dispositivo administrado por Intune. También puede aplicar una directiva de MAM según el estado administrado. Por lo tanto, cuando cree una directiva de protección de aplicaciones, debería seleccionar **No** junto a **Destinar a todos los tipos de aplicaciones**. Luego, realice cualquiera de las siguientes acciones:
- Aplique una directiva de MAM menos estricta a los dispositivos administrados por Intune y aplique una más estricta a los dispositivos no inscritos en MDM.
- Aplique una directiva de MAM solo a los dispositivos no inscritos.

## <a name="supported-platforms-for-app-protection-policies"></a>Plataformas admitidas para directivas de protección de aplicaciones

Intune ofrece diversas funcionalidades para ayudarle a conseguir las aplicaciones que necesita en los dispositivos en los que desea que se ejecuten. Para obtener más información, consulte [Funcionalidades de administración de aplicaciones por plataforma](app-management.md#app-management-capabilities-by-platform).

La compatibilidad de plataformas de directivas de aplicaciones de Intune está alineada con la compatibilidad de plataformas de aplicaciones móviles de Office para dispositivos Android e iOS/iPadOS. Para obtener más información, consulte la sección **Aplicaciones móviles** de [Requisitos del sistema de Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> Es necesario que el Portal de empresa de Intune se encuentre en el dispositivo para recibir las directivas de protección de aplicación en Android. Para más información, consulte los [requisitos de las aplicaciones de acceso al Portal de empresa de Intune](../fundamentals/end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Protección de datos de una aplicación con directivas de protección de aplicaciones

### <a name="apps-without-app-protection-policies"></a>Aplicaciones sin directivas de protección de aplicaciones

Cuando se usan aplicaciones sin restricciones, se pueden entremezclar los datos empresariales y personales. Los datos de la compañía pueden acabar en ubicaciones como el almacenamiento personal o transferirse a aplicaciones fuera de su ámbito y provocar una pérdida de datos. Las flechas del diagrama siguiente muestran el movimiento sin restricciones de los datos entre aplicaciones (personales y corporativas) y hacia ubicaciones de almacenamiento.

![Imagen conceptual de movimiento de datos entre aplicaciones sin ninguna directiva en vigor](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>Protección de datos con directivas de protección de aplicaciones (APP)

Puede usar directivas de protección de aplicaciones para evitar que los datos de empresa se guarden en el almacenamiento local del dispositivo (consulte la imagen a continuación). También puede restringir el movimiento de datos a otras aplicaciones que no estén protegidas por directivas de protección. La configuración de directivas de protección de aplicaciones incluyen:
- Las directivas de reubicación de datos como **Guardar copias de los datos de la organización** y **Restringir funciones Cortar, Copiar y Pegar**.
- Opciones de directivas de acceso como **Requerir PIN sencillo para el acceso**, **Bloquear las aplicaciones administradas para que no se ejecuten en dispositivos con jailbreak o rooting**.

![Imagen conceptual que muestra la datos de la compañía protegidos por directivas](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>Protección de datos con APP en dispositivos administrados por una solución MDM

En la ilustración siguiente se muestran las capas de protección que ofrecen juntas las directivas MDM y las directivas de protección de aplicaciones.

![Imagen que muestra cómo funcionan las directivas de protección de aplicaciones en dispositivos BYOD.](./media/app-protection-policy/app-protection-policies-with-mdm.png)

La solución MDM agrega valor al proporcionar lo siguiente:

- Inscribe el dispositivo.
- Implementa las aplicaciones en el dispositivo
- Proporciona administración y conformidad continua de los dispositivos

Las directivas de protección de aplicaciones agregan valor al proporcionar lo siguiente:

- Ayudan a evitar la fuga de datos de la compañía a aplicaciones y servicios de consumidor.
- Aplican restricciones (*Guardar como*, *Portapapeles*, *PIN*, etc.) a las aplicaciones cliente.
- Borran datos de compañía de las aplicaciones cuando es necesario sin borrar esas aplicaciones del dispositivo.

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>Protección de datos con APP para dispositivos sin inscripción

En el diagrama siguiente se muestra cómo funcionan las directivas de protección de datos en el nivel de aplicación sin MDM.

![Imagen que muestra cómo funcionan las directivas de protección de aplicaciones sin inscripción (dispositivos no administrados)](./media/app-protection-policy/app-protection-policies-without-mdm.png)

En dispositivos BYOD no inscritos en ninguna solución MDM, las directivas de protección de aplicaciones pueden ayudar a proteger los datos de la compañía a nivel de aplicación.
Sin embargo, existen algunas limitaciones que se deben tener en cuenta, como:

- No se puede implementar aplicaciones en el dispositivo. El usuario final debe obtener las aplicaciones del almacén.
- No se puede proporcionar perfiles de certificados en estos dispositivos.
- No se puede proporcionar configuraciones de Wi-Fi y VPN de compañía en estos dispositivos.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplicaciones que puede administrar con directivas de protección de aplicaciones

Cualquier aplicación integrada con el [SDK de Intune](../developer/app-sdk.md) o ajustada mediante la [herramienta de ajuste de aplicaciones de Intune](../developer/apps-prepare-mobile-application-management.md) puede administrarse con las directivas de protección de aplicaciones de Intune. Consulte la lista oficial de [aplicaciones protegidas de Microsoft Intune](apps-supported-intune-apps.md) que se han creado con estas herramientas y están disponibles para uso público.

El equipo de desarrollo del SDK de Intune comprueba y mantiene de forma activa la compatibilidad con las aplicaciones creadas con las plataformas nativas de Android, iOS/iPadOS (Obj-C, Swift), Xamarin, Xamarin.Forms y Cordova. Aunque algunos clientes han podido integrar con éxito el SDK de Intune con otras plataformas como React Native y NativeScript, no proporcionamos instrucciones explícitas o complementos para desarrolladores de aplicaciones que no utilicen nuestras plataformas compatibles.

El [SDK de Intune](../developer/app-sdk.md) usa algunas funcionalidades de autenticación modernas avanzadas de las [Bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) tanto para las versiones de primera entidad como para las de terceros del SDK. Por lo tanto, la [Biblioteca de autenticación de Microsoft](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (MSAL) no funciona bien con muchos de nuestros escenarios básicos, como la autenticación en el servicio de Intune App Protection y el inicio condicional. Dado que el objetivo general del equipo de identidades de Microsoft es migrar a MSAL en todas las aplicaciones de Microsoft Office, el [SDK de Intune](../developer/app-sdk.md) tendrá que admitirlo en algún momento, pero actualmente no está previsto.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>Requisitos del usuario final para utilizar directivas de protección de aplicaciones

En la siguiente lista se proporcionan los requisitos del usuario final para utilizar directivas de protección de aplicaciones en una aplicación administrada de Intune:

- El usuario final debe tener una cuenta de Azure Active Directory (AAD). Consulte [Agregar usuarios y conceder permiso administrativo a Intune](../fundamentals/users-add.md) para aprender a crear usuarios de Intune en Azure Active Directory.

- El usuario final debe tener una licencia de Microsoft Intune asignada a su cuenta de Azure Active Directory. Vea [Administrar licencias de Intune](../fundamentals/licenses-assign.md) para obtener información sobre cómo asignar licencias de Intune a los usuarios finales.

- El usuario final debe pertenecer a un grupo de seguridad de destino de una directiva de protección de la aplicación. La misma directiva de protección de aplicaciones debe tener como destino la aplicación específica que se va a utilizar. Las directivas de protección de aplicaciones pueden crearse e implementarse en la consola de Intune en el [portal de Azure](https://portal.azure.com). Actualmente se pueden crear grupos de seguridad en el [Centro de administración de Microsoft 365](https://admin.microsoft.com).

- El usuario final debe iniciar sesión en la aplicación con su cuenta de AAD.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Directivas de protección de aplicaciones para aplicaciones de Microsoft Office

Hay algunos requisitos adicionales que es necesario tener en cuenta al utilizar directivas de protección de aplicaciones con aplicaciones de Microsoft Office.

### <a name="outlook-mobile-app"></a>Aplicación móvil de Outlook
Entre los requisitos adicionales para usar la [aplicación móvil de Outlook](https://products.office.com/outlook) se incluyen los siguientes:

- El usuario final debe tener la aplicación móvil de Outlook instalada en su dispositivo.
- El usuario final debe tener una licencia y buzón de correo de [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) vinculados a su cuenta de Azure Active Directory.

  >[!NOTE]
  > Actualmente, la aplicación móvil de Outlook solo es compatible con Intune App Protection para Microsoft Exchange Online y [Exchange Server con autenticación moderna híbrida](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) y no admite Exchange en Office 365 dedicado.

### <a name="word-excel-and-powerpoint"></a>Word, Excel y PowerPoint
Entre los requisitos adicionales para usar las aplicaciones [Word, Excel y PowerPoint](https://products.office.com/business/office) se incluyen los siguientes:

- El usuario final debe tener una licencia de [Office 365 Empresa o Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) asignada a su cuenta de Azure Active Directory. La suscripción debe incluir las aplicaciones de Office en dispositivos móviles y puede incluir una cuenta de almacenamiento en la nube con [OneDrive para la Empresa](https://onedrive.live.com/about/business/). Las licencias de Office 365 se pueden asignar en el [Centro de administración de Microsoft 365](https://admin.microsoft.com) siguiendo estas [instrucciones](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- El usuario final debe tener una ubicación administrada configurada con la funcionalidad pormenorizada Guardar como en la configuración de directiva de protección de aplicaciones "Guardar copias de los datos de la organización". Por ejemplo, si la ubicación administrada es OneDrive, la aplicación [OneDrive](https://onedrive.live.com/about/) debe estar configurada en la aplicación Word, Excel o PowerPoint del usuario final.

- Si la ubicación administrada es OneDrive, la directiva de protección de aplicaciones implementada para el usuario final debe tener como destino la aplicación.

  >[!NOTE]
  > Las aplicaciones móviles de Office actualmente solo admiten SharePoint Online y no SharePoint local.

### <a name="managed-location-needed-for-office"></a>Ubicación administrada necesaria para Office
Para Office se necesita una ubicación administrada (como OneDrive). Intune marca todos los datos de la aplicación como "empresa" o "personal". Los datos se consideran "corporativos" cuando se originan desde una ubicación de la empresa. Para las aplicaciones de Office, Intune considera las siguientes ubicaciones de la empresa: correo electrónico (Exchange) o almacenamiento en la nube (aplicación OneDrive con una cuenta de OneDrive para la Empresa).

### <a name="skype-for-business"></a>Skype Empresarial
Existen requisitos adicionales para usar Skype Empresarial. Consulte los requisitos de licencias de [Skype Empresarial](https://products.office.com/skype-for-business/it-pros). Para configuraciones híbridas y locales de Skype Empresarial, consulte [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) (La autenticación moderna híbrida para Skype Empresarial y Exchange está disponible con carácter general) y [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910) (Autenticación moderna para Skype Empresarial local con AAD), respectivamente.

## <a name="app-protection-global-policy"></a>Directiva global de protección de aplicaciones

Si un administrador de OneDrive va a **admin.office.com** y selecciona **Acceso de dispositivo**, podrá establecer los controles **Administración de aplicaciones móviles** en las aplicaciones cliente de OneDrive y SharePoint. 

La configuración, disponible en la consola de administración de OneDrive, establece una directiva de protección de aplicaciones de Intune especial llamada **Global**. Esta directiva global se aplica a todos los usuarios de su inquilino y no tiene forma de controlar los destinos de la directiva. 

Una vez habilitada, las aplicaciones de OneDrive y SharePoint para iOS/iPadOS y Android se protegen con la configuración seleccionada de forma predeterminada. Un profesional de TI puede editar esta directiva en la consola de Intune y agregar más aplicaciones de destino y modificar cualquier configuración de directiva. 

De forma predeterminada, solo puede haber una directiva **Global** por inquilino, aunque puede usar una [Graph API de Intune](../developer/intune-graph-apis.md) para crear otras directivas globales por inquilino, aunque no se recomienda, dado que puede ser complicado solucionar problemas en la implementación de esta directiva.

Si bien la directiva **Global** se aplica a todos los usuarios del inquilino, cualquier directiva estándar de protección de aplicaciones de Intune anulará esta configuración.

## <a name="app-protection-features"></a>Características de protección de aplicaciones

### <a name="multi-identity"></a>Varias identidades

La compatibilidad con varias identidades permite a una aplicación admitir varias audiencias. Estas audiencias son tanto usuarios "corporativos" como "personales". Las audiencias "corporativas" usan cuentas profesionales y educativas, mientras que las cuentas personales se utilizarían para audiencias de consumidores como, por ejemplo, los usuarios de Microsoft Office. Una aplicación que admite varias identidades se puede lanzar públicamente allí donde las directivas de protección de aplicaciones se aplican solo al usarse la aplicación en el contexto profesional y educativo ("corporativo"). La compatibilidad con varias identidades usa el [SDK de Intune](../developer/app-sdk.md) solo para aplicar las directivas de protección de aplicaciones a la cuenta profesional o educativa con la que se ha iniciado sesión en la aplicación. Si se ha iniciado sesión en la aplicación con una cuenta personal, los datos no se modifican.

Como ejemplo de contexto "personal", piense en un usuario que empieza un documento nuevo en Word: esto se considera contexto personal por lo que no se aplican las directivas Intune App Protection. Una vez que el documento se guarda en la cuenta "corporativa" de OneDrive, se le considerará como contexto "corporativo" y se aplicarán las directivas Intune App Protection.

Como ejemplo de contexto de trabajo o "corporativo", piense en un usuario que inicia la aplicación OneDrive con su cuenta profesional. En el contexto de trabajo, no puede mover los archivos a una ubicación de almacenamiento personal. Más adelante, cuando usa OneDrive con su cuenta personal, puede copiar y mover los datos de su OneDrive personal sin restricciones.

Outlook tiene una vista de correo electrónico combinada de correos electrónicos "personales" y "corporativos". En esta situación, la aplicación Outlook solicita el PIN de Intune al iniciarse.

Para obtener más información sobre varias identidades en Intune, consulte [MAM y varias identidades](apps-supported-intune-apps.md).

### <a name="intune-app-pin"></a>PIN de aplicación de Intune

El número de identificación personal (PIN) es un código de acceso que se utiliza para comprobar que el usuario correcto está obteniendo acceso a los datos de la organización en una aplicación.

**Solicitud de PIN**<br>
Intune solicita el PIN de la aplicación del usuario cuando este esté a punto de acceder a los datos "corporativos". En las aplicaciones de varias identidades, como Word, Excel o PowerPoint, se solicitará al usuario el PIN cuando intente abrir un archivo o documento "corporativos". En las aplicaciones de una sola identidad, como las aplicaciones de línea de negocio administradas mediante la [herramienta de ajuste de aplicaciones de Intune](../developer/apps-prepare-mobile-application-management.md), el PIN se solicita en el inicio, ya que el [SDK de Intune](../developer/app-sdk.md) sabe que la experiencia del usuario en la aplicación siempre es "corporativa".

**Solicitud de PIN, solicitud de credenciales corporativas, frecuencia**<br>
El administrador de TI puede definir la opción de configuración de directivas de protección de aplicaciones de Intune **Volver a comprobar los requisitos de acceso tras (minutos)** en la consola de administración de Intune. Esta opción especifica el periodo de tiempo antes de comprobar los requisitos de acceso en el dispositivo y se vuelve a mostrar la pantalla del PIN de la aplicación, o bien la solicitud de credenciales corporativas. Sin embargo, los detalles importantes sobre el PIN que afectan a la frecuencia con la que se solicitará al usuario son los siguientes:

- **El PIN se comparte entre las aplicaciones del mismo publicador para mejorar la capacidad de uso:**<br> En iOS/iPadOS, un PIN de aplicación se comparte entre todas las aplicaciones **del mismo publicador de aplicaciones**. Por ejemplo, todas las aplicaciones de Microsoft comparten el mismo PIN. En el caso de Android, este es compartido entre todas las aplicaciones.
- **El comportamiento *Volver a comprobar los requisitos de acceso tras (minutos)* tras un reinicio del dispositivo:**<br> Un temporizador realiza el seguimiento del número de minutos de inactividad que determinan cuándo se debe mostrar el siguiente PIN de la aplicación de Intune (o la solicitud de credenciales corporativas). En iOS/iPadOS, el temporizador no se ve afectado por el reinicio del dispositivo. Por tanto, reiniciar el dispositivo no tiene ningún efecto en el número de minutos que el usuario ha estado inactivo en una aplicación iOS/iPadOS con la directiva de PIN de Intune seleccionada (o la solicitud de credenciales corporativas). En Android, el temporizador se restablece con el reinicio del dispositivo. Por tanto, las aplicaciones Android con una directiva de PIN de Intune (o solicitud de credenciales corporativas) probablemente soliciten un PIN de aplicación (o una solicitud de credenciales corporativas) con independencia del valor de configuración "Volver a comprobar los requisitos de acceso después de (minutos)" **tras un reinicio del dispositivo**.  
- **La naturaleza gradual del temporizador asociado al PIN:**<br> al escribir el PIN para acceder a una aplicación (aplicación A), cuando esta deja de estar en primer plano (foco de entrada principal) en el dispositivo, se restablece el temporizador de ese PIN. En el caso de cualquier otra aplicación (aplicación B) que use el mismo PIN, no se solicitará al usuario que lo vuelva a escribir, ya que el temporizador se habrá restablecido. La solicitud se volverá a mostrar una vez que se haya alcanzado el valor establecido en "Volver a comprobar los requisitos de acceso tras (minutos)".

Para los dispositivos iOS/iPadOS, incluso si el PIN se comparte entre aplicaciones de diferentes publicadores, se mostrará nuevamente la solicitud cuando se vuelva a alcanzar el valor **Volver a comprobar los requisitos de acceso después de (minutos)** de la aplicación que no es el foco de entrada principal. Por tanto, por ejemplo, un usuario tiene la aplicación _A_ del publicador _X_ y la aplicación _B_ del publicador _Y_, y esas dos aplicaciones comparten el mismo PIN. El usuario se centra en la aplicación _A_ (en primer plano) y la aplicación _B_ está minimizada. Después de que se alcance el valor **Volver a comprobar los requisitos de acceso después de (minutos)** y el usuario cambie a la aplicación _B_, se requeriría el PIN.

  >[!NOTE]
  > Para comprobar los requisitos de acceso del usuario más a menudo, por ejemplo, la solicitud del PIN, en particular en el caso de las aplicaciones utilizadas más a menudo, se recomienda reducir el valor de la opción "Volver a comprobar los requisitos de acceso tras (minutos)".

**PIN de aplicación integrados para Outlook y OneDrive**<br>
El PIN de Intune funciona en base a un temporizador basado en inactividad (el valor de **Volver a comprobar los requisitos de acceso tras [minutos]**). Por lo tanto, las solicitudes del PIN de Intune se muestran independientemente de las solicitudes de PIN de aplicación integrado para Outlook y OneDrive, que a menudo están vinculados al inicio de la aplicación de forma predeterminada. Si el usuario recibe ambas solicitudes de PIN al mismo tiempo, el comportamiento esperado debería ser que el PIN de Intune tiene prioridad.

**Seguridad de PIN de Intune**<br>
El PIN sirve para permitir que solo el usuario correcto disponga de acceso a los datos de su organización en la aplicación. Por lo tanto, el usuario debe iniciar sesión con su cuenta profesional o educativa para poder establecer o restablecer el PIN de la aplicación de Intune. Esta autenticación se controla mediante Azure Active Directory a través del intercambio de token seguros y no es transparente para el [SDK de Intune](../developer/app-sdk.md). Desde una perspectiva de seguridad, la mejor manera de proteger los datos profesionales o educativos es cifrarlos. El cifrado no está relacionado con el PIN de la aplicación, pero tiene su propia directiva de protección de aplicaciones.

**Protección contra ataques por fuerza bruta y el PIN de Intune**<br>
Como parte de la directiva de PIN de la aplicación, el administrador de TI puede establecer el número máximo de veces que un usuario puede intentar autenticar su PIN antes de bloquear la aplicación. Después de que se haya cumplido el número de intentos, el [SDK de Intune](../developer/app-sdk.md) puede borrar los datos "corporativos" en la aplicación.

**PIN de Intune y eliminación selectiva**<br>
En iOS/iPadOS, la información del PIN de nivel de aplicación se almacena en la cadena de claves que se comparte entre las aplicaciones con el mismo publicador, como todas las aplicaciones de Microsoft de primera entidad. Esta información de PIN también está vinculada a una cuenta de usuario final. Una eliminación selectiva de una aplicación no debe afectar a otra aplicación. 

Por ejemplo, un PIN establecido para Outlook para el usuario que ha iniciado sesión se almacena en una cadena de claves compartida. Cuando el usuario inicia sesión en OneDrive (también publicado por Microsoft), verá el mismo PIN que Outlook, ya que usa la misma cadena de claves compartida. Al cerrar la sesión de Outlook o borrar los datos de usuario en Outlook, el SDK de Intune no borra esa cadena de claves porque es posible que aún esté usando ese PIN. Por este motivo, los borrados selectivos no borran esa cadena de claves compartida, incluido el PIN. Este comportamiento permanece igual incluso si solo existe una aplicación por editor en el dispositivo. 

Dado que el PIN se comparte entre las aplicaciones con el mismo editor, si el borrado se dirige a una sola aplicación, el SDK de Intune no sabrá si hay otras aplicaciones en el dispositivo con el mismo editor. Por lo tanto, el SDK de Intune no borra el PIN, ya que puede seguir utilizándose para otras aplicaciones. Se espera que el PIN de la aplicación se borre cuando la última aplicación de ese editor se quite a la larga en el contexto de alguna limpieza del sistema operativo.
 
Si observa que el PIN se está borrando en algunos dispositivos, es probable que se produzca lo siguiente: Puesto que el PIN está asociado a una identidad, si el usuario ha iniciado sesión con una cuenta diferente después de un borrado, se le pedirá que escriba un nuevo PIN. Sin embargo, si inicia sesión con una cuenta existente, ya se puede usar un PIN almacenado en la cadena de claves para iniciar sesión.

**¿Establecer un PIN dos veces en las aplicaciones del mismo publicador?**<br>
MAM (en iOS/iPadOS) permite actualmente un PIN de nivel de aplicación con caracteres alfanuméricos y especiales (llamado "código de acceso"), que requiere la participación de aplicaciones (como WXP, Outlook, Managed Browser y Yammer) para integrar el [SDK de Intune para iOS](../developer/app-sdk-ios.md). Sin esto, la configuración de código de acceso no se aplica correctamente en las aplicaciones de destino. Se trata de una característica publicada en el SDK de Intune para iOS v. 7.1.12.

Para admitir esta característica y garantizar la compatibilidad con versiones anteriores del SDK de Intune para iOS/iPadOS, todos los PIN (ya sean numéricos o un código de acceso) de la versión 7.1.12+ se tratan por separado a partir del PIN numérico en versiones anteriores del SDK. Por lo tanto, si un dispositivo tiene aplicaciones con el SDK de Intune para iOS en versiones anteriores a 7.1.12 Y posteriores a 7.1.12 del mismo publicador, será necesario configurar dos PIN. Los dos PIN (para cada aplicación) no están relacionados de ninguna manera (es decir, deben cumplir la directiva de protección de aplicaciones correspondiente a la aplicación). Por lo tanto, *solo* si las aplicaciones A y B tienen las mismas directivas aplicadas (con respecto a los PIN), el usuario podrá configurar dos veces el mismo PIN. 

Este comportamiento es específico para el PIN en aplicaciones iOS/iPadOS que ya están habilitadas con la Administración de aplicaciones móviles de Intune. Con el tiempo, a medidas que las aplicaciones adoptan las versiones posteriores del SDK de Intune para iOS/iPadOS, el hecho de tener que establecer un PIN dos veces en las aplicaciones del mismo editor dejará de ser un problema importante. Vea la nota a continuación para obtener un ejemplo.

  >[!NOTE]
  > Por ejemplo, si la aplicación A se compila con una versión anterior a 7.1.12 y la aplicación B se compila con una versión posterior o igual a 7.1.12 del mismo editor, el usuario final tendrá que configurar por separado los PIN para A y B si ambos se instalan en un dispositivo iOS/iPadOS.
  > Si una aplicación C con la versión 7.1.9 del SDK está instalada en el dispositivo, compartirá el mismo PIN que la aplicación A. Una aplicación D compilada con 7.1.14 compartirá el mismo PIN que la aplicación B.  
  > Si solo se instalan las aplicaciones A y C se instalan en un dispositivo, tendrá que configurarse un PIN. Esto mismo se aplica si solo se instalan las aplicaciones B y D en un dispositivo.

### <a name="app-data-encryption"></a>Cifrado de datos de aplicación
Los administradores de TI pueden implementar una directiva de protección de aplicaciones que requiere cifrar los datos de aplicaciones. Como parte de la directiva, el administrador de TI también puede especificar cuándo se cifra el contenido.

**Cómo procesa el cifrado de datos de Intune**<br> Vea la [configuración de directivas de protección de aplicaciones Android](app-protection-policy-settings-android.md) y la [configuración de la protección de aplicaciones iOS/iPadOS](app-protection-policy-settings-ios.md) para obtener información detallada sobre la configuración de directiva de protección de aplicaciones de cifrado.

**Datos que están cifrados**<br>
Solo se cifran los datos marcados como "corporativos" según la directiva de protección de la aplicación del administrador de TI. Los datos se consideran "corporativos" cuando se originan desde una ubicación de la empresa. En el caso de las aplicaciones de Office, Intune considera lo siguiente como ubicaciones empresariales:

- Correo electrónico (Exchange) 
- Almacenamiento en la nube (aplicación OneDrive con una cuenta de OneDrive para la Empresa)

Para las aplicaciones de línea de negocio administradas por la [herramienta de ajuste de aplicaciones de Intune](../developer/apps-prepare-mobile-application-management.md), todos los datos de aplicaciones se consideran "corporativos".

### <a name="selective-wipe"></a>Borrado selectivo

**Borrar de forma remota los datos**<br>
Intune puede borrar los datos de aplicación de tres formas diferentes: 
- Borrado completo del dispositivo
- Borrado selectivo para MDM 
- Borrado selectivo de MAM

Para obtener más información sobre el borrado remoto de MDM, vea [Eliminación de dispositivos mediante Borrar o Retirar](../remote-actions/devices-wipe.md). Para obtener más información sobre el borrado selectivo mediante MAM, vea [la acción Retirar](../remote-actions/devices-wipe.md#retire) y [Borrado solo de datos corporativos de aplicaciones administradas por Intune](apps-selective-wipe.md).

El [borrado de dispositivo completo](../remote-actions/devices-wipe.md) quita todos los datos de usuario y la configuración del **dispositivo** restaurando el dispositivo a la configuración predeterminada de fábrica. El dispositivo se quita de Intune.

  >[!NOTE]
  > El borrado completo de dispositivo y el borrado selectivo para MDM solo se puede lograr en dispositivos inscritos con la administración de dispositivos móviles de Intune (MDM).

**Borrado selectivo para MDM**<br>
Vea [Eliminación de dispositivos: retirar](../remote-actions/devices-wipe.md#retire) para obtener información sobre cómo eliminar datos de la empresa.

**Borrado selectivo para MAM**<br>
El borrado selectivo de MAM simplemente quita los datos de la aplicación de empresa de la aplicación. La solicitud se inicia mediante el Portal de Intune Azure. Para obtener información sobre cómo iniciar una solicitud de borrado, vea [Borrado solo de datos corporativos de aplicaciones](apps-selective-wipe.md).

Si el usuario está utilizando la aplicación cuando se inicia el borrado selectivo, el [SDK de Intune](../developer/app-sdk.md) comprueba cada 30 minutos una solicitud de borrado selectivo desde el servicio Intune MAM. También comprueba el borrado selectivo cuando el usuario inicia la aplicación por primera vez e inicia sesión con su cuenta profesional o educativa.

**Cuando los servicios locales no funcionan con aplicaciones protegidas de Intune**<br>
La protección de aplicaciones de Intune depende de la identidad del usuario para ser coherente entre la aplicación y el [SDK de Intune](../developer/app-sdk.md). La única manera de garantizar esto es a través de la autenticación moderna. Hay escenarios en los que las aplicaciones pueden funcionar con una configuración local, pero no son coherentes ni ofrecen garantías.

**Forma segura de abrir vínculos web desde aplicaciones administradas**<br>
El administrador de TI puede implementar y establecer una directiva de protección de aplicaciones para la [aplicación Intune Managed Browser](app-configuration-managed-browser.md), un explorador web desarrollado por Microsoft Intune que puede administrarse fácilmente con Intune. El administrador de TI puede requerir que todos los vínculos web en aplicaciones administradas de Intune se abran con la aplicación Managed Browser.

## <a name="app-protection-experience-for-ios-devices"></a>Experiencia de protección de aplicaciones para dispositivos iOS

### <a name="device-fingerprint-or-face-ids"></a>Identificadores de cara o huella digital del dispositivo 
Las directivas de protección de aplicaciones de Intune permiten limitar el acceso a solo los usuarios con licencia de Intune. Una de las maneras de controlar el acceso a la aplicación es exigir Touch ID o Face ID de Apple en dispositivos admitidos. Intune implementa un comportamiento donde si hay algún cambio en la base de datos biométrica del dispositivo, Intune solicita al usuario un PIN cuando se alcanza el siguiente valor de tiempo de espera de inactividad. Los cambios realizados en los datos biométricos incluyen la incorporación o eliminación de una cara o una huella digital. Si el usuario de Intune no tiene establecido un PIN, se le lleva por los pasos para configurar uno.
 
La finalidad de este proceso es seguir manteniendo los datos de la organización dentro de la aplicación seguros y protegidos en el nivel de aplicación. Esta característica solo está disponible para iOS/iPadOS y requiere la participación de las aplicaciones que integran el SDK de Intune para iOS/iPadOS, versión 9.0.1 o posterior. La integración del SDK es necesaria para poder aplicar el comportamiento en las aplicaciones de destino. Esta integración ocurre de manera gradual y depende de los equipos de la aplicación específica. Algunas aplicaciones participantes incluyen WXP, Outlook, Managed Browser y Yammer.
  
### <a name="ios-share-extension"></a>Extensión de recursos compartidos de iOS
Puede usar la extensión de recursos compartidos de iOS/iPadOS para abrir los datos profesionales o educativos en aplicaciones no administradas, incluso con la directiva de transferencia de datos establecida en **solo aplicaciones administradas** o **ninguna aplicación**. La directiva de protección de aplicaciones de Intune no puede controlar la extensión de recursos compartidos de iOS/iPadOS sin administrar el dispositivo. Por lo tanto, Intune _**cifra los datos "corporativos" antes de compartirlos fuera de la aplicación**_. Puede validar este comportamiento de cifrado intentando abrir un archivo "corporativo" fuera de la aplicación administrada. El archivo debe estar cifrado y no debe poder abrirse fuera de la aplicación administrada.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Varias configuraciones de acceso de protección de aplicaciones de Intune para el mismo conjunto de aplicaciones y usuarios
Las directivas de protección de aplicaciones de Intune para el acceso se aplicarán en un orden específico en los dispositivos de usuario final cuando intenten obtener acceso a una aplicación de destino desde su cuenta corporativa. En general, tendría prioridad un borrado, seguido de un bloqueo y, después, una advertencia descartable. Por ejemplo, si es aplicable a la aplicación o usuario específico, una configuración de sistema operativo mínima de iOS/iPadOS que advierte al usuario que actualice la versión de iOS/iPadOS se aplicará después de la configuración de sistema operativo mínima de iOS/iPadOS que bloquea el acceso del usuario. Por tanto, en el caso en que el administrador de TI configure el sistema operativo mínimo de iOS en 11.0.0.0 y el sistema operativo mínimo de iOS (solo advertencia) en 11.1.0.0, mientras el dispositivo que intenta obtener acceso a la aplicación esté en iOS 10, se bloquearía al usuario final en función del valor más restrictivo para la versión de sistema operativo de iOS mínima que provoque el bloqueo del acceso.

Cuando se trabaja con distintos tipos de configuraciones, un requisito de versión del SDK de Intune tendría prioridad, seguido por el requisito de versión de la aplicación y el requisito de versión del sistema operativo de iOS/iPadOS. Después, se comprueban en el mismo orden las advertencias para todos los tipos de configuración. Se recomienda configurar los requisitos de versión del SDK de Intune solo de acuerdo con las instrucciones del equipo de producto de Intune para escenarios de bloqueo esenciales.

## <a name="app-protection-experience-for-android-devices"></a>Experiencia de protección de aplicaciones para dispositivos Android

### <a name="company-portal-app-and-intune-app-protection"></a>Aplicación del Portal de empresa y protección de aplicaciones de Intune
La mayor parte de la función de protección de aplicaciones se integra en la aplicación de portal de empresa. La inscripción de dispositivos _no es obligatoria_ aunque la aplicación de portal de empresa se requiera siempre. Para la administración de aplicaciones móviles sin inscripción (MAM-WE), el usuario final solo necesita tener la aplicación Portal de empresa instalada en el dispositivo.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Varias configuraciones de acceso de protección de aplicaciones de Intune para el mismo conjunto de aplicaciones y usuarios
Las directivas de protección de aplicaciones de Intune para el acceso se aplicarán en un orden específico en los dispositivos de usuario final cuando intenten obtener acceso a una aplicación de destino desde su cuenta corporativa. En general, tendría prioridad un bloqueo y, después, una advertencia descartable. Por ejemplo, si es aplicable a la aplicación o usuario específico, una configuración de versión de revisión mínima de Android que advierte al usuario de realizar una actualización de revisión se aplicará después de la configuración de versión de revisión mínima de Android que bloquea el acceso del usuario. Por tanto, en el caso en que el administrador de TI configure la versión de revisión de Android mínima en 01-03-2018 y la versión de revisión de Android mínima (solo advertencia) en 01-02-2018, mientras el dispositivo que intenta obtener acceso a la aplicación esté en una versión de revisión 01-01-2018, se bloquearía al usuario final en función del valor más restrictivo para la versión de revisión de Android mínima que provoque el bloqueo del acceso. 

Cuando se trabaja con diferentes tipos de configuraciones, un requisito de versión de la aplicación tendría prioridad, seguido por el requisito de versión de sistema operativo de Android y el requisito de versión de revisión de Android. Después, se comprueban en el mismo orden las advertencias para todos los tipos de configuración.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Directivas de protección de aplicaciones de Intune y atestación de SafetyNet de Google para dispositivos Android 
Las directivas de protección de aplicaciones de Intune permiten a los administradores requerir que los dispositivos de usuario final pasen la API de atestación de SafetyNet de Google para dispositivos Android. Se notificará una nueva determinación de servicio de Google Play a los administradores de TI con un intervalo determinado por el servicio Intune. La frecuencia de las llamadas de servicio está limitada debido a la carga y, por lo tanto, este valor se mantiene internamente y no es configurable. Cualquier acción que configure el administrador de TI para el valor de configuración de la atestación de SafetyNet de Google se realizará en función del último resultado notificado para el servicio de Intune en el momento del inicio condicional. Si no hay ningún dato, se permitirá el acceso siempre que no se produzcan errores en otras comprobaciones del inicio condiciona; en el back-end se iniciará un servicio de "recorrido de ida y vuelta" de Google Play para determinar los resultados de la atestación y se le solicitará al usuario de forma asincrónica si el dispositivo ha producido algún error. Si los datos disponibles son obsoletos, se permitirá o bloqueará el acceso en función del último resultado notificado; de forma similar, se iniciará un servicio de "recorrido de ida y vuelta" de Google Play para determinar los resultados de la atestación y se le pedirá al usuario de forma asincrónica si el dispositivo ha producido algún error.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Directivas de protección de aplicaciones de Intune y Verify Apps API de Google para dispositivos Android
Las directivas de Intune App Protection permiten a los administradores requerir que los dispositivos de usuario final envíen señales a través de la Verify Apps API de Google para dispositivos Android. Las instrucciones para hacerlo varían ligeramente en función del dispositivo. Lo habitual es ir a Google Play Store y, luego, hacer clic en **Mis aplicaciones y juegos**. A continuación, debe hacer clic en el resultado del último examen de la aplicación, lo que le llevará al menú de Play Protect. Asegúrese de que el conmutador **Buscas amenazas de seguridad en dispositivo** esté activado.

### <a name="googles-safetynet-attestation-api"></a>API de atestación de SafetyNet de Google 
Intune aprovecha las API de SafetyNet de Google Play Protect para agregarlas a las comprobaciones de detección de rooting para dispositivos no inscritos. Google ha desarrollado y mantenido este conjunto de API para aplicaciones Android en caso de que no se quiera ejecutarlas en dispositivos con rooting. La aplicación Android Pay ha incorporado esto, por ejemplo. Aunque Google no comparte públicamente la totalidad de las comprobaciones de detección de rooting que se producen, esperamos que estas API detecten los usuarios que hayan aplicado el rooting en sus dispositivos. Después, se puede bloquear el acceso de estos usuarios o se pueden eliminar sus cuentas de empresa desde sus aplicaciones habilitadas para la directiva. **Comprobar integridad básica** muestra información sobre la integridad general del dispositivo. Por ejemplo, dispositivos con rooting, emuladores, dispositivos virtuales y cualquier otro dispositivo con signos de error de integridad básica por manipulación. **Comprobar integridad básica y dispositivos certificados** ofrece información sobre la compatibilidad del dispositivo con los servicios de Google. Solo superan esta comprobación aquellos dispositivos que no se han manipulado y están certificados por Google. Entre los dispositivos que producirán un error se incluyen los siguientes:

- Dispositivos que producen error en la integridad básica
- Dispositivos con un cargador de arranque desbloqueado
- Dispositivos con una imagen de sistema personalizada o ROM
- Dispositivos para los que el fabricante no ha solicitado o superado la certificación de Google
- Dispositivos con una imagen de sistema creada directamente desde los archivos de origen del Android Open Source Program
- Dispositivos con una imagen de sistema de versión preliminar beta o de desarrollador

Consulte la [documentación de Google sobre la atestación de SafetyNet](https://developer.android.com/training/safetynet/attestation) para obtener detalles técnicos.

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>Opciones de configuración de atestación de dispositivo SafetyNet o "Dispositivos con jailbreak o rooting"
Las comprobaciones de la API de SafetyNet de Google Play Protect requieren que el usuario final esté en línea, al menos durante la ejecución del "recorrido de ida y vuelta" para determinar los resultados de atestación. Si el usuario final está sin conexión, el administrador de TI puede esperar igualmente que se exija un resultado de la configuración **Dispositivos con jailbreak o rooting**. Dicho esto, si el usuario final ha estado sin conexión demasiado tiempo, se aplica el valor **Período de gracia sin conexión**. Asimismo, cuando se alcanza este valor del temporizador, todo acceso a los datos profesionales o educativos se bloquea hasta que el acceso a la red esté disponible. Activar ambas opciones de configuración permite aplicar un enfoque por capas con el fin de mantener los dispositivos del usuario final en buen estado, lo que es importante cuando los usuarios finales acceden a los datos profesionales o educativos desde dispositivos móviles.

### <a name="google-play-protect-apis-and-google-play-services"></a>API de Google Play Protect y Google Play Services
La configuración de directivas de protección de aplicaciones que utilicen las API de Google Play Protect requiere Google Play Services para su funcionamiento. Ambas opciones **Atestación de dispositivo SafetyNet** y **Examen de amenazas en las aplicaciones** requieren una versión determinada de Google Play Services para funcionar correctamente. Puesto que estas opciones de configuración corresponden al área de seguridad, si el usuario final es el destinatario de esta configuración y no dispone de la versión adecuada de Google Play Services o no tiene acceso a ella, se le bloqueará.

## <a name="next-steps"></a>Pasos siguientes

[Creación e implementación de directivas de protección de aplicaciones con Microsoft Intune](app-protection-policies.md)

[Configuración de directivas de protección de aplicaciones Android disponibles con Microsoft Intune](app-protection-policy-settings-android.md)

[Configuración de directivas de protección de aplicaciones iOS/iPadOS disponibles con Microsoft Intune](app-protection-policy-settings-ios.md)

## <a name="see-also"></a>Vea también
Las aplicaciones de terceros, como la aplicación móvil de Salesforce, funcionan con Intune de formas específicas para proteger los datos corporativos. Para más información sobre cómo la aplicación de Salesforce funciona con Intune en particular (incluida la configuración de la aplicación de MDM), vea [Salesforce App and Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf) (Aplicación de Salesforce y Microsoft Intune).
