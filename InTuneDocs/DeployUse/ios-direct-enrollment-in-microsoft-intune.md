---
# required metadata

title: Inscripción directa para dispositivos iOS con Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscribir directamente dispositivos iOS mediante Apple Configurator
Intune permite inscribir dispositivos iOS de empresa con la herramienta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) desde un equipo Mac. Este proceso no restablece los valores de fábrica del dispositivo e inscribe el dispositivo con una directiva predefinida. Este método está destinado a dispositivos cuyo valor de afiliación de usuario está establecido en **Sin afinidad de usuario** y requiere una conexión USB entre el dispositivo iOS y un equipo Mac para configurar la inscripción corporativa. No se admite la aplicación de portal de empresa para dispositivos inscritos de forma directa. Esta guía supone que se usa Apple Configurator 2.0 en un equipo Mac.

1.  **Crear un perfil para dispositivos**
    Un perfil de inscripción de dispositivo define la configuración que se aplica a los dispositivos. Si aún no lo tiene, cree un perfil de inscripción de dispositivo para los dispositivos iOS inscritos mediante Apple Configurator.

    #### Para crear un perfil

    1.  En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Directiva** &gt; **Inscripción de dispositivos corporativos** y haga clic en **Agregar…**.

        ![Página Crear perfil de inscripción de dispositivo](../media/pol-sa-corp-enroll.png)

    2.  Especifique los detalles de los perfiles de dispositivo:

        -   **Nombre** : nombre del perfil de inscripción de dispositivo. No es visible para los usuarios.

        -   **Descripción**: descripción del perfil de inscripción de dispositivo. No es visible para los usuarios.

        -   **Afiliación de usuario** : especifica cómo se inscriben los dispositivos. Para la inscripción directa, seleccione **Sin afinidad de usuario**..

        -   **Asignación previa de grupo de dispositivos**: todos los dispositivos que implementan este perfil pertenecerán inicialmente a este grupo. Puede reasignar los dispositivos después de la inscripción.

    3.  Haga clic en **Guardar perfil** para agregar el perfil.

2.  **Agregar dispositivos iOS para inscribirse con Apple Configurator**
    En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Grupos** &gt; **Todos los dispositivos** &gt; **Dispositivos corporativos inscritos previamente** &gt; **Mediante número de serie de iOS** y haga clic en **Agregar dispositivos...**..

    ![Asistente de configuración de iOS](../media/pol-SA-enroll-iOS-SetupAssistant.png)

      Puede agregar dispositivos de dos maneras:

    -   **Cargar un archivo CSV que contiene números de serie**: cree una lista de valores separados por comas (.csv) con dos columnas sin encabezado, limitada a 5000 dispositivos o 5 MB por archivo .csv.

        |||
        |-|-|
        |&lt;Serie 1&gt;|&lt;Detalles del dispositivo n.º 1&gt;|
        |&lt;Serie 2&gt;|&lt;Detalles del dispositivo n.º 2&gt;|
        Este archivo .csv, cuando se ve en un editor de texto, aparece como:

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **Agregar manualmente los detalles del dispositivo**: escriba el número de serie y los detalles de hasta cinco dispositivos y después haga clic en **Siguiente**..

    > [!NOTE]
    > Si posteriormente necesita quitar dispositivos corporativos de la administración de Intune, debe quitar el número de serie del dispositivo de Intune del grupo **Dispositivos corporativos** para deshabilitar la inscripción de dispositivos.  Si Intune realiza un procedimiento de recuperación ante desastres en el momento en que se quitan los números de serie o en torno a este momento, se deberá comprobar que solo los números de serie de los dispositivos activos están presentes en ese grupo.

3.  **Seleccionar dispositivos para inscribirlos**
    Confirme los dispositivos que se van a inscribir. No se pueden importar los números de serie ya inscritos o inscritos por otros medios. Haga clic en **Siguiente** para continuar.

4.  **Asignar el perfil**
    Especifique el perfil que se va a asignar a los dispositivos agregados desde la lista de perfiles disponibles, consulte los **detalles del perfil de inscripción**y, después, haga clic en **Finalizar**. Los dispositivos agregados manualmente se pueden asignar a cualquier perfil de inscripción.

5.  **Seleccionar un perfil para implementarlo en dispositivos iOS**
    En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Directiva** &gt; **Inscripción de dispositivos corporativos** y seleccione el perfil de dispositivo que desee implementar en los dispositivos móviles. Este perfil debería ser el mismo que asignó para su implementación en el paso anterior. Haga clic en **Exportar...** en la barra de tareas. Haga clic en **Descargar perfil** y guarde el archivo .mobileconfig descargado.

6.  **Transferir el archivo**
    Copie el archivo .mobileconfig descargado en un equipo Mac.
    > [!NOTE]
    > La URL del perfil de inscripción es válida durante dos semanas de cuando se exporta. Después de dos semanas, debe exportar una nueva URL de perfil de inscripción para inscribir dispositivos iOS con el Asistente de configuración.
7.  **Preparar el dispositivo con Apple Configurator**
    Los dispositivos iOS están conectados al equipo Mac e inscritos para la administración de dispositivos móviles.

    1.  En un equipo Mac, inicie **Apple Configurator 2.0**..

    2.  Conecte el dispositivo iOS al equipo Mac con un cable USB. Cierre **Fotos**, **iTunes** y otras aplicaciones que se abran en el dispositivo cuando se detecte el dispositivo.

    3.  En Apple Configurator, haga clic en el dispositivo iOS conectado y después haga clic en el botón **Agregar**. Las opciones que se pueden agregar al dispositivo aparecen en la lista desplegable. Haga clic en **Perfiles**. .

    4.  Utilice el selector de archivos para seleccionar el archivo .mobileconfig exportado desde Intune y después haga clic en **Agregar**. El perfil se agrega al dispositivo.  Si el dispositivo es **No supervisado**, la instalación requerirá la aceptación en el dispositivo.

8.  **Instalar el perfil**
    Todo está listo para instalar el perfil en el dispositivo iOS. El dispositivo debe haber completado el Asistente de configuración y estar listo para usarse.  Si la inscripción implica implementaciones de aplicaciones, el dispositivo debe tener un identificador de Apple configurado, porque las implementaciones de aplicaciones requerirán que disponga de un identificador de Apple con la sesión iniciada en App Store.

    ###### Completar la aceptación del perfil en dispositivos iOS no supervisados

    1.  Desbloquee el dispositivo iOS.

    2.  En el diálogo **Instalar el perfil** de **Perfil de administración**, pulse **Instalar**..

    3.  Facilite el **Código de acceso del dispositivo** o el **Id. de Apple**, si es necesario.

    4.  Acepte la **Advertencia** y pulse **Instalar**..

    5.  Acepte la **Advertencia remota** y pulse **Confiar**..

    6.  Cuando el cuadro **Perfil instalado** confirma que el perfil se ha **Instalado**, haga clic en **Listo**..

9. **Comprobar el perfil**
    En el dispositivo iOS, inicie **Configuración** y vaya a **General** &gt; **Administración de dispositivos** &gt; **Perfil de administración** &gt;, confirme que la instalación del perfil aparezca y compruebe las restricciones de directivas de iOS y las aplicaciones instaladas. Las aplicaciones y las restricciones de directivas pueden tardar hasta 10 minutos en aparecer en el dispositivo.

10. **Distribuir los dispositivos**
    Ahora el dispositivo iOS está inscrito con Intune y administrado.


### Consulte también
[Preparar la inscripción de dispositivos](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


