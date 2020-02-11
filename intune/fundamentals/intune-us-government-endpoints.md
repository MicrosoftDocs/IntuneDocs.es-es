---
title: Puntos de conexión de red para las implementaciones del Gobierno de EE. UU. - Microsoft Intune
titleSuffix: ''
description: Revise los puntos de conexión del Gobierno de EE. UU para Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dfa93bb758447c872d172ded7706fd7507a42f11
ms.sourcegitcommit: c7c6be3833d9a63d43f31d598b555b49b33cf5cb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2020
ms.locfileid: "76966290"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Puntos de conexión del Gobierno de EE. UU. de Microsoft Intune

En esta página se enumeran los puntos de conexión del Gobierno de EE. UU. necesarios para la configuración del proxy en las implementaciones de Intune.

Para administrar dispositivos que se encuentren detrás de firewalls y servidores proxy, debe habilitar la comunicación para Intune.

- El servidor proxy debe ser compatible con **HTTP (80)** y **HTTPS (443)** , ya que los clientes de Intune usan ambos protocolos.
- Para algunas tareas (como descargar actualizaciones de software), Intune necesita acceso de un servidor proxy no autenticado a manage.microsoft.com.

Puede modificar la configuración del servidor proxy en equipos cliente individuales. También puede usar la opción de directiva de grupo para cambiar la configuración de todos los equipos cliente que se encuentran detrás de un servidor proxy especificado.

Los dispositivos administrados requieren configuraciones que dejen acceder a **Todos los usuarios** a los servicios a través de firewalls.

Para más información sobre la inscripción automática de Windows 10 y el registro de dispositivos para clientes de la administración pública de Estados Unidos, consulte [Configuración de la inscripción para dispositivos Windows](../enrollment/windows-enroll.md#windows-10-auto-enrollment-and-device-registration).

En las siguientes tablas se enumeran los puertos y los servicios a los que accede el cliente de Intune:

|**Punto de conexión**|**Dirección IP**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Puntos de conexión del Gobierno de EE. UU. designados por el cliente:
- Azure Portal: https:\//portal.azure.us/ 
- Office 365: https:\//portal.office365.us/ 
- Portal de empresa de Intune: https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Puntos de conexión de servicio asociados de los que depende Intune:
- Servicio sincronización de AAD: https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https:\//login.microsoftonline.us
- Proxy de directorio: https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph: https:\//directory.microsoftazure.us y https:\//graph.microsoftazure.us
- MS Graph: https:\//graph.microsoft.us
- ADRS: https:\//enterpriseregistration.microsoftonline.us

## <a name="windows-push-notification-services"></a>Servicios de notificaciones de inserción de Windows
En los dispositivos Windows administrados por Intune que se administran mediante administración de dispositivos móviles (MDM), las acciones de dispositivos y otras actividades inmediatas requieren Servicios de notificaciones de inserción de Windows (WNS). Para más información, vea [Configuraciones de firewall y proxy de empresa para admitir el tráfico de WNS](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config).

## <a name="apple-device-network-information"></a>Información de red de dispositivos de Apple

|**Se usa para**|**Nombre de host (dirección IP/subred)**|**Protocolo**|**Puerto**|
|------------|-----------|------------|-----------|
|Recuperación y visualización de contenido de los servidores de Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|Comunicación con servidores APNS|#-courier.push.apple.com<br>"#" es un número aleatorio entre 0 y 50.|TCP|5223 y 443|
|Distintas funciones, como acceso a Internet, iTunes Store, App Store de macOS, iCloud, mensajería, etc.|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 o 443|

Para obtener más información, vea:

- [Puertos TCP y UDP usados por los productos de software de Apple](https://support.apple.com/HT202944)
- [Acerca de los procesos en segundo plano de iTunes y las conexiones del host para el servidor de iTunes, iOS y macOS](https://support.apple.com/HT201999)
- [Si tus clientes macOS e iOS no reciben notificaciones push de Apple](https://support.apple.com/HT203609)

## <a name="next-steps"></a>Pasos siguientes
[Puntos de conexión de red de Microsoft Intune](intune-endpoints.md)

