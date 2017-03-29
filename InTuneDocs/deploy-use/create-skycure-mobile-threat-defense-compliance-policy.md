---
title: "Creación de directiva de cumplimiento de Mobile Threat Defense de Skycure en Intune | Microsoft Docs"
description: "Cree una directiva de cumplimiento de Mobile Threat Defense de Skycure en la consola clásica de Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 56ff1728-1119-4e8a-aae6-ed5c7fafa052
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: 3a7322bd389b6d2ca72108b9f54318000857895b
ms.lasthandoff: 03/22/2017


---

# <a name="create-skycure-mobile-threat-defense-compliance-policy"></a>Creación de directiva de cumplimiento de Mobile Threat Defense de Skycure

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune con Mobile Threat Defense de Skycure le permite detectar amenazas en dispositivos móviles y evaluar riesgos en ellos. Puede crear una regla de directivas de cumplimiento de Intune que evalúe el riesgo para determinar si el dispositivo cumple con la directiva. Luego puede usar la directiva de acceso condicional para bloquear el acceso a servicios en función del cumplimiento del dispositivo.

## <a name="before-you-begin"></a>Antes de comenzar

Requisitos previos para la directiva de cumplimiento con protección para amenazas en dispositivos de Skycure:

-   [Configuración de la integración de Skycure con Intune](https://docs.microsoft.com/en-us/intune/deploy-use/setup-the-skycure-integration-with-Intune)

-   [Habilitación de la conexión de Skycure en Intune](https://docs.microsoft.com/intune/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

Como parte de la configuración de Mobile Threat Defense de Skycure, en la consola de Skycure creó una directiva que clasifica las distintas amenazas como alta, media y baja. En la directiva de cumplimiento de Intune, ahora debe establecer el máximo nivel de amenaza permitido.

## <a name="to-create-skycure-compliance-policy"></a>Para crear la directiva de cumplimiento de Skycure

1.  Vaya a la [consola clásica de Intune](https://manage.microsoft.com/) y, a continuación, escriba sus credenciales.

2.  Elija **Directiva** &gt; **Directivas de cumplimiento**. Puede usar una directiva de cumplimiento existente o crear una nueva.

3.  Elija **Agregar** &gt; **Estado de dispositivos** y, luego, habilite **Protección contra amenazas de dispositivo**.

4.  Seleccione el **Máximo nivel de amenaza permitido**:

    a.  **Ninguno (protegido)**: es el más seguro. El dispositivo no puede tener ninguna amenaza presente y aún puede tener acceso a los recursos de la empresa. Si se encuentra alguna amenaza, el dispositivo se evalúa como no compatible.

    b.  **Bajo**: el dispositivo se evalúa como compatible si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.

    c.  **Medio**: el dispositivo se evalúa como compatible si las amenazas que se encuentran en él son de nivel bajo o medio. Si se detectan amenazas de nivel alto, se determina que el dispositivo no es conforme.

    d.  **Alto**: esta opción es la menos segura. Esto permite todos los niveles de amenaza y usa Mobile Threat Defense de Skycure solo con fines informativos.

> [!IMPORTANT] 
> Si crea directivas de acceso condicional para Office 365 u otros servicios, esta evaluación de cumplimiento se toma en consideración y se bloquea el acceso de los dispositivos no compatibles a esos servicios hasta que se resuelva la amenaza.

## <a name="span-idmonitor-device-threats-classanchorspan-idnext-steps-classanchorspan-idtoc477360344-classanchorspanspanspannext-steps"></a><span id="monitor-device-threats" class="anchor"><span id="next-steps" class="anchor"><span id="_Toc477360344" class="anchor"></span></span></span>Pasos siguientes

-   Crear una directiva de acceso condicional para:

    -   [Exchange Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
    -   [Exchange local](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
    -   [SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)
    -   [Skype Empresarial Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)
    -   [Dynamics CRM](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

