---
title: Conjuntos de directivas
titleSuffix: Microsoft Intune
description: Use conjuntos de directivas para agrupar colecciones de objetos de administración en Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d302db46510b664aec5b0a71fd8b19985e29be37
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206132"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>Uso de conjuntos de directivas para agrupar colecciones de objetos de administración

Los conjuntos de directivas permiten crear una agrupación de referencias a entidades de administración ya existentes que se deben identificar, establecer como destino y supervisar como una sola unidad conceptual. Un conjunto de directivas es una colección asignable de aplicaciones, directivas y otros objetos de administración que se han creado. La creación de un conjunto de directivas permite seleccionar muchos objetos diferentes a la vez y asignarlos desde un único lugar. A medida que la organización va cambiando, se puede regresar a un conjunto de directivas para agregarle o quitarle objetos y asignaciones. Un conjunto de directivas puede servir para asociar y asignar objetos existentes (como aplicaciones, directivas y VPN) a un único paquete. 

> [!IMPORTANT]
> Para obtener una lista de los problemas conocidos relativos a los conjuntos de directivas, vea [Problemas conocidos de los conjuntos de directivas](~/fundamentals/policy-sets.md#policy-sets-known-issues).

Los conjuntos de directivas no reemplazan los conceptos ni los objetos existentes. Puede seguir asignando objetos individuales y, asimismo, hacer referencia a objetos individuales como parte de un conjunto de directivas. Por lo tanto, cualquier cambio que se realice en esos objetos individuales se verá reflejado en el conjunto de directivas. 

Los conjuntos de directivas se pueden usar para lo siguiente:

- Agrupar objetos que se deben asignar juntos
- Asignar los requisitos mínimos de configuración de la organización en todos los dispositivos administrados
- Asignar aplicaciones relevantes o de uso frecuente a todos los usuarios

Se pueden incluir los siguientes objetos de administración en un conjunto de directivas:
- Aplicaciones
- Directivas de configuración de aplicaciones
- Directivas de protección de aplicaciones
- Perfiles de configuración de dispositivos
- Directivas de cumplimiento de dispositivos
- Restricciones de tipo de dispositivo
- Perfiles de Windows Autopilot Deployment
- Página de estado de inscripción

Cuando se crea un conjunto de directivas, se crea una única unidad de asignación y se administran las asociaciones entre los distintos objetos. Un conjunto de directivas será una referencia a los objetos que son externos a él. Cualquier cambio que se realice en los objetos incluidos también afectará al conjunto de directivas. Después de crear un conjunto de directivas, puede ver y editar repetidamente sus objetos y asignaciones. 

> [!NOTE]
> Los conjuntos de directivas admiten configuraciones de Windows, Android, macOS e iOS, y se pueden asignar entre plataformas.

## <a name="how-to-create-a-policy-set"></a>Cómo crear un conjunto de directivas

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Conjuntos de directivas** > **Conjuntos de directivas** > **Crear**.
3. En la página **Datos básicos**, agregue los siguientes valores:
    - **Nombre del conjunto de directivas**: indique un nombre para este conjunto de directivas.
    - **Descripción**: opcionalmente, especifique una descripción del conjunto de directivas.
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. Haga clic en **Siguiente: Administración de aplicaciones**.<br>
   En la página **Administración de aplicaciones** puede decidir si quiere [agregar aplicaciones](~/apps/apps-add.md), [directivas de configuración de aplicaciones](~/apps/app-configuration-policies-overview.md) y [directivas de protección de aplicaciones](~/apps/app-protection-policy.md) al conjunto de directivas. Para más información sobre cómo administrar aplicaciones, vea [¿Qué es la administración de aplicaciones de Microsoft Intune?](~/apps/app-management.md) 
5. Haga clic en **Siguiente: Administración de dispositivos**.<br>
   En la página **Administración de dispositivos** puede agregar objetos de administración de dispositivos al conjunto de directivas, como [perfiles de configuración de dispositivos](~/configuration/device-profiles.md) y [directivas de cumplimiento de dispositivos](~/protect/device-compliance-get-started.md). Asegúrese de incluir todos los objetos asociados, como otras directivas, certificados y perfiles de línea de base de seguridad.
6. Haga clic en **Siguiente: Inscripción de dispositivos**.<br>
   En la página **Inscripción de dispositivos** puede agregar objetos de inscripción de dispositivos al conjunto de directivas, como [restricciones de tipo de dispositivo](~/enrollment/enrollment-restrictions-set.md), [perfiles de Windows Autopilot Deployment](~/enrollment/enrollment-autopilot.md) y [perfiles de página de estado de la inscripción](~/enrollment/windows-enrollment-status.md).
7. Haga clic en **Siguiente: Asignaciones**.<br>
   En la página **Asignaciones** puede asignar el conjunto de directivas a usuarios y dispositivos. Es importante saber que un conjunto de directivas se puede asignar a un dispositivo, independientemente de si dicho dispositivo está administrado o no por Intune.
8. Haga clic en **Siguiente: Revisar + crear** para revisar los valores especificados en el perfil.
9. Cuando haya terminado, haga clic en **Crear** para crear el conjunto de directivas en Intune. 

## <a name="policy-sets-known-issues"></a>Problemas conocidos de los conjuntos de directivas

Los conjuntos de directivas, novedad en la versión 1910, presentan los siguientes problemas conocidos.

- Al crear un conjunto de directivas, si un administrador con ámbito intenta crear un conjunto de directivas sin seleccionar ninguna etiqueta de ámbito, cuando llegue a la página **Revisar + crear**, se producirá un error de validación y se mostrará un error en la barra de estado. El administrador deberá cambiar a otra página en el proceso y, tras ello, regresar a la página **Revisar + crear**. Esto hará que la opción **Crear** se habilite.  
 
- Actualmente, los conjuntos de directivas admiten los siguientes tipos de aplicaciones:
    - Aplicación de la tienda iOS
    - Aplicación de línea de negocio de iOS
    - Aplicación de línea de negocio de iOS administrada
    - Aplicación de la tienda Android
    - Aplicación de línea de negocio de Android
    - Aplicación de línea de negocio de Android administrada
    - Office 365 ProPlus Suite (Windows 10)
    - Vínculo web
    - Aplicación de iOS integrada
    - Aplicación de Android integrada

- Una asignación de conjunto de directivas de tipo **Todos los usuarios** no se puede establecer en **Perfil de AutoPilot**.

- Los conjuntos de directivas presentan las siguientes restricciones de inscripción y problemas de página de estado de la inscripción:
    - Las restricciones y las páginas de estado de la inscripción no admiten asignaciones de grupos virtuales.
    - Las restricciones y las páginas de estado de la inscripción no admiten asignaciones de grupos de exclusión de manera estricta. 
    - Las restricciones y las páginas de estado de la inscripción emplean una resolución de conflictos basada en prioridades. Las restricciones y las páginas de estado de la inscripción pueden no ser de aplicación en los mismos usuarios que el resto de cargas de un conjunto de directivas si esas restricciones y páginas de estado de la inscripción son el destino de una restricción y una página de estado de inscripción con una mayor prioridad.
    - Las restricciones y las páginas de estado de la inscripción predeterminadas no se pueden agregar a un conjunto de directivas.

- Los tipos de directivas MAM que admiten conjuntos de directivas son los siguientes: 
    - Protección de aplicaciones administradas de destino de MDM de WIP (Windows) MAM 
    - Protección de aplicaciones administradas de destino de iOS MAM
    - Protección de aplicaciones administradas de destino de Android MAM
    - Configuración de aplicaciones administradas de destino de iOS MAM
    - Configuración de aplicaciones administradas de destino de Android MAM

- Los tipos de directivas MAM que no admiten conjuntos de directivas son los siguientes: 
    - Protección de aplicaciones administradas de destino de WIP (Windows) MAM

- MAM procesa las asignaciones de conjuntos de directivas como asignaciones directas en los siguientes tipos de directivas:
    - Protección de aplicaciones administradas de destino de iOS MAM
    - Protección de aplicaciones administradas de destino de Android MAM
    - Configuración de aplicaciones administradas de destino de iOS MAM
    - Configuración de aplicaciones administradas de destino de Android MAM

    Si se agrega una directiva a un conjunto de directivas que está implementado en un grupo, dicho grupo se mostraría como directamente asignado en la carga de trabajo, y no "asignado mediante el conjunto de directivas". En consecuencia, MAM no procesa las eliminaciones de asignaciones de grupos procedentes de conjuntos de directivas.

- MAM no permite realizar implementaciones en grupos virtuales de tipo **Todos los usuarios** y **Todos los dispositivos** de ningún tipo de directiva.

## <a name="next-steps"></a>Pasos siguientes

- [Inscripción de dispositivos en Microsoft Intune](~/enrollment/index.yml).