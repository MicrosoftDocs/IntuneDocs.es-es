---
title: Habilitar el acceso a los recursos de empresa | Microsoft Intune
description: "Los perfiles de correo electrónico, Wi-Fi y VPN funcionan de manera conjunta para ayudar a los usuarios a acceder a los archivos y recursos que necesitan."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: ae9b3be57e4008d25f5222025c057fc4211f1119


---

# Habilitar el acceso a los recursos de empresa con Microsoft Intune
Los perfiles de correo electrónico, Wi-Fi y VPN de Microsoft Intune funcionan de manera conjunta para ayudar a los usuarios a obtener acceso a los archivos y recursos que necesitan para hacer su trabajo correctamente, estén donde estén. Los perfiles de certificado sirven para proteger ese acceso.

## [Perfiles de Wi-Fi](wi-fi-connections-in-microsoft-intune.md) y plataformas compatibles

Implementar la configuración de red inalámbrica para los usuarios. Mediante la implementación de esta configuración, se minimiza la intervención del usuario final necesaria para conectarse a la red corporativa.
#### Plataformas compatibles

|Windows 8.1 y posterior|Windows Phone 8.1 y versiones posteriores|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|Sí (se puede importar un perfil de Wi-Fi de Windows)|Sí (OMA-URI se puede configurar) |Sí|Sí|Sí|

## [Perfiles de VPN](vpn-connections-in-microsoft-intune.md) y plataformas compatibles
Implementar la configuración de red privada virtual (VPN) a los usuarios. Mediante la implementación de esta configuración, se minimiza la intervención del usuario final necesaria para conectarse a los recursos de la red corporativa.

|Windows 8.1 y posterior|Windows Phone 8.1 y versiones posteriores|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|Sí|Sí|Sí|Sí|Sí|

## [Perfiles de correo electrónico](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md) y plataformas compatibles
Cree, implemente y supervise la configuración de correo electrónico nativo en los dispositivos de su organización.

|Windows 8.1 y posterior|Windows Phone 8.1 y versiones posteriores|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|No|Sí|Sí|No|Sí|
> [!NOTE]
> [En esta entrada de blog del equipo de Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/) encontrará información sobre cómo configurar un perfil de Wi-Fi de Windows Phone 8.1 mediante OMA-URI.

## [Perfiles de certificado](secure-resource-access-with-certificate-profiles.md) y plataformas compatibles
Contribuya a proteger el acceso a los recursos de empresa tales como las redes inalámbricas y las conexiones VPN.

|Windows 8.1 y posterior|Windows Phone 8.1 y versiones posteriores|iOS|Android|Samsung KNOX|
|---------------------|---------------------------|---|-------|------------|
|Sí|Sí|Sí|Sí|Sí|



<!--HONumber=Jul16_HO4-->


