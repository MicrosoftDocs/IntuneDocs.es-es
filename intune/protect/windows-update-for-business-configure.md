---
title: Configuración de Windows Update para empresas en Microsoft Intune - Azure | Microsoft Docs
description: Administración de las actualizaciones de software de Windows 10 mediante la directiva de actualizaciones de características y anillos de actualización. Puede revisar el cumplimiento y pausar la instalación de actualizaciones con la configuración de Windows Update para empresas mediante Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9245ca028bdb5589df8c76b10560d9130a1108c
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181728"
---
# <a name="manage-windows-10-software-updates-in-intune"></a>Administración de actualizaciones de software de Windows 10 en Intune

Use Intune para administrar la instalación de actualizaciones de software de Windows 10 desde Windows Update para empresas.

Con Windows Update para empresas puede simplificar la experiencia de administración de actualizaciones. No es necesario que apruebe actualizaciones concretas para grupos de dispositivos. Para administrar el riesgo en sus entornos, puede configurar una estrategia de implementación de actualizaciones Intune ofrece la posibilidad de [configurar las actualizaciones](windows-update-settings.md) en los dispositivos y de aplazar su instalación. También puede impedir que los dispositivos instalen las características de las nuevas versiones de Windows para mantenerlos estables, permitiendo al mismo tiempo que esos dispositivos sigan instalando las actualizaciones con miras a mejorar la calidad y seguridad.

Intune solo almacena las asignaciones de las directivas de actualizaciones, no las propias actualizaciones. Los dispositivos acceden a Windows Update directamente para las actualizaciones.

Intune proporciona los siguientes tipos de directivas para administrar las actualizaciones:

- **Anillo de actualización de Windows 10**: Esta directiva es una colección de valores que se configura cuando se instalan las actualizaciones de Windows 10.

- **Actualizaciones de características de Windows 10 (versión preliminar pública)** : Esta directiva pone los dispositivos en la versión de Windows que especifique e inmoviliza el conjunto de características en dichos dispositivos hasta que decida actualizarlos a una versión posterior de Windows.  Aunque la versión de las características permanece estática, los dispositivos pueden continuar instalando las actualizaciones de calidad y seguridad que están disponibles para su versión de características.

El usuario asigna directivas para anillos de actualización de Windows 10 y actualizaciones de características de Windows 10 a grupos de dispositivos. Puede usar ambos tipos de directivas en el mismo entorno de Intune para administrar las actualizaciones de software para los dispositivos de Windows 10 y para crear una estrategia de actualización que refleje sus necesidades empresariales.

