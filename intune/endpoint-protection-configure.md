---
title: 'Configurar opciones de Endpoint Protection en Microsoft Intune: Azure | Microsoft Docs'
description: Cree la configuración de Endpoint Protection al crear un perfil de dispositivo de macOS o Windows 10 en Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 184781a315dcaeaac9540294746a9c2cd85da917
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041904"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Agregar la configuración de Endpoint Protection en Intune

Con Intune, puede usar perfiles de configuración de dispositivos para administrar características de seguridad de protección de puntos de conexión comunes en los dispositivos, incluidos:
- Firewall 
- BitLocker
- Permitir o bloquear aplicaciones  
- Windows Defender y cifrado

Por ejemplo, puede crear un perfil de Endpoint Protection que solo permita a los usuarios de macOS instalar aplicaciones desde Mac App Store. O bien, que habilite Windows SmartScreen al ejecutar aplicaciones en dispositivos de Windows 10.

Antes de crear un perfil, revise estos artículos que detallan la configuración de la protección de puntos de conexión que Intune puede administrar para cada plataforma compatible: 
   - [Configuración de macOS](endpoint-protection-macos.md)
   - [Configuración de Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Crear un perfil de dispositivo que contenga la configuración de Endpoint Protection

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=20909).
3. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
4. Escriba un **Nombre** y una **Descripción** para el perfil de Endpoint Protection.
5. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar configuración personalizada. Actualmente, puede elegir una de las siguientes plataformas para la configuración de restricciones de dispositivos:
   - **macOS**
   - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **Tipos de perfil**, pulse **Endpoint Protection**. 
7. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Vea:
   - [Configuración de macOS](endpoint-protection-macos.md)
   - [Configuración de Windows 10](endpoint-protection-windows-10.md)  

8. Después de ajustar la configuración aplicable, seleccione **Crear** en la página **Crear perfil**.

   Se creará el perfil y aparecerá en la página con la lista de perfiles. Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).


## <a name="next-steps"></a>Pasos siguientes  

Para asignar un perfil a grupos, vea [Asignación de perfiles de dispositivo](device-profile-assign.md).
