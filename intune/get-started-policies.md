---
title: "Introducción a las directivas"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 232ec25c34df5e71f70737ca5f0f8a2ef12a05f0
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="getting-started-with-policies"></a>Introducción a las directivas

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
