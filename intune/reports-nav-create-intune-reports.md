---
title: Usar el Almacenamiento de datos de Intune
titlesuffix: Microsoft Intune
description: Use el Almacenamiento de datos de Intune para generar informes que proporcionen una visión general del entorno móvil de la empresa.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 13054bcaf885173e768fefb585cb71f266e9ca9e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184665"
---
# <a name="use-the-intune-data-warehouse"></a>Usar el Almacenamiento de datos de Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use el Almacenamiento de datos de Intune para generar informes que proporcionen una visión general del entorno móvil de la empresa. Por ejemplo, algunos de los informes incluyen:
-   Tendencia de los usuarios que se inscriben en Intune para que pueda optimizar las compras de licencias.
-   Desglose de las versiones de las aplicaciones y del sistema operativo para que pueda revisar el estado de los dispositivos móviles.
-   Tendencias de inscripción y cumplimiento de dispositivos para que pueda aplicar fácilmente actualizaciones de directivas.

El Almacenamiento de datos proporciona acceso a más información sobre el entorno móvil que Azure Portal. Con el Almacenamiento de datos de Intune puede tener acceso a lo siguiente:

  -  Datos históricos de Intune
  -  Datos actualizados diariamente
  -  Un modelo de datos mediante el estándar OData

> [!Note]
> Si usa administración híbrida de dispositivos móviles (MDM) con System Center Configuration Manager y Microsoft Intune, es aconsejable que recupere los datos de SCCM. El Almacenamiento de datos de Intune solo contiene datos de Intune. Puede usar un panel de Power BI de SCCM para los informes personalizados. Para más información, vea "[Announcing the Power BI solution template for System Center Configuration Manager]( https://powerbi.microsoft.com/blog/sccm-solution-template)" (Presentación de la plantilla de solución de Power BI para System Center Configuration Manager) y "[Contenido de Power BI para Dynamics 365](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/power-bi-home-page)".

> [!Important]  
> Ahora puede usar la versión v1.0 del almacenamiento de datos de Intune mediante la configuración del parámetro de consulta  `api-version=v1.0`. Las actualizaciones de las colecciones en el almacenamiento de datos son aditivas por naturaleza y no interrumpen los escenarios existentes.<br><br>
> Puede probar las funciones más recientes del Almacenamiento de datos mediante la versión beta. Para usar la versión beta, la dirección URL debe contener el parámetro de consulta  `api-version=beta`. La versión beta permite usar ciertas características antes de que estén disponibles con carácter general como servicio admitido. A medida que Intune agrega nuevas características, la versión beta puede cambiar el comportamiento y los contratos de datos. El código personalizado o las herramientas de informes que dependan de la versión beta podrían degradarse con las actualizaciones continuas.

**Pasos siguientes**

- Obtenga un vínculo y use Power BI para aprender más. Para obtener instrucciones, vea [Connect to the Intune Data Warehouse with Power BI](reports-proc-get-a-link-powerbi.md) (Conectarse al Almacenamiento de datos de Intune con Power BI).
- Con el enlace, podrá crear un informe personalizado con Power BI. Para obtener instrucciones, consulte [Crear un informe desde la fuente OData con Power BI](reports-proc-create-with-odata.md).
- Obtenga más información sobre la API de Almacenamiento de datos de Intune, el modelo de datos y las relaciones entre las entidades<!-- , and an example of creating a custom client to retrieve data,--> en [Intune Data Warehouse API](reports-nav-intune-data-warehouse.md) (API de Almacenamiento de datos de Intune).