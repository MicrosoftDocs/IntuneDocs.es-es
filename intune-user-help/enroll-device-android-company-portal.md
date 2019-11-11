---
title: Inscribir dispositivos Android con Portal de empresa de Intune | Microsoft Docs
description: Explica cómo inscribir un dispositivo Android con Portal de empresa de Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5baf0e9079cc148101a68e5cd2d3a4ed500f567f
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414850"
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

1. Abra la aplicación Portal de empresa e inicie sesión con su cuenta profesional o educativa.  

2. Si se le pide que acepte los términos y condiciones de la organización, pulse **ACEPTAR TODO**.  

   ![Imagen de ejemplo de la Portal de empresa, pantalla de términos, resaltando el botón "aceptar todo".](./media/accept-terms-1911.png)  


3. Revise lo que su organización puede y no puede ver. Después, pulse **CONTINUAR**.


    ![Imagen de ejemplo de Portal de empresa, le interesa la pantalla de privacidad, resaltando el botón continuar.](./media/android-privacy-screen-1911.png)  
4. Revise lo que espera en los próximos pasos. A continuación, puntee en **siguiente**.  

    ![Imagen de ejemplo de Portal de empresa, la siguiente pantalla, resaltando el botón siguiente.](./media/android-whats-next-1911.png)  


5. En función de la versión de Android, es posible que se le pida que permita el acceso a determinadas partes del dispositivo. Estas solicitudes son necesarias para Google y no están controladas por Microsoft.  

    Pulse en **permitir** para los siguientes permisos:  
    * **Permitir portal de empresa para realizar y administrar llamadas telefónicas**: este permiso permite que el dispositivo comparta su número de identidad de equipo de estación móvil internacional (IMEI) con Intune, el proveedor de administración de dispositivos de la organización. Es seguro permitir este permiso. Microsoft nunca realizará ni administrará llamadas telefónicas.  
    * **Permitir que portal de empresa tenga acceso a los contactos**: este permiso permite a la aplicación portal de empresa crear, usar y administrar su cuenta profesional.  Es seguro permitir este permiso. Microsoft nunca tendrá acceso a sus contactos. 

    Si deniega el permiso, se le pedirá de nuevo la próxima vez que inicie sesión en Portal de empresa. Para desactivar estos mensajes, seleccione **No volver a preguntar**. Para administrar los permisos de la aplicación, vaya a la configuración aplicación > **aplicaciones** > **Portal de empresa** > **permisos** > **teléfono**.  

6. Active la aplicación de administración de dispositivos. 

    Portal de empresa necesita permisos de administrador de dispositivos para administrar el dispositivo de forma segura. La activación de la aplicación permite a su organización identificar posibles problemas de seguridad, como los intentos fallidos de desbloqueo del dispositivo y responder de forma adecuada.  

    ![Imagen de ejemplo de la pantalla activar administrador de dispositivos, resaltando el botón activar.](./media/activate-device-administrator-1911.png)  

> [!NOTE]
> Microsoft no controla la mensajería en esta pantalla. Sabemos que su formulación puede parecer algo drástica. Portal de empresa no pueden especificar qué restricciones y acceso son relevantes para su organización. Si tiene alguna pregunta sobre cómo su organización usa la aplicación, póngase en contacto con el personal de soporte técnico de ti. Vaya al [sitio web Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para buscar la información de contacto de su empresa.  


7. El dispositivo comienza la inscripción. Si usa un dispositivo Samsung Knox, se le pedirá que revise y confirme primero la Directiva de privacidad del agente ELM.   

    ![Imagen de ejemplo de la pantalla de la Directiva de privacidad de Samsung Knox que aparece durante la inscripción.](./media/and-enroll-7-knox-privacy-policy.png)  

8. En la pantalla **configuración de acceso a la empresa** , compruebe que el dispositivo está inscrito. Después, pulse **CONTINUAR**.  

    ![Imagen de ejemplo de Portal de empresa, la pantalla de configuración de acceso a la empresa, que muestra que el dispositivo administrado está completo.](./media/update-settings-1911.png)  

9. Su organización podría requerir que actualice la configuración del dispositivo. Puntee en **resolver** para ajustar una configuración. Cuando haya terminado de actualizar la configuración, pulse **continuar**.  

   ![Imagen de ejemplo de Portal de empresa, actualizar la configuración del dispositivo, resaltar los botones resolver y continuar.](./media/resolve-settings-1911.png)  

10. Una vez finalizada la instalación, pulse **listo**.    

    ![Imagen de ejemplo de Portal de empresa, pantalla de configuración de acceso a la empresa, en la que se muestra el botón completado de la instalación y resaltado.](./media/android-enrollment-done-1911.png) 

## <a name="next-steps"></a>Pasos siguientes  

Antes de intentar instalar una aplicación educativa o de trabajo, vaya a **configuración** > **seguridad**y Active **orígenes desconocidos**. Si no activa esta opción, verá el mensaje siguiente al intentar instalar una aplicación: "Instalación bloqueada. Por motivos de seguridad, el dispositivo está configurado para bloquear las instalaciones de aplicaciones procedentes de orígenes desconocidos". Puede pulsar **configuración** en el mensaje para ir directamente a **orígenes desconocidos**.  

> [!Note]
> Si su organización usa software de administración de gastos de telecomunicaciones, deberá completar algunos pasos adicionales antes de que el dispositivo esté completamente inscrito. Descubra más [aquí](enroll-your-device-with-telecom-expense-management-android.md).

Si aparece un error al intentar inscribir el dispositivo en Intune, puede [Enviar registros al equipo de soporte técnico de su empresa por correo electrónico](send-logs-to-your-it-admin-by-email-android.md).  

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  