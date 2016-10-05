---
title:
- "Solucionar problemas de la administración de aplicaciones móviles | Microsoft Intune"
description: 
keywords: 
author: karaman
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: 9cfb3694b2fae919fd0554a6e21b497cdcf19c72
ms.openlocfilehash: f33e8de82ee07bb4571a5bfaff63af72f9086376


---

# Solucionar problemas de la administración de aplicaciones móviles

Si tiene problemas con la administración de aplicaciones móviles, empiece por aquí. En este tema se incluyen algunos problemas comunes que pueden surgir y sus soluciones.


**Problema:** la directiva de MAM sin inscripción de la consola de Azure no se aplica a la aplicación de Skype Empresarial en dispositivos iOS y Android.

Solución: debe configurar Skype Empresarial para la autenticación moderna.  Siga las instrucciones que se indican en [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (Habilitar el inquilino para la autenticación moderna) para configurar la autenticación moderna de Skype.

**Problema:** las directivas de MAM sin inscripción no se aplican a ninguna aplicación de Office compatible (https://www.microsoft.com/es-es/cloud-platform/microsoft-intune-partners) para ningún usuario.
 
Solución: confirme que el usuario tiene licencia para Intune.  

**Problema:** el usuario administrador de TI no puede configurar directivas de MAM en Azure Portal.

Solución: los roles siguientes tienen acceso a Azure Portal:

- El administrador global, que puede configurar en el [Portal de Office](http://portal.office.com/).
- El propietario, que puede configurar en [Azure Portal](https://portal.azure.com/).
- El colaborador, que puede configurar en [Azure Portal](https://portal.azure.com/).

Consulte [Preparación para configurar directivas de administración de aplicaciones móviles con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) para obtener ayuda sobre cómo configurar estos roles. 

**Problema:** en el informe de aplicación no se muestran los usuarios a los que se ha aplicado recientemente la directiva de MAM.

Solución: si se acaba de aplicar a un usuario una directiva de MAM, dicho usuario puede tardar hasta 24 horas en aparecer en los informes como usuario de destino. 

**Problema:** los cambios o las actualizaciones de directivas pueden tardar hasta 8 horas en aplicarse.  

Solución: el usuario final puede cerrar sesión en la aplicación y volver a iniciarla para forzar la sincronización con el servicio.  

**Problema:** la directiva de MAM no se aplica a dispositivos DEP de Apple.

Solución: asegúrese de que usa la afinidad de usuario con el Programa de inscripción de dispositivos (DEP) de Apple. La afinidad de usuario es necesaria para todas las aplicaciones que requieran la autenticación de usuario en DEP.
Consulte [Inscribir dispositivos iOS de la empresa mediante el Programa de inscripción de dispositivos](https://docs.microsoft.com/en-us/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) para obtener más información sobre la inscripción de DEP de iOS.


### Consulte también
- [Validar la configuración de administración de aplicaciones móviles](https://docs.microsoft.com/en-us/intune/deploy-use/validate-mobile-application-management)
- [Get ready to configure mobile app management policies with Microsoft Intune (Preparación para configurar directivas de administración de aplicaciones móviles con Microsoft Intune)](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 





<!--HONumber=Sep16_HO2-->


