---
title: "Configurar directivas de actualización de iOS"
titlesuffix: Azure portal
description: "Configure directivas de actualización de iOS para forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible."
keywords: 
author: dougeby
manager: dougeby
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6334421-85e1-4457-9c44-e5db8d4ee00e
ms.openlocfilehash: a119f00cc8a92aa6cf7a1009f910df817593e0e8
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="configure-ios-update-policies"></a>Configurar directivas de actualización de iOS
Las directivas de actualización de iOS permiten forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible. Tiene la opción de configurar qué días y qué horas no quiere que los dispositivos instalen la actualización.

## <a name="configure-the-ios-update-policy"></a>Configurar la directiva de actualización de iOS
1. Vaya a la hoja de Intune en Azure Portal.
2. En la hoja **Intune**, elija **Actualizaciones de software** > **Directivas de actualización de iOS**.
4. En la hoja de directivas, seleccione **Crear** y escriba un nombre y una descripción para la directiva.
5. Seleccione **Configuración** > **Configurar** y especifique cuándo los dispositivos iOS no están obligados a instalar la actualización más reciente.
6. Seleccione **Aceptar** para guardar esta configuración. Ahora habrá regresado a la hoja **Crear directiva de actualización**. Seleccione **Crear** para crear la directiva y guardar la configuración.

El perfil se crea y aparece en la hoja con la lista de directivas de actualización de iOS.

## <a name="assign-an-ios-update-policy-to-users"></a>Asignación de directivas de actualización de iOS a los usuarios
Para asignar una directiva de actualización de iOS a los usuarios, seleccione una directiva que haya configurado. Las directivas existentes se encuentran en la hoja **Actualizaciones de software** > **Directivas de actualización de iOS**.
1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Se abre la hoja donde puede seleccionar grupos de seguridad de Azure Active Directory y asignarlos a la directiva.
2. Elija **Seleccionar grupos** para abrir la hoja que muestra los grupos de seguridad de Azure AD. Elija **Seleccionar** para implementar la directiva en los usuarios.

Ya ha aplicado la directiva a los usuarios. Ahora se evaluará la comprobación de actualizaciones por parte de los dispositivos usados por los usuarios a los que se aplique la directiva.

## <a name="change-the-restricted-days-for-the-policy"></a>Cambio de los días restringidos de la directiva
1. En la hoja **Actualizaciones de software**, seleccione **Directivas de actualización de iOS**.
2. Seleccione la directiva de actualización de iOS que quiere actualizar.
3. Seleccione **Propiedades** y actualice la información de los días restringidos.
