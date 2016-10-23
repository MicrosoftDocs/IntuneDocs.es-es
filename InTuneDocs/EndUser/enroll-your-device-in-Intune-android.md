---
title: Inscribir un dispositivo Android en Intune | Microsoft Intune
description: "Describe cómo inscribir un dispositivo Android en Intune."
keywords: 
author: staciebarker
manager: angrobe
ms.date: 09/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7eefcefa5e1cd0f789c77bf020c256e449099273
ms.openlocfilehash: 5d7507d9c09867b5c302caba409f1a7347fae4b6


---


# Inscriba el dispositivo Android en Intune

Si su empresa o centro educativo usa Microsoft Intune, puede inscribir un dispositivo Android para obtener acceso al correo electrónico, a los archivos y a otros recursos de la empresa. Cuando los dispositivos se inscriben, el departamento de TI puede administrar esos recursos profesionales o educativos y mantenerlos protegidos, al tiempo que los usuarios pueden usar el dispositivo que elijan libremente para realizar su trabajo. Para más información sobre la inscripción, vea [What happens when I install the Company Portal app and enroll my device?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md) (¿Qué ocurre cuando se instala la aplicación de portal de empresa y se inscribe el dispositivo?).

Estas instrucciones de inscripción son adecuadas para dispositivos Android de Samsung Knox y dispositivos Android "nativos" (distintos a Samsung Knox). Para comprobar si tiene un dispositivo Samsung Knox, vaya a **Configuración** &gt; **Acerca del dispositivo**. Si no ve "Versión KNOX" en la lista, significa que el suyo es un dispositivo Android nativo.

Antes o después de la inscripción, se le pedirá que elija una categoría que describa de la mejor forma posible cómo usar el dispositivo. El administrador de TI usa esta categoría para comprobar las aplicaciones a las que se tienen acceso.

Si recibe un error al intentar inscribir el dispositivo en Intune, puede [enviar errores de inscripción a su administrador de TI](send-enrollment-errors-to-your-it-administrator-android.md).

**Para inscribir su dispositivo Android:**

