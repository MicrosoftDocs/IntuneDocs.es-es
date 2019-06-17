---
title: Configuración de líneas de base de seguridad de Intune para Windows 10
titleSuffix: Microsoft Intune
description: Configuración de líneas de base de seguridad de Intune para administrar Windows 10
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 82fa4fc7f9e60dff3c08adf3281351cbfa8eb743
ms.sourcegitcommit: cb76efd3db60a422a65478ebce83d3aea7b5eeed
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66749926"
---
# <a name="windows-security-baseline-settings-for-intune"></a>Configuración de líneas de base de seguridad de Windows para Intune  

Vea la [configuración de línea de base de seguridad de Windows](security-baselines.md) admitida por Microsoft Intune. Los valores predeterminados de línea de base de Windows representan la configuración recomendada para Windows y podrían no coincidir con los valores predeterminados de otras líneas de base de seguridad.  

> [!NOTE]  
> La configuración de línea de base de seguridad de Windows está en **versión preliminar**. En la versión preliminar, la lista de valores de configuración disponibles, y el orden en el que este contenido presenta esos valores, variará según lo que esté disponible en el portal.  
>  
> Cuando la configuración de línea de base está fuera de la versión preliminar, este contenido se actualiza con la lista de valores de configuración de línea de base de seguridad que no es versión preliminar que sea compatible con Intune.  

## <a name="above-lock"></a>Above Lock (Por encima de la pantalla de bloqueo)  
Para más información, vea [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) (CSP de directiva: AboveLock) en la documentación de Windows.  

- **Block display of toast notifications** (Bloquear la presentación de notificaciones del sistema)  
  Esta configuración de directiva permite impedir que aparezcan notificaciones de aplicaciones en la pantalla de bloqueo. Si habilita esta configuración de directiva, no se mostrará ninguna notificación de aplicación en la pantalla de bloqueo. Si deshabilita o no establece esta configuración de directiva, los usuarios podrán elegir qué notificaciones de aplicaciones se mostrarán en la pantalla de bloqueo.
  
  **Valor predeterminado**: Sí  

## <a name="app-runtime"></a>Tiempo de ejecución de la aplicación    
Para más información, vea [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) (CSP de directiva: AppRuntime) en la documentación de Windows.  

- **Microsoft accounts optional for Windows Store apps** (Cuentas de Microsoft opcionales para las aplicaciones de Microsoft Store)  
  Esta configuración de directiva permite definir si las cuentas de Microsoft son opcionales para las aplicaciones de Microsoft Store que requieren una cuenta para iniciar sesión. Esta directiva solo afecta a las aplicaciones de Microsoft Store que la admiten. Si habilita esta configuración de directiva, las aplicaciones de Microsoft Store que normalmente requieren una cuenta de Microsoft para iniciar sesión permitirán a los usuarios iniciar sesión con una cuenta empresarial. Si deshabilita o no establece esta configuración de directiva, los usuarios tendrán que iniciar sesión con una cuenta de Microsoft.  
  
  **Valor predeterminado**: Habilitado  

## <a name="application-management"></a>Administración de aplicaciones   
Para más información, vea [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) (CSP de directiva: ApplicationManagement) en la documentación de Windows.  

- **Block game DVR (desktop only)** (Bloquear Game DVR (solo escritorio))  
  configura si se permite la grabación y difusión de los juegos.
  
  **Valor predeterminado**: Sí  

## <a name="auto-play"></a>Reproducción automática   
Para más información, vea [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) (CSP de directiva: Autoplay) en la documentación de Windows.  

- **Auto play default auto run behavior** (Comportamiento predeterminado de ejecución automática de la reproducción automática)  
  Esta configuración afecta al comportamiento predeterminado de los comandos de ejecución automática. Los comandos de ejecución automática se almacenan en archivos autorun.inf y pueden iniciar programas de instalación u otras rutinas. Cuando el valor es *Habilitada*, los administradores pueden cambiar el comportamiento de ejecución automática predeterminado en un dispositivo que ejecute Windows Vista o versiones posteriores. El comportamiento se puede establecer en: a) Deshabilitar completamente los comandos de ejecución automática, o bien en b) Volver al comportamiento anterior a Windows Vista de ejecutar automáticamente el comando de ejecución automática. Si se establece en *Deshabilitada* o *No configurada*, los dispositivos que ejecutan Windows Vista o versiones posteriores preguntarán al usuario si se debe ejecutar el comando de ejecución automática.
  
  **Valor predeterminado**: No ejecutar  
  
- **Modo de reproducción automática**  
  Esta configuración de directiva permite desactivar la característica Reproducción automática. Reproducción automática comienza a leer desde una unidad de disco en cuanto se inserta un medio en la unidad. Como resultado, el archivo de instalación de programas y la música en medios de audio se inician inmediatamente. Antes de Windows XP SP2, Reproducción automática estaba deshabilitada de forma predeterminada en unidades extraíbles, como la unidad de disco (pero no la unidad de CD-ROM) y en unidades de red. A partir de Windows XP SP2, Reproducción automática también está habilitada para las unidades extraíbles, como unidades Zip y algunos dispositivos de almacenamiento USB. Si habilita esta configuración de directiva, se deshabilita la característica Reproducción automática en unidades de CD-ROM y unidades de medios extraíbles, o bien en todas las unidades. Esta configuración de directiva deshabilita Reproducción automática en otros tipos de unidades. No puede usar esta opción para habilitar Reproducción automática en unidades en las que esta característica está deshabilitada de forma predeterminada. Si deshabilita o no establece esta configuración de directiva, se habilitará la característica Reproducción automática. Nota: Esta configuración de directiva aparece en las carpetas Configuración del equipo y Configuración de usuario. Si las configuraciones de directivas entran en conflicto, la configuración de directiva de Configuración del equipo tiene prioridad sobre la de Configuración de usuario.
  
  **Valor predeterminado**: Deshabilitado

- **Block auto play for non-volume devices** (Bloquear la reproducción automática para los dispositivos que no son volúmenes)  
  Esta configuración de directiva deshabilita la Reproducción automática para dispositivos MTP como cámaras o teléfonos. Si habilita esta configuración de directiva, Reproducción automática no se habilitará para dispositivos MTP como cámaras o teléfonos. Si deshabilita o no establece esta configuración de directiva, Reproducción automática se habilitará para dispositivos que no son de volumen.
  
  **Valor predeterminado**: Habilitado  

## <a name="bitlocker"></a>BitLocker    
Para más información, vea [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) (CSP de directiva: Bitlocker) en la documentación de Windows.  

- **Bit locker removable drive policy** (Directiva de unidad extraíble de BitLocker)  
  Esta configuración de directiva se usa para controlar el método y la intensidad del cifrado. Los valores de esta directiva determinan la intensidad del cifrado que BitLocker usa para el cifrado. A las empresas les interesa controlar el nivel de cifrado para mejorar la seguridad (AES-256 es más seguro que AES-128). Si habilita esta directiva, podrá configurar un algoritmo de cifrado y la intensidad de cifrado de clave para unidades de datos fijas, unidades del sistema operativo y unidades de datos extraíbles de manera individual. Para unidades del sistema operativo y unidades fijas, se recomienda usar el algoritmo XTS-AES. Para unidades extraíbles, debe usar el cifrado AES-CBC de 128 bits o AES-CBC de 256 bits si la unidad se usa en otros dispositivos que no ejecuten Windows 10 (versión 1511 o posterior). El cambio del método de cifrado no tendrá ningún efecto si la unidad ya está cifrada o si el cifrado está en curso. En estos casos, se omite esta configuración de directiva.

  Para la directiva de la unidad extraíble de BitLocker, configure las siguientes opciones:

    - **Require encryption for write access** (Requerir cifrado para el acceso de escritura)  
      **Valor predeterminado**: Sí  
  
    - **Método de cifrado**  
      **Valor predeterminado**: AES CBC de 256 bits  

- **Bit locker fixed drive policy** (Directiva de unidad fija de BitLocker)  
  Esta configuración de directiva se usa para controlar el método y la intensidad del cifrado. Los valores de esta directiva determinan la intensidad del cifrado que BitLocker usa para el cifrado. A las empresas les interesa controlar el nivel de cifrado para mejorar la seguridad (AES-256 es más seguro que AES-128). Si habilita esta directiva, puede configurar un algoritmo de cifrado y la intensidad de cifrado de clave para unidades de datos fijas, unidades del sistema operativo y unidades de datos extraíbles de manera individual. Para unidades del sistema operativo y unidades fijas, se recomienda usar el algoritmo XTS-AES. Para unidades extraíbles, debe usar el cifrado AES-CBC de 128 bits o AES-CBC de 256 bits si la unidad se usa en otros dispositivos que no ejecuten Windows 10 (versión 1511 o posterior). El cambio del método de cifrado no tendrá ningún efecto si la unidad ya está cifrada o si el cifrado está en curso. En estos casos, se omite esta configuración de directiva.  
 
   Para la directiva de la unidad fija de BitLocker, configure las siguientes opciones: 
   - **Método de cifrado**
     **Predeterminado**: XTS AES de 256 bits  

- **Bit locker system drive policy** (Directiva de unidad del sistema de BitLocker)  
  Esta configuración de directiva se usa para controlar el método y la intensidad del cifrado. Los valores de esta directiva determinan la intensidad del cifrado que BitLocker usa para el cifrado. A las empresas les interesa controlar el nivel de cifrado para mejorar la seguridad (AES-256 es más seguro que AES-128). Si habilita esta directiva, puede configurar un algoritmo de cifrado y la intensidad de cifrado de clave para unidades de datos fijas, unidades del sistema operativo y unidades de datos extraíbles de manera individual. Para unidades del sistema operativo y unidades fijas, se recomienda usar el algoritmo XTS-AES. Para unidades extraíbles, debe usar el cifrado AES-CBC de 128 bits o AES-CBC de 256 bits si la unidad se usa en otros dispositivos que no ejecuten Windows 10 (versión 1511 o posterior). El cambio del método de cifrado no tendrá ningún efecto si la unidad ya está cifrada o si el cifrado está en curso. En estos casos, se omite esta configuración de directiva.  

   Para la directiva de la unidad del sistema de BitLocker, configure las siguientes opciones:
  - **Método de cifrado**  
    **Valor predeterminado**: AES XTS de 256 bits  

## <a name="browser"></a>Explorador  
Para más información, vea [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) (CSP de directiva: Browser) en la documentación de Windows.  

- **Require SmartScreen for Microsoft Edge** (Requerir SmartScreen para Microsoft Edge)  
  Microsoft Edge usa SmartScreen de Windows Defender (activado) para proteger a los usuarios de software malintencionado y posibles estafas de suplantación de identidad de forma predeterminada. Además, de forma predeterminada, los usuarios no pueden deshabilitar (desactivar) SmartScreen de Windows Defender. Si habilita esta directiva se desactiva SmartScreen de Windows Defender y se impide que los usuarios lo activen. No configure esta directiva para permitir que los usuarios puedan elegir activar o desactivar SmartScreen de Windows Defender.  
  
  **Valor predeterminado**: Sí  
  
- **Block malicious site access** (Bloquear el acceso a sitios malintencionados)  
  De forma predeterminada, Microsoft Edge permite a los usuarios omitir las advertencias de SmartScreen de Windows Defender sobre sitios potencialmente malintencionados, lo que les permite continuar al sitio. Pero con esta directiva puede configurar Microsoft Edge para evitar que los usuarios omitan las advertencias, e impedir que continúen al sitio.
  
  **Valor predeterminado**: Sí  
  
- **Block unverified file download** (Bloquear la descarga de archivos no comprobados) De forma predeterminada, Microsoft Edge permite a los usuarios omitir las advertencias de SmartScreen de Windows Defender sobre archivos potencialmente malintencionados, lo que les permite continuar con la descarga de los archivos no comprobados. Al habilitar esta directiva se impide que los usuarios omitan las advertencias, y se les impide que descarguen los archivos no comprobados.
  
  **Valor predeterminado**: Sí  
  
- **Block Password Manager** (Bloquear el administrador de contraseñas)  
  De forma predeterminada, Microsoft Edge usa el Administrador de contraseñas automáticamente, lo que permite a los usuarios administrar las contraseñas de forma local. Si deshabilita esta directiva, se impide que Microsoft Edge use el Administrador de contraseñas. No configure esta directiva si quiere permitir que los usuarios elijan guardar y administrar las contraseñas localmente mediante el Administrador de contraseñas.
  
  **Valor predeterminado**: Sí  
  
- **Prevent certificate error overrides** (Evitar las invalidaciones de error de certificado)  
  Esta configuración de directiva impide que el usuario ignore errores de certificado de Capa de sockets seguros/Seguridad de la capa de transporte (SSL/TLS) que interrumpan la navegación (errores como caducado, revocado o de coincidencia de los nombres) en Internet Explorer. Si habilita esta configuración de directiva, el usuario no puede continuar la exploración. Si deshabilita o no establece esta configuración de directiva, el usuario puede elegir ignorar los errores de certificado y continuar la exploración.
  
  **Valor predeterminado**: Sí  

## <a name="connectivity"></a>Conectividad  
Para más información, vea [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) (CSP de directiva: Connectivity) en la documentación de Windows.  

- **Block Internet download for web publishing and online ordering wizards** (Bloquear la descarga de Internet para los asistentes para publicación y pedidos en línea)  
  Esta configuración de directiva especifica si Windows debe descargar una lista de proveedores para los asistentes de publicación en web y pedidos en línea. Estos asistentes permiten que los usuarios seleccionen de una lista de compañías que proporcionan servicios, como almacenamiento en línea e impresión fotográfica. De manera predeterminada, Windows mostrará los proveedores descargados de un sitio web de Windows, además de los proveedores especificados en el Registro. Si habilita esta configuración de directiva, Windows no descargará ningún proveedor y solo se mostrarán los proveedores de servicios almacenados en la memoria caché en el Registro local. Si deshabilita o no establece esta configuración de directiva, se descarga una lista de proveedores cuando el usuario usa los asistentes de publicación en web y pedidos en línea. Vea la documentación sobre los asistentes mencionados para obtener más información, incluidos detalles sobre cómo especificar proveedores de servicios en el Registro.  
  
  **Valor predeterminado**: Habilitado  

- **Block downloading of print drivers over HTTP** (Bloquear la descarga de controladores de impresión a través de HTTP)  
  Esta configuración de directiva especifica si se permite que este cliente descargue paquetes de controladores de impresión a través de HTTP. Para configurar la impresión HTTP, los controladores que no vienen incluidos necesitan descargarse a través de HTTP. Nota: Esta configuración de directiva no impide que el cliente imprima en impresoras en la intranet o Internet a través de HTTP. Solo impide que se descarguen controladores no instalados localmente. Si habilita esta configuración de directiva, no se podrán descargar controladores de impresión a través de HTTP. Si deshabilita o no establece esta configuración de directiva, los usuarios podrán descargar controladores de impresión a través de HTTP.
  
  **Valor predeterminado**: Habilitado  

## <a name="credentials-delegation"></a>Delegación de credenciales  
Para más información, vea [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) (CSP de directiva: CredentialsDelegation) en la documentación de Windows.  

- **Remote host delegation of non-exportable credentials** (Delegación de credenciales no exportables del host remoto)  
  El host remoto permite la delegación de credenciales no exportables. Cuando se usa la delegación de credenciales, los dispositivos proporcionan una versión exportable de credenciales para el host remoto, que expone a los usuarios al riesgo de robo de credenciales por parte de los atacantes en el host remoto. Si habilita esta configuración de directiva, el host admite el modo de administración restringida y el modo Credential Guard remoto. Si deshabilita o no establece esta configuración de directiva, no se admitirán el modo de administración restringida ni el modo Credential Guard remoto. El usuario siempre tendrá que pasar sus credenciales al host.  

  
  **Valor predeterminado**: Habilitado  

## <a name="credentials-ui"></a>Interfaz de usuario de credenciales  
Para más información, vea [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) (CSP de directiva: CredentialsUI) en la documentación de Windows.  

- **Enumerate administrators** (Enumerar administradores) Esta configuración de directiva controla si se muestran las cuentas de administrador cuando un usuario intenta elevar una aplicación en ejecución. De forma predeterminada, cuando un usuario intenta elevar una aplicación en ejecución no se muestran las cuentas de administrador. Si habilita esta configuración de directiva, se muestran todas las cuentas de administrador local en el equipo para que el usuario pueda elegir una y escribir la contraseña adecuada. Si deshabilita esta configuración de directiva, los usuarios siempre deberán escribir un nombre de usuario y una contraseña para realizar la elevación.  

  
  **Valor predeterminado**: Deshabilitado  

## <a name="data-protection"></a>Protección de datos  
Para más información, vea [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) (CSP de directiva: DataProtection) en la documentación de Windows.  

- **Block direct memory access** (Bloquear el acceso directo a memoria)  
  Esta configuración de directiva permite bloquear el acceso directo a memoria (DMA) para todos los puertos de bajada PCI de conexión instantánea hasta que un usuario inicie sesión en Windows. Una vez que un usuario inicie sesión, Windows mostrará los dispositivos PCI conectados a los puertos PCI de conexión instantánea. Cada vez que el usuario bloquee el equipo, DMA se bloquea en los puertos PCI de conexión instantánea sin dispositivos secundarios, hasta que el usuario inicie sesión de nuevo. Los dispositivos que ya aparecían cuando se desbloqueó el equipo seguirán funcionando hasta que se desconecten. Esta configuración de directiva solo se aplica cuando está habilitado BitLocker o el cifrado de dispositivos.
  
  
  **Valor predeterminado**: Sí  

## <a name="device-guard"></a>Device Guard  
Para más información, vea [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) (CSP de directiva: DeviceGuard) en la documentación de Windows.  

- **Credential Guard**  
  Esta opción permite a los usuarios activar Credential Guard con seguridad basada en la virtualización para ayudar a proteger las credenciales la próxima vez que se reinicie.
   
  **Valor predeterminado**: Habilitar con bloqueo UEFI 

- **Enable virtualization based security** (Habilitar la seguridad basada en la virtualización)  </br>
  Activa la seguridad basada en la virtualización (VBS) la próxima vez que se reinicie. La seguridad basada en la virtualización usa el hipervisor de Windows para proporcionar compatibilidad con los servicios de seguridad.
  
  **Valor predeterminado**: Sí  

<!-- not yet available 
- **Enable secure boot with DMA**  
  Among the commands that follow, you can choose settings for Secure Boot and Secure Boot with DMA. In most situations, we recommend that you choose Secure Boot. This option provides Secure Boot with as much protection as is supported by a given computer’s hardware. A computer with input/output memory management units (IOMMUs) will have Secure Boot with DMA protection. A computer without IOMMUs will simply have Secure Boot enabled. In contrast, with Secure Boot with DMA, the setting will enable Secure Boot—and VBS itself—only on a computer that supports DMA, that is, a computer with IOMMUs. With this setting, any computer without IOMMUs won't have VBS or HVCI protection, although it can still have WDAC enabled.
  
  
  **Default**: Yes  
  -->
- **Launch system guard**   (Iniciar protección del sistema)  
  **Valor predeterminado**: Habilitado  

## <a name="device-installation"></a>Instalación de dispositivos  
Para más información, vea [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) (CSP de directiva: DeviceInstallation) en la documentación de Windows.  

- **Hardware device installation by device identifiers** (Instalación de dispositivos de hardware mediante identificadores de dispositivo)  
  Esta configuración de directiva le permite especificar una lista de identificadores de hardware Plug and Play e identificadores compatibles para dispositivos que Windows no puede instalar. Esta configuración de directiva tiene prioridad sobre cualquier otra configuración de directiva que permita a Windows instalar dispositivos. Si habilita esta configuración de directiva, Windows no podrá instalar un dispositivo cuyo identificador de hardware o identificador compatible aparezca en la lista que usted cree. Si habilita esta configuración de directiva en un servidor de escritorio remoto, esta afectará a la redirección de los dispositivos especificados desde un cliente de escritorio remoto al servidor de escritorio remoto. Si deshabilita o no establece esta configuración de directiva, se podrán instalar o actualizar dispositivos según lo permitan o impidan otras configuraciones de directiva.
  
  **Valor predeterminado**: Bloquear la instalación de dispositivos de hardware  

    Cuando se seleccione *Bloquear la instalación de dispositivos de hardware*, las siguientes opciones están disponibles.
  
    - **Remove matching hardware devices**  (Quitar dispositivos de hardware que coinciden)  
    Esta opción solo está disponible cuando *Hardware device installation by device identifiers* (Instalación de dispositivos de hardware mediante identificadores de dispositivo) se establece en *Bloquear la instalación de dispositivos de hardware*.
      
      **Valor predeterminado**: Sí
  
    - **Hardware device identifiers that are blocked** (Identificadores de dispositivo de hardware que están bloqueados)  
       Esta opción solo está disponible cuando *Hardware device installation by device identifiers* (Instalación de dispositivos de hardware mediante identificadores de dispositivo) se establece en *Bloquear la instalación de dispositivos de hardware*.
      
      **Valor predeterminado**: Sí  
  
