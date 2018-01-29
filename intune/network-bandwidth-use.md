---
title: Uso de ancho de banda de red de Intune
description: uso de ancho de banda de red de intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/16/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f2055a0949921b52937af18bf1cd73286bf046cf
ms.sourcegitcommit: d6dc1211e9128c2e0608542b72d1caa4d6ba691d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="intune-network-bandwidth-use"></a>Uso de ancho de banda de red de Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

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

|Setting|Valor recomendado|Detalles|
|-----------|---------------------|-----------|
|Tamaño de caché|De 5 a 30 GB|El valor varía según el número de equipos cliente en la red y las configuraciones que se utilizan. Para evitar que los archivos se eliminen demasiado pronto, ajuste el tamaño de la caché para su entorno.|
|Tamaño de archivo de caché individual|950 MB|Es posible que esta opción no esté disponible en todos los servidores proxy de almacenamiento en caché.|
|Tipos de objetos que se almacenarán en caché|HTTP<br /><br />HTTPS<br /><br />BITS|Los paquetes de Intune son archivos CAB recuperados mediante la descarga del Servicio de transferencia inteligente en segundo plano (BITS) a través de HTTP.|
Para obtener información sobre el uso de un servidor proxy para almacenar contenido en caché, consulte la documentación de la solución de servidor proxy.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>Usar Servicio de transferencia inteligente en segundo plano en los equipos
Intune admite el uso del Servicio de transferencia inteligente en segundo plano (BITS) en un equipo Windows para reducir el ancho de banda de red usado durante las horas configuradas. Puede configurar la directiva para BITS en la página **Ancho de banda de red** de la directiva de agente de Intune.

Para obtener más información sobre BITS y equipos Windows, consulte [Servicio de transferencia inteligente en segundo plano](http://technet.microsoft.com/library/bb968799.aspx) en la biblioteca TechNet.

### <a name="use-branchcache-on-computers"></a>Usar BranchCache en los equipos
Los clientes de Intune pueden utilizar BranchCache para reducir el tráfico de la red de área extensa (WAN). Los siguientes sistemas operativos admiten BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Para utilizar BranchCache, el equipo cliente debe tener BranchCache habilitado y, a continuación, configurarse para el **modo de caché distribuida**.

De forma predeterminada, BranchCache y el modo de caché distribuida se habilitan en los equipos cuando se instala el cliente de Intune. Sin embargo, si la directiva de grupo deshabilitó BranchCache, Intune no invalida dicha directiva y BranchCache sigue deshabilitado.

Si usa BranchCache, colabore con otros administradores de la organización para administrar la directiva de grupo y la directiva de firewall de Intune. Asegúrese de que no implementen ninguna directiva que deshabilite las excepciones de BranchCache o de firewall. Para obtener información sobre BranchCache, vea [Información general sobre BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Requisitos de comunicación de red

Habilite las comunicaciones de red entre los dispositivos que administra y los sitios web que se requieren para los servicios basados en la nube.

Intune no usa ninguna infraestructura local, por ejemplo, servidores que ejecuten software Intune, pero existen opciones para usar la infraestructura local, como las herramientas de sincronización de Exchange y Active Directory.

Para administrar equipos que se encuentren detrás de firewalls y servidores proxy, debe habilitar la comunicación para Intune.

-   El servidor proxy debe ser compatible con **HTTP (80)** y **HTTPS (443)**, ya que los clientes de Intune usan ambos protocolos.
-   Intune necesita acceso de un servidor proxy no autenticado a manage.microsoft.com para algunas tareas como la descarga de software y actualizaciones

Puede modificar la configuración del servidor proxy o los equipos cliente individuales, o bien usar la configuración de la directiva de grupo para cambiar de todos los equipos cliente que se encuentran detrás de un servidor proxy especificado.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Los dispositivos administrados requieren configuraciones que dejen acceder a **Todos los usuarios** a los servicios a través de firewalls.

En las siguientes tablas se enumeran los puertos y los servicios a los que accede el cliente de Intune:

|**Dominios**|**Dirección IP**|
|---------------------|-----------|
|login.microsoftonline.com | Más información [URL de Office 365 e intervalos de direcciones IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |  13.64.198.190|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |13.64.188.173|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |40.71.32.174|
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |13.64.197.181 |
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |40.71.38.205|
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |13.64.191.182 |
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |40.71.37.51 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |40.118.250.246 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |13.90.142.194 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.64.250.226 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.90.151.142 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.169.155.165 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.174.188.97 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.178.190.24 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.174.16.215 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |40.69.69.27 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |52.166.196.199 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |40.69.71.164 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |52.174.182.102 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |40.69.78.145 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |52.174.192.105 |
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |13.94.46.250|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |52.163.119.15 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |13.75.124.145 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |52.163.119.5|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.175.35.226|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.163.119.6|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.175.38.24|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.163.119.3|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|23.97.165.17|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|

### <a name="apple-device-network-information"></a>Información de red de dispositivos de Apple
| Nombre de host  | Dirección URL (dirección IP/subred) | Protocol | Puerto | Dispositivo |
| --- | --- | --- | --- | --- |
|  Consola de administración  | gateway.push.apple.com (17.0.0.0/8) | TCP | 2195 | Apple iOS y macOS |
| Consola de administración  | feedback.push.apple.com(17.0.0.0/8) | TCP | 2196 | Apple iOS y macOS |
| Consola de administración  | Apple iTunesitunes.apple.com, \*.mzstatic.com, \*.phobos.apple.com y \*.phobos.apple.com.edgesuite.net | HTTP | 80 | Apple iOS y macOS  |
| Servidor de PI  | gateway.push.apple.com(17.0.0.0/8) feedback.push.apple.com(17.0.0.0/8) | TCP | 2195, 2196 | Para la mensajería de nube de Apple iOS y macOS. |
| Servicios de dispositivos  | gateway.push.apple.com | TCP | 2195 | Apple  |
| Servicios de dispositivos  | feedback.push.apple.com | TCP | 2196 | Apple  |
| Servicios de dispositivos  | Apple iTunesitunes.apple.com, \*.mzstatic.com\*, .phobos.apple.com y \*.phobos.apple.com.edgesuite.net | HTTP | 80 | Apple  |
| Dispositivos (Internet/Wi-Fi) | #-courier.push.apple.com(17.0.0.0/8) | TCP | 5223 y 443 | Solo Apple. &#39;#&#39; es un número aleatorio comprendido entre 0 y 200. |
| Dispositivos (Internet/Wi-Fi) | phobos.apple.comocsp.apple.comax.itunes.apple.com | HTTP o HTTPS | 80 o 443 | Solo Apple |
