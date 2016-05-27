---
# required metadata

title: Restringir el acceso de correo electrónico a Exchange Online y nuevo Exchange Online dedicado | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Restringir el acceso de correo electrónico a Exchange Online y nuevo Exchange Online dedicado

Si tiene un entorno de Exchange Online dedicado y necesita averiguar si es la configuración nueva o heredada, póngase en contacto con su administrador de cuentas.

Para controlar el acceso de correo electrónico a Exchange Online o a su nuevo entorno de Exchange Online dedicado, configure el acceso condicional para Exchange Online en Intune.
Para más información sobre cómo funciona el acceso condicional, vea el artículo [Restrict access to email and O365 services](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (Restringir el acceso al correo electrónico y servicios de O365).

>[!IMPORTANT]
>El acceso condicional para equipos y para dispositivos Windows 10 Mobile con aplicaciones que usan la autenticación moderna no está actualmente disponible para todos los clientes de Intune. Si ya usa estas características, no es necesario que realice ninguna acción. Puede seguir usándolas.

>Si no ha creado directivas de acceso condicional para equipos o para Windows 10 Mobile para las aplicaciones que usan la autenticación moderna y le gustaría hacerlo, debe enviar una solicitud.  Encontrará más información sobre problemas conocidos y cómo acceder a esta característica en el [sitio de Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=761472)..

**Antes** de configurar el acceso condicional, debe:

-   Tener una **suscripción de Office 365 que incluya Exchange Online (por ejemplo, E3)** y los usuarios deben tener licencia para Exchange Online.

-  Considerar la posibilidad de configurar el **conector de servicio a servicio de Microsoft Intune** opcional, que conecta [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] a Microsoft Exchange Online y hace que sea más fácil administrar información de dispositivos a través de la consola de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. No necesita usar el conector para usar directivas de cumplimiento o de acceso condicional, pero sí para ejecutar informes que ayuden a evaluar el impacto del acceso condicional.

   > [!NOTE]
   > No configure el conector de servicio a servicio si piensa usar el acceso condicional para Exchange Online y Exchange local.

   Para obtener instrucciones sobre cómo configurar el conector, vea [Intune service-to-service connector](intune-service-to-service-exchange-connector.md) (Conector de servicio a servicio de Intune).

Cuando se configuran directivas de acceso condicional y se aplican a un usuario, el **dispositivo** debe cumplir las condiciones siguientes para que los usuarios puedan conectarse al correo electrónico:

-   Debe estar **inscrito** con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o ser un equipo unido a un dominio.

-  Debe estar **registrado en Azure Active Directory**. Esto sucede automáticamente cuando el dispositivo se inscribe con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Además, el identificador de Exchange ActiveSync del cliente debe registrarse con Azure Active Directory.

  AAD DRS se activará automáticamente para los clientes de Intune y Office 365. Los clientes que ya hayan implementado el servicio de registro de dispositivos de ADFS no podrán ver los dispositivos registrados en la instancia local de Active Directory.

-   Debe ser **compatible** con todas las directivas de cumplimiento de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] implementadas en el dispositivo, o bien debe estar unido a un dominio local.

Si no se cumple una directiva de acceso condicional, el usuario recibirá uno de los mensajes siguientes cuando inicie sesión:

- Si el dispositivo no está inscrito con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], o si no está registrado en Azure Active Directory, se muestra un mensaje con instrucciones sobre cómo instalar la aplicación de portal de empresa, inscribir el dispositivo y activar el correo electrónico. Este proceso también asocia el identificador de Exchange ActiveSync del dispositivo con el registro en Azure Active Directory.

-   Si se considera que el dispositivo no es conforme con las reglas de la directiva de cumplimiento, se dirige al usuario al sitio web del portal de empresa de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o a la aplicación de portal de empresa, donde encontrará información sobre el problema y sobre cómo resolverlo.


En el diagrama siguiente se muestra el flujo que usan las directivas de acceso condicional para Exchange Online.

