---
title: 'Inicio rápido: Configurar la inscripción automática en Intune'
description: 'Inicio rápido: Configurar la inscripción automática para dispositivos Windows 10 en Intune.'
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e64c7d977fef66af0fedf556eea34bef9b9079d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503133"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Inicio rápido: Configurar la inscripción automática para dispositivos Windows 10

En este inicio rápido, configurará Microsoft Intune para inscribir automáticamente los dispositivos cuando determinados usuarios inicien sesión en dispositivos Windows 10.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos

- Suscripción a Microsoft Intune: [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).
- Para completar este inicio rápido, primero debe [crear un usuario](../fundamentals/quickstart-create-user.md) y [crear un grupo](../fundamentals/quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune. Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar la inscripción automática de Windows 10

En este ejemplo, usará la inscripción de MDM para que se puedan inscribir automáticamente tanto los dispositivos corporativos como los dispositivos personales que traen los empleados. Tendrá que registrarse para obtener una suscripción gratuita a Azure Active Directory Premium.

1. En Azure, seleccione **Azure Active Directory** > **Movilidad (MDM y MAM)** .
2. Seleccione **Obtener una prueba gratuita Premium para usar esta característica**. Si selecciona esta opción, se permitirá la inscripción automática con la versión de prueba gratuita Premium de Azure Active Directory. 

    ![Selección de la versión de prueba gratuita Premium de Azure Active Directory](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    Seleccione la opción de la versión de prueba gratuita de **Enterprise Mobility + Security E5**. Además, debe seleccionar **Activar** para activar la versión de prueba gratuita.

    ![Selección de la versión de prueba gratuita de Enterprise Mobility + Security E5](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. Seleccione **Microsoft Intune**. 

    ![Selección de Microsoft Intune en la lista](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Seleccione **Algunos** en **Ámbito de usuario de MAM** para usar la inscripción automática de MDM para administrar los datos de la empresa en los dispositivos Windows de sus empleados. La inscripción automática de MDM se configurará para los dispositivos unidos a AAD y los escenarios Bring Your Own Device.

    ![Selección de "Algunos" en la lista de configuración](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Elija **Seleccionar grupos** > **Contoso Testers (Evaluadores de Contoso)**  > **Seleccionar** como grupo asignado.

    ![Selección del grupo que se va a inscribir](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Seleccione **Algunos** en **Ámbito de usuario de MAM** para administrar los datos en los dispositivos de su personal.
7. Elija **Seleccionar grupos** > **Contoso Testers (Evaluadores de Contoso)**  > **Seleccionar** como grupo asignado. 
8. Use los valores predeterminados para los demás valores de configuración.
9. Elija **Guardar**.

## <a name="clean-up-resources"></a>Limpieza de recursos

Para volver a configurar la inscripción automática de Intune, eche un vistazo a [Configuración de la inscripción de dispositivos Windows](windows-enroll.md).

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, aprendió a configurar la inscripción automática para dispositivos Windows 10. Para obtener más información sobre la inscripción de dispositivos, consulte [¿Qué es la inscripción de dispositivos?](device-enrollment.md)

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Inscripción de dispositivos Windows 10](../quickstart-enroll-windows-device.md)
