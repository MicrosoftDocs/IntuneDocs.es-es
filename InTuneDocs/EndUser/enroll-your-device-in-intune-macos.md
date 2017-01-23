---
title: Inscribir un dispositivo macOS en Intune | Microsoft Docs
description: "Se describe cómo inscribir un dispositivo macOS en Intune."
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
searchScope:
- Company Portal
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 70b11804b6b96e76b43cc450ac4c433fb31be6f8


---

# <a name="enroll-your-macos-device-in-intune"></a>Inscribir un dispositivo macOS en Intune

Puede obtener acceso a las aplicaciones, los datos y los recursos de su organización que necesita para hacer su trabajo. Si usa un dispositivo macOS en el trabajo, esto implica instalar un __perfil de administración__. Se trata simplemente de un archivo que instala su administrador de TI que carga la configuración y la información de acceso en su Mac. ¿Quiere saber más? Descubra [qué ocurre si instala la aplicación del Portal de empresa e inscribe el dispositivo en Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md).

  > [!NOTE]
  > Si lo que intenta inscribir es un dispositivo iOS, como un iPhone o un iPad, [pruebe en su lugar con estas instrucciones](enroll-your-device-in-intune-ios.md).

1. En el __Dock__, busque __Safari__ y abra una nueva ventana; a continuación, abra el [sitio web del Portal de empresa](http://portal.manage.microsoft.com).
2. Inicie sesión en el sitio web del Portal de empresa con su cuenta profesional o educativa.

  [!INCLUDE[wit_nextref](../includes/end-user-password-guidance.md)]

3. Cuando inicie sesión, verá las __aplicaciones__ disponibles, __Mis dispositivos__ y cualquier __información de contacto__ disponible para su personal de TI. En la parte superior de la página, verá un aviso que dice **Either this device isn't enrolled, or the Company Portal can't identify it (Este dispositivo no está inscrito o el Portal de empresa no lo puede identificar). <u>Tap Here</u> to select a different device** (Pulse aquí para seleccionar un dispositivo diferente). Haga clic en __Tap Here__ (Pulse aquí).

 ![Página de inicio de macOS del Portal de empresa](./media/macOS_enroll_001_landing_page.png)

4. Aparecerá una ventana emergente con una breve explicación de por qué va a __identificar o inscribir este dispositivo__. Revísela y haga clic en __Inscribir__ para continuar.

 ![Identificar o inscribir este dispositivo macOS](./media/macOS_enroll_002_IDenroll_popup.png)

5. Aparecerá una segunda ventana emergente con una breve explicación de lo que pasará cuando __inscriba este dispositivo__. Revísela y haga clic en __Instalar__ para continuar.

 ![Inscribir este dispositivo macOS](./media/macOS_enroll_003_enroll_popup.png)

  > [!NOTE]
  > Intune necesita acceder a su equipo para asegurarse de que es lo suficientemente seguro como para acceder a los recursos de su organización. Descubra [lo que pasa cuando inscribe su dispositivo en Intune](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md).

6. Se abrirán las __preferencias del sistema__, que le preguntarán si quiere __instalar el perfil de administración__. Haga clic en __Instalar__ para continuar o en __Mostrar perfil__ para más información.

 ![Instalar el perfil de administración](./media/macOS_enroll_004_sysprefs_mgmt_profile.png)

7. Aparecerá una ventana emergente de macOS. Confirme que desea realizar cambios; para ello, proporcione el __nombre de usuario__ y la __contraseña__ del equipo y luego haga clic en __Aceptar__. Se instalará el perfil de administración en el equipo Mac.

 ![Ventana emergente de instalación del perfil de macOS](./media/macOS_enroll_005_sysprefs_admin_login.png)

8. Puede ver algunos mensajes adicionales de su equipo Mac con más información sobre el perfil o que le preguntan si quiere __instalarlo__. Haga clic en __Continuar__ y en __Instalar__ en estos mensajes para continuar. Cuando finalice la instalación, podrá ver el __perfil de administración__ recién instalado en la lista de __perfiles de dispositivo__.

 ![Perfil de macOS instalado](./media/macOS_enroll_006_sysprefs_installed_profile.png)

¿Sigue necesitando ayuda? Acuda a su administrador de TI. Puede encontrar su información de contacto en el [sitio web del Portal de empresa](http://portal.manage.microsoft.com).



<!--HONumber=Dec16_HO2-->


