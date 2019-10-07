---
title: Solución de problemas de actualizaciones de software en Microsoft Intune - Azure | Microsoft Docs
description: Resuelva problemas de actualizaciones de software en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3deb023a7e3683658139c2319945c7c3aaeb8ee
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735615"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Solucionar problemas de actualizaciones de software en Microsoft Intune

Ayude a resolver problemas de actualizaciones de software en Microsoft Intune. Para ver una lista de los códigos de error y sus descripciones, vaya al artículo sobre los [códigos de error del agente de actualización de software en Microsoft Intune](../protect/software-update-agent-error-codes.md).

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>Los dispositivos Windows 7 con muchas actualizaciones reemplazadas dejan de informar a Intune

Los clientes de Microsoft Intune pueden experimentar uno o varios de estos síntomas:

- Los dispositivos dejan de informar a Intune de manera repentina.  
- Los dispositivos experimentan un uso intensivo de la CPU.
- Las aplicaciones se instalan lentamente cuando la instalación se realiza a través de Intune.
- Microsoft Intune Center muestra el error siguiente: `An error occurred while updating your computer. Error found: Code 0x800705b4`.
- En la Consola de administración de Intune > Grupos > Todos los dispositivos > el estado muestra: `One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

Este problema puede producirse si las actualizaciones reemplazadas (las actualizaciones que reemplazó otra actualización) no se han rechazado durante un largo período. Durante ciertos procesos, como la instalación de una aplicación, Windows comprueba todas las actualizaciones reemplazadas de forma secuencial para que las actualizaciones y sus sucesores se asignen correctamente. Si la lista de actualizaciones reemplazadas aumenta demasiado, esta tarea de comprobación puede hacer un uso intensivo de la CPU debido a la carga de procesamiento y el tiempo necesario. Ese problema afecta principalmente a los dispositivos Windows 7 debido al elevado número de actualizaciones reemplazadas que están disponibles para Windows 7. Es posible que los sistemas operativos más recientes no tengan tantas actualizaciones reemplazadas y pueden no ser susceptibles a este problema.

**Solución**

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Actualizaciones de software**.
3. Rechace todas las actualizaciones reemplazadas que se apliquen a Windows 7 o a las aplicaciones, como Microsoft Office, que se instalaron en los clientes afectados.
4. Reinicie los clientes afectados.

Si ejecuta Windows 7, asegúrese de tener instalada esta actualización:[3050265 Windows Update Client para Windows 7: junio de 2015](https://support.microsoft.com/kb/3050265).

## <a name="next-steps"></a>Pasos siguientes

Obtenga [ayuda de soporte técnico de Microsoft](get-support.md) o use los [foros de la comunidad](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).