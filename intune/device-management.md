---
title: Administrar dispositivos con Intune
titleSuffix: Intune on Azure
description: Aprenda a ver los dispositivos que administra con Intune y a realizar varias operaciones en ellos.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0686b3ece3a929cb06a29f4e58046872b70ec926
ms.sourcegitcommit: b8987b8dfb009ea55678d7f640ac5f18a6ab167e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>¿Qué es la administración de dispositivos de Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador de TI, debe asegurarse de que los dispositivos administrados proporcionan los recursos que necesitan los usuarios finales para hacer su trabajo y proteger esos datos de posibles riesgos.

La carga de trabajo de **Dispositivos**ofrece información sobre los dispositivos que administra y permite realizar tareas remotas en esos dispositivos. Para acceder a la carga de trabajo:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En **Intune**, elija **Dispositivos**.
4. Puede consultar la información sobre los dispositivos y realizar las acciones de dispositivo remoto siguientes:
    - **Información general**: una instantánea de los dispositivos inscritos que puede administrar.
    - **Todos los dispositivos**: una lista de los dispositivos inscritos que administra. Elija **Filtrar** o **Columnas** para restringir la información que se muestra. Seleccione un dispositivo para [ver el inventario del dispositivo](device-inventory.md).
    - **Dispositivos de Azure AD**: una lista de los dispositivos registrados o que se han unido a Azure Active Directory (AD). Obtenga más información sobre la [administración de dispositivos de Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
    - **Acciones de dispositivo**: un historial de las acciones remotas realizadas en dispositivos, en el que se incluye la acción, el estado, quién la inició y la hora.

    ![Supervisión de acciones de dispositivo](./media/monitor-device-actions.png)

    - **TeamViewer**: el servicio TeamViewer permite que los usuarios de dispositivos Android administrados por Intune obtengan asistencia remota de su administrador de TI. Obtenga más información sobre [TeamViewer](device-profile-android-teamviewer.md).

## <a name="available-device-actions"></a>Acciones de dispositivo disponibles
Las acciones disponibles dependen de la plataforma y la configuración del dispositivo.

- [Visualización del inventario de dispositivos](device-inventory.md)
- Realice acciones de dispositivo remoto:
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

- Elija **Acciones de dispositivo** para ver el estado de las acciones realizadas en los dispositivos que administra.
