---
title: 'Configuración de quiosco para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Configure los dispositivos con Windows 10 (y versiones posteriores) como pantallas completas con una aplicación y con varias, incluida la personalización del menú Inicio, la adición de aplicaciones, la barra de tareas y la configuración de un explorador web. Configure también dispositivos con Windows Holographic for Business como pantallas completas con varias aplicaciones en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6db58b1b1f19f789a2163f497c1f0da4c7c034a5
ms.sourcegitcommit: 5f6117b83f96f7d93dde3685c2ff2b67ae53740b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39481128"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Configuración de quiosco para Windows 10 (y versiones posteriores) en Intune

Los perfiles de quiosco se usan para configurar dispositivos Windows 10 para que ejecuten una aplicación o varias. Al crear un perfil de quiosco, también se elige si se muestra un menú Inicio, si se instala un explorador web y mucho más.

## <a name="kiosk-settings"></a>Configuración de quiosco

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Introduzca las siguientes propiedades:

   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
   - **Descripción**: escriba una descripción para el perfil Es opcional, pero se recomienda hacerlo.
   - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
   - **Tipo de perfil**: seleccione **Quiosco (versión preliminar)**.
   
4. Seleccione **Quiosco** > **Agregar**.
5. Escriba un **Nombre de la configuración de quiosco** para el quiosco. Este nombre identifica un grupo de aplicaciones, la distribución de estas aplicaciones en el menú Inicio y los usuarios que están asignados a esta configuración de quiosco.
6. Seleccione el **Modo de quiosco**. **Modo de quiosco**: identifica el tipo de modo de quiosco admitido por la directiva. Las opciones son:

    - **No configurado** (valor predeterminado): la directiva no habilita la pantalla completa.
    - **Quiosco a pantalla completa con una sola aplicación**: el perfil habilita el dispositivo para que se ejecute como una cuenta de usuario único y lo bloquea en una única Plataforma universal de Windows (UWP). Así que cuando el usuario inicia sesión, se inicia una aplicación concreta. Este modo también evita que el usuario abra nuevas aplicaciones o modifique la aplicación en ejecución.
    - **Quiosco con varias aplicaciones**: el perfil permite que el dispositivo ejecute varias aplicaciones de Plataforma universal de Windows (UWP) o aplicaciones de Win32. También puede asignar diferentes aplicaciones para distintas cuentas de usuario. Solo estarán disponibles para el usuario las aplicaciones que agregue. La ventaja de un quiosco con varias aplicaciones, o un dispositivo para un propósito fijo, es que proporciona una experiencia fácil de entender para los usuarios, ya que solo acceden a las aplicaciones que necesitan. Además, se quitan de la vista las aplicaciones que no necesitan.

#### <a name="single-full-screen-app-kiosks"></a>Quioscos a pantalla completa con una sola aplicación
Escriba los valores siguientes:

- **Identificador de la aplicación para Plataforma universal de Windows (UWP)**: escriba el ** identificador de modelo de usuario de aplicación (AUMID)** de la aplicación de quiosco. O seleccione una aplicación administrada existente que haya agregado mediante [Aplicaciones móviles](apps-add.md).

    Vea [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Buscar el identificador de modelo de usuario de aplicación de una aplicación instalada).

- **Tipo de cuenta de usuario**: estas son las opciones:

  - **Inicio de sesión automático**: en el caso de quioscos en entornos de uso público con inicio de sesión automático habilitado, se debe usar un usuario con los privilegios mínimos (por ejemplo, la cuenta de usuario estándar local). Para configurar una cuenta de Azure Active Directory (AD) para el modo de pantalla completa, use el formato `AzureAD\user@contoso.com`.
  - **Cuenta de usuario local**: especifique la cuenta de usuario local (en el dispositivo) o el inicio de sesión de cuenta de Azure AD asociado a la aplicación de quiosco. En el caso de las cuentas unidas a dominios de Azure AD, especifique la cuenta con el formato `domain\username@tenant.org`.

