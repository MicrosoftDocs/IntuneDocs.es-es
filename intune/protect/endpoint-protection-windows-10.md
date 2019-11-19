---
title: 'Configuración de la protección para dispositivos Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: En los dispositivos Windows 10, use o configure opciones de protección de punto de conexión para habilitar características de Microsoft Defender, como Protección de aplicaciones, firewall, SmartScreen, cifrado y BitLocker, Protección contra vulnerabilidades, Control de aplicaciones, Security Center y seguridad de dispositivos locales en Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: karthig
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e2909e7ad1ced9483a6cec58f1f3009f56946f5f
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74058423"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Configuración de Windows 10 (y versiones posteriores) para proteger dispositivos mediante Intune

En Microsoft Intune se incluyen varias opciones de configuración para ayudarle a proteger sus dispositivos. En este artículo se describen todas las opciones que puede habilitar y configurar en Windows 10 y dispositivos más recientes. Estas opciones se crean en un perfil de configuración de Endpoint Protection, en Intune, para controlar la seguridad, incluidos BitLocker y Microsoft Defender.  

Para configurar el Antivirus de Microsoft Defender, vea [Restricciones de dispositivos con Windows 10](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).  

## <a name="before-you-begin"></a>Antes de comenzar  

[Cree un perfil de configuración de dispositivos de Endpoint Protection](endpoint-protection-configure.md).  

Para obtener más información sobre los proveedores de servicios de configuración (CSP), consulte [Referencia del proveedor de servicios de configuración](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).  

## <a name="microsoft-defender-application-guard"></a>Protección de aplicaciones de Microsoft defender  

Al utilizar Microsoft Edge, Protección de aplicaciones de Microsoft Defender protege su entorno de sitios que no son de confianza para su organización. Cuando los usuarios visitan sitios que no aparecen en el límite de red aislada, estos se abren en una sesión de exploración virtual de Hyper-V. Los sitios de confianza se definen mediante un límite de red, que puede configurarse en Configuración de dispositivos.  

Protección de aplicaciones solo está disponible para dispositivos de Windows 10 (de 64 bits). Con este perfil se instala un componente de Win32 para activar Protección de aplicaciones.  

