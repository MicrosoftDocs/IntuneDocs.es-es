---
title: "Inscripción de dispositivos iOS: Apple Configurator y el Asistente de configuración"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a usar Apple Configurator para inscribir dispositivos iOS corporativos con el Asistente de configuración."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: b2d2e4e0210526ff70b86526bd0b2e17bab0286b
ms.lasthandoff: 02/18/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-setup-assistant"></a>Inscripción de dispositivos iOS con Apple Configurator y el Asistente de configuración 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune permite la inscripción de dispositivos iOS corporativos con la herramienta [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) desde un equipo Mac. Este proceso restablece el dispositivo a la configuración de fábrica, lo prepara para ejecutar el Asistente de configuración e instala las directivas de la empresa para el nuevo usuario del dispositivo.

>[!NOTE]
>Este método de inscripción no se puede usar con el método del [administrador de inscripción de dispositivos](enroll-devices-using-device-enrollment-manager.md).

Apple Configurator puede restablecer un dispositivo iOS a la configuración de fábrica y prepararlo para que lo configure el nuevo usuario del dispositivo. Este método requiere conectar el dispositivo iOS a un equipo Mac a través de una conexión USB para configurar la inscripción corporativa. Además, se supone que está usando Apple Configurator 2.0. En la mayoría de los casos será necesario que la directiva aplicada al dispositivo iOS incluya afinidad de usuario para habilitar la aplicación Portal de empresa de Intune.

En [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (Selección del método para inscribir dispositivos iOS en Intune), se describen otros métodos de inscripción de dispositivos iOS).

## <a name="prerequisites"></a>Requisitos previos

Complete los siguientes requisitos previos antes de configurar la inscripción de dispositivos iOS:

