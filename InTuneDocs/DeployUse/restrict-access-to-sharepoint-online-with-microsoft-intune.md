---
# required metadata

title: Restringir el acceso a SharePoint Online | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Restringir el acceso a SharePoint Online con Microsoft Intune
Use el acceso condicional de [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] para controlar el acceso a los archivos que se encuentran en SharePoint Online.
El acceso condicional tiene dos componentes:
- La directiva de cumplimiento del dispositivo, con la que debe cumplir el dispositivo para que se considere conforme.
- La directiva de acceso condicional, donde se especifican las condiciones que debe cumplir el dispositivo para tener acceso al servicio.
Para más información sobre cómo funciona el acceso condicional, vea el tema [Restrict access to email and O365 services](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (Restringir el acceso al correo electrónico y servicios de O365).

Cuando un usuario intenta conectarse a un archivo con una aplicación compatible como OneDrive en su dispositivo, se produce la siguiente evaluación:

![Diagrama que muestra los puntos de decisión que determinan si un dispositivo puede tener acceso a SharePoint o si se bloquea ](../media/ConditionalAccess8-6.png)

>[!IMPORTANT]
>El acceso condicional para equipos y para dispositivos Windows 10 Mobile con aplicaciones que usan la autenticación moderna no está actualmente disponible para todos los clientes de Intune. Si ya usa estas características, no es necesario que realice ninguna acción. Puede seguir usándolas.

>Si no ha creado directivas de acceso condicional para equipos o para Windows 10 Mobile para las aplicaciones que usan la autenticación moderna y le gustaría hacerlo, debe enviar una solicitud.  Encontrará más información sobre problemas conocidos y cómo acceder a esta característica en el [sitio de Connect](http://go.microsoft.com/fwlink/?LinkId=761472)..

**Antes** de configurar una directiva de acceso condicional para SharePoint Online, debe:
- Tener una **suscripción de SharePoint Online** y los usuarios deben tener licencia para SharePoint Online.
- Tener una suscripción a **Enterprise Mobility Suite** o **Azure Active Directory Premium**..

  Para conectarse a los archivos requeridos, el dispositivo debe:
-   Estar **inscrito** con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o ser un equipo unido a un dominio.

-   **Estar registrado** en Azure Active Directory, lo que se lleva a cabo automáticamente si el dispositivo está inscrito con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).


-   Cumplir todas las directivas de cumplimiento de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] implementadas.

El estado del dispositivo se almacena en Azure Active Directory, que concede o bloquea el acceso a los archivos según las condiciones especificadas.

Si no se cumple una condición, se presentará al usuario uno de los mensajes siguientes cuando inicie sesión:

-   Si el dispositivo no está inscrito con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o si no está registrado en Azure Active Directory, se muestra un mensaje con instrucciones sobre cómo instalar la aplicación de portal de empresa e inscribirse.

-   Si el dispositivo no es conforme, se muestra un mensaje que dirige al usuario al sitio web del portal de empresa de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], donde encontrará información sobre el problema y sobre cómo resolverlo.

## Compatibilidad con dispositivos móviles
- iOS 7.1 y versiones posteriores
- Android 4.0 y versiones posteriores, Samsung Knox Standard 4.0 o versiones posteriores
- Windows Phone 8.1 y versiones posteriores

## Compatibilidad para equipos
- Windows 8.1 y versiones posteriores (cuando están inscritos en Intune)
- Windows 7.0 o Windows 8.1 (si están unidos a un dominio)

  - Los equipos unidos a un dominio debe estar configurados para [registrarse automáticamente](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) con Azure Active Directory.
AAD DRS se activará automáticamente para los clientes de Intune y Office 365. Los clientes que ya hayan implementado el servicio de registro de dispositivos de ADFS no podrán ver los dispositivos registrados en la instancia local de Active Directory.

  - Si la directiva está establecida para requerir la unión a un dominio y el equipo no está unido a ningún dominio, se muestra un mensaje que indica que es necesario ponerse en contacto con el administrador de TI.

  - Si la directiva está establecida para requerir la unión a un dominio o la conformidad y el equipo no cumple estos requisitos, se muestra un mensaje con instrucciones sobre cómo instalar la aplicación de portal de empresa e inscribirse.
-    [La autenticación moderna de Office 365 debe estar habilitada](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) y tener las últimas actualizaciones de Office.

    La autenticación moderna aporta inicio de sesión basado en la biblioteca de autenticación de Active Directory (ADAL) para los clientes de Windows en Office 2013 y habilita una mejor seguridad como la **autenticación multifactor** y la **autenticación basada en certificados**..


## Configurar el acceso condicional de SharePoint Online

### Paso 1: Configurar grupos de seguridad de Active Directory
Antes de empezar, configure los grupos de seguridad de Azure Active Directory para la directiva de acceso condicional. Estos grupos se pueden configurar en el **Centro de administración de Office 365**o el **portal de cuentas de Intune**. Estos grupos se usarán para aplicar la directiva a los usuarios o para excluirlos de ella. Cuando un usuario es destinatario de una directiva, cada dispositivo que use debe ser conforme con el fin de obtener acceso a los recursos.

