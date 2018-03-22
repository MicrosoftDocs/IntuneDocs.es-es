---
title: Configuración de la inscripción en el programa de Apple School Manager para dispositivos iOS
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo configurar la inscripción en el programa de Apple School Manager para dispositivos iOS corporativos con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d3a599ff1dff3e27214dfcca694f6b97333f370a
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="set-up-ios-device-enrollment-with-apple-school-manager"></a>Configuración de la inscripción de dispositivos iOS con Apple School Manager

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Diferencias temporales de la interfaz de usuario
>
>La actualización de las interfaces de usuario para las características descritas en esta página está en proceso. Estas actualizaciones se implementarán en todas las cuentas de usuario hasta final de abril.
>
>Si la página **Inscripción de dispositivos** es similar a la imagen siguiente, significa que la cuenta no se ha actualizado aún a la nueva interfaz de usuario y puede utilizar esta página de ayuda.
>
>![Antigua interfaz de usuario de Intune](./media/appleenroll-oldui.png)
>
>Si la página **Inscripción de dispositivos** es similar a la imagen siguiente, significa que tiene las interfaces de usuario actualizadas.  Vaya a [esta página de ayuda](apple-school-manager-set-up-ios-newui.md).
>
>![Nueva interfaz de usuario de Intune](./media/appleenroll-newui.png)