- **Hardware device installation by setup classes** (Instalación de dispositivos de hardware mediante clases de instalación)  
  Esta configuración de directiva permite especificar una lista de identificadores únicos globales (GUID) de clases de instalación de dispositivos para los controladores de dispositivos que no se pueden instalar en Windows. Esta configuración de directiva tiene prioridad sobre cualquier otra configuración de directiva que permita a Windows instalar dispositivos. Si habilita esta configuración de directiva, Windows no podrá instalar ni actualizar controladores de dispositivos cuyos GUID de clases de instalación de dispositivos aparezcan en la lista que cree. Si habilita esta configuración de directiva en un servidor de escritorio remoto, esta afectará a la redirección de los dispositivos especificados desde un cliente de escritorio remoto al servidor de escritorio remoto. Si deshabilita o no establece esta configuración de directiva, Windows puede instalar o actualizar dispositivos según lo permitan o impidan otras configuraciones de directiva.
  
  **Valor predeterminado**: Bloquear la instalación de dispositivos de hardware  

    Cuando se seleccione *Bloquear la instalación de dispositivos de hardware*, las siguientes opciones están disponibles.
    - **Remove matching hardware devices**   (Quitar dispositivos de hardware que coinciden)  
    Esta opción solo está disponible cuando *Hardware device installation by setup classes* (Instalación de dispositivos de hardware por clases de instalación) se establece en *Bloquear la instalación de dispositivos de hardware*.  

      **Valor predeterminado**: *Sin configuración predeterminada*  
  
    - **Hardware device identifiers that are blocked** (Identificadores de dispositivo de hardware que están bloqueados)  
      Esta opción solo está disponible cuando *Hardware device installation by setup classes* (Instalación de dispositivos de hardware por clases de instalación) se establece en *Bloquear la instalación de dispositivos de hardware*.
      
      **Valor predeterminado**: *Sin configuración predeterminada*  

## <a name="device-lock"></a>Bloqueo del dispositivo  
Para más información, vea [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) (CSP de directiva: DeviceLock) en la documentación de Windows.  

- **Impedir el uso de la cámara**  
  Deshabilita el conmutador para alternar la cámara en la pantalla de bloqueo en Configuración de PC y evita que una cámara se invoque en la pantalla de bloqueo. De forma predeterminada, los usuarios pueden habilitar la invocación de una cámara disponible en la pantalla de bloqueo. Si habilita esta configuración, los usuarios ya no podrán habilitar o deshabilitar el acceso a la cámara en la pantalla de bloqueo en Configuración de PC, y la cámara no se podrá invocar en la pantalla de bloqueo. 
  
  **Valor predeterminado**: Habilitado  

- **Requerir contraseña**  
  Especifica si está habilitado el bloqueo del dispositivo.
  
  **Valor predeterminado**: Sí  
  
    Cuando *Requerir contraseña* está establecido en *Sí*, las siguientes opciones están disponibles.

    - **Password minimum character set count** (Número mínimo de conjuntos de caracteres de contraseña)  
      El número de elementos complejos (letras mayúsculas y minúsculas, números y signos de puntuación) necesarios para una contraseña o PIN fuerte. El PIN aplica el comportamiento siguiente para los dispositivos móviles y de escritorios: 1 - Solo dígitos 2 - Se requieren dígitos y letras minúsculas 3 - Se requieren dígitos, letras minúsculas y letras mayúsculas. No se admite en cuentas de Microsoft de escritorio y cuentas de dominio. 4 - Se requieren dígitos, letras minúsculas, letras mayúsculas y caracteres especiales. No se admite en el escritorio. El valor predeterminado es 1. 
      
      **Valor predeterminado**: 3  
  
    - **Número de errores de inicio de sesión antes de borrar el dispositivo**  
      El número de errores de autenticación permitidos antes de que se borre el dispositivo. Un valor de 0 deshabilita la funcionalidad de borrado del dispositivo.
        
      **Valor predeterminado**: 10  
  
    - **Expiración de contraseña (días)**  
      La configuración de directiva Vigencia máxima de la contraseña determina cuánto tiempo (en días) se puede usar una contraseña antes de que el sistema requiera que el usuario la cambie. Puede establecer las contraseñas para que expiren después de un número de días comprendido entre 1 y 999, o bien que no expiren nunca si establece el número de días en 0. Si el valor de Vigencia máxima de la contraseña está comprendido entre 1 y 999 días, la vigencia mínima de la contraseña debe ser menor que la máxima. Si el valor de Vigencia máxima de la contraseña se establece en 0, la vigencia mínima de la contraseña puede ser cualquier valor entre 0 y 998 días.
      
      **Valor predeterminado**: 60  
  
    - **Tipo de contraseña obligatoria**  
      Determina el tipo de PIN o contraseña requerido.
      
      **Valor predeterminado**: Alfanumérico  
  
    - **Longitud mínima de contraseña**  
      La configuración de directiva Longitud mínima de contraseña determina el menor número de caracteres que pueden formar una contraseña para una cuenta de usuario. Puede establecer un valor comprendido entre 1 y 14 caracteres, o bien que no se requiera ninguna contraseña si establece el número de caracteres en 0.
      
      **Valor predeterminado**: 8  
  
    - **Bloquear contraseñas simples**  
      Especifica si se permiten números de PIN o contraseñas como "1111" o "1234". Para el escritorio, también controla el uso de contraseñas de imagen.
      
      **Valor predeterminado**: Sí  
        *Un valor de Sí impide el uso de contraseñas simples.* 

  - **Impedir la reutilización de contraseñas anteriores**  
    Especifica cuántas contraseñas se pueden almacenar en el historial que no se pueden usar. El valor incluye la contraseña actual del usuario. Por ejemplo, con una configuración de *1*, el usuario no puede reutilizar la contraseña actual al elegir una contraseña nueva. Un valor de *5* significa que un usuario no puede establecer la nueva contraseña en su contraseña actual o en cualquiera de sus cuatro contraseñas anteriores.
    
    **Valor predeterminado**: 24  

- **Evitar la presentación con diapositivas**  
  Deshabilita la configuración de presentación en la pantalla de bloqueo en Configuración de PC y evita que se reproduzca una presentación en la pantalla de bloqueo. De forma predeterminada, los usuarios pueden habilitar una presentación que se ejecute después de bloquear el equipo. Si habilita esta configuración, los usuarios no pueden modificar la configuración de la presentación en Configuración de PC y no se puede iniciar ninguna presentación.
  
    **Valor predeterminado**: Habilitado  
    *Una configuración de Habilitada impide que se ejecute la presentación.* 

- **Password minimum age in days** (Vigencia mínima de la contraseña en días)  
  La configuración de directiva Vigencia mínima de la contraseña determina el período de tiempo (en días) que se debe usar una contraseña antes de que el usuario pueda cambiarla. Puede establecer un valor comprendido entre 1 y 998 días, o bien puede permitir los cambios de contraseña inmediatamente si establece el número de días en 0. La vigencia mínima de la contraseña debe ser menor que la máxima, a menos que la vigencia máxima de la contraseña se establezca en 0, lo que indica que la contraseña no caducará nunca. Si el valor de Vigencia máxima de la contraseña se establece en 0, la vigencia mínima de la contraseña se puede establecer en cualquier valor entre 0 y 998.
  
    **Valor predeterminado**: 1  

## <a name="event-log-service"></a>Servicio Registro de eventos  
Para más información, vea [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) (CSP de directiva: EventLogService) en la documentación de Windows.  

- **Tamaño máximo del archivo de registro de seguridad en KB**  
  Esta configuración de directiva especifica el tamaño máximo del archivo de registro en kilobytes. Si habilita esta configuración de directiva, puede configurar el tamaño máximo del archivo de registro entre 1 megabyte (1024 KB) y 2 terabytes (2147483647 kilobytes), en incrementos de kilobytes. Si deshabilita o no establece esta configuración de directiva, el tamaño máximo del archivo de registro se establece en el valor configurado de forma local. Este valor lo puede cambiar el administrador local mediante el cuadro de diálogo Propiedades del registro y el valor predeterminado es de 20 megabytes.
  
   **Valor predeterminado**: 196608  

- **Tamaño máximo del archivo de registro del sistema en KB**  
  Esta configuración de directiva especifica el tamaño máximo del archivo de registro en kilobytes. Si habilita esta configuración de directiva, puede configurar el tamaño máximo del archivo de registro entre 1 megabyte (1024 KB) y 2 terabytes (2147483647 kilobytes), en incrementos de kilobytes. Si deshabilita o no establece esta configuración de directiva, el tamaño máximo del archivo de registro se establece en el valor configurado de forma local. Este valor lo puede cambiar el administrador local mediante el cuadro de diálogo Propiedades del registro y el valor predeterminado es de 20 megabytes.
  
  **Valor predeterminado**: 32768  

- **Tamaño máximo del archivo de registro de aplicaciones en KB**  
  Esta configuración de directiva especifica el tamaño máximo del archivo de registro en kilobytes. Si habilita esta configuración de directiva, puede configurar el tamaño máximo del archivo de registro entre 1 megabyte (1024 KB) y 2 terabytes (2147483647 kilobytes), en incrementos de kilobytes. Si deshabilita o no establece esta configuración de directiva, el tamaño máximo del archivo de registro se establece en el valor configurado de forma local. Este valor lo puede cambiar el administrador local mediante el cuadro de diálogo Propiedades del registro y el valor predeterminado es de 20 megabytes.
  
  **Valor predeterminado**: 32768  

## <a name="experience"></a>Experiencia  
Para más información, vea [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) (CSP de directiva: Experiencia) en la documentación de Windows.  

- **Bloquear el Contenido destacado de Windows**  
  Permite a los administradores de TI desactivar todas las características de Contenido destacado de Windows: Contenido destacado de Windows en la pantalla de bloqueo, sugerencias de Windows, características de consumidor de Microsoft y otras características relacionadas.
  
  **Valor predeterminado**: Sí  

  Cuando *Bloquear el Contenido destacado de Windows* está establecido en *Sí*, las siguientes opciones están disponibles.
  
  - **Bloquear sugerencias de terceros en Contenido destacado de Windows**  
    Especifica si se permiten sugerencias de contenido y aplicaciones de editores de software de terceros en características de Contenido destacado de Windows como el contenido destacado en la pantalla de bloqueo, aplicaciones sugeridas en el menú Inicio y sugerencias de Windows. Es posible que los usuarios sigan viendo sugerencias sobre características, aplicaciones y servicios de Microsoft.
      
    **Valor predeterminado**: Sí  
   - **Block consumer specific features** (Bloquear características específicas del consumidor)  
      Permite a los administradores de TI activar experiencias que suelen ser solo para consumidores, como las sugerencias de inicio, las notificaciones de suscripción, la instalación de aplicaciones tras la Bienvenida de Windows y los iconos de redireccionamiento.
      
     **Valor predeterminado**: Sí  


## <a name="exploit-guard"></a>Protección contra vulnerabilidades de seguridad  
Para más información, vea [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) (CSP de directiva: ExploitGuard) en la documentación de Windows.  

- **XML de protección contra vulnerabilidades**  
  Permite a los administradores de TI enviar a todos los dispositivos de la organización una configuración que representa las opciones de mitigación deseadas del sistema y las aplicaciones. La configuración se representa por medio de XML. Protección contra vulnerabilidades ayuda a proteger los dispositivos frente al malware que usa ataques para infectar y propagar. Use la aplicación de seguridad de Windows o PowerShell para crear un conjunto de mitigaciones (conocido como una configuración). Después, puede exportar esta configuración como un archivo XML y compartirlo con varios equipos en la red para que todos tengan el mismo conjunto de opciones de mitigación. También puede convertir e importar un archivo XML de configuración EMET en un archivo XML de configuración de protección contra vulnerabilidades.
  
  **Valor predeterminado**: *Se proporciona el código XML de ejemplo* 
 
## <a name="file-explorer"></a>Explorador de archivos  
Para más información, vea [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) (CSP de directiva: FileExplorer) en la documentación de Windows.  

- **Block data execution prevention** (Bloquear la prevención de ejecución de datos)  
  Deshabilitar la prevención de ejecución de datos puede permitir que ciertas aplicaciones de complemento heredadas funcionen sin cerrar Explorer.
  
  **Valor predeterminado**: Deshabilitado  
   
- **Block heap termination on corruption** (Bloquear la terminación del montón al resultar dañado)  
  Si deshabilita la terminación del montón al resultar dañado, es posible que algunas aplicaciones de complemento heredadas funcionen sin terminar el Explorador inmediatamente, si bien este aún podría terminar de forma inesperada más adelante.
  
  **Valor predeterminado**: Deshabilitado  
    

## <a name="internet-explorer"></a>Internet Explorer  
Para más información, vea [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) (CSP de directiva: InternetExplorer) en la documentación de Windows.  
<!-- not yet available 
- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Disabled  
  
- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Disable  
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Disable  
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: Disabled  
 -->
