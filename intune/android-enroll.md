---
title: "Inscripción de dispositivos Android en Intune | Microsoft Docs"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo inscribir dispositivos Android en Intune."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 632a5b2a5f6f5188ef034bdcff927af6a7fe1a59
ms.sourcegitcommit: 53d272defd2ec061dfdfdae3668d1b676c8aa7c6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="enroll-android-devices"></a>Inscripción de dispositivos Android

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, puede administrar dispositivos Android, incluidos los dispositivos Samsung Knox Standard. También puede administrar el perfil de trabajo en [dispositivos Android for Work](#enable-enrollment-of-android-for-work-devices).

Intune es compatible ahora con dispositivos que ejecutan Samsung Knox Standard para la administración de varios usuarios. Esto quiere decir que los usuarios pueden iniciar y cerrar sesión en un dispositivo con sus credenciales de Azure AD. El dispositivo se administra de forma centralizada tanto si se usa como si no. Cuando los usuarios inician sesión, tienen acceso a las aplicaciones y, además, se les aplican las directivas. Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación.

## <a name="prerequisite"></a>Requisito previo

Para prepararse para administrar dispositivos móviles, debe establecer la entidad de administración de dispositivos móviles (MDM) en **Microsoft Intune**. Para obtener instrucciones, consulte [Set the MDM authority](mdm-authority-set.md) (Establecimiento de la autoridad de MDM). Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles.

## <a name="set-up-android-enrollment"></a>Configuración de la inscripción de Android

De manera predeterminada, Intune permite la inscripción de dispositivos Android y Samsung KNOX Standard.

Para bloquear la inscripción de dispositivos Android, o para bloquear solo la de los dispositivos Android de propiedad personal, vea [Set device type restrictions](enrollment-restrictions-set.md) (Establecer restricciones de tipos de dispositivo).

Para habilitar la administración de dispositivos, los usuarios deben inscribir sus dispositivos descargando la aplicación del Portal de empresa de Intune (disponible desde Google Play) y, después, abriendo la aplicación y siguiendo las instrucciones para su inscripción. Cuando los dispositivos Android estén administrados, puede [asignar directivas de cumplimiento](compliance-policy-create-android.md), [administrar aplicaciones](app-management.md), etc.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Habilitación de la inscripción de dispositivos Android for Work

Para habilitar la administración del perfil de trabajo en dispositivos que [admiten Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012), debe agregar un enlace de Android for Work en Intune. Para inscribir dispositivos que admiten Android for Work, pero que anteriormente se han inscrito como dispositivos Android normales, debe anular la inscripción de esos dispositivos y volver a inscribirlos.

Si va a inscribir dispositivos Android for Work a través de una cuenta [administrador de inscripciones de dispositivos](device-enrollment-manager-enroll.md), existe un límite de 10 dispositivos que se pueden inscribir por cuenta.

## <a name="add-android-for-work-binding-for-intune"></a>Adición de un enlace de Android for Work para Intune

1. **Configuración de MDM de Intune**<br>
Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](mdm-authority-set.md) como **Microsoft Intune**.
2. **Configuración del enlace de Android for Work**<br>
    Como administrador de Intune, en Azure Portal, pulse **Más servicios** > **Supervisión y administración** > **Intune**.

   a. En la hoja **Intune**, elija **Inscripción de dispositivos** > **Inscripción de Android for Work** y seleccione **Configurar** para abrir el sitio web Android for Work de Google Play. El sitio web se abrirá en una nueva pestaña en el explorador.
   ![Captura de pantalla que muestra un vínculo para configurar el enlace de Android for Work](./media/android-work-bind.png)

   b. **Iniciar sesión en Google**<br>
   En la página de inicio de sesión de Google, escriba la cuenta de Google que se asociará con todas las tareas de administración de Android for Work para este inquilino. Se trata de la cuenta de Google que los administradores de TI de la empresa comparten para administrar y publicar aplicaciones en la consola de Play for Work. Puede usar una cuenta de Google existente o crear una nueva.  La cuenta que elija no debe estar asociada con un dominio de G Suite.

   c. **Proporcionar detalles de la organización**<br>
   Proporcione el nombre de su empresa en **Nombre de la organización**. Para el **proveedor de administración de Enterprise Mobility (EMM)**, **Microsoft Intune** debe mostrarse. Acepte el contrato de Android for Work y, después, seleccione **Confirmar**. La solicitud se procesará.

