---
title: 'Inicio rápido: Enviar notificaciones a dispositivos no conformes'
titleSuffix: Microsoft Intune
description: En este inicio rápido, usará Microsoft Intune para enviar notificaciones por correo electrónico a dispositivos no conformes.
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
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d89cfcafd5452b990509e0fa6fd431a614ee5c1
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410244"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Inicio rápido: Enviar notificaciones a dispositivos no conformes

En este inicio rápido, usará Microsoft Intune para enviar una notificación por correo electrónico a los miembros de su personal que tienen dispositivos no conformes.

De forma predeterminada, cuando Intune detecta un dispositivo que no es compatible, lo marca inmediatamente como tal. Luego, el [acceso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) de Azure Active Directory (Azure AD) bloquea el dispositivo. Cuando un dispositivo es no conforme, Intune le permite agregar acciones en caso de no conformidad, lo que le ofrece flexibilidad de decidir lo que debe hacer. Por ejemplo, puede dar a los usuarios un período de gracia antes de bloquear los dispositivos que no sean conformes.

Una acción que debe llevarse a cabo cuando un dispositivo no satisface los requisitos de cumplimiento es enviar un correo electrónico al usuario de los dispositivos. También puede personalizar una notificación por correo electrónico antes de enviarla. En concreto, puede personalizar los destinatarios, el asunto, el cuerpo del mensaje, incluido el logotipo de la empresa, y la información de contacto. Intune también incluye detalles sobre los dispositivos no conformes en la notificación por correo electrónico.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos

