---
title: Acciones en caso de incumplimiento
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: Aprenda a crear acciones para los dispositivos que no cumplen las directivas"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 16da087e741e335144266c838c0a91050bd7d520
ms.lasthandoff: 03/15/2017


---

# <a name="create-actions-for-non-compliance"></a>Creación de acciones en caso de incumplimiento

**Acciones en caso de incumplimiento** permite configurar una secuencia de acciones ordenada en el tiempo que se aplican a dispositivos que no cumplen las directivas. Por ejemplo, puede notificar por correo electrónico a los usuarios de dispositivos que no cumplen las directivas o bloquear los dispositivos para que no tengan acceso a los recursos corporativos a través del acceso condicional.

## <a name="use-case-scenario"></a>Escenarios de casos de uso

De forma predeterminada, cuando un dispositivo se notifica como No conforme mediante una directiva de cumplimiento de dispositivos de Intune, el acceso condicional bloquea inmediatamente dicho dispositivo y el usuario recibe un correo electrónico con instrucciones para que sea conforme. **Acciones en caso de incumplimiento** proporciona más flexibilidad para decidir qué hacer cuando un dispositivo no cumple las directivas. Por ejemplo, puede elegir no bloquear el dispositivo inmediatamente y, luego, conceder al usuario un período de gracia para que sea conforme.

Existen dos tipos de acciones:

-   Notificar al usuario por correo electrónico

-   Bloquear el acceso a los recursos corporativos a través del acceso condicional

## <a name="notify-the-user-via-email"></a>Notificar al usuario por correo electrónico

Puede elegir plantillas de correo electrónico predeterminadas creada previamente o crear una notificación de correo electrónico totalmente personalizada. Permitimos personalizar el asunto, el cuerpo del mensaje, incluido el logotipo de empresa, la información de contacto y los destinatarios adicionales.

## <a name="block-corporate-resource-access-through-conditional-access"></a>Bloquear el acceso a los recursos corporativos a través del acceso condicional

Puede determinar programar el número de días que se debe bloquear el dispositivo para que no tenga acceso a recursos corporativos. Puede ser inmediatamente, pero también puede conceder al usuario un período de gracia para que el dispositivo cumpla las directivas de cumplimiento de dispositivos.

## <a name="before-you-begin"></a>Antes de comenzar

Debe tener, al menos, una directiva de cumplimiento de dispositivos creada para configurar las acciones en caso de incumplimiento.

-   Obtenga más información sobre cómo crear directivas de cumplimiento de dispositivos:

    -   [Android](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android)

    -   [Android for Work](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android-for-work)

    -   [iOS](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-ios)

    -   [Windows](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-windows)

Debe tener lista la configuración del acceso condicional de EMS cuando vaya a utilizar las directivas de cumplimiento de dispositivos para bloquear los dispositivos con el fin de evitar que usen los recursos corporativos.

- Obtenga información sobre la [configuración de acceso condicional de EMS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).

Además, debe tener creada una plantilla de mensajes de notificación. La plantilla de mensajes de notificación se utiliza posteriormente en el proceso de creación de acciones en caso de incumplimiento para enviar correos electrónicos a los usuarios.

### <a name="to-add-a-notification-message-template"></a>Pasos para agregar una plantilla de mensajes de notificación

En la hoja **Device compliance policies** (Directivas de cumplimiento de dispositivos), siga estos pasos:

1.  En **Administrar**, elija **Notificaciones**; se abrirá la hoja de plantillas de mensaje de notificación.

    ![Pasos para agregar una plantilla de notificación](../media/afnc-1.png)

2.  Elija **Agregar**; deberá definir lo siguiente:

    a.  Descripción

    b.  From

    c.  Firmante

    d.  Mensaje

    e.  Encabezado de correo electrónico: incluir el logotipo de la compañía

    f.  Pie de página de correo electrónico: incluir nombre de la empresa

    g.  Pie de página de correo electrónico: incluir información de contacto

     ![Plantilla de mensajes de notificación](../media/afnc-2.png)

