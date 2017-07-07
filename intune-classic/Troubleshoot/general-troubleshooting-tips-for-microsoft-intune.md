---
title: "Sugerencias para solución de problemas generales"
description: Recursos generales para resolver problemas con Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d348cc2850864206552bf53ab1beec9b9cb55bab
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="general-troubleshooting-tips-for-microsoft-intune"></a>General troubleshooting tips for Microsoft Intune (Sugerencias de solución de problemas generales para Microsoft Intune)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Después de implementar Microsoft Intune puede encontrar problemas con la configuración o con los dispositivos cliente. Use los recursos siguientes para detectar la causa del problema y poder solucionarlo.

> [!NOTE]
> Para crear una solicitud de soporte técnico o para ver una solicitud existente, [visite el Centro de administración de Office 365](https://portal.office.com/admin/default.aspx). Para obtener más información sobre las opciones de soporte técnico, vea [Cómo obtener asistencia para Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="define-the-problem"></a>Definir el problema

-   ¿Cuál es el comportamiento?

-   ¿Quién experimenta el problema, y en qué plataformas y dispositivos?

-   ¿El dispositivo funcionaba bien anteriormente?

-   ¿Qué cambios realizó en la configuración de Intune o del dispositivo?

-   ¿Se hicieron otros cambios en el entorno en el que opera, aparte de los cambios de configuración?

-   ¿Con qué frecuencia se produce este problema? ¿Es esporádico o constante?

-   ¿Puede ser que el usuario esté experimentando un problema de autenticación? Si es posible, vea si el usuario puede iniciar sesión en otros servicios que usen Azure Active Directory. Además, vea si el usuario puede iniciar sesión desde otro dispositivo.

-   ¿Ha comprobado el estado del servicio? Puede supervisar el mantenimiento del servicio Intune en el [portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx). Elija **Mantenimiento del servicio** en el panel izquierdo.

## <a name="collect-available-data"></a>Recopilar datos disponibles

-   Los recursos siguientes pueden ayudarle a obtener información sobre cómo recopilar registros de dispositivo:
  - [Enviar registros de datos de diagnóstico al administrador de TI mediante un cable USB](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Enviar registros de datos de diagnóstico al administrador de TI mediante correo electrónico](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Enviar errores de inscripción de Android al administrador de TI](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)
  - [Enviar errores de inscripción de iOS al administrador de TI](/intune-user-help/send-errors-to-your-it-admin-ios)

-   Con los datos de la consola de administración (por ejemplo, en caso de problemas de implementación de directivas), examine la directiva que quiera y su estado, tal como se describe en [Usar grupos para administrar usuarios y dispositivos en Microsoft Intune](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## <a name="research-the-solution"></a>Investigar la solución

-   Buscar una solución en la Web. Por ejemplo, si recibe el error 0x80073CF0, busque **technet intune 0x80073cf0** en la Web y encontrará el artículo [Solucionar problemas de implementación de aplicaciones en Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md). En este artículo se ofrecen sugerencias para resolver este error.

-   Busque respuestas en el [foto de TechNet de Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  Si el problema no se abordó anteriormente, publique la pregunta para ver qué sugerencias ofrece la comunidad.

-   Abra una solicitud de soporte técnico. El soporte técnico de Intune estará más preparado para ayudarle a resolver un problema una vez que lo tenga definido y que haya recopilado los datos disponibles.

    Para crear una solicitud de soporte técnico, [visite el Centro de administración de Office 365](https://portal.office.com/admin/default.aspx). Para obtener más información sobre las opciones de soporte técnico, vea [Cómo obtener asistencia para Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="find-community-resources"></a>Encontrar recursos de la comunidad
Puede encontrar información útil en estos recursos de la comunidad:

-   La [Microsoft Intune Survival Guide (Guía de supervivencia de Microsoft Intune)](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) contiene vínculos a muchos recursos que pueden ayudarle a configurar, mantener y solucionar problemas de Intune.

-   [Blog de Intune](http://blogs.technet.com/b/windowsintune/)

-   [Seguir a Intune en Twitter](https://twitter.com/MSIntune)

-   [Foros de Intune](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### <a name="next-steps"></a>Pasos siguientes
Los temas siguientes proporcionan ayuda para solucionar problemas específicos. Si esta información no le ayuda, póngase en contacto con el soporte técnico de Microsoft como se indica en [Cómo obtener asistencia para Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

[Solucionar problemas de Endpoint Protection en Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Solucionar problemas de acceso a los recursos de la empresa con Microsoft Intune](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Solucionar problemas de implementación de aplicaciones en Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Solucionar problemas con la inscripción de dispositivos en Intune](troubleshoot-device-enrollment-in-intune.md)

[Directivas de solución de problemas en Microsoft Intune](troubleshoot-policies-in-microsoft-intune.md)

[Solucionar problemas de configuración del cliente en Microsoft Intune](troubleshoot-client-setup-in-microsoft-intune.md)

[Solucionar problemas de actualizaciones de software en Microsoft Intune](troubleshoot-software-updates-in-microsoft-intune.md)
