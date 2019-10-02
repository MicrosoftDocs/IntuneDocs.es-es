---
title: Datos que Google manda a Intune
titleSuffix: Microsoft Intune
description: Lista de los datos que Google envía a Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c675caea34f601bd49376c0523d83b010b5312a9
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722545"
---
# <a name="data-google-sends-to-intune"></a>Datos que Google manda a Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cuando se habilita la administración de dispositivos empresariales Android en un dispositivo, Microsoft Intune establece una conexión con Google y la información del usuario y del dispositivo se comparte entre Intune y Google. Antes de que Microsoft Intune pueda establecer una conexión, debe crear una cuenta de Google.

En la tabla siguiente se enumeran los datos que Google envía a Intune cuando está habilitada la administración de dispositivos en un dispositivo:


| Datos que Google manda a Intune | Detalles | Usada para | Ejemplo |
|:---:|:---:|:---:|:---:|
| Datos empresariales | Identificadores empresariales del cliente en Google. | Vincular la información del cliente entre Intune y Google. | Ejemplo de **enterpriseId**: LC04eik8a6.<br>**Nombre**. El nombre de administrador, tal y como se especificó al configurar Android Enterprise. Ejemplo: Joe Smith.<br>**Correo electrónico del administrador**. YourAdmin@gmail.com que se usó al configurar Android Enterprise. |
| Datos de aplicación | Datos para las aplicaciones administradas de Play Store. | Dirigir la aplicación a los usuarios o dispositivos como disponible o requerida. | Ejemplo de **nombre de aplicación**: aplicación de inventario de almacén de Contoso.<br>Ejemplo de **identificador único para representar la aplicación**: app:com.Contoso.Warehouse.InventoryTracking |
| Cuenta de servicio | Cuenta de servicio de Google interna y única para usarse con llamadas de clientes específicos. | Se usa para realizar llamadas en Google en el nombre del cliente (para ver las aplicaciones, los dispositivos, etc.) | Ejemplo de **nombre**: InternalAccount@InternalService.com.<br>Ejemplo de **claves**: ServiceAccountPassword |


Para dejar de usar la administración de dispositivos empresariales Android con Microsoft Intune y eliminar los datos, debe deshabilitar la administración de dispositivos empresariales Android de Microsoft Intune y también eliminar su cuenta de Google. Consulte en la cuenta de Google cómo realizar la administración de la cuenta.


