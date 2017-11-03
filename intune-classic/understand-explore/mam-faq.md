---
title: "Preguntas más frecuentes sobre MAM y la protección de la aplicación"
description: "Este artículo proporciona respuestas a algunas preguntas frecuentes en la administración de aplicaciones móvil de Intune (MAM) y la protección de aplicaciones de Intune."
keywords: 
author: oydang
ms.author: oydang
manager: angrobe
ms.date: 10/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6ba1d1d9d0b1c21c364ef97f8340157a94ae996b
ms.sourcegitcommit: 623c52116bc3fdd12680b9686dcd0e1eeb6ea5ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Preguntas más frecuentes sobre MAM y la protección de la aplicación

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este artículo proporciona respuestas a algunas preguntas frecuentes sobre la administración de aplicaciones móviles (MAM) de Intune y la protección de aplicaciones de Intune.

## <a name="mam-basics"></a>Conceptos básicos de MAM


**¿Qué es MAM?** La [administración de aplicaciones móviles de Intune](/intune/app-lifecycle) hace referencia al conjunto de funciones de administración de Intune que le permite publicar, insertar, configurar, proteger, supervisar y actualizar aplicaciones móviles para los usuarios.

**¿Cuáles son las ventajas de la protección de aplicaciones MAM?** MAM protege los datos de la organización dentro de una aplicación. Con MAM-WE, una aplicación profesional o educativa que contiene información confidencial puede administrarse en casi cualquier dispositivo, incluidos los dispositivos personales en escenarios de Bring your own device (BYOD, traiga su propio dispositivo). Muchas aplicaciones de productividad, como las aplicaciones de Microsoft Office, pueden administrarse mediante Intune MAM. Consulte la lista oficial de [aplicaciones habilitadas para Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), disponible para uso público.

**¿Qué configuraciones de dispositivo admite MAM?** Intune MAM admite dos configuraciones:
  1. **MDM Intune + MAM**: esta es la primera configuración admitida por MAM cuando se publicó por primera vez. Los administradores de TI solo pueden administrar aplicaciones mediante directivas de protección de aplicaciones y MAM en los dispositivos que están inscritos con la administración de dispositivos móviles (MDM) de Intune. Para administrar aplicaciones con MDM + MAM, los clientes deben utilizar la consola de Intune independiente en https://manage.microsoft.com.

  2. **MAM sin inscripción de dispositivo**: MAM sin inscripción de dispositivos o MAM-WE permite a los administradores de TI administrar aplicaciones mediante directivas de protección de aplicaciones y MAM en dispositivos no inscritos con Intune MDM. Esto significa que las aplicaciones pueden administrarse mediante Intune en dispositivos inscritos con proveedores de EMM de terceros. Para administrar aplicaciones mediante MAM-WE, los clientes deben usar la consola en Azure Portal, en http://portal.azure.com.


## <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

¿**Qué son las directivas de protección de aplicaciones**? Las directivas de protección de aplicaciones que garantizan los datos de la organización siguen siendo seguras o se encuentran en una aplicación administrada. Una directiva puede ser una regla que se aplica cuando el usuario intenta obtener acceso o mover datos "corporativos" o un conjunto de acciones que están prohibidas o que se supervisan cuando el usuario está dentro de la aplicación.

**¿Cuáles son los ejemplos de directivas de protección de aplicaciones?** Consulte la [configuración de directivas de protección de aplicaciones Android](../deploy-use/android-mam-policy-settings.md) y la [configuración de la protección de aplicaciones iOS](../deploy-use/ios-mam-policy-settings.md) para obtener información detallada sobre cada configuración de directiva de protección de la aplicación.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplicaciones que puede administrar con directivas de protección de aplicaciones

**¿Qué aplicaciones se pueden administrar mediante directivas de protección de aplicaciones?** Cualquier aplicación enriquecida mediante [Intune App SDK](/intune/app-sdk) o encapsulada mediante la [ herramienta de ajuste de aplicaciones de Intune ](/intune/apps-prepare-mobile-application-management) puede administrarse con las directivas de protección de aplicaciones de Intune. Consulte la lista oficial de [aplicaciones habilitadas para Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), disponible para uso público.

