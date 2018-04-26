---
title: 'Administrar dispositivos con Microsoft Intune: Azure | Microsoft Docs'
description: Revise los dispositivos que administra con Microsoft Intune, incluida la exportación de una lista de dispositivos a formato csv, vea los dispositivos unidos a Azure Active Directory, revise un registro de cambio de acciones en el dispositivo, use TeamViewer Connector para permitir que los administradores de TI solucionen problemas de dispositivos Android de forma remota y vea todas las acciones que se pueden ejecutar en los dispositivos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/02/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9a003b9ec4208bc3449dfb1b3b2ee889a29b742b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="what-is-microsoft-intune-device-management"></a>¿Qué es la administración de dispositivos de Microsoft Intune?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador de TI, debe asegurarse de que los dispositivos administrados proporcionan los recursos que necesitan los usuarios para hacer su trabajo y proteger esos datos de posibles riesgos.

La carga de trabajo de **Dispositivos**ofrece información sobre los dispositivos que administra y permite realizar tareas remotas en esos dispositivos.

## <a name="get-to-your-devices"></a>Ir a los dispositivos

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos**. Esta vista muestra información detallada sobre los dispositivos individuales y lo que se puede hacer con ellos, lo que incluye:

   - **Información general** muestra una instantánea visual de los dispositivos inscritos y además muestra cuántos dispositivos usan las diferentes plataformas, incluidas Android, iOS, etc.
   - **Todos los dispositivos** muestra una lista de los dispositivos inscritos que administra.

     Use la característica **Exportar** para crear una lista .csv de todos los dispositivos, en incrementos de 10.000 (Internet Explorer) o 30.000 (Edge, Chrome).

     Seleccione cualquier dispositivo para [ver detalles adicionales sobre ese dispositivo](device-inventory.md), incluidos detalles de hardware, aplicaciones instaladas, estado de la directiva de cumplimiento, etc.

   - **Dispositivos de Azure AD** muestra una lista de los dispositivos registrados o unidos a Azure Active Directory (Azure AD). Obtenga más información sobre la [administración de dispositivos de Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - **Acciones de dispositivo** incluye un historial de las acciones remotas realizadas en distintos dispositivos, en el que se incluye la acción, el estado, quién la inició y la hora.

     ![Captura de pantalla de supervisión de acciones de dispositivo](./media/monitor-device-actions.png)

   - **Registros de auditoría** es un registro de las actividades que generan un cambio en Intune. [Registros de auditoría](monitor-audit-logs.md) proporciona más detalles.
   - **TeamViewer Connector** es un servicio que permite que los usuarios de dispositivos Android administrados por Intune obtengan asistencia remota de su administrador de TI. Obtenga más información sobre [TeamViewer](device-profile-android-teamviewer.md).
   - **Ayuda y soporte técnico** proporciona un acceso directo para obtener sugerencias de solución de problemas, solicitar soporte técnico o comprobar el estado de Intune.

## <a name="available-device-actions"></a>Acciones de dispositivo disponibles
Las acciones disponibles dependen de la plataforma y la configuración del dispositivo.

- [Visualización del inventario de dispositivos](device-inventory.md)
- Ejecute las acciones de dispositivo remoto:
    - [Eliminar datos de la compañía](devices-wipe.md#remove-company-data)
    - [Restablecimiento de la configuración de fábrica](devices-wipe.md#factory-reset)
    - [Bloqueo remoto](device-remote-lock.md)
    - [Restablecer el código de acceso](device-passcode-reset.md)
    - [Omitir Bloqueo de activación](device-activation-lock-bypass.md) (solo para iOS)
    - [Comienzo de cero](device-fresh-start.md) (solo para Windows)
    - [Modo perdido](device-lost-mode.md) (solo para iOS)
    - [Buscar dispositivo](device-locate.md) (solo para iOS)
    - [Reiniciar](device-restart.md) (solo para Windows)
    - [Restablecimiento del PIN de Windows 10](device-windows-pin-reset.md)
    - [Control remoto en Android](device-profile-android-teamviewer.md)
    - [Sincronización del dispositivo](device-sync.md)

## <a name="next-steps"></a>Pasos siguientes

- En **Todos los dispositivos**, seleccione un dispositivo para ver más detalles sobre ese dispositivo concreto.
- Elija **Acciones de dispositivo** para ver el estado de las acciones realizadas en los dispositivos que administra.
