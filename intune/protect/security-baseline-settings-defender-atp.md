---
title: Configuración de las líneas de base de seguridad de Intune para Advanced Threat Protection de Microsoft Defender
titleSuffix: Microsoft Intune
description: Configuración de la línea de base de seguridad compatible con Intune para administrar Advanced Threat Protection de Microsoft Defender
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b7363682960cff6688e9727d2b6869b6bf357084
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74060067"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Configuración de la línea de base de Advanced Threat Protection de Microsoft Defender

Vea la configuración de la línea de base de Advanced Threat Protection de Microsoft Defender (anteriormente Advanced Threat Protection de Windows Defender) compatible con Microsoft Intune. Los valores predeterminados de línea de base de Advanced Threat Protection (ATP) representan la configuración recomendada para ATP y podrían no coincidir con los valores predeterminados para otras líneas de base de seguridad.  

La línea base de [Advanced Threat Protection de Microsoft Defender](advanced-threat-protection.md#prerequisites) está disponible si el entorno cumple con los requisitos previos para su uso. 

Esta línea base está optimizada para dispositivos físicos y actualmente no se recomienda para su uso en máquinas virtuales (VM) o puntos de conexión VDI. Ciertas configuraciones de base de referencia pueden afectar a las sesiones interactivas remotas en entornos virtualizados. Para obtener más información, vea [Aumento del cumplimiento de la base de referencia de seguridad de ATP de Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) en la documentación de Windows.

## <a name="application-guard"></a>Protección de aplicaciones  
Para más información, vea [WindowsDefenderApplicationGuard CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp) (CSP de WindowsDefenderApplicationGuard) en la documentación de Windows.  

Al utilizar Microsoft Edge, Protección de aplicaciones de Microsoft Defender protege su entorno de sitios que no son de confianza para su organización. Cuando los usuarios visitan sitios que no aparecen en el límite de red aislada, estos se abren en una sesión de exploración virtual de Hyper-V. Los sitios de confianza se definen mediante un límite de red.  

- **Protección de aplicaciones** - *Settings/AllowWindowsDefenderApplicationGuard*  
  Seleccione *Sí* para habilitar esta característica, que abre sitios que no son de confianza en un contenedor de exploración virtualizado de Hyper-V. Cuando se establece en *No configurado*, cualquier sitio (de confianza y no de confianza) se abre en el dispositivo, y no en un contenedor virtualizado.  

  **Valor predeterminado**: Sí
 
  - **Contenido externo en sitios de empresa** - *Settings/BlockNonEnterpriseContent*  
    Seleccione *Sí* para bloquear la carga de contenido de sitios web no aprobados. Cuando se establece en *No configurado*, los sitios que no sean de empresa se pueden abrir en el dispositivo. 
 
    **Valor predeterminado**: Sí

  - **Comportamiento del Portapapeles** - *Settings/ClipboardSettings*  
    Seleccione qué acciones de copiar y pegar se permiten entre el equipo local y el explorador virtual de la Protección de aplicaciones.  Las opciones son:
    - No configurado  
    - Bloquear la copia y pegar entre equipos y exploradores. No se pueden transferir datos entre el equipo y el explorador virtual.  
    - Permitir copiar y pegar desde el explorador a solo PC: los datos no se pueden transferir desde el equipo al explorador virtual.
    - Permitir copiar y pegar desde equipo a solo explorador: los datos no se pueden transferir desde el explorador virtual al equipo host.
    - Permitir copiar y pegar entre PC y explorador: no existe ningún bloque para el contenido.  

    **Valor predeterminado**: bloquear la copia y pegar entre PC y explorador  

- **Directiva de aislamiento de red de Windows: nombres de dominio de red de empresa**  
  Para más información, vea [Policy CSP - NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation) (CSP de directiva: NetworkIsolation) en la documentación de Windows.
  
  Especifique una lista de recursos empresariales como dominios, intervalos de direcciones IP y límites de red hospedados en la nube que Protección de aplicaciones trata como sitios empresariales.  

  **Valor predeterminado**: securitycenter.windows.com

## <a name="application-reputation"></a>Reputación de la aplicación  

Para más información, vea [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) (CSP de directiva: SmartScreen) en la documentación de Windows.

- **Block execution of unverified files** (Bloquear la ejecución de archivos no comprobados)  
    Impide al usuario ejecutar archivos no comprobados. Si el valor es *No configurado*, los empleados pueden omitir las advertencias de SmartScreen y ejecutar archivos malintencionados. Seleccione *Sí* para que los empleados no puedan omitir las advertencias de SmartScreen y ejecutar archivos malintencionados.  
  
    **Valor predeterminado**: Sí

- **Require SmartScreen for apps and files** (Requerir SmartScreen para aplicaciones y archivos)  
  Configúrelo en *Sí* para habilitar SmartScreen para Windows.  

  **Valor predeterminado**: Sí

## <a name="attack-surface-reduction"></a>Reducción de la superficie expuesta a ataques  

- **Office apps launch child process type** (Tipo de proceso secundario que inician las aplicaciones de Office)  
  [Regla de reducción de la superficie de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules): cuando se establece en *Bloquear*, las aplicaciones de Office no podrán crear procesos secundarios. Las aplicaciones de Office incluyen Word, Excel, PowerPoint, OneNote y Access. La creación de un proceso secundario es comportamiento de malware habitual, especialmente para los ataques basados en macros que intentan usar las aplicaciones de Office para iniciar o descargar archivos ejecutables malintencionados.  

  **Valor predeterminado**: Bloquear

- **Script downloaded payload execution type** (Tipo de ejecución de carga útil descargada de script)  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection): especifique un nivel de detección para aplicaciones potencialmente no deseadas que se descargan o intentan instalarse.  

  **Valor predeterminado**: Bloquear 

