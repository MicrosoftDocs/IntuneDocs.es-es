---
title: 'Configuración de restricciones de dispositivos para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte una lista de todas las configuraciones y sus descripciones para crear restricciones de dispositivo en Windows 10 y dispositivos posteriores. Use estos valores en un perfil de configuración para controlar las capturas de pantalla, los requisitos de contraseña, la configuración de la pantalla completa, las aplicaciones de la tienda, el explorador Microsoft Edge, Windows Defender, el acceso a la nube, el menú de inicio y más en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b3fd474e938e2e85a0a08951a9e3f154d980411
ms.sourcegitcommit: b64869b4be357c0741ec01b1a2f0bae13efce937
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "69998947"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos con Windows 10 y versiones posteriores para permitir o restringir características mediante Intune

En este artículo se enumeran y describen todos los diferentes valores de configuración que puede controlar en los dispositivos con Windows 10 y versiones posteriores. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, personalizar la pantalla de bloqueo, usar Windows Defender, etc.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos con Windows 10.

> [!Note]
> No todas las opciones están disponibles en todas las ediciones de Windows. Para ver las ediciones admitidas, consulte los [CSP de directiva](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (se abre otro sitio web de Microsoft).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>Tienda de aplicaciones

Estas opciones de configuración usan [ApplicationManagement policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) (CSP de directiva de ApplicationManagement), que también indica las ediciones de Windows compatibles.

- **Tienda de aplicaciones** (solo móviles): **Sin configurar** (valor predeterminado) permite a los usuarios finales acceder a la tienda de aplicaciones desde dispositivos móviles. **Bloquear** evita el uso de la tienda de aplicaciones.
- **Actualizar automáticamente las aplicaciones de la tienda**: **Sin configurar** (valor predeterminado) permite que las aplicaciones instaladas desde Microsoft Store se actualicen automáticamente. **Bloquear** evita que las actualizaciones se instalen automáticamente.
- **Instalación de aplicaciones de confianza**: elija si se pueden instalar aplicaciones que no sean de Microsoft Store, lo que también se conoce como transferencia local. La transferencia local consiste en instalar y luego ejecutar o probar una aplicación no certificada por Microsoft Store. Por ejemplo, una aplicación interna solo para la empresa. Las opciones son:
  - **Sin configurar** (valor predeterminado): usa el sistema operativo predeterminado.
  - **Bloquear**: evita la transferencia local. No se pueden instalar aplicaciones que no sean de Microsoft Store.
  - **Permitir**: permite la transferencia local. Se pueden instalar aplicaciones que no sean de Microsoft Store.
- **Desbloqueo de desarrollador**: permite que los usuarios finales modifiquen la configuración de desarrollador de Windows para, por ejemplo, permitir aplicaciones de transferencia local. Las opciones son:
  - **Sin configurar** (valor predeterminado): usa el sistema operativo predeterminado.
  - **Bloquear**: evita el modo de desarrollador y la transferencia local de aplicaciones.
  - **Permitir**: permite el modo de desarrollador y la transferencia local de aplicaciones.

  [Habilitar el dispositivo para el desarrollo](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) contiene más información sobre esta característica.

- **Datos de aplicación compartidos entre usuarios**: elija **Permitir** para compartir datos de aplicación entre distintos usuarios en el mismo dispositivo y con otras instancias de esa aplicación. **Sin configurar** (valor predeterminado) evita que se compartan datos con otros usuarios y otras instancias de la misma aplicación.
- **Usar solo una tienda privada**: **Permitir** solo permite que se descarguen aplicaciones de una tienda privada y no de la tienda pública, incluido un catálogo comercial. **Sin configurar** (valor predeterminado) permite que se descarguen aplicaciones de una tienda privada y de una pública.
- **Inicio de aplicaciones de la tienda**: **Bloquear** deshabilita todas las aplicaciones instaladas previamente en el dispositivo o descargadas de Microsoft Store. **Sin configurar** (valor predeterminado) permite abrir estas aplicaciones.
- **Instalar los datos de aplicación en el volumen del sistema**: **Bloquear** hace que las aplicaciones dejen de almacenar datos en el volumen del sistema del dispositivo. **Sin configurar** (valor predeterminado) permite que las aplicaciones almacenen datos en el volumen de disco del sistema.
- **Instalar las aplicaciones en la unidad del sistema**: **Bloquear** evita que las aplicaciones se instalen en la unidad del sistema del dispositivo. **Sin configurar** (valor predeterminado) permite que las aplicaciones se instalen en la unidad del sistema.
- **Game DVR** (solo equipos de escritorio): **Bloquear** deshabilita la grabación y difusión de juegos de Windows. **Sin configurar** (valor predeterminado) permite la grabación y difusión de juegos.
- **Aplicaciones solo de la tienda**: esta opción determina la experiencia del usuario cuando los usuarios instalan aplicaciones desde lugares distintos del Microsoft Store. Las opciones son:

  - **No configurado** (valor predeterminado): permite a los usuarios finales instalar aplicaciones desde lugares distintos del Microsoft Store, incluidas las aplicaciones definidas en otras configuraciones de directiva.  
  - **En cualquier lugar**: desactiva las recomendaciones de la aplicación y permite a los usuarios instalar aplicaciones desde cualquier ubicación.  
  - **Solo almacenar**: obliga a los usuarios finales a que solo instalen aplicaciones desde el Microsoft Store.
  - **Recomendaciones**: al instalar una aplicación de la web que está disponible en el Microsoft Store, los usuarios ven un mensaje que le recomienda descargarla de la tienda.  
  - **Preferir tienda**: advierte a los usuarios cuando instalan aplicaciones desde lugares distintos del Microsoft Store.

  [SmartScreen/EnableAppInstallControl CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **Control de usuario sobre las instalaciones**: si está establecido en **Sin configurar** (valor predeterminado), Windows Installer impide que los usuarios cambien las opciones de instalación que habitualmente están reservadas para los administradores del sistema, como entrar al directorio para instalar los archivos. **Bloquear** permite que los usuarios cambien estas opciones de instalación y se omiten algunas de las características de seguridad de Windows Installer.

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **Instalar aplicaciones con privilegios elevados**: si está establecido en **Sin configuración** (valor predeterminado), el sistema aplica los permisos del usuario actual cuando instala programas que un administrador del sistema no implementa ni ofrece. **Bloquear** indica a Windows Installer que use permisos elevados cuando instale cualquier programa en el sistema. Estos privilegios se extienden a todos los programas.

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **Aplicaciones de inicio**: escriba una lista de aplicaciones para abrir después de que un usuario inicie sesión en el dispositivo. Asegúrese de usar una lista delimitada por punto y coma de nombres de familia de paquete (PFN) de aplicaciones Windows. Para que esta directiva funcione, el manifiesto de las aplicaciones Windows debe usar una tarea de inicio.

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

Haga clic en **Aceptar** para guardar los cambios.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

Estas opciones de configuración usan los CSP de [directiva de conectividad](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) y [directiva de Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi), que también enumeran las ediciones de Windows compatibles.

- [Wi-Fi policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) (CSP de directiva de Wi-Fi)

- **Canal de datos móviles**: elija si los usuarios finales pueden usar datos —por ejemplo, para navegar por Internet— cuando están conectados a una red móvil. Las opciones son:
  - **Sin configurar** (valor predeterminado): usa el sistema operativo predeterminado, que puede permitir el canal de datos móviles. Los usuarios finales pueden desactivarlo.
  - **Bloquear**: no permite el canal de datos móviles. Los usuarios finales no pueden activarlo.
  - **Permitir (no editable)** : permite el canal de datos móviles. Los usuarios finales no pueden desactivarlo.

- **Itinerancia de datos**: **Bloquear** evita la itinerancia de datos móviles en el dispositivo. **Sin configurar** (valor predeterminado) permite la itinerancia entre redes al acceder a datos.
- **VPN a través de la red de telefonía móvil**: **Bloquear** evita que el dispositivo acceda a las conexiones VPN cuando se conecta a una red móvil. **Sin configurar** (valor predeterminado) permite que la VPN use cualquier conexión, incluida la móvil.
- **Itinerancia de VPN a través de la red de telefonía móvil**: **Bloquear** evita que el dispositivo acceda a conexiones VPN cuando está en itinerancia en una red móvil. **Sin configurar** (valor predeterminado) permite las conexiones VPN en itinerancia.
- **Servicio de dispositivos conectados**: **Bloquear** deshabilita el componente de plataforma de dispositivos conectados (CDP). CDP habilita la detección de otros dispositivos y la conexión a ellos (a través de Bluetooth/LAN o la nube) para permitir el inicio de aplicaciones remoto, la mensajería remota, las sesiones de aplicación remotas y otras experiencias en varios dispositivos. **Sin configurar** (valor predeterminado) permite el servicio de dispositivos conectados, lo que habilita la detección de otros dispositivos Bluetooth y la conexión a ellos.
- **NFC**: **Bloquear** evita las capacidades de transmisión de datos en proximidad (NFC). **Sin configurar** (valor predeterminado) permite a los usuarios habilitar y configurar las características de NFC en el dispositivo.
- **Wi-Fi**: **Bloquear** evita que los usuarios habiliten, configuren y usen conexiones Wi-Fi en el dispositivo. **Sin configurar** (valor predeterminado) permite las conexiones Wi-Fi.
- **Conectar automáticamente a zonas Wi-Fi**: **Bloquear** evita que los dispositivos se conecten automáticamente a zonas Wi-Fi. **Sin configurar** (valor predeterminado) permite que los dispositivos se conecten automáticamente a zonas Wi-Fi gratuitas y acepten de forma automática los términos y condiciones para la conexión.
- **Configuración manual de Wi-Fi**: **Bloquear** evita que los dispositivos se conecten a Wi-Fi fuera de redes instaladas por el servidor MDM. **Sin configurar** (valor predeterminado) permite a los usuarios finales agregar y configurar sus propios SSID de red de conexiones Wi-Fi.
- **Intervalo de detección de Wi-Fi**: permite especificar con qué frecuencia los dispositivos detectan redes Wi-Fi. Escriba un valor de 1 (más frecuente) a 500 (menos frecuente). El valor predeterminado es `0` (cero).

### <a name="bluetooth"></a>Bluetooth

Estas opciones de configuración usan [Bluetooth policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth) (CSP de directiva de Bluetooth), que también indica las ediciones de Windows compatibles.

- **Bluetooth**: **Bloquear** evita que los usuarios habiliten Bluetooth. **Sin configurar** (valor predeterminado) permite Bluetooth en el dispositivo.
- **Detectabilidad de Bluetooth**: **Bloquear** evita que otros dispositivos con Bluetooth habilitado detecten el dispositivo. **Sin configurar** (valor predeterminado) permite que otros dispositivos con Bluetooth habilitado —por ejemplo, auriculares— detecten el dispositivo.
- **Emparejamiento previo Bluetooth**: **Bloquear** evita que dispositivos Bluetooth específicos se emparejen automáticamente con un dispositivo de host. **Sin configurar** (valor predeterminado) permite el emparejamiento automático con el dispositivo de host.
- **Anuncios de Bluetooth**: **Bloquear** evita que el dispositivo envíe anuncios de Bluetooth. **Sin configurar** (valor predeterminado) permite que el dispositivo envíe anuncios de Bluetooth.
- **Servicios Bluetooth permitidos**: **Agregar** una lista de perfiles y servicios Bluetooth permitidos como cadenas hexadecimales, como `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`.

  [ServicesAllowedList usage guide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) (Guía de uso de ServicesAllowedList) contiene más información sobre la lista de servicios.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

Estas opciones de configuración usan [accounts policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts) (CSP de directiva de cuentas), que también indica las ediciones de Windows compatibles.

- **Cuenta Microsoft**: **Bloquear** evita que los usuarios finales asocien una cuenta Microsoft al dispositivo. **Sin configurar** (valor predeterminado) permite agregar y usar una cuenta Microsoft.
- **Cuenta que no es Microsoft**: **Bloquear** evita que los usuarios finales agreguen cuentas que no son de Microsoft mediante la interfaz de usuario. **Sin configurar** (valor predeterminado) permite que los usuarios agreguen cuentas de correo electrónico que no están asociadas a una cuenta Microsoft.
- **Sincronización de configuración de cuenta Microsoft**: **Sin configurar** (valor predeterminado) permite sincronizar la configuración de dispositivos y aplicaciones asociados a una cuenta Microsoft entre dispositivos. **Bloquear** evita esta sincronización.
- **Ayudante para el inicio de sesión de cuenta Microsoft**: si se establece en **Sin configurar** (valor predeterminado), los usuarios finales pueden iniciar y detener el servicio **Ayudante para el inicio de sesión de cuenta Microsoft** (wlidsvc). Este servicio del sistema operativo permite a los usuarios iniciar sesión en su cuenta Microsoft. **Deshabilitar** evita que los usuarios finales controlen el servicio Ayudante para el inicio de sesión de cuenta Microsoft (wlidsvc).

Haga clic en **Aceptar** para guardar los cambios.

## <a name="cloud-printer"></a>Impresora en la nube

Estas opciones de configuración usan [EnterpriseCloudPrint policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint) (CSP de directiva de EnterpriseCloudPrint), que también indica las ediciones de Windows compatibles.

- **Dirección URL de detección de la impresora**: especifique la dirección URL para encontrar impresoras en la nube. Por ejemplo, escriba `https://cloudprinterdiscovery.contoso.com`.
- **URL de autoridad de acceso a impresoras**: especifique la dirección URL del punto de conexión de autenticación para obtener tokens de OAuth. Por ejemplo, escriba `https://azuretenant.contoso.com/adfs`.
- **GUID de aplicación cliente nativa de Azure**: especifique el GUID de una aplicación cliente autorizada para obtener tokens de OAuth desde OAuthAuthority. Por ejemplo, escriba `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **URI de recurso de servicio de impresión**: indique el URI de recurso de OAuth para el servicio de impresión configurado en Azure Portal. Por ejemplo, escriba `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **N.º máximo de impresoras para consultar**: indique el número máximo de impresoras a las que quiere que se consulte. El valor predeterminado es `20`.
- **URI de recurso de servicio de detección de impresora**: indique el URI de recurso de OAuth para el servicio de detección de impresora configurado en Azure Portal. Por ejemplo, escriba `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Después de configurar la [impresión de Windows Server híbrida en la nube](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), puede configurar estas opciones e implementarlas en los dispositivos Windows.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="control-panel-and-settings"></a>Panel de control y configuración

- **Aplicación Configuración**: **Bloquear** evita que los usuarios finales accedan a la aplicación de configuración de Windows. **Sin configurar** (valor predeterminado) permite que los usuarios abran la aplicación Configuración en el dispositivo.
  - **Sistema**: **Bloquear** evita el acceso al área Sistema de la aplicación Configuración. **Sin configurar** (valor predeterminado) permite el acceso.
    - **Modificación de la configuración de inicio/apagado y suspensión** (solo equipos de escritorio): **Bloquear** evita que los usuarios finales cambien la configuración de inicio/apagado y suspensión en el dispositivo. **Sin configurar** (valor predeterminado) permite que los usuarios cambien la configuración de inicio/apagado y suspensión.
  - **Dispositivos**: **Bloquear** evita el acceso al área Dispositivos de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.
  - **Red e Internet**: **Bloquear** evita el acceso al área Red e Internet de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.
  - **Personalización**: **Bloquear** evita el acceso al área Personalización de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.
  - **Aplicaciones**: **Bloquear** evita el acceso al área Aplicaciones de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.
  - **Cuentas**: **Bloquear** evita el acceso al área Cuentas de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.
  - **Hora e idioma**: **Bloquear** evita el acceso al área Hora e idioma de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.
    - **Modificación de la hora del sistema**: **Bloquear** evita que los usuarios finales cambien la configuración de fecha y hora en el dispositivo. **No configurado** permite que los usuarios cambien esta configuración.
    - **Modificación de la configuración regional** (solo equipos de escritorio): **Bloquear** evita que los usuarios finales cambien la configuración regional en el dispositivo. **No configurado** permite que los usuarios cambien esta configuración.
    - **Modificación de la configuración de idioma** (solo equipos de escritorio): **Bloquear** evita que los usuarios finales cambien la configuración de idioma en el dispositivo. **No configurado** permite que los usuarios cambien esta configuración.

      [Settings policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings) (CSP de directiva de configuración)

  - **Juegos**: **Bloquear** evita el acceso al área Juegos de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.
  - **Accesibilidad**: **Bloquear** evita el acceso al área Accesibilidad de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.
  - **Privacidad**: **Bloquear** evita el acceso al área Privacidad de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.
  - **Actualización y seguridad**: **Bloquear** evita el acceso al área Actualización y seguridad de la aplicación Configuración en el dispositivo. **Sin configurar** (valor predeterminado) permite el acceso.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="display"></a>Pantalla

Estas opciones de configuración usan [display policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display) (CSP de directiva de pantalla), que también indica las ediciones de Windows compatibles.

El ajuste de escala de PPP de GDI permite a las aplicaciones sin reconocimiento de PPP lograr el reconocimiento de PPP por monitor.

- **Activar el ajuste de GDI para las aplicaciones**: **Agregar** las aplicaciones heredadas cuyo ajuste de escala de PPP de GDI quiera activar. Por ejemplo, escriba `filename.exe` o `%ProgramFiles%\Path\Filename.exe`.

  El ajuste de escala de PPP de GDI se activa para todas las aplicaciones heredadas de la lista.

- **Desactivar el ajuste de GDI para las aplicaciones**: **Agregar** las aplicaciones heredadas cuyo ajuste de escala de PPP de GDI quiera desactivar. Por ejemplo, escriba `filename.exe` o `%ProgramFiles%\Path\Filename.exe`.

  El ajuste de escala de PPP de GDI se desactiva para todas las aplicaciones heredadas de la lista.

También puede **Importar** un archivo .csv con la lista de aplicaciones.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="general"></a>General

Estas opciones de configuración usan [experience policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) (CSP de directiva de experiencia), que también indica las ediciones de Windows compatibles. 

- **Captura de pantalla** (solo móviles): **Bloquear** evita que los usuarios finales obtengan capturas de pantalla en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Copiar y pegar (solo móvil)** : **Bloquear** evita que los usuarios finales usen Copiar y Pegar entre aplicaciones en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Cancelación manual de la suscripción**: **Bloquear** evita que los usuarios finales eliminen la cuenta del área trabajo mediante el panel de control del área de trabajo en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.

  Esta configuración de directiva no se aplica si el equipo está unido a Azure AD y la inscripción automática está habilitada.

- **Instalación manual del certificado raíz** (solo móviles): **Bloquear** evita que los usuarios finales instalen manualmente certificados raíz y certificados CAP intermedios. **Sin configurar** (valor predeterminado) permite esta característica.
- **Cámara**: **Bloquear** evita que los usuarios finales usen la cámara en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Sincronización de archivos de OneDrive**: **Bloquear** evita que los usuarios finales sincronicen archivos en OneDrive desde el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Almacenamiento extraíble**: **Bloquear** evita que los usuarios finales usen dispositivos de almacenamiento externo, como tarjetas SD, con el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Geolocalización**: **Bloquear** evita que los usuarios finales activen servicios de ubicación en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Conexión compartida**: **Bloquear** evita el uso compartido de una conexión a Internet en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Restablecimiento del teléfono**: **Bloquear** evita que los usuarios finales borren o realicen un restablecimiento de fábrica en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Conexión USB**: **Bloquear** evita el acceso a dispositivos de almacenamiento externo mediante una conexión USB en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica. La carga USB no se ve afectada por esta opción.
- **Modo antirrobo** (solo móviles): **Bloquear** evita que los usuarios finales seleccionen la preferencia de modo Antirrobo en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Cortana**: **Bloquear** deshabilita el asistente de voz Cortana en el dispositivo. Si Cortana está desactivado, los usuarios pueden seguir buscando elementos en el dispositivo. **Sin configurar** (valor predeterminado) permite Cortana.
- **Grabación de voz** (solo móviles): **Bloquear** evita que los usuarios finales usen la grabadora de voz del dispositivo en este. **Sin configurar** (valor predeterminado) permite la grabación de voz para aplicaciones.
- **Modificación del nombre del dispositivo** (solo móvil): **Bloquear** evita que los usuarios finales cambien el nombre del dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Agregar paquetes de aprovisionamiento**: **Bloquear** evita que el agente de configuración en tiempo de ejecución instale paquetes de aprovisionamiento en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Quitar paquetes de aprovisionamiento**: **Bloquear** evita que el agente de configuración en tiempo de ejecución quite paquetes de aprovisionamiento del dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Detección de dispositivos**: **Bloquear** evita que otros dispositivos detecten un dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Cambio de tarea (solo móviles)** : **Bloquear** evita el cambio de tareas en el dispositivo. **Sin configurar** (valor predeterminado) permite esta característica.
- **Cuadro de diálogo de error de tarjeta SIM (sólo móviles)** : **Bloquear** la aparición de mensajes de error en el dispositivo si no se detecta ninguna tarjeta SIM. **Sin configurar** (valor predeterminado) muestra los mensajes de error.
- **Ink Workspace** (Área de trabajo de Ink): elija si el usuario tiene acceso al área de trabajo de Ink y cómo. Las opciones son:
  - **Sin configurar** (valor predeterminado): activa el área de trabajo de Ink y el usuario puede usarla por encima de la pantalla de bloqueo.
  - **Deshabilitada en la pantalla de bloqueo**: el área de trabajo de Ink está habilitada y la característica está activada. Pero el usuario no puede acceder a ella por encima de la pantalla de bloqueo.
  - **Deshabilitada**: el acceso al área de trabajo de Ink está deshabilitado. La característica está desactivada.

  [WindowsInkWorkspace policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) (CSP de directiva de WindowsInkWorkspace)

- **Reimplementación automática**: elija **Permitir** para que los usuarios con derechos administrativos puedan eliminar todos los datos y la configuración de usuario con **CTRL + Win + R** en la pantalla de bloqueo del dispositivo. El dispositivo se vuelve a configurar e inscribir automáticamente para la administración. **Sin configurar** (valor predeterminado) deshabilita esta característica.
- **Exigir que los usuarios se conecten a la red durante la configuración del dispositivo**: elija **Requerir** para que el dispositivo se conecte a una red antes de pasar de la página Red durante la configuración de Windows. **Sin configurar** (valor predeterminado) permite a los usuarios pasar de la página Red, aunque no estén conectados a una red.

  La configuración se hace efectiva la próxima vez que se borra o restablece el dispositivo. Al igual que cualquier otra configuración de Intune, el dispositivo debe estar inscrito y administrado por Intune para recibir la configuración. Pero, una vez que se ha inscrito y recibe las directivas, al restablecer el dispositivo se fuerza la configuración durante la siguiente configuración de Windows.

- **Acceso directo a memoria**: **Bloquear** impide el acceso directo a memoria (DMA) a todos los puertos de bajada PCI de conexión instantánea hasta que un usuario inicia sesión en Windows. **Habilitado** (valor predeterminado) permite el acceso a DMA, incluso cuando un usuario no ha iniciado sesión.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Finalizar procesos desde el Administrador de tareas**: esta configuración determina si los usuarios que no son administradores pueden usar el Administrador de tareas para finalizar tareas. Si selecciona **Bloquear**, se impide que los usuarios estándar (no administradores) usen el Administrador de tareas para finalizar un proceso o una tarea en el dispositivo. Si selecciona **Sin configurar** (valor predeterminado), se permite que los usuarios estándar finalicen un proceso o una tarea mediante el Administrador de tareas.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="locked-screen-experience"></a>Experiencia de pantalla bloqueada

- **Notificaciones del centro de actividades (solo móviles)** : **Bloquear** evita que las notificaciones del centro de actividades aparezcan en la pantalla de bloqueo del dispositivo. **Sin configurar** (valor predeterminado) permite a los usuarios elegir qué aplicaciones muestran notificaciones en la pantalla de bloqueo.

  [AboveLock/AllowActionCenterNotifications CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowactioncenternotifications) (CSP de AboveLock/AllowActionCenterNotifications)

- **URL de imagen de pantalla de bloqueo (solo equipos de escritorio)** : escriba la dirección URL de una imagen en formato JPG, JPEG o PNG que se use como fondo de la pantalla de bloqueo de Windows. Por ejemplo, escriba `https://contoso.com/image.png`. Esta opción bloquea la imagen y no se puede cambiar posteriormente.
- **Tiempo de espera de la pantalla configurable por el usuario (solo dispositivos móviles)** : **Permitir** permite a los usuarios configurar el tiempo de espera de la pantalla. **Sin configurar** (valor predeterminado) no da a los usuarios esta opción.

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowscreentimeoutwhilelockeduserconfig) (CSP de DeviceLock/AllowScreenTimeoutWhileLockedUserConfig)

- **Cortana en pantalla bloqueada (solo escritorio)** : **Bloquear** evita que los usuarios interactúen con Cortana cuando el dispositivo está en la pantalla de bloqueo. **Sin configurar** (valor predeterminado) permite la interacción con Cortana.

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock) (CSP de AboveLock/AllowCortanaAboveLock)

