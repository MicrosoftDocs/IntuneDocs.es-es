---
title: Creación de una directiva de acceso condicional de Exchange
titleSuffix: Microsoft Intune
description: Configure el acceso condicional en Exchange local y en el entorno de Exchange Online dedicado heredado en Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/26/2020
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
ms.openlocfilehash: 6650c091917ea265783044efd78b19a7e032e6a7
ms.sourcegitcommit: 5511b4f2b8a3383176a7afe2a22ad5a8d42caf7b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169304"
---
# <a name="configure-exchange-on-premises-access-for-intune"></a>Configuración del acceso a Exchange local para Intune

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

- **Windows Phone 8.1 y versiones posteriores**: para crear directivas de acceso condicional, vea [Creación de directivas de acceso condicional](../protect/create-conditional-access-intune.md)
- **Aplicación de correo electrónico nativo en iOS/iPadOS**: para crear directivas de acceso condicional, vea [Creación de directivas de acceso condicional](../protect/create-conditional-access-intune.md)
- **Clientes de correo EAS como Gmail en Android 4 o versiones posteriores**: para crear directivas de acceso condicional, vea [Creación de directivas de acceso condicional](../protect/create-conditional-access-intune.md)

- **Clientes de correo EAS en dispositivos con perfil de trabajo Android**: solo se admiten *Gmail* y *Nine Work for Android Enterprise* en los dispositivos de perfil de trabajo Android. Para que el acceso condicional funcione con perfiles de trabajo Android, debe implementar un perfil de correo electrónico para la aplicación *Gmail* o *Nine Work for Android Enterprise*, y también implementar esas aplicaciones como una instalación necesaria. Después de implementar la aplicación, puede configurar el acceso condicional basado en dispositivos.