- **Prevent credential stealing type** (Impedir el tipo de robo de credenciales)  
  Establézcalo en *Habilitar* para [proteger credenciales de dominio derivadas con Credential Guard](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard). Credential Guard de Microsoft Defender usa la seguridad basada en virtualización para aislar los secretos de forma que solo el software de sistema con privilegios pueda acceder a ellos. El acceso no autorizado a estos secretos puede conducir a ataques de robo de credenciales, como pass-the-hash o pass-the-ticket. Credential Guard de Microsoft Defender impide estos ataques mediante la protección de los hash de contraseña NTLM, los vales de concesión de vales de Kerberos y las credenciales almacenadas por las aplicaciones como credenciales de dominio.  

  **Valor predeterminado**: Habilitar

- **Ejecución de contenido del mensaje de correo electrónico**  
  [Regla de reducción de la superficie de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules): cuando se configura en *Bloquear*, esta regla impide que los siguientes tipos de archivo se ejecuten o se inicien desde un correo electrónico visto en Microsoft Outlook o webmail (por ejemplo, Gmail.com o Outlook.com):  

  - Archivos ejecutables (por ejemplo, .exe, .dll o .scr)  
  - Archivos de script (por ejemplo, PowerShell .ps, VisualBasic .vbs o JavaScript .js)  
  - Archivos de almacenamiento de script  

  **Valor predeterminado**: Bloquear

- **Inicio de Adobe Reader en un proceso secundario**  
  [Regla de reducción de la superficie de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules): *habilite* esta regla para impedir que Adobe Reader cree un proceso secundario. A través de ingeniería social o vulnerabilidades de seguridad, el malware puede descargar y ejecutar cargas adicionales y salir de Adobe Reader.  

  **Valor predeterminado**: Habilitar

- **Código de macro ofuscado de script**  
  [Regla de reducción de la superficie de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules): el malware y otras amenazas pueden intentar ofuscar u ocultar su código malintencionado en algunos archivos de script. Esta regla impide que se ejecuten los scripts que parecen ofuscados.  
    
  **Valor predeterminado**: Bloquear

- **Proceso de USB que no es de confianza**  
  [Regla de reducción de la superficie de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules): cuando se establece en *Bloquear*, los archivos ejecutables sin firmar o que no son de confianza de unidades extraíbles USB y tarjetas SD no se pueden ejecutar.

  Entre los archivos ejecutables figuran:
  - Archivos ejecutables (por ejemplo, .exe, .dll o .scr)
  - Archivos de script (por ejemplo, PowerShell .ps, VisualBasic .vbs o JavaScript .js)  

  **Valor predeterminado**: Bloquear

- **Inserción de aplicaciones de Office en otros procesos**  
  [Regla de reducción de la superficie de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules): cuando se establece en *Bloquear*, las aplicaciones de Office, incluidos Word, Excel, PowerPoint y OneNote, no pueden insertar código en otros procesos. La inserción de código suele usarla el malware para ejecutar código malintencionado en un intento de ocultar la actividad a los motores de detección antivirus.  

  **Valor predeterminado**: Bloquear

- **Importaciones de Win32 desde código de macros de Office**  
  [Regla de reducción de la superficie de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules): cuando se establece en *Bloquear*, esta regla intenta bloquear los archivos de Office que contienen código de macro que puede importar archivos DLL de Win32. Entre los archivos de Office figuran Word, Excel, PowerPoint y OneNote. El malware puede usar el código de macros de los archivos de Office para importar y cargar archivos DLL de Win32 que, después, se pueden usar para realizar llamadas de API para permitir continuar con la infección en todo el sistema.  

  **Valor predeterminado**: Bloquear

- **Inicio de aplicaciones de comunicación de Office en un proceso secundario**  
  [Regla de reducción de la superficie de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules): cuando se establece en *Habilitar*, esta regla impide que Outlook cree procesos secundarios. Al bloquear la creación de un proceso secundario, esta regla protege contra los ataques de ingeniería social e impide que el código se aproveche de una vulnerabilidad en Outlook.  

  **Valor predeterminado**: Habilitar

- **Inicio o creación de contenido ejecutable de las aplicaciones de Office**  
  [Regla de reducción de la superficie de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules): cuando se establece en *Bloquear*, las aplicaciones de Office no pueden crear contenido ejecutable. Las aplicaciones de Office incluyen Word, Excel, PowerPoint, OneNote y Access.  

  Esta regla tiene como destino los comportamientos típicos que se usan en complementos y scripts sospechosos y malintencionados (extensiones) que crean o inician archivos ejecutables. Se trata de una técnica de malware típica. Se impide que las aplicaciones de Office usen las extensiones. Normalmente, estas extensiones usan Windows Scripting Host (archivos .wsh) para ejecutar scripts que automatizan determinadas tareas o que proporcionan características de complementos creados por el usuario.

  **Valor predeterminado**: Bloquear

## <a name="bitlocker"></a>BitLocker  

Para más información, vea [Configuración de las directivas de grupo de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings) en la documentación de Windows.  

- **Cifrar los dispositivos**  
  Seleccione *Sí* para habilitar el cifrado de dispositivo de BitLocker. Según el hardware del dispositivo y la versión de Windows, podría pedirse a los usuarios de dispositivos que confirmen que no hay ningún cifrado de terceros en el dispositivo. La activación del cifrado de Windows mientras el cifrado de terceros está activo favorecerá la inestabilidad del dispositivo.  

   **Valor predeterminado**: Sí

