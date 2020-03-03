---
title: Preguntas más frecuentes sobre MAM y la protección de la aplicación
description: Este artículo proporciona respuestas a algunas preguntas frecuentes en la administración de aplicaciones móvil de Intune (MAM) y la protección de aplicaciones de Intune.
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
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 494878c78189aed2612883017f4808be72b8f15d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511606"
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Preguntas más frecuentes sobre MAM y la protección de la aplicación

Este artículo proporciona respuestas a algunas preguntas frecuentes sobre la administración de aplicaciones móviles (MAM) de Intune y la protección de aplicaciones de Intune.

## <a name="mam-basics"></a>Conceptos básicos de MAM

**¿Qué es MAM?**<br></br>
La [administración de aplicaciones móviles de Intune](app-lifecycle.md) hace referencia al conjunto de funciones de administración de Intune que le permite publicar, insertar, configurar, proteger, supervisar y actualizar aplicaciones móviles para los usuarios.

**¿Cuáles son las ventajas de la protección de aplicaciones MAM?**<br></br>
MAM protege los datos de la organización dentro de una aplicación. Con MAM sin inscripción (MAM-WE), una aplicación profesional o educativa que contiene información confidencial puede administrarse en casi cualquier dispositivo, incluidos los dispositivos personales en escenarios de Bring Your Own Device (BYOD). Muchas aplicaciones de productividad, como las aplicaciones de Microsoft Office, pueden administrarse mediante Intune MAM. Consulte la lista oficial de [aplicaciones administradas de Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), disponible para uso público.

