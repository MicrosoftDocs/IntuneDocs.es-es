---
title: 'Configuración de directivas de actualización de software de iOS/iPadOS en Microsoft Intune: Azure | Microsoft Docs'
description: En Microsoft Intune, cree o agregue una directiva de configuración para restringir cuándo se van a instalar automáticamente actualizaciones de software en los dispositivos iOS/iPadOS. Puede elegir la fecha y hora en la que no se instalarán las actualizaciones. También puede asignar esta directiva a grupos, usuarios o dispositivos y comprobar si hay errores de instalación.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77d4a90bb2eaa8434ff9c05362dcb0d7cb270651
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576151"
---
# <a name="add-iosipados-software-update-policies-in-intune"></a>Adición de directivas de actualización de software de iOS/iPadOS en Intune

Las directivas de actualización de software permiten forzar a los dispositivos iOS/iPadOS supervisados a instalar automáticamente las actualizaciones del sistema operativo. Los dispositivos supervisados son aquellos que se han inscrito mediante Apple Business Manager o Apple School Manager. Al configurar una directiva para implementar actualizaciones, puede:

- Elegir implementar la *última actualización* disponible, o bien implementar una actualización anterior por el número de versión de actualización si no quiere implementar la actualización más reciente. Si decide implementar una actualización anterior, también debe establecer una directiva de configuración de dispositivos para restringir la visibilidad de las actualizaciones de software.
- Especificar una programación que determine cuándo se instala la actualización. Las programaciones pueden ser tan sencillas como la instalación de actualizaciones la próxima vez que se registre el dispositivo, o bien crear intervalos de fecha y hora durante los que se puedan instalar las actualizaciones o bloquear su instalación.

Esta característica se aplica a:

- iOS 10.3 y versiones posteriores (supervisado)

De forma predeterminada, los dispositivos se registran con Intune aproximadamente cada ocho horas. Si hay una actualización disponible a través de una directiva de actualización, el dispositivo descarga la actualización. Después, el dispositivo instala la actualización la próxima vez que se registre dentro de la configuración de programación. Aunque el proceso de actualización normalmente no implica ninguna interacción del usuario, si el dispositivo tiene un código de acceso, el usuario tendrá que escribirlo para iniciar una actualización de software. Los perfiles no impiden que los usuarios actualicen el sistema operativo de forma manual. Se puede impedir que los usuarios actualicen el sistema operativo de forma manual con una directiva de configuración de dispositivos para restringir la visibilidad de las actualizaciones de software.

## <a name="configure-the-policy"></a>Configuración de la directiva

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Directivas de actualización para iOS/iPadOS** > **Crear perfil**.
3. En la pestaña **Datos básicos**, indique un nombre para la directiva y una descripción (opcional) y, después, seleccione **Siguiente**.

   ![Pestaña Datos básicos](./media/software-updates-ios/basics-tab.png)

