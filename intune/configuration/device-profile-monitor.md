---
title: Ver perfiles de dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Vea y administre la información del perfil de configuración de dispositivos en Microsoft Intune, vea un gráfico del número de dispositivos asignados a un perfil y qué dispositivos tienen perfiles asignados o implementados. También se puede solucionar problemas con perfiles de configuración de conflictos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4dc349ef7af2683b4dafeaa1cc09f5b7a727e843
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755290"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Supervisar perfiles de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune incluye algunas características para ayudar a supervisar y administrar los perfiles de configuración de dispositivos. Por ejemplo, puede comprobar el estado de un perfil, ver qué dispositivos están asignados y actualizar las propiedades de un perfil.

## <a name="view-existing-profiles"></a>Ver perfiles existentes

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración**.

Se muestran todos los perfiles existentes, se incluye información detallada, como la plataforma, y se indica si el perfil se ha asignado a algún dispositivo.

## <a name="view-details-on-a-profile"></a>Ver detalles de un perfil

Después de crear el perfil de dispositivo, Intune proporciona gráficos. Estos gráficos muestran el estado de un perfil, por ejemplo, si se asignó correctamente a los dispositivos, o si el perfil muestra un conflicto.

1. Seleccione un perfil existente. Por ejemplo, seleccione un perfil de macOS.
2. Seleccione la pestaña **Información general**.

    En el gráfico superior se muestra el número de dispositivos asignados al perfil de dispositivo. Por ejemplo, si el perfil de dispositivo de configuración se aplica a dispositivos macOS, el gráfico muestra el número de dispositivos macOS.

    También muestra el número de dispositivos de otras plataformas que se asignan al mismo perfil de dispositivo. Por ejemplo, muestra el número de dispositivos no macOS.

    ![Ver el número de dispositivos asignados al perfil de dispositivo](./media/device-profile-monitor/device-configuration-profile-graphical-chart.png)

    En el gráfico de la parte inferior se muestra el número de usuarios asignados al perfil de dispositivo. Por ejemplo, si el perfil de dispositivo de configuración se aplica a usuarios de macOS, el gráfico muestra el número de usuarios de macOS.

3. Seleccione el círculo en el gráfico superior. Se abre la opción **Estado del dispositivo**.

    Se muestran los dispositivos asignados al perfil y si el perfil se implementó correctamente. Tenga en cuenta también que solo se muestran los dispositivos con la plataforma concreta (por ejemplo, macOS).

    Cierre los detalles de **Estado del dispositivo**.

4. Seleccione el círculo en el gráfico inferior. Se abre **Estado del usuario**. 

    Se muestran los usuarios asignados al perfil y si el perfil se implementó correctamente. Tenga en cuenta también que solo se muestran los usuarios con la plataforma concreta (por ejemplo, macOS).

    Cierre los detalles de **Estado del usuario**.

5. De nuevo en la lista **Perfiles**, seleccione un perfil específico. También puede cambiar las propiedades existentes:
    - **Propiedades**: cambie el nombre o actualice cualquier configuración existente.
    - **Asignaciones**: incluya o excluya los dispositivos a los que se debe aplicar la directiva. Elija **Grupos seleccionados** para elegir grupos específicos.
    - **Estado del dispositivo**: Se muestran los dispositivos asignados al perfil y si el perfil se implementó correctamente. Puede seleccionar un dispositivo específico para obtener incluso más detalles, incluidas las aplicaciones instaladas.
    - **Estado del usuario**: se enumeran los nombres de usuario con los dispositivos afectados por este perfil, y si el perfil se ha implementado correctamente. Puede seleccionar un usuario específico para obtener incluso más detalles.
    - **Estado por valor**: se filtra el resultado, que muestra la configuración individual dentro del perfil y si la configuración se aplicó correctamente.

## <a name="view-conflicts"></a>Ver conflictos

En **Dispositivos** > **Todos los dispositivos**, puede ver cualquier configuración que cause un conflicto. Cuando hay un conflicto, también verá todos los perfiles de configuración que contienen ese valor. Los administradores pueden usar esta característica para ayudar a solucionar y corregir cualquier discrepancia con los perfiles.

1. En Intune, seleccione **Dispositivos** > **Todos los dispositivos** > seleccione un dispositivo existente en la lista. Un usuario final puede obtener el nombre del dispositivo desde la aplicación Portal de empresa.
2. Seleccione **Configuración del dispositivo**. Se muestran todas las directivas de configuración que se aplican al dispositivo.
3. Seleccione la directiva. Muestra todas las opciones de configuración de la directiva que se aplican al dispositivo. Si un dispositivo tiene como estado **Conflicto**, seleccione esa fila. En la ventana nueva, verá todos los perfiles y los nombres de perfil que tienen la configuración que provoca el conflicto.

Ahora que conoce la configuración que provoca el conflicto y las directivas que incluyen dicha configuración, será más fácil resolver el conflicto. 

## <a name="device-firmware-configuration-interface-profile-reporting"></a>Informes de perfil de Device Firmware Configuration Interface

> [!WARNING]
> En la actualidad se está creando la supervisión de perfiles de DFCI. Aunque DFCI se encuentra en versión preliminar pública, es posible que falten datos de supervisión o que estén incompletos.

Los perfiles de DFCI se notifican según la configuración, al igual que otros perfiles de configuración de dispositivos. En función de la compatibilidad del fabricante con DFCI, es posible que no se apliquen algunas opciones de configuración.

Con la configuración del perfil de DFCI, es posible que vea los estados siguientes:

- **Conforme**: este estado muestra cuándo un valor de configuración del perfil coincide con la configuración del dispositivo. Este estado se puede producir en los escenarios siguientes:

  - El perfil de DFCI ha establecido correctamente la configuración en el perfil.
  - El dispositivo no tiene la característica de hardware controlada por la configuración y la configuración del perfil es **Deshabilitado**.
  - UEFI no permite que DFCI deshabilite la característica y la configuración del perfil es **Habilitado**.
  - El dispositivo carece del hardware para deshabilitar la característica y la configuración del perfil es **Habilitado**.

- **No aplicable**: este estado muestra cuándo un valor de configuración del perfil está **Habilitado** y no se encuentra la configuración coincidente en el dispositivo. Este estado se puede producir si el hardware del dispositivo no tiene la característica.

- **No conforme**: este estado muestra cuándo un valor de configuración del perfil no coincide con la configuración del dispositivo. Este estado se puede producir en los escenarios siguientes:

  - UEFI no permite que DFCI deshabilite una característica y la configuración del perfil es **Deshabilitado**.
  - El dispositivo carece del hardware para deshabilitar la característica y la configuración del perfil es **Deshabilitado**.
  - El dispositivo no tiene la versión del firmware de DFCI más reciente.
  - DFCI se ha deshabilitado antes de inscribirse en Intune mediante un control "de no participación" local en el menú de UEFI.
  - El dispositivo se ha inscrito en Intune fuera de la inscripción de Autopilot.
  - El dispositivo no se ha registrado en Autopilot mediante un CSP de Microsoft, o bien el OEM lo ha registrado directamente.

## <a name="next-steps"></a>Pasos siguientes

[Preguntas comunes, problemas y resoluciones con perfiles de dispositivos](device-profile-troubleshoot.md)  
[Solución de problemas de directivas y perfiles en Intune](troubleshoot-policies-in-microsoft-intune.md)
