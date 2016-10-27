---
title: "Acceso condicional basado en aplicación con Office 365 | Microsoft Intune"
description: "Comprenda los conceptos de cómo el acceso condicional para MAM puede ayudar a controlar qué aplicaciones tienen acceso a los servicios de Office 365."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 64eaba6918c4a5c7ccc39fb8ccfeae729a34ff4c
ms.openlocfilehash: a03faa57f9bf1ec6784f0b1ec2d41d3f4cd88a12


---

# Creación de una directiva que permita que solo las aplicaciones móviles que admiten directivas MAM de Intune para tener acceso a servicios de Office 365
[Las directivas de administración de aplicaciones móviles (MAM) de Intune](protect-apps-and-data-with-microsoft-intune.md) ayudan a proteger los datos de su compañía en dispositivos inscritos para administración de Intune. También puede utilizar directivas MAM en **dispositivos que poseen los empleados que no están inscritos para la administración de Intune**.  En este caso, aunque no administre el dispositivo, deberá asegurarse de que los datos y los recursos de la empresa están protegidos. Al usar el acceso condicional para MAM (CA MAM), puede crear una directiva que permita que solo las aplicaciones móviles que admiten directivas MAM de Intune tengan acceso a servicios de Office 365 como Exchange Online.

Por ejemplo, al permitir que solo la **aplicación Microsoft Outlook** acceda a Exchange Online, puede **bloquear las aplicaciones de correo integradas en iOS y Android**, que no tienen protección de datos desde las directivas MAM de Intune para obtener correo electrónico desde **Exchange Online**.

## Requisitos previos
**Antes** de configurar una directiva de acceso condicional de MAM, debe tener una **suscripción de Enterprise Mobility + Security o de Azure Active Directory Premium** y los usuarios deben tener la licencia de EMS o Azure AD. Para obtener más detalles, vea la [página de precios de Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) o la [página de precios de Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).


## Aplicaciones compatibles
**Exchange Online**
* Microsoft Outlook para Android e iOS

## Superposición con otros métodos de autenticación y acceso condicionales
### Acceso condicional de MAM con autenticación basada en certificados de Azure Active Directory

El acceso condicional de MAM no debe utilizarse con autenticación basada en certificados de Azure Active Directory (Azure AD). Solo puede tener uno de lo siguiente configurado a la vez.
### Acceso condicional de MAM con acceso condicional basado en el cumplimiento del dispositivo  

Puede configurar el [acceso condicional basado en el cumplimiento del dispositivo](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**acceso condicional del dispositivo**) en la [consola de administrador de Intune](https://manage.microsoft.com) o en la [consola de administración de Azure AD Premium] (https://manage.windowsazure.com). El acceso condicional del dispositivo requiere que los usuarios se conecten a Exchange Online solo a través de los dispositivos administrados por Intune que sean compatibles con la directiva de cumplimiento del dispositivo de Intune o equipos unidos a un dominio.  Si un usuario pertenece a uno o más grupos de seguridad que tienen como destino las directivas del acceso condicional de MAM y del acceso condicional del dispositivo, el usuario debe cumplir uno de los dos requisitos siguientes:
* La aplicación que se utiliza para acceder a la aplicación móvil que es compatible con el acceso condicional de MAM y el dispositivo en el que se está ejecutando la aplicación, tiene el **autenticador de iOS (para dispositivos iOS)** o **la aplicación Portal de empresa (para dispositivos Android)** instalado.
* El dispositivo utilizado para acceder al servicio está **administrado y es conforme con Intune** con la directiva de cumplimiento del dispositivo de Intune o es un **equipo unido al dominio**.  Estos son algunos ejemplos para ayudar a ilustrar esto:
  * Si un usuario intenta conectarse desde el **aplicación de correo electrónico de iOS nativa**, deben estar en un **dispositivo administrado y conformes** ya que la aplicación de correo electrónico nativo no es compatible con el acceso condicional de MAM.
  * Si un usuario intenta conectarse desde un **equipo doméstico Windows**, se aplicará la **directiva del acceso condicional del dispositivo**, que requiere que debe usar un equipo unido al dominio.


## ¿Qué se puede esperar al usar una aplicación con el acceso condicional de MAM?
El acceso condicional de MAM comprueba la identidad de la aplicación aprobada por medio de una aplicación de agente que debe estar presente en el dispositivo:
*  En **iOS**, la **aplicación Azure Authenticator** es la aplicación de agente.
* En **Android**, la **aplicación Portal de empresa de Intune** es la aplicación de agente. 

A los usuarios finales que inician sesión por primera vez, en una aplicación compatible con el acceso condicional de MAM, como OneDrive o Outlook, se les pedirá que instalen la aplicación de agente y registren el dispositivo con Azure AD. El registro del dispositivo en Azure AD (anteriormente conocido Workplace Join) creará un registro y un certificado del dispositivo con el que se emiten los tokens.  **No** es lo mismo que la **inscripción de MDM**. No existen perfiles de administración ni directivas que se apliquen y no hay ningún inventario tomado de las aplicaciones en el dispositivo.  Solo se realizará el proceso de instalación de la aplicación de agente y de registro del dispositivo en el primer uso de una aplicación administrada.


## Pasos siguientes
[Creación de una directiva de Exchange Online para aplicaciones MAM](mam-ca-for-exchange-online.md)

[Bloqueo de aplicaciones que no tienen autenticación moderna](block-apps-with-no-modern-authentication.md)

### Consulte también

[Protección de datos de aplicación mediante directivas MAM](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


