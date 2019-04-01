---
title: 'Configuración para dispositivos compartidos con Windows Holographic for Business: Microsoft Intune (Azure) | Microsoft Docs'
description: Agregue y use Windows Holographic for Business para configurar dispositivos compartidos o que varios usuarios empleen en Microsoft Intune. Consulte una lista de las opciones de configuración de administración de cuentas y qué hacen en los dispositivos, incluido Microsoft HoloLens.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 151ceaa40f2993d3160b9de34eee92e53c35925d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565866"
---
# <a name="windows-holographic-for-business-settings-to-manage-shared-devices-using-intune"></a>Opciones de configuración de Windows Holographic for Business para administrar dispositivos compartidos con Intune

Es posible que varios usuarios empleen dispositivos con Windows Holographic, como Microsoft HoloLens. Los dispositivos con varios usuarios se denominan dispositivos compartidos y son parte de las soluciones de la administración de dispositivos móviles (MDM).

Con Microsoft Intune, los usuarios pueden iniciar sesión en estos dispositivos compartidos con una cuenta de invitado. Al usar el dispositivo, solamente tendrán acceso a las características que permita.

En este artículo se describen las opciones de configuración que usa en un perfil de configuración de dispositivos con Windows Holographic for Business. Tras crear el perfil en Intune, implementará o asignará el perfil en los grupos de dispositivos de su organización. También puede asignar este perfil a un grupo de dispositivos con distintos tipos de dispositivo y versiones del SO.

Para obtener más información sobre esta característica de Intune, vea [Control access, accounts, and power features on shared PC or multi-user devices](shared-user-device-settings.md) (Control del acceso, las cuentas y las características de energía en dispositivos con varios usuarios o equipos compartidos). Para obtener más información sobre el CSP de Windows, vea [AccountManagement CSP](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp) (CSP de AccountManagement).

## <a name="before-your-begin"></a>Antes de empezar

[Cree el perfil](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Configuración de dispositivos compartidos con varios usuarios

> [!NOTE]
> Los dispositivos que ejecutan Windows Holographic for Business, incluido Microsoft HoloLens, solo admiten las opciones de configuración de **Administración de cuentas**. El hecho de configurar cualquier otra de las opciones de Intune, incluida **Modo de PC compartido**, no tendrá ningún efecto sobre estos dispositivos.

- **Administración de cuentas**: establezca esta opción en **Habilitar** para eliminar de forma automática las cuentas locales creadas por invitados y las cuentas en AD y Azure AD. Cuando un usuario cierre sesión en el dispositivo, o cuando se ejecute el mantenimiento del sistema, estas cuentas se eliminarán. Al habilitar esta opción, también deberá establecer lo siguiente:
  - **Eliminación de la cuenta**: elegir cuándo se eliminan las cuentas: **al umbral de espacio de almacenamiento**, **al umbral de espacio de almacenamiento y el umbral inactiva**, o **inmediatamente después de cierre de sesión** . Indique también:
    - **Comience a eliminar threshold(%)**: escriba un porcentaje (0-100) de espacio en disco. Cuando el espacio de almacenamiento o en disco sea inferior al valor indicado, las cuentas en caché se eliminarán. Se eliminan las cuentas continuamente para recuperar espacio en disco. Las cuentas que lleven más tiempo inactivas serán las primeras en eliminarse.
    - **Detener la eliminación threshold(%)**: escriba un porcentaje (0-100) de espacio en disco. Cuando el espacio de almacenamiento o en disco alcance el valor indicado, la eliminación se detendrá.

  Establezca esta opción en **Deshabilitar** para mantener las cuentas locales, de AD y de Azure AD creadas por invitados.

  > [!NOTE]
  > Solo los dispositivos Microsoft HoloLens admiten las opciones de configuración de **Administración de cuentas**.

## <a name="next-steps"></a>Pasos siguientes

- [Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
- Consulte la configuración para [Windows 10 y versiones más recientes](shared-user-device-settings-windows.md).
