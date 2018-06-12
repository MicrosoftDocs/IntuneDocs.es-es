---
title: Creación de una directiva de acceso condicional de Exchange
titlesuffix: Microsoft Intune
description: Configure el acceso condicional en Exchange local y en el entorno de Exchange Online heredado dedicado en Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a1476ad4237b6355d0cb87fcc643bf0234e7f457
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744778"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Cree una directiva de acceso condicional para Exchange local y en el entorno de Exchange Online dedicado heredado

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestra cómo configurar el acceso condicional para Exchange local en función del cumplimiento del dispositivo.

Si tiene un entorno de Exchange Online dedicado y necesita averiguar si es la configuración nueva o heredada, póngase en contacto con su administrador de cuentas. Para controlar el acceso de correo electrónico a Exchange local o a al entorno de Exchange Online dedicado heredado, configure el acceso condicional para Exchange local en Intune.

## <a name="before-you-begin"></a>Antes de comenzar

Antes de configurar el acceso condicional, compruebe lo siguiente:

- Su versión de Exchange debe ser **Exchange 2010 SP1 o posterior**. Se admite la matriz del servidor de acceso de cliente (CAS) del servidor de Exchange.

- Debe usar el [conector de Exchange local de Exchange Active Sync](exchange-connector-install.md), que conecta Intune con la instancia de Exchange local.

    >[!IMPORTANT]
    >El conector de Exchange local es específico de su inquilino de Intune y no puede usarlo con otro inquilino. Intune admite ahora varias instancias locales de Exchange Connector por suscripción. Si tiene más de una organización de Exchange local, puede configurar un conector independiente para cada organización de Exchange.

- El conector para una organización de Exchange local puede instalarse en cualquier máquina, siempre que esta pueda comunicarse con Exchange Server.

- El conector es compatible con el **entorno de CAS de Exchange**. Si le interesa, el conector se puede instalar técnicamente en el servidor CAS de Exchange directamente, pero no se recomienda porque aumenta la carga en el servidor. Al configurar el conector, debe permitir que se comunique con uno de los servidores CAS de Exchange.

- **Exchange ActiveSync** se debe configurar con autenticación basada en certificados o con la entrada de credenciales de usuario.

- Cuando se configuran directivas de acceso condicional y se aplican a un usuario, el **dispositivo** debe cumplir las condiciones siguientes para que los usuarios puedan conectarse al correo electrónico:
    - Debe estar **inscrito** en Intune o estar en un equipo unido a un dominio.
    - Debe estar **registrado en Azure Active Directory**. Además, el identificador de Exchange ActiveSync del cliente debe registrarse con Azure Active Directory.
<br></br>
- El servicio Registro de dispositivos (DRS) de Azure AD se activará automáticamente para los clientes de Intune y Office 365. Los clientes que ya han implementado el servicio de registro de dispositivos de ADFS no ven los dispositivos registrados en la instancia local de Active Directory. **Esto no se aplica a equipos de Windows ni a dispositivos Windows Phone.**

- **Cumplir** todas las directivas de cumplimiento de dispositivos implementadas en ese dispositivo.

- Si el dispositivo no cumple la configuración de acceso condicional, cuando el usuario inicie sesión verá uno de los siguientes mensajes:
    - Si el dispositivo no está inscrito en Intune, o no está registrado en Azure Active Directory, se mostrará un mensaje con instrucciones sobre cómo instalar la aplicación Portal de empresa, inscribir el dispositivo y activar el correo electrónico. Este proceso también asocia el identificador de Exchange ActiveSync del dispositivo con el registro del dispositivo en Azure Active Directory.
    - Si el dispositivo no es conforme, se muestra un mensaje que dirige al usuario al sitio web del Portal de empresa de Intune o a la aplicación Portal de empresa, donde podrá encontrar información sobre el problema y cómo resolverlo.

### <a name="support-for-mobile-devices"></a>Compatibilidad con dispositivos móviles

- Windows Phone 8.1 y versiones posteriores
- Aplicación de correo electrónico nativo de iOS.
- Clientes de correo EAS como Gmail en Android 4 o versiones posteriores
- **Dispositivos Android for Work de clientes de correo EAS:** solo se admiten las aplicaciones **Gmail** y **Nine Work** en el **perfil de trabajo** en los dispositivos Android for Work. Para que el acceso condicional funcione con Android for Work, debe implementar un perfil de correo electrónico para la aplicación Gmail o Nine Work y también implementar esas aplicaciones como una instalación necesaria.

> [!NOTE]
> La aplicación Microsoft Outlook para iOS y Android no es compatible. 

### <a name="support-for-pcs"></a>Compatibilidad para equipos

