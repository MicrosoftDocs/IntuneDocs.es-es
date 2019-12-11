---
title: 'Inicio rápido: Inscribir un dispositivo Windows 10 Escritorio en Microsoft Intune'
description: 'Inicio rápido: use el Portal de empresa para inscribir su dispositivo Windows 10 Escritorio en Microsoft Intune.'
services: microsoft-intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/30/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 658a7655-a6df-4dbe-b56c-22c7fc60e706
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91f20411f668428c8bf3af8b0bd4ae6f4b0b545f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73713521"
---
# <a name="quickstart-enroll-your-windows-10-device"></a>Inicio rápido: Inscripción de dispositivos Windows 10

En este tutorial de inicio rápido, primero asumirá el rol de usuario de Intune e inscribirá su dispositivo Windows 10 en Microsoft Intune. Luego, volverá a Intune y confirmará el dispositivo inscrito.

La inscripción de dispositivos en Microsoft Intune permite que los dispositivos Windows 10 tengan acceso a datos seguros de la organización, incluidos el correo electrónico, los archivos y otros recursos. Esto se aplica tanto a dispositivos Windows 10 Escritorio como a dispositivos Windows 10 Mobile. La inscripción de dispositivos ayuda a proteger este acceso para el usuario y la organización, y permite mantener separados los datos profesionales de los datos personales.

> [!TIP]
> Averigüe lo que sucede al [inscribir el dispositivo en Intune](/intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows) y lo que conlleva para la [información que contiene el dispositivo](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune).

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos

- Suscripción a Microsoft Intune: [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md)
- Para llevar a cabo este tutorial de inicio rápido, debe seguir los pasos necesarios para [configurar la inscripción automática en Intune](quickstart-setup-auto-enrollment.md).

## <a name="confirm-your-windows-10-desktop-version"></a>Comprobar la versión de Windows 10 Escritorio

Antes de inscribir Windows 10 Escritorio, debe comprobar la versión de Windows que ha instalado.

1. Haga clic con el botón derecho en el icono **Inicio** de Windows y seleccione **Configuración** para mostrar las opciones de configuración de Windows.

   ![Captura de pantalla de la configuración de Windows - Sistema](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-01.png)

2. Seleccione **Sistema** > **Acerca de**. 

   ![Captura de pantalla de la configuración del sistema](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-02.png)

    > [!TIP]
    > También puede escribir la expresión "Acerca de tu PC" en la **barra de búsqueda** y, después, seleccionar **Acerca de tu PC**.

3. En la ventana **Configuración** verá una lista de **especificaciones de Windows** de su equipo. En esta lista, busque la **versión**.

4. Compruebe que la **versión** de Windows 10 es la **1607 o una versión posterior**.

    > [!IMPORTANT]
    > Los pasos que aparecen en este tutorial de inicio rápido son para la versión **1607 o una versión posterior** de Windows 10. Si tiene la versión **1511 o anterior**, continúe con [estos pasos](/intune-user-help/enroll-windows-10-device).  

## <a name="enroll-windows-10-desktop"></a>Inscribir Windows 10 Escritorio

1. Vuelva a la configuración de Windows y seleccione **Cuentas**.

   ![Captura de pantalla de la configuración del sistema - Cuentas](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-03.png)

2. Seleccione **Obtener acceso a trabajo o escuela** > **Conectar**.

    ![Seleccionar cuenta Obtener acceso a trabajo o escuela](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-04.png)

3. Inicie sesión en Intune con su cuenta profesional o educativa y, luego, seleccione **Siguiente**. Si ha seguido el tutorial de inicio rápido [Crear un usuario y asignar una licencia](../fundamentals/quickstart-create-user.md), puede iniciar sesión con la cuenta de usuario que ha creado.

    > [!NOTE]
    > Si va a configurar una cuenta ".onmicrosoft.com", la cuenta de usuario tendrá **.onmicrosoft.com** como parte de la dirección de la cuenta. 

   ![Introducción de la cuenta profesional o educativa](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-05.png)

    Verá un mensaje que indica que su empresa o escuela están registradas en el dispositivo.

4. Cuando las vea, significa que se ha**completado el proceso** , seleccione **Listo**. Ya ha terminado.

5. Ahora verá la cuenta que ha agregado como parte de la opción **Obtener acceso a trabajo o escuela** en el escritorio de Windows.

   ![Captura de pantalla de la cuenta recién agregada](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-06.png)

    Si después de seguir los pasos anteriores, no consigue tener acceso a la cuenta de correo electrónico profesional o educativo y a los archivos, siga los pasos de [Pasos de solución de problemas a seguir si ve acceso profesional o educativo](/intune-user-help/troubleshoot-your-windows-10-device-windows#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).

## <a name="confirm-your-device-enrollment-in-intune"></a>Comprobar la inscripción de los dispositivos en Intune

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) como administrador global o administrador de servicios de Intune.
2. Seleccione **Dispositivos** > **Todos los dispositivos** para ver los dispositivos inscritos en Intune.
3. Compruebe que dispone de un dispositivo adicional inscrito en Intune.

   ![Captura de pantalla de los dispositivos inscritos de Intune](./media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-07.png)

## <a name="clean-up-resources"></a>Limpieza de recursos

Para anular la inscripción de su dispositivo Windows, consulte [Quitar el dispositivo Windows de la administración](/intune-user-help/unenroll-your-device-from-intune-windows).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial de inicio rápido ha aprendido a inscribir un dispositivo Windows 10 en Intune. Puede conocer otras maneras de inscribir dispositivos en las distintas plataformas. Para obtener más información sobre cómo usar los dispositivos con Intune, consulte [Usar dispositivos administrados para realizar el trabajo](/intune-user-help/use-managed-devices-to-get-work-done).

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: establecer una longitud de contraseña necesaria para dispositivos Android](../quickstart-set-password-length-android.md)
