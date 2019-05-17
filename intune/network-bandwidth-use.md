---
title: Requisitos de red y detalles de ancho de banda para Microsoft Intune
titleSuffix: ''
description: Consulte los requisitos de configuración de red y los detalles de ancho de banda de Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40f9ada715570de7b5b2f95292b7ed0d238242d2
ms.sourcegitcommit: 04d29d47b61486b3586a0e0e5e8e48762351f2a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59570798"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Ancho de banda y requisitos de configuración de red de Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Esta guía ayuda a los administradores de Intune a comprender los requisitos de red para el servicio Intune. Puede utilizar esta información para comprender los requisitos de ancho de banda y la configuración de puerto y dirección IP necesaria para los parámetros del proxy.

## <a name="average-network-traffic"></a>Tráfico de red medio
En la tabla siguiente se muestra el tamaño aproximado y la frecuencia de contenido común que pasa a través de la red de cada cliente.

> [!NOTE]
> Para asegurarse de que los dispositivos reciban actualizaciones y contenido de Intune, se deben conectar a Internet de forma periódica. El tiempo que se requiere para recibir actualizaciones o contenido puede variar, pero los dispositivos deben permanecer conectados de forma continua a Internet como mínimo una hora al día.

|Tipo de contenido|Tamaño aproximado|Frecuencia y detalles|
|----------------|--------------------|-------------------------|
|Instalación del cliente de Intune<br /><br />**Los requisitos siguientes son adicionales a la instalación del cliente de Intune**|125 MB|**Una vez**<br /><br />El tamaño de la descarga de cliente varía dependiendo del sistema operativo del equipo cliente.|
|Paquete de inscripción de cliente|15 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Agente de Endpoint Protection|65 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Agente de Operations Manager|11 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Agente de directivas|3 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Asistencia remota a través de agente de Microsoft Easy Assist|6 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Operaciones diarias de cliente|6 MB|**A diario**<br /><br />El cliente de Intune se comunica regularmente con el servicio de Intune para buscar actualizaciones y directivas, y para notificar el estado del cliente al servicio.|
|Actualizaciones de definiciones de malware de Endpoint Protection|Variable<br /><br />Normalmente, de 40 KB a 2 MB|**A diario**<br /><br />Hasta tres veces al día.|
|Actualización del motor de Endpoint Protection|5 MB|**Mensual**|
|Actualizaciones de software|Variable<br /><br />El tamaño depende de las actualizaciones que implementa.|**Mensual**<br /><br />Normalmente, las actualizaciones de software se publican el segundo martes de cada mes.<br /><br />Un equipo recién inscrito o implementado puede utilizar más ancho de banda de red mientras se descarga el conjunto completo de actualizaciones publicadas anteriormente.|
|Service Packs|Variable<br /><br />El tamaño varía para cada Service Pack implementado.|**Variable**<br /><br />Depende de cuándo se implementan los Service Packs.|
|Distribución de software|Variable<br /><br />El tamaño depende del software implementado.|**Variable**<br /><br />Depende de cuándo se implementa el software.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>Formas de reducir el uso de ancho de banda de red
Puede usar uno o varios de los métodos siguientes para reducir el uso de ancho de banda de red de clientes de Intune.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>Utilizar un servidor proxy para almacenar en caché solicitudes de contenido
Un servidor proxy puede almacenar en caché contenido para reducir las descargas duplicadas y disminuir el ancho de banda de red del contenido de Internet.

Un servidor proxy de almacenamiento en caché que recibe solicitudes de contenido de los clientes puede recuperar dicho contenido y almacenar en caché tanto las respuestas web como las descargas. El servidor usa los datos almacenados en caché para responder solicitudes subsiguientes de los clientes.

A continuación, se indica la configuración típica que se utiliza para un servidor proxy que almacena en caché contenido para clientes de Intune.


|          Setting           |           Valor recomendado           |                                                                                                  Detalles                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Tamaño de caché         |             De 5 a 30 GB             | El valor varía según el número de equipos cliente en la red y las configuraciones que se utilizan. Para evitar que los archivos se eliminen demasiado pronto, ajuste el tamaño de la caché para su entorno. |
| Tamaño de archivo de caché individual |                950 MB                 |                                                                     Es posible que esta opción no esté disponible en todos los servidores proxy de almacenamiento en caché.                                                                     |
|   Tipos de objetos que se almacenarán en caché    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Los paquetes de Intune son archivos CAB recuperados mediante la descarga del Servicio de transferencia inteligente en segundo plano (BITS) a través de HTTP.                                               |
> [!NOTE]
> Si usa un servidor proxy para almacenar en caché las solicitudes de contenido, la comunicación solo se cifra entre el cliente y el proxy y desde el proxy a Intune. La conexión desde el cliente a Intune no se cifrará de un extremo a otro.

