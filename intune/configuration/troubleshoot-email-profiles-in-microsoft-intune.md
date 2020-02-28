---
title: Solución de problemas de perfiles de correo electrónico en Microsoft Intune - Azure | Microsoft Docs
description: Consulte los problemas comunes con los perfiles de correo electrónico en Microsoft Intune y sus soluciones, incluidos los perfiles de correo electrónico duplicados y errores en dispositivos Samsung KNOX Standard con Android.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a19830130f992a002b73402f5e13a8f062539917
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512677"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Problemas comunes y resoluciones con perfiles de correo electrónico en Microsoft Intune

Revise algunos problemas comunes relacionados con los perfiles de correo electrónico y cómo se pueden solucionar.

## <a name="what-you-need-to-know"></a>Aspectos que debe saber

- Se implementan perfiles de correo electrónico para el usuario que ha inscrito el dispositivo. Para configurar el perfil de correo electrónico, Intune usa las propiedades de Azure Active Directory (AD) del perfil de correo electrónico del usuario durante la inscripción. [Agregar la configuración de correo electrónico a los dispositivos](email-settings-configure.md) puede ser un buen recurso.
- En Android Enterprise, implemente Gmail o Nine for Work mediante la instancia de Google Play Store administrada. En [Agregar aplicaciones de Google Play administrado](../apps/apps-add-android-for-work.md) se enumeran los pasos.
- Microsoft Outlook para iOS/iPadOS y Android no admiten perfiles de correo electrónico. En su lugar, implemente una directiva de configuración de aplicaciones. Para más información, consulte [Opciones de configuración de Microsoft Outlook](../apps/app-configuration-policies-outlook.md).
- Es posible que los perfiles de correo electrónico destinados a grupos de dispositivos (no a grupos de usuarios) no se entreguen en el dispositivo. Cuando el dispositivo tiene un usuario primario, debe funcionar la identificación de dispositivos. Si el perfil de correo electrónico incluye certificados de usuario, asegúrese de establecer el destino de los grupos de usuarios.
- Es posible que se pida repetidas veces a los usuarios que escriban su contraseña en el perfil de correo electrónico. En este escenario, compruebe todos los certificados a los que se hace referencia en el perfil de correo electrónico. Si uno de los certificados no está destinado a un usuario, Intune vuelve a intentar la implementación del perfil de correo electrónico.

## <a name="device-already-has-an-email-profile-installed"></a>El dispositivo ya tiene instalado un perfil de correo electrónico

Si los usuarios crean un perfil de correo electrónico antes de inscribirse en Intune u Office 365 MDM, es posible que el perfil de correo electrónico implementado por Intune no funcione según lo previsto:

- **iOS/iPadOS**: Intune detecta un perfil de correo electrónico existente duplicado según el nombre de host y la dirección de correo electrónico. El perfil de correo electrónico creado por el usuario bloquea la implementación del perfil creado por Intune. Este es un problema común, ya que los usuarios de iOS/iPadOS suelen crear un perfil de correo electrónico y luego se inscriben. La aplicación Portal de empresa indica que el usuario no cumple con los requisitos y podría pedirle al usuario que quite el perfil de correo electrónico.

  El usuario debe quitar su perfil de correo electrónico para que el perfil de Intune pueda implementarse. Para evitar este problema, indique a los usuarios que realicen la inscripción y permita que Intune implemente el perfil de correo electrónico. Luego, los usuarios podrán crear su perfil de correo electrónico.

- **Windows**: Intune detecta un perfil de correo electrónico existente duplicado según el nombre de host y la dirección de correo electrónico. Intune sobrescribe el perfil de correo electrónico existente que ha creado el usuario.

- **Samsung KNOX Standard**: Intune identifica una cuenta de correo electrónico duplicada según la dirección de correo electrónico y la sobrescribe con el perfil de Intune. Si el usuario configura esa cuenta, el perfil de Intune la vuelve a sobrescribir. Esto puede confundir al usuario cuya configuración de cuenta se sobrescribe.

Samsung KNOX no usa el nombre de host para identificar el perfil. Le recomendamos que no cree varios perfiles de correo electrónico para implementar la misma dirección de correo electrónico en varios host, puesto que se sobrescribirán entre sí.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Error 0x87D1FDE8 para dispositivo KNOX Standard

**Problema**: después de crear e implementar un perfil de correo electrónico de Exchange Active Sync para Samsung KNOX Standard en distintos dispositivos Android, se notifica el error **0x87D1FDE8** o **error de corrección** en las propiedades del dispositivo > pestaña de directiva.

Revise la configuración de su perfil EAS de Samsung KNOX y la directiva de origen. Ya no se admite la opción de sincronización de notas de Samsung y no debe estar seleccionada en el perfil. Asegúrese de que los dispositivos tengan tiempo suficiente para procesar la directiva (hasta 24 horas).

## <a name="unable-to-send-images-from--email-account"></a>No se pueden enviar imágenes desde la cuenta de correo electrónico

Los usuarios que tienen cuentas de correo electrónico configuradas automáticamente no pueden enviar imágenes ni fotos desde sus dispositivos. Esto puede ocurrir si no está habilitada la opción **Allow e-mail to be sent from third-party applications** (Permitir que se envíe correo electrónico desde aplicaciones de terceros).

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración**.
3. Seleccione el perfil de correo electrónico > **Propiedades** > **Configuración**.
4. Establezca la opción **Allow e-mail to be sent from third-party applications** (Permitir que se envíe correo electrónico desde aplicaciones de terceros) en **Habilitar**.

## <a name="next-steps"></a>Pasos siguientes

Obtenga [ayuda de soporte técnico de Microsoft](../fundamentals/get-support.md) o use los [foros de la comunidad](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