1.  Instale la aplicación gratuita de portal de empresa de Intune desde [Google Play](http://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal).

2.  Abra la aplicación de portal de empresa de Microsoft Intune.

3.  En la pantalla de **inicio de sesión** del Portal de empresa, pulse **Iniciar sesión** y luego inicie sesión con su cuenta profesional o educativa.

    ![android-company-portal-sign-in](./media/and-enroll-0-welcome-screen.png)   

4.  Si el administrador de TI configuró los términos y condiciones, pulse **ACEPTAR** para aceptar los términos.

    ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5.  Inicie sesión en la aplicación de portal de empresa con su cuenta profesional o educativa y contraseña correspondiente y, luego, pulse en **Iniciar sesión**.

    ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6.  En la pantalla **Configuración de acceso a la empresa**, pulse **COMENZAR**.

    ![Pantalla Configuración de acceso de la compañía](./media/and-enroll-4a-comp-access-setup.png)

7.  En la pantalla **¿Por qué inscribir el dispositivo?**, lea lo que puede hacer si inscribe el dispositivo y, luego, pulse en **Continuar**.

    ![Pantalla ¿Por qué inscribir el dispositivo?](./media/and-enroll-4b-why-enroll.png)

8.  Revise una lista sobre lo que el administrador de TI puede y no puede ver en el dispositivo y pulse **CONTINUAR**.

    ![Configuración de privacidad](./media/and-enroll-4c-we-care-privacy.png)

9.  En la pantalla **Lo que viene después**, lea lo que sucede durante la inscripción y después pulse **INSCRIBIR**.

    ![Pantalla ¿Qué ocurre después?](./media/and-enroll-4d-what-comes-next.png)

10.  Si usa Android 6.0 o posterior, realice este paso. De lo contrario, vaya al próximo paso.

    Si el administrador de TI ha configurado algunas directivas, puede que aparezcan los siguientes mensajes:
    -   **¿Permitir que Portal de empresa realice y administre llamadas telefónicas?**

        ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

    Si ve este mensaje, pulse en **PERMITIR**. Pulsar PERMITIR no entraña riesgos, puesto que **Microsoft nunca realiza ni controla sus llamadas de teléfono**. Google es responsable del texto del mensaje, que Microsoft no puede modificar. Al permitir el acceso, lo que está haciendo es dejar que el dispositivo envíe el número de identidad de equipos de estación móvil internacional (IMEI) del dispositivo a Intune. El IMEI es un número similar a un número de serie que identifica de forma exclusiva a un dispositivo móvil.

    Si se deniega el acceso, el mensaje aparecerá de nuevo la próxima vez que inicie sesión en el Portal de empresa, pero puede desactivar los mensajes futuros si pulsa en la casilla **No volver a preguntar**. Si más adelante decide permitir el acceso, vaya a **Configuración** &gt; **Aplicaciones** &gt; **Portal de empresa** &gt; **Permisos** &gt; **Teléfono**y active el permiso.

    -   **Allow Company Portal to access your contacts? (¿Permitir que el portal de empresa tenga acceso a los contactos?)**

        ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

    Si ve este mensaje, pulse en **PERMITIR**. Pulsar PERMITIR no entraña riesgos, puesto que **Microsoft nunca tiene acceso a sus contactos**. Google es responsable del texto del mensaje, que Microsoft no puede modificar. Cuando permite el acceso, solo permite que la aplicación del Portal de empresa cree, use y administre su cuenta profesional.

    Si se deniega el acceso, el mensaje aparecerá de nuevo la próxima vez que inicie sesión en el Portal de empresa, pero puede desactivar los mensajes futuros si pulsa en la casilla **No volver a preguntar**. Si más adelante decide permitir el acceso, vaya a **Configuración** &gt; **Aplicaciones** &gt; **Portal de empresa** &gt; **Permisos** &gt; **Teléfono**y active el permiso.

11.  En la pantalla **Activar administrador del dispositivo**, pulse **Activar**.

    ![Pantalla Activate device administrator (Activar administrador del dispositivo)](./media/and-enroll-5-activate.png)

12.  Siga las instrucciones para escribir un PIN o contraseña. Si ya ha configurado un PIN o una contraseña en este dispositivo, no verá esta pantalla y no deberá escribir un PIN o contraseña nueva.

    ![Escriba el PIN o la contraseña](./media/and-enroll-6-PIN-native.png)

13.  Si usa un dispositivo Samsung Knox, pulse **Confirmar** y verá un mensaje que indica que el dispositivo se está inscribiendo. Si usa un dispositivo Android nativo, solo verá la pantalla siguiente, que muestra que el dispositivo se está inscribiendo.

    ![Directiva de privacidad de Samsung KNOX](./media/and-enroll-7-knox-privacy-policy.png)

    En esta pantalla se muestra que el dispositivo se está inscribiendo.

    ![Pantalla Inscribiendo el dispositivo...](./media/and-enroll-8-device-enrolling.png)

14. Cuando aparezca la pantalla **Configuración de acceso de la compañía**, pulse **CONTINUAR**. Si un mensaje indica que el dispositivo es incompatible, siga las instrucciones para solucionar el problema y luego pulse **CONTINUAR**.

    ![Pantalla Configuración de acceso de la compañía](./media/and-enroll-9-comp-access-setup.png)  

11. En la pantalla **Configuración de acceso de la compañía completada**, pulse **LISTO**. El dispositivo ya está inscrito.

    ![Pantalla Configuración de acceso a la empresa completada](./media/and-enroll-10-comp-access-setup-complete.png)

Antes de intentar instalar aplicaciones de empresa, vaya a **Ajustes** &gt; **Seguridad** y active **Fuentes desconocidas**. Si no activa esta opción antes de intentar instalar aplicaciones, verá el mensaje siguiente: "Instalación bloqueada. Por motivos de seguridad, el dispositivo está configurado para bloquear las instalaciones de aplicaciones procedentes de orígenes desconocidos". Puede pulsar **Configuración** en el cuadro de diálogo del error para ir a la opción **Orígenes desconocidos**.

¿Sigue necesitando ayuda? Póngase en contacto con el administrador de TI (consulte el [sitio web del Portal de empresa](http://portal.manage.microsoft.com) para obtener información de contacto) o escriba al equipo de Microsoft Android en wintunedroidfbk@microsoft.com.



<!--HONumber=Oct16_HO2-->


