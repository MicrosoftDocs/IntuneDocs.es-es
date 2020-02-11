---
title: Implementación de aplicaciones Windows 10 con Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre los escenarios de implementación de aplicaciones de Windows 10 disponibles con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa4510b95e1e84d9f94158833dac555daa33c690
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912569"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>Implementación de aplicaciones Windows 10 con Microsoft Intune 

Microsoft Intune admite una variedad de tipos de aplicaciones y escenarios de implementación en dispositivos Windows 10. Después de agregar una aplicación a Intune, puede asignarla a usuarios y dispositivos. En este artículo se proporcionan más detalles sobre los escenarios admitidos en Windows 10 y también se tratan los detalles clave que se deben tener en cuenta al implementar aplicaciones en Windows. 

Las aplicaciones de línea de negocio (LOB) y las de Microsoft Store para Empresas son los tipos de aplicaciones que se admiten en los dispositivos Windows 10. Las extensiones de archivo de las aplicaciones Windows incluyen .msi, .appx y .appxbundle.  

> [!Note]
> Para implementar aplicaciones modernas, necesita al menos:
> - Para Windows 10 1803, [23 de mayo de 2018: KB4100403 (compilación del SO 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - Para Windows 10 1709, [21 de junio de 2018: KB4284822 (compilación del SO 16299.522)](https://support.microsoft.com/help/4284822).
>
> Solo Windows 10 1803 y versiones posteriores admiten la instalación de aplicaciones cuando no hay ningún usuario primario asociado.
>
> No se admite la implementación de aplicaciones de línea de negocios en dispositivos que ejecuten ediciones Windows 10 Home.

## <a name="supported-windows-10-app-types"></a>Tipos de aplicaciones compatibles con Windows 10

Se admiten tipos de aplicación específicos en función de la versión de Windows 10 que ejecutan los usuarios. En la tabla siguiente se proporciona el tipo de aplicación y la compatibilidad con Windows 10.

| Tipo de aplicación | Inicio | Pro | Business | Enterprise | Education | Modo S | Hololense | SurfaceHub | WCOS | Móvil |
|----------------|------|-----|----------|------------|-----------|--------|-----------|------------|------|--------|
|  .MSI | No | Sí | Sí | Sí | Sí | No | No | No | No | No |
| .IntuneWin | No | Sí | Sí | Sí | Sí | 19H2+ | No | No | No | No |
| Office C2R | No | Sí | Sí | Sí | Sí | No | No | No | No | No |
| LOB: APPX/MSIX | Sí | Sí | Sí | Sí | Sí | Sí | Sí | Sí | Sí | Sí |
| MSFB sin conexión | Sí | Sí | Sí | Sí | Sí | Sí | Sí | Sí | Sí | Sí |
| MSFB en línea | Sí | Sí | Sí | Sí | Sí | Sí | RS4+ | Sí | Sí | Sí |
| Web Apps | Sí | Sí | Sí | Sí | Sí | Sí | Sí<sup>1 | Sí<sup>1 | Sí | Sí |
| Vínculo de la Tienda | Sí | Sí | Sí | Sí | Sí | Sí | Sí | Sí | Sí | Sí |

<sup>1</sup> Iniciar solo desde el portal de empresa.

> [!NOTE]
> Todos los tipos de aplicaciones de Windows requieren inscripción.

## <a name="windows-10-lob-apps"></a>Aplicaciones de línea de negocios de Windows 10

Puede firmar y cargar aplicaciones de línea de negocios de Windows 10 en la consola de administración de Intune. Pueden incluir aplicaciones modernas, como las aplicaciones de la Plataforma universal de Windows (UWP) y los paquetes de aplicaciones de Windows (AppX), así como las aplicaciones de Win 32, como los archivos de paquete de Microsoft Installer (MSI) simples. El administrador debe cargar e implementar manualmente las actualizaciones de las aplicaciones de línea de negocios. Estas actualizaciones se instalan automáticamente en los dispositivos de usuario que tienen instalada la aplicación. No es necesaria la intervención del usuario y el este no tiene ningún control sobre las actualizaciones. 

## <a name="microsoft-store-for-business-apps"></a>Aplicaciones de la Tienda Microsoft para Empresas

Las aplicaciones de Microsoft Store para Empresas son aplicaciones modernas que se compran en el portal de administración de Microsoft Store para Empresas. Después se sincronizan a través de Microsoft Intune para administrarlas. Las aplicaciones pueden ser con licencia en línea o con licencia sin conexión. Microsoft Store administra directamente las actualizaciones, sin necesidad de que el administrador realice ninguna acción adicional. También puede evitar las actualizaciones de aplicaciones específicas mediante un identificador uniforme de recursos (URI) personalizado. Para obtener más información, vea [Administración de aplicaciones empresariales - Impedir las actualizaciones automáticas de la aplicación](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). El usuario final también puede deshabilitar las actualizaciones de todas las aplicaciones de Microsoft Store para Empresas en el dispositivo. 

### <a name="categorize-microsoft-store-for-business-apps"></a>Categorización de aplicaciones de Microsoft Store para Empresas 
Para categorizar aplicaciones de Microsoft Store para Empresas: 

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones**. 
3. Seleccione una aplicación de Microsoft Store para Empresas. A continuación, seleccione **Propiedades** > **Información de la aplicación** > **Categoría**. 
4. Seleccione una categoría.

## <a name="install-apps-on-windows-10-devices"></a>Instalación de aplicaciones en dispositivos Windows 10
Según el tipo de aplicación, puede instalar la aplicación en un dispositivo Windows 10 de una de dos maneras:

- **Contexto de usuario**: cuando se implementa una aplicación en el contexto de usuario, la aplicación administrada se instala para ese usuario en el dispositivo cuando inicie sesión en el dispositivo. Tenga en cuenta que la instalación de la aplicación no surte efecto hasta que el usuario inicie sesión en el dispositivo. 
  - Las aplicaciones de línea de negocio modernas y las de Microsoft Store para Empresas (en línea y sin conexión) se pueden implementar en el contexto de usuario. Serán compatibles con las intenciones obligatorias y disponibles.
  - Las aplicaciones Win32 compiladas en modo de usuario o modo dual pueden implementarse en el contexto del usuario y admitir tanto intenciones obligatorias como disponibles. 
- **Contexto de dispositivo**: al implementarse una aplicación en el contexto de dispositivo, la aplicación administrada se instala directamente en el dispositivo por Intune.
  - Solo las aplicaciones de línea de negocio modernas y las de Microsoft Store para Empresas con licencia sin conexión se pueden implementar en el contexto de dispositivo. Estas aplicaciones solo admiten la intención obligatoria.
  - Las aplicaciones Win32 compiladas en modo máquina o modo dual pueden implementarse en el contexto del usuario y solo admiten la intención obligatoria.

> [!NOTE]
> En las aplicaciones Win32 compiladas en modo dual, el administrador debe seleccionar si la aplicación funcionará en modo de usuario o modo máquina en todas las asignaciones asociadas con esa instancia. No se puede cambiar el contexto de implementación por asignación.  

Las aplicaciones solo se pueden instalar en el contexto de dispositivo cuando las admite el dispositivo y el tipo de aplicación de Intune. Puede instalar los siguientes tipos de aplicaciones en el contexto de dispositivo y asignar estas aplicaciones a un grupo de dispositivos:

- Aplicaciones Win32
- Aplicaciones de Microsoft Store para Empresas con licencias sin conexión
- Aplicaciones LOB (MSI, appx y MSIX)
- Office 365 ProPlus

Las aplicaciones de línea de negocio de Windows (en concreto, appx y MSIX) y de Microsoft Store para Empresas (aplicaciones sin conexión) que haya seleccionado para instalar en el contexto del dispositivo deben asignarse a un grupo de dispositivos. Se produce un error en la instalación si una de estas aplicaciones está implementada en el contexto del usuario. El siguiente estado y error aparecen en la consola de administración:
  - Estado: erróneo.
  - Error: un usuario no puede ser destino de una instalación de contexto de dispositivo.

> [!IMPORTANT]
> Cuando se usa en combinación con un escenario preferencial de Autopilot, no hay ningún requisito para las aplicaciones de línea de negocio y de Microsoft Store para Empresas implementadas en el contexto de dispositivo para establecer como destino un grupo de dispositivos. Para más información, consulte [Implementación preferencial de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove).

> [!Note]
> Después de guardar una asignación de aplicación con una implementación específica, no puede modificar el contexto de esa asignación, excepto para las aplicaciones modernas. En el caso de las aplicaciones modernas, puede cambiar el contexto del contexto de usuario al contexto de dispositivo. 

Si hay un conflicto en las directivas de un solo usuario o dispositivo, se aplican las siguientes prioridades:
- Una directiva de contexto de dispositivo tiene una prioridad mayor que una directiva de contexto de usuario. 
- Una directiva de instalación tiene una prioridad mayor que una directiva de desinstalación.

Para obtener más información, vea [Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune](apps-inc-exl-assignments.md). Para obtener más información sobre los tipos de aplicaciones en Intune, vea [Incorporación de aplicaciones a Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Pasos siguientes

- [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md)
- [Supervisión de aplicaciones](apps-monitor.md)
