---
title: "Validar las directivas de protección de aplicaciones"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: en este tema se describe cómo puede probar y validar si su directiva de protección de aplicaciones está configurada correctamente y funciona según lo esperado."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 086ea61de3423be254d3d8f2224c4ad96d90385d
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-validate-your-app-protection-policy-setup"></a>Validación de la configuración de la directiva de protección de aplicaciones

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


En este tema se proporciona información sobre la búsqueda de problemas después de configurar una directiva de protección de aplicaciones. Esta guía se aplica a las directivas de protección de aplicaciones de la **versión preliminar** del portal de Azure.

### <a name="checking-for-symptoms"></a>Examinar los síntomas
Los usuarios no suelen notificar problemas, ya que la protección de aplicaciones es una herramienta de protección de datos. Si hay algún problema con la configuración de la protección de aplicaciones, el usuario tendrá acceso ilimitado, del mismo modo que si no tuviera protección de aplicaciones, y no sería consciente de que hay un problema. Por este motivo, se recomienda que valide la configuración de la protección de aplicaciones efectuando una prueba piloto de las directivas de protección de aplicaciones con un pequeño grupo de usuarios que puedan probar deliberadamente las restricciones de la protección de aplicaciones.


### <a name="what-to-check"></a>Elementos que se deben comprobar

Si las pruebas muestran que el comportamiento de la directiva de protección de aplicaciones no es el previsto, le recomendamos que compruebe lo siguiente:

- ¿Tienen licencia los usuarios para la protección de aplicaciones?
- ¿Los usuarios tienen licencia para O365?
- El estado de protección de cada una de las aplicaciones de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**.

#### <a name="user-app-protection-status"></a>Estado de protección de las aplicaciones de los usuarios
1. En el portal de Azure, elija **Administrar aplicaciones** > **Monitor** >   (Supervisar) **App protection user status** >  (Estado de usuario de protección de aplicaciones) **usuarios**.

2. Elija un usuario de la lista o bien busque y seleccione un usuario y elija **Seleccionar usuario**. En la parte superior de la columna **Informes de aplicaciones**, verá si el usuario tiene licencia para la protección de aplicaciones. Justo debajo verá si el usuario tiene licencia para Office&365;, así como el estado de la aplicación para todos los dispositivos del usuario.



### <a name="what-to-do"></a>Qué hacer
Aquí se muestran las acciones que se deben tomar en función del estado del usuario:

- Si el usuario no tiene licencia para la protección de aplicaciones, asigne una licencia de Intune al usuario.
- Si el usuario no tiene licencia para Office&365;, obtenga una.
- Si la aplicación de un usuario aparece como **No protegido**, compruebe si ha configurado correctamente una directiva de protección de aplicaciones para esa aplicación.
- Asegúrese de que estas condiciones se aplican a todos los usuarios a los que quiera aplicar directivas de protección de aplicaciones.

### <a name="see-also"></a>Consulte también

[¿Qué es la directiva de protección de aplicaciones de Intune?](app-protection-policies.md)

