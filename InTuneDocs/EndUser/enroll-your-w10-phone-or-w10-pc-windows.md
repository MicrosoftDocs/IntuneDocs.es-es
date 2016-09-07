---
title: Inscribir el dispositivo Windows 10 en Intune | Microsoft Intune
description: "Describe cómo inscribir un dispositivo móvil o de escritorio Windows 10 en Intune."
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 06/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 02287eb01598c28906045fd8def9e8b4660e3da5
ms.openlocfilehash: 8806231f8d02885a192053a35559694a8984d2f5


---


# Inscribir un dispositivo Windows 10 Mobile o Windows 10 Escritorio en Intune

Si su empresa o centro educativo usa Microsoft Intune, puede inscribir los dispositivos para obtener acceso al correo electrónico, a los archivos y a otros recursos de la empresa. Cuando los dispositivos están inscritos, la organización puede tener protegidos los datos corporativos. Para más información sobre la inscripción, vea [What happens if you install the Company Portal app and enroll your device in Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md) (¿Qué ocurre cuando se instala la aplicación de portal de empresa y se inscribe el dispositivo en Intune?) y [What your IT administrator can and can't see on your device](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md) (¿Qué puede ver y no ver el administrador de TI en el dispositivo?).


Para inscribir un dispositivo Windows 10 Mobile o Windows 10 Escritorio:

1.  Vaya a la opción **Configuración** de Windows y pulse **Cuentas**.

    ![settings-accounts](./media/w10-enroll-rs1-settings-accounts.png)

2.  Examine las dos pantallas siguientes y encuentre la que sea similar a lo que ve en el dispositivo. Siga los pasos que tienen que ver con la pantalla que verá en el dispositivo.

    Si aparece esta pantalla, siga los pasos de [Pasos a seguir si ve acceso profesional o educativo](#steps-to-follow-if-you-see-access-work-or-school).

    ![connect-to-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Si aparece esta pantalla, siga los pasos de [Pasos a seguir si ve su cuenta](#steps-to-follow-if-you-see-your-account).

    ![your-account](./media/w10-enroll-2-accounts-your-account.png)

## Pasos a seguir si ve acceso profesional o educativo

1.  Seleccione **Acceso profesional o educativo**.

    ![tap-access-work-school-account](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2.  Escriba su correo electrónico profesional o educativo y seleccione **Siguiente**.

    ![enter-your-work-or-school-account](./media/w10-enroll-rs1-set-up-work-or-school-account.png)

3. Inicie sesión en Intune con su cuenta profesional o educativa.

    ![add-work-school-account](./media/w10-enroll-rs1-enter-your-credentials.png)

    Verá un mensaje que indica que su empresa o escuela están registradas en el dispositivo.

4. Cuando las vea, significa que se ha**completado el proceso** página, seleccione **Cerrar**. Ya ha terminado.

  ![tap-close-on-you-are-all-set-screen](./media/w10-enroll-rs1-youre-all-set.png)

5. Si desea comprobar nuevamente que la conexión es correcta, vuelva a **Configuración**, y podrá ver ahora que aparece la cuenta profesional o educativa.

    ![validate-that-connection-was-set-up-correctly](./media/w10-enroll-rs1-validate-successful-enrollment.png)

Si después de seguir los pasos anteriores, no consigue tener acceso a los archivos y al correo electrónico profesional o educativo, siga los pasos en [Pasos de solución de problemas a seguir si ve acceso profesional o educativo](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).


## Pasos a seguir si ve su cuenta

1.  Vaya a la opción **Configuración** de Windows y pulse **Cuentas**.

    ![go-to-settings-accounts](./media/W10-enroll-1-settings-accounts.png)

2.  Pulse en **Su cuenta**.

    ![tap-your-account](./media/W10-enroll-2-accounts-your-account.png)

3.  Puntee en **Agregar una cuenta de trabajo o escuela**.

    ![add-work-or-school-account](./media/w10-enroll-3-add-work-school-acct.png)

4.  Inicie sesión con las credenciales de su trabajo o escuela.

    ![sign-in](./media/W10-enroll-4-sign-in.png)

Si después de seguir los pasos anteriores, no consigue tener acceso al correo electrónico profesional o educativo, a los archivos y a otros datos, siga los pasos de solución de problemas en [Pasos de solución de problemas a seguir si ve su cuenta](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account).

También se recomienda instalar la aplicación Portal de empresa, que le permitirá identificar fácilmente y obtener las aplicaciones de la empresa que son relevantes para usted y su rol. Según la forma en que su empresa configuró Intune, la aplicación Portal de empresa se pudo haber instalado como parte del proceso de inscripción. Para comprobar si tiene la aplicación, busque **Portal de empresa** en la lista de aplicaciones. Si no ve el Portal de empresa en su lista de aplicaciones, siga estos pasos para instalarlo.

1.  Pulse en **Inicio** &gt; **Tienda**.

2.  Pulse en **Buscar** y escriba **portal de empresa**.

3.  En la lista de resultados, pulse en **Portal de empresa** &gt; **Instalar**.

4.  Pulse en **Instalar** o **Gratis**. La opción que se muestra dependerá de cómo la empresa haya configurado la aplicación.

¿Sigue necesitando ayuda? Póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).

### Consulte también
[Usar un dispositivo Windows con Intune](using-your-windows-device-with-intune.md)



<!--HONumber=Aug16_HO3-->