#### <a name="multi-app-kiosks"></a>Pantallas completas con varias aplicaciones
Las aplicaciones en este modo están disponibles en el menú Inicio. Estas aplicaciones son las únicas que el usuario puede abrir. 

Las [pantallas completas con varias aplicaciones](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) usan una configuración de pantalla completa que muestra las aplicaciones permitidas y otras opciones.

Escriba los valores siguientes:

- **Agregar aplicación Win32**: una aplicación Win32 es una aplicación de escritorio tradicional. Escriba el **Nombre de aplicación** y el **Identificador**. El **Identificador** es el nombre de ruta de acceso completa del archivo ejecutable correspondiente al dispositivo.
- [Agregar aplicaciones administradas](apps-add.md): seleccione una aplicación administrada existente que haya agregado mediante **Aplicaciones móviles en Intune**.
- **Agregar aplicación por AUMID**: escriba el [AUMID de la aplicación](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (aplicaciones UWP).
- **Barra de tareas**: elija **Habilitar** (mostrar) la barra de tareas o mantenerla **No configurada** (oculta) en la pantalla completa.
- **Diseño del menú Inicio**: especifique un archivo XML que describa el modo en que las aplicaciones aparecen en el menú Inicio, incluido el orden de las aplicaciones. [Personalizar y exportar el diseño de la pantalla Inicio](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) proporciona algunas instrucciones y XML de ejemplo.

  [Crear un quiosco de Windows 10 que ejecute varias aplicaciones](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) proporciona más detalles sobre cómo usar y crear archivos XML.

- **Tipo de cuenta de usuario**: agregue una o varias cuentas de usuario que puedan usar las aplicaciones que agregue. Cuando la cuenta inicia sesión, solo están disponibles las aplicaciones definidas en la configuración. La cuenta de usuario puede ser local en el dispositivo o un inicio de sesión de cuenta de Azure AD asociada a la aplicación de quiosco.

    En el caso de quioscos en entornos de uso público con inicio de sesión automático habilitado, se debe usar un tipo de usuario con los privilegios mínimos (por ejemplo, la cuenta de usuario estándar local). Para configurar una cuenta de Azure Active Directory (AD) para el modo de pantalla completa, use el formato `domain\user@tenant.com`.

## <a name="kiosk-web-browser-settings"></a>Configuración del explorador web del quiosco

Esta configuración controla una aplicación de explorador web en el quiosco. Asegúrese de implementar una aplicación de explorador web en los dispositivos del quiosco mediante [Aplicaciones móviles](apps-add.md).

1. Escriba los valores siguientes:

    - **Dirección URL de la página principal predeterminada**: escriba la dirección URL predeterminada que abre el explorador del quiosco cuando se abre o se reinicia el explorador.

    - **Botón Inicio**: muestre (**Permitir**) u oculte (**No configurado**) el botón Inicio del explorador del quiosco. De forma predeterminada, el botón está definido como No configurado.

    - **Botón de navegación**: muestre (**Permitir**) u oculte (**No configurado**) los botones Adelante y Atrás. De forma predeterminada, los botones de navegación están definidos como No configurados.

    - **Botón Finalizar sesión**: muestre (**Permitir**) u oculte (**No configurado**) el botón Finalizar sesión. Cuando se muestra, el usuario hace clic en el botón y la aplicación solicita que finalice la sesión. Cuando se confirma, el explorador borra todos los datos de exploración (las cookies, la caché, etc.) y vuelve a la dirección URL predeterminada. De forma predeterminada, el botón está definido como No configurado. 

    - **Actualizar el explorador cuando el usuario supera el límite de tiempo de inactividad**: escriba la cantidad de tiempo de inactividad de sesión en minutos hasta que el explorador del quiosco se reinicie con un nuevo estado. El valor es un entero entre 1 y 1440 minutos. De forma predeterminada, el valor está vacío o en blanco, lo que significa que no hay ningún tiempo de espera de inactividad.

    - **Sitios web bloqueados**: lista de direcciones URL de sitios web bloqueados (con compatibilidad con caracteres comodín). Use esta opción para impedir que el explorador abra determinados sitios. También puede **Importar** un archivo .csv que contiene una lista. O bien, crear un archivo .csv (**Exportar**) que contiene los sitios que agregue.

    - **Excepciones de sitios web**: lista de excepciones para las direcciones URL de sitios web bloqueados (con compatibilidad con caracteres comodín). Use esta opción para permitir al explorador abrir sitios específicos. Estas excepciones son un subconjunto de las direcciones URL bloqueadas. Si una dirección URL se encuentra en la lista de sitios web bloqueados y la lista de excepciones de sitios web, la excepción surte efecto.

    También puede **Importar** un archivo .csv que contiene una lista. O bien, crear un archivo .csv (**Exportar**) que contiene los sitios que agregue.

2. Haga clic en **Aceptar** para guardar los cambios.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

En los dispositivos con Windows Holographic for Business, puede configurar estos dispositivos para que se ejecuten en modo de pantalla completa con una sola aplicación o con varias. 

#### <a name="single-full-screen-app-kiosks"></a>Quioscos a pantalla completa con una sola aplicación
Escriba los valores siguientes:

- **Identificador de la aplicación para Plataforma universal de Windows (UWP)**: escriba el ** identificador de modelo de usuario de aplicación (AUMID)** de la aplicación de quiosco. O seleccione una aplicación administrada existente que haya agregado mediante [Aplicaciones móviles](apps-add.md).

    Para obtener el identificador, vea [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Buscar el identificador de modelo de usuario de aplicación de una aplicación instalada).

- **Tipo de cuenta de usuario**: seleccione **Cuenta de usuario local** para escribir la cuenta de usuario local (en el dispositivo), o bien el inicio de sesión de cuenta de Microsoft (MSA) asociado a la aplicación de quiosco. Los tipos de cuenta de usuario **Inicio de sesión automático** no se admiten en Windows Holographic for Business.

#### <a name="multi-app-kiosks"></a>Pantallas completas con varias aplicaciones
Las aplicaciones en este modo están disponibles en el menú Inicio. Estas aplicaciones son las únicas que el usuario puede abrir.

Escriba los valores siguientes:

- [Agregar aplicaciones administradas](apps-add.md): seleccione una aplicación administrada existente que haya agregado mediante **Aplicaciones móviles en Intune**.
- **Agregar aplicación por AUMID**: escriba el [AUMID de la aplicación](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (aplicaciones UWP).
- **Diseño del menú Inicio**: especifique un archivo XML que describa el modo en que las aplicaciones aparecen en el menú Inicio, incluido el orden de las aplicaciones. En [Personalizar y exportar el diseño de la pantalla Inicio](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) se proporcionan algunas instrucciones y se incluye un archivo XML específico para dispositivos con Windows Holographic for Business.
- **Tipo de cuenta de usuario**: agregue una o varias cuentas de usuario que puedan usar las aplicaciones que agregue. Las opciones admitidas incluyen: 
  - **Visitante de HoloLens**: la cuenta de visitante es una cuenta de invitado que no requiere ninguna credencial de usuario ni autenticación, como se describe en [Conceptos del modo de equipo compartido](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).
  - **Usuarios de Azure AD**: requiere credenciales de usuario para iniciar sesión en el dispositivo. Use el formato `domain\user@tenant.com`.
  - **Cuentas de usuario local**: requiere credenciales de usuario para iniciar sesión en el dispositivo. 

Cuando la cuenta inicia sesión, solo están disponibles las aplicaciones definidas en la configuración.

## <a name="next-steps"></a>Pasos siguientes
[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
