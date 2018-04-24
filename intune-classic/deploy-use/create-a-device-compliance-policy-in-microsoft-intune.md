---
title: Crear una directiva de cumplimiento de dispositivos
description: Cree una directiva de cumplimiento normativo para ayudar a proteger los dispositivos móviles y equipos utilizados para acceder a los datos de su compañía.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/12/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ed6f66747364debd89661d78bcf3b002b1c8a9b6
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-device-compliance-policy-in-microsoft-intune"></a>Crear una directiva de cumplimiento normativo de dispositivos en Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

En este tema se explica cómo crear una directiva de cumplimiento normativo que un dispositivo debe seguir para que se considere compatible.

##  <a name="step-1-add-a-new-policy"></a>Paso 1: Agregar una nueva directiva
  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Directiva** &gt; **Políticas de cumplimiento** &gt; **Agregar**.

  ![Captura de pantalla de la página de directiva de cumplimiento normativo en la consola de administración de Intune, donde se muestra la opción Agregar en el menú situado en la parte superior de la página](./media/intune-sa-3a-add-compliance-policy.png)

##  <a name="step-2--configure-settings"></a>Paso 2: Configurar las opciones
En la página **Crear directiva**, habilite las opciones que considere necesarias:
  -   Opciones de seguridad del sistema, como la contraseña y el cifrado.
  -   Opciones de mantenimiento del dispositivo, por ejemplo, si el dispositivo está descodificado o no, o si el servicio de atestación de estado de dispositivo de Windows indica que es correcto.
  -   Opciones de propiedades del dispositivo, como la versión de sistema operativo mínima necesaria o la versión de sistema operativo máxima permitida.
![Pestaña General de la página Crear directiva](./media/intune-sa-3b-create-policy.png)


##  <a name="step-3-save-the-policy"></a>Paso 3: Guardar la directiva
Cuando termine, seleccione **Guardar directiva**.

Se le ofrecerá la posibilidad de implementar la directiva directamente después de guardarla, o bien puede optar por implementarla más adelante. La nueva directiva se muestra en el nodo **Directivas de cumplimiento** del área de trabajo **Directiva**.

##  <a name="step-4-set-the-compliance-status-validity-period"></a>Paso 4: Establecer el período de validez del estado de cumplimiento normativo
Para especificar el tiempo del que dispone el dispositivo para protegerse antes de que se considere no conforme, vaya a la configuración de la directiva de cumplimiento y actualice el tiempo. El valor predeterminado está establecido en 30 días.

![Opción de configuración de directiva de cumplimiento en la barra de menús de la directiva](../media/mdm-compliance-policy-settings.png)

![Cuadro de diálogo de la directiva de cumplimiento](../media/mdm-ca-compliance-status-validity-period.png)

## <a name="supported-policy-settings"></a>Opciones de configuración de directiva compatibles
En la siguiente tabla se muestran las opciones de configuración de directiva de cumplimiento normativo y las plataformas en las que se admiten.

-------------

|Setting|iOS|Android|Windows|
|-----|----|-----|-----|
|Requerir una contraseña para desbloquear dispositivos móviles|iOS 6 y versiones posteriores|Android 4.0 y versiones posteriores <br>Samsung KNOX Standard 4.0 y posterior|Windows Phone 8.1 y versiones posteriores|
|Permitir contraseñas sencillas|iOS 6 y versiones posteriores|No compatible|Windows Phone 8.1 y versiones posteriores|
|Longitud mínima de la contraseña|iOS 6 y versiones posteriores| Android 4.0 y versiones posteriores<br>Samsung KNOX Standard 4.0 y posterior| Windows Phone 8.1 y versiones posteriores<br>Windows 8.1|
|Tipo de contraseña obligatoria|iOS 6 y versiones posteriores|No disponible|Windows Phone 8.1 y versiones posteriores <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Número mínimo de conjuntos de caracteres|iOS 6 y versiones posteriores|No disponible|Windows Phone 8.1 y versiones posteriores <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Calidad de contraseña|No disponible|Android 4.0 y versiones posteriores <br>Samsung KNOX Standard 4.0 y posterior|No disponible|
|Minutos de inactividad antes de que se pida la contraseña|iOS 6 y versiones posteriores|Android 4.0 y versiones posteriores<br>Samsung KNOX Standard 4.0 y posterior|Windows Phone 8.1 y versiones posteriores<br>Windows RT y Windows RT 8.1<br>Windows 8.1|
|Expiración de contraseña (días)|iOS 6 y versiones posteriores|Android 4.0 y versiones posteriores<br>Samsung KNOX Standard 4.0 y posterior|Windows Phone 8.1 y versiones posteriores<br>Windows RT y Windows RT 8.1<br>Windows 8.1|
|Recordar el historial de contraseñas|iOS 6 y versiones posteriores|Android 4.0 y versiones posteriores<br>Samsung KNOX Standard 4.0 y posterior|Windows Phone 8.1 y versiones posteriores<br>Windows RT y Windows RT 8.1<br>Windows 8.1|
|Impedir la reutilización de contraseñas anteriores|iOS 6 y versiones posteriores|Android 4.0 y versiones posteriores<br>Samsung KNOX Standard 4.0 y posterior|Windows Phone 8.1 y versiones posteriores<br>Windows RT y Windows RT 8.1<br>Windows 8.1|
|Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad| No disponible| No disponible|Windows 10 Mobile|
|Requerir cifrado en dispositivo móvil|No disponible|Android 4.0 y versiones posteriores<br>Samsung KNOX Standard 4.0 y posterior|Windows Phone 8.1 y versiones posteriores<br> Windows 8.1|
|Requerir que se informe del mantenimiento correcto de los dispositivos| No disponible| No disponible|Windows <br>Windows 10 Mobile|
|El dispositivo no debe estar descodificado o descifrado|iOS 6 y versiones posteriores|Android 4.0 y versiones posteriores<br>Samsung KNOX Standard 4.0 y posterior|No disponible|
|La cuenta de correo electrónico debe administrarse mediante Intune|iOS 6 y versiones posteriores|No disponible| No disponible|
|Seleccione el perfil de correo electrónico que debe administrarse mediante Intune|iOS 6 y versiones posteriores|No disponible| No disponible|
|SO mínimo requerido|iOS 6 y versiones posteriores|Android 4.0 y versiones posteriores<br>Samsung KNOX Standard 4.0 y posterior| Windows Phone 8.1 y versiones posteriores<br>Windows 8.1|
|Versión de SO máxima permitida|iOS 6 y versiones posteriores|Android 4.0 y versiones posteriores<br>Samsung KNOX Standard 4.0 y posterior|Windows Phone 8.1 y versiones posteriores<br>Windows 8.1|

Seleccione una de las siguientes opciones para obtener más información sobre la configuración de cumplimiento normativo que se admite en cada plataforma:
> [!div class="op_single_selector"]
> - [Configuración de directivas de cumplimiento normativo para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
> - [Configuración de directivas de cumplimiento para dispositivos Android](android-compliance-policy-settings-in-microsoft-intune.md)
> - [Configuración de directivas de cumplimiento para dispositivos Windows y Windows Phone](windows-compliance-policy-settings-in-microsoft-intune.md)


## <a name="next-steps"></a>Pasos siguientes
[Implementar y supervisar una directiva de cumplimiento](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>Vea también
[Introducción a las directivas de cumplimiento de dispositivos](introduction-to-device-compliance-policies-in-microsoft-intune.md)
