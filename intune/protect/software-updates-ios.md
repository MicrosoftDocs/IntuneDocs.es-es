---
title: 'Configuración de directivas de actualización de software de iOS en Microsoft Intune: Azure | Microsoft Docs'
description: En Microsoft Intune, cree o agregue una directiva de configuración para restringir cuándo se van a instalar automáticamente actualizaciones de software en los dispositivos iOS. Puede elegir la fecha y hora en la que no se instalarán las actualizaciones. También puede asignar esta directiva a grupos, usuarios o dispositivos y comprobar si hay errores de instalación.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb146fdee7a1d7d770575334eeed84f73cda8894
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207492"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Adición de directivas de actualización de software de iOS en Intune

Las directivas de actualización de software permiten forzar a los dispositivos iOS supervisados a instalar automáticamente la actualización de sistema operativo más reciente disponible. Al configurar una directiva, puede agregar las horas y los días en los que no quiere que los dispositivos instalen una actualización.

Esta característica se aplica a:

- iOS 10.3 y versiones posteriores (supervisado)

El dispositivo se registra con Intune aproximadamente cada ocho horas. Si hay disponible una actualización, el dispositivo la descarga e instala, excepto en los tiempos restringidos. Aunque el proceso de actualización no implica normalmente ninguna interacción del usuario, si el dispositivo tiene un código de acceso, el usuario deberá escribirlo para iniciar una actualización de software. Esto se aplica a iOS 10.3 y versiones posteriores. La directiva no impide que un usuario actualice el sistema operativo de forma manual.

## <a name="configure-the-policy"></a>Configuración de la directiva

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Directivas de actualización para iOS** > **Crear**.
3. En la pestaña **Datos básicos**, indique un nombre para la directiva y una descripción (opcional) y, después, seleccione **Siguiente**.

   ![Pestaña Datos básicos](./media/software-updates-ios/basics-tab.png) 

4. En la pestaña **Actualizar configuración de directiva**, especifique un período de tiempo limitado cuando las actualizaciones no se instalan forzosamente.  
   - No se admiten los bloqueos nocturnos y podrían no funcionar. Por ejemplo, no configure una directiva con una *Hora de inicio* de 20:00 y una *Hora de finalización* de 6:00.
   - Una directiva que empieza a las 12:00 y termina a las 12:00 se evalúa como 0 horas en vez de 24 horas. Esta configuración no aplica ninguna restricción.

   Al establecer el período de tiempo limitado, especifique los detalles siguientes:

   - **Días**: elija los días de la semana en los que no se instalarán actualizaciones. Por ejemplo, marque el lunes, el miércoles y el viernes para impedir que las actualizaciones se instalen en estos días.
   - **Zona horaria**: elija una zona horaria.
   - **Hora de inicio**: elija la hora de inicio del período de tiempo restringido. Por ejemplo, escriba 5:00 para que las actualizaciones no se instalen a partir de las 5:00.
   - **Hora de finalización**: elija la hora de finalización del período de tiempo restringido. Por ejemplo, escriba 1:00 para que las actualizaciones no se instalen a partir de la 1:00.
  
   > [!IMPORTANT]  
   > Una directiva que tiene una *Hora de inicio* y una *Hora de finalización* establecida en las 12:00 se evalúa como 0 horas en vez de 24 horas. El resultado es que no se aplica ninguna restricción.  
    
   Para retrasar la visibilidad de las actualizaciones de software durante un período de tiempo específico en sus dispositivos iOS supervisados, establezca esta configuración en [Restricciones de dispositivos](../configuration/device-restrictions-ios.md#general). Las directivas de actualización de software invalidan cualquier restricción de dispositivo. Cuando se establece una restricción y una directiva de actualización de software para retrasar la visibilidad de las actualizaciones de software, el dispositivo fuerza una actualización de software de acuerdo con la directiva. La restricción se aplica para que los usuarios no vean la opción para actualizar ellos mismos el dispositivo, y la actualización se inserta en el primer período de tiempo definido por la directiva de actualización de iOS.

   Después de configurar *Actualizar configuración de directiva*, seleccione **Siguiente**. 

5. En la pestaña **Etiquetas de ámbito**, seleccione **+ Seleccionar etiquetas de ámbito** para abrir el panel *Seleccionar etiquetas* si quiere aplicarlas a la directiva de actualización.
   
   - En el panel **Seleccionar etiquetas**, elija una o más etiquetas y, después, haga clic en **Seleccionar** para agregarlas a la directiva y volver al panel *Etiquetas de ámbito*.  

   Cuando esté listo, seleccione **Siguiente** para avanzar a *Asignaciones*.

6. En la pestaña **Asignaciones**, seleccione **+ Seleccionar grupos para incluir** y, después, asigne la directiva de actualización a uno o varios grupos. Use **+ Seleccionar grupos para excluir** para ajustar la asignación. Cuando esté listo, seleccione **Siguiente** para continuar. 

   Se evalúa la comprobación de actualizaciones por parte de los dispositivos usados por los usuarios a los que se destina la directiva. Esta directiva también es compatible con los dispositivos sin usuario.

7. En la pestaña **Revisar y crear**, revise la configuración y seleccione **Crear** cuando esté listo para guardar la directiva de actualización de iOS. La nueva directiva se muestra en la lista de directivas de actualización de iOS.


Para obtener instrucciones del equipo de soporte técnico de Intune, vea [Delay visibility of software updates in Intune for supervised devices](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753) (Retrasar la visibilidad de las actualizaciones de software en Intune para dispositivos supervisados).

> [!NOTE]
> MDM de Apple no permite forzar a un dispositivo a instalar las actualizaciones en una hora o fecha determinada.

## <a name="edit-a-policy"></a>Editar una directiva
Puede editar una directiva existente, incluso cambiar los tiempos restringidos:

1. Seleccione **Dispositivos** > **Directivas de actualización para iOS**. Seleccione la directiva que quiere editar.

2. Mientras ve las **Propiedades** de las directivas, seleccione la opción **Editar** de la página de directiva que quiera modificar.  
   ![Edición de una directiva](./media/software-updates-ios/edit-policy.png)   

3. Después de introducir un cambio, seleccione **Revisar + guardar** > **Guardar** para guardar las modificaciones y vuelva a las *Propiedades* de las directivas.  
 
> [!NOTE]
> Si tanto la **Hora de inicio** como la **Hora de finalización** se establecen a las 12:00, Intune no comprueba las restricciones sobre cuándo instalar las actualizaciones. Esto significa que se omitirá cualquier configuración que tenga para **Seleccionar las horas en las que se impide la instalación de actualizaciones** y podrá instalar actualizaciones en cualquier momento.  


## <a name="monitor-device-installation-failures"></a>Supervisión de errores de instalación de dispositivos
<!-- 1352223 -->
En **Actualizaciones de software** > **Errores de instalación para dispositivos iOS** se muestra una lista de los dispositivos iOS supervisados a los que se destina una directiva de actualización, que han intentado una actualización y que no se pudieron actualizar. Para cada dispositivo, puede ver el estado por el que el dispositivo no se ha actualizado automáticamente. Los dispositivos actualizados y que estén en buen estado no se muestran en la lista. Los dispositivos "actualizados" incluyen la actualización más reciente que el propio dispositivo puede admitir.

## <a name="next-steps"></a>Pasos siguientes

[Supervise el estado](../configuration/device-profile-monitor.md).