Para obtener información sobre el uso de un servidor proxy para almacenar contenido en caché, consulte la documentación de la solución de servidor proxy.

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>Uso del Servicio de transferencia inteligente en segundo plano (BITS) en los equipos
Durante las horas que configuró, puede usar BITS en un equipo con Windows para disminuir el ancho de banda de red. Puede configurar la directiva para BITS en la página **Ancho de banda de red** de la directiva de agente de Intune.

> [!NOTE]
> Para la administración de MDM en Windows, solo la interfaz de administración del SO del tipo de aplicación MobileMSI usa BITS para descarga. AppX/MsiX usan su propia pila de descarga no BITS y las aplicaciones Win32 a través del agente de Intune usan Optimización de distribución en lugar de BITS.

Para obtener más información sobre BITS y equipos Windows, consulte [Servicio de transferencia inteligente en segundo plano](http://technet.microsoft.com/library/bb968799.aspx) en la biblioteca TechNet.

### <a name="use-branchcache-on-computers"></a>Usar BranchCache en los equipos
Los clientes de Intune pueden utilizar BranchCache para reducir el tráfico de la red de área extensa (WAN). Los siguientes sistemas operativos admiten BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Para utilizar BranchCache, el equipo cliente debe tener BranchCache habilitado y, a continuación, configurarse para el **modo de caché distribuida**.

Cuando el cliente Intune está instalado en los equipos, BranchCache y el modo de caché distribuida están habilitados de manera predeterminada. Sin embargo, si la directiva de grupo deshabilitó BranchCache, Intune no invalida dicha directiva y BranchCache sigue deshabilitado.

Si usa BranchCache, colabore con otros administradores de la organización para administrar la directiva de grupo y la directiva de firewall de Intune. Asegúrese de que no implementen ninguna directiva que deshabilite las excepciones de BranchCache o de firewall. Para obtener información sobre BranchCache, vea [Información general sobre BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Requisitos de comunicación de red

Habilite las comunicaciones de red entre los dispositivos que administra y los puntos de conexión que se requieren para los servicios basados en la nube.

Como un servicio solo en la nube, Intune no requiere una infraestructura local como servidores o puertas de enlace.

Para administrar dispositivos que se encuentren detrás de firewalls y servidores proxy, debe habilitar la comunicación para Intune.

- El servidor proxy debe ser compatible con **HTTP (80)** y **HTTPS (443)**, ya que los clientes de Intune usan ambos protocolos.
- Para algunas tareas (como descargar actualizaciones de software), Intune necesita acceso de un servidor proxy no autenticado a manage.microsoft.com.

Puede modificar la configuración del servidor proxy en equipos cliente individuales. También puede usar la opción de directiva de grupo para cambiar la configuración de todos los equipos cliente que se encuentran detrás de un servidor proxy especificado.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Los dispositivos administrados requieren configuraciones que dejen acceder a **Todos los usuarios** a los servicios a través de firewalls.

En las siguientes tablas se enumeran los puertos y los servicios a los que accede el cliente de Intune:

|**Dominios**|**Dirección IP**|
|---------------------|-----------|
|login.microsoftonline.com | Más información [URL de Office 365 e intervalos de direcciones IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|fei.msua01.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>fei.amsua0402.manage.microsoft.com <br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.amsub0202.manage.microsoft.com <br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>fei.amsub0302.manage.microsoft.com <br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|






### <a name="apple-device-network-information"></a>Información de red de dispositivos de Apple


|Usada para|Nombre de host (dirección IP/subred)|Protocol|Puerto|
|-----|--------|------|-------|
|Reciba notificaciones push desde el servicio Intune a través de Apple Push Notification Service (APNS). Consulte [aquí](https://support.apple.com/en-us/HT203609) la documentación de Apple|                                    gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |
|Envío de comentarios al servicio Intune a través de Apple Push Notification Service (APNS)|                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |
|Recuperación y visualización de contenido de los servidores de Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|Comunicaciones con servidores APNS|#-courier.push.apple.com (17.0.0.0/8)<br>"#" es un número aleatorio entre 0 y 50.|    TCP     |  5223 y 443  |
|Distintas funcionalidades, como acceso a la World Wide Web, iTunes Store, App Store de macOS, iCloud, mensajería, etc. |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 o 443   |

Para más información, consulte los artículos [Puertos TCP y UDP usados por los productos de software de Apple](https://support.apple.com/en-us/HT202944), [Acerca de los procesos en segundo plano de iTunes y las conexiones del host para el servidor de iTunes, iOS y macOS](https://support.apple.com/en-us/HT201999) y [Si tus clientes macOS e iOS no reciben notificaciones push de Apple](https://support.apple.com/en-us/HT203609) de Apple.
