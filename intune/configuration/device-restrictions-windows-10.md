---
title: 'Configuración de restricciones de dispositivos para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Consulte una lista de todas las configuraciones y sus descripciones para crear restricciones de dispositivo en Windows 10 y dispositivos posteriores. Use estos valores en un perfil de configuración para controlar las capturas de pantalla, los requisitos de contraseña, la configuración de la pantalla completa, las aplicaciones de la tienda, el explorador Microsoft Edge, Microsoft Defender, el acceso a la nube, el menú de inicio y más en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d697b2b0bc3fa5ffea4f8e8ff15cd7c62af3ad30
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547958"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos con Windows 10 y versiones posteriores para permitir o restringir características mediante Intune

En este artículo se enumeran y describen todos los diferentes valores de configuración que puede controlar en los dispositivos con Windows 10 y versiones posteriores. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, personalizar la pantalla de bloqueo, usar Microsoft Defender, etc.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos con Windows 10.

> [!Note]
> No todas las opciones están disponibles en todas las ediciones de Windows. Para ver las ediciones admitidas, consulte los [CSP de directiva](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (se abre otro sitio web de Microsoft).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>Tienda de aplicaciones

Estas opciones de configuración usan [ApplicationManagement policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) (CSP de directiva de ApplicationManagement), que también indica las ediciones de Windows compatibles.

- **Tienda de aplicaciones** (solo móvil): **Sin configurar** (valor predeterminado), permite a los usuarios finales acceder a la tienda de aplicaciones en dispositivos móviles. **Bloquear** evita el uso de la tienda de aplicaciones.
- **Actualizar automáticamente las aplicaciones de la tienda**: **Sin configurar** (valor predeterminado), permite que las aplicaciones instaladas desde Microsoft Store se actualicen automáticamente. **Bloquear** evita que las actualizaciones se instalen automáticamente.
- **Instalación de aplicaciones de confianza**: elija si se pueden instalar aplicaciones que no sean de Microsoft Store, lo que también se conoce como transferencia local. La transferencia local consiste en instalar y luego ejecutar o probar una aplicación no certificada por Microsoft Store. Por ejemplo, una aplicación interna solo para la empresa. Las opciones son:
  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración.
  - **Bloquear**: evita la transferencia local. No se pueden instalar aplicaciones que no sean de Microsoft Store.
  - **Permitir**: permite la transferencia local. Se pueden instalar aplicaciones que no sean de Microsoft Store.
- **Desbloqueo de desarrollador**: permita la configuración de desarrollador de Windows, por ejemplo, permita que las aplicaciones transferidas localmente sean modificadas por los usuarios finales. Las opciones son:
  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración.
  - **Bloquear**: evita el modo de desarrollador y la transferencia local de aplicaciones.
  - **Permitir**: permite el modo de desarrollador y la transferencia local de aplicaciones.

  [Habilitar el dispositivo para el desarrollo](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) contiene más información sobre esta característica.

- **Datos de aplicación compartidos entre usuarios**: seleccione **Permitir** para compartir datos de aplicación entre distintos usuarios en el mismo dispositivo y con otras instancias de esa aplicación. **Sin configurar** (valor predeterminado) evita que se compartan datos con otros usuarios y otras instancias de la misma aplicación.
- **Usar solo una tienda privada**: **Permitir** solo permite que se descarguen aplicaciones de una tienda privada y no de la tienda pública, incluido un catálogo comercial. **Sin configurar** (valor predeterminado) permite que se descarguen aplicaciones de una tienda privada y de una pública.
- **Inicio de aplicaciones de la tienda**: **Bloquear** deshabilita todas las aplicaciones que se han instalado previamente en el dispositivo, o bien que se han descargado de Microsoft Store. **Sin configurar** (valor predeterminado) permite abrir estas aplicaciones.
- **Instalar los datos de aplicación en el volumen del sistema**: **Bloquear** evita que las aplicaciones almacenen datos en el volumen del sistema del dispositivo. **Sin configurar** (valor predeterminado) permite que las aplicaciones almacenen datos en el volumen de disco del sistema.
- **Instalar las aplicaciones en la unidad del sistema**: **Bloquear** evita que las aplicaciones se instalen en la unidad del sistema del dispositivo. **Sin configurar** (valor predeterminado) permite que las aplicaciones se instalen en la unidad del sistema.
- **Game DVR** (solo escritorio): **Bloquear** deshabilita la grabación y difusión de juegos de Windows. **Sin configurar** (valor predeterminado) permite la grabación y difusión de juegos.
- **Aplicaciones solo de la tienda**: esta opción determina la experiencia del usuario cuando los usuarios instalan aplicaciones desde lugares distintos del Microsoft Store. Las opciones son:

  - **No configurado** (valor predeterminado): permite a los usuarios finales instalar aplicaciones desde lugares distintos del Microsoft Store, incluidas las aplicaciones definidas en otras configuraciones de directiva.  
  - **En cualquier lugar**: desactiva las recomendaciones de la aplicación y permite a los usuarios instalar aplicaciones desde cualquier ubicación.  
  - **Solo almacenar**: obliga a los usuarios finales a que solo instalen aplicaciones desde el Microsoft Store.
  - **Recomendaciones**: al instalar una aplicación de la web que está disponible en el Microsoft Store, los usuarios ven un mensaje que le recomienda descargarla de la tienda.  
  - **Preferir tienda**: advierte a los usuarios cuando instalan aplicaciones desde lugares distintos del Microsoft Store.

  [SmartScreen/EnableAppInstallControl CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **Control de usuario sobre las instalaciones**: si está establecido en **Sin configurar** (valor predeterminado), Windows Installer evita que los usuarios cambien las opciones de instalación que habitualmente están reservadas para los administradores del sistema, como entrar al directorio para instalar los archivos. **Bloquear** permite que los usuarios cambien estas opciones de instalación y se omiten algunas de las características de seguridad de Windows Installer.

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **Instalar aplicaciones con privilegios elevados**: si está establecido en **Sin configurar** (valor predeterminado), el sistema aplica los permisos del usuario actual cuando instala programas que un administrador del sistema no implementa ni ofrece. **Bloquear** indica a Windows Installer que use permisos elevados cuando instale cualquier programa en el sistema. Estos privilegios se extienden a todos los programas.

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **Aplicaciones de inicio**: escriba una lista de las aplicaciones que deben abrirse después de que un usuario inicie sesión en el dispositivo. Asegúrese de usar una lista delimitada por punto y coma de nombres de familia de paquete (PFN) de aplicaciones Windows. Para que esta directiva funcione, el manifiesto de las aplicaciones Windows debe usar una tarea de inicio.

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

Estas opciones de configuración usan los CSP de [directiva de conectividad](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) y [directiva de Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi), que también enumeran las ediciones de Windows compatibles.

- [Wi-Fi policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) (CSP de directiva de Wi-Fi)

- **Canal de datos móviles**: elija si los usuarios finales pueden usar datos, por ejemplo, navegar por Internet, cuando están conectados a una red móvil. Las opciones son:
  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración. Los usuarios finales pueden desactivarlo.
  - **Bloquear**: no permita el canal de datos móviles. Los usuarios finales no pueden activarlo.
  - **Permitir (no editable)** : permite el canal de datos móviles. Los usuarios finales no pueden desactivarlo.

- **Itinerancia de datos**: **Bloquear** evita la itinerancia de datos móviles en el dispositivo. **Sin configurar** (valor predeterminado) permite la itinerancia entre redes al acceder a datos.
- **VPN a través de la red de telefonía móvil**: **Bloquear** evita que el dispositivo acceda a conexiones VPN cuando se conecta a una red móvil. **Sin configurar** (valor predeterminado) permite que la VPN use cualquier conexión, incluida la móvil.
- **Itinerancia de VPN a través de la red de telefonía móvil**: **Bloquear** evita que el dispositivo acceda a conexiones VPN cuando está en itinerancia en una red móvil. **Sin configurar** (valor predeterminado) permite las conexiones VPN en itinerancia.
- **Servicio de dispositivos conectados**: **Bloquear** deshabilita el componente de plataforma de dispositivos conectados (CDP). CDP habilita la detección de otros dispositivos y la conexión a ellos (a través de Bluetooth/LAN o la nube) para permitir el inicio de aplicaciones remoto, la mensajería remota, las sesiones de aplicación remotas y otras experiencias en varios dispositivos. **Sin configurar** (valor predeterminado) permite el servicio de dispositivos conectados, lo que habilita la detección de otros dispositivos Bluetooth y la conexión a ellos.
- **NFC**: **Bloquear** evita las capacidades de transmisión de datos en proximidad (NFC). **Sin configurar** (valor predeterminado) permite a los usuarios habilitar y configurar las características de NFC en el dispositivo.
- **Wi-Fi**: **Bloquear** evita que los usuarios habiliten, configuren y usen conexiones Wi-Fi en el dispositivo. **Sin configurar** (valor predeterminado) permite las conexiones Wi-Fi.
- **Conectar automáticamente a zonas Wi-Fi**: **Bloquear** evita que los dispositivos se conecten automáticamente a zonas Wi-Fi. **Sin configurar** (valor predeterminado) permite que los dispositivos se conecten automáticamente a zonas Wi-Fi gratuitas y acepten de forma automática los términos y condiciones para la conexión.
- **Configuración manual de Wi-Fi**: **Bloquear** evita que los dispositivos se conecten a Wi-Fi fuera de redes instaladas por el servidor MDM. **Sin configurar** (valor predeterminado) permite a los usuarios finales agregar y configurar sus propios SSID de red de conexiones Wi-Fi.
- **Intervalo de detección de Wi-Fi**: especifique con qué frecuencia los dispositivos detectan redes Wi-Fi. Escriba un valor de 1 (más frecuente) a 500 (menos frecuente). El valor predeterminado es `0` (cero).

### <a name="bluetooth"></a>Bluetooth

Estas opciones de configuración usan [Bluetooth policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth) (CSP de directiva de Bluetooth), que también indica las ediciones de Windows compatibles.

- **Bluetooth**: **Bloquear** evita que los usuarios habiliten Bluetooth. **Sin configurar** (valor predeterminado) permite Bluetooth en el dispositivo.
- **Detectabilidad de Bluetooth**: **Bloquear** evita que otros dispositivos con Bluetooth habilitado detecten el dispositivo. **Sin configurar** (valor predeterminado) permite que otros dispositivos con Bluetooth habilitado —por ejemplo, auriculares— detecten el dispositivo.
- **Emparejamiento previo Bluetooth**: **Bloquear** evita que dispositivos Bluetooth específicos se emparejen automáticamente con un dispositivo de host. **Sin configurar** (valor predeterminado) permite el emparejamiento automático con el dispositivo de host.
- **Anuncios de Bluetooth**: **Bloquear** evita que el dispositivo envíe anuncios de Bluetooth. **Sin configurar** (valor predeterminado) permite que el dispositivo envíe anuncios de Bluetooth.
- **Servicios Bluetooth permitidos**: **agregue** una lista de perfiles y servicios Bluetooth permitidos como cadenas hexadecimales, por ejemplo, `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`.

  [ServicesAllowedList usage guide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) (Guía de uso de ServicesAllowedList) contiene más información sobre la lista de servicios.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

Estas opciones de configuración usan [accounts policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts) (CSP de directiva de cuentas), que también indica las ediciones de Windows compatibles.

- **Cuenta Microsoft**: **Bloquear** evita que los usuarios finales asocien una cuenta Microsoft al dispositivo. **Sin configurar** (valor predeterminado) permite agregar y usar una cuenta Microsoft.
- **Cuenta que no es Microsoft**: **Bloquear** evita que los usuarios finales agreguen cuentas que no son de Microsoft mediante la interfaz de usuario. **Sin configurar** (valor predeterminado) permite que los usuarios agreguen cuentas de correo electrónico que no están asociadas a una cuenta Microsoft.
- **Sincronización de configuración de cuenta Microsoft**: **Sin configurar** (valor predeterminado), permite que la configuración de dispositivo y aplicación asociada a una cuenta Microsoft se sincronice entre dispositivos. **Bloquear** evita esta sincronización.
- **Ayudante para el inicio de sesión de cuentas Microsoft**: si se establece en **Sin configurar** (valor predeterminado), los usuarios finales pueden iniciar y detener el servicio **Ayudante para el inicio de sesión de cuenta Microsoft** (wlidsvc). Este servicio del sistema operativo permite a los usuarios iniciar sesión en su cuenta Microsoft. **Deshabilitar** evita que los usuarios finales controlen el servicio Ayudante para el inicio de sesión de cuenta Microsoft (wlidsvc).

## <a name="cloud-printer"></a>Impresora en la nube

Estas opciones de configuración usan [EnterpriseCloudPrint policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint) (CSP de directiva de EnterpriseCloudPrint), que también indica las ediciones de Windows compatibles.

- **URL de detección de impresoras**: especifique la URL para encontrar impresoras en la nube. Por ejemplo, escriba `https://cloudprinterdiscovery.contoso.com`.
- **URL de autoridad de acceso a impresoras**: especifique la dirección URL del punto de conexión de autenticación para obtener tokens de OAuth. Por ejemplo, escriba `https://azuretenant.contoso.com/adfs`.
- **GUID de aplicación cliente nativa de Azure**: especifique el GUID de una aplicación cliente autorizada para obtener tokens de OAuth desde OAuthAuthority. Por ejemplo, escriba `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **URI de recurso de servicio de impresión**: indique el URI de recurso de OAuth del servicio de impresión configurado en Azure Portal. Por ejemplo, escriba `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **N.º máximo de impresoras para consultar**: indique el número máximo de impresoras que quiere que se consulten. El valor predeterminado es `20`.
- **URI de recurso del servicio de detección de impresoras**: indique el URI de recurso de OAuth del servicio de detección de impresoras configurado en Azure Portal. Por ejemplo, escriba `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Después de configurar la [impresión de Windows Server híbrida en la nube](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), puede configurar estas opciones e implementarlas en los dispositivos Windows.

## <a name="control-panel-and-settings"></a>Panel de control y configuración

- **Aplicación Configuración**: **Bloquear** evita que los usuarios finales accedan a la aplicación de configuración de Windows. **Sin configurar** (valor predeterminado) permite que los usuarios abran la aplicación Configuración en el dispositivo.
  - **Sistema**: **Bloquear** evita el acceso al área Sistema de la aplicación Configuración. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
    - **Modificación de la configuración de inicio/apagado y suspensión** (solo equipos de escritorio): **Bloquear** evita que los usuarios finales cambien la configuración de inicio/apagado y suspensión en el dispositivo. **Sin configurar** (valor predeterminado) permite que los usuarios cambien la configuración de inicio/apagado y suspensión.
  - **Dispositivos**: **Bloquear** evita el acceso al área Dispositivos de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Red e Internet**: **Bloquear** evita el acceso al área Red e Internet de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Personalización**: **Bloquear** evita el acceso al área Personalización de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Aplicaciones**: **Bloquear** evita el acceso al área Aplicaciones de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Cuentas**: **Bloquear** evita el acceso al área Cuentas de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Hora e idioma**: **Bloquear** evita el acceso al área Hora e idioma de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
    - **Modificación de la hora del sistema**: **Bloquear** evita que los usuarios finales cambien la configuración de fecha y hora en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Los usuarios pueden cambiar la configuración.
    - **Modificación de la configuración regional** (solo escritorio): **Bloquear** evita que los usuarios finales cambien la configuración regional en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Los usuarios pueden cambiar la configuración.
    - **Modificación de la configuración de idioma (solo equipos de escritorio)** : **Bloquear** evita que los usuarios finales cambien la configuración de idioma en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Los usuarios pueden cambiar la configuración.

      [Settings policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings) (CSP de directiva de configuración)

  - **Juegos**: **Bloquear** evita el acceso al área Juegos de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Accesibilidad**: **Bloquear** evita el acceso al área Accesibilidad de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Privacidad**: **Bloquear** evita el acceso al área Privacidad de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Actualización y seguridad**: **Bloquear** evita el acceso al área Actualización y seguridad de la aplicación Configuración en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.

## <a name="display"></a>Pantalla

Estas opciones de configuración usan [display policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display) (CSP de directiva de pantalla), que también indica las ediciones de Windows compatibles.

El ajuste de escala de PPP de GDI permite a las aplicaciones sin reconocimiento de PPP lograr el reconocimiento de PPP por monitor.

- **Activar el ajuste de GDI para las aplicaciones**: **agregue** las aplicaciones heredadas que quiere que tengan activado el ajuste de escala de PPP de GDI. Por ejemplo, escriba `filename.exe` o `%ProgramFiles%\Path\Filename.exe`.

  El ajuste de escala de PPP de GDI se activa para todas las aplicaciones heredadas de la lista.

- **Desactivar el ajuste de GDI para las aplicaciones**: **agregue** las aplicaciones heredadas que quiere que tengan desactivado el ajuste de escala de PPP de GDI. Por ejemplo, escriba `filename.exe` o `%ProgramFiles%\Path\Filename.exe`.

  El ajuste de escala de PPP de GDI se desactiva para todas las aplicaciones heredadas de la lista.

También puede **Importar** un archivo .csv con la lista de aplicaciones.

## <a name="general"></a>General

Estas opciones de configuración usan [experience policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) (CSP de directiva de experiencia), que también indica las ediciones de Windows compatibles. 

- **Captura de pantalla** (solo móviles): **Bloquear** evita que los usuarios finales obtengan capturas de pantalla en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Copiar y pegar (solo móvil)** : **Bloquear** evita que los usuarios finales usen Copiar y pegar entre aplicaciones en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Cancelar suscripción manualmente**: **Bloquear** evita que los usuarios finales eliminen la cuenta del área trabajo mediante el panel de control del área de trabajo en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.

  Esta configuración de directiva no se aplica si el equipo está unido a Azure AD y la inscripción automática está habilitada.

- **Instalación manual del certificado raíz** (solo móviles): **Bloquear** evita que los usuarios finales instalen manualmente certificados raíz y certificados CAP intermedios. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Cámara**: **Bloquear** evita que los usuarios finales usen la cámara en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.

  [CSP de cámara](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-camera)

- **Sincronización de archivos de OneDrive**: **Bloquear** evita que los usuarios finales sincronicen archivos con OneDrive desde el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Almacenamiento extraíble**: **Bloquear** evita que los usuarios finales usen dispositivos de almacenamiento externo, como tarjetas SD, con el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Geolocalización**: **Bloquear** evita que los usuarios finales activen servicios de ubicación en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Conexión compartida**: **Bloquear** evita el uso compartido de una conexión a Internet en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Restablecimiento del teléfono**: **Bloquear** evita que los usuarios finales borren o realicen un restablecimiento de fábrica en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Conexión USB**: **Bloquear** evita el acceso a dispositivos de almacenamiento externo mediante una conexión USB en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. La carga USB no se ve afectada por esta opción.
- **Modo antirrobo** (solo móviles): **Bloquear** evita que los usuarios finales seleccionen la preferencia de modo antirrobo en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Cortana**: **Bloquear** deshabilita el asistente de voz Cortana en el dispositivo. Si Cortana está desactivado, los usuarios pueden seguir buscando elementos en el dispositivo. **Sin configurar** (valor predeterminado) permite Cortana.
- **Grabación de voz** (solo móviles): **Bloquear** evita que los usuarios finales usen la grabadora de voz del dispositivo en este. **Sin configurar** (valor predeterminado) permite la grabación de voz para aplicaciones.
- **Modificación del nombre del dispositivo** (solo móvil): **Bloquear** evita que los usuarios finales cambien el nombre del dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Agregar paquetes de aprovisionamiento**: **Bloquear** evita el agente de configuración en tiempo de ejecución que instala paquetes de aprovisionamiento en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Quitar paquetes de aprovisionamiento**: **Bloquear** evita el agente de configuración en tiempo de ejecución que quita paquetes de aprovisionamiento del dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Detección de dispositivos**: **Bloquear** evita que otros dispositivos detecten este. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Cambio de tarea** (solo móviles): **Bloquear** evita el cambio de tarea en el dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Cuadro de diálogo de error de tarjeta SIM** (sólo móviles): **Bloquee** la aparición de mensajes de error en el dispositivo si no se detecta ninguna tarjeta SIM. **Sin configurar** (valor predeterminado) muestra los mensajes de error.
- **Ink Workspace** (Área de trabajo de Ink): elija si el usuario tiene acceso al área de trabajo de Ink y cómo. Las opciones son:
  - **Sin configurar** (valor predeterminado): activa el área de trabajo de Ink y el usuario tiene permitido usarla por encima de la pantalla de bloqueo.
  - **Deshabilitada en la pantalla de bloqueo**: el área de trabajo de Ink está habilitada y la característica está activada. Pero el usuario no puede acceder a ella por encima de la pantalla de bloqueo.
  - **Disabled**: el acceso al área de trabajo de Ink está deshabilitado. La característica está desactivada.

  [WindowsInkWorkspace policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) (CSP de directiva de WindowsInkWorkspace)

- **Reimplementación automática**: elija **Permitir** para que los usuarios con derechos administrativos puedan eliminar todos los datos y la configuración de usuario con **CTRL + Win + R** en la pantalla de bloqueo del dispositivo. El dispositivo se vuelve a configurar e inscribir automáticamente para la administración. **Sin configurar** (valor predeterminado) deshabilita esta característica.
- **Exigir que los usuarios se conecten a la red durante la configuración del dispositivo**: elija **Requerir** para que el dispositivo se conecte a una red antes de pasar de la página Red durante la configuración de Windows. **Sin configurar** (valor predeterminado) permite a los usuarios pasar de la página Red, aunque no estén conectados a una red.

  La configuración se hace efectiva la próxima vez que se borra o restablece el dispositivo. Al igual que cualquier otra configuración de Intune, el dispositivo debe estar inscrito y administrado por Intune para recibir la configuración. Pero, una vez que se ha inscrito y recibe las directivas, al restablecer el dispositivo se fuerza la configuración durante la siguiente configuración de Windows.

  [CSP TenantLockdown](https://docs.microsoft.com/windows/client-management/mdm/tenantlockdown-csp)

- **Acceso directo a memoria**: **Bloquear** impide el acceso directo a memoria (DMA) a todos los puertos de bajada PCI de conexión instantánea hasta que un usuario inicia sesión en Windows. **Habilitado** (valor predeterminado) permite el acceso a DMA, incluso cuando un usuario no ha iniciado sesión.

  [DataProtection/AllowDirectMemoryAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Finalizar procesos desde el Administrador de tareas**: esta configuración determina si los usuarios que no son administradores pueden usar el Administrador de tareas para finalizar tareas. Si selecciona **Bloquear**, se impide que los usuarios estándar (no administradores) usen el Administrador de tareas para finalizar un proceso o una tarea en el dispositivo. Si selecciona **Sin configurar** (valor predeterminado), se permite que los usuarios estándar finalicen un proceso o una tarea mediante el Administrador de tareas.

## <a name="locked-screen-experience"></a>Experiencia de pantalla bloqueada

- **Notificaciones del centro de actividades (solo móviles)** : **Bloquear** evita que las notificaciones del centro de actividades aparezcan en la pantalla de bloqueo del dispositivo. **Sin configurar** (valor predeterminado) permite a los usuarios elegir qué aplicaciones muestran notificaciones en la pantalla de bloqueo.

  [AboveLock/AllowActionCenterNotifications CSP](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#AboveLock_AllowActionCenterNotifications) (CSP de AboveLock/AllowActionCenterNotifications)

- **URL de imagen de pantalla de bloqueo (solo equipos de escritorio)** : escriba la dirección URL de una imagen en formato JPG, JPEG o PNG que se usa como fondo de pantalla de la pantalla de bloqueo de Windows. Por ejemplo, escriba `https://contoso.com/image.png`. Esta opción bloquea la imagen y no se puede cambiar posteriormente.
- **Tiempo de espera de la pantalla configurable por el usuario (solo dispositivos móviles)** : **Permitir** permite a los usuarios configurar el tiempo de espera de la pantalla. **Sin configurar** (valor predeterminado) no da a los usuarios esta opción.

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_AllowScreenTimeoutWhileLockedUserConfig) (CSP de DeviceLock/AllowScreenTimeoutWhileLockedUserConfig)

- **Cortana en pantalla bloqueada** (solo escritorio): **Bloquear** evita que los usuarios interactúen con Cortana cuando el dispositivo está en la pantalla de bloqueo. **Sin configurar** (valor predeterminado) permite la interacción con Cortana.

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock) (CSP de AboveLock/AllowCortanaAboveLock)

