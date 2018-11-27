---
title: Inscribir dispositivos del perfil de trabajo Android en Intune
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos del perfil de trabajo Android en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b3592ceb2b1a4e7ba32fc0a8b3de53e0f0329d8b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179735"
---
# <a name="set-up-enrollment-of-android-work-profile-devices"></a>Configure la inscripción de dispositivos de perfil de trabajo Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune le ayuda a implementar aplicaciones y opciones de configuración en dispositivos de perfil de trabajo Android a fin de garantizar que la información laboral y la personal se mantengan aparte. Para obtener detalles específicos sobre Android Enterprise, consulte [Requisitos para usar dispositivos Android en una empresa](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Para configurar la administración de perfiles de trabajo Android, siga estos pasos:

1. [Conecte su cuenta de inquilino de Intune a su cuenta de Android Enterprise](connect-intune-android-enterprise.md).
2. Especifique la configuración de inscripción del perfil de trabajo Android. Los perfiles de trabajo Android [solo se admiten en determinados dispositivos Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Cualquier dispositivo que admita perfiles de trabajo Android también admite la administración Android convencional. Intune permite especificar cómo se deben administrar los dispositivos que admiten los perfiles de trabajo Android en [Restricciones de inscripción](enrollment-restrictions-set.md).
    - **Bloquear (opción predeterminada)**: todos los dispositivos Android se inscribirán como dispositivos Android convencionales, incluidos los dispositivos que admiten perfiles de trabajo Android.
    - **Permitir**: todos los dispositivos que admiten perfiles de trabajo Android se inscribirán como dispositivos de trabajo Android. Los dispositivos Android que no admitan perfiles de trabajo Android se inscriben como dispositivos Android convencionales.
3. [Indique a los usuarios cómo deben inscribir sus dispositivos](/intune-user-help/enroll-your-device-in-intune-android).


Si quiere inscribir dispositivos en perfiles de trabajo Android, pero esos dispositivos ya se han inscrito anteriormente como dispositivos Android normales, debe anular su inscripción y volver a inscribirlos.

Si va a inscribir dispositivos de perfil de trabajo Android a través de una cuenta [administrador de inscripciones de dispositivos](device-enrollment-manager-enroll.md), existe un límite de 10 dispositivos que se pueden inscribir por cuenta.

Para obtener más información, consulte [Datos que Intune manda a Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Aprobar la aplicación Portal de empresa en una instancia administrada de Google Play Store

Para asegurarse de que los usuarios siempre tengan acceso a la versión más actualizada de la aplicación Portal de empresa, debe aprobar la aplicación Portal de empresa para Android en la versión administrada de Google Play Store. Con esta aprobación, se asegura de que cada usuario obtiene actualizaciones automáticas. Si no la aprueba, la aplicación Portal de empresa al final quedará desactualizada y es posible que no reciba correcciones importantes ni nuevas características cuando Microsoft las publique.

Siga estos pasos para aprobar el Portal de empresa de Intune:

1.  Vaya a la aplicación Portal de empresa en una [instancia administrada de Google Play Store](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Inicie sesión en la instancia administrada de Google Play Store con la misma cuenta de Google que haya usado para configurar el enlace de Android Enterprise.
3.  Haga clic en **Aprobar** y se abrirá un nuevo cuadro de diálogo.
4.  Revise los permisos de este cuadro de diálogo y luego haga clic en **Aprobar**. Tiene que permitir estos permisos para que la aplicación Portal de empresa pueda administrar el perfil de trabajo en el dispositivo.
5.  Seleccione **Keep approved when app requests new permissions** (Mantener aprobados cuando la aplicación solicite nuevos permisos) y luego haga clic en **Guardar**.

## <a name="next-steps-for-android-work-profiles"></a>Pasos siguientes para los perfiles de trabajo Android
- [Implementar aplicaciones del perfil del trabajo Android](apps-add-android-for-work.md)
- [Agregar una directiva de configuración de perfil de trabajo Android](device-profiles.md)
