---
title: 'Configuración de directivas de actualización de software de iOS en Microsoft Intune: Azure | Microsoft Docs'
description: En Microsoft Intune, cree o agregue una directiva de configuración para restringir cuándo se instalan automáticamente las actualizaciones de software en los dispositivos iOS administrados o supervisados por Intune. Puede elegir la fecha y hora en la que no se instalarán las actualizaciones. También puede asignar esta directiva a grupos, usuarios o dispositivos y comprobar si hay errores de instalación.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: de73aa069765ce75068781674ff24d097346cdba
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61505937"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Adición de directivas de actualización de software de iOS en Intune

Las directivas de actualización de software permiten forzar a los dispositivos iOS supervisados a instalar automáticamente la actualización de sistema operativo más reciente disponible. Al configurar una directiva, puede agregar las horas y los días en los que no quiere que los dispositivos instalen una actualización. 

Esta característica se aplica a:

- iOS 10.3 y versiones posteriores (supervisado)

El dispositivo se registra con Intune aproximadamente cada ocho horas. Si hay una actualización disponible, fuera de un período restringido, el dispositivo descarga e instala la actualización de sistema operativo más reciente. No se necesita ninguna interacción del usuario para actualizar el dispositivo. La directiva no impide que un usuario actualice el sistema operativo de forma manual.

## <a name="configure-the-policy"></a>Configurar la directiva

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Seleccione **Actualizaciones de software** > **Directivas de actualización para iOS** > **Crear**.
3. Escriba los valores siguientes:

    - **Nombre**: Escriba un nombre para la directiva de actualizaciones de software. Por ejemplo, escriba `iOS restricted update times`.
    - **Descripción**: Escriba una descripción para la directiva. Esta configuración es opcional pero recomendada.

4. Seleccione **Configuración > Configurar**. Escriba los valores siguientes:

    - **Seleccionar las horas en las que se impide la instalación de actualizaciones**: Especifique un período de tiempo limitado cuando las actualizaciones no se instalan forzosamente. 
      - No se admiten los bloqueos nocturnos y podrían no funcionar. Por ejemplo, no configure una directiva con una *Hora de inicio* de 20:00 y una *Hora de finalización* de 6:00.
      - Una directiva que empieza a las 12:00 y termina a las 12:00 se evalúa como 0 horas en vez de 24 horas, por lo que no se aplica ninguna restricción.

      Al establecer el período de tiempo limitado, especifique los detalles siguientes:

      - **Días**: elija los días de la semana en los que no se instalarán actualizaciones. Por ejemplo, marque el lunes, el miércoles y el viernes para impedir que las actualizaciones se instalen en estos días.
      - **Zona horaria**: elija una zona horaria.
      - **Hora de inicio**: elija la hora de inicio del período de tiempo restringido. Por ejemplo, escriba 5:00 para que las actualizaciones no se instalen a partir de las 5:00.
      - **Hora de finalización**: elija la hora de finalización del período de tiempo restringido. Por ejemplo, escriba 1:00 para que las actualizaciones no se instalen a partir de la 1:00.

    - **Retrasar la visibilidad de las actualizaciones de software para los usuarios finales sin cambios en las actualizaciones programadas (días)**: 

      **Esta opción se movió a [Restricciones de dispositivos](device-restrictions-ios.md#general). Se quitará de esta ubicación en el portal**. Durante un breve período, las directivas existentes se pueden cambiar aquí. Después de un mes, este valor se quitará de las directivas existentes.

      Para limitar el impacto, se recomienda:
        - Quitar la directiva existente de esta ubicación en el portal.
        - Crear una nueva [directiva de restricción de dispositivo](device-restrictions-ios.md#general).
        - Tener como destino los mismos usuarios que la directiva original.

      Si hay un conflicto, este valor no hace nada *a menos que* los dos valores sean idénticos. Para evitar conflictos, asegúrese de cambiar o quitar la directiva existente de esta ubicación en el portal.
      > [! Importante]  
      > Una directiva que tiene una *Hora de inicio* y una *Hora de finalización* establecida en las 12:00 se evalúa como 0 horas en vez de 24 horas. El resultado es que no se aplica ninguna restricción.  

5. Seleccione **Aceptar** > **Crear** para guardar los cambios y crear la directiva.

El perfil se crea y se muestra en la lista de directivas.

Para obtener instrucciones del equipo de soporte técnico de Intune, vea [Delay visibility of software updates in Intune for supervised devices](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753) (Retrasar la visibilidad de las actualizaciones de software en Intune para dispositivos supervisados).

> [!NOTE]
> MDM de Apple no permite forzar a un dispositivo a instalar las actualizaciones en una hora o fecha determinada.

## <a name="change-the-restricted-times-for-the-policy"></a>Cambio de los períodos restringidos de la directiva

1. En **Actualizaciones de Software**, seleccione **Directivas de actualización para iOS**.
2. Elija una directiva existente > **Propiedades**.
3. Actualice la hora restringida:

    1. Seleccione los días de la semana.
    2. Elija la zona horaria en la que se aplica esta directiva.
    3. Escriba la hora de inicio y de finalización de las horas incluidas en la lista de bloqueados.

    > [!NOTE]
    > Si tanto la **Hora de inicio** como la **Hora de finalización** se establecen a las 12:00, Intune no comprueba las restricciones sobre cuándo instalar las actualizaciones. Esto significa que se omitirá cualquier configuración que tenga para **Seleccionar las horas en las que se impide la instalación de actualizaciones** y podrá instalar actualizaciones en cualquier momento.  

## <a name="assign-the-policy-to-users"></a>Asignar la directiva a los usuarios

Las directivas existentes se asignan a grupos, usuarios o dispositivos. Cuando se asigna, la directiva se aplica.

1. En **Actualizaciones de Software**, seleccione **Directivas de actualización para iOS**.
2. Elija una directiva existente > **Asignaciones**. 
3. Seleccione los grupos, usuarios o dispositivos de Azure Active Directory que se van a incluir o excluir de la directiva.
4. Haga clic en **Guardar** para implementar la directiva en los usuarios.

Se evalúa la comprobación de actualizaciones por parte de los dispositivos usados por los usuarios a los que se destina la directiva. Esta directiva también es compatible con los dispositivos sin usuario.

## <a name="monitor-device-installation-failures"></a>Supervisión de errores de instalación de dispositivos
<!-- 1352223 -->
En **Actualizaciones de software** > **Errores de instalación para dispositivos iOS** se muestra una lista de los dispositivos iOS supervisados a los que se destina una directiva de actualización, que han intentado una actualización y que no se pudieron actualizar. Para cada dispositivo, puede ver el estado por el que el dispositivo no se ha actualizado automáticamente. Los dispositivos actualizados y que estén en buen estado no se muestran en la lista. Los dispositivos "actualizados" incluyen la actualización más reciente que el propio dispositivo puede admitir.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
