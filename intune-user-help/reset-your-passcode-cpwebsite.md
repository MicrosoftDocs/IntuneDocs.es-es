---
title: Restablecimiento del código de acceso desde el sitio web del portal de empresa | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 06/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 45b087b9617b783517f8296f1726891392764d5f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Restablecer el código de acceso de un dispositivo desde el sitio web del portal de empresa

Si pierde el PIN o la contraseña de un dispositivo inscrito en Intune, puede usar el [sitio web del portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog) para restablecerlos. Puede usar el sitio web del Portal de empresa para administrar equipos y dispositivos que haya inscrito en Intune y para realizar la mayoría de las tareas que se pueden hacer con la aplicación Portal de empresa.

> [!NOTE]
> Es posible que no vea el botón Restablecer el código de acceso en el sitio web del portal de empresa si usa un dispositivo corporativo inscrito. Si no lo hace, necesitará ponerse en contacto con el equipo de soporte técnico de su empresa para que le restablezca el código de acceso.

Para restablecer el código de acceso:

1. En el [sitio web del Portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog), pulse el botón __menú__ ![Pequeña imagen del botón menú, tres barras horizontales apiladas en paralelo.](/intune/media/CP_hamburger_menu.png), luego seleccione __Mis dispositivos__.

2. En la página __Mis dispositivos__, seleccione el nombre del dispositivo cuyo código de acceso quiere restablecer.

   ![Captura de pantalla de la página Mis dispositivos con un par de dispositivos sin identificar sobre el mensaje emergente para inscribir los dispositivos que no figuran en la lista o para identificar los no identificados.](./media/macOS_enroll_002_tap_here_banner.png)

3. El dispositivo se abrirá en una ventana emergente. Seleccione el botón **Restablecer código de acceso**.

   ![Todas las opciones de un dispositivo seleccionado en el sitio web del Portal de empresa, incluidas Cambiar nombre, Quitar, Restablecer dispositivo, Restablecer código de acceso y Bloqueo remoto. ](./media/iwp-screen-with-all-options.png)

4. Aparece un mensaje emergente que le solicita que confirme que quiere restablecer el código de acceso y que el dispositivo cerrará la sesión después de hacerlo. Luego tendrá que esperar 5 minutos antes de volver a iniciar sesión.

   ![Mensaje emergente de restablecimiento del código de acceso con la advertencia sobre el restablecimiento del código de acceso del dispositivo y el cierre de la sesión del usuario. Los botones de entrada de usuario son Cerrar sesión y Cancelar.](./media/iwp-reset-passcode-popup.png)

5. Seleccione **Cerrar sesión** y aparecerá un último mensaje sobre la eliminación del código de acceso del dispositivo. Si no tiene el dispositivo a mano, no quite el código de acceso, ya que cualquiera que tenga acceso físico a él podría acceder a la mayor parte de la información que contiene, personal o corporativa. 

   ![Segundo mensaje emergente de restablecimiento del código de acceso con la advertencia sobre el restablecimiento del código de acceso del dispositivo y la eliminación del código de acceso del dispositivo. También aconseja sobre cómo establecer un nuevo código de acceso desde los ajustes del dispositivo.](./media/iwp-reset-passcode-2nd-popup.png)

   Los dispositivos diferentes tienen distintos tipos de códigos de acceso.

   **Android**: quita el código de acceso existente y crea un código de acceso temporal con letras y números. 
  
   > [!NOTE]
   > No puede restablecer el código de acceso para los dispositivos con Android 7.0 y versiones posteriores. Debe restablecer estos dispositivos a la configuración de fábrica si ha olvidado el código de acceso.

   **iOS**: quita el código de acceso existente y no crea un código de acceso temporal. Si utiliza el escáner de huellas digitales Touch ID para abrir el dispositivo o realizar compras, deberá configurarlo de nuevo.

   **Windows 10 Mobile**: quita el código de acceso existente y crea un código de acceso temporal con letras y números. Si utiliza el reconocimiento facial de Windows Hello para iniciar sesión, seguirá siendo compatible.
    
   **Windows Phone 8.1**: elimina el código de acceso existente y crea un código de acceso temporal con números.

   Para dispositivos Android y Windows, la contraseña temporal aparecerá en **Detalles del dispositivo**. 

6. Desbloquee el dispositivo y establezca un código de acceso nuevo, o bien cambie el código de acceso temporal en **Configuración** en el dispositivo.

Para ver una notificación que confirme que la contraseña se restableció correctamente, haga clic en la marca de notificación en la parte superior derecha del sitio del portal de empresa.

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
