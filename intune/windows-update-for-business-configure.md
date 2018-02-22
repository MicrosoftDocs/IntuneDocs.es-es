---
title: "Configuración de Windows Update para empresas en Intune"
titleSuffix: Azure portal
description: "Obtenga información sobre cómo configurar Windows Update para empresas en Intune para controlar las actualizaciones de dispositivos Windows 10\"."
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 1/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: 1a7d047de1faa019eb137516ef75d64657e22e5a
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="manage-software-updates"></a>Administrar actualizaciones de software

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Windows como servicio es el método para actualizar los dispositivos Windows 10. A partir de Windows 10, todas las nuevas actualizaciones de calidad y de características contienen las actualizaciones anteriores. Es decir, siempre que tenga instalada la más reciente, sabrá que sus dispositivos Windows 10 están actualizados. A diferencia de las versiones anteriores de Windows, ahora debe instalar la actualización completa en lugar de una parte.

Gracias a Windows Update para empresas, puede simplificar la administración de actualizaciones, ya que no tendrá que aprobar actualizaciones individuales para grupos de dispositivos. Todavía puede administrar los riesgos en sus entornos configurando una estrategia de implementación de actualizaciones; Windows Update se asegurará de que las actualizaciones se instalen en el momento oportuno. Microsoft Intune ofrece la posibilidad de configurar las actualizaciones en los dispositivos y de aplazar su instalación. Intune no almacena las actualizaciones, sino únicamente la asignación de las directivas de actualización. Los dispositivos acceden a Windows Update directamente para las actualizaciones. Use Intune para configurar y administrar **círculos de actualizaciones de Windows 10**. Un anillo de actualización contiene un grupo de opciones que configuran cuándo y cómo se instalan las actualizaciones de Windows 10. Por ejemplo, puede configurar las siguientes opciones:

- **Canal de servicio de Windows 10**: elija si desea que los grupos de dispositivos reciban actualizaciones del Canal semianual o del Canal semianual (dirigido).  
- **Configuración de aplazamiento**: configure las opciones de aplazamiento de actualizaciones con el fin de retrasar la instalación de las actualizaciones para grupos de dispositivos. Puede usar esta configuración para realizar una implementación por fases para revisar el progreso de las actualizaciones.
- **Pausa**: posponga la instalación de actualizaciones si detecta un problema en cualquier momento durante la implementación.
- **Período de mantenimiento**: configure las horas en que se pueden instalar las actualizaciones.
- **Tipo de actualización**: elija los tipos de actualizaciones que se instalarán. Por ejemplo, de calidad, de características o de controladores.
- **Comportamiento de instalación**: esta opción configura cómo se instalan las actualizaciones. Por ejemplo, si quiere que el dispositivo se reinicie automáticamente después de la instalación.
- **Peer downloading** (Descarga del mismo nivel): puede especificar si desea configurar esta opción. Si lo hace, cuando un dispositivo ha terminado de descargar una actualización, otros dispositivos pueden descargar la actualización desde ese dispositivo. De esta forma, se acelera el proceso de descarga.

