---
title: Conexión de la cuenta de Intune a la cuenta de Android Enterprise
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo conectar su cuenta de Intune a su cuenta de Android Enterprise.
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
ms.custom: intune-azure
ms.openlocfilehash: 1b1f54486ab2c3d98e663cfddded346eb61662ae
ms.sourcegitcommit: e4832ea81b9a707a6ad0699a18c8b3988413c283
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279430"
---
# <a name="connect-your-intune-account-to-your-android-enterprise-account"></a>Conexión de la cuenta de Intune a la cuenta de Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para que se admitan los dispositivos de perfil de trabajo Android y los dispositivos de quiosco Android, debe conectar su cuenta de inquilino de Intune a su cuenta de Android Enterprise. 

> [!NOTE]
> Debido a la interacción entre los dominios de Google y Microsoft, es posible que para este paso deba ajustar la configuración del explorador.  Asegúrese de que "portal.azure.com" y "play.google.com" estén en la misma zona de seguridad en su explorador.

1. Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](mdm-authority-set.md) como **Microsoft Intune**.
2. Inicie sesión en [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Android** > **Google Play administrado**.  Si usas un rol de administrador de Intune personalizado, para el acceso se requieren permisos de actualización y lectura de la organización.
   
   ![Pantalla de inscripción de Android Enterprise](./media/android-work-bind.png)

3. Elija **Acepto** para permitir a Microsoft [enviar información de usuarios y dispositivos a Google](data-intune-sends-to-google.md). 
   
4. Elija **Iniciar Google para conectarse ahora** para abrir el sitio web de Google Play administrado. El sitio web se abrirá en una nueva pestaña en el explorador.
  
5. En la página de inicio de sesión de Google, escriba la cuenta de Google que se asociará con todas las tareas de administración de Android Enterprise para este inquilino. Se trata de la cuenta de Google que los administradores de TI de la empresa comparten para administrar y publicar aplicaciones en la consola de Google Play. Puede usar una cuenta de Google existente o crear una nueva. La cuenta que elija no debe estar asociada con un dominio de G Suite.
    
    > [!Note]
    > Si usa el explorador Microsoft Edge, haga clic en **Iniciar sesión** en la esquina superior derecha para iniciar sesión en su cuenta de Google.

6. Proporcione el nombre de su empresa en **Nombre de la organización**. Para el **proveedor de administración de Enterprise Mobility (EMM)**, **Microsoft Intune** debe mostrarse.

7. Acepte el contrato de Android y, después, seleccione **Confirmar**. La solicitud se procesará.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Desconectar la cuenta administrativa de Android Enterprise

Puede desactivar la inscripción y administración de Android Enterprise. Para ello, primero se deben retirar los dispositivos de perfil de trabajo de Android inscritos. Después, haga clic en **Desconectar** en la consola de administración de Intune para retirar la inscripción de todos los dispositivos de perfil de trabajo de Android inscritos y de todos los dispositivos de quiosco. Esto también quita la relación entre la cuenta empresarial de Android e Intune.

1. Como administrador de Intune, en [Azure portal](https://portal.azure.com), seleccione **Todos los servicios** > **Supervisión y administración** > **Intune**.
2. Elija **Inscripción de dispositivos** > **Inscripción de Android** > **Google Play administrado** > **Desconectar**.
3. Elija **Sí** para desconectarse y anular la inscripción de todos los dispositivos Android Enterprise de Intune.

## <a name="next-steps"></a>Pasos siguientes

Después de conectarse a la cuenta de Android Enterprise, puede configurar [dispositivos de perfil de trabajo Android](android-work-profile-enroll.md) y [dispositivos de quiosco Android](android-kiosk-enroll.md).
