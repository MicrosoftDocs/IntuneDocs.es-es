---
title: Creación de una directiva de acceso condicional de Exchange
titleSuffix: Microsoft Intune
description: Configure el acceso condicional en Exchange local y en el entorno de Exchange Online dedicado heredado en Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 644297777e8a103d6ffdc5f025ebf8f29591fda8
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188465"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Creación de una directiva de acceso condicional para Exchange local y en el entorno de Exchange Online dedicado heredado

En este artículo se muestra cómo configurar el acceso condicional para Exchange local en función del cumplimiento del dispositivo.

Si tiene un entorno de Exchange Online dedicado y necesita averiguar si es la configuración nueva o heredada, póngase en contacto con su administrador de cuentas. Para controlar el acceso de correo electrónico a Exchange local o al entorno de Exchange Online dedicado heredado, configure el acceso condicional a Exchange local en Intune.

## <a name="before-you-begin"></a>Antes de comenzar

Antes de configurar el acceso condicional, compruebe que existen las siguientes configuraciones:

- Su versión de Exchange es **Exchange 2010 SP1 o posterior**. Se admite la matriz del servidor de acceso de cliente (CAS) del servidor de Exchange.

- Ha instalado y usa la instancia de [On-Premises Exchange Connector de Exchange Active Sync](exchange-connector-install.md), que conecta Intune con Exchange local.

    >[!IMPORTANT]  
    >Intune admite varias instancias de On-premises Exchange Connector por suscripción.  Sin embargo, cada instancia de On-Premises Exchange Connector es específica de un solo inquilino de Intune y no puede usarse con otro inquilino.  Si tiene más de una organización de Exchange local, puede configurar un conector independiente para cada organización de Exchange.

- El conector para una organización de Exchange local puede instalarse en cualquier máquina, siempre que esta pueda comunicarse con el servidor Exchange.

- El conector es compatible con el **entorno de CAS de Exchange**. Intune admite la instalación directa del conector en el servidor CAS de Exchange. Se recomienda instalarlo en un equipo independiente debido a la carga adicional que el conector supone para el servidor. Al configurar el conector, debe permitir que se comunique con uno de los servidores CAS de Exchange.

- **Exchange ActiveSync** se debe configurar con autenticación basada en certificados o con la entrada de credenciales de usuario.

- Cuando se configuran directivas de acceso condicional y se aplican a un usuario, el **dispositivo** debe cumplir las condiciones siguientes para que los usuarios puedan conectarse al correo electrónico:
  - Debe estar **inscrito** en Intune o estar en un equipo unido a un dominio.
  - Debe estar **registrado en Azure Active Directory**. Además, el identificador de Exchange ActiveSync del cliente debe registrarse con Azure Active Directory.

- El servicio Registro de dispositivos (DRS) de Azure AD se activará automáticamente para los clientes de Intune y Office 365. Los clientes que ya han implementado el servicio de registro de dispositivos de ADFS no ven los dispositivos registrados en la instancia local de Active Directory. **Esto no se aplica a equipos de Windows ni a dispositivos Windows Phone.**

- **Cumplir** todas las directivas de cumplimiento de dispositivos implementadas en ese dispositivo.

- Si el dispositivo no cumple la configuración de acceso condicional, cuando el usuario inicie sesión verá uno de los siguientes mensajes:
  - Si el dispositivo no está inscrito en Intune o no está registrado en Azure Active Directory, se muestra un mensaje con instrucciones sobre cómo instalar la aplicación Portal de empresa, inscribir el dispositivo y activar el correo electrónico. Este proceso también asocia el identificador de Exchange ActiveSync del dispositivo con el registro del dispositivo en Azure Active Directory.
  - Si el dispositivo no es conforme, se muestra un mensaje que dirige al usuario al sitio web del Portal de empresa de Intune o a la aplicación Portal de empresa. En el portal de empresa pueden encontrar información sobre el problema y sobre cómo resolverlo.

### <a name="support-for-mobile-devices"></a>Compatibilidad con dispositivos móviles

- Windows Phone 8.1 y versiones posteriores
- Aplicación de correo electrónico nativo de iOS.
- Clientes de correo EAS como Gmail en Android 4 o versiones posteriores
- **Dispositivos del perfil de trabajo Android** de clientes de correo EAS: solo se admiten las aplicaciones **Gmail** y **Nine Work for Android Enterprise** en el **perfil de trabajo** en los dispositivos de perfil de trabajo Android. Para que el acceso condicional funcione con perfiles de trabajo Android, debe implementar un perfil de correo electrónico para la aplicación Gmail o Nine Work for Android Enterprise, y también implementar esas aplicaciones como una instalación necesaria.