En este tema aprenderá a configurar la inscripción de dispositivos iOS adquiridos mediante el programa de [Apple School Manager](https://school.apple.com/). Al usar Intune con Apple School Manager, puede inscribir un gran número de dispositivos iOS sin tener que tocarlos. Cuando un estudiante o profesor activa el dispositivo, se ejecuta el Asistente para la configuración con valores preconfigurados y el dispositivo se inscribe en la administración.

Para habilitar la inscripción de Apple School Manager, se usan los portales de Intune y de Apple School Manager. Se necesita una lista de números de serie o un número de pedido de compra, de manera que pueda asignar dispositivos a Intune para la administración. Puede crear perfiles de inscripción de DEP que contengan opciones que se apliquen a los dispositivos durante la inscripción.

Además, la inscripción de Apple School Manager no se puede usar con el [Programa de inscripción de dispositivos de Apple](device-enrollment-program-enroll-ios.md) ni con el [Administrador de inscripciones de dispositivos](device-enrollment-manager-enroll.md).

**Requisitos previos**
- [Certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- [Entidad de MDM](mdm-authority-set.md)
- [Certificado push MDM de Apple](apple-mdm-push-certificate-get.md)
- Se necesita una afinidad de usuario [Punto de conexión mixto/nombre de usuario de WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Más información](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Los dispositivos tienen que haberse adquirido a través del programa de [Apple School Management](http://school.apple.com)

>[!NOTE]
>Multi-Factor Authentication (MFA) no funciona durante la inscripción en dispositivos Apple School Manager con afinidad de usuario. Después de la inscripción, MFA funciona según lo previsto en estos dispositivos. Después de la inscripción, MFA funciona según lo previsto en los dispositivos. Los dispositivos no pueden pedir a los usuarios que cambien su contraseña cuando inician sesión por primera vez. Además, no se puede pedir a los usuarios cuyas contraseñas hayan expirado que las restablezcan durante la inscripción. Los usuarios deben usar un dispositivo diferente para restablecer la contraseña.

## <a name="get-the-apple-token-and-assign-devices"></a>Obtener el token de Apple y asignar los dispositivos

Antes de poder inscribir dispositivos iOS corporativos en Apple School Manager, necesita un archivo de token (.p7m) de Apple. Este token permite a Intune sincronizar información sobre dispositivos que participan en Apple School Manager. También permite a Intune realizar cargas de perfiles de inscripción a Apple y asignar dispositivos a esos perfiles. En Azure Portal, también puede asignar números de serie a los dispositivos para su administración.

**Paso 1. Descargue un certificado de clave pública de Intune necesario para crear un token de Apple.**<br>
1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** y, después, elija **Token del Programa de inscripción**.

  ![Panel Token del Programa de inscripción en el área de trabajo Certificados de Apple para descargar la clave pública](./media/enrollment-program-token-download.png)

2. En la hoja **Token del Programa de inscripción**, elija **Descargar la clave pública** para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal de Apple School Manager.

**Paso 2. Descargue un token y asigne los dispositivos.**<br>
1. Elija **Crear un token mediante Apple School Manager** e inicie sesión con su ID de Apple empresarial. Puede usar este identificador de Apple para renovar el token de Apple School Manager.
2.  En el [portal de Apple School Manager](https://school.apple.com), vaya a **MDM Servers** (Servidores MDM) y luego elija **Add MDM Server** (Agregar servidor MDM) (en la parte superior derecha).
3.  Escriba el **nombre del servidor de MDM**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.
   ![Portal de Apple School Manager con la opción de número de serie seleccionada](./media/asm-server-assignment.png)

4.  Elija **Upload File...** (Cargar archivo...) en el portal de Apple, examine el archivo .pem y elija **Save MDM Server** (Guardar servidor MDM) (en la parte inferior derecha).
5.  Elija **Get Token** (Obtener token) y luego descargue el archivo de token del servidor (.p7m) en el equipo.
6. Vaya a **Device Assignments** (Asignaciones de dispositivos) y **Choose Device** (Elegir dispositivo) con la entrada manual de **números de serie** o **números de pedido** o con la opción **Upload CSV File** (Cargar archivo CSV).
     ![Portal de Apple School Manager con la opción de número de serie seleccionada](./media/asm-device-assignment.png)
7.  Elija la acción **Assign to Server** (Asignar al servidor) y elija el **servidor MDM** que ha creado.
8. Especifique cómo **Elegir dispositivos**, después proporcione información de los dispositivos y detalles.
9. Elija **Assign to Server** (Asignar al servidor), elija el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y después elija **Aceptar**.

**Paso 3. Escriba el id. de Apple usado para crear el token de Apple School Manager.**<br>Este identificador debe usarse para renovar el token de Apple School Manager y guardarse para futuras referencias.

![Se especifica el ID de Apple que se ha usado para crear y buscar el token del programa de inscripción](./media/enrollment-program-token-apple-id.png)

**Paso 4. Busque y cargue el token.**<br>
Vaya al archivo de certificado (.p7m), elija **Abrir** y luego seleccione **Cargar**. Intune sincroniza automáticamente los dispositivos de Apple School Manager desde Apple.

## <a name="create-an-apple-enrollment-profile"></a>Creación de un perfil de inscripción de Apple
Un perfil de inscripción de dispositivos define la configuración que se aplica a un grupo de dispositivos durante la inscripción.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** y luego **Inscripción de Apple**.
2. En **Programa de inscripción**, elija **Perfiles del Programa de inscripción**.
3. En la hoja **Perfiles del Programa de inscripción**, elija **Crear**.
4. En la hoja **Crear perfil de inscripción**, escriba un **nombre** y una **descripción** para el perfil que se muestra en Intune.
5. En **Afinidad de usuario**, elija si los dispositivos con este perfil se inscribirán con o sin afinidad de usuario.

 - **Inscribir con afinidad de usuario**: asocia el dispositivo con un usuario durante la instalación.

  El modo iPad compartido de Apple School Manager requiere la inscripción del usuario sin afinidad de usuario.

 - **Inscribir sin afinidad de usuario**: seleccione esta opción para dispositivos no afiliados con un usuario único (por ejemplo, dispositivos compartidos). Se usa para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones como la aplicación de portal de empresa no funcionan.

6. Elija **Configuración de administración de dispositivos**. Estos elementos se establecen durante la activación y requieren un restablecimiento de fábrica para los cambios. Configure las siguientes opciones de perfil y, después, elija **Guardar**:

  ![Se elige el modo de administración](./media/enrollment-program-profile-mode.png)

    - **Supervisado**: un modo de administración que permite más opciones de administración y deshabilita el bloqueo de activación de forma predeterminada. Si deja en blanco la casilla, tendrá funcionalidades de administración limitadas.

     - **Inscripción bloqueada** (requiere el modo de administración Supervisado): Deshabilita la configuración de iOS que podría permitir la eliminación del perfil de administración. Si deja en blanco la casilla, permite que se quite el perfil de administración en el menú Configuración.
   - **iPad compartido habilitado** (requiere **Inscribir sin afinidad de usuario** y el modo Supervisado). Permite que varios usuarios inicien sesión en dispositivos iPad inscritos mediante el uso de un identificador de Apple administrado. Los identificadores de Apple administrados se crean en el portal de Apple School Manager. Obtenga más información sobre los dispositivos [iPad compartidos](education-settings-configure-ios-shared.md). También debe revisar los [requisitos para compartir un iPad de Apple](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56).

   >[!NOTE]
   >Si **Afinidad de usuario** se establece en **Con afinidad de usuario** o el modo **Supervisado** se establece en **Desactivado**, el modo iPad compartido está deshabilitado para el perfil de inscripción.

        - **Maximum Cached Users** - (Requires **Shared iPad** = **Yes**) Creates a partition on the device for each user. The recommended value is the number of students likely to use the device over a period of time. For example, if six students use the device regularly during the week, set this number to six.  

    - **Permitir emparejamiento**: especifica si se pueden sincronizar dispositivos iOS con equipos. Si elige **Permitir Apple Configurator mediante certificado**, debe seleccionar un certificado en **Certificado de Apple Configurator**.

      - **Certificados de Apple Configurator**: si ha pulsado **Permitir Apple Configurator mediante certificado** en **Permitir emparejamiento**, seleccione un certificado de Apple Configurator para importar.

7. Elija **Valores del Asistente de configuración**, configure las siguientes opciones de perfil y, después, elija **Guardar**:

    - **Department Name** (Nombre de departamento): aparece cuando los usuarios pulsan **About Configuration** (Acerca de la configuración) durante la activación.

    - **Teléfono del departamento**: aparece cuando el usuario hace clic en el botón Necesito ayuda durante la activación.
    - **Opciones del Asistente para la configuración**: si se excluyen de las opciones del Asistente de configuración, se pueden definir más adelante en el menú **Configuración** de iOS.
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

8. Para guardar la configuración del perfil, seleccione **Crear** en la hoja **Crear perfil de inscripción**.

## <a name="connect-school-data-sync"></a>Conectar con School Data Sync
(Opcional) Apple School Manager admite la sincronización de datos de lista de clase con Azure Active Directory (AD) mediante Microsoft School Data Sync (SDS). Complete los pasos siguientes para usar SDS para sincronizar los datos educativos.

1. En la hoja **Token del Programa de inscripción**, elija el banner informativo azul o **Conectar con SDS**.
2. Elija la opción **Permitir que Microsoft School Data Sync use este token**, establecida en **Permitir**. Esta configuración permite a Intune conectarse con SDS en Office 365.
3. Para habilitar una conexión entre Apple School Manager y Azure AD, elija **Configurar Microsoft School Data Sync**. Obtenga más información sobre [cómo configurar School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
4. Haga clic en **Aceptar** para guardar y continuar.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos administrados
Ahora que se ha concedido permiso a Intune para administrar los dispositivos de Apple School Manager, puede sincronizar Intune con el servicio de Apple para ver los dispositivos administrados en Intune.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Dispositivos del Programa de inscripción** > **Sincronizar**. La barra de progreso muestra la cantidad de tiempo que debe esperar antes de solicitar de nuevo la sincronización.

  ![Se ha seleccionado el nodo Dispositivos del Programa de inscripción y se ha elegido el vínculo Sincronizar](./media/enrollment-program-device-sync.png)
2. En la hoja **Sincronizar**, seleccione **Solicitar sincronización**. La barra de progreso muestra la cantidad de tiempo que debe esperar antes de solicitar de nuevo la sincronización.

  ![Hoja Sincronizar con el vínculo Solicitar sincronización seleccionado](./media/enrollment-program-device-request-sync.png)

  Para cumplir con las condiciones de Apple relativas a un tráfico aceptable, Intune impone las restricciones siguientes:
   -    Una sincronización completa no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune actualiza todos los números de serie que Apple ha asignado a Intune, independientemente de si el número de serie se ha sincronizado previamente o no. Si se intenta efectuar una sincronización completa sin que hayan pasado siete días desde la última sincronización completa, Intune solo actualizará los números de serie que aún no aparezcan en Intune.
   -    Las solicitudes de sincronización tardan 15 minutos en finalizar. Durante este tiempo, o hasta que la solicitud finalice correctamente, el botón **Sincronización** está deshabilitado.

>[!NOTE]
>También puede asignar números de serie de Apple School Manager a los perfiles en la hoja **Dispositivos del Programa de inscripción**.

## <a name="assign-a-profile-to-devices"></a>Asignar un perfil a los dispositivos
Los dispositivos de Apple School Manager administrados por Intune deben tener un perfil de inscripción asignado antes de la inscripción.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Apple** y, después, elija **Perfiles del Programa de inscripción**.
2. En la lista de **Perfiles del Programa de inscripción**, seleccione el perfil que quiere asignar a los dispositivos y, después, seleccione **Device Assignments** (Asignaciones de dispositivos).

 ![Asignaciones de dispositivo con la opción Asignar seleccionada.](./media/enrollment-program-device-assign.png)

3. Elija **Asignar** y, después, elija los dispositivos de Apple School Manager a los que quiere asignar este perfil. Puede filtrar para ver los dispositivos disponibles:
  - **sin asignar**
  - **cualquiera**
  - **&lt;nombre de perfil&gt;**
4. Seleccione los dispositivos que quiere asignar. La casilla que se encuentra encima de la columna selecciona hasta 1000 dispositivos enumerados. Haga clic en **Asignar**. Para inscribir más de 1000 dispositivos, repita los pasos de la asignación hasta que todos los dispositivos tengan un perfil de inscripción asignado.

  ![Botón Asignar para asignar un perfil del programa de inscripción en Intune](media/dep-profile-assignment.png)

## <a name="distribute-devices-to-users"></a>Distribuir los dispositivos a los usuarios

Ahora puede distribuir dispositivos corporativos a los usuarios. Cuando se activa un dispositivo iOS en Apple School Manager, se inscribe para que Intune lo administre. Si el dispositivo se ha activado y está en uso, el perfil no se aplicará hasta que el dispositivo se restablezca a sus valores de fábrica.
