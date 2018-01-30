---
title: Acciones en caso de incumplimiento con Intune
titleSuffix: Intune on Azure
description: "Obtenga información sobre cómo crear acciones en caso de incumplimiento con Intune"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 01/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e45f5d3836fc33851c650703f713c03204df792
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="automate-actions-for-noncompliance"></a>Acciones automáticas en caso de incumplimiento

Las **acciones en caso de incumplimiento** le permiten configurar una secuencia de acciones ordenadas en el tiempo que se aplican a dispositivos que no cumplen los criterios de la directiva. De forma predeterminada, cuando se detecta un dispositivo que no cumple los criterios de la directiva de cumplimiento, Intune lo marca inmediatamente como no compatible. A continuación, el dispositivo bloquea el acceso condicional de Azure AD. Las **acciones en caso de incumplimiento** proporcionan más flexibilidad para decidir qué hacer cuando un dispositivo no es compatible. Por ejemplo, puede elegir no bloquear el dispositivo inmediatamente y, luego, conceder al usuario un período de gracia para que sea conforme.

Existen dos tipos de acciones:

-   **Notificar a los usuarios finales por correo electrónico**: puede personalizar la notificación por correo electrónico antes de enviarla al usuario final. Intune permite personalizar los destinatarios, el asunto, el cuerpo del mensaje, incluido el logotipo de la empresa, y la información de contacto.
-   **Marcar el dispositivo como no compatible**: puede determinar una programación en que se indique el número de días pasados los cuales hay que marcar el dispositivo como no compatible. Puede configurar la acción para que surta efecto de inmediato, pero también puede conceder al usuario un período de gracia para que el dispositivo cumpla las directivas de cumplimiento de dispositivos.

## <a name="before-you-begin"></a>Antes de comenzar

- Debe tener, al menos, una directiva de cumplimiento de dispositivos creada para configurar las acciones en caso de incumplimiento. Aprenda a crear una directiva de cumplimiento de directivas para las plataformas siguientes:

    -   [Android](compliance-policy-create-android.md)
    -   [Android for Work](compliance-policy-create-android-for-work.md)
    -   [iOS](compliance-policy-create-ios.md)
    -   [macOS](compliance-policy-create-mac-os.md)
    -   [Windows](compliance-policy-create-windows.md)

- Debe tener lista la configuración del acceso condicional de Azure AD cuando vaya a usar las directivas de cumplimiento de dispositivos para bloquear los dispositivos con el fin de evitar que usen los recursos corporativos. Obtenga información sobre la [configuración de acceso condicional de EMS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).

- Debe tener creada una plantilla de mensajes de notificación. La plantilla de mensajes de notificación se utiliza posteriormente en el proceso de creación de acciones en caso de incumplimiento para enviar correos electrónicos a los usuarios.

- Debe configurar Exchange Online para que acepte el correo electrónico procedente de *IntuneNotificationService@microsoft.com* para permitir que Intune envíe la notificación de correo electrónico. Para obtener más información, vea [Configurar restricciones de entrega de mensajes para un buzón de correo](https://technet.microsoft.com/library/bb397214(v=exchg.160).aspx).

### <a name="to-create-a-notification-message-template"></a>Para crear una plantilla de mensajes de notificación:

1. Vaya a [Intune en Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de Intune.
2. Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.
3. Elija **Intune**.
4. Elija **Cumplimiento de dispositivos** y seleccione **Notificaciones** en la sección **Administrar**.
5. Elija **Crear notificación** y después escriba la siguiente información:
    - Nombre
    - Firmante
    - Mensaje
    - Encabezado de correo electrónico: incluir el logotipo de la compañía
    - Pie de página de correo electrónico: incluir nombre de la empresa
    - Pie de página de correo electrónico: incluir información de contacto

   ![ejemplo de plantilla con el mensaje de notificación](./media/actionsfornoncompliance-1.PNG)

Cuando haya terminado de agregar la información, elija **Crear**. La plantilla de mensajes de notificación está disponible para usarse.

> [!NOTE] 
> También puede editar una plantilla de notificación que creara anteriormente.

## <a name="to-create-actions-for-non-compliance"></a>Pasos para crear acciones en caso de incumplimiento

> [!TIP]
> De forma predeterminada, Intune proporciona una acción predefinida en las acciones para la sección de no cumplimiento. La acción indica que el dispositivo no es compatible después de que se haya detectado que no cumple los criterios de la directiva de cumplimiento de dispositivos. Puede personalizar en qué momento después de la detección se marca el dispositivo como no compatible. La acción no se puede suprimir.

Puede agregar una acción en el momento de crear una directiva de cumplimiento de dispositivos o al editar una ya existente.

1.  En la carga de trabajo de Intune, en la hoja **Directivas de cumplimiento de dispositivos**, seleccione **Políticas** en la sección **Administrar**.
2.  Elija una directiva de cumplimiento de dispositivos haciendo clic en ella y después elija **Propiedades** en la sección **Administrar**.
3.  En la hoja de **propiedades de directivas de cumplimiento de dispositivos**, seleccione **Acciones en caso de incumplimiento**.
4.  En la hoja **Acciones en caso de incumplimiento**, elija **Agregar** para especificar los parámetros de acción. Puede elegir la plantilla de mensaje creada anteriormente, los destinatarios adicionales y la programación de un período de gracia. En la programación, puede especificar el número de días (de 0 a 365) para aplicar las directivas de acceso condicional. Si especifica **0** como número de días, el acceso condicional bloqueará **inmediatamente** el acceso a los recursos corporativos cuando los dispositivos no cumplan las directivas de cumplimiento de dispositivos.
5.  Cuando haya terminado de agregar la información, elija **Agregar** y después **Aceptar**.

## <a name="next-steps"></a>Pasos siguientes
Puede supervisar la actividad de cumplimiento de los dispositivos mediante la ejecución de los informes disponibles en la hoja de cumplimiento de dispositivos. Para obtener más información, consulte [Supervisión del cumplimiento de dispositivos en Intune](device-compliance-monitor.md).

