---
title: Restablecimiento del código de acceso desde el sitio web del portal de empresa | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2056d37b00f5e2ae7b36c6e1c02f20dc244eb290
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502134"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Restablecer el código de acceso de un dispositivo desde el sitio web del portal de empresa

Si pierde el PIN o la contraseña del dispositivo, puede usar el [sitio web del Portal de empresa](https://portal.manage.microsoft.com) para restablecerlos. 

Es posible que la opción restablecer código de acceso no aparezca para un dispositivo inscrito en la empresa. En este caso, póngase en contacto con el equipo de soporte técnico de su empresa para que se restablezca.  

El restablecimiento del código de acceso no está disponible para los dispositivos que ejecutan Android 7,0 y versiones posteriores. Si olvida el código de acceso en uno de estos dispositivos, debe restablecer la configuración de fábrica.  

## <a name="reset-your-passcode"></a>Restablecimiento del código de acceso

1. Abra el [sitio web del Portal de empresa](https://portal.manage.microsoft.com) y haga clic en el botón __Menú__ > __Dispositivos__.  

2. Seleccione el dispositivo en el que es necesario restablecer un código de acceso.  

    ![Captura de pantalla de la página Dispositivos, con dos iconos en los que se muestran dispositivos no identificados con nombres genéricos. Directamente debajo de los dispositivos hay un banner de color gris en el que se solicita al usuario que identifique el dispositivo que está usando o que agregue uno nuevo.](./media/rename-reset-device-step2-1808.png) 

3. Haga clic en **Restablecer código de acceso**. Si la opción de código de acceso no es visible en la parte superior de la página, haga clic en **Más (...)**  > **Restablecer código de acceso**.   

   ![Página de detalles de un dispositivo seleccionado en el sitio web del Portal de empresa, con una lista de vínculos en la parte superior incluidos Cambiar nombre, Quitar, Restablecer dispositivo, Restablecer código de acceso y Bloqueo remoto. ](./media/rename-reset-device-1808.png)   

    ![Captura de pantalla del icono Más, resaltado con una flecha roja.](./media/rename-reset-device-step3-more-1808.png)  

4. Cuando se le solicite, haga clic en **Cerrar sesión**. Cuando se le solicite de nuevo, vuelva a iniciarla. Vuelva a iniciar sesión en el sitio web del Portal de empresa en cinco minutos o el Portal de empresa no restablecerá el código de acceso del dispositivo.  

   > [!NOTE]
   > Debe iniciar sesión de nuevo para confirmar su identidad. El motivo es evitar intentos malintencionados de restablecer el código de acceso del dispositivo.

   ![Capturas de pantalla de ejemplo en las que se muestra un mensaje para cerrar sesión en el Portal de empresa. Los botones de entrada de usuario son Cerrar sesión y Cancelar.](./media/iwp-reset-passcode-popup-1808.png)

5. Aparece un mensaje para avisarle de que el código de acceso del dispositivo existente se va a quitar. Haga clic en **Restablecer código acceso** para confirmar.  
    > [!WARNING]
    > Después de restablecer el código de acceso, cualquiera que tenga acceso físico al dispositivo podrá acceder a la información más personal y corporativa que contenga. Si en la actualidad no tiene el dispositivo en su posesión, no restablezca el código de acceso.  

   ![Captura de pantalla de ejemplo en la que se muestra el segundo mensaje de restablecimiento del código de acceso. Se incluye un vínculo para obtener más información sobre cómo establecer un código de acceso nuevo en la documentación y botones individuales para restablecer el código de acceso y cancelar.](./media/iwp-reset-passcode-popup2-1808.png) 

6. Si va a restablecer el código de acceso para un dispositivo iOS, se quitará el código de acceso existente. En dispositivos Android o Windows, se le emitirá un código de acceso temporal para desbloquear el dispositivo y establecer uno nuevo. 

   > [!NOTE]
   > Puede encontrar la contraseña temporal para los dispositivos Android y Windows en el Portal de empresa, en la página de detalles del dispositivo. Vea la sección [Configuración de un código de acceso nuevo](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode) para obtener más descripciones de código de acceso específicas del sistema operativo.  
   
7. En el dispositivo, vaya a **Configuración** y cambie el código de acceso temporal. 

8. Aparece una marca en la parte superior derecha del sitio web del Portal de empresa. Haga clic para leer la notificación y confirme que el código de acceso se ha restablecido correctamente.  

## <a name="set-up-a-new-passcode"></a>Configuración de un código de acceso nuevo  

En esta sección se describe el restablecimiento del código de acceso y el comportamiento de la contraseña temporal para cada plataforma de dispositivo.  

**Android**: quita el código de acceso existente y crea un código de acceso temporal compuesto de letras y números.

**iOS**: quita el código de acceso existente y no crea un código de acceso temporal. Si usa Touch ID para abrir el dispositivo o realizar compras, debe configurarlo de nuevo.  

**Windows 10 Mobile**: quita el código de acceso existente y crea un código de acceso temporal compuesto de letras y números. Si está configurado, el reconocimiento facial de Windows Hello seguirá funcionando con el dispositivo.

**Windows Phone 8.1**: quita el código de acceso existente y crea un código de acceso temporal compuesto de letras y números.  

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