La aplicación **Correo** nativa en Windows 8.1 y versiones posteriores (cuando se inscribe en Intune).


## <a name="configure-exchange-on-premises-access"></a>Configuración del acceso a Exchange local

1. Vaya a [Azure Portal](https://portal.azure.com/) e inicie sesión con sus credenciales de Intune.

1. Después de iniciar sesión correctamente, verá el **Panel de Azure**.

1. Elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

1. Elija **Intune** y aparecerá el **panel de Intune**.

1. Elija **Acceso local**. El panel **Acceso local** muestra el estado de la directiva de acceso condicional y los dispositivos que se ven afectados por ella.

1. En **Administrar**, elija **Acceso local a Exchange**.

1. En el panel **Acceso local a Exchange**, elija **Sí** para habilitar el control de acceso local a Exchange.

    > [!NOTE]
    > Si no ha configurado un conector de Exchange Active Sync local, esta opción se deshabilita.  Primero debe instalar y configurar al menos un conector antes de habilitar el acceso condicional para Exchange local. Para más información, consulte [Install the Intune On-premises Exchange Connector](exchange-connector-install.md) (Instalación del conector de Exchange local para Intune).

1. En **Asignación**, elija **Grupos incluidos**.  Use el grupo de usuarios de seguridad que debería tener aplicado el acceso condicional. Para ello, es necesario que los usuarios hayan inscrito sus dispositivos en Intune y que satisfagan los perfiles de cumplimiento.

1. Si quiere excluir determinados grupos de usuarios, puede hacerlo; para ello, elija **Grupos excluidos** y seleccione un grupo de usuarios al que quiera que se le exima de exigir la inscripción y el cumplimiento del dispositivo.

1. En **Configuración**, elija **Notificaciones de usuario** para modificar el mensaje de correo electrónico predeterminado. Este mensaje se envía a los usuarios si su dispositivo no es conforme y quieren acceder a Exchange local. La plantilla de mensaje usa lenguaje de marcado.  También puede ver la vista previa del mensaje mientras escribe.
    > [!TIP]
    > Para más información sobre el lenguaje de marcado, consulte este [artículo](https://en.wikipedia.org/wiki/Markup_language) en Wikipedia.

1. En el panel **Configuración avanzada de acceso a Exchange ActiveSync**, establezca la regla predeterminada global para el acceso desde dispositivos que no están administrados por Intune y para reglas de nivel de plataforma, como se describe en los dos pasos siguientes.

1. En dispositivos a los que no les afecta las reglas de acceso condicional o de otro tipo, puede optar por permitirles acceder a Exchange o bloquearlo.

   - Si configura esta opción para permitir el acceso, todos los dispositivos pueden acceder a Exchange local inmediatamente.  Los dispositivos que pertenecen a los usuarios de **Grupos incluidos** se bloquean si se evalúan posteriormente como no conformes con las directivas de cumplimiento o no inscritos en Intune.
   - Si configura esta opción para bloquear el acceso, se bloquea inmediatamente a todos los dispositivos el acceso a Exchange local inicialmente.  Los dispositivos que pertenecen a los usuarios de **Grupos incluidos** tienen acceso una vez que el dispositivo esté inscrito en Intune y se evalúe como conforme. En dispositivos Android que no ejecuten Samsung Knox Standard el acceso siempre está bloqueado, ya que no admiten esta configuración.

1. En **Excepciones de la plataforma de dispositivo**, elija **Agregar** para especificar las plataformas. Si el valor **Acceso a dispositivos no administrados** está establecido en **Bloqueado**, se permiten los dispositivos inscritos y conformes incluso si hay una excepción de plataforma para bloquear. Elija **Aceptar** para guardar la configuración.

1. En el panel **Local**, haga clic en **Guardar** para guardar la directiva de acceso condicional.

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Creación de directivas de acceso condicional de Azure AD en Intune

A partir de la versión 1704 de Intune, los administradores pueden crear directivas de acceso condicional de Azure AD desde Azure Portal de Intune, de forma que no tiene que cambiar entre las cargas de trabajo de Azure e Intune.

> [!IMPORTANT]
> Para crear directivas de acceso condicional de Azure AD desde el portal de Azure de Intune, debe disponer de una licencia de Azure AD Premium.

### <a name="to-create-azure-ad-conditional-access-policy"></a>Para crear una directiva de acceso condicional de Azure AD

1. En el **panel de Intune**, elija **Acceso condicional**.

2. En el panel **Directivas**, elija **Nueva directiva** para crear la directiva de acceso condicional de Azure AD.

## <a name="see-also"></a>Vea también

[Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
