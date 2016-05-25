---
# required metadata

title: Directivas de Firewall para equipos Windows | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ayudar a proteger los equipos de Windows mediante directivas del Firewall de Windows en Microsoft Intune
Microsoft Intune puede ayudarle a proteger los equipos Windows administrados de varias maneras. Una de ellas es el uso de directivas que le permiten configurar el Firewall de Windows en los equipos.

Si aún no ha instalado el cliente de equipos Windows de Intune en sus PC, consulte [Instalar el cliente de equipos Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md)..

Use la información de las siguientes secciones como ayuda para configurar, implementar y supervisar las directivas del Firewall de Windows en equipos Windows.

## Uso de directivas de Intune para administrar el Firewall de Windows
La directiva de Firewall de Windows le permite crear e implementar la configuración que controla el Firewall de Windows en los equipos administrados. No se puede administrar excepciones personalizadas para Firewall de Windows y esta configuración no afecta a ningún firewall que no sea de Microsoft.

> [!NOTE]
> Si la directiva de Microsoft Intune y la directiva de grupo están configuradas para administrar la misma opción en el equipo, la opción de la directiva de grupo anula la opción de la directiva de Microsoft Intune. Para obtener información sobre cómo evitar conflictos entre las directivas de Intune y la directiva de grupo, consulte [Resolver conflictos de directivas de Microsoft Intune y GPO](resolve-gpo-and-microsoft-intune-policy-conflicts.md)..
>
> Si quiere implementar la configuración de Firewall de Windows en equipos que ejecutan Windows Vista, primero debe instalar la [revisión KB971800](http://support2.microsoft.com/kb/971800) en estos equipos.

> [!IMPORTANT]
> Para administrar Firewall de Windows mediante Intune, debe asegurarse de que los dos servicios siguientes están habilitados en los equipos que va a administrar:
>
> -   Firewall de Windows
> -   Agente de directivas IPsec

## Para configurar una directiva de Firewall de Windows

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Directiva** &gt; **Agregar directiva**..

2.  Configurar e implementar una directiva de **Configuración de Firewall de Windows** . Puede usar la configuración recomendada o personalizar la configuración. Si necesita más información sobre cómo crear e implementar directivas, consulte [Tareas comunes de administración de PC Windows con el cliente de equipo de Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)..

    En la sección siguiente se muestran los valores que puede configurar en la directiva y también los valores predeterminados que se utilizarán si no se personaliza la directiva.

Tras implementar la directiva de Firewall de Windows, puede ver su estado en la página **Todas las directivas** del área de trabajo **Directiva**.

## Configuración de directiva para Firewall de Windows

### Activar Firewall de Windows

Esta configuración de directiva habilita el Firewall de Windows en equipos administrados que estén conectados a un dominio (por ejemplo, en el área de trabajo), a una red privada (de confianza; por ejemplo, una red doméstica) o a una red pública que no sea de confianza (por ejemplo, en una cafetería). El valor predeterminado de cada uno de estos valores es **Sí**, que es el valor más seguro. 



### Bloquear todas las conexiones entrantes, incluidas las de la lista de programas permitidos.

Con esta configuración de directiva, el Firewall de Windows bloquea el tráfico de red entrante cuando el equipo administrado está conectado a un dominio (por ejemplo, en el área de trabajo), a una red privada (de confianza; por ejemplo, una red doméstica) o a una red pública que no sea de confianza (por ejemplo, en una cafetería). El valor predeterminado de cada uno de estos valores es **Sí**, que es el valor más seguro. 

> [!IMPORTANT]
> Si su entorno incluye equipos administrados que ejecutan Windows Vista sin ningún Service Pack instalado, debe instalar la actualización asociada con el [artículo 971800](http://go.microsoft.com/fwlink/?LinkId=188405) en Microsoft Knowledge Base, o bien deshabilitar la configuración de directiva **Bloquear todas las conexiones entrantes** en las directivas implementadas en dichos equipos.

### Notificar al usuario cuando Firewall de Windows bloquee un nuevo programa

Esta configuración de directiva define si el Firewall de Windows envía una notificación al usuario del equipo al bloquear el tráfico de red entrante cuando el equipo administrado está conectado a un dominio (por ejemplo, en el área de trabajo), a una red privada (de confianza; por ejemplo, una red doméstica) o a una red pública que no sea de confianza (por ejemplo, en una cafetería). El valor predeterminado para cada uno de estos valores es **Sí**..


### Excepciones predefinidas

Después de configurar los valores básicos indicados anteriormente, puede configurar las excepciones que permiten cierto tráfico de red a través del firewall, independientemente de los valores configurados anteriormente. De forma predeterminada, no se configura ninguna de estas opciones.

|Nombre de la configuración|Detalles|
|------------------|--------------------|
|**BranchCache: recuperación de contenido**<br>(Windows 7 o posterior)|Permite a los clientes de BranchCache usar HTTP para recuperar contenido de otros en el modo distribuido y desde la caché hospedada en el modo de caché hospedada. Esta configuración usa HTTP.|
|**BranchCache: cliente de caché hospedada**<br>(Windows 7 o posterior)|Permite a los clientes de BranchCache usar una caché hospedada. Esta configuración usa HTTPS.|
|**BranchCache: servidor de caché hospedada**|Permite a los clientes de BranchCache usar una caché hospedada para comunicarse con otros clientes. Esta configuración usa HTTPS.|
|**BranchCache: detección de pares**<br>(Windows 7 o posterior)|Permite a los clientes de BranchCache usar el protocolo de detección WS para comprobar la disponibilidad del contenido en la subred local.|
|**Caché del mismo nivel de BITS**|Permite a los clientes usar Servicio de transferencia inteligente en segundo plano (BITS) para buscar y compartir archivos que se almacenan en la caché de BITS de clientes de la misma subred. Esta configuración usa WSDAPI y RPC.|
|**Conectarse a un proyector de red**|Permite a los usuarios conectarse a proyectores a través de redes cableadas o inalámbricas para poder mostrar una presentación. Esta configuración usa WSDAPI.|
|**Redes principales**|Permite a los clientes usar IPv4 e IPv6 para conectarse a recursos de red.|
|**Coordinador de transacciones distribuidas**|Permite a los equipos administrados coordinar las transacciones que actualizan los recursos protegidos contra transacciones, como, por ejemplo, las bases de datos, las colas de mensajes y los sistemas de archivos.|
|**Compartir archivos e impresoras**|Permite a los usuarios compartir archivos e impresoras locales con otros usuarios de la red. Esta configuración utiliza NetBIOS, LLMNR, SMB y RPC.|
|**Grupo Hogar**<br>(Windows 7 o posterior)|Permite a los equipos administrados participar en una red Grupo Hogar.|
|**Servicio iSCSI**|Permite a los equipos administrados conectarse a servidores y dispositivos iSCSI.|
|**Servicio de administración de claves**|Permite el recuento de equipos para el cumplimiento de licencias en entornos de empresa.|
|**Media Center Extenders**|Permite que los Media Center Extender se comuniquen con un equipo que ejecuta Windows Media Center. Esta configuración usa SSDP y qWave.|
|**Servicio de Net Logon**|Configura un canal de seguridad entre clientes del dominio y un controlador de dominio para la autenticación de usuarios y servicios. Esta configuración usa RPC.|
|**Detección de redes**|Permite a los equipos detectar otros dispositivos y ser detectados por otros dispositivos en la red. Esta configuración usa Host de detección de funciones y Servicios de publicación, así como los protocolos de red SSDP, NetBIOS, LLMNR y UPnP.|
|**Registros y alertas de rendimiento**|Permite la administración remota del servicio Registros y alertas de rendimiento. Esta configuración usa RPC.|
|**Administración remota**|Permite la administración remota del equipo.|
|**Asistencia remota**|Permite a los usuarios de equipos administrados solicitar asistencia remota de otros usuarios de la red. Esta configuración usa los protocolos de red SSDP, PNRP, Teredo y UPnP.|
|**Escritorio remoto**|Permite al equipo usar Escritorio remoto para tener acceso a otros equipos.|
|**Administración remota de registro de eventos**|Permite ver y administrar de forma remota el registro de eventos del cliente. Esta configuración usa Canalizaciones con nombre y RPC.|
|**Administración remota de tareas programadas**|Permite la administración remota del servicio de programación de tareas. Esta configuración usa RPC.|
|**Administración remota de servicios**|Permite la administración remota de los servicios locales en los clientes. Esta configuración usa Canalizaciones con nombre y RPC.|
|**Administración remota del volumen**|Permite la administración remota de volúmenes de disco de software y de hardware. Esta configuración usa RPC.|
|**Enrutamiento y acceso remoto**|Permite conexiones VPN y de acceso remoto entrantes a los equipos.|
|**Protocolo de túnel de sockets seguros**|Permite las conexiones VPN entrantes a los equipos administrados mediante el empleo del protocolo de túnel de sockets seguros (SSTP). Esta configuración usa HTTPS.|
|**Captura de SNMP**|Permite a los equipos administrados recibir tráfico del servicio Captura de SNMP.|
|**Entorno UPnP**|Configura el servicio Entorno UPnP en los equipos para permitirles detectar o utilizar dispositivos UPnP certificados.|
|**Servicio de registro de nombres de equipo de Windows Collaboration**|Permite a los equipos buscar y comunicarse con otros equipos mediante el Protocolo de resolución de nombres de mismo nivel (PRNP). Esta configuración usa SSDP y PNRP.|
|**Reproductor de Windows Media**|Permite que los usuarios reciban archivos multimedia de transmisión por secuencias sobre UDP.|
|**Servicio de uso compartido de red del Reproductor de Windows Media**|Permite que los usuarios compartan archivos multimedia a través de una red. Esta configuración usa los protocolos de red SSDP, qWave y UPnP.|
|**Servicio de uso compartido de red del Reproductor de Windows Media (Internet)**<br>(Windows 7 o posterior)|Permite a los usuarios compartir archivos multimedia domésticos a través de Internet.|
|**Área de encuentro de Windows**|Permite a los usuarios colaborar a través de una red para compartir con otras personas documentos, programas o el escritorio. Esta configuración usa DFSR y P2P.|
|**Windows Peer to Peer Collaboration Foundation**|Configura varios programas y tecnologías punto a punto para que puedan conectarse. Esta configuración usa SSDP y PNRP.|
|**Administración remota de Windows (Compatibilidad)**|Permite la administración remota de equipos administrados mediante el empleo de WS-Management, un protocolo basado en servicios web para la administración remota de sistemas operativos y dispositivos.|
|**Administración remota de Windows**<br>(Windows 8 o posterior)|Permite la administración remota de equipos administrados mediante el empleo de WS-Management, un protocolo basado en servicios web para la administración remota de sistemas operativos y dispositivos.|
|**Windows Virtual PC**<br>(Windows 7 o posterior)|Permite que las máquinas virtuales se comuniquen con otros equipos.|
|**Dispositivos portátiles inalámbricos**|Permite la transferencia de archivos multimedia a equipos administrados desde cualquier cámara o dispositivo multimedia que se pueda conectar a la red, por medio del Protocolo de transferencia multimedia (MTP). Esta configuración usa los protocolos de red SSDP y UPnP.|

### Consulte también
[Directivas para proteger equipos de Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


