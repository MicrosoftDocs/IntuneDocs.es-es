---
title: "Configuración del entorno educativo de Intune para Windows 10"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Azure de Intune: aprenda a usar Intune para configurar los ajustes de educación de Windows 10 en los dispositivos que administra."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3acb45ccc9e67fb410a9511f138d1558a49fadf9
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Configuración de los ajustes de educación de Windows 10 en Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Los perfiles de educación le permiten especificar los detalles que configuran la aplicación Take a Test de Windows, incluidos los detalles de la cuenta y la dirección URL de la prueba. Al configurar esto, la aplicación Take a Test se abre con la prueba que especifique y ninguna otra aplicación puede ejecutarse en el dispositivo hasta que se complete la prueba.

Use la información de este tema para conocer los aspectos básicos de la configuración de perfiles de restricciones de dispositivos. Luego, siga leyendo los temas correspondientes a cada plataforma para saber las peculiaridades de cada dispositivo.

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Creación de un perfil de dispositivo que contenga los parámetros del perfil de educación

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de restricción de dispositivo.
5. En la lista desplegable **Plataform** (Plataforma), elija **Windows 10 y versiones posteriores**.
6. En la lista desplegable **Profile type** (Tipo de perfil), elija **Education profile** (Perfil de educación). 
7. Elija Configuración > Configurar y, a continuación, en la hoja **Take a Test**, configure lo siguiente:
    - **Nombre de usuario de la cuenta**: especifique el nombre del usuario de la cuenta que utiliza con Take a Test. Puede ser una cuenta de dominio, una cuenta de Azure Active Directory (AAD) o una cuenta de equipo local.
    - **URL de la evaluación**: proporcione la URL de la prueba que desea que los usuarios realicen. Para obtener más información, vea la documentación sobre Take a Test.
    - **Supervisión de la pantalla**: especifique si desea poder supervisar la actividad de la pantalla mientras los usuarios realizan la prueba.
    - **Sugerencia de texto**: permita o bloquee sugerencias de texto mientras los usuarios realizan la prueba.
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).