- **Notificaciones del sistema en pantalla bloqueada**: **Bloquear** evita que las notificaciones del sistema aparezcan en la pantalla de bloqueo del dispositivo. **Sin configurar** (valor predeterminado) permite estas notificaciones.

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts) (CSP de AboveLock/AllowToasts)

- **Tiempo de espera de la pantalla (solo dispositivos móviles)** : establezca la duración (en segundos) desde que se bloquea la pantalla hasta que se apaga. Los valores admitidos son de 11 a 1800. Por ejemplo, escriba `300` para establecer este tiempo de espera en 5 minutos.

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_ScreenTimeoutWhileLocked) (CSP de DeviceLock/ScreenTimeoutWhileLocked)

## <a name="messaging"></a>Mensajería

Estas opciones de configuración usan [messaging policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging) (CSP de directiva de mensajería), que también indica las ediciones de Windows compatibles.

- **Sincronización de mensajes (solo móvil)** : **Bloquear** deshabilita la copia de seguridad y la restauración de los mensajes de texto, así como la sincronización de mensajes entre dispositivos Windows. La deshabilitación ayuda a evitar que la información se almacene en servidores fuera del control de la organización. **Sin configurar** (valor predeterminado) permite a los usuarios cambiar esta opción y sincronizar sus mensajes.
- **MMS (solo móvil)** : **Bloquear** deshabilita la funcionalidad de envío y recepción de MMS en el dispositivo. En las empresas, use esta directiva para deshabilitar MMS en los dispositivos como parte del requisito de auditoría o administración. **Sin configurar** (valor predeterminado) permite el envío y recepción de MMS.
- **RCS (solo móvil)** : **Bloquear** deshabilita la funcionalidad de envío y recepción de Rich Communication Services (RCS) en el dispositivo. En las empresas, use esta directiva para deshabilitar RCS en los dispositivos como parte del requisito de auditoría o administración. **Sin configurar** (valor predeterminado) permite el envío y recepción de RCS.

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
  - **Páginas de inicio en la configuración de la aplicación local**: Microsoft Edge empieza con la página de inicio predeterminada que define el SO.

