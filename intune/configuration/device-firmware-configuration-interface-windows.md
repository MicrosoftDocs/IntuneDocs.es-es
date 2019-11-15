---
title: 'Actualización de las características de Windows BIOS mediante directivas MDM en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue un perfil de Device Firmware Configuration Interface (DFCI) para administrar la configuración de UEFI, como la CPU, el hardware integrado y las opciones de arranque en dispositivos Windows 10 en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 899d667ca271ae5c3edced18fab8da987c49b2ca
ms.sourcegitcommit: 85c894cb4df34a5ff558e3b45e28a8b91054d9e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432527"
---
# <a name="use-device-firmware-configuration-interface-profiles-on-windows-devices-in-microsoft-intune-public-preview"></a>Uso de perfiles de Device Firmware Configuration Interface en dispositivos Windows en Microsoft Intune (versión preliminar pública)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cuando se usa Intune para administrar dispositivos Autopilot, puede administrar la configuración de UEFI (BIOS) una vez inscritos, mediante Device Firmware Configuration Interface (DFCI). Para obtener información general sobre las ventajas, los escenarios y los requisitos previos, vea [Introducción a DFCI](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Dfci_Feature/).

DFCI [permite a Windows](https://docs.microsoft.com/windows/client-management/mdm/uefi-csp) pasar comandos de administración de Intune a UEFI (Unified Extensible Firmware Interface).

En Intune, use esta característica para controlar la configuración del BIOS. Normalmente, el firmware es más resistente a los ataques malintencionados. Limita el control de los usuarios finales sobre el BIOS, lo que es adecuado en una situación de peligro.

Por ejemplo, usa dispositivos Windows 10 en un entorno seguro y quiere deshabilitar la cámara. Puede deshabilitar la cámara en el nivel de firmware, por lo que no importa lo que haga el usuario final. La reinstalación del sistema operativo o el borrado del equipo no volverán a activar la cámara. En otro ejemplo, bloquea las opciones de arranque para impedir que los usuarios arranquen otro sistema operativo, o bien una versión anterior de Windows que no tenga las mismas características de seguridad.

Al volver a instalar una versión anterior de Windows, un sistema operativo independiente o formatear la unidad de disco duro, no se puede invalidar la administración de DFCI. Esta característica puede impedir que el malware se comunique con los procesos del sistema operativo, incluidos los que tienen privilegios elevados. La cadena de confianza de DFCI usa criptografía de clave pública y no depende de la seguridad de contraseña de UEFI (BIOS) local. Este nivel de seguridad impide que los usuarios locales accedan a la configuración administrada desde los menús de UEFI (BIOS) del dispositivo.

Esta característica se aplica a:

- Windows 10 RS5 (1809) y versiones posteriores en UEFI compatible

## <a name="before-you-begin"></a>Antes de comenzar

- El fabricante del dispositivo debe haber agregado DFCI a su firmware de UEFI en el proceso de fabricación, o bien como una actualización de firmware para instalar. Trabaje con los proveedores de dispositivos para determinar los [fabricantes que admiten DFCI](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci) o la versión de firmware necesaria para usar DFCI.

- El dispositivo debe estar registrado para Windows Autopilot por un [asociado de Proveedor de soluciones en la nube (CSP) de Microsoft](https://partner.microsoft.com/cloud-solution-provider) o registrado directamente por el OEM. 

  Los dispositivos registrados de forma manual para Autopilot, como los [importados desde un archivo CSV](../enrollment/enrollment-autopilot.md#add-devices), no pueden usar DFCI. Por diseño, la administración de DFCI requiere la atestación externa de la adquisición comercial del dispositivo a través de un OEM o un registro de asociado de CSP de Microsoft en Windows Autopilot.

  Una vez registrado el dispositivo, el número de serie se muestra en la lista de dispositivos Windows Autopilot.

  Para más información sobre Autopilot, incluidos los requisitos, vea [Inscripción de dispositivos Windows en Intune con Windows Autopilot](../enrollment/enrollment-autopilot.md).

## <a name="create-your-azure-ad-security-groups"></a>Creación de los grupos de seguridad de Azure AD

Los perfiles de implementación de Autopilot se asignan a grupos de seguridad de Azure AD. Asegúrese de crear grupos que incluyan los dispositivos compatibles con DFCI. Para los dispositivos DFCI, la mayoría de las organizaciones pueden crear grupos de dispositivos, en lugar de grupos de usuarios. Tenga en cuenta los siguientes escenarios:

- Recursos Humanos (RR.HH.) tiene distintos dispositivos Windows. Por motivos de seguridad, no quiere que nadie de este grupo use la cámara de los dispositivos. En este escenario, puede crear un grupo de usuarios de seguridad de RR.HH. para que la directiva se aplique a los usuarios del grupo de RR.HH, con independencia del tipo de dispositivo.
- En la planta de fabricación, tiene 10 dispositivos. En todos los dispositivos, quiere impedir el arranque desde un dispositivo USB. En este escenario, puede crear un grupo de dispositivos de seguridad y agregar estos 10 dispositivos al grupo.

Para más información sobre la creación de grupos en Intune, vea [Adición de grupos para organizar usuarios y dispositivos](../fundamentals/groups-add.md).

## <a name="create-the-profiles"></a>Creación de los perfiles

Para usar DFCI, cree los perfiles siguientes y asígnelos al grupo.

### <a name="create-an-autopilot-deployment-profile"></a>Crear un perfil de implementación de Autopilot

Este perfil configura y configura previamente nuevos dispositivos. En [Perfil de implementación Autopilot ](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) se enumeran los pasos para crear el perfil.

### <a name="create-an-enrollment-state-page-profile"></a>Creación de un perfil de página de estado de inscripción

Este perfil garantiza que los dispositivos se comprueban y se habilitan para DFCI durante la configuración de Windows. Se recomienda encarecidamente usar este perfil para bloquear el uso del dispositivo hasta que se hayan instalado todas las aplicaciones y perfiles. En el [perfil de página de estado de inscripción](../enrollment/windows-enrollment-status.md) se muestran los pasos para crear el perfil.

### <a name="create-the-dfci-profile"></a>Creación del perfil de DFCI

Este perfil incluye los valores de DFCI que configure.

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a las directivas para que pueda identificarlas de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil es **Windows: Configuración de valores de DFCI en dispositivos Windows**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
    - **Tipo de perfil**: seleccione **Device Firmware Configuration Interface**.

4. Defina la configuración:

    - **Allow local user to change UEFI (BIOS) settings** (Permitir que el usuario local cambie la configuración de UEFI (BIOS)): Las opciones son:
      - **Solo valores no configurados**: el usuario local puede cambiar cualquier opción de configuración *excepto* las establecidas de forma explícita en **Habilitar** o **Deshabilitar** por Intune.
      - **Ninguna**: el usuario local no puede cambiar la configuración de UEFI (BIOS), incluida la que no se muestra en el perfil de DFCI.

    - **Virtualización de E/S y CPU**: Las opciones son:
        - **No configurado**: Intune no cambia esta característica y deja los valores sin modificar.
        - **Habilitada**: el BIOS habilita las funciones de virtualización de E/S y CPU de la plataforma para su uso por parte del sistema operativo. Activa la seguridad basada en la virtualización de Windows y las tecnologías de Device Guard.
        - **Deshabilitar**: el BIOS deshabilita las funciones de virtualización de E/S y CPU de la plataforma y evita que se usen.
    - **Cámaras**: Las opciones son:
        - **No configurado**: Intune no cambia esta característica y deja los valores sin modificar.
        - **Habilitada**: se habilitan todas las cámaras integradas administradas directamente mediante UEFI (BIOS). Los periféricos, como las cámaras USB, no se ven afectados.
        - **Deshabilitado**: se deshabilitan todas las cámaras integradas administradas directamente mediante UEFI (BIOS). Los periféricos, como las cámaras USB, no se ven afectados.
    - **Micrófonos y altavoces**:  Las opciones son:
        - **No configurado**: Intune no cambia esta característica y deja los valores sin modificar.
        - **Habilitada**: se habilitan todos los micrófonos y altavoces integrados administrados directamente mediante UEFI (BIOS). Los periféricos, como los dispositivos USB, no se ven afectados.
        - **Deshabilitado**: se deshabilitan todos los micrófonos y altavoces integrados administrados directamente mediante UEFI (BIOS). Los periféricos, como los dispositivos USB, no se ven afectados.
    - **Señales de radio (Bluetooth, Wi-Fi, NFC, etc.)** : Las opciones son:
        - **No configurado**: Intune no cambia esta característica y deja los valores sin modificar.
        - **Habilitada**: se habilitan todas las señales de radio administradas directamente mediante UEFI (BIOS). Los periféricos, como los dispositivos USB, no se ven afectados.
        - **Deshabilitado**: se deshabilitan todas las señales de radio administradas directamente mediante UEFI (BIOS). Los periféricos, como los dispositivos USB, no se ven afectados.

        > [!WARNING]
        > Si deshabilita el valor **Señales de radio**, el dispositivo requiere una conexión de red por cable. De lo contrario, es posible que el dispositivo no se pueda administrar.

    - **Arrancar desde medio externo (USB, SD)** : Las opciones son:
        - **No configurado**: Intune no cambia esta característica y deja los valores sin modificar.
        - **Habilitada**: UEFI (BIOS) permite el arranque desde almacenamiento que no sea un disco duro.
        - **Deshabilitado**: UEFI (BIOS) no permite el arranque desde almacenamiento que no sea un disco duro.
    - **Arrancar desde adaptadores de red**:  Las opciones son:
        - **No configurado**: Intune no cambia esta característica y deja los valores sin modificar.
        - **Habilitada**: UEFI (BIOS) permite el arranque desde interfaces de red integradas.
        - **Deshabilitado**: UEFI (BIOS) no permite el arranque desde interfaces de red integradas.

5. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios. El perfil se crea y se muestra en la lista.

## <a name="assign-the-profiles-and-reboot"></a>Asignación de los perfiles y reinicio

Una vez creados los perfiles, están [listos para asignarlos](../configuration/device-profile-assign.md). Asegúrese de asignar los perfiles a los grupos de seguridad de Azure AD que incluyan los dispositivos DFCI.

La próxima vez que se sincronice el dispositivo o se reinicie, se aplicará la configuración del perfil de DFCI. Una vez que se aplique la directiva, reinicie el dispositivo.

Cuando el dispositivo ejecuta el programa de instalación de dispositivos de Windows, DFCI puede forzar un reinicio durante la página de estado de inscripción. Una vez que ha finalizado la instalación, puede confirmar que la configuración de DFCI está activa si reinicia el dispositivo. Después, use las instrucciones del fabricante del dispositivo para abrir el menú de UEFI.

## <a name="update-existing-dfci-settings"></a>Actualización de la configuración existente de DFCI

Si quiere cambiar la configuración existente de DFCI en los dispositivos en uso, puede hacerlo. En el perfil de DFCI existente, cambie la configuración y guarde los cambios. Como el perfil ya está asignado, la nueva configuración de DFCI surte efecto cuando:

1. El dispositivo se registra con el servicio de Intune para revisar las actualizaciones del perfil. Los registros se producen varias veces. Para más información, vea [cuándo obtienen los dispositivos actualizaciones de directivas, perfiles o aplicaciones](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

2. Para aplicar la nueva configuración, reinicie el dispositivo [de forma remota](../remote-actions/device-restart.md) o local.

También puede [señalar dispositivos para que se registren](../remote-actions/device-sync.md). Después de una sincronización correcta, [señale para reiniciar](../remote-actions/device-restart.md).

>[!NOTE]
> La eliminación del perfil de DFCI o la eliminación de un dispositivo del grupo asignado al perfil no quita la configuración de DFCI ni vuelve a habilitar los menús de UEFI (BIOS). Si quiere dejar de usar DFCI, actualice el perfil de DFCI existente. Para más información sobre los pasos, vea [Retirada del dispositivo](#retire) en este artículo.

## <a name="reuse-retire-or-recover-the-device"></a>Reutilización, retirada o recuperación del dispositivo

### <a name="reuse"></a>Reutilización

Si tiene previsto restablecer Windows para reasignar el dispositivo, [borre el dispositivo ](../remote-actions/devices-wipe.md). **No** quite el registro del dispositivo Autopilot.

Después de borrar el dispositivo, mueva el dispositivo al grupo asignado a los nuevos perfiles de DFCI y Autopilot. Asegúrese de reiniciar el dispositivo para volver a ejecutar la configuración de Windows.

### <a name="retire"></a>Retirar

Cuando esté listo para retirar el dispositivo y liberarlo de la administración, actualice el perfil de DFCI a la configuración de UEFI (BIOS) que quiera en el estado de salida. Normalmente, querrá habilitar todas las opciones. Por ejemplo:

1. Abra el perfil de DFCI (**Configuración del dispositivo** > **Perfiles**).
2. Cambie **Allow local user to change UEFI (BIOS) settings** (Permitir que el usuario local cambie la configuración de UEFI (BIOS)) a **Solo valores no configurados**.
3. Establezca el resto de los valores en **No configurado**.
4. Guarde la configuración.

Con estos pasos se desbloquean los menús de UEFI (BIOS) del dispositivo. Los valores siguen siendo los mismos que en el perfil (**Habilitado**  o **Deshabilitado**), y no se vuelven a establecer en ningún valor de sistema operativo predeterminado.

Ya está listo para borrar el dispositivo. Una vez que se ha borrado el dispositivo, elimine el registro de Autopilot. Al eliminar el registro se impide que el dispositivo se vuelva a inscribir de forma automática cuando se reinicie.

### <a name="recover"></a>Recuperación

Si borra un dispositivo y elimina el registro de Autopilot antes de desbloquear los menús de UEFI (BIOS), los menús permanecen bloqueados. Intune no puede enviar actualizaciones de perfil para desbloquearlo.

Para desbloquear el dispositivo, abra el menú UEFI (BIOS) y actualice la administración desde la red. La recuperación desbloquea los menús, pero deja toda la configuración de UEFI (BIOS) establecida en los valores del perfil de DFCI de Intune anterior.

## <a name="end-user-impact"></a>Impacto en el usuario final

Cuando se aplica la directiva de DFCI, los usuarios locales no pueden cambiar la configuración establecida por DFCI, incluso si el menú de UEFI (BIOS) está protegido mediante una contraseña. En función de la configuración que establezca, es posible que los usuarios finales reciban errores sobre componentes de hardware que no se encuentran o que no se pueden diagnosticar. Asegúrese de proporcionar documentación a los usuarios finales en la que se expliquen las opciones que ha deshabilitado.  

## <a name="next-steps"></a>Pasos siguientes

Después de asignar el perfil, [supervise su estado](../device-profile-monitor.md).
