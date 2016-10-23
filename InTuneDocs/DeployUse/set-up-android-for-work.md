---
title: "Configuración de la administración de Android for Work | Microsoft Intune"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos Android for Work con Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
translationtype: Human Translation
ms.sourcegitcommit: 519b66c94f3d056e060ed11e1a3d7d6d118a94fb
ms.openlocfilehash: 5f48303dd28627f961f8c2cfd38f8977354e2724


---

# Habilitación de la inscripción de dispositivos Android for Work

Para habilitar la administración de dispositivos Android for Work, debe agregar un enlace de Android for Work en Intune. Para inscribir dispositivos que admiten Android for Work, pero anteriormente se han inscrito como dispositivos de Android normal, se debe anular la inscripción de los dispositivos y después volver a inscribirlos.

## Adición de un enlace de Android for Work Binding para Intune

1. **Configurar Intune**<br>
Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** y configure MDM.

2. **Configuración del enlace de Android for Work**<br>
    Como usuario administrativo, abra [la consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **Android for Work**, y haga clic en **Configurar** para abrir el sitio web de Android for Work en Google Play. Se abrirá en una nueva pestaña en el explorador.

3. **Iniciar sesión en Google**<br>
   En la página de inicio de sesión de Google, escriba la cuenta de Google que se asociará con todas las tareas de administración de Android for Work para este inquilino. Podría ser la cuenta de Google que se comparte entre los administradores que administran Intune. Se trata de la cuenta de Google que su organización utiliza para administrar y publicar aplicaciones en la consola de Play for Work.

4. **Proporcionar detalles de la organización**<br>
   Proporcione el nombre de su empresa en **Nombre de la organización**. Para el **proveedor de administración de Enterprise Mobility (EMM)**, *Microsoft Intune* debe mostrarse. Acepte el acuerdo Android for Work y, después, haga clic en **Confirmar**. La solicitud se procesará.

## Especificación de la configuración de inscripción de Android for Work
   Android for Work solo se admite en determinados dispositivos Android. Consulte los [requisitos de Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") de Google.  Cualquier dispositivo que admita Android for Work, también admitirá la administración Android convencional.  Intune le permite especificar cómo se deben administrar los dispositivos que admiten Android for Work:

   - **Administrar todos los dispositivos como Android**: (deshabilitado) Todos los dispositivos Android se inscribirán, incluidos los dispositivos que admiten Android for Work, como dispositivos Android convencionales.
   - **Administrar dispositivos compatibles como Android for Work**: (habilitado) Todos los dispositivos que admiten Android for Work se inscriben como dispositivos Android for Work. Todo dispositivo Android que no admita Android for Work estará inscrito como dispositivo Android convencional.
   - **Administrar los dispositivos compatibles para los usuarios únicamente en estos grupos de usuarios como Android for Work**: (pruebas) Le permite dirigir la administración de Android for Work a un conjunto limitado de usuarios. Solo los miembros de los grupos seleccionados que inscriben un dispositivo que admita Android for Work se inscriben como dispositivos Android for Work. Todos los demás se inscriben como dispositivos Android.

## Pasos siguientes para Android for Work
Después de configurar el enlace de Android for Work y la configuración, puede hacer lo siguiente:
- [Implementación de aplicaciones Android for Work](android-for-work-apps.md)
- [Adición de directivas de configuración de Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## Desenlazado de la cuenta administrativa de Android for Work

Puede desactivar la inscripción y administración de Android for Work. Si hace clic en **Desenlazar**, se quitan todos los dispositivos inscritos de Android for Work y quita la relación entre la cuenta de Android for Work y Intune.

### Cómo desenlazar una cuenta de Android for Work

1. **Eliminación del enlace de Android for Work**<br>
    Como usuario administrativo, abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **Android for Work** y haga clic en **Desenlazar**.

2. **Acepte eliminar el enlace de Android for Work.**<br>
  Haga clic en **Sí** para eliminar el enlace y anular la inscripción de todos los dispositivos Android for Work de Intune.



<!--HONumber=Oct16_HO2-->


