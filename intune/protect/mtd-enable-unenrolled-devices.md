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
ms.openlocfilehash: 9571f7d0ae10f33007d5ae50b403580232c2e870
ms.sourcegitcommit: 06dce5c8111592ad774247e86e539dd3128117e5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/30/2019
ms.locfileid: "75545945"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Habilitación del conector Mobile Threat Defense en Intune para dispositivos no inscritos

Durante la configuración de Mobile Threat Defense (MTD), ha configurado una directiva para clasificar amenazas en la consola del asociado de MTD y ha creado la directiva de protección de aplicaciones en Intune. Si ya ha configurado el conector de Intune en la consola del asociado de MTD, ya puede habilitar la conexión de MTD para las aplicaciones de asociados de MTD.

> [!NOTE]
> Este artículo se aplica a todos los asociados de Mobile Threat Defense que admiten directivas de protección de aplicaciones: Better Mobile (Android), Zimperium (Android/iOS), Lookout for Work (Android/iOS).

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Directivas de acceso condicional clásicas para aplicaciones de MTD

Al integrar una nueva aplicación en Intune Mobile Threat Defense y habilitar la conexión con Intune, este servicio crea una directiva de acceso condicional clásica en Azure Active Directory. Todas las aplicaciones de MTD que integre, incluido [ATP de Defender](advanced-threat-protection.md) o cualquiera de nuestros [asociados de MTD](mobile-threat-defense.md#mobile-threat-defense-partners) adicionales, crean una directiva de acceso condicional clásica. Estas directivas se pueden omitir, pero no se deben editar, eliminar ni deshabilitar.

Si se elimina la directiva clásica, deberá eliminar la conexión a Intune que era responsable de su creación y, luego, configurarla de nuevo. Este proceso vuelve a crear la directiva clásica. No se admite la migración de directivas clásicas de aplicaciones de MTD al nuevo tipo de directiva de acceso condicional.

Directivas de acceso condicional clásicas para aplicaciones de MTD:

- Las usa Intune MTD para requerir que los dispositivos estén registrados en Azure AD, de modo que dispongan de un id. de dispositivo antes de comunicarse con los asociados de MTD. El id. es necesario para que los dispositivos puedan informar de su estado correctamente a Intune.

- No tiene ningún efecto en otros recursos o aplicaciones en la nube.

- Son diferentes a las directivas de acceso condicional que puede crear para ayudarle con la administración de MTD.

- De manera predeterminada, no interactúan con otras directivas de acceso condicional que usa para la evaluación.

Para ver las directivas de acceso condicional clásicas, en [Azure](https://portal.azure.com/#home), vaya a **Azure Active Directory** > **Acceso condicional** > **Directivas clásicas**.

## <a name="to-enable-the-mtd-connector"></a>Para habilitar el conector de MTD

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Mobile Threat Defense**.

3. En el panel **Mobile Threat Defense**, seleccione **Agregar**.

4. Seleccione su solución de MTD como el **conector para Mobile Threat Defense a configurar** en la lista desplegable.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Habilite las opciones de alternancia de acuerdo con los requisitos de su organización. Las opciones de alternancia visibles variarán en función del asociado de MTD.

## <a name="mobile-threat-defense-toggle-options"></a>Opciones de alternancia de Mobile Threat Defense

Las opciones de alternancia de MTD que habilite dependerán de los requisitos de su organización. A continuación tiene más detalles:

**Configuración de directivas de protección de aplicaciones**

- **Conecte dispositivos Android de la versión 4.4 y posteriores a *\<nombre del asociado de MTD>* para la evaluación de la directiva de protección de aplicaciones**: Al habilitar esta opción, las directivas de protección de aplicaciones que usan la regla Nivel de amenaza de dispositivo evaluarán los dispositivos, incluidos los datos de este conector.

- **Conecte dispositivos iOS de la versión 11 y posteriores a *\<nombre del asociado de MTD>* para la evaluación de la directiva de protección de aplicaciones**: Al habilitar esta opción, las directivas de protección de aplicaciones que usan la regla Nivel de amenaza de dispositivo evaluarán los dispositivos, incluidos los datos de este conector.

**Configuración compartida común**

- **Number of days until partner is unresponsive** (Número de días hasta que el asociado no responda): número de días de inactividad antes de que Intune considere que el asociado no responde porque se perdió la conexión. Intune omite el estado de cumplimiento de los asociados de MTD que no responden.

> [!TIP]
> Puede ver el **estado de conexión** y la hora de **última sincronización** entre Intune y el asociado de MTD en el panel Mobile Threat Defense.

## <a name="next-steps"></a>Pasos siguientes

- [Cree una directiva de protección de aplicaciones de Mobile Threat Defense (MTD) con Intune](~/protect/mtd-app-protection-policy.md).
