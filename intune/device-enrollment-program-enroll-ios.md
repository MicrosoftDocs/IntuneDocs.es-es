---
title: "Inscripción de dispositivos iOS: Programa de inscripción de dispositivos"
titleSuffix: Intune on Azure
description: "Aprenda a inscribir dispositivos iOS corporativos mediante el Programa de inscripción de dispositivos."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f509f5332b2f8b5f6745816f8795a9a54c10ce2d
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="set-up-ios-device-enrollment-with-device-enrollment-program"></a>Configuración de la inscripción de dispositivos iOS con el Programa de inscripción de dispositivos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tema ayuda a los administradores de TI a habilitar la inscripción de dispositivos iOS adquiridos mediante el [Programa de inscripción de dispositivos (DEP)](https://deploy.apple.com) de Apple. Microsoft Intune puede implementar un perfil de inscripción "de forma inalámbrica" en los dispositivos que se adquieren a través de DEP. El administrador no tiene que tocar nunca cada dispositivo administrado. Un perfil de DEP contiene la configuración de administración que se aplica a los dispositivos durante la inscripción, incluidas las opciones del Asistente de configuración.

Para habilitar la inscripción de DEP, use los portales de DEP de Apple y de Intune. También se necesita una lista o el número del pedido de compra de sus dispositivos de DEP de manera que pueda asignarlos a Intune para su administración en Azure Portal.

>[!NOTE]
>La inscripción de DEP no se puede usar con el [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

**Pasos para habilitar los programas de inscripción de Apple**
1. [Obtener un token de DEP de Apple y asignar los dispositivos](#get-the-apple-dep-certificate)
2. [Crear un perfil de inscripción](#create-anapple-enrollment-profile)
3. [Sincronizar dispositivos administrados por DEP](#sync-dep-managed-devices)
4. [Asignar el perfil de DEP a los dispositivos](#assign-a-dep-profile-to-devices)
5. [Distribuir los dispositivos a los usuarios](#distribute-devices-to-users)

## <a name="get-the-apple-dep-token"></a>Obtención del token de DEP de Apple

Antes de poder inscribir dispositivos iOS corporativos en el Programa de inscripción de dispositivos (DEP) de Apple, necesita un token de DEP de Apple (archivo .p7m). Este token permite a Intune sincronizar información sobre dispositivos corporativos que participan en DEP. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles.

> [!NOTE]
> Si se ha migrado el inquilino de Intune de la consola clásica de Intune a Azure Portal y se ha eliminado un token de DEP de Apple de la consola de administración de Intune durante el período de migración, es posible que el token de DEP se haya restaurado a su cuenta de Intune. Puede volver a eliminar el token de DEP desde Azure Portal.

**Requisitos previos**
- [Certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- Suscripción al [Programa de inscripción de dispositivos de Apple](http://deploy.apple.com)

**Paso 1. Descargue un certificado de clave pública de Intune necesario para crear un token de DEP de Apple.**<br>
1. En el portal de Intune, pulse **Inscripción de dispositivos**, **Inscripción de Apple** y **Token del Programa de inscripción**.
![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo de Certificados de Apple.](./media/enrollment-program-token-add.png)
2. Seleccione **Download your public key** (Descargar la clave pública) para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.
![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo de Certificados de Apple para descargar la clave pública.](./media/enrollment-program-token-download.png)

**Paso 2. Cree y descargue un token de DEP de Apple.**<br>
Seleccione **Create a token via Apple's Device Enrollment Program** (Crear un token mediante el Programa de inscripción de dispositivos de Apple) para abrir el portal de Programas de implementación de Apple e iniciar sesión con su id. de Apple de la empresa. Puede usar este id. de Apple para renovar el token de DEP.
  ![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo de Certificados de Apple.](./media/enrollment-program-token-create.png)

  ![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo de Certificados de Apple para descargar la clave pública.](./media/enrollment-program-token-sign.png)
   1.  En el [portal Programas de implementación](https://deploy.apple.com) de Apple, seleccione **Introducción** para **Programa de inscripción de dispositivos**.
   ![Captura de pantalla del Programa de inscripción haciendo clic en Introducción para el Programa de inscripción de dispositivos.](./media/enrollment-program-token-started.png)
   2. En la página **Administrar servidores**, pulse **Add MDM Server** (Agregar servidor de MDM).
   3. Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

   ![Captura de pantalla de la adición de un nombre de servidor de MDM para DEP y, después, hacer clic en Siguiente.](./media/enrollment-program-token-add-server.png)
   4.  Se abre el cuadro de diálogo **Agregar&lt;Nombre del servidor&gt;**, indicando **Cargar la clave pública**. Elija **Elegir archivo...** para cargar el archivo .pem y, después, elija **Siguiente**.
   ![Captura de pantalla de pulsar el botón de archivo de clave pública y, después, hacer clic en Siguiente.](./media/enrollment-program-token-choose-file.png)
   4.  El cuadro de diálogo **Agregar &lt;NombreDeServidor&gt;** muestra un vínculo **Your Server Token (Su token de servidor)**. Descargue el archivo de token de servidor (.p7m) en el equipo y, después, elija **Listo**.
   ![Captura de pantalla de pulsar el botón de archivo de clave pública y, después, hacer clic en Siguiente.](./media/enrollment-program-token-your-token.png)
   5. Vaya a **Programa de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**.
   6. En **Elegir dispositivos por**, especifique cómo se identifican los dispositivos:
    - **Número de serie**
    - **Número de pedido**
    - **Cargar archivo CSV**.

   ![Captura de pantalla sobre cómo especificar Elegir dispositivos por número de serie, estableciendo Elegir acción como Asignar al servidor y seleccionando el nombre de servidor.](./media/enrollment-program-token-specify-serial.png)

   7. Para **Elegir acción**, seleccione **Asignar al servidor**, seleccione el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y pulse **Aceptar**. El portal de Apple asigna los dispositivos especificados al servidor de Intune para la administración y, después, muestra **Asignación completa**.

   En el portal de Apple, vaya a **Programas de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **View Assignment History** (Ver historial de asignaciones) para ver una lista de dispositivos y su asignación de servidor MDM.

**Paso 3. Escriba el identificador de Apple usado para crear el token del programa de inscripción.**<br>En el portal de Intune, proporcione el id. de Apple para futuras referencias. Use este id. para renovar el token del programa de inscripción para evitar la necesidad de volver a inscribir todos los dispositivos.
![Captura de pantalla sobre cómo especificar el id. de Apple que se ha usado para crear el token del programa de inscripción y buscar el token del programa de inscripción.](./media/enrollment-program-token-apple-id.png)
**Paso 4. Buscar el token del programa de inscripción que se va a cargar.**<br>
Vaya al archivo de certificado (.pem), elija **Abrir** y luego elija **Cargar**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos. Intune se sincroniza automáticamente con Apple para ver la cuenta del programa de inscripción.

## <a name="create-an-apple-enrollment-profile"></a>Creación de un perfil de inscripción de Apple

Un perfil de inscripción de dispositivos define la configuración que se aplica a un grupo de dispositivos durante la inscripción.

1. En el portal de Intune, elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
2. En **Programa de inscripción de Apple**, seleccione **Perfiles del Programa de inscripción** y, después, seleccione **Crear** en la hoja **Perfiles del Programa de inscripción**.
![Captura de pantalla sobre la elección de crear un vínculo para crear un nuevo perfil del programa de inscripción.](./media/enrollment-program-profile-create.png)
3. En la hoja **Crear perfil de inscripción**, escriba un **nombre** y una **descripción** para el perfil con fines administrativos. Los usuarios no ven estos detalles.
![Captura de pantalla de cómo especificar la descripción del nombre y, después, seleccionar Inscribir con afinidad de usuario para obtener un nuevo perfil del programa de inscripción.](./media/enrollment-program-profile-name.png)
En **Afinidad de usuario**, elija si los dispositivos con este perfil se inscribirán con o sin afinidad de usuario.

 - **Inscribir con afinidad de usuario**: los dispositivos se afilian a un usuario durante la configuración y luego se les puede permitir el acceso a los datos y al correo electrónico de la empresa. Elija la **afinidad de usuario** para dispositivos que pertenezcan a usuarios y necesiten usar el portal de empresa para hacer uso de servicios, como instalar aplicaciones.

<<<<<<< HEAD
 > [!NOTE]
 > Multi-Factor Authentication (MFA) no funciona durante la inscripción en dispositivos administrados mediante programas de inscripción con afinidad de usuario. Después de la inscripción, MFA funciona según lo previsto en estos dispositivos. No se puede pedir a los nuevos usuarios que cambien la contraseña al iniciar sesión por primera vez durante la inscripción en dispositivos. Además, no se puede pedir a los usuarios cuyas contraseñas hayan expirado que las restablezcan durante la inscripción y tienen que hacerlo desde otro dispositivo.

 >[!NOTE]
 >La administración del Programa de inscripción con afinidad de usuario requiere un [punto de conexión de nombre de usuario/mixto WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) para que se habilite para solicitar un token de usuario. [Obtenga más información sobre WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
=======
    >[!NOTE]
    >DEP con afinidad de usuario precisa que el [punto de conexión WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) esté habilitado para solicitar el token de usuario. [Obtenga más información sobre WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
>>>>>>> 0c3fe0dee88e8ef4d8ad8ad28c0f8957831dd5b3

 - **Inscribir sin afinidad de usuario**: el dispositivo no está afiliado a ningún usuario. Utilice esta afiliación para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones que requieren la afiliación de un usuario no funcionarán, incluida la aplicación Portal de empresa cuando se usa para instalar aplicaciones de línea de negocio.

4. Seleccione **Configuración de administración de dispositivos** para configurar las siguientes opciones de perfil: ![Captura de pantalla sobre seleccionar el modo de administración con Supervisado, inscripción bloqueada, permitir emparejamiento establecido en Denegar todo y los certificados de Apple Configurator atenuados para un nuevo perfil del programa de inscripción.](./media/enrollment-program-profile-mode.png)
    - **Supervisado**: un modo de administración que permite más opciones de administración y deshabilita el bloqueo de activación de forma predeterminada. Si deja en blanco la casilla, tendrá funcionalidades de administración limitadas.

    - **Inscripción bloqueada** (requiere el modo de administración Supervisado): deshabilita la configuración de iOS que podría permitir la eliminación del perfil de administración. Si deja en blanco la casilla, permite que se quite el perfil de administración en el menú Configuración. Este elemento se establece durante la activación y no se puede cambiar sin un restablecimiento de fábrica.

    - **Permitir emparejamiento**: especifica si se pueden sincronizar dispositivos iOS con equipos. Si elige **Permitir Apple Configurator mediante certificado**, debe seleccionar un certificado en **Certificado de Apple Configurator**.

    - **Certificados de Apple Configurator**: si eligió **Permitir Apple Configurator mediante certificado** en **Permitir emparejamiento**, seleccione un certificado de Apple Configurator para importar.

  Elija **Guardar**.

5. Seleccione **Valores del Asistente de configuración** para configurar las siguientes opciones del perfil: ![Captura de pantalla sobre seleccionar las opciones de configuración con las opciones disponibles para un nuevo perfil del programa de inscripción.](./media/enrollment-program-profile-settings.png)
    - **Department Name** (Nombre de departamento): aparece cuando los usuarios pulsan **About Configuration** (Acerca de la configuración) durante la activación.

    - **Teléfono del departamento**: aparece cuando el usuario hace clic en el botón Necesito ayuda durante la activación.
    - **Opciones del Asistente para la configuración**: estas opciones opcionales se pueden configurar más adelante en el menú **Configuración** de iOS.
        - **Código de acceso**: solicita el código de acceso durante la activación. Solicite siempre un código de acceso, a menos que el dispositivo esté protegido o tenga el acceso controlado de otra manera (es decir, modo de quiosco que restringe el dispositivo a una aplicación).
        - **Servicios de ubicación**: si está habilitado, el Ayudante para la configuración solicitará el servicio durante la activación.
        - **Restauración**: si está habilitado, el Ayudante para la configuración solicitará una copia de seguridad de iCloud durante la activación.
        - **Id. de Apple**: si está habilitado, iOS solicita a los usuarios un identificador de Apple cuando Intune intenta instalar una aplicación sin un identificador. Se requiere un identificador de Apple para descargar aplicaciones del App Store de iOS, incluidas las que instala Intune.
        - **Términos y condiciones**: si está habilitado, el Asistente para la configuración solicita a los usuarios que acepten los términos y condiciones de Apple durante la activación.
        - **Touch ID**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Apple Pay**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Zoom**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Siri**: si está habilitado, el Ayudante para la configuración solicitará este servicio durante la activación.
        - **Datos de diagnóstico**: si esta opción está habilitada, el Ayudante de configuración solicitará este servicio durante la activación.

    Elija **Guardar**.
9. Para guardar la configuración del perfil, seleccione **Crear** en la hoja **Crear perfil de inscripción**. El perfil de inscripción aparece en la lista de Perfiles de inscripción del Programa de inscripción de Apple.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos administrados
Ahora que Intune tiene permiso para administrar los dispositivos, puede sincronizar Intune con Apple para ver los dispositivos administrados en el portal de Intune.

1. En el portal de Intune, pulse **Inscripción de dispositivos** &gt; **Inscripción de Apple** &gt; **Dispositivos del Programa de inscripción**.
2. En **Dispositivos del Programa de inscripción**, seleccione **Sincronizar**. Aparece la hoja **Sincronización**.
![Captura de pantalla del nodo Dispositivos del Programa de inscripción seleccionado y el vínculo Sincronizar pulsado.](./media/enrollment-program-device-sync.png)
3. En la hoja **Sincronizar**, seleccione **Solicitar sincronización**. La barra de progreso muestra la cantidad de tiempo que debe esperar antes de solicitar de nuevo la sincronización.
![Captura de pantalla de la hoja Sincronización con el vínculo Solicitar sincronización seleccionado.](./media/enrollment-program-device-request-sync.png)
    Para cumplir con las condiciones de Apple relativas a un tráfico del programa de inscripción aceptable, Intune impone las restricciones siguientes:
     -  Una sincronización completa no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune actualiza todos los números de serie que Apple ha asignado a Intune, independientemente de si el número de serie se ha sincronizado previamente o no. Si se intenta efectuar una sincronización completa sin que hayan pasado siete días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.
     -  Las solicitudes de sincronización tardan 15 minutos en finalizar. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón **Sincronización** está deshabilitado.
4. En el área de trabajo de Dispositivos del Programa de inscripción, pulse **Actualizar** para ver los dispositivos.

## <a name="assign-an-enrollment-profile-to-devices"></a>Asignar un perfil de inscripción a los dispositivos
Los dispositivos administrados por Intune deben tener un perfil del programa de inscripción asignado antes de la inscripción.

>[!NOTE]
>También puede asignar números de serie a perfiles en la hoja **Números de serie de Apple**.

1. En el portal de Intune, elija **Inscripción de dispositivos** > **Inscripción de Apple** y luego seleccione **Perfiles del Programa de inscripción**.
2. En la lista de **Perfiles del Programa de inscripción**, seleccione el perfil que quiere asignar a los dispositivos y luego seleccione **Asignar dispositivos**.
![Captura de pantalla de la hoja Sincronización con el vínculo Solicitar sincronización seleccionado.](./media/enrollment-program-device-assign.png)
3. Seleccione **Asignar** y, después, seleccione los dispositivos que quiere asignar a este perfil. Puede filtrar para ver los dispositivos disponibles:
  - **sin asignar**
  - **cualquiera**
  - **&lt;nombre de perfil&gt;**
4. Seleccione los dispositivos que desea asignar. La casilla que se encuentra encima de la columna seleccionará hasta 1000 dispositivos de los que figuran en la lista; a continuación, haga clic en **Asignar**. Para inscribir más de 1000 dispositivos, repita los pasos de la asignación hasta que todos los dispositivos tengan un perfil de inscripción asignado.

  ![Captura de pantalla del botón Asignar para la asignación de un perfil del programa de inscripción en el portal de Intune](media/dep-profile-assignment.png)

## <a name="end-user-experience-with-managed-devices"></a>Experiencia del usuario final con dispositivos administrados

Ahora puede distribuir los dispositivos a los usuarios. Los dispositivos con afinidad de usuario necesitan que a cada usuario se le asigne una licencia de Intune. Si el dispositivo se ha activado y está en uso, el perfil no se aplicará hasta que el dispositivo se restablezca a sus valores de fábrica. Cuando el dispositivo iOS administrado mediante un programa de inscripción está activado, el usuario ve lo siguiente:  

1. **Configurar dispositivo iOS**: los usuarios pueden elegir entre las opciones siguientes:
  - **Set Up as New device** (Configurar como un nuevo dispositivo)
  - **Restore from iCloud Backup** (Restaurar desde la copia de seguridad de iCloud)
  - **Restore from iTunes Backup** (Restaurar desde la copia de seguridad de iTunes)
2. A los usuarios se les informa de que **Microsoft configurará su dispositivo automáticamente.** Los siguientes detalles de configuración adicionales también están disponibles:

  **La configuración permite que Microsoft administre este dispositivo de forma inalámbrica.**

  **Un administrador puede ayudarle a configurar las cuentas de red y correo electrónico, instalar y configurar aplicaciones y administrar la configuración de manera remota.**

  **Un administrador puede deshabilitar características, instalar y quitar aplicaciones, supervisar y restringir el tráfico de Internet y borrar de manera remota este dispositivo.**

  **La configuración se proporciona por:<br> Equipo Microsoft Intune iOS<br> One Microsoft Way, Redmond, WA 98052 (USA)**

3. A los usuarios se les pide su nombre de usuario y contraseña de la cuenta profesional o educativa.
4. A los usuarios se les pide su id. de Apple. Se necesita un id. de Apple para instalar la aplicación de portal de empresa de Intune y otras aplicaciones. Después de que se proporcionen las credenciales, el dispositivo instala un perfil de administración que no puede quitarse. El perfil de administración de Intune se muestra en **Configuración** > **General** > **Administración de dispositivos** en el dispositivo.

Ahora los usuarios pueden finalizar la configuración de su dispositivo propiedad de la empresa con el portal de empresa de Intune o el Asistente para la configuración de Apple.
