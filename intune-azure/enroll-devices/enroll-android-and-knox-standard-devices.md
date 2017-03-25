---
title: Inscribir dispositivos Android en Intune
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo inscribir dispositivos Android en la versión preliminar de Intune Azure."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: b664620f424f9ef612d17beb810564dbdd68ff79
ms.lasthandoff: 03/22/2017


---

# <a name="enroll-android-devices"></a>Inscripción de dispositivos Android

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune le permite administrar dispositivos Android, incluidos los dispositivos Samsung KNOX Standard. Para habilitar la administración de dispositivos, los usuarios deben inscribir sus dispositivos mediante la descarga de la aplicación del portal de empresa de Intune, que está disponible desde Google Play y, después, abrir la aplicación y seguir las instrucciones para su inscripción. Una vez que los dispositivos Android estén bajo su administración, puede [crear directivas de cumplimiento](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android) y [administrar aplicaciones](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-management), entre otros.

## <a name="prerequisite"></a>Requisito previo

Debe establecer la entidad de MDM en **Microsoft Intune** para prepararse para administrar dispositivos móviles. Para obtener instrucciones, consulte [Set the MDM authority](set-mdm-authority.md) (Establecimiento de la autoridad de MDM). Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles, así que es posible que ya lo haya configurado.

## <a name="set-up-android-enrollment"></a>Configuración de la inscripción de Android

De manera predeterminada, Intune ya permite la inscripción de dispositivos Android y Samsung KNOX Standard.

Para bloquear la inscripción de dispositivos Android, o para bloquear solo la de los dispositivos Android de propiedad personal, vea [Set device type restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions) (Establecer restricciones de tipos de dispositivo).

Para establecer el número máximo de dispositivos que un usuario puede inscribir, vea [Set device limit restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions) (Establecer restricciones de límite de dispositivos).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.

Necesitará indicar a sus usuarios finales que vayan a Google Play para descargar la aplicación del portal de empresa de Intune y, después, que abran la aplicación y sigan las indicaciones para inscribir su dispositivo. La aplicación guía a los usuarios a través del proceso de inscripción, explicándoles lo que pueden esperar y lo que pueden y no pueden ver los administradores de TI en sus dispositivos.

También puede enviarles un vínculo sobre los pasos de inscripción en línea: [Inscriba el dispositivo Android en Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android).

Para más información acerca de otras tareas de usuario final, consulte estos artículos:

- [Recursos sobre la experiencia del usuario final con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [Uso de un dispositivo Android con Intune](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)

