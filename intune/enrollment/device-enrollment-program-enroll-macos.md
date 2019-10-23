---
title: 'Inscripción de dispositivos macOS: Programa de inscripción de dispositivos o Apple School Manager'
titleSuffix: ''
description: Obtenga información sobre cómo inscribir dispositivos macOS corporativos con el Programa de inscripción de dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85f9c4f0049407dd77e532698d03cc0b71d3e3d1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505523"
---
# <a name="automatically-enroll-macos-devices-with-the-device-enrollment-program-or-apple-school-manager"></a>Inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos o Apple School Manager

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede configurar la inscripción de Intune de los dispositivos macOS adquiridos mediante el [Programa de inscripción de dispositivos (DEP)](https://deploy.apple.com) de Apple o [Apple School Manager](https://school.apple.com/). Puede usar cualquiera de estas inscripciones para un gran número de dispositivos sin siquiera tener que tocarlos. Puede enviar dispositivos macOS directamente a los usuarios. Cuando el usuario activa el dispositivo, se ejecuta el Asistente para la instalación con opciones preconfiguradas y el dispositivo se inscribe en la administración de Intune.

Para configurar la inscripción, use los portales de DEP de Apple y de Intune. Puede crear perfiles de inscripción que contengan opciones que se apliquen a los dispositivos durante la inscripción.

Ni la inscripción de DEP ni Apple School Manager funcionan con el [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Requisitos previos

- Dispositivos adquiridos en [Apple School Manager](https://school.apple.com/) o el [Programa de inscripción de dispositivos de Apple](http://deploy.apple.com)
- Una lista de números de serie o un número de pedido de compra.
- [Entidad de MDM](../fundamentals/mdm-authority-set.md)
- [Certificado push MDM de Apple](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obtener un token de DEP de Apple

Antes de poder inscribir dispositivos macOS con DEP o Apple School Manager, necesita un archivo de token de DEP (.p7m) de Apple. Este token permite a Intune sincronizar información sobre los dispositivos propiedad de su organización. También permite que Intune cargue los perfiles de inscripción en Apple y en estos perfiles a los dispositivos.

Use el portal de Apple para crear un token. También puede usar el portal de Apple para asignar dispositivos a Intune para la administración.

> [!NOTE]
> Si elimina el token desde el portal clásico de Intune antes de realizar la migración a Azure, Intune podría restaurar un token de Apple eliminado. Puede volver a eliminar el token desde Azure Portal.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Paso 1. Descargue el certificado de clave pública de Intune necesario para crear el token.

1. En [Intune, en Azure portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > **Agregar**.

    ![Obtenga un token del programa de inscripción.](./media/device-enrollment-program-enroll-macos/image01.png)

2. Conceda a Microsoft permiso para enviar información de usuario y dispositivo a Apple al seleccionar **Acepto**.

   ![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo de Certificados de Apple para descargar la clave pública.](./media/device-enrollment-program-enroll-macos/add-enrollment-program-token-pane.png)

3. Seleccione **Descargar la clave pública** para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal de Apple.

### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Paso 2. Use la clave para descargar un token de Apple.

1. Seleccione **Crear un token mediante el Programa de inscripción de dispositivos de Apple** o **Crear un token mediante Apple School Manager** para abrir el portal adecuado de Apple e iniciar sesión con su id. de Apple de la empresa. Puede usar este id. de Apple para renovar el token.
2. Para DEP, en el portal de Apple, elija **Empezar** mientras que, para **Programa de inscripción de dispositivos** > **Administrar servidores** > **Agregar servidor de MDM**.
3. Para Apple School Manager, en el portal de Apple, elija **Servidores de MDM** > **Agregar servidor de MDM**.
4. Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

5. Se abre el cuadro de diálogo **Agregar&lt;Nombre del servidor&gt;** , indicando **Cargar la clave pública**. Elija **Elegir archivo...** para cargar el archivo .pem y, después, elija **Siguiente**.

6. Vaya a **Programa de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**.
7. En **Elegir dispositivos por**, especifique cómo se identifican los dispositivos:
    - **Número de serie**
    - **Número de pedido**
    - **Cargar archivo CSV**.

   ![Captura de pantalla sobre cómo especificar Elegir dispositivos por número de serie, estableciendo Elegir acción como Asignar al servidor y seleccionando el nombre de servidor.](./media/device-enrollment-program-enroll-macos/enrollment-program-token-specify-serial.png)

8. En **Elegir acción**, pulse **Asignar al servidor**, seleccione el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y pulse **Aceptar**. El portal de Apple asigna los dispositivos especificados al servidor de Intune para la administración y, después, muestra **Asignación completa**.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Paso 3: Guarde el identificador de Apple usado para crear este token

En Intune en Azure Portal, proporcione el id. de Apple para futuras referencias.

![Captura de pantalla sobre cómo especificar el identificador de Apple que se ha usado para crear y buscar el token del Programa de inscripción.](./media/device-enrollment-program-enroll-macos/image03.png)

### <a name="step-4-upload-your-token"></a>Paso 4. Cargue el token
En el cuadro **Token de Apple**, vaya al archivo de certificado (.pem), seleccione **Abrir** y después **Crear**. Con el certificado push, Intune puede inscribir y administrar dispositivos macOS insertando la directiva en los dispositivos inscritos. Intune se sincroniza automáticamente con Apple para ver la cuenta del programa de inscripción.

## <a name="create-an-apple-enrollment-profile"></a>Creación de un perfil de inscripción de Apple

Ahora que ha instalado el token, puede crear un perfil de inscripción para dispositivos. Un perfil de inscripción de dispositivos define la configuración que se aplica a un grupo de dispositivos durante la inscripción.

1. En Intune en Azure Portal, elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción**.
2. Seleccione un token, elija **Perfiles** y después **Crear perfil**.

    ![Cree una captura de pantalla del perfil.](./media/device-enrollment-program-enroll-macos/image04.png)

3. En **Crear perfil**, escriba un **nombre** y una **descripción** para el perfil con fines administrativos. Los usuarios no ven estos detalles. Puede usar este campo de **nombre** para crear un grupo dinámico en Azure Active Directory. Use el nombre de perfil para definir el parámetro enrollmentProfileName para asignar dispositivos con este perfil de inscripción. Obtenga más información sobre los [grupos dinámicos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices).

    ![Nombre y descripción del perfil.](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. En **Plataforma**, elija **macOS**.

5. En **Afinidad de usuario**, elija si los dispositivos con este perfil deben o no inscribirse con o sin un usuario asignado.
    - **Inscribir con afinidad de usuario**: seleccione esta opción para dispositivos que pertenezcan a usuarios y necesiten usar la aplicación Portal de empresa para hacer uso de servicios, como instalar aplicaciones. Si se usa ADFS, la afinidad de usuario debe ser [Punto de conexión mixto/nombre de usuario de WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Más información](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint). La autenticación multifactor no es compatible con dispositivos DEP macOS con afinidad de usuario.

    - **Inscribir sin afinidad de usuario**: seleccione esta opción para dispositivos no afiliados con un usuario único. Use esta opción para dispositivos que realizan tareas sin tener acceso a datos de usuario local. Las aplicaciones como la aplicación de portal de empresa no funcionan.

6. Elija **Configuración de administración de dispositivos** y elija si desea o no que la inscripción de dispositivos esté bloqueada con este perfil. **Inscripción bloqueada** deshabilita la configuración de macOS que permite que el perfil de administración se quite del menú **Preferencias del sistema** o a través del **Terminal**. Tras la inscripción del dispositivo, no se puede cambiar esta configuración sin borrar el dispositivo.

    ![Captura de pantalla de Configuración de administración de dispositivos.](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)

7. Elija **Aceptar**.

8. Seleccione **Valores del Asistente de configuración** para configurar las siguientes opciones de perfil:  ![Personalización del Asistente de configuración.](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)

    | Configuración de departamento | Descripción |
    |---|---|
    | <strong>Nombre de departamento</strong> | Aparece cuando los usuarios pulsan <strong>Acerca de la configuración</strong> durante la activación. |
    | <strong>Teléfono del departamento</strong> | Aparece cuando el usuario hace clic en el botón <strong>Necesito ayuda</strong> durante la activación. |

    Cuando el usuario configura el dispositivo, es posible mostrar u ocultar varias pantallas del asistente de configuración.
    - Si elige **Ocultar**, la pantalla no se mostrará durante la configuración. Después de configurar el dispositivo, el usuario seguirá teniendo la posibilidad de ir al menú **Ajustes** para configurar la característica.
    - Si elige **Mostrar**, la pantalla se mostrará durante la configuración. A veces, el usuario puede omitir la pantalla sin realizar ninguna acción. Sin embargo, posteriormente podrá ir al menú **Ajustes** del dispositivo para configurar la característica. 

    | Configuración de pantallas del asistente | Si elige **Mostrar**, durante la configuración se producirá lo siguiente en el dispositivo: |
    |------------------------------------------|------------------------------------------|
    | <strong>Código de acceso</strong> | Se solicitará un código de acceso al usuario. Solicite siempre un código de acceso, a menos que el dispositivo esté protegido o tenga el acceso controlado de otra manera (es decir, modo de quiosco que restringe el dispositivo a una aplicación). |
    | <strong>Servicios de ubicación</strong> | Se solicitará la ubicación del usuario. |
    | <strong>Restaurar</strong> | Se mostrará la pantalla Aplicaciones y datos. En esta pantalla el usuario tendrá la opción de restaurar o transferir datos de una copia de seguridad de iCloud al configurar el dispositivo. |
    | <strong>iCloud e identificador de Apple</strong> | El usuario tendrá la opción de iniciar sesión con su **ID de Apple** y usar **iCloud**.                         |
    | <strong>Términos y condiciones</strong> | El usuario deberá aceptar los términos y condiciones de Apple. |
    | <strong>Touch ID</strong> | El usuario tendrá la opción de configurar una identificación con huella digital para el dispositivo. |
    | <strong>Apple Pay</strong> | El usuario tendrá la opción de configurar Apple Pay en el dispositivo. |
    | <strong>Zoom</strong> | El usuario tendrá la opción de ampliar el contenido de la pantalla al configurar el dispositivo. |
    | <strong>Siri</strong> | El usuario tendrá la opción de configurar Siri. |
    | <strong>Datos de diagnóstico</strong> | Se mostrará la pantalla Diagnóstico al usuario. En esta pantalla el usuario podrá enviar datos de diagnóstico a Apple. |
    | <strong>FileVault</strong> | Conceda al usuario la opción de configurar el cifrado de FileVault. |
    | <strong>Diagnósticos de iCloud</strong> | Conceda al usuario la opción de enviar datos de diagnóstico de iCloud a Apple. |
    | <strong>Almacenamiento en iCloud</strong> | Ofrezca al usuario la opción de utilizar el almacenamiento en iCloud. |    
    | <strong>Tono de visualización</strong> | El usuario tendrá la opción de configurar el tono de visualización. |
    | <strong>Aspecto</strong> | Se mostrará la pantalla Aspecto al usuario. |
    | <strong>Registro</strong>| Establezca que el usuario registre el dispositivo de manera obligatoria. |
    | <strong>Privacidad</strong>| Se mostrará la pantalla Privacidad al usuario. |
    | <strong>Tiempo de pantalla</strong>| Se mostrará la pantalla Tiempo de pantalla. |

9. Elija **Aceptar**.

10. Para guardar el perfil, elija **Crear**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos administrados

Ahora que Intune tiene permiso para administrar los dispositivos, puede sincronizar Intune con Apple para ver los dispositivos administrados en Intune en Azure Portal.

1. En Intune en Azure Portal, seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija un token de la lista > **Dispositivos** > **Sincronizar**. ![Captura de pantalla del nodo Dispositivos del Programa de inscripción seleccionado y el vínculo Sincronizar pulsado.](./media/device-enrollment-program-enroll-macos/image06.png)

   Para cumplir con las condiciones de Apple relativas a un tráfico del programa de inscripción aceptable, Intune impone las restricciones siguientes:
   - Una sincronización completa no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune captura la lista actualizada completa de números de serie asignados al servidor MDM de Apple conectado a Intune. Tras eliminar un dispositivo del Programa de inscripción desde el portal de Intune sin anular su asignación del servidor MDM de Apple, no se podrá volver a importar hasta que se ejecute la sincronización completa.   
   - Una sincronización se ejecuta automáticamente cada 24 horas. También puede sincronizar haciendo clic en el botón **Sincronizar** (no más de una vez cada 15 minutos). Todas las solicitudes de sincronización tardan 15 minutos en finalizar. El botón **Sincronizar** queda deshabilitado hasta que se completa la sincronización. Esta sincronización actualizará el estado del dispositivo existente e importará nuevos dispositivos asignados al servidor MDM de Apple.

## <a name="assign-an-enrollment-profile-to-devices"></a>Asignar un perfil de inscripción a los dispositivos

Debe asignar un perfil del Programa de inscripción a los dispositivos para poder inscribirlos.

1. En Intune en Azure Portal, seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija un token de la lista.
2. Elija **Dispositivos** > Elija los dispositivos de la lista > **Asignar perfil**.
3. En **Asignar perfil**, elija un perfil para los dispositivos y seleccione **Asignar**.

### <a name="assign-a-default-profile"></a>Asignación de un perfil predeterminado

Puede elegir un perfil de iOS o macOS predeterminado para aplicarlo a todos los dispositivos que se inscriben en un token específico. 

1. En Intune en Azure Portal, elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija un token de la lista.
2. Elija **Establecer perfil predeterminado**, seleccione un perfil en la lista desplegable y después seleccione **Guardar**. Este perfil se aplicará a todos los dispositivos que se inscriben en el token.

## <a name="distribute-devices"></a>Distribuir los dispositivos

Ha habilitado la administración y sincronización entre Apple e Intune, y ha asignado un perfil para permitir que sus dispositivos se inscriban. Ahora puede distribuir los dispositivos a los usuarios. Los dispositivos con afinidad de usuario necesitan que a cada usuario se le asigne una licencia de Intune. Los dispositivos sin afinidad de usuario necesitan una licencia de dispositivo. Un dispositivo activado no puede aplicar un perfil de inscripción hasta que se haya borrado.

## <a name="renew-a-dep-token"></a>Renovación del token de DEP

1. Vaya a deploy.apple.com.  
2. En **Administrar servidores**, elija el servidor MDM asociado con el archivo de token que desea renovar.
3. Elija **Generar nuevo token**.

    ![Captura de pantalla de Generar nuevo token.](./media/device-enrollment-program-enroll-macos/generatenewtoken.png)

4. Elija **Su token de servidor**.  
5. En [Intune en Azure Portal](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > elija el token.
    ![Captura de pantalla de Tokens del programa de inscripción.](./media/device-enrollment-program-enroll-macos/enrollmentprogramtokens.png)

6. Elija **Renovar token** y escriba el identificador de Apple usado para crear el token original.  
    ![Captura de pantalla de Generar nuevo token.](./media/device-enrollment-program-enroll-macos/renewtoken.png)

7. Cargue el token recién descargado.  
8. Elija **Renovar token**. Verá la confirmación de que el token se renovó.
    ![Captura de pantalla de confirmación.](./media/device-enrollment-program-enroll-macos/confirmation.png)

## <a name="next-steps"></a>Pasos siguientes

Después de inscribir dispositivos macOS, puede empezar a [administrarlos](../remote-actions/device-management.md).
