---
title: "Funciones de administración de PC Windows | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 665e4a1aa7ee22db91b47660a179384f7c3e4393
ms.openlocfilehash: 9e7a2f5cb2afdeca737c0c8b1b91418352ad5539


---

# Funciones de administración de equipos Windows (con el cliente de equipo de Microsoft Intune)
En la mayoría de los escenarios, los dispositivos se inscribirán con Microsoft Intune, lo que proporciona un mayor número de funciones que el cliente de equipo de Intune. Sin embargo, también puede administrar los equipos mediante el cliente de equipo de Intune, que proporciona las siguientes características:

-   **Administrar actualizaciones de software**: puede mantener actualizados los equipos y administrar cuándo se aplican las actualizaciones.

-   **Directiva del firewall de Windows**: ayuda a garantizar que ningún equipo que se use en la empresa tenga un firewall de Windows inactivo o mal configurado.

-   **Protección antimalware**: Intune incluye Endpoint Protection, que ayuda a proteger los equipos del malware.

-   **Asistencia remota:** Intune permite a los usuarios ponerse en contacto con el personal de soporte técnico de TI, que puede proporcionar asistencia mediante una característica de escritorio remoto que se incluye con Intune <!--- (requires TeamViewer software)--->.

-   **Administración de licencias de software**: realice el seguimiento del número de licencias de software disponibles y del número de licencias disponibles que se usan.
-   **Implementación de aplicaciones**: implemente software en los equipos que administra. Algunas características de administración de aplicaciones no están disponibles cuando los equipos se administran con el software cliente.


Intune admite la instalación del software cliente de equipos en hasta 7.000 dispositivos de Windows.

## Requisitos de sistema operativo
Intune puede administrar equipos que ejecutan las siguientes versiones de Windows (x86 y x64):


-   **Windows Vista**: versiones Business, Enterprise y Ultimate.

-   **Windows 7:** versiones Pro, Enterprise y Ultimate (sin Service Pack o con SP1).

-   **Windows 8:** versiones Pro y Enterprise.

-   **Windows 8.1:** versiones Pro y Enterprise.

- **Windows 10:** versiones Home, Pro, Education y Enterprise.


## Requisitos mínimos de hardware
A continuación se indican los requisitos mínimos de hardware para instalar el cliente de equipo de Intune:

|Requisito|Detalles|
|---------------|--------------------|
|Red|El cliente requiere que el equipo tenga conectividad a Internet.|
|Procesador y memoria|Consulte los requisitos de RAM y procesador para el sistema operativo del equipo.|
|Espacio en disco|200 MB de espacio disponible en el disco antes de que se instale el software cliente.|

## Requisitos adicionales
A continuación se indican los requisitos de software para instalar el cliente de equipo de Intune:

|Requisito|Detalles|
|---------------|--------------------|
|Permisos administrativos|La cuenta que instala el software de cliente debe tener permisos de administrador local en ese equipo.|
|Windows Installer 3.1|El equipo debe tener instalado como mínimo Windows Installer 3.1.|
|Quitar software cliente incompatible|Antes de instalar el software cliente de equipo de Intune, debe desinstalar el siguiente software cliente del equipo:<br /><br />- Cualquier versión de Configuration Manager<br />- Cualquier versión de Microsoft Systems Management Server (SMS)|

### Consulte también
[Capacidades de administración de dispositivos móviles en Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


