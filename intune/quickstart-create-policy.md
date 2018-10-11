---
title: 'Inicio rápido: Agregar una directiva de cumplimiento de dispositivos para dispositivos Windows 10'
description: Con este inicio rápido podrá crear directivas para proteger los datos corporativos y administrar los dispositivos que usan los usuarios finales para acceder a los recursos de la empresa. Después, asigne las directivas a grupos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73e1e0a27d128d567a924e6f2b343026b11f1a44
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581785"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>Inicio rápido: Agregar una directiva de cumplimiento de dispositivos para dispositivos Windows 10
Una directiva de cumplimiento de dispositivos de Intune para Windows especifica las reglas y la configuración que los dispositivos Windows deben cumplir para que se consideren compatibles. Puede usar estas directivas con [acceso condicional](https://docs.microsoft.com/intune/conditional-access) para permitir o bloquear el acceso a los recursos de la empresa. También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento.

En este inicio rápido, creará una directiva de cumplimiento de dispositivos para un dispositivo Windows 10 y, después, asignará un grupo de dispositivos a la directiva.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos
- Para completar este inicio rápido, primero debe [crear un usuario](quickstart-create-user.md) y [crear un grupo](quickstart-create-group.md).


## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune
Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune.

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos
1. Seleccione **Cumplimiento de dispositivos** > **Directivas** > **Crear directiva**.
2. Escriba **Cumplimiento de Windows 10** en **Nombre** y **Ejemplo de directiva de cumplimiento para Windows 10** en **Descripción**.
3. En **Plataforma**, seleccione **Windows 10 y versiones posteriores**.
4. En **Configuración**, seleccione **Seguridad del sistema** y después establezca **Requerir una contraseña para desbloquear dispositivos móviles** en **Requerir**. Cuando haya terminado de configurar su directiva, seleccione **Aceptar**.
   ![Directiva de cumplimiento](/intune/media/quickstart-create-policy/compliance-policy.png)
5. Elija el panel **Directiva de cumplimiento de Windows 10**. 
6. En el panel **Crear directiva**, seleccione **Crear**. Este paso crea la directiva e incluye la directiva en **Cumplimiento del dispositivo** > **Directivas**.
7. Seleccione la directiva nueva y luego **Asignaciones**. Puede incluir o excluir grupos de seguridad de Azure Active Directory (AD).
8. Elija **Grupos seleccionados** para ver los grupos de seguridad de Azure AD existentes. Seleccione **Contoso Testers** (Evaluadores de Contoso) y elija **Guardar** para implementar la directiva a los usuarios del grupo. Si no creó este grupo en [Crear un grupo](quickstart-create-group.md), puede usar el grupo que quiera. 

## <a name="clean-up-resources"></a>Limpieza de recursos
Cuando ya no necesite la directiva, elimínela. Para ello, seleccione la directiva **Cumplimiento de Windows 10** y haga clic en **Eliminar**. 

## <a name="next-steps"></a>Pasos siguientes
En este inicio rápido, ha creado y asignado una directiva de cumplimiento sencilla. Para inscribir un dispositivo Windows 10 que va a recibir la directiva, continúe con el inicio rápido para configurar la inscripción automática. 
 
> [!div class="nextstepaction"]
> [Configurar inscripción automática](quickstart-setup-auto-enrollment.md)