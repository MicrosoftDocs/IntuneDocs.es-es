---
title: Restringir el acceso a Skype Empresarial Online | Microsoft Intune
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1b2d7125-f63f-43cf-ac1e-94fbedf2a7e8
ms.reviewer: chrisgre
ms.suite: ems
ms.sourcegitcommit: 5cbf748ffee8fbb53f7e64a5499f06d5bd89c415
ms.openlocfilehash: c26f3b732eb42903c72e8655542ee1ed586f5c67


---

# Restringir el acceso a Skype Empresarial Online con Microsoft Intune
Use una directiva de acceso condicional para  **Skype Empresarial Online** para controlar el acceso a Skype Empresarial Online.
El acceso condicional tiene dos componentes:
- La directiva de cumplimiento del dispositivo, con la que debe cumplir el dispositivo para que se considere conforme.
- La directiva de acceso condicional, donde se especifican las condiciones que debe cumplir el dispositivo para tener acceso al servicio.
Para más información sobre cómo funciona el acceso condicional, vea el artículo [Restrict access to email and O365 services](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (Restringir el acceso al correo electrónico y servicios de O365).

Cuando un usuario determinado intenta usar Skype Empresarial Online en su dispositivo, se produce la siguiente evaluación:

![Diagrama que muestra los puntos de decisión que se usan para determinar si un dispositivo puede tener acceso a Skype Empresarial Online o si se bloquea](../media/ConditionalAccess_SkypeforBusiness.png)

**Antes** de configurar una directiva de acceso condicional para Skype Empresarial Online, debe:
- Tener una **suscripción de Skype Empresarial Online** y asignar una licencia de Skype Empresarial Online a los usuarios.
- Tener una suscripción a **Enterprise Mobility Suite** o **Azure Active Directory Premium**.
-   [Habilitar la autenticación moderna](https://docs.microsoft.com/en-us/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) para Skype Empresarial Online. 
-  Todos los usuarios finales deben usar **Skype Empresarial Online**. Si tiene una implementación con Skype Empresarial Online y Skype Empresarial local, la directiva de acceso condicional no se aplicará a los usuarios finales.

    El dispositivo que necesita tener acceso a Skype Empresarial Online:

-   Debe ser un dispositivo **Android** o **iOS**.

-   Debe estar **inscrito** con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-   Debe **cumplir** todas las directivas de cumplimiento de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] implementadas.


El estado del dispositivo se almacena en Azure Active Directory, que concede o bloquea el acceso según las condiciones especificadas.

Si no se cumple una condición, se presentará al usuario uno de los mensajes siguientes cuando inicie sesión:

-   Si el dispositivo no está inscrito con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o si no está registrado en Azure Active Directory, se muestra un mensaje con instrucciones sobre cómo instalar la aplicación de portal de empresa e inscribirse.

-   Si el dispositivo no es conforme, se muestra un mensaje que dirige al usuario a la aplicación de portal de empresa o al sitio web del portal de empresa de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], donde puede encontrar información sobre el problema y sobre cómo resolverlo.

## Configurar el acceso condicional para Skype Empresarial Online

### Paso 1: Configurar grupos de seguridad de Active Directory
Antes de empezar, configure los grupos de seguridad de Azure Active Directory para la directiva de acceso condicional. Estos grupos se pueden configurar en el **Centro de administración de Office 365**. Estos grupos se usarán para aplicar la directiva a los usuarios o para excluirlos de ella. Cuando un usuario es destinatario de una directiva, cada dispositivo que use debe ser conforme con el fin de obtener acceso a los recursos.

Puede especificar dos tipos de grupos para la directiva de Skype Empresarial:

-   **Grupos de destino**: contiene grupos de usuarios a los que se aplicará la directiva.

-   **Grupos exentos**: contiene grupos de usuarios que están exentos de la directiva.

Si un usuario pertenece a ambos grupos, estará exento de la directiva.

### Paso 2: Configurar e implementar una directiva de cumplimiento
[Cree](create-a-device-compliance-policy-in-microsoft-intune.md) e [implemente](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) una directiva de cumplimiento para todos los dispositivos que se verán afectados por la directiva. Dichos dispositivos serán los que usan los usuarios de los **Grupos de destino**.

> [!NOTE]
> [!NOTE] Mientras se implementan las directivas de cumplimiento en los grupos de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], las directivas de acceso condicional se aplican a los grupos de seguridad de Azure Active Directory.


> [!IMPORTANT]
> [!IMPORTANT] Si no ha implementado una directiva de cumplimiento, los dispositivos se considerarán no conformes.

Cuando esté listo, continúe con el **paso 3**.

### Paso 3: Configurar la directiva de Skype Empresarial Online
Después, configure la directiva para requerir que solo los dispositivos administrados y conformes puedan tener acceso a Skype Empresarial Online. Esta directiva se almacenará en Azure Active Directory.

####
1.  En la [Consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Directiva** > **Acceso condicional** > **Directiva de Skype Empresarial Online**.

![Captura de pantalla de la página de la directiva de acceso condicional de Skype Empresarial Online](./media/conditional_access_SFBPolicy.png)

2.  Seleccione **Habilitar la directiva de acceso condicional**.

3.  En **Acceso a la aplicación**, puede elegir aplicar la directiva de acceso condicional a:

    -   **iOS**

    -   **Android**

4.  En **Grupos de destino**, haga clic en **Modificar** para seleccionar los grupos de seguridad de Azure Active Directory a los que se aplicará la directiva. Puede elegir aplicarla a todos los usuarios o solo a un grupo específico de usuarios.

5.  En **Grupos exentos**, opcionalmente, haga clic en **Modificar** para seleccionar los grupos de seguridad de Azure Active Directory que se van a excluir de la directiva.

6.  Cuando haya terminado, haga clic en **Guardar**.

Acaba de configurar el acceso condicional para Skype Empresarial Online. No es necesario implementar la directiva de acceso condicional, ya que surte efecto inmediatamente.


## Supervisar el cumplimiento y las directivas de acceso condicional
En el área de trabajo **Grupos** , puede ver el estado de acceso condicional de los dispositivos.

Seleccione cualquier grupo de dispositivos móviles y, a continuación, en la pestaña **Dispositivos** , seleccione uno de los siguientes **Filtros**:

* **Dispositivos no registrados en AAD**: estos dispositivos están bloqueados en Skype Empresarial Online.

* **Dispositivos no conformes**: estos dispositivos están bloqueados en Skype Empresarial Online.

* **Dispositivos registrados en AAD y conformes**: estos dispositivos pueden tener acceso a Skype Empresarial Online.



<!--HONumber=Jul16_HO2-->


