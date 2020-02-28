---
title: Comparación de las opciones de administración de equipos con Windows
titleSuffix: Microsoft Intune
description: Inscripción de dispositivos iOS/iPadOS de empresa mediante el Programa de inscripción de dispositivos (DEP) de Apple o Apple Configurator.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/13/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: cda9a549cb12ab61da67da91272e9f388d32a2ef
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514989"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Comparación de la administración de equipos con Windows como dispositivos móviles o equipos

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Las organizaciones pueden usar Microsoft Intune para administrar equipos con Windows como dispositivos móviles con la administración de dispositivos móviles (MDM) o como equipos con el software cliente de Intune.  Microsoft recomienda que los clientes usen la solución de administración de MDM siempre que sea posible. Para ayudarle a entender mejor las diferencias entre estas opciones, en la tabla siguiente se ofrece una comparación de las dos opciones de administración.

|**Funcionalidad/escenario** |**Windows como equipo**<br>Cliente de software de Intune | **Windows como dispositivo móvil**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Sistemas operativos** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Compatibilidad con el portal de Intune** |[Consola de Silverlight](https://manage.microsoft.com)|[Portal de Azure](https://portal.azure.com) |
|**Acceso condicional**|No disponible|Disponible <br>[¿Qué es el acceso condicional?](../protect/conditional-access.md)|
|**Inscripción masiva**|No disponible|Disponible <br>[Inscripción masiva para dispositivos Windows](../enrollment/windows-bulk-enroll.md)|
|**Perfiles de dispositivo**|No disponible|Disponible <br>[¿Qué son los perfiles de dispositivo de Microsoft Intune?](../configuration/device-profiles.md)|
|**Inscripción sin agente**|No disponible |Disponible<br>[Inscribir dispositivos Windows](../enrollment/windows-enroll.md)|
|**Administración de actualizaciones de software**| Actualizaciones de Windows y actualizaciones de aplicaciones de Microsoft<br>[Mantener los equipos Windows al día con las actualizaciones de software](../keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Tienda Microsoft para Empresas para actualizaciones de aplicaciones de Windows 10 y Microsoft<br> [Configurar Windows Update para empresas](../protect/windows-update-for-business-configure.md) |
|**Administración de licencias de software**|Disponible <br>[Administrar contratos de licencia de software de equipos Windows](../manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|Tienda Microsoft para Empresas (solo aplicaciones .appx)<br>[Administración de aplicaciones adquiridas a través de la Tienda Microsoft para Empresas](../apps/windows-store-for-business.md)|
|**Inventario**|Disponible <br>[Visualización del inventario de software y hardware para equipos Windows](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|Disponible <br>[Supervisión de la información de las aplicaciones](../apps/apps-monitor.md)<br>[What is device management](../remote-actions/device-management.md) (¿Qué es la administración de dispositivos?)|
|**Directiva de Firewall de Windows**|Disponible <br>[Ayudar a proteger los equipos de Windows mediante directivas del Firewall de Windows](../help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |Disponible <br>[Firewall de Microsoft Defender](../protect/endpoint-protection-windows-10.md#microsoft-defender-firewall)|
|**Protección antimalware**|Endpoint Protection<br>[Ayudar a proteger los equipos de Windows con Endpoint Protection](../help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Microsoft Defender<br>[Habilitar Microsoft Defender](../protect/advanced-threat-protection.md)|
|**Asistencia remota** |TeamViewer<br>[Solicitar y proporcionar asistencia remota para equipos con Windows](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [Uso de TeamViewer para administrar dispositivos de Intune de forma remota](../remote-actions/teamviewer-support.md) |
|**Implementación de aplicaciones** | No está disponible para la Tienda Microsoft para Empresas. Solo para<br>.exe, .appx, y varios archivos .msi<br>[Agregar aplicaciones para PC Windows que ejecutan el software cliente de Intune](add-apps-for-windows-pcs-in-microsoft-intune.md)|Disponible para aplicaciones de la Tienda Microsoft y de línea de negocio<br>[Adición de aplicaciones de la Tienda Windows](../apps/store-apps-windows.md)<br>[Adición de aplicaciones de línea de negocio (LOB) de Windows](../apps/lob-apps-windows.md)|
|**Protección de aplicaciones**|No disponible|Available <br>[¿Qué son las directivas de protección de aplicaciones?](../apps/app-protection-policy.md)|
|**Atestación de estado**|No disponible|Disponible|


## <a name="advantages-of-mdm-windows-pc-management"></a>Ventajas de la administración de equipos con Windows de MDM
La administración de equipos con Windows con la moderna administración de dispositivos móviles presenta las siguientes ventajas:
- **Escalabilidad**: escalas de administración de MDM con administración de Intune en la nube. El software cliente de Intune está limitado a 7000 equipos.
- **Simplicidad**: uso de modernas funcionalidades de administración que se incluyen en el sistema operativo sin depender del software cliente descargado.
- **Coherencia**: los equipos con Windows se administran como todos los demás dispositivos móviles de la organización
<!-- - **Cloud optimization** - -->
