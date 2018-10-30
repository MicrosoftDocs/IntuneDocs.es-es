---
title: 'Inicio rápido: Establecer una longitud de contraseña necesaria para dispositivos Android'
titlesuffix: Microsoft Intune
description: En este tutorial usará Microsoft Intune para establecer una longitud de la contraseña necesaria para dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395302"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>Inicio rápido: Establecer una longitud de contraseña necesaria para dispositivos Android

En este tutorial, usará Microsoft Intune para exigir a los usuarios de sus recursos Android que escriban una contraseña de una longitud específica antes de concederles acceso a información en sus dispositivos Android. 

> [!IMPORTANT]
> Además de la configuración de la contraseña, también debe considerar otra configuración de la seguridad del sistema para proteger sus recursos. Para más información, vea [Configuración de seguridad del sistema](compliance-policy-create-android-for-work.md#system-security-settings).

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune. Intune se encuentra en Azure Portal, si selecciona **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos
1. Una vez abierta la hoja **Microsoft Intune**, seleccione **Conformidad de dispositivos** > **Directivas** > **Crear directiva**.
2. Agregue **Cumplimiento de Android** como **Nombre**. Agregue también una **Descripción**.
3. Para **Plataforma**, seleccione **Android**. 
4. Seleccione **Configuración** > **Seguridad del sistema** para mostrar la hoja **Seguridad del sistema** de Android.
5. En la sección **Contraseña**, junto a **Requerir contraseña para desbloquear dispositivos móviles**, haga clic en **Requerir**.
6. Junto a **Longitud mínima de la contraseña**, escriba **6**.  

    ![Captura de pantalla de creación de un grupo en Microsoft Intune](./media/quickstart-set-password-length-android-01.png)

7. Cuando haya terminado, haga clic en **Aceptar** para cerrar la hoja **Seguridad del sistema**. 
8. Haga clic en **Aceptar** para cerrar la hoja **Directiva de cumplimiento de Android**. 
9. Haga clic en **Crear** para crear la directiva.

Si ha creado correctamente la directiva, aparecerá en la lista **Conformidad de dispositivos: directivas**. 

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, se usa Intune para crear una directiva de cumplimiento para dispositivos Android de los recursos que requieran una contraseña de al menos seis caracteres de longitud.

> [!div class="nextstepaction"]
> [Configurar inscripción automática](quickstart-setup-auto-enrollment.md)
