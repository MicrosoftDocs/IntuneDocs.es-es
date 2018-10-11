---
title: 'Actualización o uso del modo S en dispositivos Windows 10 con Microsoft Intune: Azure | Microsoft Docs'
description: Cree un perfil de dispositivo en Microsoft Intune para actualizar los dispositivos Windows 10 a otras ediciones. Por ejemplo, puede actualizar de Windows 10 Professional a Windows 10 Enterprise. También puede habilitar o desactivar el modo de S en un dispositivo con el perfil de configuración. Consulte también las rutas de actualización admitidas para Windows 10 Pro, N, Education, Cloud, Enterprise, Core, Holographic y Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f0e4ba42559a068ebefb453aba18060803dc36e0
ms.sourcegitcommit: f3974c810e172f345853dacd7f2ca0abc11b1a5b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2018
ms.locfileid: "44389632"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>Uso de un perfil de configuración para actualizar Windows 10 o cambiar del modo S en Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configure un perfil de actualización en Intune para actualizar automáticamente los dispositivos que ejecutan una edición de Windows 10 a otra edición. Vea también las rutas de actualización admitidas.

## <a name="before-you-begin"></a>Antes de comenzar
Antes de actualizar los dispositivos a la versión más reciente, debe cumplir los siguientes requisitos previos:

- Tener una clave de producto válida para instalar la versión actualizada de Windows en todos los dispositivos de destino de la directiva (para ediciones de Windows 10 Desktop). Puede utilizar las claves de las claves de activación múltiple (MAK) o el servidor de administración de claves (KMS). En las ediciones Windows 10 Mobile y Windows 10 Holographic, puede usar un archivo de licencia de Microsoft que contenga la información de licencia para instalar la nueva versión de Windows en todos los dispositivos a los que se aplica la directiva.
- Los dispositivos Windows 10 a los que asigna la directiva están inscritos en Microsoft Intune. No puede usar la directiva de actualización de edición con equipos que ejecutan el software cliente de PC de Intune.

## <a name="supported-upgrade-paths"></a>Rutas de actualización compatibles
En la siguiente tabla, se muestran las rutas de actualización admitidas para el perfil de actualización de edición de Windows 10.

| Actualización de | Actualización a |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Edición Windows 10 Pro N | Edición Windows 10 Education N <br/>Edición Windows 10 Enterprise N <br/>Edición Windows 10 Pro Education N | 
| Windows 10 Pro Education | Windows 10 Education | 
| Edición Windows 10 Pro Education N | Edición Windows 10 Education N |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 Pro Education | 
| Edición Windows 10 Cloud N | Edición Windows 10 Education N <br/>Edición Windows 10 Enterprise N <br/>Edición Windows 10 Pro N <br/>Edición Windows 10 Pro Education N | 
| Windows 10 Enterprise | Windows 10 Education | 
| Edición Windows 10 Enterprise N | Edición Windows 10 Education N | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Edición Windows 10 Core N | Edición Windows 10 Education N <br/>Edición Windows 10 Enterprise N <br/>Edición Windows 10 Pro Education N | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobile | Windows 10 Mobile Enterprise |


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

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

## <a name="upgrade-the-edition"></a>Actualización de la edición

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba un **Nombre** y una **Descripción** para el perfil. Por ejemplo, escriba algo parecido a `Windows 10 edition upgrade`
4. En **Plataforma**, seleccione **Windows 10 y versiones posteriores**.
5. En **Tipo de perfil**, seleccione **Actualización de la edición**.
6. En las propiedades **Actualización de edición**, escriba la siguiente configuración:

   - **Edición a la que actualizar**: seleccione la edición de Windows 10 a la que va a actualizar. Los dispositivos de destino de esta directiva se actualizan a la edición que elija.
   - **Clave de producto**: escriba la clave de producto que recibió de Microsoft. Después de crear la directiva con la clave de producto, la clave no se puede actualizar y se oculta por motivos de seguridad. Para cambiar la clave de producto, escriba toda la clave de nuevo.
   - **Archivo de licencia**: en **Windows 10 Holographic for Business** o **Windows 10 Mobile**, haga clic en **Examinar** para seleccionar el archivo de licencia que recibió de Microsoft. Este archivo de licencia incluye información de licencia de las ediciones que instalará en los dispositivos de destino.

7. Haga clic en **Aceptar** para guardar los cambios. Haga clic en **Crear** para crear el perfil.

## <a name="switch-out-of-s-mode"></a>Desactivación del modo S

El [modo Windows 10 S](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) está diseñado por motivos de seguridad y rendimiento. Si los dispositivos solo ejecutan aplicaciones de Microsoft Store, puede usar el modo S para ayudar a proteger los dispositivos. Si los dispositivos requieren aplicaciones que no están disponibles en Microsoft Store, salga del modo S. Solo se puede salir una vez del modo S. Una vez que salga de él, no podrá volver al modo Windows 10 S.

Los pasos siguientes muestran cómo crear un perfil que controla el modo S en dispositivos Windows 10 (1809 o posteriores).

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba un **Nombre** y una **Descripción** para el perfil. Por ejemplo, escriba algo parecido a `Windows 10 switch off S mode`
4. En **Plataforma**, seleccione **Windows 10 y versiones posteriores**.
5. En **Tipo de perfil**, seleccione **Actualización de la edición**.
6. Seleccione **Cambio al modo (solo Windows Insider)** y establezca la propiedad **Switch out of S mode** (Desactivar el modo S). Las opciones son:

    - **Ninguna configuración**: el dispositivo en modo S permanece en ese modo. Un usuario final puede desactivar el modo S en el dispositivo.
    - **Keep in S mode** (Mantener en modo S): impide que el usuario final pueda desactivar el modo S en el dispositivo.
    - **Switch** (Cambiar): el modo S se desactiva en el dispositivo.

7. Haga clic en **Aceptar** para guardar los cambios. Haga clic en **Crear** para crear el perfil.

El perfil se crea y aparece en la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

[Asignar este perfil](device-profile-assign.md) a los grupos.

>[!NOTE]
>Si quita después la asignación de directiva, la versión de Windows en el dispositivo no se revierte y sigue funcionando con normalidad.
