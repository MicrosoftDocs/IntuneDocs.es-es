---
title: Configuración de Windows Update para empresas en Microsoft Intune - Azure | Microsoft Docs
description: Actualizar la configuración de las actualizaciones de software en un perfil para crear un anillo de actualización, revisar el cumplimiento y pausar las actualizaciones en la configuración de Windows Update para empresas con Microsoft Intune en dispositivos Windows 10.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d34e44c6e046ddbc9b47bbe90900f5992df9e85
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584553"
---
# <a name="manage-software-updates-in-intune"></a>Administrar las actualizaciones de software en Intune

Use Intune para definir los anillos de actualización que especifican cómo y cuándo Windows como servicio actualiza los dispositivos de Windows 10. Los anillos de actualización son directivas que debe asignar a grupos de dispositivos. Gracias a ellos, puede crear una estrategia de actualización que refleje sus necesidades empresariales. Para obtener más información, consulte [Administrar actualizaciones con Windows Update para empresas](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

A partir de Windows 10, todas las nuevas actualizaciones de calidad y de características incluyen las actualizaciones anteriores. Siempre que tenga instalada la más reciente sabrá que sus dispositivos Windows 10 están actualizados. A diferencia de las versiones anteriores de Windows, ahora debe instalar la actualización completa en lugar de una parte.


Con Windows Update para empresas puede simplificar la experiencia de administración de actualizaciones. No es necesario que apruebe actualizaciones concretas para grupos de dispositivos. Para administrar el riesgo en sus entornos, puede configurar una estrategia de implementación de actualizaciones Intune ofrece la posibilidad de [configurar las actualizaciones](../windows-update-settings.md) en los dispositivos y de aplazar su instalación. Intune no almacena las actualizaciones, sino únicamente la asignación de las directivas de actualización. Los dispositivos acceden a Windows Update directamente para las actualizaciones. Esta colección de valores que se configura cuando se instalan las actualizaciones de Windows 10 se llama *anillo de actualización de Windows 10*.

Los anillos de actualización de Windows 10 admiten las [etiquetas de ámbito](../fundamentals/scope-tags.md). Puede usar etiquetas de ámbito con los anillos de actualización para filtrar y administrar los conjuntos de configuraciones que usa.

## <a name="prerequisites"></a>Requisitos previos  

Deben cumplirse los requisitos previos siguientes para usar las actualizaciones de Windows para dispositivos Windows 10 en Intune.  

- Los equipos con Windows 10 deben ejecutar al menos Windows 10 Pro con la actualización de aniversario de Windows o posterior (versión 1607 o posterior).
- Windows Update admite estas ediciones de Windows 10:
  - Windows 10
  - Windows 10 Team (para dispositivos Surface Hub)
  - Windows Holographic for Business  

    Windows Holographic for Business admite un subconjunto de configuraciones para las actualizaciones de Windows, como:
    - **Comportamiento de las actualizaciones automáticas**
    - **Actualizaciones de productos de Microsoft**
    - **Canal de servicio**: admite las opciones **Canal semianual** y **Canal semianual (dirigido)** . Para más información, consulte [Administración de Windows Holographic](../fundamentals/windows-holographic-for-business.md).  

    > [!NOTE]  
    > **Versiones y ediciones no compatibles**:
    > - Windows 10 Mobile  
    > - Windows 10 Enterprise LTSC. Actualmente, Windows Update para empresas (WUfB) no admite versiones de *canal de servicio a largo plazo*. Planee usar métodos de revisión alternativos, como WSUS o Configuration Manager.  

- En los dispositivos Windows, **Comentarios y diagnósticos** > **Datos de uso y diagnóstico** debe establecerse en **Básico**, **Mejorado** o **Total**.  

  Puede configurar la opción *Datos de diagnóstico y uso* de los dispositivos Windows 10 de manera manual o usar un perfil de restricción de dispositivos Intune para Windows 10 o versiones posteriores. Si usa un perfil de restricción de dispositivos, establezca la [configuración de restricción de dispositivos](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) de **Compartir los datos de uso** al menos en **Básico**. Esta configuración se encuentra en la categoría **Informes y telemetría** cuando se configura una directiva de restricción de dispositivos para Windows 10 o versiones posteriores.

  Para obtener más información sobre los perfiles de dispositivo, vea [Configuración de restricciones de dispositivos en Microsoft Intune](../configuration/device-restrictions-configure.md).  

- Si usa el Portal de Azure clásico, [migre la configuración a Azure Portal](#migrate-update-settings-to-the-azure-portal).  


## <a name="create-and-assign-update-rings"></a>Crear y asignar anillos de actualización

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y, después, seleccione **Actualizaciones de software** > **Anillos de actualización de Windows 10** > **Crear**.  

2. En la pestaña Datos básicos, indique un nombre, una descripción (opcional) y, después, seleccione **Siguiente**.  

   ![Flujo de trabajo de creación de un anillo de actualización de Windows 10](./media/windows-update-for-business-configure/basics-tab.png)

3. En la pestaña **Configuración del anillo de actualización**, configure los valores según sus necesidades empresariales. Para información sobre la configuración disponible, consulte [Configuración de Windows Update](windows-update-settings.md). Después de configurar las opciones *Actualizar* y *Experiencia del usuario*, seleccione **Siguiente**.  

4. En la pestaña **Etiquetas de ámbito**, seleccione **+ Seleccionar etiquetas de ámbito** para abrir el panel *Seleccionar etiquetas* si quiere aplicarlas al anillo de actualización.  

   - En el panel **Seleccionar etiquetas**, elija una o más etiquetas y, después, haga clic en **Seleccionar** para agregarlas al anillo de actualización y volver al panel *Etiquetas de ámbito*.  

   Cuando esté listo, seleccione **Siguiente** para avanzar a *Asignaciones*. 

5. En la pestaña **Asignaciones**, seleccione **+ Seleccionar grupos para incluir** y, después, asigne el anillo de actualización a uno o varios grupos. Use **+ Seleccionar grupos para excluir** para ajustar la asignación. Seleccione **Siguiente** para continuar.  

6. En la pestaña **Revisar + crear**, revise la configuración y seleccione **Crear** cuando esté listo para guardar el anillo de actualización de Windows 10. El nuevo anillo de actualización se muestra en la lista de anillos de actualización.

## <a name="manage-your-windows-10-update-rings"></a>Administración de los anillos de actualización de Windows 10

En el portal, puede seleccionar un anillo de actualización de Windows 10 para abrir su panel de **Información general**. En este panel puede ver el estado de asignación de del anillo y realizar acciones adicionales para administrarlo.

### <a name="to-view-an-updates-rings-overview-pane"></a>Para ver el panel de Información general de un anillo de actualización: 

1. Inicie sesión en Azure Portal.
2. Vaya a **Intune** > **Actualizaciones de software** > **Anillos de actualización de Windows 10**.
3. Seleccione el anillo de actualización que quiere ver o administrar.  

Además de ver el estado de la asignación, puede seleccionar las acciones siguientes desde la parte superior del panel Información general para administrar el anillo de actualización:  
- [Eliminar](#delete)  
- [Pausar](#pause)  
- [Reanudar](#resume)  
- [Extender](#extend)  
- [Desinstalar](#uninstall)  

![Acciones disponibles](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>Eliminar  

Seleccione **Eliminar** para dejar de aplicar la configuración del anillo de actualización de Windows 10 seleccionado. Eliminar un anillo quita su configuración de Intune para que este deje de aplicar esas configuraciones.  

Eliminar un anillo de Intune no modifica la configuración de los dispositivos que tenían asignado el anillo de actualización.  En lugar de eso, el dispositivo conserva la configuración actual. Los dispositivos no mantienen un registro histórico de su configuración anterior. Los dispositivos también pueden recibir configuraciones de anillos de actualización adicionales que permanecen activos.  

#### <a name="to-delete-a-ring"></a>Para eliminar un anillo  

1. Mientras ve la página de información general de un anillo de actualización, seleccione **Eliminar**.  
2. Seleccione **Aceptar**.  

### <a name="pause"></a>Pausar  

Seleccione **Pausar** para evitar que los dispositivos asignados reciben actualizaciones de características o actualizaciones de calidad hasta por 35 días a contar del momento en que pausó el anillo. Después de que haya superado el número máximo de días, la funcionalidad de pausa expirará automáticamente y el dispositivo buscará en Windows Update las actualizaciones pertinentes. Después de este análisis, puede pausar las actualizaciones de nuevo. Si reanuda un anillo de actualización en pausa y luego vuelve a pausarlo, el período de pausa se restablece en 35 días.  

#### <a name="to-pause-a-ring"></a>Para pausar un anillo  

1. Mientras ve la página de información general de un anillo de actualización, seleccione **Pausar**.  
2. Seleccione **Característica** o **Calidad** para pausar ese tipo de actualización y seleccione **Aceptar**.  
3. Después de pausar un tipo de actualización, puede volver a seleccionar Pausar para pausar el otro tipo de actualización.  

Cuando se pausa un tipo de actualización, el panel Información genera de ese anillo muestra cuántos días quedan antes de que se reanude ese tipo de actualización.

> [!IMPORTANT]  
> Una vez que emite un comando de pausa, los dispositivos reciben este comando la próxima vez que se registren en el servicio. Es posible que antes de que se registren, instalen una actualización programada. Además, si un dispositivo de destino está apagado cuando se emite el comando de pausa, al encenderse, podría descargar e instalar actualizaciones programadas antes de que se registre con Intune.

### <a name="resume"></a>Reanudar  

Mientras un anillo de actualización está en pausa, puede seleccionar **Reanudar** para restaurar las actualizaciones de características y calidad de ese anillo para activar la operación. Una vez que reanuda un anillo de actualización, puede volver a ponerlo en pausa.  

#### <a name="to-resume-a-ring"></a>Para reanudar un anillo  

1. Mientras ve la página de información general de un anillo de actualización en pausa, seleccione **Reanudar**.  
2. En las opciones disponibles, seleccione si quiere reanudar las actualizaciones de **características** o de **calidad** y, luego, seleccione **Aceptar**.  
3. Después de reanudar un tipo de actualización, puede volver a seleccionar Reanudar para reanudar el otro tipo de actualización.  

### <a name="extend"></a>Extend  

Mientras un anillo de actualización está en pausa, puede seleccionar **Extender** para restablecer el período de pausa tanto de las actualizaciones de características como de calidad de ese anillo de actualización en 35 días.  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>Para extender el período de pausa de un anillo  

1. Mientras ve la página de información general de un anillo de actualización en pausa, seleccione **Extender**. 
2. En las opciones disponibles, seleccione si quiere reanudar las actualizaciones de **características** o de **calidad** y, luego, seleccione **Aceptar**.  
3. Después de extender la pausa de un tipo de actualización, puede volver a seleccionar Extender para extender el otro tipo de actualización.  

### <a name="uninstall"></a>Desinstalar  

Un administrador de Intune puede usar **Desinstalar** para desinstalar (revertir) la actualización de *características* o la actualización de *calidad* más reciente para un anillo de actualización activo o en pausa. Después de desinstalar un tipo, puede desinstalar el otro. Intune no admite ni administra la capacidad de los usuarios de desinstalar actualizaciones.  

> [!IMPORTANT] 
> Cuando se usa la opción de *Desinstalar*, Intune pasa inmediatamente la solicitud de desinstalación a los dispositivos. 
> - Los dispositivos Windows inician la eliminación de actualizaciones en cuanto reciben el cambio en la directiva de Intune. La eliminación de la actualización no se limita a las programaciones de mantenimiento, incluso cuando están configuradas como parte del anillo de actualización. 
> - Si la eliminación de la actualización requiere un reinicio del dispositivo, el dispositivo se reinicia sin ofrecer a los usuarios del dispositivo una opción para retrasar.


Para que la desinstalación se realice correctamente:  
- Un dispositivo debe ejecutar la actualización de Windows del 10 de abril de 2018 (versión 1803) o una versión posterior.  

Un dispositivo debe tener instalada la actualización más reciente. Como las actualizaciones son acumulativas, los dispositivos que instalan la última actualización tendrán la actualización de características y de calidad más reciente. Un ejemplo de cuando podría usar esta opción sería para revertir la última actualización si detecta un problema importante en las máquinas con Windows 10.  

Cuando realice la desinstalación, debe tener en cuenta lo siguiente:  
- La desinstalación de una actualización de característica o de calidad solo está disponible para el canal de servicio en el que se encuentra el dispositivo.  

- Usar la desinstalación de las actualizaciones de características o de calidad desencadena una directiva para restaurar la actualización anterior en las máquinas con Windows 10.  

- En un dispositivo con Windows 10, una vez que se revierte correctamente una actualización de calidad, los usuarios finales seguirán viendo la actualización en **Configuración de Windows** > **Actualizaciones** > **Historial de actualizaciones**.  

- En el caso específico de las actualizaciones de características, el plazo en el que puede desinstalar la actualización de características es limitado entre 2 y 60 días, según la configuración de la actualización **Establecimiento del período de desinstalación de actualizaciones de características (de 2 a 60 días)** de los anillos de actualización. No puede revertir una actualización de características que se haya instalado en un dispositivo después de que se haya instalado durante más tiempo que el período de desinstalación configurado.  

  Por ejemplo, imagine un anillo de actualización con un período de desinstalación de actualizaciones de características de 20 días. A los 25 días decide revertir la última actualización de características y usar la opción Desinstalar.  Los dispositivos que instalaron la actualización de características hace más de 20 días no pueden desinstalarla ya que quitaron los bits necesarios como parte de su mantenimiento. Pero los dispositivos que solo han instalado la actualización de características hace un máximo de 19 días pueden desinstalarla si se registran correctamente para recibir el comando de desinstalación antes de superar el período de desinstalación de 20 días.  

Para más información sobre las directivas de Windows Updates, consulte [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) (CSP de actualización) en la documentación de administración de clientes de Windows.  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>Para desinstalar la actualización más reciente de Windows 10  

1. Mientras ve la página de información general de un anillo de actualización en pausa, seleccione **Desinstalar**.  
2. En las opciones disponibles, seleccione si quiere desinstalar las actualizaciones de **características** o de **calidad** y, luego, seleccione **Aceptar**.  
3. Después de activar la desinstalación de un tipo de actualización, puede volver a seleccionar Desinstalar para desinstalar el otro tipo de actualización.  

## <a name="migrate-update-settings-to-the-azure-portal"></a>Migración de la configuración de actualización a Azure Portal  

El portal clásico de Azure también tiene un número limitado de otras opciones de actualizaciones de Windows 10 en el perfil de configuración de dispositivo. Si tiene alguna de estas opciones configuradas al migrar a Azure Portal, le recomendamos encarecidamente que lleve a cabo las acciones siguientes:  

1. Cree anillos de actualización de Windows 10 en Azure Portal con la configuración que necesite. La opción **Permitir características de versión preliminar** no es compatible con Azure Portal porque ya no se puede emplear en las compilaciones más recientes de Windows 10. Al crear los anillos de configuración, puede configurar las otras tres opciones, así como las otras opciones de actualizaciones de Windows 10.  

   > [!NOTE]  
   > La configuración de actualizaciones de Windows 10 creada en el portal clásico no se muestra en Azure Portal después de la migración. Pero se aplica esta configuración. Si migra cualquiera de estas opciones y edita la directiva migrada desde Azure Portal, esta configuración se quitará de la directiva.  

2. Elimine la configuración de actualización en el portal clásico. Después de migrar a Azure Portal y agregar la misma configuración a un anillo de actualización, debe eliminar la configuración en el portal clásico para evitar posibles conflictos entre directivas. Por ejemplo, si una misma opción está configurada con distintos valores, se produce un conflicto. No hay ninguna manera fácil de saberlo porque la configuración establecida en el portal clásico no se muestra en Azure Portal.  

## <a name="next-steps"></a>Pasos siguientes

[Windows update settings supported by Intune](../windows-update-settings.md) (Configuración de Windows Update compatible con Intune)  

[Informes de cumplimiento de Intune para las actualizaciones](../windows-update-compliance-reports.md)

[Troubleshooting Windows 10 update rings](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046) (Solución de problemas de los anillos de actualización de Windows 10)

