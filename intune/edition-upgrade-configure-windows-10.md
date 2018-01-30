---
title: "Configuración de actualizaciones de la edición de Windows 10 con Intune"
titlesuffix: Azure portal
description: "Aprenda a usar Intune para actualizar los dispositivos Windows 10 que administra a una edición distinta."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8581aea9db4c04efda5fe9f3281be95330bcd2e2
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>Configuración de actualizaciones de la edición de Windows 10 en Microsoft Intune
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use la información de este artículo para aprender a configurar un perfil de actualización de la edición de Windows 10. Este perfil le permite actualizar automáticamente los dispositivos que ejecutan una edición de Windows 10 a una edición distinta. 

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar a actualizar dispositivos a la versión más reciente, necesitará uno de los elementos siguientes:

- Una clave de producto válida para instalar la nueva versión de Windows en todos los dispositivos de destino de la directiva (para ediciones de Windows 10 Escritorio). Puede usar claves de activación múltiple (MAK), claves del servidor de administración de claves (KMS) o un archivo de licencia de Microsoft que contenga la información de licencia para instalar la nueva versión de Windows en todos los dispositivos a los que se aplica la directiva (para las ediciones de Windows 10 Mobile y Windows 10 Holographic).
- Los dispositivos de Windows 10 a los que asigne la directiva deben estar inscritos en Microsoft Intune. No puede usar la directiva de actualización de edición con equipos que ejecutan el software cliente de PC de Intune.

## <a name="supported-upgrade-paths-for-the-windows-10-edition-upgrade-profile"></a>Rutas de actualización admitidas para el perfil de actualización de edición de Windows 10
Las siguientes listas proporcionan las rutas de actualización admitidas para el perfil de actualización de edición de Windows 10. La edición de Windows 10 a la que se actualizará figura en negrita y a continuación se muestra la lista de las ediciones compatibles desde las que puede actualizar:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Edición Windows 10 Education N**    
- Edición Windows 10 Pro N
- Edición Windows 10 Pro Education N
- Edición Windows 10 Cloud N
- Edición Windows 10 Enterprise N
- Edición Windows 10 Core N
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Edición Windows 10 Enterprise N**
- Edición Windows 10 Pro N
- Edición Windows 10 Cloud N
- Edición Windows 10 Core N
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Edición Windows 10 Pro N**
- Edición Windows 10 Cloud N
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Edición Windows 10 Pro Education N**
- Edición Windows 10 Pro N
- Edición Windows 10 Cloud N
- Edición Windows 10 Core N

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de restricciones de dispositivos
1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de actualización de la edición.
5. En la lista desplegable **Plataforma**, elija **Windows 10 y versiones posteriores**.
6. En la lista desplegable de **tipos de perfil**, elija **Actualización de edición**.
7. En la hoja **Actualización de edición**, configure las opciones siguientes:
    - **Edición a la que actualizar**: en la lista desplegable, seleccione la versión de Windows 10 Desktop, Windows 10 Holographic o Windows 10 Mobile a la que quiere actualizar los dispositivos de destino.
    - **Clave de producto**: especifique la clave de producto que obtuvo de Microsoft, que se puede usar para actualizar todos los dispositivos de Windows 10 Escritorio de destino.<br>Después de crear una directiva que contenga una clave de producto, no se puede editar la clave de producto más adelante. Esto se debe a que la clave se oculta por motivos de seguridad. Para cambiar la clave de producto, debe escribir toda la clave de nuevo.
    - **Archivo de licencia**: elija **Examinar** para seleccionar el archivo de licencia que obtuvo de Microsoft y que contiene la información de licencia de la edición Windows Holographic o Windows 10 Mobile a la que quiere actualizar los dispositivos de destino.
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

>[!NOTE]
>Si quita después la asignación de directiva, la versión de Windows en el dispositivo no se revierte y sigue funcionando con normalidad.

