---
title: Usar plantillas para dispositivos Windows 10 en Microsoft Intune - Azure | Microsoft Docs
description: Use plantillas administrativas de Microsoft Intune para crear grupos de valores de configuración para dispositivos Windows 10. Use estos valores en un perfil de configuración de dispositivo para controlar programas de Office, Microsoft Edge, proteger características de Internet Explorer, controlar el acceso a OneDrive, usar características de escritorio remoto, habilitar la reproducción automática, establecer la configuración de administración de energía, usar la impresión a través de HTTP, usar otras opciones de inicio de sesión de usuario y controlar el tamaño del registro de eventos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 608f9045d676a756c4ee7440072040075e497605
ms.sourcegitcommit: 7269abaefb2857bc8b343896bb2138bdb01bf8dc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70214336"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Usar plantillas de Windows 10 para configurar opciones de directiva de grupo en Microsoft Intune

Al administrar dispositivos en una organización, el objetivo es crear grupos de valores de configuración que se apliquen a otros grupos de dispositivos. Por ejemplo, hay varios grupos de dispositivos. Para el grupo A, se quiere asignar un conjunto concreto de valores configuración. Para el grupo B, se quiere asignar otro conjunto de valores configuración. También se quiere obtener una vista sencilla de los valores que se pueden configurar.

Esta tarea se puede realizar con **Plantillas administrativas** de Microsoft Intune. Las plantillas administrativas incluyen cientos de valores que controlan características de Microsoft Edge, Internet Explorer, programas de Microsoft Office, el escritorio remoto, OneDrive, contraseñas y PIN, y mucho más. Esta configuración permite a los administradores de grupo administrar las directivas de grupo mediante la nube.

La configuración de Windows es similar a la configuración de la directiva de grupo (GPO) en Active Directory (AD). Estas configuraciones están integradas en Windows y son [configuraciones con respaldo de ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) en las que se usa XML. La configuración de Office está probada por ADMX y utiliza la configuración de ADMX en los [archivos de plantillas administrativas de Office](https://www.microsoft.com/download/details.aspx?id=49030). Pero las plantillas de Intune están totalmente basadas en la nube. Ofrecen una manera simple y sencilla de configurar y de buscar la configuración deseada.

Las **plantillas administrativas** están integradas en Intune y no requieren personalizaciones, ni siquiera el uso de OMA-URI. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores de plantilla como centro único para administrar los dispositivos Windows 10.

En este artículo se enumeran los pasos para crear una plantilla para dispositivos Windows 10 y se muestra cómo filtrar todas las opciones disponibles en Intune. Cuando se crea la plantilla, se crea un perfil de configuración de dispositivo. Luego se puede asignar o implementar este perfil en los dispositivos Windows 10 de la organización.

## <a name="before-you-begin"></a>Antes de comenzar

- Algunos de estos ajustes están disponibles a partir de la versión 1703 (RS2) de Windows 10. Para obtener la mejor experiencia, se recomienda usar Windows 10 Enterprise versión 1903 (19H1) y posteriores.

- La configuración de Windows usa los [CSP de directivas de Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies). El CSP funciona en diferentes ediciones de Windows, como por ejemplo, Home, Professional, Enterprise, etcétera. Para ver si un CSP funciona en una edición específica, vaya a [CSP de directivas de Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies).

## <a name="create-a-template"></a>Crear una plantilla

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: Escriba un nombre para el perfil.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
    - **Tipo de perfil**: seleccione **Plantillas administrativas**.

4. Seleccione **Crear**. En la nueva ventana, seleccione **Configuración**. Se enumeran todos los valores y puede usar las flechas Anterior y Siguiente para ver más:

    ![Lista de ejemplo de valores y uso de los botones Anterior y Siguiente](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > La configuración de Windows en Intune se correlaciona con la ruta de acceso de la directiva de grupo local que se ve en el Editor de directivas de grupo local (`gpedit`).

5. De forma predeterminada, la lista desplegable muestra **Todos los productos**. Desde la lista, también puede filtrar la configuración para que solo muestre la configuración de **Windows**, la de **Office** o la de **Microsoft Edge**:

    ![Filtrado de la lista para mostrar todas las configuraciones de Windows o de Office en las plantillas administrativas de Intune](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > La configuración de Microsoft Edge se aplica a:
    >
    > - Windows 10 RS4 y versiones más recientes con [KB 4512509](https://support.microsoft.com/kb/4512509) instalado.
    > - Windows 10 RS5 y versiones más recientes con [KB 4512534](https://support.microsoft.com/kb/4512534) instalado.
    > - Windows 10 19H1 y versiones más recientes con [KB 4512941](https://support.microsoft.com/kb/4512941) instalado.

6. Seleccione cualquier valor. Por ejemplo, filtre por **Office** y seleccione **Activar exploración restringida**. Se muestra una descripción detallada del valor. Elija **Habilitado**, **Deshabilitado** o bien deje el valor como **Sin configurar** (valor predeterminado). La descripción detallada también explica lo que sucede cuando se elige **Habilitado**, **Deshabilitado** o **Sin configurar**.
7. Haga clic en **Aceptar** para guardar los cambios.

Siga examinando la lista de valores y configure los que quiera en el entorno. Estos son algunos ejemplos:

- Use el valor **Configuración de notificaciones para macros de VBA** para controlar las macros de VBA en diferentes programas de Microsoft Office, incluidos Word y Excel.
- Use el valor **Permitir la descarga de archivos** para permitir o evitar las descargas desde Internet Explorer.
- Use **Requerir una contraseña al activar el equipo (conectado)** para solicitar una contraseña a los usuarios cuando los dispositivos se activan del modo de suspensión.
- Use el valor **Descargar los controles ActiveX no firmados** para evitar que los usuarios descarguen controles ActiveX no firmados de Internet Explorer.
- Use el valor **Desactivar Restaurar sistema** para permitir o evitar que los usuarios ejecuten una restauración del sistema en el dispositivo.
- Use la opción de **permitir la importación de favoritos** para permitir o impedir que los usuarios importen favoritos de otro explorador en Microsoft Edge.
- Y mucho más...

## <a name="find-some-settings"></a>Buscar algunos valores

Hay cientos de valores disponibles en estas plantillas. Para que sea más fácil encontrar un valor concreto, use las características integradas:

- En la plantilla, seleccione las columnas **Configuración**, **Estado**, **Tipo de configuración** o **Ruta** para ordenar la lista. Por ejemplo, seleccione la columna **Ruta** para ver todos los valores de la ruta de acceso de `Microsoft Excel`:

  ![Haga clic en la ruta de acceso para mostrar todas las configuraciones agrupadas por la directiva de grupo o la ruta de acceso de ADMX en las plantillas administrativas de Intune.](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- En la plantilla, use el cuadro **Buscar** para buscar valores específicos. Puede buscar por título de configuración o por la ruta de acceso. Por ejemplo, busque `copy`. Aparecen todos los valores con `copy`:

  ![Búsqueda de copia para mostrar las configuraciones de Windows y Office en las plantillas administrativas de Intune](./media/administrative-templates-windows/search-copy-settings.png) 

  En otro ejemplo, busque `microsoft word`. Ve todos los valores que puede establecer para el programa Microsoft Word. Busque `explorer` para ver todos los valores de Internet Explorer que puede agregar a la plantilla.

## <a name="next-steps"></a>Pasos siguientes

Se crea la plantilla, pero todavía no hace nada. A continuación, [asigne la plantilla, también denominada perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
