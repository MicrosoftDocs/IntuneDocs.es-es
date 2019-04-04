---
title: 'Tutorial: Uso del Programa de inscripción de dispositivos para inscribir dispositivos iOS en Intune'
titleSuffix: Microsoft Intune
description: En este tutorial, configurará DEP de Apple para inscribir dispositivos iOS en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9cd0eec492f5131e4015aa64eccb4c081c663ee
ms.sourcegitcommit: 8e6f4acb592dbe5de63aa7642ee9487288740714
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2019
ms.locfileid: "58646478"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>Tutorial: Uso del Programa de inscripción de dispositivos para inscribir dispositivos iOS en Intune
El Programa de inscripción de dispositivos (DEP) de Apple simplifica la inscripción de dispositivos. Con Microsoft Intune y DEP, los dispositivos se inscriben de forma automática la primera vez que el usuario activa el dispositivo. Por tanto, puede proporcionar dispositivos a muchos usuarios sin tener que configurar cada uno de forma individual. 

En este tutorial, aprenderá a:
> [!div class="checklist"]
> * Obtener un token de DEP de Apple
> * Crear un grupo de dispositivos Autopilot
> * Crear un perfil de implementación de Autopilot
> * Asignar el perfil de implementación de Autopilot al grupo de dispositivos
> * Distribuir los dispositivos Windows a los usuarios

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos
- Dispositivos adquiridos en el [Programa de inscripción de dispositivos de Apple](http://deploy.apple.com)
- Establecer la [entidad de administración de dispositivos móviles](mdm-authority-set.md)
- Obtener un [certificado push MDM de Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obtener un token de DEP de Apple
Antes de inscribir dispositivos iOS con DEP, necesita un archivo (.pem) de token de DEP de Apple. Este token permite a Intune sincronizar información sobre dispositivos corporativos de DEP. También permite a Intune cargar perfiles de inscripción en Apple y asignar dispositivos a esos perfiles.

Use el portal de DEP de Apple para crear un token de DEP. También puede usar el portal de DEP para asignar dispositivos a Intune para la administración.

1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > **Agregar**.

2. Conceda a Microsoft permiso para enviar información de usuario y dispositivo a Apple al seleccionar **Acepto**.

   ![Captura de pantalla del panel Token del Programa de inscripción en el área de trabajo de Certificados de Apple para descargar la clave pública.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Seleccione **Descargar la clave pública** para descargar y guardar localmente el archivo de la clave de cifrado (.pem). El archivo .pem se usa para solicitar un certificado de relación de confianza en el portal del Programa de Inscripción de Dispositivos de Apple.

4. Seleccione **Crear un token mediante el Programa de inscripción de dispositivos de Apple** para abrir el portal de Programas de implementación de Apple e iniciar sesión con su id. de Apple de la empresa. Puede usar este id. de Apple para renovar el token de DEP.

5.  En el [portal Programas de implementación](https://deploy.apple.com) de Apple, seleccione **Introducción** para **Programa de inscripción de dispositivos**.

4. En la página **Administrar servidores**, pulse **Add MDM Server** (Agregar servidor de MDM).

5. En **Nombre del servidor de MDM**, escriba *TestMDMServer* y, después, haga clic en **Siguiente**. El nombre del servidor es su referencia para identificar el servidor de administración de dispositivos móviles (MDM). No es el nombre ni la dirección URL del servidor de Microsoft Intune.

6. Se abre el cuadro de diálogo **Agregar&lt;Nombre del servidor&gt;**, indicando **Cargar la clave pública**. Seleccione **Elegir archivo…** para cargar el archivo .pem y, después, elija **Siguiente**.

6. Vaya a **Programas de implementación** > **Programa de inscripción de dispositivos** > **Administrar dispositivos**.
7. En **Elegir dispositivos por**, seleccione **Número de serie**. <!--ask Tiffany about this-->

8. En **Elegir acción**, pulse **Asignar al servidor**, seleccione el &lt;NombreDeServidor&gt; especificado para Microsoft Intune y pulse **Aceptar**. El portal de Apple asigna los dispositivos especificados al servidor de Intune para la administración y, después, muestra **Asignación completa**.

   En el portal de Apple, vaya a **Programas de implementación** &gt; **Programa de inscripción de dispositivos** &gt; **View Assignment History** (Ver historial de asignaciones) para ver una lista de dispositivos y su asignación de servidor MDM.

9. Para futuras referencias, en Intune en Azure Portal, proporcione el id. de Apple que ha usado para crear este token.

    ![Captura de pantalla sobre cómo especificar el identificador de Apple que se ha usado para crear y buscar el token del Programa de inscripción.](./media/device-enrollment-program-enroll-ios/image03.png)

10. En el cuadro **Token de Apple**, vaya al archivo de certificado (.pem), seleccione **Abrir** y después **Crear**. 

## <a name="create-an-apple-enrollment-profile"></a>Creación de un perfil de inscripción de Apple
Ahora que ha instalado el token, puede crear un perfil de inscripción para dispositivos de DEP. Un perfil de inscripción de dispositivos define la configuración que se aplica a un grupo de dispositivos durante la inscripción.

1. En Intune en Azure Portal, elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción**.

2. Haga clic en el token que acaba de instalar y seleccione **Perfiles** > **Crear perfil**.

3. En **Crear perfil**, escriba *TestDEPProfile* en **Nombre** y *Prueba de DEP para dispositivos iOS* en **Descripción** . Los usuarios no ven estos detalles.

4. En **Afinidad de usuario**, seleccione **Inscribir con afinidad de usuario**. Esta opción es para los dispositivos que pertenecen a usuarios que quieren usar el Portal de empresa para servicios como la instalación de aplicaciones.

5. Seleccione **No** en **Autenticar con el Portal de empresa en lugar del Asistente de configuración de Apple**.

6. Seleccione **Configuración de administración de dispositivos** y elija **No** en **Supervisado**. Los dispositivos supervisados ofrecen más opciones de administración, pero no se usarán para los fines de este tutorial.

7. Elija **Aceptar**.

8. Haga clic en **Personalización del Asistente de configuración** y escriba *Departamento Tutorial* en **Nombre de departamento**. Esta cadena es lo que los usuarios verán cuando pulsen **Acerca de la configuración** durante la activación del dispositivo.

9. En **Teléfono del departamento**, escriba un número de teléfono. Este número aparece cuando los usuarios pulsan el botón **Necesito ayuda** durante la activación.

10. También puede **Mostrar** u **ocultar** diversas pantallas durante la activación del dispositivo. Para los fines de este tutorial, establezca **Código de acceso** en **Mostrar** y todas las demás opciones en **Ocultar**.

11. Elija **Aceptar** > **Crear**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos administrados

Ahora puede ver qué dispositivos están asignados a este token.

1. En Intune en Azure Portal, seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija un token de la lista > **Dispositivos** > **Sincronizar**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Asignar un perfil de inscripción a los dispositivos iOS

Debe asignar un perfil del Programa de inscripción a los dispositivos para poder inscribirlos.

1. En Intune en Azure Portal, seleccione **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > Elija el token de la lista.
2. Elija **Dispositivos** > Elija los dispositivos de la lista > **Asignar perfil**.
3. En **Asignar perfil**, elija un perfil para los dispositivos y seleccione **Asignar**.

## <a name="distribute-devices-to-users"></a>Distribuir los dispositivos a los usuarios

Ha configurado la administración y sincronización entre Apple e Intune, y ha asignado un perfil para permitir la inscripción de los dispositivos de DEP. Ahora puede distribuir los dispositivos a los usuarios. Los dispositivos con afinidad de usuario necesitan que a cada usuario se le asigne una licencia de Intune.

## <a name="clean-up-resources"></a>Limpieza de recursos

Si ya no quiere usar más los dispositivos Autopilot, puede eliminarlos.

- Si los dispositivos están inscritos en Intune, antes hay que [eliminarlos del portal de Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>Pasos siguientes

Puede encontrar más información sobre otras opciones disponibles para la inscripción de dispositivos iOS.

> [!div class="nextstepaction"]
> [Artículo exhaustivo sobre la inscripción de DEP de iOS](device-enrollment-program-enroll-ios.md)
