---
title: 'Configuración de educación de Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Vea una lista de todas las configuraciones de educación para dispositivos Windows 10. Use estas configuraciones en un perfil de configuración de dispositivo con la aplicación Hacer un examen, elija cómo los usuarios o alumnos inician sesión, supervise la pantalla durante el examen y mucho más en Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae26d35a50ffd2b5b40f262ddebeab8d53d87223
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846713"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Configuración de la aplicación Hacer un examen en dispositivos Windows 10 con Microsoft Intune

En este artículo se muestran las opciones de configuración de la aplicación Hacer un examen de educación de Microsoft Intune que puede definir en dispositivos que ejecutan Windows 10 y versiones posteriores. Mediante esta aplicación, los alumnos pueden iniciar sesión en un dispositivo y hacer un examen.

Estos valores se agregan a un perfil de configuración de dispositivo y luego se asignan o implementan en los dispositivos mediante Microsoft Intune.

[La aplicación Hacer un examen de Intune](education-settings-configure.md) proporciona más información sobre esta característica.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Configuración de Hacer un examen

- **Tipo de cuenta**: elija cómo los usuarios inician sesión en el examen. Las opciones son:
  - Cuenta de Azure AD
  - Cuenta de dominio
  - Cuenta local
- **Nombre de usuario de la cuenta**: especifique el nombre del usuario de la cuenta que utiliza con Hacer un examen. Puede especificar cuentas en el siguiente formato:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Dirección URL de evaluación**: especifique la dirección URL del examen que desea que los usuarios realicen. Para más información sobre cómo obtener la dirección URL, vea la [documentación de Hacer un examen](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Supervisión de pantalla**: elija **Permitir** para supervisar la actividad de la pantalla mientras los usuarios realizan una prueba. **No configurada** impide la supervisión de la pantalla durante el examen.
- **Sugerencia de texto**: elija **Permitir** para que los que hacen el examen puedan ver sugerencias de texto. **No configurada** bloquea las sugerencias de texto mientras los usuarios realizan un examen.

## <a name="next-steps"></a>Pasos siguientes

El perfil se crea, pero puede que todavía no haga nada. Asegúrese de [asignar el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).
