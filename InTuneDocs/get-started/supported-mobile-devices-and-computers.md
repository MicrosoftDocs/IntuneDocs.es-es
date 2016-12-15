---
title: "Exploradores y dispositivos móviles compatibles | Microsoft Intune"
description: Muestra los exploradores y dispositivos compatibles que pueden ejecutar Intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/01/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: b0eab195c00aae4b593fff535179a1b993c36dde


---

# <a name="supported-devices-and-web-browsers-for-intune"></a>Exploradores web y dispositivos compatibles con Intune

Como administrador de Intune, puede administrar una variedad de dispositivos desde un explorador web. En este tema se proporcionan:

- [Listas de las plataformas de dispositivos compatibles](#intune-supported-devices)
- [Lista de exploradores web compatibles para usar Intune](#intune-supported-web-browsers)

## <a name="intune-supported-devices"></a>Dispositivos compatibles con Intune

Puede administrar los dispositivos siguientes con la administración de dispositivos móviles de Intune:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

No se puede usar Intune para administrar sistemas operativos de Windows Server.

La administración de dispositivos de Intune proporciona [estas funcionalidades](mobile-device-management-capabilities-in-microsoft-intune.md).

### <a name="windows-pc-software-client"></a>Cliente de software de PC Windows

Un [cliente de software Intune](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune) se puede implementar e instalar en PC Windows como método de inscripción alternativo. Puede usar el cliente de software Intune para administrar equipos con Windows 7 y versiones posteriores, con la excepción de Windows 10 Home Edition. La administración de equipos con el software cliente proporciona [estas capacidades](windows-pc-management-capabilities-in-microsoft-intune.md).

### <a name="exchange-activesync-management"></a>Administración de Exchange ActiveSync

Puede administrar [dispositivos de Exchange ActiveSync](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) desde la consola Intune. Esta opción proporciona un conjunto limitado de funcionalidades de administración, si se compara con los otros métodos. Consulte [Capacidades de administración de dispositivos móviles integrada para Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) para ver una lista de los dispositivos compatibles.

## <a name="intune-supported-web-browsers"></a>Exploradores web compatibles con Intune

Las diferentes tareas administrativas requieren que use uno de los siguientes sitios web de administración.

- [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Consola de administrador de Microsoft Intune](https://admin.manage.microsoft.com/)

|Característica de Intune |Exploradores admitidos|
|---------|---------|
|**Consola de administración de Intune**     |  Internet Explorer 10 o posterior<br /><br />Google Chrome (las versiones anteriores a la 42)<br /><br />Mozilla Firefox con Silverlight habilitado<br />**Nota:** Mozilla quitará la compatibilidad con Silverlight a partir de marzo de 2017. [Más información](https://go.microsoft.com/fwlink/?linkid=836872). |
|**Portal de administración de Office 365**     |Todos los exploradores, incluidos los exploradores móviles y los exploradores administrados  |
|**Sitio web del Portal de empresa**     |**En dispositivos móviles:** use el explorador web predeterminado para cada plataforma compatible   <br /><br />**En equipos de Windows:** Internet Explorer 10 o posterior, o Microsoft Edge<br /><br />**En Mac OS X 10.9 o posterior:** Apple Safari    |

> [!Note]
> Microsoft Edge y los exploradores móviles no son compatibles con la consola de administración porque no admiten [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). La migración de la consola de Intune desde la experiencia de Silverlight se realizará a lo largo de un período de tiempo; al final, todos los dispositivos móviles y las características de administración de aplicaciones de Intune estarán [disponibles en el nuevo portal de Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).


Solo los usuarios con permisos de administrador de servicios o que sean administradores de inquilinos con el rol de administrador global pueden iniciar sesión en este portal. Para acceder a la consola de administración, su cuenta debe tener una licencia para usar Intune y un estado de inicio de sesión de **Permitido**.
>[!div class="step-by-step"]

>[&larr; **Requisitos previos**](what-to-know-before-you-start-microsoft-intune.md)     [**Redes** &rarr;](network-bandwidth-use.md)  



<!--HONumber=Dec16_HO2-->


