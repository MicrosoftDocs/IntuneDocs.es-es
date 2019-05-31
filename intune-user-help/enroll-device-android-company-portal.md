---
title: Inscribir dispositivos Android con Portal de empresa de Intune | Microsoft Docs
description: Explica cómo inscribir un dispositivo Android con Portal de empresa de Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 736b1d891207a19f281aa1127975de1a55889e8b
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197031"
---
# <a name="enroll-your-device-with-company-portal"></a>Inscribir dispositivos con Portal de empresa  
Inscriba el dispositivo corporativo o personal Android para obtener acceso seguro al correo electrónico, las aplicaciones y los datos corporativos. Portal de empresa admite dispositivos Android, incluido Samsung Knox, con Android 4.4 y posterior.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> Samsung Knox es un tipo de seguridad que usan determinados dispositivos Samsung para lograr una protección adicional a la ofrecida por Android de forma nativa. Para comprobar si tiene un dispositivo Samsung Knox, vaya a **Configuración** > **Acerca del dispositivo**. Si no ve **Versión Knox** en la lista, tiene un dispositivo Android nativo.

## <a name="enroll-device"></a>Inscribir un dispositivo  
Asegúrese de [instalar la aplicación Portal de empresa de Intune gratuita desde Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Durante la inscripción, es posible que se le pida que elija la categoría que mejor describa la forma en que usa el dispositivo. El equipo de soporte técnico de la empresa usa la respuesta para comprobar las aplicaciones a las que se tiene acceso.  

1. Abra la aplicación del portal de empresa.  

3. En la pantalla de **inicio de sesión** del Portal de empresa, pulse **Iniciar sesión** y luego inicie sesión con su cuenta profesional o educativa.

   ![La pantalla de inicio de sesión de la aplicación del Portal de empresa para Android, que pide al usuario que inicie sesión con su cuenta profesional o educativa. También se advierte de que no se aceptan cuentas Microsoft ni otras cuentas personales.](./media/and-enroll-0-welcome-screen.png)   

4. Si se le pide que acepte los términos y condiciones de la organización, pulse **ACEPTO**. Esta pantalla puede ser ligeramente diferente a la siguiente captura de pantalla de ejemplo. 

   ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5. Inicie sesión en la aplicación de portal de empresa con su cuenta profesional o educativa y contraseña correspondiente y, luego, pulse en **Iniciar sesión**.

   ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6. En la pantalla **Configuración de acceso a la empresa**, pulse **CONTINUAR**.

   ![Pantalla Configuración de acceso de la compañía](/intune/media/android_cp_enroll_01_1709_new.png)

   > [!NOTE]
   > Los triángulos amarillos no significan que ya haya un error. Estos iconos indican que todavía hay pasos del proceso de inscripción que deben completarse.

7. Revise una lista sobre lo que el equipo de soporte técnico de su empresa puede y no puede ver en el dispositivo y, después, pulse **CONTINUAR**.

   ![Configuración de privacidad](/intune/media/android_cp_enroll_02_after_1710.png)

8. En la pantalla **What's next?** (¿Qué ocurre después?), lea lo que ocurre durante la inscripción y, luego, pulse **ENROLL** (INSCRIBIR).

   ![Pantalla ¿Qué ocurre después?](/intune/media/android_cp_enroll_03_after_1710.png)

9. Si usa Android 6.0 o posterior, realice este paso. De lo contrario, vaya al próximo paso.

   Si el equipo de soporte técnico de su empresa ha configurado algunas directivas, puede que aparezcan los siguientes mensajes:
   - **¿Permitir que el Portal de empresa realice y administre llamadas telefónicas?**

     ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

   Si ve este mensaje, pulse en **PERMITIR**. Pulsar PERMITIR no entraña riesgos, puesto que **Microsoft nunca realiza ni controla sus llamadas de teléfono**. Google es responsable del texto del mensaje, que Microsoft no puede modificar. Al permitir el acceso, lo que está haciendo es dejar que el dispositivo envíe el número de identidad de equipos de estación móvil internacional (IMEI) del dispositivo a Intune. El IMEI es un número similar a un número de serie que identifica de forma exclusiva a un dispositivo móvil.

   Si deniega el acceso, el mensaje aparece de nuevo la siguiente vez que inicia sesión en Portal de empresa. Para desactivar futuros mensajes, seleccione **Never ask again** (No volver a preguntar). Para revertir el permiso de acceso, vaya a **Configuración** > **Aplicaciones** > **Portal de empresa** > **Permisos** > **Teléfono** y active el permiso.  

   - **Allow Company Portal to access your contacts?** (¿Permitir que el Portal de empresa tenga acceso a los contactos?)

     ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

     Si ve este mensaje, pulse en **PERMITIR**. Pulsar PERMITIR no entraña riesgos, puesto que **Microsoft nunca tiene acceso a sus contactos**. Google es responsable del texto del mensaje, que Microsoft no puede modificar. Cuando permite el acceso, solo permite que la aplicación del Portal de empresa cree, use y administre su cuenta profesional.

     Si se deniega el acceso, el mensaje aparecerá de nuevo la próxima vez que inicie sesión en el Portal de empresa, pero puede desactivar los mensajes futuros si pulsa en la casilla **No volver a preguntar**. Si más adelante decide permitir el acceso, vaya a **Configuración** &gt; **Aplicaciones** &gt; **Portal de empresa** &gt; **Permisos** &gt; **Teléfono**y active el permiso.

10. En la pantalla **Activar administrador del dispositivo**, pulse **Activar**.

    ![Pantalla Activate device administrator (Activar administrador del dispositivo)](./media/and-enroll-5-activate.png)

    El rol de administrador del dispositivo es en el que el Portal de la empresa debe administrar su dispositivo. Permite al administrador ver ciertas cosas, como cuántas veces ha intentado desbloquear la pantalla, y tomar algunas medidas.    

    Microsoft no controla este mensaje, y somos conscientes de que su redacción puede parecer un poco drástica. No hay una forma de que el Portal de empresa muestre solo las restricciones y el acceso que son relevantes para su organización. Todos ellos aparecen a la vez en esta pantalla. Póngase en contacto con el equipo de soporte técnico de su empresa para obtener más información, usando la información de contacto que aparece en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980), si tiene preguntas específicas sobre el uso de su organización.  

