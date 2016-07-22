---
title: Implementar y supervisar una directiva de cumplimiento normativo en Microsoft Intune | Microsoft Intune
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ded7bd6c971a9448ad6e6492ebc5e42dfcb5d76e
ms.openlocfilehash: 52da5cf6d14a5fc3ff3db6bdb07823d3bf373466


---

# Implementar y supervisar una directiva de cumplimiento normativo en Microsoft Intune
## Implementar una directiva de cumplimiento
Implemente la directiva de cumplimiento normativo que haya [creado](create-a-device-compliance-policy-in-microsoft-intune.md) en uno o más grupos de usuarios o dispositivos de la organización.

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, haga clic en **Administrar la implementación**.
![Captura de pantalla de la página de directiva de cumplimiento normativo, donde se muestra la opción de menú Administrar implementación en la parte superior](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  En el cuadro de diálogo **Administrar implementación**, seleccione uno o varios grupos en los que quiera implementar la directiva y, después, haga clic en **Agregar > Aceptar**.
![Captura de pantalla del cuadro de diálogo Administrar implementación](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) Puede implementar una directiva de cumplimiento para usuarios o dispositivos. Use los grupos de Active Directory creados y sincronizados en Intune, o bien cree los grupos manualmente en la consola de Intune. Para obtener más información sobre cómo implementar directivas, vea [Implementar una directiva de configuración](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Use el resumen de estado y las alertas del área de trabajo **Directiva** de la página **Introducción** para identificar los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo **Panel** .

> [!IMPORTANT]Si no ha implementado una directiva de cumplimiento y habilitado la directiva de acceso condicional a Exchange, se permitirá el acceso a todos los dispositivos destinatarios.

## Cómo se resuelven los conflictos de directivas de Intune
Pueden producirse conflictos entre directivas de Intune si se aplican varias de ellas a un dispositivo. Si hay configuraciones de directivas en conflicto, Intune resuelve los conflictos con las siguientes reglas:

-   Si las configuraciones en conflicto son una directiva de configuración de Intune y una directiva de cumplimiento, la configuración de la directiva de cumplimiento tiene prioridad sobre la de la directiva de configuración, incluso en el caso de que los valores de la directiva de configuración sean más seguros.

-   Si implementó varias directivas de cumplimiento, se usará la más segura.

## Supervisar la directiva de cumplimiento

#### Para ver los dispositivos que no cumplen una directiva de cumplimiento

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Grupos > Todos los dispositivos**.

2.  Haga doble clic en el nombre de un dispositivo en la lista de dispositivos.

3.  Elija la pestaña **Directiva** para ver una lista de las directivas para ese dispositivo.

4.  En la lista desplegable **Filtros**, seleccione **No conforme con la directiva de cumplimiento normativo**.
![Captura de pantalla que muestra la lista de opciones de la lista de filtros](./media/intune-sa-3e-view-device-noncompliance.png)

#### Para ver los informes de atestación de estado

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Informes**.

2.  En la página **Informe de atestación de estado - Crear un nuevo informe**, puede ver un informe con todos los datos de atestación de estado de Windows 10 recopilados mediante Intune. También puede crear un informe con un subconjunto de los datos mediante filtros. Los filtros pueden basarse en el tipo de dispositivo, el sistema operativo o solo un subconjunto de puntos de datos.


## Pasos siguientes
Ahora puede usar la directiva de cumplimiento con las directivas de acceso condicional para controlar el acceso a los servicios de su organización.

[Restringir el acceso al correo electrónico y los servicios de O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


### Consulte también
[Introduction to device compliance policies in Intune (Introducción a las directivas de cumplimiento normativo de dispositivo en Intune)](introduction-to-device-compliance-policies-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


