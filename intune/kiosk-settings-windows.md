---
title: 'Configuración de quiosco para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Configure los dispositivos con Windows 10 y versiones posteriores como pantallas completas con una sola aplicación y con varias, personalice el menú Inicio, agregue aplicaciones, muestre la barra de tareas y configure un explorador web en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: 31cfa617e0ca5d8d0848d1ecb781fda701589ccd
ms.sourcegitcommit: 0142020a7cd75348c6367facf072ed94238e667f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2019
ms.locfileid: "55229957"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Configuración de dispositivos con Windows 10 y versiones posteriores para ejecutarse como una pantalla completa en Intune

En los dispositivos con Windows 10 y versiones posteriores, puede configurar estos dispositivos para que se ejecuten en modo de pantalla completa con una sola aplicación o con varias.

En este artículo se enumeran y describen los diferentes valores de configuración que puede controlar en los dispositivos con Windows 10 y versiones posteriores. Como parte de su solución de administración de dispositivos móviles (MDM), use estas configuraciones para definir sus dispositivos con Windows 10 y versiones posteriores a fin de que se ejecuten en pantalla completa.

Como administrador de Intune, puede crear y asignar estas opciones de configuración a los dispositivos.

Para más información sobre la característica de pantalla completa de Windows en Intune, consulte la [configuración de las opciones de pantalla completa](kiosk-settings.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree el perfil](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Quioscos a pantalla completa con una sola aplicación

Si elige el modo de pantalla completa de aplicación única, escriba la siguiente configuración:

- **Tipo de inicio de sesión de usuario**: las aplicaciones que se agregan se ejecutan como la cuenta de usuario especificada. Las opciones son:

  - **Auto logon (Windows 10 version 1803 and later)** [Inicio de sesión automático (Windows 10, versión 1803 y posteriores)]: para pantallas completas en entornos orientados al público que no requieren que el usuario inicie sesión, similar a una cuenta de invitado. Esta configuración usa el [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Cuenta de usuario local**: escriba la cuenta de usuario local (en el dispositivo). La cuenta que especifique se usa para iniciar sesión en el quiosco.

- **Tipo de aplicación**: seleccione **Aplicación de la Tienda**.

- **Aplicación para ejecutar en modo de pantalla completa**: elija **Agregar una aplicación de la tienda** y seleccione una aplicación de la lista.

    ¿No aparece ninguna aplicación? Agregue algunas siguiendo los pasos descritos en [Aplicaciones cliente](apps-add.md).

    Haga clic en **Aceptar** para guardar los cambios.

- **Configuración del explorador del Quiosco**: Esta configuración controla una aplicación de explorador web en el quiosco. Asegúrese de obtener la [aplicación Kiosk Browser](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) desde la Tienda, agréguela a Intune como una [aplicación cliente](apps-add.md) y después asígnela a los dispositivos de pantalla completa.

  Escriba los valores siguientes:

  - **Dirección URL de la página principal predeterminada**: escriba la dirección URL predeterminada que aparece en el explorador de pantalla completa cuando se abre o se reinicia el explorador. Por ejemplo, escriba `http://bing.com` o `http://www.contoso.com`.

  - **Botón Inicio**: **muestre** u **oculte** el botón Inicio del explorador de pantalla completa. De forma predeterminada, el botón no aparece.

  - **Botones de navegación**: **muestre** u **oculte** los botones Adelante y Atrás. De forma predeterminada, los botones de navegación no se muestran.

  - **Botón de finalización de sesión**: **muestre** u **oculte** el botón Finalizar sesión. Cuando se muestra, el usuario hace clic en el botón y la aplicación solicita que finalice la sesión. Cuando se confirma, el explorador borra todos los datos de exploración (las cookies, la caché, etc.) y luego abre la dirección URL predeterminada. De forma predeterminada, el botón no aparece.

  - **Actualizar el explorador después del tiempo de inactividad**: escriba el período de tiempo de inactividad (de 1 a 1440 minutos) hasta que el explorador de pantalla completa se reinicie con un nuevo estado. El tiempo de inactividad es el número de minutos desde la última interacción del usuario. De forma predeterminada, el valor está vacío o en blanco, lo que significa que no hay ningún tiempo de espera de inactividad.

  - **Sitios web permitidos**: use esta configuración para permitir que se abran sitios web específicos. En otras palabras, puede usar esta característica para restringir o impedir sitios web en el dispositivo. Por ejemplo, puede permitir que todos los sitios web de `http://contoso.com*` se abran. De forma predeterminada, se permiten todos los sitios web.
 
      Para permitir sitios web específicos, cargue un archivo que incluya una lista de los sitios web permitidos en líneas independientes. Si no agrega ningún archivo, se permitirán todos los sitios web. Intune admite * (asterisco) como un carácter comodín.

      El archivo de ejemplo debería ser parecido a esta lista:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

  Haga clic en **Aceptar** para guardar los cambios.

## <a name="multi-app-kiosks"></a>Pantallas completas con varias aplicaciones

Las aplicaciones en este modo están disponibles en el menú Inicio. Estas aplicaciones son las únicas que el usuario puede abrir.

Si elige la pantalla completa de aplicación única, escriba la siguiente configuración:

- **Destino de Windows 10 en dispositivos en modo S**: elija **Sí** para permitir aplicaciones de la Tienda y aplicaciones AUMID (se excluyen las aplicaciones Win32) en el perfil de pantalla completa. Elija **No** para permitir aplicaciones de la Tienda, aplicaciones Win32 y aplicaciones AUMID en el perfil de pantalla completa. Cuando se elige **No**, no se implementa este perfil de pantalla completa para dispositivos en modo S.

- **Tipo de inicio de sesión de usuario**: las aplicaciones que se agregan se ejecutan como la cuenta de usuario especificada. Las opciones son:

  - **Auto logon (Windows 10 version 1803 and later)** [Inicio de sesión automático (Windows 10, versión 1803 y posteriores)]: para pantallas completas en entornos orientados al público que no requieren que el usuario inicie sesión, similar a una cuenta de invitado. Esta configuración usa el [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Cuenta de usuario local**: **añada** la cuenta de usuario local (en el dispositivo). La cuenta que especifique se usa para iniciar sesión en el quiosco.
  - **Azure AD user or group (Windows 10 version 1803 and later)** [Usuario o grupo de Azure AD (Windows 10, versión 1803 y posteriores)]: Seleccione **Agregar** para elegir usuarios o grupos de Azure AD en la lista. Puede seleccionar varios usuarios y grupos. Elija **Seleccionar** para guardar los cambios.
  - **Visitante de HoloLens**: la cuenta de visitante es una cuenta de invitado que no requiere ninguna credencial de usuario ni autenticación, como se describe en [Conceptos del modo de equipo compartido](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Aplicaciones**: agregue las aplicaciones que se van a ejecutar en el dispositivo de pantalla completa. Recuerde que puede agregar varias aplicaciones.

  - **Agregar aplicación de la tienda**: agregue una aplicación de Microsoft Store para Empresas. Si no aparece ninguna aplicación, puede obtenerlas y [agregarlas a Intune](store-apps-windows.md). Por ejemplo, puede agregar Kiosk Browser, Excel, OneNote y mucho más.

  - **Agregar aplicación Win32**: una aplicación Win32 es una aplicación de escritorio tradicional, como Visual Studio Code o Google Chrome. Escriba las siguientes propiedades:

    - **Nombre de la aplicación**: Obligatorio. Escriba un nombre para la aplicación.
    - **Ruta de acceso local**: Obligatorio. Escriba la ruta de acceso al archivo ejecutable, como `C:\Program Files (x86)\Microsoft VS Code\Code.exe` o `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **Identificador de modelo del usuario de la aplicación (AUMID)**: Escriba el identificador de modelo de usuario de la aplicación (AUMID) de la aplicación Win32. Esta configuración determina el diseño de inicio del icono en el escritorio. Para obtener este identificador, vea [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).
    - **Tamaño de icono**: Obligatorio. Elija un tamaño de icono de la aplicación pequeño, mediano, ancho o grande.
  
  - **Agregar por AUMID**: use esta opción para agregar aplicaciones de Windows de bandeja de entrada, como el Bloc de notas o la Calculadora. Escriba las siguientes propiedades: 

    - **Nombre de la aplicación**: Obligatorio. Escriba un nombre para la aplicación.
    - **Identificador de modelo del usuario de la aplicación (AUMID)**: Obligatorio. Escriba el identificador de modelo de usuario de aplicación (AUMID) de la aplicación de Windows. Para obtener este identificador, vea [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Buscar el identificador de modelo de usuario de aplicación de una aplicación instalada).
    - **Tamaño de icono**: Obligatorio. Elija un tamaño de icono de la aplicación pequeño, mediano, ancho o grande.

  > [!TIP]
  > Una vez agregadas todas las aplicaciones, puede modificar el orden de visualización haciendo clic en ellas y arrastrándolas en la lista.  

  Haga clic en **Aceptar** para guardar los cambios.

- **Configuración del explorador del Quiosco**: Esta configuración controla una aplicación de explorador web en el quiosco. Asegúrese de implementar una aplicación de explorador web en los dispositivos del quiosco mediante [Aplicaciones cliente](apps-add.md).

  Escriba los valores siguientes:

  - **Dirección URL de la página principal predeterminada**: escriba la dirección URL predeterminada que aparece en el explorador de pantalla completa cuando se abre o se reinicia el explorador. Por ejemplo, escriba `http://bing.com` o `http://www.contoso.com`.

  - **Botón Inicio**: **muestre** u **oculte** el botón Inicio del explorador de pantalla completa. De forma predeterminada, el botón no aparece.

  - **Botones de navegación**: **muestre** u **oculte** los botones Adelante y Atrás. De forma predeterminada, los botones de navegación no se muestran.

  - **Botón de finalización de sesión**: **muestre** u **oculte** el botón Finalizar sesión. Cuando se muestra, el usuario hace clic en el botón y la aplicación solicita que finalice la sesión. Cuando se confirma, el explorador borra todos los datos de exploración (las cookies, la caché, etc.) y luego abre la dirección URL predeterminada. De forma predeterminada, el botón no aparece.

  - **Actualizar el explorador después del tiempo de inactividad**: escriba el período de tiempo de inactividad (de 1 a 1440 minutos) hasta que el explorador de pantalla completa se reinicie con un nuevo estado. El tiempo de inactividad es el número de minutos desde la última interacción del usuario. De forma predeterminada, el valor está vacío o en blanco, lo que significa que no hay ningún tiempo de espera de inactividad.

  - **Sitios web permitidos**: use esta configuración para permitir que se abran sitios web específicos. En otras palabras, puede usar esta característica para restringir o impedir sitios web en el dispositivo. Por ejemplo, puede permitir que todos los sitios web de `contoso.com*` se abran. De forma predeterminada, se permiten todos los sitios web.

    Para permitir sitios web específicos, cargue un archivo .csv que incluye una lista de los sitios web permitidos. Si no agrega un archivo .csv, se permitirán todos los sitios web.

  Haga clic en **Aceptar** para guardar los cambios.

- **Usar diseño de inicio alternativo**: elija **Sí** para especificar un archivo XML que describa el modo en que las aplicaciones aparecen en el menú Inicio, incluido el orden de estas. Use esta opción si necesita personalizar más el menú Inicio. [Personalizar y exportar el diseño de la pantalla Inicio](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) proporciona algunas instrucciones y XML de ejemplo.

- **Barra de tareas de Windows**: elija **Mostrar** u **Ocultar** la barra de tareas. De forma predeterminada, la barra de tareas no aparece. Se muestran iconos, por ejemplo, el icono de Wi-Fi, pero los usuarios finales no pueden cambiar la configuración.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de pantalla completa para dispositivos [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings) y [Windows Holographic for Business](kiosk-settings-holographic.md).
