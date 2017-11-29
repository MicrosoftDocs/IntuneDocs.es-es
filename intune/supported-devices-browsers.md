---
title: Dispositivos admitidos - Microsoft Intune
description: "Se muestran las plataformas y los exploradores de dispositivo admitidos para la administración de dispositivos de Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b168cbf5282b4e016133d071c56c8abd54c2e23b
ms.sourcegitcommit: dc2595bec05206a826cd10cb834bf6043145c917
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/14/2017
---
# <a name="supported-devices-and-browsers"></a>Exploradores y dispositivos admitidos

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Este artículo va dirigido a administradores del sistema que son responsables de la administración de dispositivos en la empresa. Para obtener ayuda para la instalación de Intune en el teléfono, consulte el [uso de dispositivos administrados para realizar el trabajo](/intune-user-help/company-portal-frequently-asked-questions).

Antes de empezar a configurar Microsoft Intune, revise los siguientes requisitos:

- [Equipos y dispositivos admitidos](#intune-supported-devices)
- [Lista de exploradores web compatibles para usar Intune](#intune-supported-web-browsers)

También debe familiarizarse con el [uso del ancho de banda de red de Intune](network-bandwidth-use.md) ([portal clásico](/intune-classic/get-started/network-bandwidth-use)).

## <a name="intune-supported-devices"></a>Dispositivos compatibles con Intune

Puede administrar los dispositivos siguientes con la administración de dispositivos móviles de Intune:

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Dispositivos Samsung KNOX Standard admitidos

La aplicación Portal de empresa solo intenta llevar a cabo la activación de Samsung KNOX durante la inscripción de MDM si el dispositivo aparece en la [lista de dispositivos KNOX admitidos](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Con esto se evitan errores de activación de KNOX que impiden la inscripción de MDM. Los dispositivos que no admiten la activación de Samsung KNOX se inscriben como dispositivos Android estándares. Un dispositivo Samsung podría tener algunos números de modelo que admitan KNOX, mientras que otros no. Compruebe la compatibilidad de KNOX con el distribuidor de su dispositivo antes de adquirir e implementar dispositivos Samsung.

La siguiente lista contiene modelos de dispositivos Samsung que no admiten KNOX y que se inscriben como dispositivos Android nativos mediante la aplicación Portal de empresa para Android:

| **Nombre del dispositivo** | **Números de modelo de los dispositivos** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM-T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |

No se puede usar Intune para administrar sistemas operativos de Windows Server.

### <a name="windows-pc-software-client"></a>Cliente de software de PC Windows

Un [cliente de software Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) se puede implementar e instalar en PC Windows como método de inscripción alternativo. Esta funcionalidad solo está disponible en el portal clásico de Intune. Puede usar el cliente de software de Intune para administrar equipos con Windows 7 y versiones posteriores, con la excepción de Windows 10 Home Edition.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Exploradores web compatibles con Intune

Las diferentes tareas administrativas requieren que use uno de los siguientes sitios web de administración.

- [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Portal de Azure](https://portal.azure.com/)

Estos portales son compatibles con los siguientes exploradores:
- Microsoft Edge (última versión)
- Microsoft Internet Explorer 11
- Safari (solo en Mac, última versión)
- Chrome (última versión)
- Firefox (última versión)

### <a name="intune-classic-portal"></a>Portal de Intune clásico

Las características únicamente clásicas de Intune, como el cliente de software de PC de Intune y la integración con asociados de Mobile Threat Defense, solo están disponibles en el portal de Intune clásico (https://manage.microsoft.com). El portal clásico de Intune requiere compatibilidad con el explorador Silverlight.

Los siguientes exploradores Silverlight admiten la consola de Intune:
- Internet Explorer 10 o posterior
- Google Chrome (las versiones anteriores a la 42)
- Mozilla Firefox on Silverlight habilitado [Más información](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> Microsoft Edge y los exploradores móviles no son compatibles con el portal clásico de Intune porque no admiten [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

Solo los usuarios con permisos de administrador de servicios o que sean administradores de inquilinos con el rol de administrador global pueden iniciar sesión en este portal. Para acceder a la consola de administración, su cuenta debe tener una licencia para usar Intune y un estado de inicio de sesión de **Permitido**.
