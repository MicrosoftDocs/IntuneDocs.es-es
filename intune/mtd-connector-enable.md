---
title: Habilitar el conector Mobile Threat Defense en Microsoft Intune
titleSuffix: Microsoft Intune
description: Habilite el conector entre un asociado de Mobile Threat Defense (MTD) y Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2084ad1ec0deefd24c0d61f69d99ee11149af96
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882733"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Habilitar el conector Mobile Threat Defense en Intune

> [!NOTE] 
> La información de este tema se aplica a todos los asociados de Mobile Threat Defense.

Durante la configuración de Mobile Threat Defense (MTD), ha configurado una directiva para clasificar amenazas en la consola del asociado de MTD y ha creado la directiva de cumplimiento de dispositivo en Intune. Si ya ha configurado el conector de Intune en la consola del asociado de MTD, ya puede habilitar la conexión de MTD en Intune.

## <a name="to-enable-the-mtd-connector"></a>Para habilitar el conector de MTD

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

4. En el **panel de Intune**, elija **Cumplimiento de dispositivos** y, luego, elija **Mobile Threat Defense** en la sección **Configuración**.

5. En el panel **Mobile Threat Defense**, elija **Agregar**.

6. Seleccione su solución de MTD como el **conector para Mobile Threat Defense a configurar** en la lista desplegable.

    ![Configuración de MTD en Azure Portal de Intune](./media/enable-mtd-connector-1.png)

7. Habilite las opciones de alternancia según los requisitos de su organización. Las opciones de alternancia visibles variarán en función del asociado de MTD.

## <a name="mtd-toggle-options"></a>Opciones de alternancia de MTD

Las opciones de alternancia de MTD que habilite dependerán de los requisitos de su organización. A continuación, puede ver más detalles:

- **Connect Android 4.1+ devices to [MTD partner name] for Work MTD** (Conectar dispositivos Android 4.1+ con MTD de [nombre de partner de MTD] for Work): cuando habilita esta opción, puede hacer que los dispositivos Android 4.1+ informen de un riesgo de seguridad a Intune.
  - **Mark as non compliant if no data is received** (Marcar como no conforme si no se reciben datos): si Intune no recibe datos sobre un dispositivo en esta plataforma por parte del asociado de MTD, considere que el dispositivo no es conforme.
<br></br>
- **Connect iOS 8.0+ devices to [MTD partner name] for Work MTD** (Conectar dispositivos iOS 8.0+ con MTD de [nombre de partner de MTD] for Work): cuando se habilita esta opción, los dispositivos iOS 8.0+ pueden informar a Intune de los riesgos para la seguridad.
  - **Mark as non compliant if no data is received** (Marcar como no conforme si no se reciben datos): si Intune no recibe datos sobre un dispositivo en esta plataforma por parte del asociado de MTD, considere que el dispositivo no es conforme.
<br></br>
- **Enable App Sync for iOS Devices** (Habilitar la sincronización de aplicaciones de dispositivos iOS): permite que este partner de Mobile Threat Defense solicite los metadatos de las aplicaciones iOS a Intune para usarlos con el fin de analizar las amenazas.

- **Block unsupported OS versions** (Bloquear versiones de SO no compatibles): bloquear si el dispositivo ejecuta un sistema operativo inferior a la versión mínima compatible.

- **Number of days until partner is unresponsive** (Número de días hasta que el asociado no responda): número de días de inactividad antes de que Intune considere que el asociado no responde porque se perdió la conexión. Intune omite el estado de cumplimiento de los asociados de MTD que no responden.

> [!IMPORTANT] 
> Siempre que sea posible, se recomienda agregar y asignar las aplicaciones MTD antes de crear las reglas de cumplimiento del dispositivo y de directiva de acceso condicional. Esto ayuda a garantizar que la aplicación MTD esté lista y disponible para que los usuarios finales la instalen antes de poder acceder al correo electrónico u otros recursos de empresa.

> [!TIP]
> Puede ver el **estado de conexión** y la hora de **última sincronización** entre Intune y el asociado de MTD en el panel Mobile Threat Defense.
