---
# required metadata

title: Ayudar a proteger dispositivos iOS con el bypass del bloqueo de activación para Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ayudar a proteger dispositivos iOS con el bypass del bloqueo de activación para Microsoft Intune
Microsoft Intune puede ayudarle a administrar el bloqueo de activación de iOS, una característica de la aplicación Buscar mi iPhone para dispositivos iOS 7.1 o versiones posteriores. El bloqueo de activación se habilita automáticamente cuando se usa la aplicación Buscar mi iPhone en un dispositivo. Tras su activación, se debe escribir el identificador y la contraseña de Apple del usuario para poder:

-   Desactivar Buscar mi iPhone

-   Borrar el dispositivo

-   Reactivar el dispositivo

## Cómo afecta el bloqueo de activación
Aunque el bloqueo de activación ayuda a proteger dispositivos iOS y aumenta las posibilidades de recuperarlos ante la pérdida o el robo, esta funcionalidad puede suponerle una serie de desafíos como administrador de TI. Por ejemplo:

-   Uno de los usuarios establece el bloqueo de activación en un dispositivo. Luego, el usuario se va de la empresa y devuelve el dispositivo. Sin el identificador y la contraseña de Apple del usuario, no hay forma de volver a activar el dispositivo.

-   Necesita un informe de todos los dispositivos que tienen habilitado el bloqueo de activación.

-   Durante una actualización de los dispositivos de la organización, puede que desee reasignar algunos dispositivos a un departamento diferente. Solo puede volver a asignar dispositivos que no tengan habilitado el bloqueo de activación.

Para ayudar a resolver estos problemas, Apple incorporó el bypass del bloqueo de activación en iOS 7.1. Esto permite quitar el bloqueo de activación de los dispositivos supervisados sin el identificador y la contraseña de Apple del usuario. Los dispositivos supervisados pueden generar un código de bypass del bloqueo de activación específico del dispositivo, que se almacena en el servidor de activación de Apple.

> [!TIP]
> El modo supervisado de los dispositivos iOS permite usar la herramienta Apple Configurator para bloquear un dispositivo a fin de limitar la funcionalidad para fines empresariales específicos. Generalmente, el modo supervisado es solo para los dispositivos de la empresa.

## Cómo ayuda Intune a administrar el bloqueo de activación
Intune puede solicitar el estado de bloqueo de activación de dispositivos supervisados y no supervisados que ejecutan iOS 7.1 y versiones posteriores. Para los dispositivos supervisados, Intune puede recuperar el código de bypass del bloqueo de activación y emitirlo directamente al dispositivo. Si el dispositivo se borró, puede obtener acceso directamente usando el código mencionado como nombre de usuario y dejando la contraseña en blanco.

**Las ventajas empresariales de esto son**:

-   El usuario obtiene los beneficios de seguridad de la aplicación Buscar mi iPhone.

-   Puede permitir que el usuario haga su trabajo sabiendo que, cuando el dispositivo se deba reasignar, podrá retirarlo o desbloquearlo.

## Usar el bypass del bloqueo de activación desde la consola de administración de Intune
> [!IMPORTANT]
> Después de omitir el bloqueo de activación en un dispositivo, se aplica automáticamente un nuevo bloqueo de activación si se abre la aplicación Buscar mi iPhone. Por este motivo, **para realizar este procedimiento, debe tener el dispositivo físicamente**..

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos corporativos**..

2.  Seleccione el dispositivo para el que desea omitir el bloqueo de activación. Seleccione **Bypass del bloqueo de activación**..

3.  Lea el mensaje de advertencia. Seleccione **Sí** para continuar.

Puede examinar el estado de la solicitud de desbloqueo en la página de detalles del dispositivo.

## Ver los dispositivos que usan el bloqueo de activación
Para ver los dispositivos que usan el bloqueo de activación, existen dos métodos:

-   Ejecute los **Informes de inventario de dispositivos móviles**. Este informe muestra las columnas **Estado de activación de bloqueo** y **Supervisado** para indicar el estado de los dispositivos. Los valores de **Supervisado** son **Sí** o **No**, mientras que los de **Estado de activación de bloqueo** son:

    -   Habilitado con código de derivación

    -   Habilitado sin código de derivación (el dispositivo no está supervisado)

    -   Habilitado sin código de derivación (no se puede establecer contacto con el dispositivo)

    -   No habilitado

    El campo **Estado de bloqueo de activación** está en blanco para los dispositivos que no ejecutan iOS 7.1 o versiones posteriores.

-   Seleccione un dispositivo en una vista de grupos para ver el estado de bloqueo de activación en el panel de detalles del dispositivo.

    Si selecciona un dispositivo del nodo **Todos los dispositivos corporativos** y el bloqueo de activación está habilitado para el dispositivo, también podrá ver el código de derivación. Este código se puede usar para emitir un bypass del bloqueo de activación manualmente.

### Consulte también
[Retirar dispositivos](retire-devices-from-microsoft-intune-management.md)
[Help protect your devices with remote lock and passcode reset (Protección de los dispositivos mediante bloqueo remoto y restablecimiento de código de acceso)](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


