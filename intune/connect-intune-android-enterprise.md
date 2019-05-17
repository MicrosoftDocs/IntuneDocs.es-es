---
title: Conecte su cuenta de Intune a su cuenta de Google Play administrado.
titleSuffix: Microsoft Intune
description: Aprenda a conectar su cuenta de Intune a su cuenta de Google Play administrado.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19efd0821deeac0e76c60ee67e6230da554391a0
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567392"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Conexión de una cuenta de Intune a una cuenta de Google Play administrado

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para que se admitan dispositivos de [perfil de trabajo de Android Enterprise](android-work-profile-enroll.md), [dispositivos Android Enterprise totalmente administrados](android-fully-managed-enroll.md) y [dispositivos de Android Enterprise dedicados](android-kiosk-enroll.md), debe conectar su cuenta de inquilino de Intune a su cuenta de Android Enterprise administrado.  

> [!NOTE]
> Debido a la interacción entre los dominios de Google y Microsoft, es posible que para este paso deba ajustar la configuración del explorador.  Asegúrese de que "portal.azure.com" y "play.google.com" estén en la misma zona de seguridad en su explorador.

1. Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](mdm-authority-set.md) como **Microsoft Intune**.
2. Inicie sesión en [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Android** > **Google Play administrado**.  Si usas un rol de administrador de Intune personalizado, para el acceso se requieren permisos de actualización y lectura de la organización.
   
   ![Pantalla de inscripción de Android Enterprise](./media/android-work-bind.png)

3. Elija **Acepto** para permitir a Microsoft [enviar información de usuarios y dispositivos a Google](data-intune-sends-to-google.md). 
   
4. Elija **Iniciar Google para conectarse ahora** para abrir el sitio web de Google Play administrado. El sitio web se abrirá en una nueva pestaña en el explorador.
  
5. En la página de inicio de sesión de Google, escriba la cuenta de Google que se asociará con todas las tareas de administración de Android Enterprise para este inquilino. Se trata de la cuenta de Google que los administradores de TI de la empresa comparten para administrar y publicar aplicaciones en la consola de Google Play. Puede usar una cuenta de Google existente o crear una nueva. La cuenta que elija no debe estar asociada con un dominio de G Suite.
    
    > [!Note]
    > Si usa el explorador Microsoft Edge, haga clic en **Iniciar sesión** en la esquina superior derecha para iniciar sesión en su cuenta de Google.

6. Proporcione el nombre de su empresa en **Nombre de la organización**. Para el **proveedor de administración de Enterprise Mobility (EMM)**, **Microsoft Intune** debe mostrarse.

7. Acepte el contrato de Android y, después, seleccione **Confirmar**. La solicitud se procesará.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Desconexión de una cuenta administrativa de Android Enterprise

Puede desactivar la inscripción y administración de Android Enterprise. Para ello, primero se deben retirar los dispositivos de perfil de trabajo de Android Enterprise inscritos. Después, haga clic en **Desconectar** en la consola de administración de Intune para retirar la inscripción de todos los dispositivos de perfil de trabajo de Android Enterprise inscritos y de todos los dispositivos de dedicados. Esto también quita la relación entre la cuenta de Google Play administrado e Intune.

1. Como administrador de Intune, en [Azure portal](https://portal.azure.com), seleccione **Todos los servicios** > **Supervisión y administración** > **Intune**.
2. Elija **Inscripción de dispositivos** > **Inscripción de Android** > **Google Play administrado** > **Desconectar**.
3. Elija **Sí** para desconectarse y anular la inscripción de todos los dispositivos Android Enterprise de Intune.

## <a name="next-steps"></a>Pasos siguientes

Después de conectarse a la cuenta de Google Play administrado, puede [configurar dispositivos del perfil de trabajo de Android Enterprise](android-work-profile-enroll.md) y [configurar dispositivos dedicados de Android Enterprise](android-kiosk-enroll.md).