Cuando haya terminado de agregar la información, puede hacer clic en **Crear**. La plantilla de mensajes de notificación está disponible para usarse.

> [!NOTE] 
> También puede editar una plantilla de notificación que creara anteriormente.

## <a name="to-create-actions-for-non-compliance"></a>Pasos para crear acciones en caso de incumplimiento

Puede agregar una acción en el momento de crear o editar una directiva de cumplimiento de dispositivos.

1.  En la hoja **Device compliance policies** (Directivas de cumplimiento de dispositivos), en **Administrar**, seleccione **Directivas**.

2.  Elija una directiva de cumplimiento de dispositivos haciendo clic en ella.

    ![Directivas de cumplimiento](../media/afnc-3.png)

3.  La hoja **device compliance policy properties** (Propiedades de directivas de cumplimiento de dispositivos) se abrirá. Seleccione **Acciones en caso de incumplimiento**.

4.  Se abrirá la hoja Acciones en caso de incumplimiento. Elija **Agregar** para especificar los parámetros de acción.

    ![Hoja Acciones en caso de incumplimiento](../media/afnc-4.png)

Las acciones en caso de incumplimiento son las siguientes:

-   **Aplicar una directiva de acceso condicional**

-   **Enviar un correo electrónico al usuario final**

### <a name="enforce-conditional-access-policy"></a>Aplicar una directiva de acceso condicional

Para agregar esta acción en caso de cumplimiento, siga estos pasos:

1.  En la hoja **Acciones de no conformidad**, elija **Agregar**.

2.  En la hoja **Parámetros de acción**, seleccione **Enforce conditional access policy** (Aplicar una directiva de acceso condicional) en la lista desplegable de acciones.

3.  En **Programación**, puede especificar el número de días (de 0 a 255) que se aplicará directiva de acceso condicional. Si especifica **0** como número de días, el acceso condicional bloqueará **inmediatamente** el acceso a los recursos corporativos cuando los dispositivos no cumplan las directivas de cumplimiento de dispositivos.

    ![Programación de acciones en caso de incumplimiento](../media/afnc-5.png)

4.  Elija **Agregar** y, luego, haga clic en el botón **Aceptar** de la hoja **Acciones**.

5.  En la hoja **device compliance policy properties** (Propiedades de directivas de cumplimiento de dispositivos), elija **Guardar**.

### <a name="send-e-mail-to-end-user"></a>Enviar un correo electrónico al usuario final

Puede usar una plantilla de correo electrónico para enviar notificaciones a los usuarios que no cumplan las directivas. Estos mensajes ayudan a que se cumplan las directivas de cumplimiento de dispositivos en toda la organización.

Para agregar esta acción en caso de cumplimiento, siga estos pasos:

1.  En la hoja **Acciones de no conformidad**, elija **Agregar**.

2.  En la hoja **Parámetros de acción**, seleccione **Send e-mail to end user** (Enviar un correo electrónico al usuario final) en la lista desplegable de acciones.

3.  Elija una plantilla de mensajes creada anteriormente haciendo clic en **Plantilla de mensajes**. Puede ver el contenido de la plantilla de mensajes y, luego, elegir **Seleccione**.

    ![Plantilla de mensajes](../media/afnc-6.png)

> [!NOTE] 
> Puede ver la plantilla de mensajes, pero no editarla. Si desea editar la plantilla de mensajes, debe volver a la hoja **Notificaciones**.

1.  En **Programación**, escriba el número de días que deben transcurrir para enviar el correo electrónico de no conformidad. Si especifica **0** como número de días, el mensaje se enviará **inmediatamente**.

2.  Elija **Agregar** y, luego, haga clic en el botón **Aceptar** de la hoja **Acciones**.

3.  En la hoja **device compliance policy properties** (Propiedades de directivas de cumplimiento de dispositivos), elija **Guardar**.

