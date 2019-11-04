---
title: Habilitar el conector Mobile Threat Defense en Microsoft Intune
titleSuffix: Microsoft Intune
description: Habilite el conector entre un asociado de Mobile Threat Defense (MTD) y Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4f917167baecc643e045610e86e582957e535978
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810292"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Habilitar el conector Mobile Threat Defense en Intune

> [!NOTE] 
> La información de este tema se aplica a todos los asociados de Mobile Threat Defense.

Durante la configuración de Mobile Threat Defense (MTD), ha configurado una directiva para clasificar amenazas en la consola del asociado de MTD y ha creado la directiva de cumplimiento de dispositivo en Intune. Si ya ha configurado el conector de Intune en la consola del asociado de MTD, ya puede habilitar la conexión de MTD para las aplicaciones de asociados de MTD.

Al integrar una nueva aplicación en Intune Mobile Threat Defense y habilitar la conexión con Intune, este servicio crea una directiva de acceso condicional clásica en Azure Active Directory. Todas las aplicaciones de MTD que integre, incluido [ATP de Defender](advanced-threat-protection.md) o cualquiera de nuestros [asociados de MTD](mobile-threat-defense.md#mobile-threat-defense-partners) adicionales, crean una directiva de acceso condicional clásica. Estas directivas se pueden omitir, pero no se deben editar, eliminar ni deshabilitar.

Directivas de acceso condicional clásicas para aplicaciones de MTD: 

- Las usa Intune MTD para requerir que los dispositivos estén registrados en Azure AD, de modo que dispongan de un id. de dispositivo antes de comunicarse con los asociados de MTD. El id. es necesario para que los dispositivos puedan informar de su estado correctamente a Intune.  
- No tiene ningún efecto en otros recursos o aplicaciones en la nube.  
- Son diferentes a las directivas de acceso condicional que puede crear para ayudarle con la administración de MTD.
- De manera predeterminada, no interactúan con otras directivas de acceso condicional que usa para la evaluación.  

Para ver las directivas de acceso condicional clásicas, en [Azure](https://portal.azure.com/#home), vaya a **Azure Active Directory** > **Acceso condicional** > **Directivas clásicas**.


## <a name="to-enable-the-mobile-threat-defense-connector"></a>Para habilitar el conector Mobile Threat Defense

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

4. En el **panel de Intune**, elija **Cumplimiento de dispositivos** y, luego, elija **Mobile Threat Defense** en la sección **Configuración**.

5. En el panel **Mobile Threat Defense**, elija **Agregar**.

6. Seleccione su solución de MTD como el **conector para Mobile Threat Defense a configurar** en la lista desplegable.

    ![Configuración de MTD en Azure Portal de Intune](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. Habilite las opciones de alternancia según los requisitos de su organización. Las opciones de alternancia visibles variarán en función del asociado de MTD.

## <a name="mobile-threat-defense-toggle-options"></a>Opciones de alternancia de Mobile Threat Defense

Puede decidir qué opciones de alternancia de Mobile Threat Defense necesita habilitar según los requisitos de su organización. A continuación, puede ver más detalles:

**Configuración de directivas de cumplimiento de MDM**
- **Connect Android 4.1+ devices to *\<MTD partner name>***: (Conectar dispositivos Android 4.1+ con *[nombre de asociado de MTD]***:) cuando habilita esta opción, puede hacer que los dispositivos Android 4.1+ informen de un riesgo de seguridad a Intune.
- **Connect iOS 8.0+ devices to *\<MTD partner name>***: (Conectar dispositivos iOS 8.0+ con *[nombre de asociado de MTD]***:) cuando se habilita esta opción, los dispositivos iOS 8.0+ pueden informar a Intune de los riesgos para la seguridad.
- **Enable App Sync for iOS Devices** (Habilitar la sincronización de aplicaciones de dispositivos iOS): permite que este partner de Mobile Threat Defense solicite los metadatos de las aplicaciones iOS a Intune para usarlos con el fin de analizar las amenazas.
- **Block unsupported OS versions** (Bloquear versiones de SO no compatibles): bloquear si el dispositivo ejecuta un sistema operativo inferior a la versión mínima compatible.

**Configuración de directivas de protección de aplicaciones**
- **Conecte dispositivos Android de la versión 4.1 y posteriores a *\<Nombre del asociado de MTD >* para la evaluación de la directiva de protección de aplicaciones**: Al habilitar esta opción, las directivas de protección de aplicaciones que usan la regla Nivel de amenaza de dispositivo evaluarán los dispositivos, incluidos los datos de este conector.
- **Conecte dispositivos iOS de la versión 8.0 y posteriores a *\<Nombre del asociado de MTD >* para la evaluación de la directiva de protección de aplicaciones**: Al habilitar esta opción, las directivas de protección de aplicaciones que usan la regla Nivel de amenaza de dispositivo evaluarán los dispositivos, incluidos los datos de este conector.

Para obtener más información sobre el uso de los conectores Mobile Threat Defense para la evaluación de directivas de Intune App Protection, consulte [Configuración de Mobile Threat Defense para dispositivos no inscritos](~/protect/mtd-enable-unenrolled-devices.md).

**Configuración compartida común**
- **Number of days until partner is unresponsive** (Número de días hasta que el asociado no responda): número de días de inactividad antes de que Intune considere que el asociado no responde porque se perdió la conexión. Intune omite el estado de cumplimiento de los asociados de MTD que no responden.

> [!IMPORTANT] 
> Siempre que sea posible, se recomienda agregar y asignar las aplicaciones MTD antes de crear las reglas de cumplimiento del dispositivo y de directiva de acceso condicional. Esto ayuda a garantizar que la aplicación MTD esté lista y disponible para que los usuarios finales la instalen antes de poder acceder al correo electrónico u otros recursos de empresa.

> [!TIP]
> Puede ver el **estado de conexión** y la hora de **última sincronización** entre Intune y el asociado de MTD en el panel Mobile Threat Defense.