4. En la pestaña **Actualizar configuración de directiva**, configure las opciones siguientes:

   1. **Selección de la versión para instalar**. Puede elegir entre:

      - *Actualización más reciente*: esto implementa la actualización más reciente publicada para iOS/iPadOS.
      - Cualquier versión anterior que esté disponible en el cuadro desplegable. Si selecciona una versión anterior, también debe implementar una directiva de configuración de dispositivo para retrasar la visibilidad de las actualizaciones de software.

   2. **Tipo de programación**: configure la programación para esta directiva:

      - *Actualizar en la siguiente sincronización*: la actualización se instala en el dispositivo la próxima vez que se sincronice con Intune. Esta es la opción más sencilla y no tiene ninguna configuración adicional.
      - *Actualizar durante la hora programada*: configure una o más ventanas de tiempo durante las cuales la actualización se instalará tras la sincronización.
      - *Actualizar fuera de la hora programada*: configure una o más ventanas de tiempo durante las cuales las actualizaciones no se instalarán tras la sincronización.

   3. **Programación semanal**: si elige un tipo de programación distinto de *Actualizar en la siguiente sincronización*, configure las opciones siguientes:

      ![Ejemplo de selección de actualización durante la hora programada](./media/software-updates-ios/scheduled-time.png)

      - **Zona horaria**: elija una zona horaria.
      - **Período de tiempo**: defina uno o varios bloques de tiempo que restrinjan la instalación de las actualizaciones. El efecto de las opciones siguientes depende del tipo de programación seleccionado. Si se usa un día de inicio y un día de finalización, se admiten bloqueos nocturnos. Las opciones son:

        - **Día de inicio**: elija el día en que se inicia el período de programación.
        - **Hora de inicio**: elija la hora del día a la que se inicia el período de programación. Por ejemplo, si selecciona 5:00 y tiene un tipo de programación *Actualizar durante la hora programada*, se podrá empezar a instalar las actualizaciones a las 5:00. Si elige un tipo de programación *Actualización fuera de una hora programada*, las 5:00 serán el inicio de un período de tiempo durante el que no se pueden instalar las actualizaciones.
        - **Día de finalización**: elija el día en que finaliza el período de programación.
        - **Hora de finalización**: elija la hora del día a la que se detiene el período de programación. Por ejemplo, si selecciona 1:00 y tiene un tipo de programación *Actualizar durante la hora programada*, a la 1:00 ya no se podrán instalar las actualizaciones. Si elige un tipo de programación *Actualización fuera de una hora programada*, la 1:00 será el inicio de un período de tiempo durante el que se pueden instalar las actualizaciones.

       Si no configura horas de inicio o finalización, la configuración no tendrá ninguna restricción y las actualizaciones se podrán instalar en cualquier momento.  

       > [!NOTE]
       > Para retrasar la visibilidad de las actualizaciones de software durante un período de tiempo específico en los dispositivos iOS/iPadOS supervisados, establezca esta configuración en [Restricciones de dispositivos](../configuration/device-restrictions-ios.md#general). Las directivas de actualización de software invalidan cualquier restricción de dispositivo. Cuando se establece una restricción y una directiva de actualización de software para retrasar la visibilidad de las actualizaciones de software, el dispositivo fuerza una actualización de software de acuerdo con la directiva. La restricción se aplica para que los usuarios no vean la opción de actualizar ellos mismos el dispositivo, y la actualización se inserta en función de lo definido por la directiva de actualización de iOS.

   Después de configurar *Actualizar configuración de directiva*, seleccione **Siguiente**.

5. En la pestaña **Etiquetas de ámbito**, seleccione **+ Seleccionar etiquetas de ámbito** para abrir el panel *Seleccionar etiquetas* si quiere aplicarlas a la directiva de actualización.

   - En el panel **Seleccionar etiquetas**, elija una o más etiquetas y, después, haga clic en **Seleccionar** para agregarlas a la directiva y volver al panel *Etiquetas de ámbito*.

   Cuando esté listo, seleccione **Siguiente** para avanzar a *Asignaciones*.

6. En la pestaña **Asignaciones**, seleccione **+ Seleccionar grupos para incluir** y, después, asigne la directiva de actualización a uno o varios grupos. Use **+ Seleccionar grupos para excluir** para ajustar la asignación. Cuando esté listo, seleccione **Siguiente** para continuar.

   Se evalúa la comprobación de actualizaciones por parte de los dispositivos usados por los usuarios a los que se destina la directiva. Esta directiva también es compatible con los dispositivos sin usuario.

7. En la pestaña **Revisar y crear**, revise la configuración y seleccione **Crear** cuando esté listo para guardar la directiva de actualización de iOS/iPadOS. La nueva directiva se muestra en la lista de directivas de actualización de iOS/iPadOS.

Para obtener instrucciones del equipo de soporte técnico de Intune, vea [Delay visibility of software updates in Intune for supervised devices](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753) (Retrasar la visibilidad de las actualizaciones de software en Intune para dispositivos supervisados).

> [!NOTE]
> MDM de Apple no permite forzar a un dispositivo a instalar las actualizaciones en una hora o fecha determinada. No puede usar las directivas de actualización de software de Intune para cambiar a una versión anterior del sistema operativo en un dispositivo.

## <a name="edit-a-policy"></a>Editar una directiva

Puede editar una directiva existente, incluso cambiar los tiempos restringidos:

1. Seleccione **Dispositivos** > **Directivas de actualización para iOS**. Seleccione la directiva que quiere editar.

2. Mientras ve las **Propiedades** de las directivas, seleccione la opción **Editar** de la página de directiva que quiera modificar.

   ![Editar una directiva](./media/software-updates-ios/edit-policy.png)

3. Después de introducir un cambio, seleccione **Revisar + guardar** > **Guardar** para guardar las modificaciones y vuelva a las *Propiedades* de las directivas.

> [!NOTE]
> Si tanto la **Hora de inicio** como la **Hora de finalización** se establecen a las 12:00, Intune no comprueba las restricciones sobre cuándo instalar las actualizaciones. Esto significa que se omitirá cualquier configuración que tenga para **Seleccionar las horas en las que se impide la instalación de actualizaciones** y podrá instalar actualizaciones en cualquier momento.

## <a name="monitor-device-installation-failures"></a>Supervisión de errores de instalación de dispositivos

<!-- 1352223 -->
En **Actualizaciones de software** > **Errores de instalación para dispositivos iOS** se muestra una lista de los dispositivos iOS/iPadOS supervisados a los que se destina una directiva de actualización, que han intentado una actualización y que no se han podido actualizar. Para cada dispositivo, puede ver el estado por el que el dispositivo no se ha actualizado automáticamente. Los dispositivos actualizados y que estén en buen estado no se muestran en la lista. Los dispositivos "actualizados" incluyen la actualización más reciente que el propio dispositivo puede admitir.

## <a name="next-steps"></a>Pasos siguientes

[Supervise el estado](../configuration/device-profile-monitor.md).
