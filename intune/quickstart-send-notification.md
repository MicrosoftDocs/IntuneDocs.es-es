---
title: 'Inicio rápido: Enviar notificaciones a dispositivos no conformes'
titleSuffix: Microsoft Intune
description: En este tutorial de inicio rápido usará Microsoft Intune para enviar notificaciones por correo electrónico a dispositivos no conformes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/27/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb175d2133cf2a7bc5b064c13afb7e252147c729
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044253"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Inicio rápido: Enviar notificaciones a dispositivos no conformes

En este tutorial de inicio rápido usará Microsoft Intune para enviar una notificación por correo electrónico a los miembros de su personal que tienen dispositivos no conformes.

De forma predeterminada, cuando Intune detecta un dispositivo que no es compatible, lo marca inmediatamente como tal. Después, el [acceso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) de Azure Active Directory (AAD) bloquea el dispositivo. Cuando un dispositivo no es compatible, Intune le permite agregar acciones en caso de incumplimiento, lo que le ofrece flexibilidad a la hora de decidir lo que debe hacer. Por ejemplo, puede dar a los usuarios un período de gracia antes de bloquear los dispositivos que no sean conformes.

Una de las acciones que puede llevar a cabo si los dispositivos no son conformes es enviar un correo electrónico a los usuarios finales. También puede personalizar una notificación por correo electrónico antes de enviarlo a los usuarios finales. En concreto, puede personalizar los destinatarios, el asunto, el cuerpo del mensaje, incluido el logotipo de la empresa, y la información de contacto. Intune también incluirá información sobre los dispositivos no compatibles en la notificación por correo electrónico.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos
- Al usar las directivas de cumplimiento de dispositivos para bloquear los dispositivos para evitar que usen los recursos corporativos, se debe configurar el acceso condicional de AAD. Si ha seguido el tutorial de inicio rápido [Crear una directiva de cumplimiento de dispositivos](quickstart-set-password-length-android.md), quiere decir que está usando Azure Active Directory. Para más información sobre AAD, consulte [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) y [Formas habituales de usar el acceso condicional con Intune](conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en el portal de [Intune](https://aka.ms/intuneportal) como [administrador global](users-add.md#types-of-administrators) o como [administrador de servicios](users-add.md#types-of-administrators) de Intune. Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="create-a-notification-message-template"></a>Creación de una plantilla de mensaje de notificación

Para enviar correo electrónico a los usuarios, cree una plantilla de mensaje de notificación. Cuando un dispositivo no es compatible, los detalles que especifica en la plantilla se muestran en el correo electrónico enviado a los usuarios.

1. En Intune, seleccione **Cumplimiento del dispositivo** > **Notificaciones** > **Crear notificación**. 
2. Escriba la información siguiente:

   - **Nombre**: *Administrador de Contoso*
   - **Asunto**: *Conformidad de dispositivos*
   - **Mensaje**: *Su dispositivo no cumple los requisitos de cumplimiento de nuestra organización*.
   - **Encabezado de correo electrónico: incluir logotipo de la empresa**: establézcalo en **Habilitado** para mostrar el logotipo de la organización.
   - **Pie de página de correo electrónico: incluir nombre de la empresa**: establézcalo en **Habilitado** para mostrar el nombre de la organización.
   - **Pie de página de correo electrónico: incluir información de contacto**: establézcalo en **Habilitado** para mostrar la información de contacto de la organización.

   ![Ejemplo de un mensaje de notificación compatible en Intune](./media/quickstart-send-notification-01.png)

3. Cuando haya terminado de agregar la información, elija **Crear**. La plantilla de mensaje de notificación está lista para usar.

    > [!NOTE]
    > También puede editar una plantilla de notificación que haya creado antes.

Para obtener información detallada sobre cómo establecer el nombre, la información de contacto y el logotipo de su empresa, consulte [Información de la empresa y declaración de privacidad de la empresa](company-portal-app.md#company-information-and-privacy-statement), [Información de soporte técnico](company-portal-app.md#support-information) y [Personalización de la marca de identidad de la empresa](company-portal-app.md#company-identity-branding-customization). 

## <a name="add-a-noncompliance-policy"></a>Agregar una directiva de no cumplimiento

Cuando se crea una directiva de cumplimiento de dispositivos, Intune crea automáticamente una acción en caso de incumplimiento. Cuando un dispositivo no cumple la directiva de cumplimiento, Intune marca el dispositivo como no conforme de forma automática. Puede personalizar cuánto tiempo se marca el dispositivo como no conforme. Puede agregar otra acción al crear una directiva de cumplimiento, o bien actualizar una directiva de cumplimiento existente. 

Con los pasos siguientes puede crear una directiva de cumplimiento para dispositivos Windows 10.

1. En Intune, seleccione **Cumplimiento del dispositivo**.
2. Seleccione **Directivas** > **Crear directiva**.
3. Escriba la información siguiente:

   - **Nombre**: *Cumplimiento de Windows 10*
   - **Descripción**: *Directiva de cumplimiento de Windows 10*
   - **Plataforma**: Windows 10 y versiones posteriores

4. Seleccione **Configuración** > **Seguridad del sistema** para mostrar la configuración relativa a la seguridad del dispositivo.
5. Establezca **Requerir una contraseña para desbloquear dispositivos móviles** en **Requerir**. Esta configuración especifica si es preciso que los usuarios escriban una contraseña para poder obtener acceso a información en sus dispositivos móviles. 
6. Establezca **Longitud mínima de la contraseña** en **6**. Esta configuración especifica el número mínimo de dígitos o caracteres de la contraseña.

    <img alt="System Security settings for a new compliance policy" src="./media/quickstart-send-notification-02.png" width="600">

7. Seleccione **Aceptar** > **Aceptar** > **Crear** para crear la directiva de cumplimiento.
8. Seleccione **Propiedades** > **Action for noncompliance** (Acción de incumplimiento)  > **Agregar**.
9. En el cuadro desplegable **Acción**, compruebe que la opción **Enviar correo electrónico a usuario final** está seleccionada.
10. Seleccione **Plantilla de mensaje** > **Administrador de Contoso** > **Seleccionar** para seleccionar la plantilla de mensaje que ha creado en este tema.
11. Seleccione **AGREGAR** > **Aceptar** > **Guardar** para guardar los cambios.

## <a name="assign-the-policy"></a>Asignación de la directiva

Puede asignar la directiva de cumplimiento a un grupo de usuarios específico o a todos los usuarios. Cuando Intune reconoce que un dispositivo no es conforme, se notificará al usuario que debe actualizar el dispositivo para cumplir la directiva de cumplimiento. Los pasos siguientes le permiten asignar la directiva.

1. Seleccione la directiva **Cumplimiento de Windows 10** que ha creado antes.
2. Seleccione **Asignaciones**.
3. En cuadro desplegable **Asignar a**, seleccione **Todos los usuarios**. Se seleccionarán todos los usuarios. Todos los usuarios que tengan un dispositivo **Windows 10 o posterior** que no cumple esta directiva de cumplimiento recibirán una notificación.

    > [!NOTE]
    > Puede incluir y excluir grupos al asignar las directivas de cumplimiento.

4. Haga clic en **Guardar**.

Si ha creado y guardado correctamente la directiva, aparecerá en la lista **Conformidad de dispositivos: directivas**. Observe en la lista que **Asignado** está establecido en **Sí**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial de inicio rápido ha usado Intune para crear y asignar una directiva de cumplimiento para los dispositivos Windows 10 de su personal para exigir una contraseña de al menos seis caracteres de longitud. Para obtener más información sobre cómo crear directivas de cumplimiento para dispositivos Windows, consulte [Incorporación de una directiva de cumplimiento de dispositivos para dispositivos Windows en Intune](compliance-policy-create-windows.md).

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Agregar y asignar una aplicación cliente](quickstart-add-assign-app.md)
