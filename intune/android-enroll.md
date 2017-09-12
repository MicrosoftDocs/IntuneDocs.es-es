---
title: Inscribir dispositivos Android en Intune
titlesuffix: Azure portal
description: "Obtenga información sobre cómo inscribir dispositivos Android en Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ba809003dbdf63377a0b87b747c9865393786d72
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="enroll-android-devices"></a>Inscripción de dispositivos Android

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, este le permite administrar dispositivos Android, incluidos los dispositivos Samsung KNOX Standard. También puede administrar el perfil de trabajo en dispositivos [Android for Work](#enable-enrollment-of-android-for-work-devices).

Intune es compatible ahora con dispositivos que ejecutan Samsung KNOX Standard para la administración de varios usuarios. Esto significa que los usuarios finales pueden iniciar y cerrar sesión en el dispositivo con sus credenciales de Azure AD, y el dispositivo se administra de forma central tanto si está en uso como si no. Cuando los usuarios finales inician sesión, tienen acceso a aplicaciones, además de las directivas aplicadas a ellas. Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación.

## <a name="prerequisite"></a>Requisito previo

Debe establecer la entidad de MDM en **Microsoft Intune** para prepararse para administrar dispositivos móviles. Para obtener instrucciones, consulte [Set the MDM authority](mdm-authority-set.md) (Establecimiento de la autoridad de MDM). Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles.

## <a name="set-up-android-enrollment"></a>Configuración de la inscripción de Android

De manera predeterminada, Intune permite la inscripción de dispositivos Android y Samsung KNOX Standard.

Para bloquear la inscripción de dispositivos Android, o para bloquear solo la de los dispositivos Android de propiedad personal, vea [Set device type restrictions](enrollment-restrictions-set.md) (Establecer restricciones de tipos de dispositivo).

Para habilitar la administración de dispositivos, los usuarios deben inscribir sus dispositivos mediante la descarga de la aplicación del portal de empresa de Intune, que está disponible desde Google Play y, después, abrir la aplicación y seguir las instrucciones para su inscripción. Una vez que los dispositivos Android estén administrados, puede [asignar directivas de cumplimiento](compliance-policy-create-android.md), [administrar aplicaciones](app-management.md), etc.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Habilitación de la inscripción de dispositivos Android for Work

Para habilitar la administración del perfil de trabajo en dispositivos que [admiten Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012), debe agregar un enlace de Android for Work en Intune. Para inscribir dispositivos que admiten Android for Work, pero que anteriormente se han inscrito como dispositivos de Android normal, se debe anular la inscripción de los dispositivos y después volver a inscribirlos.

## <a name="add-android-for-work-binding-for-intune"></a>Adición de un enlace de Android for Work Binding para Intune

1. **Configuración de MDM de Intune**<br>
Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](mdm-authority-set.md) como **Microsoft Intune**.
2. **Configuración del enlace de Android for Work**<br>
    Como administrador de Intune, en Azure Portal, pulse **Más servicios** > **Supervisión y administración** > **Intune**.

    1. En la hoja **Intune**, elija **Inscripción de dispositivos**, > **Inscripción de Android for Work** y haga clic en **Configurar** para abrir el sitio web Android for Work de Google Play. Se abrirá en una nueva pestaña en el explorador.
  ![Captura de pantalla que muestra un vínculo para configurar el enlace de Android for Work](./media/android-work-bind.png)

    2. **Iniciar sesión en Google**<br>
   En la página de inicio de sesión de Google, escriba la cuenta de Google que se asociará con todas las tareas de administración de Android for Work para este inquilino. Se trata de la cuenta de Google que los administradores de TI de su organización compartían para administrar y publicar aplicaciones en la consola de Play for Work.

    3. **Proporcionar detalles de la organización**<br>
   Proporcione el nombre de su empresa en **Nombre de la organización**. Para el **proveedor de administración de Enterprise Mobility (EMM)**, *Microsoft Intune* debe mostrarse. Acepte el acuerdo Android for Work y, después, haga clic en **Confirmar**. La solicitud se procesará.

## <a name="specify-android-for-work-enrollment-settings"></a>Especificación de la configuración de inscripción de Android for Work
   Android for Work solo se admite en determinados dispositivos Android. Consulte los [requisitos de Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") de Google. Cualquier dispositivo que admita Android for Work, también admitirá la administración Android convencional.  Intune le permite especificar cómo se deben administrar los dispositivos que admiten Android for Work:

   - **Administrar todos los dispositivos como Android**: se inscribirán todos los dispositivos Android, incluidos los dispositivos que admiten Android for Work, como dispositivos Android convencionales.
   - **Administrar los dispositivos compatibles como Android for Work**: todos los dispositivos que admiten Android for Work se inscriben como dispositivos Android for Work. Todo dispositivo Android que no admita Android for Work estará inscrito como dispositivo Android convencional.
   - **Manage supported devices for users only in these user groups as Android for Work** (Administrar los dispositivos compatibles para los usuarios únicamente en estos grupos de usuarios como Android for Work): le permite dirigir la administración de Android for Work a un conjunto limitado de usuarios. Solo los miembros de los grupos seleccionados que inscriben un dispositivo que admita Android for Work se inscriben como dispositivos Android for Work. Todos los demás se inscriben como dispositivos Android. Esto resulta útil durante las implementaciones piloto de Android for Work.

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.

Necesitará indicar a sus usuarios finales que vayan a Google Play para descargar la aplicación del portal de empresa de Intune y, después, que abran la aplicación y sigan las indicaciones para inscribir su dispositivo. La aplicación guía a los usuarios a través del proceso de inscripción, explicándoles lo que pueden esperar y lo que pueden y no pueden ver los administradores de TI en sus dispositivos.

También puede enviarles un vínculo sobre los pasos de inscripción en línea: [Inscriba el dispositivo Android en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android).

Para más información acerca de otras tareas de usuario final, consulte estos artículos:

- [Recursos sobre la experiencia del usuario final con Microsoft Intune](end-user-educate.md)
- [Uso de un dispositivo Android con Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Desenlazado de la cuenta administrativa de Android for Work

Puede desactivar la inscripción y administración de Android for Work. Si hace clic en **Desenlazar** en la consola de administración de Intune, se quitan todos los dispositivos inscritos de Android for Work y se quita la relación entre la cuenta de Android for Work e Intune.

### <a name="how-to-unbind-an-android-for-work-account"></a>Cómo desenlazar una cuenta de Android for Work

1. **Eliminación del enlace de Android for Work**<br>
    Como administrador de Intune, en Azure Portal, pulse **Más servicios** > **Supervisión y administración** > **Intune**.  En la hoja **Intune**, elija **Inscripción de dispositivos** > **Inscripción de Android for Work** y haga clic en **Desenlazar**.

2. **Acepte eliminar el enlace de Android for Work**.<br>
  Haga clic en **Sí** para eliminar el enlace y anular la inscripción de todos los dispositivos Android for Work de Intune.
