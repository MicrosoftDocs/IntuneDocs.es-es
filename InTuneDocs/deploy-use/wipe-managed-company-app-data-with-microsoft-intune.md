---
title: "Borrar los datos administrados de la aplicación de la empresa | Microsoft Intune"
description: Aprenda a quitar selectivamente datos de la empresa desde dispositivos de forma remota.
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: d32a66ee283906586e25173e736c02ee8bf23042


---

# <a name="wipe-managed-company-app-data-with-microsoft-intune"></a>Borrar los datos administrados de la aplicación de la empresa con Microsoft Intune
Cuando un dispositivo se pierde o lo roban, o cuando un empleado deja la empresa, le interesa asegurarse de que se eliminan del dispositivo los datos de la aplicación de empresa. Pero es posible que no quiera quitar del dispositivo los datos personales, sobre todo si se trata de un dispositivo propiedad de un empleado.

Para quitar de forma selectiva datos de la aplicación de empresa, siga los pasos de este tema para crear una solicitud de borrado. Una vez finalizada la solicitud, la próxima vez que la aplicación se ejecute en el dispositivo, los datos de la empresa se quitarán de la aplicación.
>[!NOTE]
> Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa. No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. Actualmente esto se aplica únicamente a la aplicación Microsoft Outlook.



## <a name="create-a-wipe-request"></a>Crear una solicitud de borrado

1.  En la hoja **Administración de aplicaciones móviles de Intune**, elija el icono **Solicitudes de borrado**.

    ![Captura de pantalla de la hoja Administración de aplicaciones móviles de Intune con los iconos de resumen](../media/AppManagement/AzurePortal_MAM_WipeRequests.png)

2.  Elija **Nueva solicitud de borrado**. Se abre la hoja **Nueva solicitud de borrado**.

    ![Captura de pantalla de la hoja Nueva solicitud de borrado](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

3.  Elija **Usuario** para abrir la hoja **Usuario** y seleccione el usuario cuyos datos de aplicación quiera borrar.

4.  Elija **Dispositivo**.  Se abrirá la hoja **Dispositivo** que enumera todos los dispositivos asociados con el usuario seleccionado.  Seleccione el dispositivo que desea borrar.

5.  Ahora está de nuevo en la hoja **Nueva solicitud de borrado**. Seleccione **Aceptar** para realizar una solicitud de borrado. El servicio crea y realiza el seguimiento de una solicitud de borrado de datos independiente para cada aplicación protegida en el dispositivo.


![Captura de pantalla del icono Solicitudes de borrado ](../media/AppManagement/AzurePortal_MAM_WipeRequestsSummary.png)

## <a name="monitor-your-wipe-requests"></a>Supervisar las solicitudes de borrado de datos
En la hoja **Administración de aplicaciones móviles de Intune** , encontrará un informe resumido en el icono **Borrar solicitudes** .  Esta opción muestra el estado general e incluye el número de solicitudes pendientes y de errores. Para obtener más información, siga estos pasos:

1.  En la hoja **Administración de aplicaciones móviles de Intune**, elija el icono **Solicitud de borrado** para abrir la hoja **Solicitud de borrado**.

2.  En la hoja **Solicitud de borrado**, puede ver la lista de solicitudes agrupadas según usuarios. Debido a que el sistema crea una solicitud de borrado para cada aplicación protegida que se ejecuta en el dispositivo, puede que vea varias solicitudes para un mismo usuario. Este estado indica si una solicitud de borrado está **pendiente**, ha provocado un **error** o si es **correcta**.

El usuario debe abrir la aplicación de la que se vaya a realizar el borrado, que puede tardar hasta 30 minutos después de efectuar la solicitud.

Los borrados con estado pendiente se muestran hasta que se eliminen manualmente.  Para eliminar manualmente una solicitud de borrado, haga clic derecho y seleccione Eliminar.

### <a name="see-also"></a>Consulte también
[Proteger datos mediante las directivas de administración de aplicaciones móviles con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Usar Azure Portal](azure-portal-for-microsoft-intune-mam-policies.md)



<!--HONumber=Dec16_HO2-->


