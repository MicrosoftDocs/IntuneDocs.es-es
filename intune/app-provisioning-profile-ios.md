---
title: Perfiles de aprovisionamiento de aplicaciones
titlesuffix: Azure portal
description: "Intune proporciona las herramientas para asignar proactivamente un nuevo perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b58fb0d9b69e875736b5d2ea884ae9d3453b481
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="use-ios-mobile-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Uso de perfiles de aprovisionamiento móvil iOS para evitar que las aplicaciones expiren

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>Introducción

Las aplicaciones de línea de negocio de Apple iOS asignadas en iPhone y iPad se crean con un perfil de aprovisionamiento incluido y un código firmado con un certificado. Cuando la aplicación está en ejecución, iOS confirma la integridad de la aplicación de iOS y exige el cumplimiento de las directivas definidas por el perfil de aprovisionamiento. Se producen las validaciones siguientes:

- **Integridad del archivo de instalación:** iOS compara los detalles de las aplicaciones con la clave pública del certificado de firma de la empresa. Si difieren, puede que el contenido de la aplicación haya cambiado, y esta no se podrá ejecutar.
- **Aplicación de las funcionalidades:** iOS intenta aplicar las funcionalidades de la aplicación del perfil de aprovisionamiento empresarial (no los perfiles de aprovisionamiento para desarrolladores individuales) presentes en el archivo de instalación de la aplicación (.ipa).


El certificado de firma empresarial que se usa para firmar aplicaciones normalmente tiene una validez de tres años. Sin embargo, el perfil de aprovisionamiento expira después de un año. Mientras siga siendo válido el certificado, Intune proporciona las herramientas para asignar proactivamente un nuevo perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima.
Cuando el certificado haya expirado, debe volver a firmar la aplicación con un certificado nuevo e insertar un nuevo perfil de aprovisionamiento con la clave del nuevo certificado.


## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Creación de un perfil de aprovisionamiento de aplicaciones móviles iOS

1. Inicie sesión en el portal de Azure.
2. Elija **Más servicios** > **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
1.  En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Perfiles de aprovisionamiento de iOS**.
2.  En la hoja de lista de perfiles, elija **Crear perfil**.
3. En la hoja **Crear perfil**, configure los siguientes valores:
    - **Nombre**: proporcione un nombre para este perfil de aprovisionamiento móvil.
    - **Descripción**: opcionalmente, especifique una descripción de la directiva.
    - **Archivo de perfil de carga:** elija **Importar** y, luego, elija un archivo de perfil de configuración móvil de Apple (con la extensión **.mobileprovision**) que ha descargado del sitio web para desarrolladores de Apple.
4. Cuando termine, elija **Crear**.

## <a name="next-steps"></a>Pasos siguientes

Asigne el perfil a los dispositivos iOS necesarios. Para obtener más información, siga los pasos de [Asignación de perfiles de dispositivo](device-profile-assign.md).
