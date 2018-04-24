---
title: Asignación de aplicaciones a dispositivos Android for Work
titlesuffix: Microsoft Intune
description: Descubra cómo sincronizar y asignar aplicaciones para dispositivos Android for Work desde Google Play for Work Store.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4168f78bff8937ca403cdb75b1028954cbbebd6f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Asignación de aplicaciones para dispositivos Android for Work con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work es un programa para dispositivos Android. Todas las aplicaciones que se instalan en dispositivos Android for Work proceden de Google Play for Work Store. Puede asignar aplicaciones para dispositivos Android for Work de forma diferente a cuando las asigna en dispositivos Android estándar. Inicie sesión en la tienda, busque las aplicaciones que desee y apruébelas. La aplicación aparecerá en el nodo **Aplicaciones con licencia** de Azure Portal. Desde aquí, puede administrar la asignación de la aplicación de la misma manera que asignaría cualquier otra aplicación.

Además, si ha creado sus propias aplicaciones de línea de negocio (LOB), puede asignarlas como sigue:
- Suscríbase a una cuenta de Google Developer, que le permite publicar las aplicaciones en un área privada en Google Play Store.
- Sincronícelas con Intune.

## <a name="before-you-start"></a>Antes de empezar

Asegúrese de que ha configurado Intune y Android for Work para que trabajen juntos en la carga de trabajo **Inscripción de dispositivo** de Azure Portal.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronización de una aplicación desde Google Play for Work Store

1. Vaya a [Google Play for Work Store](https://play.google.com/work). Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work.
2. Busque en la tienda y seleccione la aplicación que desea asignar mediante Intune.
3. Seleccione **Aprobar** en la página que muestra la aplicación. En los ejemplos siguientes se muestra que se ha elegido la aplicación Microsoft Excel.</br>

    ![Ejemplo: Aprobar la aplicación en el almacén de Google Play for Work](media/approve.png)</br>
    
   Se abre una ventana de la aplicación que le pide que conceda permisos a la aplicación para realizar diversas operaciones. 

4. Seleccione **Aprobar** para aceptar los permisos de la aplicación y continuar.</br>

    ![Ejemplo: aprobar permisos de la aplicación](media/approve-app-permissions.png)

5. Elija cómo controlar las nuevas solicitudes de permiso de la aplicación. A continuación, seleccione **Guardar** para guardar cómo se supervisarán las nuevas solicitudes de permiso de la aplicación.</br>

    ![Ejemplo: Guardar las nuevas solicitudes de permiso de la aplicación](media/approve-app-settings.png)</br>

    La aplicación se aprueba y se muestra en la consola de administración de TI. Ahora, puede [sincronizar la aplicación Android for Work con Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Sincronizar una aplicación Android for Work con Intune

Si se ha aprobado una aplicación desde la tienda y todavía no la ve en el nodo **Aplicaciones con licencia** de la carga de trabajo **Mobile Apps**, fuerce una sincronización inmediata como sigue:

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Aplicaciones móviles**, elija **Android for Work** en la sección **Configuración**.
5. En el panel Android for Work, elija **Sincronizar**. En la página se mostrará la hora y el estado de la última sincronización.
6. En la carga de trabajo **Aplicaciones móviles**, seleccione **Aplicaciones** para mostrar la nueva aplicación Android for Work.

Cuando la aplicación se muestre en el nodo **Licencias de aplicación** de la carga de trabajo **Aplicaciones móviles**, podrá [asignarla igual como haría con cualquier otra aplicación](/intune-azure/manage-apps/deploy-apps). Puede asignar la aplicación solo en grupos de usuarios.

Después de asignar la aplicación, se instalará en los dispositivos especificados. Al usuario del dispositivo no se le pide que apruebe la instalación.

## <a name="manage-android-for-work-app-permissions"></a>Administración de permisos de aplicaciones Android for Work
Android for Work requiere que apruebe las aplicaciones en la consola web de Play administrada por Google antes de la sincronización con Intune y de su asignación a los usuarios.  Como Android for Work le permite insertar de forma silenciosa y automáticamente estas aplicaciones en los dispositivos de los usuarios, debe aceptar los permisos de la aplicación en nombre de todos los usuarios.  Los usuarios finales no ven ningún permiso de las aplicaciones cuando las instalan, por lo que es importante que lea y comprenda estos permisos.

Cuando un desarrollador de la aplicación publica una nueva versión con permisos actualizados, esos permisos no se aceptan automáticamente, incluso si se han aprobado los permisos anteriores. Todavía se pueden usar los dispositivos que ejecutan la versión anterior de la aplicación. Sin embargo, la aplicación no se actualiza hasta que se aprueban los nuevos permisos. Los dispositivos que no tienen instalada la aplicación no la instalan hasta que se aprueben los nuevos permisos de la aplicación.

### <a name="how-to-update-app-permissions"></a>Cómo actualizar los permisos de la aplicación

Visite periódicamente la consola de Google Play administrada para buscar nuevos permisos. Puede configurar Google Play para que le envíe a usted o a otros usuarios un correo electrónico cuando se requieren nuevos permisos para una aplicación aprobada. Si asigna una aplicación y observa que no está instalado en los dispositivos, busque nuevos permisos con los siguientes pasos:

1. Visite http://play.google.com/work.
2. Inicie sesión con la cuenta de Google que usó para publicar y aprobar las aplicaciones.
3. Visite la pestaña **Actualizaciones** para ver si alguna aplicación requiere una actualización.  Las aplicaciones de la lista requieren permisos nuevos y no se asignarán hasta que se apliquen.  

Como alternativa, puede configurar Google Play para que vuelva a aprobar automáticamente los permisos de las aplicaciones por cada aplicación. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Trabajar con una aplicación de línea de negocio desde Google Play for Work Store

1. Vaya a la consola de desarrollador de Google Play, [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work. Si inicia sesión por primera vez, debe registrar y pagar una cuota para participar en el programa para desarrolladores de Google.
3. En la consola, elija **Agregar nueva aplicación**.
4. Puede cargar y proporcionar información sobre la aplicación de la misma manera que publica cualquier aplicación en Google Play Store. Sin embargo, debe seleccionar la configuración **Solo hacer que esta aplicación esté disponible para mi organización (<*nombre de la organización*>)**:</br>

    ![Opción para que solo la aplicación esté disponible para la organización](media/restrict.png)</br>

Esta operación garantiza que la aplicación solo esté disponible para su organización y no esté disponible en Google Play Store público.
Para más información sobre cómo cargar y publicar aplicaciones Android, consulte la [Ayuda de la consola de desarrollador de Google](https://support.google.com/googleplay/android-developer/answer/113469).
5. Una vez publicada la aplicación, vaya a [Google Play for Work Store](https://play.google.com/work). Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work.
6. En el nodo **Aplicaciones** de la tienda, compruebe que puede ver la aplicación publicada. La sincronización de la aplicación con Intune se ha aprobado automáticamente.

## <a name="next-steps"></a>Pasos siguientes

- [Asignación de aplicaciones a grupos](apps-deploy.md)

