---
title: Asignación de aplicaciones a dispositivos Android for Work
titlesuffix: Microsoft Intune
description: Descubra cómo sincronizar y asignar aplicaciones para dispositivos Android for Work desde la tienda de Google Play for Work.
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
ms.openlocfilehash: 1742c33642667a9e7b8ca2f780094345959cd86c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="assign-apps-to-android-for-work-devices-with-intune"></a>Asignación de aplicaciones para dispositivos Android for Work con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work es un programa para dispositivos Android. Todas las aplicaciones que se instalan en dispositivos Android for Work proceden de Google Play for Work Store. La forma de asignar aplicaciones a dispositivos Android for Work es diferente a cómo las asigna a dispositivos Android estándar. Inicie sesión en la tienda, busque las aplicaciones que desee y apruébelas. La aplicación, a continuación, aparece en el nodo **Aplicaciones con licencia** de Azure Portal y puede administrar la asignación de las aplicaciones como lo haría con cualquier otra aplicación.

Además, si ha creado sus propias aplicaciones de línea de negocio (LOB), puede asignarlas como sigue:
- Suscríbase a una cuenta de Google Developer, que le permite publicar las aplicaciones en un área privada en Google Play Store.
- Sincronícelas con Intune.

## <a name="before-you-start"></a>Antes de empezar

Asegúrese de que ha configurado Intune y Android for Work para que trabajen juntos en la carga de trabajo **Inscripción de dispositivo** de Azure Portal.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronización de una aplicación desde Google Play for Work Store

1. Vaya a [Google Play for Work Store](https://play.google.com/work). Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work.
2. Busque en la tienda y seleccione la aplicación que desea asignar mediante Intune.
3. En la página que muestra la aplicación, seleccione **Aprobar**.  
    En el ejemplo siguiente, ha elegido la aplicación Microsoft Excel.

    ![El botón Aprobar de la tienda de Google Play for Work](media/approve.png)
    
   Se abre una ventana de la aplicación que le pide que conceda permisos a la aplicación para realizar diversas operaciones. 

4. Seleccione **Aprobar** para aceptar los permisos de la aplicación y continuar.

    ![El botón Aprobar para permisos de aplicación](media/approve-app-permissions.png)

5. Seleccione una opción para controlar nuevas solicitudes de permisos de aplicación y luego seleccione **Guardar**.

    ![Opciones para controlar las nuevas solicitudes de permisos de aplicación](media/approve-app-settings.png)

    La aplicación se aprueba y se muestra en la consola de administración de TI. Después, puede [sincronizar la aplicación Android for Work con Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Sincronizar una aplicación Android for Work con Intune

Si se ha aprobado una aplicación desde la tienda y todavía no la ve en el nodo **Aplicaciones con licencia** de la carga de trabajo **Mobile Apps**, fuerce una sincronización inmediata como sigue:

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Aplicaciones móviles**.
4. En el panel de la carga de trabajo **Aplicaciones móviles**, en **Configuración**, elija **Android for Work**.
5. En el panel **Android** for Work, seleccione **Sincronizar**.  
    En la página actualiza la hora y el estado de la última sincronización.
6. En el panel de la carga de trabajo **Aplicaciones móviles**, seleccione **Aplicaciones**.  
    Se muestra la aplicación Android for Work recientemente disponible.

Cuando la aplicación se muestre en el nodo **Licencias de aplicación** del panel de la carga de trabajo **Aplicaciones móviles**, podrá [asignarla igual como haría con cualquier otra aplicación](/intune-azure/manage-apps/deploy-apps). Puede asignar la aplicación solo en grupos de usuarios.

Después de asignar la aplicación, se instala en los dispositivos que ha especificado. Al usuario del dispositivo no se le pide que apruebe la instalación.

## <a name="manage-android-for-work-app-permissions"></a>Administración de permisos de aplicaciones Android for Work
Android for Work requiere que apruebe las aplicaciones en la consola web de Google Play antes de sincronizarlas con Intune y asignarlas a los usuarios. Como Android for Work le permite insertar de forma silenciosa y automáticamente las aplicaciones en los dispositivos de los usuarios, debe aceptar los permisos de aplicación en nombre de todos los usuarios. Los usuarios no ven ningún permiso de aplicación cuando instalan las aplicaciones, por lo que es importante que lea y comprenda los permisos.

Cuando un desarrollador de la aplicación publica una nueva versión con permisos actualizados, los permisos no se aceptan automáticamente, incluso si se han aprobado los permisos anteriores. Todavía se pueden usar los dispositivos que ejecutan la versión anterior de la aplicación. Sin embargo, la aplicación no se actualiza hasta que se aprueban los nuevos permisos. Los dispositivos que no tienen instalada la aplicación no la instalan hasta que se aprueben los nuevos permisos de la aplicación.

### <a name="update-app-permissions"></a>Actualización de los permisos de la aplicación

Visite periódicamente la consola de Google Play administrada para buscar nuevos permisos. Puede configurar Google Play para que le envíe a usted o a otros usuarios un correo electrónico cuando se requieren nuevos permisos para una aplicación aprobada. Si asigna una aplicación y observa que no está instalada en los dispositivos, busque nuevos permisos haciendo lo siguiente:

1. Vaya a [Google Play](http://play.google.com/work).
2. Inicie sesión con la cuenta de Google que usó para publicar y aprobar las aplicaciones.
3. Seleccione la pestaña **Actualizaciones** y compruebe si las aplicaciones requieren una actualización.  
    Las aplicaciones de la lista requieren permisos nuevos y no se asignarán hasta que se apliquen.

Como alternativa, puede configurar Google Play para que vuelva a aprobar automáticamente los permisos de las aplicaciones por cada aplicación. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Trabajar con una aplicación de línea de negocio desde Google Play for Work Store

1. Inicie sesión en la [consola para desarrolladores Google Play](https://play.google.com/apps/publish) con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work.  
    Si inicia sesión por primera vez, debe registrar y pagar una cuota para participar en el programa para desarrolladores de Google.
2. En la consola, seleccione **Agregar nueva aplicación**.
3. Puede cargar y proporcionar información sobre la aplicación de la misma manera que publica cualquier aplicación en Google Play Store. Sin embargo, debe seleccionar **Solo hacer que esta aplicación esté disponible para mi organización (<*nombre de la organización*>)**.

    ![Hacer que la aplicación esté disponible solo para su organización](media/restrict.png)

    Esta operación garantiza que la aplicación solo esté disponible para su organización y no esté disponible en la tienda Google Play pública.

    Para más información sobre la carga y publicación de aplicaciones Android, consulte la [Ayuda de la consola para desarrolladores de Google](https://support.google.com/googleplay/android-developer/answer/113469).
4. Después de haber publicado la aplicación, inicie sesión en la [tienda de Google Play for Work](https://play.google.com/work) con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work.
5. En el nodo **Aplicaciones** de la tienda, compruebe que se muestra la aplicación publicada.  
    La sincronización de la aplicación con Intune se ha aprobado automáticamente.

## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md) 

