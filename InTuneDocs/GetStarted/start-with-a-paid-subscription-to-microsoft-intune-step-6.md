---
# required metadata

title: Creación de directivas y publicación de una aplicación | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Creación de directivas y publicación de una aplicación
Las directivas de Intune proporcionan una configuración con la que es más fácil controlar la configuración de seguridad en dispositivos móviles, mantener la configuración de Firewall de Windows y Endpoint Protection de los equipos e implementar aplicaciones. Puede obtener más información en [Manage settings and features on your devices with Microsoft Intune policies](/Intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) (Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune) y [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](/Intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) (Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune)..

Puede realizar dos tipos de instalaciones de aplicación mediante Intune. El primer tipo es una **instalación requerida**, que implementa automáticamente la aplicación en los equipos administrados. El segundo es una **instalación disponible**, que implementa la aplicación o un vínculo a la aplicación de portal de empresa de Intune, de forma que los usuarios pueden elegir si quieren instalarlo en sus equipos o en sus dispositivos móviles.

<!-- this section really isn't necessary and confuses a lot of people because most mobile device apps aren't licensed this way (and our licensing/reporting features aren't super helpful). I think it's best to avoid this during a quick start guide.

Before using Intune to deploy apps, make sure that you have the appropriate licenses to publish, distribute, and use the app. The Licenses workspace lets you add and manage license agreement information for apps or software purchased through Microsoft Volume Licensing agreements, and for Microsoft or non-Microsoft software that was purchased by other means. You can then create license reports that display managed license usage information throughout your company to stay informed of license usage activity.
-->

Los pasos siguientes le ayudarán a establecer una directiva de configuración de dispositivos móviles y una directiva de firewall para equipos Windows. También le ayudarán a configurar Skype como instalación disponible para dispositivos móviles después de haberse inscrito.

> [!TIP]
> Después de agregar e implementar una nueva directiva, todos los usuarios o dispositivos del grupo en el que se ha implementado la directiva heredan la configuración como directiva de línea de base. Puede revisar y editar los detalles de estas directivas en cualquier momento más adelante desde el área de trabajo de la Directiva.


## Creación e implementación de una directiva de configuración de dispositivo móvil

1.  Abra la [consola de administración de Intune](https://manage.microsoft.com/)..

2.  En el panel de la izquierda, elija el icono **Directiva**.

    ![admin-console-policy-workspace](./media/policy.png)

3.  En la lista **Tareas** de la página **Información general de directivas**, elija **Agregar directiva**..

4.  En la lista de directivas, expanda la plataforma para la que quiere crear una directiva, elija **Configuración general** > **Crear e implementar una directiva con la configuración recomendada** > **Crear directiva**..

5.  Cuando se le pida que **Seleccione los grupos para los que quiere implementar esta directiva**, elija **Usuarios de Intune** (el grupo creado durante el paso anterior) en la lista de grupos disponibles y elija **Agregar** > **Aceptar**..

La directiva aparece en la lista de directivas de configuración y se implementa en el grupo **Usuarios de Intune**. Haga doble clic en la directiva para ver su configuración.

## Publicación de la aplicación de Skype para dispositivos móviles

1.  En la [consola de administración de Intune](https://manage.microsoft.com/), haga clic en el icono **Aplicaciones** y elija **Aplicaciones** > **Agregar aplicación**. Si se le solicitan sus credenciales de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], especifíquelas.

    ![admin-console-apps-workspace](./media/apps.png)

    > [!NOTE]
    > Al iniciar el **editor de software de Intune** por primera vez, se producirá una breve demora mientras se instala la aplicación.

2.  Revise la advertencia de seguridad y elija **Ejecutar**..

3.  En la página **Antes de comenzar**, elija **Siguiente**..

4.  En la página **Instalación de software**, en **Seleccione cómo debe ponerse a disposición de los dispositivos este software**, elija **Vínculo externo**..

5.  Especifique el vínculo externo del software en **Especificar la dirección URL** y elija **Siguiente**. Asegúrese de preceder la dirección URL con **http://**. Para la aplicación de Skype, use el vínculo siguiente que coincida con la plataforma de dispositivo móvil que emplea:

    -   **iOS:**   [https://itunes.apple.com/es/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:**  [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 o Windows Phone 8.1:**  [http://www.windowsphone.com/es-es/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  En la página **Descripción del software**, proporcione la información que quiere que los usuarios vean en el portal de empresa para el software y elija **Siguiente**. Están disponibles los siguientes valores de configuración (este ejemplo hace referencia a Skype):

    -   **Publicador:** Escriba el nombre del publicador, "Microsoft"

    -   **Nombre:** Escriba **Skype**

    -   **Descripción:** Escriba una descripción para el software, como **aplicación de comunicación de Skype**

    -   **Categoría:** Seleccione la categoría más adecuada para el software, como **Colaboración**

    -   **Mostrar esta aplicación como destacada y resaltarla en el portal de empresa:** Seleccione esta opción para mostrar la aplicación de forma destacada en el portal de empresa en dispositivos móviles.

    -   **Icono**: elija si quiere asociar un icono al software. El tamaño máximo del icono opcional es 250 x 250 píxeles y el tamaño recomendado es 32 x 32 píxeles.

7.  En la página **Resumen**, compruebe la información del software y elija **Cargar**. Elija **Cerrar** para salir del asistente.

8.  En la [consola de administración de Intune](https://manage.microsoft.com/), elija **Aplicaciones** > **Aplicaciones** > **Skype** > **Administrar la implementación**..

9. En la página **Seleccionar grupos**, elija **Usuarios de Intune** para implementar el software en ese grupo de usuarios y elija **Agregar** > **Siguiente**..

10. En la página **Acción de implementación** , seleccione **Instalación disponible** en la columna **Aprobación** para su grupo.

11. Elija **Finalizar**..

La aplicación Skype ahora se puede instalar en dispositivos móviles desde el portal de empresa, pero primero debe instalar el software de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] en equipos y dispositivos móviles.


### Pasos siguientes
Enhorabuena. Acaba de completar el paso 6 de la *Guía de inicio rápido de Intune*..

>[!div class="step-by-step"]

>[&larr; **Organizar usuarios y dispositivos**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**Personalizar el portal de empresa** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  


<!--HONumber=May16_HO1-->

