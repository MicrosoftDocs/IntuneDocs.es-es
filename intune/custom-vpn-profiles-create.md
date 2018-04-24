---
title: Creación de perfiles de VPN personalizados con Microsoft Intune
titleSuffix: ''
description: Utilice las configuraciones personalizadas para crear perfiles de VPN en Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec9b959d086051985287a62f7d10fe8d4cbad7e9
ms.sourcegitcommit: 28ed8902a11500b195fff839d59b90c16af6e743
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Creación de perfiles de VPN personalizados en Microsoft Intune

Puede usar directivas de configuración personalizadas de Intune para crear perfiles de VPN para las siguientes plataformas:

* Android 4 y versiones posteriores
* Dispositivos inscritos que ejecutan Windows 8.1 y versiones posteriores
* Windows Phone 8.1 y versiones posteriores
* Dispositivos inscritos que ejecutan Windows 10 Escritorio 
* Windows 10 Mobile

Este tipo de directiva puede ser útil cuando las directivas estándar de VPN de Intune no tienen la configuración que quiere usar.

## <a name="to-create-a-custom-configuration-policy"></a>Para crear una directiva de configuración personalizada:

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Configuración del dispositivo**.
2. En el panel **Configuración del dispositivo**, en la sección **Administrar**, elija **Perfiles**.
5. En el panel Perfiles, elija **Crear perfil**.
6. En el panel **Crear perfil**, escriba un **Nombre** y una **Descripción** para el perfil de VPN.
7. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo a la que quiere aplicar la configuración de VPN. Actualmente, puede elegir una de las siguientes plataformas para la configuración de dispositivo personalizada:
    - **Android**
    - **Android for Work**
    - **iOS** (se configurada mediante un archivo exportado desde Apple Configurator).
    - **macOS** (se configura mediante un archivo exportado desde Apple Configurator).
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **Personalizado**.
7. En el panel **Configuración OMA-URI personalizada**, para cada valor de URI que quiera especificar, elija **Agregar**, proporcione la información solicitada y elija **Aceptar**. Este podría ser un ejemplo:

   ![Cuadro de diálogo de configuración personalizada de perfil de VPN](./media/Intune_Add_VPN_URI.png)

4.  Después de haber especificado todos los valores de URI que necesita, elija **Aceptar** y, luego, en el panel **Crear perfil**, elija **Crear**.

Se creará el perfil y aparecerá en el panel con la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).




