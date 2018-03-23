---
title: Configuración de la inscripción en el programa de Apple School Manager para dispositivos iOS
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo configurar la inscripción en el programa de Apple School Manager para dispositivos iOS corporativos con Intune (nueva interfaz de usuario).
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c35a23e-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4054eb3804c159e6256b07bf89b8ccd93f7b2e8e
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2018
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Habilitación de la inscripción de dispositivos iOS con Apple School Manager

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Diferencias temporales de la interfaz de usuario
>
>La actualización de las interfaces de usuario para las características descritas en esta página está en proceso. Estas actualizaciones se implementarán en todas las cuentas de usuario hasta final de abril.
>
>Si la página **Inscripción de dispositivos** es similar a la imagen siguiente, significa que tiene las interfaces de usuario actualizadas y puede usar esta página de ayuda.
>
>![Interfaz de usuario nueva](./media/appleenroll-newui.png)
>
>En cambio, si la página **Inscripción de dispositivos** es similar a la imagen siguiente, significa que la cuenta no se ha actualizado aún a la nueva interfaz de usuario. Vaya a [esta página de ayuda](apple-school-manager-set-up-ios.md).
>
>![Interfaz de usuario anterior](./media/appleenroll-oldui.png)

En este tema, se le ayuda a habilitar la inscripción de dispositivos iOS adquiridos mediante el programa de [Apple School Manager](https://school.apple.com/). Al usar Intune con Apple School Manager, puede inscribir un gran número de dispositivos iOS sin tener que tocarlos. Cuando un estudiante o profesor activa el dispositivo, se ejecuta el Asistente para la configuración con valores preconfigurados y el dispositivo se inscribe en la administración.

Para habilitar la inscripción de Apple School Manager, se usan los portales de Intune y de Apple School Manager. Se necesita una lista de números de serie o un número de pedido de compra, de manera que pueda asignar dispositivos a Intune para la administración. Puede crear perfiles de inscripción de DEP que contengan opciones que se apliquen a los dispositivos durante la inscripción.

La inscripción de Apple School Manager no se puede usar con el [Programa de inscripción de dispositivos de Apple](device-enrollment-program-enroll-ios.md) ni con el [Administrador de inscripciones de dispositivos](device-enrollment-manager-enroll.md).

**Requisitos previos**
- [Certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- [Entidad de MDM](mdm-authority-set.md)
- [Certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- Se necesita una afinidad de usuario [Punto de conexión mixto/nombre de usuario de WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Más información](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Los dispositivos tienen que haberse adquirido a través del programa de [Apple School Management](http://school.apple.com)

## <a name="get-an-apple-token-and-assign-devices"></a>Obtener un token de Apple y asignar los dispositivos

Antes de poder inscribir dispositivos iOS corporativos en Apple School Manager, necesita un archivo de token (.p7m) de Apple. Este token permite a Intune sincronizar información sobre dispositivos que participan en Apple School Manager. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles. En Azure Portal, también puede asignar números de serie a los dispositivos para su administración.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-an-apple-token"></a>Paso 1. Descargue el certificado de clave pública de Intune necesario para crear un token de Apple

1. En [Intune](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > **Agregar**.

  ![Obtenga un token del programa de inscripción.](./media/device-enrollment-program-enroll-ios/image01.png)

2. En la hoja **Token del Programa de inscripción**, elija **Descargar la clave pública** para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal de Apple School Manager.
     ![Hoja Tokens del programa de inscripción.](./media/device-enrollment-program-enroll-ios/image02.png)

### <a name="step-2-download-a-token-and-assign-devices"></a>Paso 2. Descargue un token y asigne los dispositivos
1. Elija **Crear un token mediante Apple School Manager** e inicie sesión en Apple School con su identificador de Apple empresarial. Puede usar este identificador de Apple para renovar el token de Apple School Manager.
2.  En el [portal de Apple School Manager](https://school.apple.com), vaya a **MDM Servers** (Servidores MDM) y luego elija **Add MDM Server** (Agregar servidor MDM) (en la parte superior derecha).
3.  Escriba el **nombre del servidor de MDM**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.
   ![Captura de pantalla del portal de Apple School Manager con la opción de número de serie seleccionada](./media/asm-server-assignment.png)

4.  Elija **Upload File...** (Cargar archivo...) en el portal de Apple, examine el archivo .pem y elija **Save MDM Server** (Guardar servidor MDM) (en la parte inferior derecha).
5.  Elija **Get Token** (Obtener token) y luego descargue el archivo de token del servidor (.p7m) en el equipo.
6. Vaya a **Device Assignments** (Asignaciones de dispositivos) y **Choose Device** (Elegir dispositivo) con la entrada manual de **números de serie** o **números de pedido** o con la opción **Upload CSV File** (Cargar archivo CSV).
     ![Captura de pantalla del portal de Apple School Manager con la opción de número de serie seleccionada](./media/asm-device-assignment.png)
7.  Elija la acción **Assign to Server** (Asignar al servidor) y elija el **servidor MDM** que ha creado.
8. Especifique cómo **Elegir dispositivos**, después proporcione información de los dispositivos y detalles.
9. Elija **Assign to Server** (Asignar al servidor), elija el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y después elija **Aceptar**.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Paso 3: Guarde el identificador de Apple usado para crear este token

En Intune en Azure Portal, proporcione el id. de Apple para futuras referencias.

![Captura de pantalla sobre cómo especificar el identificador de Apple que se ha usado para crear y buscar el token del Programa de inscripción.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Paso 4. Cargue el token
En el cuadro **Token de Apple**, vaya al archivo de certificado (.pem), seleccione **Abrir** y después **Crear**. Con el certificado push, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos. Intune sincroniza automáticamente los dispositivos de Apple School Manager desde Apple.

## <a name="create-an-apple-enrollment-profile"></a>Creación de un perfil de inscripción de Apple
Ahora que ha instalado el token, puede crear un perfil de inscripción para dispositivos de Apple School. Un perfil de inscripción de dispositivos define la configuración que se aplica a un grupo de dispositivos durante la inscripción.

1. En [Intune](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción**.
2. Seleccione un token, elija **Perfiles** y después **Crear perfil**.
3. En **Crear perfil**, escriba un **nombre** y una **descripción** para el perfil con fines administrativos. Los usuarios no ven estos detalles. Puede usar este campo de **nombre** para crear un grupo dinámico en Azure Active Directory. Use el nombre de perfil para definir el parámetro enrollmentProfileName para asignar dispositivos con este perfil de inscripción. Obtenga más información sobre los [grupos dinámicos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).
    ![Nombre y descripción del perfil.](./media/device-enrollment-program-enroll-ios/image05.png)
    
4. En **Afinidad de usuario**, elija si los dispositivos con este perfil deben inscribirse con o sin un usuario asignado.
    - **Inscribir con afinidad de usuario**: seleccione esta opción para dispositivos que pertenezcan a usuarios y necesiten usar el portal de empresa para hacer uso de servicios, como instalar aplicaciones. Esta opción también permite a los usuarios autenticar sus dispositivos mediante el portal de empresa. Se necesita una afinidad de usuario [Punto de conexión mixto/nombre de usuario de WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Más información](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).   El modo iPad compartido de Apple School Manager requiere la inscripción del usuario sin afinidad de usuario.

    - **Inscribir sin afinidad de usuario**: seleccione esta opción para dispositivos no afiliados con un usuario único, como un dispositivo compartido. Use esta opción para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones como la aplicación de portal de empresa no funcionan.

5. Si elige **Inscribir con afinidad de usuario**, tiene la opción de permitir que los usuarios se autentiquen en el portal de empresa en lugar de con el Asistente para configuración de Apple.

    ![Autenticación con el portal de empresa.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    >[!NOTE]
    >Multi-Factor Authentication (MFA) no funciona durante la inscripción en dispositivos de Apple School Manager si las propiedades del perfil están establecidas en **Use with User Affinity** (Usar con afinidad de usuario) y no usa un portal de empresa. Después de la inscripción, MFA funciona según lo previsto en estos dispositivos. Los dispositivos no pueden pedir a los usuarios que cambien su contraseña cuando inician sesión por primera vez. Además, no se puede pedir a los usuarios cuyas contraseñas hayan expirado que las restablezcan durante la inscripción. Los usuarios deben usar un dispositivo diferente para restablecer la contraseña.

6. Elija **Configuración de administración de dispositivos** y seleccione si desea o no que se supervisen los dispositivos con este perfil.
    Los dispositivos **supervisados** ofrecen más opciones de administración y, en este caso, el bloqueo de activación está deshabilitado de forma predeterminada. Microsoft recomienda usar el DEP como mecanismo para habilitar el modo de supervisión, sobre todo para las organizaciones que implementan un gran número de dispositivos iOS.

    Los usuarios reciben notificaciones de que sus dispositivos están supervisados de dos maneras:

    - En la pantalla de bloqueo aparece: "This iPhone is managed by Contoso" (Contoso administra este iPhone).
    - En la pantalla **Configuración** > **General** > **Acerca de** aparece: "This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device" (Este iPhone está supervisado. Contoso puede supervisar el tráfico de Internet y localizar este dispositivo)

     > [!NOTE]
     > Un dispositivo inscrito sin supervisión solo puede restablecerse a supervisado con Apple Configurator. Para restablecer el dispositivo de esta forma, es necesario conectar un dispositivo iOS a un Mac con un cable USB. Obtenga más información en los documentos de [Apple Configurator](http://help.apple.com/configurator/mac/2.3).

7. Elija si desea o no que la inscripción de dispositivos esté bloqueada con este perfil. **Inscripción bloqueada** deshabilita la configuración de iOS que permite que el perfil de administración se quite del menú **Configuración**. Tras la inscripción de los dispositivos, no se puede cambiar esta configuración sin restablecer el dispositivo a los valores de fábrica. Estos dispositivos deben tener el modo de administración **supervisado** definido en *Sí*. 

8. Si desea permitir que varios usuarios inicien sesión en iPads compartidos con un identificador de Apple administrado, seleccione **Sí** en **iPad compartido**. Para ello, es necesario que **Inscribir sin afinidad de usuario** y el modo **Supervisado** estén establecidos en **Sí**. Los identificadores de Apple administrados se crean en el portal de Apple School Manager. Obtenga más información sobre los dispositivos [iPad compartidos](education-settings-configure-ios-shared.md). También debe revisar los [requisitos para compartir un iPad de Apple](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56).

9. Elija si desea o no que los dispositivos que usan este perfil se puedan **sincronizar con equipos**. Si elige **Permitir Apple Configurator mediante certificado**, debe seleccionar un certificado en **Certificado de Apple Configurator**.

9. Si selecciona **Permitir Apple Configurator mediante certificado** en el paso anterior, elija un certificado de Apple Configurator para importarlo.

10. Elija **Aceptar**.

11. Seleccione **Valores del Asistente de configuración** para configurar las siguientes opciones de perfil: ![Personalización del Asistente para configuración](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png).

    | Setting | Descripción |
    | --- | --- |
    | **Nombre de departamento** | Aparece cuando los usuarios pulsan **Acerca de la configuración** durante la activación. |
    | **Teléfono del departamento** | Aparece cuando el usuario hace clic en el botón **Necesito ayuda** durante la activación. |
    | **Opciones del Asistente para la configuración** | Estas opciones opcionales se pueden configurar más adelante en el menú **Configuración** de iOS. |
    | **Código de acceso** | Solicita el código de acceso durante la activación. Solicite siempre un código de acceso, a menos que el dispositivo esté protegido o tenga el acceso controlado de otra manera (es decir, modo de quiosco que restringe el dispositivo a una aplicación). |
    | **Servicios de ubicación** | Si está habilitado, el Asistente para la configuración solicitará este servicio durante la activación. |
    | **Restaurar** | Si está habilitado, el Asistente para la configuración solicitará una copia de seguridad de iCloud durante la activación. |
    | **iCloud e identificador de Apple** | Si está habilitado, el Asistente para la configuración solicita al usuario que inicie sesión con un identificador de Apple y en la pantalla Aplicaciones y datos se permitirá restaurar el dispositivo a partir de la copia de seguridad de iCloud. |
    | **Términos y condiciones** | Si está habilitado, el Asistente para la configuración solicita a los usuarios que acepten los términos y condiciones de Apple durante la activación. |
    | **Touch ID** | Si está habilitado, el Asistente para la configuración solicitará este servicio durante la activación. |
    | **Apple Pay** | Si está habilitado, el Asistente para la configuración solicitará este servicio durante la activación. |
    | **Zoom** | Si está habilitado, el Asistente para la configuración solicitará este servicio durante la activación. |
    | **Siri** | Si está habilitado, el Asistente para la configuración solicitará este servicio durante la activación. |
    | **Datos de diagnóstico** | Si está habilitado, el Asistente para la configuración solicitará este servicio durante la activación. |

12. Elija **Aceptar**.

13. Para guardar el perfil, elija **Crear**.

## <a name="connect-school-data-sync"></a>Conectar con School Data Sync
(Opcional) Apple School Manager admite la sincronización de datos de lista de clase con Azure Active Directory (AD) mediante Microsoft School Data Sync (SDS). Solo puede sincronizar un token con SDS. Si configura otro token con School Data Sync, SDS se quitará del token que lo tenía anteriormente. Una nueva conexión reemplazará el token actual. Complete los pasos siguientes para usar SDS para sincronizar los datos educativos.

1. En [Intune](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción**.
2. Seleccione un token de Apple School Manager y elija **School Data Sync**.
3. En **School Data Sync**, elija **Permitir**. Esta configuración permite a Intune conectarse con SDS en Office 365.
4. Para habilitar una conexión entre Apple School Manager y Azure AD, elija **Configurar Microsoft School Data Sync**. Obtenga más información sobre [cómo configurar School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
5. Haga clic en **Guardar** > **Aceptar**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos administrados

Ahora que se ha concedido permiso a Intune para administrar los dispositivos de Apple School Manager, puede sincronizar Intune con el servicio de Apple para ver los dispositivos administrados en Intune.

En [Intune](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija un token de la lista > **Dispositivos** > **Sincronizar**. ![Captura de pantalla del nodo Dispositivos del Programa de inscripción seleccionado y el vínculo Sincronizar pulsado.](./media/device-enrollment-program-enroll-ios/image06.png)
  
  Para cumplir con las condiciones de Apple relativas a un tráfico del programa de inscripción aceptable, Intune impone las restricciones siguientes:
  - Una sincronización completa no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune actualiza todos los números de serie de Apple asignados a Intune. Si se intenta efectuar una sincronización completa sin que hayan pasado siete días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.
  - Las solicitudes de sincronización tardan 15 minutos en finalizar. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón **Sincronización** está deshabilitado.
  - Intune sincroniza con Apple los dispositivos nuevos y eliminados cada 24 horas.

>[!NOTE]
>También puede asignar números de serie de Apple School Manager a los perfiles en la hoja **Dispositivos del Programa de inscripción**.

## <a name="assign-a-profile-to-devices"></a>Asignar un perfil a los dispositivos
Los dispositivos de Apple School Manager administrados por Intune deben tener un perfil de inscripción asignado antes de la inscripción.

1. En [Intune](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija un token de la lista.
2. Elija **Dispositivos** > Elija los dispositivos de la lista > **Asignar perfil**.
3. En **Asignar perfil**, elija un perfil para los dispositivos y después seleccione **Asignar**.

## <a name="distribute-devices-to-users"></a>Distribuir los dispositivos a los usuarios

Ha habilitado la administración y sincronización entre Apple e Intune, y ha asignado un perfil para permitir que sus dispositivos de Apple School se inscriban. Ahora puede distribuir los dispositivos a los usuarios. Cuando se activa un dispositivo iOS en Apple School Manager, se inscribe para que Intune lo administre. Si el dispositivo se ha activado y está en uso, el perfil no se aplicará hasta que el dispositivo se restablezca a sus valores de fábrica.
