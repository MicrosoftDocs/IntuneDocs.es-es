---
title: "Creación de perfiles de VPN personalizados con Microsoft Intune"
titleSuffix: Azure portal
description: Utilice las configuraciones personalizadas para crear perfiles de VPN en Intune.
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cc1374c3ccb60ed5a3dc57449f5c772963b8efc7
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Creación de perfiles de VPN personalizados en Microsoft Intune

## <a name="create-a-custom-configuration"></a>Crear una configuración personalizada
Puede usar directivas de configuración personalizadas de Intune para crear perfiles de VPN para:

* Dispositivos que ejecutan Android 4 y versiones posteriores
* Dispositivos inscritos que ejecutan Windows 8.1 y versiones posteriores
* Dispositivos que ejecutan Windows Phone 8,1 y versiones posteriores
* Dispositivos inscritos que ejecutan Windows 10 Escritorio 
* Dispositivos que ejecutan Windows 10 Mobile

Este tipo de directiva puede ser útil cuando las directivas estándar de VPN de Intune no contienen la configuración que quiere usar.

## <a name="to-create-a-custom-configuration-policy"></a>Para crear una directiva de configuración personalizada:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
4. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
5. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
6. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de VPN.
7. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo a la que quiere aplicar la configuración de VPN. Actualmente, puede elegir una de las siguientes plataformas para la configuración de dispositivo personalizada:
    - **Android**
    - **iOS** (se configurada mediante un archivo exportado desde Apple Configurator).
    - **macOS** (se configura mediante un archivo exportado desde Apple Configurator).
    - **Windows Phone 8.1**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **Personalizado**.
7. En la hoja **Configuración OMA-URI personalizada**, para cada valor de URI que quiera especificar, elija **Agregar**, proporcione la información solicitada y elija **Aceptar**. Este podría ser un ejemplo:

   ![Cuadro de diálogo de configuración personalizada de perfil de VPN](./media/Intune_Add_VPN_URI.png)

4.  Después de haber especificado todos los valores de URI que necesita, elija **Aceptar** y, luego,, en la hoja **Create Profile** (Crear perfil), elija **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).




