---
title: Inscribir un dispositivo Android en Intune | Microsoft Docs
description: "Describe cómo inscribir un dispositivo Android en Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: e12f8d31abc4e067a6339e93cc21680921ce88e4
ms.sourcegitcommit: 2a6ad3c233d15a9fb441362105f64b2bdd550c34
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2017
---
# <a name="enroll-your-android-device-in-intune"></a>Inscriba el dispositivo Android en Intune

Si su empresa o centro educativo usa Microsoft Intune, puede inscribir un dispositivo Android para obtener acceso al correo electrónico, a los archivos y a otros recursos de la empresa. Cuando los dispositivos se inscriben, el departamento de TI puede administrar esos recursos profesionales o educativos y mantenerlos protegidos, al tiempo que los usuarios pueden usar el dispositivo que elijan libremente para realizar su trabajo. Para obtener más información sobre la inscripción, vea [What happens if you install the Company Portal app and enroll your device in Intune?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md) (¿Qué ocurre cuando se instala la aplicación de portal de empresa y se inscribe el dispositivo en Intune?).

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment/player]

Estas instrucciones se aplican a dispositivos Android nativos y Samsung KNOX. Samsung KNOX es un tipo de seguridad que utilizan determinados dispositivos Samsung para proporcionar protección adicional fuera de lo que ofrece Android de forma nativa. Para comprobar si tiene un dispositivo Samsung KNOX, vaya a **Configuración** > **Acerca del dispositivo**. Si no ve "Versión KNOX" en la lista, significa que el suyo es un dispositivo Android nativo.

Antes o después de la inscripción, se le pedirá que elija una categoría que describa de la mejor forma posible cómo usar el dispositivo. El administrador de TI usa esta categoría para comprobar las aplicaciones a las que se tienen acceso.

Si recibe un error al intentar inscribir el dispositivo en Intune, puede [enviar errores de inscripción a su administrador de TI](send-enrollment-errors-to-your-it-admin-android.md).

**Para inscribir su dispositivo Android:**

