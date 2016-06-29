---
# required metadata

title: Inscribir dispositivos | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: damionw
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscribir dispositivos para administrarlos en Intune
La administración de dispositivos móviles (MDM) de Microsoft Intune hace uso de la inscripción para incluir dispositivos en la administración y permitir el acceso a los recursos. La forma en que los dispositivos se inscriben depende del tipo de dispositivo, de la propiedad de los mismos y del nivel de administración necesario. En los escenarios "Bring Your Own Device" (BYOD) y de dispositivos propiedad de la empresa se necesita un proceso de inscripción. Las organizaciones con Exchange ActiveSync (ya sea local u hospedado en la nube) permiten una administración más fluida, sin requisitos de inscripción. Los PC Windows también se pueden administrar con el software cliente de Intune.

###  Plataformas de dispositivos compatibles

Intune puede administrar las siguientes plataformas de dispositivo:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Permitir la inscripción de dispositivos  
 Con la inscripción, los usuarios pueden tener acceso a los recursos empresariales en sus dispositivos personales y el administrador puede asegurarse de que dichos dispositivos cumplen las directivas que protegen esos recursos. Se trata de la mejor manera de dar cabida a escenarios de tipo "Bring Your Own Device" con Intune. El administrador debe habilitar la inscripción en la consola de Intune, lo que podría conllevar la creación de una relación de confianza con el dispositivo y la asignación de licencias a los usuarios. Tras ello, el dispositivo se inscribe, cosa que los usuarios realizan normalmente especificando sus credenciales profesionales o educativas. Después, el dispositivo recibe la directiva de Intune y obtiene acceso a los recursos.

[Preparar la inscripción de dispositivos en Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)

## Inscribir dispositivos de propiedad corporativa
Los dispositivos de propiedad corporativa se pueden administrar con la consola de Intune. Los dispositivos iOS se pueden inscribir directamente a través de las herramientas proporcionadas por Apple. Un administrador puede inscribir cualquier tipo de dispositivo mediante el administrador de inscripción de dispositivos. Los dispositivos con un número IMEI también se pueden identificar y etiquetar como de propiedad corporativa para, así, posibilitar escenarios de dispositivos propiedad de la empresa.

[Inscribir dispositivos de propiedad corporativa](manage-corporate-owned-devices.md)

## Administración de dispositivos móviles con Exchange ActiveSync e Intune
Los dispositivos móviles que no estén inscritos, pero que se conecten a Exchange ActiveSync (EAS), se pueden administrar mediante Intune a través de la directiva de MDM de EAS. Intune usa Exchange Connector para comunicarse con EAS, tanto localmente como hospedado en la nube.



[Administración de dispositivos móviles con Exchange ActiveSync e Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Administrar equipos Windows con Intune  
Microsoft Intune también se puede usar para administrar PC Windows con el software cliente de PC Windows de Intune. Los PC administrados con el cliente de Intune pueden encargarse de lo siguiente:

 - Informar de los inventarios de software y hardware
 - Instalar aplicaciones de escritorio (por ejemplo, archivos .msi y .exe)
 - Configuración del firewall

Los equipos administrados con el software cliente de Intune no se pueden borrar ni retirar de forma selectiva de Intune, como tampoco pueden beneficiarse de muchas características de administración de Intune, por ejemplo, el acceso condicional, la configuración de VPN y Wi-Fi o la implementación de certificados y las configuraciones de correo electrónico.

[Administrar equipos Windows con Intune](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


