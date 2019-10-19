---
title: Bloquear un dispositivo desde el portal de empresa | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: c81c13d5da8eac1616ab7274b484befaa5685511
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502161"
---
# <a name="remotely-lock-your-device-from-the-company-portal-website"></a>Bloquear un dispositivo de forma remota desde el sitio web del Portal de empresa

Bloquee de forma remota un dispositivo perdido o robado desde la aplicación Portal de empresa. Si el dispositivo lo permite, esta configuración bloquea la pantalla del dispositivo, con independencia de su ubicación. Una persona debe escribir el código de acceso correcto antes de que el dispositivo se pueda desbloquear y volver a usar.   

El valor de bloqueo remoto funciona para:

* Android
* iOS
* macOS
* Windows 10
* Windows 10 Mobile (si el dispositivo ya tenía un código de acceso establecido)
* Windows Phone 8.1 (si el dispositivo ya tenía un código de acceso establecido)  

1. En el [sitio web del Portal de empresa](https://portal.manage.microsoft.com), haga clic en el botón __Menú__ > __Dispositivos__.  

2. Seleccione el dispositivo que quiera bloquear.  

    ![Captura de pantalla de la página Dispositivos, con dos iconos en los que se muestran dispositivos no identificados con nombres genéricos. Directamente debajo de los dispositivos hay un banner de color gris en el que se solicita al usuario que identifique el dispositivo que está usando o que agregue uno nuevo.](./media/rename-reset-device-step2-1808.png) 

3. Haga clic en **Bloqueo remoto**. Si la opción de bloqueo no es visible en la parte superior de la página, haga clic en **Más (...)**  > **Bloqueo remoto**.  

   ![Página de detalles de un dispositivo seleccionado en el sitio web del Portal de empresa, con una lista de vínculos en la parte superior incluidos Cambiar nombre, Quitar, Restablecer dispositivo, Restablecer código de acceso y Bloqueo remoto. ](./media/rename-reset-device-1808.png) 

    ![Vista ampliada del icono Más, resaltado con una flecha de color rojo.](./media/rename-reset-device-step3-more-1808.png)    

4. Aparece un mensaje para advertir que se va a bloquear el dispositivo. Pulse **Bloqueo remoto** para confirmar.

Después de la confirmación, el Portal de empresa intenta bloquear el dispositivo. Durante este tiempo, aparece un mensaje de "Bloqueo remoto pendiente". Cuando el dispositivo está bloqueado, el estado aparece como "El bloqueo remoto se realizó correctamente".  

El estado Bloqueo remoto se muestra en tres lugares:

* El área de notificaciones del sitio web.
* La página **Detalles** del dispositivo.
* El icono que muestra el nombre del dispositivo en la sección **Dispositivos** de la página.  

> [!Note]
> Si ve una notificación de error de bloqueo remoto, espere unos minutos. Después, intente bloquear el dispositivo de nuevo. El estado volverá a cambiar a "Bloqueo remoto pendiente". Si el reintento no funciona, póngase en contacto con el servicio de soporte técnico de la empresa para obtener ayuda.

Si encuentra el dispositivo y quiere desbloquearlo después de usar Bloqueo remoto, simplemente escriba el código de acceso.  

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
