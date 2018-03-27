---
title: Implementar y supervisar una directiva de cumplimiento normativo
description: Siga las instrucciones paso a paso de este tema para implementar y supervisar una directiva de cumplimiento normativo del dispositivo.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e24c969206d3e1f34bfee0af46c4398c9d2739a8
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune"></a>Implementar y supervisar una directiva de cumplimiento normativo en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="deploy-a-compliance-policy"></a>Implementar una directiva de cumplimiento
Implemente la directiva de cumplimiento normativo que ha [creado](create-a-device-compliance-policy-in-microsoft-intune.md) en uno o más grupos de usuarios de la organización. Cuando se implementa una directiva de cumplimiento para un usuario, se comprueba el cumplimiento de todos los dispositivos del usuario.

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, elija **Administrar la implementación**.
![Captura de pantalla de la página de directiva de cumplimiento normativo, donde se muestra la opción de menú Administrar implementación en la parte superior](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  En el cuadro de diálogo **Administrar implementación**, seleccione uno o varios grupos en los que quiera implementar la directiva y, después, haga clic en **Agregar** > **Aceptar**.
![Captura de pantalla del cuadro de diálogo Administrar implementación](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) Utilice los grupos de Active Directory que ya ha creado y sincronizado con Intune, o cree estos grupos manualmente en la consola de Intune. Para obtener más información sobre cómo implementar directivas, consulte [Implementar una directiva de configuración](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Use el resumen de estado y las alertas del área de trabajo **Directiva** de la página **Información** para identificar los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo **Panel** .

> [!IMPORTANT]
> Si no ha implementado una directiva de cumplimiento y habilita una directiva de acceso condicional de Exchange, se permitirá el acceso a todos los dispositivos de destino.

## <a name="monitor-the-compliance-policy"></a>Supervisar la directiva de cumplimiento

#### <a name="to-view-devices-that-do-not-conform-to-a-compliance-policy"></a>Para ver los dispositivos que no cumplen una directiva de cumplimiento

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Grupos** > **Todos los dispositivos**.

2.  Haga doble clic en el nombre de un dispositivo en la lista de dispositivos.

3.  Elija la pestaña **Directiva** para ver una lista de las directivas para ese dispositivo.

4.  En la lista desplegable **Filtros**, seleccione **No conforme con la directiva de cumplimiento normativo**.
![Captura de pantalla que muestra la lista de opciones de la lista de filtros](./media/intune-sa-3e-view-device-noncompliance.png)

#### <a name="to-view-the-health-attestation-reports"></a>Para ver los informes de atestación de estado

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Informes**.

2.  En la página **Informe de atestación de estado - Crear un nuevo informe**, puede ver un informe con todos los datos de atestación de estado de Windows 10 recopilados mediante Intune. También puede crear un informe con un subconjunto de los datos mediante filtros. Los filtros pueden basarse en el tipo de dispositivo, el sistema operativo o solo un subconjunto de puntos de datos.

## <a name="how-intune-resolves-policy-conflicts"></a>Cómo Intune resuelve los conflictos de directivas
Pueden producirse conflictos entre directivas de Intune cuando se aplican varias de ellas a un dispositivo. Si las configuraciones de directivas se solapan, Intune resuelve los conflictos siguiendo estas reglas:

-   Si las configuraciones en conflicto proceden de una directiva de configuración de Intune y una directiva de cumplimiento, la configuración de la directiva de cumplimiento tiene preferencia sobre la configuración de la directiva de configuración. Esto es así incluso si la configuración de la directiva de configuración es más segura.

-   Si ha implementado varias directivas de cumplimiento, Intune utilizará la más segura de ellas.

## <a name="next-steps"></a>Pasos siguientes
Para obtener información sobre cómo usar la directiva de cumplimiento con directivas de acceso condicional para controlar el acceso a los servicios de su organización, consulte [Restringir el acceso al correo electrónico y los servicios de O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).


### <a name="see-also"></a>Vea también
[Introducción a las directivas de cumplimiento de dispositivos en Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md)
