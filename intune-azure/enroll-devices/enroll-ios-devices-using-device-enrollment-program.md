---
title: "Inscripción de dispositivos iOS: Programa de inscripción de dispositivos"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a inscribir dispositivos iOS corporativos mediante el Programa de inscripción de dispositivos."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 53f1c688aad2f810d8a887435dd8d122d4f471ae
ms.openlocfilehash: d8fa3a19915076f1a603449dd426172fbc5a613a
ms.lasthandoff: 04/27/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>Inscripción de dispositivos iOS mediante el Programa de inscripción de dispositivos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

En este tema se ayuda a los administradores de TI a inscribir dispositivos iOS propiedad de la empresa adquiridos mediante el [Programa de inscripción de dispositivos (DEP) de Apple](https://deploy.apple.com). Microsoft Intune puede implementar un perfil de inscripción que inscribe el DEP de manera inalámbrica para que el administrador nunca tenga que tocar todos los dispositivos administrados. Un perfil de DEP contiene la configuración de administración que quiere aplicar a los dispositivos durante la inscripción. El paquete de inscripción puede incluir opciones del Asistente de configuración del dispositivo.

>[!NOTE]
>La inscripción de DEP no se puede usar con el [administrador de inscripción de dispositivos](enroll-devices-using-device-enrollment-manager.md).
>Además, si los usuarios inscriben sus dispositivos iOS con la aplicación Portal de empresa y los números de serie de dichos dispositivos se importan luego y se les asigna un perfil de DEP, se anulará la inscripción del dispositivo en Intune.

**Pasos para la inscripción de DEP**
1. [Obtener un token de DEP de Apple](#get-the-apple-dep-certificate)
2. [Crear un perfil de DEP](#create-anapple-dep-profile)
3. [Asignar números de serie de DEP de Apple al servidor de Intune](#assign-apple-dep-serial-numbers-to-your-mdm-server)
4. [Sincronizar dispositivos administrados por DEP](#synchronize-dep-managed-devices)
5. [Asignar el perfil de DEP a los dispositivos](#assign-a-dep-profile-to-devices)
6. [Distribuir los dispositivos a los usuarios](#distribute-devices-to-users)

## <a name="get-the-apple-dep-certificate"></a>Obtener el certificado de DEP de Apple
Antes de poder inscribir dispositivos iOS propiedad de la empresa con el Programa de inscripción de dispositivos (DEP) de Apple, necesita un certificado de DEP (.p7m) de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos que participan en DEP. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles.

Para administrar dispositivos iOS corporativos con el DEP, la organización debe unirse a DEP de Apple y obtener los dispositivos a través de ese programa. Puede consultar los detalles de este proceso en: https://deploy.apple.com. Las ventajas del programa incluyen dispositivos configurados con manos libres sin necesidad de usar un cable USB para conectar cada dispositivo a un equipo.

> [!NOTE]
> Si se ha migrado el inquilino de Intune de la consola clásica de Intune a Azure Portal y se ha eliminado un token de DEP de Apple de la consola de administración de Intune durante el período de migración, es posible que el token de DEP se haya restaurado a su cuenta de Intune. Puede volver a eliminar el token de DEP desde Azure Portal.

**Paso 1. Descargue un certificado de clave pública de Intune necesario para crear un token de DEP de Apple.**<br>
1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**. En la hoja de Intune, elija **Inscripción de dispositivos** > **Token de DEP de Apple**.
2. Seleccione **Download your public key** (Descargar la clave pública) para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.

**Paso 2. Descargue un token de DEP de Apple desde el sitio web de Apple adecuado.**<br>
Seleccione [Crear token de DEP mediante los Programas de implementación de Apple](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su id. de Apple de empresa. Puede usar este id. de Apple para renovar el token de DEP.

   1.  En el [Portal del Programa de inscripción de dispositivos](https://deploy.apple.com) de Apple, vaya a **Device Enrollment Program (Programa de inscripción de dispositivos)** &gt; **Manage Servers (Administrar servidores)** y, después, elija **Add MDM Server** (Agregar servidor MDM).
   2.  Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.
   3.  Se abre el cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;**. Elija **Elegir archivo...** para cargar el archivo .pem y, después, elija **Siguiente**.
   4.  El cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;** muestra un vínculo **Your Server Token (Su token de servidor)**. Descargue el archivo de token de servidor (.p7m) en el equipo y, después, elija **Listo**.

**Paso 3. Escriba el id. de Apple usado para crear el token de DEP de Apple. Este id. se puede usar para renovar el token de DEP de Apple.**

**Paso 4. Vaya a su token de DEP de Apple para cargarlo. Intune se sincronizará automáticamente con su cuenta de DEP.**<br>
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.

## <a name="create-an-apple-dep-profile"></a>Crear un perfil de DEP de Apple

Un perfil de inscripción de dispositivo define la configuración que se aplica a un grupo de dispositivos. Los siguientes pasos muestran cómo crear un perfil de inscripción de dispositivos para dispositivos iOS inscritos mediante DEP.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.
2. En la hoja de Intune, elija **Inscripción de dispositivos** y luego elija **Apple Enrollment** (Inscripción de Apple).
3. En **Administrar la configuración del Programa de inscripción de dispositivos (DEP) de Apple**, seleccione **Perfiles DEP**.
4. En la hoja **Apple DEP Profiles** (Perfiles DEP de Apple), seleccione **Crear**.
5. En la hoja **Crear perfil de inscripción**, escriba un nombre y una descripción para el perfil.
6. En **Afinidad de usuario**, elija si los dispositivos con este perfil se inscribirán con o sin afinidad de usuario.

 - **Inscribir con afinidad de usuario**: el dispositivo se debe afiliar a un usuario durante la configuración inicial y luego se le puede permitir el acceso a los datos y al correo electrónico de la empresa. Elija la afinidad de usuario para dispositivos administrados por DEP que pertenezcan a usuarios y necesiten usar el Portal de empresa para hacer uso de servicios, como instalar aplicaciones. Tenga en cuenta que la autenticación multifactor (MFA) no funciona durante la inscripción en dispositivos DEP con afinidad de usuario. Después de la inscripción, MFA funciona según lo previsto en estos dispositivos. No se puede pedir a los nuevos usuarios que cambien la contraseña al iniciar sesión por primera vez durante la inscripción en dispositivos DEP. Además, no se puede pedir a los usuarios cuyas contraseñas hayan expirado que las restablezcan durante la inscripción de DEP y tienen que hacerlo desde otro dispositivo.

    >[!NOTE]
    >DEP con afinidad de usuario precisa que el [punto de conexión WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/en-us/library/adfs2-help-endpoints) esté habilitado para solicitar el token de usuario. [Obtenga más información sobre WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

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
Deben asignarse números de serie de dispositivos al servidor de MDM de Intune en el portal web de DEP de Apple para permitir a Intune que administre esos dispositivos.

1. Vaya al [portal del Programa de inscripción de dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sesión con su identificador de Apple de empresa.

2. Vaya a **Programa de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**.

3. Especifique cómo va a **elegir los dispositivos** y luego proporcione información del dispositivo y especifique los detalles de cada dispositivo, como **Número de serie**y **Número de pedido**, o seleccione **Cargar archivo CSV**.

4. Elija **Assign to Server** (Asignar al servidor), elija el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y después elija **Aceptar**.

## <a name="synchronize-dep-managed-devices"></a>Sincronizar dispositivos administrados por DEP
Ahora que se ha concedido permiso a Intune para administrar los dispositivos de DEP, puede sincronizar Intune con el servicio de DEP para ver los dispositivos administrados en el portal de Intune.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune de Azure Portal, elija **Inscripción de dispositivos** y luego elija **Apple Enrollment** (Inscripción de Apple).

3. En **Administrar la configuración del Programa de inscripción de dispositivos (DEP) de Apple**, seleccione **Números de serie de DEP**.

4. En la hoja **Números de serie de DEP de Apple**, seleccione **Sincronizar**.

5. En la hoja **Sincronizar**, seleccione **Solicitar sincronización**. La barra de progreso muestra la cantidad de tiempo que debe esperar antes de solicitar de nuevo la sincronización.

    Para cumplir con las condiciones de Apple relativas a un tráfico DEP aceptable, Intune impone las restricciones siguientes:
     -    Una sincronización completa de DEP no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune actualiza todos los números de serie que Apple ha asignado a Intune, independientemente de si el número de serie se ha sincronizado previamente o no. Si se intenta efectuar una sincronización completa sin que hayan pasado siete días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.
     -    Las solicitudes de sincronización tardan 10 minutos en finalizar. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón **Sincronización** está deshabilitado.

>[!NOTE]
>También puede asignar números de serie de DEP a perfiles en la hoja **Números de serie de DEP de Apple** hoja.

## <a name="assign-a-dep-profile-to-devices"></a>Asignación del perfil de DEP a los dispositivos
Los dispositivos de DEP administrados por Intune deben tener un perfil de DEP asignado antes de la inscripción.

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja Intune de Azure Portal, elija **Inscripción de dispositivos** > **Apple Enrollment** (Inscripción de Apple) y luego seleccione **DEP profiles** (Perfiles de DEP).

3. En la lista de **perfiles de inscripción de DEP de Apple**, seleccione el perfil que desea asignar a los dispositivos y, a continuación, elija **Device Assignments** (Asignaciones de dispositivos).

4. Seleccione **Asignar** y, a continuación, seleccione los dispositivos de DEP que desea asignar a este perfil. Puede filtrar para ver los dispositivos de DEP disponibles:
  - **sin asignar**
  - **cualquiera**
  - **&lt;Nombre de perfil de DEP&gt;**

  ![Captura de pantalla del botón Asignar para la asignación de un perfil de DEP en el portal de Intune](media/dep-profile-assignment.png)

5. Seleccione los dispositivos que desea asignar. La casilla que se encuentra encima de la columna seleccionará hasta 1000 dispositivos de los que figuran en la lista; a continuación, haga clic en **Asignar**. Para inscribir más de 1000 dispositivos, repita los pasos de la asignación hasta que todos los dispositivos tengan un perfil de DEP asignado.

## <a name="distribute-devices-to-users"></a>Distribuir los dispositivos a los usuarios

Ahora puede distribuir dispositivos corporativos a los usuarios. Los dispositivos de DEP de iOS quedan inscritos para su administración mediante Intune al activarlos. Si el dispositivo se ha activado y está en uso, el perfil no se aplicará hasta que el dispositivo se restablezca a sus valores de fábrica.

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Cómo los usuarios instalan y usan el Portal de empresa en sus dispositivos

Los dispositivos configurados con afinidad de usuario pueden instalar y ejecutar la aplicación del portal de empresa para descargar aplicaciones y administrar dispositivos. Después de que los usuarios reciben sus dispositivos, deben realizar los pasos adicionales que se describen a continuación para completar el Asistente de configuración e instalar la aplicación del Portal de empresa.

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Inscripción de dispositivos iOS de empresa con afinidad de usuario

1. Cuando los usuarios encienden su dispositivo, se les pide que completen el Asistente de configuración. Durante la instalación, se pide a los usuarios sus credenciales. Deben usar las credenciales (es decir, el nombre único personal o UPN) que están asociadas con su suscripción en Intune.

2. Durante la instalación, se pide a los usuarios un id. de Apple. Deben proporcionar un identificador de Apple para que el dispositivo instale el portal de empresa. También pueden proporcionar el identificador de Apple desde el menú de configuración de iOS una vez finalizada la instalación.

3. Tras completar la instalación, los usuarios deben instalar la aplicación Portal de empresa desde App Store.

4. Ahora los usuarios pueden iniciar sesión en el Portal de empresa con el UPN que usaron al configurar el dispositivo.

5. Después de iniciar sesión, se pide a los usuarios que inscriban su dispositivo. El primer paso es identificar su dispositivo. La aplicación presenta una lista de dispositivos iOS que ya se han inscrito en la empresa y que se han asignado a la cuenta de Intune del usuario. Debe elegir el dispositivo que corresponda. Si este dispositivo no está ya inscrito en la empresa, se debe elegir la opción para nuevo dispositivo para continuar con el flujo de inscripción estándar.

6. En la siguiente pantalla, los usuarios confirman el número de serie del nuevo dispositivo. Para ello, los usuarios seleccionan un vínculo que aparece. El vínculo inicia la aplicación de configuración, que permite a los usuarios comprobar su número de serie. Los usuarios deben especificar los últimos cuatro caracteres del número de serie en la aplicación Portal de empresa.

   Este paso comprueba que el dispositivo es el dispositivo de empresa inscrito en Intune. Si el número de serie del dispositivo no coincide, significa que el usuario ha seleccionado el dispositivo incorrecto. El usuario debe volver a la pantalla anterior y seleccionar un dispositivo diferente.

7. Después de comprobar el número de serie, la aplicación del portal de empresa redirige al sitio web del portal de empresa para finalizar la inscripción. Luego, el sitio web pide a los usuarios que vuelvan a la aplicación.

La inscripción está ahora completa y los usuarios pueden usar este dispositivo con el conjunto completo de funcionalidades.

