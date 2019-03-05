---
title: 'Configurar opciones de Endpoint Protection en Microsoft Intune: Azure | Microsoft Docs'
description: Cree la configuración de Endpoint Protection al crear un perfil de dispositivo de macOS o Windows 10 en Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 3/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8cda293fb337730c936a7fab9b7eadf4816beb67
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57237969"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Agregar la configuración de Endpoint Protection en Intune

Endpoint Protection permite controlar distintas características de seguridad de los dispositivos, como el firewall, Bitlocker, permitir y bloquear aplicaciones, Windows Defender y el cifrado, etc. Puede configurar estas opciones en Microsoft Intune mediante perfiles de dispositivo.

Por ejemplo, puede crear un perfil de Endpoint Protection que solo permita a los usuarios de macOS instalar aplicaciones desde Mac App Store. O bien, que habilite Windows SmartScreen al ejecutar aplicaciones en dispositivos de Windows 10.

En este artículo se muestra cómo crear un perfil. Luego, seleccione la plataforma del dispositivo para obtener más detalles sobre las opciones disponibles.

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Crear un perfil de dispositivo que contenga la configuración de Endpoint Protection

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
4. Escriba un **Nombre** y una **Descripción** para el perfil de Endpoint Protection.
5. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar configuración personalizada. Actualmente, puede elegir una de las siguientes plataformas para la configuración de restricciones de dispositivos:
   - **macOS**
   - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **Tipos de perfil**, pulse **Endpoint Protection**. 
7. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
   - [Configuración de macOS](endpoint-protection-macos.md)
   - [Configuración de Windows 10](endpoint-protection-windows-10.md)
8. Cuando haya terminado, vuelva a la página **Crear perfil** y haga clic en **Crear**.

Se creará el perfil y aparecerá en la página con la lista de perfiles. Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

## <a name="next-steps"></a>Pasos siguientes
Para asignar un perfil a grupos, vea [Asignación de perfiles de dispositivo](device-profile-assign.md).
