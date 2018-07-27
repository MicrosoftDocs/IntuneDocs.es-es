---
title: Solucionar problemas de instalación de aplicaciones
titlesuffix: Microsoft Intune
description: Use el panel de solución de problemas de Microsoft Intune, el cual le ayuda a solucionar problemas de instalación de aplicaciones.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: c1c2a37103f8fedc09a70b4387aae3f472dfb636
ms.sourcegitcommit: dc8b6f802cca7895a19ec38bec283d4b3150d213
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39138686"
---
# <a name="troubleshoot-app-installation-issues"></a>Solucionar problemas de instalación de aplicaciones

En algunas ocasiones, las instalaciones de aplicaciones en los dispositivos administrados por MDM de Microsoft Intune pueden presentar errores. Cuando esto ocurre, puede ser complicado entender el motivo del error o cómo solucionarlo. Microsoft Intune proporciona detalles del error de instalación de aplicaciones que permiten a los operadores del departamento de soporte técnico y a los administradores de Intune ver información de la aplicación para atender las solicitudes de ayuda al usuario. En el panel de solución de problemas de Intune se proporcionan detalles del error, incluidos aquellos sobre las aplicaciones administradas en el dispositivo de un usuario. Se proporcionan detalles sobre el ciclo de vida de un extremo a otro en cada dispositivo individual del panel **Aplicaciones administradas**. Puede ver problemas de instalación, por ejemplo, al crearse, modificarse, dirigirse y entregarse la aplicación a un dispositivo. 

## <a name="to-review-app-troubleshooting-details"></a>Para ver los detalles de solución de problemas de la aplicación, siga estos pasos:

Intune proporciona los detalles de solución de problemas de la aplicación en función de las aplicaciones instaladas en el dispositivo de un usuario específico.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Solucionar problema**.
4. Haga clic en **Seleccionar usuario** para seleccionar un usuario para solucionar problemas. Se mostrará el panel **Seleccionar usuarios**.
5. Seleccione un usuario escribiendo su nombre o dirección de correo electrónico. Haga clic en **Seleccionar** en la parte inferior del panel. La información de solución de problemas del usuario se muestra en el panel de **solución de problemas**. 
6. Seleccione el dispositivo del que desea solucionar problemas en la lista **Dispositivos**.
    ![El panel de solución de problemas de Intune.](media/troubleshoot-app-install-01.png)
7. Seleccione **Aplicaciones administradas** en el panel de dispositivo seleccionado. Se muestra una lista de aplicaciones administradas.
    ![Detalles de un dispositivo específico administrado por Intune.](media/troubleshoot-app-install-02.png)
8. Seleccione una aplicación en la lista donde **Estado de la instalación** indica un error.
    ![Una aplicación seleccionada que muestra detalles del error de instalación.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > La misma aplicación podría asignarse a varios grupos, pero con diferentes acciones previstas (intenciones) para la aplicación. Por ejemplo, una intención resuelta para una aplicación se mostrará como **excluida** si la aplicación se excluye para un usuario durante la asignación de aplicaciones. Para obtener más información, consulte [Cómo se resuelven los conflictos entre las intenciones de aplicación](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Actualmente, Intune no filtra las aplicaciones en función de la plataforma de SO.

Los detalles del error de instalación de la aplicación indicarán el problema. Puede usar estos detalles para determinar cuál es la mejor acción para resolver el problema. Para obtener más información sobre la solución de problemas de instalación de la aplicación, consulte [Error Codes For Troubleshooting App Installation Issues](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues) (Códigos de error para la solución de problemas de instalación de la aplicación).

> [!Note]  
> También puede acceder al panel de **solución de problemas** visitando la página [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) desde el explorador.

## <a name="next-steps"></a>Pasos siguientes

- Para obtener información adicional sobre la solución de problemas de Intune, consulte [Uso del portal de solución de problemas para ayudar a los usuarios de su empresa](help-desk-operators.md). 
- Obtenga información sobre los problemas conocidos de Microsoft Intune. Para obtener más información, consulte [Problemas conocidos de Microsoft Intune](known-issues.md).
- ¿Necesita más ayuda? Consulte [Cómo obtener asistencia para Microsoft Intune](get-support.md).