- **Bit locker removable drive policy** (Directiva de unidad extraíble de BitLocker)  
  Los valores de esta directiva determinan la intensidad del cifrado que BitLocker usa para el cifrado de unidades extraíbles. Las empresas controlan el nivel de cifrado para mejorar la seguridad (AES-256 es más seguro que AES-128). Si selecciona *Sí* para habilitar esta directiva, puede configurar un algoritmo de cifrado y la intensidad de cifrado de clave para unidades de datos fijas, unidades del sistema operativo y unidades de datos extraíbles de manera individual. Para unidades del sistema operativo y unidades fijas, se recomienda usar el algoritmo XTS-AES. Para unidades extraíbles, debe usar el cifrado AES-CBC de 128 bits o AES-CBC de 256 bits si la unidad se usa en otros dispositivos que no ejecuten Windows 10 (versión 1511 o posterior). El cambio del método de cifrado no tendrá ningún efecto si la unidad ya está cifrada o si el cifrado está en curso. En estos casos, se omite esta configuración de directiva. 

  Para la directiva de la unidad extraíble de BitLocker, configure las siguientes opciones:

  - **Require encryption for write access** (Requerir cifrado para el acceso de escritura)  
    **Valor predeterminado**: Sí

  - **Método de cifrado**  
    **Valor predeterminado**: AES CBC de 128 bits

- **Cifrar la tarjeta de almacenamiento (solo móvil)** Si selecciona *sí* , se cifrará la tarjeta de almacenamiento del dispositivo móvil.  

   **Valor predeterminado**: Sí

- **Bit locker fixed drive policy** (Directiva de unidad fija de BitLocker)  
  Los valores de esta directiva determinan la intensidad del cifrado que BitLocker usa para el cifrado de unidades fijas. Las empresas pueden controlar el nivel de cifrado para mejorar la seguridad (AES-256 es más seguro que AES-128). Si habilita esta directiva, puede configurar un algoritmo de cifrado y la intensidad de cifrado de clave para unidades de datos fijas, unidades del sistema operativo y unidades de datos extraíbles de manera individual. Para unidades del sistema operativo y unidades fijas, se recomienda usar el algoritmo XTS-AES. Para unidades extraíbles, debe usar el cifrado AES-CBC de 128 bits o AES-CBC de 256 bits si la unidad se usa en otros dispositivos que no ejecuten Windows 10 (versión 1511 o posterior). El cambio del método de cifrado no tendrá ningún efecto si la unidad ya está cifrada o si el cifrado está en curso. En estos casos, se omite esta configuración de directiva.

  Para la directiva de la unidad fija de BitLocker, configure las siguientes opciones:

  - **Require encryption for write access** (Requerir cifrado para el acceso de escritura)  
    **Valor predeterminado**: Sí

  - **Método de cifrado**  
    **Valor predeterminado**: AES XTS de 128 bits

- **Bit locker system drive policy** (Directiva de unidad del sistema de BitLocker)  
  Los valores de esta directiva determinan la intensidad del cifrado que BitLocker usa para el cifrado de la unidad del sistema. A las empresas les interesa controlar el nivel de cifrado para mejorar la seguridad (AES-256 es más seguro que AES-128). Si habilita esta directiva, puede configurar un algoritmo de cifrado y la intensidad de cifrado de clave para unidades de datos fijas, unidades del sistema operativo y unidades de datos extraíbles de manera individual. Para unidades del sistema operativo y unidades fijas, se recomienda usar el algoritmo XTS-AES. Para unidades extraíbles, debe usar el cifrado AES-CBC de 128 bits o AES-CBC de 256 bits si la unidad se usa en otros dispositivos que no ejecuten Windows 10 (versión 1511 o posterior). El cambio del método de cifrado no tendrá ningún efecto si la unidad ya está cifrada o si el cifrado está en curso. En estos casos, se omite esta configuración de directiva.  

  Para la directiva de la unidad del sistema de BitLocker, configure las siguientes opciones:  

  - **Método de cifrado**  
    **Valor predeterminado**: AES XTS de 128 bits

## <a name="device-control"></a>Control de dispositivos  

- **Examinar unidades extraíbles durante un examen completo**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning): cuando se establece en *Sí*, Defender busca software malintencionado y no deseado en las unidades extraíbles, como unidades flash, durante un examen completo. El Antivirus de Defender examina todos los archivos en los dispositivos USB antes de que se ejecuten.

  Valor relacionado en esta lista: *Defender/AllowFullScanOnMappedNetworkDrives*  

  **Valor predeterminado**: Sí

- **Enumeración de los dispositivos externos compatibles con Kernel DMA Protection**  
   Consulte *DmaGuard/DeviceEnumerationPolicy* en [Policy CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy) (Directiva CSP - DmaGuard)

  Esta directiva proporciona seguridad adicional contra los dispositivos compatibles con DMA externos. Permite ejercer más control sobre la enumeración de dispositivos compatibles con DMA externos que no admiten el aislamiento de memoria de dispositivos DMS y el establecimiento de espacios aislados.

  Esta directiva solo surte efecto cuando la característica Kernel DMA Protection se admite y está habilitada por el firmware del sistema. Kernel DMA Protection es una característica de plataforma que no se puede controlar por directiva o por el usuario de un dispositivo. Debe admitirse por el sistema en el momento de fabricación. 

  Para comprobar si el sistema admite Kernel DMA Protection, ejecute MSINFO32.exe en el sistema y revise el campo *Kernel DMA Protection* en la página de resumen.  

  Las opciones son: 
  - *Valor predeterminado del dispositivo*: después de iniciar sesión o desbloquear la pantalla, los dispositivos con controladores compatibles con reasignación de DMA se pueden enumerar en cualquier momento. Los controladores no compatibles con reasignación de DMA se enumerarán solo después de que el usuario desbloquee la pantalla.
  - *Permitir todo*: todos dispositivos PCI compatibles con DMA se enumerarán en cualquier momento.
  - *Bloquear todo*: los dispositivos con controladores compatibles con reasignación de DMA se pueden enumerar en cualquier momento. Los dispositivos no compatibles con reasignación de DMA no podrán nunca iniciarse y realizar DMA en cualquier momento.

  **Valor predeterminado**: Valor predeterminado del dispositivo

