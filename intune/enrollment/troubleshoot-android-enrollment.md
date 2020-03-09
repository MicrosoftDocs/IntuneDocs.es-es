---
title: Solución de problemas de dispositivos Android Enterprise en Microsoft Intune
description: Sugerencias para solucionar algunos de los problemas más habituales a la hora de inscribir dispositivos Android en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/25/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04c726c1dc6af7e92b75335d105de605ef00e712
ms.sourcegitcommit: 8b716db3c0fdbb7dff62497ec283902a5069a343
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652375"
---
# <a name="troubleshoot-android-enterprise-device-problems-in-microsoft-intune"></a>Solución de problemas de dispositivos Android Enterprise en Microsoft Intune

Este artículo ayuda a los administradores de Intune a comprender y a solucionar problemas relacionados con los dispositivos Android Enterprise en Intune.

## <a name="apps-on-android-enterprise-devices"></a>Aplicaciones en dispositivos Android Enterprise

### <a name="managed-google-play-apps-that-arent-deployed-through-intune-are-displayed-in-the-work-profile"></a>Aplicaciones de Google Play administrado no implementadas mediante Intune que se muestran en el perfil de trabajo
El OEM del dispositivo puede habilitar las aplicaciones del sistema en el perfil de trabajo en el momento de crear el perfil de trabajo. Es algo que no controla el proveedor de MDM.

Para solucionar el problema, siga estos pasos:

  1. Recopile los registros de Portal de empresa.
  2. Observe qué aplicaciones aparecen en el perfil de trabajo de forma inesperada.
  3. Anule la inscripción del dispositivo en Intune y desinstale Portal de empresa.
  4. Instale la aplicación [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc), que permite la creación de un perfil de trabajo sin un EMM para pruebas.
  5. Siga las instrucciones de [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) para crear un perfil de trabajo en el dispositivo.
  6. Revise las aplicaciones que aparecen en el perfil de trabajo. 
  7. Si las mismas aplicaciones aparecen en la aplicación Test DPC, el OEM espera las aplicaciones para ese dispositivo.

### <a name="unapproved-managed-google-play-for-work-store-apps-arent-being-removed-from-the-client-apps-page-in-intune"></a>Aplicaciones no aprobadas de Google Play for Work administrado que no desaparecen de la página Aplicaciones cliente de Intune
Este comportamiento es normal.

### <a name="managed-google-play-apps-arent-being-reported-under-the-discovered-apps-blade-in-the-intune-portal"></a>Aplicaciones de Google Play administrado que no aparecen en la hoja Aplicaciones detectadas del portal de Intune
Este comportamiento es normal. Solo las aplicaciones del sistema instaladas en el perfil de trabajo se inventarian en la hoja Aplicaciones detectadas. Para ver las aplicaciones instaladas de Google Play administrado, use la hoja **Aplicaciones administradas**.

### <a name="are-web-applications-supported-for-work-profile-enrolled-devices"></a>¿Las aplicaciones web son compatibles con los dispositivos inscritos en el perfil de trabajo?
Sí. Para obtener más información, vea [Vínculos web de Google Play administrado](../apps/apps-add-android-for-work.md#managed-google-play-web-links).

## <a name="device-management"></a>Administración de dispositivos

### <a name="file-path-internal-storageandroiddatacommicrosoftwindowsintunecompanyportalfiles-missing-on-work-profile-enrolled-devices"></a>Ruta de acceso de archivo Internal storage/Android/Data.com.microsoft.windowsintune.companyportal/files no disponible en los dispositivos inscritos en el perfil de trabajo

  **Respuesta**: Este comportamiento es normal. Esta ruta de acceso solo se crea para el escenario de administración de dispositivos (inscripción de Android heredada).

  Para recopilar registros de Portal de empresa, siga estos pasos:

  1. En la aplicación Portal de empresa con la notificación, pulse **Menú** > **Ayuda** > **Soporte técnico por correo electrónico** y, luego, en **Enviar correo electrónico y cargar registros**. 
  2. Cuando se le pida **Enviar solicitud de ayuda con**, seleccione una de las aplicaciones de correo electrónico.
  3. Se genera un correo electrónico para el administrador de TI con un identificador de incidente que se puede proporcionar al servicio de soporte técnico de Microsoft.

### <a name="managed-google-play-last-sync-time--hasnt-been-updated-in-days"></a>Falta de actualización de la hora de la última sincronización de Google Play administrado durante días
Este comportamiento es normal. La sincronización solo se desencadena de forma manual.

### <a name="encryption-is-required-when-a-device-is-enrolled-can-it-be-turned-off"></a>El cifrado es necesario a la hora de inscribir un dispositivo. ¿Se puede desactivar?
No, Google exige que el dispositivo esté cifrado para crear un perfil de trabajo. 

### <a name="samsung-devices-are-blocking-the-use-of-third-party-keyboards-like-swiftkey"></a>Uso de teclados de terceros como SwiftKey bloqueado en dispositivos Samsung
Samsung ha comenzado a aplicar esta restricción en dispositivos con Android 8.0 y versiones posteriores. Microsoft está trabajando con Samsung en este problema y publicará nueva información al respecto cuando esté disponible.

## <a name="remote-actions"></a>Acciones remotas

### <a name="wipe-factory-reset-option-isnt-available-for-work-profile-enrolled-device"></a>Opción Borrar (Restablecimiento de fábrica) no disponible para dispositivos inscritos en el perfil de trabajo
Este comportamiento es normal. En el escenario de perfil de trabajo, el proveedor de MDM no dispone de control total sobre el dispositivo. La única opción disponible es Retirar (Eliminar datos de la compañía), que quita todo el perfil de trabajo y su contenido.

### <a name="is-device-passcode-reset-supported"></a>¿Se admite el restablecimiento del código de acceso de un dispositivo?
En los dispositivos inscritos en el perfil de trabajo, solo se puede restablecer el código de acceso del perfil de trabajo en dispositivos Android 8.0 o versiones posteriores en los casos siguientes:
- El código de acceso del perfil de trabajo está administrado.
- El usuario final ha permitido restablecerlo.

En los dispositivos dedicados (COSU) y totalmente administrados, se admite el restablecimiento del código de acceso del dispositivo.


## <a name="next-steps"></a>Pasos siguientes

- [Solucionar problemas con la inscripción de dispositivos en Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Formule una pregunta en el foro de Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Revise el blog del equipo de soporte técnico de Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Revise el blog de Enterprise Mobility and Security de Microsoft](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)