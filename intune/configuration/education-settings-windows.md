---
title: 'Configuración de educación de Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Vea una lista de todas las configuraciones de educación para dispositivos Windows 10. Use estas configuraciones en un perfil de configuración de dispositivo con la aplicación Hacer un examen, elija cómo los usuarios o alumnos inician sesión, supervise la pantalla durante el examen y mucho más en Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d89f512c06dcfbf6f6ddaba5e17ac9ca6f0becf
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506795"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Configuración de la aplicación Hacer un examen en dispositivos Windows 10 con Microsoft Intune

La aplicación de prueba le permite administrar de forma segura las pruebas en línea en los dispositivos Windows 10 de su aula. Para configurar la aplicación de prueba, debe crear un perfil de configuración de dispositivo en Intune y configurar las opciones de evaluación segura. En este artículo se describe la configuración que encontrará para realizar una aplicación de prueba. 

Una vez configurado el perfil, asígnelo a los estudiantes. 

[La aplicación Hacer un examen de Intune](education-settings-configure.md) proporciona más información sobre esta característica.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Configuración de Hacer un examen
Después de crear un perfil de configuración de dispositivo, vaya a **tipo de perfil** y seleccione **evaluación segura (educación)** . Encontrará la siguiente configuración de aplicación de prueba. 


- **Tipo de cuenta**: elija cómo los usuarios inician sesión en la prueba. Las opciones son:
  - Cuenta de Azure AD
  - Cuenta de dominio
  - Cuenta local
  - Cuenta de invitado local: solo está disponible en dispositivos que ejecutan Windows 10, versión 1903 y versiones posteriores.    
- **Nombre de usuario de la cuenta**: escriba el nombre del usuario de la cuenta que se usa con la aplicación Take a Test. Puede especificar cuentas en el siguiente formato:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Nombre de cuenta**: para configurar un tipo de cuenta de invitado local, escriba el nombre de la cuenta que se usa con la aplicación Take a test. El nombre de la cuenta aparecerá como un icono en la pantalla de inicio de sesión. Los estudiantes deben hacer clic en el icono para iniciar la prueba.  
- **Dirección URL de evaluación**: escriba la dirección URL de la prueba que quiere que realicen los usuarios. Para más información sobre cómo obtener la dirección URL, vea la [documentación de Hacer un examen](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Conexión de impresora**: elija **requerir** para permitir solo el acceso a la aplicación de prueba desde dispositivos conectados a una impresora. Esta opción también hace que el botón Imprimir de la aplicación esté disponible para las pruebas. **No configurado** permite a los estudiantes tener acceso a la aplicación desde dispositivos que no están conectados a una impresora.  
- **Supervisión de pantalla**: seleccione **Permitir** para supervisar la actividad de la pantalla mientras los usuarios realizan una prueba. **No configurada** impide la supervisión de la pantalla durante el examen.
- **Sugerencia de texto**: elija **Permitir** para que los usuarios que realizan la prueba puedan ver sugerencias de texto. **No configurada** bloquea las sugerencias de texto mientras los usuarios realizan un examen.

## <a name="next-steps"></a>Pasos siguientes

Asegúrese de [asignar el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).
