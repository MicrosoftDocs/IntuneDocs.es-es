---
title: "Introducción a las directivas"
titleSuffix: Intune on Azure
description: Cree directivas para evitar que los usuarios usen sus dispositivos de forma no autorizada.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b12b80ac13868b6706d2d4e7532ec13cba9a5b7e
ms.sourcegitcommit: 45204e0fb8cb4cce449e65f2f1d7bb6f6ac4ccf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2017
---
# <a name="get-started-with-policies"></a>Introducción a las directivas

Uno de los objetivos principales de la introducción a Intune es la inscripción de dispositivos para garantizar que son compatibles con las directivas de la empresa. Las directivas de cumplimiento no solo le ayudan a administrar tipos de dispositivo especializados, como los quioscos propiedad de la empresa, sino también dispositivos sin usuario, tabletas y dispositivos personales (Bring Your Own).

![Panel de cumplimiento con muy pocos datos](/intune/media/generic-compliance-dashboard.png)

Las directivas de cumplimiento proporcionan las siguientes funciones de administración para dispositivos móviles:

* Regular el número de dispositivos que cada usuario inscribe
* Administrar la configuración de dispositivos (por ejemplo, cifrado de nivel de dispositivo, longitud de la contraseña, uso de la cámara)
* Entregar aplicaciones, perfiles de correo electrónico, perfiles de VPN, etc.
* Evaluar los criterios de nivel de dispositivo para las directivas de cumplimiento de seguridad

Cree directivas de cumplimiento para cada plataforma de manera independiente. Para este ejercicio, nos centraremos en iOS. Están disponibles las siguientes directivas para los dispositivos iOS:

* Configuración de contraseña o PIN
* Cifrado del dispositivo
* Dispositivo con Jailbreak
* Perfil de correo electrónico
* Versión de SO mínima
* Versión de SO máxima

__¿Cómo se crea una directiva?__

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. **Buscar recursos**, busque **Intune**.
3. Seleccione **Cumplimiento del dispositivo**.
4. En la hoja **Cumplimiento del dispositivo**, seleccione **Directivas**.
5. Seleccione **Crear directiva**, después rellene los detalles como **Nombre** y **Descripción**. Pulse **iOS** como la **Plataforma**.
6. En **Configuración**, seleccione **Seguridad del sistema**, después cambie **Requerir una contraseña para desbloquear dispositivos móviles** por **Requerir**. También puede establecer otras reglas, como **Longitud mínima de contraseña**, **Tipo de contraseña requerida** y **Número de caracteres no alfanuméricos en la contraseña**. Cuando haya terminado de configurar su directiva, seleccione **Aceptar**.
7. Vuelva a la hoja **Crear directiva**, después seleccione **Crear**.
8. Una vez que se haya creado la directiva, seleccione **Asignaciones** para asignarla a su grupo de prueba. Seleccione su grupo de prueba, que debe tener su usuario de prueba incluido y, después, asigne la directiva a ese grupo haciendo clic en **Guardar**.
9. Espere unos minutos, después el dispositivo inscrito debe pedirle que necesita una contraseña actualizada para seguir siendo compatible con la directiva de empresa. También puede comprobar esto manualmente en la **aplicación de portal de empresa para iOS** pulsando en el nombre del dispositivo, después en el botón **Sincronizar**.

## <a name="next-steps"></a>Pasos siguientes

[Introducción a la inscripción de dispositivos](get-started-enroll.md): obtenga información sobre la inscripción mediante esta experiencia de inscripción completa para un dispositivo iOS.

## <a name="learn-more"></a>Obtener más información

* [Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)
* [Formas habituales de usar directivas de acceso condicional con Intune](conditional-access-intune-common-ways-use.md)
