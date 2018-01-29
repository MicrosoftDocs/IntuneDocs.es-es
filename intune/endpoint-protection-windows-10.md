---
title: "Configuración de Intune Endpoint Protection para Windows 10"
titlesuffix: Azure portal
description: "Obtenga información sobre la configuración de Intune que puede usar para controlar los valores de Endpoint Protection como BitLocker en dispositivos Windows 10."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 01/16/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8393699a06def8f01c9f70561bb1894bb7cba04e
ms.sourcegitcommit: 967a7c23b863123398c40b812e2eb02c921a0afe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2018
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Configuración de Endpoint Protection para Windows 10 y versiones posteriores en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

El perfil de Endpoint Protection le permite controlar características de seguridad en dispositivos Windows 10, como BitLocker o Windows Defender.

Use la información de este tema para obtener información sobre cómo crear perfiles de Endpoint Protection.

> [!Note]
> Estas configuraciones no se admiten en las ediciones Home y Professional de Windows 10.

## <a name="create-an-endpoint-protection-profile"></a>Crear un perfil de Endpoint Protection

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Crear perfil**.
4. En la hoja **Crear perfil**, escriba un **Nombre** y una **Descripción** para el perfil de características del dispositivo.
5. En la lista desplegable **Plataform** (Plataforma), elija **Windows 10 y versiones posteriores**.
6. En la lista desplegable de **Tipos de perfil**, pulse **Endpoint Protection**.
7. Configure las opciones que desee. Use los detalles de este tema para ayudarle a entender lo que realiza cada opción de configuración. Cuando termine, elija **Aceptar**.
8. Vuelva a la hoja **Crear perfil** y seleccione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="windows-defender-application-guard"></a>Protección de aplicaciones de Windows Defender

Protección de aplicaciones solo está disponible para dispositivos de Windows 10 (de 64 bits). Con este perfil se instalará un componente de Win32 para activar Protección de aplicaciones.

- **Protección de aplicaciones**: abrir los sitios no aprobados en un contenedor de exploración virtualizado de Hyper-V.
- **Comportamiento del Portapapeles**: elegir qué acciones de copiar y pegar se permiten entre el equipo local y el explorador virtual de Protección de aplicaciones.
- **Contenido externo en sitios de empresa**: impedir la carga del contenido de sitios web no aprobados.
- **Imprimir desde el explorador virtual**: permitir que las impresoras PDF, XPS, locales o en red impriman contenido desde el explorador virtual.
- **Recopilar registros**: recopilar registros de eventos que se producen dentro de una sesión de exploración de Protección de aplicaciones.
- **Conservar datos del explorador generados por el usuario**: permitir que se guarden los datos de usuario (por ejemplo, contraseñas, favoritos y cookies) que se crean durante una sesión de exploración de Protección de aplicaciones virtual.


## <a name="windows-defender-firewall"></a>Firewall de Windows Defender

### <a name="global-settings"></a>Configuración global

Esta configuración se aplica a todos los tipos de redes.

- **Protocolo de transferencia de archivos**: bloquear FTP con estado.
- **Tiempo de inactividad de asociación de seguridad antes de la eliminación**: las asociaciones de seguridad se eliminan después de no haber detectado ningún tráfico de red durante *n* segundos.
- **Codificación de clave previamente compartida**: codificar las claves previamente compartidas mediante UTF-8.
- **Exenciones de IPsec**: configurar el tráfico específico que debe estar exento de realizar IPsec, incluidos los **códigos de tipo ICMP de IPv6 de descubrimiento de vecinos**, **ICMP**, **los códigos de tipo ICMP de IPv6 de descubrimiento de enrutadores** y **tráfico de redes DHCP de IPv4 e IPv6**.
- **Comprobación de la lista de revocación de certificados**: establecer un valor para la forma en que se aplica la comprobación de la lista de revocación de certificados, incluido **Deshabilitar comprobación CRL**, **Error de comprobación de CRL solo al encontrar un certificado revocado** y **Error de comprobación de CRL al encontrar cualquier error**.
- **Coincidencia pertinente del conjunto de autenticación por módulo de generación de claves**: establecer que los módulos de generación de claves ignoren todo el conjunto de autenticación si no admiten todos los componentes del mismo.
- **Puesta de paquetes en cola**: especificar cómo se habilita el escalado para el software en el lado de recepción para la recepción cifrada y el reenvío no cifrado para un escenario de puerta de enlace de túnel de IPsec. Esto garantiza que se conserva el orden de los paquetes.

