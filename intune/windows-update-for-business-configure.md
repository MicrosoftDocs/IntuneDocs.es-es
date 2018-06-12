---
title: Configuración de Windows Update para empresas en Microsoft Intune - Azure | Microsoft Docs
description: Actualizar la configuración de las actualizaciones de software en un perfil para crear un anillo de actualización, revisar el cumplimiento y pausar las actualizaciones en la configuración de Windows Update para empresas con Microsoft Intune en dispositivos Windows 10.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 5/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: fd63fb2023b4712a3ad49838f87f5b7cc8320954
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744897"
---
# <a name="manage-software-updates-in-intune"></a>Administrar las actualizaciones de software en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows como servicio es el método para actualizar los dispositivos Windows 10. A partir de Windows 10, todas las nuevas actualizaciones de calidad y de características incluyen las actualizaciones anteriores. Siempre que tenga instalada la más reciente sabrá que sus dispositivos Windows 10 están actualizados. A diferencia de las versiones anteriores de Windows, ahora debe instalar la actualización completa en lugar de una parte.

Con Windows Update para empresas puede simplificar la experiencia de administración de actualizaciones. No es necesario que apruebe actualizaciones concretas para grupos de dispositivos. Para administrar el riesgo en sus entornos, puede configurar una estrategia de implementación de actualizaciones y Windows Update se asegurará de que las actualizaciones se instalen en el momento oportuno. Microsoft Intune ofrece la posibilidad de configurar las actualizaciones en los dispositivos y de aplazar su instalación. Intune no almacena las actualizaciones, sino únicamente la asignación de las directivas de actualización. Los dispositivos acceden a Windows Update directamente para las actualizaciones. Use Intune para configurar y administrar **círculos de actualizaciones de Windows 10**. Un anillo de actualización incluye un grupo de opciones que configuran cuándo y cómo se instalan las actualizaciones de Windows 10. Por ejemplo, puede configurar las siguientes opciones:

