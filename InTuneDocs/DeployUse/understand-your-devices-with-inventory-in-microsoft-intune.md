---
title: Comprender el funcionamiento de sus dispositivos mediante el inventario| Microsoft Intune
description: "Usar Intune para ver información sobre el hardware de los dispositivos que administra."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/17/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: df4e0bc8a818f22d6f7327f9f1348f67882e0c49
ms.openlocfilehash: 80b157c021099513854b8ffc1fe09cd2922ee0c2


---

# Comprender el funcionamiento de sus dispositivos mediante el inventario en Microsoft Intune
Microsoft Intune permite ver el inventario de los dispositivos inscritos y los equipos de Windows que ejecutan el software de cliente de Intune.

## ¿Qué información se recopila de los dispositivos inscritos?
Para ver el inventario que recopilan los dispositivos móviles, ejecute la opción [Informes de inventario de dispositivos móviles](understand-microsoft-intune-operations-by-using-reports.md). Intune recopila el siguiente inventario de los dispositivos móviles:

|Propiedad|Recopilado por|
|------------|-----------------------|
|**Nombre**|Todos los dispositivos|
|**Sistema operativo**|Todos los dispositivos|
|**Fabricante**|Todos los dispositivos|
|**Modelo**|Todos los dispositivos|
|**Canal de administración**|Todos los dispositivos|
|**Registrado en AAD**|Todos los dispositivos excepto Mac OS X|
|**Conforme**|Todos los dispositivos|
|**EAS activado**|Todos los dispositivos excepto Mac OS X|
|**Id. de activación de EAS**|Todos los dispositivos excepto Mac OS X|
|**Hora de activación de EAS**|Todos los dispositivos excepto Mac OS X|
|**Estado de administración**|Todos los dispositivos|
|**Dirección de correo electrónico**|Todos los dispositivos|
|**Id. de Exchange ActiveSync**|Todos los dispositivos|
|**Liberado o modificado**|Solo dispositivos iOS y Android|
|**Id. de dispositivo único**|Todos los dispositivos excepto Exchange ActiveSync|
|**Número de serie**|Dispositivos iOS, Mac OS X, Android, Windows 8.1 y Windows 10|
|**Espacio de almacenamiento total**|Dispositivos iOS, Mac OS X, Windows 8.1 y Windows 10|
|**Espacio de almacenamiento libre**|Dispositivos iOS, Mac OS X, Windows 8.1 y Windows 10|
|**Número de teléfono**<br>Los teléfonos que se clasifican como corporativos se identifican con el número de teléfono completo (por ejemplo, al ejecutar un informe de inventario de dispositivos móviles). Los números de teléfono BYOD se enmascaran con &#42; y solo se muestran los últimos cuatro dígitos.|Dispositivos iOS, Android y Windows Phone|
|**IMEI**|Dispositivos Exchange ActiveSync, iOS, Android y Windows Phone|
|**MEID**<br>Identificador de equipo móvil|Solo dispositivos iOS|
|**MAC Wi-Fi**|Todos los dispositivos excepto Exchange ActiveSync|
|**Operador del suscriptor**|Solo dispositivos iOS y Android|
|**Tecnología de datos móviles**|Solo dispositivos iOS y Android|
|**Supervisado**|Solo dispositivos iOS|
|**Estado de bloqueo de activación**|Solo dispositivos iOS|
|**Fecha de inscripción**|Todos los dispositivos|
|**Última actualización**|Todos los dispositivos|
|**MAC Ethernet**|Solo dispositivos Mac OS X|
|**Bloqueo de activación habilitado**|Solo dispositivos iOS|
|**Cifrado habilitado**|Todos los dispositivos|

## ¿Qué información se recopila de los equipos PC con Windows?
> [!IMPORTANT]
> Esta sección solo se aplica a equipos de Windows que ejecutan el software de cliente de equipos de Windows Intune.

Para ver el inventario que recopilan los equipos PC con Windows, ejecute la opción [Informes de inventario de equipos](understand-microsoft-intune-operations-by-using-reports.md). Intune recopila el siguiente inventario de los equipos de Windows:

-   **Nombre**

-   **Tipo de chasis**

-   **Fabricante**

-   **Modelo**

-   **Sistema operativo**

-   **Versión de TPM**

-   **Espacio total en disco**

-   **Espacio en disco usado**

-   **Espacio libre en disco**

-   **Nombre de disco del sistema operativo**

-   **Espacio en disco del sistema operativo**

-   **Espacio libre en disco del sistema operativo**

-   **Memoria física**

-   **Nombre del procesador**

-   **Arquitectura del procesador**

-   **Velocidad de CPU**

-   **Dirección IP**

-   **Número de serie**

-   **Último usuario que inició sesión**

-   **Usuario asignado**

-   **Última actualización**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->



<!--HONumber=Aug16_HO3-->


