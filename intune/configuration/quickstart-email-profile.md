---
title: 'Inicio rápido: Creación de un perfil de dispositivo de correo para dispositivos iOS/iPadOS'
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo usar Microsoft Intune para crear un perfil de dispositivo de correo para que los dispositivos iOS/iPadOS se puedan conectar de forma segura al correo de la empresa.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
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
ms.openlocfilehash: af2576c44e0486dbd859a56896db3b7d0ffc6cff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511075"
---
# <a name="quickstart-create-an-email-device-profile-for-iosipados"></a>Inicio rápido: Creación de un perfil de dispositivo de correo para iOS/iPadOS

En este inicio rápido, aprenderá a crear un perfil de dispositivo de correo para dispositivos iOS/iPadOS. Este perfil especifica la configuración necesaria para que la aplicación de correo integrada en el dispositivo iOS/iPadOS se conecte al correo de la empresa. Con los perfiles de dispositivo de correo, puede estandarizar la configuración para todos los dispositivos y permitir a los usuarios finales acceder al correo de la empresa desde sus dispositivos personales sin necesidad de ninguna configuración por su parte. Para proteger aún más su correo, puede usar un perfil de correo electrónico para determinar si los dispositivos son compatibles y, después, establecer el acceso condicional para permitir que solo puedan acceder al correo los dispositivos que sean compatibles. Para más detalles sobre los perfiles de correo, vea [Configuración del correo electrónico en Microsoft Intune](email-settings-configure.md).

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) como administrador global o administrador de servicios de Intune. Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="create-an-iosipados-email-profile"></a>Creación de un perfil de correo electrónico para iOS/iPadOS

1. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

   ![Creación de un perfil de correo para iOS/iPadOS en Intune](./media/quickstart-email-profile/ios-create-profile.png)

2. En **Nombre**, escriba un nombre descriptivo para el nuevo perfil. En este ejemplo, escriba **iOS necesita correo electrónico de trabajo**.
3. Escriba esta información de perfil:
    - Para **Descripción**, escriba **Requiere que los dispositivos iOS/iPadOS usen correo electrónico del trabajo**.
    - Para **Plataforma**, seleccione **iOS/iPadOS**.
    - Para **Tipo de perfil**, seleccione **Correo electrónico**.

        ![Creación de un perfil de correo electrónico para usarlo con dispositivos iOS/iPadOS en Intune](./media/quickstart-email-profile/ios-email-profile-name.png)

4. Seleccione **Configuración** y configure estos valores (deje los demás valores predeterminados):
   - **Servidor de correo electrónico**: para este inicio rápido, escriba **outlook.office365.com**. Esta configuración especifica la ubicación de Exchange (dirección URL) del servidor de correo electrónico que usará la aplicación de correo electrónico de iOS/iPadOS para conectarse al correo electrónico.
   - **Nombre de la cuenta**: Escriba el **Correo electrónico de la empresa**.
   - **Atributo de nombre de usuario de AAD**: este nombre es el atributo que Intune obtiene de Azure Active Directory (Azure AD). Intune usa este nombre para generar dinámicamente el nombre de usuario para este perfil. Para este inicio rápido, suponemos que queremos que **Nombre principal de usuario** se use como nombre de usuario para el perfil (por ejemplo, user1@contoso.com).
   - **Atributo de dirección de correo electrónico de AAD**: esta configuración es la dirección de correo electrónico de Azure AD que se usará para iniciar sesión en Exchange. Para este inicio rápido, seleccione **Nombre principal de usuario**.
   - **Método de autenticación**: para este inicio rápido, seleccione **Nombre de usuario y contraseña**. (También puede elegir **Certificado** si ya ha configurado un certificado para Intune.)

        ![Creación de un perfil de correo para usarlo con iOS/iPadOS](./media/quickstart-email-profile/ios-email-profile.png)

5. Haga clic en **Aceptar** > **Crear**. El nuevo perfil aparece en la lista de perfiles con el panel mostrado para que pueda supervisar cómo se ha asignado a los dispositivos y usuarios de iOS/iPadOS.
6. Seleccione **Asignaciones**.
7. Seleccione la pestaña **Incluir** y, luego, seleccione **Todos los usuarios y dispositivos**. 
8. Seleccione **Guardar**.

## <a name="clean-up-resources"></a>Limpieza de recursos

Si no piensa usar el perfil que creó para otros tutoriales o pruebas, puede eliminarlo ahora.

1. En Intune, seleccione **Configuración del dispositivo** y **Perfiles**.
2. Seleccione el perfil de prueba que ha creado, **iOS/iPadOS necesita correo electrónico de trabajo**.
3. Seleccione los puntos suspensivos (**...**) junto al perfil y elija **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha creado un perfil de correo electrónico para dispositivos iOS/iPadOS. Ya puede usar este perfil para determinar si un dispositivo iOS/iPadOS es compatible; para ello, solo tiene que crear una directiva de cumplimiento que marque como no compatibles aquellos dispositivos iOS/iPadOS que no coincidan con el perfil. Para lograr una mayor protección, puede crear una directiva de acceso condicional que bloquee el acceso al correo electrónico para todos aquellos dispositivos iOS/iPadOS que no sean compatibles. Para obtener más información sobre las directivas de cumplimiento de dispositivos, consulte la [introducción a las directivas de cumplimiento de dispositivos en Intune](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Tutorial: Protección del correo electrónico de Exchange Online en dispositivos administrados](../tutorial-protect-email-on-enrolled-devices.md)
