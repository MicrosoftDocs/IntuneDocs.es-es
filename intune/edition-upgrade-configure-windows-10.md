---
title: "Configuración de actualizaciones de la edición de Windows 10 con Intune"
titleSuffix: Intune on Azure
description: "Aprenda a usar Intune para actualizar los dispositivos Windows 10 que administra a una edición distinta."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 30cea0ecfa62e9bbc0200d15eff94782d48a81fa
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>Configuración de actualizaciones de la edición de Windows 10 en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use la información de este tema para aprender a configurar un perfil de actualización de la edición de Windows 10. Este perfil le permite actualizar automáticamente los dispositivos que ejecutan una de las siguientes versiones de Windows 10 a una edición distinta:

- Windows 10 Home
- Windows 10 Holographic
- Windows 10 Mobile


Las siguientes rutas de acceso de actualización son compatibles:

- De Windows 10 Pro a Windows 10 Enterprise
- De Windows 10 Home a Windows 10 Education
- De Windows 10 Mobile a Windows 10 Mobile Enterprise
- De Windows 10 Holographic Pro a Windows 10 Holographic Enterprise


## <a name="before-you-start"></a>Antes de empezar
Antes de empezar a actualizar dispositivos a la versión más reciente, necesitará uno de los elementos siguientes:

- Una clave de producto válida para instalar la nueva versión de Windows en todos los dispositivos de destino de la directiva (para ediciones de Windows 10 Escritorio). Puede utilizar las claves de las claves de activación múltiple (MAK) o el servidor de administración de claves (KMS). O bien, un archivo de licencia de Microsoft que contenga la información de licencia para instalar la nueva versión de Windows en todos los dispositivos a los que se aplica la directiva (para las ediciones de Windows 10 Mobile y Windows 10 Holographic).
- Los dispositivos de Windows 10 que planee actualizar deben estar inscritos en Microsoft Intune. No puede usar la directiva de actualización de edición con equipos que ejecutan el software cliente de PC de Intune.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de restricciones de dispositivos

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de actualización de la edición.
5. En la lista desplegable **Plataforma**, elija **Windows 10 y versiones posteriores**.
6. En la lista desplegable de **tipos de perfil**, elija **Actualización de edición**.
7. En la hoja **Actualización de edición**, configure lo siguiente:
    - **Edición desde la que actualizar**: en la lista desplegable, seleccione la versión de Windows 10 que quiere actualizar en los dispositivos.
    - **Edición a la que actualizar**: en la lista desplegable, seleccione la versión de Windows 10 Desktop, Windows 10 Holographic o Windows 10 Mobile a la que quiere actualizar los dispositivos de destino.
    - **Clave de producto**: especifique la clave de producto que obtuvo de Microsoft, que se puede usar para actualizar todos los dispositivos de Windows 10 Escritorio de destino.<br>Después de crear una directiva que contenga una clave de producto, no se puede editar la clave de producto más adelante. Esto se debe a que la clave se oculta por motivos de seguridad. Para cambiar la clave de producto, debe escribir toda la clave de nuevo.
    - **Archivo de licencia**: elija **Examinar** para seleccionar el archivo de licencia que obtuvo de Microsoft y que contiene la información de licencia de la edición Windows Holographic o Windows 10 Mobile a la que quiere actualizar los dispositivos de destino.
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

