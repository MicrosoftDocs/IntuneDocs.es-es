---
title: "Supervisión de las directivas de MAM con Microsoft Intune | Microsoft Intune"
description: "Vea cuántos usuarios tienen la directiva y profundice para descubrir más detalles."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 487fe778bae73c2ac5564f90c21328932060f576


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>Supervisión de directivas de administración de aplicaciones móviles con Microsoft Intune
Cuando haya configurado una directiva de administración (MAM) de aplicaciones móviles y la haya aplicado a los usuarios, puede supervisar el estado de cumplimiento en [Azure Portal](https://portal.azure.com). Azure Portal incluye información sobre los usuarios afectados por la directiva, el estado de cumplimiento y cualquier problema que puedan estar experimentando los usuarios finales.
## <a name="summary-view"></a>Vista Resumen
En la hoja **Administración de aplicaciones móviles de Intune**, puede ver un resumen del estado de cumplimiento:


![Ventana de resumen en la hoja Administración de aplicaciones móviles de Intune](../media/mam-azure-portal-user-status-summary.png)

-   **USUARIOS:** número total de usuarios de la empresa que usan las aplicaciones que están asociadas a la directiva.

-   **ADMINISTRADO POR UNA DIRECTIVA:** número de usuarios que han usado al menos una de las aplicaciones en un contexto de trabajo.

-   **NINGUNA DIRECTIVA:** número de usuarios que usan las aplicaciones asociadas a la directiva, pero a los que no se les aplica la directiva. Considere la posibilidad de agregar estos usuarios a la directiva.

- **Usuarios marcados:** número de usuarios que experimentan problemas. Actualmente, solo los usuarios con dispositivos descodificados aparecen como **Usuarios marcados**.


## <a name="detailed-view"></a>Vista detallada
Puede obtener la vista detallada del resumen si selecciona las ventanas **Estado del usuario** y **Usuarios marcados**.

### <a name="user-status"></a>Estado del usuario
Puede buscar un solo usuario y examinar su estado de cumplimiento. La hoja **Informes de aplicaciones** muestra la siguiente información sobre el usuario seleccionado:
- Dispositivos que están asociados a la cuenta de usuario

- Aplicaciones con la directiva MAM en el dispositivo

- Estado:

  - **Protegido:** significa que la directiva se implementó para el usuario y que la aplicación se usó al menos una vez en el contexto de trabajo.

  - **No protegido:** significa que la directiva se implementó para el usuario, pero la aplicación no se ha usado desde entonces en el contexto de trabajo.

>[!NOTE]
> Si el usuario que buscó no tiene la directiva de MAM implementada, aparecerá un mensaje informándole de que el usuario no será objeto de ninguna directiva de aplicaciones.

Para ver los informes sobre un usuario, siga estos pasos:

1.  Para seleccionar un usuario, haga clic en el icono **Resumen** o elija la opción **Informes de aplicaciones por usuarios** en la hoja **Configuración**:

    ![Opción Informes de aplicaciones de la hoja Configuración](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

2. En la hoja **Informes de aplicaciones** que se abre, elija **Seleccionar usuario** para buscar un usuario de Azure Active Directory.

    ![Opción Seleccionar usuario de la hoja Informes de aplicaciones](../media/mam-azure-portal-app-reporting-select-user.png)

3. Seleccione el usuario de la lista. Verá los detalles del estado de cumplimiento de ese usuario.

    ![Detalles de Informes de aplicaciones](../media/mam-azure-portal-app-reporting-by-user.png)

### <a name="flagged-users"></a>Usuarios marcados
La vista detallada muestra el mensaje de error, la aplicación usada cuando se produjo el error, la plataforma del dispositivo y una marca de tiempo.  

### <a name="see-also"></a>Consulte también
[Administrar la transferencia de datos entre aplicaciones iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Qué esperar cuando la aplicación Android está administrada por directivas MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [Qué esperar cuando la aplicación iOS está administrada por directivas MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