Se pueden especificar dos tipos de grupo en una directiva de SharePoint Online:

-   **Grupos de destino**: contiene grupos de usuarios a los que se aplicará la directiva.

-   **Grupos exentos**: contiene grupos de usuarios que están exentos de la directiva.

Si un usuario pertenece a ambos grupos, estará exento de la directiva.

### Paso 2: Configurar e implementar una directiva de cumplimiento
Si todavía no lo ha hecho, cree e implemente una directiva de cumplimiento para todos los usuarios a los que se aplicará la directiva de SharePoint Online.

> [!NOTE]
> Mientras se implementan las directivas de cumplimiento en los grupos de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], las directivas de acceso condicional se aplican a los grupos de seguridad de Azure Active Directory.

Para saber más sobre cómo configurar la directiva de cumplimiento, vea [Create a compliance policy](create-a-device-compliance-policy-in-microsoft-intune.md) (Creación de una directiva de cumplimiento)..

> [!IMPORTANT]
> Si no ha implementado una directiva de cumplimiento, los dispositivos se considerarán no conformes.

Cuando esté listo, continúe con el **paso 3**..

### Paso 3: Configurar la directiva de SharePoint Online
A continuación, configure la directiva para requerir que solo los dispositivos administrados y conformes puedan tener acceso a SharePoint Online. Esta directiva se almacenará en Azure Active Directory.

#### <a name="bkmk_spopolicy"></a>

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** > **Acceso condicional** > **Directiva de SharePoint Online**..
![Captura de pantalla de la página de la directiva de SharePoint Online](../media/IntuneSASharePointOnlineCAPolicy.png)

2.  Seleccione **Habilitar directiva de acceso condicional para SharePoint Online**..

3.  En **Acceso a la aplicación**, puede elegir aplicar la directiva de acceso condicional a:

    -   **Todas las plataformas**

        Esto requerirá que cualquier dispositivo usado para acceder a **SharePoint Online** se inscriba en Intune y cumpla las directivas.  Cualquier aplicación cliente que use la **autenticación moderna** estará sujeta a la directiva de acceso condicional. Si la plataforma no es compatible actualmente con Intune, el acceso a **SharePoint Online** se bloqueará.
        >[!TIP]
        >Podría no ver esta opción si todavía no usa el acceso condicional para equipos.  Use en su lugar las **Plataformas específicas**. El acceso condicional para equipos no está disponible actualmente para todos los clientes de Intune.   Encontrará más información sobre problemas conocidos y cómo acceder a esta característica en el [sitio de Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=761472)..

    -   **Plataformas específicas**

         La directiva de acceso condicional se aplica a cualquier aplicación cliente que use la autenticación moderna en las plataformas que especifique.

     En el caso de los equipos de Windows, el equipo debe estar unido a un dominio o inscrito con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y ser conforme. Puede establecer los requisitos siguientes:

     -   **Los dispositivos deben estar unidos al dominio o ser compatibles.** Elija esta opción si quiere que los equipos estén unidos al dominio o que cumplan las directivas establecidas en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Si el equipo no cumple alguno de estos requisitos, se pide al usuario que inscriba el dispositivo con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

     -   **Los dispositivos deben estar unidos al dominio.** Elija esta opción para requerir que los equipos estén unidos al dominio para tener acceso a Exchange Online. Si el equipo no está unido al dominio, el acceso al correo electrónico se bloquea y el usuario debe ponerse en contacto con el administrador de TI.

     -   **Los dispositivos deben ser conformes.** Elija esta opción para requerir que los equipos estén inscritos en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y sean conformes. Si el equipo no está inscrito, se muestra un mensaje con instrucciones sobre cómo inscribirse.

4.  En **Grupos de destino**, haga clic en **Modificar** para seleccionar los grupos de seguridad de Azure Active Directory a los que se aplicará la directiva. Puede elegir dirigir esto a todos los usuarios o solo a un selecto grupo de usuarios.

5.  En **Grupos exentos**, opcionalmente, haga clic en **Modificar** para seleccionar los grupos de seguridad de Azure Active Directory que se van a excluir de la directiva.

6.  Cuando haya terminado, haga clic en **Guardar**..

No es necesario implementar la directiva de acceso condicional, ya que surte efecto inmediatamente.

### Paso 4: Supervisar el cumplimiento y las directivas de acceso condicional
En el área de trabajo **Grupos**, puede ver el estado de los dispositivos.

Seleccione cualquier grupo de dispositivos móviles y, a continuación, en la pestaña **Dispositivos** , seleccione uno de los siguientes **Filtros**:

-   **Dispositivos no registrados en AAD** : estos dispositivos están bloqueados en SharePoint Online.

-   **Dispositivos no conformes** : estos dispositivos están bloqueados en SharePoint Online.

-   **Dispositivos registrados en AAD y conformes** : estos dispositivos pueden tener acceso a SharePoint Online.

### Consulte también
[Restringir el acceso al correo electrónico y a los servicios de O365 con Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=May16_HO1-->