**¿Qué configuraciones de dispositivo admite MAM?**<br></br>
Intune MAM admite dos configuraciones:
- **Intune MDM + MAM**: Los administradores de TI solo pueden administrar aplicaciones mediante directivas de protección de aplicaciones y MAM en los dispositivos que están inscritos con la administración de dispositivos móviles (MDM) de Intune. Para administrar aplicaciones mediante MDM + MAM, los clientes deben usar la consola de Intune en Azure Portal (en https://portal.azure.com).

- **MAM sin inscripción de dispositivos**: MAM sin inscripción de dispositivos o MAM-WE permite a los administradores de TI administrar aplicaciones mediante directivas de protección de aplicaciones y MAM en dispositivos no inscritos con Intune MDM. Esto significa que las aplicaciones pueden administrarse mediante Intune en dispositivos inscritos con proveedores de EMM de terceros. Para administrar aplicaciones mediante MAM-WE, los clientes deben usar la consola de Intune en Azure Portal (en [https://portal.azure.com](https://portal.azure.com)). Además, Intune puede administrar las aplicaciones en dispositivos inscritos con otros proveedores de Enterprise Mobility Management (EMM) o no inscritos con MDM.


## <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

**¿Qué son las directivas de protección de aplicaciones?**<br></br>
Las directivas de protección de aplicaciones que garantizan los datos de la organización siguen siendo seguras o se encuentran en una aplicación administrada. Una directiva puede ser una regla que se aplica cuando el usuario intenta obtener acceso o mover datos "corporativos" o un conjunto de acciones que están prohibidas o que se supervisan cuando el usuario está dentro de la aplicación.

**¿Cuáles son los ejemplos de directivas de protección de aplicaciones?**<br></br>
Vea la [configuración de directivas de protección de aplicaciones Android](app-protection-policy-settings-android.md) y la [configuración de la protección de aplicaciones iOS/iPadOS](app-protection-policy-settings-ios.md) para obtener información detallada sobre cada configuración de directiva de protección de aplicaciones.

**¿Es posible aplicar tanto la directiva de MDM como la de MAM al mismo usuario al mismo tiempo para distintos dispositivos? Por ejemplo, si un usuario pudiera tener acceso a sus recursos de trabajo desde su propia máquina habilitada para MAM, pero también viniera a trabajar y usara un dispositivo administrado por MDM de Intune. ¿Hay alguna advertencia sobre esta idea?**<br></br>
Si aplica una directiva de MAM al usuario sin establecer el estado del dispositivo, el usuario recibirá la directiva de MAM en el dispositivo BYOD y el dispositivo administrado por Intune. También puede aplicar una directiva de MAM según el estado administrado. Por lo tanto, cuando cree una directiva de protección de aplicaciones, debería seleccionar No junto a Destinar a todos los tipos de aplicaciones. Luego, realice cualquiera de las siguientes acciones:
- Aplique una directiva de MAM menos estricta a los dispositivos administrados por Intune y aplique una más estricta a los dispositivos no inscritos en MDM.
- Aplique una directiva de MAM solo a los dispositivos no inscritos.

Para más información, consulte [Supervisión de las directivas de protección de aplicaciones](app-protection-policies-monitor.md).

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplicaciones que puede administrar con directivas de protección de aplicaciones

**¿Qué aplicaciones se pueden administrar mediante directivas de protección de aplicaciones?**<br></br>
Cualquier aplicación integrada con el [SDK para aplicaciones de Intune](../developer/app-sdk.md) o ajustada mediante la [herramienta de ajuste de aplicaciones de Intune](../developer/apps-prepare-mobile-application-management.md) puede administrarse con las directivas de protección de aplicaciones de Intune. Consulte la lista oficial de [aplicaciones administradas de Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), disponible para uso público.

**¿Cuáles son los requisitos básicos para utilizar directivas de protección de aplicaciones en una aplicación administrada de Intune?**

- El usuario final debe tener una cuenta de Azure Active Directory (AAD). Consulte [Agregar usuarios y conceder permiso administrativo a Intune](../fundamentals/users-add.md) para aprender a crear usuarios de Intune en Azure Active Directory.

- El usuario final debe tener una licencia de Microsoft Intune asignada a su cuenta de Azure Active Directory. Vea [Administrar licencias de Intune](../fundamentals/licenses-assign.md) para obtener información sobre cómo asignar licencias de Intune a los usuarios finales.

- El usuario final debe pertenecer a un grupo de seguridad de destino de una directiva de protección de la aplicación. La misma directiva de protección de aplicaciones debe tener como destino la aplicación específica que se va a utilizar. Las directivas de protección de aplicaciones pueden crearse e implementarse en la consola de Intune en el [portal de Azure](https://portal.azure.com). Actualmente se pueden crear grupos de seguridad en el [Centro de administración de Microsoft 365](https://admin.microsoft.com).

- El usuario final debe iniciar sesión en la aplicación con su cuenta de AAD.

**¿Qué ocurre si quiero habilitar una aplicación con Intune App Protection, pero esta no está usando una plataforma de desarrollo de aplicaciones compatible?**

El equipo de desarrollo del SDK de Intune comprueba y mantiene de forma activa la compatibilidad con las aplicaciones creadas con las plataformas nativas de Android, iOS/iPadOS (Obj-C, Swift), Xamarin, Xamarin.Forms y Cordova. Aunque algunos clientes han podido integrar con éxito el SDK de Intune con otras plataformas como React Native y NativeScript, no proporcionamos instrucciones explícitas o complementos para desarrolladores de aplicaciones que no utilicen nuestras plataformas compatibles.

**¿Es compatible la biblioteca de autenticación de Microsoft (MSAL) o las cuentas de redes sociales con el SDK de aplicaciones de Intune?**<br></br>
El SDK de aplicaciones de Intune usa algunas funcionalidades avanzadas de ADAL para las versiones de la primera y la tercera parte del SDK. Por lo tanto, la MSAL no funciona bien con muchos de nuestros escenarios básicos, como la autenticación en el servicio de Intune App Protection y el inicio condicional. Dado que el objetivo general del equipo de identidades de Microsoft es migrar a MSAL en todas las aplicaciones de Microsoft Office, el SDK de Intune tendrá que admitirlo en algún momento, pero actualmente no está previsto.

**¿Cuáles son los requisitos adicionales para usar la [aplicación móvil de Outlook](https://products.office.com/outlook)?**

- El usuario final debe tener la aplicación móvil de Outlook instalada en su dispositivo.

- El usuario final debe tener una licencia y buzón de correo de [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) vinculados a su cuenta de Azure Active Directory.

  >[!NOTE]
  > Actualmente, la aplicación móvil de Outlook solo es compatible con Intune App Protection para Microsoft Exchange Online y [Exchange Server con autenticación moderna híbrida](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) y no admite Exchange en Office 365 dedicado.

**¿Cuáles son los requisitos adicionales para usar las aplicaciones [Word, Excel y PowerPoint](https://products.office.com/business/office)?**

- El usuario final debe tener una licencia de [Office 365 Empresa o Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) asignada a su cuenta de Azure Active Directory. La suscripción debe incluir las aplicaciones de Office en dispositivos móviles y puede incluir una cuenta de almacenamiento en la nube con [OneDrive para la Empresa](https://onedrive.live.com/about/business/). Las licencias de Office 365 se pueden asignar en el [Centro de administración de Microsoft 365](https://admin.microsoft.com) siguiendo estas [instrucciones](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- El usuario final debe tener una ubicación administrada configurada con la funcionalidad pormenorizada Guardar como en la configuración de directiva de protección de aplicaciones "Guardar copias de los datos de la organización". Por ejemplo, si la ubicación administrada es OneDrive, la aplicación [OneDrive](https://onedrive.live.com/about/) debe estar configurada en la aplicación Word, Excel o PowerPoint del usuario final.

- Si la ubicación administrada es OneDrive, la directiva de protección de aplicaciones implementada para el usuario final debe tener como destino la aplicación.

  >[!NOTE]
  > Las aplicaciones móviles de Office actualmente solo admiten SharePoint Online y no SharePoint local.

**¿Por qué se necesita una ubicación administrada (como OneDrive) para Office?**<br></br>
Intune marca todos los datos de la aplicación como "empresa" o "personal". Los datos se consideran "corporativos" cuando se originan desde una ubicación de la empresa. Para las aplicaciones de Office, Intune considera las siguientes ubicaciones de la empresa: correo electrónico (Exchange) o almacenamiento en la nube (aplicación OneDrive con una cuenta de OneDrive para la Empresa).

**¿Cuáles son los requisitos adicionales para usar Skype Empresarial?**<br></br>
Consulte los requisitos de licencias de [Skype Empresarial](https://products.office.com/skype-for-business/it-pros). Para configuraciones híbridas y locales de Skype Empresarial, consulte [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) (La autenticación moderna híbrida para Skype Empresarial y Exchange está disponible con carácter general) y [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910) (Autenticación moderna para Skype Empresarial local con AAD), respectivamente.

## <a name="app-protection-features"></a>Características de protección de aplicaciones

**¿Qué es la compatibilidad con varias identidades?**<br></br>
La compatibilidad con varias identidades es la capacidad para Intune App SDK de solo aplicar las directivas de protección de aplicaciones a la cuenta profesional o educativa con la que se ha iniciado sesión en la aplicación. Si se ha iniciado sesión en la aplicación con una cuenta personal, los datos no se modifican.

**¿Cuál es el propósito de la compatibilidad con varias identidades?**<br></br>
La compatibilidad con varias identidades permite que aplicaciones con audiencias "corporativas" y de consumidor (por ejemplo, las aplicaciones de Office) se lancen públicamente con funcionalidad de protección de aplicaciones de Intune para las cuentas "corporativas".

**¿Qué sucede con Outlook y varias identidades?**<br></br>
Puesto que Outlook tiene una vista de correo electrónico combinada de correos electrónicos personales y "corporativos", la aplicación Outlook solicita el PIN de Intune al iniciarse.

**¿Qué es el PIN de la aplicación de Intune?**<br></br>
El número de identificación personal (PIN) es un código de acceso que se utiliza para comprobar que el usuario correcto está obteniendo acceso a los datos de la organización en una aplicación.

- **¿Cuándo se solicita al usuario que especifique el PIN?**<br></br> Intune solicita el PIN de la aplicación del usuario cuando este esté a punto de acceder a los datos "corporativos". En las aplicaciones de varias identidades, como Word, Excel o PowerPoint, se solicitará al usuario el PIN cuando intente abrir un archivo o documento "corporativos". En las aplicaciones de una sola identidad, como las aplicaciones de línea de negocio administradas mediante la herramienta de ajuste de aplicaciones de Intune, el PIN se solicita en el inicio, ya que el SDK para aplicaciones de Intune App sabe que la experiencia del usuario en la aplicación siempre es "corporativa".

- **¿Con qué frecuencia se pedirá al usuario que escriba el PIN de Intune?**<br></br> El administrador de TI puede definir la opción de configuración de directivas de protección de aplicaciones de Intune "Volver a comprobar los requisitos de acceso tras (minutos)" en la consola de administración de Intune. Esta opción permite especificar el período de tiempo antes de comprobar los requisitos de acceso en el dispositivo. El PIN de la aplicación se vuelve a mostrar. Sin embargo, los detalles importantes sobre el PIN que afectan a la frecuencia con la que se solicitará al usuario son los siguientes: 

  - **El PIN se comparte entre las aplicaciones del mismo publicador para mejorar la capacidad de uso:** En iOS/iPadOS, un PIN de aplicación se comparte entre todas las aplicaciones **del mismo publicador de aplicaciones**. En el caso de Android, este es compartido entre todas las aplicaciones.
  - **El comportamiento "Volver a comprobar los requisitos de acceso después de (minutos)" tras un reinicio del dispositivo:** Un "temporizador de PIN" realiza un seguimiento del número de minutos de inactividad que determinan cuándo se debe mostrar el siguiente el PIN de la aplicación de Intune. En iOS/iPadOS, el temporizador de PIN no se ve afectado por el reinicio del dispositivo. Por tanto, el reinicio del dispositivo no tiene ningún efecto en el número de minutos que el usuario ha permanecido inactivo desde una aplicación de iOS/iPadOS con la directiva de PIN de Intune. En Android, el temporizador de PIN se restablece con el reinicio del dispositivo. Por lo tanto, las aplicaciones de Android con una directiva de PIN de Intune probablemente soliciten un PIN de aplicación, independientemente del valor de configuración "Volver a comprobar los requisitos de acceso después de (minutos)" **tras un reinicio del dispositivo**.  
  - **La naturaleza gradual del temporizador asociado al PIN:** al escribir el PIN para acceder a una aplicación (aplicación A), cuando esta deja de estar en segundo plano (foco de entrada principal) en el dispositivo, se restablece el temporizador del PIN. En el caso de cualquier otra aplicación (aplicación B) que use el mismo PIN, no se solicitará al usuario que lo vuelva a escribir, ya que el temporizador se habrá restablecido. La solicitud se volverá a mostrar una vez que se haya alcanzado el valor establecido en "Volver a comprobar los requisitos de acceso tras (minutos)".

Para los dispositivos iOS/iPadOS, incluso si el PIN se comparte entre aplicaciones de diferentes publicadores, se mostrará nuevamente la solicitud cuando se vuelva a alcanzar el valor **Volver a comprobar los requisitos de acceso después de (minutos)** de la aplicación que no es el foco de entrada principal. Por tanto, por ejemplo, un usuario tiene la aplicación _A_ del publicador _X_ y la aplicación _B_ del publicador _Y_, y esas dos aplicaciones comparten el mismo PIN. El usuario se centra en la aplicación _A_ (en primer plano) y la aplicación _B_ está minimizada. Después de que se alcance el valor **Volver a comprobar los requisitos de acceso después de (minutos)** y el usuario cambie a la aplicación _B_, se requeriría el PIN.

  >[!NOTE] 
  > Para comprobar los requisitos de acceso del usuario más a menudo, por ejemplo, la solicitud del PIN, en particular en el caso de las aplicaciones utilizadas más a menudo, se recomienda reducir el valor de la opción "Volver a comprobar los requisitos de acceso tras (minutos)". 
      
- **¿Cómo funciona el PIN de Intune con los PIN de aplicación integrados para Outlook y OneDrive?**<br></br>
El PIN de Intune funciona según un temporizador basado en inactividad (el valor de "Volver a comprobar los requisitos de acceso tras [minutos]"). Por lo tanto, las solicitudes del PIN de Intune se muestran independientemente de las solicitudes de PIN de aplicación integrado para Outlook y OneDrive, que a menudo están vinculados al inicio de la aplicación de forma predeterminada. Si el usuario recibe ambas solicitudes de PIN al mismo tiempo, el comportamiento esperado debería ser que el PIN de Intune tiene prioridad. 

- **¿Es seguro el PIN?**<br></br> El PIN sirve para permitir que solo el usuario correcto disponga de acceso a los datos de su organización en la aplicación. Por lo tanto, el usuario debe iniciar sesión con su cuenta profesional o educativa para poder establecer o restablecer el PIN de la aplicación de Intune. Esta autenticación se controla mediante Azure Active Directory a través del intercambio de token seguros y no es transparente para Intune App SDK. Desde una perspectiva de seguridad, la mejor manera de proteger los datos profesionales o educativos es cifrarlos. El cifrado no está relacionado con el PIN de la aplicación, pero tiene su propia directiva de protección de aplicaciones.

- **¿Cómo protege el PIN contra ataques por fuerza bruta Intune?**<br></br> Como parte de la directiva de PIN de la aplicación, el administrador de TI puede establecer el número máximo de veces que un usuario puede intentar autenticar su PIN antes de bloquear la aplicación. Después de que se haya cumplido el número de intentos, Intune App SDK puede borrar los datos "corporativos" en la aplicación.
  
- **¿Por qué tengo que establecer un PIN dos veces en las aplicaciones del mismo publicador?**<br></br> MAM (en iOS/iPadOS) permite actualmente un PIN de nivel de aplicación con caracteres alfanuméricos y especiales (llamado "código de acceso"), que requiere la participación de aplicaciones (como WXP, Outlook, Managed Browser y Yammer) para integrar Intune App SDK para iOS/iPadOS. Sin esto, la configuración de código de acceso no se aplica correctamente en las aplicaciones de destino. Es una característica publicada en el SDK de Intune para iOS/iPadOS v. 7.1.12. <br><br> Para admitir esta característica y garantizar la compatibilidad con versiones anteriores del SDK de Intune para iOS/iPadOS, todos los PIN (ya sean numéricos o un código de acceso) de la versión 7.1.12+ se tratan por separado a partir del PIN numérico en versiones anteriores del SDK. Por tanto, si un dispositivo tiene aplicaciones con el SDK de Intune para iOS/iPadOS en versiones anteriores Y posteriores a 7.1.12 del mismo publicador, será necesario configurar dos PIN. <br><br> Dicho esto, los dos PIN (para cada aplicación) no están relacionados de ninguna manera, es decir, deben cumplir la directiva de protección de aplicaciones correspondiente a la aplicación. Por lo tanto, *solo* si las aplicaciones A y B tienen las mismas directivas aplicadas (con respecto a los PIN), el usuario podrá configurar dos veces el mismo PIN. <br><br> Este comportamiento es específico para el PIN en aplicaciones iOS/iPadOS que ya están habilitadas con la Administración de aplicaciones móviles de Intune. Con el tiempo, a medidas que las aplicaciones adoptan las versiones posteriores del SDK de Intune para iOS/iPadOS, el hecho de tener que establecer un PIN dos veces en las aplicaciones del mismo editor dejará de ser un problema importante. Vea la nota a continuación para obtener un ejemplo.

  >[!NOTE]
  > Por ejemplo, si la aplicación A se compila con una versión anterior a 7.1.12 y la aplicación B se compila con una versión posterior o igual a 7.1.12 del mismo editor, el usuario final tendrá que configurar por separado los PIN para A y B si ambos se instalan en un dispositivo iOS/iPadOS. <br><br> Si una aplicación C con la versión 7.1.9 del SDK está instalada en el dispositivo, compartirá el mismo PIN que la aplicación A. <br><br> Una aplicación D compilada con 7.1.14 compartirá el mismo PIN que la aplicación B. <br><br> Si solo se instalan las aplicaciones A y C se instalan en un dispositivo, tendrá que configurarse un PIN. Esto mismo se aplica si solo se instalan las aplicaciones B y D en un dispositivo.

**¿Qué sucede con el cifrado?**<br></br>
Los administradores de TI pueden implementar una directiva de protección de aplicaciones que requiere cifrar los datos de aplicaciones. Como parte de la directiva, el administrador de TI también puede especificar cuándo se cifra el contenido.

- **¿Cómo cifra Intune los datos?**<br></br> Vea la [configuración de directivas de protección de aplicaciones Android](app-protection-policy-settings-android.md) y la [configuración de la protección de aplicaciones iOS/iPadOS](app-protection-policy-settings-ios.md) para obtener información detallada sobre la configuración de directiva de protección de aplicaciones de cifrado.

- **¿Qué se cifra?**<br></br> Solo se cifran los datos marcados como "corporativos" según la directiva de protección de la aplicación del administrador de TI. Los datos se consideran "corporativos" cuando se originan desde una ubicación de la empresa. Para las aplicaciones de Office, Intune considera las siguientes ubicaciones de la empresa: correo electrónico (Exchange) o almacenamiento en la nube (aplicación OneDrive con una cuenta de OneDrive para la Empresa). Para las aplicaciones de línea de negocio administradas por la herramienta de ajuste de aplicaciones de Intune, todos los datos de aplicaciones se consideran "corporativos".

**¿Cómo Intune borra los datos de forma remota?**<br></br>
Intune puede borrar los datos de la aplicación de tres maneras diferentes: borrado completo del dispositivo, borrado selectivo para MDM y borrado selectivo de MAM. Para obtener más información sobre el borrado remoto de MDM, vea [Eliminación de dispositivos mediante Borrar o Retirar](../remote-actions/devices-wipe.md). Para obtener más información sobre el borrado selectivo mediante MAM, vea [la acción Retirar](../remote-actions/devices-wipe.md#retire) y [Borrado solo de datos corporativos de aplicaciones administradas por Intune](apps-selective-wipe.md).

- **¿Qué es el borrado?**<br></br> El [borrado](../remote-actions/devices-wipe.md) quita todos los datos de usuario y la configuración del **dispositivo** mediante su restauración a la configuración predeterminada de fábrica. El dispositivo se quita de Intune.
  >[!NOTE]
  > El borrado solo se puede lograr en los dispositivos inscritos con la administración de dispositivos móviles de Intune (MDM).

- **¿Qué es el borrado selectivo para MDM?**<br></br> Vea [Eliminación de dispositivos: retirar](../remote-actions/devices-wipe.md#retire) para obtener información sobre cómo eliminar datos de la empresa.

- **¿Qué es el borrado selectivo para MAM?**<br></br> El borrado selectivo de MAM simplemente quita los datos de la aplicación de empresa de la aplicación. La solicitud se inicia mediante el Portal de Intune Azure. Para obtener información sobre cómo iniciar una solicitud de borrado, vea [Borrado solo de datos corporativos de aplicaciones](apps-selective-wipe.md).

- **¿Con qué rapidez se produce el borrado selectivo para MAM?**<br></br> Si el usuario está utilizando la aplicación cuando se inicia el borrado selectivo, Intune App SDK comprueba cada 30 minutos una solicitud de borrado selectivo desde el servicio Intune MAM. También comprueba el borrado selectivo cuando el usuario inicia la aplicación por primera vez e inicia sesión con su cuenta profesional o educativa.

**¿Por qué no funcionan los servicios locales con aplicaciones protegidas de Intune?**<br></br>
La protección de aplicaciones de Intune depende de la identidad del usuario para ser coherente entre la aplicación e Intune App SDK. La única manera de garantizar esto es a través de la autenticación moderna. Hay escenarios en los que las aplicaciones pueden funcionar con una configuración local, pero no son coherentes ni ofrecen garantías.

**¿Hay una forma segura de abrir vínculos web desde aplicaciones administradas?**<br></br>
Sí. El administrador de TI puede implementar y establecer una directiva de protección de aplicaciones para la [aplicación Intune Managed Browser](../apps/app-configuration-managed-browser.md), un explorador web desarrollado por Microsoft Intune que puede administrarse fácilmente con Intune. El administrador de TI puede requerir que todos los vínculos web en aplicaciones administradas de Intune se abran con la aplicación Managed Browser.

## <a name="app-experience-on-android"></a>Experiencia de la aplicación en Android

**¿Por qué la aplicación de portal de empresa necesitaba la protección de aplicaciones de Intune para funcionar con dispositivos Android?**<br></br>
La mayor parte de la función de protección de aplicaciones se integra en la aplicación de portal de empresa. La inscripción de dispositivos _no es obligatoria_ aunque la aplicación de portal de empresa se requiera siempre. Para MAM-WE, el usuario final solo necesita tener la aplicación de portal de empresa instalada en el dispositivo.

**¿Cómo funcionan en Android las opciones de protección de acceso de aplicaciones de Intune configuradas para el mismo conjunto de aplicaciones y usuarios?**<br></br>
Las directivas de protección de aplicaciones de Intune para el acceso se aplicarán en un orden específico en los dispositivos de usuario final cuando intenten obtener acceso a una aplicación de destino desde su cuenta corporativa. En general, tendría prioridad un bloqueo y, después, una advertencia descartable. Por ejemplo, si es aplicable a la aplicación o usuario específico, una configuración de versión de revisión mínima de Android que advierte al usuario de realizar una actualización de revisión se aplicará después de la configuración de versión de revisión mínima de Android que bloquea el acceso del usuario. Por tanto, en el caso en que el administrador de TI configure la versión de revisión de Android mínima en 01-03-2018 y la versión de revisión de Android mínima (solo advertencia) en 01-02-2018, mientras el dispositivo que intenta obtener acceso a la aplicación esté en una versión de revisión 01-01-2018, se bloquearía al usuario final en función del valor más restrictivo para la versión de revisión de Android mínima que provoque el bloqueo del acceso. 

Cuando se trabaja con diferentes tipos de configuraciones, un requisito de versión de la aplicación tendría prioridad, seguido por el requisito de versión de sistema operativo de Android y el requisito de versión de revisión de Android. Después, se comprueban en el mismo orden las advertencias para todos los tipos de configuración.

**Las directivas de Intune App Protection permiten a los administradores requerir que los dispositivos de usuario final pasen la atestación de SafetyNet de Google para dispositivos Android. ¿Con qué frecuencia se envía un nuevo resultado de atestación de SafetyNet al servicio?** <br><br> Se notificará una nueva determinación de servicio de Google Play a los administradores de TI con un intervalo determinado por el servicio Intune. La frecuencia de las llamadas de servicio está limitada debido a la carga y, por lo tanto, este valor se mantiene internamente y no es configurable. Cualquier acción que configure el administrador de TI para el valor de configuración de la atestación de SafetyNet de Google se realizará en función del último resultado notificado para el servicio de Intune en el momento del inicio condicional. Si no hay ningún dato, se permitirá el acceso siempre que no se produzcan errores en otras comprobaciones del inicio condiciona; en el back-end se iniciará un servicio de "recorrido de ida y vuelta" de Google Play para determinar los resultados de la atestación y se le solicitará al usuario de forma asincrónica si el dispositivo ha producido algún error. Si los datos disponibles son obsoletos, se permitirá o bloqueará el acceso en función del último resultado notificado; de forma similar, se iniciará un servicio de "recorrido de ida y vuelta" de Google Play para determinar los resultados de la atestación y se le pedirá al usuario de forma asincrónica si el dispositivo ha producido algún error.

**Las directivas de Intune App Protection permiten a los administradores requerir que los dispositivos de usuario final envíen señales a través de la Verify Apps API de Google para dispositivos Android. ¿Cómo puede un usuario final activar el examen de la aplicación para evitar que el acceso quede bloqueado debido a esto?**<br><br> Las instrucciones para hacerlo varían ligeramente en función del dispositivo. Lo habitual es ir a Google Play Store y, luego, hacer clic en **Mis aplicaciones y juegos**. A continuación, debe hacer clic en el resultado del último examen de la aplicación, lo que le llevará al menú de Play Protect. Asegúrese de que el conmutador **Buscas amenazas de seguridad en dispositivo** esté activado.

**¿Qué comprueba realmente la API de la atestación de SafetyNet de Google en los dispositivos Android? ¿Cuál es la diferencia entre los valores configurables de "Comprobar integridad básica" y "Comprobar integridad básica y dispositivos certificados"?** <br><br>
Intune aprovecha las API de SafetyNet de Google Play Protect para agregarlas a las comprobaciones de detección de rooting para dispositivos no inscritos. Google ha desarrollado y mantenido este conjunto de API para aplicaciones Android en caso de que no se quiera ejecutarlas en dispositivos con rooting. La aplicación Android Pay ha incorporado esto, por ejemplo. Aunque Google no comparte públicamente la totalidad de las comprobaciones de detección de rooting que se producen, esperamos que estas API detecten los usuarios que hayan aplicado el rooting en sus dispositivos. Después, se puede bloquear el acceso de estos usuarios o se pueden eliminar sus cuentas de empresa desde sus aplicaciones habilitadas para la directiva. "Comprobar integridad básica" muestra información sobre la integridad general del dispositivo. Por ejemplo, dispositivos con rooting, emuladores, dispositivos virtuales y cualquier otro dispositivo con signos de error de integridad básica por manipulación. "Comprobar integridad básica y dispositivos certificados" ofrece información sobre la compatibilidad del dispositivo con los servicios de Google. Solo superan esta comprobación aquellos dispositivos que no se han manipulado y están certificados por Google. Entre los dispositivos que producirán un error se incluyen los siguientes:

- Dispositivos que producen error en la integridad básica
- Dispositivos con un cargador de arranque desbloqueado
- Dispositivos con una imagen de sistema personalizada o ROM
- Dispositivos para los que el fabricante no ha solicitado o superado la certificación de Google 
- Dispositivos con una imagen de sistema creada directamente desde los archivos de origen del Android Open Source Program
- Dispositivos con una imagen de sistema de versión preliminar beta o de desarrollador

Consulte la [documentación de Google sobre la atestación de SafetyNet](https://developer.android.com/training/safetynet/attestation) para obtener detalles técnicos.

**Hay dos comprobaciones similares en la sección de inicio condicional al crear una directiva de Intune App Protection para dispositivos Android. ¿Debo hacer obligatorias las opciones de configuración "Atestación de dispositivo SafetyNet" o "Dispositivos con jailbreak o rooting"?** <br><br>
Las comprobaciones de la API de SafetyNet de Google Play Protect requieren que el usuario final esté en línea, al menos durante la ejecución del "recorrido de ida y vuelta" para determinar los resultados de atestación. Si el usuario final está sin conexión, el administrador de TI puede esperar igualmente que se exija un resultado de la configuración "Dispositivos con jailbreak o rooting". Dicho esto, si el usuario final ha estado sin conexión demasiado tiempo, se aplica el valor "Período de gracia sin conexión". Asimismo, cuando se alcanza este valor del temporizador, todo acceso a los datos profesionales o educativos se bloquea hasta que el acceso a la red esté disponible. Activar ambas opciones de configuración permite aplicar un enfoque por capas con el fin de mantener los dispositivos del usuario final en buen estado, lo que es importante cuando los usuarios finales acceden a los datos profesionales o educativos desde dispositivos móviles. 

**La configuración de directivas de protección de aplicaciones que utilicen las API de Google Play Protect requiere Google Play Services para su funcionamiento. ¿Qué ocurre si Google Play Services no se permite en la ubicación en la que se encuentre el usuario final?**<br><br>
Ambas opciones "Atestación de dispositivo SafetyNet" y "Examen de amenazas en las aplicaciones" requieren una versión determinada de Google Play Services para funcionar correctamente. Puesto que estas opciones de configuración corresponden al área de seguridad, si el usuario final es el destinatario de esta configuración y no dispone de la versión adecuada de Google Play Services o no tiene acceso a ella, se le bloqueará. 

## <a name="app-experience-on-ios"></a>Experiencia de aplicación en iOS
**¿Qué ocurre si se agrega o quita una huella digital o una cara en el dispositivo?**<br></br>
Las directivas de protección de aplicaciones de Intune permiten limitar el acceso a solo los usuarios con licencia de Intune. Una de las maneras de controlar el acceso a la aplicación es exigir Touch ID o Face ID de Apple en dispositivos admitidos. Intune implementa un comportamiento donde si hay algún cambio en la base de datos biométrica del dispositivo, Intune solicita al usuario un PIN cuando se alcanza el siguiente valor de tiempo de espera de inactividad. Los cambios realizados en los datos biométricos incluyen la incorporación o eliminación de una cara o una huella digital. Si el usuario de Intune no tiene establecido un PIN, se le lleva por los pasos para configurar uno.

La finalidad de esto es seguir manteniendo los datos de la organización dentro de la aplicación seguros y protegidos en el nivel de aplicación. Esta característica solo está disponible para iOS/iPadOS y requiere la participación de las aplicaciones que integran Intune App SDK para iOS/iPadOS, versión 9.0.1 o posterior. La integración del SDK es necesaria para poder aplicar el comportamiento en las aplicaciones de destino. Esta integración ocurre de manera gradual y depende de los equipos de la aplicación específica. Algunas aplicaciones participantes incluyen WXP, Outlook, Managed Browser y Yammer.
  
**Puedo usar la extensión de recursos compartidos de iOS para abrir los datos profesionales o educativos en aplicaciones no administradas, incluso con la directiva de transferencia de datos establecida en "Solo aplicaciones administradas" o "Ninguna aplicación". ¿No es esto una pérdida de datos?**<br></br>
La directiva de protección de aplicaciones de Intune no puede controlar la extensión de recursos compartidos de iOS sin administrar el dispositivo. Por lo tanto, Intune _**cifra los datos "corporativos" antes de compartirlos fuera de la aplicación**_. Puede validar esto intentando abrir el archivo "corporativo" fuera de la aplicación administrada. El archivo debe estar cifrado y no debe poder abrirse fuera de la aplicación administrada.

**¿Cómo funcionan en iOS las opciones de protección de acceso de aplicaciones de Intune configuradas para el mismo conjunto de aplicaciones y usuarios?**<br></br>
Las directivas de protección de aplicaciones de Intune para el acceso se aplicarán en un orden específico en los dispositivos de usuario final cuando intenten obtener acceso a una aplicación de destino desde su cuenta corporativa. En general, tendría prioridad un borrado, seguido de un bloqueo y, después, una advertencia descartable. Por ejemplo, si es aplicable a la aplicación o usuario específico, una configuración de sistema operativo mínima de iOS/iPadOS que advierte al usuario que actualice la versión de iOS/iPadOS se aplicará después de la configuración de sistema operativo mínima de iOS/iPadOS que bloquea el acceso del usuario. Por tanto, en el caso en que el administrador de TI configure el sistema operativo mínimo de iOS/iPadOS en 11.0.0.0 y el sistema operativo mínimo de iOS/iPadOS (solo advertencia) en 11.1.0.0, mientras el dispositivo que intenta acceder a la aplicación esté en iOS/iPadOS 10, se bloquearía al usuario final en función del valor más restrictivo para la versión de sistema operativo de iOS/iPadOS mínima que provoque el bloqueo del acceso.

Cuando se trabaja con diferentes tipos de configuraciones, un requisito de versión de Intune App SDK tendría prioridad, seguido por el requisito de versión de la aplicación y el requisito de versión del sistema operativo de iOS/iPadOS. Después, se comprueban en el mismo orden las advertencias para todos los tipos de configuración. Se recomienda configurar los requisitos de versión de Intune App SDK solo de acuerdo con las instrucciones del equipo de producto de Intune para escenarios de bloqueo esenciales.


## <a name="see-also"></a>Vea también
- [Implementar el plan de Intune](../fundamentals/planning-guide-onboarding.md)
- [Pruebas y validación de Intune](../fundamentals/planning-guide-test-validation.md)
- [Opciones de configuración de directiva de administración de aplicaciones móviles de Android en Microsoft Intune](../apps/app-protection-policy-settings-android.md)
- [Opciones de configuración de directiva de administración de aplicaciones móviles iOS/iPadOS](../apps/app-protection-policy-settings-ios.md)
- [Actualización de las directivas de protección de aplicaciones](../apps/app-protection-policy-delivery.md)
- [Validar las directivas de protección de aplicaciones](../apps/app-protection-policy-delivery.md)
- [Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos](../apps/app-configuration-policies-managed-app.md)
- [Cómo obtener soporte técnico para Microsoft Intune](../fundamentals/get-support.md)
