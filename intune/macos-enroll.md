---
title: "Inscripción de dispositivos macOS en Intune"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo inscribir dispositivos macOS en Intune\"."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdf29fdc9c7098572ca9f06a65dc23320f7a08fb
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="enroll-macos-devices-in-intune"></a>Inscripción de dispositivos macOS en Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune le permite administrar dispositivos macOS. Para habilitar la administración de dispositivos, los usuarios deben inscribir sus dispositivos dirigiéndose al [sitio web del portal de empresa](http://portal.manage.microsoft.com) y seguir las indicaciones. Una vez que los dispositivos macOS estén bajo su administración, puede [crear una configuración personalizada para dispositivos macOS](custom-settings-macos.md). Próximamente habrá mas funciones.

## <a name="prerequisites"></a>Requisitos previos

Complete los siguientes requisitos previos antes de configurar la inscripción de dispositivos macOS:

- [Configurar dominios](custom-domain-name-configure.md)
- [Establecer la entidad de MDM](mdm-authority-set.md)
- [Crear grupos](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar el Portal de empresa](company-portal-app.md)
- Asignar licencias de usuario en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtener un certificado push MDM de Apple](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>Configuración de la inscripción de macOS

De manera predeterminada, Intune ya permite la inscripción de dispositivos macOS.

Para bloquear la inscripción de dispositivos macOS, vea [Set device type restrictions](enrollment-restrictions-set.md) (Establecer restricciones de tipos de dispositivo).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.

Necesitará indicar a sus usuarios finales que vayan al [sitio web del portal de empresa](http://portal.manage.microsoft.com) y sigan las indicaciones para inscribir sus dispositivos. También puede enviarles un vínculo sobre los pasos de inscripción en línea: [Inscriba el dispositivo macOS en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Para más información acerca de otras tareas de usuario final, consulte estos artículos:

- [Recursos sobre la experiencia del usuario final con Microsoft Intune](end-user-educate.md)
- [Uso de un dispositivo iOS o Mac OS con Intune](https://docs.microsoft.com/intune-user-help/using-your-ios-or-mac-os-x-device-with-intune)
