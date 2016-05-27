---
# required metadata

title: Iniciar una prueba de Microsoft Intune e implementar la directiva de PIN de iOS | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 06cb9a73-0f17-44b3-b334-86c98020316e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Iniciar una prueba de Microsoft Intune e implementar la directiva de PIN de iOS
Estas instrucciones paso a paso le ayudarán a configurar una prueba de Intune y una directiva de PIN para los dispositivos iOS. Para obtener una lista de otras tareas de evaluación de Intune comunes que puede probar, vea [Common Microsoft Intune evaluation tasks](common-microsoft-intune-evaluation-tasks.md) (Tareas de evaluación comunes de Microsoft Intune)..



## Revisar los requisitos previos de esta tarea.

-   PC Windows con Internet Explorer para realizar tareas administrativas.

-   Dispositivo iOS 7.1 o una versión posterior para probar la validación de directivas de usuario.

-   Teléfono para autenticarse durante la suscripción a la prueba.

## Crear una cuenta de prueba gratuita de Intune.
> [!NOTE]
> Si ya tiene una suscripción a Intune, omita esta sección y vaya a la siguiente.

1.  Con un equipo Windows, haga clic con el botón derecho en **Internet Explorer** (IE) y seleccione **Exploración de InPrivate**..

    ![Iniciar la exploración de InPrivate](../media/30-day-trial-walkthrus/30day-start-trial-1-InPrivate.png)

2.  Vaya al [portal de suscripción a Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1), proporcione la información pedida y haga clic en **Siguiente**..

    ![Registrarse para obtener una cuenta](../media/30-day-trial-walkthrus/30day-start-trial-2-abt-you.png)

3.  Escriba un identificador de usuario y una contraseña para la cuenta de administrador y haga clic en **Siguiente**. Usará este identificador para iniciar sesión en el portal de Intune y realizar tareas de administración.

    ![Crear un identificador](../media/30-day-trial-walkthrus/30day-start-trial-3-createID.png)

4.  Escriba su número de teléfono móvil y haga clic en **Envíame un mensaje** para validarlo.

    ![Validar la información](../media/30-day-trial-walkthrus/30day-start-trial-4-textme.png)

5.  Guarde la información que se muestra en la pantalla y, después, haga clic en **You're ready to go...** (Ya está listo)..

    ![Listo](../media/30-day-trial-walkthrus/30day-start-trial-5-ReadyToGo.png)

## Crear un usuario de prueba.

1.  En un equipo Windows, haga clic en **Inicio** para ir a la página de administración de usuarios.

    ![Vaya a la página de administración de usuarios.](../media/30-day-trial-walkthrus/30day-crt-user-6-click-start.png)

2.  Haga clic en el botón **+** para agregar un usuario.

    ![Agregar un usuario](../media/30-day-trial-walkthrus/30day-crt-user-7-click-plus.png)

3.  En la página **Crear nueva cuenta de usuario**:

    1.  Proporcione la información del usuario de la prueba.

    2.  Seleccione la opción **Escribir contraseña**.

    3.  Desactive la casilla **Hacer que este usuario cambie su contraseña la próxima vez que inicie sesión**.

    4.  Haga clic en **Crear**..

    ![Creación de cuentas de usuario](../media/30-day-trial-walkthrus/30day-crt-user-8-add-user-info.png)

4.  En la página de confirmación de creación del usuario, haga clic en **Cerrar**..

    ![Página de confirmación de creación del usuario](../media/30-day-trial-walkthrus/30day-crt-user-9-close-confirm.png)

5.  Haga clic en el botón **Actualizar** para ver el usuario de prueba creado.

    ![Confirmación de cuenta](../media/30-day-trial-walkthrus/30day-crt-user-10-refresh-user.png)

## Configurar una directiva de PIN de iOS para el usuario de prueba

