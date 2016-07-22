---
title: "Sugerencias de solución de problemas generales | Microsoft Intune"
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 6b2d1d5eecb543e45fca5fbb8aa1854c88ec4f9c


---

# Sugerencias de solución de problemas generales para Microsoft Intune
Después de implementar Microsoft Intune puede encontrar problemas con la configuración o con los clientes. Los recursos siguientes pueden ayudarle a averiguar la causa del problema a fin de solucionarlo.

> [!NOTE]
> Para crear una solicitud de soporte técnico o para ver una solicitud existente, [visite el Centro de administración de Office 365](https://portal.office.com/admin/default.aspx). Para obtener más información sobre las opciones de soporte técnico, vea [Cómo obtener asistencia para Microsoft Intune](how-to-get-support-for-microsoft-intune.md).
## Definir el problema

-   ¿Cuál es el comportamiento?

-   ¿Quién experimenta el problema, y en qué plataformas y dispositivos?

-   ¿El dispositivo funcionaba bien anteriormente?

-   ¿Qué cambios realizó en la configuración de Intune o del dispositivo?

-   Tenga en cuenta si se realizaron otros cambios en el entorno en el que opera, aparte de los cambios de configuración.

-   ¿Con qué frecuencia se produce este problema? ¿Es esporádico o constante?

-   ¿Puede ser que el usuario esté experimentando un problema de autenticación? Si es posible, compruebe si el usuario puede iniciar sesión en otros servicios que usen Azure Active Directory. Pruebe también si el usuario puede iniciar sesión desde otro dispositivo.

-   ¿Ha comprobado el estado del servicio? Puede supervisar el mantenimiento del servicio Intune en el [portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx). Elija **Mantenimiento del servicio** en el panel izquierdo.

## Recopilar datos disponibles

-   Registros del dispositivo. Obtenga información sobre cómo recopilar registros del dispositivo en:
  - [Send Android diagnostic data logs to your IT administrator using a USB cable (Enviar registros de datos de diagnóstico de Android al administrador de TI mediante un cable USB)](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Send Android diagnostic data logs to your IT administrator using email (Enviar registros de datos de diagnóstico de Android al administrador de TI mediante correo electrónico)](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Send Android enrollment errors to your IT administrator (Enviar errores de inscripción de Android al administrador de TI)](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
  - [Send iOS enrollment errors to your IT administrator (Enviar errores de inscripción de iOS al administrador de TI)](/intune/enduser/send-errors-to-your-it-admin-ios)

-   Datos de la consola de administración. Por ejemplo, en caso de problemas de implementación de directivas, debe examinar la directiva que quiera y su estado, tal como se describe en [Usar grupos para administrar usuarios y dispositivos en Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## Investigar la solución

-   Buscar una solución en la Web. Por ejemplo, si recibe el error 0x80073CF0, puede buscar **technet intune 0x80073cf0** en la Web y buscar el artículo [Troubleshoot app deployment problems in Microsoft Intune (Solucionar problemas de implementación de aplicaciones en Microsoft Intune)](troubleshoot-app-deployment-problems-in-microsoft-intune.md), que ofrece sugerencias para resolver este problema.

-   Puede buscar respuestas en el [foro de TechNet de Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  Si el problema no se abordó anteriormente, debe publicar la pregunta para ver qué sugerencias ofrece la comunidad.

-   Puede abrir una solicitud de soporte técnico. El soporte técnico de Intune estará más preparado para ayudarle a resolver un problema si lo tiene definido y recopiló los datos disponibles.

    Para crear una solicitud de soporte técnico, [visite el Centro de administración de Office 365](https://portal.office.com/admin/default.aspx). Para obtener más información sobre las opciones de soporte técnico, vea [Cómo obtener asistencia para Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## Recursos de la Comunidad
Puede encontrar información útil en estos recursos de la comunidad:

-   La [Microsoft Intune Survival Guide (Guía de supervivencia de Microsoft Intune)](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) contiene vínculos a muchos recursos que pueden ayudarle a configurar, mantener y solucionar problemas de Intune.

-   [Blog de Intune](http://blogs.technet.com/b/windowsintune/)

-   [Siga Intune en Twitter](https://twitter.com/MSIntune)

-   [Foros de Intune](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### Pasos siguientes
Los temas que se enumeran a continuación proporcionan ayuda para solucionar problemas específicos. Si esta información no le ayuda, póngase en contacto con el soporte técnico de Microsoft como se indica en [Cómo obtener asistencia para Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

[Troubleshoot Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Solucionar problemas de acceso a los recursos de la empresa con Microsoft Intune](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Solucionar problemas de implementación de aplicaciones en Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Solución de problemas con la inscripción de dispositivos en Intune](troubleshoot-device-enrollment-in-intune.md)

[Directivas de solución de problemas en Microsoft Intune](troubleshoot-policies-in-microsoft-intune.md)

[Solucionar los problemas de configuración del cliente en Microsoft Intune](troubleshoot-client-setup-in-microsoft-intune.md)

[Solucionar problemas de actualizaciones de software en Microsoft Intune](troubleshoot-software-updates-in-microsoft-intune.md)



<!--HONumber=Jul16_HO1-->


