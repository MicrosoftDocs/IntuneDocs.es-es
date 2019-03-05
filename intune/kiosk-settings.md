---
title: 'Configuración de pantalla completa para dispositivos Windows y Holographic en Microsoft Intune: Azure | Microsoft Docs'
description: Configure los dispositivos con Windows 10 (y versiones posteriores) y Windows Holographic for Business como pantallas completas con una sola aplicación y con varias, personalice el menú Inicio, agregue aplicaciones, muestre la barra de tareas y configure un explorador web en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5cab385b55022139b79ca4a749aba0fbe9e5ef3a
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236796"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Configuración de dispositivos con Windows 10 y Windows Holographic for Business para ejecutarse como una pantalla completa dedicada con Intune

En dispositivos con Windows 10, use Intune para ejecutar los dispositivos como una pantalla completa, lo que a veces se conoce como un dispositivo dedicado. Un dispositivo en pantalla completa puede ejecutar una aplicación o varias. Puede mostrar y personalizar un menú Inicio, agregar diferentes aplicaciones, incluidas las aplicaciones Win32, agregar una página principal específica a un explorador web y mucho más. 

Esta característica se aplica a los dispositivos que ejecutan:

- Windows 10 y versiones posteriores
- Windows Holographic for Business

Intune admite un perfil de quiosco por dispositivo. Si necesita varios perfiles de quiosco en un único dispositivo, puede usar un [OMA-URI personalizado](custom-settings-windows-10.md).

Intune usa "perfiles de configuración" para crear y personalizar estas configuraciones para las necesidades de su organización. Después de agregar estas características a un perfil, inserte o implemente estas configuraciones en grupos de la organización.

En este artículo se muestra cómo crear un perfil de configuración de dispositivo. Para una lista de todas las configuraciones, y lo que hacen, consulte [Windows 10 kiosk settings](kiosk-settings-windows.md) (Configuración de pantalla de Windows 10) y [Windows Holographic for Business kiosk settings](kiosk-settings-holographic.md) (Configuración de pantalla completa de Windows Holographic for Business).

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
   - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
   - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
   - **Tipo de perfil**: seleccione **Pantalla completa**.

4. En **Configuración**, seleccione una **pantalla completa**. **Modo de quiosco**: identifica el tipo de modo de quiosco admitido por la directiva. Las opciones son:

    - **Sin configurar** (valor predeterminado): la directiva no habilita la pantalla completa.
    - **Pantalla completa con aplicación única**: el dispositivo se ejecuta como una cuenta de usuario único y la bloquea para una única aplicación de la Tienda. Así que cuando el usuario inicia sesión, se inicia una aplicación concreta. Este modo también evita que el usuario abra nuevas aplicaciones o modifique la aplicación en ejecución.
    - **Pantalla completa con varias aplicaciones**: el dispositivo ejecuta varias aplicaciones de la Tienda, aplicaciones Win32 o aplicaciones de Windows de bandeja de entrada mediante el identificador de modelo del usuario de la aplicación (AUMID). En el dispositivo solo están disponibles las aplicaciones agregadas.

        La ventaja de un quiosco con varias aplicaciones, o un dispositivo para un propósito fijo, es que proporciona una experiencia fácil de entender para los usuarios, ya que solo acceden a las aplicaciones que necesitan. Además, se quitan de la vista las aplicaciones que no necesitan.

    Para una lista de todas las configuraciones, y lo que hacen, consulte:
      - [Configuración de pantalla completa en Windows 10](kiosk-settings-windows.md)
      - [Configuración de pantalla completa en Windows Holographic for Business](kiosk-settings-holographic.md)

5. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios. 

El perfil se crea y se muestra en la lista de perfiles. Después, [asigne](device-profile-assign.md) el perfil.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Puede crear perfiles de pantalla completa para dispositivos que ejecutan las siguientes plataformas:
- [Android](device-restrictions-android.md#kiosk)
- [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 y versiones posteriores](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
