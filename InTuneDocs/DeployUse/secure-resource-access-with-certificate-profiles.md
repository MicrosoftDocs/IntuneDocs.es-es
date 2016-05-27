---
# required metadata

title: Habilitar el acceso a los recursos de empresa mediante perfiles de certificados con Microsoft Intune | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune
Si habilita el acceso para los recursos corporativos a través de VPN, Wi-Fi o perfiles de correo electrónico, tiene la opción de protegerlo con un certificado instalado en el dispositivo de cada usuario. Funciona de la siguiente manera:

1. Asegúrese de que dispone de la infraestructura de certificados correcta, tal como se describe en [Configure certificate infrastructure](configure-certificate-infrastructure.md) (Configurar la infraestructura de certificados)..

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
> La configuración de todos estos elementos se describe en el tema [Configure certificate infrastructure](configure-certificate-infrastructure.md) (Configurar la infraestructura de certificados)..

### Pasos siguientes
- [Configurar la infraestructura de certificados](configure-certificate-infrastructure.md)
- [Configurar perfiles de certificado de Intune](configure-intune-certificate-profiles.md)



<!--HONumber=May16_HO1-->


