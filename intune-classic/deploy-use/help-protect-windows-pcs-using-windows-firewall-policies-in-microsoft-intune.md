---
title: Directivas de firewall para equipos Windows
description: Intune puede ayudarle a proteger los equipos que administra con el cliente de Intune de varias maneras. Una de ellas es configurar Firewall de Windows.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b04e6e06c2257ffc5822b28b6f81dd00ca5573cc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>Ayudar a proteger los equipos de Windows mediante directivas del Firewall de Windows en Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune puede ayudarle a proteger los equipos que administra con el cliente de Intune de varias maneras. Una de ellas es proporcionar directivas que permiten configurar Firewall de Windows en equipos.

Si aún no ha instalado el cliente de equipos Windows de Intune en sus equipos PC, vea [Instalar el cliente de equipos Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Use la información de las siguientes secciones como ayuda para configurar, implementar y supervisar las directivas de Firewall de Windows en equipos Windows.

## <a name="use-intune-policies-to-manage-windows-firewall"></a>Uso de directivas de Intune para administrar Firewall de Windows
La directiva de Firewall de Windows permite crear e implementar la configuración que controla Firewall de Windows en los equipos administrados. No puede administrar excepciones personalizadas para Firewall de Windows, y esta configuración no afecta a ningún firewall que no sea de Microsoft.

> [!NOTE]
> Si la directiva de Microsoft Intune y la directiva de grupo están configuradas para administrar la misma opción en el equipo, la opción de la directiva de grupo anula la opción de la directiva de Microsoft Intune. Para obtener información sobre cómo evitar conflictos entre la directiva de Intune y la directiva de grupo, consulte [Resolver conflictos de directivas de Microsoft Intune y GPO](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Si quiere implementar la configuración de Firewall de Windows en equipos que ejecutan Windows Vista, primero debe instalar la [revisión KB971800](http://support2.microsoft.com/kb/971800) en estos equipos.

> [!IMPORTANT]
> Para administrar Firewall de Windows mediante Intune, asegúrese de que los dos servicios siguientes estén habilitados en los equipos que administra:
>
> -   Firewall de Windows
> -   Agente de directivas IPsec

## <a name="configure-a-windows-firewall-policy"></a>Para configurar una directiva de Firewall de Windows

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Directiva** &gt; **Agregar directiva**.

2.  Configurar e implementar una directiva de **Configuración de Firewall de Windows** . Puede usar la configuración recomendada o personalizar la configuración. Si necesita más información sobre cómo crear e implementar directivas, vea [Tareas comunes de administración de PC Windows con el cliente de equipo de Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

    En la sección siguiente se muestran los valores que puede configurar en la directiva y también los valores predeterminados que se usarán si no personaliza la directiva.

Tras implementar la directiva de Firewall de Windows, puede ver su estado en la página **Todas las directivas** del área de trabajo **Directiva**.

## <a name="specify-policy-settings-for-windows-firewall"></a>Especificar la configuración de directiva para Firewall de Windows

### <a name="turn-on-windows-firewall"></a>Activar Firewall de Windows

Esta configuración de directiva habilita Firewall de Windows en equipos administrados que están conectados a:
- un dominio (por ejemplo, en el área de trabajo)
- una red privada (de confianza) (por ejemplo, una red doméstica)
- una red pública que no es de confianza (por ejemplo, una cafetería)

El valor predeterminado de cada uno de estos valores es **Sí**, que es el valor más seguro.



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>Bloquear todas las conexiones entrantes, incluidas las de la lista de programas permitidos.

Esta configuración de directiva configura Firewall de Windows para bloquear el tráfico de red de entrada en equipos administrados que están conectados a:
- un dominio (por ejemplo, en el área de trabajo)
- una red privada (de confianza) (por ejemplo, una red doméstica)
- una red pública que no es de confianza (por ejemplo, una cafetería)

El valor predeterminado de cada uno de estos valores es **Sí**, que es el valor más seguro.

> [!IMPORTANT]
> Si su entorno incluye equipos administrados que ejecutan Windows Vista sin ningún Service Pack instalado, debe instalar la actualización asociada al [artículo 971800](http://go.microsoft.com/fwlink/?LinkId=188405) de Microsoft Knowledge Base o deshabilitar la configuración de directiva **Bloquear todas las conexiones entrantes** en las directivas implementadas en dichos equipos.

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>Notificar al usuario cuando Firewall de Windows bloquee un nuevo programa

Esta configuración de directiva determina si Firewall de Windows notifica al usuario de un equipo cuando se bloquea el tráfico de red de entrada cuando el equipo administrado está conectado a:
- un dominio (por ejemplo, en el área de trabajo)
- una red privada (de confianza) (por ejemplo, una red doméstica)
- una red pública que no es de confianza (por ejemplo, una cafetería)

El valor predeterminado para cada uno de estos valores es **Sí**.


### <a name="configure-predefined-exceptions"></a>Configurar excepciones predefinidas

Puede configurar las excepciones que permiten determinados tipos de tráfico de red a través del firewall independientemente de los valores que haya configurado con anterioridad. De forma predeterminada, no se configura ninguna de estas opciones.

|Nombre de la configuración|Detalles|
|------------------|--------------------|
|**BranchCache: recuperación de contenido**<br>(Windows 7 o posterior)|Permite a los clientes de BranchCache usar HTTP para recuperar contenido de otros clientes de BranchCache en el modo distribuido y desde la caché hospedada en el modo de caché hospedada. Esta configuración usa HTTP.|
|**BranchCache: cliente de caché hospedada**<br>(Windows 7 o posterior)|Permite a los clientes de BranchCache usar una caché hospedada. Esta configuración usa HTTPS.|
|**BranchCache: servidor de caché hospedada**|Permite a los clientes de BranchCache usar una caché hospedada para comunicarse con otros clientes. Esta configuración usa HTTPS.|
|**BranchCache: detección de pares**<br>(Windows 7 o posterior)|Permite a los clientes de BranchCache usar el protocolo de detección dinámica de servicios web (WS-Discovery) para comprobar la disponibilidad del contenido en la subred local.|
|**Caché del mismo nivel de BITS**|Permite a los clientes usar Servicio de transferencia inteligente en segundo plano (BITS) para buscar y compartir archivos que se almacenan en la caché de BITS de clientes de la misma subred. Esta configuración usa Servicios web en dispositivos (WSDAPI) y Llamada a procedimiento remoto (RPC).|
|**Conectarse a un proyector de red**|Permite a los usuarios conectarse a proyectores a través de redes cableadas o inalámbricas para poder mostrar una presentación. Esta configuración usa WSDAPI.|
|**Redes principales**|Permite a los clientes usar IPv4 e IPv6 para conectarse a recursos de red.|
|**Coordinador de transacciones distribuidas**|Permite a los equipos administrados coordinar las transacciones que actualizan los recursos protegidos contra transacciones, como, por ejemplo, las bases de datos, las colas de mensajes y los sistemas de archivos.|
|**Compartir archivos e impresoras**|Permite a los usuarios compartir archivos e impresoras locales con otros usuarios de la red. Esta configuración usa NetBIOS, Resolución de nombres de multidifusión local de vínculos (LLMNR), el protocolo Bloque de mensajes del servidor (SMB) y RPC.|
|**Grupo Hogar**<br>(Windows 7 o posterior)|Permite a los equipos administrados participar en una red Grupo Hogar.|
|**Servicio iSCSI**|Permite a los equipos administrados conectarse a servidores y dispositivos iSCSI.|
|**Servicio de administración de claves**|Permite el recuento de equipos para el cumplimiento de licencias en entornos de empresa.|
|**Media Center Extenders**|Permite que los Media Center Extender se comuniquen con un equipo que ejecuta Windows Media Center. Esta configuración usa qWave y Protocolo simple de detección de servicios (SSDP).|
|**Servicio de Net Logon**|Configura un canal de seguridad entre clientes del dominio y un controlador de dominio para la autenticación de usuarios y servicios. Esta configuración usa RPC.|
|**Detección de redes**|Permite a los equipos detectar otros dispositivos y ser detectados por otros dispositivos en la red. Esta configuración usa Host de detección de funciones y Servicios de publicación, así como los protocolos de red SSDP, NetBIOS, LLMNR y UPnP.|
|**Registros y alertas de rendimiento**|Permite la administración remota del servicio Registros y alertas de rendimiento. Esta configuración usa RPC.|
|**Administración remota**|Permite la administración remota del equipo.|
|**Asistencia remota**|Permite a los usuarios de equipos administrados solicitar asistencia remota de otros usuarios de la red. Esta configuración usa los protocolos de red SSDP, Protocolo de resolución de nombres de mismo nivel (PNRP), Teredo y UPnP.|
|**Escritorio remoto**|Permite al equipo usar Escritorio remoto para tener acceso a otros equipos.|
|**Administración remota de registro de eventos**|Permite ver y administrar de forma remota el registro de eventos del cliente. Esta configuración usa Canalizaciones con nombre y RPC.|
|**Administración remota de tareas programadas**|Permite la administración remota del servicio de programación de tareas. Esta configuración usa RPC.|
|**Administración remota de servicios**|Permite la administración remota de los servicios locales en los clientes. Esta configuración usa Canalizaciones con nombre y RPC.|
|**Administración remota del volumen**|Permite la administración remota de volúmenes de disco de software y de hardware. Esta configuración usa RPC.|
|**Enrutamiento y acceso remoto**|Permite conexiones VPN y de acceso remoto entrantes a los equipos.|
|**Protocolo de túnel de sockets seguros**|Permite conexiones VPN entrantes a los equipos administrados mediante Protocolo de túnel de sockets seguros (SSTP). Esta configuración usa HTTPS.|
|**Captura de SNMP**|Permite a los equipos administrados recibir tráfico del servicio de captura de Protocolo simple de administración de redes (SNMP).|
|**Entorno UPnP**|Configura el servicio Entorno UPnP en los equipos para permitirles detectar o utilizar dispositivos UPnP certificados.|
|**Servicio de registro de nombres de equipo de Windows Collaboration**|Permite a los equipos buscar y comunicarse con otros equipos mediante SSDP y PNRP.|
|**Reproductor de Windows Media**|Permite que los usuarios reciban streaming de contenido multimedia por Protocolo de datagramas de usuario (UDP).|
|**Servicio de uso compartido de red del Reproductor de Windows Media**|Permite que los usuarios compartan archivos multimedia a través de una red. Esta configuración usa los protocolos de red SSDP, qWave y UPnP.|
|**Servicio de uso compartido de red del Reproductor de Windows Media (Internet)**<br>(Windows 7 o posterior)|Permite a los usuarios compartir archivos multimedia domésticos a través de Internet.|
|**Área de encuentro de Windows**|Permite a los usuarios colaborar a través de una red para compartir con otras personas documentos, programas y el escritorio. Esta configuración usa Replicación del sistema de archivos distribuido (DFSR) y P2P.|
|**Windows Peer to Peer Collaboration Foundation**|Configura varios programas y tecnologías punto a punto para que puedan conectarse. Esta configuración usa SSDP y PNRP.|
|**Administración remota de Windows (Compatibilidad)**|Permite la administración remota de equipos administrados con WS-Management, un protocolo basado en servicios web para la administración remota de sistemas operativos y dispositivos.|
|**Administración remota de Windows**<br>(Windows 8 o posterior)|Permite la administración remota de equipos administrados con WS-Management, un protocolo basado en servicios web para la administración remota de sistemas operativos y dispositivos.|
|**Windows Virtual PC**<br>(Windows 7 o posterior)|Permite que las máquinas virtuales se comuniquen con otros equipos.|
|**Dispositivos portátiles inalámbricos**|Permite la transferencia de archivos multimedia a equipos administrados desde cualquier cámara o dispositivo multimedia que se pueda conectar a la red, por medio de Protocolo de transferencia multimedia (MTP). Esta configuración usa los protocolos de red SSDP y UPnP.|

### <a name="see-also"></a>Vea también
[Directivas para proteger equipos de Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
