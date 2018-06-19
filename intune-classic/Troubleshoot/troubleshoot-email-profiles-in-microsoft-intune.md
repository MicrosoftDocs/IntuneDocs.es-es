---
title: Solucionar problemas de perfiles de correo electrónico
description: Perfiles de correo electrónico y cómo se pueden solucionar.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e001d1df510ac249687be9f5690c16f0a738c3e2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31013745"
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Solucionar problemas de perfiles de correo electrónico en Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Aquí se indican algunos problemas relacionados con los perfiles de correo electrónico y cómo se pueden solucionar.

Si esta información no soluciona el problema, vea [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune) para conocer otras formas de obtener ayuda.


## <a name="unable-to-send-images-from--email-account"></a>No se pueden enviar imágenes desde la cuenta de correo electrónico
Los usuarios que tienen cuentas de correo electrónico configuradas automáticamente no pueden enviar imágenes ni fotos desde sus dispositivos.
Esto ocurre cuando no está habilitada la opción **Allow e-mail to be sent from third-party applications** (Permitir que se envíe correo electrónico desde aplicaciones de terceros).

### <a name="intune-solution"></a>Solución de Intune

1.  Abra la consola de administración de Microsoft Intune, seleccione la carga de trabajo **Directiva** &gt; **Directiva de configuración**.

2.  Seleccione el perfil de correo electrónico y luego **Editar**.

3.  Seleccione **Permitir que se envíe correo electrónico desde aplicaciones de terceros.**

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integrado con la solución de Intune

1.  Abra la consola de Configuration Manager &gt; **Activos y compatibilidad**.

2.  Expanda **Introducción** -&gt;**Configuración de cumplimiento** -&gt; **Acceso a los recursos de la compañía** y seleccione **Perfiles de correo electrónico**.

3.  Haga clic con el botón derecho en el perfil de correo electrónico y abra **Propiedades**.

4.  En la pestaña **Configuración de sincronización**, seleccione **Permitir el envío de correo electrónico desde aplicaciones de terceros**.


## <a name="device-already-has-an-email-profile-installed"></a>El dispositivo ya tiene instalado un perfil de correo electrónico

Si el usuario ha instalado un perfil de correo electrónico antes del aprovisionamiento de un perfil mediante Intune, el resultado de la implementación del perfil de correo electrónico de Intune depende de la plataforma del dispositivo:

-**iOS**: Intune detecta un perfil de correo electrónico existente duplicado sobre la base del nombre de host y la dirección de correo electrónico. El perfil de correo electrónico duplicado que ha creado el usuario bloquea la implementación de un perfil de Intune creado por el administrador. Este es un problema común, ya que los usuarios de iOS suelen crear un perfil de correo y luego inscribirse. El portal de empresa informará al usuario de que no son compatibles debido a su perfil de correo configurado manualmente y le pedirá que quite ese perfil. El usuario debe quitar su perfil de correo para que se pueda implementar el perfil de Intune. Para evitar el problema, indique a los usuarios que se inscriban antes de instalar un perfil de correo y que permitan que Intune implemente el perfil.

-**Windows**: Intune detecta un perfil de correo electrónico existente duplicado sobre la base del nombre de host y la dirección de correo electrónico. Intune sobrescribe el perfil de correo electrónico existente que ha creado el usuario.

-**Samsung KNOX Standard**: Intune identifica una cuenta de correo electrónico duplicada basada en la dirección de correo electrónico y la sobrescribe con el perfil de Intune. Si el usuario configura esa cuenta, el perfil de Intune la vuelve a sobrescribir. Tenga en cuenta que esto puede confundir al usuario cuya configuración de cuenta se sobrescribe.

Dado que Samsung KNOX no usa el nombre de host para identificar el perfil, recomendamos que no cree varios perfiles de correo electrónico para implementar en la misma dirección de correo electrónico en diferentes hosts, ya que estos se sobrescriben entre sí.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>Error 0x87D1FDE8 para dispositivo KNOX Standard
**Problema**: después de crear e implementar un perfil de correo electrónico de Exchange Active Sync de Samsung KNOX Standard para varios dispositivos Android, se notifica el error **0x87D1FDE8** o **error de corrección** en las propiedades del dispositivo, pestaña de directiva.

Revise la configuración de su perfil EAS de Samsung KNOX y la directiva de origen. Ya no se admite la opción de sincronización de notas de Samsung y no debe estar seleccionada en el perfil. Asegúrese de que los dispositivos han tenido tiempo suficiente para procesar la directiva (hasta 24 horas).

## <a name="next-steps"></a>Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).
