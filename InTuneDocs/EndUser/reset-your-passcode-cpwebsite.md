---
title: "Restablecer el código de acceso de un dispositivo desde el sitio web del portal de empresa | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2aea845bc00c153f070e04abb67582a5d5a726ca
ms.openlocfilehash: 47b36616f7a8ee23d4d47b41a1db2c41c185c6f5


---


# Restablecer el código de acceso de un dispositivo desde el sitio web del portal de empresa

Si pierde el PIN o la contraseña de un dispositivo inscrito en Intune, puede usar el [sitio web del portal de empresa](http://portal.manage.microsoft.com) para restablecerlos. Puede usar el sitio web del Portal de empresa para administrar equipos y dispositivos que haya inscrito en Intune y para realizar la mayoría de las tareas que se pueden hacer con la aplicación Portal de empresa.

> [!NOTE]
> Según la configuración de Intune que haya realizado el administrador de TI, es posible que no vea el botón **Restablecer código de acceso** en el sitio web del Portal de empresa. El restablecimiento del código de acceso no se admite en dispositivos Windows 8.1.

Para restablecer el código de acceso:

1.  Abra el [sitio web del Portal de empresa](http://portal.manage.microsoft.com) y elija el dispositivo cuyo código de acceso quiere restablecer.

2.  Elija **Restablecer código de acceso**.

    ![Detalles del dispositivo con el botón Restablecer código de acceso](./media/iwp-screen-with-all-options.png)

3.  Elija **Cerrar sesión** y vuelva a iniciar sesión con las credenciales de su cuenta profesional o educativa. Tendrá que volver a iniciar sesión en un plazo de cinco minutos.

    ![Mensaje de restablecimiento con el botón Cerrar sesión](./media/iwp-2-sign-out.png)

4.  Elija **Restablecer código de acceso**.

    ![Mensaje que explica lo que ocurre al restablecer el código de acceso](./media/iwp-3-tap-reset-passcode-after-signin.png)

    Consulte la tabla para ver cómo funciona **Restablecer código de acceso** en su dispositivo.

    |Plataforma|Support|
    |------------|-----------|
    |Android|Crea un código de acceso temporal alfanumérico.|
    |iOS|Quita el código de acceso del dispositivo y no crea ningún código de acceso temporal. Si usa Touch ID deberá volver a configurarlo en el dispositivo, ya que se eliminará al restablecer el código de acceso.|
    |Windows 10 (solo para dispositivos móviles)|Crea un código de acceso temporal alfanumérico. Windows Hello es compatible.|
    |Windows Phone 8,1|Crea un código de acceso temporal numérico.|
    Después de desbloquear el dispositivo, puede establecer un código de acceso nuevo, Para ello, vaya a **Configuración** en el dispositivo.

5.  Desbloquee el dispositivo y establezca un código de acceso nuevo, o bien cambie el código de acceso temporal en **Configuración** en el dispositivo.

    Para ver una notificación que confirme que la contraseña se restableció correctamente, haga clic en la marca de notificación en la parte superior derecha del sitio del portal de empresa.

¿Sigue necesitando ayuda? Póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).



<!--HONumber=Oct16_HO3-->


