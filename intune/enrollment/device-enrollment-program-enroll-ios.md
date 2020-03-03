---
title: 'Inscripción de dispositivos iOS/iPadOS: Programa de inscripción de dispositivos'
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos iOS/iPadOS corporativos con el Programa de inscripción de dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: adca40b558a75d2c080fe453218f232a37b21daa
ms.sourcegitcommit: cd90650c339795d44702e9dcd0b9679a7b438bb2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473757"
---
# <a name="automatically-enroll-iosipados-devices-with-apples-device-enrollment-program"></a>Inscripción automática de dispositivos iOS/iPadOS con el Programa de inscripción de dispositivos de Apple

Puede configurar Intune para inscribir dispositivos iOS/iPadOS adquiridos mediante el [Programa de inscripción de dispositivos (DEP)](https://deploy.apple.com) de Apple. DEP permite inscribir una gran cantidad de dispositivos sin siquiera tocarlos. Los dispositivos como iPhone, iPad y MacBook se pueden enviar directamente a los usuarios. Cuando el usuario activa el dispositivo, se ejecuta el Asistente para la instalación, que incluye la típica experiencia predeterminada de los productos de Apple, con opciones preconfiguradas, y el dispositivo se inscribe en la administración.

Para habilitar la inscripción de DEP, se pueden usar los portales de Intune, Apple Business Manager (ABM) o Apple School Manager (ASM). Se necesita una lista de números de serie o un número de pedido de compra, de manera que pueda asignar dispositivos a Intune para la administración en ABM/ASM. Puede crear perfiles de inscripción de DEP en Intune que contengan opciones que se apliquen a los dispositivos durante la inscripción. Tenga en cuenta que la inscripción de DEP no se puede usar con una cuenta de [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).

> [!NOTE]
> DEP establece configuraciones de dispositivo que el usuario final no puede necesariamente quitar. Por lo tanto, antes de [migrar a DEP](../fundamentals/migration-guide-considerations.md), el dispositivo debe borrarse para devolverlo a su estado predeterminado (nuevo).

## <a name="dep-and-the-company-portal"></a>DEP y el Portal de empresa

Las inscripciones de DEP no son compatibles con la versión de App Store de la aplicación Portal de empresa. Puede conceder acceso a los usuarios a la aplicación Portal de empresa en un dispositivo DEP. Le recomendamos que proporcione este acceso para que los usuarios puedan elegir qué aplicaciones corporativas quieren usar en el dispositivo o para usar la autenticación moderna para completar el proceso de inscripción. 

Para habilitar la autenticación moderna durante la inscripción, inserte la aplicación en el dispositivo con **Instalar Portal de empresa con VPP** (Programa de compras por volumen) en el perfil de DEP. Para más información, vea [Inscripción automática de dispositivos iOS/iPadOS con el Programa de inscripción de dispositivos de Apple](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

Para permitir que el Portal de empresa se actualice automáticamente y proporcione la aplicación Portal de empresa en los dispositivos ya inscritos con DEP, implemente la aplicación Portal de empresa a través de Intune como una aplicación de Programa de compras por volumen (VPP) necesaria con una [directiva de Configuración de aplicación](../apps/app-configuration-policies-use-ios.md) aplicada.

## <a name="what-is-supervised-mode"></a>¿Qué es el modo de supervisión?

Apple introdujo el modo supervisado en iOS/iPadOS 5. Un dispositivo iOS/iPadOS en modo supervisado se puede administrar con más controles, como el de bloquear la captura de pantalla e impedir la instalación de aplicaciones de App Store. Por lo tanto, resulta especialmente útil para los dispositivos corporativos. Intune admite la configuración de dispositivos en el modo de supervisión como parte del Programa de inscripción de dispositivos (DEP) de Apple.

La compatibilidad con dispositivos DEP no supervisados entró en desuso en iOS/iPadOS 11. En iOS/iPadOS 11 y versiones posteriores, siempre se deben supervisar los dispositivos configurados por DEP. La marca DEP is_supervised se omitirá en una versión de iOS/iPadOS futura.

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
- [Autoridad de Administración de dispositivos móviles (MDM)](../fundamentals/mdm-authority-set.md)
- [Certificado push MDM de Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obtener un token de DEP de Apple

Antes de poder inscribir dispositivos iOS/iPadOS con DEP, necesita un archivo de token de DEP (.p7m) de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos de DEP. También permite a Intune cargar perfiles de inscripción en Apple y asignar dispositivos a esos perfiles.

Use el portal de Apple Business Manager o Apple School Manager para crear un token. También puede usar el portal de ABM/ASM para asignar dispositivos a Intune para su administración.

> [!NOTE]
> Si elimina el token desde el portal clásico de Intune antes de realizar la migración a Azure, Intune podría restaurar un token de DEP de Apple eliminado. Puede volver a eliminar el token de DEP desde Azure Portal.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Paso 1. Descargue el certificado de clave pública de Intune necesario para crear el token.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tokens del programa de inscripción** > **Agregar**.

    ![Obtenga un token del programa de inscripción.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Conceda a Microsoft permiso para enviar información de usuario y dispositivo a Apple al seleccionar **Acepto**.

> [!NOTE]
> Una vez que haya superado el paso 2 para descargar el certificado de clave pública de Intune, no cierre el asistente ni salga de esta página. Si lo hace, el certificado que ha descargado se invalidará y tendrá que repetir este proceso. Si se produce esta situación, normalmente observará que el botón Crear de la pestaña Revisar y crear está atenuado y no puede completar el proceso.

   ![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo de Certificados de Apple para descargar la clave pública.](./media/device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Seleccione **Descargar la clave pública** para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Paso 2. Use la clave para descargar un token de Apple.

1. Seleccione **Crear un token mediante el Programa de inscripción de dispositivos de Apple** para abrir el portal de Programas de implementación de Apple e iniciar sesión con su id. de Apple de la empresa. Puede usar este id. de Apple para renovar el token de DEP.
2. En el [portal Programas de implementación](https://deploy.apple.com) de Apple, seleccione **Introducción** para **Programa de inscripción de dispositivos**.

3. En la página **Administrar servidores**, pulse **Add MDM Server** (Agregar servidor de MDM).
4. Escriba el **nombre del servidor MDM** y, después, elija **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

5. Se abre el cuadro de diálogo **Agregar&lt;Nombre del servidor&gt;** , indicando **Cargar la clave pública**. Seleccione **Elegir archivo…** para cargar el archivo .pem y, después, elija **Siguiente**.

6. Vaya a **Programas de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **Administrar dispositivos**.
7. En **Elegir dispositivos por**, especifique cómo se identifican los dispositivos:
    - **Número de serie**
    - **Número de pedido**
    - **Cargar archivo CSV**.

   ![Captura de pantalla sobre cómo especificar Elegir dispositivos por número de serie, estableciendo Elegir acción como Asignar al servidor y seleccionando el nombre de servidor.](./media/device-enrollment-program-enroll-ios/enrollment-program-token-specify-serial.png)

8. En **Elegir acción**, pulse **Asignar al servidor**, seleccione el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y pulse **Aceptar**. El portal de Apple asigna los dispositivos especificados al servidor de Intune para la administración y, después, muestra **Asignación completa**.

   En el portal de Apple, vaya a **Programas de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **View Assignment History (Ver historial de asignaciones)** para ver una lista de dispositivos y su asignación de servidor MDM.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Paso 3. Guarde el identificador de Apple usado para crear este token.

En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), proporcione el identificador de Apple como referencia futura.

![Captura de pantalla sobre cómo especificar el identificador de Apple que se ha usado para crear y buscar el token del Programa de inscripción.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token-and-choose-scope-tags"></a>Paso 4. Cargue el token y elija etiquetas de ámbito.

1. En el cuadro **Token de Apple**, vaya al archivo de certificado (.pem) y elija **Abrir**.
2. Si quiere aplicar [etiquetas de ámbito](../fundamentals/scope-tags.md) en este token de DEP, elija **Ámbito (etiquetas)** y seleccione las etiquetas de ámbito que quiera. Los perfiles y dispositivos agregados a este token heredarán las etiquetas de ámbito aplicadas a un token.
3. Elija **Crear**.

Con el certificado push, Intune puede inscribir y administrar dispositivos iOS/iPadOS insertando la directiva en los dispositivos móviles inscritos. Intune se sincroniza automáticamente con Apple para ver la cuenta del programa de inscripción.

## <a name="create-an-apple-enrollment-profile"></a>Creación de un perfil de inscripción de Apple

Ahora que ha instalado el token, puede crear un perfil de inscripción para dispositivos de DEP. Un perfil de inscripción de dispositivos define la configuración que se aplica a un grupo de dispositivos durante la inscripción. Hay un límite de 100 perfiles de inscripción por token de DEP.

> [!NOTE]
> Los dispositivos se bloquean si no hay suficientes licencias de Portal de empresa para un token VPP o si el token ha expirado. Intune muestra una alerta cuando un token está a punto de expirar o las licencias están a punto de terminar.
 

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tokens del programa de inscripción**.
2. Seleccione un token, elija **Perfiles** > **Crear perfil** > **iOS.**

    ![Cree una captura de pantalla del perfil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. En la página **Básico**, escriba la información pertinente en **Nombre** y **Descripción** para el perfil con fines administrativos. Los usuarios no ven estos detalles. Puede usar este campo de **nombre** para crear un grupo dinámico en Azure Active Directory. Use el nombre de perfil para definir el parámetro enrollmentProfileName para asignar dispositivos con este perfil de inscripción. Obtenga más información sobre los [grupos dinámicos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices).

    ![Nombre y descripción del perfil.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Seleccione **Siguiente: Configuración de administración de dispositivos**.

5. En **Afinidad de usuario**, elija si los dispositivos con este perfil deben inscribirse con o sin un usuario asignado.
    - **Inscribir con afinidad de usuario**: seleccione esta opción para dispositivos que pertenezcan a usuarios y necesiten usar el Portal de empresa para hacer uso de servicios, como instalar aplicaciones. Si se usa ADFS y el perfil de inscripción tiene **Autenticar con el Portal de empresa en lugar del Asistente de configuración** está establecido en **No**, se requiere [Punto de conexión mixto/nombre de usuario de WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints)[Más información](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Inscribir sin afinidad de usuario**: seleccione esta opción para dispositivos no afiliados con un usuario único. Use esta opción para los dispositivos que no tengan acceso a los datos de usuario local. Las aplicaciones como la aplicación de portal de empresa no funcionan.

5. Si elige **Inscribir con afinidad de usuario**, puede permitir que los usuarios se autentiquen en el Portal de empresa en lugar de con el Asistente de configuración de Apple.

    ![Autenticación con el portal de empresa.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Si desea realizar una de las siguientes acciones, establezca **Seleccionar dónde deben autenticarse los usuarios**  autenticarse en **Portal de empresa**.
    >    - usar la autenticación multifactor
    >    - pedir a los usuarios que cambien su contraseña cuando inician sesión por primera vez
    >    - pedir a los usuarios que restablezcan las contraseñas expiradas durante la inscripción
    >
    > Estas operaciones no se admiten durante la autenticación con el asistente para configuración de Apple.

6. Si elige **Portal de empresa** para **Seleccionar dónde deben autenticarse los usuarios**, puede usar un token de VPP para instalar automáticamente el Portal de empresa en el dispositivo. En este caso, el usuario no tiene que proporcionar un id. de Apple. Para instalar Portal de empresa con un token de VPP, elija un token en **Instalar Portal de empresa con VPP**. Requiere que el Portal de empresa ya se haya agregado al token de VPP. Para asegurarse de que la aplicación Portal de empresa se sigue actualizando después de la inscripción, asegúrese de que ha configurado una implementación de aplicaciones en Intune (Intune>Aplicaciones cliente). Para que no sea necesaria la interacción del usuario, lo más probable es que quiera tener el Portal de empresa como una aplicación de VPP de iOS/iPadOS, convertirlo en una aplicación requerida y usar la licencia de dispositivo para la asignación. Asegúrese de que el token no expire y de que disponga de suficientes licencias de dispositivos para la aplicación Portal de empresa. Si el token expira o se agotan las licencias, Intune instala Portal de empresa de App Store y solicita un id. de Apple. 

    > [!NOTE]
    > Cuando **Seleccionar dónde deben autenticarse los usuarios**  se establezca en **Portal de empresa**, asegúrese de que el proceso de inscripción de los dispositivos se realiza en las primeras 24 horas del Portal de empresa que se descarga en el dispositivo DEP. De lo contrario, podría producirse un error en la inscripción y se necesitará un restablecimiento de fábrica para inscribir el dispositivo.
    
    ![Captura de pantalla de la instalación de Portal de empresa con VPP.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Si seleccionó **Asistente de configuración** para **Seleccionar dónde deben autenticarse los usuarios** , pero también quiere usar el acceso condicional o implementar aplicaciones de empresa en los dispositivos, debe instalar Portal de empresa en el dispositivos. Para ello, elija **Sí** para **Instalar Portal de empresa**.  Si desea que los usuarios reciban el Portal de empresa sin tener que autenticarse en la tienda de aplicaciones, elija **Instalar Portal de empresa con VPP**  y seleccione un token de VPP. Asegúrese de que el token no expire y de que disponga de suficientes licencias de dispositivos para que la aplicación Portal de empresa se implemente correctamente.

8. Si ha elegido un token para **Instalar Portal de empresa con VPP**, puede bloquear el dispositivo en modo Una aplicación (en concreto, la aplicación Portal de empresa) inmediatamente después de que finalice el Asistente de configuración. Haga clic en **Sí** en **Run Company Portal in Single App Mode until authentication** (Ejecutar el Portal de empresa en el modo de aplicación única hasta la autenticación) para establecer esta opción. Para usar el dispositivo, primero el usuario debe autenticarse iniciando sesión con el Portal de empresa.

    No se admite la autenticación multifactor en un único dispositivo bloqueado en modo Una aplicación. Esta limitación existe porque el dispositivo no puede cambiar a otra aplicación para completar el segundo factor de autenticación. Por lo tanto, si desea autenticación multifactor en un dispositivo de modo Una aplicación, el segundo factor debe estar en un dispositivo diferente.

    Esta característica solo es compatible con iOS/iPadOS 11.3.1 y versiones posteriores.

   ![Captura de pantalla del modo de aplicación única.](./media/device-enrollment-program-enroll-ios/single-app-mode.png)

9. Si desea que los dispositivos que usan este perfil se supervisen, elija **Sí** para **Supervisado**.

    ![Captura de pantalla de Configuración de administración de dispositivos.](./media/device-enrollment-program-enroll-ios/supervisedmode.png)

    Los dispositivos **supervisados** ofrecen más opciones de administración y, en este caso, el bloqueo de activación está deshabilitado de forma predeterminada. Microsoft recomienda usar el Programa de inscripción de dispositivos como mecanismo para habilitar el modo de supervisión, sobre todo si se implementa un gran número de dispositivos iOS/iPadOS.

    Los usuarios reciben notificaciones de que sus dispositivos están supervisados de dos maneras:

   - En la pantalla de bloqueo aparece: "This iPhone is managed by Contoso" (Contoso administra este iPhone).
   - En la pantalla **Configuración** > **General** > **Acerca de** aparece: "This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device" (Este iPhone está supervisado. Contoso puede supervisar el tráfico de Internet y localizar este dispositivo)

     > [!NOTE]
     > Un dispositivo inscrito sin supervisión solo puede restablecerse a supervisado con Apple Configurator. Para restablecer el dispositivo de esta forma, es necesario conectar un dispositivo iOS/iPadOS a un Mac con un cable USB. Obtenga más información en los documentos de [Apple Configurator](http://help.apple.com/configurator/mac/2.3).

10. Elija si desea que la inscripción de dispositivos esté bloqueada con este perfil. **Inscripción bloqueada** deshabilita la configuración de iOS/iPadOS que permite que el perfil de administración se quite del menú **Configuración**. Tras la inscripción del dispositivo, no se puede cambiar esta configuración sin borrar dicho dispositivo. Estos dispositivos deben tener el modo de administración **supervisado** definido en *Sí*. 

11. Elija si desea que los dispositivos que usan este perfil se puedan **sincronizar con equipos**. Si elige **Permitir Apple Configurator mediante certificado**, debe seleccionar un certificado en **Certificado de Apple Configurator**.

12. Si selecciona **Permitir Apple Configurator mediante certificado** en el paso anterior, elija un certificado de Apple Configurator para importarlo.

13. Puede especificar un formato de nombres para los dispositivos que se aplique automáticamente cuando se inscriban y en cada protección sucesiva. Para crear una plantilla de nombres, seleccione **Sí** en **Aplicar plantilla de nombre de dispositivo**. A continuación, en el cuadro **Device Name Template** (Plantilla de nombre de dispositivo), escriba la plantilla que se usará para los nombres que usan este perfil. Puede especificar un formato de plantilla que incluya el tipo de dispositivo y el número de serie. 

14. Seleccione **Siguiente: Personalización del Asistente de configuración**.

15. En la página **Personalización del Asistente de configuración**, configure la siguiente configuración de perfil: ![Personalización del Asistente de configuración.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Configuración de departamento | Descripción |
    |---|---|
    | <strong>Nombre de departamento</strong> | Aparece cuando los usuarios pulsan <strong>Acerca de la configuración</strong> durante la activación. |
    |    <strong>Teléfono del departamento</strong>     | Aparece cuando el usuario hace clic en el botón <strong>Necesito ayuda</strong> durante la activación. |

    Puede ocultar las pantallas del Asistente de configuración en el dispositivo durante la configuración del usuario.
    - Si elige **Ocultar**, la pantalla no se mostrará durante la configuración. Después de configurar el dispositivo, el usuario seguirá teniendo la posibilidad de ir al menú **Ajustes** para configurar la característica.
    - Si elige **Mostrar**, la pantalla se mostrará durante la configuración. A veces, el usuario puede omitir la pantalla sin realizar ninguna acción. Sin embargo, posteriormente podrá ir al menú **Ajustes** del dispositivo para configurar la característica. 


    | Configuración de pantallas del asistente | Si elige **Mostrar**, durante la configuración se producirá lo siguiente en el dispositivo: |
    |------------------------------------------|------------------------------------------|
    | <strong>Código de acceso</strong> | Se solicitará un código de acceso al usuario. Solicite siempre un código de acceso para dispositivos no protegidos a menos que el acceso esté controlado de otra manera (como el modo de quiosco que restringe el dispositivo a una aplicación). |
    | <strong>Servicios de ubicación</strong> | Se solicitará la ubicación del usuario. |
    | <strong>Restaurar</strong> | Se mostrará la pantalla Aplicaciones y datos. En esta pantalla el usuario tendrá la opción de restaurar o transferir datos de una copia de seguridad de iCloud al configurar el dispositivo. |
    | <strong>iCloud e identificador de Apple</strong> | El usuario tendrá la opción de iniciar sesión con su id. de Apple y usar iCloud.                         |
    | <strong>Términos y condiciones</strong> | El usuario deberá aceptar los términos y condiciones de Apple. |
    | <strong>Touch ID</strong> | El usuario tendrá la opción de configurar una identificación con huella digital para el dispositivo. |
    | <strong>Apple Pay</strong> | El usuario tendrá la opción de configurar Apple Pay en el dispositivo. |
    | <strong>Zoom</strong> | El usuario tendrá la opción de ampliar el contenido de la pantalla al configurar el dispositivo. |
    | <strong>Siri</strong> | El usuario tendrá la opción de configurar Siri. |
    | <strong>Datos de diagnóstico</strong> | Se mostrará la pantalla Diagnóstico al usuario. En esta pantalla el usuario podrá enviar datos de diagnóstico a Apple. |
    | <strong>Tono de visualización</strong> | El usuario tendrá la opción de configurar el tono de visualización. |
    | <strong>Privacidad</strong> | Se mostrará la pantalla Privacidad al usuario. |
    | <strong>Migración de Android</strong> | El usuario tendrá la opción de migrar datos de un dispositivo Android. |
    | <strong>iMessage y FaceTime</strong> | El usuario tendrá la opción de configurar iMessage y FaceTime. |
    | <strong>Incorporación</strong> | Se mostrarán las pantallas de información de incorporación, como la portada, la multitarea y el centro de control, para informar al usuario. |
    | <strong>Migración de Watch</strong> | El usuario tendrá la opción de migrar los datos de un dispositivo Watch. |
    | <strong>Tiempo de pantalla</strong> | Se mostrará la pantalla Tiempo de pantalla. |
    | <strong>Actualización de software</strong> | Se mostrará la pantalla de actualización de software obligatoria. |
    | <strong>Configuración de SIM</strong> | El usuario tendrá la opción de agregar un plan de datos móviles. |
    | <strong>Aspecto</strong> | Se mostrará la pantalla Aspecto al usuario. |
    | <strong>Express Language</strong> (Idioma rápido)| Se mostrará la pantalla Express Language (Idioma rápido) al usuario. |
    | <strong>Idioma preferido</strong> | El usuario tendrá la opción de elegir su **Idioma preferido**. |
    | <strong>Device to Device Migration</strong> (Migración entre dispositivos) | El usuario tendrá la opción de migrar los datos de un dispositivo antiguo a este dispositivo.|
    

16. Elija **Siguiente** para ir a la página **Revisar y crear**.

17. Para guardar el perfil, elija **Crear**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos administrados
Ahora que Intune tiene permiso para administrar los dispositivos, puede sincronizar Intune con Apple para ver los dispositivos administrados en Intune en Azure Portal.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tokens del programa de inscripción** > seleccione un token de la lista > **Dispositivos** > **Sincronizar**. ![Captura de pantalla del nodo Dispositivos del Programa de inscripción seleccionado y el vínculo Sincronizar.](./media/device-enrollment-program-enroll-ios/image06.png)

   Para cumplir con los términos de Apple relativos a un tráfico del programa de inscripción aceptable, Intune impone las restricciones siguientes:
   - Una sincronización completa no se puede ejecutar más de una vez cada siete días. Durante una sincronización completa, Intune captura la lista actualizada completa de números de serie asignados al servidor MDM de Apple conectado a Intune. Si se elimina un dispositivo de DEP del portal de Intune, se debe cancelar la asignación del servidor MDM de Apple en el portal de DEP. Si la asignación no se ha cancelado, no se volverá a importar a Intune hasta que se ejecute la sincronización completa.   
   - Una sincronización se ejecuta automáticamente cada 24 horas. También puede sincronizar haciendo clic en el botón **Sincronizar** (no más de una vez cada 15 minutos). Todas las solicitudes de sincronización tardan 15 minutos en finalizar. El botón **Sincronizar** queda deshabilitado hasta que se completa la sincronización. Esta sincronización actualizará el estado del dispositivo existente e importará nuevos dispositivos asignados al servidor MDM de Apple.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Asignar un perfil de inscripción a los dispositivos
Debe asignar un perfil del Programa de inscripción a los dispositivos para poder inscribirlos.

>[!NOTE]
>También puede asignar números de serie a perfiles en la hoja **Números de serie de Apple**.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tokens del programa de inscripción** y elija su token de la lista.
2. Elija **Dispositivos** > Elija los dispositivos de la lista > **Asignar perfil**.
3. En **Asignar perfil**, elija un perfil para los dispositivos y seleccione **Asignar**.

### <a name="assign-a-default-profile"></a>Asignación de un perfil predeterminado

Puede elegir un perfil predeterminado para aplicarlo a todos los dispositivos que se inscriben en un token específico.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tokens del programa de inscripción** y elija su token de la lista.
2. Elija **Establecer perfil predeterminado**, seleccione un perfil en la lista desplegable y después seleccione **Guardar**. Este perfil se aplicará a todos los dispositivos que se inscriben en el token.

## <a name="distribute-devices"></a>Distribución de los dispositivos
Ha habilitado la administración y sincronización entre Apple e Intune, y ha asignado un perfil para permitir que sus dispositivos de DEP se inscriban. Ahora puede distribuir los dispositivos a los usuarios. Los dispositivos con afinidad de usuario necesitan que a cada usuario se le asigne una licencia de Intune. Los dispositivos sin afinidad de usuario necesitan una licencia de dispositivo. Un dispositivo activado no puede aplicar un perfil de inscripción hasta que se haya borrado.

Vea [Inscribir el dispositivo iOS/iPadOS en Intune con el Programa de inscripción de dispositivos](/intune-user-help/enroll-your-device-dep-ios).

## <a name="renew-a-dep-token"></a>Renovación del token de DEP  
1. Vaya a deploy.apple.com.  
2. En **Administrar servidores**, elija el servidor MDM asociado con el archivo de token que desea renovar.
3. Elija **Generar nuevo token**.

    ![Captura de pantalla de Generar nuevo token.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Elija **Su token de servidor**.  
5. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **iOS** > **Inscripción de iOS** > **Tokens del programa de inscripción** y elija el token.
    ![Captura de pantalla de Tokens del programa de inscripción.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Elija **Renovar token** y escriba el identificador de Apple usado para crear el token original.  
    ![Captura de pantalla de Generar nuevo token.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Cargue el token recién descargado.  
9. Elija **Renovar token**. Verá la confirmación de que el token se renovó.   
    ![Captura de pantalla de confirmación.](./media/device-enrollment-program-enroll-ios/confirmation.png)
