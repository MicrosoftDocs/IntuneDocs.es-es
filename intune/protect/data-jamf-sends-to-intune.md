---
title: Datos que Jamf Pro envía a Intune
titleSuffix: Microsoft Intune
description: Revise la lista de datos que Jamf Pro envía a Microsoft Intune al integrar Jamf Pro para administrar equipos Mac con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4bf6df44335f3375d58d3c2c11da7cb3f982b3e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502422"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Datos que Jamf Pro envía a Intune

Cuando se usa [Jamf Pro](https://www.jamf.com) para administrar los equipos Mac de los usuarios finales con Intune, Jamf Pro captura información de inventario sobre los dispositivos macOS administrados. 

## <a name="data"></a>Datos  
Para obtener la lista de datos que Jamf Pro comparte con Intune, consulte [Apéndice: Información de inventario compartida con Microsoft Intune ](https://docs.jamf.com/technical-papers/jamf-pro/microsoft-intune/10.9.0/Appendix__Inventory_Information_Shared_with_Microsoft_Intune.html) en la documentación técnica de Jamf Pro. 

<!--  
Jamf Pro reports the following information to Intune:  

* Device Azure AD ID
* JAMF Inventory State (inventory state of a computer checked in with Jamf Pro within the last 24 hours)
* OS Version
* User Azure AD ID
* Encrypted (FileVault 2)
* Gatekeeper Status
* Password: minimum number of character sets
* Password expiration (days)
* Password Type - simple, alphanumeric, or unknown
* Prevent Auto Login
* Required Passcode Length
* Password: number of previous passwords to prevent reuse
* System Integrity Protection
* Last Check-In Time
* Architecture Type
* Available RAM Slots
* Battery Capacity
* Boot ROM
* Bus Speed
* Cache Size
* Device Name
* Domain Join
* Jamf ID
* MAC address
* Make
* Model
* Model Identifier
* NIC Speed
* Number of Cores
* Number of Processors
* OS
* Platform
* Processor Speed
* Processor Type
* Secondary MAC Address
* Serial Number
* SMC Version
* Total RAM
* UDID
* User Email
--> 

<!-- 
You can remove a Jamf-managed device from the Intune console by selecting **Delete** in the **All devices** view. Bulk device deletion can be enabled by selecting multiple devices and clicking **Delete**.
-->

## <a name="next-steps"></a>Pasos siguientes
Obtenga información sobre cómo [quitar un dispositivo administrado por Jamf en los documentos de Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). También puede presentar una incidencia de soporte técnico al [soporte técnico de Jamf](https://www.jamf.com/support/) para obtener más ayuda. 

