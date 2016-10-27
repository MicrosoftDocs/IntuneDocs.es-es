---
title: "Implementación de aplicaciones para dispositivos Android for Work | Microsoft Intune"
description: "Utilice este tema para sincronizar y después implementar aplicaciones para dispositivos Android for Work desde Google Play for Work Store."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 32bded5047b1a08738418e3e36382eeae1a5f3b4
ms.openlocfilehash: f3b7c3a07ef3530805f4f951bcdb99cc5f7eb93d


---

# Implementación de aplicaciones para dispositivos Android for Work con Intune

Puede implementar aplicaciones para dispositivos Android for Work de forma diferente a cuando las implementa en dispositivos Android estándar. Todas las aplicaciones que instale en Android for Work proceden de Google Play for Work Store. Inicie sesión en la tienda, busque las aplicaciones que desee y apruébelas.
La aplicación aparecerá en el nodo **Aplicaciones compradas por volumen** de la consola de Intune. Desde aquí, puede administrar la implementación de la aplicación de la misma manera que implementaría cualquier otra aplicación.
Además, si ha creado sus propias aplicaciones de línea de negocio (LOB), puede implementarlas. Para ello, debe suscribirse a una cuenta de Google Developer, que le permite publicar las aplicaciones en un área privada en Google Play Store y sincronizarlas con Intune.

## Antes de empezar

1. Asegúrese de que ha configurado Intune y Android for Work para que trabajen juntos en la pestaña **Administrador** de la consola de Intune.

## Sincronización de una aplicación desde Google Play for Work Store


1. Vaya a [Google Play for Work Store](https://play.google.com/work). Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work.
2. Busque en la tienda la aplicación que desea implementar mediante Intune.
3. En la página de la aplicación elegida, seleccione **Aprobar**. En este ejemplo, ha elegido la aplicación Microsoft Excel.<br>
  ![Ejemplo de aprobación de la aplicación](/intune/deploy-use/media/approve.png)
4. Se abre una ventana de la aplicación que le pide que conceda permisos a la aplicación para realizar diversas operaciones. Debe elegir **Aprobar** para continuar.<br>
  ![Ejemplo de permisos para aprobar la aplicación](/intune/deploy-use/media/approve-app-permissions.png)
5. Tras unos instantes, verá un mensaje de confirmación indicando que la aplicación se ha aprobado y está disponible en la consola de administración de TI. 

## Publicar y después sincronizar una aplicación de línea de negocio desde Google Play for Work Store 

1. Vaya a la consola de desarrollador de Google Play, [play.google.com/apps/publish](play.google.com/apps/publish).
2. Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work. Si inicia sesión por primera vez, debe registrar y pagar una cuota para participar en el programa para desarrolladores de Google.
3. En la consola, elija **Agregar nueva aplicación**.
4. Puede cargar y proporcionar información sobre la aplicación de la misma manera que publica cualquier aplicación en Google Play Store. Sin embargo debe seleccionar la configuración **Solo hacer que esta aplicación esté disponible para mi organización (<*nombreDeOrganización*>)** como se muestra a continuación.<br>
  ![Opción para que solo la aplicación esté disponible para la organización](/intune/deploy-use/media/restrict.png)<br>
Esto garantiza que la aplicación solo está disponible para su organización y no está disponible en Google Play Store público.
Para más información sobre cómo cargar y publicar aplicaciones Android, consulte la [Ayuda de la consola de desarrollador de Google](https://support.google.com/googleplay/android-developer/answer/113469).
5. Una vez publicada la aplicación, vaya a [Google Play for Work Store](https://play.google.com/work). Inicie sesión con la misma cuenta que utilizó para configurar la conexión entre Intune y Android for Work. 
6. En el nodo **Aplicaciones** de la tienda, compruebe que puede ver la aplicación publicada. Tenga en cuenta que se ha aprobado automáticamente para sincronizarse con Intune.

## Implementación de una aplicación Android for Work

Normalmente, Intune se sincronizará dos veces al día con Google Play for Work Store. Si se ha aprobado una aplicación desde la tienda y todavía no la ve en el nodo **Aplicaciones compradas por volumen** del área de trabajo **Aplicaciones**, puede forzar una sincronización inmediata como sigue:

1. En la [consola de administración de Intune](https://manage.microsoft.com), elija **Administrador** > **Administración de dispositivos móviles** > **Android for Work**.
2. En la página **Configuración de la administración de dispositivos móviles de Android for Work**, elija **Sincronizar ahora**.
3. La página también muestra el tiempo y el estado de la última sincronización.

Cuando la aplicación se muestra en el nodo **Aplicaciones compradas por volumen** del área de trabajo **Aplicaciones**, puede [implementarla al igual como haría con cualquier otra aplicación](deploy-apps-in-microsoft-intune.md). Puede implementar la aplicación solo en grupos de usuarios. Actualmente, solo puede seleccionar las acciones **Necesaria** y **Desinstalar**. Desde octubre de 2016, comenzaremos a agregar la acción de implementación **Disponible** a los inquilinos nuevos. 

Después de implementar la aplicación, se instalará en los dispositivos especificados. No se pedirá al usuario del dispositivo su aprobación.



<!--HONumber=Oct16_HO2-->


