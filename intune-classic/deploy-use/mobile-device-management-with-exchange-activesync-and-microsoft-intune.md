---
title: Administración de dispositivos de Exchange ActiveSync
description: Administrar dispositivos móviles con la administración de Exchange ActiveSync (EAS) mediante Exchange Connector
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f5e9bd3dd2026096c323858fc7faa915895ed55d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="exchange-activesync-mobile-device-management-with-microsoft-intune"></a>Administración de dispositivos móviles de Exchange ActiveSync con Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Para que Microsoft Intune administre directamente los dispositivos móviles, los dispositivos se deben [inscribir en Intune](prerequisites-for-enrollment.md). Como alternativa, los administradores pueden habilitar una solución de administración más limitada que use la administración de Exchange ActiveSync (EAS) con Exchange Connector. Los dispositivos se pueden administrar con servidores Exchange locales o con Exchange Online mediante Office 365. Intune solo admite una conexión de Exchange Connector de cualquier tipo por suscripción.

## <a name="exchange-access-rules-for-mobile-devices"></a>Reglas de acceso a Exchange para dispositivos móviles ##

Exchange necesita un conjunto de reglas que defina lo que sucede cuando los dispositivos móviles intentan conectarse a EAS. Estas reglas se administran en la consola de administración de Intune.

[Reglas de acceso a Exchange para dispositivos móviles](exchange-access-rules-for-mobile-devices.md)

## <a name="install-the-exchange-connector"></a>Instalar Exchange Connector
Exchange Connector le permite administrar la implementación de Exchange desde la consola de Intune. Primero debe instalar y configurar el conector Intune-Exchange adecuado. Elija la opción adecuada en función de si el servidor de Exchange es local o está hospedado como servicio en la nube:

-   [Configurar Intune para Exchange Online o los nuevos entornos de Exchange Online dedicado](intune-service-to-service-exchange-connector.md)
-   [Instalar el conector de Intune para servidores de Exchange locales y los entornos de Exchange Online dedicado heredados](intune-on-premises-exchange-connector.md)


## <a name="apply-policy-for-exchange-managed-mobile-devices"></a>Aplicar la directiva para dispositivos móviles administrados por Exchange
La consola de Intune se puede usar para administrar [la configuración de directiva EAS](exchange-activesync-policy-settings-in-microsoft-intune.md) y [restringir el acceso a recursos de la empresa](restrict-access-to-email-and-o365-services-with-microsoft-intune.md). Para obtener una lista de las configuraciones de directivas y las características de Exchange ActiveSync admitidas por dispositivos móviles específicos, vea [Exchange ActiveSync Client Comparison Table (Tabla de comparación de clientes de Exchange ActiveSync)](http://go.microsoft.com/fwlink/?LinkId=247270).

> [!NOTE]
> Al conectar Intune a un entorno de Microsoft Exchange, la directiva de EAS de todos los usuarios administrados con Intune se restablecerá a la directiva predeterminada actual en el servidor de Microsoft Exchange, a menos que haya una directiva más específica definida en Intune.

## <a name="wipe-company-data-from-mobile-devices"></a>Borrar los datos de la empresa de los dispositivos móviles
Por último, puede [borrar los datos de la empresa de los dispositivos móviles administrados por EAS](wipe-for-exchange-managed-mobile-devices.md) cuando ya no se usen o en caso de robo o pérdida del dispositivo.