1.  Instale la aplicación gratuita de portal de empresa de Intune desde [Google Play](http://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal).

2.  Abra la aplicación de portal de empresa de Microsoft Intune.

3.  En la pantalla de **inicio de sesión** del Portal de empresa, pulse **Iniciar sesión** y luego inicie sesión con su cuenta profesional o educativa.

    ![La pantalla de inicio de sesión de la aplicación del Portal de empresa para Android, que pide al usuario que inicie sesión con su cuenta profesional o educativa. También se advierte de que no se aceptan cuentas Microsoft ni otras cuentas personales.](./media/and-enroll-0-welcome-screen.png)   

4.  Si el administrador de TI configuró los términos y condiciones, pulse **ACEPTAR** para aceptar los términos. Esta pantalla puede diferir ligeramente de la imagen siguiente según la versión de Android que use actualmente.

    ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5.  Inicie sesión en la aplicación de portal de empresa con su cuenta profesional o educativa y contraseña correspondiente y, luego, pulse en **Iniciar sesión**.

    ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6.  En la pantalla **Configuración de acceso a la empresa**, pulse **COMENZAR**.

    ![Pantalla Configuración de acceso de la compañía](./media/and-enroll-4a-comp-access-setup.png)

    > [!NOTE]
    > Los triángulos amarillos no significan que ya haya un error. Estos iconos indican que todavía hay pasos del proceso de inscripción que deben completarse.

7. En la pantalla **¿Por qué inscribir el dispositivo?**, lea lo que puede hacer si inscribe el dispositivo y, luego, pulse en **Continuar**.

    ![Pantalla ¿Por qué inscribir el dispositivo?](./media/and-enroll-4b-why-enroll.png)

8.  Revise una lista sobre lo que el administrador de TI puede y no puede ver en el dispositivo y pulse **CONTINUAR**.

    ![Configuración de privacidad](./media/and-enroll-4c-we-care-privacy.png)

9.  En la pantalla **Lo que viene después**, lea lo que sucede durante la inscripción y después pulse **INSCRIBIR**.

    ![Pantalla ¿Qué ocurre después?](./media/and-enroll-4d-what-comes-next.png)

10.  Si usa Android 6.0 o posterior, realice este paso. De lo contrario, vaya al próximo paso.

    Si el administrador de TI ha configurado algunas directivas, puede que aparezcan los siguientes mensajes:
    -   **¿Permitir que el Portal de empresa realice y administre llamadas telefónicas?**

        ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

    Si ve este mensaje, pulse en **PERMITIR**. Pulsar PERMITIR no entraña riesgos, puesto que **Microsoft nunca realiza ni controla sus llamadas de teléfono**. Google es responsable del texto del mensaje, que Microsoft no puede modificar. Al permitir el acceso, lo que está haciendo es dejar que el dispositivo envíe el número de identidad de equipos de estación móvil internacional (IMEI) del dispositivo a Intune. El IMEI es un número similar a un número de serie que identifica de forma exclusiva a un dispositivo móvil.

    Si se deniega el acceso, el mensaje aparecerá de nuevo la próxima vez que inicie sesión en el Portal de empresa, pero puede desactivar los mensajes futuros si pulsa en la casilla **No volver a preguntar**. Si más adelante decide permitir el acceso, vaya a **Configuración** &gt; **Aplicaciones** &gt; **Portal de empresa** &gt; **Permisos** &gt; **Teléfono**y active el permiso.

    -   **Allow Company Portal to access your contacts?** (¿Permitir que el Portal de empresa tenga acceso a los contactos?)

        ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

        Si ve este mensaje, pulse en **PERMITIR**. Pulsar PERMITIR no entraña riesgos, puesto que **Microsoft nunca tiene acceso a sus contactos**. Google es responsable del texto del mensaje, que Microsoft no puede modificar. Cuando permite el acceso, solo permite que la aplicación del Portal de empresa cree, use y administre su cuenta profesional.

        Si se deniega el acceso, el mensaje aparecerá de nuevo la próxima vez que inicie sesión en el Portal de empresa, pero puede desactivar los mensajes futuros si pulsa en la casilla **No volver a preguntar**. Si más adelante decide permitir el acceso, vaya a **Configuración** &gt; **Aplicaciones** &gt; **Portal de empresa** &gt; **Permisos** &gt; **Teléfono**y active el permiso.

11.  En la pantalla **Activar administrador del dispositivo**, pulse **Activar**.

    ![Pantalla Activate device administrator (Activar administrador del dispositivo)](./media/and-enroll-5-activate.png)

    El rol de administrador del dispositivo es en el que el Portal de la empresa debe administrar su dispositivo. Permite al administrador ver ciertas cosas, como cuántas veces ha intentado desbloquear la pantalla, y tomar algunas medidas.

    Lo que debe recordar es que se trata de acciones que se realizan en el nombre de la seguridad. El administrador de TI no está intentando invadir su privacidad o borrar la información sin motivo, sino que desea asegurarse de que los datos corporativos se mantengan a salvo.

    Microsoft no controla este mensaje, y somos conscientes de que su redacción puede parecer un poco drástica. No hay una forma de que el Portal de empresa muestre solo las restricciones y el acceso que son relevantes para su organización. Todos ellos aparecen a la vez en esta pantalla. Póngase en contacto con el administrador de TI para obtener más información, usando la información de contacto que aparece en el [sitio web del Portal de empresa](http://portal.manage.microsoft.com), si tiene preguntas específicas sobre el uso de su organización.

12.  Siga las instrucciones para escribir un PIN o contraseña. Si ya ha configurado un PIN o una contraseña en este dispositivo, no verá esta pantalla y no deberá escribir un PIN o contraseña nueva.

    ![Escriba el PIN o la contraseña](./media/and-enroll-6-PIN-native.png)

13.  Si usa un dispositivo Samsung KNOX, pulse **Confirmar** y verá un mensaje que indica que el dispositivo se está inscribiendo. Si usa un dispositivo Android nativo, solo verá la pantalla siguiente, que muestra que el dispositivo se está inscribiendo.

    ![Directiva de privacidad de Samsung KNOX](./media/and-enroll-7-knox-privacy-policy.png)

    En esta pantalla se muestra que el dispositivo se está inscribiendo.

    ![Pantalla Inscribiendo el dispositivo...](./media/and-enroll-8-device-enrolling.png)

14. Cuando aparezca la pantalla **Configuración de acceso de la compañía**, pulse **CONTINUAR**. Si un mensaje indica que el dispositivo es incompatible, siga las instrucciones para solucionar el problema y luego pulse **CONTINUAR**.

    ![El dispositivo no cumple las directivas, pero está inscrito.](./media/and-enroll-9a-noncompliant-enrolled-device.png)

    ![Se muestran problemas de cumplimiento de dispositivos que deben resolverse.](./media/and-enroll-9b-resolve-compliance-issues.png)

    Puede encontrar más información sobre los problemas tocándolos.

    ![Problemas de cumplimiento de dispositivos expandidos](./media/and-enroll-9c-resolve-compliance-issues-expanded.png)

    ![Pantalla Configuración de acceso de la compañía](./media/and-enroll-9d-comp-access-setup.png)  

15. En la pantalla **Configuración de acceso de la compañía completada**, pulse **LISTO**. El dispositivo ya está inscrito.

    ![Pantalla Configuración de acceso a la empresa completada](./media/and-enroll-10-comp-access-setup-complete.png)

Antes de intentar instalar aplicaciones de empresa, vaya a **Ajustes** &gt; **Seguridad** y active **Fuentes desconocidas**. Si no activa esta opción antes de intentar instalar aplicaciones, verá el mensaje siguiente: "Instalación bloqueada. Por motivos de seguridad, el dispositivo está configurado para bloquear las instalaciones de aplicaciones procedentes de orígenes desconocidos". Puede pulsar **Configuración** en el cuadro de diálogo del error para ir a la opción **Orígenes desconocidos**.

> [!Note]
> Si su organización usa software de administración de gastos de telecomunicaciones, deberá completar algunos pasos adicionales antes de que el dispositivo esté completamente inscrito. Descubra más [aquí](enroll-your-device-with-telecom-expense-management-android.md).

¿Sigue necesitando ayuda? Póngase en contacto con el administrador de TI (visite el [sitio web del Portal de empresa](http://portal.manage.microsoft.com) para obtener la información de contacto), o escriba al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">equipo de Microsoft Android</a>.
