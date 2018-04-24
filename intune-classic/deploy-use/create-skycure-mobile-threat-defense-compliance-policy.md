---
title: Creación de directiva de cumplimiento de Mobile Threat Defense de Skycure
description: Cree una directiva de cumplimiento de Mobile Threat Defense de Skycure en el portal clásico de Intune.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 56ff1728-1119-4e8a-aae6-ed5c7fafa052
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a2c194e7741c8ce79d87ad68eb408508b2929167
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="create-skycure-mobile-threat-defense-compliance-policy"></a>Creación de directiva de cumplimiento de Mobile Threat Defense de Skycure

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune con Mobile Threat Defense de Skycure le permite detectar amenazas en dispositivos móviles y evaluar riesgos en ellos. Puede crear una regla de directivas de cumplimiento de Intune que evalúe el riesgo para determinar si el dispositivo cumple con la directiva. Luego puede usar la directiva de acceso condicional para bloquear el acceso a servicios en función del cumplimiento del dispositivo.

## <a name="before-you-begin"></a>Antes de comenzar

Requisitos previos para la directiva de cumplimiento con protección para amenazas en dispositivos de Skycure:

-   [Configuración de la integración de Skycure con Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

-   [Habilitación de la conexión de Skycure en Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

Como parte de la configuración de Mobile Threat Defense de Skycure, en la consola de Skycure creó una directiva que clasifica las distintas amenazas como alta, media y baja. En la directiva de cumplimiento de Intune, ahora debe establecer el máximo nivel de amenaza permitido.

## <a name="to-create-skycure-compliance-policy"></a>Para crear la directiva de cumplimiento de Skycure

1.  Vaya al [portal clásico de Intune](https://manage.microsoft.com/) y, a continuación, escriba sus credenciales.

2.  Elija **Directiva** &gt; **Directivas de cumplimiento**. Puede usar una directiva de cumplimiento existente o crear una nueva.

3.  Elija **Agregar** &gt; **Estado de dispositivos** y, luego, habilite **Protección contra amenazas de dispositivo**.

4.  Seleccione el **Máximo nivel de amenaza permitido**:

    a.  **Ninguno (protegido)**: es el más seguro. El dispositivo no puede tener ninguna amenaza presente y aún puede tener acceso a los recursos de la empresa. Si se encuentra alguna amenaza, el dispositivo se clasificará como no conforme.

    b.  **Bajo**: el dispositivo se evalúa como compatible si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.

    c.  **Medio**: el dispositivo se evalúa como compatible si las amenazas que se encuentran en él son de nivel bajo o medio. Si se detectan amenazas de nivel alto, se determinará que el dispositivo no es conforme.

    d.  **Alto**: esta opción es la menos segura. Esto permite todos los niveles de amenaza y usa Mobile Threat Defense de Skycure solo con fines informativos.

> [!IMPORTANT]
> Si crea directivas de acceso condicional para Office 365 u otros servicios, se efectuará esta evaluación de cumplimiento y se bloqueará el acceso de los dispositivos no conformes a dichos servicios hasta que se resuelva la amenaza.

## <a name="span-idmonitor-device-threats-classanchorspan-idnext-steps-classanchorspan-idtoc477360344-classanchorspanspanspannext-steps"></a><span id="monitor-device-threats" class="anchor"><span id="next-steps" class="anchor"><span id="_Toc477360344" class="anchor"></span></span></span>Pasos siguientes

-   Crear una directiva de acceso condicional para:

    -   [Exchange Online](/intune-classic/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
    -   [Exchange local](/intune-classic/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
    -   [SharePoint Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)
    -   [Skype Empresarial Online](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)
    -   [Dynamics CRM](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)
