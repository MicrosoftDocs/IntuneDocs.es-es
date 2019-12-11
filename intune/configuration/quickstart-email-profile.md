---
title: 'Inicio rápido: Crear un perfil de dispositivo de correo para iOS'
titleSuffix: Microsoft Intune
description: Aprenda a usar Microsoft Intune para crear un perfil de dispositivo de correo para que los dispositivos iOS puedan conectarse de forma segura al correo de la empresa.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b2f1372a6d7ced09a9ebdfc11cbad69501827bc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059324"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>Inicio rápido: Crear un perfil de dispositivo de correo para iOS

En este inicio rápido, aprenderá a crear un perfil de dispositivo de correo para dispositivos iOS. Este perfil especifica la configuración necesaria para que la aplicación de correo integrada en el dispositivo iOS se conecte al correo de la empresa. Con los perfiles de dispositivo de correo, puede estandarizar la configuración para todos los dispositivos y permitir a los usuarios finales acceder al correo de la empresa desde sus dispositivos personales sin necesidad de ninguna configuración por su parte. Para proteger aún más su correo, puede usar un perfil de correo electrónico para determinar si los dispositivos son compatibles y, después, establecer el acceso condicional para permitir que solo puedan acceder al correo los dispositivos que sean compatibles. Para más detalles sobre los perfiles de correo, vea [Configuración del correo electrónico en Microsoft Intune](email-settings-configure.md).

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) como administrador global o administrador de servicios de Intune. Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="create-an-ios-email-profile"></a>Crear un perfil de correo electrónico para iOS

1. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

   ![Crear un perfil de correo electrónico para iOS](./media/quickstart-email-profile/ios-create-profile.png)

2. En **Nombre**, escriba un nombre descriptivo para el nuevo perfil. En este ejemplo, escriba **iOS necesita correo electrónico de trabajo**.
3. Escriba esta información de perfil:
    - Para **Descripción**, escriba **Requiere que los dispositivos iOS usen correo electrónico del trabajo**.
    - Para **Plataforma**, seleccione **iOS**.
    - Para **Tipo de perfil**, seleccione **Correo electrónico**.

        ![Crear un perfil de correo electrónico para usarlo en iOS](./media/quickstart-email-profile/ios-email-profile-name.png)

4. Seleccione **Configuración** y configure estos valores (deje los demás valores predeterminados):
   - **Servidor de correo electrónico**: para este inicio rápido, escriba **outlook.office365.com**. Esta configuración especifica la ubicación de Exchange (URL) del servidor de correo electrónico que usará la aplicación de correo electrónico de iOS para conectarse al correo electrónico.
   - **Nombre de la cuenta**: Escriba el **Correo electrónico de la empresa**.
   - **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (Azure AD). Intune usa este nombre para generar dinámicamente el nombre de usuario para este perfil. Para este inicio rápido, suponemos que queremos que **Nombre principal de usuario** se use como nombre de usuario para el perfil (por ejemplo, user1@contoso.com).
   - **Atributo de dirección de correo electrónico de AAD**: esta configuración es la dirección de correo electrónico de Azure AD que se usará para iniciar sesión en Exchange. Para este inicio rápido, seleccione **Nombre principal de usuario**.
   - **Método de autenticación**: para este inicio rápido, seleccione **Nombre de usuario y contraseña**. (También puede elegir **Certificado** si ya ha configurado un certificado para Intune.)

        ![Crear un perfil de correo electrónico para usarlo en iOS](./media/quickstart-email-profile/ios-email-profile.png)

5. Haga clic en **Aceptar** > **Crear**. El nuevo perfil aparece en la lista de perfiles con el panel mostrado para que pueda supervisar cómo se asignó el perfil a los dispositivos iOS y los usuarios de iOS.
6. Seleccione **Asignaciones**.
7. Seleccione la pestaña **Incluir** y, luego, seleccione **Todos los usuarios y dispositivos**. 
8. Seleccione **Guardar**.

## <a name="clean-up-resources"></a>Limpieza de recursos

Si no piensa usar el perfil que creó para otros tutoriales o pruebas, puede eliminarlo ahora.

1. En Intune, seleccione **Configuración del dispositivo** y **Perfiles**.
2. Seleccione el perfil de prueba que creó, **iOS necesita correo electrónico de trabajo**.
3. Seleccione los puntos suspensivos ( **...** ) junto al perfil y elija **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha creado un perfil de correo electrónico para dispositivos iOS. Ya puede usar este perfil para determinar si un dispositivo iOS es compatible; para ello, solo tiene que crear una directiva de cumplimiento que marque como no compatibles aquellos dispositivos iOS que no coincidan con el perfil. Para lograr una mayor protección, puede crear una directiva de acceso condicional que bloquee el acceso al correo electrónico para todos aquellos dispositivos iOS que no sean compatibles. Para obtener más información sobre las directivas de cumplimiento de dispositivos, consulte la [introducción a las directivas de cumplimiento de dispositivos en Intune](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Tutorial: Protección del correo electrónico de Exchange Online en dispositivos administrados](../tutorial-protect-email-on-enrolled-devices.md)
