---
title: Requisitos de red y detalles de ancho de banda para Microsoft Intune
titleSuffix: ''
description: Consulte los requisitos de configuración de red y los detalles de ancho de banda de Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6d5e8d76a06ac45fed2b9759e519ffc7fabf7ec
ms.sourcegitcommit: d2989b9992d10d133573d9bc31479659fb7e242c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71238308"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Ancho de banda y requisitos de configuración de red de Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Puede usar esta información para comprender los requisitos de ancho de banda de las implementaciones de Intune.

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

Para obtener más información sobre BITS y equipos Windows, consulte [Servicio de transferencia inteligente en segundo plano](https://technet.microsoft.com/library/bb968799.aspx) en la biblioteca TechNet.

### <a name="delivery-optimization"></a>Optimización de entrega
La optimización de entrega le permite usar Intune para reducir el consumo de ancho de banda cuando los dispositivos Windows 10 descargan aplicaciones y actualizaciones. Mediante el uso de una memoria caché distribuida de organización automática, las descargas pueden extraerse de servidores tradicionales y orígenes alternativos (como elementos del mismo nivel de red).

Para ver la lista completa de las versiones de Windows 10 y los tipos de contenido admitidos por la optimización de entrega, consulte el [artículo sobre la optimización de entrega para actualizaciones de Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements).

Puede [configurar la optimización de entrega](delivery-optimization-settings.md) como parte de los perfiles de configuración del dispositivo.


### <a name="use-branchcache-on-computers"></a>Usar BranchCache en los equipos
Los clientes de Intune pueden utilizar BranchCache para reducir el tráfico de la red de área extensa (WAN). Los siguientes sistemas operativos admiten BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Para utilizar BranchCache, el equipo cliente debe tener BranchCache habilitado y, a continuación, configurarse para el **modo de caché distribuida**.

Cuando el cliente Intune está instalado en los equipos, BranchCache y el modo de caché distribuida están habilitados de manera predeterminada. Sin embargo, si la directiva de grupo deshabilitó BranchCache, Intune no invalida dicha directiva y BranchCache sigue deshabilitado.

Si usa BranchCache, colabore con otros administradores de la organización para administrar la directiva de grupo y la directiva de firewall de Intune. Asegúrese de que no implementen ninguna directiva que deshabilite las excepciones de BranchCache o de firewall. Para obtener información sobre BranchCache, vea [Información general sobre BranchCache](https://technet.microsoft.com/library/hh831696.aspx).

> [!NOTE]
> Puede usar Microsoft Intune para administrar equipos con Windows [como dispositivos móviles con la administración de dispositivos móviles (MDM)](windows-enroll.md) o como equipos con el software cliente de Intune. Microsoft recomienda que los clientes [usen la solución de administración de MDM](windows-enroll.md) siempre que sea posible. Cuando se administra de esta manera, no se admite BranchCache. Para más información, consulte [Comparación de la administración de equipos con Windows como dispositivos móviles o equipos](pc-management-comparison.md).


## <a name="next-steps"></a>Pasos siguientes

[Revise los puntos de conexión de Intune](intune-endpoints.md).

