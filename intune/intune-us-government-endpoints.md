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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 490c939e79659baac655cfd7d3d3a2ee10d98382
ms.sourcegitcommit: d2989b9992d10d133573d9bc31479659fb7e242c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079929"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Puntos de conexión del Gobierno de EE. UU. de Microsoft Intune

En esta página se enumeran los puntos de conexión del Gobierno de EE. UU. necesarios para la configuración del proxy en las implementaciones de Intune.

Para administrar dispositivos que se encuentren detrás de firewalls y servidores proxy, debe habilitar la comunicación para Intune.

- El servidor proxy debe ser compatible con **HTTP (80)** y **HTTPS (443)** , ya que los clientes de Intune usan ambos protocolos.
- Para algunas tareas (como descargar actualizaciones de software), Intune necesita acceso de un servidor proxy no autenticado a manage.microsoft.com.

Puede modificar la configuración del servidor proxy en equipos cliente individuales. También puede usar la opción de directiva de grupo para cambiar la configuración de todos los equipos cliente que se encuentran detrás de un servidor proxy especificado.

Los dispositivos administrados requieren configuraciones que dejen acceder a **Todos los usuarios** a los servicios a través de firewalls.

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
