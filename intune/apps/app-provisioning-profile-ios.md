---
title: Perfiles de aprovisionamiento de aplicaciones para iOS en Microsoft Intune
titleSuffix: ''
description: Intune proporciona las herramientas para asignar proactivamente un nuevo perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 624c6cec2a887396cb6ef6508ab26a16d72f8f7c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725327"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Uso de perfiles de aprovisionamiento de aplicaciones para iOS para evitar que las aplicaciones expiren

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>Introducción

Las aplicaciones de línea de negocio de Apple iOS asignadas a iPhone y iPad se crean con un perfil de aprovisionamiento incluido y un código firmado con un certificado. Cuando la aplicación está en ejecución, iOS confirma la integridad de la aplicación de iOS y exige el cumplimiento de las directivas definidas por el perfil de aprovisionamiento. Se producen las validaciones siguientes:

- **Integridad del archivo de instalación:** iOS compara los detalles de las aplicaciones con la clave pública del certificado de firma de la empresa. Si difieren, puede que el contenido de la aplicación haya cambiado y esta no se pueda ejecutar.
- **Aplicación de las funcionalidades:** iOS intenta aplicar las funcionalidades de la aplicación del perfil de aprovisionamiento empresarial (no los perfiles de aprovisionamiento para desarrolladores individuales) presentes en el archivo de instalación de la aplicación (.ipa).


El certificado de firma empresarial que se usa para firmar aplicaciones normalmente tiene una validez de tres años. Sin embargo, el perfil de aprovisionamiento expira después de un año. Mientras siga siendo válido el certificado, Intune proporciona las herramientas para asignar proactivamente un nuevo perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima.
Cuando el certificado haya expirado, debe volver a firmar la aplicación con un certificado nuevo e insertar un nuevo perfil de aprovisionamiento con la clave del nuevo certificado.

Como administrador, puede incluir y excluir grupos de seguridad para asignar la configuración del aprovisionamiento de aplicaciones de iOS. Por ejemplo, puede asignar una configuración de aprovisionamiento de aplicaciones de iOS a todos los usuarios, pero excluir un grupo de directivos.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Creación de un perfil de aprovisionamiento de aplicaciones móviles iOS

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
1. En la carga de trabajo **Aplicaciones cliente**, elija **Administrar** > **Perfiles de aprovisionamiento de aplicaciones para iOS**.
2. En la hoja de lista de perfiles, elija **Crear perfil**.
3. En el panel **Crear perfil**, configure los siguientes valores:
    - **Nombre**: proporcione un nombre para este perfil de aprovisionamiento móvil.
    - **Descripción**: opcionalmente, especifique una descripción de la directiva.
    - **Archivo de perfil de carga:** elija el icono **Abrir** y, luego, elija un archivo de perfil de configuración móvil de Apple (con la extensión `.mobileprovision`) que descargó del [sitio web para desarrolladores de Apple](https://developer.apple.com/).
4. Cuando termine, elija **Crear**.

## <a name="next-steps"></a>Pasos siguientes

Asigne el perfil a los dispositivos iOS necesarios. Para obtener más información, siga los pasos de [Asignación de perfiles de dispositivo](../device-profile-assign.md).
