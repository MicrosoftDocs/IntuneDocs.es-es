---
title: "Implementación de aplicaciones para dispositivos Android for Work | Microsoft Docs"
description: "Utilice este tema para sincronizar y después implementar aplicaciones para dispositivos Android for Work desde Google Play for Work Store."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0936051b5c33a2e98f275ef7a3a32be2e8f5a8b0
ms.openlocfilehash: 3b608d42f04b9fce457b6b61587d05ab5d59bb0a
ms.lasthandoff: 03/10/2017


---

# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>Implementación de aplicaciones para dispositivos Android for Work con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Puede implementar aplicaciones para dispositivos Android for Work de forma diferente a cuando las implementa en dispositivos Android estándar. Todas las aplicaciones que instale en Android for Work proceden de Google Play for Work Store. Inicie sesión en la tienda, busque las aplicaciones que desee y apruébelas.
La aplicación aparecerá en el nodo **Aplicaciones compradas por volumen** de la consola de Intune. Desde aquí, puede administrar la implementación de la aplicación de la misma manera que implementaría cualquier otra aplicación.

Además, si ha creado sus propias aplicaciones de línea de negocio (LOB), puede implementarlas. Para ello, debe suscribirse a una cuenta de Google Developer, que le permite publicar las aplicaciones en un área privada en Google Play Store y sincronizarlas con Intune.

## <a name="before-you-start"></a>Antes de empezar

1. Asegúrese de que ha configurado Intune y Android for Work para que trabajen juntos en la pestaña **Administrador** de la consola de Intune.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronización de una aplicación desde Google Play for Work Store


1. Vaya a [Google Play for Work Store](https://play.google.com/work). Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work.
2. Busque en la tienda la aplicación que desea implementar mediante Intune.
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

## <a name="deploy-an-android-for-work-app"></a>Implementación de una aplicación Android for Work

Si se ha aprobado una aplicación desde la tienda y todavía no la ve en el nodo **Aplicaciones compradas por volumen** del área de trabajo **Aplicaciones**, puede forzar una sincronización inmediata como sigue:

1. En la [consola de administración de Intune](https://manage.microsoft.com), elija **Administrador** > **Administración de dispositivos móviles** > **Android for Work**.
2. En la página **Configuración de la administración de dispositivos móviles de Android for Work**, elija **Sincronizar ahora**.
3. La página también muestra el tiempo y el estado de la última sincronización.

Cuando la aplicación se muestra en el nodo **Aplicaciones compradas por volumen** del área de trabajo **Aplicaciones**, puede [implementarla al igual como haría con cualquier otra aplicación](deploy-apps-in-microsoft-intune.md). Puede implementar la aplicación solo en grupos de usuarios. Actualmente, solo puede seleccionar las acciones **Necesaria** y **Desinstalar**.

La capacidad de implementar una aplicación como **disponible** aprovecha la nueva experiencia de agrupación y selección de destino. Las cuentas de servicio de Intune aprovisionadas recientemente podrán usar esta característica después de su publicación. Los clientes de Intune existentes pueden usar esta característica una vez que se haya migrado su inquilino al portal de Azure Intune. Los clientes existentes son libres de crear una cuenta de Intune de prueba para prepararse para esta característica y probarla hasta que su inquilino se haya migrado.

Después de implementar la aplicación, se instalará en los dispositivos especificados. No se pedirá al usuario del dispositivo su aprobación.

## <a name="manage-app-permissions"></a>Administrar permisos de aplicación
Android for Work requiere que apruebe las aplicaciones en la consola web de Play administrada por Google antes de la sincronización con Intune y de su implementación a los usuarios.  Como Android for Work le permite insertar de forma silenciosa y automáticamente estas aplicaciones en los dispositivos de los usuarios, debe aceptar los permisos de la aplicación en nombre de todos los usuarios.  Los usuarios finales no verán ningún permiso de las aplicaciones cuando las instalan, por lo que es importante que lea y comprenda estos permisos.

Cuando un desarrollador de la aplicación publica una nueva versión con permisos actualizados, esos permisos no se aceptan automáticamente, incluso si se han aprobado los permisos anteriores. Los dispositivos que ejecuten la versión anterior de la aplicación aún puede utilizarla, pero la aplicación no se actualizará hasta que se aprueben los nuevos permisos. Los dispositivos que no tienen instalada la aplicación no pueden instalarla hasta que se aprueben los nuevos permisos de la aplicación.

### <a name="how-to-update-app-permissions"></a>Cómo actualizar los permisos de la aplicación

Visite periódicamente la consola de Google Play administrada para buscar nuevos permisos. Si implementa una aplicación y observa que no está instalado en los dispositivos, busque nuevos permisos con los siguientes pasos:

1. Visite http://play.google.com/work
2. Inicie sesión con la cuenta de Google que usó para publicar y aprobar las aplicaciones.
3. Visite la pestaña **Actualizaciones** para ver si alguna aplicación requiere una actualización.  Las aplicaciones de la lista requieren permisos nuevos y no se implementarán hasta que estén aprobados.  

