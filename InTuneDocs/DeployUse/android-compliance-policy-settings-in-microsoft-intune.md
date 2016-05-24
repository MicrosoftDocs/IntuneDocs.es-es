---
# required metadata

title: Opciones de configuración de directivas de cumplimiento para dispositivos Android | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Opciones de configuración de directivas de cumplimiento para dispositivos Android en Microsoft Intune

Las opciones de configuración de directiva descritas en este tema son válidas para dispositivos que ejecutan Android 4.0 y versiones posteriores o Samsung KNOX 4.0 y versiones posteriores.

Si quiere información sobre otras plataformas, seleccione uno de los siguientes temas:
> [!div class="op_single_selector"]
- [Configuración de directivas de cumplimiento normativo para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Configuración de directivas de cumplimiento normativo para dispositivos Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Configuración de seguridad del sistema
### Contraseña
- **Requerir una contraseña para desbloquear dispositivos móviles:** establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña para
  tener acceso a sus dispositivos.

-  **Longitud mínima de la contraseña:** especifique el número mínimo de dígitos o caracteres que debe contener la contraseña del usuario.

- **Calidad de contraseña:** habilite esta opción para configurar requisitos de contraseña para dispositivos Android. Elija de entre las siguientes opciones:
  -   **Biométrico de seguridad baja**
  - **Requerido**
  -   **Al menos numérica**
  -   **Al menos alfabética**
  -   **Al menos alfanumérica**
  -   **Alfanumérica con símbolos**

- **Minutos de inactividad antes de que se requiera la contraseña:** especifica el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.

- **Expiración de la contraseña (días):** seleccione el número de días que deben transcurrir para que la contraseña expire
  y se deba crear otra.

- **Recordar historial de contraseñas:** use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para evitar que el usuario
  cree contraseñas usadas anteriormente.

- **Impedir la reutilización de contraseñas anteriores:** si se ha seleccionado **Recordar historial de contraseñas**, especifique el
  número de contraseñas usadas previamente que no se pueden volver a usar.

- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad:**
  Esta valor debe usarse junto con el de la opción **Minutos de inactividad antes de que se requiera la contraseña**. Se pedirá a los usuarios que escriban una contraseña para tener acceso a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción
  **Minutos de inactividad antes de que se requiera la contraseña**.

### Cifrado
- **Requerir cifrado en el dispositivo móvil:** establezca esta opción en **Sí** para requerir que los dispositivos
  estén cifrados para poder conectarse a los recursos. Los dispositivos
  se cifran al configurar la opción **Requerir una contraseña para
  desbloquear dispositivos móviles**..

## Configuración de estado del dispositivo

- **El dispositivo no debe estar descodificado o descifrado:** si habilita esta opción,
  los dispositivos descodificados se considerarán como no compatibles.

## Configuración de propiedades de dispositivo
- **Minimum OS required** (Versión mínima de sistema operativo): cuando un dispositivo no cumple el requisito de versión mínima
  del sistema operativo, se notifica como no conforme.
  Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.

- **Maximum OS version allowed** (Versión máxima de sistema operativo permitida): cuando un dispositivo usa una
  versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.


<!--HONumber=May16_HO1-->


