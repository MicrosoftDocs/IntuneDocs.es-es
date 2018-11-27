---
title: 'Inicio rápido: Crear una directiva de cumplimiento de contraseñas para dispositivos Android'
titlesuffix: Microsoft Intune
description: En este tutorial de inicio rápido usará Microsoft Intune para establecer la longitud de la contraseña necesaria para los dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 87fb7091079086e5c455376cb5c4ae8e10f28ec1
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179262"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Inicio rápido: Crear una directiva de cumplimiento de contraseñas para dispositivos Android

En este tutorial, usará Microsoft Intune para exigir a los usuarios de sus recursos Android que escriban una contraseña de una longitud específica antes de concederles acceso a información en sus dispositivos Android. 

Una directiva de cumplimiento de dispositivos de Intune especifica las reglas y la configuración que deben cumplir los dispositivos para que se consideren compatibles. Puede usar directivas de cumplimiento con acceso condicional para permitir o bloquear el acceso a los recursos de la empresa. También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento.

> [!IMPORTANT]
> Además de la configuración de la contraseña, también debe considerar otra configuración de la seguridad del sistema para proteger sus recursos. Para más información, vea [Configuración de seguridad del sistema](compliance-policy-create-android-for-work.md#system-security-settings).

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune. 

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos

En este tutorial de inicio rápido usará Intune para exigir a los usuarios de sus recursos Android que escriban una contraseña de una longitud específica antes de concederles acceso a información en sus dispositivos Android.

1. En Intune, seleccione **Cumplimiento del dispositivo** > **Directivas** > **Crear directiva**.
2. Agregue **Cumplimiento de Android** como **Nombre**. Agregue también una **Descripción**.
3. Para **Plataforma**, seleccione **Android**. 
4. Seleccione **Configuración** > **Seguridad del sistema** para mostrar la hoja **Seguridad del sistema** de Android.
5. Haga clic en **Requerir** junto a **Requerir una contraseña para desbloquear dispositivos móviles**.
6. Indique **6** junto a **Longitud mínima de la contraseña**. 

    ![Captura de pantalla de creación de un grupo en Microsoft Intune](media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. Cuando haya terminado, haga clic en **Aceptar** > **Aceptar** > **Crear** para crear la directiva.

Cuando haya creado la directiva correctamente, aparecerá en su lista de directivas de cumplimiento de dispositivos. 

## <a name="clean-up-resources"></a>Limpieza de recursos

Cuando ya no necesite la directiva, elimínela. Para ello, seleccione la directiva de cumplimiento y haga clic en **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, se usa Intune para crear una directiva de cumplimiento para dispositivos Android de los recursos que requieran una contraseña de al menos seis caracteres de longitud. Para obtener más información sobre cómo crear directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos en Intune](device-compliance-get-started.md).

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Enviar notificaciones a dispositivos no conformes](quickstart-send-notification.md)
