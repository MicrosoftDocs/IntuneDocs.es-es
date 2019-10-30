---
title: Habilitación del conector Mobile Threat Defense para dispositivos no inscritos
titleSuffix: Microsoft Intune
description: Habilite el conector Mobile Threat Defense en Microsoft Intune para dispositivos no inscritos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63079757ee3610d825601921da1d33aa94f851b6
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794412"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Habilitación del conector Mobile Threat Defense en Intune para dispositivos no inscritos

Durante la configuración de Mobile Threat Defense (MTD), ha configurado una directiva para clasificar amenazas en la consola del asociado de MTD y ha creado la directiva de protección de aplicaciones en Intune. Si ya ha configurado el conector de Intune en la consola del asociado de MTD, ya puede habilitar la conexión de MTD para las aplicaciones de asociados de MTD.

> [!NOTE] 
> Este artículo se aplica a todos los asociados de Mobile Threat Defense que admiten directivas de protección de aplicaciones: Better Mobile (Android), Zimperium (iOS) y Lookout for Work (Android/iOS).

## <a name="to-enable-the-mtd-connector"></a>Para habilitar el conector de MTD

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. En el **panel de Intune**, elija **Cumplimiento de dispositivos** y, luego, elija **Mobile Threat Defense** en la sección **Configuración**.

3. En el panel **Mobile Threat Defense**, elija **Agregar**.

4. Seleccione su solución de MTD como el **conector para Mobile Threat Defense a configurar** en la lista desplegable.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Habilite las opciones de alternancia según los requisitos de su organización. Las opciones de alternancia visibles variarán en función del asociado de MTD.

## <a name="mtd-toggle-options"></a>Opciones de alternancia de MTD

Las opciones de alternancia de MTD que habilite dependerán de los requisitos de su organización. A continuación, puede ver más detalles:

**Configuración de directivas de protección de aplicaciones**
- **Conecte dispositivos Android de la versión 4.1 y posteriores a *\<Nombre del asociado de MTD >* para la evaluación de la directiva de protección de aplicaciones**: Al habilitar esta opción, las directivas de protección de aplicaciones que usan la regla Nivel de amenaza de dispositivo evaluarán los dispositivos, incluidos los datos de este conector.
- **Conecte dispositivos iOS de la versión 8.0 y posteriores a *\<Nombre del asociado de MTD >* para la evaluación de la directiva de protección de aplicaciones**: Al habilitar esta opción, las directivas de protección de aplicaciones que usan la regla Nivel de amenaza de dispositivo evaluarán los dispositivos, incluidos los datos de este conector.

**Configuración compartida común**
- **Number of days until partner is unresponsive** (Número de días hasta que el asociado no responda): número de días de inactividad antes de que Intune considere que el asociado no responde porque se perdió la conexión. Intune omite el estado de cumplimiento de los asociados de MTD que no responden.

> [!TIP]
> Puede ver el **estado de conexión** y la hora de **última sincronización** entre Intune y el asociado de MTD en el panel Mobile Threat Defense.

> [!NOTE] 
> Al habilitar la conexión de Mobile Threat Defense a Intune, Intune crea una directiva de acceso condicional clásica en Azure Active Directory. Todas las aplicaciones de MTD que integre, incluido [ATP de Defender](advanced-threat-protection.md) o cualquiera de nuestros [asociados de MTD](mobile-threat-defense.md#mobile-threat-defense-partners) adicionales, crean una directiva de acceso condicional clásica. **Estas directivas se pueden omitir, pero no se deben editar, eliminar ni deshabilitar.**
> 
> Directivas de acceso condicional clásicas para aplicaciones de MTD: 
> - Las usa Intune MTD para requerir que los dispositivos estén registrados en Azure AD, de modo que dispongan de un id. de dispositivo antes de comunicarse con los asociados de MTD. El id. es necesario para que los dispositivos puedan informar de su estado correctamente a Intune.  
> - No tiene ningún efecto en otros recursos o aplicaciones en la nube.  
> - Son diferentes a las directivas de acceso condicional que puede crear para ayudarle con la administración de MTD o parar requerir una CA de protección de aplicaciones.
> - De manera predeterminada, no interactúan con otras directivas de acceso condicional que usa para la evaluación.  
>
> Para ver las directivas de acceso condicional clásicas, en [Azure](https://portal.azure.com/#home), vaya a **Azure Active Directory** > **Acceso condicional** > **Directivas clásicas**.

## <a name="next-steps"></a>Pasos siguientes

- [Cree una directiva de protección de aplicaciones de Mobile Threat Defense (MTD) con Intune](~/protect/mtd-app-protection-policy.md).