- **Permitir al usuario cambiar las páginas de inicio**: **Sí** (valor predeterminado), permite a los usuarios cambiar las páginas de inicio. Los administradores pueden usar `EdgeHomepageUrls` para escribir las páginas de inicio que los usuarios ven de manera predeterminada al abrir Microsoft Edge. **No** evita que los usuarios cambien las páginas de inicio.
- **Permitir contenido web en una página de nueva pestaña**: si se establece en **Sí** (valor predeterminado), Microsoft Edge abre la dirección URL especificada en la opción **Dirección URL de nueva pestaña**. Si la opción **Dirección URL de nueva pestaña** está en blanco, Microsoft Edge abre la página de nueva pestaña que aparece en la configuración de Microsoft Edge. Los usuarios pueden cambiarla. Si se establece en **No**, Microsoft Edge abre una nueva pestaña con una página en blanco. Los usuarios no pueden cambiarla.
- **Dirección URL de nueva pestaña**: escriba la dirección URL que quiera abrir en la página Nueva pestaña. Por ejemplo, escriba `https://www.bing.com` o `https://www.contoso.com`.

- **Botón Inicio**: elija lo que sucede al seleccionar el botón Inicio. Las opciones son:
  - **Páginas de inicio**: abre la opción elegida en **Iniciar Microsoft Edge con**.
  - **Página Nueva pestaña**: abre la dirección URL especificada en la opción **Dirección URL de nueva pestaña**.
  - **Dirección URL del botón de inicio**: escriba la dirección URL que se va a abrir. Por ejemplo, escriba `https://www.bing.com` o `https://www.contoso.com`.
  - **Ocultar botón Inicio**: se oculta el botón Inicio.
- **Permitir a los usuarios cambiar el botón Inicio**: **Sí** permite a los usuarios cambiar el botón Inicio. Los cambios del usuario reemplazan cualquier configuración del administrador en el botón Inicio. **No** (valor predeterminado) evita que los usuarios cambien la forma en que el administrador ha configurado el botón Inicio.
- **Mostrar la página Primera experiencia de ejecución (solo móvil)** : **Sí** (valor predeterminado) muestra la página de introducción del primer uso en Microsoft Edge. **No** evita que la página de introducción aparezca la primera vez que se ejecuta Microsoft Edge. Esta característica permite que las empresas (por ejemplo, aquellas organizaciones que usan configuraciones de cero emisiones) bloqueen esta página.
- **Ubicación de la lista de URL de Primera experiencia de ejecución** (solo Windows 10 Mobile): escriba la dirección URL que señala al archivo XML que contiene las direcciones URL de la página de primera ejecución. Por ejemplo, escriba `https://www.contoso.com/sites.xml`.