11. Siga las instrucciones para escribir un PIN o contraseña. Si ya ha configurado un PIN o una contraseña en este dispositivo, no verá esta pantalla y no deberá escribir un PIN o contraseña nueva.  

    ![Escriba el PIN o la contraseña](./media/and-enroll-6-PIN-native.png)

12. Si usa un dispositivo Samsung Knox, pulse **Confirmar** y verá un mensaje que indica que el dispositivo se está inscribiendo. Si usa un dispositivo Android nativo, solo verá la pantalla siguiente, que muestra que el dispositivo se está inscribiendo.

    ![Directiva de privacidad de Samsung Knox](./media/and-enroll-7-knox-privacy-policy.png)

    En esta pantalla se muestra que el dispositivo se está inscribiendo.

    ![Pantalla Inscribiendo el dispositivo...](./media/and-enroll-8-device-enrolling.png)

13. Cuando aparezca la pantalla **Configuración de acceso de la compañía**, pulse **CONTINUAR**. Si un mensaje indica que el dispositivo es incompatible, siga las instrucciones para solucionar el problema y luego pulse **CONTINUAR**.

    ![El dispositivo no cumple las directivas, pero está inscrito.](/intune/media/android_cp_enroll_05_post_1709.png)

    ![Se muestran problemas de cumplimiento de dispositivos que deben resolverse.](/intune/media/android_cp_enroll_03_post_1709.png)

    Puede encontrar más información sobre los problemas tocándolos.

    ![Problemas de cumplimiento de dispositivos expandidos](/intune/media/android_cp_enroll_04_post_1709.png)

    ![Pantalla Configuración de acceso de la compañía](./media/and-enroll-9d-comp-access-setup.png)  

14. En la pantalla **Configuración de acceso de la compañía completada**, pulse **LISTO**. El dispositivo ya está inscrito.

    ![Pantalla Configuración de acceso a la empresa completada](./media/and-enroll-10-comp-access-setup-complete.png)

## <a name="next-steps"></a>Pasos siguientes  

Antes de intentar instalar aplicaciones corporativas, vaya a **Configuración** > **Seguridad** y active **Orígenes desconocidos**. Si no activa esta opción antes de intentar instalar aplicaciones, verá el mensaje siguiente: "Instalación bloqueada. Por motivos de seguridad, el dispositivo está configurado para bloquear las instalaciones de aplicaciones procedentes de orígenes desconocidos". Puede pulsar **Configuración** en el cuadro de diálogo del error para ir a la opción **Orígenes desconocidos**.  

> [!Note]
> Si su organización usa software de administración de gastos de telecomunicaciones, deberá completar algunos pasos adicionales antes de que el dispositivo esté completamente inscrito. Descubra más [aquí](enroll-your-device-with-telecom-expense-management-android.md).

Si aparece un error al intentar inscribir el dispositivo en Intune, puede [Enviar registros al equipo de soporte técnico de su empresa por correo electrónico](send-logs-to-your-it-admin-by-email-android.md).  

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa (visite el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para obtener la información de contacto), o escriba al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipo de Microsoft Android</a>.
