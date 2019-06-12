---
title: Administración de dispositivos de forma remota en Microsoft Intune - Azure | Microsoft Docs
description: Consulte los roles necesarios para usar TeamViewer, cómo instalar el conector de TeamViewer y una guía paso a paso para administrar dispositivos de forma remota usando Microsoft Intune en Azure Portal
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96c05543884e0d9a00b570fb9ed4be1cdef65ca0
ms.sourcegitcommit: 1ba785f6e51517b63588a292ab5c45b9d9144b72
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "66841133"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>Uso de TeamViewer para administrar dispositivos de Intune de forma remota

Los dispositivos administrados por Intune pueden administrarse de forma remota con [TeamViewer](https://www.teamviewer.com). TeamViewer es un programa de terceros que se adquiere por separado. En este tema se muestra cómo configurar TeamViewer en Intune y cómo administrar un dispositivo de forma remota. 

## <a name="prerequisites"></a>Requisitos previos

- Use un dispositivo compatible. Los dispositivos Android, Windows, iOS y macOS administrados por Intune se pueden administrar de forma remota. Es posible que TeamViewer no sea compatible con Windows Holographic (HoloLens), Windows Team (Surface Hub) o Windows 10 S. Si tiene dudas sobre la compatibilidad, consulte [TeamViewer](https://www.teamviewer.com) para ver las actualizaciones.

- El administrador de Intune en Azure Portal debe tener los siguientes [roles de Intune](role-based-access-control.md):  

    - **Actualizar asistencia remota**: Permite a los administradores modificar la configuración del conector de TeamViewer.
    - **Solicitar asistencia remota**: Permite a los administradores iniciar una nueva sesión de asistencia remota para cualquier usuario. Los usuarios con este rol no están limitados por ningún rol de Intune dentro de un ámbito. Además, los grupos de dispositivos o usuarios a los que se ha asignado un rol de Intune dentro de un ámbito también pueden solicitar asistencia remota. 

- Cuenta de [TeamViewer](https://www.teamviewer.com) con las credenciales de inicio de sesión. Solo algunas licencias TeamViewer pueden admitir la integración con Intune. Para las necesidades específicas de TeamViewer, consulte [Partner de integración de TeamViewer: Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/).

Al usar TeamViewer, permite que el conector de TeamViewer para Intune cree sesiones de TeamViewer, lea datos de Active Directory y guarde el token de acceso de la cuenta de TeamViewer.

## <a name="configure-the-teamviewer-connector"></a>Configuración del conector de TeamViewer

Para proporcionar asistencia remota a los dispositivos, configure el conector de TeamViewer para Intune siguiendo estos pasos:

1. En [Azure Portal](https://portal.azure.com), seleccione **All Services** (Todos los servicios) y busque **Microsoft Intune**.
2. En **Microsoft Intune**, seleccione **Dispositivos** y, luego, **TeamViewer Connector**.
3. Seleccione **Conectar** y acepte el contrato de licencia.
4. Seleccione **Inicie sesión en TeamViewer para autorizar**.
5. Se abre una página web en el sitio de TeamViewer. Escriba sus credenciales de la licencia de TeamViewer y haga clic en **Iniciar sesión**.

## <a name="remotely-administer-a-device"></a>Administración remota de un dispositivo

Una vez configurado el conector, estará listo para administrar un dispositivo de forma remota. Use los pasos siguientes: 

1. En [Azure Portal](https://portal.azure.com), seleccione **All services** (Todos los servicios) y busque **Microsoft Intune**.
2. En **Microsoft Intune**, seleccione **Dispositivos** y, luego, **Todos los dispositivos**.
3. En la lista, seleccione el dispositivo que quiere administrar de forma remota. En las propiedades del dispositivo, seleccione **Nueva sesión de Asistencia remota**.
4. Cuando Intune se conecte al servicio TeamViewer, verá información sobre el dispositivo. Elija **Conectar** para iniciar la sesión remota.

![Ejemplo de uso de TeamViewer para administrar un dispositivo Android de forma remota](./media/android-teamviewer.png)

Al iniciar una sesión remota, los usuarios verán una marca de notificación en el icono de la aplicación Portal de empresa de su dispositivo. También se mostrará una notificación cuando abra la aplicación. Los usuarios pueden aceptar la solicitud de asistencia remota.

> [!NOTE]
> Los dispositivos Windows inscritos usando métodos "sin usuarios", como DEM o WCD, no muestran la notificación de TeamViewer en la aplicación Portal de empresa. En estos casos, se recomienda usar el portal de TeamViewer para generar la sesión.

En TeamViewer, puede completar una serie de acciones en el dispositivo, incluida la toma del control de este. Para obtener más detalles sobre lo que puede hacer, consulte los [manuales de TeamViewer](https://www.teamviewer.com/support/documents/).

Cuando haya finalizado, cierre la ventana de TeamViewer.
