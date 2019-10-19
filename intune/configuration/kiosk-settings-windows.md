---
title: 'Configuración de quiosco para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Configure los dispositivos con Windows 10 y versiones posteriores como pantallas completas con una sola aplicación y con varias, personalice el menú Inicio, agregue aplicaciones, muestre la barra de tareas y configure un explorador web en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17dce8f7c5aa55a2044e663f724a5784cee8b375
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506683"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Configuración de dispositivos con Windows 10 y versiones posteriores para ejecutarse como una pantalla completa en Intune

En los dispositivos con Windows 10 y versiones posteriores, puede configurar estos dispositivos para que se ejecuten en modo de pantalla completa con una sola aplicación o con varias.

En este artículo se enumeran y describen los diferentes valores de configuración que puede controlar en los dispositivos con Windows 10 y versiones posteriores. Como parte de su solución de administración de dispositivos móviles (MDM), use estas configuraciones para definir sus dispositivos con Windows 10 y versiones posteriores a fin de que se ejecuten en pantalla completa.

Como administrador de Intune, puede crear y asignar estas opciones de configuración a los dispositivos.

Para más información sobre la característica de pantalla completa de Windows en Intune, consulte la [configuración de las opciones de pantalla completa](../kiosk-settings.md).

## <a name="before-you-begin"></a>Antes de comenzar