#### <a name="to-set-up-conditional-access-for-android-work-profile-devices"></a>Para configurar el acceso condicional para dispositivos de perfil de trabajo Android

  1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
  
  2. Implemente la aplicación Gmail o Nine Work como **requerida**.

  3. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil** y escriba un **Nombre** y una **Descripción** para el perfil.

  4. Seleccione **Android Enterprise** en **Plataforma** y **Correo electrónico** en **Tipo de perfil**.

  5. Configure las [opciones del perfil de correo electrónico](https://docs.microsoft.com/intune/configuration/email-settings-android-enterprise#android-enterprise).

  6. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

  7. Después de crear el perfil de correo electrónico, [asígnelo a grupos](https://docs.microsoft.com/intune/device-profile-assign).

  8. Configure el [acceso condicional basado en dispositivos](https://docs.microsoft.com/intune/protect/conditional-access-intune-common-ways-use#device-based-conditional-access).

> [!NOTE]
> No se admite Microsoft Outlook para iOS/iPadOS y Android a través del conector local de Exchange. Si quiere aprovechar las directivas de acceso condicional de Azure Active Directory y las directivas de Intune App Protection con Outlook para iOS/iPadOS y Android en los buzones locales, vea [Uso de autenticación moderna híbrida con Outlook para iOS/iPadOS y Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

### <a name="support-for-pcs"></a>Compatibilidad para equipos

La aplicación **Correo** nativa en Windows 8.1 y versiones posteriores (cuando se inscribe en MDM con Intune).

## <a name="configure-exchange-on-premises-access"></a>Configuración del acceso a Exchange local

Para poder usar el siguiente procedimiento para configurar el control de acceso local a Exchange, debe instalar y configurar al menos una instancia de [Intune On-Premises Exchange Connector](exchange-connector-install.md) para Exchange local.

1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Vaya a **Administración de inquilinos** > **Acceso de Exchange** y **seleccione Acceso local a Exchange**.

3. En el panel **Acceso local a Exchange**, elija **Sí** para *habilitar el control de acceso local a Exchange*.

   > [!div class="mx-imgBorder"]
   > ![Captura de pantalla de ejemplo de la pantalla de acceso local a Exchange](./media/conditional-access-exchange-create/exchange-on-premises-access.png)

4. En **Asignación**, elija **Seleccionar grupos para incluir** y, a continuación, seleccione uno o varios grupos para configurar el acceso.

   Los miembros de los grupos que seleccione tendrán aplicada la directiva de acceso condicional para el acceso local a Exchange. Los usuarios que reciben esta directiva deben inscribir sus dispositivos en Intune y ser compatibles con los perfiles de cumplimiento para poder tener acceso a Exchange local.

   > [!div class="mx-imgBorder"]
   > ![Seleccionar grupos para incluir](./media/conditional-access-exchange-create/select-groups.png)

5. Para excluir grupos, elija **Seleccionar grupos para excluir** y, a continuación, seleccione uno o varios grupos que estén exentos de los requisitos para inscribir dispositivos y sean compatibles con los perfiles de cumplimiento para tener acceso a Exchange local.

   Seleccione **Guardar** para guardar la configuración y vuelva al panel **Acceso a Exchange**.

6. A continuación, configure las opciones de Intune On-Premises Exchange Connector. En la consola, seleccione **Administración de inquilinos** > **Acceso a Exchange**> **Exchange ActiveSync Connector local** y, luego, seleccione el conector para la organización de Exchange que quiere configurar.

7. En el caso de las **Notificaciones de usuario**, seleccione **Editar** para abrir el flujo de trabajo **Editar organización**, donde puede modificar el mensaje de la *Notificación del usuario*.

   > [!div class="mx-imgBorder"]
   > ![Captura de pantalla de ejemplo del flujo de trabajo Editar organización para notificaciones](./media/conditional-access-exchange-create/edit-organization-user-notification.png)

   Modifique el mensaje de correo electrónico predeterminado que se envía a los usuarios si su dispositivo no es compatible y quieren tener acceso a Exchange local. La plantilla de mensaje usa lenguaje de marcado. También puede ver la vista previa del mensaje mientras escribe.

   Seleccione **Revisar y guardar** y, luego, **Guardar** para guardar sus ediciones a fin de completar la configuración del acceso local a Exchange.

   > [!TIP]
   > Para más información sobre el lenguaje de marcado, consulte este [artículo](https://en.wikipedia.org/wiki/Markup_language) en Wikipedia.

8. A continuación, seleccione **Configuración avanzada de acceso a Exchange ActiveSync** para abrir el flujo de trabajo *Configuración avanzada de acceso a Exchange ActiveSync* donde configura las reglas de acceso de dispositivo.

   > [!div class="mx-imgBorder"]
   > ![Captura de pantalla de ejemplo del flujo de trabajo Editar organización para configuración avanzada](./media/conditional-access-exchange-create/edit-organization-advanced-settings.png)

   - En **Acceso a dispositivos no administrados**, establezca la regla predeterminada global para el acceso desde dispositivos que no se vean afectados por el acceso condicional u otras reglas:

     - **Permitir acceso**: todos los dispositivos pueden tener acceso a Exchange local inmediatamente. Los dispositivos que pertenecen a los usuarios de los grupos que configuró como incluidos en el procedimiento anterior se bloquean si se evalúan posteriormente como no conformes con las directivas de cumplimiento o no inscritos en Intune.

     - **Bloquear acceso** y **Cuarentena**: se bloquea inmediatamente a todos los dispositivos el acceso a Exchange local inicialmente. Los dispositivos que pertenecen a los usuarios de los grupos que configuró como incluidos en el procedimiento anterior obtienen acceso una vez que el dispositivo se inscribe en Intune y se evalúa como conforme.

       Los dispositivos Android que *no* ejecutan Samsung Knox Standard no admiten esta configuración y siempre están bloqueados.

   - En **Excepciones de la plataforma de dispositivo**, seleccione **Agregar** y, a continuación, especifique detalles según sea necesario para su entorno.

      Si el valor **Acceso a dispositivos no administrados** está establecido en **Bloqueado**, se permiten los dispositivos inscritos y conformes aunque haya una excepción de plataforma para bloquearlos.  

9. Seleccione **Aceptar** para guardar las ediciones.

10. Seleccione **Revisar y guardar** y, después, **Guardar** para guardar la directiva de acceso condicional de Exchange.

## <a name="next-steps"></a>Pasos siguientes

A continuación, cree una directiva de cumplimiento y asígnela a los usuarios para que Intune evalúe sus dispositivos móviles. Consulte [Introducción al cumplimiento de dispositivos](device-compliance-get-started.md).

[Solución de problemas de Intune Exchange Connector local en Microsoft Intune](https://support.microsoft.com/help/4471887)
