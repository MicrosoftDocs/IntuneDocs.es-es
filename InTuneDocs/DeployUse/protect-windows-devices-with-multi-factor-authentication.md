---
title: Multi-Factor Authentication para Windows | Microsoft Intune
description: Intune integra Multi-Factor Authentication (MFA) para ayudar a proteger los recursos corporativos.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4993982adcfbc960ad71022268cc44d216d1c585
ms.openlocfilehash: fb4ae43ffcbec24147e2e3ce3c96ec795289c925


---

# Protect Windows devices with multi-factor authentication
Microsoft Intune integra Multi-Factor Authentication (MFA) para ayudar a proteger los recursos corporativos. MFA necesita factores de autenticación como la autenticación de texto además de nombres de usuario y contraseñas. Intune admite el uso de MFA durante la inscripción de dispositivos de escritorio y móviles de Windows 8.1 o posterior, Windows Phone 8.1 o Windows 10.

## Requisitos de infraestructura local para MFA de ADFS
Para configurar la autenticación multifactor, necesita lo siguiente:

-   **Un dominio de Active Directory al que esté unido el servidor de ADFS.**

-   **n servidor de Servicios de federación de Active Directory (ADFS), configurado para MFA.** Un servidor que ejecute Windows Server 2012 R2 y esté configurado como un servidor de AD FS. Para obtener más información, consulte [Protección de recursos en la nube y locales mediante Servidor Azure Multi-Factor Authentication con Windows Server 2012 R2 AD FS](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/).

Todos los servidores enumerados anteriormente deben cumplir los requisitos del sistema incluidos en [Requisitos del sistema e información de instalación de Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx).

#### MFA con Intune
Si la organización tiene una infraestructura de TI local que incluye un dominio de Active Directory con Servicios de federación de Active Directory (AD FS), puede configurar MFA en el servidor de federación y luego habilitar MFA para la inscripción en Intune. Al configurar MFA en Intune, los usuarios pueden autenticarse una vez, durante la inscripción, y luego usar los recursos corporativos sin repetir el proceso de MFA cada vez.

>[!NOTE]
>Se puede requerir MFA por usuario o por grupo en el servidor de ADFS.  

#### MFA sin Intune
Si configura MFA en el servidor de federación, pero no habilita MFA para la inscripción en Intune, los usuarios deberán usar MFA cada vez que obtengan acceso a los recursos corporativos (no solo en la inscripción del dispositivo).

También puede usar MFA de Azure Active Directory (Azure AD) para exigir MFA por usuario cada vez que los usuarios tengan acceso a los recursos corporativos. MFA de Azure AD es un servicio en la nube que no requiere ninguna infraestructura de TI local. Para obtener más información sobre la configuración de MFA de Azure AD, vea [Introducción a Azure Multi-Factor Authentication en la nube](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/).

## Solicitar MFA de ADFS durante la inscripción de dispositivos Windows
Para obtener información sobre cómo habilitar MFA en ADFS, consulte [Administrar riesgos con la autenticación adicional de Multi-Factor Authentication para aplicaciones confidenciales](http://technet.microsoft.com/library/dn280949.aspx).

## Configurar MFA de inscripción de dispositivos en Intune
>[!Important]  
>Habilite MFA en su inquilino de Azure AD o en el entorno local antes de que necesite MFA para realizar la inscripción de dispositivos Windows en Intune. Si no lo hace, los usuarios que intentan inscribir sus dispositivos Windows o que intentan unir los dispositivos a Azure AD verán un mensaje de error si está configurada la inscripción automática durante la unión a Azure AD.

1.  En la consola de administración de Intune, elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Multi-Factor Authentication**.

2.  Elija **Configurar Multi-factor Authentication** y, luego, elija **Habilitar Multi-factor Authentication**.



<!--HONumber=Aug16_HO3-->


