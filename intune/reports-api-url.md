---
title: Punto de conexión de la API de Almacenamiento de datos de Intune
titlesuffix: Microsoft Intune
description: En este tema de referencia se describe la estructura de la dirección URL de la API de almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d552ec61d148d0489dc263405eac52448c10f9ef
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2018
ms.locfileid: "49642916"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Punto de conexión de la API de Almacenamiento de datos de Intune

Puede usar la API de Almacenamiento de datos de Intune con una cuenta con controles de acceso basados en roles específicos y credenciales de Azure AD. Después, autorizará al cliente REST con Azure AD mediante OAuth 2.0 y, por último, formará una dirección URL significativa para llamar a un recurso de almacenamiento de datos.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Autorización

Azure Active Directory (Azure AD) usa OAuth 2.0 para permitir autorizar el acceso a aplicaciones web y API web en el inquilino de Azure AD. En esta guía independiente del idioma se describe cómo enviar y recibir mensajes HTTP sin usar ninguna biblioteca de código abierto. El flujo del código de autorización de OAuth 2.0 se describe en la [sección 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) de la especificación de OAuth 2.0.

Para obtener más información, vea [Autorización del acceso a aplicaciones web mediante OAuth 2.0 y Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>Estructura de la dirección URL de la API

Los puntos de conexión de la API de Almacenamiento de datos leen las entidades de cada conjunto. La API admite un verbo HTTP **GET** y un subconjunto de opciones de consulta.

La dirección URL de Intune usa el formato siguiente:  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> En la dirección URL anterior, reemplace `{location}`, `{entity-collection}` y `{api-version}` según los detalles proporcionados en la tabla siguiente.

La dirección URL contiene los elementos siguientes:

| Elemento | Ejemplo | Descripción |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| ubicación | msua06 | Para localizar la URL base, vea la hoja de la API de Almacenamiento de datos en Azure Portal. |
| entity-collection | fechas | Nombre de la colección de entidades OData. Para obtener más información sobre las colecciones y las entidades del modelo de datos, vea [Data Model](reports-ref-data-model.md) (Modelo de datos). |
| api-version | beta | "Version" hace referencia a la versión de la API a la que se va a tener acceso. Para obtener más información, vea [Version](#API-version-information) (Versión). |
| maxhistorydays | 7 | (Opcional) Número máximo de días del historial que se va a recuperar. Este parámetro se puede proporcionar a cualquier colección, pero solo tendrá efecto en las colecciones que incluyan `dateKey` como parte de su propiedad de clave. Vea [Filtros de intervalo de DateKey](reports-api-url.md#datekey-range-filters) para obtener más información. |

## <a name="api-version-information"></a>Información de versión de la API

La versión actual de la API es `beta`. 

## <a name="odata-query-options"></a>Opciones de consulta OData

La versión actual admite los siguientes parámetros de consulta OData: `$filter, $orderby, $select, $skip,` y `$top`.

## <a name="datekey-range-filters"></a>Filtros de intervalo de DateKey

Los filtros de intervalo de `DateKey` se pueden usar para limitar la cantidad de datos que se descargan para algunas de las colecciones con `dateKey` como una propiedad de clave. El filtro `DateKey` se puede usar para optimizar el rendimiento del servicio si se proporciona el parámetro de consulta `$filter` siguiente:

1.  `DateKey` solo en `$filter`, para admitir los operadores `lt/le/eq/ge/gt` y la combinación con el operador lógico `and`, donde se pueden asignar a una fecha de inicio o de finalización.
2.  `maxhistorydays` se proporciona como opción de consulta personalizada.<br>

## <a name="filter-examples"></a>Ejemplos de filtro

> [!NOTE]
> En los ejemplos de filtro se supone que hoy es 21/2/2018.

|                             Filtro                             |           Optimización del rendimiento           |                                          Descripción                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Todas                                      |    Devolver datos con `DateKey` entre 20180214 y 20180221.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Todas                                      |    Devolver datos con `DateKey` igual a 20180214.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Todas                                      |    Devolver datos con `DateKey` entre 20180214 y 20180220.                                     |
|    `maxhistorydays=7&$filter=Id gt 1`                            |    Parcial, el identificador gt 1 no se optimizará    |    Devolver datos con `DateKey` entre 20180214 y 20180221, y el identificador mayor que 1.             |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Todas                                      |    Devolver datos con `DateKey` igual a 20180214. `maxhistorydays` se omite.                            |
|    `$filter=DateKey eq 20180214 and Id gt 1`                     |    Ninguno                                      |    No se trata como filtro de intervalo de `DateKey`, por lo que no hay aumento del rendimiento.                              |
|    `$filter=DateKey ne 20180214`                                 |    Ninguno                                      |    No se trata como filtro de intervalo de `DateKey`, por lo que no hay aumento del rendimiento.                              |
|    `maxhistorydays=7&$filter=DateKey eq 20180214 and Id gt 1`    |    Ninguno                                      |    No se trata como filtro de intervalo de `DateKey`, por lo que no hay aumento del rendimiento. `maxhistorydays` se omite.    |