- **Hardware device installation by device identifiers** (Instalación de dispositivos de hardware mediante identificadores de dispositivo)  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids): con esta directiva, puede especificar una lista de identificadores de hardware Plug and Play e identificadores compatibles para dispositivos que Windows no puede instalar. Esta configuración de directiva tiene prioridad sobre cualquier otra configuración de directiva que permita a Windows instalar dispositivos. Si habilita esta configuración de directiva (establecida en *Bloquear la instalación de dispositivos de hardware*), Windows no podrá instalar un dispositivo cuyo identificador de hardware o identificador compatible aparezca en la lista que usted cree. Si habilita esta configuración de directiva en un servidor de escritorio remoto, la directiva afecta a la redirección de los dispositivos especificados desde un cliente de escritorio remoto al servidor de escritorio remoto. Si deshabilita o no establece esta configuración de directiva (establecida en *Allow hardware device installation* [Permitir la instalación de dispositivo de hardware]), se podrán instalar o actualizar dispositivos según lo permitan o impidan otras configuraciones de directiva.  

  **Valor predeterminado**: Bloquear la instalación de dispositivos de hardware  

  Cuando se seleccione *Bloquear la instalación de dispositivos de hardware*, las siguientes opciones están disponibles.
  - **Remove matching hardware devices** (Quitar dispositivos de hardware que coinciden)  
    Esta opción solo está disponible cuando *Hardware device installation by device identifiers* (Instalación de dispositivos de hardware mediante identificadores de dispositivo) se establece en *Bloquear la instalación de dispositivos de hardware*.  

    **Valor predeterminado**: Sí

  - **Hardware device identifiers that are blocked** (Identificadores de dispositivo de hardware que están bloqueados)  
    Esta opción solo está disponible cuando *Hardware device installation by device identifiers* (Instalación de dispositivos de hardware mediante identificadores de dispositivo) se establece en *Bloquear la instalación de dispositivos de hardware*. Para configurar esta opción, expanda la opción, seleccione **+ Agregar**, y, a continuación, especifique el identificador de dispositivo de hardware que desea bloquear.  

    **Valor predeterminado**: PCI \ CC_0C0A

- **Block direct memory access** (Bloquear el acceso directo a memoria)  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess): use esta configuración de directiva para bloquear el acceso directo a memoria (DMA) para todos los puertos de bajada PCI de conexión instantánea en un dispositivo, hasta que un usuario inicie sesión en Windows. Una vez que un usuario inicie sesión, Windows mostrará los dispositivos PCI conectados a los puertos PCI de conexión instantánea. Cada vez que el usuario bloquee el equipo, DMA se bloquea en los puertos PCI de conexión instantánea sin dispositivos secundarios, hasta que el usuario inicie sesión de nuevo. Los dispositivos que ya aparecían cuando se desbloqueó el equipo seguirán funcionando hasta que se desconecten. 

  Esta configuración de directiva solo se aplica cuando está habilitado BitLocker o el cifrado de dispositivos.  

  **Valor predeterminado**: Sí


- **Hardware device installation by setup classes** (Instalación de dispositivos de hardware mediante clases de instalación)  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses): con esta directiva, puede especificar una lista de identificadores únicos globales (GUID) de clases de instalación de dispositivos para los controladores de dispositivos que no se pueden instalar en Windows. Esta configuración de directiva tiene prioridad sobre cualquier otra configuración de directiva que permita a Windows instalar dispositivos. Si habilita esta configuración de directiva, (establecida en *Bloquear la instalación de dispositivos de hardware*), Windows no podrá instalar ni actualizar controladores de dispositivos cuyos GUID de clases de instalación de dispositivos aparezcan en la lista que cree. Si habilita esta configuración de directiva en un servidor de escritorio remoto, esta afectará a la redirección de los dispositivos especificados desde un cliente de escritorio remoto al servidor de escritorio remoto. Si deshabilita o no establece esta configuración de directiva (establecida en *Allow hardware device installation* [Permitir la instalación de dispositivo de hardware]), Windows puede instalar o actualizar dispositivos según lo permitan o impidan otras configuraciones de directiva.  

  **Valor predeterminado**: Bloquear la instalación de dispositivos de hardware

  Cuando se seleccione *Bloquear la instalación de dispositivos de hardware*, las siguientes opciones están disponibles.  

  - **Remove matching hardware devices** (Quitar dispositivos de hardware que coinciden)  
    Esta opción solo está disponible cuando *Hardware device installation by setup classes* (Instalación de dispositivos de hardware por clases de instalación) se establece en *Bloquear la instalación de dispositivos de hardware*.  
 
    **Valor predeterminado**: Sí  

  - **Hardware device identifiers that are blocked** (Identificadores de dispositivo de hardware que están bloqueados)  
    Esta opción solo está disponible cuando Hardware device installation by setup classes (Instalación de dispositivos de hardware por clases de instalación) se establece en Bloquear la instalación de dispositivos de hardware. Para configurar esta opción, expanda la opción, seleccione **+ Agregar**, y, a continuación, especifique el identificador de dispositivo de hardware que desea bloquear.  
 
    **Valor predeterminado**: {d48179be-EC20-11D1-b6b8-00c04fa372a7}

