---
title: Dispositivos admitidos - Microsoft Intune | Microsoft Docs
description: "Se muestran las plataformas y los exploradores de dispositivo admitidos para la administración de dispositivos de Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 71dd44ffd05d52e29895dba5370129d88c222040
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="supported-devices-and-browsers"></a>Exploradores y dispositivos admitidos

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este artículo va dirigido a administradores del sistema que son responsables de la administración de dispositivos en la empresa. Para obtener ayuda para la instalación de Intune en el teléfono, consulte el [uso de dispositivos administrados para realizar el trabajo](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions).

Antes de empezar a configurar Microsoft Intune, revise los siguientes requisitos:

- [Equipos y dispositivos admitidos](#intune-supported-devices)
- [Lista de exploradores web compatibles para usar Intune](#intune-supported-web-browsers)

También debe familiarizarse con el [uso del ancho de banda de red de Intune](network-bandwidth-use.md).

## <a name="intune-supported-devices"></a>Dispositivos compatibles con Intune

Puede administrar los dispositivos siguientes con la administración de dispositivos móviles de Intune:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

No se puede usar Intune para administrar sistemas operativos de Windows Server.

La administración de dispositivos de Intune proporciona [estas funcionalidades](mobile-device-management-capabilities-in-microsoft-intune.md).

### <a name="windows-pc-software-client"></a>Cliente de software de PC Windows

Un [cliente de software Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) se puede implementar e instalar en PC Windows como método de inscripción alternativo. Puede usar el cliente de software de Intune para administrar equipos con Windows 7 y versiones posteriores, con la excepción de Windows 10 Home Edition.

### <a name="exchange-activesync-management"></a>Administración de Exchange ActiveSync

Puede administrar [dispositivos de Exchange ActiveSync](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) desde la consola Intune. Esta opción proporciona un conjunto limitado de funcionalidades de administración, si se compara con los otros métodos. Consulte [Capacidades de administración de dispositivos móviles integrada para Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) para ver una lista de los dispositivos compatibles.

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
> Microsoft Edge y los exploradores móviles no son compatibles con la consola de administración porque no admiten [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx). La migración de la consola de Intune desde la experiencia de Silverlight se realizará a lo largo de un período de tiempo; al final, todos los dispositivos móviles y las características de administración de aplicaciones de Intune estarán [disponibles en el nuevo portal de Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).


Solo los usuarios con permisos de administrador de servicios o que sean administradores de inquilinos con el rol de administrador global pueden iniciar sesión en este portal. Para acceder a la consola de administración, su cuenta debe tener una licencia para usar Intune y un estado de inicio de sesión de **Permitido**.

>[!div class="step-by-step"]

>[**Redes** &rarr;](network-bandwidth-use.md)  

