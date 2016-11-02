---
title: "Opciones de configuración de directivas de cumplimiento para dispositivos Android | Microsoft Intune"
description: "En este tema se describe la configuración de directivas de cumplimiento normativo para dispositivos Android."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e24de6814d9e01c64768f425e961a7822f4b27a1
ms.openlocfilehash: 5f02618da6fb3c538ad131fe8abaf35a6be6e177


---


# Opciones de configuración de directivas de cumplimiento para dispositivos Android en Microsoft Intune

Las opciones de configuración de directiva descritas en este tema son válidas para dispositivos que ejecutan Android 4.0 y versiones posteriores o Samsung KNOX 4.0 y versiones posteriores.

Si quiere información sobre otras plataformas, seleccione uno de los siguientes temas:
> [!div class="op_single_selector"]
- [Configuración de directivas de cumplimiento normativo para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Configuración de directivas de cumplimiento normativo para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Configuración de seguridad del sistema
### Contraseña
- **Requerir una contraseña para desbloquear dispositivos móviles**: establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos.

-  **Longitud mínima de la contraseña**: especifique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.

- **Calidad de contraseña**: esta opción detecta si los requisitos de contraseña que especifique se configuran en el dispositivo. Habilite esta opción para requerir a los usuarios que cumplan determinados requisitos de contraseña para dispositivos Android. Elija de entre las siguientes opciones:

  -   **Biométrico de seguridad baja**
  -   **Requerido**
  -   **Al menos numérica**
  -   **Al menos alfabética**
  -   **Al menos alfanumérica**
  -   **Alfanumérica con símbolos**

- **Minutos de inactividad antes de que sea necesaria la contraseña**: especifique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.

- **Caducidad de contraseña (días)**: seleccione el número de días que faltan para que la contraseña caduque y durante los cuales deben crear una nueva.

- **Recordar historial de contraseñas**: use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se han usado anteriormente.

- **Impedir la reutilización de contraseñas anteriores**: si ha seleccionado **Recordar historial de contraseñas**, especifique el número de contraseñas que se han usado previamente que no se pueden volver a usar.

- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**: use este valor junto con el de la opción **Minutos de inactividad antes de que sea necesaria la contraseña**. Se pedirá al usuario que escriba una contraseña para obtener acceso a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción **Minutos de inactividad antes de que sea necesaria la contraseña**.

### Cifrado
- **Requerir cifrado en el dispositivo móvil**: establezca esta opción en **Sí** para requerir que los dispositivos estén cifrados para poder conectarse a los recursos. Los dispositivos se cifran al elegir la opción **Requerir una contraseña para desbloquear dispositivos móviles**.

## Configuración de estado y la seguridad de dispositivos

- **El dispositivo no debe estar descodificado o descifrado**: si habilita esta opción, los dispositivos descodificados se considerarán como no compatibles.
- **Requerir que los dispositivos impidan la instalación de aplicaciones desde orígenes desconocidos (Android 4.0 o posterior)**: para bloquear los dispositivos que tienen **Seguridad** > **Orígenes desconocidos** habilitado en el dispositivo, habilite esta configuración y establézcala en **Sí**.  
>[!IMPORTANT]
>Las aplicaciones de instalación de prueba requieren que se habilite **Orígenes desconocidos**. Aplique esta directiva de cumplimiento solo si no tiene aplicaciones Android de instalación de prueba en dispositivos.

- **Requerir que se deshabilite la depuración USB (Android 4.2 o posterior)**: esta opción especifica si está habilitada la opción para detectar la opción de depuración USB en el dispositivo.
- **Requerir que los dispositivos habiliten el dispositivo de análisis de amenazas de seguridad (Android 4.4 4.2)**: Esta opción especifica que la característica **Comprobar aplicaciones** está habilitada en el dispositivo.
- **Nivel de revisión de seguridad mínimos de Android (Android 6.0 o posterior)**: Utilice esta opción para especificar el nivel de revisión mínima de Android. No serán compatibles los dispositivos que no están al menos en este nivel de revisión. La fecha debe especificarse en el formato: AAAA-MM-DD.
- **Requerir la habilitación de la protección frente a amenazas de dispositivo**: utilice esta opción para hacer que la evaluación del riesgo de la solución Lookout MTP sea una condición para el cumplimiento. Elija el nivel de amenaza máximo permitido, que es uno de los siguientes:

  - **Ninguno (protegido)**: es la más segura. Esto significa que el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio**: el dispositivo se evalúa como conforme si las amenazas presentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto**: esta opción es la menos segura. Básicamente, esto permite todos los niveles de amenaza. Quizás es útil si está usando esta solución solo con fines informativos.

  Para ver más detalles, consulte [Habilitar la regla de protección contra amenazas móviles en la directiva de cumplimiento normativo](enable-device-threat-protection-rule-in-compliance-policy.md).

## Configuración de propiedades de dispositivo
- **SO mínimo requerido**: cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no conforme.
  Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.

- **Versión de SO máxima permitida**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambien las reglas para permitir la versión de SO, este dispositivo no podrá usarse para tener acceso a los recursos de la empresa.



<!--HONumber=Oct16_HO3-->


