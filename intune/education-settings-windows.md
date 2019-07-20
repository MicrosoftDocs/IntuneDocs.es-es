---
title: 'Configuración de educación de Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Vea una lista de todas las configuraciones de educación para dispositivos Windows 10. Use estas configuraciones en un perfil de configuración de dispositivo con la aplicación Hacer un examen, elija cómo los usuarios o alumnos inician sesión, supervise la pantalla durante el examen y mucho más en Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d5c78f72e7ffc580cce6cfec7237a3efe3ceb3e5
ms.sourcegitcommit: fd2499df5123758ecb093b4cdd486e35f713b040
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68230097"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Configuración de la aplicación Hacer un examen en dispositivos Windows 10 con Microsoft Intune

En este artículo se muestran las opciones de configuración de la aplicación Hacer un examen de educación de Microsoft Intune que puede definir en dispositivos que ejecutan Windows 10 y versiones posteriores. Mediante esta aplicación, los alumnos pueden iniciar sesión en un dispositivo y hacer un examen.

Estos valores se agregan a un perfil de configuración de dispositivo y luego se asignan o implementan en los dispositivos mediante Microsoft Intune.

[La aplicación Hacer un examen de Intune](education-settings-configure.md) proporciona más información sobre esta característica.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Configuración de Hacer un examen  

- **Tipo de cuenta**: elija cómo los usuarios inician sesión en la prueba. Las opciones son:
  - Cuenta de Azure AD
  - Cuenta de dominio
  - Cuenta local
- **Nombre de usuario de la cuenta**: escriba el nombre del usuario de la cuenta que se usa con la aplicación Take a Test. Puede especificar cuentas en el siguiente formato:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Dirección URL de evaluación**: escriba la dirección URL de la prueba que quiere que realicen los usuarios. Para más información sobre cómo obtener la dirección URL, vea la [documentación de Hacer un examen](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Supervisión de pantalla**: seleccione **Permitir** para supervisar la actividad de la pantalla mientras los usuarios realizan una prueba. **No configurada** impide la supervisión de la pantalla durante el examen.
- **Sugerencia de texto**: elija **Permitir** para que los usuarios que realizan la prueba puedan ver sugerencias de texto. **No configurada** bloquea las sugerencias de texto mientras los usuarios realizan un examen.

## <a name="next-steps"></a>Pasos siguientes

El perfil se crea, pero puede que todavía no haga nada. Asegúrese de [asignar el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).