- **Protección de aplicaciones**  
  **Valor predeterminado**: No configurado  
   CSP de protección de aplicaciones: [Settings/AllowWindowsDefenderApplicationGuard](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **Habilitado para Edge**: activa esta característica, que abre sitios que no son de confianza en un contenedor de exploración virtualizado de Hyper-V.  
  - **No configurado** : cualquier sitio (de confianza y que no es de confianza) puede abrirse en el dispositivo.  

- **Comportamiento del Portapapeles**  
  **Valor predeterminado**: No configurado  
   CSP de protección de aplicaciones: [Settings/ClipboardSettings](https://go.microsoft.com/fwlink/?linkid=872351)  

  Seleccione qué acciones de copiar y pegar se permiten entre el equipo local y el explorador virtual de la Protección de aplicaciones.  
  - **No configurado**.  
  - **Permitir copiar y pegar solo del equipo al explorador**  
  - **Permitir copiar y pegar desde el explorador a PC solamente**  
  - **Permitir copiar y pegar entre equipos y exploradores**  
  - **Bloquear la copia y pegar entre equipos y exploradores**  

- **Contenido del portapapeles**  
  Esta opción solo está disponible cuando el *comportamiento del portapapeles* está establecido en uno de los valores de *permitir* .  
  **Valor predeterminado**: No configurado  
  CSP de protección de aplicaciones: [Settings/ClipboardFileType](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  Seleccione el contenido del portapapeles permitido.  
  - **No configurado**.  
  - **Texto**  
  - **Imágenes**  
  - **Texto e imágenes**  

- **Contenido externo en sitios de empresa**  
  **Valor predeterminado**: No configurado  
  CSP de protección de aplicaciones: [Settings/BlockNonEnterpriseContent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - **Bloquear**: impida que se cargue contenido de sitios web no aprobados.  
  - **Sin configurar**: los sitios que no sean de empresa se pueden abrir en el dispositivo.  
 
- **Imprimir desde el explorador virtual**  
  **Valor predeterminado**: No configurado  
  CSP de protección de aplicaciones: [Settings/PrintingSettings](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **Allow** : permite la impresión del contenido seleccionado desde el explorador virtual.  
  - **No configurado** Deshabilitar todas las características de impresión.  

  Al *permitir* la impresión, puede configurar las siguientes opciones:
  - **Tipos de impresión** Seleccione una o varias de las opciones siguientes:  
    - PDF  
    - XPS  
    - Impresoras locales
    - Impresoras de red  

- **Recopilar registros**  
  **Valor predeterminado**: No configurado  
  CSP de protección de aplicaciones: [Audit/AuditApplicationGuard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **Permitir**: recopile registros de eventos que se producen dentro de una sesión de exploración de Protección de aplicaciones.  
  - **Sin configurar**: no recopile ningún registro dentro de la sesión de exploración.  

- **Conservar los datos del explorador generados por el usuario**  
  **Valor predeterminado**: No configurado  
  CSP de protección de aplicaciones: [Settings/AllowPersistence](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **Permitir**: guarde los datos de usuario (como las contraseñas, los favoritos y las cookies) creados durante la sesión de exploración virtual de la Protección de aplicaciones.  
  - **Sin configurar**: descarte los datos y los archivos descargados por el usuario cuando se reinicia el dispositivo, o cuando un usuario cierra sesión.  

- **Aceleración gráfica**  
 **Valor predeterminado**: No configurado  
  CSP de protección de aplicaciones: [Settings/AllowVirtualGPU](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - **Habilitar**: cargue vídeos y sitios web con un uso intensivo de gráficos de forma más rápida mediante el acceso a una unidad de procesamiento de gráficos virtuales.  
  - **No configurado** Usar la CPU del dispositivo para los gráficos; No utilice la unidad de procesamiento de gráficos virtuales.  

- **Descargar archivos al sistema de archivos host**  
  **Valor predeterminado**: No configurado  
  CSP de protección de aplicaciones: [Settings/SaveFilesToHost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **Habilitar**: los usuarios pueden descargar archivos desde el explorador virtualizado al sistema operativo host.  
  - **Sin configurar**: mantiene los archivos locales en el dispositivo (valor predeterminado) y no descarga archivos en el sistema de archivos host.  

## <a name="microsoft-defender-firewall"></a>Firewall de Microsoft defender  
 
### <a name="global-settings"></a>Configuración global  

Esta configuración se aplica a todos los tipos de redes.  

- **Protocolo de transferencia de archivos**  
  **Valor predeterminado**: No configurado  
   CSP de Firewall: [MdmStore/global/DisableStatefulFtp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - **Bloquear**: deshabilite FTP con estado.  
  - **Sin configurar**: el firewall no realiza el filtrado de FTP con estado para permitir las conexiones secundarias.  

- **Tiempo de inactividad de asociación de seguridad antes de la eliminación**  
  **Valor predeterminado**: *Sin configurar*  
   CSP de Firewall: [MdmStore/global/SaIdleTime](https://go.microsoft.com/fwlink/?linkid=872539)  

   Especifique un tiempo de inactividad en segundos, tras el cual se eliminarán las asociaciones de seguridad.   

- **Codificación de clave precompartida**  
  **Valor predeterminado**: No configurado  
   CSP de Firewall: [MdmStore/global/PresharedKeyEncoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - **Habilitar** : codifique las claves presesgadas mediante UTF-8.  
   - **No configurado** : codifique las claves presesgadas con el valor de almacén local.  

- **Exenciones de IPsec**  
  **Valor predeterminado**: *0 seleccionado*  
   CSP de Firewall: [MdmStore/global/IPsecExempt](https://go.microsoft.com/fwlink/?linkid=872547)

   Seleccione uno o varios de los siguientes tipos de tráfico que se van a excluir de IPsec:  
   - **Códigos de tipo ICMP de IPv6 de descubrimiento de vecinos**  
   - **ICMP**  
   - **Códigos de tipo ICMP de IPv6 de descubrimiento de enrutadores**  
   - **Tráfico de red DHCP de IPv4 e IPv6**  

- **Comprobación de la lista de revocación de certificados**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [MdmStore/global/CRLcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  seleccione la forma en la que el dispositivo debe comprobar la lista de revocación de certificados. Las opciones son:  
  - **Deshabilitar comprobación de CRL**  
  - **Error de comprobación de CRL solo en el certificado revocado**  
  - Error **de comprobación de CRL en los errores encontrados**.  
 

- **Coincidencia pertinente del conjunto de autenticación por módulo de generación de claves**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [MdmStore/global/OpportunisticallyMatchAuthSetPerKM](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **Habilitar**: los módulos de generación de claves deben omitir solo los conjuntos de aplicaciones de autenticación que no admitan.  
  - **Sin configurar**: los módulos de generación de claves deben omitir el conjunto de autenticación en su totalidad si no admiten todos los conjuntos de autenticación especificados.  


- **Puesta de paquetes en cola**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [MdmStore/global/EnablePacketQueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  Especifique cómo se habilita el escalado de software en el lado de recepción para la recepción cifrada y el reenvío de texto no cifrado para un escenario de puerta de enlace de túnel IPsec. Esta opción garantiza que se conserve el orden de los paquetes. Las opciones son:  
  - **No configurado**.  
  - **Deshabilitar todas las colas de paquetes**  
  - **Poner en cola los paquetes cifrados de entrada únicamente**  
  - **Poner en cola los paquetes después de que el descifrado se realice solo para reenviar**  
  - **Configurar los paquetes entrantes y salientes**  

### <a name="network-settings"></a>Configuración de red  

La siguiente configuración se muestra en este artículo una sola vez, pero todas se aplican a los tres tipos de red específicos:  
- **Red de dominio (Workplace)**  
- **Red privada (reconocible)**  
- **Red pública (no reconocible)**  

#### <a name="general-settings"></a>Configuración general  

- **Firewall de Microsoft defender**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [EnableFirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **Habilitar**: active el firewall y la seguridad avanzada. 
  - **Sin configurar**: permite todo el tráfico de red, independientemente de las demás configuraciones de directiva.  

- **Modo sigiloso**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [DisableStealthMode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - **No configurado**.  
  - **Block** : firewall no funciona en modo oculto. Bloquear el modo sigiloso también le permite bloquear la **exención de paquete protegido por IPsec**.  
  - **Permitir** : el firewall funciona en modo oculto, lo que ayuda a evitar las respuestas a las solicitudes de sondeo.  

- **Exención de paquetes protegidos por IPsec con el modo invisible**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [DisableStealthModeIpsecSecuredPacketExemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  Esta opción se omite si el *modo Stealth* está establecido en *Block*.  

  - **No configurado**.  
  - **Bloque** : los paquetes protegidos por IPsec no reciben exenciones.  
  - **Permitir** -habilitar exenciones. El modo invisible del firewall no debe impedir que el equipo host responda al tráfico de red no solicitado protegido por IPsec.  

- **Blindada**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [blindado](https://go.microsoft.com/fwlink/?linkid=872561)  
    - **No configurado**.  
    - **Bloquear** : cuando el Firewall de Microsoft defender está activado y esta opción está establecida en *bloquear*, se bloquea todo el tráfico entrante, independientemente de la configuración de la Directiva. 
    - **Permitir** : cuando se establece en *permitir*, esta opción está desactivada y se permite el tráfico entrante en función de otras configuraciones de directiva.

- **Respuestas de unidifusión a tráfico de difusión o multidifusión**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [DisableUnicastResponsesToMulticastBroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  Normalmente, no desea recibir respuestas de unidifusión a mensajes de difusión o multidifusión. Estas respuestas pueden indicar un ataque por denegación de servicio (DDoS) o un atacante que intenta buscar un equipo activo conocido.  
  - **No configurado**.  
  - **Bloquear**: deshabilite las respuestas de unidifusión a multidifusiones.  
  - **Permitir**: permita respuestas de unidifusión a tráfico de difusión o multidifusión.  

- **Notificaciones entrantes**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [DisableInboundNotifications](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - **No configurado**.  
  - **Bloquear** : oculte las notificaciones que se usarán cuando se bloquee una aplicación para que no escuche en un puerto.  
  - **Permitir**: habilita esta configuración y puede mostrar una notificación a los usuarios cuando se impide que una aplicación escuche en un puerto.  

- **Acción predeterminada para conexiones entrantes**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [DefaultOutboundAction](https://aka.ms/intune-firewall-outboundaction)  
  
  Configurar el Firewall de la acción predeterminada se realiza en las conexiones salientes. Esta configuración se aplicará a la versión 1809 y posteriores de Windows.  

  - **No configurado**.  
  - **Bloquear** : la acción de Firewall predeterminada no se ejecuta en el tráfico saliente a menos que se especifique explícitamente que no se bloquee.  
  - **Permitir** : las acciones de Firewall predeterminadas se ejecutan en conexiones salientes.  

- **Acción predeterminada para conexiones entrantes**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [DefaultInboundAction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - **No configurado**.  
  - **Bloquear**: la acción predeterminada del firewall no se ejecuta en las conexiones entrantes.  
  - **Permitir** : las acciones de Firewall predeterminadas se ejecutan en conexiones entrantes.  

#### <a name="rule-merging"></a>Combinación de reglas  

- **Reglas de Firewall de Microsoft Defender de aplicación autorizada del almacén local**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [AuthAppsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - **No configurado**.  
  - **Bloquear**: las reglas de firewall de aplicación autorizada en el almacén local se omiten y no se aplican.  
  - **Permitir** -
   elegir **Habilitar** aplica las reglas de firewall en el almacén local de forma que se reconozcan y se exija su cumplimiento.  

- **Reglas de Firewall de Microsoft Defender de puerto globales del almacén local**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [GlobalPortsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - **No configurado**.  
  - **Bloquear** : las reglas de Firewall de Puerto global del almacén local se omiten y no se aplican.  
  - **Permitir**: aplique las reglas de puertos globales del firewall en el almacén local de forma que se reconozcan y se exija su cumplimiento.  

- **Reglas de Firewall de Microsoft Defender del almacén local**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [AllowLocalPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872567)  

  - **No configurado**.  
  - **Bloquear** : las reglas de firewall del almacén local se omiten y no se aplican.
  - **Permitir**: aplique las reglas del firewall en el almacén local de forma que se reconozcan y se exija su cumplimiento.  

- **Reglas IPsec del almacén local**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [AllowLocalIpsecPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - **No configurado**.  
  - **Bloquear**: las reglas de seguridad de conexión del almacén local se omiten y no se aplican, independientemente de la versión de esquema y la versión de regla de seguridad de conexión.  
  - **Permitir**: aplique las reglas de seguridad de conexión del almacén local, independientemente del esquema o de las versiones de dichas reglas.  

### <a name="firewall-rules"></a>Reglas de firewall  

Puede **Agregar** una o varias reglas de Firewall personalizadas. Para obtener más información, consulte [agregar reglas de Firewall personalizadas para dispositivos Windows 10](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices).  

Las reglas de Firewall personalizadas admiten las siguientes opciones:  

#### <a name="general-settings"></a>Configuración general:  

- **Nombre**  
  **Valor predeterminado**: *sin nombre*  

  Especifique un nombre descriptivo para la regla. Este nombre aparecerá en la lista de reglas para ayudarle a identificarla.  

- **Descripción**  
  **Valor predeterminado**: *sin descripción*  

  Proporcione una descripción de la regla.  

- **Dirección**   
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [FirewallRules/*FirewallRuleName*/Direction](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  Especifique si esta regla se aplica al tráfico **entrante**o **saliente** . Cuando se establece como **no configurado**, la regla se aplica automáticamente al tráfico saliente.  

- **Acción**  
  **Valor predeterminado**: No configurado  
  CSP de Firewall: [FirewallRules/*FirewallRuleName*/Action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action)y [FirewallRules/*FirewallRuleName*/Action/Type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  Seleccione **permitir** o **bloquear**. Cuando se establece como **no configurado**, la regla tiene como valor predeterminado permitir el tráfico.  

- **Tipo de red**  
  **Valor predeterminado**: 0 seleccionado  
  CSP de Firewall: [FirewallRules/*FirewallRuleName*/profiles](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  Seleccione hasta tres tipos de red a los que pertenece esta regla. Entre las opciones se incluyen **dominio**, **privado**y **público**.  Si no se selecciona ningún tipo de red, la regla se aplica a los tres tipos de red.  

#### <a name="application-settings"></a>Configuración de aplicaciones  

- **Aplicaciones**  
  **Valor predeterminado**: Todo  

  Controle las conexiones de una aplicación o un programa. Seleccione una de las siguientes opciones y, a continuación, complete la configuración adicional:  
  - **Nombre de familia de paquete** : especifique un nombre de familia de paquete. Para buscar el nombre de familia del paquete, use el comando de PowerShell **Get-AppxPackage**.   
    CSP de Firewall: [FirewallRules/*FirewallRuleName*/App/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - **Ruta de acceso de archivo** : debe especificar una ruta de acceso de archivo a una aplicación en el dispositivo cliente, que puede ser una ruta de acceso absoluta o una ruta de acceso relativa. Por ejemplo: C:\Windows\System\Notepad.exe o%WINDIR%\Notepad.exe.  
    CSP de Firewall: [FirewallRules/*FirewallRuleName*/App/FilePath](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Servicio de Windows** : especifique el nombre corto del servicio de Windows si es un servicio y no una aplicación que envía o recibe tráfico. Para buscar el nombre corto del servicio, use el comando de PowerShell **Get-Service**.  
    CSP de Firewall: [FirewallRules/*FirewallRuleName*/App/ServiceName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **Todo**: *no hay ninguna configuración adicional disponible*.  

#### <a name="ip-address-settings"></a>Configuración de la dirección IP  

Especifique las direcciones locales y remotas a las que se aplica esta regla.  

- **Direcciones locales**    
  **Valor predeterminado**: cualquier dirección  
  CSP de Firewall: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  Seleccione **cualquier dirección** o **dirección especificada**.  

  Cuando se usa la *dirección especificada*, se agregan una o más direcciones como una lista separada por comas de las direcciones locales que cubre la regla. Entre los tokens válidos se incluyen:  
  - Use un asterisco "*" para *cualquier* dirección local. Si usa un asterisco, debe ser el único token que use.  
  - Para especificar una subred, use la notación de máscara de subred o de prefijo de red. Si no se especifica una máscara de subred ni un prefijo de red, el valor predeterminado de la máscara de subred es 255.255.255.255.  
  - Una dirección IPv6 no válida.  
  - Un intervalo de direcciones IPv4 con el formato "dirección de Inicio: dirección final" sin espacios incluidos.  
  - Un intervalo de direcciones IPv6 con el formato "dirección de Inicio: dirección final" sin espacios incluidos.  

- **Direcciones remotas**  
  **Valor predeterminado**: cualquier dirección  
  CSP de Firewall: [FirewallRules/*FirewallRuleName*/RemoteAddressRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  Seleccione **cualquier dirección** o **dirección especificada**.  

  Cuando se usa la *dirección especificada*, se agregan una o más direcciones como una lista separada por comas de las direcciones remotas que cubre la regla. Los tokens no distinguen mayúsculas de minúsculas. Entre los tokens válidos se incluyen:  
  - Use un asterisco "*" para *cualquier* dirección remota. Si usa un asterisco, debe ser el único token que use.  
  - "Defaultgateway"  
  - "DHCP"  
  - "DNS"  
  - "WINS"  
  - "Intranet" (compatible con las versiones de Windows 1809 y posteriores)  
  - "RmtIntranet" (compatible con las versiones de Windows 1809 y posteriores)  
  - "Internet" (compatible con las versiones de Windows 1809 y posteriores)  
  - "Ply2Renders" (compatible con las versiones de Windows 1809 y posteriores)  
  - "LocalSubnet" indica cualquier dirección local en la subred local.  
  - Para especificar una subred, use la notación de máscara de subred o de prefijo de red. Si no se especifica una máscara de subred ni un prefijo de red, el valor predeterminado de la máscara de subred es 255.255.255.255.  
  - Una dirección IPv6 no válida.  
  - Un intervalo de direcciones IPv4 con el formato "dirección de Inicio: dirección final" sin espacios incluidos.  
  - Un intervalo de direcciones IPv6 con el formato "dirección de Inicio: dirección final" sin espacios incluidos.  

#### <a name="port-and-protocol-settings"></a>Configuración de puertos y protocolos  
Especifique los puertos locales y remotos a los que se aplica esta regla.  

- **Protocolo**  
  **Valor predeterminado**: cualquiera  
  CSP de Firewall: [FirewallRules/*FirewallRuleName*/protocolo](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  Seleccione una de las siguientes opciones y complete las configuraciones necesarias:  
  - **Todo** : no hay ninguna configuración adicional disponible.  
  - **TCP** : configurar puertos locales y remotos. Ambas opciones admiten todos los puertos o puertos especificados. Escriba los puertos especificados mediante una lista separada por comas.  
    - **Puertos locales** : CSP de Firewall: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Puertos remotos** : CSP de Firewall: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** : configurar puertos locales y remotos. Ambas opciones admiten todos los puertos o puertos especificados. Escriba los puertos especificados mediante una lista separada por comas.  
    - **Puertos locales** : CSP de Firewall: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Puertos remotos** : CSP de Firewall: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **Personalizado** : especifique un número de **Protocolo** personalizado de 0 a 255.  

#### <a name="advanced-configuration"></a>Configuración avanzada  
- **Tipos de interfaz**  
  **Valor predeterminado**: 0 seleccionado  
  CSP de Firewall: [FirewallRules/*FirewallRuleName*/InterfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  Seleccione entre las siguientes opciones:  
  - **Acceso remoto**  
  - **Inalámbrica**  
  - **Red de área local**  

- **Sólo permitir conexiones de estos usuarios**  
  **Predeterminado**: todos los usuarios *(el valor predeterminado es todos los usos cuando no se especifica ninguna lista)*  
  CSP de Firewall: [FirewallRules/*FirewallRuleName*/LocalUserAuthorizationList](https://aka.ms/intunefirewallauthorizedusers)  

  Especifique una lista de usuarios locales autorizados para esta regla. No se puede especificar una lista de usuarios autorizados si esta regla se aplica a un servicio de Windows.  


## <a name="microsoft-defender-smartscreen-settings"></a>Configuración de SmartScreen de Microsoft Defender  
 
Microsoft Edge debe estar instalado en el dispositivo.  

- **SmartScreen para aplicaciones y archivos**  
  **Valor predeterminado**: No configurado  
   CSP SmartScreen: [SmartScreen/EnableSmartScreenInShell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **No configurado** : deshabilita el uso de SmartScreen.  
  - **Habilitar**: habilite Windows SmartScreen para permitir la ejecución de archivos y de aplicaciones. SmartScreen es un componente de antimalware y contra la suplantación de identidad basado en la nube.  

- **Ejecución de archivos no comprobados**  
  **Valor predeterminado**: No configurado  
   CSP SmartScreen: [SmartScreen/PreventOverrideForFilesInShell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **Sin configurar**: deshabilita esta característica y permite que los usuarios finales ejecuten archivos que no se han comprobado.  
  - **Bloquear**: impida que los usuarios finales ejecuten archivos que no se hayan comprobado mediante Windows SmartScreen.  

## <a name="windows-encryption"></a>Cifrado de Windows  
 
### <a name="windows-settings"></a>Configuración de Windows  

- **Cifrar los dispositivos**  
  **Valor predeterminado**: No configurado  
  CSP de BitLocker: [RequireDeviceEncryption](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **Requerir**: pida a los usuarios que habiliten el cifrado de dispositivo. En función de la edición de Windows y la configuración del sistema, se podría pedir a los usuarios lo siguiente:  
    - Confirmar que no está habilitado el cifrado de otro proveedor.  
    - Obligación de desactivar el cifrado de unidad Bitlocker y, después, volver a activar BitLocker.  
  - **No configurado**.  
  
  Si el cifrado de Windows se habilita mientras otro método de cifrado está activo, el dispositivo puede volverse inestable.  

- **Cifrar la tarjeta de almacenamiento (solo móvil)**  
  *Esta configuración solo se aplica a dispositivos móviles Windows 10.*  
  **Valor predeterminado**: No configurado  
  CSP de BitLocker: [RequireStorageCardEncryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - use la opción **Requerir** para cifrar todas las tarjetas de almacenamiento extraíbles su usadas por el dispositivo.  
  - **Sin configurar**: no requiera el cifrado de tarjetas de almacenamiento y no solicite al usuario que lo active.  

### <a name="bitlocker-base-settings"></a>Configuración base de BitLocker  

La configuración base es la configuración de BitLocker universal para todos los tipos de unidades de datos. Esta configuración administra las tareas de cifrado o las opciones de configuración de unidades que el usuario final puede modificar en todos los tipos de unidades de datos.  

- **Advertencia para otro cifrado de disco**  
  **Valor predeterminado**: No configurado  
  CSP de BitLocker: [AllowWarningForOtherDiskEncryption](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **Bloquear**: deshabilite el mensaje de advertencia si hay otro servicio de cifrado de disco activado en el dispositivo.  
  - **No configurado** : permite mostrar la advertencia para que se muestre otro cifrado de disco.  

  Cuando se establece en *bloquear*, puede configurar los siguientes valores:  

  - **Permitir a los usuarios estándar habilitar el cifrado durante la unión a Azure AD**  
    *Esta configuración solo se aplica a dispositivos Azure Active Directory Unidos (Azure ADJ) y depende de la configuración anterior, `Warning for other disk encryption`.*  
    **Valor predeterminado**: No configurado  
    CSP de BitLocker: [AllowStandardUserEncryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **Permitir** : los usuarios estándar (no administradores) pueden habilitar el cifrado de BitLocker cuando se inicia sesión.  
     - **Sin configurar**: solo los administradores pueden habilitar el cifrado de BitLocker en el dispositivo.  

- **Configurar métodos de cifrado**  
  **Valor predeterminado**: No configurado  
  CSP de BitLocker: [EncryptionMethodByDriveType](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **Habilitar**: esta opción para configurar algoritmos de cifrado para el sistema operativo, los datos y las unidades extraíbles.  
  - **Sin configurar**: BitLocker usa XTS-AES de 128 bits como método de cifrado predeterminado o el método de cifrado especificado por cualquier script de instalación.  

  Cuando se establece en *Habilitar*, puede configurar estos valores:  

  - **Cifrado para unidades de sistema operativo**  
    **Valor predeterminado**: XTS-AES 128 bits  
   
    seleccione el método de cifrado para las unidades del sistema operativo. Se recomienda que use el algoritmo XTS-AES.  
    - **AES-CBC 128 bits**  
    - **AES-CBC 256 bits**  
    - **XTS-AES 128 bits**  
    - **XTS-AES 256 bits**  

  - **Cifrado para unidades de datos fijas**  
    **Valor predeterminado**: AES-CBC 128 bits  
   
    seleccione el método de cifrado para las unidades de datos fijas (integradas). Se recomienda que use el algoritmo XTS-AES.  
    - **AES-CBC 128 bits**  
    - **AES-CBC 256 bits**  
    - **XTS-AES 128 bits**  
    - **XTS-AES 256 bits**  

  - **Cifrado para unidades de datos extraíbles**  
    **Valor predeterminado**: AES-CBC 128 bits  

    seleccione el método de cifrado para unidades de datos extraíbles. Si la unidad extraíble se usa con dispositivos que no ejecutan Windows 10, entonces se recomienda que use el algoritmo AES-CBC.  
    - **AES-CBC 128 bits**  
    - **AES-CBC 256 bits**  
    - **XTS-AES 128 bits**  
    - **XTS-AES 256 bits**  

### <a name="bitlocker-os-drive-settings"></a>Configuración de BitLocker para unidades de sistema operativo  

Esta configuración se aplica específicamente a las unidades de datos de sistema operativo.  

- **Autenticación adicional al inicio**  
  **Valor predeterminado**: No configurado  
  CSP de BitLocker: [SystemDrivesRequireStartupAuthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **Requerir**: configure los requisitos de autenticación para el inicio de equipos, incluido el uso del Módulo de plataforma segura (TPM).  
  - **No configurado** : solo se configuran las opciones básicas de los dispositivos con un TPM.  

  Cuando se establece en *Requerir*, puede configurar estos valores:  

  - **BitLocker con un chip de TPM no compatible**  
    **Valor predeterminado**: No configurado  

    - **Bloquear**: deshabilite el uso de BitLocker cuando un dispositivo no tenga un chip TPM compatible.  
    - **Sin configurar**: los usuarios pueden usar BitLocker sin un chip de TPM compatible. BitLocker puede requerir una contraseña o una clave de inicio.  

  - **Inicio de TPM compatible**  
    **Valor predeterminado**: Permitir TPM  

    Configure si TPM está permitido, es obligatorio o no está permitido.  

    - **Permitir TPM**  
    - **No permitir TPM**  
    - **Requerir TPM**  

  - **PIN de inicio de TPM compatible**  
    **Valor predeterminado**: permitir PIN de inicio con TPM  

    seleccione una opción para permitir, no permitir o exigir el uso de un PIN de inicio con el chip TPM. Habilitar un PIN de inicio requiere la interacción del usuario final.  

    - **Permitir PIN de inicio con TPM**  
    - **No permitir PIN de inicio con TPM**  
    - **Requerir PIN de inicio con TPM**

  - **Clave de inicio de TPM compatible**  
    **Valor predeterminado**: permitir clave de inicio con TPM  

    seleccione una opción para permitir, no permitir o exigir el uso de una clave de inicio con el chip TPM. Habilitar una clave de inicio requiere la interacción del usuario final.  

    - **Permitir clave de inicio con TPM**  
    - **No permitir clave de inicio con TPM**  
    - **Requerir clave de inicio con TPM**  

  - **PIN y clave de inicio de TPM compatible**  
    **Valor predeterminado**: permitir clave de inicio y PIN con TPM  

    seleccione una opción para permitir, no permitir o exigir el uso de una clave de inicio y un PIN con el chip TPM. Habilitar una clave y un PIN de inicio requiere la interacción del usuario final.  
    - **Permitir clave de inicio y PIN con TPM**  
    - **No permitir clave de inicio y PIN con TPM**  
    - **Requerir clave de inicio y PIN con TPM**   

- **Longitud mínima del PIN**  
    **Valor predeterminado**: No configurado  
    CSP de BitLocker: [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **Habilitar** Configure una longitud mínima para el PIN de inicio de TPM.  
    - **Sin configurar**: los usuarios pueden configurar un PIN de inicio de cualquier longitud entre 6 y 20 dígitos.  

  Cuando se establece en *Habilitar*, puede configurar estos valores:  

  - **Mínimo de caracteres**  
    **Valor predeterminado**: CSP de BitLocker *no configurado* : [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)  

    escriba el número de caracteres necesarios para el PIN de inicio entre **4**- y **20**.  

- **Recuperación de unidades de sistema operativo**  
  **Valor predeterminado**: No configurado   
  CSP de BitLocker: [SystemDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **Habilitar**: controle cómo se recuperan las unidades del sistema operativo protegidas mediante BitLocker cuando la información de inicio necesaria no está disponible.  
  - **Sin configurar**: se admiten las opciones de recuperación predeterminadas para la recuperación de BitLocker. De forma predeterminada, se permite un DRA, las opciones de recuperación las especifica el usuario, incluida la contraseña de recuperación y la clave de recuperación, y no se guarda una copia de seguridad de la información de recuperación en AD DS.  

  Cuando se establece en *Habilitar*, puede configurar estos valores:  

  - **Agente de recuperación de datos basada en certificados**  
    **Valor predeterminado**: No configurado  
     
    - **Bloquear** : impedir el uso del agente de recuperación de datos con unidades del sistema operativo protegidas por BitLocker.  
    - **No configurado** : permite el uso de agentes de recuperación de datos con unidades del sistema operativo protegidas por BitLocker.  

  - **Creación de contraseña de recuperación por el usuario**  
    **Valor predeterminado**: permitir contraseña de recuperación de 48 dígitos  

    seleccione las opciones de los usuarios para generar una contraseña de recuperación de 48 dígitos (permitido, exigido o no permitido).  
    - **Permitir contraseña de recuperación de 48 dígitos**  
    - **No permitir contraseña de recuperación de 48 dígitos**  
    - **Requerir contraseña de recuperación de 48 dígitos**  

  - **Creación de clave de recuperación por el usuario**  
    **Valor predeterminado**: permitir clave de recuperación de 256 bits  

    seleccione las opciones de los usuarios para generar una clave de recuperación de 256 bits (permitido, exigido o no permitido).  
    - **Permitir clave de recuperación de 256 bits**  
    - **No permitir clave de recuperación de 256 bits**  
    - **Requerir clave de recuperación de 256 bits**  

  - **Opciones de recuperación en el asistente para configuración de BitLocker**  
    **Valor predeterminado**: No configurado  

    - **Bloquear**: los usuarios no pueden ver ni cambiar las opciones de recuperación. Cuando se establece en 
    - **Sin configurar**: los usuarios pueden ver y modificar las opciones de recuperación cuando activen BitLocker. 
 
  - **Guardar información de recuperación de BitLocker en Azure Active Directory**  
    **Valor predeterminado**: No configurado  

    - **Habilitar**: almacene la información de recuperación de BitLocker en Azure Active Directory (Azure AD).  
    - **No configurado** : la información de recuperación de BitLocker no se almacena en AAD.  

  - **Información de recuperación de BitLocker almacenada en Azure Active Directory**  
    **Valor predeterminado**: Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves  

    configure qué partes de la información de recuperación de BitLocker se almacenan en Azure AD. Elija de entre las siguientes opciones:  
    - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**  
    - **Realizar copia de seguridad solo de contraseñas de recuperación**  

  - **Rotación de contraseñas de recuperación controlada por el cliente**  
    **Valor predeterminado**: rotación de claves habilitada para dispositivos unidos a Azure ad  
    CSP de BitLocker: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Esta configuración inicia una rotación de contraseñas de recuperación controlada por el cliente después de la recuperación de una unidad del sistema operativo (mediante BOOTMGR o WinRE).  

    - No configurado  
    - Rotación de claves deshabilitada  
    - Rotación de claves habilitada para el Azure AD desices  
    - Rotación de claves habilitada para dispositivos Azure AD e híbridos Unidos  

  - **Almacenar información de recuperación en Azure Active Directory antes de habilitar BitLocker**  
    **Valor predeterminado**: No configurado  
 
     Impedir que los usuarios habiliten BitLocker a menos que el equipo realice correctamente una copia de seguridad de la información de recuperación de BitLocker en Azure Active Directory.  

    - **Requerir**: impida que los usuarios activen BitLocker hasta que la información de recuperación de BitLocker se almacene correctamente en Azure AD.  
    - **Sin configurar**: los usuarios pueden activar BitLocker, incluso aunque la información de recuperación no esté almacenada correctamente en Azure AD.  

- **URL y mensaje de recuperación previos al arranque**  
  **Valor predeterminado**: No configurado  
  CSP de BitLocker: [SystemDrivesRecoveryMessage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **Habilitar** : configure el mensaje y la dirección URL que se muestran en la pantalla de recuperación de la clave de prearranque.  
  - **Sin configurar**: deshabilite esta característica.  
  
  Cuando se establece en *Habilitar*, puede configurar estos valores:  
  - **Mensaje de recuperación previo al arranque**  
    **Valor predeterminado**: Usar la dirección URL y el mensaje de recuperación predeterminados   
 
    configure la forma en la que se muestra a los usuarios el mensaje de recuperación previo al arranque. Elija de entre las siguientes opciones:  
    - **Usar la dirección URL y el mensaje de recuperación predeterminados**  
    - **Usar URL y mensaje de recuperación vacíos**  
    - **Usar un mensaje de recuperación personalizado**  
    - **Usar una dirección URL de recuperación personalizada**  

### <a name="bitlocker-fixed-data-drive-settings"></a>Configuración de BitLocker para unidades de datos fijas  

Esta configuración se aplica específicamente a las unidades de datos fijas.  

- **Acceso de escritura a unidad de datos fija no protegida con BitLocker**  
  **Valor predeterminado**: No configurado  
  CSP de BitLocker: [FixedDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **Bloquear**: conceda acceso de solo lectura a las unidades de datos que no estén protegidas mediante BitLocker.  
  - **No configurado** : de forma predeterminada, el acceso de lectura y escritura a las unidades de datos que no están cifrados.  

- **Recuperación de unidad fija**  
  **Valor predeterminado**: No configurado  
  CSP de BitLocker: [FixedDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **Habilitar**: controle cómo se recuperan las unidades fijas protegidas mediante BitLocker cuando la información de inicio necesaria no está disponible.  
  - **Sin configurar**: deshabilite esta característica.  

  Cuando se establece en *Habilitar*, puede configurar estos valores:  

  - **Agente de recuperación de datos**  
    **Valor predeterminado**: No configurado  
 
    - **Bloquear**: impida el uso del agente de recuperación de datos con el editor de directivas de unidades fijas protegidas mediante BitLocker. 
    - **Sin configurar**: habilita el uso de agentes de recuperación de datos con las unidades fijas protegidas por BitLocker.  

  - **Creación de contraseña de recuperación por el usuario**  
    **Valor predeterminado**: permitir contraseña de recuperación de 48 dígitos  

    seleccione las opciones de los usuarios para generar una contraseña de recuperación de 48 dígitos (permitido, exigido o no permitido).  
    - **Permitir contraseña de recuperación de 48 dígitos**  
    - **No permitir contraseña de recuperación de 48 dígitos**  
    - **Requerir contraseña de recuperación de 48 dígitos**  

  - **Creación de clave de recuperación por el usuario**  
    **Valor predeterminado**: permitir clave de recuperación de 256 bits

    seleccione las opciones de los usuarios para generar una clave de recuperación de 256 bits (permitido, exigido o no permitido).
    - **Permitir clave de recuperación de 256 bits**  
    - **No permitir clave de recuperación de 256 bits**  
    - **Requerir clave de recuperación de 256 bits**  

  - **Opciones de recuperación en el asistente para configuración de BitLocker**  
    **Valor predeterminado**: No configurado  

    - **Bloquear**: los usuarios no pueden ver ni cambiar las opciones de recuperación. Cuando se establece en 
    - **Sin configurar**: los usuarios pueden ver y modificar las opciones de recuperación cuando activen BitLocker.
 
  - **Guardar información de recuperación de BitLocker en Azure Active Directory**  
    **Valor predeterminado**: No configurado  

    - **Habilitar**: almacene la información de recuperación de BitLocker en Azure Active Directory (Azure AD).  
    - **No configurado** : la información de recuperación de BitLocker no se almacena en AAD.

  - **Información de recuperación de BitLocker almacenada en Azure Active Directory**  
    **Valor predeterminado**: Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves  

    configure qué partes de la información de recuperación de BitLocker se almacenan en Azure AD. Elija de entre las siguientes opciones:  
    - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**  
    - **Realizar copia de seguridad solo de contraseñas de recuperación**  

  - **Rotación de contraseñas de recuperación controlada por el cliente**  
    **Valor predeterminado**: rotación de claves habilitada para dispositivos unidos a Azure ad  
    CSP de BitLocker: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Esta configuración inicia una rotación de contraseñas de recuperación controlada por el cliente después de la recuperación de una unidad del sistema operativo (mediante BOOTMGR o WinRE).  

    - No configurado  
    - Rotación de claves deshabilitada  
    - Rotación de claves habilitada para el Azure AD desices  
    - Rotación de claves habilitada para dispositivos Azure AD e híbridos Unidos  

  - **Almacenar información de recuperación en Azure Active Directory antes de habilitar BitLocker**  
    **Valor predeterminado**: No configurado  
 
    Impedir que los usuarios habiliten BitLocker a menos que el equipo realice correctamente una copia de seguridad de la información de recuperación de BitLocker en Azure Active Directory.  

    - **Requerir**: impida que los usuarios activen BitLocker hasta que la información de recuperación de BitLocker se almacene correctamente en Azure AD.  
    - **Sin configurar**: los usuarios pueden activar BitLocker, incluso aunque la información de recuperación no esté almacenada correctamente en Azure AD.  

### <a name="bitlocker-removable-data-drive-settings"></a>Configuración de BitLocker para unidades de datos extraíbles  

Esta configuración se aplica específicamente a las unidades de datos extraíbles.  

- **Acceso de escritura a discos de datos extraíbles no protegidos con BitLocker**  
  **Valor predeterminado**: No configurado  
  CSP de BitLocker: [RemovableDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **Bloquear**: conceda acceso de solo lectura a las unidades de datos que no estén protegidas mediante BitLocker.  
  - **No configurado** : de forma predeterminada, el acceso de lectura y escritura a las unidades de datos que no están cifrados.  

  Cuando se establece en *Habilitar*, puede configurar estos valores:  

  - **Acceso de escritura a dispositivos configurados en otra organización**  
    **Valor predeterminado**: No configurado  

    - **Bloquear**: impida el acceso de escritura a los dispositivos configurados en otra organización.  
    - **No configurado** : denegar acceso de escritura.  
 
## <a name="microsoft-defender-exploit-guard"></a>Protección contra vulnerabilidades de seguridad de Microsoft defender  

Use la [protección contra vulnerabilidades](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) para administrar y reducir la superficie expuesta a ataques de las aplicaciones que usan los empleados.  

### <a name="attack-surface-reduction"></a>Reducción de la superficie expuesta a ataques  

Las reglas de reducción de la superficie expuesta a ataques ayudan a evitar comportamientos que el malware usa a menudo para infectar equipos con código malintencionado.  

#### <a name="attack-surface-reduction-rules"></a>Reglas de reducción de la superficie expuesta a ataques  

- **Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows**  
  **Valor predeterminado**: No configurado  
  Regla: [Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows (lsass.exe)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe)

  Ayudar a evitar las acciones y aplicaciones usadas normalmente por malware que busca vulnerabilidades de seguridad para infectar equipos.  

  - **No configurado**.  
  - **Habilitar**: marque el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows (lsass.exe).  
  - **Solo auditoría**  

- **Creación de procesos desde Adobe Reader (beta)**  
  **Valor predeterminado**: No configurado  
  Regla: [impedir que Adobe Reader cree procesos secundarios](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)  

  - **No configurado**.  
  - **Habilitar** : bloquee los procesos secundarios creados desde Adobe Reader.  
  - **Solo auditoría**  

#### <a name="rules-to-prevent-office-macro-threats"></a>Reglas para evitar amenazas de macros de Office  

Impedir que las aplicaciones de Office realicen las siguientes acciones:  

- **Inserción de aplicaciones de Office en otros procesos (sin excepciones)**  
  **Valor predeterminado**: No configurado  
  Regla: [Impedir que las aplicaciones de Office inserten código en otros procesos](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes)  

  - **No configurado**.  
  - **Bloquear** : impide que las aplicaciones de Office inserten en otros procesos.  
  - **Solo auditoría**  

- **Macros o aplicaciones de Office que crean contenido ejecutable**  
  **Valor predeterminado**: No configurado  
  Regla: [Impedir que las aplicaciones de Office creen contenido ejecutable](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content)  

  - **No configurado**.  
  - **Bloquear** : bloquear las aplicaciones de Office y las macros para crear contenido ejecutable.  
  - **Solo auditoría**  

- **Aplicaciones de Office que inician procesos secundarios**  
  **Valor predeterminado**: No configurado  
  Regla: [Impedir que todas las aplicaciones de Office creen procesos secundarios](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)  

  - **No configurado**.  
  - **Bloquear** : impide que las aplicaciones de Office inicien procesos secundarios.  
  - **Solo auditoría**  
  
- **Importación de Win32 desde código de macros de Office**  
  **Valor predeterminado**: No configurado  
  Regla: [Impedir las llamadas a la API Win32 desde las macros de Office](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros)  

  - **No configurado**.  
  - Importaciones de Win32 de bloque **bloqueado** desde el código de la macro en Office.  
  - **Solo auditoría**  
  
- **Creación de procesos desde productos de comunicación de Office**  
  **Valor predeterminado**: No configurado  
  Regla: [bloquear la aplicación de comunicación de Office para crear procesos secundarios](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)  

  - **No configurado**.  
  - **Habilitar** : bloquee la creación de procesos secundarios desde aplicaciones de comunicaciones de Office.  
  - **Solo auditoría**  

#### <a name="rules-to-prevent-script-threats"></a>Reglas para evitar amenazas de scripts  

Bloquee los siguientes elementos para evitar las amenazas de script:  

- **Código de js/vbs/ps/macro ofuscado**  
  **Valor predeterminado**: No configurado  
  Regla: [Bloquear la ejecución de scripts potencialmente alterados](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts)    

  - **No configurado**.  
  - **Bloquear:** bloquee cualquier código de JS/VBS/PS/macro ofuscado.  
  - **Solo auditoría**  

- **js/vbs que ejecuta carga útil descargada de Internet (sin excepciones)**  
  **Valor predeterminado**: No configurado  
  Regla: [Impedir que JavaScript o VBScript inicien el contenido ejecutable descargado](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content)  

  - **No configurado**.  
  - **Block-Block** JS/vbs de ejecutar carga descargada de Internet.  
  - **Solo auditoría**  

- **Creación del proceso desde comandos PSExec y WMI**  
  **Valor predeterminado**: No configurado  
  Regla: [Bloquear creaciones del proceso que se originan desde comandos PSExec y WMI](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)  

  - **No configurado**.  
  - **Bloquear**: bloquee las creaciones del proceso que se originan desde comandos PSExec y WMI.  
  
  - **Solo auditoría**  

- **Procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB**  
  **Valor predeterminado**: No configurado  
  Regla: [Bloquear los procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb)    

  - **No configurado**.  
  - **Bloquear**: bloquee los procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB.  
  - **Solo auditoría**  
  
- **Archivos ejecutables que no cumplen unos criterios de uso habitual, edad o lista de confianza**  
  **Valor predeterminado**: No configurado  
  Regla: [Bloquear la ejecución de los archivos ejecutables a menos que cumplan unos criterios de uso habitual, edad o lista de confianza](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)    

  - **No configurado**.  
  - **Bloquear**: bloquee la ejecución de los archivos ejecutables a menos que cumplan unos criterios de uso habitual, edad o lista de confianza.  
  - **Solo auditoría**  

#### <a name="rules-to-prevent-email-threats"></a>Reglas para evitar amenazas de correo electrónico  

Bloquee los siguientes elementos para evitar las amenazas de correo electrónico:  

- **Activación de contenido ejecutable (exe, dll, ps, js, vbs, etc.) eliminada del correo electrónico (correo electrónico web/cliente de correo electrónico) (sin excepciones)**  
  **Valor predeterminado**: No configurado  
  Regla: [Bloquear contenido ejecutable del cliente de correo electrónico y el correo electrónico basado en web](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail)  

  - **No configurado**.  
  - **Bloquear**: impida la ejecución del contenido ejecutable (exe, dll, ps, js, vbs, etc.) que se quitó del correo electrónico (correo electrónico web/cliente de correo electrónico).  
  - **Solo auditoría**  

#### <a name="rules-to-protect-against-ransomware"></a>Reglas para protegerse del ransomware  

- **Protección de ransomware avanzada**  
  Valor predeterminado: Sin configurar  
  Regla: [Usar la protección avanzada frente a ransomware](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware)  

  - **No configurado**.  
  - **Habilitar**: Usar protección ransomware intensa.  
  - **Solo auditoría**  

#### <a name="attack-surface-reduction-exceptions"></a>Excepciones de reducción de la superficie expuesta a ataques

- **Archivos y carpetas que se excluirán de las reglas de reducción de la superficie expuesta a ataques**  
  CSP de defender: [AttackSurfaceReductionOnlyExclusions](https://go.microsoft.com/fwlink/?linkid=872981)  

  - **Importe** un archivo. csv que contenga los archivos y las carpetas que se van a excluir de las reglas de reducción de la superficie expuesta a ataques.  
  - **Agregue** manualmente archivos o carpetas locales.  

> [!IMPORTANT]  
> Para permitir la correcta instalación y ejecución de aplicaciones Win32 de LOB, la configuración de antimalware debe excluir los directorios siguientes del análisis:  
> **En máquinas cliente X64**:  
> *C:\Archivos de programa (x86)\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  
>  
> **En máquinas cliente X86**:  
> *C:\Archivos de programa\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  

### <a name="controlled-folder-access"></a>Acceso controlado a carpetas  

Ayude a [proteger los datos importantes](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) de las amenazas y las aplicaciones malintencionadas, como ransomware.  

- **Protección de carpetas**  
  **Valor predeterminado**: No configurado  
  CSP de defender: [EnableControlledFolderAccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  Proteger los archivos y carpetas frente a cambios no autorizados de aplicaciones hostiles.  

  - **No configurado**.  
  - **Habilitar**  
  - **Solo auditoría**  
  - **Solo impedir la modificación del disco**  
  - **Auditoría de la modificación del disco**  

  Al seleccionar una configuración distinta de *no configurada*, puede configurar:  
  - **Lista de aplicaciones que tienen acceso a las carpetas protegidas**  
    CSP de defender: [ControlledFolderAccessAllowedApplications](https://go.microsoft.com/fwlink/?linkid=872616)  

    - **Importe** un archivo. csv que contenga una lista de aplicaciones.  
    - **Agregar** aplicaciones a esta lista manualmente.  

  - **Lista de carpetas adicionales que deben protegerse**  
    CSP de defender: [ControlledFolderAccessProtectedFolders](https://go.microsoft.com/fwlink/?linkid=872617)  

    - **Importe** un archivo. csv que contenga una lista de carpetas.  
    - **Agregue** carpetas a esta lista manualmente.  

### <a name="network-filtering"></a>Filtrado de red  

Bloquee las conexiones salientes desde cualquier aplicación a direcciones IP o dominios con una reputación baja. El filtrado de red es compatible con el modo de auditoría y de bloque.  

- **Protección de red**  
  **Valor predeterminado**: No configurado  
  CSP de defender: [EnableNetworkProtection](https://go.microsoft.com/fwlink/?linkid=872618)  

  La intención de esta configuración es proteger a los usuarios finales de las aplicaciones con acceso a estafas de suplantación de identidad (phishing), sitios de hospedaje de vulnerabilidades y contenido malintencionado en Internet. También evita que los exploradores de terceros se conecten a sitios peligrosos.  

  - **Sin configurar**: deshabilite esta característica. No se impide que los usuarios y las aplicaciones se conecten a dominios peligrosos. Los administradores no pueden ver esta actividad en el Centro de seguridad de Microsoft Defender.  
  - **Habilitar** : activar la protección de red y evitar que los usuarios y las aplicaciones se conecten a dominios peligrosos. Los administradores pueden ver esta actividad en el Centro de seguridad de Microsoft Defender.  
  - **Solo auditoría**:-los usuarios y las aplicaciones no están bloqueados para conectarse a dominios peligrosos. Los administradores pueden ver esta actividad en el Centro de seguridad de Microsoft Defender.  

### <a name="exploit-protection"></a>Protección contra vulnerabilidades  

- **Cargar XML**  
  **Valor predeterminado**: *Sin configurar*  

  Para usar la protección contra vulnerabilidades de seguridad para [proteger los dispositivos frente a vulnerabilidades](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), cree un archivo XML que incluya la configuración de mitigación del sistema y de la aplicación que desee. Existen dos métodos para crear el archivo XML:  

  - *PowerShell*: use uno o varios de los cmdlets de PowerShell *Get-ProcessMitigation*, *Set-ProcessMitigation* y *ConvertTo-ProcessMitigationPolicy*. Los cmdlets configuran los valores de mitigación y exportan una representación XML de ellos.  

  - *IU del Centro de seguridad de Microsoft Defender*: en el Centro de seguridad de Microsoft Defender, haga clic en Control de aplicaciones y navegador y, a continuación, desplácese hasta la parte inferior de la pantalla resultante para buscar Protección contra vulnerabilidades. Primero, use las pestañas Configuración del sistema y Configuración del programa para establecer la configuración de mitigación. Después, busque el vínculo Exportar configuración en la parte inferior de la pantalla para exportar una representación XML de esta.  

- **Edición de usuarios de la interfaz de protección contra vulnerabilidades**  
  **Valor predeterminado**: No configurado  
  CSP ExploitGuard: [ExploitProtectionSettings](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **Bloquear** : carga de un archivo XML que le permite configurar la memoria, el flujo de control y las restricciones de la Directiva. La configuración del archivo XML puede usarse para proteger una aplicación frente a las vulnerabilidades.  
  - **No configurado** : no se usa ninguna configuración personalizada.  

## <a name="microsoft-defender-application-control"></a>Control de aplicaciones de Microsoft Defender  

Elija las aplicaciones adicionales que se deben auditar o que pueden ser de confianza para que las ejecute el control de aplicaciones de Microsoft defender. Se confía automáticamente en la ejecución de los componentes de Windows y de todas las aplicaciones de la Tienda Windows.  


- **Directivas de integridad de código de control de aplicación**  
  **Valor predeterminado**: No configurado  
   CSP: [CSP de AppLocker](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **Aplicar** : elija las directivas de integridad de código de control de la aplicación para los dispositivos de los usuarios.  
  
    Una vez habilitado en un dispositivo, el control de aplicaciones solo puede deshabilitarse si se cambia el modo de *Aplicar* a *Solo auditoría*. El cambio de modo de *Aplicar* a *No configurado* da lugar a que el control de aplicaciones siga aplicándose en los dispositivos asignados.  

  - **No configurado** : el control de aplicaciones no se agrega a los dispositivos. Sin embargo, la configuración que se agregó anteriormente sigue aplicándose a los dispositivos asignados. 
 
  - **Solo auditoría** : las aplicaciones no están bloqueadas. Todos los eventos se registran en los registros del cliente local.  

## <a name="microsoft-defender-credential-guard"></a>Protección de credenciales de Microsoft defender  

Credential Guard de Microsoft Defender protege frente a los ataques de robo de credenciales. Aísla secretos para que solo el software del sistema con privilegios pueda acceder a ellos.  

- **Credential Guard**  
  **Valor predeterminado**: Deshabilitar  
  [CSP DeviceGuard](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **Deshabilitar**: desactive Credential Guard de manera remota, si se ha activado anteriormente con la opción **Habilitar sin bloqueo UEFI**.  

  - **Habilitar con bloqueo UEFI**: Credential Guard no puede deshabilitarse de forma remota mediante una clave de Registro o la directiva de grupo.  

    > [!NOTE]
    > Si usa esta configuración y, posteriormente, quiere deshabilitar Credential Guard, debe establecer la directiva de grupo en **Deshabilitado**. Además, borre físicamente la información de configuración de UEFI de cada equipo. Mientras se conserve la configuración de UEFI, Credential Guard estará habilitado.  

  - **Habilitar sin bloqueo UEFI**: permite que se deshabilite Credential Guard de manera remota mediante la directiva de grupo. Los dispositivos que usan esta opción deben ejecutar Windows 10 versión 1511 o posterior.  

  Al *habilitar* Credential Guard, también se habilitan las siguientes características necesarias:  
  
  - **Seguridad basada en virtualización** (VBS)  
    se activa en el próximo reinicio. La seguridad basada en la virtualización usa el hipervisor de Windows para proporcionar compatibilidad con los servicios de seguridad.  
  - **Arranque seguro con acceso directo a memoria**  
    activa las protecciones de VBS con arranque seguro y acceso directo a memoria (DMA). Las protecciones de DMA requieren compatibilidad con el hardware y solo se habilitan en dispositivos configurados correctamente.  

## <a name="microsoft-defender-security-center"></a>Centro de seguridad de Microsoft Defender  

El Centro de seguridad de Microsoft Defender funciona como una aplicación o proceso independiente de cada una de las características individuales. Las notificaciones se muestran a través del Centro de actividades. Actúa como recopilador o lugar único para ver el estado y configurar algunas opciones para cada una de las características. Obtenga más información en los documentos de [Microsoft defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) .  

### <a name="microsoft-defender-security-center-app-and-notifications"></a>Aplicación y notificaciones del Centro de seguridad de Microsoft Defender  

Bloquear el acceso del usuario final a las diversas áreas de la aplicación Centro de seguridad de Microsoft Defender. Si se oculta una sección, también se bloquean las notificaciones relacionadas.  

- **Protección contra amenazas y virus**  
  **Valor predeterminado**: No configurado  
  CSP WindowsDefenderSecurityCenter: [DisableVirusUI](https://go.microsoft.com/fwlink/?linkid=873662)  

  Configure si los usuarios finales pueden ver el área protección contra virus y amenazas en el Security Center de Microsoft defender. Al ocultar esta sección, también se bloquearán todas las notificaciones relacionadas con la protección contra virus y amenazas.  

  - **No configurado**.  
  - **Ocultar**  

- **Protección de ransomware**  
  **Valor predeterminado**: No configurado  
  CSP WindowsDefenderSecurityCenter: [HideRansomwareDataRecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  Configure si los usuarios finales pueden ver el área de protección de ransomware en el Security Center de Microsoft defender. Al ocultar esta sección, también se bloquearán todas las notificaciones relacionadas con la protección de ransomware.  

  - **No configurado**.  
  - **Ocultar**  

- **Protección de cuenta**  
  **Valor predeterminado**: No configurado  
  CSP WindowsDefenderSecurityCenter: [DisableAccountProtectionUI](https://go.microsoft.com/fwlink/?linkid=873666)  

  Configure si los usuarios finales pueden ver el área de protección de cuentas en el Security Center de Microsoft defender. Al ocultar esta sección, también se bloquearán todas las notificaciones relacionadas con la protección de cuentas.  

  - **No configurado**.  
  - **Ocultar**  

- **Firewall y protección de red**  
  **Valor predeterminado**: No configurado  
  CSP WindowsDefenderSecurityCenter: [DisableNetworkUI](https://go.microsoft.com/fwlink/?linkid=873668)  

  Configure si los usuarios finales pueden ver el firewall y el área de protección de red en Microsoft defender Security Center. Al ocultar esta sección, también se bloquearán todas las notificaciones relacionadas con el firewall y la protección de la red.  

  - **No configurado**.  
  - **Ocultar**  

- **Control de aplicaciones y explorador**  
  **Valor predeterminado**: No configurado  
  CSP WindowsDefenderSecurityCenter: [DisableAppBrowserUI](https://go.microsoft.com/fwlink/?linkid=873669)  

  Configure si los usuarios finales pueden ver el área de control de la aplicación y el explorador en Microsoft defender Security Center. Al ocultar esta sección, también se bloquearán todas las notificaciones relacionadas con el control de aplicaciones y exploradores.  

  - **No configurado**.  
  - **Ocultar**  

- **Protección de hardware**  
  **Valor predeterminado**: No configurado  
  CSP WindowsDefenderSecurityCenter: [DisableDeviceSecurityUI](https://go.microsoft.com/fwlink/?linkid=873670)  

  Configure si los usuarios finales pueden ver el área de protección de hardware en el Security Center de Microsoft defender. Al ocultar esta sección, también se bloquearán todas las notificaciones relacionadas con la protección de hardware.  

  - **No configurado**.  
  - **Ocultar**  

- **Mantenimiento y estado del dispositivo**  
  **Valor predeterminado**: No configurado  
  CSP WindowsDefenderSecurityCenter: [DisableHealthUI](https://go.microsoft.com/fwlink/?linkid=873671)  

  Configure si los usuarios finales pueden ver el área de estado y el rendimiento del dispositivo en el centro de seguridad de Microsoft defender. Al ocultar esta sección, también se bloquearán todas las notificaciones relacionadas con el rendimiento y el estado de los dispositivos.  
  
  - **No configurado**.  
  - **Ocultar**  

- **Opciones de familia**  
  **Valor predeterminado**: No configurado  
  CSP WindowsDefenderSecurityCenter: [DisableFamilyUI](https://go.microsoft.com/fwlink/?linkid=873673)  

  Configure si los usuarios finales pueden ver el área de opciones de la familia en Microsoft defender Security Center. Al ocultar esta sección, también se bloquearán todas las notificaciones relacionadas con las opciones de la familia.  
  
  - **No configurado**.  
  - **Ocultar**  

- **Notificaciones de las áreas que se muestran de la aplicación**  
  **Valor predeterminado**: No configurado  
  CSP WindowsDefenderSecurityCenter: [DisableNotifications](https://go.microsoft.com/fwlink/?linkid=873675)  

  seleccione las notificaciones que se mostrarán a los usuarios finales. Las notificaciones que no son críticas incluyen resúmenes de la actividad del Antivirus de Microsoft Defender, así como notificaciones cuando se completan los exámenes. Todas las otras notificaciones se consideran críticas.  

  - **No configurado**.  
  - **Bloquear notificaciones no críticas**  
  - **Bloquear todas las notificaciones**  

- **Icono de Security Center de Windows en la bandeja del sistema**  
  **Valor predeterminado**: No configurado  

  Configurar la presentación del control del área de notificación. El usuario debe cerrar sesión e iniciar sesión o reiniciar el equipo para que esta configuración surta efecto.  
  
  - **No configurado**.  
  - **Ocultar**  

- **Botón Borrar TPM**  
  **Valor predeterminado**: No configurado  

  Configurar la visualización del botón Borrar TPM.  
  
  - **No configurado**.  
  - **Deshabilitar**  

- **ADVERTENCIA de actualización de firmware de TPM**  
  **Valor predeterminado**: No configurado  
  
  Configure la visualización del firmware del TPM de la actualización cuando se detecte un firmware vulnerable.  

  - **No configurado**.  
  - **Ocultar**  

- **Protección contra alteraciones**  
  **Valor predeterminado**: No configurado

  Active o desactive la protección contra alteraciones en los dispositivos. Para usar la protección contra manipulaciones, debe [integrar protección contra amenazas avanzada de Microsoft defender con Intune](advanced-threat-protection.md)y tener [Enterprise Mobility + Security licencias de E5](../fundamentals/licenses.md).  
  - **No configurado** : no se realiza ningún cambio en la configuración del dispositivo.
  - **Habilitado** : la protección contra manipulaciones está activada y las restricciones se aplican en los dispositivos.
  - **Deshabilitado** : la protección contra manipulaciones está desactivada y no se aplican restricciones.

### <a name="it-contact-information"></a>Información de contacto de TI  

Proporcione la información de contacto de TI que aparecerá en la aplicación Centro de seguridad de Microsoft Defender y en las notificaciones de la aplicación.  

Puede elegir **Mostrar en la aplicación y en las notificaciones**, **Mostrar solo en la aplicación**, **Mostrar solo en las notificaciones** o **No mostrar**. Escriba el **nombre de la organización de TI** y al menos una de las siguientes opciones de contacto:  


- **Información de contacto de TI**  
  **Valor predeterminado**: no mostrar  
  CSP WindowsDefenderSecurityCenter: [EnableCustomizedToasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  Configure dónde se mostrará la información de contacto de ti a los usuarios finales.  
  
  - **Mostrar en la aplicación y en las notificaciones**  
  - **Mostrar solo en la aplicación**  
  - **Mostrar solo en notificaciones**  
  - **No mostrar**  

  Cuando se configura para mostrar, puede configurar las siguientes opciones:  

  - **Nombre de la organización de TI**  
    **Valor predeterminado**: *Sin configurar*  
    CSP WindowsDefenderSecurityCenter: [CompanyName](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **Número de teléfono o usuario de Skype del departamento de TI**  
    **Valor predeterminado**: *Sin configurar*  
    CSP WindowsDefenderSecurityCenter: [teléfono](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **Dirección de correo electrónico del departamento de TI**  
    **Valor predeterminado**: *Sin configurar*  
    CSP WindowsDefenderSecurityCenter: [correo electrónico](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **Dirección URL del sitio web de soporte técnico del departamento de TI**  
    **Valor predeterminado**: *Sin configurar*  
    CSP WindowsDefenderSecurityCenter: [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>Opciones de seguridad de dispositivos locales  

Use estas opciones para configurar la seguridad local en dispositivos Windows 10.  

### <a name="accounts"></a>Cuentas  

- **Agregar nuevas cuentas de Microsoft**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **Bloquear**: impida que los usuarios puedan agregar nuevas cuentas de Microsoft al dispositivo.  
  - **No configurado** : los usuarios pueden usar cuentas de Microsoft en el dispositivo.  

- **Inicio de sesión remoto sin contraseña**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **Bloquear**: permita que solo las cuentas locales con contraseñas en blanco puedan iniciar sesión con el teclado del dispositivo.  
   - **Sin configurar**: permita que las cuentas locales con contraseñas en blanco inicien sesión desde ubicaciones distintas al dispositivo físico.  

#### <a name="admin"></a>Administración  

- **Cuenta de administrador local**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **Bloquear** Impedir el uso de una cuenta de administrador local.  
  - **No configurado**.  

- **Cambiar nombre de la cuenta de administrador**  
  **Valor predeterminado**: *Sin configurar*  
  CSP LocalPoliciesSecurityOptions: [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  Defina otro nombre de cuenta para asociarlo al identificador de seguridad (SID) de la cuenta "Administrador".  

 #### <a name="guest"></a>Invitado  

- **Cuenta de invitado**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [LocalPoliciesSecurityOptions](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **Bloquear** : impide el uso de una cuenta de invitado.  
  - **No configurado**.  

- **Cambiar nombre de cuenta de invitado**  
  **Valor predeterminado**: *Sin configurar*  
  CSP LocalPoliciesSecurityOptions: [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  Defina un nombre de cuenta distinto para asociarlo al identificador de seguridad (SID) de la cuenta "Invitado".  

### <a name="devices"></a>Dispositivos  

- **Desacoplar dispositivo sin iniciar sesión**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **Bloquear**: los usuarios pueden presionar el botón de expulsión física de un dispositivo portátil acoplado para desacoplar el dispositivo de forma segura.  
  - **Sin configurar** : un usuario debe iniciar sesión en el dispositivo y recibir permiso para desacoplar el dispositivo.  

- **Instalar controladores de impresora para impresoras compartidas**  
  **Valor predeterminado**: Sin configurar  
  CSP LocalPoliciesSecurityOptions: [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **Habilitado**: cualquier usuario puede instalar un controlador de impresora como parte de la conexión a una impresora compartida.  
  - **Sin configurar**: solo los administradores pueden instalar un controlador de impresora como parte de la conexión a una impresora compartida.  

- **Restringir el acceso al CD-ROM a un usuario activo local**  
  **Valor predeterminado**: Sin configurar  
  CSP: [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **Habilitado**: solo el usuario que haya iniciado la sesión de forma interactiva puede usar los medios de CD-ROM. Si esta directiva está habilitada y nadie ha iniciado sesión, entonces se accede al CD-ROM a través de la red.  
  - **No configurado** : cualquiera tiene acceso al CD-ROM.  

- **Formatear y expulsar medios extraíbles**  
  **Valor predeterminado**: administradores  
  CSP: [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  defina quién tiene permiso para formatear y expulsar medios extraíbles NTFS:  
  - **No configurado**.  
  - **Administradores**  
  - **Administrators and Power Users** (Administradores y usuarios avanzados)  
  - **Administrators and Interactive Users** (Administradores y usuarios interactivos)  

### <a name="interactive-logon"></a>Inicio de sesión interactivo  

- **Minutos de inactividad de la pantalla de bloqueo hasta que se activa el protector de pantalla**  
  **Valor predeterminado**: *Sin configurar*  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  Escriba el número máximo de minutos de inactividad en la pantalla de inicio de sesión interactiva del escritorio hasta que se active el protector de pantalla. (**0** - **99 999**)  

- **Requerir CTRL+ALT+SUPR para iniciar sesión**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **Habilitar**: no es necesario que los usuarios presionen CTRL + ALT + SUPR para iniciar la sesión.  
  - **Sin configurar**: exija que los usuarios presionen CTRL + ALT + SUPR antes de iniciar sesión en Windows.  

- **Comportamiento de extracción de tarjeta inteligente**  
  **Valor predeterminado**: Bloquear la estación de trabajo   
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  determina lo que sucede cuando la tarjeta inteligente de un usuario que haya iniciado sesión se extrae del lector de tarjetas inteligentes. Las opciones son:  

  - **Bloquear estación de trabajo**: la estación de trabajo se bloquea cuando se quita la tarjeta inteligente. Esta opción permite a los usuarios abandonar el área, llevarse consigo su tarjeta inteligente y seguir manteniendo una sesión protegida.  
  - **Ninguna acción**  
  - **Forzar cierre de sesión**: el usuario se desconecta automáticamente cuando se quita la tarjeta inteligente.  
  - **Desconectar si es una sesión de Servicios de Escritorio remoto**: al quitar la tarjeta inteligente se desconecta la sesión sin cerrar la sesión del usuario. Esta opción permite al usuario insertar la tarjeta inteligente y reanudar la sesión más tarde o en otro equipo equipado con lector de tarjeta inteligente, sin necesidad de volver a iniciar la sesión. Si la sesión es local, esta directiva funciona de forma idéntica a Bloquear estación de trabajo.  

#### <a name="display"></a>Pantalla  

- **Información del usuario al bloquearse la pantalla**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  configure la información del usuario que se muestra cuando se bloquea la sesión. Si no se configura, se muestran el nombre de usuario, el dominio y el nombre para mostrar del usuario.  

  - **No configurado**.  
  - **Nombre para mostrar de usuario, dominio y nombre de usuario**  
  - **User display name only** (Solo nombre para mostrar del usuario)  
  - **Do not display user information** (No mostrar información del usuario)  

- **Ocultar el último usuario que inició sesión**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **Habilitar** : oculte el nombre de usuario.  
  - **No configurado** : muestra el último nombre de usuario.  

- **Ocultar el nombre de usuario en el inicio de sesión**
  **valor predeterminado**: no configurado  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **Habilitar** : oculte el nombre de usuario.  
  - **No configurado** : muestra el último nombre de usuario.  

- **Título del mensaje de inicio de sesión**  
  **Valor predeterminado**: *Sin configurar*  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  establece el título del mensaje para los usuarios que inicien sesión.  

- **Texto del mensaje de inicio de sesión**  
  **Valor predeterminado**: *Sin configurar*  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  establece el texto del mensaje para los usuarios que inicien sesión.  
  
### <a name="network-access-and-security"></a>Seguridad y acceso a la red

- **Acceso anónimo a los recursos compartidos y las canalizaciones con nombre**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **Sin configurar**: restrinja el acceso anónimo a la configuración de recursos compartidos y canalizaciones con nombre. Se aplica a la configuración a la que se puede acceder de forma anónima.  
  - **Bloquear** : deshabilite esta Directiva, haciendo que el acceso anónimo esté disponible.  

- **Enumeración anónima de cuentas SAM**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **No configurado** : los usuarios anónimos pueden enumerar cuentas SAM.  
  - **Bloquear**: evite la enumeración anónima de cuentas SAM.  

- **Enumeración anónima de recursos compartidos y cuentas SAM**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **Sin configurar**: los usuarios anónimos pueden enumerar los nombres de los recursos compartidos de red y las cuentas de dominio.  
  - **Bloquear**: evite la enumeración anónima de recursos compartidos y cuentas SAM. 

- **Valor hash de LAN Manager almacenado al cambiar la contraseña**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  Determine si el valor hash de las contraseñas se almacenará la próxima vez que se cambie la contraseña. 
  - **No configurado** : el valor hash no está almacenado  
  - **Block** : el administrador de LAN (LM) almacena el valor hash de la nueva contraseña.  

- **Solicitudes de autenticación PKU2U**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **No configurado**: permite solicitudes PU2U.  
  - **Bloquee** : bloquee las solicitudes de autenticación PKU2U al dispositivo.  

- **Restringir las conexiones RPC remotas a SAM**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **No configurado** : Utilice el descriptor de seguridad predeterminado, que puede permitir a los usuarios y grupos realizar llamadas RPC remotas a Sam.
  - **Permitir: permite** a los usuarios y grupos realizar llamadas RPC remotas al administrador de cuentas de seguridad (SAM), que almacena las cuentas de usuario y las contraseñas. **Permitir** también le permite cambiar la cadena de lenguaje de definición de descriptores de seguridad (SDDL) predeterminada para permitir o denegar explícitamente a los usuarios y grupos que realicen estas llamadas remotas.  

    - **Descriptor de seguridad**  
      **Valor predeterminado**: *Sin configurar*  
    
- **Seguridad de sesión mínima para clientes NTLM basados en SSP**  
  **Valor predeterminado**: ninguno  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  Esta configuración de seguridad permite que un servidor requiera la negociación de cifrado de 128 bits o la seguridad de sesión NTLMv2.  

  - **Ninguno**  
  - **Requerir seguridad de sesión NTLMv2**  
  - **Requerir cifrado de 128 bits**  
  - **Requerir NTLMv2 y cifrado de 128 bits**  
 
- **Seguridad de sesión mínima para servidores NTLM basados en SSP**  
  **Valor predeterminado**: ninguno  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  Esta configuración de seguridad determina qué protocolo de autenticación de desafío o respuesta se usa para los inicios de sesión de red.  

  - **Ninguno**  
  - **Requerir seguridad de sesión NTLMv2**  
  - **Requerir cifrado de 128 bits**  
  - **Requerir NTLMv2 y cifrado de 128 bits**  

- **Nivel de autenticación de LAN Manager**  
  **Valor predeterminado**: LM y NTLM  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM y NTLM**  
  - **LM, NTLM y NTLMv2**  
  - **NTLM**  
  - **NTLMv2**  
  - **NTLMv2 y no LM**  
  - **NTLMv2 y no LM o NTLM**  
  
- **Inicios de sesión de invitados inseguros**  
  **Valor predeterminado**: No configurado  
  CSP LanmanWorkstation: [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  Si habilita esta configuración, el cliente SMB rechazará los inicios de sesión invitados inseguros.  

  - **No configurado**.  
  - **Block** : el cliente SMB rechaza los inicios de sesión invitados no seguros.  

### <a name="recovery-console-and-shutdown"></a>Cierre y consola de recuperación  

- **Borrar archivo de paginación de la memoria virtual al apagar**  
  **Valor predeterminado**: No configurado  
   CSP LocalPoliciesSecurityOptions: [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **Habilitar**: borre el archivo de paginación de la memoria virtual cuando se apague el dispositivo.  
  - **Sin configurar**: no borra la memoria virtual.  

- **Apagar sin inicio de sesión**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **Bloquear**: oculte la opción de apagado en la pantalla de inicio de sesión de Windows. Los usuarios deben iniciar sesión en el dispositivo y, después, apagarlo.  
  - **Sin configurar**: permita que los usuarios apaguen el dispositivo desde la pantalla de inicio de sesión de Windows.  

### <a name="user-account-control"></a>Control de cuentas de usuario  

- **Integridad UIA sin ubicación segura**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - **Bloquear** : las aplicaciones que se encuentran en una ubicación segura en el sistema de archivos solo se ejecutarán con integridad UIAccess.  
  - **Sin configurar**: permite que las aplicaciones se ejecuten con integridad UIAccess, incluso si las aplicaciones no están en una ubicación segura del sistema de archivos.  

- **Virtualizar los errores de escritura de archivo y del Registro a ubicaciones por usuario**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **Habilitado**: las aplicaciones que escriben datos en ubicaciones protegidas devuelven un error.  
  - **Sin configurar**: los errores de escritura de aplicaciones se redireccionan en tiempo de ejecución a ubicaciones de usuario definidas para el sistema de archivos y el Registro.  

- **Elevar solo los archivos ejecutables firmados y validados**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **Habilitado**: exija la validación de la ruta de certificación de PKI de un archivo ejecutable antes de ejecutarlo.  
  - **Sin configurar**: no aplique la validación de la ruta de certificación de PKI antes de que se pueda ejecutar un archivo ejecutable.  

#### <a name="uia-elevation-prompt-behavior"></a>Comportamiento de petición de elevación de UIA  

- **Petición de elevación para los administradores**  
  **Valor predeterminado**: Pedir consentimiento para binarios que no son de Windows  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  Defina el comportamiento de la petición de elevación para los administradores en Modo de aprobación de administrador.  

  - **No configurado**.  
  - **Elevar sin preguntar**  
  - **Prompt for credentials on the secure desktop** (Pedir credenciales en el escritorio seguro)  
  - **Prompt for credentials** (Pedir credenciales)  
  - **Prompt for consent** (Pedir consentimiento)  
  - **Pedir consentimiento para binarios que no son de Windows**  


- **Petición de elevación para usuarios estándar**  
  **Valor predeterminado**: Pedir credenciales  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  Defina el comportamiento de la petición de elevación para los usuarios estándar.  

  - **No configurado**.  
  - **Denegar solicitudes de elevación automáticamente**  
  - **Prompt for credentials on the secure desktop** (Pedir credenciales en el escritorio seguro)  
  - **Prompt for credentials** (Pedir credenciales)  

- **Enrutar peticiones de elevación al escritorio interactivo del usuario**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - **Habilitado** : todas las solicitudes de elevación para ir al escritorio del usuario interactivo en lugar de al escritorio seguro. Se usa cualquier configuración de directiva de comportamiento de petición para administradores y usuarios estándar.  
  - **Sin configurar**: obliga a que todas las solicitudes de elevación vayan al escritorio seguro independientemente de la configuración de la directiva de comportamiento de petición para administradores y usuarios estándar.

- **Petición con privilegios elevados para instalaciones de aplicaciones**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **Habilitado**: los paquetes de instalación de aplicaciones no se detectan ni se pide la elevación.
   - **Sin configurar**: se pide a los usuarios que escriban un nombre de usuario y una contraseña de administrador cuando se detecta que un paquete de instalación de aplicación requiere privilegios elevados.

- **Petición de elevación UIA sin escritorio seguro**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **Habilitar**: permita que las aplicaciones de UIAccess pidan confirmación de elevación de permisos sin usar el escritorio seguro.  
- **No configurado** : los mensajes de elevación usan un escritorio seguro.  

#### <a name="admin-approval-mode"></a>Modo de aprobación de administrador  

- **Modo de aprobación de administrador para la cuenta predefinida de administrador**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **Habilitado**: permita que la cuenta predefinida de administrador use el modo de aprobación de administrador. Cualquier operación que requiera la elevación de privilegios solicita al usuario que apruebe la operación.  
  - **Sin configurar**: ejecuta todas las aplicaciones con privilegios completos de administrador.  

- **Ejecutar todos los administradores en Modo de aprobación de administrador**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - **Habilitado**: habilita el modo de aprobación de administrador.  
  - **Sin configurar**: deshabilite el Modo de aprobación de administrador y todas las configuraciones de directiva de UAC relacionadas.  

### <a name="microsoft-network-client"></a>Cliente de redes de Microsoft  

- **Firmar digitalmente las comunicaciones (si el servidor lo permite)**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  determina si el cliente de SMB negocia la firma de paquetes SMB.  
  - **Bloquear** : el cliente SMB nunca negocia la firma de paquetes SMB.
  - **Sin configurar**: el cliente de redes de Microsoft solicita al servidor que realice la firma de paquetes SMB tras la configuración de la sesión. Si la firma de paquetes está habilitada en el servidor, esta se negocia.  

- **Enviar contraseña sin cifrar a servidores SMB de terceros**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **Bloquear**: el redirector de Bloque de mensajes del servidor (SMB) pueda enviar contraseñas sin cifrar a servidores SMB que no sean de Microsoft no compatibles con el cifrado de contraseñas durante la autenticación.  
  - **No configurado** : bloquear el envío de contraseñas de texto no cifrado. Las contraseñas se cifran.  

- **Firmar digitalmente las comunicaciones (siempre)**  
  **Valor predeterminado**: No configurado  
  CSP LocalPoliciesSecurityOptions: [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **Habilitar**: el servidor de red de Microsoft no se comunicará con un servidor de red de Microsoft a menos que este acepte la firma de paquetes SMB.  
  - **No configurado** : la firma de paquetes SMB se negocia entre el cliente y el servidor.  

### <a name="microsoft-network-server"></a>Servidor de red de Microsoft  
  
- **Firmar digitalmente las comunicaciones (si el cliente lo permite)**  
  **Valor predeterminado**: No configurado  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **Habilitar**: el servidor de red de Microsoft negocia la firma de paquetes SMB a petición del cliente. Es decir, si está habilitada la firma de paquetes en el cliente, esta se negocia.  
  - **No configurado** : el cliente SMB nunca negocia la firma de paquetes SMB.  

- **Firmar digitalmente las comunicaciones (siempre)**  
  **Valor predeterminado**: No configurado  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **Habilitar**: el servidor de red de Microsoft no se comunicará con un cliente de red de Microsoft a menos que este acepte la firma de paquetes SMB.  
  - **No configurado** : la firma de paquetes SMB se negocia entre el cliente y el servidor.  

## <a name="xbox-services"></a>Servicios de Xbox

- **Tarea de guardar juego Xbox**  
  **Valor predeterminado**: No configurado  
  CSP: [TaskScheduler/EnableXboxGameSaveTask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  Esta opción determina si la tarea de guardar juego Xbox está habilitada o deshabilitada.  
  - **Habilitado**
  - **No configurado**.

- **Servicio de administración de accesorios de Xbox**  
  **Valor predeterminado**: manual  
  CSP: [SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875481)  

  Esta configuración determina el tipo de inicio del servicio de administración de accesorios.  
  - **Manual**
  - **Automático**
  - **Deshabilitado**

- **Servicio del administrador de autenticación de Xbox Live**  
  **Valor predeterminado**: manual  
  CSP: [SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  Esta configuración determina el tipo de inicio del servicio Administrador de autenticación activa.  
  - **Manual**
  - **Automático**
  - **Deshabilitado**
 
- **Servicio de guardado de juegos de Xbox Live**  
  **Valor predeterminado**: manual  
  CSP: [SystemServices/ConfigureXboxLiveGameSaveServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875483)  

  Esta configuración determina el tipo de inicio del servicio de guardado de juegos en directo.  
  - **Manual**
  - **Automático**
  - **Deshabilitado**

- **Servicio de red de Xbox Live**  
  **Valor predeterminado**: manual  
  CSP: [SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875484)  

  Esta configuración determina el tipo de inicio del servicio de red.  
  - **Manual**
  - **Automático**
  - **Deshabilitado**

## <a name="user-rights"></a>Derechos de usuario

- **Obtener acceso al administrador de credenciales como un llamador de confianza**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/AccessCredentialManagerAsTrustedCaller](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-accesscredentialmanagerastrustedcaller)

  El administrador de credenciales usa este derecho de usuario durante las operaciones de copia de seguridad y restauración. Las credenciales guardadas de los usuarios podrían verse comprometidas si se concede este privilegio a otras entidades.
  - **No configurado**.
  - **Permitir**

- **Permitir el inicio de sesión local**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/AllowLocalLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-allowlocallogon)

  Este derecho de usuario determina qué usuarios pueden iniciar sesión en el equipo.
  - **No configurado**.
  - **Permitir**

- **Permitir el acceso desde la red**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/AccessFromNetwork](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-accessfromnetwork)

  Este derecho de usuario determina qué usuarios y grupos pueden conectarse al equipo a través de la red.
  - **No configurado**.
  - **Permitir**

- **Actuar como parte del sistema operativo**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/ActAsPartOfTheOperatingSystem](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-actaspartoftheoperatingsystem)

  Actuar como parte del sistema operativo
  - **No configurado**.
  - **Permitir**  

- **Hacer copias de seguridad de archivos y directorios**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/BackupFilesAndDirectories](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-backupfilesanddirectories)

  Este derecho de usuario determina qué usuarios pueden omitir los permisos de archivo, directorio, registro y otros objetos persistentes al realizar copias de seguridad de archivos y directorios.
  - **No configurado**.
  - **Permitir**

- **Cambiar la hora del sistema**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/ChangeSystemTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-changesystemtime)

  Este derecho de usuario determina qué usuarios y grupos pueden cambiar la hora y la fecha en el reloj interno del equipo.
  - **No configurado**.
  - **Permitir**

- **Crear objetos globales**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/CreateGlobalObjects](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createglobalobjects)

  Esta configuración de seguridad determina si los usuarios pueden crear objetos globales que están disponibles para todas las sesiones. Los usuarios que pueden crear objetos globales podrían afectar a los procesos que se ejecutan en las sesiones de otros usuarios, lo que podría provocar un error de la aplicación o daños en los datos.
  - **No configurado**.
  - **Permitir**

- **Crear archivo de paginación**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/CreatePageFile](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createpagefile)

  Este derecho de usuario determina qué usuarios y grupos pueden llamar a una API interna para crear y cambiar el tamaño de un archivo de paginación.
  - **No configurado**.
  - **Permitir**

- **Crear objetos compartidos permanentes**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/CreatePermanentSharedObjects](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createpermanentsharedobjects)

  Este derecho de usuario determina qué cuentas pueden usar los procesos para crear un objeto de directorio mediante el administrador de objetos.
  - **No configurado**.
  - **Permitir**

- **Crear vínculos simbólicos**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/CreateSymbolicLinks](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createsymboliclinks)

  Este derecho de usuario determina si el usuario puede crear un vínculo simbólico desde el equipo en el que ha iniciado sesión.
  - **No configurado**.
  - **Permitir**

- **Crear tokens**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/CreateToken](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createtoken)

  Este derecho de usuario determina qué usuarios o grupos pueden usar los procesos para crear un token que luego se puede usar para obtener acceso a los recursos locales cuando el proceso utiliza una API interna para crear un token de acceso.
  - **No configurado**.
  - **Permitir**

- **Depurar programas**  
  **Valor predeterminado**: No configurado  
    CSP: [UserRights/DebugPrograms](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-debugprograms)

  Este derecho de usuario determina qué usuarios pueden adjuntar un depurador a cualquier proceso o al kernel.
  - **No configurado**.
  - **Permitir**

- **Denegar el acceso desde la red**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/DenyAccessFromNetwork](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denyaccessfromnetwork)

  Este derecho de usuario determina qué usuarios no pueden tener acceso a un equipo a través de la red.
  - **No configurado**.
  - **Permitir**

- **Denegar el inicio de sesión como servicio**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/DenyLocalLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denylocallogon)

  Esta configuración de seguridad determina qué cuentas de servicio no pueden registrar un proceso como servicio.
  - **No configurado**.
  - **Permitir**

- **Denegar inicio de sesión a través de Servicios de Escritorio remoto**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/DenyRemoteDesktopServicesLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denyremotedesktopserviceslogon)

  Este derecho de usuario determina a qué usuarios y grupos se les prohíbe iniciar sesión como Servicios de Escritorio remoto cliente.
  - **No configurado**.
  - **Permitir**

- **Habilitar la delegación**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/EnableDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-enabledelegation)

 Este derecho de usuario determina qué usuarios pueden establecer la configuración de confianza para la delegación en un objeto de usuario o de equipo.
  - **No configurado**.
  - **Permitir**

- **Generar auditorías de seguridad**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/GenerateSecurityAudits](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-generatesecurityaudits)

  Este derecho de usuario determina qué cuentas puede usar un proceso para agregar entradas al registro de seguridad. El registro de seguridad se usa para realizar el seguimiento del acceso al sistema no autorizado.
  - **No configurado**.
  - **Permitir**

- **Suplantar a un cliente**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/ImpersonateClient](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-impersonateclient)

  La asignación de este derecho de usuario a un usuario permite a los programas que se ejecutan en nombre del usuario suplantar a un cliente. Requerir este derecho de usuario para este tipo de suplantación impide que un usuario no autorizado convenza a un cliente para que se conecte a un servicio que ha creado y, a continuación, suplanta a ese cliente, lo que puede elevar los permisos del usuario no autorizado a niveles administrativos o del sistema.
  - **No configurado**.
  - **Permitir**

- **Aumentar prioridad de programación**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/IncreaseSchedulingPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-increaseschedulingpriority)

  Este derecho de usuario determina qué cuentas pueden usar un proceso con acceso de propiedad de escritura a otro proceso para aumentar la prioridad de ejecución asignada al otro proceso.
  - **No configurado**.
  - **Permitir**

- **Cargar y descargar controladores de dispositivo**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/LoadUnloadDeviceDrivers](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-loadunloaddevicedrivers)

  Este derecho de usuario determina qué usuarios pueden cargar y descargar dinámicamente controladores de dispositivo u otro código en el modo kernel.
  - **No configurado**.
  - **Permitir**

- **Bloquear páginas en la memoria**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/LockMemory](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-lockmemory)

  Este derecho de usuario determina qué cuentas pueden utilizar un proceso para mantener los datos en la memoria física, impidiendo que el sistema realice la paginación de los datos en la memoria virtual del disco.
  - **No configurado**.
  - **Permitir**

- **Administrar registro de seguridad y auditoría**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/ManageAuditingAndSecurityLog](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-manageauditingandsecuritylog)

  Este derecho de usuario determina qué usuarios pueden especificar opciones de auditoría de acceso a objetos para recursos individuales, como archivos, objetos de Active Directory y claves del registro.
  - **No configurado**.
  - **Permitir**

- **Realizar tareas de mantenimiento del volumen**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/ManageVolume](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-managevolume)

  Este derecho de usuario determina qué usuarios y grupos pueden ejecutar tareas de mantenimiento en un volumen, como la desfragmentación remota.
  - **No configurado**.
  - **Permitir**

- **Modificar valores de entorno firmware**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/ModifyFirmwareEnvironment](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-modifyfirmwareenvironment)

  Este derecho de usuario determina quién puede modificar los valores de entorno de firmware.
  - **No configurado**.
  - **Permitir**

- **Modificar la etiqueta de un objeto**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/ModifyObjectLabel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-modifyobjectlabel)

  Este derecho de usuario determina qué cuentas de usuario pueden modificar la etiqueta de integridad de los objetos, como los archivos, las claves del registro o los procesos que pertenecen a otros usuarios.
  - **No configurado**.
  - **Permitir**

- **Analizar un solo proceso**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/ProfileSingleProcess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-profilesingleprocess)

  Este derecho de usuario determina qué usuarios pueden usar las herramientas de supervisión de rendimiento para supervisar el rendimiento de los procesos del sistema.
  - **No configurado**.
  - **Permitir**

- **Apagado remoto**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/RemoteShutdown](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-remoteshutdown)

  Este derecho de usuario determina qué usuarios pueden apagar un equipo desde una ubicación remota de la red. El uso incorrecto de este derecho de usuario puede dar lugar a una denegación de servicio.
  - **No configurado**.
  - **Permitir**
  
- **Restaurar archivos y directorios**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/RestoreFilesAndDirectories](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-restorefilesanddirectories)
  
  Este derecho de usuario determina qué usuarios pueden omitir los permisos de archivo, directorio, registro y otros objetos persistentes al restaurar copias de seguridad de archivos y directorios, y determina qué usuarios pueden establecer cualquier entidad de seguridad válida como propietario de un objeto.
  - **No configurado**.
  - **Permitir**
  
- **Tomar posesión de archivos u objetos**  
  **Valor predeterminado**: No configurado  
  CSP: [UserRights/TakeOwnerShip](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-takeownership)

  Este derecho de usuario determina qué usuarios pueden tomar posesión de cualquier objeto protegible en el sistema, como Active Directory objetos, archivos y carpetas, impresoras, claves del registro, procesos y subprocesos.
  - **No configurado**.
  - **Permitir**

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](../configuration/device-profile-assign.md) y [supervise su estado](../configuration/device-profile-monitor.md).  

Configure las opciones de protección de los puntos de conexión en los dispositivos [macOS](endpoint-protection-macos.md).  
