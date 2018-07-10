---
title: Procesamiento y almacenamiento de datos en Intune
description: Obtenga más información sobre cómo se almacenan y procesan los datos personales en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5f7c24775f03011bd936b22e41cfd318e92b5d64
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34474656"
---
# <a name="data-storage-and-processing-in-intune"></a>Procesamiento y almacenamiento de datos en Intune

Después de que Intune [recopile los datos](privacy-data-collect.md), el almacenamiento y procesamiento de estos se realiza como se detalla a continuación.

## <a name="storing-personal-data"></a>Almacenamiento de los datos personales

Todos los datos recopilados que no sean de telemetría se procesan mediante el servicio de Intune y se almacenan en una o varias de las siguientes ubicaciones de almacenamiento: 

- SQLAzure 
- Reliable Collections (Service Fabric)  
- Almacenamiento de Azure 

Se envía la telemetría (registros de servicio, registros de rendimiento, errores, etc.) que es clave para supervisar y proporcionar un servicio estable a almacenes de datos de telemetría de Microsoft.

### <a name="storage-locations"></a>Ubicaciones de almacenamiento

Microsoft ofrece y opera los servicios de Intune en muchas regiones en todo el mundo. Intune respeta las decisiones relativas a la ubicación de almacenamiento de los datos del cliente que tome el administrador.

Para obtener más información, vea [Microsoft Intune Where is my customer data?](For more information, see Microsoft Intune Where is my customer data?) (Microsoft Intune: ¿dónde están los datos de mi cliente?).

### <a name="personal-data-retention"></a>Retención de datos personales

En general, Intune conserva los datos personales hasta treinta días después de quitar al usuario de la administración de Intune.

Los datos de telemetría recopilados como parte del uso de Intune se conservan durante un máximo de treinta días.

Los registros de auditoría se conservan hasta un máximo de un año.

## <a name="processing-personal-data"></a>Procesamiento de datos personales

Intune procesa los datos personales con sistemas con certificación ISO. Para obtener más información, vea el [Portal de confianza de servicios](https://www.microsoft.com/en-us/TrustCenter/stp).

### <a name="profiling-and-marketing"></a>Generación de perfiles y marketing

Microsoft Intune no usa ningún dato personal recopilado para prestar servicios de generación de perfiles o con fines comerciales. 

### <a name="restrict-processing-of-personal-data"></a>Restricción del procesamiento de datos personales

Para restringir el procesamiento de los datos personales de un usuario, puede eliminar la cuenta de dicho usuario mediante los procesos siguientes:
1. Exportación de una copia electrónica de los datos personales del usuario, incluidos
    - cuentas
    - los datos del servicio
    - y los registros asociados.
2. Eliminación de la cuenta del usuario y los datos asociados de Intune.

## <a name="next-steps"></a>Pasos siguientes

Obtenga más información sobre cómo Intune [protege y comparte](privacy-data-secure-share.md) los datos personales. 