Al usar las directivas de cumplimiento de dispositivos para bloquear los dispositivos para evitar que usen los recursos corporativos, se debe configurar el acceso condicional de Azure AD. Si ha seguido el inicio rápido [Creación de una directiva de cumplimiento de dispositivos](quickstart-set-password-length-android.md), estará usando Azure Active Directory. Para más información sobre Azure AD, consulte [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) y [Formas habituales de usar el acceso condicional con Intune](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) como [administrador global](../fundamentals/users-add.md#types-of-administrators) o [administrador de servicios](../fundamentals/users-add.md#types-of-administrators) de Intune. Si ha creado una suscripción de prueba de Intune, la cuenta con la que la haya creado es el administrador global.

## <a name="create-a-notification-message-template"></a>Creación de una plantilla de mensaje de notificación

Para enviar correo electrónico a los usuarios, cree una plantilla de mensaje de notificación. Cuando un dispositivo no es compatible, los detalles que especifica en la plantilla se muestran en el correo electrónico enviado a los usuarios.

1. En Intune, seleccione **Dispositivos** > **Directivas de cumplimiento** > **Notificaciones** > **Crear notificación**.
2. Escriba la información siguiente:

   - **Nombre**: *Administrador de Contoso*
   - **Asunto**: *Conformidad de dispositivos*
   - **Mensaje**: *Su dispositivo no cumple los requisitos de cumplimiento de nuestra organización*.
   - **Encabezado de correo electrónico: incluir logotipo de la empresa**: establézcalo en **Habilitado** para mostrar el logotipo de la organización.
   - **Pie de página de correo electrónico: incluir nombre de la empresa**: establézcalo en **Habilitado** para mostrar el nombre de la organización.
   - **Pie de página de correo electrónico: incluir información de contacto**: establézcalo en **Habilitado** para mostrar la información de contacto de la organización.

   ![Ejemplo de un mensaje de notificación compatible en Intune](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Seleccione **Siguiente** y revise la notificación. Seleccione **Crear**; la plantilla del mensaje de notificación estará lista para su uso.

   > [!NOTE]
   > También puede editar una plantilla de notificación que haya creado antes.

Para más información sobre cómo establecer el nombre, la información de contacto y el logotipo de la empresa, consulte los siguientes artículos:

- [Información de la empresa y declaración de privacidad de la empresa](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [Información de soporte técnico](../apps/company-portal-app.md#support-information)
- [Personalización de la marca de identidad de la empresa](../apps/company-portal-app.md#company-identity-branding-customization)

## <a name="add-a-noncompliance-policy"></a>Agregar una directiva de no cumplimiento

Cuando se crea una directiva de cumplimiento de dispositivos, Intune crea automáticamente una acción en caso de incumplimiento. Luego, Intune marca los dispositivos como no conformes cuando no satisfacen la directiva de cumplimiento. Puede personalizar cuánto tiempo se marca el dispositivo como no conforme. Puede agregar otra acción al crear una directiva de cumplimiento, o bien actualizar una directiva de cumplimiento existente.

Con los pasos siguientes puede crear una directiva de cumplimiento para dispositivos Windows 10.

1. Seleccione **Dispositivos** > **Directivas de cumplimiento** > **Crear directiva**.

2. Escriba la información siguiente:

   - **Nombre**: *Cumplimiento de Windows 10*
   - **Descripción**: *Directiva de cumplimiento de Windows 10*
   - **Plataforma**: Windows 10 y versiones posteriores

3. Seleccione **Configuración** > **Seguridad del sistema** para mostrar la configuración relativa a la seguridad del dispositivo.

4. Configure las siguientes opciones:

   - Establezca **Requerir una contraseña para desbloquear dispositivos móviles** en **Requerir**. Esta configuración especifica si es preciso que los usuarios escriban una contraseña para poder obtener acceso a información en sus dispositivos móviles.

   - Establezca **Longitud mínima de la contraseña** en **6**. Esta configuración especifica el número mínimo de dígitos o caracteres de la contraseña.

   ![Configuración de la seguridad del sistema de una nueva directiva de cumplimiento](./media/quickstart-send-notification/system-security-settings-01.png)

5. Seleccione **Aceptar** > **Aceptar** > **Crear** para crear la directiva de cumplimiento.

6. Seleccione **Propiedades** > **Action for noncompliance** (Acción de incumplimiento)  > **Agregar**.

7. En el cuadro desplegable **Acción**, compruebe que la opción **Enviar correo electrónico a usuario final** está seleccionada.

8. Seleccione **Plantilla de mensaje**, la plantilla que creó anteriormente en este artículo y, luego, **Seleccionar** para seleccionarla.

9. Seleccione **AGREGAR** > **Aceptar** > **Guardar** para guardar los cambios.

## <a name="assign-the-policy"></a>Asignación de la directiva

Puede asignar la directiva de cumplimiento a un grupo de usuarios específico o a todos los usuarios. Cuando Intune reconoce que un dispositivo no es conforme, se notificará al usuario que debe actualizar el dispositivo para cumplir la directiva de cumplimiento. Use estos pasos para asignar la directiva.

1. En Intune, vaya a **Dispositivos** > **Directivas de cumplimiento** y seleccione **Directiva de cumplimiento de Windows 10** que creó anteriormente.

2. Seleccione **Asignaciones**.

3. En cuadro desplegable **Asignar a**, seleccione **Todos los usuarios**. Se seleccionarán todos los usuarios. Todos los usuarios que tengan un dispositivo **Windows 10 o posterior** que no cumple esta directiva de cumplimiento recibirán una notificación.

    > [!NOTE]
    > Puede incluir y excluir grupos al asignar las directivas de cumplimiento.

4. Haga clic en **Guardar**.

Si ha creado y guardado correctamente la directiva, aparecerá en la lista **Directivas de cumplimiento: directivas**. Observe en la lista que **Asignado** está establecido en **Sí**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial de inicio rápido ha usado Intune para crear y asignar una directiva de cumplimiento para los dispositivos Windows 10 de su personal para exigir una contraseña de al menos seis caracteres de longitud. Para obtener más información sobre cómo crear directivas de cumplimiento para dispositivos Windows, consulte [Incorporación de una directiva de cumplimiento de dispositivos para dispositivos Windows en Intune](compliance-policy-create-windows.md).

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Agregar y asignar una aplicación cliente](../apps/quickstart-add-assign-app.md)
