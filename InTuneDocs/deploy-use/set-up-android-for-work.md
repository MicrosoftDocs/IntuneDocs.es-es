---
title: "Configuración de Android for Work | Microsoft Docs"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos Android for Work con Microsoft Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 660d0c69fc09c6ec8b82185b3808269ef4bb6852
ms.lasthandoff: 04/24/2017


---

# <a name="enable-enrollment-of-android-for-work-devices"></a>Habilitación de la inscripción de dispositivos Android for Work

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para habilitar la administración de dispositivos Android for Work, debe agregar un enlace de Android for Work en Intune. Para inscribir dispositivos que admiten Android for Work, pero que anteriormente se han inscrito como dispositivos de Android normal, se debe anular la inscripción de los dispositivos y después volver a inscribirlos.

## <a name="add-android-for-work-binding-for-intune"></a>Adición de un enlace de Android for Work Binding para Intune

1. **Configurar Intune**<br>
Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-8#enable-device-enrollment) como **Microsoft Intune** y configure MDM.

2. **Configuración del enlace de Android for Work**<br>
    Como administrador de Intune, abra la [consola de administración de Microsoft Intune](https://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles**&gt;**Android for Work**, y haga clic en **Configurar** para abrir el sitio web de Android for Work en Google Play. Se abrirá en una nueva pestaña en el explorador.

3. **Iniciar sesión en Google**<br>
   En la página de inicio de sesión de Google, escriba la cuenta de Google que se asociará con todas las tareas de administración de Android for Work para este inquilino. Se trata de la cuenta de Google que los administradores de TI de su organización compartían para administrar y publicar aplicaciones en la consola de Play for Work.

4. **Proporcionar detalles de la organización**<br>
   Proporcione el nombre de su empresa en **Nombre de la organización**. Para el **proveedor de administración de Enterprise Mobility (EMM)**, *Microsoft Intune* debe mostrarse. Acepte el acuerdo Android for Work y, después, haga clic en **Confirmar**. La solicitud se procesará.

## <a name="specify-android-for-work-enrollment-settings"></a>Especificación de la configuración de inscripción de Android for Work
   Android for Work solo se admite en determinados dispositivos Android. Consulte los [requisitos de Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") de Google.  Cualquier dispositivo que admita Android for Work, también admitirá la administración Android convencional.  Intune le permite especificar cómo se deben administrar los dispositivos que admiten Android for Work:

   - **Administrar todos los dispositivos como Android**: se inscribirán todos los dispositivos Android, incluidos los dispositivos que admiten Android for Work, como dispositivos Android convencionales.
   - **Administrar los dispositivos compatibles como Android for Work**: todos los dispositivos que admiten Android for Work se inscriben como dispositivos Android for Work. Todo dispositivo Android que no admita Android for Work estará inscrito como dispositivo Android convencional.
   - **Manage supported devices for users only in these user groups as Android for Work** (Administrar los dispositivos compatibles para los usuarios únicamente en estos grupos de usuarios como Android for Work): le permite dirigir la administración de Android for Work a un conjunto limitado de usuarios. Solo los miembros de los grupos seleccionados que inscriben un dispositivo que admita Android for Work se inscriben como dispositivos Android for Work. Todos los demás se inscriben como dispositivos Android. Esto resulta útil durante las implementaciones piloto de Android for Work.

## <a name="next-steps-for-android-for-work"></a>Pasos siguientes para Android for Work
Después de configurar el enlace de Android for Work y la configuración, puede hacer lo siguiente:
- [Implementación de aplicaciones Android for Work](android-for-work-apps.md)
- [Adición de directivas de configuración de Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Desenlazado de la cuenta administrativa de Android for Work

Puede desactivar la inscripción y administración de Android for Work. Si hace clic en **Desenlazar** en la consola de administración de Intune, se quitan todos los dispositivos inscritos de Android for Work y se quita la relación entre la cuenta de Android for Work e Intune.

### <a name="how-to-unbind-an-android-for-work-account"></a>Cómo desenlazar una cuenta de Android for Work

1. **Eliminación del enlace de Android for Work**<br>
    Como usuario administrativo, abra la [consola de administración de Microsoft Intune](https://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **Android for Work** y haga clic en **Desenlazar**.

2. **Acepte eliminar el enlace de Android for Work**.<br>
  Haga clic en **Sí** para eliminar el enlace y anular la inscripción de todos los dispositivos Android for Work de Intune.

