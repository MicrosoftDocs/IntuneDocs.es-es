---
title: Asignar aplicaciones de Google Play administrado a dispositivos de Android Enterprise
titleSuffix: Microsoft Intune
description: Descubra cómo sincronizar y asignar aplicaciones a dispositivos de Android Enterprise desde Google Play Store administrado.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/25/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b99f9e394fdced985b5b1309640b09b8e7fa5e6
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568757"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Incorporación de aplicaciones de Google Play administrado a dispositivos de Android Enterprise con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android Enterprise es un programa para dispositivos de perfil de trabajo, dispositivos de quiosco o dedicados y dispositivos completamente administrados de Android. Para los dispositivos de perfil de trabajo Android, Android Enterprise es un conjunto de características y servicios que permite separar las aplicaciones y los datos personales de aplicaciones y datos laborales. Android Enterprise proporciona opciones de administración adicionales y privacidad cuando las personas usan sus dispositivos Android para trabajar. Intune le ayuda a implementar aplicaciones y opciones de configuración en dispositivos de perfil de trabajo Android a fin de garantizar que la información laboral y la personal se mantengan aparte. Todas las aplicaciones que se instalen en dispositivos de perfiles de trabajo Android proceden de Google Play Store administrado. La forma de asignar aplicaciones a dispositivos de perfil de trabajo Android es diferente a cómo las asigna a dispositivos Android estándar. Inicie sesión en la tienda, busque las aplicaciones que desee y apruébelas. La aplicación, a continuación, aparece en el nodo **Aplicaciones con licencia** de Azure Portal y puede administrar la asignación de las aplicaciones como lo haría con cualquier otra aplicación.

Además, si ha creado sus propias aplicaciones de línea de negocio (LOB), puede asignarlas como sigue:
- Suscríbase a una cuenta de Google Developer, que le permite publicar las aplicaciones en un área privada en Google Play Store.
- Sincronícelas con Intune.

## <a name="before-you-start"></a>Antes de empezar

Asegúrese de que ha configurado Intune y perfiles de trabajo Android para que trabajen juntos en la carga de trabajo **Inscripción de dispositivo** de Azure Portal. Para obtener más información, vea [Inscripción de dispositivos Android](android-work-profile-enroll.md).

>[!NOTE]
>Cuando trabaja con Microsoft Intune, se recomienda usar el explorador Microsoft Edge o Google Chrome.

