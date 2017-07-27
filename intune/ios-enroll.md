---
title: "Elegir cómo inscribir dispositivos Windows en Intune"
titleSuffix: Intune on Azure
description: "Obtenga información sobre cómo configurar la inscripción de dispositivos Windows en Microsoft Intune.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61bdbc7ca68995e23295cf099ce73dfdcaeba37c
ms.sourcegitcommit: 5eb209ae48173ddfdbbab131f12f3ac3498dcd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2017
---
# <a name="enroll-ios-devices-in-intune"></a>Inscripción de dispositivos iOS en Intune

Intune permite la administración de dispositivos móviles (MDM) de iPads y iPhones para conceder acceso a los usuarios al correo electrónico y las aplicaciones de la empresa.

Como administrador de Intune, puede habilitar la inscripción para dispositivos iOS. Puede permitir que los usuarios inscriban dispositivos propios, lo que se conoce como la inscripción "Bring Your Own Device" (BYOD). También puede habilitar la inscripción de dispositivos de la empresa.

## <a name="prerequisites-for-ios-enrollment"></a>Requisitos previos para la inscripción de iOS
Antes de que pueda habilitar dispositivos iOS, complete estos pasos:
- [Configurar Intune](setup-steps.md): estos pasos configurar la infraestructura de Intune. En concreto, la inscripción de dispositivos requiere que [establezca su autoridad de MDM](mdm-authority-set.md).
- [Obtención de un certificado push MDM de Apple](apple-mdm-push-certificate-get.md): Apple requiere un certificado para habilitar la administración de dispositivos iOS y macOS.

Una vez que se completen estos requisitos previos, los usuarios pueden instalar la aplicación Portal de empresa para inscribir dispositivos iOS personales, o bien el administrador puede configurar la administración de dispositivos iOS corporativos. Los administradores también pueden asignar [administradores de inscripción de dispositivos](device-enrollment-manager-enroll.md) que pueden inscribir muchos dispositivos con una sola cuenta de administración. Intune admite los siguientes métodos de inscripción de dispositivos iOS corporativos:

## <a name="device-enrollment-program"></a>Programa de inscripción de dispositivos
Las organizaciones pueden adquirir dispositivos iOS a través del Programa de inscripción de dispositivos (DEP) de Apple. DEP permite implementar un perfil de inscripción "de forma inalámbrica" que traiga los dispositivos a la administración. Más información sobre el [Programa de inscripción de dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager es un programa de compra e inscripción de dispositivos para centros escolares. Al igual que DEP, puede implementar un perfil para inscribir dispositivos en la administración. Más información sobre [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Puede inscribir dispositivos iOS con Apple Configuration en un equipo Mac. Para preparar los dispositivos, se conectan mediante USB y se instala un perfil de inscripción. Puede inscribir dispositivos con Apple Configuration de dos maneras:
- Inscripción con el Asistente de configuración: este proceso restablece el dispositivo a la configuración de fábrica, lo prepara para ejecutar el Asistente de configuración e instala las directivas de la empresa para el nuevo usuario del dispositivo.
- Inscripción directa: este proceso no restablece los valores de fábrica del dispositivo e inscribe el dispositivo con una directiva predefinida. Este método está destinado a los dispositivos sin afinidad de usuario.

Más información sobre [Inscripción de Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).
