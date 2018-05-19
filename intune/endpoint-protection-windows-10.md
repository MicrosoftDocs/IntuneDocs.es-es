---
title: Agregar protección de punto de conexión a Windows 10 en Microsoft Intune - Azure | Microsoft Docs
description: En los dispositivos Windows 10 puede usar o configurar opciones de protección de punto de conexión para habilitar características de Windows Defender, como Protección de aplicaciones, firewall, SmartScreen, cifrado y BitLocker, Protección contra vulnerabilidades, Control de aplicaciones, Centro de seguridad y seguridad de dispositivos locales en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 069f71d75c0a9c7cec083a929f89a2b39bb4aac5
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Configuración de Endpoint Protection para Windows 10 (y versiones posteriores) en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

El perfil de Endpoint Protection le permite controlar características de seguridad en dispositivos Windows 10, como BitLocker o Windows Defender.

Use la información de este artículo para crear perfiles de Endpoint Protection. Para configurar el Antivirus de Windows Defender, consulte las [restricciones de los dispositivos Windows 10](device-restrictions-windows-10.md#windows-defender-antivirus). 

> [!NOTE]
> Estas configuraciones no se admiten en las ediciones Home y Professional de Windows 10.

## <a name="windows-defender-application-guard"></a>Protección de aplicaciones de Windows Defender

Al utilizar Microsoft Edge, Protección de aplicaciones de Windows Defender protege su entorno de sitios que todavía su organización no ha definido como de confianza. Cuando los usuarios visitan sitios que no figuran en el límite de red aislada, estos se abren en una sesión de exploración virtual en Hyper-V. Los sitios de confianza se definen mediante un límite de red, que puede configurarse en Configuración de dispositivos. 

Protección de aplicaciones solo está disponible para dispositivos de Windows 10 (de 64 bits). Con este perfil se instala un componente de Win32 para activar Protección de aplicaciones.

- **Protección de aplicaciones**: abra los sitios no aprobados en un contenedor de exploración virtualizado de Hyper-V.
- **Comportamiento del Portapapeles**: elija qué acciones de copiar y pegar se permiten entre el equipo local y el explorador virtual de Protección de aplicaciones.
- **Contenido externo en sitios de empresa**: impida la carga del contenido de sitios web no aprobados.
- **Imprimir desde el explorador virtual**: permita que las impresoras PDF, XPS, locales o en red impriman contenido desde el explorador virtual.
- **Recopilar registros**: recopile registros de eventos que se producen dentro de una sesión de exploración de Protección de aplicaciones.
- **Conservar los datos del explorador generados por el usuario**: guarde los datos de usuario (por ejemplo, contraseñas, favoritos y cookies) que se crean durante una sesión de exploración de Protección de aplicaciones virtual.
- **Aceleración gráfica**: cargue más rápido los sitios web con gran cantidad de gráficos al trabajar en la sesión de exploración virtual de Protección de aplicaciones. Los sitios web se cargan más rápidos al habilitar el acceso a una unidad virtual de procesamiento de gráficos.
- **Descargar archivos al sistema de archivos host**: con esta opción los usuarios pueden descargar archivos del explorador virtualizado al sistema operativo host.

## <a name="windows-defender-firewall"></a>Firewall de Windows Defender

### <a name="global-settings"></a>Configuración global

Esta configuración se aplica a todos los tipos de redes.

- **Protocolo de transferencia de archivos**: bloquea FTP con estado.
- **Tiempo de inactividad de la asociación de seguridad antes de la eliminación**: las asociaciones de seguridad se eliminan después de no haber detectado ningún tráfico de red durante *n* segundos.
- **Codificación de clave previamente compartida**: codifica las claves previamente compartidas mediante UTF-8.
- **Exenciones de IPsec**: configure el tráfico específico que debe estar exento de IPsec, incluidos los **códigos de tipo ICMP de IPv6 de descubrimiento de vecinos**, **ICMP**, **los códigos de tipo ICMP de IPv6 de descubrimiento de enrutadores** y el **tráfico de red DHCP de IPv4 e IPv6**.
- **Comprobación de la lista de revocación de certificados**: establezca un valor para la forma en que se aplica la comprobación de la lista de revocación de certificados, incluido **Deshabilitar comprobación CRL**, **Fail CRL verification on revoked certificate only** (Error de comprobación de CRL solo al encontrar un certificado revocado) y **Fail CRL verification on any error encountered** (Error de comprobación de CRL al encontrar cualquier error).
- **Coincidencia pertinente del conjunto de autenticación por módulo de generación de claves**: establece que los módulos de generación de claves omitan todo el conjunto de autenticación si no admiten todos los componentes de este.
- **Puesta de paquetes en cola**: especifique cómo se habilita el escalado de software en el lado de recepción para la recepción cifrada y el reenvío de texto no cifrado para un escenario de puerta de enlace de túnel IPsec. Esta opción garantiza que se conserve el orden de los paquetes.

### <a name="network-settings"></a>Configuración de red

Estas opciones son aplicables a tipos de red específicos, incluidas la **red del dominio (área de trabajo)**, la **red privada (reconocible)** y la **red pública (no reconocible)**.

#### <a name="general-settings"></a>Configuración general

- **Firewall de Windows Defender**: al habilitar esta opción se bloquea el tráfico de red.
- **Modo sigiloso**: se bloquea el firewall para que no funcione en el modo sigiloso. Bloquear el modo sigiloso también le permite bloquear la **exención de paquete protegido por IPsec**.
- **Blindada**: al habilitar esta opción y la configuración del firewall, se bloquea todo el tráfico entrante.
- **Respuestas de unidifusión a multidifusiones**: se bloquean todas las respuestas de unidifusión a multidifusiones. Normalmente, no desea recibir respuestas de unidifusión a mensajes de difusión o multidifusión. Estas respuestas pueden indicar un ataque por denegación de servicio (DOS) o un atacante que intenta buscar un equipo activo conocido.
- **Notificaciones entrantes**: impide que se muestren las notificaciones a los usuarios cuando se impide que una aplicación escuche en un puerto.
- **Acción predeterminada para las conexiones entrantes**: bloquea la acción predeterminada que realiza el firewall sobre las conexiones entrantes.

#### <a name="rule-merging"></a>Combinación de reglas

- **Reglas de Firewall de Windows Defender de aplicación autorizada del almacén local**: se aplican reglas de firewall autorizadas al almacén local para que se reconozcan y se apliquen.
- **Reglas de Firewall de Windows Defender de puerto globales del almacén local**: se aplican reglas de firewall de puerto globales al almacén local para que se reconozcan y se apliquen.
- **Reglas de Firewall de Windows Defender del almacén local**: se aplica reglas de firewall globales al almacén local para que se reconozcan y se apliquen.
- **Reglas IPsec del almacén local**: se aplican reglas de seguridad de conexión del almacén local, con independencia del esquema o de las versiones de dichas reglas.

## <a name="windows-defender-smartscreen-settings"></a>Configuración de SmartScreen de Windows Defender

- **SmartScreen para aplicaciones y archivos**: habilita Windows SmartScreen para la ejecución de archivos y aplicaciones.
- **Ejecución de archivos no comprobados**: evita que los usuarios finales puedan ejecutar archivos que no haya comprobado Windows SmartScreen.

## <a name="windows-encryption"></a>Cifrado de Windows

### <a name="windows-settings"></a>Configuración de Windows

Las dos siguientes opciones se aplican a todas las versiones de Windows 10:

- **Cifrar dispositivos**: si está habilitada, a los usuarios se les pide que habiliten el cifrado de dispositivo. Además, se les pide que confirmen que el cifrado de otro proveedor no se ha habilitado. Si el cifrado de Windows se habilita mientras otro método de cifrado está activo, el dispositivo puede volverse inestable.
- **Encrypt storage card** (Cifrar la tarjeta de almacenamiento): habilite esta opción para cifrar cualquier tarjeta de almacenamiento extraíble que use el dispositivo.


### <a name="bitlocker-base-settings"></a>Configuración base de BitLocker

La configuración base es la configuración de BitLocker universal para todos los tipos de unidades de datos. La configuración de directiva de grupo de BitLocker administra las tareas de cifrado o las opciones de configuración de unidades que el usuario final puede modificar en todos los tipos de unidades de datos.

- **Warning for other disk encryption** (Advertencias para otro cifrado de discos): deshabilita el mensaje de advertencia de otro cifrado de disco en las máquinas de los usuarios finales.
- **Configure encryption methods** (Configurar métodos de cifrado): habilite esta opción para configurar algoritmos de cifrado para el sistema operativo, los datos y las unidades extraíbles.
  - **Cifrado para unidades de sistema operativo**: elija el método de cifrado para las unidades del sistema operativo. Se recomienda que use el algoritmo XTS-AES.
  - **Cifrado para unidades de datos fijas**: elija el método de cifrado para las unidades de datos fijas (integradas). Se recomienda que use el algoritmo XTS-AES.
  - **Encryption for removable data-drives** (Cifrado para unidades de datos extraíbles): elija el método de cifrado para las unidades de datos extraíbles. Si la unidad extraíble se usa con dispositivos que no ejecutan Windows 10, recomendamos que use el algoritmo AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Configuración de BitLocker para unidades de sistema operativo

Esta configuración se aplica específicamente a las unidades de datos de sistema operativo.

- **Additional authentication at startup** (Autenticación adicional al inicio): configure los requisitos de autenticación para el inicio de equipos, incluido el uso del Módulo de plataforma segura (TPM).
  - **BitLocker con un chip de TPM no compatible**
  - **Compatible TPM startup** (Inicio del TPM compatible): elija entre permitir, no permitir o requerir el chip de TPM.
  - **Compatible TPM startup PIN** (NIP de inicio TPM compatible): elija entre permitir, no permitir o requerir el uso de un PIN de inicio con el chip de TPM.
  - **Compatible TPM startup key** (Clave de inicio TPM compatible): elija entre permitir, no permitir o requerir el uso de una clave de inicio con el chip de TPM.
  - **Compatible TPM startup key and PIN** (Clave de inicio y PIN de TPM compatibles): elija entre permitir, no permitir o requerir el uso de una clave de inicio y un PIN con el chip de TPM.
- **Longitud mínima del PIN**: habilite esta opción para configurar una longitud mínima de PIN de inicio con TPM.
  - **Mínimo de caracteres**: escriba el número de caracteres necesarios para el PIN de inicio entre **4**- y **20**.
- **Recuperación de unidades de sistema operativo**: habilite esta opción para controlar cómo se recuperan las unidades de sistema operativo protegidas mediante BitLocker cuando la información de inicio necesaria no está disponible.
  - **Agente de recuperación de datos (basado en certificado)**: habilite esta opción si quiere que los agentes de recuperación de datos puedan usarse con las unidades de sistema operativo protegidas mediante BitLocker.
  - **Creación de contraseña de recuperación por el usuario**: elija si los usuarios pueden, necesitan o no pueden generar una contraseña de recuperación de 48 dígitos.
  - **Creación de clave de recuperación por el usuario**: elija si los usuarios pueden, necesitan o no pueden generar una clave de recuperación de 256 bits.
  - **Opciones de recuperación en el asistente para configuración de BitLocker**: habilite esta opción para evitar que los usuarios vean o cambien las opciones de recuperación cuando activen BitLocker.
  - **Guardar la información de recuperación de BitLocker en AD DS**: permite el almacenamiento de la información de recuperación de BitLocker en Active Directory.
  - **Información de recuperación de BitLocker almacenada en AD DS**: configure qué partes de la información de recuperación de BitLocker se almacenan en Active Directory. Elija de entre las siguientes opciones:
    - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**
    - **Realizar copia de seguridad solo de contraseñas de recuperación**
  - **Almacenar la información de recuperación en AD DS antes de habilitar BitLocker**: habilite esta opción para impedir que los usuarios activen BitLocker a no ser que el dispositivo esté unido a un dominio y la información de recuperación de BitLocker esté almacenada correctamente en Active Directory.
- **URL y mensaje de recuperación previos al arranque**: habilite esta opción para configurar el mensaje y la dirección URL que se muestra en la pantalla de recuperación previa al arranque.
  - **Mensaje de recuperación previo al arranque**: configure cómo se muestra el mensaje de recuperación previo al arranque a los usuarios. Elija de entre las siguientes opciones:
    - **Usar la dirección URL y el mensaje de recuperación predeterminados**
    - **Usar URL y mensaje de recuperación vacíos**
    - **Usar un mensaje de recuperación personalizado**
    - **Usar una dirección URL de recuperación personalizada**

### <a name="bitlocker-fixed-data-drive-settings"></a>Configuración de BitLocker para unidades de datos fijas

- **Acceso de escritura a unidad de datos fija no protegida con BitLocker**: si está habilitada, la protección de BitLocker debe habilitarse en todas las unidades de datos fijas o integradas para poder escribir en ellas.
- **Recuperación de unidades fijas**: habilite esta opción para controlar cómo se recuperan las unidades fijas protegidas mediante BitLocker cuando la información de inicio necesaria no está disponible.
  - **Agente de recuperación de datos**: habilite esta opción si quiere que los agentes de recuperación de datos puedan usarse con las unidades fijas protegidas mediante BitLocker.
  - **Creación de contraseña de recuperación por el usuario**: configure si los usuarios pueden, necesitan o no pueden generar una contraseña de recuperación de 48 dígitos.  
  - **Creación de clave de recuperación por el usuario**: configure si los usuarios pueden, necesitan o no pueden generar una clave de recuperación de 256 bits.
  - **Opciones de recuperación en el asistente para configuración de BitLocker**: habilite esta opción para evitar que los usuarios vean o cambien las opciones de recuperación cuando activen BitLocker.
  - **Guardar la información de recuperación de BitLocker en AD DS**: permite el almacenamiento de la información de recuperación de BitLocker en Active Directory.
  - **Información de recuperación de BitLocker en AD DS**: configure qué partes de la información de recuperación de BitLocker se almacenan en Active Directory. Elija de entre las siguientes opciones:
    - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**
    - **Realizar copia de seguridad solo de contraseñas de recuperación**
  - **Requerir que la información de recuperación se almacene en AD DS antes de habilitar BitLocker**: habilite esta opción para impedir que los usuarios activen BitLocker a no ser que el dispositivo esté unido a un dominio y la información de recuperación de BitLocker se haya almacenado correctamente en Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>Configuración de BitLocker para unidades de datos extraíbles

- **Acceso de escritura a discos de datos extraíbles no protegidos con BitLocker**: especifique si se necesita el cifrado de BitLocker para las unidades de almacenamiento extraíbles.
  - **Acceso de escritura a dispositivos configurados en otra organización**: especifique si se puede escribir en las unidades de datos extraíbles que pertenecen a otra organización.

## <a name="windows-defender-exploit-guard"></a>Protección contra vulnerabilidades de seguridad de Windows Defender

Use la [Protección contra vulnerabilidades de seguridad de Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) para administrar y reducir la superficie expuesta a ataques de las aplicaciones que usan sus empleados.

### <a name="attack-surface-reduction"></a>Reducción de la superficie expuesta a ataques

- **Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows**

Ayudar a [evitar las acciones y aplicaciones](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) usadas normalmente por malware que busca vulnerabilidades de seguridad para infectar equipos.

#### <a name="rules-to-prevent-office-macro-threats"></a>Reglas para evitar amenazas de macros de Office

Impedir que las aplicaciones de Office realicen las siguientes acciones:

- **Inserción de aplicaciones de Office en otros procesos (sin excepciones)**
- **Macros o aplicaciones de Office que crean contenido ejecutable**
- **Aplicaciones de Office que inician procesos secundarios**
- **Importación de Win32 desde código de macros de Office**

#### <a name="rules-to-prevent-script-threats"></a>Reglas para evitar amenazas de scripts

Bloquee los siguientes elementos para evitar las amenazas de script:

- **Código de js/vbs/ps/macro ofuscado**
- **js/vbs que ejecuta carga útil descargada de Internet (sin excepciones)**
- **Creación del proceso desde comandos PSExec y WMI**
- **Procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB**
- **Archivos ejecutables que no cumplen unos criterios de uso habitual, edad o lista de confianza**

#### <a name="rules-to-prevent-email-threats"></a>Reglas para evitar amenazas de correo electrónico

Bloquee los siguientes elementos para evitar las amenazas de correo electrónico:

- **Activación de contenido ejecutable (exe, dll, ps, js, vbs, etc.) eliminada del correo electrónico (correo electrónico web/cliente de correo electrónico) (sin excepciones)**

#### <a name="rules-to-protect-against-ransomware"></a>Reglas para protegerse del ransomware
- **Protección de ransomware avanzada**

> [!TIP]
> En [Reducir las superficies de ataque con Protección contra vulnerabilidades de seguridad de Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) se proporciona más información detallada sobre estas reglas.

#### <a name="attack-surface-reduction-exceptions"></a>Excepciones de reducción de la superficie expuesta a ataques

- **Archivos y carpetas que se excluirán de las reglas de reducción de la superficie expuesta a ataques**: importe o agregue una lista de ubicaciones que se excluirán de las reglas configuradas.

### <a name="controlled-folder-access"></a>Acceso controlado a carpetas

Ayude a proteger los datos importantes de las amenazas y las aplicaciones malintencionadas, como ransomware.

- **Protección de carpetas**: proteja archivos y carpetas de cambios no deseados por parte de aplicaciones malintencionadas. Puede importar una **lista de aplicaciones que tienen acceso a carpetas protegidas** o agregarlas manualmente. También puede agregar una **lista de carpetas adicionales que necesita proteger** mediante una carga o agregarlas manualmente.

### <a name="network-filtering"></a>Filtrado de red

Bloquear las conexiones salientes desde cualquier aplicación a IP y dominios de mala reputación.

### <a name="exploit-protection"></a>Protección contra vulnerabilidades

Impida la **edición por el usuario de la interfaz de Protección contra vulnerabilidades** mediante la carga de un archivo XML que le permite configurar la memoria, el flujo de control y las restricciones de directiva. La configuración del archivo XML puede usarse para proteger una aplicación frente a las vulnerabilidades.

Para habilitar la protección contra vulnerabilidades, cree un archivo XML que represente la configuración de su elección para la mitigación de las aplicaciones y del sistema. Para ello, use uno de estos dos métodos:

 1. PowerShell: use uno o varios de los cmdlets de PowerShell Get-ProcessMitigation, Set-ProcessMitigation y ConvertTo-ProcessMitigationPolicy. Los cmdlets configuran los valores de mitigación y exportan una representación XML de ellos.

 2. IU del Centro de seguridad de Windows Defender: en el Centro de seguridad de Windows Defender, haga clic en Control de aplicaciones y navegador y, a continuación, desplácese hasta la parte inferior de la pantalla resultante para buscar Protección contra vulnerabilidades. Primero, use las pestañas Configuración del sistema y Configuración del programa para establecer la configuración de mitigación. Después, busque el vínculo Exportar configuración en la parte inferior de la pantalla para exportar una representación XML de esta.

## <a name="windows-defender-application-control"></a>Windows Defender Application Control

Use **directivas de integridad del código de control de aplicaciones** para elegir aplicaciones adicionales que deban auditarse o con confianza para ejecutarse mediante Windows Defender Application Control. Se confía automáticamente en la ejecución de los componentes de Windows y de todas las aplicaciones de la Tienda Windows.

Las aplicaciones no se bloquearán al ejecutarse en modo **solo auditoría**. El modo **Solo auditoría** registra todos los eventos en registros locales del cliente.

Una vez habilitado, el control de aplicaciones solo puede deshabilitarse si se cambia el modo de **Aplicar** a **Solo auditoría**. El cambio de modo de **Aplicar** a **No configurado** da lugar a que el control de aplicaciones siga aplicándose en los dispositivos asignados.

## <a name="windows-defender-credential-guard"></a>Credential Guard de Windows Defender
Credential Guard de Windows Defender protege frente a los ataques de robo de credenciales. Aísla secretos para que solo el software del sistema con privilegios pueda acceder a ellos.

La configuración de **Credential Guard** incluye:

- **Deshabilitado**: desactiva Credential Guard de forma remota, si se activó anteriormente con la opción **Enabled without UEFI lock** (Habilitado sin bloqueo de UEFI).
- **Habilitado con el bloqueo UEFI**: garantiza que Credential Guard no puede deshabilitarse de forma remota mediante una clave de Registro o la directiva de grupo.

    > [!NOTE]
    > Si usa esta configuración y, posteriormente, quiere deshabilitar Credential Guard, debe establecer la directiva de grupo en **Deshabilitado**. Además, borre físicamente la información de configuración de UEFI de cada equipo. Mientras se conserve la configuración de UEFI, Credential Guard estará habilitado.

- **Enabled without UEFI lock** (Habilitado sin el bloqueo UEFI): permite que se deshabilite Credential Guard de manera remota mediante la directiva de grupo. Los dispositivos que usan esta opción deben ejecutar Windows 10 versión 1511 o posterior.

Al habilitar Credential Guard, también se habilitan las siguientes características necesarias:

- **Virtualization-based Security** (VBS) (Seguridad basada en la virtualización [VBS]): se activa durante el siguiente reinicio. La seguridad basada en la virtualización usa el hipervisor de Windows para proporcionar compatibilidad con los servicios de seguridad.
- **Secure Boot with Directory Memory Access** (Arranque seguro con acceso a la memoria de directorio): activa VBS con arranque seguro y las protecciones de acceso directo a memoria (DMA). Las protecciones de DMA requieren compatibilidad con el hardware y solo se habilitan en dispositivos configurados correctamente.

## <a name="windows-defender-security-center"></a>Centro de seguridad de Windows Defender

La aplicación Centro de seguridad de Windows Defender funciona como una aplicación o proceso independiente de cada una de las características individuales. Las notificaciones se muestran a través del Centro de actividades. Actúa como recopilador o lugar único para ver el estado y configurar algunas opciones para cada una de las características. Obtenga más información en los documentos de [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Aplicación y notificaciones del Centro de seguridad de Windows Defender

Bloquear el acceso del usuario final a las diversas áreas de la aplicación Centro de seguridad de Windows Defender. Si se oculta una sección, también se bloquearán las notificaciones relacionadas.

- **Protección contra amenazas y virus**
- **Mantenimiento y estado del dispositivo**
- **Firewall y protección de red**
- **Control de aplicaciones y explorador**
- **Opciones de familia**
- **Notificaciones de las áreas que se muestran de la aplicación**: elija qué notificaciones se mostrarán a los usuarios finales. Las notificaciones que no son críticas incluyen resúmenes de la actividad del Antivirus de Windows Defender, así como notificaciones cuando se completan los exámenes. Todas las otras notificaciones se consideran críticas.

#### <a name="it-contact-information"></a>Información de contacto de TI

Proporcione la información de contacto de TI que aparecerá en la aplicación Centro de seguridad de Windows Defender y en las notificaciones de la aplicación. Puede elegir **Mostrar en la aplicación y en las notificaciones**, **Mostrar solo en la aplicación**, **Mostrar solo en las notificaciones** o **No mostrar**. Debe definir el **nombre de la organización de TI** y al menos una de las siguientes opciones de contacto:

- **Número de teléfono o usuario de Skype del departamento de TI**
- **Dirección de correo electrónico del departamento de TI**
- **Dirección URL del sitio web de soporte técnico del departamento de TI**

## <a name="local-device-security-options"></a>Opciones de seguridad de dispositivos locales

Use estas opciones para configurar la seguridad local en dispositivos Windows 10.

### <a name="accounts"></a>Cuentas

- **Agregar nuevas cuentas de Microsoft**: impide que los usuarios agreguen nuevas cuentas de Microsoft a este equipo.
- **Remote log on without password** (Inicio de sesión remoto sin contraseña): permite que las cuentas locales que no están protegidas con contraseña inicien sesión desde ubicaciones que no son el dispositivo físico.

#### <a name="admin"></a>Administración

- **Cuenta de administrador local**: determina si la cuenta de administrador local está habilitada o deshabilitada.
- **Cambiar nombre de la cuenta de administrador**: defina un nombre de cuenta distinto para asociar con el identificador de seguridad (SID) de la cuenta de administrador.

#### <a name="guest"></a>Invitado

- **Cuenta de invitado**: determine si la cuenta de invitado está habilitada o deshabilitada.
- **Cambiar nombre de cuenta de invitado**: defina un nombre de cuenta distinto para asociar con el identificador de seguridad (SID) de la cuenta de invitado.

### <a name="devices"></a>Dispositivos

- **Desacoplar dispositivo sin iniciar sesión**: impide que un equipo portátil se desacople sin tener que iniciar sesión.
- **Install printer drivers for shared printers** (Instalar controladores de impresora para impresoras compartidas): restringe la instalación de controladores de impresora como parte de la conexión a una impresora compartida a solo los administradores.
- **Restrict CD-ROM access to local active user** (Restringir el acceso al CD-RO al usuario local activo): al habilitar esta opción, solo el usuario que ha iniciado sesión de forma interactiva puede acceder a la unidad de CD-ROM.
- **Format and eject removable media** (Formatear y expulsar los medios extraíbles): defina a quién se le permite formatear y expulsar medios extraíbles NTFS:
  - **No configurado**.
  - **Administrators and Power Users** (Administradores y usuarios avanzados)
  - **Administrators and Interactive Users** (Administradores y usuarios interactivos)

### <a name="interactive-logon"></a>Inicio de sesión interactivo

- **Minutes of lock screen inactivity until screen saver activates** (Minutos de inactividad de pantalla de bloqueo hasta que se activa el protector de pantalla): defina los minutos máximos de inactividad en la pantalla de inicio de sesión del escritorio interactivo hasta que se activa el protector de pantalla.
- **Require CTRL+ALT+DEL to log on** (Requerir CTRL+ALT+SUPR para iniciar sesión): exige que se presione CTRL+ALT+SUPR para que un usuario pueda iniciar sesión.
- **Comportamiento de extracción de tarjeta inteligente**: determina lo que sucede cuando la tarjeta inteligente de un usuario conectado se extrae del lector de tarjetas inteligentes.
En [LocalPoliciesSecurity options](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) (Opciones de LocalPoliciesSecurity) se proporciona más información.

#### <a name="display"></a>Pantalla

- **User information on lock screen** (Información del usuario en la pantalla de bloqueo): configure la información del usuario que se muestra cuando la sesión se bloquea. Si no se configura, se muestran el nombre de usuario, el dominio y el nombre para mostrar del usuario.
  - **User display name only** (Solo nombre para mostrar del usuario)
  - **Do not display user information** (No mostrar información del usuario)
  - **No configurado**: nombre de usuario, dominio y nombre para mostrar del usuario.
- **Ocultar el último usuario que inició sesión**: no se muestra el nombre de usuario de la última persona que inició sesión en este dispositivo.
- **Hide username at sign-in** (Ocultar nombre de usuario al inicio de la sesión): no se muestra el nombre de usuario de la persona que inicia sesión en este dispositivo después de escribir las credenciales y antes de que se muestre el escritorio del dispositivo.
- **Logon message title** (Título del mensaje de inicio de sesión): defina el título del mensaje para los usuarios que intentan iniciar sesión.
- **Logon message text** (Texto del mensaje de inicio de sesión): defina el texto del mensaje para los usuarios que intentan iniciar sesión.

### <a name="network-access-and-security"></a>Seguridad y acceso a la red

- **Anonymous access to Named Pipes and Shares** (Acceso anónimo a las canalizaciones con nombre y los recursos compartidos): restringe el acceso anónimo a la configuración de canalizaciones con nombre y recursos compartidos. Se aplica a la configuración a la que se puede acceder de forma anónima.
- **Anonymous enumeration of SAM accounts** (Enumeración anónima de cuentas de SAM): permite que los usuarios anónimos enumeren las cuentas de SAM. Windows permite a los usuarios anónimos enumerar los nombres de las cuentas de dominio y de los recursos compartidos de red.
- **Anonymous enumeration of SAM accounts and shares** (Enumeración anónima de cuentas de SAM y recursos compartidos): es posible bloquear la enumeración anónima de cuentas de SAM y recursos compartidos. Windows permite a los usuarios anónimos enumerar los nombres de las cuentas de dominio y de los recursos compartidos de red.
- **LAN Manager hash value stored on password change** (Valor de hash de LAN Manager almacenado en el cambio de contraseña): en el siguiente cambio de contraseña, elija si se almacena el valor de hash de LAN Manager (LM) de la nueva contraseña. De forma predeterminada, no se almacena.
- **Solicitudes de autenticación PKU2U**: impide que las solicitudes de autenticación PKU2U a este dispositivo usen identidades en línea.
- **Restrict remote RPC connections to SAM** (Restringir conexiones RPC remotas a SAM): edite la cadena predeterminada de lenguaje de definición de descriptor de seguridad para permitir o impedir que usuarios y grupos realicen llamadas remotas a SAM.
- **Descriptor de seguridad**

### <a name="recovery-console-and-shutdown"></a>Cierre y consola de recuperación

- **Clear virtual memory pagefile when shutting down** (Borrar el archivo de paginación de memoria virtual al cerrar): borra el archivo de paginación de memoria virtual cuando se apaga el dispositivo.
- **Apagar sin inicio de sesión**: bloquea la opción para apagar el equipo desde la pantalla de inicio de sesión de Windows. En este caso, los usuarios deben poder iniciar sesión correctamente en el equipo y antes de que puedan realizar un apagado del sistema.

### <a name="user-account-control"></a>Control de cuentas de usuario

- **Integridad UIA sin ubicación segura**: permite que las aplicaciones de ubicaciones poco seguras del sistema de archivos se ejecuten con el nivel de integridad de UIAccess.
- **Virtualize file and registry write failures to per-user locations** (Virtualizar errores de escritura de archivos y del registro en ubicaciones por usuario): determina si los errores de escritura de las aplicaciones se redirigen a ubicaciones definidas del sistema de archivos y del Registro. O bien, provocan que la aplicación genere un error.
- **Only elevate executable files that are signed and validated** (Elevar solo los archivos ejecutables firmados y validados): aplica la validación de la ruta de acceso de certificación de PKI a un archivo ejecutable determinado antes de que se le permita ejecutarse.

#### <a name="uia-elevation-prompt-behavior-settings"></a>Configuración del comportamiento de petición de elevación de UIA

- **Elevation prompt for admins** (Petición de elevación para administradores): define el comportamiento de la petición de elevación para los administradores en Modo de aprobación de administrador:
  - **Elevar sin preguntar**
  - **Prompt for credentials on the secure desktop** (Pedir credenciales en el escritorio seguro)
  - **Prompt for consent on the secure desktop** (Pedir consentimiento en el escritorio seguro)
  - **Prompt for credentials** (Pedir credenciales)
  - **Prompt for consent** (Pedir consentimiento)
  - **No configurado**: se pide consentimiento para binarios que no son de Windows.
- **Elevation prompt for standard users** (Petición de elevación para usuarios estándar): define el comportamiento de la petición de elevación para usuarios estándar:
  - **Denegar solicitudes de elevación automáticamente**
  - **Prompt for credentials on the secure desktop** (Pedir credenciales en el escritorio seguro)
  - **No configurado**: se piden credenciales.
- **Route elevation prompts to user’s interactive desktop** (Enruta las peticiones de elevación al escritorio interactivo del usuario): permite que todas las peticiones de elevación vayan al escritorio interactivo del usuario en lugar de al escritorio seguro. Se usa la configuración de directiva de comportamiento de petición para administradores y usuarios estándar.
- **Elevated prompt for app installations** (Petición de elevación para instalaciones de aplicaciones): las instalaciones de aplicaciones que requieren privilegios elevados solicitarán credenciales de administrador.
- **Petición de elevación UIA sin escritorio seguro**: permite que las aplicaciones de UIAccess soliciten elevación sin usar el escritorio seguro.

#### <a name="admin-approval-mode-settings"></a>Configuración del Modo de aprobación de administrador

- **Admin approval Mode for Built-in Administrator** (Modo de aprobación de administrador para la cuenta predefinida de administrador): define si la cuenta predefinida de administrador usa el Modo de aprobación de administrador o ejecuta todas las aplicaciones con privilegios de administrador completos.
- **Run all admins in Admin Approval Mode** (Ejecutar todas las cuentas de administrador en Modo de aprobación de administrador): define si están habilitados el Modo de aprobación de administrador y toda la configuración de directiva de UAC.

### <a name="microsoft-network-client"></a>Cliente de redes de Microsoft

- **Firmar digitalmente las comunicaciones (si el servidor lo permite)**: determina si el cliente SMB intenta negociar la firma de paquetes SMB. Cuando está habilitada (valor predeterminado), el cliente de redes de Microsoft solicita al servidor que realice la firma de paquetes SMB tras la configuración de la sesión. Si se ha habilitado la firma de paquetes en el servidor, esta se negocia. Si esta directiva está deshabilitada, el cliente SMB no negocia nunca la firma de paquetes SMB.
- **Send unencrypted password to third-party SMB servers** (Enviar contraseña no cifrada a servidores de SMB de terceros): cuando está habilitada, se permite al redirector de Bloque de mensajes de servidor (SMB) enviar contraseñas sin cifrar a servidores SMB que no son de Microsoft que no admiten el cifrado de contraseñas durante la autenticación.

### <a name="microsoft-network-server"></a>Servidor de red de Microsoft

- **Firmar digitalmente las comunicaciones (si el cliente lo permite)**: determina si el servidor SMB negocia la firma de paquetes SMB con los clientes que lo solicitan. Cuando está habilitada, el servidor de red de Microsoft negocia la firma de paquetes SMB a petición del cliente. Es decir, si está habilitada la firma de paquetes en el cliente, esta se negocia. Cuando está deshabilitada (valor predeterminado), el cliente SMB nunca negocia la firma de paquetes SMB.
- **Firmar digitalmente las comunicaciones (siempre)**: determina si el componente de servidor SMB requiere la firma de paquetes. Cuando está habilitada, el servidor de red de Microsoft no se comunicará con un cliente de red de Microsoft a menos que este acepte realizar la firma de paquetes SMB. Cuando está deshabilitada (valor predeterminado), la firma de paquetes SMB se negocia entre el cliente y el servidor.

## <a name="next-steps"></a>Pasos siguientes

Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).
