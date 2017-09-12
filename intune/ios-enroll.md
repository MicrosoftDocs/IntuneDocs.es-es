---
title: "Elegir cómo inscribir dispositivos Windows en Intune"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo configurar la inscripción de dispositivos Windows en Microsoft Intune.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 72b30ceed928ed2d3768441a5b5c2fbd8ffdeea4
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="enroll-ios-devices-in-intune"></a>Inscripción de dispositivos iOS en Intune

Intune permite la administración de dispositivos móviles (MDM) de iPads y iPhones para conceder acceso a los usuarios al correo electrónico y las aplicaciones de la empresa.

Como administrador de Intune, puede habilitar la inscripción para dispositivos iOS. Puede permitir que los usuarios inscriban dispositivos propios, lo que se conoce como la inscripción "Bring Your Own Device" (BYOD). También puede habilitar la inscripción de dispositivos de la empresa.

## <a name="prerequisites-for-ios-enrollment"></a>Requisitos previos para la inscripción de iOS
Antes de que pueda habilitar dispositivos iOS, complete estos pasos:
- [Configurar Intune](setup-steps.md): estos pasos configurar la infraestructura de Intune. En concreto, la inscripción de dispositivos requiere que [establezca su autoridad de MDM](mdm-authority-set.md).
- [Obtención de un certificado push MDM de Apple](apple-mdm-push-certificate-get.md): Apple requiere un certificado para habilitar la administración de dispositivos iOS y macOS.

## <a name="user-owned-ios-devices-byod"></a>Dispositivos iOS corporativos (BYOD)

Puede permitir que los usuarios inscriban sus dispositivos personales para la administración de Intune. Esto se conoce como "Bring Your Own Device" o BYOD. Tras completar los requisitos previos y asignar licencias a los usuarios, estos podrán descargar la aplicación Portal de empresa para iOS del App Store y seguir las instrucciones de inscripción.

## <a name="company-owned-ios-devices"></a>Dispositivos iOS propiedad de la empresa
Para las organizaciones que adquieran dispositivos para sus usuarios, Intune admite los métodos de inscripción de dispositivos de empresa siguientes para iOS:

- Programa de inscripción de dispositivos (DEP) de Apple
- Apple School Manager
- Inscripción de Apple Configurator mediante el Asistente de configuración
- Inscripción directa de Apple Configurator

También puede inscribir dispositivos iOS de empresa con una cuenta de [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programa de inscripción de dispositivos
Las organizaciones pueden adquirir dispositivos iOS a través del Programa de inscripción de dispositivos (DEP) de Apple. DEP permite implementar un perfil de inscripción "de forma inalámbrica" que traiga los dispositivos a la administración. Más información sobre el [Programa de inscripción de dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager es un programa de compra e inscripción de dispositivos para centros escolares. Al igual que DEP, puede implementar un perfil para inscribir dispositivos en la administración. Más información sobre [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Puede inscribir dispositivos iOS con Apple Configuration en un equipo Mac. Para preparar los dispositivos, se conectan mediante USB y se instala un perfil de inscripción. Puede inscribir dispositivos con Apple Configuration de dos maneras:
- Inscripción con el Asistente de configuración: este proceso restablece el dispositivo a la configuración de fábrica, lo prepara para ejecutar el Asistente de configuración e instala las directivas de la empresa para el nuevo usuario del dispositivo.
- Inscripción directa: este proceso no restablece los valores de fábrica del dispositivo e inscribe el dispositivo con una directiva predefinida. Este método está destinado a los dispositivos sin afinidad de usuario.

Más información sobre [Inscripción de Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).
