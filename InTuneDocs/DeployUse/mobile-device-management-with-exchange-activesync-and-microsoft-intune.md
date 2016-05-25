---
# required metadata

title: Administración de dispositivos móviles con Exchange ActiveSync y Microsoft Intune | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Administración de dispositivos móviles con Exchange ActiveSync e Microsoft Intune
Para que Microsoft Intune administre directamente los dispositivos móviles, los usuarios tendrán que inscribirlos en Intune. Para los dispositivos móviles que los usuarios no hayan inscrito, se puede habilitar la administración de Exchange ActiveSync (EAS) mediante Exchange Connector. Los dispositivos se pueden administrar tanto en servidores Exchange locales como en Exchange hospedado en la nube Microsoft Office 365.

## Reglas de acceso a Exchange para dispositivos móviles ##

Exchange necesita un conjunto de reglas que defina lo que sucede cuando los dispositivos móviles intentan conectarse a EAS. Estas reglas se administran en la consola de administración de Intune.

[Reglas de acceso a Exchange para dispositivos móviles](exchange-access-rules-for-mobile-devices.md)

## Instalar Exchange Connector
Exchange Connector le permite administrar la implementación de Exchange desde la consola de Intune. Primero debe instalar y configurar el conector Intune-Exchange adecuado. Elija la opción adecuada en función de si el servidor de Exchange es local o está hospedado como servicio en la nube:

-   [Instalar el conector de Intune para Exchange local](intune-on-premises-exchange-connector.md)
-   [Configurar Intune Service to Service Connector para Hosted Exchange](intune-service-to-service-exchange-connector.md)

## Aplicar la directiva para dispositivos móviles administrados por Exchange
La configuración de directiva se puede aplicar mediante la consola de Intune; consulte [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md). Para obtener una lista de las configuraciones de directivas y las características de Exchange ActiveSync admitidas por dispositivos móviles específicos, consulte [Exchange ActiveSync Client Comparison Table](http://go.microsoft.com/fwlink/?LinkId=247270) (Tabla de comparación de clientes de Exchange ActiveSync)..

> [!NOTE]
> Al conectar Intune a un entorno de Microsoft Exchange, la directiva de EAS de todos los usuarios administrados con Intune se restablecerá a la directiva predeterminada actual en el servidor de Microsoft Exchange, a menos que haya una directiva más específica definida en Intune.

## Borrar los datos de la empresa de los dispositivos móviles
Por último, puede [borrar los datos de la empresa de los dispositivos móviles administrados por EAS](wipe-for-exchange-managed-mobile-devices.md) cuando ya no se usen o en caso de robo o pérdida del dispositivo.


<!--HONumber=May16_HO1-->


