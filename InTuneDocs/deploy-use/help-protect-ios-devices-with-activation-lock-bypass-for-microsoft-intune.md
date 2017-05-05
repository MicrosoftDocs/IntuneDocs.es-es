---
title: "Administrar el bloqueo de activación de iOS en dispositivos | Microsoft Docs"
description: "Microsoft Intune puede ayudarle a administrar el bloqueo de activación de iOS, una característica de la aplicación Buscar mi iPhone para dispositivos iOS 7.1 o versiones posteriores."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 742fac9c401c24bfc0f2500a238c41fa00c47fd3
ms.lasthandoff: 04/24/2017


---

# <a name="help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune"></a>Ayudar a proteger dispositivos iOS con el bypass del bloqueo de activación para Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune puede ayudarle a administrar el bloqueo de activación de iOS, una característica de la aplicación Buscar mi iPhone para dispositivos iOS 8.0 y posteriores. El bloqueo de activación se habilita automáticamente cuando un usuario abre la aplicación Buscar mi iPhone en un dispositivo. Tras su activación, se debe escribir el identificador y la contraseña de Apple del usuario para poder: 

-   Desactivar Buscar mi iPhone

-   Borrar el dispositivo

-   Reactivar el dispositivo

## <a name="how-activation-lock-affects-you"></a>Cómo afecta el bloqueo de activación
Aunque el bloqueo de activación ayuda a proteger los dispositivos iOS y aumenta las posibilidades de recuperar un dispositivo perdido o robado, esta funcionalidad puede suponerle una serie de desafíos como administrador de TI. Por ejemplo:

-   Un usuario establece el bloqueo de activación en un dispositivo. Luego, el usuario se va de la empresa y devuelve el dispositivo. Sin el identificador y la contraseña de Apple del usuario, no hay forma de volver a activar el dispositivo.

-   Necesita un informe de todos los dispositivos que tienen habilitado el bloqueo de activación.

-   Durante una actualización de los dispositivos de la organización, puede que quiera reasignar algunos dispositivos a un departamento diferente. Solo puede volver a asignar dispositivos que no tengan habilitado el bloqueo de activación.

Para ayudar a resolver estos problemas, Apple incorporó el bypass del bloqueo de activación en iOS 7.1. Esto permite quitar el bloqueo de activación de los dispositivos supervisados sin el identificador y la contraseña de Apple del usuario. Los dispositivos supervisados pueden generar un código de bypass del bloqueo de activación específico del dispositivo, que se almacena en el servidor de activación de Apple.

> [!TIP]
> El modo supervisado de los dispositivos iOS permite usar Apple Configurator para bloquear un dispositivo y limitar la funcionalidad para fines empresariales específicos. Generalmente, el modo supervisado es solo para los dispositivos de la empresa.

[Aquí](https://support.apple.com/en-us/HT201365)encontrará más información sobre el bloqueo de activación.

## <a name="how-intune-helps-you-manage-activation-lock"></a>Cómo ayuda Intune a administrar el bloqueo de activación
Intune puede solicitar el estado de bloqueo de activación de dispositivos supervisados que ejecutan iOS 8.0 y versiones posteriores. Solamente para los dispositivos supervisados, Intune puede recuperar el código de bypass del bloqueo de activación y emitirlo directamente al dispositivo. En caso de que el dispositivo se haya borrado, puede acceder directamente a él usando un nombre de usuario en blanco y el código como la contraseña.

**Las ventajas empresariales de esto son**:

-   El usuario obtiene los beneficios de seguridad de la aplicación Buscar mi iPhone.

-   Puede permitir que los usuarios hagan su trabajo y sepan que, cuando el dispositivo se deba reasignar, podrá retirarlo o desbloquearlo.

## <a name="before-you-start"></a>Antes de empezar

Para omitir el Bloqueo de activación en los dispositivos, primero debe habilitarlo. Para ello:

1. Use la información del tema [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) para crear una [directiva de configuración de dispositivos](/intune/deploy-use/ios-policy-settings-in-microsoft-intune) de iOS.
2. En la sección **Inscripción** de la página de configuración, configure el parámetro **Permitir bloqueo de activación cuando el dispositivo está en modo supervisado** en **Sí**.
3. Guarde la directiva e impleméntela en los dispositivos en los que desea administrar la omisión del Bloqueo de activación.

## <a name="how-to-use-activation-lock-bypass-from-the-intune-admin-console"></a>Usar el bypass del bloqueo de activación desde la consola de administración de Intune
> [!IMPORTANT]
> Después de omitir el bloqueo de activación en un dispositivo, un nuevo bloqueo de activación se aplica automáticamente si se abre la aplicación Buscar mi iPhone. Por este motivo, **para realizar este procedimiento, debe tener el dispositivo físicamente**.

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos corporativos**.

2.  Seleccione el dispositivo para el que desea omitir el bloqueo de activación. Seleccione **Bypass del bloqueo de activación**.

3.  Lea el mensaje de advertencia. Seleccione **Sí** para continuar.

Puede examinar el estado de la solicitud de desbloqueo en la página de detalles del dispositivo.

## <a name="how-to-see-which-devices-are-using-activation-lock"></a>Ver los dispositivos que usan el bloqueo de activación
Para ver los dispositivos que usan el bloqueo de activación, existen dos métodos:

-   Ejecute los **Informes de inventario de dispositivos móviles**. En este informe se muestran las columnas **Estado de bloqueo de activación** y **Supervisado** para indicar el estado de los dispositivos. Los valores de **Supervisado** son **Sí** o **No**, mientras que los de **Estado de activación de bloqueo** son:

    -   Habilitado con código de derivación

    -   Habilitado sin código de derivación (el dispositivo no está supervisado)

    -   Habilitado sin código de derivación (no se puede establecer contacto con el dispositivo)

    -   No habilitado

    El cuadro **Estado del bloqueo de activación** está en blanco para los dispositivos que no ejecutan iOS 8.0 o versiones posteriores.

-   Seleccione un dispositivo en una vista de grupos para ver el estado de bloqueo de activación en el panel de detalles del dispositivo.

    Si selecciona un dispositivo del nodo **Todos los dispositivos corporativos** y el bloqueo de activación está habilitado para el dispositivo, también puede ver el código de derivación. Este código se puede usar para emitir un bypass del bloqueo de activación manualmente.

    > [!IMPORTANT]
    >Intune hace un inventario de dispositivos para el bloqueo de activación cada siete días. Por este motivo, puede que los dispositivos no se muestren inmediatamente con el estado Bloqueo de activación en la consola de Intune.


### <a name="see-also"></a>Consulte también
[Retirar dispositivos](retire-devices-from-microsoft-intune-management.md)
[Ayudar a proteger los dispositivos con el restablecimiento de código de acceso y el bloqueo remoto](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)

