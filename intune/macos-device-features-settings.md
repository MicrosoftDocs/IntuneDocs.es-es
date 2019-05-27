---
title: 'Configuración de características de dispositivos macOS en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte las opciones para configurar dispositivos macOS para AirPrint y personalizar la ventana de inicio de sesión para mostrar u ocultar los botones de encendido en Microsoft Intune. Consulte los pasos para obtener la dirección IP, la ruta de acceso y la configuración de puertos de un servidor de AirPrint en la red. Use esta configuración en un perfil de configuración de dispositivo para configurar dispositivos macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1826498b3bfa2191900d7574f79051af8f758558
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041711"
---
# <a name="macos-device-feature-settings-in-intune"></a>Configuración de características de dispositivos macOS en Intune

Intune incluye algunas opciones integradas para personalizar las características de los dispositivos macOS. En este artículo se enumeran estas opciones de configuración y se describe lo que hace cada una de ellas. También muestra los pasos para obtener la dirección IP, la ruta de acceso y el puerto de las impresoras AirPrint mediante la aplicación Terminal (emulador).

Esta característica se aplica a:

- macOS

Como parte de la solución de administración de dispositivos móviles (MDM), use estas opciones para crear un mensaje emergente, elegir cómo inician sesión los usuarios, agregar un servidor de AirPrint y mucho más.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos macOS.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo macOS](device-features-configure.md).

## <a name="airprint"></a>AirPrint

