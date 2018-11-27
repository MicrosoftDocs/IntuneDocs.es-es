---
title: Mensajes de Portal de empresa que los usuarios pueden ver en los dispositivos
titlesuffix: Microsoft Intune
description: Comprenda los distintos mensajes que los usuarios finales pueden ver en Portal de empresa.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/09/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 44e7307997df67ad1c1ae6170da3bcc13e99070d
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185056"
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>Ayudar a que los usuarios finales comprendan los mensajes de la aplicación Portal de empresa

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

> [!NOTE]
> La siguiente información se aplica solo a dispositivos con Android 6.0 y versiones posteriores.

Comprenda los distintos mensajes de la aplicación que los usuarios finales pueden ver en Portal de empresa. Normalmente, estos mensajes de la aplicación se muestran en distintos puntos del proceso de inscripción. Descubra dónde aparecen, cuál es su significado y qué ocurre si los usuarios deniegan el acceso. Además, aprenderá a explicar mejor los mensajes a los usuarios.

- __¿Permitir que el Portal de empresa realice y administre llamadas telefónicas?__
- __¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?__

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>¿Permitir que Portal de empresa realice y administre llamadas telefónicas?

### <a name="where-it-appears"></a>Dónde aparece
El mensaje **¿Permitir que Portal de empresa realice y administre llamadas telefónicas?** aparece cuando los usuarios pulsan **Inscribir** en la aplicación Portal de empresa mientras inscriben su dispositivo.

### <a name="what-it-means"></a>Significado
Al aceptar este aviso, los usuarios permiten que se envíen los números de teléfono y de IMEI del dispositivo al servicio Intune. Aparecerán en la consola de administración en la página __Hardware__.

> [!NOTE]
> **La aplicación Portal de empresa nunca hace ni administra llamadas telefónicas.** Google controla el texto del mensaje y no se puede cambiar.

Para ver la página **Hardware**, debe ir a **Grupos** > **All mobile devices (Todos los dispositivos móviles)** > **Dispositivos**. Seleccione el dispositivo del usuario y vaya a **Ver propiedades** > **Hardware**.

### <a name="what-happens-if-users-deny-access"></a>Qué sucede si los usuarios deniegan el acceso
Si los usuarios deniegan el acceso, pueden seguir usando la aplicación de Portal de empresa e inscribir su dispositivo. Sin embargo, el número de teléfono y el IMEI del dispositivo estarán en blanco en la página de __hardware__ de la consola de administración. La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla de verificación **Never ask again** (No volver a preguntar) que los usuarios pueden marcar para detener el aviso.

Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparecerá la próxima vez que los usuarios inicien sesión en la aplicación Portal de empresa después de la inscripción.

Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración** > **Aplicaciones** > **Portal de empresa** > **Permisos** > **Teléfono** y activarlo.

### <a name="how-to-explain-this-to-your-users"></a>Cómo explicar esto a los usuarios
Envíe a los usuarios a [Inscribir el dispositivo Android en Intune](/intune-user-help/enroll-your-device-in-intune-android) para más información.

## <a name="allow-company-portal-to-access-your-contacts"></a>Allow Company Portal to access your contacts? (¿Permitir que el portal de empresa tenga acceso a los contactos?)

### <a name="where-it-appears"></a>Dónde aparece
El mensaje **¿Permitir que el portal de empresa tenga acceso a los contactos?** aparece cuando los usuarios pulsan **Inscribir** en la aplicación Portal de empresa mientras inscriben el dispositivo.

### <a name="what-it-means"></a>Significado
Al aceptar este aviso, los usuarios permiten a Intune crear su cuenta de trabajo y administrar la identidad de Azure Active Directory registrada para el usuario en ese dispositivo.

> [!NOTE]
> **Microsoft nunca accede a los contactos.** Google controla el texto del mensaje y no se puede cambiar.

### <a name="what-happens-if-users-deny-access"></a>Qué sucede si los usuarios deniegan el acceso
Si los usuarios deniegan el acceso, el dispositivo no se inscribirá en Intune ni se podrá administrar. La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para detener el aviso.

Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios inicien sesión en la aplicación Portal de empresa después de la inscripción.

Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración** > **Aplicaciones** > **Portal de empresa** > **Permisos** > **Teléfono** y activarlo.

### <a name="how-to-explain-this-to-your-users"></a>Cómo explicar esto a los usuarios
Envíe a los usuarios a [Inscribir el dispositivo Android en Intune](/intune-user-help/enroll-your-device-in-intune-android) para más información.

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?

### <a name="where-it-appears"></a>Dónde aparece
El mensaje **¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?** aparece cuando los usuarios pulsan **Enviar datos** para enviar registros a su administrador de TI.

### <a name="what-it-means"></a>Significado
Al aceptar este aviso, los usuarios permiten que su dispositivo escriba registros de datos en la tarjeta SD de este. Esto también permite que esos registros se trasladen mediante un cable USB.   

> [!NOTE]
> **La aplicación Portal de empresa nunca tiene acceso a las fotos, elementos multimedia ni archivos de los usuarios.** Google controla el texto del mensaje y no se puede cambiar.

### <a name="what-happens-if-users-deny-access"></a>Qué sucede si los usuarios deniegan el acceso
Si los usuarios deniegan el acceso, podrán enviar registros de datos por correo electrónico, pero los registros no se copiarán en la tarjeta SD del dispositivo.

La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para que el mensaje no se vuelva a mostrar. Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios intenten enviar registros. No obstante, si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración** > **Aplicaciones** > **Portal de empresa** > **Permisos** > **Almacenamiento** y activar el permiso.


### <a name="how-to-explain-this-to-your-users"></a>Cómo explicar esto a los usuarios
Envíe a sus usuarios a [Enviar registros al administrador de TI mediante correo electrónico](/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>El servicio de soporte técnico de su empresa debe concederle acceso a sus recursos

### <a name="where-it-appears"></a>Dónde aparece
Si no ha agregado la aplicación Portal de empresa a las listas **Aplicaciones permitidas** o **Aplicaciones exentas** y un usuario intenta iniciar sesión, se producirá un error en el inicio de sesión. Se mostrará el siguiente mensaje:

> **El servicio de soporte técnico de su empresa debe concederle acceso a sus recursos**  
> Su empresa está usando directivas de Windows Information Protection para proteger su dispositivo. El servicio de soporte técnico de su empresa tendrá que asegurarse de que permite que Portal de empresa pueda acceder a esos recursos.

### <a name="what-it-means"></a>Significado

Agregue Portal de empresa a las listas **Aplicaciones permitidas** o **Aplicaciones exentas** en la directiva de protección de la aplicación Windows Information Protection (WIP). Para obtener más información, consulte [Creación e implementación de una directiva de protección de aplicaciones de Windows Information Protection (WIP) con Intune](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune).

### <a name="see-also"></a>Consulta también
[Qué decirles a los usuarios finales sobre el uso de Intune](end-user-educate.md)
