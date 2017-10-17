---
title: "Configuración de directivas de cumplimiento para Android"
description: "En este tema se describe la configuración de directivas de cumplimiento normativo para dispositivos Android."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f781c5498a569a067f0f2aa6f780a6cc37c9985c
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="compliance-policy-settings-for-android-devices-in-microsoft-intune"></a>Opciones de configuración de directivas de cumplimiento para dispositivos Android en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Las opciones de configuración de directiva descritas en este tema son válidas para dispositivos que ejecutan Android 4.0 y versiones posteriores o Samsung KNOX 4.0 y versiones posteriores.

Si quiere información sobre otras plataformas, seleccione uno de los siguientes temas:
> [!div class="op_single_selector"]
- [Configuración de directivas de cumplimiento normativo para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Configuración de directivas de cumplimiento para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)
- [Configuración de directivas de cumplimiento para dispositivos Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Configuración de seguridad del sistema
### <a name="password"></a>Contraseña
- **Requerir una contraseña para desbloquear dispositivos móviles**: establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos.

-  **Longitud mínima de la contraseña**: especifique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.

- **Calidad de contraseña**: esta opción detecta si los requisitos de contraseña que especifique se configuran en el dispositivo. Habilite esta opción para requerir a los usuarios que cumplan determinados requisitos de contraseña para dispositivos Android. Elija de entre las siguientes opciones:

  -   **Biométrico de seguridad baja**
  -   **Requerido**
  -   **Al menos numérica**
  -   **Al menos alfabética**
  -   **Al menos alfanumérica**
  -   **Alfanumérica con símbolos**

- **Minutos de inactividad antes de que sea necesaria la contraseña:** especifique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.

- **Caducidad de contraseña (días)**: seleccione el número de días que faltan para que la contraseña caduque y durante los cuales deben crear una nueva.

- **Recordar historial de contraseñas**: use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se han usado anteriormente.

- **Impedir la reutilización de contraseñas anteriores:** especifique el número de contraseñas usadas previamente que no se pueden volver a usar (si la opción **Recordar historial de contraseñas** está seleccionada).

- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**: úselo junto con el de la opción **Minutos de inactividad antes de que sea necesaria la contraseña**. Se les pedirá a los usuarios que escriban una contraseña para obtener acceso a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción **Minutos de inactividad antes de que sea necesaria la contraseña**.

### <a name="encryption"></a>Cifrado
- **Requerir cifrado en el dispositivo móvil**: establezca esta opción en **Sí** para requerir que los dispositivos estén cifrados para poder conectarse a los recursos. Los dispositivos se cifran al configurar la opción de **Requerir una contraseña para desbloquear dispositivos móviles**.

## <a name="device-health-and-security-settings"></a>Configuración de estado y la seguridad de dispositivos

- **El dispositivo no debe estar descodificado o descifrado**: si habilita esta opción, los dispositivos descodificados se consideran como no compatibles.
- **Requerir que los dispositivos impidan la instalación de aplicaciones desde orígenes desconocidos (Android 4.0 o posterior)**: para bloquear los dispositivos que tienen **Seguridad > Orígenes desconocidos** habilitado en el dispositivo, habilite esta configuración y establézcala en **Sí**.  

>[!IMPORTANT]
>Las aplicaciones de instalación de prueba requieren que se habilite **Orígenes desconocidos**. Aplique esta directiva de cumplimiento solo si no tiene aplicaciones Android de instalación de prueba en dispositivos.

- **Requerir que se deshabilite la depuración USB (Android 4.2 o posterior)**: especifique si está habilitada la opción para detectar la opción de depuración USB en el dispositivo.
- **Requerir que los dispositivos habiliten el dispositivo de análisis de amenazas de seguridad (Android 4.4 4.2)**: especifique que la característica **Comprobar aplicaciones** está habilitada en el dispositivo.
- **Nivel de revisión de seguridad mínimos de Android (Android 6.0 o posterior)**: especifique el nivel de revisión mínima de Android.  No serán compatibles los dispositivos que no están al menos en este nivel de revisión. La fecha debe especificarse en el formato: AAAA-MM-DD.
- **Requerir la habilitación de la protección frente a amenazas de dispositivo**: utilice esta opción para hacer que la evaluación del riesgo de la solución Lookout MTP sea una condición para el cumplimiento. Seleccione el nivel de amenaza máximo permitido, que es uno de los siguientes:

  - **Ninguno (protegido)** es la más segura. Esto significa que el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier amenaza en el dispositivo, se evalúa como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor superior coloca al dispositivo en un estado de no conformidad.
  - **Medio**: el dispositivo se evalúa como conforme si las amenazas presentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto:** esta opción es la menos segura. Básicamente, permite todos los niveles de amenaza, que quizás solo sea útil si usa esta solución únicamente para fines informativos.

  Para obtener más detalles, consulte [Creación de la directiva de cumplimiento de dispositivos de Lookout](create-lookout-device-compliance-policy.md).

## <a name="device-property-settings"></a>Configuración de propiedades de dispositivo

- **SO mínimo requerido**: cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no conforme.
  Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.

- **Versión de SO máxima permitida**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras que cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.