> [!NOTE]
> No se admite Microsoft Outlook para iOS y Android a través del conector local de Exchange. Si desea aprovechar las directivas de acceso condicional de Azure Active Directory y las directivas de Intune App Protection con Outlook para iOS y Android en los buzones locales, vea la página sobre [uso de autenticación moderna híbrida con Outlook para iOS y Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

### <a name="support-for-pcs"></a>Compatibilidad para equipos

La aplicación **Correo** nativa en Windows 8.1 y versiones posteriores (cuando se inscribe en MDM con Intune).

## <a name="configure-exchange-on-premises-access"></a>Configuración del acceso a Exchange local

Para poder usar el siguiente procedimiento para configurar el control de acceso local a Exchange, debe instalar y configurar al menos una instancia de [Intune On-Premises Exchange Connector](exchange-connector-install.md) para Exchange local.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Vaya a **Administración de inquilinos** > **Acceso de Exchange** y **seleccione Acceso local a Exchange**.

3. En el panel **Acceso local a Exchange**, elija **Sí** para *habilitar el control de acceso local a Exchange*.

4. En **Asignación**, elija **Seleccionar grupos para incluir** y, a continuación, seleccione uno o varios grupos para configurar el acceso.

   Los miembros de los grupos que seleccione tendrán aplicada la directiva de acceso condicional para el acceso local a Exchange. Los usuarios que reciben esta directiva deben inscribir sus dispositivos en Intune y ser compatibles con los perfiles de cumplimiento para poder tener acceso a Exchange local.

5. Para excluir grupos, elija **Seleccionar grupos para excluir** y, a continuación, seleccione uno o varios grupos que estén exentos de los requisitos para inscribir dispositivos y sean compatibles con los perfiles de cumplimiento para tener acceso a Exchange local. 

6. A continuación, configure las opciones de Intune On-Premises Exchange Connector.  En **Configuración**, en la ventana *Acceso local a Exchange*, seleccione **Exchange ActiveSync Connector local** y, luego, seleccione el conector para la organización de Exchange que quiere configurar.

7. En **Configuración**, elija **Notificaciones de usuario** para modificar el mensaje de correo electrónico predeterminado que se envía a los usuarios si su dispositivo no es compatible y quieren tener acceso a Exchange local. La plantilla de mensaje usa lenguaje de marcado.  También puede ver la vista previa del mensaje mientras escribe.
   > [!TIP]
   > Para más información sobre el lenguaje de marcado, consulte este [artículo](https://en.wikipedia.org/wiki/Markup_language) en Wikipedia.
 
   Seleccione **Aceptar** para guardar sus ediciones a fin de completar la configuración del acceso local a Exchange.

8. A continuación, seleccione **Configuración avanzada de acceso a Exchange ActiveSync** para abrir el panel *Configuración avanzada de acceso a Exchange ActiveSync* donde configura las reglas de acceso de dispositivo:  

   - En **Acceso a dispositivos no administrados**, establezca la regla predeterminada global para el acceso desde dispositivos que no se vean afectados por el acceso condicional u otras reglas:

     - **Permitir acceso**: todos los dispositivos pueden tener acceso a Exchange local inmediatamente. Los dispositivos que pertenecen a los usuarios de los grupos que configuró como incluidos en el procedimiento anterior se bloquean si se evalúan posteriormente como no conformes con las directivas de cumplimiento o no inscritos en Intune.

     - **Bloquear acceso** y **Cuarentena**: se bloquea inmediatamente a todos los dispositivos el acceso a Exchange local inicialmente. Los dispositivos que pertenecen a los usuarios de los grupos que configuró como incluidos en el procedimiento anterior obtienen acceso una vez que el dispositivo se inscribe en Intune y se evalúa como conforme. 

       Los dispositivos Android que *no* ejecutan Samsung Knox Standard no admiten esta configuración y siempre están bloqueados.

   -  En **Excepciones de la plataforma de dispositivo**, seleccione **Agregar** y, a continuación, especifique detalles de la plataforma según sea necesario para su entorno. 
   
      Si el valor **Acceso a dispositivos no administrados** está establecido en **Bloqueado**, se permiten los dispositivos inscritos y conformes aunque haya una excepción de plataforma para bloquearlos.  
   
   Seleccione **Aceptar** para guardar las ediciones.

9. Seleccione **Guardar** para guardar la directiva de acceso condicional de Exchange.

A continuación, cree una directiva de cumplimiento y asígnela a los usuarios para que Intune evalúe sus dispositivos móviles. Consulte [Introducción al cumplimiento de dispositivos](device-compliance-get-started.md).

## <a name="next-steps"></a>Pasos siguientes

[Solución de problemas de Intune Exchange Connector local en Microsoft Intune](https://support.microsoft.com/help/4471887)