- [Cree el perfil](kiosk-settings.md#create-the-profile).

- Este perfil de pantalla completa está directamente relacionado con el perfil de restricciones de dispositivo que se crea mediante la [Configuración de quiosco de Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser). En resumen:

  1. Cree este perfil de pantalla completa para ejecutar el dispositivo en pantalla completa.
  2. Cree el [perfil de restricciones de dispositivo](device-restrictions-windows-10.md#microsoft-edge-browser) y configure opciones y características específicas que se permiten en Microsoft Edge.

> [!IMPORTANT]
> Asegúrese de asignar este perfil de pantalla completa a los mismos dispositivos que su [perfil de Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

## <a name="single-full-screen-app-kiosks"></a>Quioscos a pantalla completa con una sola aplicación

Solo se ejecuta una aplicación en el dispositivo.

- **Seleccionar un modo de pantalla completa**: elija **Pantalla completa con aplicación única**.

- **Tipo de inicio de sesión de usuario**: las aplicaciones que se agregan se ejecutan como la cuenta de usuario especificada. Las opciones son:

  - **Inicio de sesión automático (Windows 10 versión 1803 y posteriores)** : se usa en quioscos en entornos orientados al público que no requieren que el usuario inicie sesión, similar a una cuenta de invitado. Esta configuración usa el [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Cuenta de usuario local**: escriba la cuenta de usuario local (en el dispositivo). La cuenta que especifique inicia sesión en la pantalla completa.

- **Tipo de aplicación**: seleccione el tipo de aplicación. Las opciones son:

  - **Agregar explorador Microsoft Edge**: seleccione **Explorador Microsoft Edge** y elija el **Tipo de modo de quiosco de Microsoft Edge**:

    - **Señal digital o interactiva**: abra una URL en pantalla completa y muestre solo el contenido de ese sitio web. En [Configurar señales digitales](https://docs.microsoft.com/windows/configuration/setup-digital-signage) se proporciona más información sobre esta característica.
    - **Exploración pública (InPrivate)** : se ejecuta una versión limitada de varias pestaña de Microsoft Edge. Los usuarios pueden explorar públicamente o finalizar su sesión de exploración.

    Para más información sobre estas opciones, vea [Implementar la pantalla completa de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Esta valor habilita el explorador de Microsoft Edge en el dispositivo. Para configurar opciones específicas de Microsoft Edge, cree un perfil de configuración de dispositivo (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10** para la plataforma > **Restricciones de dispositivos** >  **Explorador de Microsoft Edge**). [Explorador de Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) muestra y describe las opciones disponibles.

  - **Agregar explorador del Quiosco**: seleccione **Configuración del explorador del Quiosco**. Esta configuración controla una aplicación de explorador web en el quiosco. Asegúrese de obtener la [aplicación de pantalla completa del explorador](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) y agréguela a Intune como una [aplicación cliente](../apps/apps-add.md). A continuación, asigne la aplicación a los dispositivos de pantalla completa.

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

    > [!NOTE]
    > Los quioscos de Windows 10 con el inicio de sesión automático habilitado mediante Microsoft quiosco Browser deben usar una licencia sin conexión del Microsoft Store para empresas. Este requisito se debe a que el inicio de sesión automático utiliza una cuenta de usuario local sin credenciales de Azure Active Directory (AD). Por lo tanto, no se pueden evaluar las licencias en línea. Para obtener más información, vea [Distribuir aplicaciones sin conexión](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Agregar aplicación de la tienda**: elija **Agregar una aplicación de la tienda** y seleccione una aplicación de la lista.

    ¿No aparece ninguna aplicación? Agregue algunas siguiendo los pasos descritos en [Aplicaciones cliente](../apps/apps-add.md).
    
 - **Especificar la ventana de mantenimiento para los reinicios de la aplicación**: el valor predeterminado es "no configurado", seleccione "requerir" para buscar aplicaciones que requieran un reinicio para completar la instalación.
 
     Si usa el explorador de quiosco u otro Microsoft Store para la aplicación empresarial, decida con qué frecuencia se deben buscar las actualizaciones de aplicaciones que requieran reinicio para completar la instalación de la aplicación. Si no está configurado, Microsoft Store para las aplicaciones empresariales se reiniciarán en un momento no programado 3 días después de instalar una actualización de la aplicación.
     
     - **Hora de inicio**de la ventana de mantenimiento: seleccione la fecha y la hora del día en que se iniciará la comprobación de las actualizaciones de aplicaciones que requieran reinicio. La hora de inicio predeterminada es medianoche o cero minutos.
     
     - **Periodicidad**de la ventana de mantenimiento: el valor predeterminado es diariamente.
         Establezca la frecuencia con que se realizarán las ventanas de mantenimiento para las actualizaciones de aplicaciones. La recomendación es diaria para evitar reinicios de aplicaciones no programados.

  [ApplicationManagement/ScheduleForceRestartForUpdateFailures CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures)

## <a name="multi-app-kiosks"></a>Pantallas completas con varias aplicaciones

Las aplicaciones en este modo están disponibles en el menú Inicio. Estas aplicaciones son las únicas que el usuario puede abrir. Si una aplicación tiene una dependencia de otra, ambas deben estar incluidas en la lista de aplicaciones permitidas. Por ejemplo, Internet Explorer de 64 bits tiene una dependencia de Internet Explorer de 32 bits, por lo que debe permitir ambas, "C:\Program Files\internet explorer\iexplore.exe" y "C:\Program Files (x86)\Internet Explorer\iexplore.exe". 

- **Seleccionar un modo de pantalla completa**: elija **Pantalla completa con varias aplicaciones**.

- **Destino de Windows 10 en dispositivos en modo S**:
  - **Sí**: permite aplicaciones de la Tienda y aplicaciones AUMID (se excluyen las aplicaciones Win32) en el perfil de pantalla completa.
  - **No**: permite aplicaciones de la Tienda, Win32 y AUMID en el perfil de pantalla completa. Este perfil de pantalla completa no se implementa en dispositivos en modo S.

- **Tipo de inicio de sesión de usuario**: las aplicaciones que se agregan se ejecutan como la cuenta de usuario especificada. Las opciones son:

  - **Inicio de sesión automático (Windows 10 versión 1803 y posteriores)** : se usa en quioscos en entornos orientados al público que no requieren que el usuario inicie sesión, similar a una cuenta de invitado. Esta configuración usa el [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Cuenta de usuario local**: **agregue** la cuenta de usuario local (en el dispositivo). La cuenta que especifique inicia sesión en la pantalla completa.
  - **Usuario o grupo de Azure AD (Windows 10 versión 1803 y posteriores)** : haga clic en **Agregar** y seleccione los usuarios o grupos de Azure AD en la lista. Puede seleccionar varios usuarios y grupos. Elija **Seleccionar** para guardar los cambios.
  - **Visitante de HoloLens**: la cuenta de visitante es una cuenta de invitado que no requiere ninguna credencial de usuario ni autenticación, como se describe en [Conceptos del modo de equipo compartido](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Explorador y aplicaciones**: agregue las aplicaciones que se van a ejecutar en el dispositivo de pantalla completa. Recuerde que puede agregar varias aplicaciones.

  - **Exploradores**

    - **Agregar explorador Microsoft Edge**: se agrega Microsoft Edge a la cuadrícula de la aplicación, y todas las aplicaciones se pueden ejecutar en esta pantalla completa. Elija el **Tipo de modo de quiosco de Microsoft Edge**:

      - **Modo normal (versión completa de Microsoft Edge)** : se ejecuta una versión completa de Microsoft Edge con todas las características de exploración. Los datos de usuario y el estado se guardan entre sesiones.
      - **Exploración pública (InPrivate)** : se ejecuta una versión de varias pestaña de InPrivate de Microsoft Edge con una experiencia adaptada a los quioscos que se ejecutan en modo de pantalla completa.

      Para más información sobre estas opciones, vea [Implementar la pantalla completa de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Esta valor habilita el explorador de Microsoft Edge en el dispositivo. Para configurar opciones específicas de Microsoft Edge, cree un perfil de configuración de dispositivo (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10** para la plataforma > **Restricciones de dispositivos** >  **Explorador de Microsoft Edge**). [Explorador de Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) muestra y describe las opciones disponibles.

    - **Agregar explorador del Quiosco**: esta configuración controla una aplicación de explorador web en el quiosco. Asegúrese de implementar una aplicación de explorador web en los dispositivos del quiosco mediante [Aplicaciones cliente](../apps/apps-add.md).

      Escriba los valores siguientes:

      - **Dirección URL de la página principal predeterminada**: escriba la dirección URL predeterminada que abre el explorador del quiosco cuando se abre o se reinicia el explorador. Por ejemplo, escriba `http://bing.com` o `http://www.contoso.com`.

      - **Botón Inicio**: **muestre** u **oculte** el botón Inicio del explorador del quiosco. De forma predeterminada, el botón no aparece.

      - **Botones de navegación**: **muestre** u **oculte** los botones Adelante y Atrás. De forma predeterminada, los botones de navegación no se muestran.

      - **Botón Finalizar sesión**: **muestre** u **oculte** el botón Finalizar sesión. Cuando se muestra, el usuario hace clic en el botón y la aplicación solicita que finalice la sesión. Cuando se confirma, el explorador borra todos los datos de exploración (las cookies, la caché, etc.) y luego abre la dirección URL predeterminada. De forma predeterminada, el botón no aparece.

      - **Actualizar el explorador después del tiempo de inactividad**: escriba la cantidad de tiempo de inactividad (1-1440 minutos) hasta que el explorador del quiosco se reinicie con un nuevo estado. El tiempo de inactividad es el número de minutos desde la última interacción del usuario. De forma predeterminada, el valor está vacío o en blanco, lo que significa que no hay ningún tiempo de espera de inactividad.

      - **Sitios web permitidos**: use esta opción para permitir que sitios web específicos se abran. En otras palabras, puede usar esta característica para restringir o impedir sitios web en el dispositivo. Por ejemplo, puede permitir que todos los sitios web de `contoso.com*` se abran. De forma predeterminada, se permiten todos los sitios web.

        Para permitir sitios web específicos, cargue un archivo .csv que incluye una lista de los sitios web permitidos. Si no agrega un archivo .csv, se permitirán todos los sitios web.

      > [!NOTE]
      > Los quioscos de Windows 10 con el inicio de sesión automático habilitado mediante Microsoft quiosco Browser deben usar una licencia sin conexión del Microsoft Store para empresas. Este requisito se debe a que el inicio de sesión automático utiliza una cuenta de usuario local sin credenciales de Azure Active Directory (AD). Por lo tanto, no se pueden evaluar las licencias en línea. Para obtener más información, vea [Distribuir aplicaciones sin conexión](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Aplicaciones**

    - **Agregar aplicación de la tienda**: agregue una aplicación de Microsoft Store para Empresas. Si no aparece ninguna aplicación, puede obtenerlas y [agregarlas a Intune](../apps/store-apps-windows.md). Por ejemplo, puede agregar Kiosk Browser, Excel, OneNote y mucho más.

    - **Agregar aplicación Win32**: una aplicación Win32 es una aplicación de escritorio tradicional, como Visual Studio Code o Google Chrome. Escriba las propiedades siguientes:

      - **Nombre de la aplicación**: requerido. Escriba un nombre para la aplicación.
      - **Ruta de acceso local**: requerida. Escriba la ruta de acceso al archivo ejecutable, como `C:\Program Files (x86)\Microsoft VS Code\Code.exe` o `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
      - **Identificador de modelo del usuario de la aplicación (AUMID)** : escriba el identificador de modelo de usuario de la aplicación (AUMID) de la aplicación Win32. Esta configuración determina el diseño de inicio del icono en el escritorio. Para obtener este identificador, vea [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).

    - **Agregar por AUMID**: use esta opción para agregar aplicaciones de Windows de bandeja de entrada, como el Bloc de notas o la calculadora. Escriba las propiedades siguientes:

      - **Nombre de la aplicación**: requerido. Escriba un nombre para la aplicación.
      - **Identificador de modelo de usuario de aplicación (AUMID)** : requerido. Escriba el identificador de modelo de usuario de aplicación (AUMID) de la aplicación de Windows. Para obtener este identificador, vea [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Buscar el identificador de modelo de usuario de aplicación de una aplicación instalada).

    - **Inicio automático**: opcional. Elija una aplicación que se inicie automáticamente cuando el usuario inicie sesión. Solo puede iniciarse automáticamente una única aplicación.
    - **Tamaño de icono**: requerido. Elija un tamaño de icono de la aplicación pequeño, mediano, ancho o grande.

  > [!TIP]
  > Una vez agregadas todas las aplicaciones, puede modificar el orden de visualización haciendo clic en ellas y arrastrándolas en la lista.  

- **Usar diseño de inicio alternativo**: elija **Sí** para especificar un archivo XML que describa el modo en que las aplicaciones aparecen en el menú Inicio, incluido el orden de las aplicaciones. Use esta opción si necesita personalizar más el menú Inicio. [Personalizar y exportar el diseño de la pantalla Inicio](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) proporciona algunas instrucciones y XML de ejemplo.

- **Barra de tareas de Windows**: elija **Mostrar** u **Ocultar** la barra de tareas. De forma predeterminada, la barra de tareas no aparece. Se muestran iconos, por ejemplo, el icono de Wi-Fi, pero los usuarios finales no pueden cambiar la configuración.

- **Permitir acceso a la carpeta Descargas**: elija **Sí** para permitir que los usuarios accedan a la carpeta de descargas en el Explorador de Windows. De forma predeterminada, el acceso a la carpeta de descargas está deshabilitado. Esta característica se usa normalmente para que los usuarios finales accedan a los elementos descargados de un explorador.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de pantalla completa para dispositivos [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) y [Windows Holographic for Business](kiosk-settings-holographic.md).