### <a name="network-settings"></a>Configuración de red

Estas opciones son aplicables a tipos de red específicos, incluidas la **red del dominio (área de trabajo)**, la **red privada (reconocible)** y la **red pública (no reconocible)**.

#### <a name="general-settings"></a>Configuración general

- **Firewall de Windows Defender**: al habilitar esta opción se bloquea el tráfico de la red.
- **Modo sigiloso**: bloquear el firewall para que no funcione en el modo sigiloso. Bloquearlo también le permite impedir la **exención de paquete protegido por IPsec**.
- **Blindada**: al habilitar esta opción y la configuración del firewall se bloqueará todo el tráfico entrante.
- **Respuestas de unidifusión a multidifusiones**: bloquear todas las respuestas de unidifusión a multidifusiones. Por lo general, no le interesa recibir respuestas de unidifusión a mensajes de multidifusión o difusión, puesto que tales respuestas pueden indicar un ataque por denegación de servicio o que un atacante intenta sondear un equipo en vivo conocido.
- **Notificaciones entrantes**: impedir que se muestren las notificaciones a los usuarios cuando se impide que una aplicación escuche en un puerto.
- **Acción predeterminada para las conexiones entrantes**: bloquear la acción predeterminada que realiza el firewall sobre las conexiones entrantes.

#### <a name="rule-merging"></a>Combinación de reglas

- **Reglas de Firewall de Windows Defender de aplicación autorizada del almacén local**: aplicar reglas de firewall autorizadas al almacén local para que se reconozcan y se apliquen.
- **Reglas de Firewall de Windows Defender de puerto globales del almacén local**: aplicar reglas de firewall de puerto globales al almacén local para que se reconozcan y se apliquen.
- **Reglas de Firewall de Windows Defender del almacén local**: aplicar reglas de firewall globales al almacén local para que se reconozcan y se apliquen.
- **Reglas IPsec del almacén local**: aplicar reglas de seguridad de conexión del almacén local, con independencia del esquema o de las versiones de dichas reglas.

## <a name="windows-defender-smartscreen-settings"></a>Configuración de SmartScreen de Windows Defender

- **SmartScreen para aplicaciones y archivos**: habilite Windows SmartScreen para la ejecución de archivos y aplicaciones.
- **Ejecución de archivos no comprobados**: evite que los usuarios finales puedan ejecutar archivos que no haya comprobado Windows SmartScreen.

## <a name="windows-encryption"></a>Cifrado de Windows

### <a name="windows-settings"></a>Configuración de Windows

Esta configuración se aplica a todas las versiones de Windows 10.

- **Cifrar dispositivos**: si está habilitado, a los usuarios se les pide que habiliten el cifrado de dispositivo. Además, se les pide que confirmen que el cifrado de otro proveedor no se ha habilitado. Si el cifrado de Windows se habilita mientras otro método de cifrado está activo, el dispositivo puede volverse inestable.
- **Cifrar la tarjeta de almacenamiento**: habilite esta opción para cifrar cualquier tarjeta de almacenamiento extraíble que use el dispositivo.


### <a name="bitlocker-base-settings"></a>Configuración base de BitLocker

La configuración base es la configuración de BitLocker universal para todos los tipos de unidades de datos. La configuración de directiva de grupo de BitLocker administra las tareas de cifrado o las opciones de configuración de unidades que el usuario final puede modificar en todos los tipos de unidades de datos.

- **Advertencias para otro cifrado de discos**: deshabilita el mensaje de advertencia de otro cifrado de disco en las máquinas de los usuarios finales.
- **Configurar métodos de cifrado**: habilite esta opción para configurar algoritmos de cifrado para el sistema operativo, los datos y las unidades extraíbles.
    - **Cifrado para unidades de sistema operativo**: elija el método de cifrado para las unidades del sistema operativo. Se recomienda que use el algoritmo XTS-AES.
    - **Cifrado para unidades de datos fijas**: elija el método de cifrado para las unidades de datos fijas (integradas). Se recomienda que use el algoritmo XTS-AES.
    - **Cifrado para unidades de datos extraíbles**: elija el método de cifrado para las unidades de datos extraíbles. Si la unidad extraíble se usa con dispositivos que no ejecutan Windows 10, recomendamos que use el algoritmo AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Configuración de BitLocker para unidades de sistema operativo

