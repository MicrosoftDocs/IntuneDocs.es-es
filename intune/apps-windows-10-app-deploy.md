---
title: Implementación de aplicaciones Windows 10 con Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre los escenarios de implementación de aplicaciones de Windows 10 disponibles con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c853608f46bb01263ddd08193f729cdfb018fed9
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550069"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Implementación de aplicaciones Windows 10 con Microsoft Intune 

En la actualidad, Microsoft Intune admite una variedad de tipos de aplicaciones y escenarios de implementación en dispositivos Windows 10. Después de agregar una aplicación a Intune, puede asignarla a usuarios y dispositivos. En la información siguiente se proporcionan más detalles relacionados con los escenarios de Windows 10 admitidos. Además, en la información siguiente se proporcionan detalles clave para tener en cuenta al implementar aplicaciones en Windows. 

Las aplicaciones de línea de negocio (LOB) y las de Microsoft Store para Empresas son los tipos de aplicaciones que se admiten en los dispositivos Windows 10. Las extensiones de archivo de las aplicaciones Windows incluyen **.msi**, **.appx** y **.appxbundle**.  

> [!Note]
> Las actualizaciones de Windows 10 mínimas necesarias para implementar aplicaciones modernas son los siguientes:
> - Para Windows 10 1803, [23 de mayo de 2018: KB4100403 (compilación del SO 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - Para Windows 10 1709, [21 de junio de 2018: KB4284822 (compilación del SO 16299.522)](https://support.microsoft.com/help/4284822).
>
> Solo Windows 10 1803 y versiones posteriores admiten la instalación de aplicaciones cuando no hay ningún usuario primario asociado.

## <a name="windows-10-line-of-business-apps"></a>Aplicaciones de línea de negocio de Windows 10

Las aplicaciones LOB de Windows 10 se firman y se cargan en la consola de administración de Intune y pueden incluir aplicaciones modernas, como las aplicaciones de la Plataforma universal de Windows (UWP) y los paquetes de aplicaciones de Windows (AppX), así como las aplicaciones de Win 32, como los archivos de paquete de Microsoft Installer (MSI) simples. El administrador debe cargar manualmente e implementar todas las actualizaciones de las aplicaciones LOB. Las actualizaciones que se implementan se instalan de forma automática en los dispositivos de usuario final en los que se ha instalado la aplicación sin intervención del usuario. El usuario no tiene control sobre las actualizaciones. 

## <a name="microsoft-store-for-business-apps"></a>Aplicaciones de Tienda Microsoft para Empresas

Las aplicaciones de Microsoft Store para Empresas son aplicaciones modernas que se compran en el portal de administración de Microsoft Store para Empresas y se sincronizan a través de Microsoft Intune para administrarlas. Las aplicaciones pueden ser **con licencia en línea** o **con licencia sin conexión**. Las actualizaciones de las aplicaciones de Microsoft Store para Empresas se administran directamente mediante Microsoft Store, sin ninguna acción adicional exigida por el administrador. El administrador también puede evitar las actualizaciones de aplicaciones específicas mediante un identificador uniforme de recursos (URI) personalizado. Para obtener más información, vea [Administración de aplicaciones empresariales - Impedir las actualizaciones automáticas de la aplicación](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). En el dispositivo, el usuario final también puede deshabilitar las actualizaciones de todas las aplicaciones de Microsoft Store para Empresas en el dispositivo. 

### <a name="categorize-microsoft-store-for-business-apps"></a>Categorización de aplicaciones de Microsoft Store para Empresas 
Para categorizar las aplicaciones de la Tienda Microsoft para Empresas, siga estos pasos: 

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Aplicaciones cliente** > **Aplicaciones** > seleccione Aplicación de la Tienda Microsoft para Empresas > **Información de la aplicación** > **Categoría**. 
3. Seleccione una categoría en el menú desplegable.

## <a name="installing-apps-on-windows-10-devices"></a>Instalación de aplicaciones en dispositivos Windows 10
Según el tipo de aplicación, se puede instalar en un dispositivo Windows 10 de una de dos maneras:

- **Contexto de usuario**: cuando se implementa una aplicación en el contexto de usuario, la aplicación administrada se instalará para ese usuario en el dispositivo cuando inicie sesión en el dispositivo. Tenga en cuenta que la instalación de la aplicación no surtirá efecto hasta que el usuario inicie sesión en el dispositivo. 
  - Las aplicaciones de línea de negocio modernas y las de Microsoft Store para Empresas (en línea y sin conexión) se pueden implementar en el contexto de usuario y serán compatibles con las intenciones Requerido y Disponible.
  - Las aplicaciones Win32 compiladas en **modo de usuario** o **modo dual** pueden implementarse en el contexto del usuario y admitir tanto intenciones **obligatorias** como **disponibles**. 
- **Contexto de dispositivo**: al implementarse una aplicación en el contexto de dispositivo, la aplicación administrada se instalará directamente en el dispositivo de Intune.
  - Solo las aplicaciones de línea de negocio modernas y las de Microsoft Store para Empresas con licencia sin conexión se pueden implementar en el contexto de dispositivo y solo admitirán la intención Requerido.
  - Las aplicaciones Win32 compiladas en **modo máquina** o **modo dual** pueden implementarse en el contexto del usuario y solo admitirán la intención **obligatoria**.

> [!NOTE]
> En las aplicaciones Win32 compiladas en **modo dual**, el administrador debe seleccionar si la aplicación funcionará en **modo de usuario** o **modo máquina** en todas las asignaciones asociadas con esa instancia. No se puede cambiar el contexto de implementación por asignación.  

Cuando una aplicación se implementa en el contexto de dispositivo, solo se realizará correctamente la instalación cuando el destino sea un dispositivo que admite el contexto de dispositivo. Además, la implementación en el contexto de dispositivo admite las condiciones siguientes:
- Si una aplicación se implementa en el contexto de dispositivo y está destinada a un usuario, se producirá un error en la instalación y se mostrarán el estado y el error siguientes en la consola de administración:
  - Estado: erróneo.
  - Error: un usuario no puede ser destino de una instalación de contexto de dispositivo.
- Si una aplicación se implementa en el contexto de dispositivo pero se destina a un dispositivo que no lo admite, se producirá un error en la instalación con el estado y el error siguientes en la consola de administración:
  - Estado: erróneo.
  - Error: esta plataforma no admite la instalación de contexto de dispositivo. 

> [!Note]
> Después de guardar una asignación de aplicación con una implementación específica, no se puede modificar el contexto de esa asignación, excepto para las aplicaciones modernas. En el caso de las aplicaciones modernas, el contexto se puede cambiar de contexto de usuario a contexto de dispositivo. 

En caso de que haya un conflicto en las directivas en un único usuario o dispositivo, las prioridades de directiva que se usarán para determinar la directiva final son las siguientes:
- Una directiva de contexto de dispositivo tiene una prioridad mayor que una directiva de contexto de usuario. 
- Una directiva de instalación tiene una prioridad mayor que una directiva de desinstalación.

Para obtener más información sobre la asignación de aplicaciones con Microsoft Intune, vea [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md) e [Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune](apps-inc-exl-assignments.md). Para obtener más información sobre los tipos de aplicaciones en Intune, vea [Incorporación de aplicaciones a Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Pasos siguientes

- Para obtener más información sobre cómo asignar aplicaciones a los grupos, vea [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).
- Para más información sobre la supervisión de las asignaciones de aplicaciones, consulte [Supervisión de las aplicaciones](apps-monitor.md).
