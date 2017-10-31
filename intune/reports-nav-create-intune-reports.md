---
title: Usar el Almacenamiento de datos de Intune | Microsoft Docs
description: "Use el Almacenamiento de datos de Intune para generar informes que proporcionen una visión general del entorno móvil de la empresa."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e399c36d4c6a855766ee956b3ca24c503a1f974b
ms.sourcegitcommit: e57512698a479df0d25ece6ece4492ec0e4f0f3e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2017
---
# <a name="use-the-intune-data-warehouse"></a>Usar el Almacenamiento de datos de Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use el Almacenamiento de datos de Intune para generar informes que proporcionen una visión general del entorno móvil de la empresa. Por ejemplo, algunos de los informes incluyen:
-   Tendencia de los usuarios que se inscriben en Intune para que pueda optimizar las compras de licencias.
-   Desglose de las versiones de las aplicaciones y del sistema operativo para que pueda revisar el estado de los dispositivos móviles.
-   Tendencias de inscripción y cumplimiento de dispositivos para que pueda aplicar fácilmente actualizaciones de directivas.

El Almacenamiento de datos proporciona acceso a más información sobre el entorno móvil que Azure Portal. Con el Almacenamiento de datos de Intune puede tener acceso a lo siguiente:

  -  Datos históricos de Intune
  -  Datos actualizados diariamente
  -  Un modelo de datos mediante el estándar OData

> [!Important]  
> Puede probar las funciones más recientes del Almacenamiento de datos mediante la versión beta. Para usar la versión beta, la dirección URL debe contener el parámetro de consulta `api-version=beta`. La versión beta permite usar ciertas características antes de que estén disponibles con carácter general como servicio admitido. A medida que Intune agrega nuevas características, la versión beta puede cambiar el comportamiento y los contratos de datos. El código personalizado o las herramientas de informes que dependan de la versión beta podrían degradarse con las actualizaciones continuas. <!-- If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

**Pasos siguientes**

- Obtenga un vínculo y use Power BI para aprender más. Para obtener instrucciones, vea [Connect to the Intune Data Warehouse with Power BI](reports-proc-get-a-link-powerbi.md) (Conectarse al Almacenamiento de datos de Intune con Power BI).
- Con el enlace, podrá crear un informe personalizado con Power BI. Para obtener instrucciones, consulte [Crear un informe desde la fuente OData con Power BI](reports-proc-create-with-odata.md).
- Obtenga más información sobre la API de Almacenamiento de datos de Intune, el modelo de datos y las relaciones entre las entidades<!-- , and an example of creating a custom client to retrieve data,--> en [Intune Data Warehouse API](reports-nav-intune-data-warehouse.md) (API de Almacenamiento de datos de Intune).