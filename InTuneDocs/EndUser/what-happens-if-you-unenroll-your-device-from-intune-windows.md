---
title: "¿Qué ocurre si anula la inscripción del dispositivo Windows de Intune? | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08f31db90f324ef5f93076c4e13bfa5328a15adc
ms.openlocfilehash: ebd1300c490f3d69110a5f1920fd25d1dc5cb850


---


# ¿Qué ocurre si anula la inscripción del dispositivo Windows de Intune?

Use los vínculos de la derecha de esta página, debajo de "En este artículo", para obtener información sobre el tipo de dispositivo que está utilizando.


## Windows 10, Windows 8.1, Windows 8, Windows 7, Vista

-   El dispositivo no aparecerá más en el Portal de empresa y ya no se podrán instalar aplicaciones desde este.

-   Si ha instalado el software cliente de Intune, este se quitará del equipo.

-   El software Intune Endpoint Protection se quitará del equipo. Si el equipo tiene instalado otro software antivirus y está deshabilitado, dicho software podrá habilitarse de nuevo cuando se haya quitado Intune Endpoint Protection. Debe comprobar el equipo después de quitarlo del Portal de empresa.

    > [!IMPORTANT]
    > Si no se vuelve a habilitar el software antivirus o no hay otro software antivirus instalado, el equipo puede ser vulnerable a virus y malware.

-   Todos los valores de configuración que se modificaron cuando se agregó el dispositivo (por ejemplo, deshabilitar la cámara) dejarán de aplicarse.

-   El equipo dejará de recibir actualizaciones de software automáticas o actualizaciones de software antivirus desde el servicio de Intune. Sin embargo, en función de la configuración, el equipo aún podrá recibir actualizaciones a través de Servicios de actualización de Windows Server, Windows Update o Microsoft Update.

Además, para Windows 8.1:

-   No se podrán utilizar las aplicaciones y los datos de la empresa.

-   Algunas aplicaciones de correo, como Correo de Windows, dejarán de tener acceso al correo electrónico de la empresa almacenado en el dispositivo.

-   No se podrá conectar a la red de su empresa mediante Wi-Fi o una red privada virtual.

-   Es posible que deje de tener acceso en su dispositivo a algunos recursos de la empresa, como recursos compartidos de archivos o sitios web internos.

## Windows 10 Mobile y Windows Phone 8.1

-   La aplicación Portal de empresa se desinstala del dispositivo, es decir, el dispositivo ya no aparecerá en el Portal de empresa y no se podrán instalar aplicaciones desde la aplicación Portal de empresa o desde el sitio web de Portal de empresa.

-   No se podrán utilizar las aplicaciones y los datos de la empresa.

-   Dejará de aplicarse cualquier configuración que se haya modificado en el dispositivo cuando se agregó, por ejemplo, deshabilitar la cámara o exigir una determinada longitud de la contraseña.

    > [!IMPORTANT]
    > La única excepción son las directivas de cifrado, que se seguirán aplicando. Si la directiva de la compañía requería el cifrado de Windows Phone, la única manera de descifrar el teléfono es restablecerlo a través del menú **Configuración** de Windows Phone.

## Windows RT con Windows 8.1

-   La aplicación Portal de empresa se desinstala del dispositivo, es decir, el dispositivo ya no aparecerá en el Portal de empresa y no se podrán instalar aplicaciones desde el Portal de empresa.

-   No se podrán utilizar las aplicaciones y los datos de la empresa.

-   Dejará de aplicarse cualquier configuración que se haya modificado en el dispositivo cuando se agregó, por ejemplo, deshabilitar la cámara o exigir una determinada longitud de la contraseña.

-   Ya no se podrá conectar a la red de su empresa mediante Wi-Fi o una red privada virtual.

-   Es posible que deje de tener acceso en su dispositivo a algunos recursos de la empresa, como recursos compartidos de archivos o sitios web internos.

-   Algunas aplicaciones de correo, como Correo de Windows, dejarán de tener acceso al correo electrónico de la empresa almacenado en el dispositivo.

Si se quita un dispositivo Windows RT, ocurre lo siguiente:

-   La aplicación Portal de empresa se desinstala del dispositivo, es decir, el dispositivo ya no aparecerá en el Portal de empresa y no se podrán instalar aplicaciones desde el Portal de empresa.

-   No se podrán utilizar las aplicaciones y los datos de la empresa.

-   Dejará de aplicarse cualquier configuración que se haya modificado en el dispositivo cuando se agregó, por ejemplo, deshabilitar la cámara o exigir una determinada longitud de la contraseña.

Si tiene alguna pregunta, póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).




<!--HONumber=Oct16_HO2-->


