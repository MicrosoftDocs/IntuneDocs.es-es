---
title: Puntos de conexión de red de Microsoft Intune
titleSuffix: ''
description: Revise los puntos de conexión de Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30fee770e4af561cac62241e65b673d2f608c918
ms.sourcegitcommit: cc5d757018d05fc03ac9ea3d30f563df9bfd61ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66819721"
---
# <a name="network-endpoints-for-microsoft-intune"></a>Puntos de conexión de red de Microsoft Intune

En esta página se enumeran las direcciones IP y los valores de puerto necesarios para la configuración del proxy en las implementaciones de Intune.

Como un servicio solo en la nube, Intune no requiere una infraestructura local como servidores o puertas de enlace.

Para administrar dispositivos que se encuentren detrás de firewalls y servidores proxy, debe habilitar la comunicación para Intune.

- El servidor proxy debe ser compatible con **HTTP (80)** y **HTTPS (443)** , ya que los clientes de Intune usan ambos protocolos. Windows Information Protection utiliza el puerto 444.
- Para algunas tareas (como descargar actualizaciones de software para el agente de PC clásico), Intune necesita acceso de un servidor proxy no autenticado a manage.microsoft.com.

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
|portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
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


### <a name="network-requirements-for-powershell-scripts-and-win32-apps"></a>Requisitos de red para aplicaciones Win32 y scripts de Powershell
Si usa Intune para implementar scripts de Powershell o aplicaciones Win32, también deberá conceder acceso a los puntos de conexión en los que reside actualmente el inquilino.

|ASU | Nombre de almacenamiento | CDN |
| --- | --- |--- |
| AMSUA0601 | prodmsua06data | https://prodmsua06data.azureedge.net |
| AMSUA0602 | prodamsua0602data | https://prodamsua0602data.azureedge.net |
| AMSUA0101 | prodmsua01data | https://prodmsua01data.azureedge.net |
| AMSUA0201 | prodmsua02data | https://prodmsua02data.azureedge.net |
| AMSUA0202 | Prodmsua0202rcdata | https://prodamsua0202data.azureedge.net/ |
| AMSUA0401 | prodmsua04data | https://prodmsua04data.azureedge.net |
| AMSUA0402 | Prodmsua0402rcdata | https://prodamsua0402data.azureedge.net/ |
| AMSUA0501 | prodmsua05data | https://prodmsua05data.azureedge.net |
| AMSUA0502 | prodmsua0502data | https://prodmsua0502data.azureedge.net |
| AMSUB0101 | prodmsub01data | https://prodmsub01data.azureedge.net |
| AMSUB0102 | prodamsub0102data | https://prodamsub0102data.azureedge.net |
| AMSUB0201 | prodmsub02data | https://prodmsub02data.azureedge.net |
| AMSUB0202 | Prodmsub0202rcdata | https://prodamsub0202data.azureedge.net |
| AMSUB0301 | Prodmsub03data2 | https://prodmsub03data2.azureedge.net |
| AMSUB0302 | Prodmsub0302rcdata | https://prodamsub0302data.azureedge.net |
| AMSUB0501 | prodmsub05data | https://prodmsub05data.azureedge.net |
| AMSUC0101 | prodmsuc01data | https://prodmsuc01data.azureedge.net |
| AMSUC0201 | prodmsuc02data | https://prodmsuc02data.azureedge.net |
| AMSUC0301 | prodmsuc03data | https://prodmsuc03data.azureedge.net |
| AMSUC0501 | prodmsuc05data | https://prodmsuc05data.azureedge.net |
| AMSUA0701 | pemsua07rcdata | https://pemsua07data.azureedge.net |

### <a name="windows-push-notification-services-wns"></a>Servicios de notificaciones de inserción de Windows (WNS)
En los dispositivos de Windows administrados por Intune que se administran mediante administración de dispositivos móviles (MDM), las acciones de dispositivos y otras actividades inmediatas requieren el uso de servicios de notificaciones de inserción de Windows (WNS). Para más información, vea [Permitir el tráfico de notificaciones de Windows a través de firewalls empresariales](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config).    

### <a name="delivery-optimization-port-requirements"></a>Requisitos de puerto para la optimización de entrega

#### <a name="port-requirements"></a>Requisitos de puerto
En el tráfico de punto a punto, la optimización de entrega usa 7680 para TCP/IP o 3544 para NAT transversal (si lo desea, Teredo). Para la comunicación entre servicio y cliente, utiliza HTTP o HTTPS a través del puerto 80/443.

#### <a name="proxy-requirements"></a>Requisitos de proxy
Para usar la optimización de entrega, debe permitir las solicitudes de intervalo de bytes. Para más información, vea [Requisitos de proxy para Windows Update](https://docs.microsoft.com/windows/deployment/update/windows-update-troubleshooting).

#### <a name="firewall-requirements"></a>Requisitos de firewall
Permita los nombres de host siguientes a través del firewall para admitir la optimización de entrega.
Para la comunicación entre los clientes y el servicio en la nube de la optimización de entrega:
- *.do.dsp.mp.microsoft.com

Para los metadatos de optimización de entrega:
- *.dl.delivery.mp.microsoft.com
- *.emdl.ws.microsoft.com

### <a name="apple-device-network-information"></a>Información de red de dispositivos de Apple


|Usada para|Nombre de host (dirección IP/subred)|Protocol|Puerto|
|-----|--------|------|-------|
|Recuperación y visualización de contenido de los servidores de Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|Comunicaciones con servidores APNS|#-courier.push.apple.com<br>"#" es un número aleatorio entre 0 y 50.|    TCP     |  5223 y 443  |
|Distintas funcionalidades, como acceso a la World Wide Web, iTunes Store, App Store de macOS, iCloud, mensajería, etc. |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 o 443   |

Para más información, consulte los artículos [Puertos TCP y UDP usados por los productos de software de Apple](https://support.apple.com/en-us/HT202944), [Acerca de los procesos en segundo plano de iTunes y las conexiones del host para el servidor de iTunes, iOS y macOS](https://support.apple.com/en-us/HT201999) y [Si tus clientes macOS e iOS no reciben notificaciones push de Apple](https://support.apple.com/en-us/HT203609) de Apple.
