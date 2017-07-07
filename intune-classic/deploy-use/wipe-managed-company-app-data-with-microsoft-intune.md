---
title: "Borrar los datos administrados de la aplicación de la empresa"
description: Aprenda a quitar selectivamente datos de la empresa desde dispositivos de forma remota.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7025bdd5d89e52f1c99f9cd834232daf324f3285
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="wipe-company-app-data-with-intune-mam"></a>Borrado de datos de aplicaciones de empresa con Intune MAM

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Cuando un dispositivo se pierde o lo roban, o cuando un empleado deja la empresa, le interesa asegurarse de que se eliminan del dispositivo los datos de la aplicación de empresa. Pero es posible que no quiera quitar del dispositivo los datos personales, sobre todo si se trata de un dispositivo propiedad de un empleado.

Para quitar de forma selectiva datos de la aplicación de empresa, siga los pasos de este tema para crear una solicitud de borrado. Una vez finalizada la solicitud, la próxima vez que la aplicación se ejecute en el dispositivo, los datos de la empresa se quitarán de la aplicación.

>[!IMPORTANT]
> Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa. No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. Actualmente, esto solo se aplica a la aplicación Microsoft Outlook.

## <a name="create-a-wipe-request"></a>Crear una solicitud de borrado

1.  Inicie sesión en el [Portal de Azure](https://portal.azure.com).

2.  Elija **More Services** (Más servicios), escriba **Intune** en el cuadro de texto de filtro y seleccione **Intune App Protection** (Protección de aplicaciones de Intune). Se abre la hoja de administración de aplicaciones móviles de Intune.

    ![Captura de pantalla de la hoja Nueva solicitud de borrado](../media/AppManagement/wipe-request-mam-main-blade.png)

2.  En la hoja **Configuración**, elija **Solicitudes de borrado**.

3.  Elija **Nueva solicitud de borrado**. Se abre la hoja **Nueva solicitud de borrado**.

    ![Captura de pantalla de la hoja Nueva solicitud de borrado](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

4.  Elija **Usuario** para abrir la hoja **Usuario** y seleccione el usuario cuyos datos de aplicación quiera borrar.

5.  Elija **Dispositivo**. Se abre la hoja **Dispositivo** que muestra todos los dispositivos asociados al usuario seleccionado. También proporciona dos columnas: el nombre del dispositivo, que es un nombre descriptivo definido por el usuario, y el tipo de dispositivo, la plataforma del dispositivo. Seleccione el dispositivo que desea borrar.

6.  Ahora está de nuevo en la hoja **Nueva solicitud de borrado**. Seleccione **Aceptar** para realizar una solicitud de borrado. 

El servicio crea y realiza el seguimiento de una solicitud de borrado independiente para cada aplicación protegida en el dispositivo, y del usuario asociado a la solicitud de borrado.

>[!NOTE]
> También puede crear **solicitudes de borrado** si hace clic en el **icono de solicitud de borrado** en la hoja de administración de aplicaciones móviles de Intune.

## <a name="monitor-your-wipe-requests"></a>Supervisar las solicitudes de borrado de datos

Puede tener un informe resumido que muestre el estado general de la solicitud de borrado y que incluya el número de solicitudes pendientes y errores. Para obtener más información, siga estos pasos:

1.  En la hoja Administración de aplicaciones móviles de Intune, haga clic en el icono **Solicitudes de borrado**.

2.  En la hoja **Solicitud de borrado**, elija el icono **Solicitud de borrado** para abrir la hoja **Solicitud de borrado**.

3.  En la hoja **Solicitud de borrado**, puede ver la lista de solicitudes agrupadas según usuarios. Debido a que el sistema crea una solicitud de borrado para cada aplicación protegida que se ejecuta en el dispositivo, puede que vea varias solicitudes para un mismo usuario. Este estado indica si una solicitud de borrado está **pendiente**, ha provocado un **error** o si es **correcta**.

    ![Captura de pantalla de la hoja Nueva solicitud de borrado](../media/AppManagement/wipe-request-status-1.png)

Además, podrá ver el nombre del dispositivo, y su tipo, lo que puede ser útil cuando se lean los informes.

>[!IMPORTANT]
> El usuario debe abrir la aplicación de la que se vaya a realizar el borrado, que puede tardar hasta 30 minutos después de efectuar la solicitud.

## <a name="delete-a-wipe-request"></a>Eliminación de una solicitud de borrado

Los borrados con estado pendiente se muestran hasta que se eliminen manualmente.  Eliminación manual de una solicitud de borrado

1.  En la hoja Administración de aplicaciones móviles de Intune, haga clic en el icono **Solicitudes de borrado**.

2.  En la hoja **Solicitud de borrado**, elija el icono **Solicitud de borrado** para abrir la hoja **Solicitud de borrado**.

3.  Haga clic con el botón derecho en la solicitud de borrado que quiere eliminar y elija **Delete wipe request** (Eliminar solicitud de borrado).

    ![Captura de pantalla de la hoja Nueva solicitud de borrado](../media/AppManagement/delete-wipe-request.png)

4.  Se le pedirá que confirme la eliminación. Elija **Sí** o **No** y luego haga clic en **Aceptar**.


### <a name="see-also"></a>Consulte también
[Proteger datos mediante las directivas de administración de aplicaciones móviles con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Usar Azure Portal](azure-portal-for-microsoft-intune-mam-policies.md)
