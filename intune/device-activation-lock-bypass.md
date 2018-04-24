---
title: Omisión del bloqueo de activación de iOS con Intune
titlesuffix: Microsoft Intune
description: Aprenda a usar Intune para omitir el bloqueo de activación de iOS a fin de acceder a los dispositivos bloqueados.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2a8c14e523d33c9e0994134ff1ef468b290b3992
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>Omisión del bloqueo de activación en dispositivos iOS supervisados con Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune puede ayudarle a administrar el bloqueo de activación de iOS, una característica de la aplicación Buscar mi iPhone para dispositivos iOS 8.0 y posteriores. El bloqueo de activación se habilita automáticamente cuando un usuario abre la aplicación Buscar mi iPhone en un dispositivo. Tras su activación, se debe escribir el identificador y la contraseña de Apple del usuario para poder:

- Desactivar Buscar mi iPhone
- Borrar el dispositivo
- Reactivar el dispositivo

## <a name="how-activation-lock-affects-you"></a>Cómo afecta el bloqueo de activación

Aunque el bloqueo de activación ayuda a proteger los dispositivos iOS y aumenta las posibilidades de recuperar un dispositivo perdido o robado, esta funcionalidad puede suponerle una serie de desafíos como administrador de TI. Por ejemplo:

- Un usuario establece el bloqueo de activación en un dispositivo. Luego, el usuario se va de la empresa y devuelve el dispositivo. Sin el identificador y la contraseña de Apple del usuario, no hay forma de volver a activar el dispositivo.
- Necesita un informe de todos los dispositivos que tienen habilitado el bloqueo de activación.
- Durante una actualización de los dispositivos de la organización, puede que quiera reasignar algunos dispositivos a un departamento diferente. Solo puede volver a asignar dispositivos que no tengan habilitado el bloqueo de activación.

Para ayudar a resolver estos problemas, Apple incorporó el bypass del bloqueo de activación en iOS 7.1. El bypass del Bloqueo de activación permite quitar el Bloqueo de activación de los dispositivos supervisados sin el identificador y la contraseña de Apple del usuario. Los dispositivos supervisados pueden generar un código de bypass del bloqueo de activación específico del dispositivo, que se almacena en el servidor de activación de Apple.

>[!TIP]
>El modo supervisado de los dispositivos iOS permite usar Apple Configurator para bloquear un dispositivo y limitar la funcionalidad para fines empresariales específicos. El modo supervisado solo se usa para los dispositivos de la empresa.

Puede leer más acerca de bloqueo de activación en [el sitio web de Apple](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>Cómo ayuda Intune a administrar el bloqueo de activación
Intune puede solicitar el estado de bloqueo de activación de dispositivos supervisados que ejecutan iOS 8.0 y versiones posteriores. Solamente para los dispositivos supervisados, Intune puede recuperar el código de bypass del bloqueo de activación y emitirlo directamente al dispositivo. En caso de que el dispositivo se haya borrado, puede acceder directamente a él usando un nombre de usuario en blanco y el código como la contraseña.

**Las ventajas empresariales de usar Intune para administrar el Bloqueo de activación son las siguientes:**

- El usuario obtiene los beneficios de seguridad de la aplicación Buscar mi iPhone.
- Puede permitir que los usuarios hagan su trabajo y sepa que, cuando el dispositivo se deba reasignar, podrá retirarlo o desbloquearlo.

## <a name="before-you-start"></a>Antes de empezar
Para omitir el Bloqueo de activación en los dispositivos, primero debe habilitarlo. Para ello, siga estas instrucciones:

1. Configure un perfil de restricción de Intune para iOS mediante la información que se describe en [Configuración de restricciones de dispositivos en Microsoft Intune](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. En la [configuración de restricción de dispositivos para iOS](device-restrictions-ios.md), en la sección **General**, habilite la opción **Bloqueo de activación**.
3. Guarde el perfil y [asígnelo](device-profile-assign.md) a los dispositivos en los que quiera administrar la omisión de Bloqueo de activación.


## <a name="how-to-use-activation-lock-bypass"></a>Uso de la omisión del bloqueo de activación

>[!IMPORTANT]
>Después de omitir el Bloqueo de activación en un dispositivo, si se abre la aplicación Buscar mi iPhone, se aplicará automáticamente un nuevo Bloqueo de activación. Por este motivo, **para realizar este procedimiento, debe tener el dispositivo físicamente**.

La acción de dispositivo remoto **Omitir bloqueo de activación** quita el bloqueo de activación de un dispositivo iOS sin el id. de Apple y la contraseña del usuario. Cuando se omite el bloqueo de activación, el dispositivo activa de nuevo el bloqueo de activación cuando se inicia la aplicación Buscar mi iPhone. Omita el bloqueo de activación solo si tiene acceso físico al dispositivo.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos**, pulse **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo iOS supervisado, **Más** y, luego, la acción remota de dispositivo **Omisión del bloqueo de activación**.

## <a name="next-steps"></a>Pasos siguientes

Puede examinar el estado de la solicitud de desbloqueo en la página de detalles del dispositivo de la carga de trabajo **Administrar dispositivos**.
