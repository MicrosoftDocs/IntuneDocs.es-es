---
title: Validación de la configuración de la directiva de protección de aplicaciones
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo probar si su directiva de protección de aplicaciones está configurada y funciona correctamente.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ea79a2e177b8a4e85454140c7efb9172defe5b6
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31834040"
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Validación de la configuración de la directiva de protección de aplicaciones

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Compruebe que su directiva de protección de aplicaciones esté configurada y funcione correctamente. Esta guía se aplica a las directivas de protección de aplicaciones de Azure Portal.

### <a name="checking-for-symptoms"></a>Examinar los síntomas
Los usuarios no suelen notificar problemas, ya que la protección de aplicaciones es una herramienta de protección de datos. Si hay algún problema con la configuración de la protección de aplicaciones, el usuario tendrá acceso ilimitado, del mismo modo que si no tuviera protección de aplicaciones, y no podrá detectar que hay un problema. Por este motivo, se recomienda que valide la configuración de la protección de aplicaciones efectuando una prueba piloto de las directivas de protección de aplicaciones con un pequeño grupo de usuarios que puedan probar deliberadamente las restricciones de la protección de aplicaciones.


### <a name="what-to-check"></a>Elementos que se deben comprobar

Si las pruebas muestran que el comportamiento de la directiva de protección de aplicaciones no es el previsto, le recomendamos que compruebe lo siguiente:

- ¿Tienen licencia los usuarios para la protección de aplicaciones?
- ¿Los usuarios tienen licencia para O365?
- El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**.

#### <a name="user-app-protection-status"></a>Estado de protección de las aplicaciones de los usuarios
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
1. Elija **Administrar aplicaciones** > **Supervisar** >  **Estado de protección de aplicaciones** > **Usuarios asignados**.

2. Elija a un usuario de la lista o bien busque y seleccione a un usuario y elija **Seleccionar usuario**. En la parte superior de la columna **Informes de aplicaciones**, verá si el usuario tiene licencia para la protección de aplicaciones. También puede consultar si el usuario tiene licencia para Office 365, así como el estado de la aplicación para todos los dispositivos del usuario.



### <a name="what-to-do"></a>Qué hacer
Aquí se muestran las acciones que se deben tomar en función del estado del usuario:

- Si el usuario no tiene licencia para la protección de aplicaciones, asigne una licencia de Intune al usuario.
- Si el usuario no tiene licencia para Office 365, obtenga una.
- Si la aplicación de un usuario aparece como **No protegida**, compruebe si ha configurado correctamente una directiva de protección de aplicaciones para esa aplicación.
- Asegúrese de que estas condiciones se aplican a todos los usuarios a los que quiera aplicar directivas de protección de aplicaciones.

### <a name="see-also"></a>Vea también

[¿Qué es la directiva de protección de aplicaciones de Intune?](app-protection-policies.md)
