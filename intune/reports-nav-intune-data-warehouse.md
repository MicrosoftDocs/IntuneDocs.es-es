---
title: API de Almacenamiento de datos de Intune | Microsoft Docs
description: "Puede usar la API para generar informes que proporcionen una visión general del entorno móvil de la empresa."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 52b498beb024b86282c93be7aa5a248800db6609
ms.sourcegitcommit: 294de4d4058de2c625abb8143e90880d27da9284
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2017
---
#  <a name="intune-data-warehouse-api"></a>API de Almacenamiento de datos de Intune

La API de Almacenamiento de datos de Intune le permite obtener acceso a los datos de Intune en un formato legible para el equipo, de modo que pueda usarlos con la herramienta de análisis que prefiera. Puede usar la API para generar informes que proporcionen una visión general del entorno móvil de la empresa. La API usa el protocolo OData, que sigue patrones estándar para:

  -   Encabezados de solicitud y respuesta
  -   Códigos de estado
  -   Métodos HTTP
  -   Convenciones de direcciones URL
  -   Tipos de medios
  -   Formatos de carga
  -   Opciones de consulta

OData (Open Data Protocol) es un estándar de OASIS (Organization for the Advancement of Structured Information Standards) que define los procedimientos recomendados para compilar y usar API de RESTful. El Almacenamiento de datos de Intune usa OData versión 4.0.

Esta sección de referencia contiene información general sobre los puntos de conexión, los métodos HTTP admitidos, los formatos de la carga devuelta y la documentación del modelo de datos del Almacenamiento de datos de Intune.

> [!Important]  
> Puede probar las funciones más recientes del Almacenamiento de datos mediante la versión beta. Para usar la versión beta, la dirección URL debe contener el parámetro de consulta `api-version=beta`. La versión beta permite usar ciertas características antes de que estén disponibles con carácter general como servicio admitido. A medida que Intune agrega nuevas características, la versión beta puede cambiar el comportamiento y los contratos de datos. El código personalizado o las herramientas de informes que dependan de la versión beta podrían degradarse con las actualizaciones continuas. <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

## <a name="odata-custom-client"></a>Cliente personalizado de OData

Puede acceder al modelo de datos de almacenamiento de datos de Intune a través de puntos de conexión RESTful. Para obtener acceso a los datos, el cliente debe realizar la autorización con Microsoft Azure Active Directory (Azure AD) mediante OAuth 2.0. Configure una aplicación web y una aplicación cliente en Azure y conceda permisos al cliente. El cliente local obtendrá la autorización y, luego, podrá comunicarse con los puntos de conexión de almacenamiento de datos.

Para obtener más información, consulte [Get data from the Data Warehouse API with a REST client (Obtener datos de la API de almacenamiento de datos con un cliente de REST)](reports-proc-data-rest.md)

## <a name="interacting-with-the-api"></a>Interactuar con la API

La API requiere autorización con Azure AD. Azure AD usa OAuth 2.0. Una vez obtenida la autorización, para obtener datos de la API, use un verbo HTTP GET y póngase en contacto con las colecciones de entidades expuestas. Para obtener más información, consulte:

 -  [Autorización](reports-api-url.md)
 -  [Estructura de la dirección URL de la API](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Modelo de datos del Almacenamiento de datos de Intune

OData define un modelo de datos abstracto y un protocolo que permiten que todos los clientes tengan acceso a la información expuesta por cualquier origen de datos. El tema de documentación del modelo de datos contiene una explicación de los espacios de nombres, las entidades y los objetos devueltos en el modelo de datos del Almacenamiento de datos de Intune. Para más información, vea [Data Warehouse Data Model](reports-ref-data-model.md) (Modelo de datos del Almacenamiento de datos).

## <a name="next-steps"></a>Pasos siguientes

[Escenarios de autenticación para Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)  
[odata.org](http://www.odata.org)  
[OData versión 4.0](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  
