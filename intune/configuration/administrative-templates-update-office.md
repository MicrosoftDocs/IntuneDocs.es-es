---
title: Actualización de Office 365 con plantillas administrativas en Microsoft Intune - Azure | Microsoft Docs
description: Use plantillas administrativas en Microsoft Intune para actualizar las aplicaciones de Office 365 a la versión más reciente y elija la frecuencia con la que Office busca actualizaciones. Consulte las claves del registro del dispositivo que se actualizan cuando se aplica una directiva de Intune a Office Update.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf872387d6e6f4f91af9f074f54695b081b79119
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74549114"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>Uso de los parámetros Canal de actualización y Versión de destino para actualizar Office 365 con las plantillas administrativas de Microsoft Intune

En Intune, puede usar [plantillas de Windows 10 para configurar opciones de directiva de grupo](administrative-templates-windows.md). En este artículo se muestra cómo actualizar Office 365 mediante una plantilla administrativa en Intune. También proporciona instrucciones para confirmar que las directivas se aplican correctamente. Asimismo, esta información ayuda a solucionar problemas.

En este escenario, creará una plantilla administrativa en Intune que actualice Office 365 en los dispositivos.

Para más información sobre las plantillas administrativas, vea [Usar plantillas de Windows 10 para configurar opciones de directiva de grupo en Microsoft Intune](administrative-templates-windows.md).

Se aplica a:

- Windows 10 y versiones posteriores
- Office 365

## <a name="prerequisites"></a>Requisitos previos

Asegúrese de [habilitar las actualizaciones automáticas de Office 365 ProPlus](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus) para las aplicaciones de Office. Para ello, puede usar una directiva de grupo o la plantilla ADMX de Office 2016 de Intune:

