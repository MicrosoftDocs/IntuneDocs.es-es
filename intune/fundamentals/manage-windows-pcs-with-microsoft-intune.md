---
title: 'Administrar PC con software cliente en Microsoft Intune: Azure | Microsoft Docs'
description: Administre equipos Windows instalando el software cliente de Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb67cf2cb17b78c4034c3b73e229e160723d975e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414388"
---
# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>Administración de PC con Windows con el software de cliente de PC de Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!WARNING]
> Microsoft anunció que el [soporte técnico para Windows 7 terminará el 14 de enero de 2020](https://support.microsoft.com/help/4057281/windows-7-support-will-end-on-january-14-2020). En esta fecha, Intune también retirará la compatibilidad con dispositivos que ejecutan Windows 7. Microsoft recomienda encarecidamente que cambie a Windows 10 para evitar las interrupciones de servicio o soporte técnico.
> 
> Para más información, consulte [Plan de cambio de Intune: aproximación de la finalización del ciclo de vida de soporte técnico de Windows 7](../fundamentals/whats-new.md#intune-plan-for-change-nearing-end-of-support-for-windows-7).

> [!NOTE]
> Puede usar Microsoft Intune para administrar equipos con Windows [como dispositivos móviles con la administración de dispositivos móviles (MDM)](../enrollment/windows-enroll.md) o como equipos con el software cliente de Intune, tal y como se describe a continuación. Sin embargo, Microsoft recomienda que los clientes [usen la solución de administración de MDM](../enrollment/windows-enroll.md) siempre que sea posible. Para obtener más información, vea [Comparación de la administración de equipos con Windows como dispositivos móviles o equipos](pc-management-comparison.md). 

Intune proporciona una solución completa para que las organizaciones administren dispositivos móviles. Intune puede administrar PC con Windows como dispositivos móviles mediante las funcionalidades de administración de dispositivos modernos integradas en el sistema operativo de Windows 10. Para satisfacer las necesidades de administración de su organización, Intune también puede administrar PC con Windows como equipos con el cliente de software de Intune. Este método de administración utiliza las funcionalidades de administración de equipos tradicionales en el sistema operativo de Windows heredado.

El cliente de software de Intune es ideal para PC con Windows que ejecutan sistemas operativos heredados, como Windows 7, que no se pueden administrar como dispositivos móviles. El cliente de software de Intune usa las funcionalidades de administración como la Directiva de grupos para administrar los equipos desde la nube.

Intune admite la administración de PC con Windows como equipos con el cliente de software para 7000 equipos como máximo. Para implementaciones más grandes, administre los PC con Windows 10 como dispositivos móviles. Cada versión de Intune y actualización de Windows 10 incluyen características de administración basadas en la arquitectura de administración de dispositivos móviles. Se recomienda encarecidamente que traslade su organización a Windows 10 administrado como dispositivos móviles.

> [!NOTE]
> Puede administrar dispositivos con Windows 8.1 o versiones posteriores como equipos con el software de cliente de Intune, o como dispositivos móviles. No puede usar ambos métodos en el mismo dispositivo. Piense detenidamente antes de decidir administrar equipos con el software de cliente de Intune. Este tema solo se aplica a la administración de dispositivos como equipos mediante la ejecución del software cliente de Intune.

## <a name="requirements-for-intune-pc-client-management"></a>Requisitos para la administración de clientes de PC de Intune

**Hardware**:  
Estos son los requisitos mínimos de hardware para instalar el software cliente de Intune:

|Requisito|Más información|
|---------------|--------------------|
|Network (Red)|El cliente requiere que el equipo tenga conectividad a Internet.|
|Procesador y memoria|Consulte los requisitos de RAM y procesador para el sistema operativo del equipo.|
|Espacio en disco|200 MB de espacio disponible en el disco antes de que se instale el software cliente.|

**Software**:  
Estos son los requisitos de software para instalar el software cliente:

|Requisito|Más información|
|---------------|--------------------|
|Sistema operativo | Dispositivo Windows con Windows 7 SP1 y Windows 8.1 o posterior. </br></br>**No se admiten las versiones Home Edition.**|
|Permisos administrativos|La cuenta que instala el software cliente debe tener permisos de administrador local en ese dispositivo.|
|Windows Installer 3.1|El equipo debe tener, como mínimo, Windows Installer 3.1.<br /><br />Para ver la versión de Windows Installer de un equipo:<br /><br />  En el PC, haga clic con el botón derecho en **%windir%\System32\msiexec.exe** y, luego, haga clic en **Propiedades**.<br /><br />Puede descargar la última versión de Windows Installer desde [Windows Installer Redistributables (Paquetes redistribuibles de Windows Installer)](https://go.microsoft.com/fwlink/?LinkID=234258) en el sitio web de Microsoft Developer Network.|
|Quitar software cliente incompatible|Antes de instalar el software cliente de Intune, desinstale cualquier software cliente de Configuration Manager, Operations Manager y Service Manager desde ese equipo.|

## <a name="deploying-the-intune-software-client"></a>Implementación del cliente de software de Intune
Como administrador de Intune, puede hacer que el cliente de software de Intune esté disponible para los usuarios de diversas formas. Para obtener una guía, vea [Instalar el cliente de software de Intune en equipos con Windows](../install-the-windows-pc-client-with-microsoft-intune.md).

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Características de administración de equipos con el software cliente de Intune
En la mayoría de los escenarios, los dispositivos se inscribirán con Microsoft Intune, lo que proporciona un mayor número de capacidades. En cambio, también puede administrar los PC mediante el cliente de software de Intune, que proporciona las siguientes características:

- **[Administración de actualizaciones de software](../keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)** : puede mantener actualizados los equipos y decidir cuándo se aplican las actualizaciones.

- **[Directiva de Firewall de Windows](../help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)** : ayuda a asegurarse de que ningún equipo que se use en la empresa tenga un Firewall de Windows inactivo o mal configurado.

- **[Protección antimalware](../help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)** : Intune incluye Endpoint Protection, que ayuda a proteger los equipos contra el malware.

- **[Asistencia remota](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)** : Intune permite a los usuarios ponerse en contacto con el personal de soporte técnico de TI, que puede proporcionar asistencia mediante una característica de Escritorio remoto incluida en Intune (requiere el software TeamViewer).

- **[Administración de licencias de software](../manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)** : realice el seguimiento del número de licencias de software disponibles y cuántas de estas se usan.
- **[Implementación de aplicaciones](add-apps-for-windows-pcs-in-microsoft-intune.md)** : implemente software en los equipos que administra. Algunas características de administración de aplicaciones no están disponibles cuando los PC se administran con el cliente de software.

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Directivas e implementaciones de aplicación para el software cliente de Intune

Aunque el software cliente de Intune admite [características de administración que ayudan a proteger los equipos](policies-to-protect-windows-pcs-in-microsoft-intune.md) mediante la administración de actualizaciones de software, Firewall de Windows y Endpoint Protection, los equipos administrados con el software cliente de Intune no pueden ser objeto de otras directivas de Intune, incluida la configuración de directivas de **Windows** que es específica de la administración de dispositivos móviles.

Cuando use el software cliente de Intune para administrar equipos con Windows, solo puede usar las directivas que se muestran en la sección **Administración de equipos**.

Intune administra equipos con Windows mediante directivas, de la misma forma en que los objetos de directiva de grupo (GPO) de Active Directory Domain Services (AD DS) de Windows Server. Si administra equipos unidos a un dominio de Active Directory con Intune, [asegúrese de que las directivas de Intune no entren en conflicto con ningún GPO](resolve-gpo-and-microsoft-intune-policy-conflicts.md) utilizado en la organización. Para obtener más información, vea [Directiva de grupo para principiantes](https://technet.microsoft.com/library/hh147307.aspx).

  ![Selección de la plantilla para la nueva directiva de equipo de Windows](./media/manage-windows-pcs-with-microsoft-intune/select-template-for-pc-policy.png)

Al implementar aplicaciones, puede usar solo Windows Installer (.exe o .msi).

  ![Selección de la plataforma y la ubicación de los archivos del software cliente de PC](./media/manage-windows-pcs-with-microsoft-intune/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Tareas comunes de equipos con Windows

Puede usar la consola de administración de Intune para realizar otras tareas comunes de administración del equipo en equipos con Windows que tengan instalado el cliente:
- [Usar directivas para simplificar la administración de PC](use-policies-to-simplify-windows-pc-management.md): describe las directivas de **administración de equipos** y enumera las opciones de Microsoft Intune Center.

- [Ver el inventario de hardware y software para PC de Windows](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md): explica cómo crear un informe que muestra información acerca de las capacidades de hardware de PC y el software instalado en ellos. También explica cómo actualizar el inventario de PC para asegurarse de que está actualizado.
- [Retirar un PC de Windows](retire-a-windows-pc-with-microsoft-intune.md): enumera los pasos necesarios para retirar un PC de Windows y describe lo que sucede cuando se retira un PC.
- [Administrar la vinculación del dispositivo de usuario para PC de Windows](../manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md): explica cómo y cuándo debe vincular un usuario a un PC antes de implementar software para el usuario.
- [Solicitar y proporcionar asistencia remota a los PC de Windows](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md): explica cómo los usuarios de PC de Intune obtienen ayuda de asistencia remota gracias a usted y describe los requisitos previos y el programa de instalación de TeamViewer.

Para obtener más información sobre las tareas anteriores, vea [Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

## <a name="management-limitations-of-the-intune-client-software"></a>Limitaciones de administración del software cliente de Intune

Algunas opciones de administración, que pueden usarse para administrar equipos como dispositivos móviles, no pueden usarse en equipos administrados con el software cliente de Intune:

- Borrado completo (el borrado selectivo está disponible)
- Acceso condicional

También tenga en cuenta que en la consola de administración de Intune, determinadas secciones, como **Actualizaciones**, **Protección** y **Licencia** solo aparecen si se han inscrito dispositivos mediante el software de cliente de Intune.

  ![Elementos de la consola de administración que aparecen solo para el equipo cliente](./media/manage-windows-pcs-with-microsoft-intune/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>Ayuda con la solución de problemas

El software cliente de Intune, normalmente, se ejecuta silenciosamente en segundo plano sin necesidad de mucha interacción con el usuario o de solucionar problemas. Si necesita solucionar problemas de administración de equipos, puede comprobar los registros. El software cliente de Intune y los registros correspondientes están instalados en el directorio %Archivos de programa%\Microsoft\OnlineManagement.

También puede revisar la [inscripción de dispositivos](../enrollment/device-enrollment.md) para obtener más información sobre cómo inscribir dispositivos con Microsoft Intune.
