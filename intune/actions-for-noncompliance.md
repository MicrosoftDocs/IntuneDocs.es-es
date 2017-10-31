---
title: Acciones en caso de incumplimiento con Intune
titleSuffix: Intune on Azure
description: "Obtenga información sobre cómo crear acciones en caso de incumplimiento con Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3adc3c01d4657accfdb5cd70970ff191d06a9aef
ms.sourcegitcommit: a1c751959c9b3d5678bd9d67007e762df30eab59
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2017
---
# <a name="automate-actions-for-noncompliance"></a>Acciones automáticas en caso de incumplimiento

Las **acciones en caso de incumplimiento** le permiten configurar una secuencia de acciones ordenadas en el tiempo que se aplican a dispositivos que no cumplen los criterios de la directiva. De forma predeterminada, cuando se detecta un dispositivo que no cumple los criterios de la directiva de cumplimiento, Intune lo marca inmediatamente como no compatible. A continuación, el dispositivo bloquea el acceso condicional de Azure AD. Las **acciones en caso de incumplimiento** proporcionan más flexibilidad para decidir qué hacer cuando un dispositivo no es compatible. Por ejemplo, puede elegir no bloquear el dispositivo inmediatamente y, luego, conceder al usuario un período de gracia para que sea conforme.

Existen dos tipos de acciones:

-   **Notificar a los usuarios finales por correo electrónico**: puede personalizar la notificación por correo electrónico antes de enviarla al usuario final. Intune permite personalizar el asunto, el cuerpo del mensaje, incluido el logotipo de empresa, la información de contacto y los destinatarios adicionales.

-   **Marcar el dispositivo como no compatible**: puede determinar una programación en que se indique el número de días pasados los cuales hay que marcar el dispositivo como no compatible. Puede ser inmediatamente, pero también puede conceder al usuario un período de gracia para que el dispositivo cumpla las directivas de cumplimiento de dispositivos.

## <a name="before-you-begin"></a>Antes de comenzar

Debe tener, al menos, una directiva de cumplimiento de dispositivos creada para configurar las acciones en caso de incumplimiento.

-   Obtenga más información sobre cómo crear directivas de cumplimiento de dispositivos:

    -   [Android](compliance-policy-create-android.md)

    -   [Android for Work](compliance-policy-create-android-for-work.md)

    -   [iOS](compliance-policy-create-ios.md)
    
    -   [macOS](compliance-policy-create-mac-os.md)

    -   [Windows](compliance-policy-create-windows.md)

Debe tener lista la configuración del acceso condicional de Azure AD cuando vaya a usar las directivas de cumplimiento de dispositivos para bloquear los dispositivos con el fin de evitar que usen los recursos corporativos.

- Obtenga información sobre la [configuración de acceso condicional de EMS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).

Además, debe tener creada una plantilla de mensajes de notificación. La plantilla de mensajes de notificación se utiliza posteriormente en el proceso de creación de acciones en caso de incumplimiento para enviar correos electrónicos a los usuarios.

### <a name="to-create-a-notification-message-template"></a>Para crear una plantilla de mensajes de notificación:

1. Vaya a [Intune en Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de Intune.

2. Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Intune**.

4. Elija **Cumplimiento de dispositivos** y seleccione **Notificaciones** en la sección **Administrar**.

5. Elija **Crear notificación** y después escriba lo siguiente:

    a.  Nombre

    b.  Firmante

    c.  Mensaje

    d.  Encabezado de correo electrónico: incluir el logotipo de la compañía

    e.  Pie de página de correo electrónico: incluir nombre de la empresa

    f.  Pie de página de correo electrónico: incluir información de contacto

![ejemplo de plantilla con el mensaje de notificación](./media/actionsfornoncompliance-1.PNG)

Cuando haya terminado de agregar la información, elija **Crear**. La plantilla de mensajes de notificación está disponible para usarse.

> [!NOTE] 
> También puede editar una plantilla de notificación que creara anteriormente.

## <a name="to-create-actions-for-non-compliance"></a>Pasos para crear acciones en caso de incumplimiento

> [!TIP]
> De forma predeterminada, Intune proporciona una acción predefinida en las acciones para la sección de no cumplimiento. Se trata de la acción que sirve para indicar que el dispositivo no es compatible después de que se haya detectado que no cumple los criterios de la directiva de cumplimiento de dispositivos. Puede personalizar en qué momento después de la detección se marca el dispositivo como no compatible. Esta acción no se puede suprimir.

Puede agregar una acción en el momento de crear o editar una directiva de cumplimiento de dispositivos.

1.  En la carga de trabajo de Intune, en la hoja **Directivas de cumplimiento de dispositivos**, seleccione **Políticas** en la sección **Administrar**.

2.  Elija una directiva de cumplimiento de dispositivos haciendo clic en ella y después elija **Propiedades** en la sección **Administrar**.

3.  La hoja **device compliance policy properties** (Propiedades de directivas de cumplimiento de dispositivos) se abrirá. Seleccione **Acciones en caso de incumplimiento**.

4.  Se abrirá la hoja Acciones en caso de incumplimiento. Elija **Agregar** para especificar los parámetros de acción. Puede elegir la plantilla de mensaje creada anteriormente, los destinatarios adicionales y la programación de un período de gracia. En la programación, puede especificar el número de días (de 0 a 365) para aplicar las directivas de acceso condicional. Si especifica **0** como número de días, el acceso condicional bloqueará **inmediatamente** el acceso a los recursos corporativos cuando los dispositivos no cumplan las directivas de cumplimiento de dispositivos.

5.  Cuando haya terminado de agregar la información, elija **Agregar** y después **Aceptar**.

## <a name="next-steps"></a>Pasos siguientes

Puede supervisar la actividad de cumplimiento de los dispositivos mediante la ejecución de los informes disponibles en la hoja de cumplimiento de dispositivos. Obtenga más información sobre [cómo supervisar el cumplimiento de dispositivos en Intune](device-compliance-monitor.md).

