---
# required metadata

title: ¿Qué ocurre si anula la inscripción del dispositivo de Intune? | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: priyar
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# ¿Qué ocurre si anula la inscripción del dispositivo de Intune?

Para más información sobre lo que ocurre, seleccione el vínculo de la sección anterior "En este artículo" correspondiente al tipo de dispositivo que use.

- [Windows 10 Mobile, 8.1, Windows 8, Windows 7, Vista](#windows-10-mobile--8-1,-windows-8,-windows-7,-vista)
- [Windows 10, Windows 8.1 o Windows Phone 8](#windows-10--windows-8-1-or-windows-phone-8)
- [Windows RT con Windows 8.1 o Windows RT](#windows-rt-running-windows-8-1-or-windows-rt)


## Windows 10, Windows 8.1, Windows 8, Windows 7, Vista

-   El dispositivo no aparecerá más en el Portal de empresa y ya no se podrán instalar aplicaciones desde este.

-   Si ha instalado el software cliente de Intune, este se quitará del equipo.

-   El software Intune Endpoint Protection se quitará del equipo. Si el equipo tiene instalado otro software antivirus y está deshabilitado, dicho software podrá habilitarse de nuevo cuando se haya quitado Intune Endpoint Protection. Debe comprobar el equipo después de quitarlo del Portal de empresa.

    > [!IMPORTANT] Si no se vuelve a habilitar el software antivirus o no hay instalado otro software antivirus, el equipo puede ser vulnerable a virus y malware.

-   Todos los valores de configuración que se modificaron cuando se agregó el dispositivo (por ejemplo, deshabilitar la cámara) dejarán de aplicarse.

-   El equipo dejará de recibir actualizaciones de software automáticas o actualizaciones de software antivirus desde el servicio de Intune. Sin embargo, en función de la configuración, el equipo aún podrá recibir actualizaciones a través de Servicios de actualización de Windows Server, Windows Update o Microsoft Update.

Además, para Windows 8.1:

-   No se podrán utilizar las aplicaciones y los datos de la empresa.

-   Algunas aplicaciones de correo, como Correo de Windows, dejarán de tener acceso al correo electrónico de la empresa almacenado en el dispositivo.

-   No se podrá conectar a la red de su empresa mediante Wi-Fi o una red privada virtual.

-   Es posible que deje de tener acceso en su dispositivo a algunos recursos de la empresa, como recursos compartidos de archivos o sitios web internos.

## Windows 10 Mobile, Windows Phone 8.1 o Windows Phone 8

-   La aplicación Portal de empresa se desinstala del dispositivo, es decir, el dispositivo ya no aparecerá en el Portal de empresa y no se podrán instalar aplicaciones desde la aplicación Portal de empresa o desde el sitio web de Portal de empresa.

-   No se podrán utilizar las aplicaciones y los datos de la empresa.

-   Dejará de aplicarse cualquier configuración que se haya modificado en el dispositivo cuando se agregó, por ejemplo, deshabilitar la cámara o exigir una determinada longitud de la contraseña.

    > [!IMPORTANT]
    > La única excepción son las directivas de cifrado, que se seguirán aplicando. Si la directiva de la compañía requería el cifrado de Windows Phone, la única manera de descifrar el teléfono es restablecerlo a través del menú **Configuración** de Windows Phone.

## Windows RT con Windows 8.1 o Windows RT

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

### Consulte también
[Usar un dispositivo Windows con Intune](using-your-windows-device-with-intune.md)

<!--HONumber=Jun16_HO2-->


