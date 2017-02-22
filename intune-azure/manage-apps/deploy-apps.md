---
title: "Asignación de aplicaciones a grupos | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: cuando haya agregado una aplicación a Intune, querrá asignarla a grupos de usuarios o dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 424fae862592c1ab5b4221fb5ad40a52c39f6760
ms.openlocfilehash: 145f27e44d57e0f5ff7bbed76e14db713dd75286

---

# <a name="how-to-assign-apps-to-groups"></a>Asignación de aplicaciones a grupos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Cuando haya agregado una aplicación a Intune, querrá usarla para los usuarios y dispositivos. Para ello, asígnela.

Se pueden asignar aplicaciones a dispositivos aunque no estén administrados en Intune. Use la tabla siguiente para ayudarle a comprender las diversas opciones para asignar aplicaciones a usuarios y dispositivos:

||||
|-|-|-|-|
|&nbsp;|Dispositivos inscritos en Intune|Dispositivos no inscritos en Intune|
|Asignar a usuarios|Sí|Sí|
|Asignar a dispositivos|Sí|No|
|Asignar aplicaciones ajustadas o aplicaciones que incorporan el SDK de Intune (para directivas de protección de aplicaciones)|Sí|Sí|
|Asignar aplicaciones como disponibles|Sí|Sí|
|Asignar aplicaciones como obligatorias|Sí|No|
|Desinstalar aplicaciones|Sí|Sí|
|Los usuarios finales instalan las aplicaciones disponibles desde la aplicación Portal de empresa|Sí|No|
|Los usuarios finales instalan aplicaciones disponibles desde el Portal de empresa basado en web|Sí|Sí|

> [!NOTE]
> Actualmente, puede asignar aplicaciones iOS y Android (tanto de línea de negocio como comparas en la tienda) a dispositivo que no estén inscritos en Intune.

## <a name="how-to-assign-an-app"></a>Asignación de una aplicación

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Administrar aplicaciones**.
1. En la carga de trabajo **Administrar aplicaciones**, elija **Administrar** > **Aplicaciones**.
2. En la hoja de lista de aplicaciones, haga clic en la aplicación que quiere asignar.
3. En la hoja <*nombre de la aplicación*> - **Overview** (Información general), elija **Administrar** > **Asignaciones**.
4. Elija **Seleccionar grupos** y, en la hoja **Seleccionar grupos**, elija los grupos de Azure AD al que quiere asignar la aplicación.
5. Para cada aplicación que elija, seleccione un **tipo de asignación** para la aplicación, como:
    - **Disponible**: los usuarios instalan la aplicación desde el sitio web o la aplicación del Portal de empresa.
    - **No aplicable**: la aplicación no está instalada ni se muestra en el Portal de empresa.
    - **Requerida**: la aplicación se instala en dispositivos de los grupos seleccionados.
    - **Desinstalar**: la aplicación se ha desinstalado de dispositivos de los grupos seleccionados.
    - **Available with or without enrollment** (Disponible con o sin inscripción): asignar esta aplicación a grupos de usuarios cuyos dispositivos no se hayan inscrito en Intune. Consulte la tabla anterior para obtener ayuda.
6. Cuando termine, elija **Guardar**.

La aplicación ahora se asigna al grupo que eligió.

Consulte [Supervisión de aplicaciones](monitor-apps.md) para obtener información que le ayude a supervisar las asignaciones de aplicaciones.



<!--HONumber=Feb17_HO1-->