- **Dirección IP**: escriba la dirección IPv4 o IPv6 de la impresora. Si usa nombres de host para identificar las impresoras, puede obtener la dirección IP haciendo ping a la impresora en la aplicación Terminal. En la sección [Obtención de la dirección IP y la ruta de acceso](#get-the-ip-address-and-path) (en este artículo) se proporcionan más detalles.
- **Ruta de acceso**: escriba la ruta de acceso de la impresora. La ruta de acceso suele ser `ipp/print` para las impresoras de la red. En la sección [Obtención de la dirección IP y la ruta de acceso](#get-the-ip-address-and-path) (en este artículo) se proporcionan más detalles.
- **Puerto** (iOS 11.0 y versiones posteriores) escriba el puerto de escucha del destino de AirPrint. Si se deja esta propiedad en blanco, AirPrint usa el puerto predeterminado.
- **TLS** (iOS 11.0 y versiones posteriores): elija **Habilitar** para proteger las conexiones AirPrint con Seguridad de la capa de transporte (TLS).

**Agregue** el servidor de AirPrint. Puede agregar varios servidores AirPrint.

- **Importar** (opcional): también puede **importar** un archivo separado por comas (.csv) que incluya una lista de impresoras AirPrint. Además, después de agregar impresoras AirPrint en Intune, puede **Exportar** esta lista.

Haga clic en **Aceptar** para guardar la configuración.

### <a name="get-the-ip-address-and-path"></a>Obtención de la dirección IP y la ruta de acceso

Para agregar servidores AirPrinter, necesita la dirección IP de la impresora, la ruta de acceso de recursos y el puerto. Los pasos siguientes muestran cómo obtener esta información.

1. En un equipo Mac conectado a la misma red local (subred) que las impresoras AirPrint, abra **Terminal** (en **/Aplicaciones/Utilidades**).
2. En la aplicación Terminal, escriba `ippfind` y seleccione Entrar.

    Anote la información de la impresora. Por ejemplo, puede devolver algo parecido a `ipp://myprinter.local.:631/ipp/port1`. La primera parte es el nombre de la impresora. La última parte (`ipp/port1`) es la ruta de acceso del recurso.

3. En Terminal, escriba `ping myprinter.local` y seleccione Entrar.

   Anote la dirección IP. Por ejemplo, puede devolver algo parecido a `PING myprinter.local (10.50.25.21)`.

4. Use los valores de dirección IP y de ruta de acceso del recurso. En este ejemplo, la dirección IP es `10.50.25.21` y la ruta de acceso del recurso es `/ipp/port1`.

## <a name="login-window"></a>Ventana de inicio de sesión

### <a name="window-layout"></a>Diseño de ventana

- **Mostrar información adicional en la barra de menús**: cuando se selecciona el área de tiempo en la barra de menús, **Permitir** muestra el nombre de host y la versión de macOS. **No configurado** (valor predeterminado) no muestra esta información en la barra de menús.
- **Banner**: escriba un mensaje que se mostrará en la pantalla de inicio de sesión del dispositivo. Por ejemplo, escriba la información de su organización, un mensaje de bienvenida, información de objetos perdidos, etc.
- **Elegir formato de inicio de sesión**: elija cómo inician sesión en el dispositivo los usuarios. Las opciones son:
  - **Solicitar nombre de usuario y contraseña** (valor predeterminado): los usuarios deben escribir un nombre de usuario y una contraseña.
  - **Enumerar todos los usuarios, solicitar contraseña**: los usuarios deben seleccionar su nombre de usuario de una lista de usuarios y, después, escribir su contraseña. Configure también:

    - **Usuarios locales**: **Ocultar** no muestra las cuentas de usuarios locales en la lista de usuarios, que puede incluir las cuentas de administrador y estándar. Se muestran únicamente las cuentas de usuario de red y del sistema. **No configurado** (valor predeterminado) muestra las cuentas de usuarios locales en la lista de usuarios.
    - **Cuentas móviles**: **Ocultar** no muestra las cuentas móviles en la lista de usuarios. **No configurado** (valor predeterminado) muestra las cuentas móviles en la lista de usuarios. Algunas cuentas móviles pueden aparecer como usuarios de red.
    - **Usuarios de red**: seleccione **Mostrar** para enumerar los usuarios de red en la lista de usuarios. **No configurado** (valor predeterminado) no muestra las cuentas de usuarios de red en la lista de usuarios.
    - **Usuarios administradores**: **Ocultar** no muestra las cuentas de usuarios administradores en la lista de usuarios. **No configurado** (valor predeterminado) muestra las cuentas de usuarios administradores en la lista de usuarios.
    - **Otros usuarios**: seleccione **Mostrar** para enumerar los usuarios de **Otros...** en la lista de usuarios. **No configurado** (valor predeterminado) no muestra las cuentas de otros usuarios en la lista de usuarios.

### <a name="login-screen-power-settings"></a>Configuración de energía de la pantalla de inicio de sesión

- **Botón Apagar**: **Ocultar** no muestra el botón de apagado en la pantalla de inicio de sesión. **No configurado** (valor predeterminado) muestra el botón de apagado.
- **Botón Reiniciar**: **Ocultar** no muestra el botón de reinicio en la pantalla de inicio de sesión. **No configurado** (valor predeterminado) muestra el botón de reinicio.
- **Botón de suspensión**: **Ocultar** no muestra el botón de suspensión en la pantalla de inicio de sesión. **No configurado** (valor predeterminado) muestra el botón de suspensión.

### <a name="other"></a>Otros

- **Deshabilitar inicio de sesión del usuario desde la consola**: **Deshabilitar** oculta la línea de comandos de macOS usada para iniciar sesión. Para usuarios típicos, **deshabilite** esta configuración. **No configurado** (valor predeterminado) permite a los usuarios avanzados iniciar sesión con la línea de comandos de macOS. Para entrar en modo de consola, los usuarios escriben `>console` en el campo de nombre de usuario de campo y deben autenticarse en la ventana de la consola.

### <a name="apple-menu"></a>Menú Apple

Después de que los usuarios inicien sesión en los dispositivos, la siguiente configuración afecta a lo que puede hacer.

- **Deshabilitar Apagar**: **Deshabilitar** impide que los usuarios seleccionen la opción **Apagado** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Apagado** en el dispositivo.
- **Deshabilitar Reiniciar**: **Deshabilitar** impide que los usuarios seleccionen la opción **Reiniciar** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Reiniciar** en el dispositivo.
- **Deshabilitar Desconectar**: **Deshabilitar** impide que los usuarios seleccionen la opción **Desconectar** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Desconectar** en el dispositivo.
- **Deshabilitar Cerrar sesión** (macOS 10.13 y versiones posteriores): **Deshabilitar** impide que los usuarios seleccionen la opción **Cerrar sesión** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Cerrar sesión** en el dispositivo.
- **Deshabilitar pantalla de bloqueo** (macOS 10.13 y versiones posteriores): **Deshabilitar** impide que los usuarios seleccionen la opción **Pantalla de bloqueo** después de que el usuario inicie sesión. **No configurado** (valor predeterminado) permite que los usuarios seleccionen el elemento de menú **Pantalla de bloqueo** en el dispositivo.

Haga clic en **Aceptar** para guardar la configuración.

## <a name="next-steps"></a>Pasos siguientes

- Vea toda la configuración para dispositivos [iOS](ios-device-features-settings.md).
- [Asigne este perfil](device-profile-assign.md) a sus grupos y [supervise su estado](device-profile-monitor.md).
