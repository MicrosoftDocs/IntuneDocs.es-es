---
title: "Creación y asignación de directiva de acceso condicional de Exchange local"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: cómo configurar el acceso condicional para Exchange local y Exchange Online heredado dedicado en Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 2a011bf390bb55d685f580cfc782b21ff0c2ebd5
ms.lasthandoff: 04/26/2017


---

# <a name="how-to-create-and-assign-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated-in-microsoft-intune-azure-preview"></a>Creación y asignación de una directiva de acceso condicional para Exchange local y Exchange Online heredado dedicado en la versión preliminar de Azure Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Este tema le guiará en el proceso de configuración del acceso condicional para Exchange local basado en el cumplimiento de dispositivos.

Si tiene un entorno de Exchange Online dedicado y necesita averiguar si es la configuración nueva o heredada, póngase en contacto con su administrador de cuentas. Para controlar el acceso de correo electrónico a Exchange local o a al entorno de Exchange Online dedicado heredado, configure el acceso condicional para Exchange local en Intune.

## <a name="before-you-begin"></a>Antes de comenzar

Antes de configurar el acceso condicional, compruebe lo siguiente:

- Su versión de Exchange debe ser **Exchange 2010 SP1 o posterior**. Se admite la matriz del servidor de acceso de cliente (CAS) del servidor de Exchange.