Para obtener más información, consulte [Administrar actualizaciones con Windows Update para empresas](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="prerequisites"></a>Requisitos previos

Deben cumplirse los requisitos previos siguientes para usar las actualizaciones de Windows para dispositivos Windows 10 en Intune.

- Los equipos con Windows 10 deben ejecutar las siguientes versiones de Windows 10:
  - **Anillos de actualización de Windows 10**: versión 1607 o posterior
  - **Actualizaciones de características de Windows 10**: versión 1703 o posterior

- Windows Update admite estas ediciones de Windows 10:
  - Windows 10
  - Windows 10 Team: para dispositivos Surface Hub (no es compatible con *actualizaciones de características de Windows 10*)
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

## <a name="windows-10-update-rings"></a>Anillos de actualización de Windows 10

Cree anillos de actualización que especifican cómo y cuándo Windows como servicio actualiza los dispositivos de Windows 10 con actualizaciones de características y de calidad. A partir de Windows 10, todas las nuevas actualizaciones de calidad y de características incluyen las actualizaciones anteriores. Siempre que tenga instalada la más reciente sabrá que sus dispositivos Windows 10 están actualizados. A diferencia de las versiones anteriores de Windows, ahora debe instalar la actualización completa en lugar de una parte.

Los anillos de actualización de Windows 10 admiten las [etiquetas de ámbito](../fundamentals/scope-tags.md). Puede usar etiquetas de ámbito con los anillos de actualización para filtrar y administrar los conjuntos de configuraciones que usa.

### <a name="create-and-assign-update-rings"></a>Crear y asignar anillos de actualización

1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Windows** > **Anillos de actualización de Windows 10** > **Crear**.

3. En la pestaña *Datos básicos*, indique un nombre, una descripción (opcional) y, después, seleccione **Siguiente**.
  ![Creación de un anillo de actualización](./media/windows-update-for-business-configure/basics-tab.png)

4. En **Configuración del anillo de actualización**, configure los valores según sus necesidades empresariales. Para información sobre la configuración disponible, consulte [Configuración de Windows Update](../protect/windows-update-settings.md). Después de configurar las opciones *Actualizar y Experiencia del usuario*, seleccione **Siguiente**.

5. En **Etiquetas de ámbito**, seleccione **+ Seleccionar etiquetas de ámbito** para abrir el panel *Seleccionar etiquetas* si quiere aplicarlas al anillo de actualización. Elija una o más etiquetas y, después, haga clic en **Seleccionar** para agregarlas al anillo de actualización y volver al panel *Etiqueta de ámbito*.

   Cuando esté listo, seleccione **Siguiente** para avanzar a *Asignaciones*.

6. En **Asignaciones**, seleccione **+ Seleccionar grupos para incluir** y, después, asigne el anillo de actualización a uno o varios grupos. Use **+ Seleccionar grupos para excluir** para ajustar la asignación. Seleccione **Siguiente** para continuar.

7. En **Revisar y crear**, revise la configuración y seleccione **Crear** cuando esté listo para guardar el anillo de actualización de Windows 10. El nuevo anillo de actualización se muestra en la lista de anillos de actualización.

### <a name="manage-your-windows-10-update-rings"></a>Administración de los anillos de actualización de Windows 10

En el portal, vaya a **Dispositivos** > **Windows** > **Anillos de actualización de Windows 10** y seleccione la directiva que desea administrar.  La directiva se abre en su página de **información general**.

Desde esta página, puede ver el estado de la asignación de los anillos y seleccionar las acciones siguientes desde la parte superior del panel Información general para administrar el anillo de actualización:

- [Eliminar](#delete)
- [Pausar](#pause)
- [Reanudar](#resume)
- [Extender](#extend)
- [Desinstalar](#uninstall)

![Acciones disponibles](./media/windows-update-for-business-configure/overview-actions.png)

#### <a name="delete"></a>Eliminar

Seleccione **Eliminar** para dejar de aplicar la configuración del anillo de actualización de Windows 10 seleccionado. Eliminar un anillo quita su configuración de Intune para que este deje de aplicar esas configuraciones.

Eliminar un anillo de Intune no modifica la configuración de los dispositivos que tenían asignado el anillo de actualización.  En lugar de eso, el dispositivo conserva la configuración actual. Los dispositivos no mantienen un registro histórico de su configuración anterior. Los dispositivos también pueden recibir configuraciones de anillos de actualización adicionales que permanecen activos.

##### <a name="to-delete-a-ring"></a>Para eliminar un anillo

1. Mientras ve la página de información general de un anillo de actualización, seleccione **Eliminar**.
2. Seleccione **Aceptar**.

#### <a name="pause"></a>Pausar

Seleccione **Pausar** para evitar que los dispositivos asignados reciben actualizaciones de características o actualizaciones de calidad hasta por 35 días a contar del momento en que pausó el anillo. Después de que haya superado el número máximo de días, la funcionalidad de pausa expirará automáticamente y el dispositivo buscará en Windows Update las actualizaciones pertinentes. Después de este análisis, puede pausar las actualizaciones de nuevo.
Si reanuda un anillo de actualización en pausa y luego vuelve a pausarlo, el período de pausa se restablece en 35 días.

##### <a name="to-pause-a-ring"></a>Para pausar un anillo

1. Mientras ve la página de información general de un anillo de actualización, seleccione **Pausar**.
2. Seleccione **Característica** o **Calidad** para pausar ese tipo de actualización y seleccione **Aceptar**.
3. Después de pausar un tipo de actualización, puede volver a seleccionar Pausar para pausar el otro tipo de actualización.

Cuando se pausa un tipo de actualización, el panel Información genera de ese anillo muestra cuántos días quedan antes de que se reanude ese tipo de actualización.

> [!IMPORTANT]
> Una vez que emite un comando de pausa, los dispositivos reciben este comando la próxima vez que se registren en el servicio. Es posible que antes de que se registren, instalen una actualización programada. Además, si un dispositivo de destino está apagado cuando se emite el comando de pausa, al encenderse, podría descargar e instalar actualizaciones programadas antes de que se registre con Intune.

#### <a name="resume"></a>Reanudar

Mientras un anillo de actualización está en pausa, puede seleccionar **Reanudar** para restaurar las actualizaciones de características y calidad de ese anillo para activar la operación. Una vez que reanuda un anillo de actualización, puede volver a ponerlo en pausa.

##### <a name="to-resume-a-ring"></a>Para reanudar un anillo

1. Mientras ve la página de información general de un anillo de actualización en pausa, seleccione **Reanudar**.
2. En las opciones disponibles, seleccione si quiere reanudar las actualizaciones de **características** o de **calidad** y, luego, seleccione **Aceptar**.
3. Después de reanudar un tipo de actualización, puede volver a seleccionar Reanudar para reanudar el otro tipo de actualización.

#### <a name="extend"></a>Extend  

Mientras un anillo de actualización está en pausa, puede seleccionar **Extender** para restablecer el período de pausa tanto de las actualizaciones de características como de calidad de ese anillo de actualización en 35 días.

##### <a name="to-extend-the-pause-period-for-a-ring"></a>Para extender el período de pausa de un anillo

1. Mientras ve la página de información general de un anillo de actualización en pausa, seleccione **Extender**.
2. En las opciones disponibles, seleccione si quiere reanudar las actualizaciones de **características** o de **calidad** y, luego, seleccione **Aceptar**.
3. Después de extender la pausa de un tipo de actualización, puede volver a seleccionar Extender para extender el otro tipo de actualización.

#### <a name="uninstall"></a>Desinstalar  

Un administrador de Intune puede usar **Desinstalar** para desinstalar (revertir) la actualización de *características* o la actualización de *calidad* más reciente para un anillo de actualización activo o en pausa. Después de desinstalar un tipo, puede desinstalar el otro. Intune no admite ni administra la capacidad de los usuarios de desinstalar actualizaciones.  

> [!IMPORTANT]
> Cuando se usa la opción de *Desinstalar*, Intune pasa inmediatamente la solicitud de desinstalación a los dispositivos.
>
> - Los dispositivos Windows inician la eliminación de actualizaciones en cuanto reciben el cambio en la directiva de Intune. La eliminación de la actualización no se limita a las programaciones de mantenimiento, incluso cuando están configuradas como parte del anillo de actualización.
> - Si la eliminación de la actualización requiere un reinicio del dispositivo, el dispositivo se reinicia sin ofrecer a los usuarios del dispositivo una opción para retrasar.

Para que la desinstalación se realice correctamente:

- Un dispositivo debe ejecutar la actualización de Windows del 10 de abril de 2018 (versión 1803) o una versión posterior.

Un dispositivo debe tener instalada la actualización más reciente. Como las actualizaciones son acumulativas, los dispositivos que instalan la última actualización tendrán la actualización de características y de calidad más reciente. Un ejemplo de cuando podría usar esta opción sería para revertir la última actualización si detecta un problema importante en las máquinas con Windows 10.

Cuando realice la desinstalación, debe tener en cuenta lo siguiente:

- La desinstalación de una actualización de característica o de calidad solo está disponible para el canal de servicio en el que se encuentra el dispositivo.

- Usar la desinstalación de las actualizaciones de características o de calidad desencadena una directiva para restaurar la actualización anterior en las máquinas con Windows 10.

- En un dispositivo con Windows 10, una vez que se revierte correctamente una actualización de calidad, los usuarios de los dispositivos seguirán viendo la actualización en **Configuración de Windows** > **Actualizaciones** > **Historial de actualizaciones**.

- En el caso concreto de las actualizaciones de características, el tiempo durante el que puede desinstalar la actualización está limitado de 2 a 60 días. Este período se configura mediante la opción de actualización de los anillos de actualización **Establecimiento del período de desinstalación de actualizaciones de características (de 2 a 60 días)** . No puede revertir una actualización de características que se haya instalado en un dispositivo después de que la actualización se haya instalado durante más tiempo que el período de desinstalación configurado.

  Por ejemplo, imagine un anillo de actualización con un período de desinstalación de actualizaciones de características de 20 días. A los 25 días decide revertir la última actualización de características y usar la opción Desinstalar.  Los dispositivos que instalaron la actualización de características hace más de 20 días no pueden desinstalarla ya que quitaron los bits necesarios como parte de su mantenimiento. Pero los dispositivos que solo han instalado la actualización de características hace un máximo de 19 días pueden desinstalarla si se registran correctamente para recibir el comando de desinstalación antes de superar el período de desinstalación de 20 días.

Para más información sobre las directivas de Windows Updates, consulte [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) (CSP de actualización) en la documentación de administración de clientes de Windows.

##### <a name="to-uninstall-the-latest-windows-10-update"></a>Para desinstalar la actualización más reciente de Windows 10

1. Mientras ve la página de información general de un anillo de actualización en pausa, seleccione **Desinstalar**.
2. En las opciones disponibles, seleccione si quiere desinstalar las actualizaciones de **características** o de **calidad** y, luego, seleccione **Aceptar**.
3. Después de activar la desinstalación de un tipo de actualización, puede volver a seleccionar Desinstalar para desinstalar el otro tipo de actualización.

## <a name="windows-10-feature-updates"></a>Actualizaciones de características de Windows 10

*Esta característica está en versión preliminar pública.*

Con las *actualizaciones de características de Windows 10*, puede seleccionar la versión de las características de Windows en la que desea que se mantengan los dispositivos, como la versión 1803 o la versión 1809 de Windows 10. Puede establecer un nivel de características de 1803 o posterior.

Cuando un dispositivo recibe una directiva de actualizaciones de características de Windows 10:

- El dispositivo se actualizará a la versión de Windows especificada en la directiva. Un dispositivo que ya ejecuta una versión posterior de Windows permanece en su versión actual. Al inmovilizar la versión, el conjunto de características de los dispositivos permanece estable mientras dure la directiva.

- Mientras se mantiene la versión instalada de Windows, los dispositivos pueden seguir recibiendo e instalando actualizaciones de calidad y seguridad para su versión de Windows durante el tiempo de compatibilidad de esa versión, lo que le ayuda a mantener los dispositivos actualizados y seguros.

- A diferencia de *Pausar* un anillo de actualización, que expira después de 35 días, la directiva de actualizaciones de características de Windows 10 permanece en vigor. Los dispositivos no instalarán una nueva versión de Windows hasta que modifique o quite la directiva de actualizaciones de características de Windows 10. Si edita la directiva para especificar una versión más reciente, los dispositivos pueden instalar las características desde esa versión de Windows.

### <a name="prerequisites-for-windows-10-feature-updates"></a>Requisitos previos de las actualizaciones de características de Windows 10

Deben cumplirse los requisitos previos siguientes para usar las actualizaciones de características de Windows 10 en Intune.

- Los dispositivos deben estar inscritos en Intune MDM y unidos a Azure AD o registrados en Azure AD.
- Para usar la directiva de actualizaciones de características con Intune, los dispositivos deben tener la telemetría activada, con un valor mínimo de [*Básico*](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry). La telemetría se configura en *Informes y telemetría* como parte de la [directiva de restricción de dispositivos](../configuration/device-restrictions-configure.md).
  
  Los dispositivos que reciben la directiva de actualizaciones de características y que tienen la telemetría establecida en *No configurado* (lo que significa que está desactivada), pueden instalar una versión posterior de Windows que la definida en la directiva de actualización de características. El requisito previo de requerir telemetría está en revisión, ya que esta característica está en transición hacia la disponibilidad general.

### <a name="limitations-for-windows-10-feature-updates"></a>Limitaciones de las actualizaciones de características de Windows 10

- Cuando implemente una directiva de *actualización de características de Windows 10* en un dispositivo que también recibe una directiva de *anillo de actualización de Windows 10*, revise que el anillo de actualización incluya las siguientes configuraciones:
  - El **período de aplazamiento de actualizaciones de características (días)** se debe establecer en **0**.
  - Las actualizaciones de características para el anillo de actualización deben estar *en ejecución*. No se deben pausar.

- Las directivas de actualización de características de Windows 10 no se pueden aplicar durante la configuración rápida (OOBE) de Autopilot y solo se aplican en el primer análisis de Windows Update una vez que el dispositivo haya finalizado el aprovisionamiento (que suele ser un día).

### <a name="create-and-assign-windows-10-feature-updates"></a>Creación y asignación de actualizaciones de características de Windows 10

1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Windows** > **Actualizaciones de características de Windows 10** > **Crear**.

3. En **Datos básicos**, especifique un nombre, una descripción (opcional) y, para **Actualización de características para implementar**, seleccione la versión de Windows con el conjunto de características que desee y, a continuación, seleccione **Siguiente**.

4. En **Asignaciones**, seleccione **+ Seleccionar grupos para incluir** y, después, asigne la implementación de actualizaciones de características a uno o varios grupos. Seleccione **Siguiente** para continuar.

5. En **Revisar + crear**, revise la configuración y seleccione **Crear** cuando esté listo para guardar la directiva de actualizaciones de características de Windows 10.  

### <a name="manage-windows-10-feature-updates"></a>Administración de actualizaciones de características de Windows 10

En el centro de administración, vaya a **Dispositivos** > **Windows** > **Actualizaciones de características de Windows 10** y seleccione la directiva que desea administrar. La directiva se abre en su panel de **información general**.

Desde este panel, podrá:

- Seleccionar **Eliminar** para eliminar la directiva de Intune y quitarla de los dispositivos.
- Seleccione **Propiedades** para modificar la implementación.  En el panel *Propiedades*, seleccione **Editar** para abrir las *asignaciones o la configuración de la implementación*, donde podrá modificar la implementación.
- Seleccione **Estado de actualización del usuario final** para ver información acerca de la directiva.

## <a name="validation-and-reporting-for-windows-10-updates"></a>Validación e informes de las actualizaciones de Windows 10

En el caso de los anillos de actualización de Windows 10 y de las actualizaciones de características de Windows 10, use [Informes de cumplimiento de Intune para las actualizaciones](../windows-update-compliance-reports.md) para supervisar el estado de las actualizaciones de los dispositivos. Esta solución usa [Update Compliance](https://docs.microsoft.com/windows/deployment/update/update-compliance-monitor) con la suscripción de Azure.

## <a name="next-steps"></a>Pasos siguientes

[Windows update settings supported by Intune](../windows-update-settings.md) (Configuración de Windows Update compatible con Intune)

[Troubleshooting Windows 10 update rings](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046) (Solución de problemas de los anillos de actualización de Windows 10)
