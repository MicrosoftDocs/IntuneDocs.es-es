---
title: "Configuración del entorno educativo de Intune para iOS | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda sobre la configuración que puede usar para controlar la configuración del entorno educativo en dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44c427f8-0f22-43c2-8c29-e0f9fa533b1f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f05e0018fb202ab5774e935c3f59855e4aa2e75
ms.openlocfilehash: e52fdf8c30a680d62071cd31e308dd0180e8b9dc


---

# <a name="how-to-configure-intune-education-settings-for-ios-devices-in-intune-azure-preview"></a>Configuración del entorno educativo de Intune para dispositivos iOS en la versión preliminar de Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="create-a-device-profile-containing-ios-education-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de educación de iOS

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, seleccione **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de actualización de la edición.
5. En la lista desplegable **Plataforma**, elija **iOS**.
6. En la lista desplegable **Tipo de perfil**, elija **Educación**.
7. En la hoja **Educación**, seleccione lo siguiente:
    - **Archivo de certificado raíz de profesor**
    - **Profesor PKCS12/Perfil PFX**
    - **Archivo de certificado de raíz de estudiante**
    - **Estudiante PKCS12 /Perfil PFX**
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.



<!--HONumber=Feb17_HO1-->


