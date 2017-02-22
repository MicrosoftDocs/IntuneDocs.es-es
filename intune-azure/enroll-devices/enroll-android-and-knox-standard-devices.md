---
title: "Inscripción de dispositivos Android en Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda cómo inscribir dispositivos Android en la versión preliminar de Intune Azure."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: edd6303f3bb05dfff758cbb7d4bd08e21f083998


---

# <a name="enroll-android-devices"></a>Inscripción de dispositivos Android

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Como administrador de Intune, puede habilitar la administración de dispositivos Android, incluidos dispositivos Samsung Knox Standard, desde el Portal de empresa. Luego los usuarios pueden inscribir sus dispositivos mediante la aplicación del Portal de empresa, disponible en Google Play.

## <a name="prerequisite"></a>Requisito previo

Debe establecer la entidad de MDM en **Microsoft Intune** para prepararse para administrar dispositivos móviles. Para obtener instrucciones, consulte [Set the MDM authority](set-mdm-authority.md) (Establecimiento de la autoridad de MDM). Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles, así que es posible que ya lo haya configurado. 

## <a name="set-up-android-enrollment"></a>Configuración de la inscripción de Android

De forma predeterminada, Intune está configurado para permitir la inscripción de dispositivos Android y Samsung Knox Standard. 

Para ver la configuración para permitir o bloquear la inscripción de dispositivos Android, vaya a la hoja de Intune en el portal de Azure y elija **Inscripción** > **Restricciones de inscripción**. 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.

Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Android en Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android). El proceso de inscripción indica a los usuarios lo que pueden esperar y qué pueden o no ver los administradores de TI en sus dispositivos.

Para más información acerca de otras tareas de usuario final, consulte estos artículos:

- [Recursos sobre la experiencia del usuario final con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Uso de un dispositivo Android con Intune](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)


<!--HONumber=Feb17_HO1-->


