---
title: Eliminación de dispositivos móviles administrados por Exchange
description: Microsoft Intune permite borrar datos o restablecer dispositivos móviles administrados mediante Exchange ActiveSync (EAS) con Intune Exchange Connector
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 753e5e9dac7199dff18d110808524f05aa669036
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Wipe for Exchange-managed mobile devices

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune permite borrar datos o restablecer dispositivos móviles administrados mediante Exchange ActiveSync (EAS) con Intune Exchange Connector. En la tabla siguiente se describen las funcionalidades de borrado de datos mediante Exchange ActiveSync:


|      Tipo de borrado de datos       |              Windows 8.1 y Windows RT 8.1              |                            iOS                             |                          Android                          |
|-------------------------|----------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|        Borrar todos los datos        |          Permite quitar cuentas de correo y correo almacenado en caché.           |                      Restablecimiento de la configuración de fábrica.                       |                      Restablecimiento de la configuración de fábrica.                       |
|  Borrado selectivo/correo electrónico   |                  Quita cuentas de correo electrónico.                  |                       No compatible.                       |                      No compatible.                       |
| Borrado selectivo/directivas | Se quita el cumplimiento de directivas, pero no se cambia la configuración | Se quita el cumplimiento de directivas, pero no se cambia la configuración. | Se quita el cumplimiento de directivas, pero no se cambia la configuración. |