**¿Cuáles son los requisitos básicos para utilizar directivas de protección de aplicaciones en una aplicación habilitada para Intune?**
  1. El usuario final debe tener una cuenta de Azure Active Directory (AAD). Consulte [Agregar usuarios y conceder permiso administrativo a Intune](/intune/users-permissions-add) para aprender a crear usuarios de Intune en Azure Active Directory.

  2. El usuario final debe tener una licencia de Microsoft Intune asignada a su cuenta de Azure Active Directory. Consulte [Administrar licencias de Intune](/intune/licenses-assign) para obtener información sobre cómo asignar licencias de Intune a los usuarios finales.

  3. El usuario final debe pertenecer a un grupo de seguridad de destino de una directiva de protección de la aplicación. La misma directiva de protección de aplicaciones debe tener como destino la aplicación específica que se va a utilizar. Las directivas de protección de aplicaciones pueden crearse e implementarse en la consola de Intune en el [portal de Azure](http://portal.azure.com). Actualmente, se pueden crear grupos de seguridad en el [portal de Office](http://portal.office.com).

  4. El usuario final debe iniciar sesión en la aplicación con su cuenta de AAD.

**¿Cuáles son los requisitos adicionales para usar la [aplicación móvil de Outlook](https://www.microsoft.com/outlook-com/mobile/)?**

  1. El usuario final debe tener la aplicación móvil de Outlook instalada en su dispositivo.

  2. El usuario final debe tener una licencia y buzón de correo de [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) vinculados a su cuenta de Azure Active Directory.

  >[!NOTE]
  > Actualmente, la aplicación móvil de Outlook solo es compatible con Microsoft Exchange Online y no admite Exchange local o Exchange en Office 365 dedicado.

**¿Cuáles son los requisitos adicionales para usar las aplicaciones [Word, Excel y PowerPoint](https://products.office.com/business/office)?**

  1. El usuario final debe tener una licencia de [Office 365 Empresa o Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) asignada a su cuenta de Azure Active Directory. La suscripción debe incluir las aplicaciones de Office en dispositivos móviles y puede incluir una cuenta de almacenamiento en la nube con [OneDrive para la Empresa](https://onedrive.live.com/about/business/). Las licencias de Office 365 se pueden asignar en el [portal de Office](http://portal.office.com) siguiendo estas [instrucciones](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

  2. El usuario final debe tener una ubicación administrada configurada con la funcionalidad pormenorizada Guardar como en la configuración de directiva de protección de aplicaciones "Impedir Guardar como". Por ejemplo, si la ubicación administrada es OneDrive, la aplicación [OneDrive](https://onedrive.live.com/about/) debe estar configurada en la aplicación Word, Excel o PowerPoint del usuario final.

  3. Si la ubicación administrada es OneDrive, la directiva de protección de aplicaciones implementada para el usuario final debe tener como destino la aplicación.

  >[!NOTE]
  > Las aplicaciones móviles de Office actualmente solo admiten SharePoint Online y no SharePoint local.

**¿Por qué se necesita una ubicación administrada (como OneDrive) para Office?** Intune marca todos los datos de la aplicación como "empresa" o "personal". Los datos se consideran "corporativos" cuando se originan desde una ubicación de la empresa. Para las aplicaciones de Office, Intune considera las siguientes ubicaciones de la empresa: correo electrónico (Exchange) o almacenamiento en la nube (aplicación OneDrive con una cuenta de OneDrive para la Empresa).

**¿Cuáles son los requisitos adicionales para usar Skype Empresarial?** Consulte los requisitos de licencias de [Skype Empresarial](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > La aplicación móviles Skype Empresarial admite actualmente solo Skype Empresarial Online.

## <a name="app-protection-features"></a>Funciones de protección de aplicaciones

**¿Qué es la compatibilidad con varias identidades?** La compatibilidad con varias identidades es la capacidad para Intune App SDK de solo aplicar las directivas de protección de aplicaciones a la cuenta profesional o educativa con la que se ha iniciado sesión en la aplicación. Si se ha iniciado sesión en la aplicación con una cuenta personal, los datos no se modifican.

**¿Cuál es el propósito de la compatibilidad con varias identidades?** La compatibilidad con varias identidades permite que aplicaciones con audiencias "corporativas" y de consumidor (por ejemplo, las aplicaciones de Office) se lancen públicamente con funcionalidad de protección de aplicaciones de Intune para las cuentas "corporativas".

**¿Cuándo se muestra la pantalla de PIN?** La pantalla de PIN de Intune solo aparece cuando el usuario está intentando obtener acceso a datos "corporativos" en la aplicación. Por ejemplo, en aplicaciones de Word, Excel, o PowerPoint, aparecería cuando el usuario final intentara abrir un documento desde OneDrive para la empresa (suponiendo que se implementó correctamente una directiva de protección de aplicaciones que aplica el PIN).

**¿Qué sucede con Outlook y varias identidades?** Puesto que Outlook tiene una vista de correo electrónico combinada de correos electrónicos personales y "corporativos", la aplicación Outlook solicita el PIN de Intune al iniciarse.

**¿Qué es el PIN de la aplicación de Intune?** El número de identificación personal (PIN) es un código de acceso que se utiliza para comprobar que el usuario correcto está obteniendo acceso a los datos de la organización en una aplicación.

  1. **¿Cuándo se solicita al usuario que especifique el PIN?** Intune solo le solicitará el PIN de la aplicación del usuario cuando este esté a punto de obtener acceso a los datos "corporativos". En las aplicaciones de varias identidades, como Word, Excel o PowerPoint, se solicitará al usuario el PIN cuando intente abrir un archivo o documento "corporativos". En las aplicaciones de una sola identidad, como las aplicaciones de línea de negocio enriquecidas mediante la herramienta de ajuste de aplicaciones de Intune, el PIN se solicita en el inicio, ya que Intune App SDK sabe que la experiencia del usuario en la aplicación siempre es "corporativa".

  2. **¿Es seguro el PIN?** El PIN sirve para permitir que solo el usuario correcto disponga de acceso a los datos de su organización en la aplicación. Por lo tanto, el usuario debe iniciar sesión con su cuenta profesional o educativa para poder establecer o restablecer el PIN de la aplicación de Intune. Esta autenticación se controla mediante Azure Active Directory a través del intercambio de token seguros y no es transparente para Intune App SDK. Desde una perspectiva de seguridad, la mejor manera de proteger los datos profesionales o educativos es cifrarlos. El cifrado no está relacionado con el PIN de la aplicación, pero tiene su propia directiva de protección de aplicaciones.

  3. **¿Cómo protege el PIN contra ataques por fuerza bruta Intune?** Como parte de la directiva de PIN de la aplicación, el administrador de TI puede establecer el número máximo de veces que un usuario puede intentar autenticar su PIN antes de bloquear la aplicación. Después de que se haya cumplido el número de intentos, Intune App SDK puede borrar los datos "corporativos" en la aplicación.
  
**¿Cómo funciona el PIN de la aplicación Intune entre el tipo numérico y el tipo de código de acceso?**
MAM permite actualmente un PIN de nivel de aplicación (iOS) con caracteres alfanuméricos y especiales (llamado "código de acceso"), el que requiere la participación de aplicaciones (como WXP, Outlook, Managed Browser, Yammer) para integrar el SDK de aplicaciones de Intune para iOS. Sin esto, la configuración de código de acceso no se aplica correctamente en las aplicaciones de destino. Como las aplicaciones seguirán esta integración de manera gradual, el comportamiento entre el PIN numérico y el código de acceso se cambia temporalmente para el usuario final y requiere una aclaración importante. Para la versión de octubre de 2017 de Intune, el comportamiento es el siguiente...

Las aplicaciones que
1. tienen el mismo editor de aplicaciones
2. tienen un PIN de código de acceso de destino a través de la consola y 
3. adoptaron el SDK con esta característica (v 7.1.12+) podrán compartir el código de acceso entre estas aplicaciones. 

Las aplicaciones que
1. tienen el mismo editor de aplicaciones
2. tienen un PIN numérico de destino a través de la consola podrán compartir el PIN numérico entre estas aplicaciones. 

**¿Qué sucede con el cifrado?** Los administradores de TI pueden implementar una directiva de protección de aplicaciones que requiere cifrar los datos de aplicaciones. Como parte de la directiva, el administrador de TI también puede especificar cuándo se cifra el contenido.

  1. **¿Cómo cifra Intune los datos?** Consulte la [configuración de directivas de protección de aplicaciones Android](../deploy-use/android-mam-policy-settings.md) y la [configuración de la protección de aplicaciones iOS](../deploy-use/ios-mam-policy-settings.md) para obtener información detallada sobre la configuración de directiva de protección de aplicaciones de cifrado.

  2. **¿Qué se cifra?** Solo se cifran los datos marcados como "corporativos" según la directiva de protección de la aplicación del administrador de TI. Los datos se consideran "corporativos" cuando se originan desde una ubicación de la empresa. Para las aplicaciones de Office, Intune considera las siguientes ubicaciones de la empresa: correo electrónico (Exchange) o almacenamiento en la nube (aplicación OneDrive con una cuenta de OneDrive para la Empresa). Para las aplicaciones de línea de negocio habilitadas por la herramienta de ajuste de aplicaciones de Intune, todos los datos de aplicaciones se consideran "corporativos".

**¿Cómo Intune borra los datos de forma remota?** Intune puede borrar los datos de la aplicación de tres maneras diferentes: borrado completo del dispositivo, borrado selectivo para MDM y borrado selectivo de MAM. Para obtener más información sobre el borrado remoto para MDM, consulte [Ayudar a proteger sus datos con el borrado completo o selectivo con Microsoft Intune](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md). Para obtener más información acerca del borrado selectivo mediante MAM, consulte [Borrar los datos administrados de la aplicación de la empresa con Microsoft Intune](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md)

  1. **¿Qué es el borrado completo?** [Borrado completo](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe) quita todos los datos de usuario y la configuración del **dispositivo** restaurando el dispositivo a la configuración predeterminada de fábrica. El dispositivo se quita de Intune.
  >[!NOTE]
  > El borrado completo solo se puede lograr en dispositivos inscritos con la administración de dispositivos móviles de Intune (MDM).

  2. **¿Qué es el borrado selectivo para MDM?** Consulte [Ayudar a proteger los datos con el borrado selectivo o completo mediante Microsoft Intune](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) para leer sobre el borrado selectivo.

  3. **¿Qué es el borrado selectivo para MAM?** El borrado selectivo de MAM simplemente quita los datos de la aplicación de empresa de la aplicación. La solicitud se inicia mediante el Portal de Intune Azure. Para obtener información sobre cómo iniciar una solicitud de borrado, consulte [Borrar los datos administrados de la aplicación de la empresa con Microsoft Intune](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md)

  4. **¿Con qué rapidez se produce el borrado selectivo para MAM?** Si el usuario está utilizando la aplicación cuando se inicia el borrado selectivo, Intune App SDK comprueba cada 30 minutos una solicitud de borrado selectivo desde el servicio Intune MAM. También comprueba el borrado selectivo cuando el usuario inicia la aplicación por primera vez e inicia sesión con su cuenta profesional o educativa.

**¿Por qué no funcionan los servicios locales con aplicaciones protegidas de Intune?** La protección de aplicaciones de Intune depende de la identidad del usuario para ser coherente entre la aplicación e Intune App SDK. La única manera de garantizar esto es a través de la autenticación moderna. Hay escenarios en los que las aplicaciones pueden funcionar con una configuración local, pero no son coherentes ni ofrecen garantías.

**¿Hay una forma segura de abrir vínculos web desde aplicaciones administradas?** Sí. El administrador de TI puede implementar y establecer una directiva de protección de aplicaciones para la [aplicación Intune Managed Browser](../deploy-use/manage-internet-access-using-managed-browser-policies.md), un explorador web desarrollado por Microsoft Intune que puede administrarse fácilmente con Intune. El administrador de TI puede requerir que todos los vínculos web en aplicaciones habilitadas para Intune se abran con la aplicación Managed Browser.


## <a name="app-experience-on-android"></a>Experiencia de la aplicación en Android

**¿Por qué la aplicación de portal de empresa necesitaba la protección de aplicaciones de Intune para funcionar con dispositivos Android?** La mayor parte de la función de protección de aplicaciones se integra en la aplicación de portal de empresa. La inscripción de dispositivos _no es obligatoria_ aunque la aplicación de portal de empresa se requiera siempre. Para MAM-WE, el usuario final solo necesita tener la aplicación de portal de empresa instalada en el dispositivo.

## <a name="app-experience-on-ios"></a>Experiencia de aplicación en iOS

**Puedo usar la extensión de recursos compartidos de iOS para abrir los datos profesionales o educativos en aplicaciones no administradas, incluso con la directiva de transferencia de datos establecida en "Solo aplicaciones administradas" o "Ninguna aplicación". ¿No es esto una pérdida de datos?** La directiva de protección de aplicaciones de Intune no puede controlar la extensión de recursos compartidos de iOS sin administrar el dispositivo. Por lo tanto, Intune _**cifra los datos "corporativos" antes de compartirlos fuera de la aplicación**_. Puede validar esto intentando abrir el archivo "corporativo" fuera de la aplicación administrada. El archivo debe estar cifrado y no debe poder abrirse fuera de la aplicación administrada.

### <a name="see-also"></a>Consulte también
- [Opciones de configuración de directiva de administración de aplicaciones móviles de Android en Microsoft Intune](../deploy-use/android-mam-policy-settings.md)
- [Opciones de configuración de directiva de administración de aplicaciones móviles iOS](../deploy-use/ios-mam-policy-settings.md)
- [Validar la configuración de administración de aplicaciones móviles](../deploy-use/validate-mobile-application-management.md)
- [Preparación para configurar directivas de administración de aplicaciones móviles con Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [Cómo obtener soporte técnico para Microsoft Intune](../troubleshoot/how-to-get-support-for-microsoft-intune.md)
