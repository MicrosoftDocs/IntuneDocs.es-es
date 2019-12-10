---
title: 'Inicio rápido: Directiva de cumplimiento de contraseñas para dispositivos Android'
titleSuffix: Microsoft Intune
description: En este inicio rápido se usará Microsoft Intune para establecer la longitud de la contraseña que se exige en dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61fdf91d57ce5d187a0c43153f317b0b42c6b46c
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409779"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Inicio rápido: Crear una directiva de cumplimiento de contraseñas para dispositivos Android

En este inicio rápido, usará Microsoft Intune para exigir a los usuarios de Android de sus recursos que escriban una contraseña de una longitud determinada que les permita acceder a la información de sus dispositivos Android.

Una directiva de cumplimiento de dispositivos de Intune especifica las reglas y la configuración que deben cumplir los dispositivos para que se consideren compatibles. Puede usar directivas de cumplimiento con acceso condicional para permitir o bloquear el acceso a los recursos de la empresa. También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento.

> [!IMPORTANT]
> Además de la configuración de la contraseña, también debe considerar otra configuración de la seguridad del sistema para proteger sus recursos. Para más información, vea [Configuración de seguridad del sistema](compliance-policy-create-android-for-work.md).

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) como [administrador global](../fundamentals/users-add.md#types-of-administrators) o [administrador de servicios](../fundamentals/users-add.md#types-of-administrators) de Intune.

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos

Cree una directiva de cumplimiento de dispositivos para exigir a los usuarios de Android de los recursos que escriban una contraseña de una longitud determinada que les permita acceder a la información de sus dispositivos Android.

1. Seleccione **Dispositivos** > **Directivas de cumplimiento** > **Crear directiva**.

2. Agregue **Cumplimiento de Android** como **Nombre**. Agregue también una **Descripción**.

3. Para **Plataforma**, seleccione **Android Enterprise**.

4. En **Tipo de perfil**, seleccione **Perfil de trabajo**.

5. Seleccione **Configuración** > **Seguridad del sistema** para mostrar la hoja **Seguridad del sistema** de Android.

6. En **Requerir una contraseña para desbloquear dispositivos móviles**, seleccione **Requerir**.

7. En **Tipo de contraseña requerida**, seleccione **Al menos numérica**.

8. En **Longitud mínima de contraseña**, escriba **6**.

    ![Captura de pantalla de creación de un grupo en Microsoft Intune](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

9. Cuando haya terminado, seleccione **Aceptar** > **Aceptar** > **Crear** para crear la directiva.

Una vez que la directiva se ha creado correctamente, aparece en la lista de directivas de cumplimiento de dispositivos.

## <a name="clean-up-resources"></a>Limpieza de recursos

Cuando ya no necesite la directiva, elimínela. Para ello, seleccione la directiva de cumplimiento y haga clic en **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, se usa Intune para crear una directiva de cumplimiento para dispositivos Android de los recursos que requieran una contraseña de al menos seis caracteres de longitud. Para obtener más información sobre cómo crear directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos en Intune](device-compliance-get-started.md).

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Enviar notificaciones a dispositivos no conformes](../quickstart-send-notification.md)