- **Canal de servicio de Windows 10**: elija el canal de servicio desde el que quiere que los grupos de dispositivos reciban actualizaciones. Están disponibles los siguientes canales: 
  - Canal semianual
  - Canal semianual (destino)
  - Windows Insider: Rápida
  - Windows Insider: Lenta
  - Lanzamiento de Windows Insider 
      
  Para obtener información detallada sobre los canales de servicio disponibles, vea [Información general de Windows como servicio](https://docs.microsoft.com/en-us/windows/deployment/update/waas-overview#servicing-channels).
- **Configuración de aplazamiento**: configure las opciones de aplazamiento de actualizaciones con el fin de retrasar la instalación de las actualizaciones para grupos de dispositivos. Puede usar esta configuración para organizar su implementación de actualización para poder revisar el progreso sobre la marcha.
- **Pausa**: posponga la instalación de actualizaciones si detecta un problema en cualquier momento durante la implementación.
- **Período de mantenimiento**: configure las horas en que se pueden instalar las actualizaciones.
- **Tipo de actualización**: elija los tipos de actualizaciones que se instalarán. Por ejemplo, de calidad, de características o de controladores.
- **Comportamiento de instalación**: esta opción configura cómo se instalan las actualizaciones. Por ejemplo, si quiere que el dispositivo se reinicie automáticamente después de la instalación.
- **Peer downloading** (Descarga del mismo nivel): puede optar por configurar la descarga del mismo nivel. Si lo hace, cuando un dispositivo ha terminado de descargar una actualización, otros dispositivos pueden descargar la actualización desde ese dispositivo. Esta opción acelera el proceso de descarga.

Después de crear anillos de actualización, debe asignarnos a grupos de dispositivos. Gracias a ellos, puede crear una estrategia de actualización que refleje sus necesidades empresariales. Para obtener más información, consulte [Administrar actualizaciones con Windows Update para empresas](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="before-you-start"></a>Antes de empezar

- Para actualizar equipos con Windows 10, debe estar ejecutando, al menos, Windows 10 Pro con la actualización Windows Anniversary Update.

- Windows Update admite las siguientes versiones de Windows 10:
  - Windows 10
  - Windows 10 Team (para dispositivos Surface Hub)
  - [Windows Holographic for Business](#windows-holographic-for-business-support)

  No se admiten los dispositivos que ejecutan Windows 10 Mobile.

- En los dispositivos Windows, el valor de las opciones **Comentarios y diagnósticos** > **Datos de uso y diagnóstico** debe establecerse en, al menos, **Básico**.

    ![Configuración de Windows para Datos de diagnóstico y uso](./media/telemetry-basic.png)

    Puede configurar esta opción manualmente, o bien utilizar un perfil de restricción de dispositivos Intune para Windows 10 y versiones posteriores. Para ello, configure la opción **General** > **Envío de datos de diagnóstico** con, al menos, el valor **Básico**. Para obtener más información sobre los perfiles de dispositivo, vea [Configuración de restricciones de dispositivos en Microsoft Intune](device-restrictions-configure.md).

- En la consola de administración de Intune, hay cuatro opciones que controlan el comportamiento de las actualizaciones de software. Estos forman parte de la directiva de configuración general para dispositivos móviles y equipos con Windows 10:
  - **Permitir actualizaciones automáticas**
  - **Permitir características de evaluación**
  - **Día de instalación programado**
  - **Hora de instalación programada**

  El portal clásico de Azure también tiene un número limitado de otras opciones de actualizaciones de Windows 10 en el perfil de configuración de dispositivo. Si tiene alguna de estas opciones configuradas al migrar a Azure Portal, le recomendamos encarecidamente que haga lo siguiente:

1. Cree anillos de actualización de Windows 10 en Azure Portal con la configuración que necesite. La opción **Permitir características de versión preliminar** no es compatible con Azure Portal porque ya no se puede emplear en las compilaciones más recientes de Windows 10. Al crear los anillos de configuración, puede configurar las otras tres opciones, así como otras opciones de actualizaciones de Windows 10.

   > [!NOTE]
   > La configuración de actualizaciones de Windows 10 creada en el portal clásico no se muestra en Azure Portal después de la migración. Pero se aplica esta configuración. Si migra cualquiera de estas opciones y edita la directiva migrada desde Azure Portal, esta configuración se quitará de la directiva.

2. Elimine la configuración de actualización en el portal clásico. Después de migrar a Azure Portal y agregar la misma configuración a un anillo de actualización, debe eliminar la configuración en el portal clásico para evitar posibles conflictos entre directivas. Por ejemplo, si una misma opción está configurada con distintos valores, se produce un conflicto. No hay ninguna manera fácil de saberlo porque la configuración establecida en el portal clásico no se muestra en Azure Portal.

## <a name="create-and-assign-update-rings"></a>Crear y asignar anillos de actualización

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Actualizaciones de software** > **Anillos de actualización de Windows 10** > **Crear**.
4. Escriba un nombre, una descripción (opcional) y, después, elija **Configurar**.
5. En **Configuración**, especifique la siguiente información:

   - **Canal de servicio**: establezca el canal desde el que el dispositivo recibe las actualizaciones de Windows.
   - **Actualizaciones de productos de Microsoft**: elija si quiere buscar actualizaciones de aplicaciones de Microsoft Update.
   - **Controladores de Windows**: elija si desea excluir los controladores de Windows Update durante las actualizaciones.
   - **Comportamiento de actualización automática**: elija cómo se deben instalar las actualizaciones automáticas y cuándo se deben reiniciar. Para obtener más información, consulte la sección [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate).
     - **Frecuencia de comportamiento automático**: si selecciona **Auto install and restart at scheduled time** (Instalar y reiniciar automáticamente a la hora programada) para el comportamiento de las actualizaciones, se mostrará esta opción. Use esta opción para programar cuándo se instalarán las actualizaciones (semana, día y hora).

   - **Comprobaciones de reinicio**: opción habilitada de forma predeterminada. Al reiniciar un dispositivo se efectúan algunas comprobaciones, como la comprobación de los usuarios activos, los niveles de batería, los juegos de ejecución, etc. Para omitir estas comprobaciones al reiniciar un dispositivo, seleccione **Omitir**.

   - **Período de aplazamiento de actualizaciones de calidad (días)**: indique el número de días que se aplazarán las actualizaciones de calidad. Puede aplazar la recepción de estas actualizaciones de calidad un máximo de 30 días a partir de su publicación.

     Las actualizaciones de calidad suelen ser correcciones y mejoras de la funcionalidad de Windows y se publican el primer martes de cada mes, aunque Microsoft puede publicarlas en cualquier momento. Puede definir si quiere aplazar la recepción de actualizaciones de calidad cuando estén disponibles en Windows Update, así como el tiempo que quiere aplazarla.

   - **Período de aplazamiento de actualizaciones de características (días)**: indique el número de días que se aplazarán las actualizaciones de características. Puede aplazar la recepción de las actualizaciones de características un máximo de 180 días a partir de su publicación.

     Las actualizaciones de características suelen ser características nuevas de Windows. Después de configurar la opción **Canal de servicio**, puede definir si quiere aplazar la recepción de actualizaciones de características cuando estén disponibles en Windows Update, así como el tiempo que quiere aplazarla.

     Por ejemplo, **si el canal de servicio está establecido en Canal semianual (dirigido) y el período de aplazamiento es de 30 días**, supongamos que la actualización de características X se publica inicialmente en Windows Update como Canal semianual (dirigido) en enero. El dispositivo no recibirá la actualización hasta febrero: 30 días más tarde.

     **Si el canal de servicio se establece en Canal semianual y el período de aplazamiento es de 30 días**: supongamos que la actualización de características X se publica inicialmente en Windows Update como Canal semianual (dirigido) en enero. Cuatro meses más tarde, en abril, la actualización de características X se publicará en el Canal semianual. El dispositivo recibe la actualización de características 30 días después de esta publicación en el Canal semianual y se actualizará en mayo.

   - **Modo de descarga de optimización de distribución**: elija el método por el que los dispositivos descargarán las actualizaciones de Windows. Para obtener más información, consulte [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode).

6. Cuando haya terminado, seleccione **Aceptar**. En **Crear anillo de actualización**, seleccione **Crear**.

El nuevo anillo de actualización se muestra en la lista de anillos de actualización.

1. Para asignar el anillo, en la lista de anillos de actualización, seleccione un anillo y, luego, en la pestaña <*nombre del anillo*>, elija **Asignaciones**.
2. En la pestaña siguiente, elija **Seleccionar grupos para incluir** y, luego, seleccione los grupos a los que quiere asignar este anillo.
3. Una vez que haya terminado, elija **Seleccionar** para completar la asignación.

## <a name="update-compliance-reporting"></a>Informes de comprobación de actualizaciones
Puede consultar la comprobación de actualizaciones en Intune o mediante una solución gratuita en la instancia de Operations Management Suite (OMS) llamada Update Compliance.

### <a name="review-update-compliance-in-intune"></a>Revisar la comprobación de actualizaciones en Intune 
<!-- 1352223 -->
Consulte un informe de directiva para conocer el estado de implementación para los círculos de actualizaciones de Windows 10 que ha configurado.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Elija **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Actualizaciones de software** > **Información general**. Puede ver información general sobre el estado de los círculos de actualizaciones que tenga asignados.
4. Abra uno de los informes siguientes:

   **Para todos los anillos de implementación**:  
   1. En **Actualizaciones de software** > **Anillos de actualización de Windows 10**
   2. En la **sección Supervisar**, elija **Por el estado de implementación del círculo de implementaciones**.

   **Para anillos de implementación específicos**:  
   1. En **Actualizaciones de software** > **Anillos de actualización de Windows 10**, elija los anillos de implementación que va a revisar.
   2. En la sección **Supervisar**, elija uno de los siguientes informes para ver información más detallada sobre el círculo de actualizaciones:
      - **Estado del dispositivo**
      - **Estado del usuario**

### <a name="review-update-compliance-using-oms"></a>Revisar la comprobación de actualizaciones con OMS
Puede supervisar las implementaciones de actualización de Windows 10 utilizando una solución gratuita en la instancia de Operations Management Suite (OMS) llamada "Comprobación de actualizaciones". Para obtener más información, consulte [Monitor Windows Updates with Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor) (Supervisión de actualizaciones de Windows con Comprobación de actualizaciones). Cuando se utiliza esta solución, puede implementar un identificador comercial en cualquiera de sus dispositivos Windows 10 administrados con Intune para el que desea que se informe de la comprobación de actualizaciones.

En la consola de Intune, puede usar la configuración OMA-URI de una directiva personalizada para configurar el identificador comercial. Para obtener más información, consulte [Configuración de directivas de Intune para dispositivos Windows 10 en Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

La ruta OMA-URI (distingue mayúsculas de minúsculas) para configurar el identificador comercial es: ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

Por ejemplo, puede usar los siguientes valores en **Agregar o editar configuración OMA-URI**:

- **Nombre del valor de configuración**: identificador comercial de Windows Analytics
- **Descripción del valor de configuración**: configuración del identificador comercial para soluciones de Windows Analytics
- **OMA-URI** (distingue mayúsculas de minúsculas): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Tipo de datos:** Cadena
- **Valor**: <*Utilizar el GUID que se muestra en la pestaña Telemetría de Windows del área de trabajo de OMS*>

![Configuración de OMA-URI - Editar fila](./media/commID-edit.png)

> [!NOTE]
> Para obtener más información sobre MS DM Server, vea [DMClient configuration service provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp) (Proveedor de servicios de configuración (CSP) de DMClient).

## <a name="pause-updates"></a>Pausar las actualizaciones
Puede pausar un dispositivo para que deje de recibir actualizaciones de características o de calidad durante un período máximo de 35 días desde el momento en que se pausa las actualizaciones. Después de que haya superado el número máximo de días, la funcionalidad de pausa expirará automáticamente y el dispositivo buscará en Windows Update las actualizaciones pertinentes. Después de este análisis, puede pausar las actualizaciones de nuevo.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Actualizaciones de software** > **Anillos de actualización de Windows 10**.
4. En la lista de anillos de actualización, elija el anillo que quiere pausar y, después, seleccione **...** > **Pausar actualizaciones de calidad** > o **Pausar actualizaciones de características**, según el tipo de actualizaciones que quiera pausar.

> [!IMPORTANT]
> Al emitir un comando de pausa, los dispositivos reciben este comando la próxima vez que se registren en el servicio. Es posible que antes de que se registren, instalen una actualización programada.
> Además, si un dispositivo de destino está apagado cuando se emite el comando de pausa, al encenderse, podría descargar e instalar actualizaciones programadas antes de que se registre con Intune.

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>Desinstalar las últimas actualizaciones de software de Windows 10 
En caso de que detecte un problema importante en las máquinas con Windows 10, puede optar por desinstalar (revertir) la última actualización de características o la última actualización de calidad. La desinstalación de una actualización de característica o de calidad solo está disponible para el canal de servicio en el que se encuentra el dispositivo. La desinstalación desencadenará una directiva para restaurar la actualización anterior en las máquinas con Windows 10. Para las actualizaciones de características concretamente, puede limitar el tiempo de 2 a 60 días durante el cual se puede aplicar una desinstalación de la versión más reciente. Para configurar las opciones de desinstalación de actualización de software, seleccione **Actualizaciones de software** en la hoja **Microsoft Intune** en el portal de Azure. Después, seleccione **Anillos de actualización de Windows 10** en la hoja **Actualizaciones de software**. Elija después la opción **Desinstalar** en la sección **Información general**.

> [!NOTE]
> En máquinas con Windows 10, después de revertir correctamente la actualización de calidad, los usuarios finales podrán seguir viendo la actualización revertida correctamente si seleccionan **Configuración de Windows** > **Actualizaciones** > **Actualizar historial**.

## <a name="windows-holographic-for-business-support"></a>Compatibilidad con Windows Holographic for Business

Windows Holographic for Business es compatible con las siguientes opciones de configuración:

- **Comportamiento de las actualizaciones automáticas**
- **Actualizaciones de productos de Microsoft**
- **Canal de servicio**: admite las opciones **Canal semianual** y **Canal semianual (dirigido)**
