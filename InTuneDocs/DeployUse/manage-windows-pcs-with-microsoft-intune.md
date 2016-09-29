---
title: Administrar PC con software cliente | Microsoft Intune
description: Administre equipos Windows instalando el software cliente de Intune.
keywords: 
author: nathbarn
manager: angrobe
ms.date: 08/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4cc8b7e34e8809eebd7fdec8ffac0599c96d309
ms.openlocfilehash: ce27fc737fdf47903d7554eb15f24f07b3524406


---

# Administración de PC con Windows con el software de cliente de PC de Intune
En lugar de [inscribir los PC con Windows como dispositivos móviles](set-up-windows-device-management-with-microsoft-intune.md), puede inscribir y administrar sus PC con Windows mediante la instalación del software de cliente de Intune.

Intune administra equipos Windows mediante directivas, del mismo modo que los objetos de directiva de grupo (GPO) de los Servicios de dominio de Active Directory (AD DS) de Windows Server. Si va a administrar equipos unidos a un dominio de Active Directory con Intune, debe [asegurarse de que las directivas de Intune no entren en conflicto con ningún GPO](resolve-gpo-and-microsoft-intune-policy-conflicts.md) configurado para la organización.

Aunque el cliente de software de Intune admite [capacidades de administración que ayudan a proteger los PC](policies-to-protect-windows-pcs-in-microsoft-intune.md) mediante la administración de actualizaciones de software, Firewall de Windows y Endpoint Protection, los PC administrados con el cliente de software de Intune no pueden ser objeto de otras directivas de Intune, incluida la configuración de directiva de **Windows** específica de la administración de dispositivos móviles.

> [!NOTE]
> Los dispositivos que ejecutan Windows 8.1 o versiones posteriores se pueden administrar con el cliente de Intune o como dispositivos móviles. Este tema se aplica a los equipos que ejecutan el cliente de software de Intune. No se admite la instalación del cliente de Intune ni la inscripción en la administración de dispositivos móviles.

## Requisitos para la administración de clientes de PC de Intune

**Hardware**: los siguientes son los requisitos mínimos de hardware para instalar el cliente de Intune:

|Requisito|Más información|
|---------------|--------------------|
|Red|El cliente requiere que el equipo tenga conectividad a Internet.|
|Procesador y memoria|Consulte los requisitos de RAM y procesador para el sistema operativo del equipo.|
|Espacio en disco|200 MB de espacio disponible en el disco antes de que se instale el software cliente.|

**Software**: los siguientes son los requisitos de software para instalar el cliente:

|Requisito|Más información|
|---------------|--------------------|
|Sistema operativo | Dispositivo Windows con Windows Vista o posterior. No se admiten las versiones Home Edition.|
|Permisos administrativos|La cuenta que instala el software cliente debe tener permisos de administrador local en ese dispositivo.|
|Windows Installer 3.1|El equipo debe tener, como mínimo, Windows Installer 3.1.<br /><br />Para ver la versión de Windows Installer de un equipo:<br /><br />-   En el equipo, haga clic con el botón derecho en **%windir%\System32\msiexec.exe** y, luego, haga clic en **Propiedades**.<br /><br />Puede descargar la última versión de Windows Installer desde [Windows Installer Redistributables (Paquetes redistribuibles de Windows Installer)](http://go.microsoft.com/fwlink/?LinkID=234258) en el sitio web de Microsoft Developer Network.|
|Quitar software cliente incompatible|Antes de instalar el software cliente de Intune, debe desinstalar cualquier software cliente de Configuration Manager o Systems Management Server que esté instalado en ese equipo.|

## Administración de equipos con el cliente de equipos de Intune
Una vez instalado el cliente de software de Intune, estas son algunas de las funciones de administración incluidas: [administración de aplicaciones](deploy-apps-in-microsoft-intune.md), [supervisión en tiempo real y Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md), [administración de la configuración de Windows Firewall](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), inventario de hardware y software, control remoto (a través de solicitudes de asistencia remota), [configuración de las actualizaciones de software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) e informes de configuración de cumplimiento.

Determinadas opciones de administración disponibles para los equipos administrados como dispositivos móviles no están disponibles para los equipos administrados con el cliente de software, como por ejemplo:

-   Borrado completo (el borrado selectivo está disponible)
-   Acceso condicional
-   Directivas de Windows diferentes a las directivas **Administración de equipos**

![Plantilla de directivas para equipos con Windows](../media/pc_policy_template.png)

Además de las acciones de agente de cliente de Intune realizadas localmente en equipos individuales, también puede utilizar la consola de administración de Intune para realizar otras [tareas comunes de administración de equipos](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) en equipos Windows con el cliente instalado como:

-   Ver información de inventario de hardware y software sobre los equipos administrados

-   Reiniciar un equipo de forma remota

-   Retirar un equipo para desinstalar el software cliente y quitarlo de la administración con Intune

-   Vincular usuarios a determinados equipos administrados

-   Responder a solicitudes de asistencia remota

El agente cliente de Intune, normalmente, se ejecuta silenciosamente en segundo plano sin necesidad de mucha interacción con el usuario o de solucionar problemas. Sin embargo, si necesita ayuda para resolver problemas de administración de equipos, hay varios [recursos disponibles para ayudarle a solucionarlos](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune).



<!--HONumber=Sep16_HO2-->


