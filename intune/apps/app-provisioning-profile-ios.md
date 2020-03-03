---
title: Perfiles de aprovisionamiento de aplicaciones iOS/iPadOS en Microsoft Intune
titleSuffix: ''
description: Intune proporciona las herramientas para asignar proactivamente un nuevo perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f40b6f458a95a466874a2d1ce44fcafa37249d46
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513634"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Uso de perfiles de aprovisionamiento de aplicaciones para iOS para evitar que las aplicaciones expiren

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>Introducción

Las aplicaciones de línea de negocio iOS/iPadOS de Apple asignadas a iPhone e iPad se crean con un perfil de aprovisionamiento incluido y un código firmado con un certificado. Cuando se ejecuta la aplicación, iOS/iPadOS confirma la integridad de la aplicación iOS/iPadOS y exige el cumplimiento de las directivas definidas por el perfil de aprovisionamiento. Se producen las validaciones siguientes:

- **Integridad del archivo de instalación**: iOS/iPadOS compara los detalles de las aplicaciones con la clave pública del certificado de firma de la empresa. Si difieren, puede que el contenido de la aplicación haya cambiado y esta no se pueda ejecutar.
- **Aplicación de las funcionalidades**: iOS/iPadOS intenta aplicar las funcionalidades de la aplicación desde el perfil de aprovisionamiento empresarial (no los de desarrolladores individuales) presentes en el archivo de instalación de la aplicación (.ipa).


El certificado de firma empresarial que se usa para firmar aplicaciones normalmente tiene una validez de tres años. Sin embargo, el perfil de aprovisionamiento expira después de un año. Mientras siga siendo válido el certificado, Intune proporciona las herramientas para asignar proactivamente un nuevo perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima.
Cuando el certificado haya expirado, debe volver a firmar la aplicación con un certificado nuevo e insertar un nuevo perfil de aprovisionamiento con la clave del nuevo certificado.

Como administrador, puede incluir y excluir grupos de seguridad para asignar la configuración del aprovisionamiento de aplicaciones iOS/iPadOS. Por ejemplo, puede asignar una configuración de aprovisionamiento de aplicaciones iOS/iPadOS a todos los usuarios, pero excluir un grupo de directivos.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Creación de un perfil de aprovisionamiento de aplicaciones móviles iOS

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Perfiles de aprovisionamiento de aplicaciones de iOS** > **Crear perfil**.
3. En la página **Datos básicos**, agregue los siguientes valores:
    - **Nombre**: proporcione un nombre para este perfil de aprovisionamiento móvil.
    - **Descripción**: opcionalmente, especifique una descripción de la directiva.
    - **Archivo de perfil de carga:** elija el icono **Abrir** y, luego, elija un archivo de perfil de configuración móvil de Apple (con la extensión `.mobileprovision`) que descargó del [sitio web para desarrolladores de Apple](https://developer.apple.com/).

   La **Fecha de expiración** se rellenará a partir de un valor en el archivo del perfil de configuración móvil de Apple que se agregó anteriormente.<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. Haga clic en **Siguiente: Etiquetas de ámbito**.<br>
   En la página **Etiquetas de ámbito** puede configurar opcionalmente etiquetas de ámbito para determinar quién puede ver el perfil de aprovisionamiento de aplicaciones iOS/iPadOS en Intune. Para obtener más información sobre las etiquetas de ámbito, consulte [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Uso del control de acceso basado en roles y de las etiquetas de ámbito para la TI distribuida).
5. Haga clic en **Siguiente: Asignaciones**.<br>
   En la página **Asignaciones** puede asignar el perfil a usuarios y dispositivos. Es importante saber que un perfil se puede asignar a un dispositivo independientemente de si dicho dispositivo está administrado o no por Intune.
6. Haga clic en **Siguiente: Revisar + crear** para revisar los valores especificados en el perfil.
7. Cuando termine, haga clic en **Crear** para crear el perfil de aprovisionamiento de aplicaciones iOS/iPadOS en Intune. 

## <a name="next-steps"></a>Pasos siguientes

Asigne el perfil a los dispositivos iOS/iPadOS necesarios. Para obtener más información, siga los pasos de [Asignación de perfiles de dispositivo](../device-profile-assign.md).
