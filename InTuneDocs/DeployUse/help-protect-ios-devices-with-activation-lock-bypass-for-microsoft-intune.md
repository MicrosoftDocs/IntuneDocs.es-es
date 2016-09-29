---
title: "Administrar el bloqueo de activación de iOS en dispositivos | Microsoft Intune"
description: "Microsoft Intune puede ayudarle a administrar el bloqueo de activación de iOS, una característica de la aplicación Buscar mi iPhone para dispositivos iOS 7.1 o versiones posteriores."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d9e08429fb6c834476fd0029d559059c5132afca
ms.openlocfilehash: 2b44779fdac0764a3e7a18f1c365050e9800f902


---

# Ayudar a proteger dispositivos iOS con el bypass del bloqueo de activación para Microsoft Intune
Microsoft Intune puede ayudarle a administrar el bloqueo de activación de iOS, una característica de la aplicación Buscar mi iPhone para dispositivos iOS 8.0 y posteriores. El bloqueo de activación se habilita automáticamente cuando un usuario abre la aplicación Buscar mi iPhone en un dispositivo. Tras su activación, se debe escribir el identificador y la contraseña de Apple del usuario para poder: 

-   Desactivar Buscar mi iPhone

-   Borrar el dispositivo

-   Reactivar el dispositivo

## Cómo afecta el bloqueo de activación
Aunque el bloqueo de activación ayuda a proteger los dispositivos iOS y aumenta las posibilidades de recuperar un dispositivo perdido o robado, esta funcionalidad puede suponerle una serie de desafíos como administrador de TI. Por ejemplo:

-   Un usuario establece el bloqueo de activación en un dispositivo. Luego, el usuario se va de la empresa y devuelve el dispositivo. Sin el identificador y la contraseña de Apple del usuario, no hay forma de volver a activar el dispositivo.

-   Necesita un informe de todos los dispositivos que tienen habilitado el bloqueo de activación.

-   Durante una actualización de los dispositivos de la organización, puede que quiera reasignar algunos dispositivos a un departamento diferente. Solo puede volver a asignar dispositivos que no tengan habilitado el bloqueo de activación.

Para ayudar a resolver estos problemas, Apple incorporó el bypass del bloqueo de activación en iOS 7.1. Esto permite quitar el bloqueo de activación de los dispositivos supervisados sin el identificador y la contraseña de Apple del usuario. Los dispositivos supervisados pueden generar un código de bypass del bloqueo de activación específico del dispositivo, que se almacena en el servidor de activación de Apple.

> [!TIP]
> El modo supervisado de los dispositivos iOS permite usar Apple Configurator para bloquear un dispositivo y limitar la funcionalidad para fines empresariales específicos. Generalmente, el modo supervisado es solo para los dispositivos de la empresa.

## Cómo ayuda Intune a administrar el bloqueo de activación
Intune puede solicitar el estado de bloqueo de activación de dispositivos supervisados y no supervisados que ejecutan iOS 8.0 y versiones posteriores. Solamente para los dispositivos supervisados, Intune puede recuperar el código de bypass del bloqueo de activación y emitirlo directamente al dispositivo. En caso de que el dispositivo se haya borrado, puede obtener acceso directamente a él si usa el código como nombre de usuario y deja la contraseña en blanco.

**Las ventajas empresariales de esto son**:

-   El usuario obtiene los beneficios de seguridad de la aplicación Buscar mi iPhone.

-   Puede permitir que los usuarios hagan su trabajo y sepa que, cuando el dispositivo se deba reasignar, podrá retirarlo o desbloquearlo.

## Usar el bypass del bloqueo de activación desde la consola de administración de Intune
> [!IMPORTANT]
> Después de omitir el bloqueo de activación en un dispositivo, un nuevo bloqueo de activación se aplica automáticamente si se abre la aplicación Buscar mi iPhone. Por este motivo, **para realizar este procedimiento, debe tener el dispositivo físicamente**.

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos corporativos**.

2.  Seleccione el dispositivo para el que desea omitir el bloqueo de activación. Seleccione **Bypass del bloqueo de activación**.

3.  Lea el mensaje de advertencia. Seleccione **Sí** para continuar.

Puede examinar el estado de la solicitud de desbloqueo en la página de detalles del dispositivo.

## Ver los dispositivos que usan el bloqueo de activación
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


### Consulte también
[Retirar dispositivos](retire-devices-from-microsoft-intune-management.md)
[Ayudar a proteger los dispositivos con el restablecimiento de código de acceso y el bloqueo remoto](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


