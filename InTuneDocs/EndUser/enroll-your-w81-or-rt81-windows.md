---
# required metadata

title: Inscribir el dispositivo Windows 8.1 o Windows RT 8.1 en Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 28984f26-1070-4f7a-877c-669a59375c0c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Inscribir el dispositivo Windows 8.1 o Windows RT 8.1 en Intune

Si su empresa o centro educativo usa Microsoft Intune, puede inscribir los dispositivos para obtener acceso al correo electrónico, a los archivos y a otros recursos de la empresa. Cuando los dispositivos están inscritos, la organización puede tener protegidos los datos corporativos. Para obtener más información sobre la inscripción, vea [What happens if you install the Company Portal app and enroll your device in Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md) (¿Qué ocurre cuando se instala la aplicación de portal de empresa y se inscribe el dispositivo en Intune?) y [What your IT administrator can and can't see on your device](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md) (¿Qué puede ver y no ver el administrador de TI en el dispositivo?)..


Para inscribir el dispositivo Windows 8.1 o Windows RT 8.1:

1.  En el dispositivo, pulse **Configuración** &gt; **Configuración de PC** &gt; **Red** &gt; **Área de trabajo**..

    ![nav-to-workplace](./media/W81-1-workplacejoin.png)

2.  Escriba una dirección de correo del trabajo o educativa para el identificador de usuario y pulse **Unirse**..

    Si el identificador de usuario no es necesario, entonces se usará la dirección de correo electrónico que especificó al iniciar sesión en este dispositivo.

3.  Escriba la contraseña del correo electrónico de su empresa o centro educativo.

    ![type-password](./media/W81-2-workplacesettings_signin.png)

4.  En **Turn on device management** (Activar administración de dispositivos), pulse **Activar**..

    ![turn-on-device-management](./media/W81-3-dev-mgt-turn-on.png)

5.  En el cuadro de diálogo **Permitir aplicaciones y servicios del administrador de TI**, active la casilla **Acepto** y, luego, pulse **Activar**..

    ![turn-on-allow-apps-services](./media/W81-4-agree-allow-apps-services.png)

    Cuando se haya registrado correctamente, verá la siguiente pantalla.

    ![enrollment-complete](./media/W81-5-enrolled-done.png)

También se recomienda instalar la aplicación Portal de empresa, que le permitirá identificar fácilmente y obtener las aplicaciones de la empresa que son relevantes para usted y su rol. Según la forma en que su empresa configuró Intune, la aplicación Portal de empresa se pudo haber instalado como parte del proceso de inscripción. Para comprobar si tiene la aplicación, busque **Portal de empresa** en la lista de aplicaciones. Si no ve el Portal de empresa en su lista de aplicaciones, siga estos pasos para instalarlo.

1.  Pulse **Iniciar** &gt; **Tienda**..

2.  Pulse **Buscar** y escriba **portal de empresa**..

3.  En la lista de resultados, pulse **Portal de empresa**..

4.  Pulse en **Instalar** o **Gratis**. La opción que se muestra dependerá de cómo la empresa haya configurado la aplicación.


### Consulte también
[Inscriba el dispositivo Windows en Intune](enroll-your-device-in-intune-windows.md)</br>
[Usar un dispositivo Windows con Intune](using-your-windows-device-with-intune.md)


<!--HONumber=May16_HO1-->


