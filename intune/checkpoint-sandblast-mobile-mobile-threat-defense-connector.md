---
title: Conector SandBlast Mobile de Check Point con Intune
titlesuffix: Azure portal
description: "Integración de SandBlast de Check Point con Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d528ee9b72b5b7476845c0051f67f8a6ed887d1c
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Conector de defensa contra amenazas SandBlast Mobile de Check Point con Intune

Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por SandBlast Mobile de Check Point, una solución de defensa contra amenazas móviles integrada en Microsoft Intune. El riesgo se evalúa según la telemetría recopilada de dispositivos que ejecutan la aplicación SandBlast Mobile de Check Point.

Puede configurar directivas de acceso condicional según la evaluación de riesgos de SandBlast Mobile de Check Point habilitada mediante las directivas de cumplimiento de dispositivos de Intune, que puede usar a fin de permitir o bloquear dispositivos que no cumplan los requisitos para que no obtengan acceso a recursos corporativos en función de las amenazas detectadas.

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>¿Cómo ayudan Intune y SandBlast Mobile de Check Point a proteger los recursos de su empresa?

La aplicación SandBlast Mobile de Check Point para Android e iOS capta el sistema de archivos, la pila de red y la telemetría de aplicaciones y dispositivos cuando está disponible. Después, envía los datos de telemetría al servicio en la nube de SandBlast Mobile de Check Point para evaluar el riesgo del dispositivo frente a las amenazas móviles.

La directiva de cumplimiento de dispositivos de Intune incluye una regla para el conector de defensa contra amenazas SandBlast Mobile de Check Point, que se basa en la evaluación de riesgos de SandBlast de Check Point. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó. Si se detecta que el dispositivo no cumple con la directiva, se bloqueará el acceso de los usuarios a los recursos corporativos, como Exchange Online y SharePoint Online. Los usuarios también reciben los pasos de la aplicación móvil de SandBlast de Check Point instalada en sus dispositivos para resolver el problema y volver a obtener acceso a los recursos corporativos.

<!-- ## Sample scenarios

Here are some common scenarios:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

-   Connecting to corporate e-mail

-   Syncing corporate files with the OneDrive for Work app

-   Accessing company apps

**Block when malicious apps are detected:**

![Check Point MTD block when malicious apps are detected](./media/checkpoint-MTD-2.PNG)

**Access granted on remediation:**

![Check Point MTD access granted](./media/checkpoint-MTD-3.PNG)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

**Block network access through Wi-Fi:**

![Check Point MTD block network access through Wi-Fi](./media/checkpoint-MTD-4.PNG)

**Access granted on remediation:**

![Check Point MTD Wi-Fi access granted](./media/checkpoint-MTD-5.PNG)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

**Block SharePoint Online when network threats are detected:**

![Check Point MTD block SharePoint Online access](./media/checkpoint-MTD-6.PNG)

**Access granted on remediation:**

![Check Point MTD SharePoint Online access granted](./media/checkpoint-MTD-7.PNG)

## Supported platforms

-   **Android 4.1 and later**

-   **iOS 8 and later**

## Pre-requisites

-   Azure Active Directory Premium

-   Microsoft Intune subscription

-   Check Point SandBlast Mobile Threat Defense subscription
    -   See [CheckPoint SandBlast website](https://www.checkpoint.com/) for more information.

## Next steps

- [Integrate CheckPoint SandBlast with Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [Set up CheckPoint SandBlast Mobile app](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Create CheckPoint SandBlast Mobile device compliance policy](mtd-device-compliance-policy-create.md)

- [Enable CheckPoint SandBlast Mobile MTD connector](mtd-connector-enable.md)
