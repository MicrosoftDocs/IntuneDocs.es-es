---
title: Uso de ancho de banda de red de Intune | Microsoft Docs
description: uso de ancho de banda de red de intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0f5972171349325eeb750e552481cbcf903fdf95
ms.openlocfilehash: 9f1cd7ea3e92ac2e3a1b828e8185961060a7c619
ms.lasthandoff: 02/10/2017


---

# <a name="intune-network-bandwidth-use"></a>Uso de ancho de banda de red de Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Esta guía va dirigida a administradores del sistema que son responsables de la administración de dispositivos en la empresa. Para obtener ayuda con el uso de Intune en su dispositivo móvil, consulte las [preguntas más frecuentes sobre el Portal de empresa de Intune](https://docs.microsoft.com/intune/enduser/company-portal-frequently-asked-questions).

Antes de configurar Microsoft Intune, repase este tema y los requisitos que aparecen en [What to know before you start Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md) (Información necesaria antes de iniciar Microsoft Intune).

Utilice la información de las siguientes secciones para planear el tráfico de red para los clientes de Microsoft Intune.

## <a name="average-network-traffic"></a>Tráfico de red medio
En la tabla siguiente se muestra el tamaño aproximado y la frecuencia de contenido común que pasa a través de la red de cada cliente.

> [!NOTE]
> Para asegurarse de que los equipos y dispositivos móviles reciban las actualizaciones y el contenido necesarios del servicio de Intune, se deben conectar periódicamente a Internet. El tiempo que se tarda en recibir actualizaciones o contenido varía, pero como norma, se debe permanecer conectado de forma continua a Internet como mínimo una hora al día.

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
Puede utilizar un servidor proxy que pueda almacenar en caché contenido para reducir la duplicación de descargas y el uso de ancho de banda de red por parte de clientes que solicitan contenido de Internet.

Un servidor proxy de almacenamiento en caché recibe solicitudes de contenido de equipos cliente de su red, recupera ese contenido de Internet y puede almacenar en caché las respuestas HTTP y las descargas binarias. El servidor utiliza la información almacenada en caché para responder las sucesivas solicitudes procedentes de equipos cliente de Intune.

A continuación, se indica la configuración típica que se utiliza para un servidor proxy que almacena en caché contenido para clientes de Intune.

|Configuración|Valor recomendado|Detalles|
|-----------|---------------------|-----------|
|Tamaño de caché|De 5 a 30 GB|El valor varía según el número de equipos cliente en la red y las configuraciones que se utilizan. Para evitar que los archivos se eliminen demasiado pronto, ajuste el tamaño de la caché para su entorno.|
|Tamaño de archivo de caché individual|950 MB|Es posible que esta opción no esté disponible en todos los servidores proxy de almacenamiento en caché.|
|Tipos de objetos que se almacenarán en caché|HTTP<br /><br />HTTPS<br /><br />BITS|Los paquetes de Intune son archivos CAB recuperados mediante la descarga del Servicio de transferencia inteligente en segundo plano (BITS) a través de HTTP.|
Para obtener información sobre el uso de un servidor proxy para almacenar contenido en caché, consulte la documentación de la solución de servidor proxy.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>Usar Servicio de transferencia inteligente en segundo plano en los equipos
Intune admite el uso del Servicio de transferencia inteligente en segundo plano (BITS) en un equipo Windows para reducir el ancho de banda de red usado durante las horas configuradas. Puede configurar la directiva para BITS en la página **Ancho de banda de red** de la directiva de agente de Intune.

