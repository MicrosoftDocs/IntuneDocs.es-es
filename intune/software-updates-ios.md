---
title: Configurar directivas de actualización de iOS en Microsoft Intune
titlesuffix: ''
description: Configure directivas de actualización de iOS para forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 6ba354fb3b39544f09363651abfd9e1a5c0f6154
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Configurar directivas de actualización de iOS en Microsoft Intune
Las directivas de actualización de iOS permiten forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible. Tiene la opción de configurar qué días y qué horas no quiere que los dispositivos instalen la actualización.

## <a name="configure-the-ios-update-policy"></a>Configurar la directiva de actualización de iOS
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
2. En el panel **Intune**, elija **Actualizaciones de software** > **Directivas de actualización de iOS**.
4. En el panel de directivas, elija **Crear** y escriba un nombre y una descripción para la directiva.
5. Seleccione **Configuración** > **Configurar** y especifique cuándo los dispositivos iOS no están obligados a instalar la actualización más reciente.
6. Seleccione **Aceptar** para guardar esta configuración. Regresará al panel **Crear directiva de actualización**. Seleccione **Crear** para crear la directiva y guardar la configuración.

El perfil se crea y aparece en el panel con la lista de directivas de actualización de iOS.

## <a name="assign-an-ios-update-policy-to-users"></a>Asignación de directivas de actualización de iOS a los usuarios
Para asignar una directiva de actualización de iOS a los usuarios, seleccione una directiva que haya configurado. Las directivas existentes se encuentran en el panel **Actualizaciones de software** > **Directivas de actualización de iOS**.
1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Se abre el panel donde puede seleccionar grupos de seguridad de Azure Active Directory y asignarlos a la directiva.
2. Elija **Grupos seleccionados** para abrir el panel en el que se muestran los grupos de seguridad de Azure AD.
3. Elija **Guardar** para implementar la directiva en los usuarios.

Ya ha aplicado la directiva a los usuarios. Se evalúa la comprobación de actualizaciones por parte de los dispositivos usados por los usuarios a los que se aplique la directiva.

## <a name="change-the-restricted-days-for-the-policy"></a>Cambio de los días restringidos de la directiva
1. En el panel **Actualizaciones de software**, elija **Directivas de actualización de iOS**.
2. Seleccione la directiva de actualización de iOS que quiere actualizar.
3. Seleccione **Propiedades** > **Configuración** y actualice la información de los días restringidos.

## <a name="monitor-ios-devices-with-older-ios-versions"></a>Supervisar dispositivos iOS con versiones anteriores de iOS
<!-- 1352223 -->
El informe **Dispositivos iOS no actualizados** está disponible en el panel **Actualizaciones de software** > **Directivas de actualización de iOS**. En el informe, puede ver una lista de dispositivos iOS supervisados destinados mediante una directiva de actualización iOS y que no se pudieron actualizar. Para cada dispositivo, puede ver un estado por el que el dispositivo no se ha actualizado automáticamente.
