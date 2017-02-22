---
title: "Administración de dispositivos con Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: cómo ver los dispositivos que administra con Intune y realizar diversas operaciones en ellos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 040c4e18d87110ab7380a64540d08127574a7c46
ms.openlocfilehash: 5a967cc1be387f83f95591186f786db61d3debcd


---

# <a name="what-is-device-management"></a>¿Qué es la administración de dispositivos? 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

La carga de trabajo de **dispositivos y grupos** le ofrece información sobre los dispositivos que administra y le permite realizar tareas remotas en esos dispositivos. Para acceder a la carga de trabajo:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos y grupos**.

    ![Carga de trabajo de dispositivos y grupos](./media/devices-and-groups-workload.png)

Ahora, elija una de las opciones siguientes:

- **Overview** (Información general): obtenga información sobre los dispositivos que ha inscrito y los sistemas operativos en los que se ejecuta cada dispositivo.
- **Administrar**: elija **Todos los dispositivos** para ver una lista de todos los dispositivos administrados.
    Seleccione uno de los dispositivos de la lista para abrir la hoja *nombre de dispositivo*> **Overview** (Información general) donde puede seleccionar una de estas opciones:
    - **Overview** (Información general): consulte las limitaciones generales sobre el dispositivo, como la información sobre su nombre, el propietario, si se trata de un dispositivo BYOD, cuándo se registró por última vez, y mucho más. Además, puede realizar las siguientes acciones remotas en el dispositivo (no todas las acciones se admiten en todas las plataformas de dispositivo):
        - **Eliminar datos de la compañía**: quita únicamente los datos administrados por Intune. No se quitan datos personales del dispositivo. Intune ya no administra el dispositivo y este dejará de poder acceder a recursos corporativos (no aplicable a dispositivos Windows unidos a Azure Active Directory).
        - **Restablecimiento de fábrica**: devuelve el dispositivo a su configuración predeterminada. Intune ya no administrará el dispositivo y se quitan tanto los datos de la compañía como los personales. No se puede deshacer esta acción.
        - **Bloqueo remoto**: bloquea el dispositivo. El propietario del dispositivo debe usar su contraseña para desbloquearlo. Solo puede bloquear de forma remota un dispositivo que tenga definidos un PIN o una contraseña.
        - **Restablecer contraseña**: genera una nueva contraseña para el dispositivo que se muestra en la hoja *nombre del dispositivo*> **Overview** (Información general).
        - **Omitir bloqueo de activación**: quita el bloqueo de activación de un dispositivo iOS sin el id. y la contraseña de Apple del usuario. Cuando se omite el bloqueo de activación, el dispositivo activa de nuevo el bloqueo de activación cuando se inicia la aplicación Buscar mi iPhone. Omita el bloqueo de activación solo si tiene acceso físico al dispositivo.
        - **Modo de pérdida**: si un dispositivo ha sido robado, puede habilitar el modo de pérdida. Esto le permite especificar un mensaje y un número de teléfono que se mostrarán en la pantalla de bloqueo del dispositivo.
        - **Reiniciar**: hace que el dispositivo se reinicie. Como al propietario del dispositivo no se le informa automáticamente del reinicio, podría perder trabajo.
        ![Información general del dispositivo](http://i.imgur.com/4Rx4VXm.png)
        
    - **Hardware**: consulte información más detallada sobre el dispositivo, como el espacio libre de almacenamiento, el modelo, el fabricante y mucho más.
    ![Inventario de hardware de dispositivo administrado](./media/hardware-inventory.png)
    - **Aplicaciones detectadas**: muestra una lista de todas las aplicaciones instaladas en el dispositivo que encuentra Intune.
    ![Nodo de aplicaciones detectadas](./media/detected-applications.png)
- **Monitor** (Supervisar): elija **Acciones de dispositivo** para ver una lista de acciones de dispositivo que se han realizado en los dispositivos administrados y el estado actual de tales acciones.
![Supervisión de acciones de dispositivo](./media/monitor-device-actions.png)



<!--HONumber=Feb17_HO1-->


