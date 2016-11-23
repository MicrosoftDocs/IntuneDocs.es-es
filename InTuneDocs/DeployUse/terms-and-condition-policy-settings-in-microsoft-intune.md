---
title: "Configuración de la directiva de términos y condiciones | Microsoft Intune"
description: "Puede implementar los términos y condiciones de Intune en los grupos de usuarios para explicar en qué afecta la inscripción, el acceso a los recursos de trabajo y el uso del portal de empresa a los dispositivos y los usuarios."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6edf0ac1-4f46-4543-a9e5-f484ac37e9a5
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cba0d6d781d3050f4dd8aabd661d677ae849eff1
ms.openlocfilehash: bc9a7b837ab4dcd402aeec572b819d56070eba82


---

# <a name="terms-and-condition-policy-settings-in-microsoft-intune"></a>Configuración de la directiva de términos y condiciones en Microsoft Intune
Puede implementar los términos y condiciones de Intune en los grupos de usuarios para explicar en qué afecta la inscripción, el acceso a los recursos de trabajo y la aplicación Portal de empresa a los dispositivos y los usuarios. Los usuarios deben aceptar los términos y las condiciones para poder usar el portal de empresa a fin de inscribirse y obtener acceso a su trabajo.

Puede crear e implementar varias directivas que contienen diferentes términos y condiciones. También puede generar versiones de los mismos términos y condiciones en distintos idiomas e implementarlas en los grupos correspondientes.

## <a name="create-a-terms-and-conditions-policy"></a>Crear una directiva de términos y condiciones

1.  En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), haga clic en **Directiva** &gt; **Términos y condiciones**.

    ![Captura de pantalla de la directiva de términos y condiciones](./media/pol-sa-terms-conditions.png)

2.  Haga clic en **Agregar** para crear una nueva directiva de términos y condiciones.

    También puede **Editar** o **Eliminar** una directiva existente.

3.  En la página **Crear términos y condiciones**, especifique la siguiente información:

    -   **Nombre**&mdash;Nombre de directiva único que aparece en la consola de Intune.

    -   **Descripción**&mdash;Detalles que le ayudan a identificar la directiva en la consola de Intune.

    -   **Título**&mdash;Título que ven los usuarios en el Portal de empresa.

    -   **Texto para explicar qué significa la aceptación del usuario**&mdash;Etiqueta que ven los usuarios en relación con la aceptación. Por ejemplo, "Acepto los términos y condiciones".

4.  Cuando termine, haga clic en **Guardar**. La nueva directiva se muestra en el nodo **Términos y condiciones** del área de trabajo **Directiva**.

## <a name="deploy-a-terms-and-conditions-policy"></a>Implementar una directiva de términos y condiciones

1.  En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), haga clic en **Directiva** &gt; **Términos y condiciones**.

2.  En la lista **Directivas de términos y condiciones**, seleccione la directiva que desea implementar y, luego, haga clic en **Administrar implementación**.

3.  En el cuadro de diálogo **Administrar implementación**, seleccione los grupos de usuarios en los que quiera implementar la directiva y haga clic en **Aceptar**.

    Cuando los usuarios de destino tienen acceso al portal de la empresa, Intune muestra los términos y las condiciones que implementó. Los usuarios deben aceptar estos términos para tener acceso a los recursos de la empresa.

## <a name="monitor-a-terms-and-conditions-policy"></a>Supervisar una directiva de términos y condiciones

1.  En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), haga clic en **Directiva** &gt; **Términos y condiciones**.

2.  En la ventana **Crear nuevo informe**, haga clic en **Ver informe**. El informe se abrirá e indicará los usuarios que aceptaron los términos y las condiciones que implementó.

### <a name="updates-and-version-control-for-terms-and-conditions"></a>Actualizaciones y control de versiones de los términos y condiciones
Al editar una directiva existente de términos y condiciones, puede elegir el comportamiento al implementar la directiva. Use el procedimiento siguiente, que lo ayudará a actualizar las directivas existentes de términos y condiciones.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Trabajar con varias versiones de los términos y las condiciones

1.  En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), haga clic en **Directiva** &gt; **Términos y condiciones**.

2.  Seleccione la directiva de términos y condiciones que desea modificar y luego haga clic en **Editar**.

3.  En la página **Editar términos y condiciones**, realice las modificaciones necesarias y luego especifique si esta nueva versión exige que todos los usuarios acepten los términos y las condiciones o si solo los usuarios nuevos verán la versión nueva.

    Se recomienda aumentar el número de versión y exigir aceptación cada vez que realice cambios importantes en la directiva de términos y condiciones. Si va a corregir errores tipográficos o cambiar el formato, por ejemplo, mantenga el número de versión actual.

### <a name="see-also"></a>Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Nov16_HO2-->


