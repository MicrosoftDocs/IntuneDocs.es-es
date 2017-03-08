---
title: Administrar PC con software cliente | Microsoft Docs
description: Administre equipos Windows instalando el software cliente de Intune.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 2e7062169ceb855f03a13d1afb4b4de41af593ac
ms.openlocfilehash: 10ba007095182c9cb07710656ba5f275e254d92e
ms.lasthandoff: 02/15/2017


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>Administración de PC con Windows con el software de cliente de PC de Intune
[Inscripción de equipos Windows como dispositivos móviles](set-up-windows-device-management-with-microsoft-intune.md) es el método preferido para inscribir equipos Windows en Intune, pero puede elegir de manera alternativa inscribir y administrar equipos Windows mediante la instalación del software cliente de Intune, como se describe en este tema.

Intune administra equipos Windows mediante directivas, del mismo modo que los objetos de directiva de grupo (GPO) de los Servicios de dominio de Active Directory (AD DS) de Windows Server. Si va a administrar equipos unidos a un dominio de Active Directory con Intune, [asegúrese de que las directivas de Intune no entren en conflicto con ningún GPO](resolve-gpo-and-microsoft-intune-policy-conflicts.md) configurado para la organización. Puede leer más información sobre los GPO [aquí](https://technet.microsoft.com/library/hh147307.aspx).

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Directivas e implementaciones de aplicación para el software cliente de Intune

Aunque el software cliente de Intune admite [características de administración que ayudan a proteger los equipos](policies-to-protect-windows-pcs-in-microsoft-intune.md) mediante la administración de actualizaciones de software, Firewall de Windows y Endpoint Protection, los equipos administrados con el software cliente de Intune no pueden ser objeto de otras directivas de Intune, incluida la configuración de directivas de **Windows** que es específica de la administración de dispositivos móviles. 

Cuando use el software cliente de Intune para administrar equipos con Windows, solo puede usar las directivas que se muestran en la sección **Administración de equipos**.

  ![Selección de la plantilla para la nueva directiva de equipo de Windows](../media/select-template-for-pc-policy.png)

Para obtener descripciones detalladas de las directivas que puede definir, consulte:

- [Usar directivas para ayudar a proteger los equipos Windows que ejecutan el software cliente de Intune](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)
- [Mantener los equipos Windows al día con las actualizaciones de software de Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)
- [Ayudar a proteger los equipos de Windows mediante directivas del Firewall de Windows en Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)
- [Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

Además, al implementar aplicaciones, puede solo el instalador de Windows (.exe, .msi).

  ![Selección de la plataforma y la ubicación de los archivos del software cliente de PC](../media/select-platform-of-software-files-for-pc-agent.png)

> [!NOTE]
> Puede administrar dispositivos Windows 8.1 o versiones posteriores como equipos, con el software cliente de Intune, o como dispositivos móviles con la función de administración de dispositivos móviles (MDM). No puede usar ambos métodos juntos, así que medite su decisión antes de optar por la administración de los equipos mediante el software cliente de Intune. Este tema solo se aplica a la administración de dispositivos como equipos mediante la ejecución del software cliente de Intune.

## <a name="requirements-for-intune-pc-client-management"></a>Requisitos para la administración de clientes de PC de Intune

**Hardware**: los siguientes son los requisitos mínimos de hardware para instalar el software cliente de Intune:

|Requisito|Más información|
|---------------|--------------------|
|Red|El cliente requiere que el equipo tenga conectividad a Internet.|
|Procesador y memoria|Consulte los requisitos de RAM y procesador para el sistema operativo del equipo.|
|Espacio en disco|200 MB de espacio disponible en el disco antes de que se instale el software cliente.|

**Software**: los siguientes son los requisitos de software para instalar el software cliente:

|Requisito|Más información|
|---------------|--------------------|
|Sistema operativo | Dispositivo Windows con Windows Vista o posterior. </br></br>**No se admiten las versiones Home Edition.**|
|Permisos administrativos|La cuenta que instala el software cliente debe tener permisos de administrador local en ese dispositivo.|
|Windows Installer 3.1|El equipo debe tener, como mínimo, Windows Installer 3.1.<br /><br />Para ver la versión de Windows Installer de un equipo:<br /><br />  En el PC, haga clic con el botón derecho en **%windir%\System32\msiexec.exe** y, luego, haga clic en **Propiedades**.<br /><br />Puede descargar la última versión de Windows Installer desde [Windows Installer Redistributables (Paquetes redistribuibles de Windows Installer)](http://go.microsoft.com/fwlink/?LinkID=234258) en el sitio web de Microsoft Developer Network.|
|Quitar software cliente incompatible|Antes de instalar el software cliente de Intune, desinstale cualquier software cliente de Configuration Manager, Operations Manager, Operations Management Suite y Service Manager desde ese equipo.|

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Características de administración de equipos con el software cliente de Intune

Después de que el software cliente de Intune se instale, las características de administración incluyen: 

- [Administración de aplicaciones](deploy-apps-in-microsoft-intune.md)

- [Supervisión en tiempo real y Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md): Endpoint Protection es lo mismo que Windows Defender. Endpoint Protection se aplica a Windows 7 y Windows 8. Para Windows 10 y versiones posteriores, el nombre del producto ha cambiado a Windows Defender.

- [Administración de la configuración de Firewall de Windows](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), inventario de hardware y software, control remoto (a través de solicitudes de asistencia remota)

- [Configuración de la actualización de software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- Informes de la configuración de cumplimiento

En la consola de administración de Intune, determinadas secciones, como "Actualizaciones", "Protección" y "Licencia" solo aparecen si se han inscrito dispositivos mediante el software cliente de Intune.

  ![Elementos de la consola de administración que aparecen solo para el equipo cliente](../media/admin-console-settings-only-for-pc-agent.png)

También puede usar la consola de administración de Intune para realizar otras tareas comunes de administración del equipo en equipos Windows que tengan instalado el cliente:

-   Ver información de inventario de hardware y software sobre los equipos administrados
-   Reiniciar un equipo de forma remota
-   Retirar un equipo para desinstalar el software cliente y quitarlo de la administración con Intune
-   Vincular usuarios a determinados equipos administrados
-   Responder a solicitudes de asistencia remota

Para obtener más información sobre las tareas anteriores, vea [Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

## <a name="management-limitations-of-the-intune-client-software"></a>Limitaciones de administración del software cliente de Intune

Algunas opciones de administración, que pueden usarse para administrar equipos como dispositivos móviles, no pueden usarse en equipos administrados con el software cliente de Intune:

-   Borrado completo (el borrado selectivo está disponible)

-   Acceso condicional

## <a name="help-with-troubleshooting"></a>Ayuda con la solución de problemas

El software cliente de Intune, normalmente, se ejecuta silenciosamente en segundo plano sin necesidad de mucha interacción con el usuario o de solucionar problemas. Si necesita solucionar problemas de administración de equipos, puede comprobar los registros. El software cliente de Intune y los registros correspondientes están instalados en el directorio %Archivos de programa%\Microsoft\OnlineManagement.

También puede revisar [Solucionar los problemas de configuración del cliente en Microsoft Intune](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune) para buscar problemas que podrían producirse y las soluciones o alternativas.

