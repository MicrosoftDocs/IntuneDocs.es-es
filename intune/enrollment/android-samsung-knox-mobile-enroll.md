---
title: Inscripción automática de dispositivos Android mediante Knox Mobile Enrollment de Samsung
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Android mediante Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f290370dd6ec05677a7073d9ca3edd854c9aa5e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505571"
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


Una lista de identificadores de dispositivos (números de serie e IME) se agrega automáticamente al portal de Knox cuando se compran dispositivos de revendedores autorizados que participan en el programa de implementación de Knox.


## <a name="prerequisites"></a>Requisitos previos

Para inscribir un dispositivo en Intune mediante KME, primero debe registrar la empresa en el portal de Samsung Knox con estos pasos:
1. [Asegúrese de que KME está disponible en su país o región](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME está disponible en más de 55 países o regiones. Asegúrese de que se admita su país o región de implementación.

2. [Dispositivos compatibles](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): KME está disponible en todos los dispositivos que tengan como mínimo Samsung Knox versión 2.4 para la inscripción de Android y como mínimo Knox versión 2.8 para la inscripción de Android Enterprise.

3. [Requisitos de red](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): asegúrese de que su red permite las reglas de acceso de red y firewall necesarias.

4. [Registrarse para obtener una cuenta Samsung](https://www2.samsungknox.com/en/user/register): necesita una cuenta Samsung para registrarse y para habilitar KME y administrar todos los derechos de Knox Enterprise en un solo lugar.

5. Revisión del registro: una vez que complete y envíe su perfil, Samsung revisará la solicitud y la aprobará de inmediato o la dejará con estado de revisión pendiente para un seguimiento posterior. Una vez que se aprueba la cuenta, puede seguir con los demás pasos.

## <a name="create-mdm-profile"></a>Creación de un perfil de MDM

Cuando la empresa esté registrada correctamente, puede crear su perfil de MDM para Microsoft Intune en el portal de Knox con la información que aparece debajo. Puede crear perfiles de MDM para Android y Android Enterprise en el portal de Knox. 

### <a name="for-android-enterprise"></a>Para Android Enterprise

| Campos del perfil de MDM| ¿Necesario? | Valores | 
|-------------------|-----------|-------| 
|MDM Server URI     | No        |Déjelo en blanco. 
|Nombre del perfil       | Sí       |Escriba el nombre de perfil que prefiera. 
|Descripción        | No        |Escriba texto que describa el perfil. 
|MDM Agent APK      | Sí       |https://aka.ms/intune_kme_deviceowner 
|Habilitar esta aplicación como un propietario del dispositivo de Google | Sí | Elija esta opción para inscribirse en Android Enterprise. 
|MDM admitido      | Sí       |Microsoft Intune 
|Deje todas las aplicaciones de sistema habilitadas | No | Elija esta opción para asegurarse de que todas las aplicaciones están habilitadas y disponibles para el perfil. Si no se selecciona esta opción, solo se mostrará un conjunto limitado de aplicaciones del sistema en la bandeja de aplicaciones del dispositivo. Algunas aplicaciones, como la aplicación Correo electrónico, permanecen ocultas. 
|Custom JSON        | No        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "Enter Intune enrollment token string"}. Obtenga más información sobre cómo [crear un perfil de inscripción](android-kiosk-enroll.md). 
| Agregar contratos legales | No | Déjelo en blanco. 

### <a name="for-android"></a>Para Android

Para una guía detallada, consulte las instrucciones del [Asistente para crear perfiles de Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm).

| Campos del perfil de MDM| ¿Necesario? | Valores |
|-------------------|-----------|-------|
|MDM Server URI     | No        |Déjelo en blanco.
|Nombre del perfil       | Sí       |Escriba el nombre de perfil que prefiera.
|description        | No        |Escriba texto que describa el perfil.
|MDM Agent APK      | Sí       |https://aka.ms/intune_kme
|Habilitar esta aplicación como un propietario del dispositivo de Google | No | Deje esta opción no seleccionada para Android. Esta opción solo se aplica a Android Enterprise.
|Skip Setup wizard  | No        |Elija esta opción para omitir las instrucciones de configuración de dispositivo estándar para el usuario final.
|Allow End User to Cancel Enrollment | No | Elija esta opción para permitir que los usuarios cancelen KME.
|Custom JSON        | No        |Déjelo en blanco.
| Agregar contratos legales | No | Déjelo en blanco.
Associate a Knox license with this profile | No | Deje esta opción no seleccionada. Inscribir un dispositivo en Intune mediante KME no requiere una licencia de Knox.

## <a name="add-devices"></a>Agregar dispositivos

Para asignar perfiles de MDM a los dispositivos, se deben agregar dispositivos compatibles de Samsung Knox al portal de Knox a través de uno de estos métodos:
- **Uso de revendedores aprobados por Samsung:** use este método si compra dispositivos de uno de los revendedores aprobados por Samsung. Los revendedores pueden cargar automáticamente los dispositivos cuando se aprueban. [Consulte la guía Samsung Knox Enrollment User Guide para saber cómo agregar revendedores](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Uso de la aplicación de implementación de Knox (KDA):** use este método si tiene dispositivos existentes que se deben inscribir mediante KME. Puede usar Bluetooth o NFC para agregar dispositivos al portal de Knox con este método. [Consulte la guía Samsung Knox Enrollment User Guide para saber cómo usar la KDA](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Asignación de un perfil de MDM a los dispositivos
Debe asignar un perfil de MDM a los dispositivos agregados en el portal de Knox antes de poder inscribirlos. [Consulte la guía Samsung Knox Enrollment User Guide para información sobre la configuración de dispositivos](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>Configure el inicio de sesión de los usuarios finales

En el caso de los dispositivos inscritos en Intune mediante KME para Android, puede configurar cómo un usuario final inicia sesión de la siguiente manera:

- **Sin asociación de nombre de usuario:** en el portal de Knox, en **Detalles del dispositivo**, deje en blanco los campos **Identificador del usuario** y **Contraseña** de los dispositivos agregados. Esta opción requiere que el usuario final escriba tanto su nombre de usuario como la contraseña cuando se inscriba en Intune.

- **Con asociación de nombre de usuario:** en el portal de Knox, en **Detalles del dispositivo**, proporcione un **Identificador de usuario**, como un nombre de usuario para el usuario asignado o una cuenta [Administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md), para los dispositivos agregados. Esta opción rellena previamente el nombre de usuario y requiere que el usuario final escriba una contraseña cuando se inscriba en Intune.

> [!NOTE]
>
>La asociación de usuarios solo se aplica a la inscripción de administradores de dispositivos Android. Cuando se define una asociación de usuario, solo el usuario asociado puede inscribir el dispositivo mediante KME. Esto sucede incluso después de restablecer el dispositivo a los valores de fábrica. Cuando no se define ninguna asociación en el portal de Knox, cualquier usuario con una licencia de Intune válida puede inscribir el dispositivo mediante KME.
>En el caso de los dispositivos Android Enterprise totalmente administrados, incluso si se define la asociación de usuarios, no se pasará al dispositivo ni conectará el dispositivo al usuario.
>

## <a name="distribute-devices"></a>Distribuir los dispositivos

Después de crear y asignar un perfil de MDM, asociar un nombre de usuario e identificar los dispositivos como corporativos en Intune, puede distribuir los dispositivos a los usuarios.

¿Sigue necesitando ayuda? Consulte la [guía de usuario de KME](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm) completa.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

- **Compatibilidad con el propietario del dispositivo:**  - **Compatibilidad con el propietario del dispositivo:** Intune admite la inscripción de dispositivos dedicados y totalmente administrados mediante el portal de KME. Se admitirán otros modos de propietario de dispositivo de Android Enterprise en cuanto estén disponibles en Intune.

- **Sin compatibilidad con el perfil de trabajo:** KME es un método de inscripción de dispositivos corporativo y los dispositivos inscritos en el perfil de trabajo de Android garantizan que los datos profesionales y personales estén separados en los dispositivos personales. Así pues, la inscripción de dispositivos en un perfil de trabajo mediante KME no es un escenario admitido en Intune.

- **Restablecimiento de fábrica para inscribirse en Android Enterprise:** si se reasignan dispositivos que ya se han configurado, es necesario restablecer los dispositivos a la configuración de fábrica al realizar la inscripción en Android Enterprise.

- **Actualizaciones mediante la cuenta de Google Play:** no se necesita una cuenta de Google Play para inscribir el dispositivo en Microsoft Intune. Sin embargo, para las inscripciones de administrador de dispositivos Android, es probable que actualizaciones futuras de la aplicación Portal de empresa de Intune sí requieran una cuenta de Google Play en el dispositivo. No se necesita una cuenta de Google Play al realizar la inscripción en Propietario de dispositivo de Google.

- **El campo "Contraseña" se omite:** si el campo **Contraseña** se completa en **Detalles del dispositivo** en el portal de Knox, la aplicación Portal de empresa de Intune no lo tomará en cuenta durante la inscripción de Android. El usuario final debe escribir una contraseña en el dispositivo para completar la inscripción del mismo.


## <a name="getting-support"></a>Ayuda
Obtenga más información sobre cómo [recibir soporte técnico para Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


