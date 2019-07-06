---
title: Inscripción de dispositivos macOS proporcionados por la organización en la administración | Microsoft Docs
description: En este artículo se describe cómo inscribir un dispositivo macOS en Intune adquirido o proporcionado por la organización.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3941c41b24d458d14acb1361bc463af657a0ca67
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67511932"
---
# <a name="enroll-your-organization-provided-macos-device-in-management"></a>Inscripción de dispositivos macOS proporcionados por la organización en la administración

Obtenga información sobre cómo administrar un dispositivo macOS nuevo en Intune.  

Los dispositivos proporcionados por su empresa o centro educativo a menudo están preconfigurados antes de recibirlos. La organización enviará estas opciones configuradas previamente al dispositivo después de encenderlo e iniciar sesión por primera vez. Una vez configurado el dispositivo, recibirá acceso a los recursos profesionales o educativos. 

Para comenzar con la configuración de administración, encienda el dispositivo e inicie sesión con sus credenciales profesionales o educativas. A continuación, en este artículo se describirán los pasos y las pantallas que verá en el asistente de configuración.   

## <a name="what-is-apple-dep"></a>¿Qué es DEP de Apple?
Es posible que la organización haya comprado los dispositivos a través de lo que se denomina *Programa de inscripción de dispositivos de Apple* (DEP). DEP de Apple permite a las organizaciones comprar una gran cantidad de dispositivos iOS o macOS. De este modo, pueden configurar y administrar esos dispositivos con su proveedor de administración de dispositivos móviles preferido, como Intune. Si es un administrador y quiere obtener más información sobre DEP de Apple, vea [Inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos de Apple](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos).  

## <a name="get-your-device-managed"></a>Conversión del dispositivo en administrado 
Complete los siguientes pasos para inscribir un dispositivo macOS en la administración. Si usa un dispositivo propio, que la organización no le haya proporcionado, siga los pasos para los [dispositivos personales y Bring Your Own Device](enroll-your-device-in-intune-macos-cp.md).  

1. Encienda el dispositivo macOS. 
2. Elija el país y haga clic en **Continuar**.  

   ![Captura de la pantalla de bienvenida del asistente de configuración de dispositivos macOS en la que se muestra una lista de idiomas.](./media/macos-dep-welcome-1808.png)   
3. Elija una distribución de teclado. En la lista se muestra una o más opciones, según el país seleccionado. Para ver todas las opciones de distribución, independientemente del país seleccionado, haga clic en **Mostrar todo**. Cuando termine, haga clic en **Continuar**.  

   ![Captura de la pantalla de distribución de teclado del asistente de configuración de dispositivos macOS en la que se muestra una lista de idiomas de teclado con la opción Mostrar todo desactivada y los botones Atrás y Continuar.](./media/macos-dep-keyboard-1808.png)  
4. Seleccione la red Wi-Fi. Debe disponer de conexión a Internet para continuar con la configuración. Si no ve la red o necesita conectarse mediante cable, haga clic en **Otras opciones de red**. Cuando termine, haga clic en **Continuar**.  

   ![Captura de la pantalla de selección de red Wi-Fi del asistente de configuración de dispositivos macOS en la que se muestra una lista de redes disponibles. También se muestran los botones Otras opciones de red, Atrás y Continuar.](./media/macos-dep-wifi-1808.png)  
5. Tras conectarse a la red Wi-Fi, aparecerá la pantalla **Administración remota**. Esto permite al administrador de la organización configurar de forma remota el dispositivo con cuentas, opciones de configuración, aplicaciones y redes requeridas por la empresa. Lea toda la explicación sobre administración remota para comprender mejor cómo se administra el dispositivo. Después, haga clic en **Continuar**.  

   ![Captura de la pantalla de administración remota del asistente de configuración de dispositivos macOS con un texto en el que se explica la administración remota y un vínculo a documentación para obtener más información. También se muestran los botones Atrás y Continuar.](./media/macos-dep-remote-management-1-1808.png)  
6. Cuando se le solicite, inicie sesión con su cuenta profesional o educativa. Tras autenticarse, el dispositivo instalará un perfil de administración. Este configurará y habilitará el acceso a los recursos de su organización.  
7. Obtenga información sobre las condiciones de privacidad y datos de Apple para posteriormente poder identificar cuándo se está recopilando información personal. Después, haga clic en **Continuar**.  

   ![Captura de la pantalla de datos y privacidad del asistente de configuración de dispositivos macOS en la que se muestra una ilustración de dos personas dándose la mano y en la que se describe el uso que hace Apple de la información personal. También se muestran los botones Atrás y Continuar.](./media/macos-dep-apple-data-privacy-1808.png)  
8. Tras haber inscrito el dispositivo, es posible que deba completar algún paso más. Los pasos dependerán de si su organización ha personalizado la experiencia de configuración. Podría tener que hacer lo siguiente:
    * Iniciar sesión con una cuenta de Apple
    * Aceptar los términos y condiciones
    * Crear una cuenta en el equipo
    * Completar los pasos de una configuración rápida
    * Configurar el equipo Mac  
## <a name="get-the-company-portal-app"></a>Obtener la aplicación Portal de empresa      
Descargue la aplicación Portal de empresa de Intune para macOS en el dispositivo. La aplicación le permite supervisar, sincronizar, agregar y quitar el dispositivo de la administración, así como instalar aplicaciones. En este proceso también se describe cómo registrar el dispositivo con Portal de empresa.  
1. En el dispositivo macOS, vaya a https://portal.manage.microsoft.com/EnrollmentRedirect.aspx.
2. Inicie sesión en el sitio web del Portal de empresa con su cuenta profesional o educativa. 
3. Haga clic en **Obtener la aplicación** para descargar el instalador de Portal de empresa para macOS.
4. Cuando se le pida, abra el archivo .pkg y complete los pasos de instalación.
4. Abra la aplicación Portal de empresa e inicie sesión con su cuenta profesional o educativa.
5. Busque el dispositivo y haga clic en **Registrar**.
6. Haga clic en **Continuar** > **Listo**. El dispositivo debería aparecer ahora en la aplicación Portal de empresa como un dispositivo corporativo compatible.

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
