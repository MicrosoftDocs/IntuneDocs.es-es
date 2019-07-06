---
title: Inscribir un dispositivo macOS en Intune con Portal de empresa | Microsoft Docs
description: Se describe cómo inscribir un dispositivo macOS en Intune con la aplicación Portal de empresa.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee17e963964b6d2e4aa9d3e05c7a562f3c61bbf5
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545726"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Inscribir un dispositivo macOS en Intune con la aplicación Portal de empresa

Inscriba un dispositivo macOS con la aplicación Portal de empresa de Intune para obtener acceso seguro a las aplicaciones, los archivos y el correo electrónico de su organización.

A menudo, las organizaciones requieren que se administre el dispositivo antes de poder acceder a datos confidenciales desde él. Después de que un dispositivo se convierta en administrado, las organizaciones pueden insertar directivas y aplicaciones en él a través de su proveedor de administración de dispositivos móviles. Para obtener acceso continuo a la información profesional o educativa desde el dispositivo, debe configurarlo para que coincida con la configuración de directiva.  

En este artículo se describe cómo la aplicación Portal de empresa de Intune para macOS le ayuda a inscribir, configurar y mantener su dispositivo para que cumpla los requisitos de su organización.  
</br>
> [!VIDEO https://www.youtube.com/embed/Pa2pfhwq_yk?rel=0]

## <a name="what-to-expect-from-the-company-portal-app"></a>Qué esperar de la aplicación Portal de empresa

Durante la instalación inicial, la aplicación requiere que se autentique con la organización. Después, le informa de cualquier configuración del dispositivo que tenga que realizar. Por ejemplo, las organizaciones suelen definir requisitos de caracteres mínimos o máximos para las contraseñas que tendrá que cumplir.    

Una vez inscrito el dispositivo, la aplicación Portal de empresa continuará para asegurarse de que el dispositivo esté protegido. Por ejemplo, si instala una aplicación desde un origen que no sea de confianza, la aplicación le avisará y, en ocasiones, revocará el acceso a los datos de la empresa. Las directivas de protección de aplicaciones como esta son comunes en las organizaciones y suelen requerirle que desinstale las aplicaciones que no sean de confianza antes de recuperar el acceso.

Si después de la inscripción, la organización exige un nuevo requisito de seguridad, como la autenticación multifactor, la aplicación Portal de empresa se lo notificará. Tendrá la oportunidad de ajustar la configuración para poder seguir trabajando desde su dispositivo.  

Para obtener más información sobre la inscripción, vea [¿Qué ocurre si instalo la aplicación de Portal de empresa e inscribo el dispositivo?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-device-managed"></a>Conversión del dispositivo en administrado  
Siga estos pasos para inscribir dispositivos macOS con OS X El Capitan 10.11 y versiones posteriores.   


1. Para acceder al sitio web de Portal de empresa, abra una ventana nueva en __Safari__ y vaya a https://portal.manage.microsoft.com.  

2. Inicie sesión en el sitio web del Portal de empresa con su cuenta profesional o educativa.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. Vaya a la esquina superior izquierda de la página y haga clic en **Menú** > **Dispositivos**.  

4. En la página __Dispositivos__ se mostrará una lista de los dispositivos administrados o un banner. Lo que vea dependerá de si ya tiene un dispositivo administrado. 
    * Para agregar un dispositivo que no aparece en la lista, seleccione el banner en el que se lee **Tap here to tell us which device you're using or add a new device.** (Pulse aquí para indicarnos el dispositivo que está usando o agregar un dispositivo nuevo).
    * Si no tiene ningún dispositivo, en el banner se indicará: **You don't have any managed devices. Add this one by tapping here.** (No tiene dispositivos inscritos. Agregue este pulsando aquí). Haga clic en el banner para agregar el dispositivo.  

     ![Captura de pantalla de la página Dispositivos, con un cuadrado de color rojo alrededor de la opción de banner para resaltar dónde hacer clic.](./media/CP-enroll-MACOS-1808.png)  
5. Complete el paso siguiente que coincida con el mensaje que aparece actualmente en el Portal de empresa.  
    * Si es la primera vez que va a agregar un dispositivo, se le pedirá que descargue la aplicación Portal de empresa en el dispositivo. Haga clic en **Descargar** para continuar.  

         ![Captura de pantalla de ejemplo de la pantalla de mensaje para descargar la aplicación de Portal de empresa para macOS. El usuario tiene la opción de hacer clic en el botón Descargar de color azul en la parte inferior izquierda del mensaje, o bien en el botón Cancelar de color gris en la parte inferior derecha.](./media/CP-enroll-download-macOS-1808.png)  

    * Si ya tiene un dispositivo macOS administrado, recibirá un mensaje con una lista de los dispositivos macOS administrados en ese momento. Seleccione **Mi dispositivo no aparece aquí** > **Descargar** para descargar la aplicación Portal de empresa en el dispositivo que va a agregar.  

         ![Captura de pantalla de ejemplo de la pantalla de mensaje para descargar la aplicación de Portal de empresa para macOS. El usuario tiene la opción de seleccionar *Mi dispositivo no aparece aquí* o un dispositivo específico en la parte central de la página. Aparecerá un botón Descargar de color azul en la parte inferior izquierda del mensaje y un botón Cancelar de color gris en la parte inferior derecha](./media/cp-mac-os-device-isnt-here-1808.png)  

6. El dispositivo comprobará para asegurarse de que **CompanyPortal.pkg** se puede abrir con seguridad. Cuando termine, abra el programa de instalación y complete la instalación.  

7. Cuando haya finalizado el programa de instalación, vaya a **Launchpad** y abra **Portal de empresa**.  

8. El dispositivo macOS le pedirá que confirme que quiere abrir la aplicación Portal de empresa. Haga clic en **Abrir**.  

   > [!TIP]
   > Intune necesita acceder a su equipo para asegurarse de que es lo suficientemente seguro como para acceder a los recursos de su organización. Si el equipo se niega a abrir la aplicación Portal de empresa, [desactive Gatekeeper](https://support.apple.com/HT202491). Después, abra la aplicación.

9. La primera pantalla que verá en la aplicación Portal de empresa le pedirá que **inicie sesión**. Use la misma cuenta profesional o educativa que ha usado para iniciar sesión en el sitio web del Portal de empresa.

10. La aplicación Portal de empresa confirma la información de la cuenta y muestra los estados de **Inscripción de dispositivos** y **Cumplimiento de dispositivos**. Con triángulos de color amarillo se resaltan las acciones que debe emprender para proteger su dispositivo macOS para la escuela o el trabajo. Haga clic en **Comenzar** para iniciar la inscripción. 

11. Si se le pide, escriba la información de inicio de sesión del equipo.  

Puede que tarde unos minutos en inscribir el dispositivo en la administración. Durante este tiempo, puede realizar otras acciones en el dispositivo. Una vez haya completado la configuración de acceso de la empresa, recibirá un mensaje para informarle de que ya ha terminado.  

## <a name="unverified-profiles"></a>Perfiles sin comprobar
Cuando se consultan los perfiles de administración de dispositivos móviles (MDM) instalados para el dispositivo macOS, algunos perfiles podrían mostrar un estado **Sin comprobar**. Mientras el **Perfil de administración** muestre un estado **Comprobado**, no tiene por qué preocuparse.  

El perfil de administración es lo que define la conexión del canal de MDM. Mientras se compruebe el perfil de administración, cualquier otro perfil entregado a la máquina a través de ese canal, hereda las características de seguridad del perfil de administración.

Además, como los otros perfiles no necesitan comprobaciones individuales, se generan y se entregan más rápidamente a los dispositivos. 

## <a name="updating-the-company-portal-app"></a>Actualización de la aplicación del Portal de empresa

La actualización de la aplicación del Portal de empresa se realiza del mismo modo que la de cualquier otra aplicación de Office, a través de Microsoft AutoUpdate para Mac. Obtenga más información sobre cómo [actualizar aplicaciones de Microsoft para macOS aquí](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Pasos siguientes  
¿Necesita más ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa. Puede encontrar su información de contacto en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  