1.  Use un equipo con Windows y establezca que la autoridad de MDM sea Intune:

    1.  Vaya a la [consola de administración de Intune](http://manage.microsoft.com/), inicie sesión con su cuenta de administrador y haga clic en **Empezar a administrar dispositivos móviles**. Se abre la página Entidad de administración de dispositivos móviles.

        ![Introducción a la consola de Intune](../media/30-day-trial-walkthrus/30day-cfg-pol-11-start-mg-mobl-dev.png)

    2.  Haga clic en el vínculo **Establecer la entidad de administración de dispositivos móviles**.

        ![Establecer la entidad de administración de dispositivos móviles](../media/30-day-trial-walkthrus/30day-cfg-pol-12-link-set-mdm.png)

2.  Habilite los dispositivos iOS para la inscripción. Este proceso configura un certificado de confianza entre el Servicio de notificaciones push de Apple (APNs) y su suscripción a Intune.

    1.  Haga clic en **Habilitar la plataforma iOS y Mac OS X**..

        ![Habilitar inscripción de iOS y Mac OS X](../media/30-day-trial-walkthrus/30day-cfg-pol-13-enbl-ios-plat.png)

    2.  Haga clic en **Descargar la solicitud de certificado de APNs**..

        ![Descargar el certificado de APNs](../media/30-day-trial-walkthrus/30day-cfg-pol-14-dwnld-cert-reqst.png)

    3.  Especifique un nombre de archivo y una ubicación para la solicitud de firma de certificado (CSR) y, después, haga clic en **Guardar**. Este archivo contiene la clave pública que corresponde a una clave privada que se incluye en la suscripción a Intune.

        ![Especificar una solicitud de firma de certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-15-cert-name-loc.png)

    4.  Haga clic en **Portal de certificados push de Apple** para abrir una nueva pestaña.

        ![Ir a la página de certificados de APNs](../media/30-day-trial-walkthrus/30day-cfg-pol-16-cert-portl-link.png)

    5.  Escriba el identificador y la contraseña de Apple y haga clic en **Iniciar sesión**. Este identificador puede ser que usa en el dispositivo iOS para obtener aplicaciones desde el App Store de iOS.

        ![Iniciar sesión en el portal de certificados push de Apple](../media/30-day-trial-walkthrus/30day-cfg-pol-17-id-passw-signin.png)

    6.  Haga clic en **Crear un certificado**..

        ![Crear un certificado de APNs](../media/30-day-trial-walkthrus/30day-cfg-pol-18-create-cert.png)

    7.  Lea las condiciones de uso de Apple, active la casilla y haga clic en **Aceptar**..

        ![Aceptar los términos](../media/30-day-trial-walkthrus/30day-cfg-pol-19-TOU.png)

    8.  Haga clic en **Examinar**..

        ![Vaya al lugar en el que guardó el certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-20-browse.png)

    9. Seleccione el archivo CSR que guardó anteriormente y haga clic en **Abrir**..

        ![Abrir el certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-21-CSRfile-open.png)

    10. Haga clic en el botón **Cargar**.

        ![Cargar el certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-22-upld-reqst.png)

    11. Cuando se le pida que descargue un archivo JSON, haga clic en **Guardar como**..

        ![Guarde el archivo JSON](../media/30-day-trial-walkthrus/30day-cfg-pol-23-json-saveas.png)

    12. Especifique una ubicación para el archivo JSON y haga clic en **Guardar**..

        ![Especificar dónde se quiere guardar el archivo JSON](../media/30-day-trial-walkthrus/30day-cfg-pol-24-json-save-loc.png)

        Si la página no se redirige automáticamente después de unos segundos, haga clic en **Cancelar**..

        ![Cancelar si una página no se redirige](../media/30-day-trial-walkthrus/30day-cfg-pol-25-json-pg-cancel.png)

    13. Para recuperar el archivo de certificado recién creado, haga clic en **Descargar**..

        ![Descargar el certificado](../media/30-day-trial-walkthrus/30day-cfg-pol-26-dwnld-retrv-cert.png)

    14. Cuando se le pida que descargue un archivo PEM, haga clic en **Guardar como**..

        ![Descargar el archivo PEM](../media/30-day-trial-walkthrus/30day-cfg-pol-27-pem-saveas.png)

    15. Especifique una ubicación para el archivo PEM y haga clic en **Guardar**..

        ![Guardar el archivo PEM](../media/30-day-trial-walkthrus/30day-cfg-pol-28-pem-save-loc.png)

    16. Vuelva a la pestaña Consola de administración de Intune y haga clic en **Cargar el certificado de APNs**..

        ![Cargar el certificado de APNs](../media/30-day-trial-walkthrus/30day-cfg-pol-29-upld-cert.png)

    17. Escriba su identificador de Apple y haga clic en **Examinar**..

        ![Escribir el identificador de Apple](../media/30-day-trial-walkthrus/30day-cfg-pol-30-app-id-browse.png)

    18. Seleccione el archivo PEM que acaba de guardar y haga clic en **Abrir**..

        ![Abrir el archivo PEM](../media/30-day-trial-walkthrus/30day-cfg-pol-31-sel-pem-open.png)

    19. Haga clic en **Cargar**..

        ![Cargar el archivo PEM](../media/30-day-trial-walkthrus/30day-cfg-pol-32-pem-upload.png)

        Su certificado de APNs ya está configurado.

        ![Configuración del certificado de APNs realizada correctamente](../media/30-day-trial-walkthrus/30day-cfg-pol-33-apns-confgd.png)

3.  Cree un grupo de usuarios de prueba al que aplicar la directiva:

    1.  En el panel de la izquierda, haga clic en **Grupos**..

        ![Abrir grupos](../media/30-day-trial-walkthrus/30day-cfg-pol-34-clk-groups.png)

    2.  En el extremo derecho, haga clic en **Crear grupo**..

        ![Crear un grupo](../media/30-day-trial-walkthrus/30day-cfg-pol-35-crt-group.png)

    3.  Proporcione un nombre de grupo, seleccione **Todos los usuarios** como el grupo primario y haga clic en **Siguiente**..

        ![Seleccionar todos los usuarios como grupo primario](../media/30-day-trial-walkthrus/30day-cfg-pol-36-name-group.png)

    4.  En el campo **Iniciar pertenencia a grupos con**, seleccione **Todos los usuarios del grupo primario** y haga clic en **Finalizar**..

        ![Iniciar pertenencia a grupos con el grupo primario](../media/30-day-trial-walkthrus/30day-cfg-pol-37-all-users-group.png)

4.  Cree una directiva de PIN de iOS y aplíquela al grupo de usuarios de prueba:

    1.  En el panel de la izquierda, haga clic en **Directiva**..

        ![Abrir el área de trabajo Directiva](../media/30-day-trial-walkthrus/30day-cfg-pol-38-clk-policy.png)

    2.  En el extremo derecho, haga clic en **Agregar directiva**..

        ![Agregar una directiva](../media/30-day-trial-walkthrus/30day-cfg-pol-39-add-policy.png)

    3.  Expanda el nodo iOS, seleccione la fila **Configuración general** y haga clic en **Crear directiva**..

        ![Crear una directiva de configuración general de iOS](../media/30-day-trial-walkthrus/30day-cfg-pol-40-gen_cfg_pol.png)

    4.  Escriba un nombre para la directiva, active la opción **Requerir una contraseña para desbloquear dispositivos móviles** y establezca **Longitud mínima de contraseña** en **4**..

        ![Configurar las opciones de contraseña](../media/30-day-trial-walkthrus/30day-cfg-pol-41-name-policy.png)

    5.  Haga clic en **Sí** para implementar la directiva.

        ![Implementar Directiva](../media/30-day-trial-walkthrus/30day-cfg-pol-42-yes-deploy-pol.png)

    6.  Haga clic en el grupo de usuarios creado anteriormente, en **Agregar** y en **Aceptar**..

        ![Seleccionar el grupo para la directiva](../media/30-day-trial-walkthrus/30day-cfg-pol-43-add-pol-to-grp.png)

        Ahora tiene una directiva de PIN de iOS que se aplicará al grupo de usuarios de prueba.

        ![Configuración de directiva completa](../media/30-day-trial-walkthrus/30day-cfg-pol-44-policy-applied.png)

## Validar la aplicación de la directiva en un dispositivo iOS.

1.  En un iPad, inicie el App Store de iOS, instale la aplicación **Portal de empresa de Microsoft Intune** gratuita y ábrala.

    ![Instalar el portal de empresa](../media/30-day-trial-walkthrus/30day-cfg-pol-45-cportal-installed.png)

2.  Escriba el nombre de su cuenta de usuario de prueba y la contraseña y pulse **Iniciar sesión**..

    ![Proporcionar las credenciales](../media/30-day-trial-walkthrus/30day-cfg-pol-46-cportal-signin.png)

3.  Pulse **Inscribir** para empezar a inscribir el dispositivo en Intune.

    ![Iniciar la inscripción](../media/30-day-trial-walkthrus/30day-cfg-pol-47-tap-enroll.jpg)

4.  En la pantalla **Instalar el perfil**, pulse **Instalar**..

    ![Instalar un perfil](../media/30-day-trial-walkthrus/30day-cfg-pol-48-profile-install-1.jpg)

5.  En el cuadro de diálogo **Instalar el perfil**, pulse **Instalar**..

    ![Continuar con la instalación del perfil](../media/30-day-trial-walkthrus/30day-cfg-pol-49-profile-install-2.jpg)

6.  En la pantalla **Advertencia**, pulse **Instalar**..

    ![Aceptar el mensaje de advertencia](../media/30-day-trial-walkthrus/30day-cfg-pol-50-warning-install-3.png)

7.  En el cuadro de diálogo **Administración remota**, pulse **Confianza**..

    ![Confiar en la administración remota](../media/30-day-trial-walkthrus/30day-cfg-pol-51-remt-mgmt-trust.jpg)

8.  Cuando finalice la instalación del perfil de administración, pulse **Listo**. La inscripción está completa.

    ![Inscripción completa](../media/30-day-trial-walkthrus/30day-cfg-pol-52-profile-done.jpg)

9. Cuando se complete la inscripción, pulse **Aceptar** y, después, cierre la aplicación Portal de empresa.

    ![Pulse Aceptar para cerrar la aplicación de portal de empresa.](../media/30-day-trial-walkthrus/30day-cfg-pol-53-devc-enrolled-ok.png)

10. Cuando se le pida configurar un código de acceso, pulse **Continuar**..

    ![Aceptar el símbolo del sistema para configurar el código de acceso](../media/30-day-trial-walkthrus/30day-cfg-pol-54-passcode-req-cont.png)

11. Escriba el código de acceso, pulse **Continuar**, vuelva a escribir el código de acceso y pulse **Guardar**..

    ![Proporcionar un código de acceso](../media/30-day-trial-walkthrus/30day-cfg-pol-55-passcode-enter.jpg)

12. Presione el botón de encendido para bloquear el iPad, deslice para desbloquearlo y observe que ahora debe introducir el código de acceso para desbloquearlo.

### Consulte también
[Guía de evaluación de Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md)


<!--HONumber=May16_HO1-->