Después de crear anillos de actualización, debe asignarnos a grupos de dispositivos. Gracias a ellos, puede crear una estrategia de actualización que refleje sus necesidades empresariales. Para obtener más información, consulte [Administrar actualizaciones con Windows Update para empresas](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="before-you-start"></a>Antes de empezar

- Para actualizar equipos con Windows 10, debe estar ejecutando, al menos, Windows 10 Pro con la actualización Windows Anniversary Update.

- Windows Update admite las siguientes versiones de Windows 10:
    - Windows 10
    - Windows 10 Team (para dispositivos Surface Hub)
    - [Windows Holographic for Business](#windows-holographic-for-business-support)

 No se admiten dispositivos que ejecuten Windows 10 Mobile.

- En los dispositivos Windows, el valor de las opciones **Comentarios y diagnósticos** > **Datos de uso y diagnóstico** debe establecerse en, al menos, **Básico**.

    ![Configuración de Windows para Datos de diagnóstico y uso](./media/telemetry-basic.png)

    Puede configurar esta opción manualmente, o bien utilizar un perfil de restricción de dispositivos Intune para Windows 10 y versiones posteriores. Para ello, configure la opción **General** > **Envío de datos de diagnóstico** con, al menos, el valor **Básico**. Para obtener más información sobre los perfiles de dispositivo, consulte [Configuración de restricciones de dispositivos en Microsoft Intune](device-restrictions-configure.md).

- En la consola de administración de Intune, hay cuatro opciones que controlan el comportamiento de las actualizaciones de software. Estos forman parte de la directiva de configuración general para dispositivos móviles y equipos con Windows 10:
    - **Permitir actualizaciones automáticas**
    - **Permitir características de evaluación**
    - **Día de instalación programado**
    - **Hora de instalación programada**

  El portal clásico también tiene un número limitado de otras opciones de actualizaciones de Windows 10 en el perfil de configuración de dispositivo. Si tiene alguna de estas opciones configuradas en la consola de administración de Intune al migrar a Azure Portal, le recomendamos encarecidamente que haga lo siguiente:

1. Cree anillos de actualización de Windows 10 en Azure Portal con la configuración que necesite. La opción **Permitir características de versión preliminar** no es compatible con Azure Portal porque ya no se puede emplear en las compilaciones más recientes de Windows 10. Al crear los anillos de configuración, puede configurar las otras tres opciones, así como otras opciones de actualizaciones de Windows 10.

  > [!NOTE]
  > La configuración de actualizaciones de Windows 10 creada en el portal clásico no se muestra en Azure Portal después de la migración. Sin embargo, sí que siguen aplicando estas opciones. Si ha migrado cualquiera de estas opciones y editado la directiva migrada desde Azure Portal, esta configuración se quitará de la directiva.

2. Elimine la configuración de actualización en el portal clásico. Después de migrar a Azure Portal y agregar la misma configuración a un anillo de actualización, debe eliminar la configuración en el portal clásico para evitar posibles conflictos entre directivas. Por ejemplo, cuando se configuran las mismas opciones con valores diferentes, se produce un conflicto y no hay una manera sencilla de saberlo, ya que la configuración del portal clásico no se muestra en Azure Portal.

## <a name="how-to-create-and-assign-update-rings"></a>Creación y asignación de anillos de actualización

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Actualizaciones de software**.
4. En la hoja **Actualizaciones de Software**, elija **Administrar** > **Windows 10 Update Rings** (Anillos de actualización de Windows 10).
5. En la hoja que muestra la lista de perfiles, elija **Crear**.
6. En la hoja **Create Update Ring** (Crear anillo de actualización), proporcione un nombre y una descripción opcional para el anillo de actualización. Luego, elija **Configuración**.
7. En la hoja **Configuración**, configure la siguiente información:
    - **Canal de servicio**: establezca el canal para el que el dispositivo recibe actualizaciones de Windows, ya sea Canal semianual o Canal semianual (dirigido).
    - **Actualizaciones de Microsoft**: elija si desea buscar actualizaciones de aplicaciones de Microsoft Update.
    - **Controladores de Windows**: elija si desea excluir los controladores de Windows Update durante las actualizaciones.
    - **Automatic update behavior** (Comportamiento de actualización automática): elija cómo administrar el comportamiento de actualización automática para examinar, descargar e instalar actualizaciones. Para obtener más información, consulte la sección [Update/AllowAutoUpdate](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate).
    - **Período de aplazamiento de actualizaciones de calidad (días)**: especifique el número de días que se aplazarán las actualizaciones de calidad. Puede aplazar la recepción de estas actualizaciones de calidad durante un período de hasta 30 días a partir de su publicación.  

    Las actualizaciones de calidad suelen ser correcciones y mejoras de la funcionalidad de Windows y se publican normalmente el primer martes de cada mes, aunque Microsoft puede lanzarlas en cualquier momento. Puede definir si, y durante cuánto tiempo, desea aplazar la recepción de actualizaciones de calidad después de su disponibilidad.
    - **Período de aplazamiento de actualizaciones de características (días)**: especifique el número de días que se aplazarán las actualizaciones de características. Puede aplazar la recepción de estas actualizaciones de características durante un período de hasta 180 días a partir de su publicación.

    Las actualizaciones de características suelen ser nuevas características de Windows. Después de configurar la opción **Canal de servicio**, ya sea Canal semianual o el Canal semianual (dirigido), podrá definir si quiere aplazar la recepción de actualizaciones de características (y durante cuánto tiempo) después de que Microsoft las publique en Windows Update.

    Por ejemplo, **si el canal de servicio está establecido en Canal semianual (dirigido) y el período de aplazamiento es de 30 días**, supongamos que la actualización de características X se publica inicialmente en Windows Update como Canal semianual (dirigido) en enero. El dispositivo no recibirá la actualización hasta febrero: 30 días más tarde.

    **Si el canal de servicio se establece en Canal semianual y el período de aplazamiento es de 30 días**: supongamos que la actualización de características X se publica inicialmente en Windows Update como Canal semianual (dirigido) en enero. Cuatro meses más tarde, en abril, la actualización de características X se publicará en el Canal semianual. El dispositivo recibirá la actualización de características 30 días después de esta publicación en el Canal semianual y se actualizará en mayo.

    - **Optimización de distribución**: elija el método por el que los dispositivos descargarán las actualizaciones de Windows. Para obtener más información, consulte [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode).
1. Una vez que haya terminado, haga clic en **Aceptar**y, luego, en la hoja **Create Update Ring** (Crear anillo de actualización), haga clic en **Crear**.

El nuevo anillo de actualización se muestra en la lista de anillos de actualización.

1. Para asignar el anillo, en la lista de anillos de actualización, seleccione un anillo y, luego, en la pestaña <*nombre del anillo*>, elija **Asignaciones**.
2. En la pestaña siguiente, elija **Seleccionar grupos**y, luego, seleccione los grupos a los que desea asignar este anillo.
3. Una vez que haya terminado, elija **Seleccionar** para completar la asignación.

## <a name="update-compliance-reporting"></a>Informes de comprobación de actualizaciones
Puede consultar la comprobación de actualizaciones en Intune o mediante una solución gratuita en la instancia de Operations Management Suite (OMS) llamada Update Compliance.

### <a name="review-update-compliance-in-intune"></a>Revisar la comprobación de actualizaciones en Intune 
<!-- 1352223 -->
Consulte un informe de directiva para conocer el estado de implementación para los círculos de actualizaciones de Windows 10 que ha configurado. 
1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Actualizaciones de software**.
4. En la hoja **Actualizaciones de software**, seleccione **Información general**. A partir de aquí, puede ver información general sobre el estado de los círculos de actualizaciones que tenga asignados.
5. Abra uno de los informes siguientes: 
     
   **Para todos los círculos de implementación:**
   1. En la hoja **Actualizaciones de software** > **Círculos de actualizaciones de Windows 10**. 
   2. En la **sección Supervisar**, elija **Por el estado de implementación del círculo de implementaciones**.
                   
   **Para círculos de implementación específicos:** 
   1. En la hoja **Actualizaciones de software** > **Círculos de actualizaciones de Windows 10**, elija los círculos de implementaciones para revisar.
   2. En la sección **Supervisar**, elija uno de los siguientes informes para ver información más detallada sobre el círculo de actualizaciones:
      - **Implementación del círculo de actualizaciones para dispositivos**
      - **Implementación del círculo de actualizaciones para usuarios**
      - **Estado de implementación por configuración**

### <a name="review-update-compliance-using-oms"></a>Revisar la comprobación de actualizaciones con OMS
Puede supervisar las implementaciones de actualización de Windows 10 utilizando una solución gratuita en la instancia de Operations Management Suite (OMS) llamada "Comprobación de actualizaciones". Para obtener más información, consulte [Monitor Windows Updates with Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor) (Supervisión de actualizaciones de Windows con Comprobación de actualizaciones). Cuando se utiliza esta solución, puede implementar un identificador comercial en cualquiera de sus dispositivos Windows 10 administrados con Intune para el que desea que se informe de la comprobación de actualizaciones.

En la consola de Intune, puede usar la configuración OMA-URI de una directiva personalizada para configurar el identificador comercial. Para obtener más información, consulte [Configuración de directivas de Intune para dispositivos Windows 10 en Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

La ruta OMA-URI (distingue mayúsculas de minúsculas) para configurar el identificador comercial es: ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

Por ejemplo, puede usar los siguientes valores en **Agregar o editar configuración OMA-URI**:

- **Nombre del valor de configuración**: identificador comercial de Windows Analytics
- **Descripción del valor de configuración**: configuración del identificador comercial para soluciones de Windows Analytics
- **Tipo de datos:** Cadena
- **OMA-URI** (distingue mayúsculas de minúsculas): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Valor**: <*Utilizar el GUID que se muestra en la pestaña Telemetría de Windows del área de trabajo de OMS*>

![Configuración de Windows para Datos de diagnóstico y uso](./media/commID.png)

## <a name="how-to-pause-updates"></a>Pausa de actualizaciones
Puede pausar un dispositivo para que deje de recibir actualizaciones de características o de calidad durante un período máximo de 35 días desde el momento en que se pausa las actualizaciones. Después de que haya superado el número máximo de días, la funcionalidad de pausa expirará automáticamente y el dispositivo buscará en Windows Update las actualizaciones pertinentes. Después de este análisis, puede pausar las actualizaciones de nuevo.
1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Actualizaciones de software**.
4. En la hoja **Actualizaciones de Software**, elija **Administrar** > **Windows 10 Update Rings** (Anillos de actualización de Windows 10).
5. En la hoja que muestra la lista de anillos de actualización, elija el anillo que desea pausar y, luego, seleccione **...** > **Pausar actualizaciones de calidad** > o **Pausar actualizaciones de características**, según el tipo de actualizaciones que desee pausar.

> [!IMPORTANT]
> Al emitir un comando de pausa, los dispositivos reciben este comando una vez que se registran con el servicio. Es posible que antes de que se registren, instalen una actualización programada.
> Además, si un dispositivo de destino está apagado cuando se emite el comando de pausa, al encenderse, podría descargar e instalar actualizaciones programadas antes de que se registre con Intune.

## <a name="windows-holographic-for-business-support"></a>Compatibilidad con Windows Holographic for Business

Windows Holographic for Business es compatible con las siguientes opciones de configuración:

- **Comportamiento de las actualizaciones automáticas**
- **Actualizaciones de productos de Microsoft**
- **Canal de servicio**