- **Actualizar el explorador después del tiempo de inactividad**: escriba el número de minutos de inactividad hasta que se actualiza el explorador, de 0 a 1440 minutos. El valor predeterminado es `5` minutos. Cuando se establece en `0` (cero), el explorador no se actualiza tras estar inactivo.

  Esta configuración solo está disponible cuando se ejecuta en [Exploración pública InPrivate (pantalla completa con una sola aplicación)](#use-microsoft-edge-kiosk-mode).

- **Permitir elementos emergentes** (solo escritorio): **Sí** (valor predeterminado) permite los elementos emergentes en el explorador web. **No** evita las ventanas emergentes en el explorador.
- **Enviar el tráfico de la intranet a Internet Explorer** (solo escritorio): **Sí** permite a los usuarios abrir sitios web de intranet en Internet Explorer en lugar de Microsoft Edge. Esta opción es para la compatibilidad con versiones anteriores. **No** (valor predeterminado) permite que los usuarios usen Microsoft Edge.
- **Ubicación de la lista de sitios del modo de empresa** (solo escritorio): escriba la dirección URL que señala al archivo XML que contiene una lista de los sitios web que se abren en el modo de empresa. Los usuarios no pueden cambiar esta lista. Por ejemplo, escriba `https://www.contoso.com/sites.xml`.
- **Mensaje al abrir sitios en Internet Explorer**: use este valor para configurar Microsoft Edge de modo que muestre una notificación antes de que se abra un sitio en Internet Explorer 11. Las opciones son:
  - **No volver a mostrar este mensaje**: se usa el comportamiento predeterminado del sistema operativo, que puede que no muestre un mensaje.
  - **Mostrar mensaje de que el sitio está abierto en Internet Explorer 11**: se muestra el mensaje al abrir sitios en Internet Explorer. Los sitios se abren en IE. 
  - **Mostrar el mensaje con la opción para abrir sitios en Microsoft Edge**: muestre el mensaje al abrir sitios en Microsoft Edge. El mensaje incluye un vínculo **Keep going in Microsoft Edge** (Seguir en Microsoft Edge) para que los usuarios puedan elegir Microsoft Edge en lugar de IE.

  > [!IMPORTANT]
  > Este valor exige usar la opción **Ubicación de la lista de sitios del modo de empresa**, **Enviar el tráfico de la intranet a Internet Explorer** o ambas.

- **Permitir lista de compatibilidad de Microsoft**: **Sí** (valor predeterminado) permite usar una lista de compatibilidad de Microsoft. **No** evita la lista de compatibilidad de Microsoft en Microsoft Edge. La lista de Microsoft ayuda a que Microsoft Edge muestre de manera correcta sitios con problemas de compatibilidad conocidos.
- **Precarga de páginas de inicio y páginas de nueva pestaña**: **Sí** (valor predeterminado) usa el comportamiento predeterminado del sistema operativo, que puede ser precargar estas páginas. La carga previa minimiza el tiempo de inicio de Microsoft Edge y carga nuevas pestañas. **No** evita que Microsoft Edge cargue previamente las páginas de inicio y la página Nueva pestaña.
- **Inicio previo de páginas de inicio y página Nueva pestaña**: **Sí** (valor predeterminado) usa el comportamiento predeterminado del sistema operativo, que puede ser preiniciar estas páginas. El inicio previo ayuda al rendimiento de Microsoft Edge y minimiza el tiempo necesario para iniciar Microsoft Edge. **No** evita que Microsoft Edge inicie previamente las páginas de inicio y la página Nueva pestaña.

### <a name="favorites-and-search"></a>Favoritos y búsqueda

- **Mostrar barra de favoritos**: elija qué le ocurre a la barra de favoritos en cualquier página de Microsoft Edge. Las opciones son:
  - **En el inicio y páginas de nueva pestaña**: muestra la barra de favoritos cuando se inicia Microsoft Edge y en todas las páginas de pestaña. Los usuarios finales pueden cambiar esta opción.
  - **En todas las páginas**: se muestra la barra de favoritos en todas las páginas. Los usuarios no pueden cambiar esta opción.
  - **Oculto**: se oculta la barra de favoritos en todas las páginas. Los usuarios no pueden cambiar esta opción.
- **Permitir cambios en favoritos**: **Sí** (valor predeterminado) usa el valor predeterminado del sistema operativo, lo que permite a los usuarios cambiar la lista. **No** evita que los usuarios finales agreguen, importen, ordenen o modifiquen la lista de favoritos.
  - **Lista de favoritos**: agregue una lista de direcciones URL al archivo de favoritos. Por ejemplo, agregue `http://contoso.com/favorites.html`.
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

### <a name="privacy-and-security"></a>Privacidad y seguridad

- **Permitir exploración de InPrivate**: **Sí** (valor predeterminado) permite la exploración de InPrivate en Microsoft Edge. Después de cerrar todas las pestañas de InPrivate, Microsoft Edge elimina los datos de exploración del dispositivo. **No** evita que los usuarios finales abran sesiones de exploración de InPrivate.
- **Guardar historial de exploración**: **Sí** (valor predeterminado) permite guardar el historial de exploración en Microsoft Edge. **No** evita guardar el historial de exploración.
- **Borrar datos de navegación al salir** (solo escritorio): **Sí** borra el historial y los datos de exploración cuando el usuario sale de Microsoft Edge. **No** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede almacenar en caché los datos de exploración.
- **Sincronizar la configuración del explorador entre los dispositivos del usuario**: elija cómo quiere sincronizar la configuración del explorador entre dispositivos. Las opciones son:
  - **Permitir**: permita la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario.
  - **Bloquear y habilitar el reemplazo de usuarios**: bloquee la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario. Los usuarios pueden reemplazar esta configuración.
  - **Bloquear**: bloquee la sincronización de la configuración del explorador Microsoft Edge entre los dispositivos del usuario. Los usuarios no pueden reemplazar esta configuración.

Si "Bloquear y habilitar el reemplazo de usuarios" está seleccionado, el usuario puede invalidar la designación de administrador.

- **Permitir administrador de contraseñas**: **Sí** (valor predeterminado) permite que Microsoft Edge use automáticamente el administrador de contraseñas, lo que permite a los usuarios guardar y administrar contraseñas en el dispositivo. **No** evita que Microsoft Edge use el administrador de contraseñas.
- **Cookies**: elija cómo se administran las cookies en el explorador web. Las opciones son:
  - **Permitir**: las cookies se almacenan en el dispositivo.
  - **Bloquear todas las cookies**: las cookies no se almacenan en el dispositivo.
  - **Bloquear solo cookies de terceros**: las cookies de terceros o de asociados no se almacenan en el dispositivo.
- **Permitir autorrelleno en los formularios**: **Sí** (valor predeterminado) permite a los usuarios cambiar la configuración de Autocompletar del explorador y rellenar automáticamente los campos de formulario. **No** deshabilita la característica Autorrelleno en Microsoft Edge.
- **Enviar encabezados de no seguimiento**: **Sí** envía encabezados de no seguimiento a los sitios web que solicitan información de seguimiento (recomendado). **No** (valor predeterminado) no envía encabezados, lo que permite a los sitios web realizar un seguimiento del usuario. El usuario puede configurar.
- **Mostrar dirección IP de localhost para WebRTC**: **Sí** (valor predeterminado) permite que la dirección IP de localhost de los usuarios se muestre cuando se hacen llamadas telefónicas a través de este protocolo. **No** evita que la dirección IP de localhost de los usuarios se muestre. 
- **Permitir recopilación de datos para iconos dinámicos**: **Sí** (valor predeterminado) permite que Microsoft Edge recopile información de los iconos dinámicos anclados al menú Inicio. **No** evita la recopilación de esta información, lo que puede limitar la experiencia de los usuarios.
- **User can override certificate errors** (El usuario puede invalidar los errores de certificado): **Sí** (valor predeterminado) permite a los usuarios acceder a sitios web que tienen errores de Capa de sockets seguros (SSL) o Seguridad de la capa de transporte (TLS). **No** (recomendado para una mayor seguridad) evita que los usuarios accedan a sitios web con errores de SSL o TLS.

### <a name="additional"></a>Adicional

- **Permitir el explorador de Microsoft Edge** (solo Mobile): **Sí** (valor predeterminado) permite usar el explorador web Microsoft Edge en el dispositivo móvil. **No** evita el uso de Microsoft Edge en el dispositivo. Si elige **No**, la demás configuración individual solo se aplica a los equipos de escritorio.
- **Permitir la lista desplegable de la barra de direcciones**: **Sí** (valor predeterminado) permite que Microsoft Edge despliegue la barra de direcciones con una lista de sugerencias. **No** evita que Microsoft Edge muestre una lista de sugerencias desplegable cuando se escribe. Cuando se establece en **No**, puede:
  - Ayudar a minimizar el ancho de banda de red entre Microsoft Edge y los servicios de Microsoft.
  - Deshabilitar **Mostrar sugerencias de búsqueda y sitios al escribir** en Microsoft Edge > Configuración.
- **Permitir modo de pantalla completa**: **Sí** (valor predeterminado) permite que Microsoft Edge use el modo de pantalla completa, que muestra solo el contenido web y oculta la interfaz de usuario de Microsoft Edge. **No** evita el modo de pantalla completa en Microsoft Edge.
- **Permitir la página about flags**: **Sí** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede permitir el acceso a la página `about:flags`. La página `about:flags` permite a los usuarios cambiar la configuración de desarrollador y habilitar características experimentales. **No** evita que los usuarios finales accedan a la página `about:flags` en Microsoft Edge.
- **Permitir herramientas de desarrollo**: **Sí** (valor predeterminado) permite a los usuarios usar las herramientas de desarrollo F12 para compilar y depurar páginas web de forma predeterminada. **No** evita que los usuarios finales usen las herramientas de desarrollo F12.
- **Permitir JavaScript**: **Sí** (valor predeterminado) permite la ejecución de scripts, como JavaScript, en el explorador Microsoft Edge. **No** evita la ejecución de scripts de Java en el explorador.
- **El usuario puede instalar extensiones**: **Sí** (valor predeterminado) permite que los usuarios finales instalen extensiones de Microsoft Edge en el dispositivo. **No** evita la instalación.
- **Permitir la instalación de prueba de extensiones de desarrollador**: **Sí** (valor predeterminado) usa el valor predeterminado del sistema operativo, que puede permitir la instalación de prueba. La transferencia local instala y ejecuta extensiones sin comprobar. **No** evita que Microsoft Edge transfiera localmente mediante la característica **Cargar extensiones**. No evita la transferencia local de extensiones de otras maneras, como PowerShell.
- **Required extensions** (Extensiones obligatorias): elija cuáles son las extensiones que los usuarios finales no pueden desactivar en Microsoft Edge. Escriba los nombres de familia de paquete y seleccione **Agregar**. [Busque un nombre de familia de paquete (PFN) para la VPN por aplicación](https://docs.microsoft.com/configmgr/protect/deploy-use/find-a-pfn-for-per-app-vpn) proporciona alguna orientación.

  También puede **Importar** un archivo .csv que incluya los nombres de familia de paquete. O bien puede **Exportar** los nombres de familia de paquete que especifique.

## <a name="network-proxy"></a>Proxy de red

Estas opciones de configuración usan [NetworkProxy policy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp) (CSP de directiva de NetworkProxy), que también indica las ediciones de Windows compatibles.

- **Detectar automáticamente configuración de proxy**: **Bloquear** evita que el dispositivo detecte automáticamente un script de configuración automática de proxy (PAC). **Sin configurar** (valor predeterminado) habilita esta característica. cuando esta opción está habilitada, el dispositivo intenta encontrar la ruta de acceso a un script de configuración automática del proxy.
- **Usar script de proxy**: seleccione **Permitir** para especificar una ruta de acceso al script de PAC para configurar el servidor proxy. **Sin configurar** (valor predeterminado) no permite especificar la dirección URL de un script de PAC.
  - **URL del script de configuración**: escriba la URL de un script de configuración automática que quiera usar para configurar el servidor proxy.
- **Usar un servidor proxy manual**: seleccione **Permitir** para escribir manualmente el nombre o la dirección IP y el número de puerto TCP de un servidor proxy. **Sin configurar** (valor predeterminado) no permite escribir manualmente detalles de un servidor proxy.
  - **Dirección**: escriba el nombre o la dirección IP del servidor proxy.
  - **Número de puerto**: escriba el número de puerto del servidor proxy.
  - **Excepciones del proxy**: escriba las direcciones URL que no deben usar el servidor proxy. Use un punto y coma para separar cada elemento.
  - **Omitir el servidor proxy para direcciones locales**: **Sin configurar** (valor predeterminado) evita usar un servidor proxy para direcciones locales en la intranet. **Permitir** usa un servidor proxy para direcciones locales.

## <a name="password"></a>Contraseña

Estas opciones de configuración usan [DeviceLock policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) (CSP de directiva de DeviceLock), que también indica las ediciones de Windows compatibles.

- **Contraseña**: **Requerir** que el usuario final escriba una contraseña para acceder al dispositivo. **Sin configurar** (valor predeterminado) permite el acceso al dispositivo sin contraseña. Solo se aplica a las cuentas locales. Las contraseñas de las cuentas de dominio permanecen configuradas por Active Directory (AD) y Azure AD.

  - **Tipo de contraseña requerida**: elija el tipo de contraseña. Las opciones son:
    - **No configurado**: la contraseña puede incluir números y letras.
    - **Numérica**: la contraseña solo debe contener números.
    - **Alfanumérica**: la contraseña debe ser una combinación de letras y números.
  - **Longitud mínima de la contraseña**: escriba el número mínimo de caracteres o los caracteres requeridos, de 4 a 16. Por ejemplo, escriba `6` para exigir al menos seis caracteres de longitud de la contraseña.
  
    > [!IMPORTANT]
    > Cuando el requisito de contraseña se cambia a un escritorio de Windows, los usuarios se ven afectados la próxima vez que inician sesión, porque es entonces cuando el dispositivo pasa de inactivo a activo. Los usuarios con contraseñas que cumplan el requisito de todos modos tendrán que cambiarlas.
    
  - **Número de errores de inicio de sesión antes de borrar el dispositivo**: escriba el número de errores de autenticación permitidos antes de que se pueda borrar el dispositivo, hasta 11. El número válido que escriba dependerá de la edición. [DeviceLock/MAXDEVICEPASSWORDFAILEDATTEMPTS CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) enumera los valores admitidos. `0` (cero) puede deshabilitar la funcionalidad de borrado del dispositivo.

    Esta opción también tiene un impacto diferente en función de la edición. Para obtener información detallada de esta configuración, vea [DeviceLock/MaxDevicePasswordFailedAttempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) (CSP de DeviceLock/MaxDevicePasswordFailedAttempts).

  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el tiempo durante el que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.
  - **Expiración de la contraseña (días)** : especifique el periodo de tiempo en días tras el cual debe cambiarse la contraseña del dispositivo, de 1 a 365. Por ejemplo, escriba `90` para que la contraseña caduque pasados 90 días.
  - **Impedir la reutilización de contraseñas anteriores**: escriba el número de contraseñas usadas previamente que no se pueden volver a usar, de 1 a 24. Por ejemplo, escriba `5` para que los usuarios no puedan establecer una nueva contraseña en su contraseña actual o en cualquiera de sus cuatro contraseñas anteriores.
  - **Requerir contraseña cuando el dispositivo vuelve de un estado de inactividad** (Mobile y Holographic): seleccione **Requerir** para que los usuarios tengan que escribir una contraseña para desbloquear el dispositivo después de estar inactivo. **Sin configurar** (valor predeterminado) no requiere un PIN o una contraseña cuando el dispositivo se reanuda desde un estado de inactividad.
  - **Contraseñas sencillas**: establezca en **Bloquear** para que los usuarios no puedan crear contraseñas sencillas, como `1234` o `1111`. Establezca en **Sin configurar** (valor predeterminado) para permitir a los usuarios crear contraseñas como `1234` o `1111`. Esta configuración también permite o bloquea el uso de contraseñas de imagen de Windows.
- **Cifrado automático durante AADJ**: **Bloquear** evita el cifrado automático de dispositivos de BitLocker cuando el dispositivo está preparado para el primer uso y está unido a Azure AD. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Más información sobre el [cifrado de dispositivos de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [CSP Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Directiva del Estándar federal de procesamiento de información (FIPS)** : **Permitir** usa la directiva del Estándar federal de procesamiento de información (FIPS), que es un estándar del Gobierno de los Estados Unidos para el cifrado, las operaciones hash y la firma. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Es posible que el valor predeterminado del sistema operativo no use FIPS.

  [CSP Cryptography/AllowFipsAlgorithmPolicy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Autenticación de dispositivos con Windows Hello**: **Permitir** deja que los usuarios usen un dispositivo complementario Windows Hello, como un teléfono, una pulsera de actividad o un dispositivo IoT, para iniciar sesión en un equipo Windows 10. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. El valor predeterminado del sistema operativo puede impedir que los dispositivos complementarios de Windows Hello se autentiquen con Windows.

  [CSP Authentication/AllowSecondaryAuthenticationDevice](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Inicio de sesión web**: habilita la compatibilidad del inicio de sesión de Windows con proveedores federados que no sean de AD FS (Servicios de federación de Active Directory), como el Lenguaje de marcado de aserción de seguridad (SAML). SAML usa tokens seguros que proporcionan a los exploradores web una experiencia de inicio de sesión único (SSO). Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración.
  - **Habilitada**: el proveedor de credenciales web está habilitado para el inicio de sesión.
  - **Disabled**: el proveedor de credenciales web está deshabilitado para el inicio de sesión.

  [CSP Authentication/EnableWebSignIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Dominio de inquilino de Azure AD preferido**: escriba un nombre de dominio existente en la organización de Azure AD. Cuando los usuarios de este dominio inicien sesión, no tendrán que escribir el nombre de dominio. Por ejemplo, escriba `contoso.com`. Los usuarios del dominio `contoso.com` pueden iniciar sesión con su nombre de usuario, como `abby`, en lugar de `abby@contoso.com`.

  [CSP Authentication/PreferredAadTenantDomainName](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>Excepciones de privacidad para cada aplicación

Puede agregar aplicaciones que deben tener un comportamiento de privacidad diferente del definido en "Privacidad determinada".

- **Nombre del paquete**: nombre de familia de paquete de la aplicación.
- **Nombre de la aplicación**: nombre de la aplicación.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: defina si esta aplicación puede acceder al nombre de usuario, la imagen y otra información de contacto.
- **Aplicaciones en segundo plano**: defina si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: defina si esta aplicación puede acceder al calendario.
- **Historial de llamadas**: defina si esta aplicación puede acceder al historial de llamadas.
- **Cámara**: defina si esta aplicación puede acceder a la cámara.
- **Contactos**: defina si esta aplicación puede acceder a los contactos.
- **Correo electrónico**: defina si esta aplicación puede acceder al correo electrónico.
- **Ubicación**: defina si esta aplicación puede acceder a información de ubicación.
- **Mensajería**: defina si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: defina si esta aplicación puede usar el micrófono.
- **Movimiento**: defina si esta aplicación puede acceder a la información de movimiento del dispositivo.
- **Notificaciones**: defina si esta aplicación puede acceder a las notificaciones.
- **Teléfono**: defina si esta aplicación puede acceder al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos, y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: defina si esta aplicación puede acceder a las tareas.
- **Dispositivos de confianza**: elija si esta aplicación puede usar dispositivos de confianza. Es decir, hardware ya conectado o que se proporciona con el dispositivo. Por ejemplo, use televisores, proyectores, etc. como dispositivos de confianza.
- **Comentarios y diagnósticos**: defina si esta aplicación puede acceder a la información de diagnóstico.
- **Sincronizar con dispositivos**: elija si esta aplicación puede compartir y sincronizar automáticamente información con dispositivos inalámbricos que no se emparejan explícitamente con el dispositivo.

## <a name="personalization"></a>Personalization

Estas opciones de configuración usan [personalization policy CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp) (CSP de directiva de personalización), que también indica las ediciones de Windows compatibles.

- **URL de imagen de fondo de escritorio (solo equipos de escritorio)** : escriba la dirección URL de una imagen en formato .jpg, .jpeg o .png que quiera usar como fondo de escritorio de Windows. Los usuarios no pueden cambiar la imagen. Por ejemplo, escriba `https://contoso.com/logo.png`.

## <a name="printer"></a>Impresora

- **Impresoras**: lista de impresoras locales que se han agregado.
- **Impresora predeterminada**: establezca la impresora predeterminada.
- **User access to add new printers** (Acceso de usuarios para agregar nuevas impresoras): permita o bloquee el uso de las impresoras locales.

## <a name="privacy"></a>Privacidad

Estas opciones de configuración usan [privacy policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy) (CSP de directiva de privacidad), que también indica las ediciones de Windows compatibles.

- **Personalización de entrada**: **Bloquear** evita el uso de voz para dictado y que se hable a Cortana y otras aplicaciones que usan el reconocimiento de voz basado en la nube de Microsoft. Está deshabilitado y los usuarios no pueden habilitar el reconocimiento de voz en línea mediante la configuración. **Sin configurar** (valor predeterminado) permite a los usuarios elegir. Si permite estos servicios, Microsoft puede recopilar datos de voz para mejorar el servicio.
- **Aceptación automática de los mensajes de consentimiento del usuario sobre emparejamiento y privacidad**: seleccione **Permitir** para que Windows pueda aceptar automáticamente los mensajes de consentimiento de privacidad y emparejamiento al ejecutar aplicaciones. **Sin configurar** (valor predeterminado) evita la aceptación automática de la ventana de consentimiento del usuario sobre emparejamiento y privacidad al abrir aplicaciones.
- **Publicar las actividades del usuario**: **Bloquear** evita las experiencias compartidas y la detección de recursos usados recientemente en la fuente de actividades. **Sin configurar** (valor predeterminado) habilita esta característica para que las aplicaciones puedan publicar las actividades del usuario final.
- **Solo actividades locales**: si elige **Bloquear**, se impiden las experiencias compartidas y la detección de recursos usados recientemente en el conmutador de tareas, según la actividad local únicamente. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.

Puede configurar la información a la que pueden tener acceso todas las aplicaciones del dispositivo. También, puede definir excepciones para cada aplicación mediante **excepciones de privacidad de cada aplicación**.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: defina si esta aplicación puede acceder al nombre de usuario, la imagen y otra información de contacto.
- **Aplicaciones en segundo plano**: defina si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: defina si esta aplicación puede acceder al calendario.
- **Historial de llamadas**: defina si esta aplicación puede acceder al historial de llamadas.
- **Cámara**: defina si esta aplicación puede acceder a la cámara.
- **Contactos**: defina si esta aplicación puede acceder a los contactos.
- **Correo electrónico**: defina si esta aplicación puede acceder al correo electrónico.
- **Ubicación**: defina si esta aplicación puede acceder a información de ubicación.
- **Mensajería**: defina si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: defina si esta aplicación puede usar el micrófono.
- **Movimiento**: defina si esta aplicación puede acceder a la información de movimiento del dispositivo.
- **Notificaciones**: defina si esta aplicación puede acceder a las notificaciones.
- **Teléfono**: defina si esta aplicación puede acceder al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos, y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: defina si esta aplicación puede acceder a las tareas.
- **Dispositivos de confianza**: elija si esta aplicación puede usar dispositivos de confianza. Es decir, hardware ya conectado o que se proporciona con el dispositivo. Por ejemplo, use televisores, proyectores, etc. como dispositivos de confianza.
- **Comentarios y diagnósticos**: elija si esta aplicación puede acceder a la información de diagnóstico.
- **Sincronización con dispositivos**: define si esta aplicación puede compartir y sincronizar información automáticamente con dispositivos inalámbricos que no se emparejan explícitamente con este PC, tableta o teléfono.

## <a name="projection"></a>Proyección

Estas opciones de configuración usan [WirelessDisplay policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay) (CSP de directiva de WirelessDisplay), que también indica las ediciones de Windows compatibles.

- **Entrada de usuario desde receptores de pantalla inalámbricos**: **Bloquear** evita la entrada de usuario desde receptores de pantalla inalámbricos. **Sin configurar** (valor predeterminado) permite que una pantalla inalámbrica envíe entrada de teclado, mouse, lápiz y táctil de vuelta al dispositivo de origen.
- **Proyección en este equipo**: **Bloquear** evita que otros dispositivos encuentren el equipo para proyección. **Sin configurar** (valor predeterminado) permite que el dispositivo sea detectable y que se pueda proyectar a él por encima de la pantalla de bloqueo.
- **Requerir PIN para emparejamiento**: seleccione **Requerir** para solicitar siempre un PIN cuando se conecte a un dispositivo de proyección. **Sin configurar** (valor predeterminado) no requiere un PIN para emparejar el dispositivo con un dispositivo de proyección.

## <a name="reporting-and-telemetry"></a>Informes y telemetría

- **Compartir los datos de uso**: elija el nivel de datos de diagnóstico que se envía. Las opciones son:
  - **No configurado**: no se comparten datos.
  - **Seguridad**: información necesaria para ayudar a proteger Windows, incluidos datos sobre la configuración del componente Experiencia del usuario y telemetría asociadas, la Herramienta de eliminación de software malintencionado y Microsoft Defender.
  - **Básica**: información básica del dispositivo que incluye datos relacionados con la calidad, la compatibilidad de aplicaciones, datos de uso de aplicaciones y datos del nivel de seguridad.
  - **Mejorada**: información adicional que incluye: cómo se usan Windows, Windows Server, System Center y las aplicaciones, cómo funcionan, datos avanzados de confiabilidad y datos de los niveles Seguridad y Básica.
  - **Completa**: todos los datos necesarios para identificar y ayudar a solucionar problemas, además de datos de los niveles Seguridad, Básica y Mejorada.

  [System/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) (CSP de System/AllowTelemetry)

- **Send Microsoft Edge browsing data to Microsoft 365 Analytics** (Enviar los datos de exploración de Microsoft Edge a Microsoft 365 Analytics): para usar esta característica, establezca la configuración **Share usage data** (Compartir los datos de uso) en **Mejorado** o **Completo**. Esta característica controla los datos que Microsoft Edge envía a Microsoft 365 Analytics para los dispositivos empresariales que tienen configurado un identificador comercial. Las opciones son:
  - **No configurado**: Intune no cambia ni actualiza esta configuración. Es posible que el valor predeterminado del sistema operativo no envíe datos del historial de exploración.
  - **Only send intranet data** (Solo enviar datos de la intranet): se permite que el administrador envíe el historial de datos de la intranet.
  - **Only send internet data** (Solo enviar datos de Internet): se permite que el administrador envíe el historial de datos de Internet.
  - **Send intranet and internet data** (Enviar datos de la intranet e Internet): se permite que el administrador envíe el historial de datos de la intranet e Internet.

  [Browser/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics) (CSP de Browser/ConfigureTelemetryForMicrosoft365Analytics)

- **Servidor proxy de telemetría**: escriba el nombre de dominio completo (FQDN) o la dirección IP de un servidor proxy para reenviar las solicitudes de Telemetría y experiencias del usuario conectado mediante una conexión de Capa de sockets seguros (SSL). El formato de esta configuración es *servidor*:*puerto*. Si se produce un error en el proxy mencionado o si no hay ningún proxy especificado cuando esta directiva está habilitada, los datos de Telemetría y experiencias del usuario conectado no se envían y permanecen en el dispositivo local.

  Formatos de ejemplo:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy) (CSP de System/TelemetryProxy)

Haga clic en **Aceptar** para guardar los cambios.

## <a name="search"></a>Búsqueda

Estas opciones de configuración usan [search policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) (CSP de directiva de búsqueda), que también indica las ediciones de Windows compatibles. 

- **Búsqueda segura (solo móvil)** : se controla cómo Cortana filtra el contenido para adultos en los resultados de la búsqueda. Las opciones son:
  - **Definido por el usuario**: permita a los usuarios finales elegir su propia configuración.
  - **Estricto**: filtrado más alto del contenido para adultos.
  - **Moderado**: filtrado moderado del contenido para adultos. No se filtran los resultados de búsqueda válidos.
- **Mostrar los resultados de los sitios web en la búsqueda**: cuando se establece en **Bloquear**, los usuarios no pueden buscar y los resultados web no se muestran en la búsqueda. **Sin configurar** (valor predeterminado) permite a los usuarios buscar en Internet y los resultados se muestran en el dispositivo.

## <a name="start"></a>Start

Estas opciones de configuración usan [start policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start) (CSP de directiva de inicio), que también indica las ediciones de Windows compatibles.  

- **Diseño del menú Inicio**: invalide el diseño de inicio predeterminado y personalice el menú Inicio en dispositivos de escritorio. Cargue un archivo XML que incluya las personalizaciones, incluido el orden en que aparecen las aplicaciones, etc. Los usuarios no pueden cambiar el diseño del menú Inicio que especifique.
- **Anclar los sitios web a iconos del menú Inicio**: importe imágenes desde Microsoft Edge que se muestran como vínculos en el menú Inicio de Windows de los dispositivos de escritorio.
- **Desanclar aplicaciones de la barra de tareas**: **Bloquear** evita que los usuarios desanclen aplicaciones de la barra de tareas. **Sin configurar** (valor predeterminado) permite que los usuarios desanclen aplicaciones de la barra de tareas.
- **Cambio rápido de usuario**: **Bloquear** evita el cambio entre usuarios que han iniciado sesión al mismo tiempo sin cerrar la sesión. **Sin configurar** (valor predeterminado) muestra **Cambiar usuario** en el icono de usuario.
- **La mayoría de las aplicaciones usadas**: **Bloquear** oculta las aplicaciones más usadas en el menú Inicio. También deshabilita la alternancia correspondiente en la aplicación Configuración. **Sin configurar** (valor predeterminado) muestra las aplicaciones más usadas.
- **Aplicaciones agregadas recientemente**: **Bloquear** oculta las aplicaciones agregadas recientemente en el menú Inicio. También deshabilita la alternancia correspondiente en la aplicación Configuración. **Sin configurar** (valor predeterminado) muestra las aplicaciones agregadas recientemente en el menú Inicio.
- **Modo de pantalla de inicio**: elija cómo se muestra la pantalla de inicio. Las opciones son:
  - **Definido por el usuario**: no fuerza el tamaño de Inicio. Los usuarios pueden establecer el tamaño.
  - **Pantalla completa**: fuerza un tamaño de pantalla completa de Inicio.
  - **Pantalla parcial**: fuerza un tamaño de pantalla parcial de Inicio.
- **Elementos abiertos recientemente en listas de accesos directos**: **Bloquear** oculta las listas de accesos directos recientes en el menú Inicio y la barra de tareas. También deshabilita la alternancia correspondiente en la aplicación Configuración. **Sin configurar** (valor predeterminado) muestra los elementos abiertos recientemente en las listas de accesos directos.
- **Lista de aplicaciones**: elija cómo se muestran las listas de todas las aplicaciones. Las opciones son:
  - **Definido por el usuario**: no se fuerza ninguna opción. Los usuarios eligen cómo se muestra la lista de aplicaciones en el dispositivo.
  - **Contraer**: oculte la lista de todas las aplicaciones.
  - **Contraer y deshabilitar la aplicación Configuración**: oculte la lista de todas aplicaciones y deshabilite **Mostrar lista de aplicaciones en el menú Inicio** en la aplicación Configuración.
  - **Quitar y deshabilitar la aplicación Configuración**: oculte la lista de todas las aplicaciones, quite el botón de todas las aplicaciones y deshabilite **Mostrar lista de aplicaciones en el menú Inicio** en la aplicación Configuración.
- **Botón de encendido**: **Bloquear** oculta el botón de encendido en el menú Inicio. **Sin configurar** (valor predeterminado) muestra el botón de encendido.
- **Icono del usuario**: **Bloquear** oculta el icono del usuario en el menú Inicio. **Sin configurar** (valor predeterminado) muestra el icono del usuario y además establece los valores siguientes:
  - **Bloquear**: **Bloquear** oculta la opción **Bloquear** en el icono del usuario del menú Inicio. **Sin configurar** (valor predeterminado) muestra la opción **Bloquear**.
  - **Cerrar sesión**: **Bloquear** oculta la opción **Cerrar sesión** en el icono del usuario del menú Inicio. **Sin configurar** (valor predeterminado) muestra la opción **Cerrar sesión**.
- **Apagar**: **Bloquear** oculta las opciones **Actualizar y apagar** y **Apagar** en el botón de encendido del menú Inicio. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Suspender**: **Bloquear** oculta la opción **Suspender** en el botón de encendido del menú Inicio. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Hibernar**: **Bloquear** oculta la opción **Hibernar** en el botón de encendido del menú Inicio. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Cambiar cuenta**: **Bloquear** oculta la opción **Cambiar cuenta** en el icono del usuario del menú Inicio. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Opciones de reinicio**:  **Bloquear** oculta las opciones **Actualizar y reiniciar** y **Reiniciar** en el botón de encendido del menú Inicio. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
- **Documentos en Inicio**: oculte o muestre la carpeta Documentos en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.
- **Descargas en Inicio**: oculte o muestre la carpeta Descargas en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.
- **Explorador de archivos en Inicio**: oculte o muestre Explorador de archivos en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.
- **Grupo Hogar en Inicio**: oculte o muestre el acceso directo Grupo Hogar en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.
- **Música en Inicio**: oculte o muestre la carpeta Música en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.
- **Red en Inicio**: oculte o muestre Red en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.
- **Carpeta Personal en Inicio**: oculte o muestre la carpeta Personal en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.
- **Imágenes en Inicio**: oculte o muestre la carpeta de imágenes en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.
- **Configuración en Inicio**: oculte o muestre el acceso directo Configuración en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.
- **Vídeos en Inicio**: oculte o muestre la carpeta de vídeos en el menú Inicio de Windows. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se fuerza ninguna opción. Los usuarios eligen mostrar u ocultar el acceso directo.
  - **Ocultar**: el acceso directo se oculta y se deshabilita la opción en la aplicación Configuración.
  - **Mostrar**: el acceso directo se muestra y se deshabilita la opción en la aplicación Configuración.

## <a name="microsoft-defender-smart-screen"></a>Microsoft defender Smart Screen

- **SmartScreen para Microsoft Edge**: **Requerir** desactiva SmartScreen de Microsoft Defender y evita que los usuarios lo activen. **Sin configurar** (valor predeterminado) activa SmartScreen. Ayuda a proteger a los usuarios frente a amenazas potenciales y evita que lo desactiven.

  Microsoft Edge usa SmartScreen de Microsoft Defender (activado) para proteger a los usuarios de software malintencionado y posibles estafas de suplantación de identidad.

  [Browser/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) (CSP de Browser/AllowSmartScreen)

- **Acceso a sitios malintencionados**: **Bloquear** evita que los usuarios omitan las advertencias del filtro SmartScreen de Microsoft Defender y no permite que vayan al sitio. **Sin configurar** (valor predeterminado) permite a los usuarios omitir las advertencias e ir al sitio.

  [Browser/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) (CSP de Browser/PreventSmartScreenPromptOverride)

- **Descarga de archivos no comprobados**: **Bloquear** evita que los usuarios omitan las advertencias del filtro SmartScreen de Microsoft Defender y bloquea la descarga de archivos no comprobados. **Sin configurar** (valor predeterminado) permite a los usuarios omitir las advertencias y seguir descargando los archivos no comprobados.

  [Browser/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) (CSP de Browser/PreventSmartScreenPromptOverrideForFiles)

## <a name="windows-spotlight"></a>Contenido destacado de Windows

Estas opciones de configuración usan [experience policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) (CSP de directiva de experiencia), que también indica las ediciones de Windows compatibles.

- **Contenido destacado de Windows**: **Bloquear** desactiva Contenido destacado de Windows en la pantalla de bloqueo, las recomendaciones de Windows, las características de consumidor de Microsoft y otras características relacionadas. Si su objetivo es minimizar el tráfico de red desde los dispositivos, establezca esta opción en **Bloquear**. **Sin configurar** (valor predeterminado) permite las características de contenido destacado de Windows y puede ser controlado por los usuarios finales. Cuando está habilitado, también puede permitir o bloquear las siguientes opciones:

  - **Contenido destacado de Windows en la pantalla de bloqueo**: **Bloquear** evita que Contenido destacado de Windows muestre información en la pantalla de bloqueo del dispositivo. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Sugerencias de terceros en Contenido destacado de Windows**: **Bloquear** evita que Contenido destacado de Windows sugiera contenido que no haya publicado Microsoft. **Sin configurar** (valor predeterminado) permite sugerencias de contenido y aplicaciones de editores de software asociados en características de Contenido destacado de Windows, como el contenido destacado en la pantalla de bloqueo, aplicaciones sugeridas en el menú Inicio y recomendaciones de Windows.
  - **Características de consumidor**: **Bloquear** desactiva experiencias que suelen ser solo para consumidores, como las sugerencias de inicio, las notificaciones de suscripción, la instalación de aplicaciones tras la configuración rápida y los iconos de redireccionamiento. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.
  - **Sugerencias de Windows**: **Bloquear** deshabilita las recomendaciones emergentes de Windows. **Sin configurar**: (valor predeterminado) permite que se muestren las recomendaciones de Windows.
  - **Contenido destacado de Windows en el centro de actividades**: **Bloquear** evita que las notificaciones de Contenido destacado de Windows aparezcan en el centro de actividades. **Sin configurar** (valor predeterminado) puede mostrar notificaciones en el centro de actividades que sugieran aplicaciones o características para ayudar a los usuarios a ser más productivos en Windows.
  - **Personalización de Contenido destacado de Windows**: **Bloquear** evita que Windows use datos de diagnóstico para proporcionar experiencias personalizadas al usuario. **Sin configurar** (valor predeterminado) permite a Microsoft usar datos de diagnóstico para proporcionar recomendaciones y sugerencias personalizadas y ofrece personalizar Windows para las necesidades del usuario.
  - **Experiencia de bienvenida de Windows**: **Bloquear** desactiva la característica de experiencia de bienvenida de Windows de Contenido destacado de Windows. La experiencia de bienvenida de Windows no muestra si hay actualizaciones y cambios para Windows y sus aplicaciones. **Sin configurar** (valor predeterminado) permite que la experiencia de bienvenida de Windows muestre al usuario información sobre características nuevas o actualizadas.

## <a name="microsoft-defender-antivirus"></a>Antivirus de Microsoft defender

Estas opciones de configuración usan [defender policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) (CSP de directiva de Defender), que también indica las ediciones de Windows compatibles.

- **Supervisión en tiempo real**: **Habilitar** activa la detección de malware, spyware y otro tipo de software no deseado en tiempo real. Los usuarios no pueden desactivarlo. 

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo activa esta característica y permite a los usuarios cambiarla.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

- **Supervisión de comportamiento**: **Habilitar** activa la supervisión del comportamiento y comprueba determinados patrones conocidos de actividad sospechosa en los dispositivos. Los usuarios no pueden desactivar la supervisión del comportamiento. 

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo activa la supervisión del comportamiento y permite a los usuarios cambiarla.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)

- **Sistema de inspección de red (NIS)** : NIS ayuda a proteger los dispositivos contra las vulnerabilidades de seguridad basadas en red. Usa las firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para ayudar a detectar y bloquear el tráfico malintencionado.

  **Habilitar** activa la protección de red y el bloqueo de red. Los usuarios no pueden desactivarlo. Cuando está habilitada, los usuarios no pueden conectarse a vulnerabilidades conocidas.

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo activa NIS y permite a los usuarios cambiarlo.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

- **Examinar todas las descargas**: **habilita** activar esta opción y defender examina todos los archivos descargados de Internet. Los usuarios no pueden desactivar esta opción. 

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo activa esta configuración y permite a los usuarios cambiarla.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)

- **Examinar scripts cargados en exploradores web de Microsoft**: **Habilitar** permite que Defender analice los scripts que se usan en Internet Explorer. Los usuarios no pueden desactivar esta opción. 

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo activa esta configuración y permite a los usuarios cambiarla.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)

- **Acceso de usuario final a Defender**: **Bloquear** oculta la interfaz de usuario de Microsoft Defender a los usuarios finales. También se suprimen todas las notificaciones de Microsoft Defender.

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si bloquea la configuración y, a continuación, la vuelve a cambiar a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo permite el acceso de los usuarios a la interfaz de usuario de Microsoft defender y permite a los usuarios cambiarla.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario final.

  [CSP de defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess)

- **Intervalo de actualización de inteligencia de seguridad (en horas)** : especifique el intervalo en el que defender comprueba la nueva inteligencia de seguridad, en 0-24. Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración. El valor predeterminado del sistema operativo puede comprobar si hay actualizaciones cada 8 horas.
  - **No comprobar**: defender no busca nuevas actualizaciones de inteligencia de seguridad.
  - **1-24**: `1` busca cada hora, `2` busca cada dos horas, `24` busca cada día, etc.
  
  [CSP de defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)
  
- **Supervisar la actividad de archivos y programas**: Permite que Defender supervise la actividad de archivos y programas en los dispositivos. Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración. El valor predeterminado del sistema operativo puede supervisar todos los archivos.
  - **Supervisión deshabilitada**
  - **Supervisar todos los archivos**
  - **Supervisar solo los archivos entrantes**
  - **Supervisar solo los archivos salientes**

  [CSP de defender/RealTimeScanDirection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)

- **Días antes de eliminar el malware en cuarentena**: siga realizando el seguimiento de malware resuelto durante el número de días especificado para poder comprobar de forma manual los dispositivos previamente afectados. Si establece el número de días en `0`, el malware permanece en la carpeta de cuarentena y no se quita automáticamente. Cuando se establece en `90`, los elementos en cuarentena se almacenan durante 90 días en el sistema y luego se eliminan.

  [CSP de defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware)

- **Límite de uso de la CPU durante un examen**: limite la cantidad de CPU que pueden usar los exámenes, de `0` a `100`.
- **Examinar archivos de almacenamiento**: **habilita activar** defender para que examine archivos de almacenamiento, como archivos zip o CAB. Los usuarios no pueden desactivar esta opción.

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo activa este análisis y permite a los usuarios cambiarlo.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)

- **Examinar mensajes de correo entrante**: **Habilitar** permite que Defender examine los mensajes de correo electrónico en cuanto llegan al dispositivo. Cuando está habilitada, el motor analiza el buzón y los archivos de correo para analizar el cuerpo del correo y los datos adjuntos. Puede examinar los formatos. pst (Outlook),. dbx,. MBX, MIME (Outlook Express) y BinHex (Mac).

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo desactiva este análisis y permite a los usuarios cambiarlo.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning)

- **Examinar unidades extraíbles durante un examen completo**: **habilita la activación** de los exámenes de unidades extraíbles de defender durante un examen completo. Los usuarios no pueden desactivar esta opción.

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo permite que defender examine unidades extraíbles, como sticks USB, y permite a los usuarios cambiar esta configuración.

  Durante un examen rápido, es posible que se sigan analizando las unidades extraíbles.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)

- **Examinar unidades de red asignadas durante un examen completo**: **Habilitar** permite que Defender examine archivos en unidades de red asignadas. Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos. Los usuarios no pueden desactivar esta opción.

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo activa esta característica y permite a los usuarios cambiarla.

  Durante un examen rápido, es posible que se sigan analizando las unidades de red asignadas.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives)

