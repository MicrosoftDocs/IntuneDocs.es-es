---
title: ¿Qué ocurre si anula la inscripción del dispositivo Windows? | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: d970db26aa9f48063ed77fb6af1503ee9d29dc67
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75858784"
---
# <a name="what-happens-if-you-unenroll-your-windows-device-from-intune"></a>¿Qué ocurre si anula la inscripción del dispositivo Windows de Intune?

Use los vínculos de la derecha de esta página, debajo de **En este artículo**, para obtener información sobre el tipo de dispositivo que está usando.


## <a name="windows-10-windows-81-windows-8-windows-7-windows-vista"></a>Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista

- El dispositivo ya no aparece en el Portal de empresa ni se pueden instalar aplicaciones desde este.

- Si ha instalado el software cliente de Intune, este se quitará del equipo.

- El software Intune Endpoint Protection se quitará del equipo. Si el equipo tiene instalado otro software antivirus y está deshabilitado, dicho software podrá habilitarse de nuevo cuando se haya quitado Intune Endpoint Protection. Compruebe el equipo después de quitarlo del Portal de empresa.

    > [!IMPORTANT]
    > Si no se vuelve a habilitar el software antivirus o no hay otro software antivirus instalado, el equipo puede ser vulnerable a virus y malware.

- Todos los valores de configuración que se modificaron cuando se agregó el dispositivo (por ejemplo, deshabilitar la cámara) dejarán de aplicarse.

- El equipo deja de recibir actualizaciones de software automáticas o actualizaciones de software antivirus desde el servicio de Intune. Sin embargo, en función de la configuración, el equipo aún podría recibir actualizaciones a través de Servicios de actualización de Windows Server, Windows Update o Microsoft Update.

Además, para Windows 8.1:

- No se podrán utilizar las aplicaciones y los datos de la empresa.

- Algunas aplicaciones de correo, como Correo de Windows, ya no pueden acceder al correo electrónico de la empresa almacenado en el dispositivo.

- Es posible que no se pueda conectar a la red de la empresa mediante Wi-Fi o una red privada virtual.

- Es posible que ya no tenga acceso en el dispositivo a algunos recursos de la empresa, como recursos compartidos de archivos o sitios web internos.

## <a name="windows-10-mobile-and-windows-phone-81"></a>Windows 10 Mobile y Windows Phone 8.1

- Se desinstalará la aplicación Portal de empresa del dispositivo. Esto significa que el dispositivo ya no aparece en el Portal de empresa ni se pueden instalar aplicaciones desde la aplicación Portal de empresa ni desde el sitio web del Portal de empresa.

- No se podrán utilizar las aplicaciones y los datos de la empresa.

- Dejará de aplicarse cualquier configuración que se modificara en el dispositivo al agregarlo, por ejemplo, deshabilitar la cámara o exigir una determinada longitud de la contraseña.

    > [!IMPORTANT]
    > La única excepción son las directivas de cifrado, que se siguen aplicando. Si la directiva de su empresa exigía cifrar el dispositivo Windows Phone, la única forma de hacerlo es restablecerlo mediante el menú **Configuración**.

## <a name="windows-rt-running-windows-81"></a>Windows RT con Windows 8.1

- Se desinstalará la aplicación Portal de empresa del dispositivo. Eso significa que el dispositivo ya no aparece en el Portal de empresa ni se pueden instalar aplicaciones desde este.

- No se podrán utilizar las aplicaciones y los datos de la empresa.

- Dejará de aplicarse cualquier configuración que se modificara en el dispositivo al agregarlo, por ejemplo, deshabilitar la cámara o exigir una determinada longitud de la contraseña.

- Es posible que ya no se pueda conectar a la red de su empresa mediante Wi-Fi o una red privada virtual.

- Es posible que ya no tenga acceso en el dispositivo a algunos recursos de la empresa, como recursos compartidos de archivos o sitios web internos.

- Algunas aplicaciones de correo, como Correo de Windows, ya no pueden acceder al correo electrónico de la empresa almacenado en el dispositivo.

Si se quita un dispositivo Windows RT, ocurre lo siguiente:

- Se desinstalará la aplicación Portal de empresa del dispositivo. Eso significa que el dispositivo ya no aparece en el Portal de empresa ni se pueden instalar aplicaciones desde este.

- No se podrán utilizar las aplicaciones y los datos de la empresa.

- Dejará de aplicarse cualquier configuración que se modificara en el dispositivo al agregarlo, por ejemplo, deshabilitar la cámara o exigir una determinada longitud de la contraseña.

Si tiene alguna pregunta, póngase en contacto con el equipo de soporte técnico de su empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
