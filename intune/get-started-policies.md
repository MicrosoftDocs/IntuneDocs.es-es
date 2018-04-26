---
title: Introducción a las directivas en Microsoft Intune
titlesuffix: ''
description: Cree directivas para ayudar a proteger los datos corporativos y administrar los dispositivos que utilizan los usuarios finales para acceder a recursos de la empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b8bffd0435988cc59c5c0e4d754b861729d466ae
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-with-creating-policies"></a>Introducción a la creación de directivas

Uno de los objetivos principales de la introducción a Intune es la inscripción de dispositivos para garantizar que cumplen las directivas de la empresa. Las directivas de cumplimiento no solo le ayudan a administrar tipos de dispositivo especializados, como los quioscos propiedad de la empresa, sino también dispositivos sin usuario, tabletas y dispositivos personales (Bring Your Own).

![Panel de cumplimiento con pocos datos](/intune/media/generic-compliance-dashboard.png)

Administre dispositivos móviles en las siguientes áreas mediante directivas de cumplimiento:

* Regular el número de dispositivos que cada usuario inscribe
* Administrar la configuración del dispositivo (por ejemplo, el cifrado de nivel de dispositivo, la longitud de la contraseña o el uso de la cámara)
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

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Seleccione **Cumplimiento del dispositivo**.
4. En el panel **Cumplimiento del dispositivo**, seleccione **Directivas**.
5. Seleccione **Crear directiva**, después rellene los detalles como **Nombre** y **Descripción**. 
6. Pulse **iOS** como la **Plataforma**.
6. En **Configuración**, seleccione **Seguridad del sistema**, después cambie **Requerir una contraseña para desbloquear dispositivos móviles** por **Requerir**. También puede establecer otras reglas, como **Longitud mínima de contraseña**, **Tipo de contraseña requerida** y **Número de caracteres no alfanuméricos en la contraseña**. Cuando haya terminado de configurar su directiva, seleccione **Aceptar**.
7. Vuelva al panel **Crear directiva** y, después, seleccione **Crear**.
8. Una vez que se haya creado la directiva, seleccione **Asignaciones** para asignarla a su grupo de prueba. Seleccione su grupo de prueba, que debe tener su usuario de prueba incluido y, después, asigne la directiva a ese grupo haciendo clic en **Guardar**.
9. Espere unos minutos, después el dispositivo inscrito debe pedirle que necesita una contraseña actualizada para seguir siendo compatible con la directiva de empresa. También puede comprobar esto manualmente en la **aplicación de portal de empresa para iOS** pulsando en el nombre del dispositivo, después en el botón **Sincronizar**.

## <a name="next-steps"></a>Pasos siguientes

[Introducción a la inscripción de dispositivos](get-started-enroll.md): obtenga información sobre la inscripción mediante esta experiencia de inscripción completa para un dispositivo iOS.

## <a name="learn-more"></a>Obtener más información

* [Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)
* [Formas habituales de usar directivas de acceso condicional con Intune](conditional-access-intune-common-ways-use.md)
