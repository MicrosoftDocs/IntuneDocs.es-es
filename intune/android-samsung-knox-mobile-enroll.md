---
title: Inscripción automática de dispositivos Android mediante Knox Mobile Enrollment de Samsung
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Android mediante Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f7565972d37c5df5acb83012bb7cebbdc1fa1cec
ms.sourcegitcommit: 378474debffbc85010c54e20151d81b59b7a7828
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028654"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Inscripción automática de dispositivos Android mediante Knox Mobile Enrollment de Samsung

En este tema aprenderá a configurar Intune para inscribir dispositivos Android compatibles mediante Samsung Knox Mobile Enrollment (KME). Mediante el uso de Intune con Samsung KME, puede inscribir un gran número de dispositivos Android corporativos cuando los usuarios finales enciendan por primera vez sus dispositivos y se conecten a una red WiFi o de telefonía móvil. Además, es posible inscribir los dispositivos mediante Bluetooth o NFC con la aplicación de implementación Knox.

Para habilitar la inscripción de Intune mediante Samsung KME, use los portales de Intune y de Samsung Knox en este orden:

1. En el portal de Knox:
    1. [Cree un perfil de MDM](#create-mdm-profile)
    2. [Agregue los dispositivos](#add-devices)
    3. [Asigne un perfil de MDM a los dispositivos](#assign-an-mdm-profile-to-devices)
2. En el portal de Knox, [configure el inicio de sesión del usuario final](#configure-how-end-users-sign-in).
3. [Distribuya los dispositivos](#distribute-devices).


Una lista de identificadores de dispositivos (números de serie e IME) se agregan automáticamente al portal de Knox cuando se compran dispositivos de revendedores autorizados que participan en el programa de implementación de Knox.


## <a name="prerequisites"></a>Requisitos previos

Para inscribir un dispositivo en Intune mediante KME, primero debe registrar la empresa en el portal de Samsung Knox con estos pasos:
1.  [Asegúrese de que KME esté disponible en su región](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME está disponible en más de 55 países. Asegúrese de que se admita su país de implementación.

2.  [Dispositivos compatibles](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): KME está disponible en todos los dispositivos Samsung con una versión mínima de Knox 2.4.

3.  [Requisitos de red](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): asegúrese de que su red permite las reglas de acceso de red y firewall necesarias.

4.  [Regístrese para obtener una cuenta Samsung](https://www2.samsungknox.com/en/user/register): necesita una cuenta Samsung para registrarse y para habilitar KME y administrar todos los derechos de Knox Enterprise en un solo lugar.

5.  Revisión del registro: una vez que complete y envíe su perfil, Samsung revisará la solicitud y la aprobará de inmediato o la dejará con estado de revisión pendiente para un seguimiento posterior. Una vez que se aprueba la cuenta, puede seguir con los demás pasos.

## <a name="create-mdm-profile"></a>Creación de un perfil de MDM

Cuando la empresa esté registrada correctamente, puede crear su perfil de MDM para Microsoft Intune en el portal de Knox con la información que aparece a continuación. Para una guía detallada, consulte las instrucciones del [Asistente para crear perfiles de Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm).

| Campos del perfil de MDM| ¿Necesario? | Valores |
|-------------------|-----------|-------|
|MDM Server URI     | No        |Déjelo en blanco.
|Nombre del perfil       | Sí       |Escriba el nombre de perfil que prefiera.
|description        | No        |Escriba texto que describa el perfil.
|MDM Agent APK      | Sí       |https://aka.ms/intune_kme
|Skip Setup wizard  | No        |Elija esta opción para omitir las instrucciones de configuración de dispositivo estándar en nombre del usuario final.
|Allow End User to Cancel Enrollment | No | Elija esta opción para permitir que los usuarios cancelen KME.
|Custom JSON        | No        |Déjelo en blanco.
| EULAs, Terms of Service & User Agreements| No | Elija esta opción para mostrar los acuerdos relacionados con Knox para que el usuario los acepte.
Associate a Knox license with this profile | No | Deje esta opción no seleccionada. Inscribir un dispositivo en Intune mediante KME no requiere una licencia de Knox.

## <a name="add-devices"></a>Agregar dispositivos

Para asignar perfiles de MDM a los dispositivos, se deben agregar dispositivos compatibles de Samsung Knox al portal de Knox a través de uno de estos métodos:
- **Using Samsung-Approved Reseller(s)** (Uso de revendedores aprobados por Samsung): use este método si compra dispositivos de uno de los revendedores aprobados por Samsung. Los revendedores pueden cargar automáticamente los dispositivos cuando se aprueban. [Consulte la guía Samsung Knox Enrollment User Guide para saber cómo agregar revendedores](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Using the Knox Deployment App (KDA)** (Uso de la aplicación de implementación de Knox [KDA]): use este método si tiene dispositivos existentes que se deben inscribir mediante KME. Puede usar Bluetooth o NFC para agregar dispositivos al portal de Knox con este método. [Consulte la guía Samsung Knox Enrollment User Guide para saber cómo usar la KDA](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Asignación de un perfil de MDM a los dispositivos
Debe asignar un perfil de MDM a los dispositivos agregados en el portal de Knox antes de poder inscribirlos. [Consulte la guía Samsung Knox Enrollment User Guide para información sobre la configuración de dispositivos](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>Configure el inicio de sesión de los usuarios finales

En el caso de los dispositivos inscritos en Intune mediante KME, puede configurar cómo un usuario final inicia sesión de la siguiente manera:

- **Without user name association** (Sin asociación de nombre de usuario): en el portal de Knox, en **Device details** (Detalles del dispositivo), deje en blanco los campos **User ID** (Identificador del usuario) y **Password** (Contraseña) de los dispositivos agregados. Esto requiere que el usuario final escriba tanto su nombre de usuario como la contraseña cuando se inscriba en Intune.

- **With user name association** (Con asociación de nombre de usuario): en el portal de Knox, en **Device details** (Detalles del dispositivo), proporcione un **User ID** (Identificador del usuario), como un nombre de usuario para el usuario asignado o una cuenta [Administrador de inscripción de dispositivos](https://docs.microsoft.com/intune/device-enrollment-manager-enroll), para los dispositivos agregados. Esta acción rellena previamente el nombre de usuario y requiere que el usuario final escriba una contraseña cuando se inscriba en Intune.

> [!NOTE]
>
>Cuando se define una asociación de usuario, solo el usuario asociado puede inscribir el dispositivo mediante KME. Esto sucede incluso después de restablecer el dispositivo mediante un borrado. Cuando no se define ninguna asociación en el portal de Knox, cualquier usuario con una licencia de Intune válida puede inscribir el dispositivo mediante KME.
>

## <a name="distribute-devices"></a>Distribuir los dispositivos

Después de crear y asignar un perfil de MDM, asociar un nombre de usuario e identificar los dispositivos como corporativos en Intune, puede distribuir los dispositivos a los usuarios.

¿Sigue necesitando ayuda? Consulte la guía [Knox Mobile Enrollment User Guide](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm) completa.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
- **Cuenta de Google Play Account:** no se necesita una cuenta de Google Play para inscribir el dispositivo en Microsoft Intune, pero es probable que actualizaciones futuras de la aplicación Portal de empresa de Intune sí requieran una cuenta de Google Play en el dispositivo.

- **Modo Propietario de dispositivo de Google:** esta versión preliminar no permite la inscripción en el modo Propietario de dispositivo de Google mediante KME. Es un escenario que se está investigando.

- **No se considera el campo "Password" (Contraseña):** si el campo **Password** (Contraseña) se completa en **Device details** (Detalles del dispositivo) en el portal de Knox, la aplicación Portal de empresa de Intune no lo tomará en cuenta. El usuario final debe escribir una contraseña en el dispositivo para completar la inscripción del mismo.

- **Inscripción de Android Enterprise:** KME no admite la inscripción de Android Enterprise.

## <a name="getting-support"></a>Ayuda
Obtenga más información sobre cómo [recibir soporte técnico para Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


