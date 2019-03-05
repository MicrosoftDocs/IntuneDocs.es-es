---
title: 'Incorporación o definición de configuración de educación en Microsoft Intune: Azure | Microsoft Docs'
description: Use la aplicación Hacer un examen en un perfil de configuración de dispositivo en Windows 10 y dispositivos posteriores en Microsoft Intune. Cree un perfil de configuración mediante la configuración de educación y escriba una dirección URL de aplicación de examen, elija cómo los usuarios inician sesión, supervise la pantalla durante el examen y permita o evite sugerencias de texto durante el examen.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3c34935f161050bae51a2fbbee9b49f9fc1156f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228891"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>Uso de la aplicación Hacer un examen en dispositivos Windows 10 en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Los perfiles de educación en Intune están diseñados para que los alumnos realicen una prueba o un examen en dispositivos. Esta característica incluye la aplicación **Hacer un examen** y la configuración para agregar una dirección URL de examen, elegir cómo los usuarios finales inician sesión en el examen, etc. Esta característica es compatible con la siguiente plataforma:

- Windows 10 y versiones posteriores

Cuando el usuario inicia sesión, la aplicación Hacer un examen se abre automáticamente con el examen especificado. No se pueden ejecutar otras aplicaciones en el dispositivo mientras el examen está en curso. [Hacer exámenes en Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10) proporciona más detalles sobre la aplicación Hacer un examen.

En este artículo se enumeran los pasos para crear un perfil de configuración de dispositivos en Microsoft Intune. También incluye información para leer y obtener información sobre la configuración de educación disponible para los dispositivos Windows 10.

## <a name="create-a-device-profile"></a>Creación del perfil de un dispositivo

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
    - **Perfil**: elija **Perfil educativo**.

4. Escriba la configuración que desee definir:

    - [Windows 10 y versiones posteriores](education-settings-windows.md)

5. Seleccione **Aceptar** > **Crear** para guardar los cambios.

Después de escribir la configuración y crear el perfil, el perfil se muestra en la lista de perfiles. A continuación, [asigne este perfil a algunos grupos](device-profile-assign.md).

## <a name="next-steps"></a>Pasos siguientes

Consulte una lista de las [configuraciones de educación de Windows 10](education-settings-windows.md) y sus descripciones.

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
