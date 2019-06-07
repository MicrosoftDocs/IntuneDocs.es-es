---
title: Solución de problemas de perfiles de correo electrónico en Microsoft Intune - Azure | Microsoft Docs
description: Consulte los problemas comunes con los perfiles de correo electrónico en Microsoft Intune y sus soluciones, incluidos los perfiles de correo electrónico duplicados y errores en dispositivos Samsung KNOX Standard con Android.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0fe37deb63457fef869df0f7263970a4e53cb29
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402721"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Problemas comunes y resoluciones con perfiles de correo electrónico en Microsoft Intune

Revise algunos problemas comunes relacionados con los perfiles de correo electrónico y cómo se pueden solucionar.

## <a name="device-already-has-an-email-profile-installed"></a>El dispositivo ya tiene instalado un perfil de correo electrónico

Si los usuarios crean un perfil de correo electrónico antes de inscribirse en Intune, es posible que el perfil de correo electrónico de Intune no funcione según lo esperado:

- **iOS:** Intune detecta un perfil de correo electrónico existente duplicado sobre la base del nombre de host y la dirección de correo electrónico. El perfil de correo electrónico creado por el usuario bloquea la implementación del perfil creado por Intune. Este es un problema común, ya que los usuarios de iOS suelen crear un perfil de correo electrónico y luego se inscriben. La aplicación Portal de empresa indica que el usuario no cumple con los requisitos y podría pedirle al usuario que quite el perfil de correo electrónico.

  El usuario debe quitar su perfil de correo electrónico para que el perfil de Intune pueda implementarse. Para evitar este problema, indique a los usuarios que realicen la inscripción y permita que Intune implemente el perfil de correo electrónico. Luego, los usuarios podrán crear su perfil de correo electrónico.

- **Windows:** Intune detecta un perfil de correo electrónico existente duplicado sobre la base del nombre de host y la dirección de correo electrónico. Intune sobrescribe el perfil de correo electrónico existente que ha creado el usuario.

- **Samsung KNOX Standard**: Intune identifica una cuenta de correo electrónico duplicada basada en la dirección de correo electrónico y la sobrescribe con el perfil de Intune. Si el usuario configura esa cuenta, el perfil de Intune la vuelve a sobrescribir. Esto puede confundir al usuario cuya configuración de cuenta se sobrescribe.

Samsung KNOX no usa el nombre de host para identificar el perfil. Le recomendamos que no cree varios perfiles de correo electrónico para implementar la misma dirección de correo electrónico en varios host, puesto que se sobrescribirán entre sí.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Error 0x87D1FDE8 para dispositivo KNOX Standard

**Problema**: después de crear e implementar un perfil de correo electrónico de Exchange Active Sync de Samsung KNOX Standard para distintos dispositivos Android, se notifica el error **0x87D1FDE8** o **error de corrección** en las propiedades del dispositivo > pestaña de directiva.

Revise la configuración de su perfil EAS de Samsung KNOX y la directiva de origen. Ya no se admite la opción de sincronización de notas de Samsung y no debe estar seleccionada en el perfil. Asegúrese de que los dispositivos tengan tiempo suficiente para procesar la directiva (hasta 24 horas).

## <a name="unable-to-send-images-from--email-account"></a>No se pueden enviar imágenes desde la cuenta de correo electrónico

Se aplica a Intune en el Portal de Azure clásico.

Los usuarios que tienen cuentas de correo electrónico configuradas automáticamente no pueden enviar imágenes ni fotos desde sus dispositivos. Esto puede ocurrir si no está habilitada la opción **Allow e-mail to be sent from third-party applications** (Permitir que se envíe correo electrónico desde aplicaciones de terceros).

### <a name="intune-solution"></a>Solución de Intune

1. Abra la consola de administración de Microsoft Intune, seleccione la carga de trabajo **Directiva** > **Directiva de configuración**.

2. Seleccione el perfil de correo electrónico y luego **Editar**.

3. Seleccione **Permitir que se envíe correo electrónico desde aplicaciones de terceros.**

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integrado con la solución de Intune

1. Abra la consola de Configuration Manager > **Recursos y cumplimiento**.

2. Expanda **Introducción** > **Configuración de cumplimiento** > **Acceso a los recursos de la compañía** y seleccione **Perfiles de correo electrónico**.

3. Haga clic con el botón derecho en el perfil de correo electrónico y abra **Propiedades**.

4. En la pestaña **Configuración de sincronización**, seleccione **Permitir el envío de correo electrónico desde aplicaciones de terceros**.

## <a name="next-steps"></a>Pasos siguientes

Obtenga [ayuda de soporte técnico de Microsoft](get-support.md) o use los [foros de la comunidad](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).