## <a name="specify-android-for-work-enrollment-settings"></a>Especificación de la configuración de inscripción de Android for Work
   Android for Work solo se admite en determinados dispositivos Android. Consulte los [requisitos de Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") de Google. Cualquier dispositivo que admita Android for Work también admite la administración Android convencional. Intune le permite especificar cómo se deben administrar los dispositivos que admiten Android for Work:

   - **Administrar todos los dispositivos como Android**. Todos los dispositivos Android se inscribirán como dispositivos Android convencionales, incluidos los dispositivos que admiten Android for Work.
   - **Administrar los dispositivos compatibles como Android for Work**. Todos los dispositivos que admiten Android for Work se inscriben como dispositivos Android for Work. Todo dispositivo Android que no admita Android for Work estará inscrito como dispositivo Android convencional.
   - **Administrar los dispositivos compatibles para usuarios solo en estos grupos de usuarios como Android for Work**. Puede dirigir la administración de Android for Work a un conjunto limitado de usuarios. Solo los miembros de los grupos seleccionados que inscriben un dispositivo que admita Android for Work se inscriben como dispositivos Android for Work. Todos los demás se inscriben como dispositivos Android. Esto resulta útil durante las implementaciones piloto de Android for Work.

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Aprobar la aplicación Portal de empresa en una instancia administrada de Google Play Store
Tiene que aprobar la aplicación Portal de empresa para Android en la instancia administrada de Google Play Store para asegurarse de que reciba actualizaciones automáticas. Si no la aprueba, la aplicación Portal de empresa al final quedará desactualizada y es posible que no reciba correcciones importantes ni nuevas características cuando Microsoft las publique.

Siga estos pasos para aprobar el Portal de empresa de Intune:

1.  Vaya a la aplicación Portal de empresa en una [instancia administrada de Google Play Store](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Inicie sesión en la instancia administrada de Google Play Store con la misma cuenta de Google que haya usado para configurar el enlace de Android for Work.
3.  Haga clic en **Aprobar**.  Se abre un nuevo cuadro de diálogo.
4.  Revise los permisos de este cuadro de diálogo y luego haga clic en **Aprobar**. Tiene que permitir estos permisos para que la aplicación Portal de empresa pueda administrar el perfil de trabajo en el dispositivo.
5.  Seleccione **Keep approved when app requests new permissions** (Mantener aprobados cuando la aplicación solicite nuevos permisos) y luego haga clic en **Guardar**.

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.

Indique a sus usuarios finales que vayan a Google Play para descargar la aplicación del Portal de empresa de Intune y, después, que abran la aplicación y sigan las indicaciones para inscribir su dispositivo. La aplicación guía a los usuarios a través del proceso de inscripción, explicándoles lo que pueden esperar y lo que pueden y no pueden ver los administradores de TI en sus dispositivos.

También puede enviarles un vínculo sobre los pasos de inscripción en línea: [Inscriba el dispositivo Android en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android).

Para más información sobre otras tareas de usuario final, vea estos artículos:

- [Recursos sobre la experiencia del usuario final con Microsoft Intune](end-user-educate.md)
- [Uso de un dispositivo Android con Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbind-your-android-for-work-administrative-account"></a>Desenlazado de la cuenta administrativa de Android for Work

Puede desactivar la inscripción y administración de Android for Work. Si hace clic en **Desenlazar** en la consola de administración de Intune, se quitan todos los dispositivos Android for Work inscritos. También se quita la relación entre la cuenta de Android for Work e Intune.

### <a name="to-unbind-an-android-for-work-account"></a>Para desenlazar una cuenta de Android for Work

1. **Eliminación del enlace de Android for Work**<br>
    Como administrador de Intune, en Azure Portal, pulse **Más servicios** > **Supervisión y administración** > **Intune**.  En la hoja **Intune**, elija **Inscripción de dispositivos** > **Inscripción de Android for Work** y seleccione **Desenlazar**.

2. **Acepte eliminar el enlace de Android for Work**.<br>
  Elija **Sí** para eliminar el enlace y anular la inscripción de todos los dispositivos Android for Work de Intune.