Esta configuración se aplica específicamente a las unidades de datos de sistema operativo.

- **Autenticación adicional al inicio**: configurar los requisitos de autenticación para el inicio de equipos, incluido el uso del Módulo de plataforma segura (TPM).
    - **BitLocker con un chip de TPM no compatible**
    - **Inicio de TPM compatible**: configurar si el chip TPM se permite, no se permite o se necesita.
    - **PIN de inicio de TPM compatible**: configurar si usar un PIN de inicio con el chip TPM se permite, no se permite o se necesita.
    - **Clave de inicio de TPM compatible**: configurar si usar una clave de inicio con el chip TPM se permite, no se permite o se necesita.
    - **Clave y PIN de inicio de TPM compatible**: configurar si usar una clave de inicio y PIN con el chip TPM se permite, no se permite o se necesita.
- **Longitud mínima del PIN**: habilite esta opción para configurar una longitud mínima del PIN de inicio con TPM.
    - **Mínimo de caracteres**: escriba el número de caracteres necesarios para el PIN de inicio de **4**-**20**.
- **Recuperación de unidades de sistema operativo**: habilite esta opción para controlar cómo se recuperan las unidades de sistema operativo protegidas mediante BitLocker cuando la información de inicio necesaria no está disponible.
    - **Agente de recuperación de datos basada en el certificado**: habilite esta opción si quiere que los agentes de recuperación de datos puedan usarse con las unidades de sistema operativo protegidas mediante BitLocker.
    - **Creación de contraseña de recuperación por el usuario**: configure si los usuarios pueden, necesitan o no pueden generar una contraseña de recuperación de 48 dígitos.
    - **Creación de clave de recuperación por el usuario**: configure si los usuarios pueden, necesitan o no pueden generar una clave de recuperación de 256 bits.
    - **Opciones de recuperación en el asistente para configuración de BitLocker**: habilite esta opción para evitar que los usuarios vean o cambien las opciones de recuperación cuando activen BitLocker.
    - **Guardar la información de recuperación de BitLocker en AD DS**: habilita el almacenamiento de la información de recuperación de BitLocker en Active Directory.
    - **Información de recuperación de BitLocker almacenada en AD DS**: configure qué partes de la información de recuperación de BitLocker se almacenan en Active Directory. Elija de entre las siguientes opciones:
        - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**
        - **Realizar copia de seguridad solo de contraseñas de recuperación**
    - **Almacenar la información de recuperación en AD DS antes de habilitar BitLocker**: habilite esta opción para impedir que los usuarios activen BitLocker a no ser que el dispositivo esté unido a dominio y la información de recuperación de BitLocker esté almacenada correctamente en Active Directory.
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
    - **Guardar la información de recuperación de BitLocker en AD DS**: habilita el almacenamiento de la información de recuperación de BitLocker en Active Directory.
    - **Información de recuperación de BitLocker en AD DS**: configure qué partes de la información de recuperación de BitLocker se almacenan en Active Directory. Elija de entre las siguientes opciones:
        - **Realizar copia de seguridad de contraseñas de recuperación y paquetes de claves**
        - **Realizar copia de seguridad solo de contraseñas de recuperación**
    - **Requerir que la información de recuperación se almacene en AD DS antes de habilitar BitLocker**: habilite esta opción para impedir que los usuarios activen BitLocker a no ser que el dispositivo esté unido a dominio y la información de recuperación de BitLocker se haya almacenado correctamente en Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>Configuración de BitLocker para unidades de datos extraíbles

- **Acceso de escritura a discos de datos extraíbles no protegidos con BitLocker**: especifique si se necesita el cifrado de BitLocker para las unidades de almacenamiento extraíbles.
  - **Acceso de escritura a dispositivos configurados en otra organización**: especifique si se puede escribir en las unidades de datos extraíbles que pertenecen a otra organización.

## <a name="windows-defender-exploit-guard"></a>Protección contra vulnerabilidades de seguridad de Windows Defender

Use la [Protección contra vulnerabilidades de seguridad de Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) para administrar y reducir la superficie expuesta a ataques de las aplicaciones que usan sus empleados.

### <a name="attack-surface-reduction"></a>Reducción de la superficie expuesta a ataques

Ayudar a [evitar las acciones y aplicaciones](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) usadas normalmente por malware que busca vulnerabilidades de seguridad para infectar equipos.

