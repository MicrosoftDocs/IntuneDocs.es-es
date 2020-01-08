---
title: 'Administrar dispositivos con Microsoft Intune: Azure | Microsoft Docs'
description: Revise los dispositivos que administra con Microsoft Intune, incluida la exportación de una lista de dispositivos a formato csv, vea los dispositivos unidos a Azure Active Directory, revise un registro de cambio de acciones en el dispositivo, use TeamViewer Connector para permitir que los administradores de TI solucionen problemas de dispositivos Android de forma remota y vea todas las acciones que se pueden ejecutar en los dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
redirect_url: https://docs.microsoft.com/intune
ms.openlocfilehash: ff82b1ed70d3021c33a166c694e3efe5d10905e0
ms.sourcegitcommit: e4602481a25a5e12379f673dfe801c611f51c35b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75731371"
---
# <a name="what-is-microsoft-intune-device-management"></a>¿Qué es la administración de dispositivos de Microsoft Intune?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Como administrador de TI, debe asegurarse de que los dispositivos administrados proporcionan los recursos que necesitan los usuarios para hacer su trabajo y proteger esos datos de posibles riesgos.

La carga de trabajo de **Dispositivos**ofrece información sobre los dispositivos que administra y permite realizar tareas remotas en esos dispositivos.

## <a name="get-to-your-devices"></a>Ir a los dispositivos

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Dispositivos**. Esta vista muestra información detallada sobre los dispositivos individuales y lo que se puede hacer con ellos, lo que incluye:

   - **Información general** muestra una instantánea visual de los dispositivos inscritos y además muestra cuántos dispositivos usan las diferentes plataformas, incluidas Android, iOS, etc.
   - **Todos los dispositivos** muestra una lista de los dispositivos inscritos que administra.

     Use la característica **Exportar** para crear una lista .csv de todos los dispositivos, en incrementos de 10.000 (Internet Explorer) o de 30.000 (Microsoft Edge y Chrome).

     Seleccione cualquier dispositivo para [ver detalles adicionales sobre ese dispositivo](device-inventory.md), incluidos detalles de hardware, aplicaciones instaladas, estado de la directiva de cumplimiento, etc.

   - **Dispositivos de Azure AD** muestra una lista de los dispositivos registrados o unidos a Azure Active Directory (Azure AD). Obtenga más información sobre la [administración de dispositivos de Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - **Acciones de dispositivo** incluye un historial de las acciones remotas realizadas en distintos dispositivos, en el que se incluye la acción, el estado, quién la inició y la hora.

     ![Captura de pantalla de supervisión de acciones de dispositivo](./media/device-management/monitor-device-actions.png)

   - **Registros de auditoría** es un registro de las actividades que generan un cambio en Intune. [Registros de auditoría](../fundamentals/monitor-audit-logs.md) proporciona más detalles.
   - **TeamViewer Connector** es un servicio que permite que los usuarios de dispositivos Android administrados por Intune obtengan asistencia remota de su administrador de TI. Obtenga más información sobre [TeamViewer](teamviewer-support.md).
   - **Ayuda y soporte técnico** proporciona un acceso directo para obtener sugerencias de solución de problemas, solicitar soporte técnico o comprobar el estado de Intune.

## <a name="available-device-actions"></a>Acciones de dispositivo disponibles
Las acciones disponibles dependen de la plataforma y la configuración del dispositivo.

- [Visualización del inventario de dispositivos](device-inventory.md)
- Ejecute las acciones de dispositivo remoto:
  - [Retirar](devices-wipe.md#retire)
  - [Borrar](devices-wipe.md#wipe)
  - [Bloqueo remoto](device-remote-lock.md)
  - [Restablecer el código de acceso](device-passcode-reset.md)
  - [Omitir Bloqueo de activación](device-activation-lock-bypass.md) (solo para iOS)
  - [Comienzo de cero](device-fresh-start.md) (solo para Windows)
  - [Modo perdido](device-lost-mode.md) (solo para iOS)
  - [Buscar dispositivo](device-locate.md) (solo para iOS)
  - [Reiniciar](device-restart.md) (solo para Windows)
  - [Restablecimiento del PIN de Windows 10](device-windows-pin-reset.md)
  - [Control remoto en Android](teamviewer-support.md)
  - [Sincronización del dispositivo](device-sync.md)
  - [Cambio de nombre de un dispositivo](device-rename.md)
  - [Envío de notificaciones personalizadas](custom-notifications.md#send-a-custom-notification-to-a-single-device) (Android, iOS)
  - [Rotación de claves de BitLocker](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) (solo Windows)

## <a name="next-steps"></a>Pasos siguientes

- En **Todos los dispositivos**, seleccione un dispositivo para ver más detalles sobre ese dispositivo concreto.
- Elija **Acciones de dispositivo** para ver el estado de las acciones realizadas en los dispositivos que administra.