Para obtener más información sobre BITS y equipos Windows, consulte [Servicio de transferencia inteligente en segundo plano](http://technet.microsoft.com/library/bb968799.aspx) en la biblioteca TechNet.

### <a name="use-branchcache-on-computers"></a>Usar BranchCache en los equipos
Los clientes de Intune pueden utilizar BranchCache para reducir el tráfico de la red de área extensa (WAN). Los siguientes sistemas operativos admitidos como clientes también admiten BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Para utilizar BranchCache, el equipo cliente debe tener BranchCache habilitado y, a continuación, configurarse para el **modo de caché distribuida**.

De forma predeterminada, BranchCache y el modo de caché distribuida se habilitan en un equipo cuando se instala el cliente de Intune. Sin embargo, si el cliente ya tiene una directiva de grupo que deshabilita BranchCache, Intune no invalida esa directiva y BranchCache permanecerá deshabilitado en ese equipo.

Si utiliza BranchCache, debe comunicarse con los demás administradores de su organización que administren la directiva de grupo y la directiva de Firewall de Intune para asegurarse de que no implementan la directiva que deshabilita las excepciones de Firewall o BranchCache. Para obtener información sobre BranchCache, vea [Información general sobre BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Requisitos de comunicación de red

Para administrar su suscripción de Intune y los sitios web necesarios para los servicios basados en la nube, debe habilitar las comunicaciones de red entre los dispositivos que administra y usa.

Intune no usa ninguna infraestructura local, por ejemplo, servidores que ejecuten software Intune, pero existen opciones para usar la infraestructura local, como las herramientas de sincronización de Exchange y Active Directory.

Para administrar los equipos que están detrás de firewalls y servidores proxy, debe configurar los firewalls y los servidores proxy de modo que permitan las comunicaciones de Intune.

### <a name="requirements-for-proxy-servers"></a>Requisitos de los servidores proxy
Para administrar los equipos que están detrás de un servidor proxy, tenga en cuenta que:

-   El servidor proxy debe ser compatible con **HTTP** y **HTTPS**, ya que los clientes de Intune usan ambos protocolos.
-   Intune es compatible con servidores proxy no autenticados

Puede modificar la configuración del servidor proxy o los equipos cliente individuales, o bien usar la configuración de la directiva de grupo para cambiar de todos los equipos cliente que se encuentran detrás de un servidor proxy especificado.

### <a name="requirements-for-firewalls-ports-and-domains"></a>Requisitos de los firewalls, puertos y dominios
Los dispositivos administrados requieren configuraciones que dejen acceder a **Todos los usuarios** a los servicios a través de firewalls.

En la tabla siguiente se enumeran los puertos y los servicios a los que accede el cliente de Intune.

|**Dominio**|**Puertos**|**Dirección IP**|
|------|----|---|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>p.manage.microsoft.com<br>r.manage.microsoft.com|80 y 443|134.170.168.254<br>134.170.51.126
|m.manage.microsoft.com|80 y 443| 13.91.59.243<br>40.68.30.140
|portal.manage.microsoft.com|80 y 443|40.121.50.69<br>52.169.30.159
|account.manage.microsoft.com|80 y 443|157.56.13.59
|fef.msua01.manage.microsoft.com|80 y 443|138.91.243.97
|fef.msua02.manage.microsoft.com|80 y 443|23.96.112.46
|fef.msua04.manage.microsoft.com|80 y 443|23.96.112.28
|fef.msua05.manage.microsoft.com|80 y 443|138.91.244.151
|fef.msub01.manage.microsoft.com|80 y 443|137.135.128.214
|fef.msub02.manage.microsoft.com|80 y 443|137.135.130.29
|fef.msub03.manage.microsoft.com|80 y 443|23.97.165.17
|fef.msub05.manage.microsoft.com|80 y 443|23.97.166.52
|fef.msuc01.manage.microsoft.com|80 y 443|207.46.225.1
|fef.msuc02.manage.microsoft.com|80 y 443|23.98.66.118
|fef.msuc03.manage.microsoft.com|80 y 443|23.101.0.100
|fef.msuc05.manage.microsoft.com|80 y 443|207.46.154.33
|fef.msua06.manage.microsoft.com|80 y 443|104.42.188.1
|fei.msua01.manage.microsoft.com|80 y 443|138.91.240.131
|fei.msua02.manage.microsoft.com|80 y 443|23.96.112.143
|fei.msua04.manage.microsoft.com|80 y 443|23.96.112.147
|fei.msua05.manage.microsoft.com|80 y 443|138.91.240.163
|fei.msub01.manage.microsoft.com|80 y 443|137.135.130.85
|fei.msub02.manage.microsoft.com|80 y 443|137.135.132.149
|fei.msub03.manage.microsoft.com|80 y 443|23.97.160.232
|fei.msub05.manage.microsoft.com|80 y 443|23.97.162.250
|fei.msuc01.manage.microsoft.com|80 y 443|207.46.224.73
|fei.msuc02.manage.microsoft.com|80 y 443|23.98.66.194
|fei.msuc03.manage.microsoft.com|80 y 443|23.101.2.105
|fei.msuc05.manage.microsoft.com|80 y 443|207.46.147.126
|fei.msua06.manage.microsoft.com|80 y 443|138.91.149.190
|m.fei.msua01.manage.microsoft.com|80 y 443|138.91.240.131
|m.fei.msua02.manage.microsoft.com|80 y 443|23.96.112.143
|m.fei.msua04.manage.microsoft.com|80 y 443|23.96.112.147
|m.fei.msua05.manage.microsoft.com|80 y 443|138.91.240.163
|m.fei.msub01.manage.microsoft.com|80 y 443|137.135.130.85
|m.fei.msub02.manage.microsoft.com|80 y 443|137.135.132.149
|m.fei.msub03.manage.microsoft.com|80 y 443|23.97.160.232
|m.fei.msub05.manage.microsoft.com|80 y 443|23.97.162.250
|m.fei.msuc01.manage.microsoft.com|80 y 443|207.46.224.73
|m.fei.msuc02.manage.microsoft.com|80 y 443|23.98.66.194
|m.fei.msuc03.manage.microsoft.com|80 y 443|23.101.2.105
|m.fei.msuc05.manage.microsoft.com|80 y 443|207.46.147.126
|m.fei.msua06.manage.microsoft.com|80 y 443|138.91.149.190
|m.msua01.manage.microsoft.com|80 y 443|157.55.50.182
|m.msua02.manage.microsoft.com|80 y 443|134.170.49.121
|m.msua04.manage.microsoft.com|80 y 443|134.170.49.126
|m.msua05.manage.microsoft.com|80 y 443|157.55.240.190
|m.msua06.manage.microsoft.com|80 y 443|134.170.49.114
|m.msub01.manage.microsoft.com|80 y 443|94.245.121.50
|m.msub02.manage.microsoft.com|80 y 443|94.245.121.58
|m.msub03.manage.microsoft.com|80 y 443|94.245.121.56
|m.msub05.manage.microsoft.com|80 y 443|157.56.113.123
|m.msuc01.manage.microsoft.com|80 y 443|104.44.84.187
|m.msuc02.manage.microsoft.com|80 y 443|104.44.84.188
|m.msuc03.manage.microsoft.com|80 y 443|104.44.84.189
|m.msuc05.manage.microsoft.com|80 y 443|111.221.76.60
|msua01.manage.microsoft.com|80 y 443|157.55.50.182
|msua02.manage.microsoft.com|80 y 443|134.170.49.121
|msua04.manage.microsoft.com|80 y 443|134.170.49.126
|msua05.manage.microsoft.com|80 y 443|157.55.240.190
|msub01.manage.microsoft.com|80 y 443|94.245.121.50
|msub02.manage.microsoft.com|80 y 443|94.245.121.58
|msub03.manage.microsoft.com|80 y 443|94.245.121.56
|msub05.manage.microsoft.com|80 y 443|157.56.113.123
|msuc01.manage.microsoft.com|80 y 443|104.44.84.187
|msuc02.manage.microsoft.com|80 y 443|104.44.84.188
|msuc03.manage.microsoft.com|80 y 443|104.44.84.189
|msuc05.manage.microsoft.com|80 y 443|111.221.76.60
|msua06.manage.microsoft.com|80 y 443|134.170.49.114
|ncufun.account.manage.microsoft.com|80 y 443|157.55.252.224
|neufun.account.manage.microsoft.com|80 y 443|65.52.229.134
|portal.fei.msua01.manage.microsoft.com|80 y 443|138.91.240.131
|portal.fei.msua02.manage.microsoft.com|80 y 443|23.96.112.143
|portal.fei.msua04.manage.microsoft.com|80 y 443|23.96.112.147
|portal.fei.msua05.manage.microsoft.com|80 y 443|138.91.240.163
|portal.fei.msub01.manage.microsoft.com|80 y 443|137.135.130.85
|portal.fei.msub02.manage.microsoft.com|80 y 443|137.135.132.149
|portal.fei.msub03.manage.microsoft.com|80 y 443|23.97.160.232
|portal.fei.msub05.manage.microsoft.com|80 y 443|23.97.162.250
|portal.fei.msuc01.manage.microsoft.com|80 y 443|207.46.224.73
|portal.fei.msuc02.manage.microsoft.com|80 y 443|23.98.66.194
|portal.fei.msuc03.manage.microsoft.com|80 y 443|23.101.2.105
|portal.fei.msuc05.manage.microsoft.com|80 y 443|207.46.147.126
|portal.fei.msua06.manage.microsoft.com|80 y 443|138.91.149.190
|portal.msua01.manage.microsoft.com|80 y 443|157.55.50.182
|portal.msua02.manage.microsoft.com|80 y 443|134.170.49.121
|portal.msua04.manage.microsoft.com|80 y 443|134.170.49.126
|portal.msua05.manage.microsoft.com|80 y 443|157.55.240.190
|portal.msub01.manage.microsoft.com|80 y 443|94.245.121.50
|portal.msub02.manage.microsoft.com|80 y 443|94.245.121.58
|portal.msub03.manage.microsoft.com|80 y 443|94.245.121.56
|portal.msub05.manage.microsoft.com|80 y 443|157.56.113.123
|portal.msuc01.manage.microsoft.com|80 y 443|104.44.84.187
|portal.msuc02.manage.microsoft.com|80 y 443|104.44.84.188
|portal.msuc03.manage.microsoft.com|80 y 443|104.44.84.189
|portal.msuc05.manage.microsoft.com|80 y 443|111.221.76.60
|portal.msua06.manage.microsoft.com|80 y 443|134.170.49.114
|ssu2.manage.microsoft.com|80 y 443|157.55.99.181
|status.manage.microsoft.com|80 y 443|157.55.99.170
|swda01.manage.microsoft.com<br>swda02.manage.microsoft.com<br>swdb01.manage.microsoft.com<br>swdb02.manage.microsoft.com<br>swdc01.manage.microsoft.com<br>swdc02.manage.microsoft.com|80 y 443|93.184.215.200
|*.microsoftonline-p.com|80 y 443||
|has.spserv.microsoft.com<br>Necesario para el servicio de atestación de estado de dispositivo|443||
|*.microsoftonline-p.net|80 y 443||
|*.portal.office.com|80 y 443||
|*.spynet2.microsoft.com|443||
|c.microsoft.com|80 y 443||
|c1.microsoft.com|80 y 443||
|blob.core.windows.net|80 y 443||
|ajax.aspnetcdn.com|80 y 443||
|*.googleapis.com<br>Este dominio es necesario para la compatibilidad con JQuery cuando se utiliza el sitio web del portal de empresa.|80 y 443||
|wustat.microsoft.com|80 y 443||
|Servicios de Microsoft Update|\*.update.microsoft.com<br>download.microsoft.com<br>update.microsoft.com<br>\*.download.windowsupdate.com<br>download.windowsupdate.com<br>\*.windowsupdate.com<br>windowsupdate.microsoft.com<br>ntservicepack.microsoft.com|80 y 443|
|Solicitudes de búsqueda de DNS|manage.microsoft.com.nsatc.net|80|
|Comunicación de dispositivos de Samsung KNOX Standard a través del firewall|Para permitir que los dispositivos de Samsung KNOX Standard se comuniquen con servidores KNOX Standard a través del firewall, siga las instrucciones que se indican en las preguntas frecuentes de Samsung KNOX Standard.||
|Comunicación de acceso condicional|443|204.79.197.200|
|Documentación, ayuda y soporte técnico:</br></br>*.livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.Microsoft.com<br>www.microsoft.com|80|||


>[!div class="step-by-step"]

>[&larr; **Requisitos previos**](what-to-know-before-you-start-microsoft-intune.md)     [**Suscripción** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)  

