---
title: Dispositivos admitidos - Microsoft Intune
description: "Se muestran las plataformas y los exploradores de dispositivo admitidos para la administración de dispositivos de Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f862129d73c83e078d8b29201f1d92b9b65aa609
ms.sourcegitcommit: ce8a1f0f4e95444949556600d1837937b6efd769
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2017
---
# <a name="supported-devices-and-browsers"></a>Exploradores y dispositivos admitidos

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Este artículo va dirigido a administradores del sistema que son responsables de la administración de dispositivos en la empresa. Para obtener ayuda para la instalación de Intune en el teléfono, consulte el [uso de dispositivos administrados para realizar el trabajo](/intune-user-help/company-portal-frequently-asked-questions).

Antes de empezar a configurar Microsoft Intune, revise los siguientes requisitos:

- [Equipos y dispositivos admitidos](#intune-supported-devices)
- [Lista de exploradores web compatibles para usar Intune](#intune-supported-web-browsers)

También debe familiarizarse con el [uso del ancho de banda de red de Intune](network-bandwidth-use.md) ([consola clásica](/intune-classic/get-started/network-bandwidth-use)).

## <a name="intune-supported-devices"></a>Dispositivos compatibles con Intune

Puede administrar los dispositivos siguientes con la administración de dispositivos móviles de Intune:

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

No se puede usar Intune para administrar sistemas operativos de Windows Server.

### <a name="windows-pc-software-client"></a>Cliente de software de PC Windows

Un [cliente de software Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) se puede implementar e instalar en PC Windows como método de inscripción alternativo. Esta funcionalidad solo está disponible en la consola clásica de Intune. Puede usar el cliente de software de Intune para administrar equipos con Windows 7 y versiones posteriores, con la excepción de Windows 10 Home Edition.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Exploradores web compatibles con Intune

Las diferentes tareas administrativas requieren que use uno de los siguientes sitios web de administración.

- [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Portal de Intune](https://portal.azure.com/)

Estos portales son compatibles con los siguientes exploradores:
- Microsoft Edge (última versión)
- Microsoft Internet Explorer 11
- Safari (solo en Mac, última versión)
- Chrome (última versión)
- Firefox (última versión)

### <a name="intune-classic-portal"></a>Portal de Intune clásico

Las características únicamente clásicas de Intune, como el cliente de software de PC de Intune y la integración con asociados de Mobile Threat Defense, solo están disponibles en el portal de Intune clásico (https://manage.microsoft.com). El portal clásico de Intune requiere compatibilidad con el explorador Silverlight.

Los siguientes exploradores Silverlight admiten la consola clásica de Intune:
- Internet Explorer 10 o posterior
- Google Chrome (las versiones anteriores a la 42)
- Mozilla Firefox on Silverlight habilitado [Más información](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> Microsoft Edge y los exploradores móviles no son compatibles con la consola clásica de Intune porque no admiten [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

Solo los usuarios con permisos de administrador de servicios o que sean administradores de inquilinos con el rol de administrador global pueden iniciar sesión en este portal. Para acceder a la consola de administración, su cuenta debe tener una licencia para usar Intune y un estado de inicio de sesión de **Permitido**.