#### <a name="rules-to-prevent-office-macro-threats"></a>Reglas para evitar amenazas de macros de Office

Impedir que las aplicaciones de Office realicen las siguientes acciones:

- **Inserción de aplicaciones de Office en otros procesos (sin excepciones)**
- **Macros o aplicaciones de Office que crean contenido ejecutable**
- **Aplicaciones de Office que inician procesos secundarios**
- **Importación de Win32 desde código de macros de Office**

#### <a name="rules-to-prevent-script-threats"></a>Reglas para evitar amenazas de scripts

Bloquee estos elementos para ayudar a evitar las amenazas de script:

- **Código de js/vbs/ps/macro ofuscado**
- **js/vbs que ejecuta carga útil descargada de Internet (sin excepciones)**

#### <a name="rules-to-prevent-email-threats"></a>Reglas para evitar amenazas de correo electrónico

Bloquee esta opción para ayudar a evitar las amenazas de correo electrónico:

- **Activación de contenido ejecutable (exe, dll, ps, js, vbs, etc.) eliminada del correo electrónico (correo electrónico web/cliente de correo electrónico) (sin excepciones)**

#### <a name="attack-surface-reduction-exceptions"></a>Excepciones de reducción de la superficie expuesta a ataques

- **Archivos y carpetas que se excluirán de las reglas de reducción de la superficie expuesta a ataques**: importar o agregar una lista de ubicaciones que se excluirán de las reglas configuradas.

### <a name="controlled-folder-access"></a>Acceso controlado a carpetas

Ayude a proteger los datos importantes de las amenazas y las aplicaciones malintencionadas, como ransomware.

- **Protección de carpetas**: proteger los archivos y carpetas de cambios no deseados por parte de aplicaciones malintencionadas. Puede importar una **lista de aplicaciones que tienen acceso a carpetas protegidas** o agregarlas manualmente. También puede agregar una **lista de carpetas adicionales que necesita proteger** mediante una carga o agregarlas manualmente.

### <a name="network-filtering"></a>Filtrado de red

Bloquear las conexiones salientes desde cualquier aplicación a IP y dominios de mala reputación.

### <a name="exploit-protection"></a>Protección contra vulnerabilidades

Impida la **edición del usuario de la interfaz de Protección contra vulnerabilidades** mediante la carga de un archivo XML que le permite configurar la memoria, el flujo de control y las restricciones de directiva que se pueden usar para bloquear una aplicación frente a las vulnerabilidades.

Para habilitar la protección contra vulnerabilidades, cree un archivo XML que represente la configuración de su elección para la mitigación de las aplicaciones y del sistema. Para ello, use uno de estos dos métodos:

 1. PowerShell: use uno o varios de los cmdlets Get-ProcessMitigation, Set-ProcessMitigation y ConvertTo-ProcessMitigationPolicy de PowerShell para establecer la configuración de mitigación y exportar una representación XML de esta.

 2. IU del Centro de seguridad de Windows Defender: en el Centro de seguridad de Windows Defender, haga clic en Control de aplicaciones y navegador y, a continuación, desplácese hasta la parte inferior de la pantalla resultante para buscar Protección contra vulnerabilidades. Primero, use las pestañas Configuración del sistema y Configuración del programa para establecer la configuración de mitigación. Después, busque el vínculo Exportar configuración en la parte inferior de la pantalla para exportar una representación XML de esta.

## <a name="windows-defender-application-control"></a>Windows Defender Application Control

Use **	directivas de integridad del código de control de aplicaciones** para elegir aplicaciones adicionales que deban auditarse o con confianza para ejecutarse mediante Windows Defender Application Control. Se confía automáticamente en la ejecución de los componentes de Windows y de todas las aplicaciones de la Tienda Windows.

Las aplicaciones no se bloquearán al ejecutarse en modo "solo auditoría". El modo de "solo auditoría" registra todos los eventos en registros del cliente local.

## <a name="windows-defender-security-center"></a>Centro de seguridad de Windows Defender

La aplicación Centro de seguridad de Windows Defender funciona como un proceso o aplicación independiente de cada una de las características individuales y mostrará notificaciones a través del centro de actividades. Actúa como recopilador o lugar único para ver el estado y configurar algunas opciones para cada una de las características. Obtenga más información en los documentos de [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

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

## <a name="next-steps"></a>Pasos siguientes

Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).
