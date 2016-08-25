---
title: "Elegir cómo administrar dispositivos | Microsoft Intune"
description: "Obtenga información sobre las distintas formas en las que puede inscribir y administrar dispositivos."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c329bd08aaf72ae2acaa03dcb12c911d84b46b4e
ms.openlocfilehash: cfd9df3814d0d306a254a5566155a91ce5d0ca16


---

# Elegir cómo administrar dispositivos
Intune le permite administrar una variedad de dispositivos si se *inscriben* en el servicio. Así, los usuarios pueden usar un *portal de la empresa* para realizar diversas operaciones, como inscribir sus dispositivos, examinar e instalar aplicaciones, garantizar que los dispositivos cumplen con las directivas de la empresa y ponerse en contacto con el equipo de TI.

## Formas de administrar dispositivos móviles
Intune puede administrar las siguientes plataformas de dispositivo:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

> [!NOTE]
> Si ya tiene inscritos dispositivos que ejecutan una versión de iOS anterior a la versión compatible, los dispositivos seguirán estando inscritos. Consulte la documentación para confirmar si la característica es compatible con esa versión de iOS.

Intune puede administrar los dispositivos de los usuarios, popularmente conocidos como "Bring Your Own Device" (BYOD). También puede administrar dispositivos de empresa, incluidos los escenarios donde la empresa proporciona una lista de dispositivos que los usuarios pueden elegir, conocidos como "Choose Your Own Device" (CYOD).

### Inscripción de dispositivos en la administración
Siempre se deben inscribir los sistemas operativos de dispositivos móviles, como iOS, Android y Windows Phone. El modo en que inscriba los dispositivos dependerá de las necesidades de su organización:

|Tipo de inscripción|BYOD|CYOD|Dispositivo compartido con cuenta de administrador|Dispositivo compartido sin una cuenta de usuario|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**Descripción**|Dispositivo personal inscrito mediante Microsoft Intune|Dispositivo propiedad de la organización para un solo usuario|Dispositivo propiedad de la organización que se administra con una cuenta de administrador y se comparte entre varios usuarios.|Dispositivo sin usuario propiedad de la organización utilizado por muchos usuarios.|
|**Usuario del dispositivo**|Propietario|Usuario asignado|Ninguna cuenta específica del usuario|Ningún usuario específico|
|**¿Quién lo inscribe?**|Propietario|Administrador|Administrador de dispositivos|Cualquiera|
|**¿Quién anula la inscripción?**|Propietario o administrador|Plataforma |Administrador o usuario|Administrador o usuario|
|**¿Quién puede restablecerlo?**|Propietario o administrador|Administrador|Administrador|Administrador|

Para obtener más información, vea [Elegir cómo inscribir dispositivos móviles](/intune/get-started/choose-how-to-enroll-devices1).

> [!NOTE]
> Consulte [Capacidades de administración de dispositivos móviles](mobile-device-management-capabilities-in-microsoft-intune.md) para ver una lista completa de las capacidades que se obtienen al inscribir dispositivos.

## Formas de administrar PC Windows
Intune puede administrar equipos PC con Windows Vista y versiones posteriores con el cliente de equipos de Intune. Pero, en el caso de los equipos PC con Windows, puede elegir entre inscribirlos o instalar el software cliente de equipo de Intune, que ofrece algunas funcionalidades que no están disponibles al inscribir los dispositivos. En la mayoría de los escenarios,se inscribirá el dispositivo Windows con Intune, lo que proporciona un mayor número de funciones que el cliente de equipo.

Sopese la posibilidad de usar el cliente de equipo de Intune cuando quiera hacer lo siguiente:

- Usar alguna de las funcionalidades habilitadas por el cliente de equipo de Microsoft Intune para administrar los equipos PC con Windows
- Administrar un equipo PC con Windows que ejecuta un sistema operativo que no admite inscripciones

> [!NOTE]
> Consulte [Windows PC management capabilities](windows-pc-management-capabilities-in-microsoft-intune.md) (Capacidades de administración de PC Windows) para ver una lista completa de las capacidades que se obtienen al instalar el cliente de equipo de Intune en PC Windows compatibles.

## Administración de Exchange ActiveSync
Los dispositivos también se pueden administrar con Exchange ActiveSync. Para ello, es necesario instalar On-Premises Connector o usar Service to Service Connector integrado para conectarse a su servidor Exchange Server.

Para más información sobre los requisitos de hardware y software para instalar On-Premises Connector, consulte la sección [Requirements for the On-Premises Connector](/intune/deploy-use/intune-on-premises-exchange-connector#requirements-for-the-on-premises-connector) (Requisitos para On-Premises Connector).

Para obtener más información sobre cómo usar On-Premises Connector o Service to Service Connector con Exchange, vea [Administración de dispositivos móviles con Exchange ActiveSync y Microsoft Intune](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune).



## Pasos siguientes
Ahora ya conoce algunas de las capacidades que se pueden usar al inscribir dispositivos con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. A continuación, deberá [inscribir los dispositivos](/intune/deploy-use/enroll-devices-in-microsoft-intune). Tras inscribirlos, podrá beneficiarse de todas las capacidades que hemos visto en este tema. <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->



<!--HONumber=Aug16_HO3-->


