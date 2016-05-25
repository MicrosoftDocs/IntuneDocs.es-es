---
# required metadata

title: Uso de ancho de banda de red de Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Uso de ancho de banda de red de Intune

Antes de configurar [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)], repase este tema y los requisitos que aparecen en [What to know before you start Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md) (Información necesaria antes de iniciar Microsoft Intune)..

Utilice la información de las siguientes secciones para planear el tráfico de red para los clientes de [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)].

## Tráfico de red medio
La tabla siguiente muestra el tamaño aproximado y la frecuencia de contenido común que pasa a través de la red de cada cliente.

> [!NOTE]
> Para asegurarse de que los equipos y dispositivos móviles reciban las actualizaciones necesarias y contenido del servicio de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], se deben conectar periódicamente a Internet. El tiempo que se tarda en recibir actualizaciones o contenido varía, pero como norma, se debe permanecer conectado de forma continua a Internet como mínimo una hora al día.

|Tipo de contenido|Tamaño aproximado|Frecuencia y detalles|
|----------------|--------------------|-------------------------|
|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] instalación de cliente<br /><br />**Los requisitos siguientes son adicionales a la instalación de cliente de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]**|125 MB|**Una vez**<br /><br />El tamaño de la descarga de cliente varía dependiendo del sistema operativo del equipo cliente.|
|Paquete de inscripción de cliente|15 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Agente de Endpoint Protection|65 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Agente de Operations Manager|11 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Agente de directivas|3 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Asistencia remota a través de agente de Microsoft Easy Assist|6 MB|**Una vez**<br /><br />Las descargas adicionales son posibles cuando hay actualizaciones para este tipo de contenido.|
|Operaciones diarias de cliente|6 MB|**A diario**<br /><br />El cliente de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] se comunica regularmente con el servicio de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para comprobar actualizaciones y directivas, y para notificar el estado del cliente al servicio.|
|Actualizaciones de definiciones de malware de Endpoint Protection|Variable<br /><br />Normalmente, de 40 KB a 2 MB|**A diario**<br /><br />Hasta tres veces al día.|
|Actualización del motor de Endpoint Protection|5 MB|**Mensual**|
|Actualizaciones de software|Variable<br /><br />El tamaño depende de las actualizaciones que implementa.|**Mensual**<br /><br />Normalmente, las actualizaciones de software se publican el segundo martes de cada mes.<br /><br />Un equipo recién inscrito o implementado puede utilizar más ancho de banda de red mientras se descarga el conjunto completo de actualizaciones publicadas anteriormente.|
|Service Packs|Variable<br /><br />El tamaño varía para cada Service Pack implementado.|**Variable**<br /><br />Depende de cuándo se implementan los Service Packs.|
|Distribución de software|Variable<br /><br />El tamaño depende del software implementado.|**Variable**<br /><br />Depende de cuándo se implementa el software.|

## Formas de reducir el uso de ancho de banda de red
Puede usar los métodos siguientes para reducir el uso de ancho de banda de red de clientes de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

### Utilizar un servidor proxy para almacenar en caché solicitudes de contenido
Puede utilizar un servidor proxy que pueda almacenar en caché contenido para reducir la duplicación de descargas y el uso de ancho de banda de red por parte de clientes que solicitan contenido de Internet.

Un servidor proxy de almacenamiento en caché recibe solicitudes de contenido de equipos cliente de su red, recupera ese contenido de Internet y puede almacenar en caché las respuestas HTTP y las descargas binarias. El servidor utiliza la información almacenada en caché para responder las solicitudes posteriores de equipos cliente de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

A continuación, se indica la configuración típica que se utiliza para un servidor proxy que almacena en caché contenido para clientes de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

|Configuración|Valor recomendado|Detalles|
|-----------|---------------------|-----------|
|Tamaño de caché|De 5 a 30 GB|El valor varía según el número de equipos cliente en la red y las configuraciones que se utilizan. Para evitar que los archivos se eliminen demasiado pronto, ajuste el tamaño de la caché para su entorno.|
|Tamaño de archivo de caché individual|950 MB|Es posible que esta opción no esté disponible en todos los servidores proxy de almacenamiento en caché.|
|Tipos de objetos que se almacenarán en caché|HTTP<br /><br />HTTPS<br /><br />BITS|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] son archivos CAB recuperados por el servicio de transferencia inteligente en segundo plano (BITS) descargados a través de HTTP.|
Para obtener información sobre el uso de un servidor proxy para almacenar contenido en caché, consulte la documentación de la solución de servidor proxy.

### Usar Servicio de transferencia inteligente en segundo plano en los equipos
[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] admite el uso del Servicio de transferencia inteligente en segundo plano en un equipo Windows para reducir el ancho de banda de red usado durante las horas configuradas. Puede configurar la directiva para BITS en la página **Ancho de banda de red** de la directiva de agente de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Para obtener más información sobre BITS y equipos Windows, consulte [Servicio de transferencia inteligente en segundo plano](http://technet.microsoft.com/library/bb968799.aspx) en la biblioteca TechNet.

### Usar BranchCache en los equipos
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] pueden utilizar BranchCache para reducir el tráfico de la red de área extensa (WAN). Los siguientes sistemas operativos admitidos como clientes también admiten BranchCache:

-   [!INCLUDE[nextref_client_7](../includes/nextref_client_7_md.md)]

-   [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]

-   [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)]

Para usar BranchCache, el equipo cliente debe tener BranchCache habilitado y configurarse para el **modo Caché distribuida**..

De forma predeterminada, BranchCache y el modo de caché distribuida se habilitan en un equipo cuando se instala el cliente de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Sin embargo, si el cliente ya tiene una directiva de grupo que deshabilita BranchCache, [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] no invalida esa directiva y BranchCache permanecerá deshabilitado en ese equipo.

Si utiliza BranchCache, debe comunicarse con los demás administradores de su organización que administren la directiva de grupo y la directiva de Firewall de [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] para asegurarse de que no implementan la directiva que deshabilita las excepciones de Firewall o BranchCache. Para obtener información sobre BranchCache, consulte [Información general sobre BranchCache](http://technet.microsoft.com/library/hh831696.aspx)..

### Consulte también
[What to know before you start Microsoft Intune (Información necesaria antes de iniciar Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)

<!--HONumber=May16_HO1-->


