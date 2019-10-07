---
title: Mover los datos de la cuenta de almacenamiento de datos de Intune
titleSuffix: Microsoft Intune
description: Comprenda cómo hacer copias de seguridad de los datos de almacenamiento de datos de Intune al mover la cuenta.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb86b066755c85208e9d9c2b5b823305f6011df9
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733652"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Mover los datos de la cuenta de almacenamiento de datos de Intune 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mediante la solicitud de un movimiento de cuenta, insta a que su centro de datos se cambie a otra ubicación. Tras el movimiento, el almacenamiento de datos se restablecerá y comenzará a grabar datos en la nueva ubicación según lo especificado el día en que comienza dicho movimiento. Para hacer una copia de seguridad de los datos del almacenamiento de datos anteriores, complete los pasos siguientes **antes** de mover la cuenta. La mayoría de las tablas de almacenamiento de datos conservan los datos durante 30 días, por lo que cualquier intervalo de datos en estas tablas ya no estará disponible 30 días después de mover la cuenta. Para más información sobre la duración de retención para tablas concretas, consulte [Modelo de datos de Almacenamiento de datos](reports-ref-data-model.md). 

## <a name="back-up-your-data-warehouse-data"></a>Copia de seguridad de los datos de almacenamiento de datos 

Para hacer una copia de seguridad de los datos de almacenamiento de datos, debe guardar dichos datos en un archivo *.csv* la API de almacenamiento de datos:  

1. Si es la primera vez que usa la API de almacenamiento de datos, siga el proceso de una sola vez proporcionado en el artículo [Obtener datos de la API de almacenamiento de datos de Intune con un cliente de REST](reports-proc-data-rest.md).
2. Use el ejemplo de PowerShell denominado [Access the Intune Data Warehouse with PowerShell](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell) (Acceso al almacenamiento de datos de Intune con PowerShell) para descargar todos los datos en archivos CSV. 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Copia de seguridad de los gráficos de tendencia desde Azure Portal

Algunos gráficos de tendencia en la vista de Azure Portal se restablecerán. Puede realizar una copia de seguridad de estos gráficos ejecutando el siguiente script en **Graph**:   

### <a name="terms--conditions-acceptance-reports"></a>Informes de aceptación de los términos y las condiciones
1. En Azure Portal, vaya a **Microsoft Intune** -> **Inscripción de dispositivos** -> **Términos y condiciones**.
2. Para cada elemento **Términos y condiciones**, seleccione **Informe de aceptación** y luego **Exportar**.
3. Guarde el informe localmente.
 
### <a name="app-protection-reports"></a>Informes de protección de la aplicación  
1. En Azure Portal, vaya a **Microsoft Intune** -> **Aplicaciones cliente** -> **Estado de protección de la aplicación**.
2. Haga clic en el icono de descarga (⤓) para guardar cada informe.

### <a name="device-configuration-charts"></a>Gráficos de configuración del dispositivo 
1. En Azure Portal, vaya a **Microsoft Intune** -> **Configuración del dispositivo**.
2. Mediante [Probador de Graph](https://developer.microsoft.com/graph/graph-explorer) de Microsoft, descargue los datos detrás de los gráficos. 
    - Para el estado de implementación de todos los perfiles de configuración de dispositivo para todos los dispositivos, consulte [Device deployment status](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content) (Estado de implementación de los dispositivos).

    - Para el estado de implementación de todos los perfiles de configuración de dispositivo para todos los usuarios, consulte [User deployment status](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content) (Estado de implementación de los usuarios).

    - Para el estado de implementación de perfil, consulte [Provide deployment status](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview) (Proporcionar estado de implementación).
  
    > [!NOTE]
    > Debe tener un token de autenticación válido para acceder a la configuración del dispositivo y la información de estado de implementación.

## <a name="device-enrollment-charts"></a>Gráficos de inscripción de dispositivos
1. En Azure Portal, vaya a **Microsoft Intune** -> **Inscripción de dispositivos**.
2. Mediante [Probador de Graph](https://developer.microsoft.com/graph/graph-explorer) de Microsoft, descargue los datos detrás de los gráficos.
    - Para el estado de inscripción, copie esta [consulta de estado de inscripción](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content) y péguela en [Probador de Graph](https://developer.microsoft.com/graph/graph-explorer).
    - Para errores de inscripción esta semana, copie esta [consulta de estado de inscripción](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content) y péguela en [Probador de Graph](https://developer.microsoft.com/graph/graph-explorer).

    > [!NOTE]
    > Debe tener un token de autenticación válido para acceder a los datos de inscripción de dispositivo. 

## <a name="after-a-data-warehouse-account-move"></a>Después de un movimiento de cuenta de almacenamiento de datos

Tras el movimiento de cuenta de almacenamiento de datos, verá en Intune que el almacenamiento de datos se ha restablecido y los datos ahora se almacenan en la nueva ubicación. Los gráficos y las opciones de exportación se restablecerán y verá una notificación, que, al hacer clic en ella, le dirigirá a un artículo que explica por qué se han restablecido los gráficos.  

## <a name="data-warehouse-move-example"></a>Ejemplo de movimiento del almacén de datos 

El cliente X solicita que un movimiento de cuenta se inicie el 06/01/2018. En respuesta a la solicitud, el cliente recibirá un vínculo para ver la documentación que detalla los pasos que se deben seguir si desea hacer una copia de seguridad de su almacenamiento de datos anterior. El 06/01/2018, el almacenamiento de datos y los gráficos que admite se restablecerán y comenzarán a almacenar datos en el nuevo centro de datos. 

## <a name="next-steps"></a>Pasos siguientes

- Conozca las [novedades semanales de Intune](../fundamentals/whats-new.md). También podrá obtener información sobre los próximos cambios, notificaciones importantes sobre el servicio e información sobre las versiones anteriores.
- Lea el [Blog de Microsoft Intune](https://go.microsoft.com/fwlink/?LinkID=273882).
