---
title: "Inscripción de dispositivos iOS: Programa de inscripción de dispositivos | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda a inscribir dispositivos iOS corporativos mediante el Programa de inscripción de dispositivos."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: da6d377c94ce5db7bbfa1cb3fc165581d649a1fb
ms.lasthandoff: 02/15/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>Inscripción de dispositivos iOS mediante el Programa de inscripción de dispositivos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune puede implementar un perfil de inscripción que inscriba dispositivos iOS que se han adquirido a través del Programa de inscripción de dispositivos (DEP) de Apple "de forma inalámbrica". Un perfil contiene la configuración de administración que quiere aplicar a los dispositivos. El paquete de inscripción puede incluir opciones del Asistente de configuración del dispositivo. Los usuarios no pueden anular la inscripción de dispositivos inscritos a través de DEP.

>[!NOTE]
>Este método de inscripción no se puede usar con el método del [administrador de inscripción de dispositivos](enroll-devices-using-device-enrollment-manager.md).

Para administrar dispositivos iOS corporativos con el Programa de inscripción de dispositivos (DEP) de Apple, la organización debe unirse a DEP de Apple y obtener dispositivos a través de ese programa. Puede consultar los detalles de este proceso en:  [https://deploy.apple.com](https://deploy.apple.com). Las ventajas del programa incluyen dispositivos configurados con manos libres sin necesidad de usar un cable USB para conectar cada dispositivo a un equipo.

Para poder inscribir dispositivos iOS corporativos con DEP, necesita un [token de DEP](get-apple-dep-token.md) de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos que participan en DEP. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles.

En [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (Selección del método para inscribir dispositivos iOS en Intune), se describen otros métodos de inscripción de dispositivos iOS).

## <a name="prerequisites"></a>Requisitos previos

Complete los siguientes requisitos previos antes de configurar la inscripción de dispositivos iOS:

- [Configurar dominios](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Establecer la entidad de MDM](set-mdm-authority.md)
- [Crear grupos](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- Asignar licencias de usuario en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtener un certificado push MDM de Apple](get-an-apple-mdm-push-certificate.md)
- [Obtener un token de DEP de Apple](get-apple-dep-token.md)

## <a name="create-an-apple-dep-profile-for-devices"></a>Creación de un perfil de DEP de Apple para dispositivos

Un perfil de inscripción de dispositivo define la configuración que se aplica a un grupo de dispositivos. Los siguientes pasos muestran cómo crear un perfil de inscripción de dispositivos para dispositivos iOS inscritos mediante DEP.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Inscripción de Apple**.

3. En **Administrar la configuración del Programa de inscripción de dispositivos (DEP) de Apple**, seleccione **Perfiles DEP**.

4. En la hoja **Apple DEP Profiles** (Perfiles DEP de Apple), seleccione **Crear**.

5. En la hoja **Crear perfil de inscripción**, escriba un nombre y una descripción para el perfil.

6. En **Afinidad de usuario**, elija si los dispositivos con este perfil se inscribirán con o sin afinidad de usuario.

 - **Inscribir con afinidad de usuario**: el dispositivo se debe afiliar a un usuario durante la configuración inicial y luego se le puede permitir el acceso a los datos y al correo electrónico de la empresa. Elija la afinidad de usuario para dispositivos administrados por DEP que pertenezcan a usuarios y necesiten usar el Portal de empresa para hacer uso de servicios, como instalar aplicaciones. Tenga en cuenta que la autenticación multifactor (MFA) no funciona durante la inscripción en dispositivos DEP con afinidad de usuario. Después de la inscripción, MFA funciona según lo previsto en estos dispositivos.

    >[!NOTE]
    >DEP con la afinidad de usuario requiere un punto de conexión de WS-Trust 1.3 nombreDeUsuario/Mixto para que se habilite para solicitar el token de usuario.

 - **Inscribir sin afinidad de usuario**: el dispositivo no está afiliado a ningún usuario. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de un usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.

7. Seleccione **Configuración de administración de dispositivos**, configure las siguientes opciones de perfil y luego seleccione **Guardar**:

    - **Supervisado**: un modo de administración que permite más opciones de administración y deshabilita el bloqueo de activación de forma predeterminada. Si deja en blanco la casilla, tendrá funcionalidades de administración limitadas.

    - **Inscripción bloqueada** (requiere el modo de administración Supervisado): deshabilita la configuración de iOS que podría permitir la eliminación del perfil de administración. Si deja en blanco la casilla, permite que se quite el perfil de administración en el menú Configuración. Este elemento se establece durante la activación y no se puede cambiar sin un restablecimiento de fábrica.

    - **Permitir emparejamiento**: especifica si se pueden sincronizar dispositivos iOS con equipos. Si elige **Permitir Apple Configurator mediante certificado**, debe seleccionar un certificado en **Certificado de Apple Configurator**.

    - **Certificados de Apple Configurator**: si eligió **Permitir Apple Configurator mediante certificado** en **Permitir emparejamiento**, seleccione un certificado de Apple Configurator para importar.

8. Seleccione **Valores del Asistente de configuración**, configure las siguientes opciones de perfil y, a continuación, seleccione **Guardar**:

    - **Department Name** (Nombre de departamento): aparece cuando los usuarios pulsan **About Configuration** (Acerca de la configuración) durante la activación.

    - **Teléfono del departamento**: aparece cuando el usuario hace clic en el botón Necesito ayuda durante la activación.
    - **Opciones del Asistente para la configuración**: estas opciones opcionales se pueden configurar más adelante en el menú **Configuración** de iOS.
        - **Código de acceso**: solicita el código de acceso durante la activación. Solicite siempre un código de acceso, a menos que el dispositivo esté protegido o tenga el acceso controlado de otra manera (es decir, modo de quiosco que restringe el dispositivo a una aplicación).
        - **Servicios de ubicación**: si está habilitado, el Ayudante para la configuración solicitará el servicio durante la activación.
        - **Restauración**: si está habilitado, el Ayudante para la configuración solicitará una copia de seguridad de iCloud durante la activación.
        - **ID de Apple**: si está habilitado, iOS solicitará a los usuarios un identificador de Apple cuando Intune intente instalar una aplicación sin un identificador. Se requiere un identificador de Apple para descargar aplicaciones del App Store de iOS, incluidas las que instala Intune.
        - **Términos y condiciones**: si está habilitado, el Asistente para la configuración solicita a los usuarios que acepten los términos y condiciones de Apple durante la activación.
        - **Touch ID**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Apple Pay**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Zoom**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Siri**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Datos de diagnóstico**: si esta opción está habilitada, el Ayudante de configuración solicitará este servicio durante la activación.

9. Para guardar la configuración del perfil, seleccione **Crear** en la hoja **Crear perfil de inscripción**.

## <a name="assign-apple-dep-serial-numbers-to-your-mdm-server"></a>Asignación de números de serie de DEP de Apple al servidor de MDM

1. Vaya al [portal del Programa de inscripción de dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su identificador de Apple de empresa. 

2. Vaya a **Programa de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**. 

3. Especifique cómo va a **elegir los dispositivos** y luego proporcione información del dispositivo y especifique los detalles de cada dispositivo, como **Número de serie**y **Número de pedido**, o seleccione **Cargar archivo CSV**. 

4. Elija **Assign to Server** (Asignar al servidor), elija el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y después elija **Aceptar**.

## <a name="synchronize-dep-managed-devices"></a>Sincronizar los dispositivos administrados por DEP

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune del portal de Azure, elija **Inscribir dispositivos** y luego elija **Inscripción de Apple**.

3. En **Administrar la configuración del Programa de inscripción de dispositivos (DEP) de Apple**, seleccione **Números de serie de DEP**.

4. En la hoja **Números de serie de DEP de Apple**, seleccione **Sincronizar**.

5. En la hoja **Sincronizar**, seleccione **Solicitar sincronización**. La barra de progreso muestra la cantidad de tiempo que debe esperar antes de solicitar de nuevo la sincronización.

    Para cumplir con las condiciones de Apple relativas a un tráfico DEP aceptable, Intune impone las restricciones siguientes:
     -    Una sincronización completa de DEP no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune actualiza todos los números de serie que Apple ha asignado a Intune, independientemente de si el número de serie se ha sincronizado previamente o no. Si se intenta efectuar una sincronización completa sin que hayan pasado siete días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.
     -    Las solicitudes de sincronización tardan 10 minutos en finalizar. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón **Sincronización** está deshabilitado.

>[!NOTE]
>También puede asignar números de serie de DEP a perfiles en la hoja **Números de serie de DEP de Apple** hoja.

## <a name="distribute-devices-to-users"></a>Distribuir los dispositivos a los usuarios

Ahora puede distribuir dispositivos corporativos a los usuarios. Los dispositivos iOS quedan inscritos para su administración mediante Intune al activarlos.


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Cómo los usuarios instalan y usan el Portal de empresa en sus dispositivos

Los dispositivos configurados con afinidad de usuario pueden instalar y ejecutar la aplicación del portal de empresa para descargar aplicaciones y administrar dispositivos. Después de que los usuarios reciben sus dispositivos, deben realizar los pasos adicionales que se describen a continuación para completar el Asistente de configuración e instalar la aplicación del Portal de empresa.

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Inscripción de dispositivos iOS de empresa con afinidad de usuario 

1. Cuando los usuarios encienden su dispositivo, se les pide que completen el Asistente de configuración. Durante la instalación, se pide a los usuarios sus credenciales. Deben usar las credenciales (es decir, el nombre único personal o UPN) que están asociadas con su suscripción en Intune.

2. Durante la instalación, se pide a los usuarios un id. de Apple. Deben proporcionar un identificador de Apple para que el dispositivo instale el portal de empresa. También pueden proporcionar el identificador desde el menú de configuración de iOS una vez finalizada la instalación.

3. Tras completar la instalación, los usuarios deben instalar la aplicación Portal de empresa desde App Store.

4. Ahora los usuarios pueden iniciar sesión en el Portal de empresa con el UPN que usaron al configurar el dispositivo.

5. Después de iniciar sesión, se pide a los usuarios que inscriban su dispositivo. El primer paso es identificar su dispositivo. La aplicación presenta una lista de dispositivos iOS que ya se han inscrito en la empresa y que se han asignado a la cuenta de Intune del usuario. Debe elegir el dispositivo que corresponda. Si este dispositivo no está ya inscrito en la empresa, se debe elegir la opción para nuevo dispositivo para continuar con el flujo de inscripción estándar.

6. En la siguiente pantalla, los usuarios confirman el número de serie del nuevo dispositivo. Para ello, los usuarios seleccionan un vínculo que aparece. El vínculo inicia la aplicación de configuración, que permite a los usuarios comprobar su número de serie. Los usuarios deben especificar los últimos cuatro caracteres del número de serie en la aplicación Portal de empresa.

   Este paso comprueba que el dispositivo es el dispositivo de empresa inscrito en Intune. Si el número de serie del dispositivo no coincide, significa que el usuario ha seleccionado el dispositivo incorrecto. El usuario debe volver a la pantalla anterior y seleccionar un dispositivo diferente.

7. Después de comprobar el número de serie, la aplicación del portal de empresa redirige al sitio web del portal de empresa para finalizar la inscripción. Luego, el sitio web pide a los usuarios que vuelvan a la aplicación.

La inscripción está ahora completa y los usuarios pueden usar este dispositivo con el conjunto completo de funcionalidades.

