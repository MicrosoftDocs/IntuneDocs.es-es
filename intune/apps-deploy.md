---
title: "Asignación de aplicaciones a grupos | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: cuando haya agregado una aplicación a Intune, querrá asignarla a grupos de usuarios o dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 1246ef539c044b894b4e4a93f449e60e6462600a
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Asignación de aplicaciones a grupos con Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

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
|Desinstalar aplicaciones|Sí|No|
|Los usuarios finales instalan las aplicaciones disponibles desde la aplicación Portal de empresa|Sí|No|
|Los usuarios finales instalan aplicaciones disponibles desde el Portal de empresa basado en web|Sí|Sí|

> [!NOTE]
> Actualmente, puede asignar aplicaciones iOS y Android (tanto de línea de negocio como comparas en la tienda) a dispositivo que no estén inscritos en Intune.

## <a name="changes-to-how-you-assign-apps-to-groups-in-the-intune-preview"></a>Cambios en la asignación de aplicaciones a grupos en la versión preliminar de Intune

En la versión preliminar de Azure de Intune ya no se usan grupos de Intune para asignar aplicaciones. Ahora se usan grupos de seguridad de Azure Active Directory (Azure AD). Por este motivo, debe conocer algunos cambios en el funcionamiento de las asignaciones de aplicaciones, especialmente cuando haya asignado aplicaciones a grupos secundarios de Intune.
Lo más importante que debe tener en cuenta es que en Azure AD no existe el concepto de grupo secundario. En cambio, es posible que algunos grupos contengan los mismos miembros. En este caso, el comportamiento entre la versión clásica de Intune y la versión preliminar de Azure de Intune es diferente. En la tabla siguiente se muestra este comportamiento:

||||||
|-|-|-|-|-|
|**Versión clásica de Intune (antes de la migración de inquilino)**|-|**Azure de Intune (después de completar la migración de inquilino)**|-|**Más información**|
|**Intención de asignación de grupo primario**|**Intención de asignación de grupo secundario**|**Intento de asignación resultante para los miembros comunes del grupo primario y secundario anterior**|**Acción de intento de asignación resultante para los miembros del grupo primario**|-|
|Available|Requerido|Requerido y Disponible|Available|Requerido y Disponible significa que las aplicaciones asignadas como requeridas también pueden verse en la aplicación Portal de empresa.
|No aplicable|Available|No aplicable|No aplicable|Solución alternativa: Quite la intención de asignación "No aplicable" del grupo primario de Intune.
|Requerido|Available|Requerido y Disponible|Requerido|-|
|Requerido y Disponible<sup>1</sup>|Available|Requerido y Disponible|Requerido y Disponible|-|
|Requerido|No aplicable|Requerido|Requerido|-|
|Requerido y Disponible|No aplicable|Requerido y Disponible|Requerido y Disponible|-|
|Requerido|Desinstalar|Requerido|Requerido|-|
|Requerido y Disponible|Desinstalar|Requerido y Disponible|Requerido y Disponible|-|
<sup>1</sup> Solo para aplicaciones administradas de la tienda de iOS, cuando se agregan a Intune y se asignan como requeridas, se crean automáticamente con las intenciones Requerido y Disponible.

Puede realizar las siguientes acciones para evitar conflictos de asignación:

1.    Si ha asignado previamente aplicaciones en grupos primarios y secundarios relacionados de Intune, considere la posibilidad de quitar estas asignaciones antes de comenzar la migración del inquilino.
2.    Quite los grupos secundarios de los grupos primarios y cree un nuevo grupo que contenga los miembros del grupo secundario anterior. Después, puede crear una nueva asignación de aplicación para este grupo.
Notas: Si el grupo primario anterior era "Todos los usuarios", deberá crear un nuevo grupo dinámico que no incluya a los miembros del grupo secundario.
Debe realizar los cambios a los grupos en [Azure Portal](https://portal.azure.com/) para grupos de usuarios y dispositivos. El [Portal de Azure clásico](https://manage.windowsazure.com/) solo permite realizar cambios en grupos de usuarios.


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
    - **Available with or without enrollment** (Disponible con o sin inscripción): asignar esta aplicación a grupos de usuarios cuyos dispositivos no se hayan inscrito en Intune. Consulte la tabla anterior para obtener ayuda.
6. Cuando termine, elija **Guardar**.

La aplicación ahora se asigna al grupo que eligió.

Consulte [Supervisión de aplicaciones](apps-monitor.md) para obtener información que le ayude a supervisar las asignaciones de aplicaciones.

