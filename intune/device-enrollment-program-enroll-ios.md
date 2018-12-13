---
title: 'Inscripción de dispositivos iOS: Programa de inscripción de dispositivos'
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos iOS corporativos con el Programa de inscripción de dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 94e7bc3e3b936489ea34170616d1ab0ad49bafd3
ms.sourcegitcommit: 8ddd3b0d4636a4516b2a05fa83c60ec111903c6c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2018
ms.locfileid: "52546047"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Inscribir dispositivos iOS automáticamente con el Programa de inscripción de dispositivos de Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artículo le ayuda a habilitar la inscripción de dispositivos iOS adquiridos por medio del [Programa de inscripción de dispositivos (DEP)](https://deploy.apple.com) de Apple. Puede habilitar la inscripción de DEP para muchos dispositivos sin ni siquiera tocarlos. Puede proporcionar dispositivos como iPhone e iPad directamente a los usuarios. Cuando el usuario activa el dispositivo, se ejecuta el Asistente para la instalación con opciones preconfiguradas y el dispositivo se inscribe en la administración.

Para habilitar la inscripción de DEP, use los portales de DEP de Apple y de Intune. Se necesita una lista de números de serie o un número de pedido de compra, de manera que pueda asignar dispositivos a Intune para la administración. Puede crear perfiles de inscripción de DEP que contengan opciones que se apliquen a los dispositivos durante la inscripción.

Además, la inscripción de DEP no funciona con el [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

## <a name="what-is-supervised-mode"></a>¿Qué es el modo de supervisión?
Apple introdujo el modo de supervisión en iOS 5. Los dispositivos iOS que estén en modo de supervisión se pueden administrar con más controles. Por lo tanto, resulta especialmente útil para los dispositivos corporativos. Intune admite la configuración de dispositivos en el modo de supervisión como parte del Programa de inscripción de dispositivos (DEP) de Apple. 

La compatibilidad con dispositivos DEP no supervisados entró en desuso en iOS 11. En iOS 11 y versiones posteriores, siempre se deben supervisar los dispositivos configurados por DEP. La marca DEP is_supervised se omitirá en una versión de iOS futura.

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

## <a name="get-an-apple-dep-token"></a>Obtener un token de DEP de Apple

Antes de poder inscribir dispositivos iOS con DEP, necesita un archivo de token de DEP (.p7m) de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos de DEP. También permite a Intune cargar perfiles de inscripción en Apple y asignar dispositivos a esos perfiles.

Use el portal de DEP de Apple para crear un token de DEP. También puede usar el portal de DEP para asignar dispositivos a Intune para la administración.

> [!NOTE]
> Si elimina el token desde el portal clásico de Intune antes de realizar la migración a Azure, Intune podría restaurar un token de DEP de Apple eliminado. Puede volver a eliminar el token de DEP desde Azure Portal.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Paso 1. Descargue el certificado de clave pública de Intune necesario para crear el token.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > **Agregar**.

    ![Obtenga un token del programa de inscripción.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Conceda a Microsoft permiso para enviar información de usuario y dispositivo a Apple al seleccionar **Acepto**.

   ![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo de Certificados de Apple para descargar la clave pública.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Seleccione **Descargar la clave pública** para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Paso 2. Use la clave para descargar un token de Apple.

1. Seleccione **Crear un token mediante el Programa de inscripción de dispositivos de Apple** para abrir el portal de Programas de implementación de Apple e iniciar sesión con su id. de Apple de la empresa. Puede usar este id. de Apple para renovar el token de DEP.
2.  En el [portal Programas de implementación](https://deploy.apple.com) de Apple, seleccione **Introducción** para **Programa de inscripción de dispositivos**.

3. En la página **Administrar servidores**, pulse **Add MDM Server** (Agregar servidor de MDM).
4. Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

5. Se abre el cuadro de diálogo **Agregar&lt;Nombre del servidor&gt;**, indicando **Cargar la clave pública**. Elija **Elegir archivo...** para cargar el archivo .pem y, después, elija **Siguiente**.

6. Vaya a **Programa de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**.
7. En **Elegir dispositivos por**, especifique cómo se identifican los dispositivos:
    - **Número de serie**
    - **Número de pedido**
    - **Cargar archivo CSV**.

   ![Captura de pantalla sobre cómo especificar Elegir dispositivos por número de serie, estableciendo Elegir acción como Asignar al servidor y seleccionando el nombre de servidor.](./media/enrollment-program-token-specify-serial.png)

8. En **Elegir acción**, pulse **Asignar al servidor**, seleccione el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y pulse **Aceptar**. El portal de Apple asigna los dispositivos especificados al servidor de Intune para la administración y, después, muestra **Asignación completa**.

   En el portal de Apple, vaya a **Programas de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **View Assignment History** (Ver historial de asignaciones) para ver una lista de dispositivos y su asignación de servidor MDM.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Paso 3: Guarde el identificador de Apple usado para crear este token.

En Intune en Azure Portal, proporcione el id. de Apple para futuras referencias.

![Captura de pantalla sobre cómo especificar el identificador de Apple que se ha usado para crear y buscar el token del Programa de inscripción.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Paso 4. Cargue el token.
En el cuadro **Token de Apple**, vaya al archivo de certificado (.pem), seleccione **Abrir** y después **Crear**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos. Intune se sincroniza automáticamente con Apple para ver la cuenta del programa de inscripción.

## <a name="create-an-apple-enrollment-profile"></a>Creación de un perfil de inscripción de Apple

Ahora que ha instalado el token, puede crear un perfil de inscripción para dispositivos de DEP. Un perfil de inscripción de dispositivos define la configuración que se aplica a un grupo de dispositivos durante la inscripción.

1. En Intune en Azure Portal, elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción**.
2. Seleccione un token, elija **Perfiles** y después **Crear perfil**.

    ![Cree una captura de pantalla del perfil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. En **Crear perfil**, escriba un **nombre** y una **descripción** para el perfil con fines administrativos. Los usuarios no ven estos detalles. Puede usar este campo de **nombre** para crear un grupo dinámico en Azure Active Directory. Use el nombre de perfil para definir el parámetro enrollmentProfileName para asignar dispositivos con este perfil de inscripción. Obtenga más información sobre los [grupos dinámicos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Nombre y descripción del perfil.](./media/device-enrollment-program-enroll-ios/image05.png)

4. En **Afinidad de usuario**, elija si los dispositivos con este perfil deben inscribirse con o sin un usuario asignado.
    - **Inscribir con afinidad de usuario**: seleccione esta opción para dispositivos que pertenezcan a usuarios y necesiten usar el Portal de empresa para hacer uso de servicios, como instalar aplicaciones. Si el uso de ADFS y el perfil de inscripción tiene **Authenticate with Company Portal instead of Setup Assistant** (Autenticar con el Portal de empresa en lugar del Asistente de configuración) está establecido en **No**, se requiere [Punto de conexión mixto/nombre de usuario de WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) [Más información](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Inscribir sin afinidad de usuario**: seleccione esta opción para dispositivos no afiliados con un usuario único. Use esta opción para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones como la aplicación de portal de empresa no funcionan.

5. Si elige **Inscribir con afinidad de usuario**, tiene la opción de permitir que los usuarios se autentiquen en el portal de empresa en lugar de con el Asistente para configuración de Apple.

    ![Autenticación con el portal de empresa.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Si quiere realizar alguna de las acciones siguientes, establezca **Authenticate with Company Portal instead of Apple Setup Assistant** (Autenticar con el Portal de empresa en lugar del Asistente de configuración) en **Sí**.
    >    - usar la autenticación multifactor
    >    - pedir a los usuarios que cambien su contraseña cuando inician sesión por primera vez
    >    - pedir a los usuarios que restablezcan las contraseñas expiradas durante la inscripción
    >
    > Estas operaciones no se admiten durante la autenticación con el asistente de configuración de Apple.

6. Si ha elegido **Sí** para **Autenticar con el Portal de empresa en lugar del Asistente para configuración de Apple**, tiene la opción para usar un token del Programa de compras por volumen (VPP) para instalar automáticamente Portal de empresa en el dispositivo sin que el usuario tenga que proporcionar un identificador de Apple. Para instalar Portal de empresa con un token de VPP, elija un token en **Instalar Portal de empresa con VPP**. Asegúrese de que el token no expire y de que disponga de suficientes licencias de dispositivos para la aplicación Portal de empresa. Si el token expira o se agotan las licencias, Intune instalará Portal de empresa del App Store y solicitará un identificador de Apple.

    ![Captura de pantalla de la instalación de Portal de empresa con VPP.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Si ha elegido un token para **Instalar Portal de empresa con VPP**, tiene la opción de bloquear el dispositivo en Modo de aplicación única (en concreto la aplicación Portal de empresa) inmediatamente después de que finalice el Asistente de configuración. Haga clic en **Sí** en **Run Company Portal in Single App Mode until authentication** (Ejecutar el Portal de empresa en el modo de aplicación única hasta la autenticación) para establecer esta opción. Para usar el dispositivo, primero el usuario debe autenticarse iniciando sesión con el Portal de empresa.
    Esta característica solo es compatible con iOS 11.3.1 y versiones posteriores.

8. Elija **Configuración de administración de dispositivos** y seleccione si desea o no que se supervisen los dispositivos con este perfil.

    ![Captura de pantalla de Configuración de administración de dispositivos.](./media/device-enrollment-program-enroll-ios/devicemanagementsettingsblade.png)

    Los dispositivos **supervisados** ofrecen más opciones de administración y, en este caso, el bloqueo de activación está deshabilitado de forma predeterminada. Microsoft recomienda usar el DEP como mecanismo para habilitar el modo de supervisión, sobre todo para las organizaciones que implementan un gran número de dispositivos iOS.

    Los usuarios reciben notificaciones de que sus dispositivos están supervisados de dos maneras:

   - En la pantalla de bloqueo aparece: "This iPhone is managed by Contoso" (Contoso administra este iPhone).
   - En la pantalla **Configuración** > **General** > **Acerca de** aparece: "This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device" (Este iPhone está supervisado. Contoso puede supervisar el tráfico de Internet y localizar este dispositivo)

     > [!NOTE]
     > Un dispositivo inscrito sin supervisión solo puede restablecerse a supervisado con Apple Configurator. Para restablecer el dispositivo de esta forma, es necesario conectar un dispositivo iOS a un Mac con un cable USB. Obtenga más información en los documentos de [Apple Configurator](http://help.apple.com/configurator/mac/2.3).

9. Elija si desea o no que la inscripción de dispositivos esté bloqueada con este perfil. **Inscripción bloqueada** deshabilita la configuración de iOS que permite que el perfil de administración se quite del menú **Configuración**. Tras la inscripción del dispositivo, no se puede cambiar esta configuración sin borrar el dispositivo. Estos dispositivos deben tener el modo de administración **supervisado** definido en *Sí*. 

10. Elija si desea o no que los dispositivos que usan este perfil se puedan **sincronizar con equipos**. Si elige **Permitir Apple Configurator mediante certificado**, debe seleccionar un certificado en **Certificado de Apple Configurator**.

11. Si selecciona **Permitir Apple Configurator mediante certificado** en el paso anterior, elija un certificado de Apple Configurator para importarlo.

12. Elija **Aceptar**.

13. Seleccione **Personalización del Asistente para configuración** para configurar las opciones de perfil siguientes: ![Personalización del Asistente para configuración.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Configuración de departamento | Descripción |
    |---|---|
    | <strong>Nombre de departamento</strong> | Aparece cuando los usuarios pulsan <strong>Acerca de la configuración</strong> durante la activación. |
    |    <strong>Teléfono del departamento</strong>     | Aparece cuando el usuario hace clic en el botón <strong>Necesito ayuda</strong> durante la activación. |

  Cuando el usuario configura el dispositivo, es posible mostrar u ocultar varias pantallas del asistente de configuración.
  - Si elige **Ocultar**, la pantalla no se mostrará durante la configuración. Después de configurar el dispositivo, el usuario seguirá teniendo la posibilidad de ir al menú **Ajustes** para configurar la característica.
  - Si elige **Mostrar**, la pantalla se mostrará durante la configuración. A veces, el usuario puede omitir la pantalla sin realizar ninguna acción. Sin embargo, posteriormente podrá ir al menú **Ajustes** del dispositivo para configurar la característica. 


    | Configuración de pantallas del asistente | Si hace clic en **Mostrar**, durante la configuración se producirá lo siguiente en el dispositivo... |
    |------------------------------------------|------------------------------------------|
    | <strong>Código de acceso</strong> | Se solicitará un código de acceso al usuario. Solicite siempre un código de acceso, a menos que el dispositivo esté protegido o tenga el acceso controlado de otra manera (es decir, modo de quiosco que restringe el dispositivo a una aplicación). |
    | <strong>Servicios de ubicación</strong> | Se solicitará la ubicación del usuario. |
    | <strong>Restaurar</strong> | Se mostrará la pantalla **Aplicaciones y datos**. En esta pantalla el usuario tendrá la opción de restaurar o transferir datos de una copia de seguridad de iCloud al configurar el dispositivo. |
    | <strong>iCloud e identificador de Apple</strong> | El usuario tendrá la opción de iniciar sesión con su **ID de Apple** y usar **iCloud**.                         |
    | <strong>Términos y condiciones</strong> | El usuario deberá aceptar los términos y condiciones de Apple. |
    | <strong>Touch ID</strong> | El usuario tendrá la opción de configurar una identificación con huella digital para el dispositivo. |
    | <strong>Apple Pay</strong> | El usuario tendrá la opción de configurar Apple Pay en el dispositivo. |
    | <strong>Zoom</strong> | El usuario tendrá la opción de ampliar el contenido de la pantalla al configurar el dispositivo. |
    | <strong>Siri</strong> | El usuario tendrá la opción de configurar Siri. |
    | <strong>Datos de diagnóstico</strong> | Se mostrará la pantalla **Diagnóstico** al usuario. En esta pantalla el usuario podrá enviar datos de diagnóstico a Apple. |


14. Elija **Aceptar**.

15. Para guardar el perfil, elija **Crear**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos administrados
Ahora que Intune tiene permiso para administrar los dispositivos, puede sincronizar Intune con Apple para ver los dispositivos administrados en Intune en Azure Portal.

1. En Intune en Azure Portal, seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija un token de la lista > **Dispositivos** > **Sincronizar**. ![Captura de pantalla del nodo Dispositivos del Programa de inscripción seleccionado y el vínculo Sincronizar pulsado.](./media/device-enrollment-program-enroll-ios/image06.png)

   Para cumplir con las condiciones de Apple relativas a un tráfico del programa de inscripción aceptable, Intune impone las restricciones siguientes:
   - Una sincronización completa no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune captura la lista actualizada completa de números de serie asignados al servidor MDM de Apple conectado a Intune. Tras eliminar un dispositivo del Programa de inscripción desde el portal de Intune sin anular su asignación del servidor MDM de Apple, no se podrá volver a importar hasta que se ejecute la sincronización completa.   
   - Una sincronización se ejecuta automáticamente cada 24 horas. También puede sincronizar haciendo clic en el botón **Sincronizar** (no más de una vez cada 15 minutos). Todas las solicitudes de sincronización tardan 15 minutos en finalizar. El botón **Sincronizar** queda deshabilitado hasta que se completa la sincronización. Esta sincronización actualizará el estado del dispositivo existente e importará nuevos dispositivos asignados al servidor MDM de Apple.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Asignar un perfil de inscripción a los dispositivos
Debe asignar un perfil del Programa de inscripción a los dispositivos para poder inscribirlos.

>[!NOTE]
>También puede asignar números de serie a perfiles en la hoja **Números de serie de Apple**.

1. En Intune en Azure Portal, seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija un token de la lista.
2. Elija **Dispositivos** > Elija los dispositivos de la lista > **Asignar perfil**.
3. En **Asignar perfil**, elija un perfil para los dispositivos y seleccione **Asignar**.

### <a name="assign-a-default-profile"></a>Asignación de un perfil predeterminado

Puede elegir un perfil predeterminado para aplicarlo a todos los dispositivos que se inscriben en un token específico.

1. En Intune en Azure Portal, seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija un token de la lista.
2. Elija **Establecer perfil predeterminado**, seleccione un perfil en la lista desplegable y después seleccione **Guardar**. Este perfil se aplicará a todos los dispositivos que se inscriben en el token.

## <a name="distribute-devices"></a>Distribuir los dispositivos
Ha habilitado la administración y sincronización entre Apple e Intune, y ha asignado un perfil para permitir que sus dispositivos de DEP se inscriban. Ahora puede distribuir los dispositivos a los usuarios. Los dispositivos con afinidad de usuario necesitan que a cada usuario se le asigne una licencia de Intune. Los dispositivos sin afinidad de usuario necesitan una licencia de dispositivo. Un dispositivo activado no puede aplicar un perfil de inscripción hasta que se haya borrado.

Vea [Inscribir el dispositivo iOS en Intune con el Programa de inscripción de dispositivos](/intune-user-help/enroll-your-device-dep-ios).

## <a name="renew-a-dep-token"></a>Renovación del token de DEP  
1. Vaya a deploy.apple.com.  
2. En **Administrar servidores**, elija el servidor MDM asociado con el archivo de token que desea renovar.
3. Elija **Generar nuevo token**.

    ![Captura de pantalla de Generar nuevo token.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Elija **Su token de servidor**.  
5. En [Intune en Azure Portal](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > elija el token.
    ![Captura de pantalla de Tokens del programa de inscripción.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Elija **Renovar token** y escriba el identificador de Apple usado para crear el token original.  
    ![Captura de pantalla de Generar nuevo token.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Cargue el token recién descargado.  
9. Elija **Renovar token**. Verá la confirmación de que el token se renovó.   
    ![Captura de pantalla de confirmación.](./media/device-enrollment-program-enroll-ios/confirmation.png)
