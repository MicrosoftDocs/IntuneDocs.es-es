---
# required metadata

title: Inscripción mediante Asistente de configuración para dispositivos iOS con Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscribir dispositivos iOS con Apple Configurator y el Asistente de configuración
Intune permite inscribir dispositivos iOS de empresa con la herramienta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) desde un equipo Mac. Este proceso restablece la configuración de fábrica del dispositivo y lo prepara para que el nuevo usuario del dispositivo ejecute el Asistente de configuración con las directivas de la compañía preinstaladas.


## Inscripción mediante Asistente de configuración para dispositivos iOS con Microsoft Intune
Con el Configurador de Apple, puede restablecer los valores de fábrica de los dispositivos iOS y prepararlos para la configuración por parte del usuario nuevo del dispositivo.  Este método requiere que se conecte el dispositivo iOS a un equipo Mac a través de una conexión USB para configurar la inscripción corporativa. Además, el método supone que se está usando Apple Configurator 2.0. En la mayoría de los casos será necesario que la directiva aplicada al dispositivo iOS incluya *afinidad de usuario* para habilitar la aplicación Portal de empresa de Intune.

**Requisitos previos**
* Acceso físico a dispositivos iOS: deben ser dispositivos sin configurar (restablecidos a estado de fábrica) sin protección por contraseña
* Números de serie del dispositivo: [Cómo obtener un número de serie de iOS](https://support.apple.com/en-us/HT204308)
* Cables de conexión USB
* Equipo Mac con [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


1.  **Crear un grupo de dispositivos móviles** (opcional) Si su empresa requiere grupos de dispositivos móviles para ayudar a administrar los dispositivos, cree los grupos. [Use grupos para administrar usuarios y dispositivos con Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

2.  **Crear un perfil para dispositivos** Un perfil de inscripción de dispositivo define la configuración que se aplica a un grupo de dispositivos. Si aún no lo tiene, cree un perfil de inscripción de dispositivo para los dispositivos iOS inscritos mediante Apple Configurator.

    ###### Para crear un perfil

    1.  En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Directiva** &gt; **Dispositivos corporativos** y, después, elija **Agregar...**.

    ![Crear perfil de inscripción de dispositivo](../media/pol-sa-corp-enroll.png)

    2.  Especifique los detalles de los perfiles de dispositivo:

        -   **Nombre** : nombre del perfil de inscripción de dispositivo. (No es visible para los usuarios)

        -   **Descripción**: descripción del perfil de inscripción de dispositivo. (No es visible para los usuarios)

        -   **Detalles de inscripción**: especifica cómo se inscriben los dispositivos.

            -   **Pedir afinidad de usuario**: el dispositivo iOS se puede afiliar con un usuario durante la instalación inicial y, después, se le puede permitir el acceso a los datos y al correo electrónico de la compañía como dicho usuario. Para la mayoría de los escenarios del Asistente de configuración, use **Solicitar afinidad de usuario**.
            Este modo admite varios escenarios:

                -   **Dispositivo personal de empresa**: elección de un dispositivo propio, o lo que se conoce como "Choose Your Own Device" (CYOD). Similar a dispositivos personales o de propiedad privada, pero el administrador tiene ciertos privilegios, incluidos permisos para borrar, restablecer, administrar y anular la inscripción del dispositivo. El usuario del dispositivo puede instalar aplicaciones y tiene la mayoría de los demás permisos para usar el dispositivo que no estén bloqueados por la directiva de administración.

                -   **Cuenta de administrador de inscripción de dispositivos** : el dispositivo se inscribe con una cuenta de administrador de Intune especial. Se puede administrar como una cuenta privada, pero solo un usuario que conozca las credenciales del administrador de inscripción puede instalar aplicaciones, borrar, restablecer, administrar y anular la inscripción del dispositivo. Para obtener información sobre cómo inscribir un dispositivo que compartan varios usuarios mediante una cuenta común, vea [Inscribir dispositivos propiedad de la empresa con el Administrador de inscripción de dispositivos de Microsoft Intune](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

            -   **No hay afinidad de usuario**: el dispositivo no tiene usuarios. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren una afiliación de usuario están deshabilitadas o no funcionarán.

        -   **Asignación previa de grupo de dispositivos**: todos los dispositivos que implementan este perfil pertenecerán inicialmente a este grupo. Puede reasignar los dispositivos después de la inscripción.

          -  **Programa de inscripción de dispositivos**: el programa de inscripción de dispositivos de Apple (DEP) no se puede utilizar con la inscripción del Asistente de configuración. Asegúrese de que el botón de alternancia está establecido en **desactivado**.

    3.  Elija **Guardar perfil** para agregar el perfil.

3.  **Agregar dispositivos iOS para inscribirse con el Asistente para la instalación** En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos corporativos** &gt; **Todos los dispositivos** y después elija **Agregar dispositivos...**. Puede agregar dispositivos de dos maneras:

    ![Agregar cuadro de diálogo de dispositivos](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   **Cargar un archivo CSV que contiene números de serie**: cree una lista de valores separados por comas (.csv) con dos columnas sin encabezado, limitada a 5000 dispositivos o 5 MB por archivo .csv.

        |||
        |-|-|
        |&lt;Serie 1&gt;|&lt;Detalles del dispositivo n.º 1&gt;|
        |&lt;Serie 2&gt;|&lt;Detalles del dispositivo n.º 2&gt;|
        Este archivo .csv, cuando se ve en un editor de texto, aparece como:

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **Agregar manualmente los detalles del dispositivo**: especifique el número de serie y los detalles de hasta cinco dispositivos

    > [!NOTE]
    > Si posteriormente necesita quitar dispositivos corporativos de la administración de Intune, es posible que tenga que quitar el número de serie del dispositivo de Intune del grupo de dispositivos **Mediante número de serie de iOS** en **Dispositivos corporativos inscritos previamente** para deshabilitar la inscripción de dispositivos.  Si Intune realiza un procedimiento de recuperación ante desastres en el momento en que se quitan los números de serie o en torno a este momento, se deberá comprobar que solo los números de serie de los dispositivos activos están presentes en ese grupo.

    Seleccione **Siguiente**.

4.  **Seleccionar dispositivos para inscribir** Confirme los dispositivos que se van a inscribir. No se pueden importar los números de serie ya inscritos o inscritos por otros medios. Elija **Siguiente** para continuar.

5.  **Asignar perfil** Especifique el perfil que se va a asignar a los dispositivos agregados desde la lista de perfiles disponibles, consulte los **detalles del perfil de inscripción** y luego elija **Finalizar**. Los dispositivos agregados manualmente se pueden asignar a cualquier perfil de inscripción.

6.  **Exportar un perfil para implementarlo en dispositivos iOS** En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Directiva** &gt; **Inscripción de dispositivos corporativos** y, después, seleccione el perfil de dispositivo que quiera implementar en los dispositivos móviles. Elija **Exportar...** en la barra de tareas. Copie y guarde el valor de **Dirección URL del perfil**. Se cargará en Apple Configurator más tarde para definir el perfil de Intune utilizado por los dispositivos iOS.
    Para admitir Apple Configurator 2, se debe editar URL de perfil 2.0. Reemplazar
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    con

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   En el procedimiento siguiente, esta dirección URL de perfil se carga en el servicio DEP de Apple mediante la herramienta Apple Configurator para definir el perfil de Intune utilizado por dispositivos iOS.



7.  **Preparar el dispositivo con Apple Configurator** Los dispositivos iOS están conectados al equipo Mac e inscritos para la administración de dispositivos móviles.

    1.  En un equipo Mac, abra **Apple Configurator 2**. En la barra de menús, elija **Apple Configurator 2** y, después, elija **Preferencias**.

         > [!WARNING]
         > Los dispositivos se restablecerán en la configuración de fábrica durante el proceso de inscripción. Como práctica recomendada, restablezca el dispositivo y enciéndalo. Como práctica recomendada, los dispositivos deberían estar en la pantalla **Hola** cuando conecte el dispositivo.

    2. En el panel de preferencias, seleccione **Servidores** y elija el símbolo “+” debajo del panel izquierdo para iniciar el asistente del servidor MDM. Seleccione **Siguiente**.

    3. Escriba el **Nombre** y la **dirección URL de inscripción** para el servidor MDM del paso 6 anterior. En la dirección URL de inscripción, escriba la dirección URL de perfil de inscripción exportada desde Intune. Seleccione **Siguiente**.  

       Si recibe una advertencia sobre los requisitos de perfil de confianza para Apple TV, puede cancelar sin riesgo alguno la opción **Trust Profile** (Perfil de confianza) al elegir la “X” de color gris. También de forma segura, puede omitir cualquier advertencia de certificado Anchor. Para continuar, elija **Siguiente** hasta que se complete el asistente.

    4.  En el panel **Servidores**, elija “Editar” al lado del perfil del nuevo servidor. Asegúrese de que la dirección URL de inscripción coincide exactamente con la dirección URL exportada desde Intune. Vuelva a escribir la dirección URL original si es diferente y **guarde** el perfil de inscripción exportado desde Intune.

    5.  Conecte los dispositivos móviles iOS al equipo Apple con un adaptador USB.

        > [!WARNING]
        > Los dispositivos se restablecerán en la configuración de fábrica durante el proceso de inscripción. Como práctica recomendada, restablezca el dispositivo y enciéndalo. Como práctica recomendada, los dispositivos deberían estar en la pantalla **Hola** cuando inicia el Asistente de configuración.

    6.  Elija **Preparar**. En el panel **Prepare iOS Device** (Preparar el dispositivo iOS), seleccione **Manual** y luego elija **Siguiente**.

    7. En el panel **Enroll in MDM Server** (Inscribir en servidor MDM), seleccione el nuevo servidor y elija **Siguiente**.

    8. En el panel **Supervise Devices** (Supervisar dispositivos), seleccione el nivel de supervisión y luego elija **Siguiente**.

    9. En el panel **Create an Organization** (Crear una organización), seleccione la **Organización** o cree una nueva y luego elija **Siguiente**.

    10. En el panel **Configurar el Asistente de configuración de iOS**, elija los pasos que se presentan al usuario y, después, elija **Preparar**. Si se le solicita, autentíquese para actualizar la configuración de confianza.  

    11. Cuando el dispositivo iOS termina la preparación, puede desconectar el cable USB.  

8.  **Distribuir los dispositivos** Los dispositivos ya están listos para la inscripción corporativa. Apague los dispositivos y distribúyalos a los usuarios. Cuando se encienda el dispositivo, se iniciará el Asistente de configuración.



### Consulte también
[Preparar la inscripción de dispositivos](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=Jun16_HO3-->


