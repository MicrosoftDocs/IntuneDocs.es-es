---
title: "Comparación de las opciones de administración de equipos con Windows"
description: "Inscripción de dispositivos iOS de empresa mediante el Programa de inscripción de dispositivos (DEP) de Apple o Apple Configurator"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 37c4c3a1b51479b1a6450cc66ab502d579804015
ms.sourcegitcommit: f100c943a635f5a08254ba7cf30f1aaebb7e810e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2017
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Comparación de la administración de equipos con Windows como dispositivos móviles o equipos

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Las organizaciones pueden usar Microsoft Intune para administrar equipos con Windows como dispositivos móviles con la administración de dispositivos móviles (MDM) o como equipos con el software cliente de Intune.  Microsoft recomienda que los clientes usen la solución de administración de MDM siempre que sea posible. Para ayudarle a entender mejor las diferencias entre estas opciones, en la tabla siguiente se ofrece una comparación de las dos opciones de administración.

|**Funcionalidad/escenario** |**Windows como equipo**<br>Cliente de software de Intune | **Windows como dispositivo móvil**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Sistemas operativos** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Compatibilidad con el portal de Intune** |[Consola de Silverlight](https://manage.microsoft.com)|[Portal de Azure](https://portal.azure.com) |
|**Acceso condicional**|No disponible|Available <br>[¿Qué es el acceso condicional?](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)|
|**Inscripción masiva**|No disponible|Available <br>[Inscripción masiva para dispositivos Windows](https://docs.microsoft.com/intune-azure/enroll-devices/bulk-enroll-windows)|
|**Perfiles de dispositivo**|No disponible|Available <br>[¿Qué son los perfiles de dispositivo de Microsoft Intune?](https://docs.microsoft.com/intune-azure/configure-devices/what-are-device-profiles)|
|**Inscripción sin agente**|No disponible |Available<br>[Inscribir dispositivos Windows](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-windows-devices)|
|**Administración de actualizaciones de software**| Actualizaciones de Windows y actualizaciones de aplicaciones de Microsoft<br>[Mantener los equipos Windows al día con las actualizaciones de software](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)|Tienda Microsoft para Empresas para actualizaciones de aplicaciones de Windows 10 y Microsoft<br> [Configurar Windows Update para empresas](https://docs.microsoft.com/intune-azure/configure-devices/how-to-configure-windows-update-for-business) |
|**Administración de licencias de software**|Available <br>[Administrar contratos de licencia de software de equipos Windows](https://docs.microsoft.com/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)|Tienda Microsoft para Empresas (solo aplicaciones .appx)<br>[Administración de aplicaciones adquiridas a través de la Tienda Windows para empresas](https://docs.microsoft.com/intune-azure/manage-apps/wsfb-apps)|
|**Inventario**|Available <br>[Visualización del inventario de software y hardware para equipos Windows](https://docs.microsoft.com/intune/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune)|Available <br>[Supervisión de la información de las aplicaciones](https://docs.microsoft.com/intune/apps-monitor)<br>[What is device management](https://docs.microsoft.com/intune/device-management) (¿Qué es la administración de dispositivos?)|
|**Directiva de Firewall de Windows**|Available <br>[Ayudar a proteger los equipos de Windows mediante directivas del Firewall de Windows](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune) |No disponible|
|**Protección antimalware**|Endpoint Protection<br>[Ayudar a proteger los equipos de Windows con Endpoint Protection](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|Windows Defender<br>[Configuración de Windows Defender](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-windows-10#windows-defender-settings)|
|**Asistencia remota** |TeamViewer<br>[Solicitar y proporcionar asistencia remota para equipos con Windows](https://docs.microsoft.com/intune/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune)|No disponible |
|**Implementación de aplicaciones** | No está disponible para la Tienda Microsoft para Empresas. Solo para<br>.exe, .appx, y varios archivos .msi<br>[Agregar aplicaciones para PC Windows que ejecutan el software cliente de Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)|Disponible para aplicaciones de la Tienda Microsoft y de línea de negocio<br>[Adición de aplicaciones de la Tienda Windows](https://docs.microsoft.com/intune/store-apps-windows)<br>[Adición de aplicaciones de línea de negocio (LOB) de Windows](https://docs.microsoft.com/intune/lob-apps-windows)|
|**Protección de aplicaciones**|No disponible|Available <br>[¿Qué son las directivas de protección de aplicaciones?](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy)|


### <a name="advantages-of-mdm-windows-pc-management"></a>Ventajas de la administración de equipos con Windows de MDM
La administración de equipos con Windows con la moderna administración de dispositivos móviles presenta las siguientes ventajas:
- **Escalabilidad**: escalas de administración de MDM con administración de Intune en la nube. El software cliente de Intune está limitado a 7000 equipos.
- **Simplicidad**: uso de modernas funcionalidades de administración que se incluyen en el sistema operativo sin depender del software cliente descargado.
- **Coherencia**: los equipos con Windows se administran como todos los demás dispositivos móviles de la organización
<!-- - **Cloud optimization** - -->