![En la plantilla administrativa de Intune, establezca la opción Habilitar actualizaciones automáticas para Office.](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>Establecimiento del canal de actualización en la plantilla administrativa de Intune

1. En la [plantilla administrativa de Intune](administrative-templates-windows.md#create-a-template), vaya al ajuste **Canal de actualización** y especifique el canal que desee. Por ejemplo, elija `Semi-Annual Channel`:

    ![En la plantilla administrativa de Intune, establecimiento del ajuste Canal de actualización para Office](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > Se recomienda actualizar con más frecuencia. En este caso, se usa semestral solo como ejemplo.

2. Asegúrese de [asignar la directiva](device-profile-assign.md) a sus dispositivos Windows 10. Para probar la directiva antes, también puede sincronizarla:

    - [Sincronización de la directiva en Intune](../remote-actions/device-sync.md)
    - [Sincronización manual de la directiva en el dispositivo](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>Comprobación de las claves del Registro de Intune

Después de asignar la directiva y de que se sincronice el dispositivo, puede confirmar que la directiva se aplica:

1. En el dispositivo, abra la aplicación **Editor del Registro**.
2. Vaya a la ruta de acceso de la directiva de Intune: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.

    > [!TIP]
    > Cambia `<Provider ID>` en la clave del Registro. Para buscar el identificador de proveedor para el dispositivo, abra la aplicación **Editor del Registro** y vaya a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`. Se muestra el identificador del proveedor.

    Cuando se aplique la directiva, verá las siguientes claves del Registro:

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    En el ejemplo siguiente, verá que `L_UpdateBranch` tiene un valor similar a `<enabled /><data id="L_UpdateBranchID" value="Deferred" />`. Este valor significa que se establece en Semi-Annual Channel:

    ![Ejemplo de clave del Registro L_Updatebranch de la plantilla](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > [Administrar Office 365 ProPlus con Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager) enumera los valores y su significado. Los valores del Registro se basan en el canal de distribución seleccionado:
    >
    >- Monthly Channel                - value="Current"
    >- Monthly Channel (Targeted)     - value="Current"
    >- Semi-Annual Channel            - value="Current"
    >- Semi-Annual Channel (Targeted) - value="FirstReleaseDeferred"
    >- Insider Fast                   - value="InsiderFast"

En este momento, la directiva de Intune se aplica correctamente al dispositivo.

## <a name="check-the-office-registry-keys"></a>Comprobación de las claves del Registro de Office

1. En el dispositivo, abra la aplicación **Editor del Registro**.
2. Vaya a la ruta de acceso de la directiva de Office: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`.

    Verá las siguientes claves del Registro:

    - `UpdateChannel`: Una clave dinámica que cambia en función de los valores configurados.
    - `CDNBaseUrl`: Se establece cuando Office 365 se instala en el dispositivo.

3. Fíjese en el valor `UpdateChannel`. El valor indica la frecuencia con la que se actualiza Office. [Administrar Office 365 ProPlus con Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager) enumera los valores y su configuración.

    En el ejemplo siguiente, verá que `UpdateChannel` está establecido en `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`, que es **mensual**:

    ![Ejemplo de clave del Registro Office UpdateChannel de la plantilla administrativa](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    Este ejemplo significa que la directiva aún no se ha aplicado, ya que todavía está establecida en **mensual**, en lugar de **semestral**.

Esta clave del registro se actualiza cuando se ejecuta **Programador de tareas** > **Actualizaciones automáticas de Office 2.0** , o cuando un usuario inicia sesión en el dispositivo. Para confirmarlo, abra la tarea **Actualizaciones automáticas de Office 2.0** > **Desencadenadores**. En función de los desencadenadores, la clave del registro `UpdateChannel` puede tardar al menos un día o incluso más en actualizarse.

## <a name="force-office-automatic-updates-to-run"></a>Forzado de la ejecución de actualizaciones automáticas de Office

Para probar la directiva, puede forzar la configuración de la directiva en el dispositivo. Los pasos siguientes actualizan en Registro. Como siempre, tenga cuidado al actualizar el Registro.

1. Borre la clave del Registro:

    1. Vaya a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates`.
    2. Haga doble clic en la clave `UpdateDetectionLastRunTime`, elimine los datos del valor > **Aceptar**.

2. Ejecute la tarea de Actualizaciones automáticas de Office:

    1. Abra la aplicación **Programador de tareas** en el dispositivo.
    2. Expanda **Biblioteca de Programador de tareas** > **Microsoft** > **Office**.
    3. Seleccione **Actualizaciones automáticas de Office 2.0** > **Ejecutar**:

        ![Apertura del Programador de tareas y ejecución de Actualizaciones automáticas de Office](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        Espere a que finalice la tarea, lo cual puede tardar varios minutos.

3. En el **Editor del Registro**, vaya a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`. Compruebe el valor de `UpdateChannel`.

    Debe actualizarse con el valor establecido en la directiva. En nuestro ejemplo, el valor se debe establecer en `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`.

En este momento, el canal de actualización de Office se ha cambiado correctamente en el dispositivo. Puede abrir una aplicación de Office 365 para un usuario que reciba esta actualización para comprobar el estado.

## <a name="force-the-office-synchronization-to-update-account-information"></a>Forzado de la sincronización de Office para actualizar la información de la cuenta  

Si desea hacer más, puede forzar a Office a obtener la actualización de la versión más reciente. Los siguientes pasos solo deben realizarse como confirmación, o si necesita que los dispositivos obtengan rápidamente la última actualización de la versión de ese canal. De lo contrario, deje que Office realice su trabajo y actualice automáticamente.

### <a name="step-1-force-the-office-version-to-update"></a>Paso 1: Forzar la actualización de la versión de Office

1. Confirme que la versión de Office es compatible con el canal de actualización que está eligiendo. El [historial de actualizaciones de Office 365 ProPlus](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date) enumera los números de compilación que admiten los distintos canales de actualización.

2. En la [plantilla administrativa de Intune](administrative-templates-windows.md#create-a-template), vaya al ajuste **Versión de destino** y especifique el canal que desee.

    La configuración de la **Versión de destino** tiene un aspecto similar al siguiente:

    ![En la plantilla administrativa de Intune, establecimiento del ajuste Versión de destino para Office](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - Asegúrese de asignar la directiva.
> - Si cambia una directiva existente, los cambios afectarán a todos los usuarios asignados.
> - Si está probando esta característica, se recomienda crear una directiva de prueba y asignarla a un grupo de usuarios de prueba.

### <a name="step-2-check-the-office-version"></a>Paso 2: Comprobar la versión de Office

Considere la posibilidad de usar estos pasos para probar la directiva antes de implementarla para todos los usuarios.

1. En el **Editor del Registro**, vaya a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.

2. Fíjese en el valor `L_UpdateTargetVersion`. Una vez que se aplica la directiva, el valor se establece en la versión especificada, como `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`.

    En este momento, la directiva de Intune se aplica correctamente al dispositivo.

3. A continuación, puede forzar la actualización de Office. Abra una aplicación de Office, como Excel. Elija la opción para actualizar ahora (posiblemente en el menú **Cuenta**).

    El proceso de actualización tarda varios minutos. Puede confirmar que Office está intentando obtener la versión que especifique:

      1. En el dispositivo, vaya a `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`.
      2. Abra el archivo `VersionDescriptor.xml` y vaya a la sección `<Version>`. La versión disponible debe ser la misma que especificó en la directiva de Intune, como:

          ![Comprobación de la sección de versión del archivo XML de Office del descriptor de versión](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. Una vez instalada la actualización, la aplicación de Office debería mostrar la nueva versión (por ejemplo, en el menú **Cuenta**).

## <a name="next-steps"></a>Pasos siguientes

[Valores del canal de actualización para clientes de Office 365](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager)

[Información general del servicio de directivas de la nube de Office para Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[Usar plantillas de Windows 10 para configurar opciones de directiva de grupo (plantillas ADMX) en Microsoft Intune](administrative-templates-windows.md)
