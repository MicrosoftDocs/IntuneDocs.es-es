---
title: "Asignación de aplicaciones a dispositivos Android for Work | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Azure de Intune: Use este tema para sincronizar y, luego, asigne aplicaciones a dispositivos Android for Work desde Google Play for Work Store."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 49e86ab665d9022739c0330092734ba897ea3b02
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Asignación de aplicaciones para dispositivos Android for Work con Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Puede asignar aplicaciones para dispositivos Android for Work de forma diferente a cuando las asigna en dispositivos Android estándar. Todas las aplicaciones que instale en Android for Work proceden de Google Play for Work Store. Inicie sesión en la tienda, busque las aplicaciones que desee y apruébelas.
La aplicación aparecerá en el nodo **Aplicaciones con licencia** del portal Intune. Desde aquí, puede administrar la asignación de la aplicación de la misma manera que asignaría cualquier otra aplicación.

Además, si ha creado sus propias aplicaciones de línea de negocio (LOB), puede asignarlas. Para ello, debe suscribirse a una cuenta de Google Developer, que le permite publicar las aplicaciones en un área privada en Google Play Store y sincronizarlas con Intune.

## <a name="before-you-start"></a>Antes de empezar

Asegúrese de que ha configurado Intune y Android for Work para que trabajen juntos en la carga de trabajo **Inscripción de dispositivo** del portal Intune.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronización de una aplicación desde Google Play for Work Store


1. Vaya a [Google Play for Work Store](https://play.google.com/work). Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work.
2. Busque en la tienda la aplicación que desea asignar mediante Intune.
3. En la página de la aplicación elegida, seleccione **Aprobar**. En este ejemplo, ha elegido la aplicación Microsoft Excel.<br>
  ![Ejemplo de aprobación de la aplicación](media/approve.png)
4. Se abre una ventana de la aplicación que le pide que conceda permisos a la aplicación para realizar diversas operaciones. Debe elegir **Aprobar** para continuar.<br>
  ![Ejemplo de permisos para aprobar la aplicación](media/approve-app-permissions.png)
5. Tras unos instantes, verá un mensaje de confirmación indicando que la aplicación se ha aprobado y está disponible en la consola de administración de TI.

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Publicar y después sincronizar una aplicación de línea de negocio desde Google Play for Work Store

1. Vaya a la consola de desarrollador de Google Play, [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work. Si inicia sesión por primera vez, debe registrar y pagar una cuota para participar en el programa para desarrolladores de Google.
3. En la consola, elija **Agregar nueva aplicación**.
4. Puede cargar y proporcionar información sobre la aplicación de la misma manera que publica cualquier aplicación en Google Play Store. Sin embargo debe seleccionar la configuración **Solo hacer que esta aplicación esté disponible para mi organización (<*nombreDeOrganización*>)** como se muestra a continuación.<br>
  ![Opción para que solo la aplicación esté disponible para la organización](media/restrict.png)<br>
Esto garantiza que la aplicación solo está disponible para su organización y no está disponible en Google Play Store público.
Para más información sobre cómo cargar y publicar aplicaciones Android, consulte la [Ayuda de la consola de desarrollador de Google](https://support.google.com/googleplay/android-developer/answer/113469).
5. Una vez publicada la aplicación, vaya a [Google Play for Work Store](https://play.google.com/work). Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work.
6. En el nodo **Aplicaciones** de la tienda, compruebe que puede ver la aplicación publicada. Tenga en cuenta que se ha aprobado automáticamente para sincronizarse con Intune.

## <a name="assign-an-android-for-work-app"></a>Asignación de una aplicación Android for Work

Si se ha aprobado una aplicación desde la tienda y todavía no la ve en el nodo **Aplicaciones con licencia** de la carga de trabajo **Mobile Apps**, puede forzar una sincronización inmediata como sigue:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Mobile apps**.
4. En la carga de trabajo **Mobile Apps**, elija **Configuración** > **Android for Work**.
5. En la hoja Android for Work, elija **Sincronizar ahora**.
6. La página también muestra el tiempo y el estado de la última sincronización.

Cuando la aplicación se muestra en el nodo **Aplicaciones con licencia** de la carga de trabajo **Mobile Apps**, puede [asignarla al igual como haría con cualquier otra aplicación](/intune-azure/manage-apps/deploy-apps). Puede asignar la aplicación solo en grupos de usuarios.

Después de asignar la aplicación, se instalará en los dispositivos especificados. No se pedirá al usuario del dispositivo que apruebe la instalación.

## <a name="manage-app-permissions"></a>Administrar permisos de aplicación
Android for Work requiere que apruebe las aplicaciones en la consola web de Play administrada por Google antes de la sincronización con Intune y de su asignación a los usuarios.  Como Android for Work le permite insertar de forma silenciosa y automáticamente estas aplicaciones en los dispositivos de los usuarios, debe aceptar los permisos de la aplicación en nombre de todos los usuarios.  Los usuarios finales no verán ningún permiso de las aplicaciones cuando las instalan, por lo que es importante que lea y comprenda estos permisos.

Cuando un desarrollador de la aplicación publica una nueva versión con permisos actualizados, esos permisos no se aceptan automáticamente, incluso si se han aprobado los permisos anteriores. Los dispositivos que ejecuten la versión anterior de la aplicación aún puede utilizarla, pero la aplicación no se actualizará hasta que se aprueben los nuevos permisos. Los dispositivos que no tienen instalada la aplicación no pueden instalarla hasta que se aprueben los nuevos permisos de la aplicación.

### <a name="how-to-update-app-permissions"></a>Cómo actualizar los permisos de la aplicación

Visite periódicamente la consola de Google Play administrada para buscar nuevos permisos. Si asigna una aplicación y observa que no está instalado en los dispositivos, busque nuevos permisos con los siguientes pasos:

1. Visite http://play.google.com/work
2. Inicie sesión con la cuenta de Google que usó para publicar y aprobar las aplicaciones.
3. Visite la pestaña **Actualizaciones** para ver si alguna aplicación requiere una actualización.  Las aplicaciones de la lista requieren permisos nuevos y no se asignarán hasta que se apliquen.  
