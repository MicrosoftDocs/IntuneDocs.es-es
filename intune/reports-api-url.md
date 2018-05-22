---
title: Punto de conexión de la API de Almacenamiento de datos de Intune
titlesuffix: Microsoft Intune
description: En este tema de referencia se describe la estructura de la dirección URL de la API de almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6f99ce2ae7937fe0b90353037e72f453a703dd8c
ms.sourcegitcommit: 49dc405bb26270392ac010d4729ec88dfe1b68e4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2018
---
# <a name="intune-data-warehouse-api-endpoint"></a>Punto de conexión de la API de Almacenamiento de datos de Intune

Puede usar la API de Almacenamiento de datos de Intune con una cuenta con controles de acceso basados en roles específicos y credenciales de Azure AD. Después, autorizará al cliente REST con Azure AD mediante OAuth 2.0 y, por último, formará una dirección URL significativa para llamar a un recurso de almacenamiento de datos.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Autorización

Azure Active Directory (Azure AD) usa OAuth 2.0 para permitir autorizar el acceso a aplicaciones web y API web en el inquilino de Azure AD. En esta guía independiente del idioma se describe cómo enviar y recibir mensajes HTTP sin usar ninguna de nuestras bibliotecas de código abierto. El flujo del código de autorización de OAuth 2.0 se describe en la [sección 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) de la especificación de OAuth 2.0.

Para obtener más información, vea [Autorización del acceso a aplicaciones web mediante OAuth 2.0 y Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>Estructura de la dirección URL de la API

Los puntos de conexión de la API de Almacenamiento de datos leen las entidades de cada conjunto. La API admite un verbo HTTP **GET** y un subconjunto de opciones de consulta.

La dirección URL de Intune usa el formato siguiente:  
`https://fef.{<strong><em>location</em></strong>}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{<strong><em>entity-collection</em></strong>}?api-version={<strong><em>api-version</em></strong>}`

La dirección URL contiene los elementos siguientes:

| Elemento | Ejemplo | Descripción |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| ubicación | msua06 | Para localizar la URL base, vea la hoja de la API de Almacenamiento de datos en Azure Portal. |
| entity-collection | fechas | Nombre de la colección de entidades OData. Para obtener más información sobre las colecciones y las entidades del modelo de datos, vea [Data Model](reports-ref-data-model.md) (Modelo de datos). |
| api-version | beta | "Version" hace referencia a la versión de la API a la que se va a tener acceso. Para obtener más información, vea [Version](#API-version-information) (Versión). |


## <a name="api-version-information"></a>Información de versión de la API

La versión actual de la API es `beta`. 

## <a name="odata-query-options"></a>Opciones de consulta OData

La versión actual admite los siguientes parámetros de consulta OData: `$filter, $orderby, $select, $skip,` y `$top`.