## <a name="endpoint-detection-and-response"></a>Endpoint Detection and Response  
Para más información, vea [WindowsAdvancedThreatProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp) (CSP de WindowsAdvancedThreatProtection) en la documentación de Windows.  

- **Frecuencia de informes de telemetría urgentes** - *Configuration/TelemetryReportingFrequency*

  Frecuencia de informes de telemetría de Advanced Threat Protection de Microsoft Defender urgentes.  

  **Valor predeterminado**: Sí

- **Uso compartido de muestras para todos los archivos** - *SampleSharing/configuración* 

  Devuelve o establece el parámetro de configuración de uso compartido de muestras de Advanced Threat Protection de Microsoft Defender.  

  **Valor predeterminado**: Sí

## <a name="exploit-protection"></a>Protección contra vulnerabilidades  

- **XML de protección contra vulnerabilidades**  
  Para obtener más información, consulte [Importar, exportar e implementar configuraciones de protección contra vulnerabilidades](/windows/security/threat-protection/microsoft-defender-atp/import-export-exploit-protection-emet-xml) en la documentación de Windows.  

  Permite a los administradores de TI enviar a todos los dispositivos de la organización una configuración que representa las opciones de mitigación deseadas del sistema y las aplicaciones. La configuración se representa por medio de XML. 

  Protección contra vulnerabilidades se aplica para ayudar a proteger los dispositivos frente al malware que usa ataques para infectar y propagar. Use la aplicación de seguridad de Windows o PowerShell para crear un conjunto de mitigaciones (conocido como una configuración). Después, puede exportar esta configuración como un archivo XML y compartirlo con varios equipos en la red para que todos tengan el mismo conjunto de opciones de mitigación.
 
  También puede convertir e importar un archivo XML de configuración EMET en un archivo XML de configuración de protección contra vulnerabilidades.

- **Bloqueo de la invalidación de la protección contra vulnerabilidades**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride): configúrelo en *Sí* para evitar que los usuarios realicen cambios en el área de configuración de protección contra vulnerabilidades en el Centro de seguridad de Microsoft Defender. Si deshabilita o no configura esta opción, los usuarios locales pueden realizar cambios en el área de configuración de protección contra vulnerabilidades.  
  **Valor predeterminado**: Sí  

## <a name="microsoft-defender-antivirus"></a>Antivirus de Microsoft defender  

Para más información, vea [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) (CSP de directiva: Defender) en la documentación de Windows.

- **Examinar scripts cargados en exploradores web de Microsoft**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning): configúrelo en *Sí* para permitir la funcionalidad de examen de scripts de Microsoft Defender.  

  **Valor predeterminado**: Sí

- **Examinar mensajes de correo entrante**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning): configúrelo en *Sí* para permitir que Microsoft Defender examine el correo electrónico.  

  **Valor predeterminado**: Sí

- **Consentimiento de envío de muestra de Microsoft Defender**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent): comprueba el nivel de consentimiento del usuario en Microsoft Defender para enviar datos. Si ya se ha concedido el consentimiento requerido, Microsoft Defender los envía. En caso contrario (y si el usuario ha especificado que no se pida nunca) se inicia la interfaz de usuario para solicitar el consentimiento del usuario (cuando *Protección que proporciona la nube* está configurado en *Sí*) antes de enviar los datos.  

  **Valor predeterminado**: Enviar muestras seguras automáticamente

- **Sistema de inspección de red (NIS)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection): bloquee el tráfico malintencionado detectado por las firmas en el sistema de inspección de red (NIS).  
 
  **Valor predeterminado**: Sí

- **Intervalo de actualización de firma (en horas)**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval): especifique en horas la frecuencia con que el dispositivo busca nuevas actualizaciones de firmas de Defender.  
 
  **Valor predeterminado**: 4

- **Configurar la prioridad baja de CPU para los exámenes programados**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority): cuando se establece en *Sí*, la prioridad de CPU para los exámenes se establece en baja. Cuando el valor es *No configurado*, no hay cambios en la prioridad de CPU para los exámenes programados.  

    **Valor predeterminado**: Sí

- **Bloqueo de la protección en el acceso de Defender**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection): cuando se configura en *Sí*, la protección en el acceso de Microsoft Defender está habilitada.  

  **Valor predeterminado**: Sí

- **Tipo de examen del sistema para realizar**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter): tipo de examen de Defender.  

  **Valor predeterminado**: examen rápido

- **Examinar todas las descargas**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection): cuando se establece en *Sí*, Defender examina todos los archivos descargados y los datos adjuntos.  

  **Valor predeterminado**: Sí

- **Días antes de eliminar el malware en cuarentena**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware): especifique cuántos días se mantendrán en cuarentena los elementos en el sistema antes de que se eliminen automáticamente. Cuando se establece en cero, los elementos en cuarentena no se eliminan automáticamente nunca.  

  **Valor predeterminado**: 0

- **Hora de inicio del examen programada**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime): programe una hora del día para que Defender examine los dispositivos. 
  
  Opción relacionada de esta lista: *Defender/ScheduleScanDay*   

  **Valor predeterminado**: 2 AM

- **Protección que proporciona la nube**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection): cuando se establece en *Sí*, Microsoft Defender envía información a Microsoft acerca de los problemas que encuentre. Microsoft analizará esa información, obtendrá detalles sobre los problemas que le afectan a usted y a otros clientes, y ofrecerá soluciones mejoradas.

  Cuando esta directiva se establece en *Sí*, puede usar el *tipo de consentimiento de envío de muestra de Defender* para proporcionar a los usuarios control sobre el envío de información desde su dispositivo.  

  **Valor predeterminado**: Sí

