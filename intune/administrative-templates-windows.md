---
title: Usar plantillas para dispositivos Windows 10 en Microsoft Intune - Azure | Microsoft Docs
description: Use plantillas administrativas de Microsoft Intune para crear grupos de valores de configuración para dispositivos Windows 10. Use estos valores en un perfil de configuración de dispositivo para controlar programas de Office, proteger características de Internet Explorer, controlar el acceso a OneDrive, usar características de escritorio remoto, habilitar la reproducción automática, establecer la configuración de administración de energía, usar la impresión a través de HTTP, usar otras opciones de inicio de sesión de usuario y controlar el tamaño del registro de eventos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d0426b63cb4601a73451ec9509ddea8e39271c29
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204978"
---
# <a name="windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Plantillas de Windows 10 para configurar opciones de directiva de grupo en Microsoft Intune

Al administrar dispositivos en una organización, el objetivo es crear un grupo de valores de configuración que se apliquen a diferentes grupos de dispositivos. Por ejemplo, hay varios grupos de dispositivos. Para el grupo A, se quiere asignar un conjunto concreto de valores configuración. Para el grupo B, se quiere asignar otro conjunto de valores configuración. También se quiere obtener una vista sencilla de los valores que se pueden configurar.

Esta tarea se puede realizar con **Plantillas administrativas** de Microsoft Intune. Las plantillas administrativas incluyen cientos de valores que controlan características de Internet Explorer, programas de Microsoft Office, el escritorio remoto, el acceso a OneDrive, el uso de una contraseña de imagen o un PIN para iniciar sesión, etc. Estas plantillas son similares a las opciones de directiva de grupo (GPO) de Active Directory (AD) y son [valores respaldados por ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) que usan XML. Pero las plantillas de Intune están completamente basadas en la nube. Ofrecen una manera más simple y sencilla de configurar y de buscar la configuración deseada.

Las **plantillas administrativas** están integradas en Intune y no requieren personalizaciones, ni siquiera el uso de OMA-URI. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores de plantilla como centro único para administrar los dispositivos Windows 10.

En este artículo se enumeran los pasos para crear una plantilla para dispositivos Windows 10 y se muestra cómo filtrar todas las opciones disponibles en Microsoft Intune. Cuando se crea la plantilla, se crea un perfil de configuración de dispositivo. Luego se puede asignar o implementar este perfil en los dispositivos Windows 10 de la organización.

> [!NOTE]
> Las plantillas administrativas son compatibles con los dispositivos independientes. Actualmente no se admiten en dispositivos administrados conjuntamente de System Center Configuration Manager (SCCM).

## <a name="create-a-template"></a>Crear una plantilla

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las siguientes propiedades:

    - **Nombre**: Escriba un nombre para el perfil.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
    - **Tipo de perfil**: seleccione **Plantillas administrativas (vista previa)**.

4. Seleccione **Crear**. En la nueva ventana, seleccione **Configuración**. Se enumeran todos los valores y puede usar las flechas Anterior y Siguiente para ver más:

    ![Lista de ejemplo de valores y uso de los botones Anterior y Siguiente](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. Seleccione cualquier valor. Por ejemplo, seleccione **Permitir la descarga de archivos**. Se muestra una descripción detallada del valor. Elija **Habilitar**, **Deshabilitar** o bien deje el valor como **Sin configurar** (valor predeterminado). La descripción detallada también explica lo que sucede cuando se elige **Habilitar**, **Deshabilitar** o **Sin configurar**.
6. Haga clic en **Aceptar** para guardar los cambios.

Siga examinando la lista de valores y configure los que quiera en el entorno. Estos son algunos ejemplos:

- Use el valor **Configuración de notificaciones para macros de VBA** para controlar las macros de VBA en diferentes programas de Microsoft Office, incluidos Word y Excel.
- Use el valor **Permitir la descarga de archivos** para permitir o evitar las descargas desde Internet Explorer.
- Use el valor **Requerir una contraseña al reactivar el equipo (conectado)** para solicitar una contraseña a los usuarios cuando los dispositivos se reactivan del modo de suspensión.
- Use el valor **Descargar los controles ActiveX no firmados** para evitar que los usuarios descarguen controles ActiveX no firmados de Internet Explorer.
- Use el valor **Desactivar Restaurar sistema** para permitir o evitar que los usuarios ejecuten una restauración del sistema en el dispositivo.
- Y mucho más...

## <a name="find-some-settings"></a>Buscar algunos valores

Hay cientos de valores disponibles en estas plantillas. Para que sea más fácil encontrar un valor concreto, use las características integradas:

- En la plantilla, seleccione las columnas **Configuración**, **Estado** o **Ruta** para ordenar la lista. Por ejemplo, seleccione la columna **Ruta** para ver todos los valores de la ruta de acceso de `Microsoft Excel`:

  ![Clic en Ruta para ordenar alfabéticamente](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- En la plantilla, use el cuadro **Buscar** para buscar valores específicos. Por ejemplo, busque `copy`. Aparecen todos los valores con `copy`:

  ![Clic en Ruta para ordenar alfabéticamente](./media/administrative-templates-windows/search-copy-settings.png)

  En otro ejemplo, busque `microsoft word`. Ve todos los valores que puede establecer para el programa Microsoft Word. Busque `explorer` para ver todos los valores de Internet Explorer que puede agregar a la plantilla.

## <a name="next-steps"></a>Pasos siguientes

Se crea la plantilla, pero todavía no hace nada. A continuación, [asigne la plantilla, también denominada perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
