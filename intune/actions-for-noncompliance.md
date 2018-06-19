---
title: 'Acciones y mensajes en caso de incumplimiento con Microsoft Intune: Azure | Microsoft Docs'
description: Cree un correo electrónico de notificación para enviar a los dispositivos no compatibles. Agregue acciones después de que un dispositivo se marque como no compatible (como agregar un período de gracia hasta que lo sea) o bien cree una programación para bloquear el acceso hasta que el dispositivo sea compatible. Haga esto mediante Microsoft Intune en Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8e8603ca59b46937b1529e710a8bc83aec5dd4d6
ms.sourcegitcommit: 4c18352d5b3b30080f7c7257fa63d852b1894850
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
ms.locfileid: "32017964"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>Automatización del correo electrónico y adición de acciones para dispositivos no compatibles: Intune

Hay una característica **Acciones en caso de incumplimiento** que configura una secuencia de acciones ordenadas en el tiempo. Estas acciones se aplican a los dispositivos que no cumplen la directiva de cumplimiento. 

## <a name="overview"></a>Introducción
De forma predeterminada, cuando Intune detecta un dispositivo que no es compatible, lo marca inmediatamente como tal. Después, el [acceso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) de Azure Active Directory (AD) bloquea el dispositivo. Cuando un dispositivo no es compatible, las **acciones en caso de incumplimiento** también proporcionan flexibilidad para decidir qué hacer. Por ejemplo, no bloquear el dispositivo inmediatamente y conceder al usuario un período de gracia para que sea compatible.

Existen dos tipos de acciones:

- **Notificar a los usuarios finales por correo electrónico**: personalice la notificación por correo electrónico antes de enviarla al usuario final. Puede personalizar los destinatarios, el asunto, el cuerpo del mensaje, incluido el logotipo de la empresa, y la información de contacto.

    Además, Intune incluye información sobre los dispositivos no compatibles en la notificación por correo electrónico.

- **Marcar el dispositivo como no conforme**: cree una programación en la que se indique el número de días pasados los cuales el dispositivo se marcará como no compatible. Puede configurar la acción para que surta efecto de inmediato, o bien conceder al usuario un período de gracia para que el dispositivo sea conforme.

## <a name="before-you-begin"></a>Antes de comenzar

- Para configurar las acciones en caso de incumplimiento, necesita al menos una directiva de cumplimiento de dispositivos. Para crear una directiva de cumplimiento de dispositivos, vea las plataformas siguientes:

  - [Android](compliance-policy-create-android.md)
  - [Android for Work](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Al usar las directivas de cumplimiento de dispositivos para bloquear los dispositivos para evitar que usen los recursos corporativos, se debe configurar el acceso condicional de Azure AD. Para obtener instrucciones, vea [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

- Se debe crear una plantilla de mensaje de notificación. Para enviar el correo electrónico a los usuarios, se usa esta plantilla para crear acciones en caso de incumplimiento.

## <a name="create-a-notification-message-template"></a>Creación de una plantilla de mensaje de notificación

1. Inicie sesión en [Azure Portal](https://portal.azure.com) con las credenciales de Intune. 
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Cumplimiento del dispositivo** y, después, **Notificaciones**. 
4. Haga clic en **Crear notificación** y después escriba la siguiente información:

   - Nombre
   - Firmante
   - Mensaje
   - Encabezado de correo electrónico: incluir el logotipo de la empresa
   - Pie de página de correo electrónico: incluir nombre de la empresa
   - Pie de página de correo electrónico: incluir información de contacto

   ![Ejemplo de un mensaje de notificación compatible en Intune](./media/actionsfornoncompliance-1.PNG)

Cuando haya terminado de agregar la información, elija **Crear**. La plantilla de mensaje de notificación está lista para usar.

> [!NOTE]
> También puede editar una plantilla de notificación que creara anteriormente.

## <a name="add-actions-for-noncompliance"></a>Adición de acciones en caso de incumplimiento

De forma predeterminada, Intune crea automáticamente una acción en caso de incumplimiento. Cuando un dispositivo no cumple la directiva de cumplimiento, esta acción marca el dispositivo como no conforme. Puede personalizar cuánto tiempo se marca el dispositivo como no conforme. Esta acción no se puede suprimir.

Puede agregar una acción al crear una directiva de cumplimiento, o bien actualizar una directiva de cumplimiento existente. 

1. En [Azure Portal](https://portal.azure.com), abra **Microsoft Intune** y seleccione **Cumplimiento del dispositivo**.
2. Seleccione **Directivas**, elija una de las directivas y, después, seleccione **Propiedades**. 

  ¿Aún no tiene una directiva? Cree una directiva de [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) o de otra plataforma.
  
  > [!NOTE]
  > Los dispositivos JAMF y los dispositivos dirigidos con grupos de dispositivos no pueden recibir acciones de cumplimiento por el momento.

3. Seleccione **Acciones en caso de incumplimiento** y, después, haga clic en **Agregar** para escribir los parámetros de acción. Puede elegir la plantilla de mensaje creada anteriormente, agregar destinatarios adicionales y actualizar la programación del período de gracia. En la programación, puede escribir el número de días (de 0 a 365) para aplicar las directivas de acceso condicional. Si escribe **0** número de días, el acceso condicional bloquea **inmediatamente** el acceso a los recursos corporativos.

4. Cuando termine, haga clic en **Agregar** > **Aceptar** para guardar los cambios.

## <a name="next-steps"></a>Pasos siguientes
Supervise la actividad de cumplimiento de los dispositivos mediante la ejecución de los informes. En [Supervisión del cumplimiento de dispositivos](device-compliance-monitor.md) se proporcionan algunas instrucciones.
