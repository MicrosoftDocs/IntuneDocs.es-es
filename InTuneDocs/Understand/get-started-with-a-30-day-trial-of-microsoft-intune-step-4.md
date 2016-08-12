---
title: "Crear directivas y publicar una aplicación para los usuarios | Microsoft Intune"
description: "Cómo crear directivas y publicar una aplicación al registrarse para obtener una evaluación gratuita de 30 días de Intune"
keywords: 
author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 51fba2b01d8978bc062c50c4388714609be0fdf0
ms.openlocfilehash: 1a41bfd926b1dac88ca8c8cd33483955f1150e34


---


# Crear directivas y publicar una aplicación para los usuarios de evaluación
Las directivas de Intune proporcionan una configuración con la que es más fácil: controlar la configuración de seguridad en dispositivos móviles, mantener la configuración de Firewall de Windows y Endpoint Protection de los equipos e implementar aplicaciones. Si está planeando usar Intune para los dispositivos que configura para su uso de producción después de la evaluación, es fundamental que siga las instrucciones de [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) y [Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).

Puede realizar dos tipos de instalaciones de aplicación mediante Intune. El primer tipo es una **instalación requerida**, que implementa automáticamente la aplicación en los equipos administrados. El segundo es una **instalación disponible**, que implementa la aplicación o un vínculo a la aplicación de Portal de empresa de Intune, de forma que los usuarios pueden elegir si quieren instalarlo en sus equipos o en sus dispositivos móviles.

Antes de usar Intune para implementar aplicaciones, asegúrese de que tiene las licencias apropiadas para publicar, distribuir y usar la aplicación. El área de trabajo **Licencias** le permite agregar y administrar la información de contratos de licencias de aplicaciones o software adquiridos a través de Contratos de licencias por volumen de Microsoft, así como de aplicaciones o software de Microsoft o de otros fabricantes adquiridos por otros medios. A continuación, puede crear informes de licencias, que muestran la información de uso de las licencias administradas en toda la empresa, para mantenerse informado de la actividad de uso de las licencias.

Por medio de estos pasos, se establece una directiva de configuración de dispositivos móviles y una directiva de firewall para equipos Windows, y se configurar Skype como instalación disponible para dispositivos móviles después de haberse inscrito. Después de agregar e implementar una nueva directiva, todos los usuarios o dispositivos del grupo en el que se ha implementado la directiva heredan la configuración como directiva de línea de base. Siempre puede revisar y editar los detalles de estas directivas más adelante en el área de trabajo **Directiva** en la consola de administración.

## Creación e implementación de una directiva de configuración de dispositivo móvil

1.  Abra la [consola de administración de Intune](https://manage.microsoft.com/).

2.  En el panel de la izquierda, elija el icono **Directiva**.

3.  En la lista **Tareas** de la página **Información general de directivas**, seleccione **Agregar directiva**.

4.  En la lista de directivas, expanda la plataforma para la que quiere crear una directiva, seleccione **Configuración general**, elija **Crear e implementar una directiva con la configuración recomendada** y, después, haga clic en **Crear directiva**.

5.  Cuando se le pida que **Seleccione los grupos para los que quiere implementar esta directiva**, seleccione **Mis usuarios de prueba** de la lista y elija **Agregar**&gt;**Aceptar**.

La directiva aparecerá en la lista de directivas de configuración y se implementará al grupo **Mis usuarios de pruebas** . Haga doble clic en la directiva para ver su configuración.

## Publicación de la aplicación de Skype para dispositivos móviles

1.  En la [consola de administración de Intune](https://manage.microsoft.com/), haga clic en el icono **Aplicaciones** y elija **Aplicaciones**&gt;**Agregar aplicación**. Si se le solicitan, introduzca sus credenciales de Intune.

    > [!NOTE]
    > Al iniciar el **editor de software de Intune** por primera vez, se producirá una breve demora mientras se instala la aplicación.

2.  Revise la advertencia de seguridad y seleccione **Ejecutar**.

3.  En la página **Antes de comenzar**, seleccione **Siguiente**.

4.  En la página **Instalación de software** , en **Seleccionar cómo el software debe ponerse a disposición de los dispositivos**, seleccione **Vínculo externo**.

5.  Escriba el vínculo externo del software en **Especificar la dirección URL** y elija **Siguiente**. Asegúrese de comenzar la dirección URL con **https://**. Para la aplicación de Skype, use el vínculo siguiente que coincida con la plataforma de dispositivo móvil que emplea:

    -   **iOS:** [https://itunes.apple.com/es/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:** [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 o Windows Phone 8.1:** [http://www.windowsphone.com/es-es/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  En la página **Descripción del software**, proporcione la información que quiere que los usuarios vean en el Portal de empresa para el software y elija **Siguiente**. Están disponibles los siguientes valores de configuración (este ejemplo hace referencia a Skype):

    -   **Editor:** escriba el nombre del editor, **Microsoft**

    -   **Nombre:** Escriba **Skype**

    -   **Descripción:** Escriba una descripción para el software, como **aplicación de comunicación de Skype**

    -   **Categoría:** Seleccione la categoría más adecuada para el software, como **Colaboración**

    -   **Mostrar esta aplicación como destacada y resaltarla en el portal de empresa:** seleccione esta opción para mostrar la aplicación de forma destacada en el Portal de empresa en dispositivos móviles.

    -   **Icono:**  (Opcional) Elija si desea asociar un icono con el software. El tamaño de icono máximo es 250 x 250 píxeles, pero el tamaño de icono recomendado es 32 x 32 píxeles.

7.  En la página **Resumen**, compruebe la información del software y elija **Cargar**. Elija **Cerrar** para salir del asistente.

8.  En la [consola de administración de Intune](https://manage.microsoft.com/), elija **Aplicaciones** &gt; **Aplicaciones** &gt; **Skype** &gt; **Administrar la implementación**.

9. En la página **Seleccionar grupos**, seleccione **Mis usuarios de prueba** para implementar el software en ese grupo de usuarios y, después, elija **Agregar**&gt;**Siguiente**.

10. En la página **Acción de implementación** , seleccione **Instalación disponible** en la columna **Aprobación** para su grupo.

11. Seleccione **Finalizar**.

La aplicación de Skype ahora se puede instalar en dispositivos móviles desde el Portal de empresa, pero primero debe instalar el software de Intune en equipos y dispositivos móviles.

### Pasos siguientes
Enhorabuena. Acaba de completar el paso 4 del tutorial de *evaluación de Microsoft Intune*.

>[!div class="step-by-step"]

>[&larr; **Crear grupos**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)     [**Inscribir dispositivos** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md)  



<!--HONumber=Aug16_HO2-->


