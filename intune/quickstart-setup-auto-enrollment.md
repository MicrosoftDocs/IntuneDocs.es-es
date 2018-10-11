---
title: 'Inicio rápido: Configurar la inscripción automática en Intune'
description: 'Inicio rápido: Configurar la inscripción automática para dispositivos Windows 10 en Intune.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581778"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Inicio rápido: Configurar la inscripción automática para dispositivos Windows 10

En este inicio rápido, configurará Microsoft Intune para inscribir automáticamente los dispositivos cuando determinados usuarios inicien sesión en dispositivos Windows 10.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos

- Para completar este inicio rápido, primero debe [crear un usuario](quickstart-create-user.md) y [crear un grupo](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar la inscripción automática de Windows 10

En este ejemplo, usará la inscripción de MDM para que se puedan inscribir automáticamente tanto los dispositivos corporativos como los dispositivos personales que traen los empleados.

1. En Azure, elija **Azure Active Directory** > **Movilidad (MDM y MAM)** > **Microsoft Intune** > **Algunos**.
![Explorador](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. Elija **Seleccionar grupos** > **Contoso Testers (Evaluadores de Contoso)** > **Seleccionar**.
3. Use los valores predeterminados para las siguientes direcciones URL:
    - URL de términos de uso de MDM
    - URL de detección de MDM
    - URL de cumplimiento de MDM
4. Elija **Guardar**.
5. Inicie sesión como un usuario en el grupo en un dispositivo Windows 10 y siga las indicaciones.

## <a name="clean-up-resources"></a>Limpieza de recursos

Para volver a configurar la inscripción automática de Intune, eche un vistazo a [Configuración de la inscripción de dispositivos Windows](windows-enroll.md).

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, aprendió a configurar la inscripción automática para dispositivos Windows 10. Puede conocer otras maneras de inscribir dispositivos en las distintas plataformas.

> [!div class="nextstepaction"]
> [Artículo ¿Qué es la inscripción de dispositivos?](device-enrollment.md)