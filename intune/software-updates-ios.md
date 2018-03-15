---
title: "Configurar directivas de actualización de iOS en Microsoft Intune"
titlesuffix: 
description: "Configure directivas de actualización de iOS para forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.openlocfilehash: 2062f9cd551ec6d7f42449041e6c8de837221631
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Configurar directivas de actualización de iOS en Microsoft Intune
Las directivas de actualización de iOS permiten forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible. Tiene la opción de configurar qué días y qué horas no quiere que los dispositivos instalen la actualización.

## <a name="configure-the-ios-update-policy"></a>Configurar la directiva de actualización de iOS
1. Vaya a la página Intune en Azure Portal.
2. En la página **Intune**, elija **Actualizaciones de software** > **Directivas de actualización de iOS**.
4. En la página de directivas, seleccione **Crear** y escriba un nombre y una descripción para la directiva.
5. Seleccione **Configuración** > **Configurar** y especifique cuándo los dispositivos iOS no están obligados a instalar la actualización más reciente.
6. Seleccione **Aceptar** para guardar esta configuración. Ha vuelto a la página **Crear directiva de actualización**. Seleccione **Crear** para crear la directiva y guardar la configuración.

El perfil se crea y aparece en la página con la lista de directivas de actualización de iOS.

## <a name="assign-an-ios-update-policy-to-users"></a>Asignación de directivas de actualización de iOS a los usuarios
Para asignar una directiva de actualización de iOS a los usuarios, seleccione una directiva que haya configurado. Las directivas existentes se encuentran en la página **Actualizaciones de software** > **Directivas de actualización de iOS**.
1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Se abre la página donde puede seleccionar grupos de seguridad de Azure Active Directory y asignarlos a la directiva.
2. Elija **Seleccionar grupos** para abrir la página que muestra los grupos de seguridad de Azure AD. Elija **Seleccionar** para implementar la directiva en los usuarios.

Ya ha aplicado la directiva a los usuarios. Se evalúa la comprobación de actualizaciones por parte de los dispositivos usados por los usuarios a los que se aplique la directiva.

## <a name="change-the-restricted-days-for-the-policy"></a>Cambio de los días restringidos de la directiva
1. En la página **Actualizaciones de software**, elija **Directivas de actualización de iOS**.
2. Seleccione la directiva de actualización de iOS que quiere actualizar.
3. Seleccione **Propiedades** y actualice la información de los días restringidos.

## <a name="monitor-ios-devices-with-older-ios-versions"></a>Supervisar dispositivos iOS con versiones anteriores de iOS 
<!-- 1352223 -->
El informe **Dispositivos iOS no actualizados** está disponible en la página **Actualizaciones de software** > **Directivas de actualización de iOS**. En el informe, puede ver una lista de dispositivos iOS supervisados destinados mediante una directiva de actualización iOS y que no se pudieron actualizar. Para cada dispositivo, puede ver un estado por el que el dispositivo no se ha actualizado automáticamente.