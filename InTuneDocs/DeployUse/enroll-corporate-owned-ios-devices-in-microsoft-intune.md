---
title: Inscribir dispositivos iOS de propiedad corporativa en Microsoft Intune | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 48359b44bec9ac3e1c9510debc01d2cf8abf6d2b


---

# Inscribir dispositivos iOS de empresa en Microsoft Intune
Microsoft Intune permite inscribir dispositivos iOS de propiedad corporativa con el programa de inscripción de dispositivos (DEP) de Apple o la herramienta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) que se ejecuta en un equipo Mac.

Puede inscribir dispositivos iOS de empresa de tres maneras:

-   **Inscripción con el asistente de configuración** : restablece la configuración de fábrica del dispositivo y lo prepara para que el nuevo usuario del dispositivo lo instale. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac donde se ejecute Apple Configurator para preconfigurar la inscripción. Tras esto, los dispositivos se entregan a los usuarios, que ejecutan el proceso del asistente de instalación, configuran el dispositivo con sus credenciales profesionales o educativas y finalizan el proceso de inscripción. [Inscribir dispositivos iOS con Apple Configurator y el asistente de instalación](ios-setup-assistant-enrollment-in-microsoft-intune.md)

-   **Inscripción directa:** crea un archivo compatible con Apple Configurator para su uso durante la preparación del dispositivo. No se restablece la configuración de fábrica del dispositivo inscrito pero no tiene ninguna afiliación de usuario. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac donde se ejecute Apple Configurator para inscribir el dispositivo. [Inscribir dispositivos iOS mediante inscripción directa de Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md)

-   **Programa de inscripción de dispositivos (DEP):** implementa un perfil de inscripción "de forma inalámbrica" en los dispositivos adquiridos a través del programa de inscripción de dispositivos de Apple. Cuando se ejecuta el asistente de instalación en el dispositivo, el dispositivo se inscribe en Intune.  Los usuarios no pueden anular la inscripción de dispositivos inscritos a través de DEP. [Inscribir dispositivos iOS del programa de inscripción de dispositivos](ios-device-enrollment-program-in-microsoft-intune.md)




### Consulte también
[Preparar la inscripción de dispositivos en Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