- **Internet Explorer internet zone access to data sources** (Acceso a orígenes de datos de la zona de Internet de Internet Explorer)  
  Esta configuración de directiva le permite administrar si Internet Explorer puede acceder a datos de otra zona de seguridad con Analizador XML de Microsoft (MSXML) u Objetos de datos ActiveX (ADO). Si habilita esta configuración de directiva, los usuarios podrán cargar una página en la zona que usa MSXML o ADO para acceder a datos de otro sitio en la zona. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir que una página se cargue en la zona que usa MSXML o ADO para acceder a datos de otro sitio de la zona. Si deshabilita esta configuración de directiva, los usuarios no podrán cargar ninguna página en la zona que usa MSXML o ADO para acceder a datos de otro sitio de la zona. Si no establece esta configuración de directiva, los usuarios no podrán cargar ninguna página en la zona que usa MSXML o ADO para acceder a datos de otro sitio de la zona.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone drag content from different domains within windows** (Arrastrar contenido de diferentes dominios desde ventanas en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite establecer las opciones para arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentran en la misma ventana. Si habilita esta configuración de directiva y hace clic en Habilitar, los usuarios podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en la misma ventana. Los usuarios no pueden cambiar esta configuración. Si habilita esta configuración de directiva y hace clic en Deshabilitar, los usuarios no podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en la misma ventana. Los usuarios no pueden cambiar esta configuración en el cuadro de diálogo Opciones de Internet. En Internet Explorer 10, si deshabilita o no establece esta configuración de directiva, los usuarios no podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en la misma ventana. Los usuarios pueden cambiar esta configuración en el cuadro de diálogo Opciones de Internet. En Internet Explorer 9 y versiones anteriores, si deshabilita o no establece esta configuración de directiva, los usuarios podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en la misma ventana. Los usuarios no pueden cambiar esta configuración en el cuadro de diálogo Opciones de Internet.
  
  **Valor predeterminado**: Deshabilitado
  
- **Internet Explorer certificate address mismatch warning** (Advertencia de error de coincidencia de direcciones de certificado de Internet Explorer)  
  Esta configuración de directiva permite activar la advertencia de seguridad de falta de coincidencia en la dirección de los certificados. Cuando se activa esta configuración, se advierte al usuario cuando visita sitios web HTTP seguros (HTTPS) que presentan certificados emitidos para otra dirección de sitio web. Esta advertencia ayuda a prevenir ataques de suplantación de identidad. Si habilita esta configuración de directiva, aparece siempre la advertencia de falta de coincidencia en la dirección de certificados. Si deshabilita o no establece esta configuración de directiva, el usuario puede elegir si se muestra la advertencia de falta de coincidencia en la dirección de los certificados (con la página Opciones avanzadas del panel de control de Internet).
  
  **Valor predeterminado**: Habilitado 
  
- **Internet Explorer restricted zone less privileged sites** (Sitios con menos privilegios de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si los sitios web de zonas con menos privilegios, como los de Internet, pueden desplazarse hacia ella. Si habilita esta configuración de directiva, los sitios web de zonas con menos privilegios podrán abrir nuevas ventanas en esta zona o desplazarse hacia ella. La zona de seguridad se ejecutará sin la capa agregada de seguridad proporcionada por la característica de seguridad Protección contra elevación de zona. Si selecciona Preguntar en el cuadro desplegable, se emitirá una advertencia al usuario que indica que se va a realizar una navegación potencialmente arriesgada. Si deshabilita esta configuración de directiva, se evitará cualquier navegación que pueda ser dañina. La característica de seguridad de Internet Explorer está activada en esta zona como lo establece el control de la característica Protección contra elevación de zona. Si no establece esta configuración de directiva, se evitará cualquier navegación que pueda ser dañina. La característica de seguridad de Internet Explorer está activada en esta zona como lo establece el control de la característica Protección contra elevación de zona.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone automatic prompt for file downloads** (Solicitud automática de descargas de archivos en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva determina si se solicita la intervención de los usuarios para las descargas de archivos no iniciadas por usuarios. Independientemente de esta configuración, se presentarán cuadros de diálogo de descarga de archivos a los usuarios en las descargas iniciadas por ellos. Si habilita esta configuración de directiva, se presentará un cuadro de diálogo de descarga de archivos a los usuarios cuando se intente realizar una descarga automática. Si deshabilita esta configuración o no la establece, se bloquea cualquier descarga de archivos no iniciada por usuarios y estos verán la barra de notificación en lugar del cuadro de diálogo de descarga de archivos. Los usuarios podrán hacer clic en la barra de notificación para permitir que se les solicite su intervención para descargar el archivo.
  
  **Valor predeterminado**: Deshabilitado
  
- **Internet Explorer internet zone .NET Framework reliant components** (Componentes que dependen de .NET Framework en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar si los componentes de .NET Framework que no están firmados con Authenticode se pueden ejecutar en Internet Explorer. Entre esos componentes figuran los controles administrados a los que una etiqueta de objeto hizo referencia y los archivos ejecutables administrados a los que un vínculo hizo referencia. Si habilita esta configuración de directiva, Internet Explorer ejecutará los componentes administrados firmados. Si selecciona Preguntar en el cuadro desplegable, Internet Explorer solicitará la intervención de los usuarios para determinar si quieren ejecutar los componentes administrados firmados. Si deshabilita esta configuración de directiva, Internet Explorer no ejecutará ningún componente administrado sin firma. Si no establece esta configuración de directiva, Internet Explorer ejecutará los componentes administrados sin firma.
  
  **Valor predeterminado**: Deshabilitar 
  
- **Internet Explorer internet zone allow only approved domains to use Active X controls** (Permitir que solo los dominios aprobados usen controles ActiveX de TDC en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva controla si el usuario puede ejecutar el control ActiveX de TDC en sitios web. Si habilita esta configuración de directiva, el control ActiveX de TDC no se ejecutará desde los sitios web de esta zona. Si deshabilita esta configuración de directiva, el control ActiveX de TDC se ejecutará desde todos los sitios de esta zona.
  
  **Valor predeterminado**: Habilitado 
  
- **Internet Explorer restricted zone script initiated windows** (Ventanas iniciadas por scripts de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar las restricciones sobre ventanas emergentes iniciadas por scripts y sobre ventanas que incluyen la barra de título y estado. Si habilita esta directiva, la seguridad de restricciones de ventanas no se aplicará en esta zona. La zona de seguridad se ejecutará sin la capa agregada de seguridad proporcionada por esta característica. Si deshabilita esta configuración de directiva, no se podrán ejecutar las acciones potencialmente dañinas contenidas en las ventanas emergentes iniciadas por scripts y en las ventanas que incluyen la barra de título y estado. Esta característica de seguridad de Internet Explorer está activada en esta zona como lo indica el control de la característica Restricciones de seguridad de ventanas con scripts para el proceso. Si no establece esta configuración de directiva, no se podrán ejecutar las acciones posiblemente dañinas contenidas en las ventanas emergentes iniciadas por scripts y en las ventanas que incluyen la barra de título y estado. Esta característica de seguridad de Internet Explorer está activada en esta zona como lo indica el control de la característica Restricciones de seguridad de ventanas con scripts para el proceso.
  
  **Valor predeterminado**: Deshabilitado 
  
- **Internet Explorer internet zone include local path when uploading files to server** (Incluir la ruta de acceso local al cargar archivos al servidor en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva controla si la información de la ruta de acceso local se envía cuando el usuario carga un archivo por medio de un formulario HTML. Si se envía la información de la ruta de acceso local, es posible que parte de la información sea revelada sin querer al servidor. Por ejemplo, los archivos enviados desde el escritorio del usuario pueden contener el nombre de usuario como parte de la ruta de acceso. Si habilita esta configuración de directiva, la información de la ruta de acceso se envía cuando el usuario carga un archivo por medio de un formulario HTML. Si deshabilita esta configuración de directiva, la información de la ruta de acceso se elimina cuando el usuario carga un archivo por medio de un formulario HTML. Si no establece esta configuración de directiva, el usuario puede elegir si la información de la ruta de acceso se envía cuando carga un archivo por medio de un formulario HTML. De manera predeterminada, la información de la ruta de acceso se envía.
  
  **Valor predeterminado**: Deshabilitado 
  
- **Internet Explorer disable processes in enhanced protected mode** (Deshabilitar los procesos en modo protegido mejorado de Internet Explorer)  
  Esta configuración de directiva determina si Internet Explorer 11 usa procesos de 64 bits (de cara a una mayor seguridad) o de 32 bits (de cara a una mejor compatibilidad) cuando se ejecuta el modo protegido mejorado en las versiones de 64 bits de Windows. Importante: Es posible que algunas barras de herramientas y controles ActiveX no estén disponibles cuando se usan procesos de 64 bits. Si habilita esta configuración de directiva, Internet Explorer 11 usará procesos de pestañas de 64 bits cuando se ejecute el modo protegido mejorado en las versiones de 64 bits de Windows. Si deshabilita esta configuración de directiva, Internet Explorer 11 usará procesos de pestañas de 32 bits cuando se ejecute el modo protegido mejorado en las versiones de 64 bits de Windows. Si no establece esta configuración de directiva, los usuarios pueden activar y desactivar esta característica en la configuración de Internet Explorer. Esta característica está desactivada de manera predeterminada.
  
  **Valor predeterminado**: Habilitado 
  
- **Internet Explorer ignore certificate errors** (Omitir errores de certificado de Internet Explorer)  
  Esta configuración de directiva impide que el usuario ignore errores de certificado de Capa de sockets seguros/Seguridad de la capa de transporte (SSL/TLS) que interrumpan la navegación (errores como caducado, revocado o de coincidencia de los nombres) en Internet Explorer. Si habilita esta configuración de directiva, el usuario no puede continuar la exploración. Si deshabilita o no establece esta configuración de directiva, el usuario puede elegir ignorar los errores de certificado y continuar la exploración.
  
  **Valor predeterminado**: Deshabilitado 
  
- **Internet Explorer internet zone loading of XAML files** (Carga de archivos XML en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar la carga de archivos de lenguaje de marcado de aplicaciones extensible (XAML). XAML es un lenguaje de marcado declarativo basado en XML que habitualmente se usa para crear interfaces de usuario y gráficos enriquecidos que aprovechan Windows Presentation Foundation. Si habilita esta configuración de directiva y establece el cuadro desplegable en Habilitar, los archivos XAML se cargan automáticamente dentro de Internet Explorer. El usuario no puede cambiar este comportamiento. Si establece el cuadro desplegable en Preguntar, se le pregunta al usuario para cargar los archivos XAML. Si deshabilita esta configuración de directiva, los archivos XAML no se cargan en Internet Explorer. El usuario no puede cambiar este comportamiento. Si no establece esta configuración de directiva, el usuario puede decidir si cargar los archivos XAML en Internet Explorer.
  
  **Valor predeterminado**: Deshabilitar 
  
- **Internet Explorer internet zone automatic prompt for file downloads** (Solicitud automática de descargas de archivos en la zona Internet de Internet Explorer)  
  Esta configuración de directiva determina si se solicita la intervención de los usuarios para las descargas de archivos no iniciadas por usuarios. Independientemente de esta configuración, se presentarán cuadros de diálogo de descarga de archivos a los usuarios en las descargas iniciadas por ellos. Si habilita esta configuración de directiva, se presentará un cuadro de diálogo de descarga de archivos a los usuarios cuando se intente realizar una descarga automática. Si deshabilita esta configuración o no la establece, se bloquea cualquier descarga de archivos no iniciada por usuarios y estos verán la barra de notificación en lugar del cuadro de diálogo de descarga de archivos. Los usuarios podrán hacer clic en la barra de notificación para permitir que se les solicite su intervención para descargar el archivo.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files** (Advertencia de seguridad de la zona de sitios restringidos de Internet Explorer para archivos potencialmente no seguros)  
  Esta configuración de directiva controla si el mensaje "Abrir archivo: advertencia de seguridad" aparece cuando el usuario intenta abrir archivos ejecutables u otros archivos que puedan no ser seguros (por ejemplo, desde un recurso compartido de archivos de intranet mediante el Explorador de archivos). Si habilita esta configuración de directiva y establece el cuadro desplegable en Habilitar, estos archivos se abren sin una advertencia de seguridad. Si establece el cuadro desplegable en Preguntar, aparece una advertencia de seguridad antes de que se abra el archivo. Si deshabilita esta configuración de directiva, estos archivos no se abren. Si no establece esta configuración de directiva, el usuario puede configurar cómo controla el equipo estos archivos. De manera predeterminada, estos archivos están bloqueados en la zona Sitios restringidos, habilitados en las zonas Intranet y Equipo local, y establecidos en Preguntar en las zonas Internet y Sitios de confianza.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer internet zone cross site scripting filter** (Filtro de scripts de sitios de la zona de Internet de Internet Explorer)  
  Esta directiva controla si el filtro de scripts de sitios (XSS) detectará e impedirá la inserción de scripts de sitios en los sitios web de esta zona. Si habilita esta configuración de directiva, el filtro XSS se activa para los sitios de esta zona y el filtro XSS intenta bloquear las inserciones de scripts de sitios. Si deshabilita esta configuración de directiva, el filtro XSS se desactiva para los sitios de esta zona e Internet Explorer permite las inserciones de scripts de sitios.
  
  **Valor predeterminado**: Habilitado 
  
- **Internet Explorer fallback to SSL3** (Reserva para SSL 3.0 de Internet Explorer)  
  Esta configuración de directiva permite bloquear una reserva no segura para SSL 3.0. Cuando esté habilitada, Internet Explorer intentará conectarse a los sitios con SSL 3.0 o una versión anterior cuando se produzca un error en TLS 1.0 o una versión posterior. Se recomienda no permitir la reserva no segura con el fin de evitar un ataque de tipo "Man in the middle". Esta directiva no afecta a la selección de protocolos de seguridad habilitados. Si deshabilita esta directiva, se usan los valores predeterminados del sistema.
  
  **Valor predeterminado**: No hay sitios 
  
- **Internet Explorer locked down internet zone smart screen** (Bloqueo de SmartScreen para la zona de Internet de Internet Explorer)  
  Esta configuración de directiva controla si el filtro SmartScreen examina las páginas de la zona para detectar contenido malintencionado. Si habilita esta configuración de directiva, el filtro SmartScreen examina las páginas de la zona para detectar contenido malintencionado. Si deshabilita esta configuración de directiva, el filtro SmartScreen no examina las páginas de la zona para detectar contenido malintencionado. Si no establece esta configuración de directiva, el usuario puede elegir si el filtro SmartScreen examina las páginas de esta zona para detectar contenido malintencionado. Nota: En Internet Explorer 7, esta configuración de directiva controla si el filtro de suplantación de identidad examina las páginas de esta zona para detectar contenido malintencionado.
  
  **Valor predeterminado**: Habilitado 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame** (Iniciar aplicaciones y archivos en un iFrame en la zona restringida de Internet Explorer)  
  Esta configuración de directiva permite administrar si se pueden ejecutar aplicaciones y descargar archivos de una referencia IFRAME en el código HTML de las páginas de esta zona. Si habilita esta configuración de directiva, los usuarios podrán ejecutar aplicaciones y descargar archivos desde IFRAME en las páginas de esta zona sin pedirles su intervención. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren ejecutar aplicaciones y descargar archivos desde IFRAME en las páginas de esta zona. Si deshabilita esta configuración de directiva, se impedirá que los usuarios ejecuten aplicaciones y descarguen archivos desde IFRAME en las páginas de esta zona. Si no establece esta configuración de directiva, se impide que los usuarios ejecuten aplicaciones y descarguen archivos desde IFRAME en las páginas de esta zona.
  
  **Valor predeterminado**: Deshabilitar 
  
- **Internet Explorer bypass smart screen warnings about uncommon files** (Omitir las advertencias de SmartScreen de Internet Explorer sobre archivos no comunes)  
  Esta configuración de directiva determina si el usuario puede omitir las advertencias del filtro SmartScreen. El filtro SmartScreen advierte al usuario sobre los archivos ejecutables que los usuarios de Internet Explorer no suelen descargar de Internet. Si habilita esta configuración de directiva, las advertencias del filtro SmartScreen bloquean al usuario. Si deshabilita o no establece esta configuración de directiva, el usuario puede omitir las advertencias del filtro SmartScreen.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer internet zone popup blocker** (Bloqueador de ventanas emergentes de la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar si se muestran las ventanas emergentes no deseadas. Las ventanas emergentes que se abren cuando el usuario final hace clic en un vínculo no se bloquean. Si habilita esta configuración de directiva, se impide que se muestre la mayoría de las ventanas emergentes no deseadas. Si deshabilita esta configuración de directiva, no se impide la aparición de ventanas emergentes. Si no establece esta configuración de directiva, se impide que se muestre la mayoría de las ventanas emergentes no deseadas.
  
  **Valor predeterminado**: Habilitar  
  
- **Internet Explorer processes consistent MIME handling** (Administración de MIME coherente para procesos de Internet Explorer)  
  Internet Explorer contiene comportamientos de binarios dinámicos: componentes que encapsulan funcionalidad específica de los elementos HTML a los que están conectados. Esta configuración de directiva controla si se impide o se permite la restricción de seguridad del comportamiento binario. Si habilita esta configuración de directiva, se impiden los comportamientos binarios en los procesos del Explorador de archivos e Internet Explorer. Si deshabilita esta configuración de directiva, se permiten los comportamientos binarios en los procesos del Explorador de archivos e Internet Explorer. Si no establece esta configuración de directiva, se impiden los comportamientos binarios en los procesos del Explorador de archivos e Internet Explorer.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer restricted zone java permissions** (Permisos de Java en la zona restringida de Internet Explorer)  
  Esta configuración de directiva permite administrar los permisos para applets Java. Si habilita esta configuración de directiva, podrá elegir una opción del cuadro desplegable. Personalizado, para controlar la configuración de permisos individualmente. Seguridad baja habilita a los applets para realizar todas las operaciones. Seguridad media habilita a los applets para ejecutarse en su espacio aislado (un área de memoria fuera de la cual el programa no puede hacer llamadas), además de funcionalidades como espacio de desecho (un área de almacenamiento segura en el equipo cliente) y E/S de archivos controlada por usuario. Seguridad alta habilita a los applets para ejecutarse en su espacio aislado. Deshabilite Java para impedir la ejecución de los applets. Si deshabilita esta configuración de directiva, los applets Java no se ejecutarán. Si no establece esta configuración de directiva, los applets Java se deshabilitan.
  
  **Valor predeterminado**: Deshabilitar Java  
    
  
- **Internet Explorer Active X controls in protected mode** (Controles ActiveX en modo protegido de Internet Explorer )  
  Esta directiva evita que los controles ActiveX se ejecuten en modo protegido cuando está habilitado el modo protegido mejorado. Cuando un usuario tiene instalado un control ActiveX que no es compatible con el modo protegido mejorado y el sitio web intenta cargar el control, Internet Explorer informa al usuario y ofrece la opción de ejecutar el sitio web en el modo protegido normal. Esta configuración de directiva deshabilita esta notificación y fuerza la ejecución de todos los sitios web en el modo protegido mejorado. El modo protegido mejorado utiliza procesos de 64 bits en versiones de Windows de 64 bits para proporcionar seguridad adicional contra los sitios web malintencionados. En equipos que ejecutan al menos Windows 8, el modo protegido mejorado también limita las ubicaciones que Internet Explorer puede leer del Registro y del sistema de archivos. Cuando el modo protegido mejorado está habilitado y un usuario encuentra un sitio web que intenta cargar un control ActiveX que no es compatible con el modo protegido mejorado, Internet Explorer informa al usuario y ofrece la opción de deshabilitar el modo protegido mejorado para ese sitio web en particular. Si habilita esta configuración de directiva, Internet Explorer no ofrecerá al usuario la opción de deshabilitar el modo protegido mejorado. Todos los sitios web en modo protegido se ejecutarán en el modo protegido mejorado. Si deshabilita o no establece esta configuración de directiva, Internet Explorer informa a los usuarios y proporciona la opción de ejecutar sitios web con controles ActiveX incompatibles en el modo protegido normal.  
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer restricted zone loading of XAML files** (Carga de archivos XML en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar la carga de archivos de lenguaje de marcado de aplicaciones extensible (XAML). XAML es un lenguaje de marcado declarativo basado en XML que habitualmente se usa para crear interfaces de usuario y gráficos enriquecidos que aprovechan Windows Presentation Foundation. Si habilita esta configuración de directiva y establece el cuadro desplegable en Habilitar, los archivos XAML se cargan automáticamente dentro de Internet Explorer. El usuario no puede cambiar este comportamiento. Si establece el cuadro desplegable en Preguntar, se le pregunta al usuario para cargar los archivos XAML. Si deshabilita esta configuración de directiva, los archivos XAML no se cargan en Internet Explorer. El usuario no puede cambiar este comportamiento. Si no establece esta configuración de directiva, el usuario puede decidir si cargar los archivos XAML en Internet Explorer.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer processes scripted window security restrictions** (Restricciones de seguridad para ventanas creadas por scripts para los procesos de Internet Explorer)  
  Internet Explorer permite que los scripts, mediante programación, abran ventanas de diferentes tipos y cambien su tamaño y ubicación. La característica de seguridad Restricciones de ventanas restringe las ventanas emergentes e impide a los scripts que muestren ventanas en las que las barras de título y estado no sean visibles para el usuario u obstruyan las barras de estado y título de otras ventanas. Si habilita esta configuración de directiva, se restringirán las ventanas creadas por scripts para todos los procesos. Si deshabilita esta configuración de directiva o no la establece, no se restringirá ninguna ventana creada por scripts.
  
  **Valor predeterminado**: Habilitado   
  
- **Internet Explorer restricted zone run Active X controls and plugins** (Ejecutar controles ActiveX y complementos de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si los controles ActiveX y complementos se pueden ejecutar en páginas de la zona especificada. Si habilita esta configuración de directiva, los controles y complementos podrán ejecutarse sin la intervención del usuario. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir la ejecución de los controles o complementos. Si deshabilita esta configuración de directiva, se impedirá que los controles y complementos se ejecuten. Si no establece esta configuración de directiva, se impedirá que los controles y complementos se ejecuten.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting** (Incluir en scripts controles ActiveX marcados como seguros para ejecutar scripts de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si un control ActiveX marcado como seguro para ejecutar scripts puede interactuar con un script. Si habilita esta configuración de directiva, la interacción con el script podrá realizarse automáticamente sin la intervención del usuario. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir la interacción con el script. Si deshabilita esta configuración de directiva, se impedirá que la interacción con el script se realice. Si no establece esta configuración de directiva, se impedirá que se realice la interacción con el script.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone logon options** (Opciones de inicio de sesión de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar la configuración de las opciones de inicio de sesión. Si habilita esta configuración de directiva, puede elegir una de las opciones de inicio de sesión siguientes. 
  - *Anónimo*: use el inicio de sesión anónimo para deshabilitar la autenticación HTTP y usar la cuenta de invitado solo para el protocolo de Sistema de archivos de Internet común (CIFS). 
  - *Preguntar*: use preguntar por el nombre de usuario y la contraseña para consultar al usuario sobre los id. de usuario y las contraseñas. Después de la consulta, estos valores se pueden usar de modo silencioso en lo que resta de la sesión. 
  - *Inicio de sesión automático solo en la zona Intranet*: use esta opción para consultar al usuario sobre los id. de usuario y contraseñas en otras zonas. Después de la consulta, estos valores se pueden usar de modo silencioso en lo que resta de la sesión. 
  - *Inicio de sesión automático con el nombre de usuario y contraseña actuales*: use esta opción para intentar el inicio de sesión mediante la Respuesta de desafío de autenticación Windows NT (conocida también como autenticación NTLM). Si el servidor es compatible con la Respuesta de desafío de autenticación Windows NT, el inicio de sesión usará el nombre de usuario y la contraseña de red del usuario para iniciar la sesión. Si el servidor no es compatible con la respuesta de desafío de Windows NT, se consultará al usuario para que proporcione el nombre de usuario y la contraseña. 

  Si deshabilita esta configuración de directiva, el inicio de sesión se establece en *Inicio de sesión automático solo en la zona Intranet*. Si no establece esta configuración de directiva, el inicio de sesión se establece en *Preguntar* para el nombre de usuario y la contraseña.
  
  **Valor predeterminado**: Anónimo  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe** (Inicializar e incluir en scripts controles ActiveX no marcados como seguros en la zona de sitios de confianza de Internet Explorer)  
  Esta configuración de directiva permite administrar los controles ActiveX no marcados como seguros. Si habilita esta configuración de directiva, los controles ActiveX se ejecutarán, se cargarán con parámetros y se incluirán en scripts sin establecer la seguridad de objetos para los datos o scripts que no sean de confianza. Esta configuración no se recomienda, excepto para zonas seguras y administradas. Esta configuración hace que los controles seguros y no seguros se inicialicen y se activen los scripts, omitiendo la opción "Generar scripts de los controles ActiveX marcados como seguros para scripts". Si habilita esta configuración de directiva y selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir que el control se cargue con parámetros o se activen los scripts. Si deshabilita esta configuración de directiva, ningún control ActiveX que no pueda hacerse seguro se cargará con parámetros ni se activarán los scripts. Si no establece esta configuración de directiva, se consultará a los usuarios si se permite que el control se cargue con parámetros o se activen los scripts.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer check server certificate revocation** (Comprobar la revocación de certificados de servidor de Internet Explorer)  
  Esta configuración de directiva permite administrar si Internet Explorer comprueba el estado de revocación de los certificados de los servidores. Los certificados se revocan cuando se ponen en peligro o ya no son válidos; esta opción protege a los usuarios de enviar datos confidenciales a un sitio que pueda ser fraudulento o no seguro. Si habilita esta configuración de directiva, Internet Explorer comprobará si los certificados del servidor han sido revocados. Si deshabilita esta configuración de directiva, Internet Explorer no comprobará si los certificados del servidor han sido revocados. Si no establece esta configuración de directiva, Internet Explorer no comprobará si los certificados del servidor han sido revocados.
  
  **Valor predeterminado**: Habilitado 
  
- **Internet Explorer internet zone less privileged sites** (Sitios con menos privilegios de la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar si los sitios web de zonas con menos privilegios, como Sitios restringidos, pueden desplazarse hacia ella. Si habilita esta configuración de directiva, los sitios web de zonas con menos privilegios podrán abrir nuevas ventanas en esta zona o desplazarse hacia ella. La zona de seguridad se ejecutará sin la capa agregada de seguridad proporcionada por la característica de seguridad Protección contra elevación de zona. Si selecciona Preguntar en el cuadro desplegable, se emitirá una advertencia al usuario que indica que se va a realizar una navegación potencialmente arriesgada. Si deshabilita esta configuración de directiva, se evitará cualquier navegación que pueda ser dañina. La característica de seguridad de Internet Explorer está activada en esta zona como lo establece el control de la característica Protección contra elevación de zona. Si no establece esta configuración de directiva, los sitios web de zonas con menos privilegios podrán abrir nuevas ventanas en esta zona o desplazarse hacia ella.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone file downloads** (Descargas de archivo de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si se permite la descarga de archivos de la zona. Esta opción se determina por la zona de la página con el vínculo que ocasiona la descarga, no por la zona desde donde se entrega el archivo. Si habilita esta configuración de directiva, los archivos podrán descargarse de la zona. Si deshabilita esta configuración de directiva, se impedirá que los archivos se descarguen de la zona. Si no establece esta configuración de directiva, se impedirá que los archivos se descarguen de la zona.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with authenticode** (Ejecutar componentes que dependen de .NET Framework firmados con Authenticode en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar si los componentes de .NET Framework firmados con Authenticode se pueden ejecutar en Internet Explorer. Entre esos componentes figuran los controles administrados a los que una etiqueta de objeto hizo referencia y los archivos ejecutables administrados a los que un vínculo hizo referencia. Si habilita esta configuración de directiva, Internet Explorer ejecutará los componentes administrados firmados. Si selecciona Preguntar en el cuadro desplegable, Internet Explorer solicitará la intervención de los usuarios para determinar si se quieren ejecutar los componentes administrados firmados. Si deshabilita esta configuración de directiva, Internet Explorer no ejecutará ningún componente administrado con firma. Si no establece esta configuración de directiva, Internet Explorer no ejecutará ningún componente administrado con firma.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer prevent per user installation of Active X controls** (Impedir la instalación por usuario de controles ActiveX de Internet Explorer)  
  Esta configuración de directiva permite impedir la instalación por usuario de controles ActiveX. Si habilita esta configuración de directiva, los controles ActiveX no se pueden instalar para cada usuario. Si deshabilita o no establece esta configuración de directiva, los controles ActiveX se pueden instalar por cada usuario.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer prevent managing smart screen filter** (Impedir la administración del filtro SmartScreen de Internet Explorer)  
  Esta configuración de directiva impide que el usuario administre el filtro SmartScreen, que le advierte de si el sitio web que visita es conocido por haber realizado intentos fraudulentos de reunir información personal a través de la suplantación de identidad, o si se sabe que contiene malware. Si habilita esta configuración de directiva, no se pedirá al usuario que active el filtro SmartScreen. Todas las direcciones de los sitios web que no se encuentren en la lista de sitios web permitidos del filtro se envían de forma automática a Microsoft sin solicitar la confirmación del usuario. Si deshabilita o no establece esta configuración de directiva, se pide al usuario que decida si quiere activar el filtro SmartScreen durante la primera ejecución.
  
  **Valor predeterminado**: Habilitar  
  
- **Internet Explorer processes MIME sniffing safety feature** (Característica de seguridad de examen de MIME de procesos de Internet Explorer)  
  Esta configuración de directiva determina si el examen de MIME de Internet Explorer impedirá la promoción del tipo de un archivo a otro tipo más peligroso. Si habilita esta configuración de directiva, el examen de MIME nunca promoverá el tipo de un archivo a otro tipo más peligroso. Si deshabilita esta configuración de directiva, los procesos de Internet Explorer permitirán que el examen de MIME promueva el tipo de un archivo a otro tipo más peligroso. Si no establece esta configuración de directiva, el examen de MIME nunca promoverá el tipo de un archivo a otro tipo más peligroso.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer restricted zone download signed Active X controls** (Descargar controles ActiveX firmados de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si los usuarios pueden descargar controles ActiveX firmados de una página en la zona. Si habilita esta directiva, los usuarios podrán descargar controles firmados sin solicitarles su intervención. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si se pueden descargar controles firmados por editores que no son de confianza. El código firmado por editores de confianza se descarga en modo silencioso. Si deshabilita la configuración de directiva, no se podrán descargar los controles firmados. Si no establece esta configuración de directiva, se consultará con los usuarios si se pueden descargar controles firmados por editores que no son de confianza. El código firmado por editores de confianza se descarga en modo silencioso.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer auto complete** (Autocompletar de Internet Explorer)  
  Esta característica Autocompletar puede recordar y sugerir nombres y contraseñas de usuarios en formularios. Si habilita esta opción, el usuario no puede cambiar "Nombres de usuario y contraseñas en formularios" ni "Preguntar si se guardan las contraseñas". Se activará la característica Autocompletar para nombres de usuario y contraseñas en formularios. Debe decidir si quiere seleccionar "Preguntar si se guardan las contraseñas". Si deshabilita esta opción, el usuario no puede cambiar "Nombres de usuario y contraseñas en formularios" ni "Preguntar si se guardan las contraseñas". Se desactivará la característica Autocompletar para nombres de usuario y contraseñas en formularios. El usuario tampoco puede optar porque se le pregunte si se guardan las contraseñas. Si no establece esta configuración, los usuarios tendrán la libertad de activar Autocompletar para nombres de usuario y contraseñas en los formularios y la opción de preguntar si quieren guardar las contraseñas. Para mostrar esta opción, los usuarios deben abrir el cuadro de diálogo Opciones de Internet, hacer clic en la pestaña Contenido y hacer clic en el botón Configuración.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer internet zone allow vbscript to run** (Permitir que VBScript se ejecute en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar si VBScript se puede ejecutar en las páginas de zonas específicas de Internet Explorer. Las opciones son: 
  - *Habilitar*: VBScript se ejecuta en páginas de zonas específicas sin la intervención del usuario. 
  - *Preguntar*: se consultará con los empleados si quieren permitir la ejecución de VBScript en la zona. 
  - *Deshabilitar*: se impide que VBScript se ejecute en la zona. Si deshabilita o no establece esta configuración de directiva, VBScript se ejecuta en la zona especificada sin ninguna interacción. 
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls** (Permitir que solo los dominios aprobados usen controles ActiveX de TDC en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva controla si el usuario puede ejecutar el control ActiveX de TDC en sitios web. Si habilita esta configuración de directiva, el control ActiveX de TDC no se ejecutará desde los sitios web de esta zona. Si deshabilita esta configuración de directiva, el control ActiveX de TDC se ejecutará desde todos los sitios de esta zona.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls** (No ejecutar antimalware en los controles ActiveX de la zona de sitios de confianza de Internet Explorer)  
  Esta configuración de directiva determina si Internet Explorer ejecuta programas antimalware en controles ActiveX con objeto de comprobar si es seguro cargarlos en las páginas. Si habilita esta configuración de directiva, Internet Explorer no comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX de forma segura. Si deshabilita esta configuración de directiva, Internet Explorer siempre comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX con seguridad. Si no se establece esta configuración de directiva, Internet Explorer siempre comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX de forma segura. Los usuarios pueden activar o desactivar este comportamiento por medio de las opciones de seguridad de Internet Explorer.
  
  **Valor predeterminado**: Deshabilitado 
  
- **Internet Explorer local machine zone java permissions** (Permisos de Java de la zona Equipo local de Internet Explorer)  
  Esta configuración de directiva permite administrar los permisos para applets Java. Si habilita esta configuración de directiva, podrá elegir una opción del cuadro desplegable. Personalizado, para controlar la configuración de permisos individualmente. Seguridad baja habilita a los applets para realizar todas las operaciones. Seguridad media habilita a los applets para ejecutarse en su espacio aislado (un área de memoria fuera de la cual el programa no puede hacer llamadas), además de funcionalidades como espacio de desecho (un área de almacenamiento segura en el equipo cliente) y E/S de archivos controlada por usuario. Seguridad alta habilita a los applets para ejecutarse en su espacio aislado. Deshabilite Java para impedir la ejecución de los applets. Si deshabilita esta configuración de directiva, los applets Java no se ejecutarán. Si no establece esta configuración de directiva, el permiso se establece como Seguridad media.
  
  **Valor predeterminado**: Deshabilitar Java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls** (No ejecutar antimalware en los controles ActiveX de la zona de intranet de Internet Explorer) Esta configuración de directiva determina si Internet Explorer ejecuta programas antimalware en controles ActiveX con objeto de comprobar si es seguro cargarlos en las páginas. Si habilita esta configuración de directiva, Internet Explorer no comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX de forma segura. Si deshabilita esta configuración de directiva, Internet Explorer siempre comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX con seguridad. Si no se establece esta configuración de directiva, Internet Explorer no comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX de forma segura. Los usuarios pueden activar o desactivar este comportamiento por medio de las opciones de seguridad de Internet Explorer.
  
  **Valor predeterminado**: Deshabilitado  

- **Scriptlets de zona de sitios restringidos de Internet Explorer**  
  Esta configuración de directiva permite administrar si el usuario puede ejecutar scriptlets. Si habilita esta configuración de directiva, el usuario puede ejecutar scriptlets. Si deshabilita esta configuración de directiva, el usuario no puede ejecutar scriptlets. Si no establece esta configuración de directiva, el usuario puede habilitar o deshabilitar los scriptlets.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer processes notification bar** (Barra de notificación para procesos de Internet Explorer)  
  Esta configuración de directiva permite administrar si se muestra la barra de notificación para procesos de Internet Explorer cuando las instalaciones de archivos o código están restringidas. De forma predeterminada, la barra de notificación se muestra para procesos de Internet Explorer. Si habilita esta configuración de directiva, la barra de notificación se muestra para Procesos de Internet Explorer. Si deshabilita esta configuración de directiva, la barra de notificación no se mostrará para procesos de Internet Explorer. Si no establece esta configuración de directiva, la barra de notificación no se muestra para procesos de Internet Explorer.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer internet zone download signed Active X controls** (Descargar controles ActiveX firmados de la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar si los usuarios pueden descargar controles ActiveX firmados de una página en la zona. Si habilita esta directiva, los usuarios podrán descargar controles firmados sin solicitarles su intervención. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si se pueden descargar controles firmados por editores que no son de confianza. El código firmado por editores de confianza se descarga en modo silencioso. Si deshabilita la configuración de directiva, no se podrán descargar los controles firmados. Si no establece esta configuración de directiva, se consultará con los usuarios si se pueden descargar controles firmados por editores que no son de confianza. El código firmado por editores de confianza se descarga en modo silencioso.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone smart screen** (SmartScreen de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva controla si el filtro SmartScreen examina las páginas de la zona para detectar contenido malintencionado. Si habilita esta configuración de directiva, el filtro SmartScreen examina las páginas de la zona para detectar contenido malintencionado. Si deshabilita esta configuración de directiva, el filtro SmartScreen no examina las páginas de la zona para detectar contenido malintencionado. Si no establece esta configuración de directiva, el usuario puede elegir si el filtro SmartScreen examina las páginas de esta zona para detectar contenido malintencionado. Nota: En Internet Explorer 7, esta configuración de directiva controla si el filtro de suplantación de identidad examina las páginas de esta zona para detectar contenido malintencionado.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer remove run this time button for outdated Active X controls** (Quitar el botón Ejecutar esta vez para los controles ActiveX obsoletos de Internet Explorer)  
  Esta configuración de directiva permite impedir que los usuarios vean el botón "Ejecutar esta vez" y ejecuten determinados controles ActiveX obsoletos en Internet Explorer. Si habilita esta configuración de directiva, los usuarios no verán el botón "Ejecutar esta vez" en el mensaje de advertencia que aparece cuando Internet Explorer bloquea un control ActiveX obsoleto. Si deshabilita o no establece esta configuración de directiva, los usuarios verán el botón "Ejecutar esta vez" en el mensaje de advertencia que aparece cuando Internet Explorer bloquea un control ActiveX obsoleto. Este botón permite al usuario ejecutar el control ActiveX obsoleto una vez. Para más información, vea "Controles ActiveX obsoletos" en la biblioteca de TechNet de Internet Explorer.
  
  **Valor predeterminado**: Habilitado 
  
- **Internet Explorer internet zone launch applications and files in an iframe** (Iniciar aplicaciones y archivos en un iFrame en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar si se pueden ejecutar aplicaciones y descargar archivos de una referencia IFRAME en el código HTML de las páginas de esta zona. Si habilita esta configuración de directiva, los usuarios podrán ejecutar aplicaciones y descargar archivos desde IFRAME en las páginas de esta zona sin pedirles su intervención. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren ejecutar aplicaciones y descargar archivos desde IFRAME en las páginas de esta zona. Si deshabilita esta configuración de directiva, se impedirá que los usuarios ejecuten aplicaciones y descarguen archivos desde IFRAME en las páginas de esta zona. Si no establece esta configuración de directiva, se consultará con los usuarios si quieren ejecutar aplicaciones y descargar archivos desde IFRAME en las páginas de esta zona.
  
  **Valor predeterminado**: Deshabilitar 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains** (Navegar por ventanas y marcos de diferentes dominios en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite establecer las opciones para arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Si habilita esta configuración de directiva y hace clic en Habilitar, los usuarios podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios no pueden cambiar esta configuración. Si habilita esta configuración de directiva y hace clic en Deshabilitar, los usuarios no podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios no pueden cambiar esta configuración. En Internet Explorer 10, si deshabilita o no establece esta configuración de directiva, los usuarios no podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios pueden cambiar esta configuración en el cuadro de diálogo Opciones de Internet. En Internet Explorer 9 y versiones anteriores, si deshabilita o no configura esta directiva, los usuarios podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios no pueden cambiar esta configuración.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer internet zone smart screen** (SmartScreen de la zona de Internet de Internet Explorer)  
  Esta configuración de directiva controla si el filtro SmartScreen examina las páginas de la zona para detectar contenido malintencionado. Si habilita esta configuración de directiva, el filtro SmartScreen examina las páginas de la zona para detectar contenido malintencionado. Si deshabilita esta configuración de directiva, el filtro SmartScreen no examina las páginas de la zona para detectar contenido malintencionado. Si no establece esta configuración de directiva, el usuario puede elegir si el filtro SmartScreen examina las páginas de esta zona para detectar contenido malintencionado. Nota: En Internet Explorer 7, esta configuración de directiva controla si el filtro de suplantación de identidad examina las páginas de esta zona para detectar contenido malintencionado.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer locked down trusted zone java permissions** (Bloqueo de permisos de Java en la zona de sitios de confianza de Internet Explorer)  
  Esta configuración de directiva permite administrar los permisos para applets Java. Si habilita esta configuración de directiva, podrá elegir una opción del cuadro desplegable. Personalizado, para controlar la configuración de permisos individualmente. Seguridad baja habilita a los applets para realizar todas las operaciones. Seguridad media habilita a los applets para ejecutarse en su espacio aislado (un área de memoria fuera de la cual el programa no puede hacer llamadas), además de funcionalidades como espacio de desecho (un área de almacenamiento segura en el equipo cliente) y E/S de archivos controlada por usuario. Seguridad alta habilita a los applets para ejecutarse en su espacio aislado. Deshabilite Java para impedir la ejecución de los applets. Si deshabilita esta configuración de directiva, los applets Java no se ejecutarán. Si no establece esta configuración de directiva, los applets Java se deshabilitan.
  
  **Valor predeterminado**: Deshabilitar Java 
  
- **Internet Explorer check signatures on downloaded programs** (Comprobar las firmas de los programas descargados de Internet Explorer)  
  Esta configuración de directiva permite administrar si Internet Explorer debe comprobar las firmas digitales (lo que sirve para identificar el editor de software firmado y comprobar que no se ha modificado ni alterado) en los equipos de los usuarios antes de descargar programas ejecutables. Si habilita esta configuración de directiva, Internet Explorer comprobará las firmas digitales de los programas ejecutables y mostrará sus identidades antes de descargarlas en los equipos de los usuarios. Si deshabilita esta configuración de directiva, Internet Explorer no comprobará las firmas digitales de los programas ejecutables ni mostrará sus identidades antes de descargarlas en los equipos de los usuarios. Si no establece esta configuración de directiva, Internet Explorer no comprobará las firmas digitales de los programas ejecutables ni mostrará sus identidades antes de descargarlas en los equipos de los usuarios.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer restricted zone scripting of web browser controls** (Scripting de controles de explorador web en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva determina si una página puede controlar los controles WebBrowser insertados mediante scripts. Si habilita esta configuración de directiva, se permite el acceso por scripts al control WebBrowser. Si deshabilita esta configuración de directiva, no se permite el acceso por scripts al control WebBrowser. Si no establece esta configuración de directiva, el usuario puede habilitar o deshabilitar el acceso por scripts al control WebBrowser. De manera predeterminada, el acceso por scripts al control WebBrowser solo se permite en las zonas Intranet y Equipo local.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer restricted zone cross site scripting filter** (Filtro de scripts de sitios de la zona de sitios restringidos de Internet Explorer)  
  Esta directiva controla si el filtro de scripts de sitios (XSS) detectará e impedirá la inserción de scripts de sitios en los sitios web de esta zona. Si habilita esta configuración de directiva, el filtro XSS se activa para los sitios de esta zona y el filtro XSS intenta bloquear las inserciones de scripts de sitios. Si deshabilita esta configuración de directiva, el filtro XSS se desactiva para los sitios de esta zona e Internet Explorer permite las inserciones de scripts de sitios.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer restricted zone binary and script behaviors** (Comportamientos de binarios y scripts de la zona de sitios restringidos de Internet Explorer)  
  Esta directiva permite administrar los comportamientos de binarios y scripts dinámicos: componentes que encapsulan funcionalidad específica para elementos HTML a los que están conectados. Si habilita esta configuración de directiva, los comportamientos de binarios y scripts estarán disponibles. Si selecciona Aprobados por el administrador en el cuadro desplegable, únicamente estarán disponibles los comportamientos mostrados en Comportamientos aprobados por el administrador en la directiva Restricción de seguridad del comportamiento binario. Si deshabilita esta configuración de directiva, ningún comportamiento binario y de scripts estará disponible a menos que las aplicaciones tengan implementado un administrador de seguridad personalizado. Si no establece esta configuración de directiva, ningún comportamiento binario y de scripts estará disponible a menos que las aplicaciones tengan implementado un administrador de seguridad personalizado.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer security settings check** (Comprobación de la configuración de seguridad de Internet Explorer)  
  Esta configuración de directiva desactiva la característica de comprobación de la configuración de seguridad, que comprueba la configuración de seguridad de Internet Explorer para determinar cuándo la configuración pone en peligro a Internet Explorer. Si habilita esta configuración de directiva, se desactiva la característica. Si deshabilita o no establece esta configuración de directiva, se activa la característica.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer internet zone security warning for potentially unsafe files** (Advertencia de seguridad de la zona de Internet de Internet Explorer para archivos potencialmente no seguros)  
  Esta configuración de directiva controla si el mensaje "Abrir archivo: advertencia de seguridad" aparece cuando el usuario intenta abrir archivos ejecutables u otros archivos que puedan no ser seguros (por ejemplo, desde un recurso compartido de archivos de intranet mediante el Explorador de archivos). Si habilita esta configuración de directiva y establece el cuadro desplegable en Habilitar, estos archivos se abren sin una advertencia de seguridad. Si establece el cuadro desplegable en Preguntar, aparece una advertencia de seguridad antes de que se abra el archivo. Si deshabilita esta configuración de directiva, estos archivos no se abren. Si no establece esta configuración de directiva, el usuario puede configurar cómo controla el equipo estos archivos. De manera predeterminada, estos archivos están bloqueados en la zona Sitios restringidos, habilitados en las zonas Intranet y Equipo local, y establecidos en Preguntar en las zonas Internet y Sitios de confianza.
  
  **Valor predeterminado**: Preguntar  
  
- **Internet Explorer intranet zone java permissions** (Permisos de Java en la zona Intranet de Internet Explorer)  
  Esta configuración de directiva permite administrar los permisos para applets Java. Si habilita esta configuración de directiva, podrá elegir una opción del cuadro desplegable. Personalizado, para controlar la configuración de permisos individualmente. Seguridad baja habilita a los applets para realizar todas las operaciones. Seguridad media habilita a los applets para ejecutarse en su espacio aislado (un área de memoria fuera de la cual el programa no puede hacer llamadas), además de funcionalidades como espacio de desecho (un área de almacenamiento segura en el equipo cliente) y E/S de archivos controlada por usuario. Seguridad alta habilita a los applets para ejecutarse en su espacio aislado. Deshabilite Java para impedir la ejecución de los applets. Si deshabilita esta configuración de directiva, los applets Java no se ejecutarán. Si no establece esta configuración de directiva, el permiso se establece como Seguridad media.
  
  **Valor predeterminado**: Seguridad alta 
  
- **Internet Explorer block outdated Active X controls** (Bloqueo de controles ActiveX obsoletos de Internet Explorer)  </br>
  Esta configuración de directiva determina si Internet Explorer bloquea determinados controles ActiveX obsoletos. Nunca se bloquean los controles ActiveX obsoletos en la zona Intranet. Si habilita esta configuración de directiva, Internet Explorer dejará de bloquear los controles ActiveX obsoletos. Si deshabilita o no establece esta configuración de directiva, Internet Explorer seguirá bloqueando determinados controles ActiveX obsoletos. Para más información, vea "Controles ActiveX obsoletos" en la biblioteca de TechNet de Internet Explorer.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer restricted zone popup blocker** (Bloqueador de ventanas emergentes de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si se muestran las ventanas emergentes no deseadas. Las ventanas emergentes que se abren cuando el usuario final hace clic en un vínculo no se bloquean. Si habilita esta configuración de directiva, se impide que se muestre la mayoría de las ventanas emergentes no deseadas. Si deshabilita esta configuración de directiva, no se impide la aparición de ventanas emergentes. Si no establece esta configuración de directiva, se impide que se muestre la mayoría de las ventanas emergentes no deseadas.
  
  **Valor predeterminado**: Habilitar  
  
- **Internet Explorer processes MK protocol security restriction** (Restricción de seguridad del protocolo MK de procesos de Internet Explorer)  
  La configuración de directiva Restricción de seguridad del protocolo MK reduce el área expuesta a ataques al impedir el uso del protocolo MK. Se producirá un error en los recursos hospedados en el protocolo MK. Si habilita esta configuración de directiva, se impide el uso del protocolo MK para el Explorador de archivos e Internet Explorer, y se producirá un error en los recursos hospedados en el protocolo MK. Si deshabilita esta configuración de directiva, las aplicaciones pueden usar la API del protocolo MK. Los recursos hospedados en el protocolo MK funcionarán para los procesos del Explorador de archivos e Internet Explorer. Si no establece esta configuración de directiva, se impide el uso del protocolo MK para el Explorador de archivos e Internet Explorer, y se producirá un error en los recursos hospedados en el protocolo MK.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer trusted zone java permissions** (Permisos de Java en la zona de sitios de confianza de Internet Explorer)  </br>
  Esta configuración de directiva permite administrar los permisos para applets Java. Si habilita esta configuración de directiva, podrá elegir una opción del cuadro desplegable. Personalizado, para controlar la configuración de permisos individualmente. Seguridad baja habilita a los applets para realizar todas las operaciones. Seguridad media habilita a los applets para ejecutarse en su espacio aislado (un área de memoria fuera de la cual el programa no puede hacer llamadas), además de funcionalidades como espacio de desecho (un área de almacenamiento segura en el equipo cliente) y E/S de archivos controlada por usuario. Seguridad alta habilita a los applets para ejecutarse en su espacio aislado. Deshabilite Java para impedir la ejecución de los applets. Si deshabilita esta configuración de directiva, los applets Java no se ejecutarán. Si no establece esta configuración de directiva, el permiso se establece como Seguridad baja.
  
  **Valor predeterminado**: Seguridad alta  
  
- **Internet Explorer restricted zone scripting of java applets** (Scripting de applets Java en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si los applets se exponen a scripts dentro de la zona. Si habilita esta configuración de directiva, los scripts podrán acceder a los applets automáticamente, sin la intervención del usuario. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir que los scripts accedan a los applets. Si deshabilita esta configuración de directiva, se impedirá que los scripts accedan a applets. Si no establece esta configuración de directiva, se impedirá que los scripts accedan a applets.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer locked down restricted zone java permissions** (Bloqueo de permisos de Java en la zona de sitios restringidos de Internet Explorer)  </br>
  Esta configuración de directiva permite administrar los permisos para applets Java. Si habilita esta configuración de directiva, podrá elegir una opción del cuadro desplegable. Personalizado, para controlar la configuración de permisos individualmente. Seguridad baja habilita a los applets para realizar todas las operaciones. Seguridad media habilita a los applets para ejecutarse en su espacio aislado (un área de memoria fuera de la cual el programa no puede hacer llamadas), además de funcionalidades como espacio de desecho (un área de almacenamiento segura en el equipo cliente) y E/S de archivos controlada por usuario. Seguridad alta habilita a los applets para ejecutarse en su espacio aislado. Deshabilite Java para impedir la ejecución de los applets. Si deshabilita esta configuración de directiva, los applets Java no se ejecutarán. Si no establece esta configuración de directiva, los applets Java se deshabilitan.
  
  **Valor predeterminado**: Deshabilitar Java 
  
- **Internet Explorer internet zone allow only approved domains to use Active X controls** (Permitir que solo los dominios aprobados usen controles ActiveX en la zona de Internet de Internet Explorer)  </br>
  Esta configuración de directiva controla si se le pide al usuario que permita la ejecución de los controles ActiveX en sitios web distintos al sitio web que ha instalado el control ActiveX. Si habilita esta configuración de directiva, el usuario debe confirmar si permite la ejecución de los controles ActiveX desde sitios web en esta zona. El usuario puede permitir que el control se ejecute desde el sitio actual, o bien desde todos los sitios. Si deshabilita esta configuración de directiva, el usuario no ve el mensaje de ActiveX por sitio, y los controles ActiveX pueden ejecutarse desde todos los sitios de esta zona.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer include all network paths** (Incluir todas las rutas de acceso de red de Internet Explorer)  
  Incluir todas las rutas de acceso de red de Internet Explorer
  
  **Valor predeterminado**: Deshabilitado 
  
- **Internet Explorer internet zone protected mode** (Modo protegido de la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite activar el modo protegido. El modo protegido ayuda a proteger los puntos vulnerables y susceptibles de ataque de Internet Explorer mediante la reducción de las ubicaciones en las que Internet Explorer puede escribir en el Registro y en el sistema de archivos. Si habilita esta configuración de directiva, se activa el modo protegido. El usuario no puede desactivar el modo protegido. Si deshabilita esta configuración de directiva, se desactiva el modo protegido. El usuario no puede activar el modo protegido. Si no establece esta configuración de directiva, el usuario puede activar o desactivar el modo protegido.
  
  **Valor predeterminado**: Habilitar 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe** (Inicializar e incluir en scripts controles ActiveX no marcados como seguros en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar los controles ActiveX no marcados como seguros. Si habilita esta configuración de directiva, los controles ActiveX se ejecutarán, se cargarán con parámetros y se incluirán en scripts sin establecer la seguridad de objetos para los datos o scripts que no sean de confianza. Esta configuración no se recomienda, excepto para zonas seguras y administradas. Esta configuración hace que los controles seguros y no seguros se inicialicen y se activen los scripts, omitiendo la opción "Generar scripts de los controles ActiveX marcados como seguros para scripts". Si habilita esta configuración de directiva y selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir que el control se cargue con parámetros o se activen los scripts. Si deshabilita esta configuración de directiva, ningún control ActiveX que no pueda hacerse seguro se cargará con parámetros ni se activarán los scripts. Si no establece esta configuración de directiva, ningún control ActiveX que no pueda hacerse seguro se cargará con parámetros ni se activarán los scripts.
  
  **Valor predeterminado**: Deshabilitar 
  
- **Internet Explorer restricted zone smart screen** (Bloquear SmartScreen en la zona de sitios restringidos de Internet Explorer)  </br>
  Esta configuración de directiva controla si el filtro SmartScreen examina las páginas de la zona para detectar contenido malintencionado. Si habilita esta configuración de directiva, el filtro SmartScreen examina las páginas de la zona para detectar contenido malintencionado. Si deshabilita esta configuración de directiva, el filtro SmartScreen no examina las páginas de la zona para detectar contenido malintencionado. Si no establece esta configuración de directiva, el usuario puede elegir si el filtro SmartScreen examina las páginas de esta zona para detectar contenido malintencionado. Nota: En Internet Explorer 7, esta configuración de directiva controla si el filtro de suplantación de identidad examina las páginas de esta zona para detectar contenido malintencionado.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer crash detection** (Detección de bloqueos de Internet Explorer)  
  Esta configuración de directiva permite administrar la característica de detección de bloqueos de Administración de complementos. Si habilita esta configuración de directiva, los bloqueos en Internet Explorer tendrán el comportamiento de Windows XP Professional Service Pack 1 y versiones anteriores, que es invocar Informes de errores de Windows. Todas las configuraciones de directiva para Informes de errores de Windows se seguirán aplicando. Si deshabilita o no establece esta configuración de directiva, la característica de detección de bloqueos de Administración de complementos sigue funcionando.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer internet zone java permissions** (Permisos de Java en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar los permisos para applets Java. Si habilita esta configuración de directiva, podrá elegir una opción del cuadro desplegable. Personalizado, para controlar la configuración de permisos individualmente. Seguridad baja habilita a los applets para realizar todas las operaciones. Seguridad media habilita a los applets para ejecutarse en su espacio aislado (un área de memoria fuera de la cual el programa no puede hacer llamadas), además de funcionalidades como espacio de desecho (un área de almacenamiento segura en el equipo cliente) y E/S de archivos controlada por usuario. Seguridad alta habilita a los applets para ejecutarse en su espacio aislado. Deshabilite Java para impedir la ejecución de los applets. Si deshabilita esta configuración de directiva, los applets Java no se ejecutarán. Si no establece esta configuración de directiva, el permiso se establece como Seguridad alta.
  
  **Valor predeterminado**: Deshabilitar Java  
  
- **Internet Explorer restricted zone active scripting** (Activar scripting de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si se ejecuta código de script en páginas de la zona. Si habilita esta configuración de directiva, el código de script se podrá ejecutar automáticamente en páginas de la zona. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir la ejecución de código de script en páginas de la zona. Si deshabilita esta configuración de directiva, se impedirá la ejecución de código de script en páginas de la zona. Si no establece esta configuración de directiva, se impedirá la ejecución de código de script en páginas de la zona.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer internet zone logon options** (Opciones de inicio de sesión de la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar la configuración de las opciones de inicio de sesión. Si habilita esta configuración de directiva, puede elegir una de las opciones de inicio de sesión siguientes. Inicio de sesión anónimo para deshabilitar la autenticación HTTP y usar la cuenta de invitado solo para el protocolo de Sistema de archivos de Internet común (CIFS). Preguntar por el nombre de usuario y la contraseña para consultar al usuario sobre los id. de usuario y contraseñas. Después de consultar al usuario, estos valores se pueden usar de modo silencioso en lo que resta de la sesión. Inicio de sesión automático solo en la zona Intranet para consultar al usuario sobre los id. de usuario y contraseñas en otras zonas. Después de la consulta, estos valores se pueden usar de modo silencioso en lo que resta de la sesión. Inicio de sesión automático con el nombre de usuario y contraseña actuales para intentar el inicio de sesión mediante la Respuesta de desafío de autenticación Windows NT (conocida también como autenticación NTLM). Si el servidor es compatible con la Respuesta de desafío de autenticación Windows NT, el inicio de sesión usará el nombre de usuario y la contraseña de red del usuario para iniciar la sesión. Si el servidor no es compatible con la respuesta de desafío de Windows NT, se consultará al usuario para que proporcione el nombre de usuario y la contraseña. Si deshabilita esta configuración de directiva, el inicio de sesión se establece en Inicio de sesión automático solo en la zona Intranet. Si no establece esta configuración de directiva, el inicio de sesión se establece en Inicio de sesión automático solo en la zona Intranet.
  
  **Valor predeterminado**: Preguntar  
  
- **Internet Explorer restricted zone allow vbscript to run** (Permitir que VBScript se ejecute en la zona de sitios restringidos de Internet Explorer)  </br>  
  Esta configuración de directiva le permite administrar si VBScript puede ejecutarse en las páginas de la zona especificada en Internet Explorer. Si se selecciona Habilitar en el cuadro desplegable, VBScript podrá ejecutarse sin la intervención del usuario. Si se selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir la ejecución de VBScript. Si se selecciona Deshabilitar en el cuadro desplegable, se impedirá que VBScript se ejecute. Si no establece o deshabilita esta configuración de directiva, VBScript no podrá ejecutarse.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer internet zone drag content from different domains across windows** (Arrastrar contenido de diferentes dominios entre ventanas a la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite establecer las opciones para arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Si habilita esta configuración de directiva y hace clic en Habilitar, los usuarios podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios no pueden cambiar esta configuración. Si habilita esta configuración de directiva y hace clic en Deshabilitar, los usuarios no podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios no pueden cambiar esta configuración. En Internet Explorer 10, si deshabilita o no establece esta configuración de directiva, los usuarios no podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios pueden cambiar esta configuración en el cuadro de diálogo Opciones de Internet. En Internet Explorer 9 y versiones anteriores, si deshabilita o no configura esta directiva, los usuarios podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios no pueden cambiar esta configuración.
  
  **Valor predeterminado**: Deshabilitado 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe** (Inicializar e incluir en scripts controles ActiveX no marcados como seguros en la zona Intranet de Internet Explorer)  
  Esta configuración de directiva permite administrar los controles ActiveX no marcados como seguros. Si habilita esta configuración de directiva, los controles ActiveX se ejecutarán, se cargarán con parámetros y se incluirán en scripts sin establecer la seguridad de objetos para los datos o scripts que no sean de confianza. Esta configuración no se recomienda, excepto para zonas seguras y administradas. Esta configuración hace que los controles seguros y no seguros se inicialicen y se activen los scripts, omitiendo la opción "Generar scripts de los controles ActiveX marcados como seguros para scripts". Si habilita esta configuración de directiva y selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir que el control se cargue con parámetros o se activen los scripts. Si deshabilita esta configuración de directiva, ningún control ActiveX que no pueda hacerse seguro se cargará con parámetros ni se activarán los scripts. Si no establece esta configuración de directiva, ningún control ActiveX que no pueda hacerse seguro se cargará con parámetros ni se activarán los scripts.
  
  **Valor predeterminado**: Deshabilitar 
  
- **Internet Explorer download enclosures** (Descargar caracteres enmarcados de Internet Explorer)  
  Esta configuración de directiva impide que el usuario descargue caracteres enmarcados (datos adjuntos) desde una fuente al equipo del usuario. Si habilita esta configuración de directiva, el usuario no puede configurar el motor de sincronización de fuentes para que descargue caracteres enmarcados a través de la página de propiedades de fuente. Los desarrolladores no pueden cambiar la opción de descarga por medio de las API de fuentes. Si deshabilita o no establece esta configuración de directiva, el usuario puede configurar el motor de sincronización de fuentes para que descargue caracteres enmarcados a través de la página de propiedades de fuente. Los desarrolladores pueden cambiar la opción de descarga por medio de las API de fuentes.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer restricted zone download unsigned Active X controls** (Descargar controles ActiveX sin firmar de la zona de sitios restringidos de Internet Explorer)  </br>
  Esta configuración de directiva le permite administrar si los usuarios pueden descargar controles ActiveX sin firmar de la zona. Dicho código es potencialmente dañino, más aún si proviene de una zona que no es de confianza. Si habilita esta configuración de directiva, los usuarios podrán ejecutar controles sin firmar sin solicitarles la intervención. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir la ejecución de controles sin firmar. Si deshabilita esta configuración de directiva, los usuarios no podrán ejecutar controles sin firmar. Si no establece esta configuración de directiva, los usuarios no podrán ejecutar controles sin firmar.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer internet zone drag content from different domains within windows** (Arrastrar contenido de diferentes dominios de ventanas de la zona de Internet de Internet Explorer)  
  Esta configuración de directiva le permite administrar si los usuarios pueden descargar controles ActiveX sin firmar de la zona. Dicho código es potencialmente dañino, más aún si proviene de una zona que no es de confianza. Si habilita esta configuración de directiva, los usuarios podrán ejecutar controles sin firmar sin solicitarles la intervención. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir la ejecución de controles sin firmar. Si deshabilita esta configuración de directiva, los usuarios no podrán ejecutar controles sin firmar. Si no establece esta configuración de directiva, los usuarios no podrán ejecutar controles sin firmar.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer processes restrict Active X install** (Restringir la instalación de ActiveX para los procesos de Internet Explorer)  </br>
  Esta configuración de directiva permite que las aplicaciones que tienen el Control del Explorador web bloqueen la intervención automática de usuario para instalar controles ActiveX. Si habilita esta configuración de directiva, el Control del Explorador web bloqueará la intervención de usuario automática en la instalación de controles ActiveX para todos los procesos. Si deshabilita o no establece esta configuración de directiva, el Control del Explorador web no bloqueará la intervención de usuario automática en la instalación de controles ActiveX para todos los procesos.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer internet zone scriptlets** (Scriptlets de la zona de Internet de Internet Explorer) Esta configuración de directiva permite administrar si el usuario puede ejecutar scriptlets. Si habilita esta configuración de directiva, el usuario puede ejecutar scriptlets. Si deshabilita esta configuración de directiva, el usuario no puede ejecutar scriptlets. Si no establece esta configuración de directiva, el usuario puede habilitar o deshabilitar los scriptlets.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files** (Arrastrar y colocar, o copiar y pegar archivos en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva le permite administrar si los usuarios pueden arrastrar o copiar y pegar archivos de un origen dentro de la zona. Si habilita esta configuración de directiva, los usuarios podrán automáticamente arrastrar o copiar y pegar archivos de esta zona. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren arrastrar o copiar archivos de esta zona. Si deshabilita esta configuración de directiva, se impedirá que los usuarios arrastren, copien y peguen archivos de esta zona. Si no establece esta configuración de directiva, se consultará con los usuarios si quieren arrastrar o copiar archivos de esta zona.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer software when signature is invalid** (Software de Internet Explorer cuando la firma no es válida) </br>
  Esta configuración de directiva permite administrar si el usuario puede instalar o ejecutar software, como controles ActiveX y descargas de archivos, aunque la firma no sea válida. Es posible que una firma no válida indique que alguien ha manipulado el archivo. Si habilita esta configuración de directiva, se le pregunta a los usuarios si quieren instalar o ejecutar archivos con una firma no válida. Si deshabilita esta configuración de directiva, los usuarios no podrán instalar o ejecutar archivos con una firma no válida. Si no establece esta configuración de directiva, los usuarios pueden elegir si instalan o ejecutan archivos con una firma no válida.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer restricted zone copy and paste via script** (Copiar y pegar mediante scripts en la zona de sitios restringidos de Internet Explorer) </br> Esta configuración de directiva permite administrar si los scripts pueden realizar operaciones del Portapapeles (por ejemplo, cortar, copiar y pegar) en una región especificada. Si habilita esta configuración de directiva, los scripts podrán realizar operaciones de Portapapeles. Si selecciona Preguntar en el cuadro desplegable, se consulta con los usuarios si se pueden realizar operaciones de Portapapeles. Si deshabilita esta configuración de directiva, ningún script podrá realizar operaciones de Portapapeles. Si no establece esta configuración de directiva, ningún script podrá realizar operaciones de Portapapeles.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone drag content from different domains across windows** (Arrastrar contenido de diferentes dominios entre ventanas en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite establecer las opciones para arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Si habilita esta configuración de directiva y hace clic en Habilitar, los usuarios podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios no pueden cambiar esta configuración. Si habilita esta configuración de directiva y hace clic en Deshabilitar, los usuarios no podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios no pueden cambiar esta configuración. En Internet Explorer 10, si deshabilita o no establece esta configuración de directiva, los usuarios no podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios pueden cambiar esta configuración en el cuadro de diálogo Opciones de Internet. En Internet Explorer 9 y versiones anteriores, si deshabilita o no configura esta directiva, los usuarios podrán arrastrar contenido entre diferentes dominios cuando el origen y el destino se encuentren en diferentes ventanas. Los usuarios no pueden cambiar esta configuración.  <br><br>
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer users adding sites** (Los usuarios agregan sitios de Internet Explorer)  
  Impide que los usuarios agreguen o quiten sitios de las zonas de seguridad. Una zona de seguridad es un grupo de sitios web con el mismo nivel de seguridad. Si habilita esta directiva, se deshabilitará la configuración de administración de sitios para zonas de seguridad. (Para ver la configuración de administración de sitios para zonas de seguridad, en el cuadro de diálogo de Opciones de Internet, haga clic en la pestaña Seguridad y haga clic en el botón Sitios). Si deshabilita o no establece esta directiva, los usuarios podrán agregar o quitar sitios web de las zonas de sitios de confianza y sitios restringidos, y modificar la configuración de la zona Intranet local. Esta directiva impide que los usuarios cambien la configuración de la administración de sitios para zonas de seguridad establecida por el administrador. Nota: La directiva "Deshabilitar la página Seguridad" (ubicada en \Configuración de usuario\Plantillas administrativas\Componentes de Windows\Internet Explorer\Panel de control Internet), que quita la pestaña Seguridad de la interfaz, tiene prioridad sobre esta directiva. Si está habilitada, esta directiva se omite. Además, vea también la directiva "Zonas de seguridad: usar solo la configuración del equipo".
  
  **Valor predeterminado**: Deshabilitado  
  
- **Ventanas iniciadas por scripts de la zona de Internet de Internet Explorer**  
  Esta configuración de directiva permite administrar las restricciones sobre ventanas emergentes iniciadas por scripts y sobre ventanas que incluyen la barra de título y estado. Si habilita esta directiva, la seguridad de restricciones de ventanas no se aplicará en esta zona. La zona de seguridad se ejecutará sin la capa agregada de seguridad proporcionada por esta característica. Si deshabilita esta configuración de directiva, no se podrán ejecutar las acciones potencialmente dañinas contenidas en las ventanas emergentes iniciadas por scripts y en las ventanas que incluyen la barra de título y estado. Esta característica de seguridad de Internet Explorer está activada en esta zona como lo indica el control de la característica Restricciones de seguridad de ventanas con scripts para el proceso. Si no establece esta configuración de directiva, no se podrán ejecutar las acciones posiblemente dañinas contenidas en las ventanas emergentes iniciadas por scripts y en las ventanas que incluyen la barra de título y estado. Esta característica de seguridad de Internet Explorer está activada en esta zona como lo indica el control de la característica Restricciones de seguridad de ventanas con scripts para el proceso.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer security zones use only machine settings** (Usar solo la configuración del equipo de zonas de seguridad de Internet Explorer)  
  Aplica la información de zona de seguridad a todos los usuarios del mismo equipo. Una zona de seguridad es un grupo de sitios web con el mismo nivel de seguridad. Si habilita esta directiva, los cambios que realice el usuario en la zona de seguridad se aplicarán a todos los usuarios del equipo. Si deshabilita esta directiva o no la configura, los usuarios del mismo equipo pueden establecer su propia configuración de zona de seguridad. Use esta directiva para garantizar que la configuración de la zona de seguridad se aplique uniformemente al mismo equipo y no varíe de un usuario a otro. Vea también la directiva "Zonas de seguridad: no permitir a los usuarios cambiar las directivas".
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer locked down local machine zone java permissions** (Bloqueo de permisos de Java en la zona Equipo local de Internet Explorer)  
  Esta configuración de directiva permite administrar los permisos para applets Java. Si habilita esta configuración de directiva, podrá elegir una opción del cuadro desplegable. Personalizado, para controlar la configuración de permisos individualmente. Seguridad baja habilita a los applets para realizar todas las operaciones. Seguridad media habilita a los applets para ejecutarse en su espacio aislado (un área de memoria fuera de la cual el programa no puede hacer llamadas), además de funcionalidades como espacio de desecho (un área de almacenamiento segura en el equipo cliente) y E/S de archivos controlada por usuario. Seguridad alta habilita a los applets para ejecutarse en su espacio aislado. Deshabilite Java para impedir la ejecución de los applets. Si deshabilita esta configuración de directiva, los applets Java no se ejecutarán. Si no establece esta configuración de directiva, los applets Java se deshabilitan.
  
  **Valor predeterminado**: Deshabilitar Java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls** (No ejecutar antimalware en los controles ActiveX de la zona de sitios restringidos de Internet Explorer)  </br>
  Esta configuración de directiva determina si Internet Explorer ejecuta programas antimalware en controles ActiveX con objeto de comprobar si es seguro cargarlos en las páginas. Si habilita esta configuración de directiva, Internet Explorer no comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX de forma segura. Si deshabilita esta configuración de directiva, Internet Explorer siempre comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX con seguridad. Si no se establece esta configuración de directiva, Internet Explorer siempre comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX de forma segura. Los usuarios pueden activar o desactivar este comportamiento por medio de las opciones de seguridad de Internet Explorer.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode** (Ejecutar componentes que dependen de .NET Framework firmados con Authenticode en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si los componentes de .NET Framework firmados con Authenticode se pueden ejecutar en Internet Explorer. Entre esos componentes figuran los controles administrados a los que una etiqueta de objeto hizo referencia y los archivos ejecutables administrados a los que un vínculo hizo referencia. Si habilita esta configuración de directiva, Internet Explorer ejecutará los componentes administrados firmados. Si selecciona Preguntar en el cuadro desplegable, Internet Explorer solicitará la intervención de los usuarios para determinar si se quieren ejecutar los componentes administrados firmados. Si deshabilita esta configuración de directiva, Internet Explorer no ejecutará ningún componente administrado con firma. Si no establece esta configuración de directiva, Internet Explorer no ejecutará ningún componente administrado con firma.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer restricted zone access to data sources** (Acceso a orígenes de datos de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si Internet Explorer puede acceder a datos de otra zona de seguridad con Analizador XML de Microsoft (MSXML) u Objetos de datos ActiveX (ADO). Si habilita esta configuración de directiva, los usuarios podrán cargar una página en la zona que usa MSXML o ADO para acceder a datos de otro sitio en la zona. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir que una página se cargue en la zona que usa MSXML o ADO para acceder a datos de otro sitio de la zona. Si deshabilita esta configuración de directiva, los usuarios no podrán cargar ninguna página en la zona que usa MSXML o ADO para acceder a datos de otro sitio de la zona. Si no establece esta configuración de directiva, los usuarios no podrán cargar ninguna página en la zona que usa MSXML o ADO para acceder a datos de otro sitio de la zona.
  
  **Valor predeterminado**: Deshabilitar 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls** (No ejecutar antimalware en los controles ActiveX de la zona de Internet de Internet Explorer)  </br>
  Esta configuración de directiva determina si Internet Explorer ejecuta programas antimalware en controles ActiveX con objeto de comprobar si es seguro cargarlos en las páginas. Si habilita esta configuración de directiva, Internet Explorer no comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX de forma segura. Si deshabilita esta configuración de directiva, Internet Explorer siempre comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX con seguridad. Si no se establece esta configuración de directiva, Internet Explorer siempre comprobará el programa antimalware para saber si se puede crear una instancia del control ActiveX de forma segura. Los usuarios pueden activar o desactivar este comportamiento por medio de las opciones de seguridad de Internet Explorer.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer internet zone copy and paste via script** (Copiar y pegar mediante scripts en la zona de Internet de Internet Explorer) </br> Esta configuración de directiva permite administrar si los scripts pueden realizar operaciones de Portapapeles (como cortar, copiar y pegar) en una zona especificada. Si habilita esta configuración de directiva, los scripts podrán realizar operaciones de Portapapeles. Si selecciona Preguntar en el cuadro desplegable, se consulta con los usuarios si se pueden realizar operaciones de Portapapeles. Si deshabilita esta configuración de directiva, ningún script podrá realizar operaciones de Portapapeles. Si no establece esta configuración de directiva, ningún script podrá realizar operaciones de Portapapeles.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer use Active X installer service** (Usar el servicio del instalador de ActiveX de Internet Explorer)  </br>
  Esta configuración de directiva permite especificar cómo se deben instalar los controles ActiveX. Si habilita esta configuración de directiva, los controles ActiveX solamente se instalan si el servicio de instalador de ActiveX está presente y si se ha configurado para permitir la instalación de los controles ActiveX. Si deshabilita o no establece esta configuración de directiva, los controles ActiveX, incluidos los controles por usuario, se instalan mediante el proceso de instalación estándar.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer processes protection from zone elevation** (Protección contra la elevación de zona para los procesos de Internet Explorer)  
  Internet Explorer impone restricciones cada vez que abre una página web. Las restricciones dependen de la ubicación de cada página web (zona Internet, Intranet, Equipo local, etc.). Por ejemplo, las páginas web del equipo local son las que tienen menos restricciones de seguridad y están en la zona Equipo local, lo que convierte a esta zona en el objetivo principal de los usuarios malintencionados. Si habilita esta configuración de directiva, todas las zonas podrán protegerse de la elevación de zona para todos los procesos. Si deshabilita o no establece esta configuración de directiva, los procesos que no sean de Internet Explorer o no figuren en la Lista de procesos no recibirán dicha protección.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer internet zone download unsigned Active X controls** (Descargar controles ActiveX sin firmar de la zona de Internet de Internet Explorer)  </br>
  Esta configuración de directiva permite administrar si los usuarios pueden descargar controles ActiveX sin firmar de la zona. Dicho código es potencialmente dañino, más aún si proviene de una zona que no es de confianza. Si habilita esta configuración de directiva, los usuarios podrán ejecutar controles sin firmar sin solicitarles la intervención. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir la ejecución de controles sin firmar. Si deshabilita esta configuración de directiva, los usuarios no podrán ejecutar controles sin firmar. Si no establece esta configuración de directiva, los usuarios no podrán ejecutar controles sin firmar.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer internet zone navigate windows and frames across different domains** (Navegar por ventanas y marcos de diferentes dominios en la zona de Internet de Internet Explorer)  </br>
  Esta configuración de directiva le permite administrar la apertura de ventanas y marcos, y el acceso de aplicaciones a través de dominios distintos. Si habilita esta configuración de directiva, los usuarios podrán abrir ventanas y marcos, y acceder a aplicaciones de otros dominios. Si selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir el acceso de ventanas y marcos a aplicaciones de otros dominios. Si deshabilita esta configuración de directiva, los usuarios no podrán abrir ventanas y marcos para acceder a aplicaciones de otros dominios. Si no establece esta configuración de directiva, los usuarios podrán abrir ventanas y marcos, y acceder a aplicaciones de otros dominios.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer internet zone updates to status bar via script** (Actualizaciones de la barra de estado mediante scripts en la zona de Internet de Internet Explorer)  
  Esta configuración de directiva permite administrar si un script puede actualizar la barra de estado dentro de la zona. Si habilita esta configuración de directiva, los scripts pueden actualizar la barra de estado. Si deshabilita o no establece esta configuración de directiva, no se permite al script actualizar la barra de estado.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer restricted zone include local path when uploading files to server** (Incluir la ruta de acceso local al cargar archivos al servidor en la zona de sitios restringidos de Internet Explorer)  </br> Esta configuración de directiva controla si la información de la ruta de acceso local se envía cuando el usuario carga un archivo por medio de un formulario HTML. Si se envía la información de la ruta de acceso local, es posible que parte de la información sea revelada sin querer al servidor. Por ejemplo, los archivos enviados desde el escritorio del usuario pueden contener el nombre de usuario como parte de la ruta de acceso. Si habilita esta configuración de directiva, la información de la ruta de acceso se envía cuando el usuario carga un archivo por medio de un formulario HTML. Si deshabilita esta configuración de directiva, la información de la ruta de acceso se elimina cuando el usuario carga un archivo por medio de un formulario HTML. Si no establece esta configuración de directiva, el usuario puede elegir si la información de la ruta de acceso se envía cuando cargue un archivo por medio de un formulario HTML. De manera predeterminada, la información de la ruta de acceso se envía.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer processes restrict file download** (Restringir la descarga de archivos para los procesos de Internet Explorer)  </br> Esta configuración de directiva permite que las aplicaciones que tienen el Control del Explorador web bloqueen la intervención automática de usuario para la descarga de archivos no iniciada por el usuario. Si habilita esta configuración de directiva, el Control del Explorador web bloqueará la intervención de usuario automática en la descarga de archivos no iniciada por el usuario para todos los procesos. Si deshabilita esta configuración de directiva, el Control del Explorador web no bloqueará la intervención de usuario automática en la descarga de archivos no iniciada por el usuario para todos los procesos.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls** (Permitir que solo los dominios aprobados usen controles ActiveX en la zona de sitios restringidos de Internet Explorer)  </br>
  Esta configuración de directiva controla si se le pide al usuario que permita la ejecución de los controles ActiveX en sitios web distintos al sitio web que ha instalado el control ActiveX. Si habilita esta configuración de directiva, el usuario debe confirmar si permite la ejecución de los controles ActiveX desde sitios web en esta zona. El usuario puede permitir que el control se ejecute desde el sitio actual, o bien desde todos los sitios. Si deshabilita esta configuración de directiva, el usuario no ve el mensaje de ActiveX por sitio, y los controles ActiveX pueden ejecutarse desde todos los sitios de esta zona.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe** (Inicializar e incluir en scripts controles ActiveX no marcados como seguros en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar los controles ActiveX no marcados como seguros. Si habilita esta configuración de directiva, los controles ActiveX se ejecutarán, se cargarán con parámetros y se incluirán en scripts sin establecer la seguridad de objetos para los datos o scripts que no sean de confianza. Esta configuración no se recomienda, excepto para zonas seguras y administradas. Esta configuración hace que los controles seguros y no seguros se inicialicen y se activen los scripts, omitiendo la opción "Generar scripts de los controles ActiveX marcados como seguros para scripts". Si habilita esta configuración de directiva y selecciona Preguntar en el cuadro desplegable, se consultará con los usuarios si quieren permitir que el control se cargue con parámetros o se activen los scripts. Si deshabilita esta configuración de directiva, ningún control ActiveX que no pueda hacerse seguro se cargará con parámetros ni se activarán los scripts. Si no establece esta configuración de directiva, ningún control ActiveX que no pueda hacerse seguro se cargará con parámetros ni se activarán los scripts.
  
  **Valor predeterminado**: Deshabilitar  
  
- **Internet Explorer users changing policies** (Directivas de cambio de usuarios de Internet Explorer)  
    Impide que los usuarios cambien la configuración de zona de seguridad. Una zona de seguridad es un grupo de sitios web con el mismo nivel de seguridad. Si habilita esta directiva, el botón Nivel personalizado y el control deslizante de nivel de seguridad de la pestaña Seguridad del cuadro de diálogo Opciones de Internet estarán deshabilitados. Si deshabilita esta directiva o no la configura, los usuarios pueden cambiar la configuración de zona de seguridad. Esta directiva impide que los usuarios cambien la configuración de zona de seguridad establecida por el administrador. Nota: La directiva "Deshabilitar la página Seguridad" (ubicada en \Configuración de usuario\Plantillas administrativas\Componentes de Windows\Internet Explorer\Panel de control Internet), que quita la pestaña Seguridad del Panel de control de Internet Explorer, tiene prioridad sobre esta directiva. Si está habilitada, esta directiva se omite. Además, vea también la directiva "Zonas de seguridad: usar solo la configuración del equipo".
    
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer restricted zone protected mode** (Modo protegido de la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite activar el modo protegido. El modo protegido ayuda a proteger los puntos vulnerables y susceptibles de ataque de Internet Explorer mediante la reducción de las ubicaciones en las que Internet Explorer puede escribir en el Registro y en el sistema de archivos. Si habilita esta configuración de directiva, se activa el modo protegido. El usuario no puede desactivar el modo protegido. Si deshabilita esta configuración de directiva, se desactiva el modo protegido. El usuario no puede activar el modo protegido. Si no establece esta configuración de directiva, el usuario puede activar o desactivar el modo protegido.
  
  **Valor predeterminado**: Habilitar  
  
- **Internet Explorer internet zone user data persistence** (Persistencia de datos de usuario de la zona de Internet de Internet Explorer)  
  Esta configuración de directiva le permite administrar la preservación de información en el Historial del explorador, en Favoritos, en un almacén XML o directamente dentro de una página web guardada en disco. Cuando el usuario vuelva a una página persistente, el estado de dicha página podrá restaurarse si esta configuración de directiva se establece correctamente. Si habilita esta configuración de directiva, los usuarios podrán preservar información en el Historial del explorador, en Favoritos, en un almacén XML o directamente dentro de una página web guardada en disco. Si deshabilita esta configuración de directiva, los usuarios no podrán conservar información en el historial del explorador, en Favoritos, en un almacén XML ni directamente dentro de una página web guardada en disco. Si no establece esta configuración de directiva, los usuarios podrán conservar información en el historial del explorador, en Favoritos, en un almacén XML o directamente dentro de una página web guardada en disco.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer internet zone scripting of web browser controls** (Scripting de controles de explorador web en la zona de Internet de Internet Explorer)  
 
  Esta configuración de directiva determina si una página puede controlar los controles WebBrowser insertados mediante scripts. Si habilita esta configuración de directiva, se permite el acceso por scripts al control WebBrowser. Si deshabilita esta configuración de directiva, no se permite el acceso por scripts al control WebBrowser. Si no establece esta configuración de directiva, el usuario puede habilitar o deshabilitar el acceso por scripts al control WebBrowser. De manera predeterminada, el acceso por scripts al control WebBrowser solo se permite en las zonas Intranet y Equipo local.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer restricted zone user data persistence** (Persistencia de datos de usuario de la zona de sitios restringidos de Internet Explorer)  
    Esta configuración de directiva le permite administrar la preservación de información en el Historial del explorador, en Favoritos, en un almacén XML o directamente dentro de una página web guardada en disco. Cuando el usuario vuelva a una página persistente, el estado de dicha página podrá restaurarse si esta configuración de directiva se establece correctamente. Si habilita esta configuración de directiva, los usuarios podrán preservar información en el Historial del explorador, en Favoritos, en un almacén XML o directamente dentro de una página web guardada en disco. Si deshabilita esta configuración de directiva, los usuarios no podrán conservar información en el historial del explorador, en Favoritos, en un almacén XML ni directamente dentro de una página web guardada en disco. Si no establece esta configuración de directiva, los usuarios no podrán conservar información en el historial del explorador, en Favoritos, en un almacén XML o directamente dentro de una página web guardada en disco.  
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer locked down intranet zone java permissions** (Bloqueo de permisos de Java en la zona Intranet de Internet Explorer)  
  Esta configuración de directiva permite administrar los permisos para applets Java. Si habilita esta configuración de directiva, podrá elegir una opción del cuadro desplegable. Personalizado, para controlar la configuración de permisos individualmente. Seguridad baja habilita a los applets para realizar todas las operaciones. Seguridad media habilita a los applets para ejecutarse en su espacio aislado (un área de memoria fuera de la cual el programa no puede hacer llamadas), además de funcionalidades como espacio de desecho (un área de almacenamiento segura en el equipo cliente) y E/S de archivos controlada por usuario. Seguridad alta habilita a los applets para ejecutarse en su espacio aislado. Deshabilite Java para impedir la ejecución de los applets. Si deshabilita esta configuración de directiva, los applets Java no se ejecutarán. Si no establece esta configuración de directiva, los applets Java se deshabilitan.
  
  **Valor predeterminado**: Deshabilitar Java  
  
- **Modo protegido mejorado de Internet Explorer**  
  El modo protegido mejorado utiliza procesos de 64 bits en versiones de Windows de 64 bits para proporcionar seguridad adicional contra los sitios web malintencionados. En equipos que ejecutan al menos Windows 8, el modo protegido mejorado también limita las ubicaciones que Internet Explorer puede leer del Registro y del sistema de archivos. Si habilita esta configuración de directiva, se activa el modo protegido mejorado. Cualquier zona que tenga el modo protegido habilitado utilizará el modo protegido mejorado. Los usuarios no podrán deshabilitar el modo protegido mejorado. Si deshabilita esta configuración de directiva, se desactiva el modo protegido mejorado. Cualquier zona que tenga el modo protegido habilitado utilizará la versión del modo de protegido presentada en Internet Explorer 7 para Windows Vista. Si no configura esta directiva, los usuarios pueden activar o desactivar el modo protegido mejorado en la pestaña Opciones avanzadas del cuadro de diálogo Opciones de Internet.
  
  **Valor predeterminado**: Habilitado  
  
- **Internet Explorer bypass smart screen warnings** (Omitir las advertencias de SmartScreen de Internet Explorer)  
  Esta configuración de directiva determina si el usuario puede omitir las advertencias del filtro SmartScreen. El filtro SmartScreen advierte al usuario sobre los archivos ejecutables que los usuarios de Internet Explorer no suelen descargar de Internet. Si habilita esta configuración de directiva, las advertencias del filtro SmartScreen bloquean al usuario. Si deshabilita o no establece esta configuración de directiva, el usuario puede omitir las advertencias del filtro SmartScreen.
  
  **Valor predeterminado**: Deshabilitado  
  
- **Internet Explorer restricted zone meta refresh** (Meta Refresh en la zona de sitios restringidos de Internet Explorer)  
  Esta configuración de directiva permite administrar si el explorador de un usuario se puede redirigir a otra página web si el autor de la página web usa la opción Meta Refresh (etiqueta) para redirigir a los exploradores a otra página web. Si habilita esta configuración de directiva, el explorador de un usuario en el que se cargue una página que contenga una opción Meta Refresh activa se puede redirigir a otra página web. Si deshabilita esta configuración de directiva, el explorador de un usuario en el que se cargue una página que contenga una opción Meta Refresh activa no se puede redirigir a otra página web. Si no establece esta configuración de directiva, el explorador de un usuario en el que se cargue una página que contenga una opción Meta Refresh activa no se puede redirigir a otra página web.
  
  **Valor predeterminado**: Deshabilitado  
  
## <a name="local-policies-security-options"></a>Opciones de seguridad de directivas locales
Para más información, vea [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) (CSP de directiva: LocalPoliciesSecurityOptions) en la documentación de Windows. 

- **Restrict anonymous access to named pipes and shares** (Restringir el acceso anónimo a las canalizaciones con nombre y los recursos compartidos)  
  Cuando se habilita, esta configuración de seguridad restringe el acceso anónimo a recursos compartidos y canalizaciones a la configuración de: (1) Canalizaciones con nombre a las que se puede acceder de forma anónima (2) Recursos compartidos a los que se puede acceder de forma anónima
  
  **Valor predeterminado**: Sí  
  
- **Seguridad de sesión mínima para servidores NTLM basados en SSP**  
  Esta configuración de seguridad permite que un servidor requiera la negociación de cifrado de 128 bits o la seguridad de sesión NTLMv2. Estos valores dependen del valor de configuración de seguridad Nivel de autenticación de LAN Manager. Las opciones son: Requerir seguridad de sesión NTLMv2: se producirá un error en la conexión si no se negocia la integridad del mensaje. Requerir cifrado de 128 bits. Se producirá un error en la conexión si no se negocia el cifrado de alta seguridad (128 bits).
  
  **Valor predeterminado**: Requerir NTLM V2 y cifrado de 128 bits  
  
- **Minutos de inactividad de la pantalla de bloqueo hasta que se activa el protector de pantalla**  
  Windows detecta inactividad en una sesión de inicio de sesión y, si el tiempo de inactividad excede el límite de inactividad, se ejecutará el protector de pantalla y se bloqueará la sesión.
  
  **Valor predeterminado**: 15
  
- **Require client to always digitally sign communications** (Requerir que el cliente siempre firme digitalmente las comunicaciones) Esta configuración de seguridad determina si todo el tráfico de canal seguro iniciado por el miembro de dominio debe estar firmado o cifrado. Cuando un equipo se une a un dominio, se crea una cuenta de equipo. Después, cuando se inicia el sistema, este usa la contraseña de cuenta de equipo para crear un canal seguro con un controlador de dominio para su dominio. Este canal seguro se usa para realizar operaciones como la autenticación de paso a través de NTLM, la búsqueda de SID o nombre de LSA y mucho más. Esta configuración determina si todo el tráfico de canal seguro iniciado por el miembro de dominio cumple los requisitos mínimos de seguridad. En concreto, determina si todo el tráfico de canal seguro iniciado por el miembro de dominio se debe firmar o cifrar. Si esta directiva está habilitada, no se establecerá el canal seguro, a menos que se negocie la firma o el cifrado de todo el tráfico de canal seguro. Si esta directiva está deshabilitada, el cifrado y la firma de todo el tráfico de canal seguro se negocian con el controlador de dominio, en cuyo caso el nivel de firma y cifrado depende de la versión del controlador de dominio y la configuración de las dos directivas siguientes: Miembro de dominio: cifrar digitalmente datos de un canal seguro (cuando sea posible) Miembro de dominio: firmar digitalmente datos de un canal seguro (cuando sea posible)
  
  **Valor predeterminado**: Sí
  
- **Nivel de autenticación**  
  Esta configuración de seguridad determina qué protocolo de autenticación de desafío o respuesta se usa para los inicios de sesión de red. Esta elección afecta al nivel del protocolo de autenticación que usan los clientes, el nivel de seguridad de sesión negociada y el nivel de autenticación aceptado por los servidores como sigue:  
  - *Enviar respuestas LM y NTLM*: los clientes usan la autenticación LM y NTLM, y nunca usan la seguridad de sesión NTLMv2; los controladores de dominio aceptan la autenticación LM, NTLM y NTLMv2. 
  - *Enviar LM y NTLM: NTLMv2 si se negocia*: los clientes usan la autenticación LM y NTLM, y usan la seguridad de sesión NTLMv2 si el servidor la admite; los controladores de dominio aceptan la autenticación LM, NTLM y NTLMv2. 
  - *Enviar solo respuesta NTLM*: los clientes usan solo la autenticación NTLM y usan la seguridad de sesión NTLMv2 si el servidor la admite; los controladores de dominio aceptan la autenticación LM, NTLM y NTLMv2. 
  - *Enviar solo respuesta NTLMv2*: los clientes usan solo la autenticación NTLMv2 y usan la seguridad de sesión NTLMv2 si el servidor la admite; los controladores de dominio aceptan la autenticación LM, NTLM y NTLMv2. 
  - *Enviar solo respuesta NTLMv2 y rechazar LM*: los clientes usan solo la autenticación NTLMv2 y usan la seguridad de sesión NTLMv2 si el servidor la admite; los controladores de dominio rechazan LM (aceptan solo la autenticación NTLM y NTLMv2). 
  - *Enviar solo respuesta NTLMv2 y rechazar LM y NTLM*: los clientes usan solo la autenticación NTLMv2 y usan la seguridad de sesión NTLMv2 si el servidor la admite; los controladores de dominio rechazan LM y NTLM (aceptan solo la autenticación NTLMv2). 
    
  **Valor predeterminado**: Enviar solo respuesta NTLMv2. Rechazar LM y NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers** (Impedir que los clientes envíen contraseñas sin cifrar a servidores SMB de terceros)  
  Si se habilita esta configuración de seguridad, el redirector de Bloque de mensajes de servidor (SMB) puede enviar contraseñas sin cifrar a servidores SMB que no son de Microsoft que no admiten el cifrado de contraseñas durante la autenticación. El envío de contraseñas sin cifrar es un riesgo de seguridad.
  
  **Valor predeterminado**: Sí
  
- **Disable server digitally signing communications always** (Deshabilitar siempre la firma digital de las comunicaciones en el servidor)  
  Esta configuración de seguridad determina si el cliente SMB intenta negociar la firma de paquetes SMB. El protocolo de bloque de mensajes del servidor (SMB) proporciona la forma de compartir impresoras y archivos de Microsoft y otras muchas operaciones de red, como la administración remota de Windows. Para evitar ataques de tipo "Man in the middle" que modifiquen los paquetes SMB en tránsito, el protocolo SMB admite la firma digital de los paquetes SMB. Esta configuración de directiva determina si el componente de cliente SMB intenta negociar la firma de paquetes SMB cuando se conecta a un servidor SMB. Si se habilita esta configuración, el cliente de red de Microsoft solicitará al servidor que realice la firma de paquetes SMB tras la configuración de la sesión. Si se ha habilitado la firma de paquetes en el servidor, esta se negocia. Si esta directiva está deshabilitada, el cliente SMB no negociará nunca la firma de paquetes SMB.
  
  **Valor predeterminado**: Sí
  
- **Administrator elevation prompt behavior** (Comportamiento de petición de elevación del administrador)  
  Esta configuración de directiva controla el comportamiento de la petición de elevación para los administradores. Las opciones son: 
    - *Elevar sin preguntar*: permite a las cuentas con privilegios realizar una operación que requiera elevación sin requerir consentimiento o credenciales. Nota: Use esta opción solo en los entornos más restringidos. 
    - *Pedir credenciales en el escritorio seguro*: cuando una operación requiere la elevación de privilegios, pide al usuario del escritorio seguro que escriba un nombre de usuario y una contraseña con privilegios. Si el usuario escribe credenciales válidas, la operación continuará con el mayor privilegio disponible del usuario. 
    - *Pedir consentimiento en el escritorio seguro*: cuando una operación requiere la elevación de privilegios, se pide al usuario del escritorio seguro que haga clic en Permitir o Denegar. Si el usuario selecciona Permitir, la operación continúa con el mayor privilegio disponible del usuario. 
    - *Pedir credenciales*: cuando una operación requiere la elevación de privilegios, se pide al usuario que escriba un nombre de usuario y una contraseña de administrador. Si el usuario escribe credenciales válidas, la operación continúa con el privilegio aplicable. 
    - *Pedir consentimiento*: cuando una operación requiere la elevación de privilegios, se pide al usuario que haga clic en Permitir o Denegar. Si el usuario selecciona Permitir, la operación continúa con el mayor privilegio disponible del usuario.  
    - *Pedir consentimiento para binarios que no son de Windows*: cuando una operación para una aplicación que no es de Microsoft requiere la elevación de privilegios, se pide al usuario del escritorio seguro que haga clic en Permitir o Denegar. Si el usuario selecciona Permitir, la operación continúa con el mayor privilegio disponible del usuario.   
  
  **Valor predeterminado**: Pedir consentimiento en el escritorio seguro
  
- **Seguridad de sesión mínima para clientes NTLM basados en SSP**  
  Esta configuración de seguridad permite que un cliente requiera la negociación de cifrado de 128 bits o la seguridad de sesión NTLMv2. Estos valores dependen del valor de configuración de seguridad Nivel de autenticación de LAN Manager. Las opciones son:
  - Requerir seguridad de sesión NTLMv2: se producirá un error en la conexión si no se negocia el protocolo NTLMv2. 
  - *Requerir cifrado de 128 bits:* se producirá un error en la conexión si no se negocia el cifrado de alta seguridad (128 bits).
  - *Requerir NTLMv2 y cifrado de 128 bits*. 

  **Valor predeterminado**: Requerir cifrado NTLM V2 128
  
- **Comportamiento de extracción de tarjeta inteligente**  
    Esta configuración de seguridad determina lo que sucede cuando la tarjeta inteligente de un usuario que haya iniciado sesión se extrae del lector de tarjetas inteligentes. Las opciones son:
     - *Ninguna acción*. 
     - *Bloquear la estación de trabajo*: la estación de trabajo se bloquea cuando se retira la tarjeta inteligente, lo que permite a los usuarios abandonar el área, llevarse su tarjeta inteligente y seguir manteniendo una sesión protegida.
     - *Forzar cierre de sesión*: el usuario se desconecta automáticamente cuando se quita la tarjeta inteligente.
     - *Desconectar sesión de Escritorio remoto*: al quitar la tarjeta inteligente se desconecta la sesión sin cerrar la sesión del usuario. Esta opción permite al usuario insertar la tarjeta inteligente y reanudar la sesión más tarde o en otro equipo equipado con lector de tarjeta inteligente, sin necesidad de volver a iniciar la sesión. Si la sesión es local, esta directiva funciona de forma idéntica a Bloquear estación de trabajo.  <br><br>
    
  **Valor predeterminado**: Bloquear la estación de trabajo
  
- **Block anonymous enumeration of SAM accounts and shares** (Bloquear la enumeración anónima de recursos compartidos y cuentas SAM)  
  Esta configuración de seguridad determina si se permite la enumeración anónima de cuentas y recursos compartidos SAM. Windows permite a los usuarios anónimos realizar ciertas actividades, como enumerar los nombres de cuentas de dominio y recursos compartidos de red. Esto es conveniente, por ejemplo, cuando un administrador quiere conceder acceso a usuarios en un dominio de confianza que no mantiene una confianza recíproca. Si no quiere permitir la enumeración anónima de cuentas y recursos compartidos SAM, establezca esta directiva en *Sí*.
  
  **Valor predeterminado**: Sí
  
- **Block remote logon with blank password** (Bloquear el inicio de sesión remoto con contraseña en blanco)  
  Esta configuración de seguridad determina si las cuentas locales que no están protegidas mediante contraseña se pueden usar para iniciar sesión desde ubicaciones distintas de la consola física del equipo. Si se habilita, las cuentas locales que no están protegidas mediante contraseña deben usar el teclado del equipo para iniciar sesión. 

  *Advertencia*: En los equipos que no se encuentran en ubicaciones físicamente seguras, siempre se deben aplicar directivas de contraseña segura para todas las cuentas de usuario locales. De lo contrario, cualquiera con acceso físico al equipo puede iniciar sesión con una cuenta de usuario que no tiene una contraseña. Esto es especialmente importante para los equipos portátiles. 

  Si aplica esta directiva de seguridad al grupo Todos, nadie podrá iniciar sesión a través de Servicios de Escritorio remoto. Esta configuración no afecta a los inicios de sesión que usan cuentas de dominio. Las aplicaciones que usan inicios de sesión interactivos remotos pueden omitir esta configuración.
  
  **Valor predeterminado**: Sí
  
- **Standard user elevation prompt behavior** (Comportamiento de petición de elevación de usuarios estándar)  
  Esta configuración de directiva controla el comportamiento de la petición de elevación para los usuarios estándar. 
  - *Rechazar solicitudes de elevación automáticamente*: cuando una operación requiere la elevación de privilegios, se muestra un mensaje de error de acceso denegado configurable. Una empresa que ejecuta escritorios como usuario estándar puede elegir esta configuración para reducir las llamadas al departamento de soporte técnico. 
  - *Pedir credenciales en el escritorio seguro*: cuando una operación requiere la elevación de privilegios, se le pide al usuario del escritorio seguro que escriba otro nombre de usuario y contraseña. Si el usuario escribe credenciales válidas, la operación continúa con el privilegio aplicable. 
  - *Pedir credenciales*: cuando una operación requiere la elevación de privilegios, se pide al usuario que escriba un nombre de usuario y una contraseña de administrador. Si el usuario escribe credenciales válidas, la operación continúa con el privilegio aplicable.  
  
  **Valor predeterminado**: Rechazar solicitudes de elevación automáticamente
  
- **Require admin approval mode for administrators** (Requerir el modo de aprobación de administrador para administradores)  
  Esta configuración de directiva controla el comportamiento de todas las configuraciones de directiva del Control de cuentas de usuario (UAC) en el equipo. Si cambia esta configuración de directiva, debe reiniciar el equipo. Las opciones son:   
  - *No configurado*: se deshabilitan el Modo de aprobación de administrador y todas las configuraciones de directiva de UAC relacionadas. Nota: Si se deshabilita esta configuración de directiva, el Centro de seguridad notifica que ha disminuido la seguridad global del sistema operativo. 
  - *Sí*: se habilita el Modo de aprobación de administrador. Debe habilitarse esta directiva y las configuraciones de directiva de UAC relacionadas se deben establecer de forma apropiada para permitir que se ejecuten en Modo de aprobación de administrador la cuenta predefinida Administrador y el resto de usuarios que son miembros del grupo Administradores.  
  
  **Valor predeterminado**: Sí
  
- **Prevent anonymous enumeration of SAM accounts** (Evitar la enumeración anónima de cuentas SAM)  
  Esta configuración de seguridad determina los permisos adicionales que se conceden para las conexiones anónimas al equipo. Windows permite a los usuarios anónimos realizar ciertas actividades, como enumerar los nombres de cuentas de dominio y recursos compartidos de red. Esto es conveniente, por ejemplo, cuando un administrador quiere conceder acceso a usuarios en un dominio de confianza que no mantiene una confianza recíproca. Esta opción de seguridad permite colocar restricciones adicionales en las conexiones anónimas como sigue: 
  - *Sí*: no se permiten las enumeraciones anónimas de cuentas SAM. Esta opción sustituye Todo por Usuarios autenticados en los permisos de seguridad para los recursos.
  - *No configurado*: No hay restricciones adicionales. Basar en los permisos predeterminados.  
  
  **Valor predeterminado**: Sí
  
- **Allow remote calls to security accounts manager** (Permitir llamadas remotas al Administrador de cuentas de seguridad)  
  Esta configuración de directiva permite restringir conexiones remotas de RPC a SAM. Si no se selecciona, se usa el descriptor de seguridad predeterminado.
  
  **Valor predeterminado**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Usar Modo de aprobación de administrador**  
  Esta configuración de directiva controla el comportamiento del modo de aprobación de administrador para la cuenta predefinida Administrador. Las opciones son: 
  - *Sí*: la cuenta predefinida de administrador usa el Modo de aprobación de administrador. De manera predeterminada, cualquier operación que requiera la elevación de privilegios pedirá al usuario que apruebe la operación. 
  - *No configurado*: la cuenta predefinida de administrador ejecuta todas las aplicaciones con privilegios de administración completos.  

  **Valor predeterminado**: Sí
  
- **Allow UI access applications for secure locations** (Permitir aplicaciones UIAccess para ubicaciones seguras)  
  Esta configuración de directiva controla si los programas de accesibilidad de la interfaz de usuario (UIAccess o UIA) pueden deshabilitar automáticamente el escritorio seguro para las peticiones de elevación usadas por un usuario estándar. 
  - *Sí*: los programas de UIA, incluida Asistencia remota de Windows, deshabilitan de forma automática el escritorio seguro para las peticiones de elevación. Si no deshabilita la configuración de directiva "Control de cuentas de usuario: cambiar al escritorio seguro cuando se pida confirmación de elevación", las peticiones aparecen en el escritorio del usuario interactivo en lugar del escritorio seguro. 
  - *No configurado*: el escritorio seguro solo lo puede deshabilitar el usuario del escritorio interactivo o si se deshabilita la configuración de directiva "Control de cuentas de usuario: cambiar al escritorio seguro cuando se pida confirmación de elevación".  

  **Valor predeterminado**: Sí

- **Detectar instalaciones de aplicaciones y pedir confirmación de elevación**  
  Esta configuración de directiva controla el comportamiento de la detección de instalaciones de aplicaciones en el equipo. Las opciones son: 
  - *Habilitado*: cuando se detecta un paquete de instalación de aplicaciones que requiere la elevación de privilegios, se pide al usuario que escriba un nombre de usuario y una contraseña de administrador. Si el usuario escribe credenciales válidas, la operación continúa con el privilegio aplicable. 
  - *Deshabilitado*: los paquetes de instalación de aplicaciones no se detectan ni se pide la elevación. Las empresas que ejecuten escritorios de usuarios estándar y usen las tecnologías de instalación delegada como la Directiva de grupo de Instalación de software o Systems Management Server (SMS) deben deshabilitar esta configuración de directiva. En este caso, la detección del instalador no es necesaria.  
  
  **Valor predeterminado**: Sí
  
- **Prevent storing LAN manager hash value on next password change** (Impedir el almacenamiento del valor de hash de LAN Manager en el próximo cambio de contraseña)  
  Esta configuración de seguridad determina si, en el siguiente cambio de contraseña, se almacena el valor de hash de LAN Manager (LM) para la nueva contraseña. El hash de LM es relativamente poco seguro y vulnerable a ataques, si se compara con el hash de Windows NT, con mayor seguridad criptográfica. Como el hash de LM se almacena en el equipo local, en la base de datos de seguridad, las contraseñas pueden estar en peligro si la base de datos de seguridad recibe un ataque.
  
  **Valor predeterminado**: Sí

- **Virtualizar los errores de escritura de archivo y del Registro a ubicaciones por usuario**  
  Esta configuración de directiva controla si se redireccionan los errores de escritura de aplicaciones a ubicaciones definidas en el Registro y el sistema de archivos. Esta configuración de directiva mitiga las aplicaciones que se ejecutan como administrador y que escriben los datos de aplicaciones en tiempo de ejecución en *%ProgramFiles%* , *%Windir%* , *%Windir%\system32* o *HKLM\Software*.
  
  **Valor predeterminado**: Sí

## <a name="ms-security-guide"></a>Guía de seguridad de MS  
Para más información, vea [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) (CSP de directiva: MSSecurityGuide) en la documentación de Windows.  

- **Apply UAC restrictions to local accounts on network logon** (Aplicar restricciones de UAC a cuentas locales en el inicio de sesión de red)  
  **Valor predeterminado**: Habilitado
  
- **SMB v1 client driver start configuration** (Configuración de inicio del controlador de cliente SMB v1)  
  **Valor predeterminado**: Controlador deshabilitado
  
- **Servidor SMB v1**  
  **Valor predeterminado**: Deshabilitado
  
- **Autenticación de texto implícita**  
  **Valor predeterminado**: Deshabilitado
  
- **Structured exception handling overwrite protection** (Protección contra sobrescritura de control de excepciones estructuradas)  
  **Valor predeterminado**: Habilitado
  
## <a name="mss-legacy"></a>MSS heredado  
Para más información, vea [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) (CSP de directiva: MSSLegacy) en la documentación de Windows.  

- **Network IP source routing protection level** (Nivel de protección del enrutamiento de origen de IP de red)  
  **Valor predeterminado**: La protección más alta  
  
- **Network ignore NetBIOS name release requests except from WINS servers** (Omitir solicitudes de liberación de nombre NetBIOS, excepto de servidores WINS de la red)  
  **Valor predeterminado**: Habilitado
  
- **Network IPv6 source routing protection level** (Nivel de protección del enrutamiento de origen de IPv6 de red)  
  **Valor predeterminado**: La protección más alta

- **Network ICMP redirects override OSPF generated** (Los redireccionamientos ICMP de red invalidan los generados por OSPF)  
  **Valor predeterminado**: Deshabilitado
  
## <a name="power"></a>Potencia  
Para más información, vea [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) (CSP de directiva: Power) en la documentación de Windows.  

- **Require password on wake while plugged in** (Requerir contraseña al activarse durante la conexión)  
  Esta configuración de directiva especifica si el sistema solicitará al usuario una contraseña cuando el equipo salga de la suspensión y reanude su funcionamiento. Si habilita o no establece esta configuración de directiva, el sistema solicitará una contraseña al usuario cuando el equipo salga de la suspensión y reanude su funcionamiento. Si deshabilita esta configuración de directiva, el sistema no solicitará ninguna contraseña al usuario cuando el equipo salga de la suspensión y reanude su funcionamiento.
  
  **Valor predeterminado**: Habilitado
  
- **Standby states when sleeping while on battery** (Estados de espera mientras el equipo está en suspensión con batería)  
  Esta configuración de directiva controla si Windows puede usar los estados de espera al poner el equipo en estado de suspensión. Si habilita o no establece esta configuración de directiva, Windows usará los estados de espera para poner el equipo en estado de suspensión. Si deshabilita esta configuración de directiva, no se permitirán los estados de espera (S1-S3).
  
  **Valor predeterminado**: Deshabilitado
  
- **Standby states when sleeping while plugged in** (Estados de espera mientras el equipo está en suspensión conectado)  
  Esta configuración de directiva controla si Windows puede usar los estados de espera al poner el equipo en estado de suspensión. Si habilita o no establece esta configuración de directiva, Windows usará los estados de espera para poner el equipo en estado de suspensión. Si deshabilita esta configuración de directiva, no se permitirán los estados de espera (S1-S3).
  
  **Valor predeterminado**: Deshabilitado
  
- **Require password on wake while on battery** (Requerir contraseña al activarse mientras el equipo está con batería)  
  Esta configuración de directiva especifica si el sistema solicitará al usuario una contraseña cuando el equipo salga de la suspensión y reanude su funcionamiento. Si habilita o no establece esta configuración de directiva, el sistema solicitará una contraseña al usuario cuando el equipo salga de la suspensión y reanude su funcionamiento. Si deshabilita esta configuración de directiva, el sistema no solicitará ninguna contraseña al usuario cuando el equipo salga de la suspensión y reanude su funcionamiento.
  
  **Valor predeterminado**: Habilitado
  
## <a name="remote-desktop-services"></a>Servicios de Escritorio Remoto  
Para más información, vea [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) (CSP de directiva: RemoteDesktopServices) en la documentación de Windows.  

- **Block password saving** (Bloquear Guardar contraseñas)  
  Controla si se pueden guardar contraseñas en este equipo desde Conexión a Escritorio remoto. Si habilita esta opción, se deshabilita la casilla para guardar contraseñas en Conexión a Escritorio remoto y los usuarios no podrán guardar contraseñas. Cuando un usuario abre un archivo RDP por medio de Conexión a Escritorio remoto y guarda su configuración, se eliminan todas las contraseñas que existían con anterioridad en el archivo RDP. Si deshabilita esta opción o no la configura, el usuario puede guardar contraseñas mediante Conexión a Escritorio remoto.
  
   **Valor predeterminado**: Habilitado
  
- **Secure RPC communication** (Comunicación RPC segura)  
  Especifica si un servidor host de sesión de Escritorio remoto requiere comunicaciones RPC seguras con todos los clientes o permite comunicaciones no seguras. Puede usar esta opción para reforzar la seguridad de la comunicación RPC con los clientes al permitir solo peticiones autenticadas y cifradas. Si el estado se establece en Habilitado, Servicios de Escritorio remoto acepta peticiones de clientes RPC que admiten peticiones seguras y no permite la comunicación no segura con clientes que no sean de confianza. Si el estado se establece en Deshabilitado, Servicios de Escritorio remoto siempre solicita seguridad para todo el tráfico RPC. Pero se permite la comunicación no segura para los clientes RPC que no responden a la petición. Si el estado se establece en No configurado, se permite la comunicación no segura. Nota: La interfaz RPC se usa para administrar y configurar Servicios de Escritorio remoto.
  
  **Valor predeterminado**: Habilitado
  
- **Block drive redirection** (Bloquear la redirección de unidad)  
  Esta configuración de directiva especifica si se debe impedir la asignación de unidades cliente en una sesión de Servicios de Escritorio remoto (redirección de unidad). De forma predeterminada, el servidor host de sesión de Escritorio remoto asigna unidades cliente automáticamente al conectarse. Las unidades asignadas aparecen en el árbol de carpetas de sesión en el Explorador de archivos o en Equipo con el formato *\<letraDeUnidad>* en *\<nombreDeEquipo>* . Puede usar esta directiva para invalidar este comportamiento. Si habilita esta configuración de directiva, no se permitirá la redirección de unidades cliente en sesiones de Servicios de Escritorio remoto ni se permitirá la redirección de copias de archivos del Portapapeles en equipos que ejecuten Windows Server 2003, Windows 8 y Windows XP. Si deshabilita esta configuración de directiva, se permitirá siempre la redirección de unidades cliente. Además, la redirección de copias de archivo del Portapapeles siempre se permite si se permite la redirección del Portapapeles. Si no establece esta configuración de directiva, la redirección de unidades cliente y la redirección de copias de archivo del Portapapeles no se especificarán en el nivel de directiva de grupo.
  
  **Valor predeterminado**: Habilitado
  
- **Prompt for password upon connection** (Solicitar contraseña al conectarse)  
  Esta configuración de directiva especifica si Servicios de Escritorio remoto pide siempre al cliente una contraseña al conectarse. Puede usar esta opción para exigir la petición de una contraseña a los usuarios que se conecten a Servicios de Escritorio remoto, aunque ya hayan proporcionado la contraseña en el cliente de Conexión a Escritorio remoto. De forma predeterminada, Servicios de Escritorio remoto permite a los usuarios iniciar sesión de forma automática si especifican una contraseña en el cliente de Conexión a Escritorio remoto. Si habilita esta configuración de directiva, los usuarios no podrán iniciar sesión automáticamente en Servicios de Escritorio remoto mediante la especificación de su contraseña en el cliente de Conexión a Escritorio remoto. Se les pedirá una contraseña para iniciar sesión. Si deshabilita esta configuración de directiva, los usuarios podrán iniciar sesión siempre automáticamente en Servicios de Escritorio remoto mediante la especificación de su contraseña en el cliente de Conexión a Escritorio remoto. Si no establece esta configuración de directiva, el inicio de sesión automático no se especificará en el nivel de directiva de grupo. 
  
  **Valor predeterminado**: Habilitado
  
- **Remote desktop services client connection encryption level** (Nivel de cifrado de conexión de cliente de servicios de Escritorio remoto)  
  Especifica si es necesario usar un nivel de cifrado específico para proteger las comunicaciones entre equipos cliente y servidores host de sesión de Escritorio remoto durante las conexiones de Protocolo de escritorio remoto (RDP). Esta directiva solo se aplica si se usa el cifrado RDP nativo. Pero no se recomienda usar el cifrado RDP nativo (al contrario que el cifrado SSL). Esta directiva no se aplica al cifrado SSL. Si habilita esta configuración de directiva, todas las comunicaciones entre clientes y servidores host de sesión de Escritorio remoto realizadas durante las conexiones remotas deberán usar el método de cifrado especificado en esta configuración. De forma predeterminada, el nivel de cifrado se establece en Alto. Los métodos de cifrado disponibles son los siguientes:  
  - *Alto*: el valor Alto cifra los datos enviados del cliente al servidor y del servidor al cliente mediante un cifrado de alta seguridad de 128 bits. Use este nivel de cifrado en entornos que contengan únicamente clientes de 128 bits (por ejemplo, clientes que ejecuten Conexión a Escritorio remoto). Los clientes que no admitan este nivel de cifrado no se podrán conectar a los servidores host de sesión de Escritorio remoto.  
  - *Compatible con el cliente*: la opción Compatible con el cliente cifra los datos enviados entre el cliente y el servidor con la seguridad de clave máxima compatible con el cliente. Use este nivel de cifrado en entornos que contengan clientes no compatibles con el cifrado de 128 bits.  
  - *Bajo*: el valor Bajo cifra únicamente los datos enviados del cliente al servidor mediante un cifrado de 56 bits.  
  
  Si deshabilita o no establece esta configuración, el nivel de cifrado que se usará en las conexiones remotas a servidores host de sesión de Escritorio remoto no se aplicará mediante la directiva de grupo. Importante: Se puede configurar la compatibilidad con FIPS a través de la opción Criptografía del sistema. Use algoritmos compatibles con FIPS para las configuraciones de cifrado, firma y operaciones hash en la directiva de grupo (en Configuración del equipo\Configuración de Windows\Configuración de seguridad\Directivas locales\Opciones de seguridad). La configuración de compatibilidad con FIPS cifra y descifra los datos enviados entre el cliente y el servidor con los algoritmos de cifrado del Estándar federal de procesamiento de información (FIPS) 140, mediante los módulos criptográficos de Microsoft. Use este nivel de cifrado cuando las comunicaciones entre clientes y servidores host de sesión de Escritorio remoto requieran el máximo nivel de cifrado.
  
  **Valor predeterminado**: Alto
  
## <a name="remote-management"></a>Administración remota  
Para más información, vea [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) (CSP de directiva: RemoteManagement) en la documentación de Windows.  

- **Block storing run as credentials** (Bloquear el almacenamiento de credenciales Ejecutar como)  
  Autenticación básica de cliente
  
  **Valor predeterminado**: Habilitado
  
- **Autenticación básica**  
  Esta configuración de directiva permite administrar si el servicio Administración remota de Windows (WinRM) aceptará la autenticación básica de un cliente remoto. Si habilita esta configuración de directiva, el servicio WinRM aceptará la autenticación básica de un cliente remoto. Si deshabilita o no establece esta configuración de directiva, el servicio WinRM no aceptará la autenticación básica de un cliente remoto.
  
  **Valor predeterminado**: Deshabilitado
  
- **Block client digest authentication** (Bloquear la autenticación implícita de cliente)  
  Esta configuración de directiva permite administrar si el cliente Administración remota de Windows (WinRM) usa la autenticación implícita. Si habilita esta configuración de directiva, el cliente WinRM no usa la autenticación implícita. Si deshabilita o no establece esta configuración de directiva, el cliente WinRM usa la autenticación implícita.
  
  **Valor predeterminado**: Habilitado
  
- **Tráfico sin cifrar**  
  Esta configuración de directiva permite administrar si el servicio Administración remota de Windows (WinRM) envía y recibe mensajes sin cifrar a través de la red. Si habilita esta configuración de directiva, el cliente WinRM envía y recibe mensajes sin cifrar a través de la red. Si deshabilita o no establece esta configuración de directiva, el cliente WinRM envía o recibe únicamente mensajes cifrados a través de la red.  
  
  **Valor predeterminado**: Deshabilitado
  
- **Tráfico del cliente sin cifrar**  
  Esta configuración de directiva permite administrar si el cliente de Administración remota de Windows (WinRM) envía y recibe mensajes sin cifrar a través de la red. Si habilita esta configuración de directiva, el cliente WinRM envía y recibe mensajes sin cifrar a través de la red. Si deshabilita o no establece esta configuración de directiva, el cliente WinRM envía o recibe únicamente mensajes cifrados a través de la red.
  
  **Valor predeterminado**: Deshabilitado
  
- **Autenticación básica de cliente**  
  Esta configuración de directiva permite administrar si el cliente Administración remota de Windows (WinRM) usa la autenticación básica. Si habilita esta configuración de directiva, el cliente WinRM usa la autenticación básica. Si WinRM está configurado para usar el transporte HTTP, el nombre de usuario y la contraseña se envían a través de la red como texto sin cifrar. Si deshabilita o no establece esta configuración de directiva, el cliente WinRM no usa la autenticación básica.
  
  **Valor predeterminado**: Deshabilitado
  

## <a name="remote-procedure-call"></a>Llamada a procedimiento remoto  
Para más información, vea [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) (CSP de directiva: RemoteProcedureCall) en la documentación de Windows.  

- **RPC unauthenticated client options** (Opciones de cliente RPC no autenticado)  
  Esta configuración de directiva controla la forma en la que el tiempo de ejecución del servidor de RPC administra los clientes de RPC no autenticados que se conectan a servidores de RPC. Esta configuración de directiva afecta a todas las aplicaciones de RPC. En un entorno de dominio, use esta configuración de directiva con precaución, ya que puede afectar a un amplio rango de funcionalidades, entre ellas el propio procesamiento de la directiva de grupo. Revertir un cambio en esta configuración de directiva puede requerir intervención manual en cada equipo afectado. Esta configuración de directiva nunca debe aplicarse a un controlador de dominio. Si deshabilita esta configuración de directiva, el tiempo de ejecución del servidor de RPC usa el valor "Autenticado" en el cliente de Windows y el valor "Ninguno" en las versiones de Windows Server que son compatibles con esta configuración de directiva. Si no establece esta configuración de directiva, permanece deshabilitada. El tiempo de ejecución del servidor RPC se comporta como si estuviera habilitado con el valor de "Autenticado" que se usa para el cliente de Windows y el valor de "Ninguno" que se usa para las SKU de servidor que son compatibles con esta configuración de directiva. Si habilita esta configuración de directiva, el tiempo de ejecución del servidor de RPC impedirá que los clientes de RPC no autenticados se conecten a los servidores de RPC que se ejecuten en un equipo. Un cliente se considera como autenticado cuando usa una canalización con nombre para comunicarse con el servidor o cuando usa seguridad de RPC. Las interfaces de RPC que solicitaron específicamente ser accesibles a clientes no autenticados pueden quedar exentas de esta restricción, según el valor seleccionado para esta configuración de directiva.  
  - *Ninguno* permite que todos los clientes de RPC se conecten a los servidores de RPC que se ejecutan en el equipo donde se aplica la configuración de directiva. 
  - *Autenticado* permite que solo los clientes de RPC autenticados (según la definición anterior) se conecten a los servidores de RPC que se ejecutan en el equipo donde se aplica la configuración de directiva. Se otorgan excepciones para las interfaces que las solicitan. 
  - *Autenticado sin excepciones* permite que solo los clientes de RPC autenticados (según la definición anterior) se conecten a los servidores de RPC que se ejecuten en el equipo donde se aplica la configuración de directiva. No se permite ninguna excepción. Nota: Esta configuración de directiva no se aplicará hasta que se reinicie el sistema.  

  **Valor predeterminado**: Autenticado

## <a name="search"></a>Buscar 
Para más información, vea [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) (CSP de directiva: Search) en la documentación de Windows.  

- **Disable indexing encrypted items** (Deshabilitar la indexación de elementos cifrados)  
  Permite o deniega la indexación de elementos. Este modificador se aplica al indizador de Windows Search, que controla si se indexarán los elementos cifrados, como los archivos protegidos de Windows Information Protection (WIP). Cuando la directiva está habilitada, los elementos protegidos por WIP se indexan y los metadatos sobre ellos se almacenan en una ubicación sin cifrar. Los metadatos incluyen elementos tales como la ruta de acceso de archivo y la fecha de modificación. Cuando la directiva está deshabilitada, los elementos protegidos por WIP no se indexan y no se muestran en los resultados de Cortana o del explorador de archivos. También puede haber un impacto en el rendimiento de fotografías y aplicaciones de Groove si hay muchos archivos multimedia protegidos por WIP en el dispositivo.
  
**Valor predeterminado**: Sí
  
## <a name="smart-screen"></a>SmartScreen  
Para más información, vea [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) (CSP de directiva: SmartScreen) en la documentación de Windows.  

- **Block execution of unverified files** (Bloquear la ejecución de archivos no comprobados)  
  Impide al usuario ejecutar archivos no comprobados. 
  - *No configurado*: los empleados pueden omitir las advertencias de SmartScreen y ejecutar archivos malintencionados. 
  - *Sí*: los empleados no pueden omitir las advertencias de SmartScreen y ejecutar archivos malintencionados.

  **Valor predeterminado**: Sí

<!-- Not currently available? - **Block unverified file download**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes
 --> 
- **Require SmartScreen for apps and files** (Requerir SmartScreen para aplicaciones y archivos)  
  Permite que los administradores de TI configuren SmartScreen para Windows.

  **Valor predeterminado**: Sí
  
## <a name="system"></a>System (Sistema)  
Para más información, vea [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) (CSP de directiva: System) en la documentación de Windows.  

- **System boot start driver initialization** (Inicialización de controladores de arranque del sistema)  
  Esta configuración de directiva permite especificar qué controladores de arranque se inicializarán de acuerdo con la clasificación determinada por un controlador de arranque de inicio temprano. El controlador de Antimalware de inicio temprano puede proporcionar las siguientes clasificaciones para cada controlador de arranque: 
  - *Bueno*: el controlador se ha firmado y no se ha alterado.  
  - *Defectuoso*: el controlador se ha identificado como malware. Se recomienda no permitir la inicialización de controladores defectuosos. 
  - *Defectuoso, pero necesario para el arranque*: el controlador se ha identificado como malware, pero el equipo no puede arrancar correctamente sin cargar este controlador. 
  - *Desconocido*: la aplicación de detección de malware no ha certificado este controlador y el controlador de arranque de Antimalware de inicio temprano no lo ha clasificado.  

  Si habilita esta configuración de directiva, puede elegir los controladores de arranque que se inicializarán la próxima vez que se arranque el equipo. Si deshabilita o no establece esta configuración de directiva, los controladores de arranque clasificados como Buenos, Desconocidos o Defectuosos pero críticos se inicializarán y se omite la inicialización de controladores clasificados como Defectuosos. Si la aplicación de detección de malware no incluye un controlador de arranque de Antimalware de inicio temprano o si dicho controlador se ha deshabilitado, esta configuración no tiene efecto y se inicializarán todos los controladores de arranque.  
  
  **Valor predeterminado**: Bueno, Desconocido y Defectuoso pero crítico


## <a name="wi-fi"></a>Wi-Fi  
Para más información, vea [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) (CSP de directiva: Wifi) en la documentación de Windows.  

- **Impedir el uso compartido de Internet**  
  Especifica si la conexión compartida es posible en el dispositivo.  

  **Valor predeterminado**: Sí  

- **Block Automatically connecting to Wi-Fi hotspots** (Bloquear la conexión automática a zonas Wi-Fi)  
  Habilita o deshabilita la conexión automática del dispositivo a zonas Wi-Fi.  

  **Valor predeterminado**: Sí  
  
## <a name="windows-connection-manager"></a>Administrador de conexiones de Windows  
Para más información, vea [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) (CSP de directiva: WindowsConnectionManager) en la documentación de Windows.  

- **Block connection to non-domain networks** (Bloquear la conexión a redes que no son de dominio)  
  Esta configuración de directiva evita que los equipos se conecten a una red basada en dominio y a una red no basada en dominio al mismo tiempo. Si esta configuración de directiva está habilitada, el equipo responde a intentos de conexión manual y automática a redes de acuerdo con las siguientes circunstancias: 
  - Intentos de conexión automática Si el equipo ya está conectado a una red basada en dominio, se bloquean todos los intentos de conexión automática a redes no basadas en dominio. Si el equipo ya está conectado a una red no basada en dominio, se bloquean los intentos de conexión automática a redes basadas en dominio. 
  - Intentos de conexión manual Si el equipo ya está conectado a una red no basada en dominio o a una red basada en dominio a través de medios diferentes de Ethernet y un usuario intenta crear una conexión manual a una red adicional infringiendo esta configuración de directiva, la conexión de red existente se desconecta y se permite realizar la conexión manual. Si el equipo ya está conectado a una red no basada en dominio o a una red basada en dominio a través de Ethernet y un usuario intenta crear una conexión manual a una red adicional infringiendo esta configuración de directiva, la conexión Ethernet se mantiene y se bloquea el intento de conexión manual.  

  Si esta configuración de directiva está deshabilitada o no se establece, los equipos se pueden conectar de manera simultánea a ambos tipos de red: basada en dominio y no basada en dominio.  

  **Valor predeterminado**: Habilitado
  
## <a name="windows-defender"></a>Windows Defender  
Para más información, vea [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) (CSP de directiva: Defender) en la documentación de Windows.  

- **Examinar mensajes de correo entrante**  
  Permite o impide el examen de correo electrónico.
  
  **Valor predeterminado**: Sí  

- **Office apps launch child process type** (Tipo de proceso secundario que inician las aplicaciones de Office)  
  No se permite que las aplicaciones de Office creen procesos secundarios. Esto incluye Word, Excel, PowerPoint, OneNote y Access. Se trata de un comportamiento de malware habitual, especialmente para los ataques basados en macros que intentan usar las aplicaciones de Office para iniciar o descargar archivos ejecutables malintencionados.
  
  **Valor predeterminado**: Bloquear
  
- **Defender sample submission consent type** (Tipo de consentimiento de envío de muestra de Windows Defender)  
  Comprueba el nivel de consentimiento del usuario en Windows Defender para enviar datos. Si ya se ha concedido el consentimiento requerido, Windows Defender los envía. En caso contrario (y si el usuario ha especificado que no se pida nunca) se inicia la interfaz de usuario para solicitar el consentimiento del usuario (cuando se permite Defender/AllowCloudProtection) antes de enviar los datos.
  
  **Valor predeterminado**: Enviar muestras seguras automáticamente 
  
- **Intervalo de actualización de firma (en horas)**  
  Intervalo de actualización de firma en horas de Defender
  
  **Valor predeterminado**: 4
  
- **Script downloaded payload execution type** (Tipo de ejecución de carga útil descargada de script)  
  Tipo de ejecución de carga útil descargada de script de Windows Defender
  
  **Valor predeterminado**: Bloquear
  
- **Prevent credential stealing type** (Impedir el tipo de robo de credenciales)  
  Credential Guard de Windows Defender usa la seguridad basada en virtualización para aislar los secretos de forma que solo el software de sistema con privilegios pueda acceder a ellos. El acceso no autorizado a estos secretos puede conducir a ataques de robo de credenciales, como pass-the-hash o pass-the-ticket. Credential Guard de Windows Defender impide estos ataques mediante la protección de los hash de contraseña NTLM, los vales de concesión de vales de Kerberos y las credenciales almacenadas por las aplicaciones como credenciales de dominio.
  
  **Valor predeterminado**: Habilitar

- **Email content execution type** (Tipo de ejecución de contenido del mensaje de correo electrónico)  
  Esta regla impide que los siguientes tipos de archivos se ejecuten o inicien desde un correo electrónico visto en Microsoft Outlook o webmail (como Gmail.com o Outlook.com): archivos ejecutables (como .exe, .dll o .scr) archivos de script (como un archivo PowerShell.ps, VisualBasic.vbs o JavaScript.js) o archivos de almacenamiento de script.
  
  **Valor predeterminado**: Bloquear
  
- **Tipo de protección de red**  
  Esta directiva permite activar o desactivar la protección de red (Bloquear o Auditar) en Protección contra vulnerabilidades de seguridad de Windows Defender. Protección de red es una característica de Protección contra vulnerabilidades de seguridad de Windows Defender que evita que los empleados que usan una aplicación accedan a estafas de suplantación de identidad, sitios que hospedan vulnerabilidades de seguridad y contenido malintencionado en Internet. Esto incluye impedir que exploradores de terceros se conecten a sitios peligrosos. El tipo de valor es entero. Si habilita esta configuración, se activa la protección de red y los empleados no podrán desactivarla. Este comportamiento se puede controlar mediante las opciones siguientes: Bloquear y Auditar. Si habilita esta directiva con la opción "Bloquear", se impide que usuarios y aplicaciones se conecten a dominios peligrosos. Podrá ver esta actividad en el Centro de seguridad de Windows Defender. Si habilita esta directiva con la opción "Auditar", no se impedirá que los usuarios o las aplicaciones se conecten a dominios peligrosos. Pero podrá seguir viendo esta actividad en el Centro de seguridad de Windows Defender. Si deshabilita esta directiva, no se impedirá que los usuarios o las aplicaciones se conecten a dominios peligrosos. No verá ninguna actividad de red en el Centro de seguridad de Windows Defender. Si no configura esta directiva, se deshabilitará el bloqueo de la red de forma predeterminada.
  
  **Valor predeterminado**: Habilitar
  
- **Defender schedule scan day** (Programar día de examen de Windows Defender)  
  Programar día de examen de Windows Defender.
  
  **Valor predeterminado**: Todos los días
  
- **Protección que proporciona la nube**  
  Para proteger mejor el PC, Windows Defender enviará información a Microsoft sobre los problemas que encuentre. Microsoft analizará esa información, obtendrá detalles sobre los problemas que le afectan a usted y a otros clientes, y ofrecerá soluciones mejoradas.
  
  **Valor predeterminado**: Sí  

- **Defender potentially unwanted app action** (Acción frente a aplicaciones potencialmente no deseadas de Windows Defender)  
  La característica de protección frente a aplicaciones potencialmente no deseadas (PUA) del Antivirus de Windows Defender puede identificar aplicaciones PUA e impedir que se descarguen e instalen en puntos de conexión de la red. Estas aplicaciones no se consideran virus, malware u otro tipo de amenazas, pero es posible que realicen acciones en los puntos de conexión que afecten de forma negativa a su rendimiento o uso. PUA también puede hacer referencia a las aplicaciones que se consideran que tienen una mala reputación. Incluye el comportamiento típico de las aplicaciones potencialmente no deseadas: varios tipos de paquetes de software que insertan anuncios en exploradores web, optimizadores de controladores y registros que detectan problemas y solicitan pagos para corregir los errores, pero permanecen en el punto de conexión y no realizan cambios ni optimizaciones (también conocidos como programas "antivirus fraudulentos"). Estas aplicaciones pueden aumentar el riesgo de que su red se infecte con malware, provocar que las infecciones de malware sean más difíciles de identificar y desperdiciar recursos de TI en la limpieza de las aplicaciones.  
  
  **Valor predeterminado**: Bloquear  

- **Script obfuscated macro code type** (Tipo de código de macro ofuscado de script)  
  El malware y otras amenazas pueden intentar ofuscar u ocultar su código malintencionado en algunos archivos de script. Esta regla impide que se ejecuten los scripts que parecen ofuscados.
  
  **Valor predeterminado**: Bloquear
  
- **Examinar unidades extraíbles durante un examen completo**  
  Permite que Windows Defender busque software malintencionado y no deseado en las unidades extraíbles (por ejemplo, unidades flash) durante un examen completo. Antivirus de Windows Defender examina todos los archivos en los dispositivos USB antes de la ejecución.
  
  **Valor predeterminado**: Sí  
  
- **Examinar archivos de almacenamiento**  
  Examinar archivos de almacenamiento de Windows Defender.
  
  **Valor predeterminado**: Sí
  
- **Supervisión de comportamiento**  
  Permite o impide la funcionalidad Supervisión de comportamiento de Windows Defender. Insertados en Windows 10, estos sensores recopilan y procesan las señales de comportamiento de procesos del sistema operativo y envían estos datos de sensor a la instancia de nube privada y aislada de ATP de Microsoft Defender.
  
  **Valor predeterminado**: Sí

- **Examinar archivos abiertos desde carpetas de red**  
  Si los archivos son de solo lectura, el usuario no podrá quitar el malware detectado.
  
  **Valor predeterminado**: Sí

- **Untrusted USB process type** (Tipo de proceso de USB que no es de confianza)  
  Con esta regla, los administradores pueden impedir que los archivos ejecutables sin firmar o que no son de confianza se ejecuten desde unidades USB extraíbles, como tarjetas SD.
  
  **Valor predeterminado**: Bloquear
  
- **Office apps other process injection type** (Tipo de inserción de aplicaciones de Office en otros procesos)  
  Las aplicaciones de Office, incluido Word, Excel, PowerPoint y OneNote, no podrán insertar código en otros procesos. El malware usa esto normalmente para ejecutar código malintencionado en un intento de ocultar la actividad a los motores de detección antivirus.
  
  **Valor predeterminado**: Bloquear
  
- **Office macro code allow Win32 imports type** (Tipo de importaciones de Win32 desde código de macros de Office)  
  El malware puede usar el código de macros de los archivos de Office para importar y cargar archivos DLL de Win32 que, después, se pueden usar para realizar llamadas de API para permitir continuar con la infección en todo el sistema. Esta regla intenta bloquear los archivos de Office que contienen código de macro capaz de importar archivos DLL de Win32. Esto incluye Word, Excel, PowerPoint y OneNote.
  
  **Valor predeterminado**: Bloquear  
  
- **Defender cloud block level** (Nivel de bloqueo en la nube de Windows Defender)  
  Nivel de bloqueo en la nube de Windows Defender.
  
  **Valor predeterminado**: No configurado

- **Supervisión en tiempo real**  
  Windows Defender requiere supervisión en tiempo real.
  
  **Valor predeterminado**: Sí
  
- **Office apps executable content creation or launch type** (Tipo de inicio o creación de contenido ejecutable de las aplicaciones de Office)  
  Esta regla tiene como destino los comportamientos típicos que se usan en complementos y scripts sospechosos y malintencionados (extensiones) que crean o inician archivos ejecutables. Se trata de una técnica de malware típica. Se impide que las aplicaciones de Office usen las extensiones. Normalmente, estas extensiones usan Windows Scripting Host (archivos .wsh) para ejecutar scripts que automatizan determinadas tareas o que proporcionan características de complementos creados por el usuario
  
  **Valor predeterminado**: Bloquear

## <a name="windows-ink-workspace"></a>Área de trabajo de Windows Ink  
Para más información, vea [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) (CSP de directiva: WindowsInkWorkspace) en la documentación de Windows.  

- **Ink Workspace** (Área de trabajo de Ink)  
  Especifica si permitir que el usuario acceda al área de trabajo de Windows Ink. 
  - *Deshabilitado*: el acceso al área de trabajo de Ink está deshabilitado. La característica está desactivada.
  - *Habilitado*: la característica Área de trabajo de Windows Ink está activada, pero el usuario no puede acceder a ella por encima de la pantalla de bloqueo.
  - *No configurado*: la característica Área de trabajo de Windows Ink está activada, y el usuario puede usarla por encima de la pantalla de bloqueo.  

  **Valor predeterminado**: Habilitado
 
## <a name="windows-powershell"></a>Windows PowerShell  
Para más información, vea [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) (CSP de directiva: WindowsPowerShell) en la documentación de Windows.  

- **Power shell shell script block logging** (Bloquear el registro de scripts de PowerShell)  
  Esta configuración de directiva permite el registro de todas las entradas de script de PowerShell en el registro de eventos Microsoft-Windows-PowerShell/Operational. Si habilita esta configuración de directiva, Windows PowerShell registrará el procesamiento de comandos, bloques de script, funciones y scripts, ya sea invocado de forma interactiva o mediante la automatización. Si deshabilita esta configuración de directiva, se deshabilitará el registro de entradas de script de PowerShell. Si habilita el registro de invocación de bloque de script, PowerShell también registrará los eventos cuando se inicie o se detenga la invocación de un comando, bloque de script, función o script. Si habilita el registro de invocación, se generará una gran cantidad de registros de eventos. Nota: Esta configuración de directiva se encuentra en Configuración del equipo y Configuración del usuario en el Editor de directivas de grupo. La configuración de directiva de Configuración del equipo tiene prioridad sobre la de Configuración del usuario.
  
  **Valor predeterminado**: Habilitado
 