- **Examinar archivos abiertos desde carpetas de red**: **Habilitar** with defender examina archivos abiertos desde carpetas de red o unidades de red compartidas, como los archivos a los que se accede desde una ruta de acceso UNC. Los usuarios no pueden desactivar esta opción. Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos.

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo examina los archivos abiertos desde carpetas de red y permite a los usuarios cambiarlos.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles)

- **Protección de la nube**: **Habilitar** permite que Microsoft Active Protection Service reciba información relativa a la actividad de malware de los dispositivos que administra. Los usuarios no pueden cambiar esta configuración. 

  Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración. Si habilita la opción y, a continuación, vuelve a cambiarla a **no configurado**, Intune deja la configuración en su estado configurado previamente. De forma predeterminada, el sistema operativo permite al Microsoft Active Protection Service recibir información y permite a los usuarios cambiar esta configuración.

  Intune no desactiva esta característica. Para deshabilitarlo, use un URI personalizado.

  [CSP de defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)

- **Preguntar a los usuarios antes de enviar muestras**: se controla si los archivos potencialmente malintencionados que podrían requerir un análisis en mayor profundidad se envían automáticamente a Microsoft. Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración. El valor predeterminado del sistema operativo puede enviar muestras seguras automáticamente.
  - **Preguntar siempre**
  - **Preguntar antes de enviar datos personales**
  - **No enviar datos nunca**
  - **Enviar todos los datos sin preguntar**: los datos se envían automáticamente.

  [CSP de defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent)