- Debe usar el [conector de Exchange local de Exchange Active Sync](https://docs.microsoft.com/intune-azure/conditional-access/install-intune-on-premises-exchange-connector), que conecta Intune con la instancia de Exchange local.

    >[!IMPORTANT]
    >El conector de Exchange local es específico de su inquilino de Intune y no puede usarlo con otro inquilino. También debe asegurarse de que la versión de Exchange Connector del inquilino esté instalada **en un solo equipo**.

- El conector puede instalarse en cualquier máquina, siempre que esta pueda comunicarse con el servidor Exchange.

- El conector es compatible con el **entorno de CAS de Exchange**. Si le interesa, el conector se puede instalar técnicamente en el servidor CAS de Exchange directamente, pero no se recomienda porque aumenta la carga en el servidor. Al configurar el conector, debe permitir que se comunique con uno de los servidores CAS de Exchange.

- **Exchange ActiveSync** se debe configurar con autenticación basada en certificados o con la entrada de credenciales de usuario.

- Cuando se configuran directivas de acceso condicional y se aplican a un usuario, el **dispositivo** debe cumplir las condiciones siguientes para que los usuarios puedan conectarse al correo electrónico:
    - Debe estar **inscrito** en Intune o estar en un equipo unido a un dominio.
    - Debe estar **registrado en Azure Active Directory**. Además, el identificador de Exchange ActiveSync del cliente debe registrarse con Azure Active Directory.
<br></br>
- AAD DRS se activará automáticamente para los clientes de Intune y Office 365. Los clientes que ya hayan implementado el servicio de registro de dispositivos de ADFS no podrán ver los dispositivos registrados en la instancia local de Active Directory. **Esto no se aplica a equipos de Windows ni a dispositivos Windows Phone.**

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
> La aplicación Microsoft Outlook para iOS y Android no es compatible. Android for Work se implantará entre los inquilinos de Intune durante los próximos meses.

### <a name="support-for-pcs"></a>Compatibilidad para equipos

La aplicación **Correo** nativa en Windows 8.1 y versiones posteriores (cuando se inscribe en Intune).


## <a name="configure-exchange-on-premises-access"></a>Configuración del acceso a Exchange local

1. Vaya a [Azure Portal](https://portal.azure.com/) e inicie sesión con sus credenciales de Intune.

2. Después de iniciar sesión correctamente, verá el **Panel de Azure**.

3. Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

4. Elija **Intune** y aparecerá el **panel de Intune**.

5.  Elija **Acceso condicional** y luego

6. La hoja **Local** muestra el estado de la directiva de acceso condicional y los dispositivos que se ven afectados por ella.

7. En **Administrar**, elija **Acceso local a Exchange**.

8. En la hoja **Acceso local a Exchange**, elija **Sí** para el control de acceso local a Exchange.

      > [!NOTE]
      > Si no ha configurado el conector de Exchange Active Sync local, esta opción se deshabilitará.  Primero debe instalar y configurar este conector antes de habilitar el acceso condicional para Exchange local. Para más información, consulte [Install the Intune On-premises Exchange Connector](install-intune-on-premises-exchange-connector.md) (Instalación del conector de Exchange local para Intune).

9. En **Asignación**, elija **Grupos incluidos**.  Use el grupo de usuarios de seguridad que debería tener aplicado el acceso condicional. Para ello, es necesario que los usuarios hayan inscrito sus dispositivos en Intune y que satisfagan los perfiles de cumplimiento.

10. Si quiere excluir determinados grupos de usuarios, puede hacerlo; para ello, elija **Grupos excluidos** y seleccione un grupo de usuarios al que quiera que se le exima de exigir la inscripción y el cumplimiento del dispositivo.

11. En **Configuración**, elija **Notificaciones de usuario** para modificar el mensaje de correo electrónico predeterminado. Este mensaje se envía a los usuarios si su dispositivo no es conforme y quieren acceder a Exchange local. La plantilla de mensaje usa lenguaje de marcado.  También podrá ver la vista previa del mensaje mientras escribe.
    > [!TIP]
    > Para más información sobre el lenguaje de marcado, consulte este [artículo](https://en.wikipedia.org/wiki/Markup_language) en Wikipedia.

12. En la hoja **Advanced Exchange Active Sync** (Configuración avanzada de acceso a Exchange Active Sync), establezca la regla predeterminada global para el acceso desde dispositivos que no están administrados por Intune y para reglas de nivel de plataforma, como se describe en los dos pasos siguientes.

13. En dispositivos a los que no les afecta las reglas de acceso condicional o de otro tipo, puede optar por permitirles acceder a Exchange o bloquearlo.
  - Cuando configure esta opción para permitir el acceso, todos los dispositivos podrán acceder a Exchange local inmediatamente.  Los dispositivos que pertenecen a los usuarios de **Grupos incluidos** se bloquean si se evalúan posteriormente como no conformes con las directivas de cumplimiento o no inscritos en Intune.
  - Cuando configure esta opción para bloquear el acceso, se bloqueará inmediatamente a todos los dispositivos el acceso a Exchange local inicialmente.  Los dispositivos que pertenecen a los usuarios de **Grupos incluidos** tendrán acceso una vez que el dispositivo esté inscrito en Intune y se evalúe como conforme. En dispositivos Android que no ejecuten Samsung KNOX Standard el acceso siempre estará bloqueado ya que no admiten esta configuración.
<br></br>
14. En **Excepciones de la plataforma de dispositivo**, elija **Agregar** para especificar las plataformas. Si la opción **Acceso a dispositivos no administrados** está establecida en **Bloqueado**, se permitirán los dispositivos inscritos y conformes incluso si hay una excepción de plataforma para bloquear. Elija **Aceptar** para guardar la configuración.

15. En la hoja **Local**, haga clic en **Guardar** para guardar la directiva de acceso condicional.

## <a name="create-azure-ad-conditional-access-policies-in-intune-azure-preview"></a>Creación de directivas de acceso condicional de Azure AD en la versión preliminar de Intune Azure

A partir de la versión 1704 de Intune, los administradores pueden crear directivas de acceso condicional de Azure AD desde la vista preliminar de Intune Azure, que facilita el proceso para que no sea necesario cambiar entre las cargas de trabajo de Azure y Intune.

> [!IMPORTANT]
> Debe disponer de una licencia premium de Azure AD para crear directivas de acceso condicional de Azure AD desde el portal de la versión preliminar de Intune Azure.

### <a name="to-create-azure-ad-conditional-access-policy"></a>Para crear una directiva de acceso condicional de Azure AD

1. En el **panel de Intune**, elija **Acceso condicional**.

2. En el **panel de acceso condicional**, elija **Acceso condicional en Azure Active Directory**.

3. Elija **Nueva directiva** para crear la nueva directiva de acceso condicional de Azure AD.

    ![Directivas de acceso condicional de Azure AD](../media/Azure-AD-CA-Intune.png)

## <a name="see-also"></a>Consulte también

[Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
