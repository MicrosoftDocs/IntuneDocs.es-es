---
title: "Proteger el correo electrónico en Exchange Online | Microsoft Docs"
description: "Proteja y controle el acceso al correo electrónico de empresa en Exchange Online con el acceso condicional."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 53d2c0d5b2157869804837ae2fa08b1cce429982
ms.openlocfilehash: ab4b244e733f973581216f3358fce0653609aaaa


---


# <a name="protect-email-access-to-exchange-online-and-new-exchange-online-dedicated-with-intune"></a>Proteger el acceso de correo electrónico a Exchange Online y nuevo Exchange Online dedicado

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Puede configurar el acceso condicional para Exchange Online o Exchange Online dedicado con Microsoft Intune. Para más información sobre cómo funciona el acceso condicional, consulte el artículo [Proteger el acceso al correo electrónico, a O365 y a otros servicios](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

> [!NOTE]
>Si tiene un entorno de Exchange Online dedicado y necesita averiguar si es la configuración nueva o heredada, póngase en contacto con su administrador de cuentas.

## <a name="before-you-begin"></a>Antes de comenzar

Para configurar el acceso condicional, debe:

-   Tener una **suscripción de Office 365 que incluya Exchange Online (por ejemplo, E3)** y los usuarios deben tener licencia para Exchange Online.

- Tener una **suscripción de Enterprise Mobility + Security (EMS)** o una **suscripción de Azure Active Directory (Azure AD) Premium** y los usuarios deben tener la licencia de EMS o Azure AD. Para obtener más detalles, vea la [página de precios de Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) o la [página de precios de Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).

-  Considerar la posibilidad de configurar el **conector de servicio a servicio de Intune** opcional, que conecta [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] a Exchange Online y facilita la administración de información de dispositivos a través de la consola de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. No necesita usar el conector para usar directivas de cumplimiento o de acceso condicional, pero sí para ejecutar informes que ayuden a evaluar el impacto del acceso condicional.
    -  Obtenga más información sobre el [Intune Service to Service Connector](intune-service-to-service-exchange-connector.md).

   > [!NOTE]
   > No configure el Intune Service to Service Connector si piensa usar el acceso condicional tanto para Exchange Online como para Exchange local.

### <a name="device-compliance-requirements"></a>Requisitos de cumplimiento del dispositivo

Cuando configura directivas de acceso condicional y se aplican a un usuario, antes de que este pueda conectarse a su correo electrónico, el **dispositivo** que usa debe ser:

-   Un PC unido a un dominio o estar **inscrito** con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-  Debe estar **registrado en Azure Active Directory**. Esto sucede automáticamente cuando el dispositivo se inscribe con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Además, el identificador de Exchange ActiveSync del cliente debe registrarse con Azure Active Directory.

  El servicio Registro de dispositivos de Azure Active Directory se activa automáticamente para los clientes de Intune y Office 365. Los clientes que ya hayan implementado el servicio Registro de dispositivos de ADFS no podrán ver los dispositivos registrados en la instancia local de Active Directory.

-   Debe ser **compatible** con todas las directivas de cumplimiento de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] que se han implementado en el dispositivo, o bien debe estar unido a un dominio local.

### <a name="when-the-device-is-not-compliant"></a>Cuando el dispositivo no es conforme

Si no se cumple una directiva de acceso condicional, el dispositivo inmediatamente se pone en cuarentena y el usuario recibe un correo electrónico con una de las siguientes notificaciones de cuarentena cuando inicia sesión:

- Si el dispositivo no está inscrito con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o no está registrado en Azure Active Directory, se muestra un mensaje con instrucciones sobre cómo instalar la aplicación de portal de empresa, inscribir el dispositivo y activar el correo electrónico. Este proceso también asocia el identificador de Exchange ActiveSync del dispositivo con el registro en Azure Active Directory.

-   Si se considera que el dispositivo no es compatible con las reglas de la directiva de cumplimiento, se dirige al usuario al sitio web del portal de empresa de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o a la aplicación de portal de empresa, donde encontrará información sobre el problema y sobre cómo resolverlo.

