---
title: "Inscripción de dispositivos iOS: Programa de inscripción de dispositivos"
titlesuffix: Azure portal
description: "Aprenda a inscribir dispositivos iOS corporativos mediante el Programa de inscripción de dispositivos."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 311bb42f2ef9fbf689e32eacca7420c8189251bf
ms.sourcegitcommit: 001577b700f634da2fec0b44af2a378150d1f7ac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2017
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Inscribir dispositivos iOS automáticamente con el Programa de inscripción de dispositivos de Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tema le ayuda a habilitar la inscripción de dispositivos iOS adquiridos mediante el [Programa de inscripción de dispositivos (DEP)](https://deploy.apple.com) de Apple. Puede habilitar la inscripción de DEP para muchos dispositivos sin ni siquiera tocarlos. Puede proporcionar dispositivos como iPhone e iPad directamente a los usuarios. Cuando el usuario activa el dispositivo, se ejecuta el Asistente para la instalación con opciones preconfiguradas y el dispositivo se inscribe en la administración.

Para habilitar la inscripción de DEP, use los portales de DEP de Apple y de Intune. Se necesita una lista de números de serie o un número de pedido de compra, de manera que pueda asignar dispositivos a Intune para la administración. Puede crear perfiles de inscripción de DEP que contengan opciones que se apliquen a los dispositivos durante la inscripción.

Además, la inscripción de DEP no funciona con el [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

## <a name="what-is-supervised-mode"></a>¿Qué es el modo de supervisión?
Apple introdujo el modo de supervisión en iOS 5. Los dispositivos iOS que estén en modo de supervisión se pueden administrar con más controles. Por lo tanto, resulta especialmente útil para los dispositivos corporativos. Intune admite la configuración de dispositivos en el modo de supervisión como parte del Programa de inscripción de dispositivos (DEP) de Apple. 

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Requisitos previos
- Dispositivos adquiridos en el [Programa de inscripción de dispositivos de Apple](http://deploy.apple.com)
- [Entidad de MDM](mdm-authority-set.md)
- [Certificado push MDM de Apple](apple-mdm-push-certificate-get.md)

> [!NOTE]
> Multi-Factor Authentication (MFA) no funciona durante la configuración de la inscripción de DEP para la afinidad de usuario. Después de la inscripción, MFA funciona según lo previsto en los dispositivos. Los dispositivos no pueden pedir a los usuarios que cambien su contraseña cuando inician sesión por primera vez. Además, no se puede pedir a los usuarios cuyas contraseñas hayan expirado que las restablezcan durante la inscripción. Los usuarios deben usar un dispositivo diferente para restablecer la contraseña.

## <a name="get-the-apple-dep-token"></a>Obtención del token de DEP de Apple

Antes de poder inscribir dispositivos iOS con DEP, necesita un archivo de token de DEP (.p7m) de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos de DEP. También permite a Intune cargar perfiles de inscripción en Apple y asignar dispositivos a esos perfiles.

Use el portal de DEP de Apple para crear un token de DEP. También puede usar el portal de DEP para asignar dispositivos a Intune para la administración.

> [!NOTE]
> Si elimina el token desde el portal clásico de Intune antes de realizar la migración a Azure, Intune podría restaurar un token de DEP de Apple eliminado. Puede volver a eliminar el token de DEP desde Azure Portal. Puede volver a eliminar el token de DEP desde Azure Portal.

**Paso 1. Descargue un certificado de clave pública de Intune necesario para crear un token de DEP de Apple.**<br>

1. En Intune en Azure Portal, pulse **Inscripción de dispositivos** > **Inscripción de Apple** > **Token del Programa de inscripción**.

  ![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo Certificados de Apple.](./media/enrollment-program-token-add.png)

2. Seleccione **Descargar la clave pública** para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.

  ![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo de Certificados de Apple para descargar la clave pública.](./media/enrollment-program-token-download.png)

**Paso 2. Cree y descargue un token de DEP de Apple.**<br>
1. Seleccione **Create a token via Apple's Device Enrollment Program** (Crear un token mediante el Programa de inscripción de dispositivos de Apple) para abrir el portal de Programas de implementación de Apple e iniciar sesión con su id. de Apple de la empresa. Puede usar este id. de Apple para renovar el token de DEP.
2.  En el [portal Programas de implementación](https://deploy.apple.com) de Apple, seleccione **Introducción** para **Programa de inscripción de dispositivos**.

3. En la página **Administrar servidores**, pulse **Add MDM Server** (Agregar servidor de MDM).
4. Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

   ![Captura de pantalla de la adición de un nombre de servidor de MDM para DEP y, después, hacer clic en Siguiente.](./media/enrollment-program-token-add-server.png)

5. Se abre el cuadro de diálogo **Agregar&lt;Nombre del servidor&gt;**, indicando **Cargar la clave pública**. Elija **Elegir archivo...** para cargar el archivo .pem y, después, elija **Siguiente**.


7. Vaya a **Programa de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**.
8. En **Elegir dispositivos por**, especifique cómo se identifican los dispositivos:
    - **Número de serie**
    - **Número de pedido**
    - **Cargar archivo CSV**.

   ![Captura de pantalla sobre cómo especificar Elegir dispositivos por número de serie, estableciendo Elegir acción como Asignar al servidor y seleccionando el nombre de servidor.](./media/enrollment-program-token-specify-serial.png)

9. En **Elegir acción**, pulse **Asignar al servidor**, seleccione el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y pulse **Aceptar**. El portal de Apple asigna los dispositivos especificados al servidor de Intune para la administración y, después, muestra **Asignación completa**.

   En el portal de Apple, vaya a **Programas de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **View Assignment History** (Ver historial de asignaciones) para ver una lista de dispositivos y su asignación de servidor MDM.

**Paso 3. Escriba el identificador de Apple usado para crear el token del programa de inscripción.**<br>En Intune en Azure Portal, proporcione el id. de Apple para futuras referencias. Use este id. para renovar el token del Programa de inscripción en el futuro para evitar la necesidad de volver a inscribir todos los dispositivos.

![Captura de pantalla sobre cómo especificar el identificador de Apple que se ha usado para crear y buscar el token del Programa de inscripción.](./media/enrollment-program-token-apple-id.png)

**Paso 4. Buscar el token del programa de inscripción que se va a cargar.**<br>
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos. Intune se sincroniza automáticamente con Apple para ver la cuenta del programa de inscripción.

## <a name="create-an-apple-enrollment-profile"></a>Creación de un perfil de inscripción de Apple

Ahora que ha instalado el token, puede crear un perfil de inscripción para dispositivos de DEP. Un perfil de inscripción de dispositivos define la configuración que se aplica a un grupo de dispositivos durante la inscripción.

1. En Intune en Azure Portal, pulse **Inscripción de dispositivos** > **Inscripción de Apple**.
2. En **Programa de inscripción de Apple**, seleccione **Perfiles del Programa de inscripción** > **Crear**.
3. En **Crear perfil de inscripción**, escriba un **nombre** y una **descripción** para el perfil con fines administrativos. Los usuarios no ven estos detalles. Puede usar este campo de **nombre** para crear un grupo dinámico en Azure Active Directory. Use el nombre de perfil para definir el parámetro enrollmentProfileName para asignar dispositivos con este perfil de inscripción. Obtenga más información sobre los [grupos dinámicos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

  En **Afinidad de usuario**, elija si los dispositivos con este perfil se inscribirán con o sin un usuario asignado.

 - **Inscribir con afinidad de usuario**: seleccione esta opción para dispositivos que pertenezcan a usuarios y necesiten usar el portal de empresa para hacer uso de servicios, como instalar aplicaciones. Se necesita una afinidad de usuario [Punto de conexión mixto/nombre de usuario de WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Más información](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Inscribir sin afinidad de usuario**: seleccione esta opción para dispositivos no afiliados con un usuario único. Se usa para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones como la aplicación de portal de empresa no funcionan.

4. Seleccione **Configuración de administración de dispositivos** para configurar las siguientes opciones de perfil:

  ![Captura de pantalla sobre cómo elegir el modo de administración. El dispositivo tiene las opciones Supervisado, Inscripción bloqueada y Permitir emparejamiento con el valor Denegar todo. Los certificados de Apple Configurator correspondientes a un nuevo perfil del Programa de inscripción aparecen en gris.](./media/enrollment-program-profile-mode.png)
    - **Supervisado**: un modo de administración que permite más opciones de administración y deshabilita el bloqueo de activación de forma predeterminada. Si deja en blanco la casilla, tendrá funcionalidades de administración limitadas. Microsoft recomienda usar el DEP como mecanismo para habilitar el modo de supervisión, sobre todo para las organizaciones que implementan un gran número de dispositivos iOS.

 > [!NOTE]
 > La configuración de un dispositivo en el modo de supervisión no se puede llevar a cabo con Intune después de que se haya inscrito el dispositivo. Después de la inscripción, la única forma de habilitar el modo de supervisión pasa por conectar un dispositivo iOS a un equipo Mac con un cable USB y usar Apple Configurator, con lo que se restablecerá el dispositivo y se configurará en modo de supervisión. Obtenga más información en los documentos de [Apple Configurator](http://help.apple.com/configurator/mac/2.3). En la pantalla de bloqueo de los dispositivos supervisados aparecerá el mensaje "This iPhone is managed by Contoso" (Este iPhone está administrado por Contoso). Por otro lado, aparecerá "This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device" (Este iPhone está supervisado. Contoso puede supervisar el tráfico de Internet y localizar este dispositivo) en **Ajustes** > **General** > **Acerca de**.

    - **Inscripción bloqueada** (requiere el modo de administración Supervisado): Deshabilita la configuración de iOS que podría permitir la eliminación del perfil de administración. Si deja en blanco la casilla, permite que se quite el perfil de administración en el menú Configuración. Tras la inscripción de los dispositivos, no se puede cambiar esta configuración sin restablecer el dispositivo a los valores de fábrica.

  - **Habilitar iPad compartido**: el Programa de inscripción de dispositivos de Apple no admite iPad compartido.

    - **Permitir emparejamiento**: especifica si se pueden sincronizar dispositivos iOS con equipos. Si pulsa **Permitir Apple Configurator mediante certificado**, debe seleccionar un certificado en **Certificados de Apple Configurator**.

    - **Certificados de Apple Configurator**: si ha pulsado **Permitir Apple Configurator mediante certificado** en **Permitir emparejamiento**, seleccione un certificado de Apple Configurator para importar.

  Elija **Guardar**.

5. Seleccione **Valores del Asistente de configuración** para configurar las siguientes opciones de perfil:

  ![Captura de pantalla sobre cómo elegir la configuración con las opciones disponibles para un nuevo perfil del Programa de inscripción.](./media/enrollment-program-profile-settings.png)
    - **Department Name** (Nombre de departamento): aparece cuando los usuarios pulsan **About Configuration** (Acerca de la configuración) durante la activación.

    - **Teléfono del departamento**: aparece cuando el usuario hace clic en el botón **Necesito ayuda** durante la activación.
    - **Opciones del Asistente para la configuración**: estas opciones opcionales se pueden configurar más adelante en el menú **Configuración** de iOS.
        - **Código de acceso**
        - **Servicios de ubicación**
        - **Restaurar**
        - **ID de Apple**
        - **Términos y condiciones**
        - **Touch ID**
        - **Apple Pay**
        - **Zoom**
        - **Siri**
        - **Datos de diagnóstico**

    Elija **Guardar**.

9. Para guardar la configuración del perfil, seleccione **Crear** en la hoja **Crear perfil de inscripción**. El perfil de inscripción aparece en la lista de Perfiles de inscripción del Programa de inscripción de Apple.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos administrados
Ahora que Intune tiene permiso para administrar los dispositivos, puede sincronizar Intune con Apple para ver los dispositivos administrados en Intune en Azure Portal.

1. En Intune en Azure Portal, pulse **Inscripción de dispositivos** >  **Inscripción de Apple** > **Dispositivos del Programa de inscripción**.
2. En **Dispositivos del Programa de inscripción**, seleccione **Sincronizar**.

  ![Captura de pantalla del nodo Dispositivos del Programa de inscripción seleccionado y el vínculo Sincronizar pulsado.](./media/enrollment-program-device-sync.png)
3. En la hoja **Sincronizar**, seleccione **Solicitar sincronización**. La barra de progreso muestra la cantidad de tiempo que debe esperar antes de solicitar de nuevo la sincronización.

  ![Captura de pantalla de la hoja Sincronización con el vínculo Solicitar sincronización seleccionado.](./media/enrollment-program-device-request-sync.png)

  Para cumplir con las condiciones de Apple relativas a un tráfico del programa de inscripción aceptable, Intune impone las restricciones siguientes:
     -  Una sincronización completa no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune actualiza todos los números de serie de Apple asignados a Intune. Si se intenta efectuar una sincronización completa sin que hayan pasado siete días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.
     -  Las solicitudes de sincronización tardan 15 minutos en finalizar. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón **Sincronización** está deshabilitado.
     - Intune sincroniza con Apple los dispositivos nuevos y eliminados cada 24 horas.

4. En el área de trabajo de Dispositivos del Programa de inscripción, pulse **Actualizar** para ver los dispositivos.

## <a name="assign-an-enrollment-profile-to-devices"></a>Asignar un perfil de inscripción a los dispositivos
Debe asignar un perfil del Programa de inscripción a los dispositivos para poder inscribirlos.

>[!NOTE]
>También puede asignar números de serie a perfiles en la hoja **Números de serie de Apple**.

1. En Intune en Azure Portal, pulse **Inscripción de dispositivos** > **Inscripción de Apple** y, después, pulse **Perfiles del Programa de inscripción**.
2. En la lista de **Perfiles del Programa de inscripción**, seleccione el perfil que quiere asignar a los dispositivos y, después, seleccione **Asignar dispositivos**.

 ![Captura de pantalla de las asignaciones de dispositivos con la opción Asignar seleccionada.](./media/enrollment-program-device-assign.png)

3. Seleccione **Asignar** y, después, seleccione los dispositivos que quiere asignar a este perfil. Puede filtrar para ver los dispositivos disponibles:
  - **sin asignar**
  - **cualquiera**
  - **&lt;nombre de perfil&gt;**
4. Seleccione los dispositivos que quiere asignar. La casilla que se encuentra encima de la columna selecciona hasta 1000 dispositivos de los que figuran en la lista; después, haga clic en **Asignar**. Para inscribir más de 1000 dispositivos, repita los pasos de la asignación hasta que todos los dispositivos tengan un perfil de inscripción asignado.

  ![Captura de pantalla del botón Asignar para la asignación de un perfil del programa de inscripción en Intune](media/dep-profile-assignment.png)

## <a name="distribute-devices"></a>Distribuir los dispositivos
Ha habilitado la administración y sincronización entre Apple e Intune, y ha asignado un perfil para permitir que sus dispositivos de DEP se inscriban. Ahora puede distribuir los dispositivos a los usuarios. Los dispositivos con afinidad de usuario necesitan que a cada usuario se le asigne una licencia de Intune. Los dispositivos sin afinidad de usuario necesitan una licencia de dispositivo. Un dispositivo activado no puede aplicar un perfil de inscripción hasta que el dispositivo se haya restablecido a la configuración de fábrica.

Vea [Inscribir el dispositivo iOS en Intune con el Programa de inscripción de dispositivos](/intune-user-help/enroll-your-device-dep-ios).
