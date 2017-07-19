---
title: "Asignación de aplicaciones a grupos"
titleSuffix: Intune on Azure
description: "Cuando haya agregado una aplicación a Intune, querrá asignarla a grupos de usuarios o dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 059c6d2c65c78b6a94f93c26d606abe0451edbbb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Asignación de aplicaciones a grupos con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Cuando haya agregado una aplicación a Intune, puede asignarla a los usuarios y dispositivos.

Se pueden asignar aplicaciones a dispositivos aunque no estén administrados en Intune. Use la tabla siguiente para ayudarle a comprender las diversas opciones para asignar aplicaciones a usuarios y dispositivos:

||||
|-|-|-|-|
|&nbsp;|Dispositivos inscritos en Intune|Dispositivos no inscritos en Intune|
|Asignar a usuarios|Sí|Sí|
|Asignar a dispositivos|Sí|No|
|Asignar aplicaciones ajustadas o aplicaciones que incorporan el SDK de Intune (para directivas de protección de aplicaciones)|Sí|Sí|
|Asignar aplicaciones como disponibles|Sí|Sí|
|Asignar aplicaciones como obligatorias|Sí|No|
|Desinstalar aplicaciones|Sí|No|
|Los usuarios finales instalan las aplicaciones disponibles desde la aplicación Portal de empresa|Sí|No|
|Los usuarios finales instalan aplicaciones disponibles desde el Portal de empresa basado en web|Sí|Sí|

> [!NOTE]
> Actualmente, puede asignar aplicaciones iOS y Android (tanto de línea de negocio como comparas en la tienda) a dispositivo que no estén inscritos en Intune.

## <a name="how-to-assign-an-app"></a>Asignación de una aplicación

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Mobile apps**.
1. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
2. En la hoja de lista de aplicaciones, haga clic en la aplicación que quiere asignar.
3. En la hoja <*nombre de la aplicación*> - **Overview** (Información general), elija **Administrar** > **Asignaciones**.
4. Elija **Seleccionar grupos** y, en la hoja **Seleccionar grupos**, elija los grupos de Azure AD al que quiere asignar la aplicación.
5. Para cada aplicación que elija, seleccione un **tipo de asignación** para la aplicación, como:
    - **Disponible**: los usuarios instalan la aplicación desde el sitio web o la aplicación del Portal de empresa.
    - **No aplicable**: la aplicación no está instalada ni se muestra en el Portal de empresa.
    - **Requerida**: la aplicación se instala en dispositivos de los grupos seleccionados.
    - **Desinstalar**: la aplicación se ha desinstalado de dispositivos de los grupos seleccionados.
    - **Available with or without enrollment** (Disponible con o sin inscripción): asignar esta aplicación a grupos de usuarios cuyos dispositivos no se hayan inscrito en Intune.
6. Cuando termine, elija **Guardar**.

La aplicación ahora se asigna al grupo que ha seleccionado.

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Cómo se resuelven los conflictos entre las intenciones de aplicación

A veces, la misma aplicación se asigna a varios grupos, pero con diferentes intenciones. En estos casos, use esta tabla para entender la intención resultante.

||||
|-|-|-|
|Intención del grupo 1|Intención del grupo 2|Intención resultante|
|Usuario Requerido|Usuario disponible|Requerido y Disponible|
|Usuario Requerido|Usuario no disponible|Requerido|
|Usuario Requerido|Desinstalar usuario|Requerido|
|Usuario disponible|Usuario no disponible|No disponible|
|Usuario disponible|Desinstalar usuario|Desinstalar|
|Usuario no disponible|Desinstalar usuario|Desinstalar
|Usuario Requerido|Dispositivo Requerido|Ambos existen, se necesita tratar la puerta de enlace 
|Usuario Requerido|Desinstalar dispositivo|Ambos existen, se necesita resolver la puerta de enlace como Requerido 
|Usuario disponible|Dispositivo Requerido|Ambos existen, se necesita resolver la puerta de enlace (Requerido y Disponible)
|Usuario disponible|Desinstalar dispositivo|Ambos existen, se necesita resolver la puerta de enlace como Disponible.<br>La aplicación se muestra en el portal de empresa.<br>En caso de que la aplicación ya esté instalada (como aplicación necesaria con la intención anterior), entonces la aplicación se desinstala.<br>Pero si el usuario hace clic en Instalar desde el portal de empresa, entonces la aplicación se instala y la intención de desinstalación no se respeta.|
|Usuario no disponible|Dispositivo Requerido|Requerido|
|Usuario no disponible|Desinstalar dispositivo|Desinstalar|
|Desinstalar usuario|Dispositivo Requerido|Ambos existen, se necesita resolver la puerta de enlace como Requerido|
|Desinstalar usuario|Desinstalar dispositivo|Ambos existen, se necesita resolver la puerta de enlace como Desinstalar|
|Dispositivo Requerido|Desinstalar dispositivo|Requerido|
|Usuario Requerido y Disponible|Usuario disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Desinstalar usuario|Requerido y Disponible|
|Usuario Requerido y Disponible|Usuario no disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Dispositivo Requerido|Ambos existen, Requerido y Disponible
|Usuario Requerido y Disponible|Dispositivo no disponible|Requerido y Disponible|
|Usuario Requerido y Disponible|Desinstalar dispositivo|Ambos existen, se necesita resolver la puerta de enlace como Requerido Requerido + Disponible
|Usuario no disponible|Dispositivo no disponible|No disponible|
|Usuario disponible|Dispositivo no disponible|Available|
|Usuario Requerido|Dispositivo no disponible|Requerido|
|Usuario disponible sin inscripción|Usuario Requerido y Disponible|Requerido y Disponible
|Usuario disponible sin inscripción|Usuario Requerido|Requerido
|Usuario disponible sin inscripción|Usuario no disponible|No disponible
|Usuario disponible sin inscripción|Usuario disponible|Available|
|Usuario disponible sin inscripción|Dispositivo Requerido|Requerido y Disponible sin inscripción|
|Usuario disponible sin inscripción|Dispositivo no disponible|Disponible sin inscripción|
|Usuario disponible sin inscripción|Desinstalar dispositivo|Desinstalar y Disponible sin inscripción.<br>Si el usuario no ha instalado la aplicación desde el portal de empresa entonces se respetará la desinstalación.<br>Si el usuario instala la aplicación desde el portal de empresa, entonces la instalación se priorizará sobre la desinstalación.|

>[!NOTE]
>Solo para aplicaciones administradas de la tienda de iOS, cuando se agregan a Intune y se asignan como necesarias, se crean automáticamente con las intenciones Requerido y Disponible.

## <a name="next-steps"></a>Pasos siguientes

Consulte [Supervisión de aplicaciones](apps-monitor.md) para obtener información que le ayude a supervisar las asignaciones de aplicaciones.
