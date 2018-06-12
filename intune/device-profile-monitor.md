---
title: Ver perfiles de dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Vea y administre la información del perfil de configuración de dispositivos en Microsoft Intune, y vea un gráfico del número de dispositivos asignados a un perfil y qué dispositivos tienen perfiles asignados o implementados.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bffb6832200379fca0221d8718afdebe06163980
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744795"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Supervisar perfiles de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune incluye algunas características en Azure Portal para ayudar a supervisar y administrar los perfiles de configuración de dispositivos. Por ejemplo, puede comprobar el estado de un perfil, ver qué dispositivos están asignados y actualizar las propiedades de un perfil.

## <a name="view-existing-profiles"></a>Ver perfiles existentes

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo** > **Perfiles**.

Se muestran todos los perfiles existentes, y se incluye información detallada, como la plataforma y si el perfil se ha asignado a algún dispositivo.

## <a name="view-details-on-a-profile"></a>Ver detalles de un perfil

Después de crear el perfil de dispositivo, Intune proporciona gráficos. Estos gráficos muestran el estado de un perfil, por ejemplo, si se asignó correctamente a los dispositivos, o si el perfil muestra un conflicto.

1. Seleccione un perfil existente. Por ejemplo, seleccione un perfil de macOS.
2. Seleccione la pestaña **Información general**.

    El gráfico superior muestra el número de dispositivos asignados al perfil de dispositivo específico. Por ejemplo, si el perfil de dispositivo de configuración se aplica a dispositivos macOS, el gráfico muestra el número de dispositivos macOS.

    También muestra el número de dispositivos de otras plataformas que se asignan al mismo perfil de dispositivo. Por ejemplo, muestra el número de dispositivos no macOS.

    ![Ver el número de dispositivos asignados al perfil de dispositivo](./media/device-configuration-profile-graphical-chart.png)

    El gráfico inferior muestra el número de usuarios asignados al perfil de dispositivo específico. Por ejemplo, si el perfil de dispositivo de configuración se aplica a usuarios de macOS, el gráfico muestra el número de usuarios de macOS.

3. Seleccione el círculo en el gráfico superior. Se abre la opción **Estado del dispositivo**.

    Se muestran los dispositivos asignados al perfil y si el perfil se implementó correctamente. Tenga en cuenta también que solo se muestran los dispositivos con la plataforma concreta (por ejemplo, macOS).

    Cierre los detalles de **Estado del dispositivo**.

4. Seleccione el círculo en el gráfico inferior. Se abre **Estado del usuario**. 

    Se muestran los usuarios asignados al perfil y si el perfil se implementó correctamente. Tenga en cuenta también que solo se muestran los usuarios con la plataforma concreta (por ejemplo, macOS).

    Cierre los detalles de **Estado del usuario**.

5. De nuevo en la lista **Perfiles**, seleccione un perfil específico. También puede cambiar las propiedades existentes:
  - **Propiedades**: cambie el nombre o actualice cualquier configuración existente.
  - **Asignaciones**: incluya o excluya los dispositivos a los que se debe aplicar la directiva. Elija **Grupos seleccionados** para elegir grupos específicos.
  - **Estado del dispositivo**: se muestran los dispositivos asignados al perfil y si el perfil se implementó correctamente. Puede seleccionar un dispositivo específico para obtener incluso más detalles, incluidas las aplicaciones instaladas.
  - **Estado del usuario**: se muestran los nombres de usuario con los dispositivos afectados por este perfil, y si el perfil se implementó correctamente. Puede seleccionar un usuario específico para obtener incluso más detalles.
  - **Estado por valor**: se filtra el resultado, que muestra la configuración individual dentro del perfil y si la configuración se aplicó correctamente.

## <a name="next-steps"></a>Pasos siguientes
[Asignación de perfiles de usuario y dispositivo](device-profile-assign.md)  
[Problemas comunes y resoluciones con perfiles de dispositivo](device-profile-troubleshoot.md)