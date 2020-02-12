---
title: Conecte su cuenta de Intune a su cuenta de Google Play administrado.
titleSuffix: Microsoft Intune
description: Aprenda a conectar su cuenta de Intune a su cuenta de Google Play administrado.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 581d88e49391bc874625e9c84318c039706b0c1b
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124833"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Conexión de una cuenta de Intune a una cuenta de Google Play administrado

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Para que se admitan dispositivos de [perfil de trabajo de Android Enterprise](android-work-profile-enroll.md), [dispositivos Android Enterprise totalmente administrados](android-fully-managed-enroll.md) y [dispositivos de Android Enterprise dedicados](android-kiosk-enroll.md), debe conectar su cuenta de inquilino de Intune a su cuenta de Android Enterprise administrado.  

Para facilitarle la configuración y el uso de la administración de Android Enterprise, tras conectarse a Google Play, Intune agregará automáticamente cuatro aplicaciones comunes relacionadas con Android Enterprise a la consola de administración de Intune. Las cuatro aplicaciones de Android Enterprise son las siguientes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : se usa para escenarios totalmente administrados de Android Enterprise.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : ayuda a iniciar sesión en las cuentas si se usa la verificación de dos fases.
- **[Portal de empresa de Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : se usa para las directivas de protección de aplicación y escenarios de perfil de trabajo de Android Enterprise.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise): se usa para los escenarios de pantalla completa o dedicados de Android Enterprise.

> [!NOTE]
> Debido a la interacción entre los dominios de Google y Microsoft, es posible que para este paso deba ajustar la configuración del explorador.  Asegúrese de que "portal.azure.com" y "play.google.com" estén en la misma zona de seguridad en su explorador.

1. Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](../fundamentals/mdm-authority-set.md) como **Microsoft Intune**.
2. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **Android** > **Inscripción de Android** > **Google Play administrado**.  Si usas un rol de administrador de Intune personalizado, para el acceso se requieren permisos de actualización y lectura de la organización.
   
   ![Pantalla de inscripción de Android Enterprise](./media/connect-intune-android-enterprise/android-work-bind.png)

3. Elija **Acepto** para permitir a Microsoft [enviar información de usuarios y dispositivos a Google](../protect/data-intune-sends-to-google.md). 
   
4. Elija **Iniciar Google para conectarse ahora** para abrir el sitio web de Google Play administrado. El sitio web se abre en una pestaña nueva del explorador.
  
5. En la página de inicio de sesión de Google, escriba la cuenta de Google que se asociará con todas las tareas de administración de Android Enterprise para este inquilino. Se trata de la cuenta de Google que los administradores de TI de la empresa comparten para administrar y publicar aplicaciones en la consola de Google Play. Puede usar una cuenta de Google existente o crear una nueva. La cuenta que elija no debe estar asociada con un dominio de G Suite.
    
    > [!Note]
    > Si usa el explorador Microsoft Edge, haga clic en **Iniciar sesión** en la esquina superior derecha para iniciar sesión en su cuenta de Google.

6. Especifique el nombre de su empresa en **Nombre de la organización**. Para el **proveedor de administración de Enterprise Mobility (EMM)** , **Microsoft Intune** debe mostrarse.

7. Acepte el contrato de Android y, después, seleccione **Confirmar**. La solicitud se procesará.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Desconexión de una cuenta administrativa de Android Enterprise

Puede desactivar la inscripción y administración de Android Enterprise. Para ello, debe retirar primero la inscripción de cualquier dispositivo Android Enterprise, incluidos los dispositivos de perfil de trabajo, los dispositivos dedicados y los dispositivos totalmente administrados. Después, elija **Desconectar** en la consola de administración de Intune para retirar la inscripción de todos los dispositivos del perfil de trabajo, los dispositivos dedicados y los dispositivos totalmente administrados de Android Enterprise que se hayan inscrito. Esto también quita la relación entre la cuenta de Google Play administrado e Intune.

1. Como administrador de Intune, inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Choose **Dispositivos** > **Android** > **Inscripción de Android** > **Google Play administrado** > **Desconectar**.
3. Elija **Sí** para desconectarse y anular la inscripción de todos los dispositivos Android Enterprise de Intune.

## <a name="next-steps"></a>Pasos siguientes

Después de conectarse a la cuenta de Google Play administrado, puede [configurar dispositivos del perfil de trabajo de Android Enterprise](android-work-profile-enroll.md), [configurar dispositivos dedicados de Android Enterprise](android-kiosk-enroll.md) y [configurar dispositivos totalmente administrados de Android Enterprise](android-fully-managed-enroll.md)
