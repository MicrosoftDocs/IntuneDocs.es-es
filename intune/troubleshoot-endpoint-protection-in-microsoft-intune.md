---
title: 'Mensajes comunes de Endpoint Protection en Microsoft Intune: Azure | Microsoft Docs'
description: Vea los mensajes comunes y las soluciones posibles al usar y solucionar problemas de Endpoint Protection y Windows Defender en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c76466acb375fe49afefc542606350733970f416
ms.sourcegitcommit: 18be0ccc6e51073af32c44abeba421d69a5ae21a
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302350"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Problemas de Endpoint Protection y posibles soluciones en Microsoft Intune

En este artículo se enumeran y describen las posibles causas y soluciones de algunos errores y advertencias. Use la información para resolver problemas cuando usa Endpoint Protection.

## <a name="windows-defender-error-codes"></a>Códigos de error de Windows Defender

Revise los registros de eventos y los códigos de error para [solucionar problemas con el antivirus de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

## <a name="common-intune-errors-and-possible-resolutions"></a>Errores comunes de Intune y posibles resoluciones

### <a name="endpoint-protection-engine-unavailable"></a>Motor de Endpoint Protection no disponible

**Causa posible**: el motor de Intune Endpoint Protection se dañó o eliminó.

**Soluciones posibles**:

- Si Endpoint Protection está dañado o no se actualiza, actualice o vuelva a instalar el programa.
- Fuerce una actualización inmediata. En el programa cliente de Endpoint Protection (posiblemente en la barra de tareas), elija **Actualizar**.
- En Panel de control > Programas, seleccione **Agente de Microsoft Intune Endpoint Protection**. Desinstale la aplicación.
- Durante la próxima sincronización de actualización, el Administrador de actualizaciones de Microsoft Online Management detectará el programa que falta y lo reinstalará a la hora de instalación programada.

### <a name="features-are-disabled"></a>Las características están deshabilitadas

Puede que vea un mensaje que indique que algunas características están deshabilitadas. Estos mensajes pueden ocurrir si un administrador deshabilitó Intune Endpoint Protection o Windows Defender con un perfil de configuración. O bien, si un usuario final los deshabilitó en el dispositivo. Mensajes posibles:

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**Soluciones posibles**: habilite estas características. Para obtener instrucciones, consulte:

- [Agregar la configuración de Endpoint Protection](endpoint-protection-configure.md)
- [Antivirus de Windows Defender](device-restrictions-windows-10.md#microsoft-defender-antivirus)
- [End users: Turn on real-time protection to access company resources](/intune-user-help/turn-on-defender-windows) (Usuarios finales: activación de la protección en tiempo real para acceder a los recursos de la empresa)

### <a name="malware-definitions-out-of-date"></a>Definiciones de malware desactualizadas

Este estado aparece cuando las definiciones de malware del dispositivo no se han actualizado como mínimo desde hace 14 días. Por ejemplo, el mensaje puede mostrar si el dispositivo está desconectado de Internet o si las definiciones de malware no están actualizadas.

**Soluciones posibles**: si las definiciones de malware no están actualizadas, use el [antivirus de Windows Defender](device-restrictions-windows-10.md#microsoft-defender-antivirus) para actualizarlas.

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>Examen completo vencido o examen rápido vencido

No se ha realizado un examen completo ni un examen rápido en los últimos 14 días. Este escenario puede ocurrir si el dispositivo se reinicia durante un examen completo.

**Soluciones posibles**: si hay un examen vencido, puede ejecutar un examen único o programar exámenes recurrentes. Vea [Antivirus de Windows Defender](device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="another-endpoint-protection-application-running"></a>Otra aplicación de protección de extremos en ejecución

Se está ejecutando otra aplicación de Endpoint Protection y el dispositivo está en buenas condiciones.

**Soluciones posibles**: si se instala otra aplicación de Endpoint Protection e Intune detecta esa aplicación, es posible que el dispositivo se vuelva inestable.

## <a name="next-steps"></a>Pasos siguientes

Obtenga [ayuda de soporte técnico de Microsoft](get-support.md) o use los [foros de la comunidad](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