- **Hora a la que se realizará un examen rápido diario**: elija la hora a la que se va a ejecutar un examen rápido diario. **No configurado**: no se ejecuta ningún examen diario. Si quiere personalizar más esta opción, configure el valor **Tipo de examen del sistema para realizar**.

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- **Tipo de examen del sistema para realizar**: programe un examen del sistema, incluido el nivel de examen, así como el día y la hora en que se va a ejecutar el examen. Las opciones son:
  - **No configurado**: no se programa ningún examen del sistema en el dispositivo. Los usuarios finales pueden ejecutar exámenes manualmente según necesiten o quieran en sus dispositivos.
  - **Deshabilitar**: deshabilita cualquier examen del sistema en el dispositivo. Elija esta opción si usa una solución antivirus de un asociado que examina los dispositivos.
  - **Examen rápido**: examina ubicaciones comunes donde podría haber malware registrado, como las claves del Registro y las carpetas de inicio de Windows conocidas.
    - **Día programado**: elija el día en el que se va a ejecutar el examen.
    - **Hora programada**: elija la hora a la que se va a ejecutar el examen.
  - **Examen completo**: examina ubicaciones comunes donde podría haber malware registrado y también examina todos los archivos y las carpetas del dispositivo.
    - **Día programado**: elija el día en el que se va a ejecutar el examen.
    - **Hora programada**: elija la hora a la que se va a ejecutar el examen.

  > [!TIP]
  > Esta configuración podría entrar en conflicto con la configuración **Hora a la que se realizará un examen rápido diario**. Algunas recomendaciones:  
  >
  > - Si desea programar un examen rápido diario y un examen completo semanal, haga lo siguiente:
  >   1. Configure el **tiempo para realizar una configuración de examen rápido diaria** .
  >   2. Configure el **tipo de examen del sistema para realizar** un examen completo.
  > 
  > - Si solo desea un examen rápido diario (sin examen completo), use cualquiera de estas opciones: **Time (tiempo) para realizar un examen rápido diario** o el **tipo de examen del sistema que se va a realizar**. Por ejemplo, para ejecutar un examen rápido todos los martes a las 6:00, configure el valor **Tipo de examen del sistema para realizar**.
  > 
  > - No configure el valor **Hora a la que se realizará un examen rápido diario** simultáneamente con **Tipo de examen del sistema para realizar** establecido en **Examen rápido**. Esta configuración podría entrar en conflicto y puede que no se ejecute un examen.

  [CSP Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [CSP Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [CSP Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Detectar aplicaciones potencialmente no deseadas**: elija el nivel de protección cuando Windows detecte aplicaciones potencialmente no deseadas. Las opciones son:
  - **Sin configurar** (valor predeterminado): la protección de Microsoft Defender frente a aplicaciones potencialmente no deseadas está deshabilitada.
  - **Bloquear**: Microsoft Defender detecta aplicaciones potencialmente no deseadas y los elementos detectados se bloquean. Estos elementos se muestran en el historial junto con otras amenazas.
  - **Auditar**: Microsoft Defender detecta aplicaciones potencialmente no deseadas pero no toma ninguna medida. Puede revisar la información sobre las aplicaciones contra las que Microsoft Defender tomaría medidas. Por ejemplo, busque eventos creados por Microsoft Defender en el Visor de eventos.

  Para obtener más información sobre aplicaciones potencialmente no deseadas, vea [Detectar y bloquear aplicaciones potencialmente no deseadas](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).

  [CSP de defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

- **Consentimiento**de los ejemplos de envío: Actualmente, esta configuración no tiene ningún impacto. No use esta configuración. Puede quitarse en una versión futura.

- **Acciones sobre amenazas de malware detectadas**: elija cómo desea controlar los subprocesos de malware. **No configurado** (valor predeterminado) permite a Microsoft defender elegir la mejor opción. Cuando se establece en **Habilitar**, seleccione las acciones que quiere que Defender realice para cada nivel de amenaza que detecte (bajo, moderado, alto y grave). Las opciones son:
  
  - **Limpiar**
  - **Cuarentena**
  - **Quitar**
  - **Permitir**
  - **Definido por el usuario**
  - **Bloquear**

  Si la acción no es posible, Microsoft defender elige la mejor opción para garantizar que se corrija la amenaza. 

  [CSP de defender/ThreatSeverityDefaultAction](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-threatseveritydefaultaction)

### <a name="microsoft-defender-antivirus-exclusions"></a>Exclusiones del antivirus de Microsoft Defender

- **Archivos y carpetas para excluir de exámenes y protección en tiempo real**: Agrega uno o varios archivos y carpetas como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluyen en ningún examen en tiempo real ni programado.
- **Extensiones de archivo para excluir de exámenes y protección en tiempo real**: Agrega una o varias extensiones de archivo como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluyen en los exámenes en tiempo real ni programados.
- **Procesos para excluir de exámenes y protección en tiempo real**: Agrega uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluyen en los exámenes en tiempo real ni programados.

## <a name="power-settings"></a>Configuración de energía

### <a name="battery"></a>Batería

- **Nivel de batería para activar el ahorro de energía**: cuando el dispositivo usa la energía de la batería, escriba el nivel de carga de la batería para activar el ahorro de energía de 0-100. Escriba un valor de porcentaje que indique el nivel de carga de la batería. El valor predeterminado es 70 %. Cuando se establece en 70%, el ahorro de energía se activa cuando la batería tiene un cargo del 70% o menos disponible.

  [CSP de Power/EnergySaverBatteryThresholdOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-energysaverbatterythresholdonbattery)

- **Cierre de la tapa (solo móvil)** : cuando el dispositivo usa la energía de la batería, elija lo que sucederá cuando se cierre la tapa. Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración.
  - **Ninguna acción**: el dispositivo permanece encendido y continúa usando la energía de la batería.
  - **Suspensión**: el dispositivo entra en modo de suspensión y utiliza una pequeña cantidad de carga de la batería. El equipo todavía está encendido, y las aplicaciones y los archivos abiertos se almacenan en la memoria de acceso aleatorio (RAM).
  - **Hibernación**: el dispositivo entra en modo de hibernación. Las aplicaciones y los archivos abiertos se almacenan en el disco duro y el dispositivo se apaga.
  - **Shutdown**: el dispositivo se apaga. Las aplicaciones y los archivos abiertos se cierran sin guardarlos.

  [CSP de Power/SelectLidCloseActionOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectlidcloseactiononbattery)

- **Botón de encendido**: cuando el dispositivo usa la energía de la batería, elija lo que ocurre cuando se selecciona el botón de encendido. Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración.
  - **Ninguna acción**: el dispositivo permanece encendido y continúa usando la energía de la batería.
  - **Suspensión**: el dispositivo entra en modo de suspensión y utiliza una pequeña cantidad de carga de la batería. El equipo todavía está encendido, y las aplicaciones y los archivos abiertos se almacenan en la memoria de acceso aleatorio (RAM).
  - **Hibernación**: el dispositivo entra en modo de hibernación. Las aplicaciones y los archivos abiertos se almacenan en el disco duro y el dispositivo se apaga.
  - **Shutdown**: el dispositivo se apaga. Las aplicaciones y los archivos abiertos se cierran sin guardarlos.

  [CSP de Power/SelectPowerButtonActionOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectpowerbuttonactiononbattery)

- **Botón de suspensión**: cuando el dispositivo usa la energía de la batería, elija lo que ocurre cuando se selecciona el botón de suspensión. Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración.
  - **Ninguna acción**: el dispositivo permanece encendido y continúa usando la energía de la batería.
  - **Suspensión**: el dispositivo entra en modo de suspensión y utiliza una pequeña cantidad de carga de la batería. El equipo todavía está encendido, y las aplicaciones y los archivos abiertos se almacenan en la memoria de acceso aleatorio (RAM).
  - **Hibernación**: el dispositivo entra en modo de hibernación. Las aplicaciones y los archivos abiertos se almacenan en el disco duro y el dispositivo se apaga.
  - **Shutdown**: el dispositivo se apaga. Las aplicaciones y los archivos abiertos se cierran sin guardarlos.

  [CSP de Power/SelectSleepButtonActionOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectsleepbuttonactiononbattery)

- **Suspensión híbrida**: cuando el dispositivo usa la energía de la batería, la **deshabilitación** impide que el dispositivo entre en modo de suspensión híbrida. En el modo de suspensión híbrida, las aplicaciones y los archivos abiertos se almacenan en la memoria de acceso aleatorio (RAM) y en el disco duro. Utiliza una pequeña cantidad de carga de la batería. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.

  [CSP de Power/TurnOffHybridSleepOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-turnoffhybridsleeponbattery)

### <a name="pluggedin"></a>PluggedIn

- **Nivel de batería para activar el ahorro de energía**: cuando el dispositivo está conectado, escriba el nivel de carga de la batería para activar el ahorro de energía de 0-100. Escriba un valor de porcentaje que indique el nivel de carga de la batería. El valor predeterminado es 70 %. Cuando se establece en 70%, el ahorro de energía se activa cuando la batería tiene un cargo del 70% o menos disponible.

  [CSP de Power/EnergySaverBatteryThresholdPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-energysaverbatterythresholdpluggedin)

- **Cierre de la tapa (solo móvil)** : cuando el dispositivo está conectado, elija lo que ocurre cuando se cierra la tapa. Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración.
  - **Ninguna acción**: el dispositivo permanece encendido.
  - **Suspensión**: el dispositivo entra en modo de suspensión. El equipo todavía está encendido, y las aplicaciones y los archivos abiertos se almacenan en la memoria de acceso aleatorio (RAM).
  - **Hibernación**: el dispositivo entra en modo de hibernación. Las aplicaciones y los archivos abiertos se almacenan en el disco duro y el dispositivo se apaga.
  - **Shutdown**: el dispositivo se apaga. Las aplicaciones y los archivos abiertos se cierran sin guardarlos.
  
    [CSP de Power/SelectLidCloseActionPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectlidcloseactionpluggedin)
  
- **Botón de encendido**: cuando el dispositivo está conectado, elija lo que ocurre cuando se selecciona el botón de encendido. Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración.
  - **Ninguna acción**: el dispositivo permanece encendido.
  - **Suspensión**: el dispositivo entra en modo de suspensión. El equipo todavía está encendido, y las aplicaciones y los archivos abiertos se almacenan en la memoria de acceso aleatorio (RAM).
  - **Hibernación**: el dispositivo entra en modo de hibernación. Las aplicaciones y los archivos abiertos se almacenan en el disco duro y el dispositivo se apaga.
  - **Shutdown**: el dispositivo se apaga. Las aplicaciones y los archivos abiertos se cierran sin guardarlos.

  [CSP de Power/SelectPowerButtonActionPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectpowerbuttonactionpluggedin)

- **Botón de suspensión**: cuando el dispositivo está conectado, elija lo que ocurre cuando se selecciona el botón de suspensión. Las opciones son:

  - **No configurado** (valor predeterminado): Intune no cambia ni actualiza esta configuración.
  - **Ninguna acción**: el dispositivo permanece encendido.
  - **Suspensión**: el dispositivo entra en modo de suspensión. El equipo todavía está encendido, y las aplicaciones y los archivos abiertos se almacenan en la memoria de acceso aleatorio (RAM).
  - **Hibernación**: el dispositivo entra en modo de hibernación. Las aplicaciones y los archivos abiertos se almacenan en el disco duro y el dispositivo se apaga.
  - **Shutdown**: el dispositivo se apaga. Las aplicaciones y los archivos abiertos se cierran sin guardarlos.

  [CSP de Power/SelectSleepButtonActionPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectsleepbuttonactionpluggedin)

- **Suspensión híbrida**: cuando el dispositivo está conectado, la **deshabilitación** impide que el dispositivo entre en modo de suspensión híbrida. En el modo de suspensión híbrida, las aplicaciones y los archivos abiertos se almacenan en la memoria de acceso aleatorio (RAM) y en el disco duro. Cuando se establece en **no configurado** (valor predeterminado), Intune no cambia ni actualiza esta configuración.

  [CSP de Power/TurnOffHybridSleepPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-turnoffhybridsleeppluggedin)

## <a name="next-steps"></a>Pasos siguientes

Para obtener detalles técnicos adicionales sobre cada configuración y sobre las ediciones de Windows compatibles, consulte [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Referencia sobre el CSP de directivas de Windows 10).