## <a name="managed-google-play-app-type"></a>Tipo de aplicaicón de Google Play administrado
El tipo de aplicación de **Google Play administrado** le permitirá agregar específicamente [aplicaciones de Google Play administrado](https://play.google.com/work/search?q=microsoft&c=apps) a Intune. Como administrador de Intune, ahora podrá examinar, buscar, aprobar, sincronizar y asignar aplicaciones de Google Play administrado aprobadas dentro de Intune.  Ya no necesita ir a la consola de Google Play administrado por separado ni tiene que volver a autenticarse.

> [!NOTE]
> Si prefiere sincronizar una aplicación de Google Play administrado con Intune, consulte [Sincronización de una aplicación de Google Play administrado con Intune](apps-add-android-for-work.md#synchronize-a-managed-google-play-app-with-intune-alternative)

## <a name="add-a-managed-google-play-app-using-intune"></a>Incorporación de una aplicación de Google Play administrado mediante Intune

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**.  
    Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Aplicaciones cliente** > **Aplicaciones**.
5. En el panel **Aplicaciones**, seleccione **Agregar**.
6. En el cuadro de lista desplegable **Tipo de aplicación**, seleccione **Google Play administrado**.
7. Seleccione **Google Play administrado: Aprobar** para abrir el catálogo de Google Play administrado.
8. Use el cuadro de búsqueda para buscar las aplicaciones que quiera incluir.
9. Haga clic en **Aprobar** para aprobar la aplicación de Google Play administrado y en **Aprobar** para aceptar los permisos de aplicación.
10. Seleccione **Keep approved when app requests new permissions** (Mantener aprobada cuando la aplicación solicite nuevos permisos) en la ventana de configuración de la aprobación y, luego, haga clic en **Guardar**. Si no elige esta opción, deberá aprobar manualmente los nuevos permisos si el desarrollador de la aplicación publica una actualización.  Como consecuencia, las instalaciones y actualizaciones de la aplicación se detendrán hasta que se aprueben los permisos. Por este motivo, se recomienda seleccionar la opción para aprobar automáticamente los nuevos permisos. 
11. Haga clic en **Aceptar** para incluir las aplicaciones que ha aprobado.
12. Haga clic en **Sincronizar** en el panel **Aprobar aplicación** para realizar la sincronización con el servicio de Google Play administrado.

## <a name="synchronize-a-managed-google-play-app-with-intune-alternative"></a>Sincronización de una aplicación de Google Play administrado con Intune (alternativa)
Si prefiere sincronizar una aplicación de Google Play administrado con Intune, en lugar de agregarla directamente mediante Intune, use los pasos siguientes.

> [!IMPORTANT]
> La información proporcionada a continuación es un método alternativo para agregar una aplicación de Google Play administrado mediante Intune, como se describió anteriormente.

### <a name="synchronize-an-app-from-the-managed-google-play-store"></a>Sincronización de una aplicación desde Google Play Store administrado

1. Vaya a [Google Play Store administrado](https://play.google.com/work). Inicie sesión con la misma cuenta que usó para configurar la conexión entre Intune y Android Enterprise.
2. Busque en la tienda y seleccione la aplicación que desea asignar mediante Intune.
3. En la página que muestra la aplicación, seleccione **Aprobar**.  
    En el ejemplo siguiente, ha elegido la aplicación Microsoft Excel.

    ![Botón Aprobar de Google Play Store administrado](media/approve.png)

   Se abre una ventana de la aplicación que le pide que conceda permisos a la aplicación para realizar diversas operaciones.

4. Seleccione **Aprobar** para aceptar los permisos de la aplicación y continuar.

    ![El botón Aprobar para permisos de aplicación](media/approve-app-permissions.png)

5. Seleccione una opción para controlar nuevas solicitudes de permisos de aplicación y luego seleccione **Guardar**.

    ![Opciones para controlar las nuevas solicitudes de permisos de aplicación](media/approve-app-settings.png)

    La aplicación se aprueba y se muestra en la consola de administración de TI. Después, puede [sincronizar la aplicación de perfil de trabajo Android con Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).

### <a name="sync-a-managed-google-play-app-with-intune"></a>Sincronizar una aplicación administrada en Google Play con Intune

Si se ha aprobado una aplicación desde la tienda y todavía no se ve en el nodo **Aplicaciones con licencia** de la carga de trabajo **Aplicaciones cliente**, fuerce una sincronización inmediata como sigue:

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En el panel de la carga de trabajo **Aplicaciones cliente**, en **Configuración**, elija **Google Play administrado**.
5. En el panel **Google Play administrado**, elija **Actualizar**.  
    En la página actualiza la hora y el estado de la última sincronización.
6. En el panel de la carga de trabajo **Aplicaciones cliente**, seleccione **Aplicaciones**.  
    Se muestra la aplicación Google Play administrado que se ha publicado recientemente.

## <a name="assigning-the-managed-google-play-app"></a>Asignación de una aplicación de Google Play administrado

Cuando la aplicación se muestre en el nodo **Licencias de aplicación** del panel de la carga de trabajo **Aplicaciones cliente**, podrá [asignarla igual que haría con cualquier otra aplicación](/intune-azure/manage-apps/deploy-apps) asignando la aplicación a grupos de usuarios.

Después de asignar la aplicación, se instala en los dispositivos que ha especificado. Al usuario del dispositivo no se le pide que apruebe la instalación.

## <a name="manage-android-enterprise-app-permissions"></a>Administración de permisos de aplicaciones Android Enterprise
Android Enterprise requiere que apruebe las aplicaciones en la consola web de Google Play antes de sincronizarlas con Intune y asignarlas a los usuarios. Como Android Enterprise le permite insertar de forma silenciosa y automáticamente las aplicaciones en los dispositivos de los usuarios, debe aceptar los permisos de aplicación en nombre de todos los usuarios. Los usuarios no ven ningún permiso de aplicación cuando instalan las aplicaciones, por lo que es importante que comprenda los permisos.

Cuando un desarrollador de la aplicación actualiza los permisos con una nueva versión de la aplicación, los permisos no se aceptan automáticamente, incluso si se han aprobado los permisos anteriores. Todavía se pueden usar los dispositivos que ejecutan la versión anterior de la aplicación. Sin embargo, la aplicación no se actualiza hasta que se aprueban los nuevos permisos. Los dispositivos que no tienen instalada la aplicación no la instalan hasta que se aprueben los nuevos permisos de la aplicación.

### <a name="update-app-permissions"></a>Actualización de los permisos de la aplicación

Visite periódicamente la consola de Google Play administrada para buscar nuevos permisos. Puede configurar Google Play para que le envíe a usted o a otros usuarios un correo electrónico cuando se requieren nuevos permisos para una aplicación aprobada. Si asigna una aplicación y observa que no está instalada en los dispositivos, compruebe si existen los nuevos permisos siguiendo estos pasos:

1. Vaya a [Google Play](https://play.google.com/work).
2. Inicie sesión con la cuenta de Google que usó para publicar y aprobar las aplicaciones.
3. Seleccione la pestaña **Actualizaciones** y compruebe si las aplicaciones requieren una actualización.  
    Las aplicaciones de la lista requieren permisos nuevos y no se asignarán hasta que se apliquen.

Como alternativa, puede configurar Google Play para que vuelva a aprobar automáticamente los permisos de las aplicaciones por cada aplicación.

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>Trabajar con una aplicación de línea de negocio desde Google Play Store administrado

1. Inicie sesión en la [consola para desarrolladores Google Play](https://play.google.com/apps/publish) con la misma cuenta que usó para configurar la conexión entre Intune y Android Enterprise.  
    Si inicia sesión por primera vez, debe registrar y pagar una cuota para participar en el programa para desarrolladores de Google.
2. En la consola, seleccione **Agregar nueva aplicación**.
3. Puede cargar y proporcionar información sobre la aplicación de la misma manera que publica cualquier aplicación en Google Play Store. Sin embargo, debe seleccionar **Solo hacer que esta aplicación esté disponible para mi organización (<*nombre de la organización*>)**.

    ![Hacer que la aplicación esté disponible solo para su organización](media/restrict.png)

    Con esta operación, la aplicación solo estará disponible para su organización, y no en Google Play Store público.

    Para más información sobre la carga y publicación de aplicaciones Android, consulte la [Ayuda de la consola para desarrolladores de Google](https://support.google.com/googleplay/android-developer/answer/113469).
4. Después de haber publicado la aplicación, inicie sesión en [Google Play Store administrado](https://play.google.com/work) con la misma cuenta que usó para configurar la conexión entre Intune y Android Enterprise.
5. En el nodo **Aplicaciones** de la tienda, compruebe que se muestra la aplicación publicada.  
    La sincronización de la aplicación con Intune se ha aprobado automáticamente.

## <a name="delete-managed-google-play-apps"></a>Eliminación de aplicaciones de Google Play administrado
Cuando sea necesario, podrá eliminar aplicaciones de Google Play administrado desde Microsoft Intune. Para eliminar una aplicación de Google Play administrado, abra Microsoft Intune en Azure Portal y seleccione **Aplicaciones cliente** > **Aplicaciones**. En la lista de aplicaciones, seleccione los puntos suspensivos (...) a la derecha de la aplicación de Google Play administrado y luego seleccione **Eliminar** en la lista que aparece. Cuando se elimina una aplicación de Google Play administrada de la lista de aplicaciones, automáticamente se desactiva la aprobación de la aplicación administrada de Google Play.

## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
