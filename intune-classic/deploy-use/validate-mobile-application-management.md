---
title: "Validación de la configuración de MAM"
description: "En este tema se describe cómo puede probar y verificar si su directiva de MAM está configurada correctamente y funciona según lo esperado."
keywords: 
author: andredm7
ms.author: andredm
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.custom: intune-classic
ms.openlocfilehash: e0cb44177f830236865dce0ab68bb1084fcebc2d
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="validating-your-mobile-application-management-setup"></a>Validar la configuración de administración de aplicaciones móviles

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

En este tema se proporciona información sobre cómo comprobar si hay problemas después de configurar la administración de aplicaciones móviles (MAM). Esta guía se aplica a las directivas de MAM del portal de Azure.

### <a name="checking-for-symptoms"></a>Examinar los síntomas
Los usuarios no suelen notificar problemas, ya que MAM es una herramienta de protección de datos. Si hay algún problema con la configuración de MAM, el usuario tendrá acceso ilimitado, del mismo modo que si no tuviera MAM, y no sería consciente de que hay un problema. Por este motivo, se recomienda que valide la configuración de MAM efectuando una prueba piloto de las directivas de MAM con un pequeño grupo de usuarios que puedan probar deliberadamente las restricciones de MAM.


### <a name="what-to-check"></a>Elementos que se deben comprobar

Si las pruebas muestran que el comportamiento de la directiva de MAM no es el previsto, le recomendamos que compruebe lo siguiente:

- ¿Los usuarios tienen licencia para MAM?
- ¿Los usuarios tienen licencia para O365?
- El estado de cada una de las aplicaciones de MAM de los usuarios. Los estados posibles de las aplicaciones son **Protegido** y **No protegido**.

#### <a name="user-mam-status"></a>Estado de MAM del usuario
1. En el portal de Azure, elija **Administración de aplicaciones móviles de Intune** > **Configuración** > **Administración de aplicaciones** > **Toda la configuración** > **Informes de aplicaciones por usuario** > **Usuarios**.

2. Elija un usuario de la lista o bien busque y seleccione un usuario y elija **Seleccionar usuario**. En la parte superior de la columna **Informes de aplicaciones** verá si el usuario tiene licencia para MAM. Justo debajo verá si el usuario tiene licencia para Office 365, así como el estado de la aplicación para todos los dispositivos del usuario.

![Estado de aplicación para MAM](..\media\ts-mam-user-apps.png)

### <a name="what-to-do"></a>Qué hacer
Aquí se muestran las acciones que se deben tomar en función del estado del usuario:

- Si el usuario no tiene licencia para MAM, asígnele una licencia de Intune, como se describe en [Administración de licencias de Intune](/intune/setup-steps).
- Si el usuario no tiene licencia para Office 365, obtenga una.
- Si la aplicación de un usuario aparece como **No protegido**, compruebe si ha configurado correctamente una directiva de MAM para esa aplicación.
- Asegúrese de que estas condiciones se aplican a todos los usuarios a los que quiera aplicar directivas de MAM.

### <a name="see-also"></a>Consulte también
[Preparación para configurar directivas de administración de aplicaciones móviles con Microsoft Intune](..\deploy-use\get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Proteger datos mediante las directivas de administración de aplicaciones móviles con Microsoft Intune](..\deploy-use\protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
