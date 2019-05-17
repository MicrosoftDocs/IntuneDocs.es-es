---
title: Creación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Agregue o configure un perfil de configuración de dispositivo en Microsoft Intune. Seleccione el tipo de plataforma, ajuste la configuración y agregue una etiqueta de ámbito.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570408"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Creación de un perfil de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Los perfiles de dispositivo le permiten agregar y ajustar configuraciones y, luego, insertar esas configuraciones en dispositivos de su organización. El artículo [Aplicación de la configuración y características en dispositivos con perfiles de dispositivos Microsoft Intune](device-profiles.md) entra en más detalles, incluido lo que puede hacer el usuario.

En este artículo:

- Se enumeran los pasos para crear un perfil.
- Se muestra cómo agregar una etiqueta de ámbito para "filtrar" el perfil.
- Se enumeran los tiempos de ciclo de actualización de sincronización cuando los dispositivos reciben perfiles y cualquier actualización de perfil.

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Intune**.

2. Seleccione **Configuración del dispositivo**. Dispone de las siguientes opciones:

    - **Información general**: muestra el estado de los perfiles y proporciona detalles adicionales sobre los perfiles que ha asignado a usuarios y dispositivos.
    - **Administrar**: cree perfiles de dispositivo, cargue [scripts de PowerShell](intune-management-extension.md) personalizados para ejecutarlos en el perfil y agregue planes de datos a los dispositivos con [eSIM](esim-device-configuration.md).
    - **Supervisión**: compruebe si el estado de un perfil es correcto o erróneo, y consulte registros sobre los perfiles.
    - **Configuración**: agregue una entidad de certificación SCEP o PFX, o bien habilite la [Administración de gastos de telecomunicaciones](telecom-expenses-monitor.md) en el perfil.

3. Seleccione **Perfiles** > **Crear perfil**. Escriba las propiedades siguientes:

   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil sería **Perfil de correo electrónico de WP para toda la empresa**.
   - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
   - **Plataforma**: seleccione la plataforma de los dispositivos. Las opciones son:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 y versiones posteriores**
       - **Windows 10 y versiones posteriores**

   - **Tipo de perfil**: seleccione el tipo de opciones de configuración que quiere crear. La lista dependerá de la **plataforma** que elija.
   - **Configuración**: En los siguientes temas se describen los valores de cada tipo de perfil:

       - [Plantillas administrativas](administrative-templates-windows.md)
       - [Personalizado](custom-settings-configure.md)
       - [Optimización de entrega](delivery-optimization-windows.md)
       - [Características del dispositivo](device-features-configure.md)
       - [Restricciones de dispositivos](device-restrictions-configure.md)
       - [Actualización de edición y conmutador de modo](edition-upgrade-configure-windows-10.md)
       - [Educación](education-settings-configure.md)
       - [Correo electrónico](email-settings-configure.md)
       - [Endpoint Protection](endpoint-protection-configure.md)
       - [Protección de identidad](identity-protection-configure.md)  
       - [Quiosco](kiosk-settings.md)
       - [Certificado PKCS](certficates-pfx-configure.md)
       - [Certificado SCEP](certificates-scep-configure.md)
       - [Certificado de confianza](certificates-configure.md)
       - [Directivas de actualización](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [ATP de Windows Defender](advanced-threat-protection.md)
       - [Windows Information Protection](windows-information-protection-configure.md)

     Por ejemplo, si selecciona **iOS** como plataforma, las opciones de tipo de perfil serán similares al perfil siguiente:

     ![Creación de perfil de iOS en Intune](./media/create-device-profile.png)

4. Cuando termine, seleccione **Aceptar** > **Crear** para guardar los cambios. El perfil se crea y se muestra en la lista.

## <a name="scope-tags"></a>Etiquetas de ámbito

Una vez que agrega la configuración, también puede agregar una etiqueta de ámbito al perfil. Las etiquetas de ámbito asignan y filtrar las directivas a grupos específicos, como Recursos Humanos o Todos los empleados de Carolina del Norte en EE. UU.

Para más información sobre las etiquetas de ámbito y lo que puede hacer el usuario, consulte el artículo sobre [el uso de RBAC y las etiquetas de ámbito para TI distribuida](scope-tags.md).

### <a name="add-a-scope-tag"></a>Incorporación de una etiqueta de ámbito

1. Seleccione **Ámbito (etiquetas)**.
2. Seleccione **Agregar** para crear una etiqueta de ámbito. O seleccione una etiqueta de ámbito existente en la lista.
3. Haga clic en **Aceptar** para guardar los cambios.

## <a name="refresh-cycle-times"></a>Tiempos de ciclo de actualización

Intune usa los ciclos de actualización siguientes para comprobar si hay actualizaciones para los perfiles de configuración:

| Plataforma | Ciclo de actualización|
| --- | --- |
| iOS | Cada 6 horas |
| macOS | Cada 6 horas |
| Android | Cada 8 horas |
| Equipos Windows 10 inscritos como dispositivos | Cada 8 horas |
| Windows Phone | Cada 8 horas |
| Windows 8.1 | Cada 8 horas |

Si el dispositivo se inscribió recientemente, la sincronización se ejecuta con más frecuencia:

| Plataforma | Frecuencia |
| --- | --- |
| iOS | Cada 15 minutos durante 6 horas y, después, cada 6 horas |  
| macOS | Cada 15 minutos durante 6 horas y, después, cada 6 horas | 
| Android | Cada 3 minutos durante 15 minutos y, después, cada 15 minutos durante 2 horas y, después cada 8 horas | 
| Equipos Windows 10 inscritos como dispositivos | Cada 3 minutos durante 30 minutos y, después, cada 8 horas | 
| Windows Phone | Cada 5 minutos durante 15 minutos y, después, cada 15 minutos durante 2 horas y, después cada 8 horas | 
| Windows 8.1 | Cada 5 minutos durante 15 minutos y, después, cada 15 minutos durante 2 horas y, después cada 8 horas | 

En cualquier momento, los usuarios pueden abrir la aplicación Portal de empresa de Intune y sincronizar el dispositivo para comprobar de inmediato las actualizaciones del perfil.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
