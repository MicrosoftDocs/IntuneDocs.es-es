---
title: "Elegir cómo inscribir los dispositivos iOS en Intune"
titleSuffix: Intune on Azure
description: "Aprenda a configurar la inscripción de dispositivos iOS en Microsoft Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 092f582cf30210858bd8cdd3879edfa873523ccb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="choose-how-to-enroll-ios-and-macos-devices"></a>Elegir cómo inscribir dispositivos iOS y macOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En este tema se describen los métodos que un administrador de TI puede usar para habilitar la inscripción de dispositivos iOS en Intune.

Use la siguiente información para decidir qué método usar para inscribir dispositivos iOS. Todos los métodos siguientes, excepto BYOD, son para la inscripción de dispositivos corporativos.

**Requisito previo:** se requiere un [certificado de Apple Push Notification Service](apple-mdm-push-certificate-get.md).

## <a name="user-owned-ios-devices-byod"></a>Dispositivos iOS corporativos (BYOD)

Si los usuarios quieren inscribir sus dispositivos personales, BYOD (traiga su propio dispositivo), pueden descargar la aplicación Portal de empresa para iOS desde la Tienda de aplicaciones y seguir las instrucciones de inscripción de la aplicación. Una vez inscritos, los usuarios pueden conectarse a la red de empresa, unirse al dominio o a Azure Active Directory y obtener acceso a los recursos corporativos. Para habilitar BYOD, el único requisito es un [certificado de Apple Push Notification Service](apple-mdm-push-certificate-get.md). También puede bloquear la inscripción de los dispositivos iOS de propiedad personal. Vea [Set device type restrictions](enrollment-restrictions-set.md) (Establecer restricciones de tipos de dispositivo) para obtener instrucciones.

## <a name="user-owned-macos-devices-byod"></a>Dispositivos macOS propiedad del usuario (BYOD)

Puede habilitar la inscripción de dispositivos macOS. Para habilitar la inscripción de macOS, el único requisito es un [certificado de Apple Push Notification Service](apple-mdm-push-certificate-get.md). Para más información, vea [Inscripción de dispositivos macOS](./macos-enroll.md).

## <a name="enrollment-program-with-apple"></a>Programa de inscripción de Apple
Apple ofrece programas de compra de dispositivos que incluyen una infraestructura de administración e inscripción de dispositivos. Los dispositivos adquiridos a través de alguno de estos programas pueden inscribirse de forma masiva "por vía inalámbrica" mediante la asignación de números de serie de dispositivo en la infraestructura de administración de Intune.

- **Programa de inscripción de dispositivos (DEM)**: programa de inscripción de dispositivos de Apple para organizaciones y empresas. Para más información, consulte [Inscripción de dispositivos iOS mediante el Programa de inscripción de dispositivos](device-enrollment-program-enroll-ios.md).
- **Apple School Manager**: programa de inscripción de dispositivos de Apple para centros escolares. Para obtener más información, vea [Habilitación de la inscripción de dispositivos iOS con Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator

Puede inscribir dispositivos iOS mediante la exportación de un perfil de inscripción corporativa y, después, mediante la conexión de esos dispositivos móviles a un equipo Mac que ejecuta Apple Configurator. Apple Configurator admite dos formas de inscripción:

- **Inscripción con el Asistente de configuración**: restablece la configuración de fábrica del dispositivo y lo prepara para que el nuevo usuario del dispositivo lo configure. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute Apple Configurator para preconfigurar la inscripción. Después, los dispositivos se entregan a los usuarios, que ejecutan el proceso del Asistente de configuración la primera vez que se inician los dispositivos. Este proceso configura el dispositivo con las credenciales profesionales o educativas de los usuarios y completa el proceso de inscripción. Para más información, consulte [Inscripción de dispositivos iOS con Apple Configurator y el Asistente de configuración](apple-configurator-setup-assistant-enroll-ios.md).

- **Inscripción directa**: crea un archivo compatible con Apple Configurator para su uso durante la preparación del dispositivo. No se restablece la configuración de fábrica del dispositivo inscrito, y no está asociado a ningún usuario. Para inscribir dispositivos, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute Apple Configurator. Para obtener más información, consulte [Inscribir directamente dispositivos iOS mediante Apple Configurator](apple-configurator-direct-enroll-ios.md).

## <a name="use-the-device-enrollment-program-dep"></a>Usar el Programa de inscripción de dispositivos (DEP)

DEP implementa un perfil de inscripción "de forma inalámbrica" en los dispositivos que se adquieren a través de DEP. Cuando un usuario ejecuta el Asistente de configuración en el dispositivo la primera vez que se inicia, el dispositivo se inscribe en Intune. Para más información, consulte [Inscripción de dispositivos iOS mediante el Programa de inscripción de dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="use-the-device-enrollment-manager-dem"></a>Uso del administrador de inscripción de dispositivos (DEM)
El administrador de inscripción de dispositivos es una cuenta de usuario genérica que puede inscribir y administrar hasta 1000 dispositivos. Los dispositivos administrados por el administrador de inscripción de dispositivos no pueden tener afinidad de usuario, por lo que el dispositivo nunca tiene propietario. Asigne a un usuario de Intune permisos de DEM para proporcionarles estas funciones. En cada dispositivo que el usuario de DEM inscribe usa una licencia de Intune. Para más información, consulte [Inscripción de dispositivos con el administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md).
