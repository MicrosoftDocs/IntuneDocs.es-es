---
title: "Configuración de Windows Information Protection: Intune"
titleSuffix: Azure portal
description: "Obtenga información sobre la configuración de Intune que puede usar para administrar Windows Information Protection\"."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 1/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e33fa9b22687f7f8c4d301c6cd82ecd787c23246
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Configuración de Windows Information Protection en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Con el aumento en las empresas de dispositivos que pertenecen a los empleados, existe también un riesgo mayor de pérdidas accidentales de datos a través de aplicaciones y servicios como el correo electrónico, los medios sociales y la nube pública, que están fuera del control de la empresa. Por ejemplo, un empleado envía las imágenes de ingeniería más recientes desde una cuenta de correo electrónico personal, copia y pega la información del producto en un tweet o guarda un informe de ventas en curso en un almacenamiento en la nube pública.

**Windows Information Protection** ayuda a proporcionar protección ante esta pérdida potencial de datos sin interferir como contrapartida en la experiencia de empleado. También ayuda a proteger los datos y aplicaciones empresariales ante las pérdidas de datos accidentales en dispositivos propiedad de la empresa y personales que los empleados llevan al trabajo sin necesidad de realizar cambios en su entorno u otras aplicaciones.

Esta directiva de Intune administra la lista de aplicaciones protegidas por Windows Information Protection, las ubicaciones de red de la empresa, el nivel de protección y la configuración de cifrado.

>[!NOTE]
> Para usar la aplicación Portal de empresa de Windows 10 con Windows Information Protection, debe agregar la aplicación Portal de empresa en el modo **Exento** de Windows Information Protection. 

### <a name="next-steps"></a>Pasos siguientes
Para obtener más información, vea:
-  [Protege los datos de tu empresa con Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
- [Crear una directiva de Windows Information Protection (WIP) con Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune)
- [Crear una directiva Windows Information Protection (WIP) con MDM usando el portal de Azure de Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune-azure)
- [Crear una directiva Windows Information Protection (WIP) con MAM usando el portal de Azure de Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure)