- [Configurar dominios](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Establecer la entidad de MDM](set-mdm-authority.md)
- [Crear grupos](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar el Portal de empresa](/intune-azure/manage-apps/company-portal-app.md)
- Asignar licencias de usuario en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtener un certificado push MDM de Apple](get-an-apple-mdm-push-certificate.md)
- Asegurarse de tener acceso físico a dispositivos iOS
- Tener los números de serie de los dispositivos (consulte [Encontrar el número de serie de un producto Apple](https://support.apple.com//HT204308))
- Tener a mano cables de conexión USB
- Asegurarse de tener un equipo Mac que tenga instalado [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)
- [Agregar números de serie de Apple Configurator](add-apple-configurator-serial-numbers.md)


## <a name="create-an-apple-configurator-profile-for-devices"></a>Creación de un perfil de Apple Configurator para los dispositivos

Un perfil de inscripción de dispositivo define la configuración que se aplica a un grupo de dispositivos. Los siguientes pasos muestran cómo crear un perfil de inscripción de dispositivos para dispositivos iOS inscritos mediante Apple Configurator.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Inscripción de Apple**.

3. En **Administrar la configuración de inscripción de Apple Configurator**, seleccione **Perfiles AC**.

4. En la hoja **Perfiles de inscripción de Apple Configurator**, seleccione **Crear**.

5. En la hoja **Crear perfil de inscripción**, escriba un nombre y una descripción para el perfil.

6. En **Afinidad de usuario**, elija si los dispositivos con este perfil se inscribirán con o sin afinidad de usuario.

   - **Inscribir con afinidad de usuario**: el dispositivo se debe afiliar a un usuario durante la configuración inicial y luego se le puede permitir el acceso a los datos y al correo electrónico de la empresa. La afinidad de usuario debe configurarse para dispositivos administrados por DEP que pertenezcan a usuarios y necesiten usar el Portal de empresa para hacer uso de servicios, como instalar aplicaciones.

   - **Inscribir sin afinidad de usuario**: el dispositivo no está afiliado a ningún usuario. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de un usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.

7. Seleccione **Crear** para guardar el perfil.

## <a name="assign-serial-numbers-to-an-apple-configurator-profile"></a>Asignación de números de serie a un perfil de Apple Configurator

Después de crear perfiles de Apple Configurator, puede asignar números de serie de dispositivos a los perfiles. Para poder asignar números de serie, primero debe agregarlos a Intune siguiendo los pasos que se indican en [Add Apple Configurator serial numbers](add-apple-configurator-serial-numbers.md) (Agregar números de serie de Apple Configurator).

### <a name="assign-serial-numbers-to-apple-configurator-profiles"></a>Asignación de números de serie a perfiles de Apple Configurator

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja **Perfiles de inscripción de Apple Configurator**, seleccione el perfil al que quiere asignar números de serie.

3. En la hoja con nombre para el perfil, seleccione **Números de serie** > **Asignar**.

4. Seleccione los números de serie que quiere asignar al perfil y luego seleccione el botón **Asignar**.

## <a name="export-the-profile-to-ios-devices"></a>Exportación del perfil a dispositivos iOS

Después de crear el perfil y asignar números de serie, tendrá que exportar el perfil de Intune, bien como una dirección URL o como un archivo en el formato que se describe a continuación. A continuación, impórtelo manualmente en el programa Apple Configurator en un Mac, después de lo cual este programa lo implementará en los dispositivos.

### <a name="export-a-profile-using-setup-assistant-enrollment"></a>Exportación de un perfil mediante la inscripción con el Asistente de instalación

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja **Perfiles de inscripción de Apple Configurator**, elija el perfil que se exportará.

3. En la hoja del perfil, seleccione **Exportar perfil**.

4. Copie la dirección URL en [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12), con el dispositivo iOS conectado. Se cargará en Apple Configurator más tarde para definir el perfil de Intune utilizado por los dispositivos iOS.

  Para admitir Apple Configurator 2, se debe editar URL de perfil 2.0. Para ello, reemplace este código:
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    por este código:

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   En el procedimiento siguiente, esta dirección URL de perfil se carga en el servicio DEP de Apple mediante la herramienta Apple Configurator para definir el perfil de Intune utilizado por dispositivos iOS.

5. Cargue esta URL del perfil en el servicio DEP de Apple mediante la herramienta Apple Configurator para definir el perfil de Intune utilizado por dispositivos iOS.


    1.  En un equipo Mac, abra **Apple Configurator 2**. En la barra de menús, elija **Apple Configurator 2** y, después, elija **Preferencias**.

         > [!WARNING]
         > Los dispositivos se restablecerán en la configuración de fábrica durante el proceso de inscripción. Como procedimiento recomendado, restablezca el dispositivo y enciéndalo. Los dispositivos deberían estar en la pantalla **Hola** cuando conecte el dispositivo.

    2. En el panel de **preferencias**, seleccione **Servidores** y elija el símbolo más (+) para iniciar el asistente del servidor MDM. Seleccione **Siguiente**.

    3. Escriba el **nombre** y la **dirección URL de inscripción** para el servidor MDM del paso 6 en el Asistente de configuración para la inscripción de dispositivos de iOS con Microsoft Intune. Para la dirección URL de inscripción, escriba la dirección URL del perfil de inscripción exportada desde Intune. Seleccione **Siguiente**.  

       Puede omitir de forma segura una advertencia que indica "no se comprueba la dirección URL del servidor". Para continuar, elija **Siguiente** hasta que finalice el asistente.

    4.  Conecte los dispositivos móviles iOS al equipo Mac con un adaptador USB.

        > [!WARNING]
        > Los dispositivos se restablecerán en la configuración de fábrica durante el proceso de inscripción. Como procedimiento recomendado, restablezca el dispositivo y enciéndalo. Los dispositivos deberían estar en la pantalla **Hola** cuando inicia el Asistente de configuración.

    5.  Elija **Preparar**. En el panel **Prepare iOS Device** (Preparar el dispositivo iOS), seleccione **Manual** y luego elija **Siguiente**.

    6. En el panel **Enroll in MDM Server** (Inscribir en servidor MDM), seleccione el nuevo servidor y elija **Siguiente**.

    7. En el panel **Supervise Devices** (Supervisar dispositivos), seleccione el nivel de supervisión y luego elija **Siguiente**.

    8. En el panel **Create an Organization** (Crear una organización), seleccione la **organización** o cree una nueva y luego elija **Siguiente**.

    9. En el panel **Configure iOS Setup Assistant** (Configurar el Asistente de configuración de iOS), elija los pasos que se presentan al usuario y, después, elija **Preparar**. Si se le solicita, autentíquese para actualizar la configuración de confianza.  

    10. Cuando el dispositivo iOS termine la preparación, desconecte el cable USB.  

6.  **Distribuir los dispositivos**.
    Los dispositivos ya están listos para la inscripción corporativa. Apague los dispositivos y distribúyalos a los usuarios. Cuando los usuarios enciendan sus dispositivos, se iniciará el Asistente de configuración.

## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Cómo los usuarios instalan y usan el Portal de empresa en sus dispositivos

Los dispositivos configurados con afinidad de usuario pueden instalar y ejecutar la aplicación del portal de empresa para descargar aplicaciones y administrar dispositivos. Después de que los usuarios reciben sus dispositivos, deben realizar los pasos adicionales que se describen a continuación para completar el Asistente de configuración e instalar la aplicación del Portal de empresa.

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Inscripción de dispositivos iOS de empresa con afinidad de usuario

1. Cuando los usuarios encienden su dispositivo, se les pide que completen el Asistente de configuración. Durante la instalación, se pide a los usuarios sus credenciales. Deben usar las credenciales (es decir, el nombre único personal o UPN) que están asociadas con su suscripción en Intune.

2. Durante la instalación, se pide a los usuarios un id. de Apple. Deben proporcionar un identificador de Apple para que el dispositivo instale el portal de empresa. También pueden proporcionar el identificador desde el menú de configuración de iOS una vez finalizada la instalación.

3. Tras completar la instalación, el dispositivo iOS debe instalar la aplicación del portal de empresa desde la Tienda de aplicaciones.

4. El usuario puede ahora iniciar sesión en el portal de empresa con el UPN que usó al configurar el dispositivo.

5. Después de iniciar sesión, se pide a los usuarios que inscriban su dispositivo. El primer paso es identificar su dispositivo. La aplicación presenta una lista de dispositivos iOS que ya se han inscrito en la empresa y que se han asignado a la cuenta de Intune del usuario. Debe elegir el dispositivo que corresponda. Si este dispositivo no está ya inscrito en la empresa, se debe elegir la opción para nuevo dispositivo para continuar con el flujo de inscripción estándar.

6. En la siguiente pantalla, los usuarios deben confirmar el número de serie del nuevo dispositivo. Los usuarios pueden pulsar el vínculo para confirmar el número de serie para iniciar la aplicación de configuración y así comprobar el número de serie. Los usuarios deben especificar los últimos cuatro caracteres del número de serie en la aplicación Portal de empresa.

    Este paso comprueba que el dispositivo es el dispositivo de empresa inscrito en Intune. Si el número de serie del dispositivo no coincide, significa que se ha seleccionado el dispositivo equivocado. El usuario debe volver a la pantalla anterior y seleccionar un dispositivo diferente.

7. Después de comprobar el número de serie, la aplicación del portal de empresa redirige al sitio web del portal de empresa para finalizar la inscripción. Luego, el sitio web pide a los usuarios que vuelvan a la aplicación.

La inscripción está ahora completa y los usuarios pueden usar este dispositivo con el conjunto completo de funcionalidades.