- **Defender potentially unwanted app action** (Acción frente a aplicaciones potencialmente no deseadas de Windows Defender)  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection): el Antivirus de Microsoft Defender puede identificar *aplicaciones potencialmente no deseadas* e impedir que se descarguen e instalen en puntos de conexión de la red. 
 
  - Cuando se establece en *Bloquear*, Microsoft Defender bloquea las aplicaciones potencialmente no deseadas y las muestra en el historial, junto con otras amenazas.
  - Cuando se establece en *Auditar*, Microsoft Defender detecta aplicaciones potencialmente no deseadas pero no las bloquea. La información sobre las aplicaciones para las que Microsoft Defender habría tomado medidas se puede encontrar al buscar eventos creados por Microsoft Defender en el Visor de eventos.  
  - Cuando se establece en *Valor predeterminado del dispositivo*, la protección de aplicaciones potencialmente no deseadas está desactivada.  
 
  **Valor predeterminado**: Bloquear

- **Tiempo de expiración extendido en la nube de Defender**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout): especifique el tiempo máximo durante el que Antivirus de Microsoft Defender debe bloquear un archivo mientras espera un resultado de la nube. La cantidad base de tiempo que espera Microsoft Defender es de 10 segundos. El tiempo adicional que especifique aquí (hasta 50 segundos) se agrega a los 10 segundos. En la mayoría de los casos, la detección tarda menos que el tiempo máximo. Si amplía el tiempo, permitirá que la nube investigue a fondo los archivos sospechosos.  

  De forma predeterminada, el valor de tiempo expandido es 0 (deshabilitado). Intune recomienda que habilite esta opción y que especifique al menos 20 segundos adicionales.  
 
  **Valor predeterminado**: 0

- **Examinar archivos de almacenamiento**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning): se configura en *Sí* para que Microsoft Defender examine los archivos de almacenamiento.  

  **Valor predeterminado**: Sí

- **Programación de exámenes de sistema de Defender**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday): programe el día en que Defender examina los dispositivos. 
 
  Opción relacionada de esta lista: *Defender/ScheduleScanTime*

  **Valor predeterminado**: definido por el usuario

- **Supervisión de comportamiento**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring): configúrelo en *Sí* para activar la funcionalidad Supervisión de comportamiento de Microsoft Defender. Insertados en Windows 10, los sensores de Supervisión de comportamiento de Microsoft Defender recopilan y procesan las señales de comportamiento del sistema operativo y envían estos datos de sensor a la instancia de nube privada y aislada de ATP de Microsoft Defender.  

  **Valor predeterminado**: Sí

- **Examinar archivos abiertos desde carpetas de red**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles): configúrelo en *Sí* para que Microsoft Defender examine los archivos de la red. El usuario no podrá quitar el malware detectado de los archivos de solo lectura.  

  **Valor predeterminado**: Sí

- **Defender cloud block level** (Nivel de bloqueo en la nube de Windows Defender)  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel): use esta directiva para determinar el nivel de rigor del Antivirus de Microsoft Defender para el bloqueo y análisis de los archivos sospechosos. Las opciones son:

  - Alto: bloquea de forma agresiva los archivos desconocidos mientras efectúa una optimización del rendimiento (mayor posibilidad de falsos positivos)
  - Más elevado: bloquea de forma agresiva los archivos desconocidos y aplica medidas de protección adicionales (podría afectar al rendimiento del dispositivo)
  - Tolerancia cero: bloquea todos los archivos ejecutables desconocidos

  **Valor predeterminado**: No configurado

- **Supervisión en tiempo real**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring): configúrelo en *Sí* para permitir la supervisión en tiempo real de Microsoft Defender.  

  **Valor predeterminado**: Sí

- **Límite de uso de la CPU durante un examen**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor): especifique el promedio máximo de uso de porcentaje de CPU para Microsoft Defender durante un examen.  

  **Valor predeterminado**: 50

- **Examinar unidades de red asignadas durante un examen completo**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives): configúrelo en *Sí* para que Microsoft Defender examine los archivos de la red. El usuario no puede quitar el malware detectado de los archivos de solo lectura.

  Parámetro relacionado de esta lista: *Defender/AllowScanningNetworkFiles*

  **Valor predeterminado**: Sí

- **Bloqueo del acceso de usuario final a Defender**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess): configúrelo en *Sí* para bloquear el acceso a los usuarios finales a la interfaz de usuario de Microsoft Defender en su dispositivo.  

  **Valor predeterminado**: Sí

- **Hora de inicio de examen rápido**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime): programe una hora del día para que Defender ejecute un examen rápido.  

  **Valor predeterminado**: 2 AM

## <a name="microsoft-defender-firewall"></a>Firewall de Microsoft defender
Para más información, vea [Firewall CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) (CSP de Firewall) en la documentación de Windows.

- **Tiempo de inactividad de asociación de seguridad antes de la eliminación** - *MdmStore/Global/SaIdleTime*   
  Las asociaciones de seguridad se eliminan si no se detecta tráfico de red para este número de segundos.  
  **Valor predeterminado**: 300

- **Protocolo de transferencia de archivos** - *MdmStore/Global/DisableStatefulFtp*   
  Bloquea el Protocolo de transferencia de archivos con estado.  
  **Valor predeterminado**: Sí

