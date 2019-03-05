---
title: 'Configuración de pantalla completa para Windows Holographic for Business en Microsoft Intune: Azure | Microsoft Docs'
description: Configure los dispositivos con Windows Holographic for Business como pantallas completas con una sola aplicación y con varias, personalice el menú Inicio, agregue aplicaciones, muestre la barra de tareas y configure un explorador web en Microsoft Intune.
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
ms.openlocfilehash: 38bc5ed233bf3368ae9b0ce21b8688966a1ffdef
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57232360"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Configuración de dispositivos con Windows Holographic for Business para ejecutarse como una pantalla completa en Intune

En los dispositivos con Windows Holographic for Business, puede configurar estos dispositivos para que se ejecuten en modo de pantalla completa con una sola aplicación o con varias. Algunas características no se admiten en Windows Holographic for Business.

En este artículo se enumeran y describen las distintas opciones de configuración que puede controlar en los dispositivos Windows Holographic for Business. Como parte de su solución de administración de dispositivos móviles (MDM), use estas opciones de configuración para configurar sus dispositivos Windows Holographic for Business para que se ejecuten en pantalla completa.

Como administrador de Intune, puede crear y asignar estas opciones de configuración a los dispositivos.

Para más información sobre la característica de pantalla completa de Windows en Intune, consulte la [configuración de las opciones de pantalla completa](kiosk-settings.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree el perfil](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Quioscos a pantalla completa con una sola aplicación

Si elige el modo de pantalla completa de aplicación única, escriba la siguiente configuración:

- **Tipo de inicio de sesión de usuario**: seleccione **Cuenta de usuario local** para escribir la cuenta de usuario local (en el dispositivo), o bien una cuenta de Microsoft (MSA) asociada a la aplicación de pantalla completa. Los tipos de cuenta de usuario **Inicio de sesión automático** no se admiten en Windows Holographic for Business.

- **Tipo de aplicación**: seleccione **Aplicación de la Tienda**.

- **Aplicación para ejecutar en modo de pantalla completa**: elija **Agregar una aplicación de la tienda** y seleccione una aplicación de la lista.

    ¿No aparece ninguna aplicación? Agregue algunas siguiendo los pasos descritos en [Aplicaciones cliente](apps-add.md).

    Haga clic en **Aceptar** para guardar los cambios.

## <a name="multi-app-kiosks"></a>Pantallas completas con varias aplicaciones

Las aplicaciones en este modo están disponibles en el menú Inicio. Estas aplicaciones son las únicas que el usuario puede abrir. Si elige la pantalla completa de aplicación única, escriba la siguiente configuración:

- **Destino de Windows 10 en dispositivos en modo S**: elija **No**. El modo S no se admite en Windows Holographic for Business.

- **Tipo de inicio de sesión de usuario**: agregue una o varias cuentas de usuario que puedan usar las aplicaciones que agregue. Las opciones son: 

  - **Inicio de sesión automático**: no se admite en Windows Holographic for Business.
  - **Cuentas de usuarios locales**: **añada** la cuenta de usuario local (en el dispositivo). La cuenta que especifique se usa para iniciar sesión en el quiosco.
  - **Azure AD user or group (Windows 10, version 1803 and later)** [Usuario o grupo de Azure AD (Windows 10, versión 1803 y posteriores)]: se requieren credenciales de usuario para iniciar sesión en el dispositivo. Seleccione **Agregar** para elegir usuarios o grupos de Azure AD en la lista. Puede seleccionar varios usuarios y grupos. Elija **Seleccionar** para guardar los cambios.
  - **Visitante de HoloLens**: la cuenta de visitante es una cuenta de invitado que no requiere ninguna credencial de usuario ni autenticación, como se describe en [Conceptos del modo de equipo compartido](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Aplicaciones**: agregue las aplicaciones que se van a ejecutar en el dispositivo de pantalla completa. Recuerde que puede agregar varias aplicaciones.

  - **Add Store apps** (Agregar aplicaciones de Store): seleccione una aplicación existente que haya agregado mediante [Aplicaciones cliente](apps-add.md). Si no aparece ninguna aplicación, puede obtenerlas y [agregarlas a Intune](store-apps-windows.md).
  - **Agregar aplicación Win32**: no se admite en Windows Holographic for Business.
  - **Agregar por AUMID**: use esta opción para agregar aplicaciones de Windows de bandeja de entrada. Escriba las siguientes propiedades: 

    - **Nombre de la aplicación**: Obligatorio. Escriba un nombre para la aplicación.
    - **Identificador de modelo del usuario de la aplicación (AUMID)**: Obligatorio. Escriba el identificador de modelo de usuario de aplicación (AUMID) de la aplicación de Windows. Para obtener este identificador, vea [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Buscar el identificador de modelo de usuario de aplicación de una aplicación instalada).
    - **Tamaño de icono**: Obligatorio. Elija un tamaño de icono de la aplicación pequeño, mediano, ancho o grande.

- **Configuración del explorador del Quiosco**: no se admite en Windows Holographic for Business.

- **Usar diseño de inicio alternativo**: elija **Sí** para especificar un archivo XML que describa el modo en que las aplicaciones aparecen en el menú Inicio, incluido el orden de estas. Use esta opción si necesita personalizar más el menú Inicio. En [Personalizar y exportar el diseño de la pantalla Inicio](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) se proporcionan algunas instrucciones y se incluye un archivo XML específico para dispositivos con Windows Holographic for Business.

- **Barra de tareas de Windows**: no se admite en Windows Holographic for Business.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de pantalla completa para dispositivos [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) y [Windows 10 y versiones posteriores](kiosk-settings-windows.md).