### <a name="how-conditional-access-works-with-exchange-online"></a>Cómo funciona el acceso condicional con Exchange Online

En el diagrama siguiente se muestra el flujo que usan las directivas de acceso condicional para Exchange Online.

![Diagrama que muestra los puntos de decisión que determinan si se permite el acceso a un dispositivo o se bloquea](../media/ConditionalAccess8-1.png)

## <a name="support-for-mobile-devices"></a>Compatibilidad con dispositivos móviles
Puede proteger el acceso al correo electrónico de Exchange Online desde **Outlook** y otras **aplicaciones que usan la autenticación moderna**. No se admite lo siguiente:

- Android 4.0 y versiones posteriores, Samsung Knox Standard 4.0 y versiones posteriores, y Android for Work
- iOS 8.0 y versiones posteriores

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

La **autenticación moderna** proporciona el inicio de sesión basado en la biblioteca de autenticación de Active Directory (ADAL) a los clientes de Microsoft Office.

-   La autenticación basada en ADAL permite a los clientes de Office realizar la autenticación basada en explorador (también conocida como autenticación pasiva). Para realizar la autenticación, se envía un usuario a una página web de inicio de sesión.
-   Este nuevo método de inicio de sesión permite mejorar la seguridad como la **autenticación multifactor** y la **autenticación basada en certificados**. Para obtener información más detallada, vea [Cómo funciona la autenticación moderna](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517). Puede configurar reglas de notificaciones de ADFS para bloquear protocolos de autenticación no moderna. Se proporcionan instrucciones detalladas en el [Escenario 3: Bloquear todo el acceso externo a Office 365 excepto las aplicaciones basadas en explorador](https://technet.microsoft.com/library/dn592182.aspx).

Puede proteger el acceso a **Outlook Web Access (OWA)** en Exchange Online cuando un usuario accede a él desde un explorador en dispositivos **iOS** y **Android**. Solo se permite el acceso desde exploradores compatibles en dispositivos que también lo sean:

* Safari (iOS)
* Chrome (Android)
* Intune Managed Browser (iOS, Android 5.0 y versiones posteriores)

   > [!IMPORTANT]
   > **Los exploradores no compatibles están bloqueados**.

**La aplicación OWA para iOS y Android puede modificarse de modo que no use la autenticación moderna, y no se admite. El acceso desde la aplicación OWA se debe bloquear mediante reglas de notificaciones de ADFS.**


Puede proteger el acceso al correo electrónico de Exchange desde el **cliente de correo electrónico de Exchange ActiveSync** integrado en las siguientes plataformas:

- Android 4.0 y versiones posterior, Samsung Knox Standard 4.0 y versiones posteriores

- iOS 8.0 y versiones posteriores

- Windows Phone 8.1 y versiones posteriores

## <a name="support-for-pcs"></a>Compatibilidad para equipos

Puede configurar el acceso condicional para PC que ejecutan aplicaciones de escritorio de Office, para que tengan acceso a **Exchange Online** y **SharePoint Online** en los PC que cumplen los requisitos siguientes:

-   El PC debe ejecutar Windows 7.0, Windows 8.1 o Windows 10.

  >[!NOTE]
  > Para usar el acceso condicional con equipos Windows 10, debe actualizarlos con la Actualización de aniversario de Windows 10.

  El equipo debe estar unido a un dominio o cumplir las reglas de la directiva de cumplimiento.

  Para que se considere compatible, el equipo debe estar inscrito en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y cumplir las directivas.

  Para los PC unidos a un dominio debe configurar el acceso condicional para [registrar automáticamente el dispositivo](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) con Azure Active Directory.

  >[!NOTE]
    >No se admite el acceso condicional en los PC que ejecutan el cliente del equipo de Intune.

-   [La autenticación moderna de Office 365 debe estar habilitada](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) y tener las actualizaciones más recientes de Office.

    La autenticación moderna proporciona el inicio de sesión basado en la biblioteca de autenticación de Active Directory (ADAL) a los clientes de Office 2013 o Windows. Permite mejorar la seguridad como la **autenticación multifactor** y la **autenticación basada en certificados**.

-   Las reglas de notificaciones de ADFS se configuran para bloquear protocolos de autenticación no moderna. Se proporcionan instrucciones detalladas en el [Escenario 3: Bloquear todo el acceso externo a Office 365 excepto las aplicaciones basadas en explorador](https://technet.microsoft.com/library/dn592182.aspx).

## <a name="configure-conditional-access"></a>Configurar el acceso condicional
### <a name="step-1-configure-and-deploy-a-compliance-policy"></a>Paso 1: configurar e implementar una directiva de cumplimiento
Asegúrese de [crear](create-a-device-compliance-policy-in-microsoft-intune.md) e [implementar](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) una directiva de cumplimiento para los grupos de usuarios que también obtendrán la directiva de acceso condicional.


> [!IMPORTANT]
> Si no ha implementado una directiva de cumplimiento, los dispositivos se consideran compatibles y se les permite el acceso a Exchange.

### <a name="step-2-evaluate-the-effect-of-the-conditional-access-policy"></a>Paso 2: evaluar el impacto de la directiva de acceso condicional
Puede usar los **Informes de inventario de dispositivos móviles** para identificar los dispositivos a los que se les podría bloquear el acceso a Exchange después de configurar la directiva de acceso condicional.

Para ello, configure una conexión entre [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y Exchange mediante el [conector de servicio a servicio de Microsoft Intune](intune-service-to-service-exchange-connector.md).
1.  Vaya a **Informes** > **Informes de inventario de dispositivos móviles**.
![Captura de pantalla de la página de informes de inventario de dispositivos móviles](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  En los parámetros del informe, seleccione el grupo de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] que quiere evaluar y, si es necesario, las plataformas de dispositivos en las que se aplicará la directiva.
3.  Después de que haya seleccionado los criterios que satisfagan las necesidades de la organización, elija **Ver informe**.
El Visor de informes se abrirá en una nueva ventana.
![Captura de pantalla de un ejemplo de informe de inventario de dispositivos móviles](../media/IntuneSA2cViewReport.PNG)

Después de ejecutar el informe, examine estas cuatro columnas para determinar si un usuario se bloqueará:

-   **Canal de administración**: indica si Intune, Exchange ActiveSync o ambas aplicaciones administran el dispositivo.

-   **Registrado en AAD**: indica si el dispositivo está registrado con Azure Active Directory (lo que se conoce como Unión al área de trabajo).

-   **Conforme**: indica si el dispositivo cumple con las directivas de cumplimiento que ha implementado.

-   **Id. de Exchange ActiveSync**: los dispositivos iOS y Android deben tener su id. de Exchange ActiveSync asociado al registro del dispositivo en Azure Active Directory. Esto sucede cuando un usuario pulsa el vínculo **Activar correo electrónico** en el mensaje de correo en cuarentena.

    > [!NOTE]
    > Los dispositivos Windows Phone siempre muestran un valor en esta columna.

Los dispositivos que forman parte de un grupo de destino tienen bloqueado el acceso a Exchange, a menos que los valores de la columna coincidan con los de la tabla siguiente:

--------------------------
|Canal de administración|Registrado en AAD|Conforme|Id. de Exchange ActiveSync|Acción resultante|
|----------------------|------------------|-------------|--------------------------|--------------------|
|**Administrado por Microsoft Intune y Exchange ActiveSync**|Sí|Sí|Se muestra un valor|Se permite el acceso al correo electrónico|
|Cualquier otro valor|No|No|No se muestra ningún valor|El acceso al correo electrónico está bloqueado|
----------------------
Puede exportar el contenido del informe y usar la columna **Dirección de correo electrónico** para informar a los usuarios de que se les va a bloquear.

### <a name="step-3-configure-user-groups-for-the-conditional-access-policy"></a>Paso 3: configurar grupos de usuarios para la directiva de acceso condicional
Las directivas de acceso condicional se aplican a diferentes grupos de seguridad de usuarios de Azure Active Directory. También puede excluir determinados grupos de usuarios de una directiva de acceso condicional. Cuando un usuario es destinatario de una directiva, cada dispositivo que use debe ser compatible con el fin de obtener acceso al correo electrónico.

Estos grupos se pueden configurar en el **Centro de administración de Office 365**o en el **portal de cuentas de Intune**.

Se pueden especificar dos tipos de grupo en cada directiva:

-   **Grupos de destino**: grupos de usuarios a los que se aplica la directiva.

-   **Grupos exentos**: grupos de usuarios que están exentos de la directiva (opcional).

Si un usuario pertenece a ambos grupos, estará exento de la directiva.

Solo se evalúan los grupos en los que se aplica la directiva de acceso condicional.

### <a name="step-4-configure-the-conditional-access-policy"></a>Paso 4: configurar la directiva de acceso condicional

>[!NOTE]
> También puede crear una directiva de acceso condicional en la consola de administración de Azure AD. La consola de administración de Azure AD le permite crear una directiva de acceso condicional de dispositivos de Intune (denominada **directiva de acceso condicional basada en dispositivos** en Azure AD), además de otras directivas de acceso condicional, como la autenticación multifactor.

>También puede establecer directivas de acceso condicional para aplicaciones empresariales de terceros compatibles con Azure AD, como Salesforce y Box. Para más información, vea [Establecimiento de una directiva de acceso condicional basado en dispositivos para aplicaciones conectadas a Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-policy-connected-applications/).


1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** > **Acceso condicional** > **Directiva de Exchange Online**.

2.  En la página **Directivas de Exchange Online**, seleccione **Habilitar directiva de acceso condicional para Exchange Online**.

    > [!NOTE]
    > Si no ha implementado una directiva de cumplimiento, los dispositivos se consideran compatibles.
    >
    > Independientemente del estado de cumplimiento, todos los usuarios a los que se aplique la directiva deben inscribir sus dispositivos en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

3.  En **Acceso a la aplicación**, en el caso de las aplicaciones que usan la autenticación moderna, tiene dos maneras de elegir en qué plataformas se debe aplicar la directiva. Las plataformas compatibles incluyen Android, iOS, Windows y Windows Phone.

    -   **Todas las plataformas**

        Esto requiere que cualquier dispositivo que se usa para tener acceso a **Exchange Online** se inscriba en Intune y que sea compatible con las directivas. Cualquier aplicación cliente que use la **autenticación moderna** estará sujeta a la directiva de acceso condicional. Si la plataforma no es compatible actualmente con Intune, el acceso a **Exchange Online** se bloqueará.

        Seleccionar la opción **Todas las plataformas** significa que Azure Active Directory aplica esta directiva a todas las solicitudes de autenticación, independientemente de la plataforma notificada por la aplicación cliente. Todas las plataformas tienen que inscribirse y ser compatibles, excepto:
        *    Los dispositivos Windows, que deben estar inscritos y ser compatibles, estar unidos a dominio con Active Directory local, o ambos.
        * Plataformas no compatibles como Mac OS. Por el contrario, las aplicaciones que usan la autenticación moderna y proceden de estas plataformas seguirán bloqueadas.

    -   **Plataformas específicas**

         La directiva de acceso condicional se aplica a cualquier aplicación cliente que use la **autenticación moderna** en las plataformas de dispositivo que especifique.

4. En **Outlook Web Access (OWA)**, puede permitir el acceso a Exchange Online solo a través de los exploradores admitidos: Safari (iOS) y Chrome (Android). El acceso desde otros exploradores está bloqueado. Las mismas restricciones de plataforma que seleccionó para el acceso a la aplicación de Outlook también se aplican aquí.

  En los dispositivos **Android**, los usuarios deben habilitar el acceso al explorador. Para ello, el usuario debe habilitar la opción **Habilitar acceso al explorador** en el dispositivo inscrito de este modo:
  1.    Abra la **aplicación de portal de empresa**.
  2.    Vaya a la página **Configuración** desde los tres puntos (...) o desde el botón del menú de hardware.
  3.    Pulse el botón **Habilitar acceso al explorador**.
  4.    En el explorador Chrome, cierre la sesión de Office 365 y reinicie Chrome.

  En las plataformas **iOS** y **Android**, para identificar el dispositivo que se usa para obtener acceso al servicio, Azure Active Directory emite un certificado de seguridad de la capa de transporte (TLS) para el dispositivo. El dispositivo muestra el certificado en una petición para que el usuario final lo seleccione, como se muestra en las capturas de pantalla siguientes. El usuario debe seleccionar este certificado para poder continuar usando el explorador.

  **iOS**

  ![Captura de pantalla de la solicitud de certificado en un iPad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![captura de pantalla de la petición de certificado en un dispositivo Android](../media/mdm-browser-ca-android-cert-prompt.png)

5.  En **Aplicaciones de Exchange ActiveSync**, puede elegir bloquear el acceso a Exchange Online de dispositivos no conformes. También puede seleccionar si quiere permitir o bloquear el acceso al correo cuando el dispositivo no ejecuta una plataforma compatible. Las plataformas compatibles incluyen Android, iOS, Windows y Windows Phone.

 Aplicaciones de Exchange Active Sync en dispositivos **Android for Work**:
 -  Solo se admiten las aplicaciones **Gmail** y **Nine Work** en el **perfil de trabajo** en los dispositivos Android for Work. Para que el acceso condicional funcione en dispositivos Android for Work, debe implementar un perfil de correo electrónico para la aplicación Gmail o Nine Work, y también implementarla como una instalación **requerida**.

6.  En **Grupos de destino**, seleccione los grupos de seguridad de Active Directory de usuarios en los que se aplica la directiva. Puede elegir como destino todos los usuarios o puede seleccionar una lista de grupos de usuarios.
![Captura de pantalla de la página de la directiva de acceso condicional de Exchange Online que muestra las opciones de grupo de destino y exento](../media/IntuneSA5eTargetedExemptedGroups.PNG)
    > [!NOTE]
    > En el caso de los usuarios que se encuentren en los **Grupos de destino**, las directivas de Intune reemplazan las directivas y reglas de Exchange.
    >
    > Exchange solo aplica sus directivas y sus reglas de permiso, bloqueo y cuarentena si:
    >
    > -   Un usuario no tiene licencia para Intune.
    > -   Un usuario tiene licencia para Intune pero no pertenece a ningún grupo de seguridad de destino de la directiva de acceso condicional.

6.  En **Grupos exentos**, seleccione los grupos de seguridad de Active Directory que se van a excluir de la directiva. Si un usuario está incluido tanto en los grupos de destino como en los grupos exentos, está exento de la directiva.

7.  Cuando termine, elija **Guardar**.

-   No es necesario implementar la directiva de acceso condicional, ya que surte efecto inmediatamente.

-   Cuando un usuario crea una cuenta de correo electrónico, el dispositivo se bloquea inmediatamente.

-   Si un usuario bloqueado inscribe el dispositivo con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y corrige los problemas de no conformidad, el acceso al correo electrónico se desbloquea en dos minutos.

-   Si el usuario anula la inscripción de su dispositivo, el correo se bloquea después de aproximadamente seis horas.

Para ver algunos **escenarios de ejemplo sobre la configuración de la directiva de acceso condicional para proteger el acceso a los dispositivos**, vea [Proteger el acceso al correo electrónico con Microsoft Intune: escenarios de ejemplo](restrict-email-access-example-scenarios.md).

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Supervisar el cumplimiento y las directivas de acceso condicional

#### <a name="to-view-devices-that-are-blocked-from-exchange"></a>Para ver los dispositivos que tienen bloqueado el acceso a Exchange

En el panel de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], elija el icono **Dispositivos bloqueados de Exchange** para que se muestren el número de dispositivos bloqueados y los vínculos para más información.
![Captura de pantalla del panel de Intune que muestra el número de dispositivos a los que se ha bloqueado el acceso a Exchange](../media/IntuneSA6BlockedDevices.PNG)

## <a name="next-steps"></a>Pasos siguientes
- [Proteger el acceso a SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

- [Proteger el acceso a Skype Empresarial Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)



<!--HONumber=Feb17_HO2-->


