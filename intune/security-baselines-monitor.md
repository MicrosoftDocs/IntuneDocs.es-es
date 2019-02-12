---
title: 'Comprobación del éxito o error de las líneas de base de seguridad en Microsoft Intune: Azure | Microsoft Docs'
description: Compruebe el estado de error, conflicto y éxito al implementar líneas de base de seguridad en usuarios y dispositivos en MDM de Microsoft Intune. Vea cómo solucionar problemas mediante registros de cliente y las características de informes en Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfbdad6d98065a691528d4cdada0b6f9377e1109
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848243"
---
# <a name="monitor-the-security-baseline-and-profile-in-microsoft-intune"></a>Supervisión de la línea de base de seguridad y el perfil en Microsoft Intune

Hay distintas opciones de supervisión a la hora de utilizar líneas de base de seguridad. Puede supervisar el perfil de las líneas de base de seguridad que se aplica a los usuarios y dispositivos. También puede supervisar la línea de base real y todos los dispositivos que coinciden (o no) con los valores recomendados.

Este artículo le guiará a través de ambas opciones de supervisión.

Las [líneas de base de seguridad en Intune](security-baselines.md) proporcionan más detalles sobre la característica de las líneas de base de seguridad en Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Supervisión de la línea base y los dispositivos

Al supervisar la línea de base, obtiene conclusiones sobre el estado de seguridad de los dispositivos según las recomendaciones de Microsoft.

> [!NOTE]
> Tras asignar una línea de base por primera vez, los informes pueden tardar hasta 24 horas en actualizarse. Después, pueden tardar hasta 6 horas en actualizarse.

1. En [Azure Portal](https://portal.azure.com/), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Seleccione **Líneas base de seguridad (vista previa)** y seleccione una línea de base.
3. En **Información general**, el gráfico muestra cuántos dispositivos se ven afectados por la línea de base elegida y los diferentes estados:

    ![Comprobación del estado de los dispositivos](./media/security-baselines-monitor/overview.png)

    Están disponibles los siguientes estados:

    - **Matches baseline** (Coincide con la línea de base): todas las configuraciones de la línea de base coinciden con la configuración recomendada.
    - **Does not match baseline** (No coincide con la línea de base): al menos un valor de configuración de la línea de base no coincide con la configuración recomendada.
    - **Configuración errónea**: al menos un valor de configuración no está configurado correctamente. Este estado significa que la configuración está en un estado de conflicto, error o pendiente.
    - **No aplicable**: al menos un valor de configuración no es aplicable y no se aplica.

4. Seleccione uno de los estados que tenga dispositivos. Por ejemplo, seleccione el estado **Configuración errónea**.

5. Se muestra una lista de todos los dispositivos con ese estado. Seleccione un dispositivo específico para obtener más detalles. 

    En el ejemplo siguiente, seleccione **Configuración del dispositivo**  y seleccione el perfil con un estado de error:

    ![Comprobación del estado de los dispositivos](./media/security-baselines-monitor/device-configuration-profile-list.png)

    Seleccione el perfil con error. Se muestra una lista de todas las configuraciones del perfil y su estado. Ahora, puede desplazarse para encontrar la configuración que produce el error:

    ![Visualización de la configuración que causa el error](./media/security-baselines-monitor/profile-with-error-status.png)

Use este informe para ver cualquier configuración de un perfil que está provocando un problema. Obtenga también más detalles sobre las directivas y los perfiles implementados en los dispositivos.

> [!NOTE]
> Cuando se establece una propiedad en **No configurada** en la línea de base, la configuración se omite y no se aplican restricciones. La propiedad no se muestra en los informes.

## <a name="monitor-the-profile"></a>Supervisión del perfil

La supervisión del perfil proporciona conclusiones sobre el estado de implementación de los dispositivos, pero no el estado de seguridad según las recomendaciones de la línea de base.

1. En Intune, seleccione **Líneas base de seguridad**> seleccione una línea de base > **Profiles created** (Perfiles creados).

2. Seleccione un perfil. En **Información general**, la imagen muestra cuántos dispositivos y usuarios tienen asignado este perfil:

    ![Visualización del número de dispositivos y usuarios que tienen asignado el perfil de líneas de base de seguridad](./media/security-baselines-monitor/existing-profile-overview.png)

3. En **Administrar** > **Propiedades**, se muestra una lista de todas las configuraciones de la línea de base. También puede cambiar cualquiera de estas configuraciones:

    ![Visualización y actualización de la configuración en el perfil de las líneas de base de seguridad](./media/security-baselines-monitor/manage-settings.png)

4. En **Monitor**, puede ver el estado de implementación del perfil en dispositivos individuales, el estado de cada usuario y el estado de cada valor de configuración en la línea de base:

    ![Visualización de diferentes opciones de supervisión para un perfil de las líneas de base de seguridad](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>Solución de problemas utilizando el estado por valor de configuración

Ha implementado una línea de base de seguridad, pero el estado de implementación muestra un error. Los pasos siguientes ofrecen algunas instrucciones sobre cómo solucionar el error.

1. En Intune, seleccione **Líneas base de seguridad**> seleccione una línea de base > **Profiles created** (Perfiles creados).
2. Seleccione un perfil > **Monitor** > **Estado por valor**.
3. La tabla muestra todas las configuraciones y el estado de cada valor de configuración. Seleccione la columna **Error** o la columna **Conflicto** para ver el valor de configuración que causa el error.

### <a name="mdm-diagnostic-information"></a>Información de diagnóstico MDM

Ahora conoce el valor de configuración problemático. El siguiente paso es averiguar por qué este valor de configuración está causando un error o conflicto. 

En dispositivos con Windows 10, hay un informe de detalles de diagnóstico integrado de MDM. Este informe incluye valores predeterminados, valores actuales, enumera la directiva, muestra si se implementa en el dispositivo o el usuario, etc. Use este informe para ayudar a determinar por qué el valor de configuración está causando un conflicto o error.

1. En el dispositivo, vaya a **Configuración** > **Cuentas** > **Obtener acceso a trabajo o escuela**.
2. Seleccione la cuenta > **Información** > **Advanced Diagnostic Report (Informe de diagnóstico avanzado)** > **Crear informe**.
3. Elija **Exportar** y abra el archivo generado.
4. En el informe, busque el error o el valor de configuración conflictivo en las diferentes secciones del informe.

  Por ejemplo, busque en las secciones **Enrolled configuration sources and target resources** (Recursos de destino y orígenes de configuración inscritos) o **Unmanaged policies** (Directivas no administradas). Puede hacerse una idea de por qué está causando un error o conflicto.

En [Diagnose MDM failures in Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) (Diagnósticos de errores MDM en Windows 10) se proporciona más información sobre este informe integrado.

> [!TIP]
> - Algunas configuraciones también enumeran el GUID. Puede buscar este GUID en el registro local (regedit) para cualquier valor establecido.
> - Los registros del Visor de eventos también pueden incluir alguna información de error sobre el valor de configuración problemático (**Visor de eventos** > **Registros de aplicaciones y servicios** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**).

## <a name="next-steps"></a>Pasos siguientes

[Supervisar perfiles de dispositivo](device-profile-monitor.md) y [ver algunos problemas comunes y resoluciones](device-profile-troubleshoot.md).
