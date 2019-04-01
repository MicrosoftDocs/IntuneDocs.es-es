---
title: 'Configuración de quiosco para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Configure los dispositivos con Windows 10 y versiones posteriores como pantallas completas con una sola aplicación y con varias, personalice el menú Inicio, agregue aplicaciones, muestre la barra de tareas y configure un explorador web en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/11/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55a0cb45cd3e3a8e367b0bff7bd8e856b02af953
ms.sourcegitcommit: aab39bf86707ccaef45fd6527fff4f1c89336710
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2019
ms.locfileid: "58429698"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Configuración de dispositivos con Windows 10 y versiones posteriores para ejecutarse como una pantalla completa en Intune

En los dispositivos con Windows 10 y versiones posteriores, puede configurar estos dispositivos para que se ejecuten en modo de pantalla completa con una sola aplicación o con varias.

En este artículo se enumeran y describen los diferentes valores de configuración que puede controlar en los dispositivos con Windows 10 y versiones posteriores. Como parte de su solución de administración de dispositivos móviles (MDM), use estas configuraciones para definir sus dispositivos con Windows 10 y versiones posteriores a fin de que se ejecuten en pantalla completa.

Como administrador de Intune, puede crear y asignar estas opciones de configuración a los dispositivos.

Para más información sobre la característica de pantalla completa de Windows en Intune, consulte la [configuración de las opciones de pantalla completa](kiosk-settings.md).

## <a name="before-you-begin"></a>Antes de comenzar