![Diagrama que muestra los puntos de decisión que determinan si se permite el acceso al dispositivo o se bloquea](../media/ConditionalAccess8-1.png)

## Compatibilidad con dispositivos móviles
Puede restringir el acceso al correo electrónico de Exchange Online desde **Outlook** y otras **aplicaciones que usan la autenticación moderna**:

- Android 4.0 y versiones posterior, Samsung Knox Standard 4.0 y versiones posteriores
- iOS 7.1 y versiones posteriores
- Windows Phone 8.1 y versiones posteriores

 La **autenticación moderna** proporciona el inicio de sesión basado en la biblioteca de autenticación de Active Directory (ADAL) a los clientes de Microsoft Office.

> -   La autenticación basada en ADAL permite a los clientes de Office realizar la autenticación basada en explorador (también conocida como autenticación pasiva).  Para realizar la autenticación, se envía al usuario a una página web de inicio de sesión. Este nuevo método de inicio de sesión permite mejorar la seguridad como **la autenticación multifactor** y la **autenticación basada en certificados**.
> Este [artículo](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) contiene información más detallada sobre cómo funciona la autenticación moderna.


Puede restringir el acceso al correo electrónico de Exchange desde el **cliente de correo electrónico de Exchange ActiveSync** integrado en las siguientes plataformas:

- Android 4.0 y versiones posterior, Samsung Knox Standard 4.0 y versiones posteriores

- iOS 7.1 y versiones posteriores

- Windows Phone 8.1 y versiones posteriores

## Compatibilidad para equipos

Puede configurar el acceso condicional para equipos que ejecutan aplicaciones de escritorio de Office, para que tengan acceso a **Exchange Online** y **SharePoint Online** en los equipos que cumplen los requisitos siguientes:

-   El equipo debe ejecutar Windows 7.0 o Windows 8.1.

-   El equipo debe estar unido a un dominio o cumplir las reglas de la directiva de cumplimiento.

    Para que se considere compatible, el equipo debe estar inscrito en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y cumplir las directivas.

    Los equipos unidos a un dominio deben configurarse para [registrar automáticamente el dispositivo.](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) con Azure Active Directory.

-   [La autenticación moderna de Office 365 debe estar habilitada](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) y tener las últimas actualizaciones de Office.

    La autenticación moderna aporta inicio de sesión basado en la biblioteca de autenticación de Active Directory (ADAL) para los clientes de Windows en Office 2013 y habilita una mejor seguridad como la **autenticación multifactor** y la **autenticación basada en certificados**..

