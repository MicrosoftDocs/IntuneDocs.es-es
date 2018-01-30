---
title: Inscribir un dispositivo macOS en Intune con Portal de empresa | Microsoft Docs
description: "Se describe cómo inscribir un dispositivo macOS en Intune con la aplicación Portal de empresa."
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: 
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 0da2ba5d842a004f167a4bbeca62d4b00f756612
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Inscribir un dispositivo macOS en Intune con la aplicación Portal de empresa

Puede acceder a las aplicaciones, los datos y los recursos de su organización que necesita para hacer su trabajo con mayor facilidad. Su organización usa Intune para [administrar el acceso a esos recursos](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md), lo que requiere que descargue la aplicación Portal de empresa para macOS. Estas instrucciones funcionarán para los dispositivos macOS en OS X El Capitan 10.11 y versiones posteriores.

> [!NOTE]
> [Aquí](enroll-your-device-in-intune-macos-legacy.md) encontrará instrucciones para inscribir dispositivos macOS en versiones anteriores de macOS.

1. En el __Dock__, busque __Safari__ y abra una nueva ventana; a continuación, abra el [sitio web del Portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).

2. Inicie sesión en el sitio web del Portal de empresa con su cuenta profesional o educativa.

[!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

3. Después de iniciar sesión, haga clic en el **menú** en la esquina superior izquierda de la página y seleccione **Mis dispositivos**.

   ![Captura de pantalla de la página de inicio del portal web en la que se muestra que aún no se puede instalar ninguna aplicación, con un botón Mis dispositivos debajo.](./media/macOS_enroll_001_landing_page.png)

4. En la página __Mis dispositivos__, verá una lista de dispositivos inscritos o simplemente un mensaje emergente. Esto depende de si ya tiene un dispositivo inscrito, macOS o de otro tipo. Para inscribir un dispositivo que no aparece, seleccione el mensaje emergente que indica __Si aparece el dispositivo, pulse aquí para identificarlo. También se puede pulsar para inscribir el dispositivo si no aparece__. Si no tiene ningún dispositivo inscrito, en el banner se indicará lo siguiente: **No tiene dispositivos inscritos. Inscriba este pulsando aquí.**

    ![Captura de pantalla de la página Mis dispositivos con un par de dispositivos sin identificar sobre el mensaje emergente para inscribir los dispositivos que no figuran en la lista o para identificar los no identificados.](./media/macOS_enroll_002_tap_here_banner.png)

5. Descargue la aplicación de Portal de empresa en el dispositivo macOS para proseguir con la inscripción.

    ![Mensaje en el que se pide al usuario que descargue la aplicación de Portal de empresa de macOS. En este mensaje, el texto del paso anterior aparece encima de un botón "Descargar" situado en la esquina inferior derecha.](./media/macOS_enroll_IWP_CP_app_notice.png)

6. El equipo Mac comprobará la descarga para asegurarse de que **CompanyPortal.pkg** se puede abrir con seguridad. Abra el instalador y siga el proceso de instalación.

7. Cuando el instalador finalice, abra la carpeta **Aplicaciones** o **Launchpad** y, después, **Portal de empresa**.

8. El equipo Mac mostrará un mensaje: **"Portal de empresa" es una aplicación que se ha descargado de Internet. ¿Seguro que quiere continuar?** Haga clic en **Abrir**.

  > [!NOTE]
  > Intune necesita acceder a su equipo para asegurarse de que es lo suficientemente seguro como para acceder a los recursos de su organización. Si el equipo se niega a abrir la aplicación Portal de empresa, intente [desactivar Gatekeeper](https://support.apple.com/HT202491) y abra la aplicación.

9. La primera pantalla que verá en la aplicación Portal de empresa le pedirá que **inicie sesión** con la misma cuenta profesional o educativa que usa para iniciar sesión en el sitio web de Portal de empresa.

10. Portal de empresa confirmará la información de su cuenta y mostrará sus estados de **inscripción de dispositivos** y **cumplimiento de dispositivos**. Verá triángulos amarillos que le informarán de que dispone de las acciones que debe realizar para asegurarse de que el equipo Mac se pueda usar en el trabajo con seguridad. Haga clic en **Comenzar** para iniciar la [inscripción del dispositivo en el sistema de administración](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).

11. El equipo Mac iniciará la inscripción en el sistema de administración. Puede que deba proporcionar información de inicio de sesión del equipo. El proceso de inscripción puede tardar unos minutos. Durante este tiempo, puede seguir usando el equipo. Una vez haya completado la configuración de acceso de la empresa, se mostrará un mensaje para informarle de que ya ha terminado.

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa. Puede encontrar su información de contacto en el [sitio web del Portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
