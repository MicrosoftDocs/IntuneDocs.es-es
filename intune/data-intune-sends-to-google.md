---
title: Datos que Intune manda a Google
titleSuffix: Microsoft Intune
description: Lista de los datos que Intune envía a Google.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ed713e63b63b4eb4a2696e9fd53b39cb139b4115
ms.sourcegitcommit: 2162ed46d939b4a9b85fa4e7e9943f2fb5948f1e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
ms.locfileid: "31617282"
---
# <a name="data-intune-sends-to-google"></a>Datos que Intune manda a Google

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cuando se habilita la administración de dispositivos empresariales Android en un dispositivo, Microsoft Intune establece una conexión con Google y comparte información del usuario y el dispositivo con Google. Antes de que Microsoft Intune pueda establecer una conexión, debe crear una cuenta de Google.

En la tabla siguiente se enumeran los datos que Microsoft Intune envía a Google cuando está habilitada la administración de dispositivos en un dispositivo:


| Datos que se envían a Google | Detalles | Usada para | Ejemplo |
|:---:|:---:|:---:|:---:|
| EnterpriseId | Se originan en Google al enlazar la cuenta de Gmail con Intune. | Identificador principal que se usa para comunicarse entre Intune y Google.  Esta comunicación incluye la configuración de directivas, la administración de dispositivos y el enlace o desenlace de la empresa Android con Intune. | Identificador único, formato de ejemplo: LC04eik8a6 |
| Cuerpo de la directiva | Se origina en Intune cuando se guarda una nueva directiva de aplicación o configuración. | Aplicar directivas a los dispositivos. | Se trata de una colección de todos los valores configurados para una directiva de aplicación o configuración. Puede contener información del cliente si se proporciona como parte de una directiva, como nombres de red, nombres de aplicaciones y configuración específica de la aplicación. |
| Datos del dispositivo | Los dispositivos de escenarios de perfil de trabajo comienzan con la inscripción en Intune. Los dispositivos de escenarios de dispositivo administrado comienzan con la inscripción en Google. | La información de los datos del dispositivo se envía entre Intune y Google para realizar varias acciones como la aplicación de directivas, la administración del dispositivo y la creación de informes generales. | **Identificador único para representar el nombre del dispositivo.** Ejemplo: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**Identificador único para representar el nombre de usuario.** Ejemplo: Enterprises/LC04ebru7b/users/116838519924207449711<br>**Estado del dispositivo.** Ejemplos: activo, deshabilitado, aprovisionamiento.<br>**Estados de cumplimiento.** Ejemplos: configuración no admitida, faltan aplicaciones necesarias<br>**Información del software.** Ejemplos: versiones de software y nivel de revisión.<br>**Información de red.** Ejemplos: IMEI, MEID, WifiMacAddress<br>**Configuración del dispositivo.** Ejemplos: información sobre niveles de cifrado y si el dispositivo permite aplicaciones desconocidas.<br> Vea a continuación un ejemplo de un mensaje JSON. |
| newPassword | Se origina en Intune. | Restablecer la contraseña del dispositivo. | Cadena que representa una nueva contraseña. |
| Usuario de Google | Google | Administrar el perfil del trabajo para los escenarios de perfil de trabajo (BYOD). | Identificador único para representar la cuenta de Gmail vinculada. Ejemplo: 114223373813435875042 |
| Datos de programa | Se origina en Intune al guardar la directiva de aplicación. |  | Cadena de nombre de aplicación. Ejemplo: app:com.microsoft.windowsintune.companyportal |
| Cuenta de servicio de empresa | Se origina en Google tras la solicitud de Intune. | Se usa para la autenticación entre Intune y Google para transacciones relacionadas con este cliente. | Hay varias partes:<br> **Id. de empresa**: documentado anteriormente.<br>**UPN**: UPN generado usado en la autenticación en nombre del cliente.<br>Ejemplo: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**Clave**: blob codificado en Base64 usado en solicitudes de autenticación que se almacena cifrado en el servicio, pero este es el aspecto del blob:<br> Identificador único para representar la clave del cliente<br>Ejemplo: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |


Para dejar de usar la administración de dispositivos empresariales Android con Microsoft Intune y eliminar los datos, debe deshabilitar la administración de dispositivos empresariales Android de Microsoft Intune y también eliminar su cuenta de Google. Consulte en la cuenta de Google cómo realizar la administración de la cuenta.


