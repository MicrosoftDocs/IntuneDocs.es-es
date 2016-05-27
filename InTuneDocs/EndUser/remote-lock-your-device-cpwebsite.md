---
# required metadata

title: Bloquear un dispositivo de forma remota desde el sitio web del Portal de empresa | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Bloquear un dispositivo de forma remota desde el sitio web del Portal de empresa

Si el dispositivo se ha perdido o ha sido robado, es posible bloquearlo mediante la opción Bloqueo remoto del [sitio web del Portal de empresa](http://portal.manage.microsoft.com). Bloqueo remoto funciona en los siguientes tipos de dispositivos:

Plataforma  |Detalles sobre compatibilidad  
---------|---------
Android | Compatible.       
iOS | Compatible.
Windows 10 Mobile | Compatible únicamente si el teléfono tiene establecido un código de acceso     
Windows 10 Escritorio | No compatible  
Windows Phone 8,1 | Compatible únicamente si el teléfono tiene establecido un código de acceso
Windows Phone 8.0 | No compatible
PC (Windows 8.0 y anteriores) | No compatible       
PC (Windows 8.1) | No compatible

</br>
Para usar Bloqueo remoto para bloquear el dispositivo:

1.  En el [sitio web del Portal de empresa](http://portal.manage.microsoft.com), puntee en el nombre del dispositivo que quiera bloquear.

2.  Puntee en **Bloqueo remoto**..

    Después de puntear en **Bloqueo remoto**, aparece el estado "Bloqueo remoto pendiente".  Cuando el bloqueo remoto se realiza correctamente, el estado cambia a "El bloqueo remoto se realizó correctamente".

    El estado se muestra en tres lugares:

    * El área de notificaciones del sitio web. 
    * La página de detalles del dispositivo.
    * El icono que muestra el nombre del dispositivo en la sección Mis dispositivos de la página.

    Si ve una notificación "Error de bloqueo remoto", espere unos minutos y vuelva a intentar bloquear el dispositivo. Después de puntear para intentarlo de nuevo, el estado vuelve a cambiar a "Bloqueo remoto pendiente". 

    Si un reintento no funciona, póngase en contacto con el administrador de TI para obtener ayuda. Si encuentra el dispositivo y quiere desbloquearlo después de usar Bloqueo remoto, simplemente escriba el código de acceso.


### Consulte también
[Usar el sitio web del Portal de empresa de Intune](using-the-intune-company-portal-website.md)

<!--HONumber=May16_HO1-->

