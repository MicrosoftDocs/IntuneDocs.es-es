---
title: "Inscripción de dispositivos macOS en Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda a inscribir dispositivos macOS en la versión preliminar de Intune Azure."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 1/3/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2affcdbcdfcd690d671c7b20f9d1e14a74f764
ms.openlocfilehash: 171175689adca027181f3da4d05222117de97e13


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Inscripción de dispositivos macOS en la versión preliminar de Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Como administrador de Intune, puede administrar dispositivos macOS. De forma predeterminada, el portal de Azure permite a los usuarios inscribir sus dispositivos macOS. Basta con que indique a los usuarios que vayan al [sitio web del Portal de empresa](http://portal.manage.microsoft.com) e inscriban su dispositivo macOS. 

## <a name="prerequisites"></a>Requisitos previos

Complete los siguientes requisitos previos antes de configurar la inscripción de dispositivos macOS:

- [Configurar dominios](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Establecer la entidad de MDM](set-mdm-authority.md)
- [Crear grupos](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar el Portal de empresa](/intune-azure/manage-apps/company-portal-app.md)
- Asignar licencias de usuario en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtener un certificado push MDM de Apple](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>Configuración de la inscripción de macOS

De forma predeterminada, Intune ya está configurado para permitir la inscripción de dispositivos macOS. 

Para ver la configuración que permite o bloquea la inscripción de dispositivos macOS, vaya a la hoja de Intune en el portal de Azure y elija **Inscripción** > **Restricciones de inscripción**. 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.

Para obtener instrucciones de inscripción para usuarios finales, consulte [Inscribir un dispositivo macOS en Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos). El proceso de inscripción indica a los usuarios lo que pueden esperar y qué pueden o no ver los administradores de TI en sus dispositivos.

Para más información acerca de otras tareas de usuario final, consulte estos artículos:

- [Recursos sobre la experiencia del usuario final con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Uso de un dispositivo iOS o Mac OS con Intune](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)


<!--HONumber=Feb17_HO1-->