- **Puesta de paquetes en cola** - *MdmStore/EnablePacketQueue/Global*    
  Especifique cómo se habilita el escalado para el software en el lado de recepción para la recepción cifrada y el reenvío no cifrado para un escenario de puerta de enlace de túnel de IPsec. Esto garantiza que se conserva el orden de los paquetes.  
  **Valor predeterminado**: Valor predeterminado del dispositivo

- **Dominio del perfil de Firewall** - *FirewallRules/FirewallRuleName/perfiles*  
  Especifica los perfiles a la que pertenece la regla: dominio, privado o público. Este valor representa el perfil para las redes que están conectadas a dominios.  

  Opciones de configuración disponibles:  
  - **Unicast responses to multicast broadcasts required** (Respuestas de unidifusión a tráfico de difusión o multidifusión requeridas)  
    **Valor predeterminado**: Sí

  - **Authorized application rules from group policy merged** (Reglas de aplicación autorizadas de la directiva de grupo combinadas)  
    **Valor predeterminado**: Sí

  - **Inbound notifications blocked** (Notificaciones entrantes bloqueadas)  
    **Valor predeterminado**: Sí

  - **Global port rules from group policy merged** (Reglas de puerto globales de la directiva de grupo combinadas)  
    **Valor predeterminado**: Sí

  - **Stealth mode blocked** (Modo sigiloso bloqueado)  
    **Valor predeterminado**: Sí

  - **Firewall habilitado**  
    **Valor predeterminado**: Permitido

  - **Connection security rules from group policy not merged** (Reglas de seguridad de conexión de la directiva de grupo no combinadas)  
    **Valor predeterminado**: Sí

  - **Policy rules from group policy not merged** (Reglas de directiva de la directiva de grupo no combinadas)  
    **Valor predeterminado**: Sí

- **Perfil de Firewall público** - *FirewallRules/FirewallRuleName/perfiles*  
  Especifica los perfiles a la que pertenece la regla: dominio, privado o público. Este valor representa el perfil para las redes públicas. Estas redes se clasifican como públicas por los administradores en el host del servidor. La clasificación se produce la primera vez que el host se conecta a la red. Por lo general, estas redes se encuentran en aeropuertos, cafeterías y otros lugares públicos, donde otros usuarios o el administrador de la red no son de confianza.  

  Opciones de configuración disponibles:

  - **Inbound connections blocked** (Conexiones entrantes bloqueadas)  
    **Valor predeterminado**: Sí 

  - **Unicast responses to multicast broadcasts required** (Respuestas de unidifusión a tráfico de difusión o multidifusión requeridas)  
    **Valor predeterminado**: Sí  

  - **Stealth mode required** (Modo sigiloso requerido)  
    **Valor predeterminado**: Sí 
 
  - **Outbound connections required** (Conexiones salientes requeridas)  
    **Valor predeterminado**: Sí  

  - **Authorized application rules from group policy merged** (Reglas de aplicación autorizadas de la directiva de grupo combinadas)  
    **Valor predeterminado**: Sí  

  - **Inbound notifications blocked** (Notificaciones entrantes bloqueadas)  
    **Valor predeterminado**: Sí  

  - **Global port rules from group policy merged** (Reglas de puerto globales de la directiva de grupo combinadas)  
    **Valor predeterminado**: Sí

  - **Stealth mode blocked** (Modo sigiloso bloqueado)  
    **Valor predeterminado**: Sí

  - **Firewall habilitado**  
    **Valor predeterminado**: Permitido  

  - **Connection security rules from group policy not merged** (Reglas de seguridad de conexión de la directiva de grupo no combinadas)  
    **Valor predeterminado**: Sí  

  - **Incoming traffic required** (Tráfico entrante requerido)  
    **Valor predeterminado**: Sí

  - **Policy rules from group policy not merged** (Reglas de directiva de la directiva de grupo no combinadas)  
    **Valor predeterminado**: Sí  

- **Perfil de Firewall privado** - *FirewallRules/FirewallRuleName/perfiles*  
  Especifica los perfiles a la que pertenece la regla: dominio, privado o público. Este valor representa el perfil para las redes privadas.  

  Opciones de configuración disponibles: 

  - **Inbound connections blocked** (Conexiones entrantes bloqueadas)  
    **Valor predeterminado**: Sí

  - **Unicast responses to multicast broadcasts required** (Respuestas de unidifusión a tráfico de difusión o multidifusión requeridas)  
    **Valor predeterminado**: Sí

  - **Stealth mode required** (Modo sigiloso requerido)  
    **Valor predeterminado**: Sí

  - **Outbound connections required** (Conexiones salientes requeridas)  
    **Valor predeterminado**: Sí

  - **Inbound notifications blocked** (Notificaciones entrantes bloqueadas)  
    **Valor predeterminado**: Sí

  - **Global port rules from group policy merged** (Reglas de puerto globales de la directiva de grupo combinadas)  
    **Valor predeterminado**: Sí

  - **Stealth mode blocked** (Modo sigiloso bloqueado)  
    **Valor predeterminado**: Sí  

  - **Firewall habilitado**  
    **Valor predeterminado**: Permitido

  - **Authorized application rules from group policy not merged** (Reglas de aplicación autorizadas de la directiva de grupo no combinadas)  
    **Valor predeterminado**: Sí

  - **Connection security rules from group policy not merged** (Reglas de seguridad de conexión de la directiva de grupo no combinadas)  
    **Valor predeterminado**: Sí

  - **Incoming traffic required** (Tráfico entrante requerido)  
    **Valor predeterminado**: Sí

  - **Policy rules from group policy not merged** (Reglas de directiva de la directiva de grupo no combinadas)  
    **Valor predeterminado**: Sí  