- **Notificaciones del sistema en pantalla bloqueada**: **Bloquear** evita que las notificaciones del sistema aparezcan en la pantalla de bloqueo del dispositivo. **Sin configurar** (valor predeterminado) permite estas notificaciones.

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts) (CSP de AboveLock/AllowToasts)

- **Tiempo de espera de la pantalla (solo dispositivos móviles)** : establezca la duración (en segundos) desde que se bloquea la pantalla hasta que se apaga. Los valores admitidos son de 11 a 1800. Por ejemplo, escriba `300` para establecer este tiempo de espera en 5 minutos.

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-screentimeoutwhilelocked) (CSP de DeviceLock/ScreenTimeoutWhileLocked)

Haga clic en **Aceptar** para guardar los cambios.

## <a name="messaging"></a>Mensajería

Estas opciones de configuración usan [messaging policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging) (CSP de directiva de mensajería), que también indica las ediciones de Windows compatibles.

- **Sincronización de mensajes (solo móvil)** : **Bloquear** deshabilita la copia de seguridad y la restauración de los mensajes de texto, así como la sincronización de mensajes entre dispositivos Windows. La deshabilitación ayuda a evitar que la información se almacene en servidores fuera del control de la organización. **Sin configurar** (valor predeterminado) permite a los usuarios cambiar esta opción y sincronizar sus mensajes.
- **MMS (solo móvil)** : **Bloquear** deshabilita la funcionalidad de envío y recepción de MMS en el dispositivo. En las empresas, use esta directiva para deshabilitar MMS en los dispositivos como parte del requisito de auditoría o administración. **Sin configurar** (valor predeterminado) permite el envío y recepción de MMS.
- **RCS (solo móvil)** : **Bloquear** deshabilita la funcionalidad de envío y recepción de Rich Communication Services (RCS) en el dispositivo. En las empresas, use esta directiva para deshabilitar RCS en los dispositivos como parte del requisito de auditoría o administración. **Sin configurar** (valor predeterminado) permite el envío y recepción de RCS.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="microsoft-edge-browser"></a>Explorador Microsoft Edge

