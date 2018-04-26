---
title: Configurar directivas de actualización de software de iOS en Microsoft Intune
titlesuffix: ''
description: Configure directivas de actualización de iOS para forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 1d4223ae4feb417f77909b320cd0295347b44461
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Configurar directivas de actualización de iOS en Microsoft Intune

Las directivas de actualización de software le permiten forzar los dispositivos iOS que ejecutan iOS 10.3 y versiones posteriores para que instalen de forma automática la actualización de sistema operativo disponible más reciente. Esta característica solo está disponible en los dispositivos supervisados. Tiene la opción de configurar qué días y qué horas no quiere que los dispositivos instalen la actualización. 

Al registrar el dispositivo, más o menos cada 8 horas, si hay una actualización disponible y no está en un periodo restringido, el dispositivo intentará descargar e instalar la actualización de sistema operativo más reciente. No se necesita ninguna interacción del usuario para actualizar el dispositivo. La directiva no impediría que un usuario actualizara el sistema operativo.

## <a name="configure-the-ios-update-policy"></a>Configurar la directiva de actualización de iOS
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Actualizaciones de software** > **Directivas de actualización de iOS**.
4. En el panel de directivas, elija **Crear** y escriba un nombre y una descripción para la directiva.
5. Seleccione **Configuración** > **Configurar** y especifique cuándo los dispositivos iOS no están obligados a instalar la actualización más reciente. Puede configurar los días de la semana, la zona horaria, la hora de inicio y la hora de finalización.
6. Seleccione **Aceptar** para guardar esta configuración. Regresará al panel **Crear directiva de actualización**. Seleccione **Crear** para crear la directiva y guardar la configuración.

El perfil se crea y aparece en el panel con la lista de directivas de actualización de iOS. La administración de dispositivos móviles (MDM) de Apple no permite la posibilidad de forzar que el dispositivo instale la actualización en una hora o una fecha concretas. 

## <a name="change-the-restricted-times-for-the-policy"></a>Cambio de los períodos restringidos de la directiva

1.  En la hoja **Actualizaciones de software**, seleccione **Directivas de actualización de iOS**.
2.  Seleccione la directiva de actualización de iOS que quiere actualizar.
3.  Seleccione **Propiedades** y actualice la información de los períodos restringidos.
4.  Seleccione los días de la semana.
5.  Seleccione la zona horaria en la que se aplicará esta directiva.
6.  Seleccione la hora de inicio y de finalización de las horas incluidas en la lista de bloqueados.

## <a name="assign-an-ios-update-policy-to-users"></a>Asignación de directivas de actualización de iOS a los usuarios

Para asignar una directiva de actualización de iOS a los usuarios, seleccione una directiva que haya configurado. Las directivas existentes se encuentran en el panel **Actualizaciones de software** > **Directivas de actualización de iOS**.

1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Se abre el panel donde puede seleccionar grupos de seguridad de Azure Active Directory y asignarlos a la directiva.
2. Elija **Grupos seleccionados** para abrir el panel en el que se muestran los grupos de seguridad de Azure AD. Determine quién tiene acceso a la directiva asignando los grupos que quiera incluir o excluir.
3. Elija **Guardar** para implementar la directiva en los usuarios.

Ya ha aplicado la directiva a los usuarios o dispositivos. Se evalúa la comprobación de actualizaciones por parte de los dispositivos usados por los usuarios a los que se aplique la directiva. Esta directiva también es compatible con los dispositivos sin usuario.

## <a name="monitor-ios-device-installation-failures"></a>Supervisión de errores de instalación de dispositivos iOS
<!-- 1352223 -->
El informe **Errores de instalación de dispositivos iOS** está disponible en el panel **Actualizaciones de software**. En el informe puede ver una lista de dispositivos iOS supervisados que fueron objetivo de una directiva de actualización de iOS y que han intentado llevar a cabo una actualización, pero que no la completaron. Para cada dispositivo, puede ver un estado por el que el dispositivo no se ha actualizado automáticamente. Los dispositivos actualizados y que estén en buen estado no figurarán en la lista. Por "actualizados" entendemos la actualización más reciente que puede admitir el propio dispositivo.