- [Cree el perfil](kiosk-settings.md#create-the-profile).

- Este perfil de quiosco está directamente relacionado con el perfil de restricciones de dispositivos se crea mediante la [configuración de pantalla de Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser). En resumen:

  1. Crear este perfil de quiosco para ejecutar el dispositivo en modo de quiosco.
  2. Crear el [perfil de restricciones de dispositivo](device-restrictions-windows-10.md#microsoft-edge-browser)y configurar características específicas y valores permitidos en Microsoft Edge.

> [!IMPORTANT] 
> Asegúrese de asignar este perfil de quiosco a los mismos dispositivos su [perfil de Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

## <a name="single-full-screen-app-kiosks"></a>Quioscos a pantalla completa con una sola aplicación

Se ejecuta solo una aplicación en el dispositivo.

- **Seleccione un modo de quiosco**: elija **aplicación única, pantalla completa**.

- **Tipo de inicio de sesión de usuario**: las aplicaciones que se agregan se ejecutan como la cuenta de usuario especificada. Las opciones son:

  - **Inicio de sesión automático (Windows 10 versión 1803 y posteriores)**: se usa en quioscos en entornos orientados al público que no requieren que el usuario inicie sesión, similar a una cuenta de invitado. Esta configuración usa el [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Cuenta de usuario local**: escriba la cuenta de usuario local (en el dispositivo). La cuenta que especifique inicia sesión en la pantalla completa.

- **Tipo de aplicación**: seleccione el tipo de aplicación. Las opciones son:

  - **Agregar un explorador Microsoft Edge**: seleccione **explorador Microsoft Edge**y elija el **perimetral de tipo de modo de quiosco**:

    - **Señalización digital/interactivo**: abre una pantalla completa de la dirección URL y solo se muestra el contenido en dicho sitio Web. [Configurar la firma digital](https://docs.microsoft.com/windows/configuration/setup-digital-signage) proporciona más información sobre esta característica.
    - **Exploración pública (InPrivate)**: se ejecuta una versión limitada de varias pestaña de Microsoft Edge. Los usuarios pueden examinar públicamente o finalizar su sesión de exploración.

    Para obtener más información sobre estas opciones, consulte [modo de pantalla completa de la implementación de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Esta configuración habilita el explorador Microsoft Edge en el dispositivo. Para configurar opciones específicas de Microsoft Edge, cree un perfil de configuración de dispositivo (**configuración del dispositivo** > **perfiles** > **Crear perfil**  >  **Windows 10** para plataforma > **restricciones de dispositivos** >  **explorador Microsoft Edge**). [Explorador Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) se enumeran y describen las opciones disponibles.

    Haga clic en **Aceptar** para guardar los cambios.

  - **Agregar un explorador del quiosco**: seleccione **configuración del explorador de pantalla completa**. Esta configuración controla una aplicación de explorador web en el quiosco. Asegúrese de obtener la [aplicación Kiosk Browser](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) desde la Tienda, agréguela a Intune como una [aplicación cliente](apps-add.md) y después asígnela a los dispositivos de pantalla completa.

    Escriba los valores siguientes:

    - **Dirección URL de la página principal predeterminada**: escriba la dirección URL predeterminada que abre el explorador del quiosco cuando se abre o se reinicia el explorador. Por ejemplo, escriba `http://bing.com` o `http://www.contoso.com`.

    - **Botón Inicio**: **muestre** u **oculte** el botón Inicio del explorador del quiosco. De forma predeterminada, el botón no aparece.

    - **Botones de navegación**: **muestre** u **oculte** los botones Adelante y Atrás. De forma predeterminada, los botones de navegación no se muestran.

    - **Botón Finalizar sesión**: **muestre** u **oculte** el botón Finalizar sesión. Cuando se muestra, el usuario hace clic en el botón y la aplicación solicita que finalice la sesión. Cuando se confirma, el explorador borra todos los datos de exploración (las cookies, la caché, etc.) y luego abre la dirección URL predeterminada. De forma predeterminada, el botón no aparece.

    - **Actualizar el explorador después del tiempo de inactividad**: escriba la cantidad de tiempo de inactividad (1-1440 minutos) hasta que el explorador del quiosco se reinicie con un nuevo estado. El tiempo de inactividad es el número de minutos desde la última interacción del usuario. De forma predeterminada, el valor está vacío o en blanco, lo que significa que no hay ningún tiempo de espera de inactividad.

    - **Sitios web permitidos**: use esta opción para permitir que sitios web específicos se abran. En otras palabras, puede usar esta característica para restringir o impedir sitios web en el dispositivo. Por ejemplo, puede permitir que todos los sitios web de `http://contoso.com*` se abran. De forma predeterminada, se permiten todos los sitios web.

      Para permitir sitios web específicos, cargue un archivo que incluya una lista de los sitios web permitidos en líneas independientes. Si no agrega ningún archivo, se permitirán todos los sitios web. Intune admite `*` (asterisco) como un carácter comodín.

      El archivo de ejemplo debería ser parecido a esta lista:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

    Haga clic en **Aceptar** para guardar los cambios.

  - **App Store Add**: seleccione **agregar una aplicación de tienda**y elija una aplicación de la lista.

    ¿No aparece ninguna aplicación? Agregue algunas siguiendo los pasos descritos en [Aplicaciones cliente](apps-add.md).

  Haga clic en **Aceptar** para guardar los cambios.

## <a name="multi-app-kiosks"></a>Pantallas completas con varias aplicaciones

Las aplicaciones en este modo están disponibles en el menú Inicio. Estas aplicaciones son las únicas que el usuario puede abrir. Si una aplicación tiene una dependencia en otra aplicación, ambos deben incluirse en la lista de aplicaciones permitidas. Por ejemplo, Internet Explorer 64 bits tiene una dependencia en Internet Explorer 32 bits, por lo que debe permitir "C:\Program programa\internet explorer\iexplore.exe" y "C:\Program Files (x86) \Internet". 

- **Seleccione un modo de quiosco**: elija **pantalla completa de aplicaciones de múltiples**.

- **Destino de Windows 10 en dispositivos en modo S**:
  - **Sí**: permite aplicaciones de la Tienda y aplicaciones AUMID (se excluyen las aplicaciones Win32) en el perfil de pantalla completa.
  - **No**: permite aplicaciones de la Tienda, Win32 y AUMID en el perfil de pantalla completa. No se implementa este perfil de quiosco para dispositivos de modo S.

- **Tipo de inicio de sesión de usuario**: las aplicaciones que se agregan se ejecutan como la cuenta de usuario especificada. Las opciones son:

  - **Inicio de sesión automático (Windows 10 versión 1803 y posteriores)**: se usa en quioscos en entornos orientados al público que no requieren que el usuario inicie sesión, similar a una cuenta de invitado. Esta configuración usa el [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Cuenta de usuario local**: **agregue** la cuenta de usuario local (en el dispositivo). La cuenta que especifique inicia sesión en la pantalla completa.
  - **Usuario o grupo de Azure AD (Windows 10 versión 1803 y posteriores)**: haga clic en **Agregar** y seleccione los usuarios o grupos de Azure AD en la lista. Puede seleccionar varios usuarios y grupos. Elija **Seleccionar** para guardar los cambios.
  - **Visitante de HoloLens**: la cuenta de visitante es una cuenta de invitado que no requiere ninguna credencial de usuario ni autenticación, como se describe en [Conceptos del modo de equipo compartido](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Explorador y aplicaciones**: agregue las aplicaciones que se van a ejecutar en el dispositivo de pantalla completa. Recuerde que puede agregar varias aplicaciones.

  - **Exploradores**

    - **Agregar Microsoft Edge**: Microsoft Edge se agrega a la cuadrícula de la aplicación, y todas las aplicaciones pueden ejecutar en esta pantalla. Elija la **tipo de modo de quiosco de Microsoft Edge**:

      - **Modo normal (versión completa de Microsoft Edge)**: se ejecuta una versión completa de Microsoft Edge con todas las características de exploración. Se guardan los datos de usuario y el estado entre sesiones.
      - **Exploración pública (InPrivate)**: se ejecuta una versión de varias pestaña de InPrivate de Microsoft Edge con una experiencia adaptada a los quioscos que se ejecutan en modo de pantalla completa.

      Para obtener más información sobre estas opciones, consulte [modo de pantalla completa de la implementación de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Esta configuración habilita el explorador Microsoft Edge en el dispositivo. Para configurar opciones específicas de Microsoft Edge, cree un perfil de configuración de dispositivo (**configuración del dispositivo** > **perfiles** > **Crear perfil**  >  **Windows 10** para plataforma > **restricciones de dispositivos** >  **explorador Microsoft Edge**). [Explorador Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) se enumeran y describen las opciones disponibles.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Agregar explorador del Quiosco**: esta configuración controla una aplicación de explorador web en el quiosco. Asegúrese de implementar una aplicación de explorador web en los dispositivos del quiosco mediante [Aplicaciones cliente](apps-add.md).

      Escriba los valores siguientes:

      - **Dirección URL de la página principal predeterminada**: escriba la dirección URL predeterminada que abre el explorador del quiosco cuando se abre o se reinicia el explorador. Por ejemplo, escriba `http://bing.com` o `http://www.contoso.com`.

      - **Botón Inicio**: **muestre** u **oculte** el botón Inicio del explorador del quiosco. De forma predeterminada, el botón no aparece.

      - **Botones de navegación**: **muestre** u **oculte** los botones Adelante y Atrás. De forma predeterminada, los botones de navegación no se muestran.

      - **Botón Finalizar sesión**: **muestre** u **oculte** el botón Finalizar sesión. Cuando se muestra, el usuario hace clic en el botón y la aplicación solicita que finalice la sesión. Cuando se confirma, el explorador borra todos los datos de exploración (las cookies, la caché, etc.) y luego abre la dirección URL predeterminada. De forma predeterminada, el botón no aparece.

      - **Actualizar el explorador después del tiempo de inactividad**: escriba la cantidad de tiempo de inactividad (1-1440 minutos) hasta que el explorador del quiosco se reinicie con un nuevo estado. El tiempo de inactividad es el número de minutos desde la última interacción del usuario. De forma predeterminada, el valor está vacío o en blanco, lo que significa que no hay ningún tiempo de espera de inactividad.

      - **Sitios web permitidos**: use esta opción para permitir que sitios web específicos se abran. En otras palabras, puede usar esta característica para restringir o impedir sitios web en el dispositivo. Por ejemplo, puede permitir que todos los sitios web de `contoso.com*` se abran. De forma predeterminada, se permiten todos los sitios web.

        Para permitir sitios web específicos, cargue un archivo .csv que incluye una lista de los sitios web permitidos. Si no agrega un archivo .csv, se permitirán todos los sitios web.

      Haga clic en **Aceptar** para guardar los cambios.

  - **Aplicaciones**

    - **Agregar aplicación de la tienda**: agregue una aplicación de Microsoft Store para Empresas. Si no aparece ninguna aplicación, puede obtenerlas y [agregarlas a Intune](store-apps-windows.md). Por ejemplo, puede agregar Kiosk Browser, Excel, OneNote y mucho más.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Agregar aplicación Win32**: una aplicación Win32 es una aplicación de escritorio tradicional, como Visual Studio Code o Google Chrome. Escriba las propiedades siguientes:

      - **Nombre de la aplicación**: requerido. Escriba un nombre para la aplicación.
      - **Ruta de acceso local**: requerida. Escriba la ruta de acceso al archivo ejecutable, como `C:\Program Files (x86)\Microsoft VS Code\Code.exe` o `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
      - **Identificador de modelo del usuario de la aplicación (AUMID)**: escriba el identificador de modelo de usuario de la aplicación (AUMID) de la aplicación Win32. Esta configuración determina el diseño de inicio del icono en el escritorio. Para obtener este identificador, vea [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).

      Haga clic en **Aceptar** para guardar los cambios.

    - **Agregar por AUMID**: use esta opción para agregar aplicaciones de Windows de bandeja de entrada, como el Bloc de notas o la calculadora. Escriba las propiedades siguientes:

      - **Nombre de la aplicación**: requerido. Escriba un nombre para la aplicación.
      - **Identificador de modelo de usuario de aplicación (AUMID)**: requerido. Escriba el identificador de modelo de usuario de aplicación (AUMID) de la aplicación de Windows. Para obtener este identificador, vea [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Buscar el identificador de modelo de usuario de aplicación de una aplicación instalada).

      Haga clic en **Aceptar** para guardar los cambios.

    - **Ejecución automática de**: opcional. Elija una aplicación para inicio automático cuando el usuario inicia sesión. Solo una única aplicación puede ser AutoLaunched.
    - **Tamaño de icono**: requerido. Elija un tamaño de icono de la aplicación pequeño, mediano, ancho o grande.

  > [!TIP]
  > Una vez agregadas todas las aplicaciones, puede modificar el orden de visualización haciendo clic en ellas y arrastrándolas en la lista.  

- **Usar diseño de inicio alternativo**: elija **Sí** para especificar un archivo XML que describa el modo en que las aplicaciones aparecen en el menú Inicio, incluido el orden de las aplicaciones. Use esta opción si necesita personalizar más el menú Inicio. [Personalizar y exportar el diseño de la pantalla Inicio](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) proporciona algunas instrucciones y XML de ejemplo.

- **Barra de tareas de Windows**: elija **Mostrar** u **Ocultar** la barra de tareas. De forma predeterminada, la barra de tareas no aparece. Se muestran iconos, por ejemplo, el icono de Wi-Fi, pero los usuarios finales no pueden cambiar la configuración.

- **Permitir el acceso a la carpeta descargas**: elija **Sí** para permitir que los usuarios accedan a la carpeta descargas en el Explorador de Windows. De forma predeterminada, el acceso a la carpeta de descargas está deshabilitado. Esta característica se usa normalmente para los usuarios finales para tener acceso a elementos descargados desde un explorador.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de pantalla completa para dispositivos [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) y [Windows Holographic for Business](kiosk-settings-holographic.md).
