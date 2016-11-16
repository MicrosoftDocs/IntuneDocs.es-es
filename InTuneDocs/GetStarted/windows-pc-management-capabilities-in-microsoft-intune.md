---
title: Capacidades de cliente de software de PC de Intune | Microsoft Intune
description: "Obtenga información acerca de las funcionalidades de Intune cuando se administran PC Windows con el cliente de software de Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: e786cd33b5c963fa373d281e93721d0dd0f5456c


---

# Funciones de administración de equipos Windows cuando se usa el cliente de software de Intune
En la mayoría de los escenarios, los dispositivos se inscribirán con Microsoft Intune, lo que proporciona un mayor número de capacidades. En cambio, también puede administrar los PC mediante el cliente de software de Intune, que proporciona las siguientes características:

-   **[Administración de actualizaciones de software](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)**: puede mantener actualizados los equipos y decidir cuándo se aplican las actualizaciones.

-   **[Directiva de Firewall de Windows](/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)**: ayuda a asegurarse de que ningún equipo que se use en la empresa tenga un Firewall de Windows inactivo o mal configurado.

-   **[Protección antimalware](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)**: Intune incluye Endpoint Protection, que ayuda a proteger los equipos contra el malware.

-   **[Asistencia remota](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-to-windows-pcs-that-use-the-intune-client-software )**: Intune permite a los usuarios ponerse en contacto con el personal de soporte técnico de TI, que puede proporcionar asistencia mediante una característica de Escritorio remoto incluida en Intune (requiere el software TeamViewer).

-   **[Administración de licencias de software](/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)**: realice el seguimiento del número de licencias de software disponibles y cuántas de estas se usan.
-   **[Implementación de aplicaciones](/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)**: implemente software en los equipos que administra. Algunas características de administración de aplicaciones no están disponibles cuando los PC se administran con el cliente de software.


Intune admite la instalación del cliente de software en hasta 7000 dispositivos de Windows.

## Requisitos de sistema operativo
Intune puede administrar equipos que ejecutan las siguientes versiones de Windows (32 y 64 bits):


-   **Windows Vista**: versiones Business, Enterprise y Ultimate

-   **Windows 7**: versiones Pro, Enterprise y Ultimate (sin Service Pack o con SP1)

-   **Windows 8**: versiones Pro y Enterprise

-   **Windows 8.1**: versiones Pro y Enterprise

- **Windows 10**: versiones Pro, Education y Enterprise


## Requisitos mínimos de hardware
A continuación se indican los requisitos mínimos de hardware para instalar el cliente de software de Intune:

|Requisito|Detalles|
|---------------|--------------------|
|Red|El cliente requiere que el equipo tenga conectividad a Internet.|
|Procesador y memoria|Consulte los requisitos de RAM y procesador para el sistema operativo del equipo.|
|Espacio en disco|200 MB de espacio disponible en el disco antes de que se instale el software cliente.|

## Requisitos adicionales
A continuación se indican los requisitos de software para instalar el cliente de software de Intune:

|Requisito|Detalles|
|---------------|--------------------|
|Permisos administrativos|La cuenta que instala el software cliente debe tener permisos de administrador local en ese equipo.|
|Windows Installer 3.1|El equipo debe tener, como mínimo, Windows Installer 3.1.|
|Quitar software cliente incompatible|Antes de instalar el software cliente de equipo de Intune, debe desinstalar el siguiente software cliente del equipo:<br /><br />- Cualquier versión de Configuration Manager<br />- Cualquier versión de Microsoft Systems Management Server (SMS)|

### Consulte también
[Funcionalidades de administración de dispositivos inscritos en Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Oct16_HO4-->


