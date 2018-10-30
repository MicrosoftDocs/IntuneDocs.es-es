---
title: Solucionar problemas de Endpoint Protection en Intune - Azure | Microsoft Docs
description: Resolver problemas al usar Microsoft Intune Endpoint Protection.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1d8794345f22b2c19cf89eca2d3603fe8ac68161
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2018
ms.locfileid: "49643066"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Solucionar problemas de Endpoint Protection en Intune

Utilice la información para resolver problemas cuando utiliza Endpoint Protection. También puede [revisar los registros de eventos y códigos de error para solucionar problemas con el antivirus de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

Si esta información no le es de ayuda, también puede [obtener soporte técnico de Microsoft Intune](get-support.md).

### <a name="error-messages"></a>Mensajes de error
En esta sección se describen las posibles causas y soluciones de los siguientes errores y advertencias.

|Elemento de estado|Posibles causas|Posibles soluciones|
|---------------|--------------------|-----------------------|
|**Motor de Endpoint Protection no disponible**|El motor de Intune Endpoint Protection se ha dañado o eliminado.|Si el motor de Intune Endpoint Protection se ha dañado, puede intentar actualizar o reinstalar el software.<br /><br />Para forzar una actualización inmediata, seleccione **Actualizar** en el software cliente de Endpoint Protection (se encuentra en la barra de tareas de los equipos administrados).<br /><br />Si no se puede actualizar, deberá reinstalar el motor de Endpoint Protection.<br /><br />En la lista de programas instalados, en el Panel de control del equipo administrado, localice **Agente de Microsoft Intune Endpoint Protection** y desinstale la aplicación.<br /><br />Durante la próxima sincronización de actualización, el Administrador de actualizaciones de Microsoft Online Management detectará el programa que falta y lo reinstalará a la hora de instalación programada.|
|**Endpoint Protection deshabilitado**|Intune Endpoint Protection lo deshabilitó un administrador mediante un perfil de configuración o un usuario en un equipo administrado.|Habilitar Endpoint Protection. Vea [Agregar la configuración de Endpoint Protection en Intune](endpoint-protection-configure.md) o [Activar Windows Defender para tener acceso a los recursos de la empresa](/intune-user-help/turn-on-defender-windows).|
|**Protección en tiempo real deshabilitada**|Protección en tiempo real deshabilitada por un administrador mediante un perfil o por un usuario en un equipo administrado.|Habilitar Endpoint Protection. Vea [Antivirus de Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) en Intune o [Activar Windows Defender para tener acceso a los recursos de la empresa](/intune-user-help/turn-on-defender-windows). |
|**Examen de descargas deshabilitado**|El examen de descargas lo deshabilitó un administrador mediante el uso de un perfil o un usuario en un equipo administrado.|Habilite el análisis. Vea [Antivirus de Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) en Intune o [Activar Windows Defender para tener acceso a los recursos de la empresa](/intune-user-help/turn-on-defender-windows). |
|**Supervisión de actividad de archivos y programas deshabilitada**|La supervisión de la actividad de archivos y programas la deshabilitó un administrador mediante el uso de un perfil o un usuario en un equipo administrado.|Habilite la actividad de archivos y programas. Vea [Antivirus de Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) en Intune o [Activar Windows Defender para tener acceso a los recursos de la empresa](/intune-user-help/turn-on-defender-windows). |
|**Supervisión de comportamiento deshabilitada**|Supervisión del comportamiento deshabilitada por un administrador mediante un perfil o por un usuario en un equipo administrado.|Habilite la supervisión del comportamiento. Vea [Antivirus de Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) en Intune o [Activar Windows Defender para tener acceso a los recursos de la empresa](/intune-user-help/turn-on-defender-windows). |
|**Análisis de scripts deshabilitado**|Análisis de scripts deshabilitado por un administrador mediante un perfil o por un usuario en un equipo administrado.|Habilite el análisis de scripts. Vea [Antivirus de Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) en Intune o [Activar Windows Defender para tener acceso a los recursos de la empresa](/intune-user-help/turn-on-defender-windows). |
|**Sistema de inspección de red deshabilitado**|El Sistema de inspección de red lo deshabilitó un administrador mediante el uso de un perfil o un usuario en un equipo administrado.|Habilite el Sistema de inspección de red (NIS). Vea [Antivirus de Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) en Intune o [Activar Windows Defender para tener acceso a los recursos de la empresa](/intune-user-help/turn-on-defender-windows). |
|**Definiciones de malware desactualizadas**|Puede que el equipo haya permanecido desconectado de Internet durante un período prolongado de tiempo y que sus definiciones de malware no hayan sido actualizadas aún. Este estado aparece cuando las definiciones de malware del equipo no se han actualizado como mínimo desde hace 14 días.|Si las definiciones de malware no están actualizadas, puede actualizarlas mediante el [antivirus de Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**Examen completo vencido**|No se ha completado un examen completo en los últimos 14 días. Esto puede deberse a un reinicio del equipo durante un examen completo.|Si ha vencido un examen completo, puede ejecutar un examen completo único o programar exámenes completos periódicos. Vea [Antivirus de Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus). |
|**Examen rápido vencido**|No se ha completado un examen rápido en los últimos 14 días. Esto puede deberse a un reinicio durante un examen rápido.|Si ha vencido un examen rápido, puede ejecutar un examen rápido único o programar exámenes rápidos periódicos. Vea [Antivirus de Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**Otra aplicación de protección de extremos en ejecución**|Se está ejecutando otra aplicación de protección de extremos y el equipo está en buenas condiciones.|De forma predeterminada, si se instala otra aplicación de Endpoint Protection y Intune detecta dicha aplicación, el dispositivo puede volverse inestable.|

### <a name="next-steps"></a>Pasos siguientes
Si esta información no le es de ayuda, también puede [obtener soporte técnico de Microsoft Intune](get-support.md).