- **Método de codificación de claves previamente compartidas de Firewall**  
  **Valor predeterminado**: UTF8

- **Comprobación de la lista de revocación de certificados**  
  **Valor predeterminado**: Valor predeterminado del dispositivo

## <a name="web--network-protection"></a>Protección de la red y la Web  

- **Tipo de protección de red**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection): esta directiva permite activar o desactivar la protección de red en Protección contra vulnerabilidades de seguridad de Microsoft Defender. Protección de red es una característica de Protección contra vulnerabilidades de seguridad de Microsoft Defender que evita que los empleados que usan una aplicación accedan a estafas de suplantación de identidad, sitios que hospedan vulnerabilidades de seguridad y contenido malintencionado en Internet. Esto incluye impedir que exploradores de terceros se conecten a sitios peligrosos.  

  Cuando se establece en *Habilitar* o *Modo de auditoría*, los usuarios no pueden desactivar la protección de red, y puede usar el Centro de seguridad de Microsoft Defender para ver información sobre los intentos de conexión.  
 
  - La opción *Habilitar* impedirá a los usuarios y aplicaciones conectarse a dominios peligrosos.  
  - La opción *Modo de auditoría* no impide a los usuarios y aplicaciones conectarse a dominios peligrosos.  

  Cuando se establece en *Definido por el usuario*, no se impide a los usuarios y aplicaciones que se conecten a dominios peligrosos, y la información sobre las conexiones no está disponible en el Centro de seguridad de Microsoft Defender.  

  **Valor predeterminado**: Modo de auditoría

- **Require SmartScreen for Microsoft Edge** (Requerir SmartScreen para Microsoft Edge)  
  [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen): Microsoft Edge usa SmartScreen de Microsoft Defender (activado) para proteger a los usuarios de software malintencionado y posibles estafas de suplantación de identidad de forma predeterminada. De forma predeterminada, esta directiva está habilitada (establecida en *Sí*) y cuando se habilita impide que los usuarios desactiven SmartScreen de Microsoft Defender.  Cuando la directiva en vigor para un dispositivo es igual a No configurado, los usuarios pueden desactivar SmartScreen de Microsoft Defender, lo que deja el dispositivo sin protección.  

  **Valor predeterminado**: Sí
  
- **Block malicious site access** (Bloquear el acceso a sitios malintencionados)  
  [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride): de forma predeterminada, Microsoft Edge permite a los usuarios omitir las advertencias de SmartScreen de Microsoft Defender sobre sitios potencialmente malintencionados, lo que les permite continuar al sitio. Con esta directiva habilitada (configurada en *Sí*), Microsoft evita que los usuarios omitan las advertencias e impedir que continúen al sitio.  

  **Valor predeterminado**: Sí

- **Block unverified file download** (Bloquear la descarga de archivos no comprobados)  
  [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles): de forma predeterminada, Microsoft Edge permite a los usuarios omitir las advertencias de SmartScreen de Microsoft Defender sobre archivos potencialmente malintencionados, lo que les permite continuar con la descarga de los archivos no comprobados. Con esta directiva habilitada (configurada en *Sí*), se impide a los usuarios omitir las advertencias y no pueden descargar los archivos no comprobados.  

  **Valor predeterminado**: Sí

## <a name="windows-hello-for-business"></a>Windows Hello para empresas  

Para más información, vea [PassportForWork CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp) (CSP de PassportForWork) en la documentación de Windows.

- **Configurar Windows Hello para empresas** - *TenantId/Policies/UsePassportForWork*    
  Windows Hello para empresas es un método alternativo para iniciar sesión en dispositivos Windows mediante la sustitución de contraseñas, tarjetas inteligentes y tarjetas inteligentes virtuales.  

  - Cuando se establece en *sí*, se habilita esta directiva y el dispositivo aprovisiona Windows Hello para empresas.  
  - Cuando se establece en *no configurado*, la línea de base no afecta a la configuración de la Directiva del dispositivo. Esto significa que si Windows Hello para empresas está deshabilitado en un dispositivo, permanece deshabilitado. Si está habilitada, permanece habilitada. 

  No se puede deshabilitar Windows Hello para empresas a través de esta línea base. Puede deshabilitar Windows Hello para empresas al configurar la [inscripción de Windows](windows-hello.md)o como parte de un perfil de configuración de dispositivo para la [protección de identidades](identity-protection-configure.md).  

Windows Hello para empresas es un método alternativo para iniciar sesión en dispositivos Windows mediante la sustitución de contraseñas, tarjetas inteligentes y tarjetas inteligentes virtuales.  

  Si habilita o no configura esta opción de directiva, el dispositivo aprovisiona Windows Hello para empresas. Si deshabilita esta opción de directiva, el dispositivo no aprovisiona Windows Hello para empresas para ningún usuario.

  Intune no admite la deshabilitación de Windows Hello. En su lugar, puede configurar la directiva para habilitar Windows Hello para empresas (Sí) o no configurar Windows Hello directamente (no configurado). Cuando no está configurado, un dispositivo puede recibir la configuración a través de otra directiva, que puede habilitar o deshabilitar esta característica.  

  **Valor predeterminado**: Sí  

- **Requerir minúsculas en el PIN** - *TenantId/Policies/PINComplexity/LowercaseLetters*  
  **Valor predeterminado**: Permitido  

- **Requerir caracteres especiales en el PIN** - *TenantId/Policies/PINComplexity/SpecialCharacters*  
  **Valor predeterminado**: Permitido  

- **Requerir mayúsculas en el PIN** - *TenantId/Policies/PINComplexity/UppercaseLetters*   
  **Valor predeterminado**: Permitido  

