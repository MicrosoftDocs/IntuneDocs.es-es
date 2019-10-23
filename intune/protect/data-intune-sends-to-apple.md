---
title: Datos que Intune manda a Apple
titleSuffix: Microsoft Intune
description: Lista de los datos que Intune envía a Apple.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2f1be7a2457cca7da62883370c9e273168c6a29
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502429"
---
# <a name="data-intune-sends-to-apple"></a>Datos que Intune manda a Apple

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cuando se habilita cualquiera de los siguientes servicios de Apple en un dispositivo, Microsoft Intune establece una conexión con Apple y comparte información del usuario y el dispositivo con Apple: 

- [Programa de inscripción de dispositivos (DEP) de Apple](../enrollment/device-enrollment-program-enroll-ios.md)
- [Certificado push MDM de Apple (APNS)](../enrollment/apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Programa de Compras por Volumen de Apple (VPP)](../apps/vpp-apps-ios.md)

Para que Microsoft Intune pueda establecer una conexión, debe crear una cuenta de Apple para cada servicio de Apple.

En la tabla siguiente se muestran los datos que Microsoft Intune envía desde un dispositivo a los servicios habilitados de Apple. 

| Servicio | Datos que se envían a Apple | Usada para |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token, PushMagic | Si el servidor acepta el dispositivo, este proporciona su token de dispositivo de notificación push al servidor. El servidor debe usar este token para enviar mensajes push al dispositivo. Este mensaje de registro también contiene una cadena de PushMagic. El servidor debe recordar esta cadena e incluirla en cualquier mensaje push que envíe al dispositivo. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token de servidor | Token de dispositivo de notificación push usado para autenticar el servicio de Apple. |
| ASM/DEP | nombre_de_servidor | Nombre de identificación del servidor MDM. |
| ASM/DEP | server_uuid | Identificador del servidor generado por el sistema. |
| ASM/DEP | admin_id | ID de Apple de la persona que ha generado los tokens actuales que están en uso. |
| ASM/DEP | org_name | Nombre de la organización. |
| ASM/DEP | org_email | Dirección de correo electrónico de la organización. |
| ASM/DEP | org_phone | Teléfono de la organización. |
| ASM/DEP | org_address | Dirección de la organización. |
| ASM/DEP | org_id | Id. de cliente de DEP. Esta clave solo está disponible en la versión 3 del protocolo y versiones posteriores. |
| ASM/DEP | serial_number | Número de serie del dispositivo (cadena). |
| ASM/DEP | modelo | Nombre del modelo (cadena). |
| ASM/DEP | description | Descripción del dispositivo (cadena). |
| ASM/DEP | asset_tag | Etiqueta de activo del dispositivo (cadena). |
| ASM/DEP | profile_status | Estado de instalación del perfil. Los valores posibles son **vacío**, **asignado**, **insertado** o **eliminado**. |
| ASM/DEP | profile_uuid | Identificador único del perfil asignado. |
| ASM/DEP | device_assigned_by | Dirección de correo electrónico de la persona que ha asignado el dispositivo. |
| ASM/DEP | os | Sistema operativo del dispositivo: iOS, OSX o tvOS. Esta clave es válida en X-Server-Protocol-Version 2 y versiones posteriores. |
| ASM/DEP | device_family | Familia de productos de Apple del dispositivo: iPad, iPhone, iPod, Mac o AppleTV. Esta clave es válida en X-Server-Protocol-Version 2 y versiones posteriores. |
| ASM/DEP | profile_name | Cadena. Nombre legible para el perfil. |
| ASM/DEP | support_phone_number | Opcional. Cadena. Número de teléfono de soporte técnico de la organización. |
| ASM/DEP | support_email_address | Opcional. Cadena. Dirección de correo electrónico de soporte técnico de la organización. Esta clave es válida en X-Server-Protocol-Version 2 y versiones posteriores. |
| ASM/DEP | department | Opcional. Cadena. Nombre de la ubicación o el departamento definido por el usuario. |
| ASM/DEP | dispositivos | Matriz de cadenas que contienen números de serie de dispositivos. (Puede estar vacía). |
| VPP | Intune UserId guid | GUID generado por Intune. |
| VPP | Managed AppleId UPN | ID de Apple especificado por el administrador al configurar la conexión de token de VPP con Apple. |
| VPP | Número de serie | Número de serie del dispositivo administrado. |

Para dejar de usar los servicios de Apple con Microsoft Intune y eliminar los datos, debe deshabilitar la administración de token de Apple de Microsoft Intune y también eliminar su cuenta de Apple. Consulte en la cuenta de Apple cómo realizar la administración de la cuenta.


