---
title: "Adición de pantallas de estado de inscripción"
titlesuffix: Azure portal
description: "Dé la bienvenida a los usuarios que inscriben dispositivos Windows 10."
keywords: 
author: barlan
manager: barlanmsft
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 479f2c1998cd8dfd637f1487a7f4c767b17a5fa7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="set-up-an-enrollment-status-screen"></a>Configurar una pantalla de estado de inscripción

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Cuando un usuario final inscribe un dispositivo Windows, lo que espera con ello es que sea capaz de tener acceso a todo lo que necesita para ser productivo inmediatamente después de la inscripción. Algo de lo que no son conscientes los usuarios finales es que sus dispositivos siguen recibiendo contenido, aplicaciones, directivas y configuraciones después de que la inscripción finalice.

Puede configurar una pantalla de estado de inscripción para proporcionar información adicional a los usuarios finales, de forma que estén informados sobre lo que realmente sucede tras el proceso de inscripción. Esta opción se encuentra en **inscripción de dispositivos** > **Inscripción de Windows** > **Pantalla de estado de la inscripción**.

![Pantalla de estado de la inscripción de Windows 10.](win10-enrollment-status-admin-setup.png)

Hay tres campos que se pueden definir: **Saludo**, **Mensaje** e **Hipervínculo de ayuda**, donde puede establecer el **Texto del vínculo** y la **Dirección URL de ayuda al usuario**.

Los usuarios finales también verán el progreso de la **Seguridad**, **Red**, **Aplicaciones** y **Certificados** que van a instalar.
