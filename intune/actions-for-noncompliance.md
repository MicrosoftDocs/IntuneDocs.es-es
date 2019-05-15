---
title: 'Acciones y mensajes en caso de incumplimiento con Microsoft Intune: Azure | Microsoft Docs'
description: Cree un correo electrónico de notificación para enviar a los dispositivos no compatibles. Agregue acciones después de que un dispositivo se marque como no compatible (como agregar un período de gracia hasta que lo sea) o bien cree una programación para bloquear el acceso hasta que el dispositivo sea compatible. Haga esto mediante Microsoft Intune en Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/01/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 751d89ef023bea07d3c8bdb69904605d88c9e0b6
ms.sourcegitcommit: dde4b8788e96563edeab63f612347fa222d8ced0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135223"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>Automatización del correo electrónico y adición de acciones para dispositivos no compatibles en Intune

Para aquellos dispositivos que no cumplen las reglas o las directivas de cumplimiento, puede agregar **Acciones en caso de incumplimiento**. Esta característica configura una secuencia de acciones ordenadas en el tiempo, como enviar un correo al usuario final, entre otras.

## <a name="overview"></a>Introducción

De forma predeterminada, cuando Intune detecta un dispositivo que no es compatible, lo marca inmediatamente como tal. Después, el [acceso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) de Azure Active Directory (AD) bloquea el dispositivo. Cuando un dispositivo no es compatible, las **acciones en caso de incumplimiento** también proporcionan flexibilidad para decidir qué hacer. Por ejemplo, no bloquear el dispositivo inmediatamente y conceder al usuario un período de gracia para que sea compatible.

Hay varios tipos de acciones:

- **Enviar correo electrónico a usuario final**: personalice una notificación por correo electrónico antes de enviarla al usuario final. Puede personalizar los destinatarios, el asunto, el cuerpo del mensaje, incluido el logotipo de la empresa, y la información de contacto.

    Además, Intune incluye información sobre los dispositivos no compatibles en la notificación por correo electrónico.

- **Bloquear de forma remota el dispositivo no conforme**: para los dispositivos que no son compatibles se puede emitir un bloqueo remoto. Después se pide al usuario un PIN o una contraseña para desbloquear el dispositivo. Más información sobre la característica [Bloqueo remoto](device-remote-lock.md). 

- **Marcar dispositivo como no compatible**: cree una programación en la que se indique el número de días pasados los cuales el dispositivo se marcará como no compatible. Puede configurar la acción para que surta efecto de inmediato, o bien conceder al usuario un período de gracia para que el dispositivo sea conforme.

En este artículo se muestra cómo:

- Crear una plantilla de notificación de mensaje
- Creación de una acción en caso de incumplimiento, como enviar un correo electrónico o bloquear de forma remota un dispositivo


## <a name="before-you-begin"></a>Antes de comenzar

- Para configurar las acciones en caso de incumplimiento, necesita al menos una directiva de cumplimiento de dispositivos. Para crear una directiva de cumplimiento de dispositivos, vea las plataformas siguientes:

  - [Android](compliance-policy-create-android.md)
  - [Perfiles de trabajo Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Al usar las directivas de cumplimiento de dispositivos para bloquear los dispositivos para evitar que usen los recursos corporativos, se debe configurar el acceso condicional de Azure AD. Vea [¿Qué es el acceso condicional en Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) o [¿Cuáles son las formas habituales de usar el acceso condicional con Intune?](conditional-access-intune-common-ways-use.md) para obtener instrucciones.

## <a name="create-a-notification-message-template"></a>Creación de una plantilla de mensaje de notificación

Para enviar correo electrónico a los usuarios, cree una plantilla de mensaje de notificación. Cuando un dispositivo no es compatible, los detalles que especifica en la plantilla se muestran en el correo electrónico enviado a los usuarios.

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Cumplimiento del dispositivo** > **Notificaciones**.
3. Seleccione **Crear notificación**. Escriba la información siguiente:

   - **Nombre**
   - **Asunto**
   - **Message**
   - **Encabezado de correo electrónico: incluir logotipo de la empresa**
   - **Pie de página de correo electrónico: incluir nombre de la empresa**
   - **Pie de página de correo electrónico: incluir información de contacto**

   ![Ejemplo de un mensaje de notificación compatible en Intune](./media/actionsfornoncompliance-1.PNG)

4. Cuando haya terminado de agregar la información, elija **Crear**. La plantilla de mensaje de notificación está lista para usar. El logotipo que se carga como parte de la personalización de marca del Portal de empresa se usa para las plantillas de correo electrónico. Para más información sobre la personalización de marca del Portal de empresa, vea [Personalización de la marca de empresa](company-portal-app.md#company-identity-branding-customization).

> [!NOTE]
> También puede cambiar o actualizar una plantilla de notificación existente que creó anteriormente.

## <a name="add-actions-for-noncompliance"></a>Adición de acciones en caso de incumplimiento

Cuando se crea una directiva de cumplimiento de dispositivos, Intune crea automáticamente una acción en caso de incumplimiento. Si un dispositivo no cumple la directiva de cumplimiento, esta acción marca el dispositivo como no conforme. Puede personalizar cuánto tiempo se marca el dispositivo como no conforme. Esta acción no se puede suprimir.

Puede agregar otra acción al crear una directiva de cumplimiento, o bien actualizar una directiva existente. 

1. En [Azure Portal](https://portal.azure.com), abra **Microsoft Intune** > **Cumplimiento del dispositivo**.
2. Seleccione **Directivas**, elija una de las directivas y, después, seleccione **Propiedades**. 

    ¿Aún no tiene una directiva? Cree una directiva de [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) o de otra plataforma.
  
    > [!NOTE]
    > Los dispositivos JAMF y los dispositivos dirigidos con grupos de dispositivos no pueden recibir acciones de cumplimiento por el momento.

3. Seleccione **Actions for noncompliance** (Acciones en caso no conformidad) > **Agregar**.
4. Seleccione la **Acción**: 

    - **Enviar correo electrónico a usuario final**: cuando el dispositivo no sea compatible, elija la opción de enviar un correo al usuario. Además: 
    
         - Elija la **Plantilla de mensaje** que ha creado antes
         - Escriba los **Destinatarios adicionales** mediante la selección de grupos
    
    - **Bloquear de forma remota el dispositivo no conforme**: cuando el dispositivo no sea compatible, bloquéelo. Esta acción obliga al usuario a escribir un PIN o una contraseña para desbloquear el dispositivo. 
    
5. Configurar una **programación**: escriba el número de días (de 0 a 365) después del incumplimiento para desencadenar la acción en los dispositivos de los usuarios. Después de este período de gracia, puede aplicar una directiva de acceso condicional. Si escribe **0** (cero) para el número de días, el acceso condicional surte efecto **inmediatamente**. Por ejemplo, puede bloquear inmediatamente el acceso a los recursos corporativos si un dispositivo no es compatible.

6. Cuando termine, haga clic en **Agregar** > **Aceptar** para guardar los cambios.

## <a name="next-steps"></a>Pasos siguientes

[Supervise las directivas](compliance-policy-monitor.md).
