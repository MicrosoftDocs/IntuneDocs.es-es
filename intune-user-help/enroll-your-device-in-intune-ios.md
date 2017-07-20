---
title: Inscribir un dispositivo iOS en Intune | Microsoft Docs
description: "Describe cómo inscribir un dispositivo iOS en Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 07/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope: User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 4d7ad138a8aa59ceeff00866469e59e2e1d19520
ms.sourcegitcommit: 2a6ad3c233d15a9fb441362105f64b2bdd550c34
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2017
---
# <a name="enroll-your-ios-device-in-intune"></a>Inscriba el dispositivo iOS en Intune

Si su empresa o centro educativo usa Microsoft Intune, puede inscribir un dispositivo iOS para obtener acceso al correo electrónico, a los archivos y a otros recursos de la empresa. Cuando los dispositivos se inscriben, el departamento de TI puede administrar esos recursos profesionales o educativos y mantenerlos protegidos, al tiempo que los usuarios pueden usar el dispositivo que elijan libremente para realizar su trabajo. Para obtener más información sobre la inscripción, vea [What happens if you install the Company Portal app and enroll your device in Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md) (¿Qué ocurre cuando se instala la aplicación de portal de empresa y se inscribe el dispositivo en Intune?).

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment/player]

> [!NOTE]
> Si lo que intenta inscribir es un dispositivo macOS, como un equipo MacBook Pro o iMac, [siga estas instrucciones](enroll-your-device-in-intune-macos.md).

**Antes de empezar**

- Asegúrese de que termina la inscripción después de iniciar los pasos. Hacer una pausa durante unos minutos suele detener el proceso, por lo que deberá reiniciarla.
- Si por algún motivo se produce un error en la inscripción, deberá volver a la aplicación Portal de empresa para intentarlo de nuevo.
- Asegúrese de que funciona la red Wi-Fi. De lo contrario, se producirá un error en la inscripción.
- Si bloquea Safari en el dispositivo, debe desbloquearlo. Safari se usa como parte del proceso de inscripción de dispositivos.


**Para inscribir el dispositivo iOS:**

1.  Siga los pasos de [Install and sign in to the Intune Company Portal app](install-and-sign-in-to-the-intune-company-portal-app-ios.md) (Instalar la aplicación de portal de empresa de Intune e iniciar sesión en ella).

2. En la página **Configuración de acceso a la empresa**, pulse en **Comenzar**.

    ![ios-enroll-comp-access-setup-begin](./media/ios-enroll-1a-comp-access-setup.png)

3. En la pantalla **¿Por qué inscribir el dispositivo?**, lea lo que puede hacer si inscribe el dispositivo y, luego, pulse en **Continuar**.

    ![ios-enroll-why-enroll](./media/ios-enroll-1b-why-enroll.png)

  > [!NOTE]
  > Los triángulos amarillos no significan que ya haya un error. Estos iconos indican que todavía hay pasos del proceso de inscripción que deben completarse.

4. Revise una lista sobre lo que el administrador de TI puede y no puede ver en el dispositivo inscrito y después pulse **Continuar**.

    ![ios-enroll-what-it-can-see](./media/ios-enroll-1c-we-care-privacy.png)

5.  En la pantalla **¿Qué ocurre después?**, lea lo que ocurre durante la inscripción y, luego, pulse en **Inscribir**.

    ![ios-enroll-what-comes-next](./media/ios-enroll-1d-what-comes-next.png)

6.  En la pantalla **Instalar perfil**, pulse **Instalar** y escriba su contraseña, si se le pide.

    ![ios-enroll-install-profile](./media/ios-enroll-2-mgt-profile-install.png)

7.  Pulse **Instalar**.

    ![ios-enroll-tap-install](./media/ios-enroll-3-mgt-profile-install-2.png)    

8.  Pulse **Instalar** para indicar que ha leído la advertencia.

    ![ios-enroll-tap-install-after-warning](./media/ios-enroll-4-warning.png)

9.  Pulse **Confiar**.

    ![ios-enroll-tap-trust](./media/ios-enroll-5-trust.png)

10.  Cuando la pantalla cambie para indicar que el perfil ha terminado de instalarse, pulse en **Listo**.

    ![ios-enroll-tap-done](./media/ios-enroll-6-done.png)

    Aparece el mensaje "Inscribiendo el dispositivo" en pantalla.

11.  Cuando se muestre un mensaje en el que se le pregunte si quiere abrir la página en el Portal de empresa, pulse **Abrir**.

    ![ios-enroll-open-comp-portal](./media/ios-enroll-7-open-cp.png)

12. En la pantalla **Configuración de acceso a la empresa**, pulse **Continuar**. En esta pantalla se muestran los demás requisitos que debería cumplir para que el dispositivo sea compatible (como establecer una contraseña). Siga las instrucciones que aparecen en pantalla hasta que cumpla todos los requisitos de cumplimiento. Cuando haya terminado, volverá a la pantalla Configuración de acceso a la empresa. Pulse **Continuar**.

    ![ios-enroll-comp-access-tap-continue](./media/ios-enroll-8-comp-access-setup-compliance.png)

13. Pulse **Listo**.

    ![ios-enroll-tap-done](./media/ios-enroll-9-comp-access-setup-complete.png)

El dispositivo ya está inscrito en Intune. Se le dirigirá de nuevo a la aplicación de portal de empresa.

> [!Note]
> Debe seguir unos pocos pasos más para que el dispositivo esté totalmente inscrito. Obtenga más información sobre cómo [inscribir el dispositivo mediante la administración de gastos de telecomunicaciones](enroll-your-device-with-telecom-expense-management-ios.md). Si su organización usa el Programa de inscripción de dispositivos de Apple, obtenga más información [aquí](enroll-your-device-dep-ios.md).

¿Sigue necesitando ayuda? Póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).
