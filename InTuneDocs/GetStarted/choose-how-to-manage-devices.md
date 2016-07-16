---
title: "Elegir cómo administrar dispositivos | Microsoft Intune"
description: 
keywords: 
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: c9b34408e4af34dafc700d016304a6d29c2e8585


---

# Elegir cómo administrar dispositivos
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] permite administrar una variedad de dispositivos si se *inscriben* en el servicio. Así, los usuarios pueden usar un *portal de la empresa* para realizar diversas operaciones, como inscribir sus dispositivos, examinar e instalar aplicaciones, garantizar que los dispositivos cumplen con las directivas de la empresa y ponerse en contacto con el equipo de TI.

## Formas de administrar dispositivos móviles
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] puede administrar las siguientes plataformas de dispositivo:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Sugerencia</h5>
  <p>Si ya tiene inscritos dispositivos en los que se ejecuta una versión de iOS anterior a la versión compatible indicada arriba, seguirán estando inscritos. De todas formas, consulte la documentación correspondiente a cada [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para asegurarse de que la versión de iOS es compatible con la característica.</p>
</div>

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] puede administrar los dispositivos de los usuarios, popularmente conocidos como "Bring Your Own Device" (BYOD). También puede administrar dispositivos de empresa, incluidos los escenarios donde la empresa proporciona una lista de dispositivos que los usuarios pueden elegir, conocidos como "Choose Your Own Device" (CYOD).

### Inscripción de dispositivos en la administración
Siempre se deben inscribir los sistemas operativos de dispositivos móviles, como iOS, Android y Windows Phone. Pero el modo en que lo haga dependerá de las necesidades de su organización:

|Tipo de inscripción|BYOD|CYOD|Dispositivo compartido con cuenta de administrador|Dispositivo compartido sin una cuenta de usuario|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**Descripción**|Dispositivo personal inscrito mediante Microsoft Intune|Dispositivo propiedad de la organización para un solo usuario|Dispositivo propiedad de la organización que se administra con una cuenta de administrador y se comparte entre varios usuarios.|Dispositivo sin usuario propiedad de la organización utilizado por muchos usuarios.|
|**Usuario del dispositivo**|Propietario|Usuario asignado|Ninguna cuenta específica del usuario|Ningún usuario específico|
|**¿Quién lo inscribe?**|Propietario|Administrador|Administrador de dispositivos|Cualquiera|
|**¿Quién anula la inscripción?**|Propietario o administrador|Administrador|Administrador|Administrador|
|**¿Quién puede restablecerlo?**|Propietario o administrador|Administrador|Administrador|Administrador|

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Sugerencia</h5>
  <p>Consulte [Capacidades de administración de dispositivos móviles](mobile-device-management-capabilities-in-microsoft-intune.md) para ver una lista completa de las capacidades que se obtienen al inscribir dispositivos.</p>
</div>



## Formas de administrar PC Windows
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] puede administrar PC Windows con Windows Vista en adelante por medio del cliente de equipos de Intune. Pero, en el caso de los PC Windows, puede elegir entre inscribirlos o instalar el software cliente de equipo de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] que reporta algunas funciones que no se obtienen con la inscripción de dispositivos. En la mayoría de los escenarios,se inscribirá el dispositivo Windows con Intune, lo que proporciona un mayor número de funciones que el cliente de equipo.

Sopese la posibilidad de usar el cliente de equipo de Intune cuando quiera hacer lo siguiente:
<ul>
<li>Usar alguna de las funciones habilitadas por el cliente de equipo de Microsoft Intune para administrar los PC Windows.</li>
<li>Administrar un PC Windows que ejecuta un sistema operativo que no admite inscripciones.</li>
</ul>

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Sugerencia</h5>
  <p>Consulte [Windows PC management capabilities](windows-pc-management-capabilities-in-microsoft-intune.md) (Capacidades de administración de PC Windows) para ver una lista completa de las capacidades que se obtienen al instalar el cliente de equipo de Intune en PC Windows compatibles.</p>
</div>

## Administración de Exchange ActiveSync
Los dispositivos también se pueden administrar con Exchange ActiveSync. Para ello, es necesario instalar On-Premises Connector o usar Service to Service Connector integrado para conectarse a su servidor Exchange Server.

Para obtener más información sobre los requisitos de hardware y software para instalar On-Premises Connector, vea [Requisitos para On-Premises Connector](/intune/deploy-use/intune-on-premises-exchange-connector#requirements-for-the-on-premises-connect).

Para obtener más información sobre cómo usar On-Premises Connector o Service to Service Connector con Exchange, vea [Administración de dispositivos móviles con Exchange ActiveSync y Microsoft Intune](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune).



## Pasos siguientes
Ahora ya conoce algunas de las capacidades que se pueden usar al inscribir dispositivos con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. A continuación, deberá [inscribir los dispositivos](/intune/deploy-use/enroll-devices-in-microsoft-intune). Tras inscribirlos, podrá beneficiarse de todas las capacidades que hemos visto en este tema. <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->



<!--HONumber=Jun16_HO4-->


