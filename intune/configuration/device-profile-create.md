---
title: Creación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Agregue o configure un perfil de configuración de dispositivo en Microsoft Intune. Seleccione el tipo de plataforma, ajuste la configuración y agregue una etiqueta de ámbito.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02603651587837211d9a67d7e4bbeb90cb358dc5
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059573"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Creación de un perfil de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Los perfiles de dispositivo le permiten agregar y ajustar configuraciones y, luego, insertar esas configuraciones en dispositivos de su organización. El artículo [Aplicación de la configuración y características en dispositivos con perfiles de dispositivos Microsoft Intune](device-profiles.md) entra en más detalles, incluido lo que puede hacer el usuario.

En este artículo:

- Se enumeran los pasos para crear un perfil.
- Se muestra cómo agregar una etiqueta de ámbito para "filtrar" el perfil.
- Describe las reglas de aplicabilidad en dispositivos Windows 10 y muestra cómo crear una regla.
- Se enumeran los tiempos de ciclo de actualización de sincronización cuando los dispositivos reciben perfiles y cualquier actualización de perfil.

## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración**. Dispone de las siguientes opciones:

    - **Información general**: muestra el estado de los perfiles y proporciona detalles adicionales sobre los perfiles que ha asignado a usuarios y dispositivos.
    - **Administrar**: cree perfiles de dispositivo, cargue [scripts de PowerShell](../apps/intune-management-extension.md) personalizados para ejecutarlos en el perfil y agregue planes de datos a los dispositivos con [eSIM](esim-device-configuration.md).
    - **Supervisión**: compruebe si el estado de un perfil es correcto o erróneo, y consulte registros sobre los perfiles.
    - **Configuración**: agregue una entidad de certificación SCEP o PFX, o bien habilite la [Administración de gastos de telecomunicaciones](telecom-expenses-monitor.md) en el perfil.

