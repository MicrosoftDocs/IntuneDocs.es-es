---
title: Perfiles de certificado para el acceso a los recursos | Microsoft Intune
description: "Proteja VPN, Wi-Fi y el acceso al correo electrónico con un certificado instalado en cada dispositivo de usuario."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 98c32f924b60734d9a592ebdd7e00429dc32af26


---

# Secure resource access with certificate profiles in Microsoft Intune (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)
Si habilita el acceso para los recursos corporativos a través de VPN, Wi-Fi o perfiles de correo electrónico, tiene la opción de protegerlo con un certificado instalado en el dispositivo de cada usuario. Funciona de la siguiente manera:

1. Asegúrese de disponer de la infraestructura de certificados correcta, como se explica en [Configurar la infraestructura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) o en [Configurar la infraestructura de certificados](configure-certificate-infrastructure-for-pfx.md).

2. Instale un certificado raíz (o certificado de CA intermedia) en cada dispositivo para que el dispositivo reconozca la legitimidad de la entidad de certificación. Esto se hace mediante la creación e implementación de un **perfil de certificado de confianza**. Al implementar este perfil, los dispositivos que se administran con Intune solicitarán y recibirán el certificado raíz. Debe crear un perfil independiente para cada plataforma. El **perfil de certificado de confianza** está disponible para estas plataformas:
 -  iOS 7.1 y versiones posteriores
 -  Mac OS X 10.9 y versiones posteriores
 -  Android 4.0 y versiones posteriores
 -  Windows 8.1 y posterior
 -  Windows Phone 8.1 y versiones posteriores

3. Configure cada dispositivo para que pida un certificado para la autenticación del acceso al correo, VPN y Wi-Fi, tal como se describe en [Configure intune certificate profiles](configure-intune-certificate-profiles.md) (Configurar perfiles de certificado de Intune). Puede crear e implementar un **perfil de certificado PKCS #12 (.PFX)** o un **perfil de certificado SCEP** para dispositivos en estas plataformas:

-  Android 4.0 y versiones posteriores
-  iOS 7.1 y versiones posteriores
-  Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores

Use el **perfil de certificado SCEP** para:
-   Mac OS X 10.9 y versiones posteriores
-   Windows Phone 8.1 y versiones posteriores

Debe crear un perfil independiente para cada plataforma. Al crear el perfil, debe asociarlo al **perfil de certificado raíz de confianza** que creó previamente.

> [!NOTE]           
> -    Si no dispone de una entidad de certificación empresarial, tiene que crear una.
>- Si decide, en función de sus plataformas de dispositivo, usar el Protocolo de inscripción de certificados simple (SCEP), también debe configurar un servidor del Servicio de inscripción de dispositivos de red (NDES).
>-  Si planea usar SCEP o perfiles PFX, tendrá que descargar y configurar el conector de certificado de Microsoft Intune.
> Se describe la configuración de todos ellos en [Configurar la infraestructura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) y [Configurar la infraestructura de certificados](configure-certificate-infrastructure-for-pfx.md).

### Pasos siguientes
- [Configurar la infraestructura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md)
- [Configurar la infraestructura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md)
- [Configurar perfiles de certificado de Intune](configure-intune-certificate-profiles.md)



<!--HONumber=Jul16_HO4-->