-   Configure reglas de notificaciones de ADFS para bloquear protocolos de autenticación no moderna. Se proporcionan instrucciones detalladas en el Escenario 3: [Bloquear todo el acceso externo a O365 excepto las aplicaciones basadas en explorador](https://technet.microsoft.com/library/dn592182.aspx)..

## Configurar el acceso condicional
### Paso 1: configurar e implementar una directiva de cumplimiento
Asegúrese de [crear](create-a-device-compliance-policy-in-microsoft-intune.md) e [implementar](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) una directiva de cumplimiento para los grupos de usuarios que también obtendrán la directiva de acceso condicional.


> [!IMPORTANT]
> Si no ha implementado una directiva de cumplimiento, los dispositivos se considerarán compatibles y se les permitirá el acceso a Exchange.

### Paso 2: evaluar el impacto de la directiva de acceso condicional
Puede usar los **Informes de inventario de dispositivos móviles** para identificar los dispositivos a los que se les podría bloquear el acceso a Exchange después de configurar la directiva de acceso condicional.

Para ello, configure una conexión entre [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y Exchange mediante el [conector de servicio a servicio de Microsoft Intune](intune-service-to-service-exchange-connector.md)..
1.  Vaya a **Informes -> Informes de inventario de dispositivos móviles**..
![Captura de pantalla de la página de informe de inventario de dispositivos móviles](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  En los parámetros del informe, seleccione el grupo de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] que desea evaluar y, si es necesario, las plataformas de dispositivos a las que se aplicará la directiva.
3.  Una vez que haya seleccionado los criterios que satisfagan las necesidades de la organización, elija **Ver informe**..
El Visor de informes se abrirá en una nueva ventana.
![Captura de pantalla de un ejemplo de informe de inventario de dispositivos móviles](../media/IntuneSA2cViewReport.PNG)

Después de ejecutar el informe, examine estas cuatro columnas para determinar si un usuario se bloqueará:

-   **Canal de administración** : indica si Intune, Exchange ActiveSync o ambas aplicaciones administran el dispositivo.

-   **Registrado en AAD** : indica si el dispositivo está registrado con Azure Active Directory (lo que se conoce como unión al "área de trabajo").

-   **Conforme** : indica si el dispositivo cumple con las directivas de cumplimiento que se han implementado.

-   **Id. de Exchange ActiveSync** : los dispositivos iOS y Android deben tener su id. de Exchange ActiveSync asociado al registro de registro del dispositivo en Azure Active Directory. Esto sucede cuando el usuario hace clic en **Activar correo electrónico** en el mensaje de correo en cuarentena.

    > [!NOTE]
    > Los dispositivos Windows Phone siempre muestran un valor en esta columna.

Los dispositivos que forman parte de un grupo de destino tendrán bloqueado el acceso a Exchange, a menos que los valores de la columna coincidan con los de la tabla siguiente:

--------------------------
|Canal de administración|Registrado en AAD|Conforme|Id. de Exchange ActiveSync|Acción resultante|
|----------------------|------------------|-------------|--------------------------|--------------------|
|**Administrado por Microsoft Intune y Exchange ActiveSync**|Sí|Sí|Se muestra un valor|Acceso a correo electrónico concedido|
|Cualquier otro valor|No|No|No se muestra ningún valor|Acceso a correo electrónico bloqueado|
----------------------
Puede exportar el contenido del informe y usar la columna **Dirección de correo electrónico** para informar a los usuarios de que se les va a bloquear.

### Paso 3: configurar grupos de usuarios para la directiva de acceso condicional
Las directivas de acceso condicional se aplican a diferentes grupos de seguridad de usuarios de Azure Active Directory. También puede excluir determinados grupos de usuarios de esta directiva.  Cuando un usuario es destinatario de una directiva, cada dispositivo que use debe ser conforme con el fin de obtener acceso al correo electrónico.

Estos grupos se pueden configurar en el **Centro de administración de Office 365** o en el **portal de cuentas de Intune**..

Se pueden especificar dos tipos de grupo en cada directiva:

-   **Grupos de destino**: grupos de usuarios a los que se aplica la directiva.

-   **Grupos exentos** : grupos de usuarios que están exentos de la directiva (opcional)

Si un usuario pertenece a ambos grupos, estará exento de la directiva.

Solo se evalúan los grupos a los que se aplica la directiva de acceso condicional.

### Paso 4: configurar la directiva de acceso condicional

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** > **Acceso condicional** > **Directiva de Exchange Online**..
![Captura de pantalla de la página de la directiva de acceso condicional de Exchange Online](../media/IntuneSA5dExchangeOnlinePolicy.png)

2.  En la página **Directiva de Exchange Online**, seleccione **Habilitar directiva de acceso condicional para Exchange Online**..

    > [!NOTE]
    > Si no ha implementado una directiva de cumplimiento, los dispositivos se consideran no conformes.
    >
    > Independientemente del estado de cumplimiento, todos los usuarios a los que se aplique la directiva deberán inscribir sus dispositivos con Intune. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

3.  En **Acceso a la aplicación**, en el caso de las aplicaciones que usan la autenticación moderna, tiene dos maneras de elegir qué plataformas debe aplicar la directiva. Las plataformas compatibles incluyen Android, iOS, Windows y Windows Phone.

    -   **Todas las plataformas**

        Esto requerirá inscribir en Itune cualquier dispositivo que se use para acceder a **Exchange Online** y que sea compatible con las directivas.  Toda aplicación cliente que use la **autenticación moderna** está sujeta a la directiva de acceso condicional y si la plataforma no es compatible actualmente con Intune, se bloqueará el acceso a **Exchange Online**.
        >[!TIP]
           Podría no ver esta opción si todavía no usa el acceso condicional para equipos.  Use en su lugar las **Plataformas específicas**. El acceso condicional para equipos no está disponible actualmente para todos los clientes de Intune.   Encontrará más información sobre problemas conocidos y cómo acceder a esta característica en el [sitio de Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=761472)..

    -   **Plataformas específicas**

         La directiva de acceso condicional se aplicará a cualquier aplicación cliente que use la **autenticación moderna** en las plataformas de dispositivo que especifique.

4.  En **Aplicaciones de Exchange ActiveSync**, puede elegir bloquear el acceso a Exchange Online de dispositivos no conformes. También puede seleccionar si quiere permitir o bloquear el acceso al correo cuando el dispositivo no ejecuta una plataforma compatible. Las plataformas compatibles incluyen Android, iOS, Windows y Windows Phone.


5.  En **Grupos de destino**, seleccione los grupos de seguridad de Active Directory a los que se aplicará la directiva. Puede elegir como destino todos los usuarios o puede seleccionar una lista de grupos de usuarios.
![Captura de pantalla de la página de la directiva de acceso condicional de Exchange Online que muestra las opciones de grupo de destino y exento](../media/IntuneSA5eTargetedExemptedGroups.PNG)
    > [!NOTE]
    > En el caso de los usuarios que se encuentren en los **grupos de destino**, las directivas de Intune reemplazarán las directivas y reglas de Exchange.
    >
    > Exchange solo aplicará sus directivas y sus reglas de permiso, bloqueo y cuarentena si:
    >
    > -   El usuario no tiene licencia para Intune.
    > -   El usuario tiene licencia para Intune pero no pertenece a ningún grupo de seguridad de destino de la directiva de acceso condicional.

6.  En **Grupos exentos**, seleccione los grupos de seguridad de Active Directory que se van a excluir de la directiva. Si un usuario está incluido tanto los grupos de destino como en los grupos exentos, estará exento de la directiva.

7.  Cuando termine, elija **Guardar**..

-   No es necesario implementar la directiva de acceso condicional, ya que surte efecto inmediatamente.

-   Cuando un usuario crea una cuenta de correo electrónico, el dispositivo se bloquea inmediatamente.

-   Si un usuario bloqueado inscribe el dispositivo con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y corrige los problemas de no conformidad, el acceso al correo electrónico se desbloquea en dos minutos.

-   Si el usuario anular la inscripción de su dispositivo, el correo se bloquea después de aproximadamente 6 horas.

**Para ver algunos escenarios de ejemplo sobre la configuración de la directiva de acceso condicional para restringir el acceso a los dispositivos, vea [Restrict email access example scenarios](restrict-email-access-example-scenarios.md) (Escenarios de ejemplo sobre cómo restringir el acceso de correo electrónico)..**

## Supervisar el cumplimiento y las directivas de acceso condicional

#### Para ver los dispositivos que tienen bloqueado el acceso a Exchange

En el panel de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], elija el icono **Dispositivos bloqueados de Exchange** para que se muestren el número de dispositivos bloqueados y los vínculos para más información.
![Captura de pantalla del panel de Intune que muestra el número de dispositivos a los que se ha bloqueado el acceso a Exchange](../media/IntuneSA6BlockedDevices.PNG)

## Pasos siguientes
[Restringir el acceso a SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Restringir el acceso a Skype Empresarial Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)


<!--HONumber=May16_HO1-->


