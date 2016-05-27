---
# required metadata

title: Administrar equipos Windows con Intune | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Administrar equipos Windows con Microsoft Intune
Además de inscribir dispositivos móviles, también puede utilizar Intune para administrar equipos que ejecutan sistemas operativos compatibles a través del software cliente de equipo Windows de Intune. Los requisitos de hardware y software para ejecutar el equipo cliente son mínimos y, básicamente, se admite cualquier sistema capaz de ejecutar Windows 7 o posterior.  El software cliente también puede instalarse fácilmente en equipos unidos a un dominio (en cualquier dominio) o no unidos a un dominio.

Intune administra equipos Windows mediante directivas, del mismo modo que los objetos de directiva de grupo (GPO) de los Servicios de dominio de Active Directory (AD DS) de Windows Server. Si va a administrar equipos unidos a un dominio de Active Directory con Intune, debe [asegurarse de que las directivas de Intune no entren en conflicto con ningún GPO](resolve-gpo-and-microsoft-intune-policy-conflicts.md) configurado para la organización.

> [!NOTE]
> Microsoft Intune, como servicio independiente, ofrece las siguientes funciones de administración de equipos. Los dispositivos que ejecutan Windows 8.1 se pueden administrar mediante el cliente de Intune o se pueden inscribir como dispositivos móviles. La siguiente información se aplica a equipos que ejecutan el cliente de Intune.

## Requisitos para la administración de equipos con Intune

**Hardware**:
los siguientes son requisitos mínimos de hardware para instalar el cliente de Intune:

|Requisito|Más información|
|---------------|--------------------|
|Red|El cliente requiere que el equipo tenga conectividad a Internet.|
|Procesador y memoria|Consulte los requisitos de RAM y procesador para el sistema operativo del equipo.|
|Espacio en disco|200 MB de espacio disponible en el disco antes de que se instale el software cliente.|

**Software**:
los siguientes son los requisitos de software para instalar el cliente:

|Requisito|Más información|
|---------------|--------------------|
|Permisos administrativos|La cuenta que instala el software de cliente debe tener permisos de administrador local en ese equipo.|
|Windows Installer 3.1|El equipo debe tener, como mínimo, Windows Installer 3.1.<br /><br />Para ver la versión de Windows Installer de un equipo:<br /><br />-   En el equipo, haga clic con el botón derecho en **%windir%\System32\msiexec.exe** y, después, haga clic en **Propiedades**..<br /><br />Puede descargar la última versión de Windows Installer desde [Windows Installer Redistributables (Paquetes redistribuibles de Windows Installer)](http://go.microsoft.com/fwlink/?LinkID=234258) en el sitio web de Microsoft Developer Network.|
|Quitar software cliente incompatible|Antes de instalar el software cliente de Intune, debe desinstalar cualquier software cliente de Configuration Manager o Systems Management Server que esté instalado en ese equipo.|

## Instalar el cliente de equipo de Intune
El primer paso en la administración de equipos Windows con Intune consiste en instalar el cliente. El software cliente se puede instalar cuando un equipo está inscrito en la administración mediante el servicio Intune de una de las maneras siguientes:

-   Puede [implementar manualmente el software cliente de Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md#to-manually-deploy-the-client-software). En este tipo de implementación, un administrador descarga el software de cliente de Intune y lo instala manualmente en cada equipo.

    Para descargar el software de cliente de Intune, abra la consola de administración de Intune y, en el área de descarga de software de cliente, descargue el paquete de software cliente. Después de instalar el software cliente, Intune instala automáticamente software adicional según sea necesario para administrar el equipo.

-   Puede usar los mismos archivos que descargó para instalar manualmente el cliente de Intune para [implementar el cliente en equipos unidos a un dominio mediante GPO de Active Directory](install-the-windows-pc-client-with-microsoft-intune.md#to-automatically-deploy-the-client-software-by-using-group-policy)..

-   [Los usuarios finales pueden inscribir por sí mismos cada uno de sus equipos](install-the-windows-pc-client-with-microsoft-intune.md#how-users-can-self-enroll-their-computers) a través del Portal de empresa de Microsoft Intune. Cada equipo inscrito, a continuación, se vincula automáticamente a la cuenta de usuario que se utilizó para instalar el software cliente de Intune.

-   Por último, también puede implementar el software cliente de Intune en equipos como parte de una [implementación de sistema operativo](install-the-windows-pc-client-with-microsoft-intune.md#install-the-microsoft-intune-client-software-as-part-of-an-image)..

## Administración de equipos con el cliente de equipos de Intune
Después de instalar el cliente de Intune, el software cliente habilita varias funciones de administración de equipo, por ejemplo: [administración de aplicaciones](deploy-apps-in-microsoft-intune.md), Endpoint Protection, inventario de hardware y software, control remoto (a través de solicitudes de asistencia remota), actualizaciones de software e informes de configuración de cumplimiento.

Varias tareas de administración de equipos habilitadas por el cliente de equipos se administran mediante directivas de Intune, como:

-   Configurar los [parámetros del Firewall de Windows](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) en los equipos administrados.

-   Configurar [parámetros de actualización de software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) para que los equipos administrados busquen y descarguen actualizaciones de software necesarias.

-   Contribuir a proteger equipos administrados de posibles amenazas y software malintencionado a través de la administración de [Endpoint Protection y la supervisión en tiempo real](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).

Además de las acciones de agente de cliente de Intune realizadas localmente en equipos individuales, también puede utilizar la consola de administración de Intune para realizar otras [tareas comunes de administración de equipos](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) en equipos Windows con el cliente instalado como:

-   Ver información de inventario de hardware y software sobre los equipos administrados

-   Reiniciar un equipo de forma remota

-   Retirar un equipo para desinstalar el software cliente y quitarlo de la administración con Intune

-   Vincular usuarios a determinados equipos administrados

-   Responder a solicitudes de asistencia remota

El agente cliente de Intune, normalmente, se ejecuta silenciosamente en segundo plano sin necesidad de mucha interacción con el usuario o de solucionar problemas. Sin embargo, si necesita ayuda para resolver problemas de administración de equipos, hay varios [recursos disponibles para ayudarle a solucionarlos](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune)..


<!--HONumber=May16_HO1-->


