---
title: Inscribir un dispositivo macOS en Intune | Microsoft Docs
description: "Se describe cómo inscribir un dispositivo macOS en Intune."
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
searchScope: User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 04009fa3fea401e3093a444b0fdbbbe12bd31c84
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2017
---
# <a name="enroll-your-macos-device-in-intune"></a>Inscribir un dispositivo macOS en Intune

Puede obtener acceso a las aplicaciones, los datos y los recursos de su organización que necesita para hacer su trabajo. Si usa un dispositivo macOS en el trabajo, esto implica instalar un __perfil de administración__. Se trata de un archivo que instala el equipo de soporte técnico de su empresa que carga la configuración y la información de acceso en su Mac. ¿Quiere obtener más información? Descubra [qué ocurre si instala la aplicación del Portal de empresa e inscribe el dispositivo en Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md).

  > [!NOTE]
  > Si lo que intenta inscribir es un dispositivo iOS, como un iPhone o un iPad, [pruebe en su lugar con estas instrucciones](enroll-your-device-in-intune-ios.md).

1. En el __Dock__, busque __Safari__ y abra una nueva ventana; a continuación, abra el [sitio web del Portal de empresa](https://portal.manage.microsoft.com).
2. Inicie sesión en el sitio web del Portal de empresa con su cuenta profesional o educativa.

  [!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

3. Cuando inicie sesión, verá las pestañas __Inicio__, __Aplicaciones__ y __Categorías__ que haya disponibles. Esta página muestra las aplicaciones disponibles para instalar. Si aún no tiene ningún dispositivo inscrito, verá un aviso que indica que **no se puede mostrar ninguna aplicación**. Puede continuar si selecciona __Mis dispositivos__.

 ![Captura de pantalla de la página de inicio del portal web en la que se muestra que aún no se puede instalar ninguna aplicación, con un botón Mis dispositivos debajo.](./media/macOS_enroll_001_landing_page.png)

4. En la página __Mis dispositivos__, verá una lista de dispositivos inscritos o simplemente un mensaje emergente. Esto depende de si ya tiene un dispositivo inscrito, macOS o de otro tipo. Para inscribir un dispositivo que no aparece, seleccione el mensaje emergente que indica __Si aparece el dispositivo, pulse aquí para identificarlo. También se puede pulsar para inscribir el dispositivo si no aparece__.

  ![Captura de pantalla de la página Mis dispositivos con un par de dispositivos sin identificar sobre el mensaje emergente para inscribir los dispositivos que no figuran en la lista o para identificar los no identificados.](./media/macOS_enroll_002_tap_here_banner.png)

5. Aparecerá una ventana emergente con una breve explicación de por qué va a __identificar o inscribir este dispositivo__. Revísela y haga clic en __Inscribir__ para continuar.

 ![Identificar o inscribir este dispositivo macOS](./media/macOS_enroll_003_IDenroll_popup.png)

6. Aparecerá una segunda ventana emergente con una breve explicación de lo que pasará cuando __inscriba este dispositivo__. Revísela y haga clic en __Instalar__ para continuar.

 ![Inscribir este dispositivo macOS](./media/macOS_enroll_004_enroll_popup.png)

  > [!NOTE]
  > Intune necesita acceder a su equipo para asegurarse de que es lo suficientemente seguro como para acceder a los recursos de su organización. Descubra [lo que pasa cuando inscribe su dispositivo en Intune](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md).

7. Se abrirán las __preferencias del sistema__, que le preguntarán si quiere __instalar el perfil de administración__. Haga clic en __Instalar__ para continuar o en __Mostrar perfil__ para más información.

 ![Instalar el perfil de administración](./media/macOS_enroll_005_sysprefs_mgmt_profile.png)

8. Aparecerá una ventana emergente de macOS. Confirme que desea realizar cambios; para ello, proporcione el __nombre de usuario__ y la __contraseña__ del equipo y luego haga clic en __Aceptar__. Se instalará el perfil de administración en el equipo Mac.

 ![Ventana emergente de instalación del perfil de macOS](./media/macOS_enroll_006_sysprefs_admin_login.png)

9. Puede ver algunos mensajes adicionales de su equipo Mac con más información sobre el perfil o que le preguntan si quiere __instalarlo__. Haga clic en __Continuar__ y en __Instalar__ en estos mensajes para continuar. Cuando finalice la instalación, podrá ver el __perfil de administración__ recién instalado en la lista de __perfiles de dispositivo__.

 ![Perfil de macOS instalado](./media/macOS_enroll_007_sysprefs_installed_profile.png)

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa. Puede encontrar su información de contacto en el [sitio web del Portal de empresa](https://portal.manage.microsoft.com).
