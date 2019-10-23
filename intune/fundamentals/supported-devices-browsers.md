---
title: Sistemas operativos y exploradores compatibles con Microsoft Intune
titleSuffix: ''
description: Se muestran las plataformas y los exploradores de dispositivo admitidos para la administración de dispositivos de Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9fec08511303c15a7197014fd80834d95948191
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504888"
---
# <a name="supported-operating-systems-and-browsers-in-intune"></a>Exploradores y sistemas operativos compatibles en Intune

Antes de configurar Microsoft Intune, consulte los sistemas operativos y exploradores compatibles.

Para obtener ayuda para la instalación de Intune en su dispositivo, consulte el [uso de dispositivos administrados para realizar el trabajo](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions) y [Uso de ancho de banda de red de Intune](network-bandwidth-use.md).

Para más información sobre la compatibilidad con proveedores de servicios de configuración, consulte [Configuration service provider reference](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (Referencia del proveedor de servicios de configuración).

## <a name="intune-supported-operating-systems"></a>Sistemas operativos admitidos por Intune

Puede administrar los dispositivos que ejecuten los siguientes sistemas operativos:

[!INCLUDE [mdm-supported-devices](../../intune-classic/includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Dispositivos Samsung Knox Standard admitidos

Para evitar errores de activación de Knox que impidan la inscripción de MDM, la aplicación Portal de empresa solo intenta llevar a cabo la activación de Samsung Knox durante la inscripción de MDM si el dispositivo aparece en la [lista de dispositivos Knox admitidos](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Los dispositivos que no admiten la activación de Samsung Knox se inscriben como dispositivos Android estándares. Un dispositivo Samsung podría tener algunos números de modelo que admitan Knox, mientras que otros no. Compruebe la compatibilidad de KNOX con el distribuidor de su dispositivo antes de adquirir e implementar dispositivos Samsung.

> [!NOTE]
> La inscripción de dispositivos Samsung Knox puede requerir que [habilite el acceso a servidores de Samsung](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers). 

Los modelos de dispositivos Samsung siguientes no admiten Knox. Se inscriben como dispositivos Android nativos mediante la aplicación Portal de empresa para Android:

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


### <a name="windows-pc-software-client"></a>Cliente de software de PC Windows

Un [cliente de software Intune](../manage-windows-pcs-with-microsoft-intune.md) se puede implementar e instalar en PC Windows como método de inscripción alternativo. Esta funcionalidad solo está disponible en el portal clásico de Intune. Puede usar el cliente de software de Intune para administrar equipos con Windows 7 y versiones posteriores, con la excepción de Windows 10 Home Edition.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](../enrollment/device-enrollment.md#mobile-device-management-with-exchange-activesync-and-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Exploradores web compatibles con Intune

Las diferentes tareas administrativas requieren que use uno de los siguientes sitios web de administración.

- [Centro de administración de Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Portal de Azure](https://portal.azure.com/)

Estos portales son compatibles con los siguientes exploradores:
- Microsoft Edge (última versión)
- Microsoft Internet Explorer 11
- Safari (solo en Mac, última versión)
- Chrome (última versión)
- Firefox (última versión)




### <a name="intune-classic-portal"></a>Portal de Intune clásico

El portal de Intune clásico solo se usa para administrar dispositivos inscritos con el cliente de software de equipos de Intune (https://manage.microsoft.com) ). El portal clásico de Intune requiere compatibilidad con el explorador Silverlight.

Los siguientes exploradores Silverlight admiten la consola de Intune:
- Internet Explorer 10 o posterior
- Google Chrome (las versiones anteriores a la 42)
- Mozilla Firefox con Silverlight habilitado (versiones anteriores a la 56)

> [!Note]
> Microsoft Edge y los exploradores móviles no son compatibles con el portal clásico de Intune porque no admiten [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

Solo los usuarios con permisos de administrador de servicios o que sean administradores de inquilinos con el rol de administrador global pueden iniciar sesión en este portal. Para acceder a la consola de administración, su cuenta debe tener una licencia para usar Intune y un estado de inicio de sesión de **Permitido**.
