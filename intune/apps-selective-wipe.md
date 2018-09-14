---
title: Borrado solo de datos corporativos de aplicaciones
titleSuffix: Microsoft Intune
description: Descubra cómo borrar aplicaciones de forma selectiva con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 66f26811f5021b71c62a2e994c73e2144409d199
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329552"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Borrado solo de datos corporativos de aplicaciones administradas por Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cuando un dispositivo se pierde o lo roban, o cuando un empleado deja la empresa, le interesa asegurarse de que se eliminan del dispositivo los datos de la aplicación de empresa. Pero es posible que no quiera quitar del dispositivo los datos personales, sobre todo si se trata de un dispositivo propiedad de un empleado.

>[!NOTE]
> Actualmente, solo se admiten las plataformas iOS y Android para borrar datos corporativos de aplicaciones administradas de Intune.

Para quitar de forma selectiva datos de la aplicación de empresa, siga los pasos de este tema para crear una solicitud de borrado. Una vez finalizada la solicitud, la próxima vez que la aplicación se ejecute en el dispositivo, los datos de la empresa se quitarán de la aplicación. Además de crear una solicitud de borrado, puede configurar un borrado selectivo de los datos de la organización como una nueva acción cuando no se cumplan las condiciones de Configuración de acceso de las Directivas de protección de aplicaciones (APP). Mediante esta característica, podrá proteger y eliminar automáticamente datos confidenciales de la organización en las aplicaciones, en función de criterios configurados previamente.

>[!IMPORTANT]
> Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa. No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. Actualmente, esto solo se aplica a la aplicación Microsoft Outlook.

## <a name="create-a-wipe-request"></a>Crear una solicitud de borrado

1.  Inicie sesión en el [Portal de Azure](https://portal.azure.com).

2.  Elija **Todos los servicios**, escriba **Intune** en el cuadro de texto de filtro y seleccione **Intune**. En el panel de Intune que se abre, haga clic en el panel **Aplicaciones cliente**.

    ![Captura de pantalla del panel de Microsoft Intune](./media/apps-selective-wipe01.png)

3.  En el **panel Aplicaciones móviles**, elija **Borrado selectivo de aplicaciones**.

4.  Elija **Nueva solicitud de borrado**. Se abrirá el panel **Nueva solicitud de borrado**.

    ![Captura de pantalla del panel Nueva solicitud de borrado](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Seleccione un usuario y después elija **Seleccionar** para seleccionar el usuario cuyos datos de aplicación quiera borrar.

6.  Luego, elija **Dispositivo** en el panel **Nueva solicitud de borrado**. Se abre el panel **Seleccionar dispositivo**, en el que muestran todos los dispositivos asociados al usuario seleccionado. También se proporcionan dos columnas: el nombre del dispositivo, que es un nombre descriptivo definido por el usuario, y el tipo de dispositivo, que indica la plataforma. Seleccione el dispositivo que desea borrar.

7.  Ahora está de nuevo en el panel **Nueva solicitud de borrado**. Seleccione **Aceptar** para realizar una solicitud de borrado.

El servicio crea y realiza el seguimiento de una solicitud de borrado independiente para cada aplicación protegida en el dispositivo, y del usuario asociado a la solicitud de borrado.

## <a name="monitor-your-wipe-requests"></a>Supervisar las solicitudes de borrado de datos

Puede tener un informe resumido que muestre el estado general de la solicitud de borrado y que incluya el número de solicitudes pendientes y errores. Para obtener más información, siga estos pasos:

1.  En el panel **Aplicaciones móviles - Borrado selectivo de aplicaciones**, puede ver la lista de solicitudes agrupadas por usuarios. Debido a que el sistema crea una solicitud de borrado para cada aplicación protegida que se ejecuta en el dispositivo, puede que vea varias solicitudes para un mismo usuario. Este estado indica si una solicitud de borrado está **pendiente**, ha provocado un **error** o si es **correcta**.

    ![Captura de pantalla del estado de la solicitud de borrado en el panel Borrado selectivo de aplicaciones](./media/wipe-request-status-1.png)

Además, podrá ver el nombre del dispositivo y su tipo, lo que puede resultar útil al leer los informes.

>[!IMPORTANT]
> El usuario debe abrir la aplicación de la que se vaya a realizar el borrado, que puede tardar hasta 30 minutos después de efectuar la solicitud.

## <a name="delete-a-wipe-request"></a>Eliminación de una solicitud de borrado

Los borrados con estado pendiente se muestran hasta que se eliminen manualmente. Para eliminar manualmente una solicitud de borrado:

1.  En el panel **Aplicaciones móviles - Borrado selectivo de aplicaciones**.

2.  En la lista, haga clic con el botón derecho en la solicitud de borrado que quiere eliminar y elija **Eliminar solicitud de borrado**.

    ![Captura de pantalla de la lista de solicitudes de borrado en el panel Borrado selectivo de aplicaciones](./media/delete-wipe-request.png)

3.  Se le pedirá que confirme la eliminación. Elija **Sí** o **No** y luego haga clic en **Aceptar**.

### <a name="see-also"></a>Vea también
[What's app protection policy](app-protection-policy.md) (¿Qué es la directiva de protección de aplicaciones?)

[¿Qué es la administración de aplicaciones?](app-management.md)
