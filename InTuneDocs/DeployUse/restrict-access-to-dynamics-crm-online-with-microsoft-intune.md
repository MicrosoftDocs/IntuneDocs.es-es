---
title: "Restringir el acceso al correo electrónico a Dynamics CRM Online | Microsoft Intune"
description: "Proteja y controle el acceso a Dynamics CRM en línea con el acceso condicional."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f1c4522b-5a34-4f5a-89d2-7809c4352af7
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: db1d43dd647122e7ba8ebd4e6df48e3c970a3392
ms.openlocfilehash: 233b7cad41fbd35e0fef615737fc41f8a49db35e


---

# Restringir el acceso al correo electrónico a Dynamics CRM Online con Intune
Puede controlar el acceso a Microsoft Dynamics CRM Online desde los dispositivos de iOS y Android con el acceso condicional de Microsoft Intune.  El acceso condicional de Intune tiene dos componentes:
* [La directiva de cumplimiento del dispositivo](introduction-to-device-compliance-policies-in-microsoft-intune.md), con la que debe cumplir el dispositivo para que se considere compatible.
* [La directiva de acceso condicional](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), donde se especifican las condiciones que debe cumplir el dispositivo para tener acceso al servicio.

Para obtener más información sobre cómo funciona el acceso condicional, lea el artículo [Restrict access to email, 0365, and other services (Restringir el acceso al correo electrónico, a O365 y a otros servicios)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

[!IMPORTANT] Para implementar el acceso condicional debe tener suscripciones a Intune y Azure Active Directory Premium, y los usuarios deben tener la licencia de ambos productos. La **suscripción a Enterprise Mobility + Security (EMS)** incluye suscripciones a Intune y Azure Active Directory Premium. Para obtener más información, consulte la [página de precios de Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing). Si no tiene la suscripción de EMS, puede obtener una para Azure Active Directory Premium. Consulte la [página de precios de Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/). 

Cuando un usuario determinado intenta usar la aplicación Dynamics CRM en su dispositivo, se produce la siguiente evaluación:

![Diagrama que muestra los puntos de decisión usados para determinar si un dispositivo puede tener acceso a un servicio o si se bloquea](../media/mdm-ca-dynamics-crm-flow-diagram.png)

El dispositivo que necesita tener acceso a Dynamics CRM Online:
* Debe ser un dispositivo **Android** o **iOS**.
* Debe estar **inscrito** en Microsoft Intune.
* Debe **cumplir** todas las directivas de cumplimiento de Microsoft Intune implementadas.

El estado del dispositivo se almacena en Azure Active Directory, que concede o bloquea el acceso según las condiciones especificadas.

Si no se cumple una condición, se presentará al usuario uno de los mensajes siguientes cuando inicie sesión:
* Si el dispositivo no está inscrito en Microsoft Intune o registrado en Azure Active Directory, se muestra un mensaje con instrucciones sobre cómo instalar la aplicación de portal de empresa e inscribirse.
* Si el dispositivo no es compatible, se muestra un mensaje que dirige al usuario al sitio web de portal de empresa de Microsoft Intune o a la aplicación de portal de empresa, donde puede encontrar información sobre el problema y sobre cómo resolverlo.

## Configurar un acceso condicional para Dynamics CRM Online  
### Paso 1: Configurar grupos de seguridad de Active Directory

Antes de empezar, configure los grupos de seguridad de Azure Active Directory para la directiva de acceso condicional. Estos grupos se pueden configurar en el **Centro de administración de Office 365**. Estos grupos se usarán para aplicar la directiva a los usuarios o para excluirlos de ella. Cuando un usuario es destinatario de una directiva, cada dispositivo que use debe ser conforme con el fin de obtener acceso a los recursos.

Puede especificar dos tipos de grupos para usarlos con la directiva de Dynamics CRM:
* **Grupos de destino**: contiene grupos de usuarios a los que se aplicará la directiva.
* **Grupos exentos**: contiene grupos de usuarios que están exentos de la directiva.

Si un usuario pertenece a ambos grupos, estará exento de la directiva.

### Paso 2: Configurar e implementar una directiva de cumplimiento
[Cree](create-a-device-compliance-policy-in-microsoft-intune.md) e [implemente](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) una directiva de cumplimiento para todos los dispositivos que se verán afectados por la directiva. Dichos dispositivos serán los que usen los usuarios de los Grupos de destino.

> [!NOTE]
> Mientras que las directivas de cumplimiento se implementan en los grupos de Microsoft Intune, las directivas de acceso condicional se aplican a los grupos de seguridad de Azure Active Directory.

> [!IMPORTANT]
> Si no ha implementado una directiva de cumplimiento, los dispositivos se considerarán no conformes.

Cuando esté listo, continúe en el paso 3.
### Paso 3: Configurar la directiva de Dynamics CRM
A continuación, configure la directiva para requerir que solo los dispositivos administrados y compatibles puedan tener acceso a Dynamics CRM. Esta directiva se almacenará en Azure Active Directory.

1.  En la consola de administración de Microsoft Intune, elija **Directiva > Acceso condicional > Directiva de Dynamics CRM Online**.

  ![Captura de pantalla de la página de la directiva de acceso condicional de Dynamics CRM Online](../media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  Seleccione **Habilitar la directiva de acceso condicional**.
3.  En **Acceso a la aplicación**, puede elegir aplicar la directiva de acceso condicional a:
  * **iOS**
  * **Android**
4.  En **Grupos de destino**, elija **Modificar** para seleccionar los grupos de seguridad de Azure Active Directory a los que se aplicará la directiva. Puede elegir aplicarla a todos los usuarios o solo a un grupo específico de usuarios.
5.  En **Grupos exentos**, opcionalmente, elija **Modificar** para seleccionar los grupos de seguridad de Azure Active Directory exentos de esta directiva.
6.  Cuando termine, elija **Guardar**.

Acaba de configurar el acceso condicional para Dynamics CRM. No es necesario implementar la directiva de acceso condicional, ya que surte efecto inmediatamente.
##  Supervisar el cumplimiento y las directivas de acceso condicional

En el área de trabajo **Grupos** , puede ver el estado de acceso condicional de los dispositivos.

Seleccione cualquier grupo de dispositivos móviles y, a continuación, en la pestaña **Dispositivos** , seleccione uno de los siguientes **Filtros**:
* **Dispositivos no registrados en AAD**: estos dispositivos están bloqueados en Dynamics CRM.
* **Dispositivos no compatibles**: estos dispositivos están bloqueados en Dynamics CRM.
* **Dispositivos registrados en AAD y compatibles**: estos dispositivos pueden tener acceso a Dynamics CRM.

##  Pasos siguientes
[Restringir el acceso a Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)

[Restringir el acceso a Exchange local](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
[Restringir el acceso a SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Restringir el acceso a Skype Empresarial Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)



<!--HONumber=Oct16_HO1-->