Estas opciones de configuración usan [browser policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) (CSP de directiva de explorador), que también indica las ediciones de Windows compatibles.

### <a name="use-microsoft-edge-kiosk-mode"></a>Usar el modo de pantalla completa de Microsoft Edge

Las opciones de configuración disponibles cambian en función de lo que elija. Las opciones son:

- **No** (valor predeterminado): Microsoft Edge no se ejecuta en pantalla completa. Toda la configuración de Microsoft Edge está disponible y puede cambiarla y configurarla.
- **Señal digital o interactiva (pantalla completa con una sola aplicación)** : filtra la configuración de Microsoft Edge que se aplica a la pantalla completa de Microsoft Edge de señal digital o interactiva para que solo se use en pantallas completas con una sola aplicación de Windows 10. Elija esta configuración para abrir una URL en pantalla completa y mostrar solo el contenido de ese sitio web. En [Configurar señales digitales](https://docs.microsoft.com/windows/configuration/setup-digital-signage) se proporciona más información sobre esta característica.
- **Exploración pública InPrivate (pantalla completa con una sola aplicación)** : filtra la configuración de Microsoft Edge que se aplica a la pantalla completa de Microsoft Edge de exploración pública InPrivate para que se use en pantallas completas con una sola aplicación de Windows 10. Se ejecuta una versión de varias pestañas de Microsoft Edge.
- **Modo normal (pantalla completa con varias aplicaciones)** : filtra la configuración de Microsoft Edge que se aplica a la pantalla completa normal de Microsoft Edge. Se ejecuta una versión completa de Microsoft Edge con todas las características de exploración.
- **Exploración pública (pantalla completa con varias aplicaciones)** : filtra la configuración de Microsoft Edge que se aplica a la exploración pública en una pantalla completa con varias aplicaciones de Windows 10.  Se ejecuta una versión de varias pestañas de Microsoft Edge InPrivate.

> [!TIP]
> Para obtener más información sobre qué hacen estas opciones, consulte [Tipos de configuración del modo de pantalla completa de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Este perfil de restricciones de dispositivos está directamente relacionado con el perfil de pantalla completa que se crea mediante la [configuración de pantalla completa de Windows](kiosk-settings-windows.md). En resumen:

1. Cree el perfil de [configuración de pantalla completa de Windows](kiosk-settings-windows.md) para ejecutar el dispositivo en pantalla completa. Seleccione Microsoft Edge como la aplicación y establezca Pantalla completa de Microsoft Edge en el perfil de pantalla completa.
2. Cree el perfil de restricciones de dispositivos que se describe en este artículo y configure opciones y características específicas que se permiten en Microsoft Edge. Asegúrese de elegir el mismo tipo de pantalla completa de Microsoft Edge que el que ha seleccionado en el perfil de pantalla completa ([configuración de pantalla completa de Windows](kiosk-settings-windows.md)). 

    [Configuración de la pantalla completa admitida](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) es un excelente recurso.

> [!IMPORTANT] 
> Asegúrese de asignar este perfil de Microsoft Edge a los mismos dispositivos que su perfil de pantalla completa ([configuración de pantalla completa de Windows](kiosk-settings-windows.md)).

[CSP ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Inicio de la experiencia

- **Iniciar Microsoft Edge con**: elija qué páginas se abren cuando se inicia Microsoft Edge. Las opciones son:
  - **Páginas de inicio personalizadas**: escriba las páginas de inicio, como `http://www.contoso.com`. Microsoft Edge carga las páginas de inicio que se escriben.
  - **Página Nueva pestaña**: Microsoft Edge carga todo lo que se escribe en la opción **Dirección URL de nueva pestaña**.
  - **Página de última sesión**: Microsoft Edge carga la página de la última sesión.
  - **Páginas de inicio en la configuración de la aplicación local**: Microsoft Edge empieza con la página de inicio predeterminada que define el sistema operativo.

- **Permitir al usuario cambiar las páginas de inicio**: **Sí** (valor predeterminado) permite a los usuarios cambiar las páginas de inicio. Los administradores pueden usar `EdgeHomepageUrls` para escribir las páginas de inicio que los usuarios ven de manera predeterminada al abrir Microsoft Edge. **No** evita que los usuarios cambien las páginas de inicio.
- **Permitir contenido web en una página de nueva pestaña**: si se establece en **Sí** (valor predeterminado), Microsoft Edge abre la dirección URL especificada en la opción **Dirección URL de nueva pestaña**. Si la opción **Dirección URL de nueva pestaña** está en blanco, Microsoft Edge abre la página de nueva pestaña que aparece en la configuración de Microsoft Edge. Los usuarios pueden cambiarla. Si se establece en **No**, Microsoft Edge abre una nueva pestaña con una página en blanco. Los usuarios no pueden cambiarla.
- **Dirección URL de nueva pestaña**: escriba la dirección URL que se va a abrir en la página Nueva pestaña. Por ejemplo, escriba `https://www.bing.com` o `https://www.contoso.com`.

- **Botón Inicio**: elija lo que sucede al seleccionar el botón Inicio. Las opciones son:
  - **Páginas de inicio**: se abre la opción elegida en **Iniciar Microsoft Edge con**.
  - **Página Nueva pestaña**: abre la dirección URL especificada en la opción **Dirección URL de nueva pestaña**.
  - **Dirección URL del botón de inicio**: escriba la dirección URL que se va a abrir. Por ejemplo, escriba `https://www.bing.com` o `https://www.contoso.com`.
  - **Hide Home button** (Ocultar el botón Inicio): oculta el botón Inicio
- **Permitir a los usuarios cambiar el botón Inicio**: **Sí** permite a los usuarios cambiar el botón Inicio. Los cambios del usuario reemplazan cualquier configuración del administrador en el botón Inicio. **No** (valor predeterminado) evita que los usuarios cambien la forma en que el administrador ha configurado el botón Inicio.
- **Mostrar la página Primera experiencia de ejecución (solo móvil)** : **Sí** (valor predeterminado) muestra la página de introducción del primer uso en Microsoft Edge. **No** evita que la página de introducción aparezca la primera vez que se ejecuta Microsoft Edge. Esta característica permite que las empresas (por ejemplo, aquellas organizaciones que usan configuraciones de cero emisiones) bloqueen esta página.
- **Ubicación de la lista de URL de Primera experiencia de ejecución** (solo Windows 10 Mobile): escriba la dirección URL que dirige al archivo XML que contiene las direcciones URL de página de primera ejecución. Por ejemplo, escriba `https://www.contoso.com/sites.xml`.

- **Actualizar el explorador después del tiempo de inactividad**: escriba el número de minutos de inactividad hasta que se actualiza el explorador, de 0 a 1440 minutos. El valor predeterminado es `5` minutos. Cuando se establece en `0` (cero), el explorador no se actualiza tras estar inactivo.

  Esta configuración solo está disponible cuando se ejecuta en [Exploración pública InPrivate (pantalla completa con una sola aplicación)](#use-microsoft-edge-kiosk-mode).

- **Permitir elementos emergentes** (solo equipos de escritorio): **Sí** (valor predeterminado) permite elementos emergentes en el explorador web. **No** evita las ventanas emergentes en el explorador.
- **Enviar el tráfico de la intranet a Internet Explorer**  (solo equipos de escritorio): **Sí** permite que los usuarios abran sitios web de intranet en Internet Explorer en lugar de Microsoft Edge. Esta opción es para la compatibilidad con versiones anteriores. **No** (valor predeterminado) permite que los usuarios usen Microsoft Edge.
- **Ubicación de la lista de sitios del modo de empresa** (solo escritorio): escriba la dirección URL que dirige al archivo XML que contiene una lista de los sitios web que se abren en el modo de empresa. Los usuarios no pueden cambiar esta lista. Por ejemplo, escriba `https://www.contoso.com/sites.xml`.
- **Message when opening sites in Internet Explorer** (Mensaje al abrir sitios en Internet Explorer): use este valor para configurar Microsoft Edge para que muestre una notificación antes de que un sitio se abra en Internet Explorer 11. Las opciones son:
  - **No volver a mostrar este mensaje**: se usa el comportamiento predeterminado del sistema operativo, que puede no mostrar un mensaje.
  - **Mostrar mensaje de que el sitio está abierto en Internet Explorer 11**: muestra el mensaje cuando se abren sitios en IE. Los sitios se abren en IE. 
  - **Mostrar el mensaje con la opción para abrir sitios en Microsoft Edge**: muestra el mensaje al abrir sitios en Edge. El mensaje incluye un vínculo **Keep going in Microsoft Edge** (Seguir en Microsoft Edge) para que los usuarios puedan elegir Microsoft Edge en lugar de IE.

  > [!IMPORTANT]
  > Este valor exige usar la opción **Ubicación de la lista de sitios del modo de empresa**, **Enviar el tráfico de la intranet a Internet Explorer** o ambas.

- **Permitir lista de compatibilidad de Microsoft**: **Sí** (valor predeterminado) permite usar una lista de compatibilidad de Microsoft. **No** evita la lista de compatibilidad de Microsoft en Microsoft Edge. La lista de Microsoft ayuda a que Microsoft Edge muestre de manera correcta sitios con problemas de compatibilidad conocidos.
- **Precarga de páginas de inicio y página Nueva pestaña**: **Sí** (valor predeterminado) usa el comportamiento predeterminado del sistema operativo, que puede ser cargar previamente estas páginas. La carga previa minimiza el tiempo de inicio de Microsoft Edge y carga nuevas pestañas. **No** evita que Microsoft Edge cargue previamente las páginas de inicio y la página Nueva pestaña.
- **Inicio previo de páginas de inicio y página Nueva pestaña**: **Sí** (valor predeterminado) usa el comportamiento predeterminado del sistema operativo, que puede ser iniciar previamente estas páginas. El inicio previo ayuda al rendimiento de Microsoft Edge y minimiza el tiempo necesario para iniciar Microsoft Edge. **No** evita que Microsoft Edge inicie previamente las páginas de inicio y la página Nueva pestaña.

Haga clic en **Aceptar** para guardar los cambios.

### <a name="favorites-and-search"></a>Favoritos y búsqueda

- **Mostrar barra de favoritos**: elija lo que sucede con la barra de favoritos en cualquier página de Microsoft Edge. Las opciones son:
  - **En el inicio y páginas de nueva pestaña**: muestra la barra de favoritos cuando se inicia Microsoft Edge y en todas las páginas de pestaña. Los usuarios finales pueden cambiar esta opción.
  - **En todas las páginas**: muestra la barra de favoritos en todas las páginas. Los usuarios no pueden cambiar esta opción.
  - **Oculto**: oculta la barra de favoritos en todas las páginas. Los usuarios no pueden cambiar esta opción.
- **Permitir cambios en favoritos**: **Sí** (valor predeterminado) usa el valor predeterminado del sistema operativo, lo que permite a los usuarios cambiar la lista. **No** evita que los usuarios finales agreguen, importen, ordenen o modifiquen la lista de favoritos.
  - **Lista de favoritos**: agrega una lista de las direcciones URL al archivo de favoritos. Por ejemplo, agregue `http://contoso.com/favorites.html`.
- **Sincronizar favoritos entre exploradores de Microsoft** (solo escritorio): **Sí** obliga a Windows a sincronizar los favoritos entre Internet Explorer y Microsoft Edge. Las incorporaciones, eliminaciones, modificaciones y cambios de orden en los favoritos se comparten entre los distintos exploradores.  **No** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede dar a los usuarios la opción de sincronizar los favoritos entre los exploradores.
- **Motor de búsqueda predeterminado**: elija el motor de búsqueda predeterminado del dispositivo. Los usuarios finales pueden cambiar este valor en cualquier momento. Las opciones son:
  - Motor de búsqueda de la configuración del cliente de Microsoft Edge
  - Bing
  - Google
  - Yahoo
  - Valor personalizado: en **URL de archivo XML OpenSearch**, escriba una dirección URL HTTPS con el archivo XML que incluye el nombre corto y la dirección URL del motor de búsqueda, como mínimo. Por ejemplo, escriba `https://www.contoso.com/opensearch.xml`.
- **Mostrar sugerencias de búsqueda**: **Sí** (valor predeterminado) permite que el motor de búsqueda sugiera sitios a medida que escribe frases de búsqueda en la barra de direcciones. **No** evita esta característica.
- **Permitir cambios en el motor de búsqueda**: **Sí** (valor predeterminado) permite que los usuarios agreguen nuevos motores de búsqueda o cambien el motor de búsqueda predeterminado en Microsoft Edge. Elija **No** para impedir que los usuarios personalicen el motor de búsqueda.

  Esta configuración solo está disponible cuando se ejecuta en [Modo normal (pantalla completa con varias aplicaciones)](#use-microsoft-edge-kiosk-mode).

Haga clic en **Aceptar** para guardar los cambios.

### <a name="privacy-and-security"></a>Privacidad y seguridad

- **Permitir exploración de InPrivate**: **Sí** (valor predeterminado) permite la exploración de InPrivate en Microsoft Edge. Después de cerrar todas las pestañas de InPrivate, Microsoft Edge elimina los datos de exploración del dispositivo. **No** evita que los usuarios finales abran sesiones de exploración de InPrivate.
- **Guardar historial de exploración**: **Sí** (valor predeterminado) permite guardar el historial de exploración en Microsoft Edge. **No** evita guardar el historial de exploración.
- **Borrar datos de navegación al salir** (solo escritorio): **Sí** borra el historial y los datos de exploración cuando el usuario sale de Microsoft Edge. **No** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede almacenar en caché los datos de exploración.
- **Sync browser settings between user's devices** (Sincronizar la configuración del explorador entre los dispositivos del usuario): elija cómo quiere sincronizar la configuración del explorador entre los dispositivos. Las opciones son:
  - **Permitir**: permita la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario
  - **Block and enable user override** (Bloquear y habilitar el reemplazo de usuario): bloquee la sincronización de la configuración del explorador de Microsoft Edge entre los dispositivos del usuario. Los usuarios pueden reemplazar esta configuración.
  - **Bloquear**: bloquea la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario. Los usuarios no pueden reemplazar esta configuración.

Si "Bloquear y habilitar el reemplazo de usuarios" está seleccionado, el usuario puede invalidar la designación de administrador.

- **Permitir administrador de contraseñas**: **Sí** (valor predeterminado) permite que Microsoft Edge use automáticamente el administrador de contraseñas, lo que permite a los usuarios guardar y administrar contraseñas en el dispositivo. **No** evita que Microsoft Edge use el administrador de contraseñas.
- **Cookies**: elija cómo se administran las cookies en el dispositivo. Las opciones son:
  - **Permitir**: las cookies se almacenan en el dispositivo.
  - **Bloquear todas las cookies**: las cookies no se almacenan en el dispositivo.
  - **Bloquear solo cookies de terceros**: las cookies de terceros o de asociados no se almacenan en el dispositivo.
- **Permitir autorrelleno en los formularios**: **Sí** (valor predeterminado) permite a los usuarios cambiar la configuración de Autocompletar del explorador y rellenar automáticamente los campos de formulario. **No** deshabilita la característica Autorrelleno en Microsoft Edge.
- **Enviar encabezados de no seguimiento**: **Sí** envía encabezados de no seguimiento a los sitios web que solicitan información de seguimiento (recomendado). **No** (valor predeterminado) no envía encabezados, lo que permite a los sitios web realizar un seguimiento del usuario. El usuario puede configurar.
- **Mostrar dirección IP de localhost para WebRTC**: **Sí** (valor predeterminado) permite que la dirección IP de localhost de los usuarios se muestre cuando se hacen llamadas telefónicas a través de este protocolo. **No** evita que la dirección IP de localhost de los usuarios se muestre. 
- **Permitir recopilación de datos para iconos dinámicos**: **Sí** (valor predeterminado) permite que Microsoft Edge recopile información de los iconos dinámicos anclados al menú Inicio. **No** evita la recopilación de esta información, lo que puede limitar la experiencia de los usuarios.
- **User can override certificate errors** (El usuario puede invalidar los errores de certificado): **Sí** (valor predeterminado) permite a los usuarios acceder a sitios web que tienen errores de Capa de sockets seguros (SSL) o Seguridad de la capa de transporte (TLS). **No** (recomendado para una mayor seguridad) evita que los usuarios accedan a sitios web con errores de SSL o TLS.

Haga clic en **Aceptar** para guardar los cambios.

### <a name="additional"></a>Adicional

- **Permitir el explorador de Microsoft Edge** (solo Mobile): **Sí** (valor predeterminado) permite el uso del explorador web Microsoft Edge en el dispositivo móvil. **No** evita el uso de Microsoft Edge en el dispositivo. Si elige **No**, la demás configuración individual solo se aplica a los equipos de escritorio.
- **Permitir la lista desplegable de la barra de direcciones**: **Sí** (valor predeterminado) permite que Microsoft Edge despliegue la barra de direcciones con una lista de sugerencias. **No** evita que Microsoft Edge muestre una lista de sugerencias desplegable cuando se escribe. Cuando se establece en **No**, puede:
  - Ayudar a minimizar el ancho de banda de red entre Microsoft Edge y los servicios de Microsoft.
  - Deshabilitar **Mostrar sugerencias de búsqueda y sitios al escribir** en Microsoft Edge > Configuración.
- **Permitir modo de pantalla completa**: **Sí** (valor predeterminado) permite que Microsoft Edge use el modo de pantalla completa, que muestra solo el contenido web y oculta la interfaz de usuario de Microsoft Edge. **No** evita el modo de pantalla completa en Microsoft Edge.
- **Permitir la página about flags**: **Sí** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede permitir el acceso a la página `about:flags`. La página `about:flags` permite a los usuarios cambiar la configuración de desarrollador y habilitar características experimentales. **No** evita que los usuarios finales accedan a la página `about:flags` en Microsoft Edge.
- **Permitir herramientas de desarrollo**: **Sí** (valor predeterminado) permite a los usuarios usar las herramientas de desarrollo F12 para compilar y depurar páginas web de forma predeterminada. **No** evita que los usuarios finales usen las herramientas de desarrollo F12.
- **Permitir JavaScript**: **Sí** (valor predeterminado) permite la ejecución de scripts, como JavaScript, en el explorador Microsoft Edge. **No** evita la ejecución de scripts de Java en el explorador.
- **El usuario puede instalar extensiones**: **Sí** (valor predeterminado) permite que los usuarios finales instalen extensiones de Microsoft Edge en el dispositivo. **No** evita la instalación.
- **Permitir la instalación de prueba de extensiones de desarrollador**: **Sí** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede permitir la transferencia local. La transferencia local instala y ejecuta extensiones sin comprobar. **No** evita que Microsoft Edge transfiera localmente mediante la característica **Cargar extensiones**. No evita la transferencia local de extensiones de otras maneras, como PowerShell.
- **Required extensions** (Extensiones necesarias): elija cuáles son las extensiones que los usuarios finales de Microsoft Edge no pueden desactivar. Escriba los nombres de familia de paquete y seleccione **Agregar**. [Buscar un nombre de familia de paquete (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) brinda alguna orientación.

  También puede **Importar** un archivo .csv que incluya los nombres de familia de paquete. O bien puede **Exportar** los nombres de familia de paquete que especifique.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="network-proxy"></a>Proxy de red

Estas opciones de configuración usan [NetworkProxy policy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp) (CSP de directiva de NetworkProxy), que también indica las ediciones de Windows compatibles.

- **Detectar automáticamente configuración de proxy**: **Bloquear** evita que el dispositivo detecte automáticamente un script de configuración automática de proxy (PAC). **Sin configurar** (valor predeterminado) habilita esta característica. cuando esta opción está habilitada, el dispositivo intenta encontrar la ruta de acceso a un script de configuración automática del proxy.
- **Usar script de proxy**: seleccione **Permitir** para especificar una ruta de acceso al script de PAC para configurar el servidor proxy. **Sin configurar** (valor predeterminado) no permite especificar la dirección URL de un script de PAC.
  - **URL del script de configuración**: escriba la dirección URL de un script de configuración automática que desee usar para configurar el servidor proxy.
- **Usar un servidor proxy manual**: seleccione **Permitir** para escribir manualmente el nombre o la dirección IP y el número de puerto TCP de un servidor proxy. **Sin configurar** (valor predeterminado) no permite escribir manualmente detalles de un servidor proxy.
  - **Dirección**: escriba el nombre o la dirección IP del servidor proxy.
  - **Número de puerto**: escriba el número de puerto del servidor proxy.
  - **Excepciones de proxy**: escriba las direcciones URL que no deben usar el servidor proxy. Use un punto y coma para separar cada elemento.
  - **Omitir el servidor proxy para direcciones locales**: **Sin configurar** (valor predeterminado) evita usar un servidor proxy para direcciones locales en la intranet. **Permitir** usa un servidor proxy para direcciones locales.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="password"></a>Contraseña

Estas opciones de configuración usan [DeviceLock policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) (CSP de directiva de DeviceLock), que también indica las ediciones de Windows compatibles.

- **Contraseña**: **Requerir** que el usuario final escriba una contraseña para acceder al dispositivo. **Sin configurar** (valor predeterminado) permite el acceso al dispositivo sin contraseña. Solo se aplica a las cuentas locales. Las contraseñas de las cuentas de dominio permanecen configuradas por Active Directory (AD) y Azure AD.

  - **Tipo de contraseña requerida**: elija el tipo de contraseña. Las opciones son:
    - **Sin configurar**: la contraseña puede incluir números y letras.
    - **Numérica**: la contraseña solo debe contener números.
    - **Alfanumérica**: la contraseña debe ser una combinación de letras y números.
  - **Longitud mínima de la contraseña**: escriba el número mínimo de caracteres o los caracteres requeridos, de 4 a 16. Por ejemplo, escriba `6` para exigir al menos seis caracteres de longitud de la contraseña.
  
    > [!IMPORTANT]
    > Cuando el requisito de contraseña se cambia a un escritorio de Windows, los usuarios se ven afectados la próxima vez que inician sesión, porque es entonces cuando el dispositivo pasa de inactivo a activo. Los usuarios con contraseñas que cumplan el requisito de todos modos tendrán que cambiarlas.
    
  - **Número de errores de inicio de sesión antes de borrar el dispositivo**: escriba el número de errores de autenticación permitido antes de que se borre el dispositivo, hasta 11. El número válido que escriba dependerá de la edición. [DeviceLock/MAXDEVICEPASSWORDFAILEDATTEMPTS CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) enumera los valores admitidos. `0` (cero) puede deshabilitar la funcionalidad de borrado del dispositivo.

    Esta opción también tiene un impacto diferente en función de la edición. Para obtener información detallada de esta configuración, vea [DeviceLock/MaxDevicePasswordFailedAttempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) (CSP de DeviceLock/MaxDevicePasswordFailedAttempts).

  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el periodo de tiempo que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.
  - **Caducidad de la contraseña (días)** : especifique el periodo de tiempo en días tras el cual debe cambiarse la contraseña del dispositivo, de 1 a 365. Por ejemplo, escriba `90` para que la contraseña caduque pasados 90 días.
  - **Impedir la reutilización de contraseñas anteriores**: especifique el número de contraseñas usadas anteriormente que no se pueden emplear, de 1 a 24. Por ejemplo, escriba `5` para que los usuarios no puedan establecer una nueva contraseña en su contraseña actual o en cualquiera de sus cuatro contraseñas anteriores.
  - **Requerir contraseña cuando el dispositivo vuelve de un estado de inactividad** (Mobile y Holographic): seleccione **Requerir** para que los usuarios deban escribir una contraseña para desbloquear el dispositivo después de estar inactivo. **Sin configurar** (valor predeterminado) no requiere un PIN o una contraseña cuando el dispositivo se reanuda desde un estado de inactividad.
  - **Contraseñas sencillas**: establezca en **Bloquear** para que los usuarios no puedan crear contraseñas sencillas, como `1234` o `1111`. Establezca en **Sin configurar** (valor predeterminado) para permitir a los usuarios crear contraseñas como `1234` o `1111`. Esta configuración también permite o bloquea el uso de contraseñas de imagen de Windows.
- **Cifrado automático durante AADJ**: **Bloquear** impide el cifrado automático de dispositivos de BitLocker cuando el dispositivo está preparado para el primer uso y está unido a Azure AD. **No configurado** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede habilitar el cifrado. Más información sobre el [cifrado de dispositivos de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [CSP Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Directiva del Estándar federal de procesamiento de información (FIPS)** : **Permitir** usa la directiva del Estándar federal de procesamiento de información (FIPS), que es un estándar del gobierno de Estados Unidos para el cifrado, las operaciones hash y la firma. **No configurado** (valor predeterminado) usa el valor predeterminado del sistema operativo, que no utiliza FIPS.

  [CSP Cryptography/AllowFipsAlgorithmPolicy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Autenticación de dispositivos con Windows Hello**: **Permitir** que los usuarios utilicen un dispositivo complementario Windows Hello, como un teléfono, una pulsera de actividad o un dispositivo IoT, para iniciar sesión en un equipo Windows 10. **No configurado** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede impedir que los dispositivos complementarios Windows Hello se autentiquen con Windows.

  [CSP Authentication/AllowSecondaryAuthenticationDevice](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Inicio de sesión web**: habilita la compatibilidad del inicio de sesión de Windows con proveedores federados que no sean de AD FS (Servicios de federación de Active Directory), como el Lenguaje de marcado de aserción de seguridad (SAML). SAML usa tokens seguros que proporcionan a los exploradores web una experiencia de inicio de sesión único (SSO). Las opciones son:

  - **No configurado** (valor predeterminado) usa el valor predeterminado del sistema operativo en el dispositivo.
  - **Habilitado**: el proveedor de credenciales web está habilitado para el inicio de sesión.
  - **Deshabilitado**: el proveedor de credenciales web está deshabilitado para el inicio de sesión.

  [CSP Authentication/EnableWebSignIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Dominio de inquilino de Azure AD preferido**: escriba un nombre de dominio existente en su organización de Azure AD. Cuando los usuarios de este dominio inicien sesión, no tendrán que escribir el nombre de dominio. Por ejemplo, escriba `contoso.com`. Los usuarios del dominio `contoso.com` pueden iniciar sesión con su nombre de usuario, como `abby`, en lugar de `abby@contoso.com`.

  [CSP Authentication/PreferredAadTenantDomainName](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

Haga clic en **Aceptar** para guardar los cambios.

## <a name="per-app-privacy-exceptions"></a>Excepciones de privacidad para cada aplicación

Puede agregar aplicaciones que deben tener un comportamiento de privacidad diferente del definido en "Privacidad determinada".

- **Nombre del paquete**: nombre de la familia del paquete de aplicaciones.
- **Nombre de la aplicación**: el nombre de la aplicación.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: define si esta aplicación puede tener acceso al nombre de usuario, las imágenes u otra información de contacto.
- **Aplicaciones en segundo plano**: define si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: define si esta aplicación puede tener acceso al calendario.
- **Historial de llamadas**: define si esta aplicación puede tener acceso al historial de llamadas.
- **Cámara**: define si esta aplicación puede tener acceso a la cámara.
- **Contactos**: define si esta aplicación puede tener acceso a los contactos.
- **Correo electrónico**: define si esta aplicación puede tener acceso al correo electrónico.
- **Ubicación**: define si esta aplicación puede tener acceso a información de ubicación.
- **Mensajería**: define si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: define si esta aplicación puede usar el micrófono.
- **Movimiento**: define si esta aplicación puede tener acceso a información de movimiento.
- **Notificaciones**: define si esta aplicación puede tener acceso a las notificaciones.
- **Teléfono**: define si esta aplicación puede tener acceso al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: define si esta aplicación puede tener acceso a las tareas.
- **Dispositivos de confianza**: elija si esta aplicación puede usar dispositivos de confianza. Es decir, hardware ya conectado o que se proporciona con el dispositivo. Por ejemplo, use televisores, proyectores, etc. como dispositivos de confianza.
- **Comentarios y diagnóstico**: define si esta aplicación puede tener acceso a la información de diagnóstico.
- **Sincronización con dispositivos**: defina si esta aplicación puede compartir y sincronizar automáticamente información con dispositivos inalámbricos que no se emparejan explícitamente con el dispositivo.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="personalization"></a>Personalization

Estas opciones de configuración usan [personalization policy CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp) (CSP de directiva de personalización), que también indica las ediciones de Windows compatibles.

- **URL de imagen de fondo de escritorio (solo equipos de escritorio)** : indique la dirección URL de una imagen en formato .jpg, .jpeg o .png que quiera usar como fondo de escritorio de Windows. Los usuarios no pueden cambiar la imagen. Por ejemplo, escriba `https://contoso.com/logo.png`.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="printer"></a>Impresora

- **Impresoras**: lista de impresoras locales que se han agregado.
- **Impresora predeterminada**: establezca la impresora predeterminada.
- **Acceso de usuario para agregar nuevas impresoras**: permita o bloquee el uso de las impresoras locales.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="privacy"></a>Privacidad

Estas opciones de configuración usan [privacy policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy) (CSP de directiva de privacidad), que también indica las ediciones de Windows compatibles.

- **Personalización de entrada**: **Bloquear** evita el uso de voz para dictado y que se hable a Cortana y otras aplicaciones que usan el reconocimiento de voz basado en la nube de Microsoft. Está deshabilitado y los usuarios no pueden habilitar el reconocimiento de voz en línea mediante la configuración. **Sin configurar** (valor predeterminado) permite a los usuarios elegir. Si permite estos servicios, Microsoft puede recopilar datos de voz para mejorar el servicio.
- **Aceptación automática de los mensajes de consentimiento del usuario sobre emparejamiento y privacidad**: seleccione **Permitir** para que Windows pueda aceptar automáticamente los mensajes de consentimiento sobre emparejamiento y privacidad al ejecutar aplicaciones. **Sin configurar** (valor predeterminado) evita la aceptación automática de la ventana de consentimiento del usuario sobre emparejamiento y privacidad al abrir aplicaciones.
- **Publicar las actividades del usuario**: **Bloquear** evita las experiencias compartidas y la detección de recursos usados recientemente en la fuente de actividades. **Sin configurar** (valor predeterminado) habilita esta característica para que las aplicaciones puedan publicar las actividades del usuario final.
- **Solo actividades locales**: **Bloquear** evita experiencias compartidas y la detección de recursos usados recientemente en el selector de tareas según la actividad local únicamente. **Sin configurar** (valor predeterminado) habilita esta característica.

Puede configurar la información a la que pueden tener acceso todas las aplicaciones del dispositivo. También, puede definir excepciones para cada aplicación mediante **excepciones de privacidad de cada aplicación**.

Haga clic en **Aceptar** para guardar los cambios.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: define si esta aplicación puede tener acceso al nombre de usuario, las imágenes u otra información de contacto.
- **Aplicaciones en segundo plano**: define si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: define si esta aplicación puede tener acceso al calendario.
- **Historial de llamadas**: define si esta aplicación puede tener acceso al historial de llamadas.
- **Cámara**: define si esta aplicación puede tener acceso a la cámara.
- **Contactos**: define si esta aplicación puede tener acceso a los contactos.
- **Correo electrónico**: define si esta aplicación puede tener acceso al correo electrónico.
- **Ubicación**: define si esta aplicación puede tener acceso a información de ubicación.
- **Mensajería**: define si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: define si esta aplicación puede usar el micrófono.
- **Movimiento**: define si esta aplicación puede tener acceso a información de movimiento.
- **Notificaciones**: define si esta aplicación puede tener acceso a las notificaciones.
- **Teléfono**: define si esta aplicación puede tener acceso al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: define si esta aplicación puede tener acceso a las tareas.
- **Dispositivos de confianza**: elija si esta aplicación puede usar dispositivos de confianza. Es decir, hardware ya conectado o que se proporciona con el dispositivo. Por ejemplo, use televisores, proyectores, etc. como dispositivos de confianza.
- **Comentarios y diagnóstico**: elija si esta aplicación puede tener acceso a la información de diagnóstico.
- **Sincronización con dispositivos**: define si esta aplicación puede compartir y sincronizar información automáticamente con dispositivos inalámbricos que no se emparejan explícitamente con este PC, tableta o teléfono.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="projection"></a>Proyección

Estas opciones de configuración usan [WirelessDisplay policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay) (CSP de directiva de WirelessDisplay), que también indica las ediciones de Windows compatibles.

- **Entrada de usuario desde receptores de pantalla inalámbricos**: **Bloquear** evita la entrada de usuario desde receptores de pantalla inalámbricos. **Sin configurar** (valor predeterminado) permite que una pantalla inalámbrica envíe entrada de teclado, mouse, lápiz y táctil de vuelta al dispositivo de origen.
- **Proyección en este equipo**: **Bloquear** evita que otros dispositivos encuentren el equipo para proyección. **Sin configurar** (valor predeterminado) permite que el dispositivo sea detectable y que se pueda proyectar a él por encima de la pantalla de bloqueo.
- **Requerir PIN para emparejamiento**: seleccione **Requerir** para solicitar siempre un PIN cuando se conecte a un dispositivo de proyección. **Sin configurar** (valor predeterminado) no requiere un PIN para emparejar el dispositivo con un dispositivo de proyección.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="reporting-and-telemetry"></a>Informes y telemetría

- **Compartir datos de uso**: elija el nivel de datos de diagnóstico que se envía. Las opciones son:
  - **Sin configurar**: no se comparte ningún dato.
  - **Seguridad**: información necesaria para ayudar a proteger Windows, incluidos datos sobre la configuración del componente Experiencia del usuario y telemetría asociadas, la Herramienta de eliminación de software malintencionado y Windows Defender.
  - **Básica**: información básica del dispositivo que incluye datos relacionados con la calidad, la compatibilidad de aplicaciones, datos de uso de aplicaciones y datos del nivel de seguridad.
  - **Mejorada**: información adicional que incluye: cómo se usan Windows, Windows Server, System Center y las aplicaciones, cómo funcionan, datos avanzados de confiabilidad y datos de los niveles Seguridad y Básica.
  - **Completa**: todos los datos necesarios para identificar y ayudar a solucionar problemas, además de datos de los niveles Seguridad, Básica y Mejorada.

  [System/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) (CSP de System/AllowTelemetry)

- **Send Microsoft Edge browsing data to Microsoft 365 Analytics** (Enviar datos de exploración de Microsoft Edge a Microsoft 365 Analytics): para usar esta característica, establezca la configuración **Compartir datos de uso** en **Mejorado** o **Completo**. Esta característica controla los datos que Microsoft Edge envía a Microsoft 365 Analytics para los dispositivos empresariales que tienen configurado un identificador comercial. Las opciones son:
  - **No configurado**: usa el valor predeterminado del sistema operativo, que no puede enviar ningún dato de navegación histórico.
  - **Only send intranet data** (Enviar solo datos de la intranet): permite que el administrador envíe el historial de datos de la intranet.
  - **Only send internet data** (Enviar solo datos de Internet): permite que el administrador envíe el historial de datos de Internet.
  - **Send intranet and internet data** (Enviar datos de la intranet y de Internet): permite que el administrador envíe el historial de datos de la intranet y de Internet.

  [Browser/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics) (CSP de Browser/ConfigureTelemetryForMicrosoft365Analytics)

- **Servidor proxy de telemetría**: especifique el nombre de dominio completo (FQDN) o la dirección IP de un servidor proxy para las solicitudes de Telemetría y experiencias del usuario conectado mediante una conexión de Capa de sockets seguros. El formato de esta configuración es *servidor*:*puerto*. Si se produce un error en el proxy mencionado o si no hay ningún proxy especificado cuando esta directiva está habilitada, los datos de Telemetría y experiencias del usuario conectado no se envían y permanecen en el dispositivo local.

  Formatos de ejemplo:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy) (CSP de System/TelemetryProxy)

Haga clic en **Aceptar** para guardar los cambios.

## <a name="search"></a>Buscar

Estas opciones de configuración usan [search policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) (CSP de directiva de búsqueda), que también indica las ediciones de Windows compatibles. 

- **Búsqueda segura (solo dispositivos móviles)** : controla cómo Cortana filtra contenido para adultos en los resultados de la búsqueda. Las opciones son:
  - **Definido por el usuario**: permita a los usuarios finales elegir su propia configuración.
  - **Estricto**: filtrado más alto del contenido para adultos.
  - **Moderado**: filtrado moderado del contenido para adultos. No se filtran los resultados de búsqueda válidos.
- **Mostrar los resultados de los sitios web en la búsqueda**: cuando se establece en **Bloquear**, los usuarios no pueden buscar y los resultados web no se muestran en la búsqueda. **Sin configurar** (valor predeterminado) permite a los usuarios buscar en Internet y los resultados se muestran en el dispositivo.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="start"></a>Start

Estas opciones de configuración usan [start policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start) (CSP de directiva de inicio), que también indica las ediciones de Windows compatibles.  

- **Diseño del menú Inicio**: invalide el diseño de inicio predeterminado y personalice el menú Inicio en dispositivos de escritorio. Cargue un archivo XML que incluya las personalizaciones, incluido el orden en que aparecen las aplicaciones, etc. Los usuarios no pueden cambiar el diseño del menú Inicio que especifique.
- **Anclar los sitios web a iconos del menú Inicio**: puede importar imágenes desde Microsoft Edge que se muestran como vínculos en el menú Inicio de Windows de los dispositivos de escritorio.
- **Desanclar aplicaciones de la barra de tareas**: **Bloquear** evita que los usuarios desanclen aplicaciones de la barra de tareas. **Sin configurar** (valor predeterminado) permite que los usuarios desanclen aplicaciones de la barra de tareas.
- **Cambio rápido de usuario**: **Bloquear** evita el cambio entre usuarios que han iniciado sesión al mismo tiempo sin cerrar la sesión. **Sin configurar** (valor predeterminado) muestra **Cambiar usuario** en el icono de usuario.
- **Aplicaciones más usadas**: **Bloquear** oculta las aplicaciones más usadas en el menú Inicio. También deshabilita la alternancia correspondiente en la aplicación Configuración. **Sin configurar** (valor predeterminado) muestra las aplicaciones más usadas.
- **Aplicaciones agregadas recientemente**: **Bloquear** oculta las aplicaciones agregadas recientemente en el menú Inicio. También deshabilita la alternancia correspondiente en la aplicación Configuración. **Sin configurar** (valor predeterminado) muestra las aplicaciones agregadas recientemente en el menú Inicio.
- **Modo de pantalla de inicio**: elija cómo quiere que se muestre la pantalla de inicio. Las opciones son:
  - **Definido por el usuario**: no fuerza el tamaño de Inicio. Los usuarios pueden establecer el tamaño.
  - **Pantalla completa**: fuerza un tamaño de pantalla completa de Inicio.
  - **Pantalla parcial**: fuerza un tamaño de pantalla parcial de Inicio.
- **Elementos abiertos recientemente en listas de accesos directos**: **Bloquear** oculta las listas de accesos directos recientes en el menú Inicio y la barra de tareas. También deshabilita la alternancia correspondiente en la aplicación Configuración. **Sin configurar** (valor predeterminado) muestra los elementos abiertos recientemente en las listas de accesos directos.
- **Lista de aplicaciones**: elija cómo se muestra toda la lista de aplicaciones. Las opciones son:
  - **Definido por el usuario**: no se fuerza ninguna opción. Los usuarios eligen cómo se muestra la lista de aplicaciones en el dispositivo.
  - **Contraer**: oculta toda la lista de aplicaciones.
  - **Contraer y deshabilitar la aplicación Configuración**: oculte toda la lista de aplicaciones y deshabilite **Mostrar lista de aplicaciones en el menú Inicio** en la aplicación Configuración.
  - **Quitar y deshabilitar la aplicación Configuración**: oculte toda la lista de aplicaciones, quite todos los botones de aplicaciones y deshabilite **Mostrar lista de aplicaciones en el menú Inicio** en la aplicación Configuración.
- **Botón de encendido**: **Bloquear** oculta el botón de encendido en el menú Inicio. **Sin configurar** (valor predeterminado) muestra el botón de encendido.
- **Icono del usuario**: **Bloquear** oculta el icono del usuario en el menú Inicio. **Sin configurar** (valor predeterminado) muestra el icono del usuario y además establece los valores siguientes:
  - **Bloquear**: **Bloquear** oculta la opción **Bloquear** en el icono del usuario del menú Inicio. **Sin configurar** (valor predeterminado) muestra la opción **Bloquear**.
  - **Cerrar sesión**: **Bloquear** oculta la opción **Cerrar sesión** en el icono del usuario del menú Inicio. **Sin configurar** (valor predeterminado) muestra la opción **Cerrar sesión**.
- **Apagar**: **Bloquear** oculta las opciones **Actualizar y apagar** y **Apagar** en el botón de encendido del menú Inicio. **Sin configurar** (valor predeterminado) muestra estas opciones.
- **Suspender**: **Bloquear** oculta la opción **Suspender** en el botón de encendido del menú Inicio. **Sin configurar** (valor predeterminado) muestra esta opción.
- **Hibernar**: **Bloquear** oculta la opción **Hibernar** en el botón de encendido del menú Inicio. **Sin configurar** (valor predeterminado) muestra esta opción.
- **Cambiar cuenta**: **Bloquear** oculta la opción **Cambiar cuenta** en el icono del usuario del menú Inicio. **Sin configurar** (valor predeterminado) muestra esta opción.
- **Opciones de reinicio**: **Bloquear** oculta las opciones **Actualizar y reiniciar** y **Reiniciar** en el botón de encendido del menú Inicio. **Sin configurar** (valor predeterminado) muestra estas opciones.
- **Documentos en Inicio**: oculta o muestra la carpeta Documentos en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.
- **Descargas en Inicio**: oculta o muestra la carpeta Descargas en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.
- **Explorador de archivos en Inicio**: oculte o muestre el Explorador de archivos en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.
- **Grupo Hogar en Inicio**: oculte o muestre el acceso directo Grupo Hogar en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.
- **Música en Inicio**: oculta o muestra la carpeta Música en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.
- **Red en Inicio**: oculte o muestre Red en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.
- **Carpeta Personal en Inicio**: oculte o muestre la carpeta Personal en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.
- **Imágenes en Inicio**: oculta o muestra la carpeta de imágenes en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.
- **Configuración en Inicio**: oculte o muestre el acceso directo Configuración en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.
- **Vídeos en Inicio**: oculta o muestra la carpeta de vídeos en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción de la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción de la aplicación Configuración.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="windows-defender-smart-screen"></a>SmartScreen de Windows Defender

- **SmartScreen para Microsoft Edge**: **Requerir** desactiva SmartScreen de Windows Defender y evita que los usuarios lo activen. **Sin configurar** (valor predeterminado) activa SmartScreen. Ayuda a proteger a los usuarios frente a amenazas potenciales y evita que lo desactiven.

  Microsoft Edge usa SmartScreen de Windows Defender (activado) para proteger a los usuarios frente a software malintencionado y posibles estafas de suplantación de identidad.

  [Browser/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) (CSP de Browser/AllowSmartScreen)

- **Acceso a sitios malintencionados**: **Bloquear** evita que los usuarios omitan las advertencias del filtro SmartScreen de Windows Defender y no permite que vayan al sitio. **Sin configurar** (valor predeterminado) permite a los usuarios omitir las advertencias e ir al sitio.

  [Browser/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) (CSP de Browser/PreventSmartScreenPromptOverride)

- **Descarga de archivos no comprobados**: **Bloquear** evita que los usuarios omitan las advertencias del filtro SmartScreen de Windows Defender y no permite que descarguen archivos no comprobados. **Sin configurar** (valor predeterminado) permite a los usuarios omitir las advertencias y seguir descargando los archivos no comprobados.

  [Browser/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) (CSP de Browser/PreventSmartScreenPromptOverrideForFiles)

Haga clic en **Aceptar** para guardar los cambios.

## <a name="windows-spotlight"></a>Contenido destacado de Windows

Estas opciones de configuración usan [experience policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) (CSP de directiva de experiencia), que también indica las ediciones de Windows compatibles.

- **Contenido destacado de Windows**: **Bloquear** desactiva el contenido destacado de Windows en la pantalla de bloqueo, las recomendaciones de Windows, las características de consumidor de Microsoft y otras características relacionadas. Si su objetivo es minimizar el tráfico de red desde los dispositivos, establezca esta opción en **Bloquear**. **Sin configurar** (valor predeterminado) permite las características de contenido destacado de Windows y puede ser controlado por los usuarios finales. Cuando está habilitado, también puede permitir o bloquear las siguientes opciones:

  - **Contenido destacado de Windows en la pantalla de bloqueo**: **Bloquear** evita que Contenido destacado de Windows muestre información en la pantalla de bloqueo del dispositivo. **Sin configurar** (valor predeterminado) habilita esta característica.
  - **Sugerencias de terceros en Contenido destacado de Windows**: **Bloquear** evita que Contenido destacado de Windows sugiera contenido que no ha sido publicado por Microsoft. **Sin configurar** (valor predeterminado) permite sugerencias de contenido y aplicaciones de editores de software asociados en características de Contenido destacado de Windows, como el contenido destacado en la pantalla de bloqueo, aplicaciones sugeridas en el menú Inicio y recomendaciones de Windows.
  - **Características de consumidor**: **Bloquear** desactiva experiencias que suelen ser solo para consumidores, como las sugerencias de inicio, las notificaciones de suscripción, la instalación de aplicaciones tras la configuración rápida y los iconos de redireccionamiento. **No configurado** (valor predeterminado) permite estas características.
  - **Recomendaciones de Windows**: **Bloquear** deshabilita las recomendaciones emergentes de Windows. **Sin configurar**: (valor predeterminado) permite que se muestren las recomendaciones de Windows.
  - **Contenido destacado de Windows en el centro de actividades**: **Bloquear** evita que las notificaciones de Contenido destacado de Windows aparezcan en el centro de actividades. **Sin configurar** (valor predeterminado) puede mostrar notificaciones en el centro de actividades que sugieran aplicaciones o características para ayudar a los usuarios a ser más productivos en Windows.
  - **Personalización de Contenido destacado de Windows**: **Bloquear** evita que Windows use datos de diagnóstico para proporcionar experiencias personalizadas al usuario. **Sin configurar** (valor predeterminado) permite a Microsoft usar datos de diagnóstico para proporcionar recomendaciones y sugerencias personalizadas y ofrece personalizar Windows para las necesidades del usuario.
  - **Experiencia de bienvenida de Windows**: **Bloquear** desactiva la característica de experiencia de bienvenida de Windows de Contenido destacado de Windows. La experiencia de bienvenida de Windows no muestra si hay actualizaciones y cambios para Windows y sus aplicaciones. **Sin configurar** (valor predeterminado) permite que la experiencia de bienvenida de Windows muestre al usuario información sobre características nuevas o actualizadas.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="windows-defender-antivirus"></a>Antivirus de Windows Defender

Estas opciones de configuración usan [defender policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) (CSP de directiva de Defender), que también indica las ediciones de Windows compatibles.

- **Supervisión en tiempo real**: **Habilitar** evita el examen en tiempo real de malware, spyware y otro software no deseado. **Sin configurar** (valor predeterminado) permite esta característica.
- **Supervisión de comportamiento**: **Habilitar** evita que Defender compruebe determinados patrones conocidos de actividad sospechosa en los dispositivos. **Sin configurar** (valor predeterminado) permite la supervisión de comportamiento de Windows Defender.
- **Sistema de inspección de red (NIS)** : NIS ayuda a proteger los dispositivos contra las vulnerabilidades de seguridad basadas en red. Usa las firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para ayudar a detectar y bloquear el tráfico malintencionado.
- **Analizar todas las descargas**: controla si Defender examina todos los archivos descargados de Internet.
- **Examinar scripts cargados en exploradores web de Microsoft**: **Sin configurar** (valor predeterminado) permite a Defender examinar scripts que se usan en Internet Explorer. **Habilitar** evita este examen.
- **Acceso de usuario final a Defender**: **Bloquear** oculta la interfaz de usuario de Windows Defender a los usuarios finales. También se suprimen todas las notificaciones de Windows Defender. **Sin configurar** (valor predeterminado) permite el acceso de los usuarios a la interfaz de usuario de Windows Defender. Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario final.
- **Intervalo de actualización de firma (en horas)** : especifique el intervalo durante el que Defender busca nuevos archivos de firmas, de 0 a 24. Las opciones son:

  - **Sin configurar** (valor predeterminado).
  - **No comprobar**: Defender no busca nuevos archivos de firmas.
  - **1-24**: `1` busca cada hora, `2` busca cada dos horas, `24` busca cada día, etc.
- **Supervisar la actividad de archivos y programas**: permite que Defender supervise la actividad de archivos y programas en los dispositivos.
- **Días antes de eliminar el malware en cuarentena**: siga realizando el seguimiento de malware resuelto durante el número de días especificado para poder comprobar de forma manual los dispositivos previamente afectados. Si establece el número de días en **0**, el malware permanece en la carpeta de cuarentena y no se quita automáticamente. Cuando se establece en `90`, los elementos en cuarentena se almacenan durante 90 días en el sistema y luego se eliminan.
- **Límite de uso de la CPU durante un examen**: limita la cantidad de CPU que pueden usar los exámenes (de **1** a **100**).
- **Examinar archivos de almacenamiento**: **Habilitar** evita que Defender examine archivos almacenados, como archivos .zip o .cab. **Sin configurar** (valor predeterminado) permite este examen.
- **Examinar mensajes de correo entrante**: **Habilitar** permite que Defender examine los mensajes de correo electrónico a medida que llegan al dispositivo. **Sin configurar** (valor predeterminado) evita el examen de correo electrónico.
- **Examinar unidades extraíbles durante un examen completo**: **Habilitar** evita los exámenes completos de las unidades extraíbles. **Sin configurar** (valor predeterminado) permite que Defender examine unidades extraíbles, como sticks USB.
- **Examinar unidades de red asignadas durante un examen completo**: **Habilitar** permite que Defender examine archivos en unidades de red asignadas. **Sin configurar** (valor predeterminado) evita el examen completo. Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos.
- **Examinar archivos abiertos desde carpetas de red**: **Sin configurar** (valor predeterminado) permite que Defender examine archivos en unidades de red compartidas, como los archivos a los que se accede desde una ruta de acceso UNC. **Habilitar** evita este examen. Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos.
- **Protección de la nube**: **Sin configurar** (valor predeterminado) permite que Microsoft Active Protection Service reciba información relativa a la actividad de malware de los dispositivos que administra. **Habilitar** bloquea esta característica.
- **Preguntar a los usuarios antes de enviar muestras**: controla si los archivos potencialmente malintencionados que podrían requerir un análisis posterior se envían automáticamente a Microsoft. Las opciones son:
  - **No configurado**.
  - **Preguntar siempre**
  - **Preguntar antes de enviar datos personales**
  - **No enviar datos nunca**
  - **Enviar todos los datos sin preguntar**: los datos se envían automáticamente

- **Hora a la que se realizará un examen rápido diario**: elija la hora a la que se ejecutará un examen rápido diario. **No configurado**: no se ejecuta ningún examen diario. Si quiere personalizar más esta opción, configure el valor **Tipo de examen del sistema para realizar**.

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- **Tipo de examen del sistema para realizar**: programe un examen del sistema, incluido el nivel de examen, así como el día y la hora a la que se ejecutará el examen. Las opciones son:
  - **No configurado**: no se programa ningún examen del sistema en el dispositivo. Los usuarios finales pueden ejecutar exámenes manualmente según necesiten o quieran en sus dispositivos.
  - **Deshabilitar**: deshabilita cualquier examen del sistema en el dispositivo. Elija esta opción si usa una solución antivirus de un asociado que examina los dispositivos.
  - **Examen rápido**: examina ubicaciones comunes donde podría haber malware registrado, como las claves del Registro y las carpetas de inicio de Windows conocidas.
    - **Día programado**: elija el día en el que se ejecutará el examen.
    - **Hora programada**: elija la hora a la que se ejecutará el examen.
  - **Examen completo**: examina ubicaciones comunes donde podría haber malware registrado y también examina todos los archivos y las carpetas del dispositivo.
    - **Día programado**: elija el día en el que se ejecutará el examen.
    - **Hora programada**: elija la hora a la que se ejecutará el examen.

  Esta configuración podría entrar en conflicto con la configuración **Hora a la que se realizará un examen rápido diario**. Algunas recomendaciones:

  - Para ejecutar un examen rápido diario, configure el valor **Hora a la que se realizará un examen rápido diario**.
  - Para ejecutar un examen rápido diario y uno completo semanal, configure **Hora a la que se realizará un examen rápido diario**. Establezca **Tipo de examen del sistema para realizar** en un examen completo con el día y la hora.
  - No configure el valor **Hora a la que se realizará un examen rápido diario** simultáneamente con **Tipo de examen del sistema para realizar** establecido en **Examen rápido**. Esta configuración podría entrar en conflicto y puede que no se ejecute un examen.
  - Para ejecutar un examen rápido todos los martes a las 6:00, configure el valor **Tipo de examen del sistema para realizar**.

  [CSP Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [CSP Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [CSP Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Detectar aplicaciones potencialmente no deseadas**: elija el nivel de protección cuando Windows detecte aplicaciones potencialmente no deseadas. Las opciones son:
  - **Sin configurar** (valor predeterminado): la protección de Windows Defender frente a aplicaciones potencialmente no deseadas se deshabilita.
  - **Bloquear**: Windows Defender detecta aplicaciones potencialmente no deseadas y los elementos detectados se bloquean. Estos elementos se muestran en el historial junto con otras amenazas.
  - **Auditar**: Windows Defender detecta aplicaciones potencialmente no deseadas pero no toma ninguna medida. Puede revisar la información sobre las aplicaciones contra las que Windows Defender tomaría medidas. Por ejemplo, busque eventos creados por Windows Defender en el Visor de eventos.

  Para obtener más información sobre aplicaciones potencialmente no deseadas, vea [Detectar y bloquear aplicaciones potencialmente no deseadas](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).

- **Acciones para amenazas de malware detectadas**: elija las acciones que quiere que Defender realice para cada nivel de amenaza que detecte: bajo, moderado, alto y grave. Si no es posible, Windows Defender elige la mejor opción para asegurarse de corregir la amenaza. Las opciones son:
  - **Limpiar**
  - **Cuarentena**
  - **Quitar**
  - **Permitir**
  - **Definido por el usuario**
  - **Bloquear**

Haga clic en **Aceptar** para guardar los cambios.

### <a name="windows-defender-antivirus-exclusions"></a>Exclusiones del antivirus de Windows Defender

- **Archivos y carpetas para excluir de exámenes y protección en tiempo real**: agrega uno o varios archivos y carpetas, como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluyen en los exámenes en tiempo real ni programados.
- **Extensiones de archivo para excluir de exámenes y protección en tiempo real**: agrega una o varias extensiones de archivo, como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluyen en los exámenes en tiempo real ni programados.
- **Procesos para excluir de exámenes y protección en tiempo real**: agregar uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluyen en los exámenes en tiempo real ni programados.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="next-steps"></a>Pasos siguientes

Para obtener detalles técnicos adicionales sobre cada configuración y sobre las ediciones de Windows compatibles, consulte [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Referencia sobre el CSP de directivas de Windows 10).
