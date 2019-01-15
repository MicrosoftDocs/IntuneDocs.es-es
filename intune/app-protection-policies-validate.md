---
title: Validación de la configuración de la directiva de protección de aplicaciones
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo probar si su directiva de protección de aplicaciones está configurada y funciona correctamente.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/13/2018
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 60cf35814f64f2f237c3f2ec3ea8f4d56460dd71
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297220"
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Validación de la configuración de la directiva de protección de aplicaciones

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Compruebe que su directiva de protección de aplicaciones esté configurada y funcione correctamente. Esta guía se aplica a las directivas de protección de aplicaciones de Azure Portal.

## <a name="checking-for-symptoms"></a>Examinar los síntomas
Los usuarios no suelen notificar problemas, ya que la protección de aplicaciones es una herramienta de protección de datos. Si hay algún problema con la configuración de la protección de aplicaciones, el usuario tendrá acceso ilimitado, del mismo modo que si no tuviera protección de aplicaciones, y no podrá detectar que hay un problema. Por este motivo, se recomienda que valide la configuración de la protección de aplicaciones efectuando una prueba piloto de las directivas de protección de aplicaciones con un pequeño grupo de usuarios que puedan probar deliberadamente las restricciones de la protección de aplicaciones.


## <a name="what-to-check"></a>Elementos que se deben comprobar

Si las pruebas muestran que el comportamiento de la directiva de protección de aplicaciones no es el previsto, compruebe lo siguiente:

- ¿Tienen licencia los usuarios para la protección de aplicaciones?
- ¿Los usuarios tienen licencia para O365?
- El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**.

### <a name="user-app-protection-status"></a>Estado de protección de las aplicaciones de los usuarios
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Seleccione **Aplicaciones cliente** > **Supervisar** >  **Estado de protección de la aplicación** y luego seleccione el icono **Usuarios asignados**. 
4. En la página **Informes de aplicaciones**, seleccione **Seleccionar usuario** para abrir una lista de usuarios y grupos. 
5. Busque y seleccione un usuario de la lista y luego elija **Seleccionar usuario**. En la parte superior del panel **Informes de aplicaciones**, verá si el usuario tiene licencia para la protección de aplicaciones. También puede consultar si el usuario tiene licencia para Office 365, así como el estado de la aplicación para todos los dispositivos del usuario.



## <a name="what-to-do"></a>Qué hacer
Aquí se muestran las acciones que se deben tomar en función del estado del usuario:

- Si el usuario no tiene licencia para la protección de aplicaciones, asigne una licencia de Intune al usuario.
- Si el usuario no tiene licencia para Office 365, obtenga una.
- Si la aplicación de un usuario aparece como **No protegida**, compruebe si ha configurado correctamente una directiva de protección de aplicaciones para esa aplicación.
- Asegúrese de que estas condiciones se aplican a todos los usuarios a los que quiera aplicar directivas de protección de aplicaciones.

## <a name="see-also"></a>Consulte también

[¿Qué es la directiva de protección de aplicaciones de Intune?](app-protection-policies.md)
