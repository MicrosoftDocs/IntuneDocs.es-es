---
title: Habilitar el conector Mobile Threat Defense en Microsoft Intune
titleSuffix: ''
description: Habilite el conector entre un asociado de Mobile Threat Defense (MTD) y Microsoft Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6fccfcbceecc9aa0667aa9fd6656c2fcc524d363
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34569364"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Habilitar el conector Mobile Threat Defense en Intune

> [!NOTE] 
> La información de este tema se aplica a todos los asociados de Mobile Threat Defense.

Durante la configuración de Mobile Threat Defense (MTD), ha configurado una directiva para clasificar amenazas en la consola del asociado de MTD y ha creado la directiva de cumplimiento de dispositivo en Intune. Si ya ha configurado el conector de Intune en la consola del asociado de MTD, ya puede habilitar la conexión de MTD en Intune.

## <a name="to-enable-the-mtd-connector"></a>Para habilitar el conector de MTD

1. Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de Intune. Después de iniciar sesión correctamente, verá el **Panel de Azure**.

2. En el **panel de Azure**, elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Intune** y se abrirá el **panel de Intune**.

4. En el **panel de Intune**, elija **Cumplimiento de dispositivos** y, luego, elija **Mobile Threat Defense** en la sección **Configuración**.

5. En el panel **Mobile Threat Defense**, elija **Agregar**.

6. Seleccione su solución de MTD como el **conector para Mobile Threat Defense a configurar** en la lista desplegable.

    ![Configuración de MTD en Azure Portal de Intune](./media/enable-mtd-connector-1.png)

7. Habilite las opciones de alternancia según los requisitos de su organización.

## <a name="mtd-toggle-options"></a>Opciones de alternancia de MTD

Puede decidir qué opciones de alternancia de MTD necesita habilitar según los requisitos de su organización. A continuación, puede ver más detalles:

- **Connect Android 4.1+ devices to [MTD partner name] for Work MTD** (Conectar dispositivos Android 4.1+ con MTD de [nombre del partner de MTD] for Work): cuando habilita esta opción, puede hacer que los dispositivos Android 4.1+ informen un riesgo de seguridad a Intune.
    - **Mark as non compliant if no data is received** (Marcar como no conforme si no se reciben datos): si Intune no recibe datos sobre un dispositivo en esta plataforma por parte del asociado de MTD, considere que el dispositivo no es conforme.
<br></br>
- **Connect iOS 8.0+ devices to [MTD partner name] for Work MTD** (Conectar dispositivos iOS 8.0+ con MTD de [nombre del partner de MTD] for Work): cuando habilita esta opción, puede hacer que los dispositivos iOS 8.0+ informen de un riesgo de seguridad a Intune.
    - **Mark as non compliant if no data is received** (Marcar como no conforme si no se reciben datos): si Intune no recibe datos sobre un dispositivo en esta plataforma por parte del asociado de MTD, considere que el dispositivo no es conforme.
<br></br>
- **Enable App Sync for iOS Devices** (Habilitar la sincronización de aplicaciones de dispositivos iOS): permite que este asociado de Mobile Threat Defense solicite los metadatos de las aplicaciones iOS a Intune para usarlos con el fin de analizar las amenazas.

- **Block unsupported OS versions** (Bloquear versiones de SO no compatibles): bloquee si el dispositivo ejecuta un sistema operativo inferior a la versión mínima compatible.

- **Number of days until partner is unresponsive** (Número de días hasta que el asociado no responda): número de días de inactividad antes de que Intune considere que el asociado no responde porque se perdió la conexión. Intune omite el estado de cumplimiento de los asociados de MTD que no responden.

> [!IMPORTANT] 
> Debe agregar y asignar las aplicaciones de MTD antes de crear el cumplimiento de dispositivo y las reglas de directiva de acceso condicional. Esto garantiza que la aplicación de MTD esté lista y disponible para que los usuarios finales la instalen antes de poder acceder al correo electrónico u otros recursos de empresa.

> [!TIP]
> Puede ver el **estado de conexión** y la hora de **última sincronización** entre Intune y el asociado de MTD en el panel Mobile Threat Defense.