3. Seleccione **Crear perfil**. Escriba las propiedades siguientes:

   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil sería **Perfil de correo electrónico de WP para toda la empresa**.
   - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
   - **Plataforma**: seleccione la plataforma de los dispositivos. Las opciones son:  

       - **Android**
       - **Android Enterprise**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 y versiones posteriores**
       - **Windows 10 y versiones posteriores**

   - **Tipo de perfil**: seleccione el tipo de opciones de configuración que quiere crear. La lista dependerá de la **plataforma** que elija.
   - **Configuración**: En los siguientes temas se describen los valores de cada tipo de perfil:

       - [Plantillas administrativas](administrative-templates-windows.md)
       - [Personalizado](../custom-settings-configure.md)
       - [Optimización de entrega](../delivery-optimization-windows.md)
       - [Características del dispositivo](../device-features-configure.md)
       - [Restricciones de dispositivos](device-restrictions-configure.md)
       - [Actualización de edición y conmutador de modo](edition-upgrade-configure-windows-10.md)
       - [Educación](education-settings-configure.md)
       - [Correo electrónico](email-settings-configure.md)
       - [Endpoint Protection](../protect/endpoint-protection-configure.md)
       - [Protección de identidad](../protect/identity-protection-configure.md)  
       - [Quiosco](kiosk-settings.md)
       - [Certificado PKCS](../protect/certficates-pfx-configure.md)
       - [Certificado PKCS importado](../protect/certificates-imported-pfx-configure.md)
       - [Certificado SCEP](../protect/certificates-scep-configure.md)
       - [Certificado de confianza](../protect/certificates-configure.md)
       - [Directivas de actualización](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [ATP de Microsoft Defender](../protect/advanced-threat-protection.md)
       - [Windows Information Protection](../protect/windows-information-protection-configure.md)

     Por ejemplo, si selecciona **iOS/iPadOS** como plataforma, las opciones de tipo de perfil serán similares al perfil siguiente:

     ![Creación de perfil de iOS en Intune](./media/device-profile-create/create-device-profile.png)

4. Cuando termine, seleccione **Aceptar** > **Crear** para guardar los cambios. El perfil se crea y se muestra en la lista.

## <a name="scope-tags"></a>Etiquetas de ámbito

Una vez que agrega la configuración, también puede agregar una etiqueta de ámbito al perfil. Las etiquetas de ámbito asignan y filtrar las directivas a grupos específicos, como Recursos Humanos o Todos los empleados de Carolina del Norte en EE. UU.

Para más información sobre las etiquetas de ámbito y lo que puede hacer el usuario, consulte el artículo sobre [el uso de RBAC y las etiquetas de ámbito para TI distribuida](../fundamentals/scope-tags.md).

### <a name="add-a-scope-tag"></a>Incorporación de una etiqueta de ámbito

1. Seleccione **Ámbito (etiquetas)** .
2. Seleccione **Agregar** para crear una etiqueta de ámbito. O seleccione una etiqueta de ámbito existente en la lista.
3. Haga clic en **Aceptar** para guardar los cambios.

## <a name="applicability-rules"></a>Reglas de aplicabilidad

Se aplica a:

- Windows 10 y versiones posteriores

Las reglas de aplicabilidad permiten a los administradores dirigirse a los dispositivos de un grupo que cumplen criterios específicos. Por ejemplo, se crea un perfil de restricciones de dispositivos que se aplica al grupo **Todos los dispositivos Windows 10**. Además, solo desea que el perfil esté asignado a los dispositivos que ejecutan Windows 10 Enterprise.

Para realizar esta tarea, cree una **regla de aplicabilidad**. Estas reglas son útiles para los escenarios siguientes:

- Utiliza Windows 10 Education (EDU). En Bellow College, desea dirigirse a todos los dispositivos Windows 10 EDU entre RS3 y RS4.
- Quiere dirigirse a todos los usuarios de recursos humanos en Contoso, pero solo desea dispositivos Windows 10 Professional o Enterprise.

Para abordar estos escenarios, puede:

- Crear un grupo de dispositivos que incluya todos los dispositivos de Bellows College. En el perfil, agregue una regla de aplicabilidad para que se aplique si la versión mínima del sistema operativo es `16299` y la versión máxima es `17134`. Asigne este perfil al grupo de dispositivos de Bellows College.

  Cuando se asigna, el perfil se aplica a los dispositivos entre las versiones mínima y máxima que especifique. En el caso de los dispositivos que no están entre las versiones mínima y máxima que especifique, su estado se muestra como **No aplicable**.

- Crear un grupo de usuarios que incluya a todos los usuarios de recursos humanos (RR  HH.) en Contoso. En el perfil, agregue una regla de aplicabilidad para que se aplique a los dispositivos que ejecutan Windows 10 Professional o Enterprise. Asigne este perfil al grupo usuarios de Recursos Humanos.

  Cuando se asigna, el perfil se aplica a los dispositivos que ejecutan Windows 10 Professional o Enterprise. En el caso de los dispositivos que no ejecutan estas ediciones, su estado se muestra como **No aplicable**.

- Si hay dos perfiles con la misma configuración exacta, se aplica el perfil sin una regla de aplicabilidad. 

  Por ejemplo, el perfil A tiene como destino el grupo de dispositivos de Windows 10, habilita BitLocker y no tiene una regla de aplicabilidad. El perfil B tiene como destino el mismo grupo de dispositivos de Windows 10, habilita BitLocker y tiene una regla de aplicabilidad para aplicar solo el perfil a Windows 10 Enterprise.

  Cuando se asignan ambos perfiles, se aplica el perfil A porque no tiene una regla de aplicabilidad. 

Al asignar el perfil a los grupos, las reglas de aplicabilidad actúan como un filtro y solo se dirigen a los dispositivos que cumplen los criterios.

### <a name="add-a-rule"></a>Agregar una regla

1. Seleccione **Reglas de aplicabilidad**. Puede elegir los valores de **Regla**, **Propiedad** y **Edición del sistema operativo**:

    ![Agregue una regla de aplicabilidad a un perfil de configuración de dispositivo en Microsoft Intune.](./media/device-profile-create/applicability-rules.png)

2. En **Regla**, elija si desea incluir o excluir usuarios o grupos. Las opciones son:

    - **Asignar perfil si**: incluye usuarios o grupos que cumplen los criterios especificados.
    - **No asignar perfil si**: excluye los usuarios o grupos que cumplen los criterios especificados.

3. En **Propiedad**, elija el filtro. Las opciones son: 

    - **Edición del SO**: en la lista, compruebe las ediciones de Windows 10 que quiere incluir (o excluir) en la regla.
    - **Versión del SO**: escriba los números de versión **min** y **max** de Windows 10 que quiere incluir (o excluir) en la regla. Ambos valores son necesarios.

      Por ejemplo, puede especificar `10.0.16299.0` (RS3 o 1709) para la versión mínima y `10.0.17134.0` (RS4 o 1803) para la versión máxima. O bien, puede ser más específico e indicar `10.0.16299.001` para la versión mínima y `10.0.17134.319` para la versión máxima.

4. Haga clic en **Agregar** para guardar los cambios.

## <a name="refresh-cycle-times"></a>Tiempos de ciclo de actualización

Intune usa diferentes ciclos de actualización para comprobar si hay actualizaciones para los perfiles de configuración. Si el dispositivo se inscribió recientemente, la inserción en el repositorio se ejecuta con más frecuencia. En el artículo sobre [ciclos de actualización de directivas y perfiles](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) se muestran los tiempos de actualización estimados.

En cualquier momento, los usuarios pueden abrir la aplicación Portal de empresa de Intune y sincronizar el dispositivo para comprobar de inmediato las actualizaciones del perfil.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](../device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
