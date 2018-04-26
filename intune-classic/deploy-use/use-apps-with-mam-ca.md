---
title: Uso de aplicaciones con CA MAM
description: Comprenda los conceptos de cómo el acceso condicional para MAM puede ayudar a controlar qué aplicaciones tienen acceso a los servicios de Office 365.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 71dcf9bc-bfd1-4e06-b7ad-14b33a2288d0
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2f313fcbfa26c8f82708f8f830404da97a3eca25
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="what-to-expect-when-using-an-app-with-app-based-ca"></a>¿Qué se puede esperar al usar una aplicación con acceso condicional basado en la aplicación?

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

El acceso condicional basado en la aplicación comprueba la identidad de la aplicación aprobada por medio de una aplicación de agente que debe estar presente en el dispositivo:
*  En **iOS**, la **aplicación Azure Authenticator** es la aplicación de agente.
* En **Android**, la **aplicación Portal de empresa de Intune** es la aplicación de agente. 

A los usuarios finales que inician sesión por primera vez en una aplicación compatible con el acceso condicional basado en la aplicación, como OneDrive o Outlook, se les pedirá que instalen la aplicación de agente y registren el dispositivo en Azure AD. El registro del dispositivo en Azure AD (anteriormente conocido Workplace Join) creará un registro y un certificado del dispositivo con el que se emiten los tokens.  **No** es lo mismo que la **inscripción de MDM**. No existen perfiles de administración ni directivas que se apliquen y no hay ningún inventario tomado de las aplicaciones en el dispositivo.  Solo se realizará el proceso de instalación de la aplicación de agente y de registro del dispositivo en el primer uso de una aplicación administrada.

La siguiente es una lista de propiedades que se obtienen directamente del dispositivo:

* alternativeSecurityIds (huella digital de certificado de Azure Active Directory y hash de clave pública)
* deviceOSType
* deviceOSVersion
* displayName

> [!NOTE]
> En dispositivos Android:
>   * Es necesario que la aplicación Portal de empresa esté instalada en el dispositivo, pero no es necesario que el usuario final inicie sesión en esa aplicación.
>   * El registro de dispositivos se debe hacer mediante OneDrive o la aplicación Outlook.

## <a name="to-remove-a-device-from-azure-ad-registration"></a>Para quitar un dispositivo del registro de Azure AD
Es posible quitar el registro del dispositivo a través de la consola de administración de Azure AD, lo que suele llevar a cabo el administrador de TI.  También puede hacerlo el usuario final en el propio dispositivo.

* **Consola de administración de Azure AD**: en la consola de administración de Azure AD**, elimine el dispositivo que quiera quitar.
* **Dispositivo iOS**: abra la aplicación Azure Authenticator, desplácese a la izquierda en la cuenta y elija anular el registro.  
* **Dispositivo Android**: desinstale la aplicación de portal de empresa o elimine la cuenta de la **configuración del sistema**.

## <a name="app-based-ca-with-device-based-ca"></a>Entidad de certificación basada en la aplicación con entidad de certificación basada en dispositivos  

Puede configurar el [acceso condicional basado en el cumplimiento del dispositivo](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (<strong>acceso condicional del dispositivo</strong>) en la [consola de administrador de Intune](https://manage.microsoft.com) o en la [consola de administración de Azure AD Premium](https://manage.windowsazure.com). El acceso condicional del dispositivo requiere que los usuarios se conecten a Exchange Online solo a través de los dispositivos administrados por Intune que sean compatibles con la directiva de cumplimiento del dispositivo de Intune o equipos unidos a un dominio.  Si un usuario pertenece a uno o varios grupos de seguridad que tienen como destino las directivas del acceso condicional basado en la aplicación y del acceso condicional del dispositivo, este debe cumplir uno de los dos requisitos siguientes:
* La aplicación que se utiliza para acceder al servicio es una aplicación móvil compatible. 
* El dispositivo en el que se está ejecutando la aplicación tiene el **autenticador de iOS (para dispositivos iOS)** o la **aplicación del Portal de empresa (para dispositivos Android)** instalados.
* El dispositivo utilizado para acceder al servicio está **administrado y es conforme con Intune** con la directiva de cumplimiento del dispositivo de Intune o es un **equipo unido al dominio**.  Estos son algunos ejemplos para ayudar a ilustrar esto:
  * Si un usuario intenta conectarse desde la **aplicación nativa de correo electrónico de iOS**, deberá estar en un **dispositivo administrado y compatible**, ya que la aplicación nativa de correo electrónico no es compatible con el acceso condicional basado en la aplicación.
  * Si un usuario intenta conectarse desde un **equipo doméstico Windows**, se aplicará la **directiva del acceso condicional del dispositivo**, que requiere que debe usar un equipo unido al dominio.

## <a name="next-steps"></a>Pasos siguientes
[Creación de una directiva de Exchange Online para aplicaciones MAM](mam-ca-for-exchange-online.md)

[Bloqueo de aplicaciones que no usan la autenticación moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Vea también

[Protección de datos de aplicaciones con directivas de protección de aplicaciones](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
