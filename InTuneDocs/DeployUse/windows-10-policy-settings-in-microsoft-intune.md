---
title: "Configuración de directivas de Windows 10 | Microsoft Intune"
description: "Use la configuración de directiva indicada en este tema para configurar las opciones integradas y personalizadas de los dispositivos Windows 10 Escritorio y Windows 10 Mobile inscritos."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 10/03/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b8522406a3c73746b09616c3ec917464cf751312
ms.openlocfilehash: 6e482beb5e2edce648ecb6f1821baa6214fa0f2f


---

# Configuración de directivas de Intune para dispositivos Windows 10 en Microsoft Intune

Este tema contiene información que le ayudará a entender la configuración de directivas de Intune que puede usar para administrar dispositivos Windows 10. Lea este tema, además de los procedimientos de [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) para configurar opciones integradas y personalizadas para el escritorio de Windows 10 inscrito y los dispositivos Windows 10 Mobile. No puede usar estas directivas con equipos que ejecutan el [software cliente de PC de Intune](/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune).

Puede elegir entre dos tipos de directivas:

- **Directiva personalizada**: use la **directiva personalizada** de Microsoft Intune para Windows 10 y Windows 10 Mobile para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que se puede usar para controlar las características en los dispositivos. Windows 10 ofrece muchas opciones de configuración mediante el [proveedor de servicios de configuración de directivas](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Directiva de configuración general**: use este tipo de directiva si quiere seleccionar una configuración de la lista integrada que se proporciona con Microsoft Intune.

## Configuración de directivas personalizadas

Proporcione las siguientes opciones en una directiva personalizada:

## &nbsp;&nbsp;&nbsp;General

Escriba un nombre y, si lo desea, una descripción para esta directiva que le ayude a identificarla en la consola de Intune.

## &nbsp;&nbsp;&nbsp;Configuración de OMA-URI

Para cada configuración de OMA-URI que quiera agregar, escriba la siguiente información. Use la [referencia de configuración de URI de Windows 10](/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) de este tema para obtener información sobre la configuración que puede usar: 

- **Nombre de la configuración**: escriba un nombre único para la configuración de OMA-URI que le ayude a identificarla en la lista de valores de configuración.
- **Descripción de la configuración**: si lo desea, escriba una descripción para la configuración.
- **Tipo de datos**: elija una de estas opciones:
    - **String**
    - **Cadena (XML)**
    - **Fecha y hora**
    - **Integer**
    - **Punto flotante**
    - **Boolean**
- **OMA-URI (distingue mayúsculas de minúsculas)**: especifique el OMA-URI para el que quiere proporcionar un valor de configuración.
- **Valor**: especifique el valor que quiere asociar al OMA-URI especificado.

### Ejemplo
En la siguiente captura de pantalla, se ha habilitado el valor **Connectivity/AllowVPNOverCellular**. De esta forma, un dispositivo Windows 10 puede abrir una conexión VPN cuando se encuentra en una red de telefonía móvil.

> ![Ejemplo de una directiva personalizada que contiene opciones de VPN](./media/custom-policy-example.png)

## - Configuración de URI de Windows 10
Use esta sección para obtener información sobre la configuración de OMA-URI que puede configurar con una **directiva personalizada de Windows 10**.

## &nbsp;&nbsp;&nbsp;Directiva

|Nombre y URI de la directiva|Detalles|
|---------------|------------|-----------|
|**Permitir la actualización automática**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Solo escritorio<br>**Tipo de datos:** entero<br />**Valores:** **0** - **5** (valor predeterminado: **1**)|
|**Programa el día de la instalación**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Solo Mobile<br>**Tipo de datos:** entero<br />**Values:**<br>**0**: todos los días (valor predeterminado)<br>**1**: domingo<br>**2**: lunes<br>**3**: martes<br>**4**: miércoles<br>**5**: jueves<br>**6**: viernes<br>**7**: sábado|
|**Programar la hora de la instalación**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: **23** horas (**0** es medianoche) (valor predeterminado: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|Solo Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: el usuario no puede establecer el temporizador de período de gracia de la contraseña y el valor se establece como "siempre"<br>**1**: el usuario puede establecer el temporizador de período de gracia de la contraseña (valor predeterminado)|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|Solo Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: no se permite **usar la conexión Wi-Fi**.<br>**1**: **se permite usar la conexión Wi-Fi** (valor predeterminado)|
|**Wi-Fi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|Escritorio y Mobile<br>**Tipo de datos:** entero<br />**Valores:** **0**: No permitir el uso compartido de Internet; **1**: Permitir compartir Internet (valor predeterminado)|
|**Wi-Fi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Wi-Fi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|Solo Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: no se permite la conexión Wi-Fi fuera de la MDM aprovisionada.<br>**1**: se permite agregar nuevos SSID de red más allá de los de la MDM aprovisionada (valor predeterminado).|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|Escritorio y Mobile<br>**Tipo de datos:** entero<br />**Values:**<br>**0** : no permitido (valor de Enterprise solo)<br>**1** : limitado<br>**2**: completo (valor predeterminado)<br>**3**: completo e información de diagnóstico|
|**Sistema/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0** : no permitido<br>**1**: solo configuración (valor predeterminado)<br>**2**: configuración y experimentación|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|Solo Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: no permitir el modo antirrobo<br>**1**: preferencia del usuario (valor predeterminado)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: no se permite la VPN a través de la red de telefonía móvil<br>**1**: la VPN puede usar cualquier conexión, incluida la de la red de telefonía móvil (valor predeterminado)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: no se permite al usuario activar el Bluetooth.<br>**1**: reservado. El usuario puede activar y configurar el Bluetooth (no admitido en Windows Phone 8.1 para MDM, EAS, Windows 10 Escritorio o Windows 10 Mobile)<br>**2**: permitido El usuario puede activar y configurar el Bluetooth (valor predeterminado)|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: No permitir itinerancia; **1**: Permitir itinerancia (valor predeterminado)|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0** (valor predeterminado), **1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**, **1** (valor predeterminado)|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0** (valor predeterminado), **1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0** (valor predeterminado), **1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0** (valor predeterminado), **1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**, **1** (valor predeterminado)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0** (valor predeterminado), **1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0** (valor predeterminado), **1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0** : no permitir<br>El diccionario extendido abierto está desactivado.<br>Un usuario no puede:<br>- Agregar un nuevo diccionario extendido abierto<br />- Agregar un nuevo archivo de configuración de integración de búsqueda<br>- Usar la característica de candidato en la nube<br>- Enviar la palabra registrada del usuario.<br>**1**: permitir<br>El diccionario extendido abierto se puede agregar y usar de forma predeterminada. La función de integración de búsqueda también se puede usar de forma predeterminada.<br>Un usuario puede:<br>Usar la característica de candidato en la nube.|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: el registro de conversión incorrecta está desactivado.<br>**1**: el registro de conversión incorrecta está activado (valor predeterminado).|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: no se filtra ningún carácter (valor predeterminado).<br>**1**: se filtra todo excepto los caracteres Shift JIS.|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br />**0**: no se filtra ningún carácter (valor predeterminado).<br>**1**: se filtra todo excepto los caracteres JIS0208.|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: no se filtra ningún carácter (valor predeterminado).<br>**1**: se filtra todo excepto los caracteres JIS0208 o EUDC.|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|Solo Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0** : filtrado estricto más alto del contenido para adultos<br>**1**: filtrado moderado del contenido para adultos (no se filtrarán los resultados de búsqueda válidos, valor predeterminado)|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Forzar tamaño inicial**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|Solo Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: permitir al usuario cambiar el tamaño (valor predeterminado)<br>**1**: forzar la pantalla no completa<br>**2**: forzar la pantalla completa|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: no aplazar la actualización (permanecer en la rama actual, CB, valor predeterminado)<br>**1**: habilitar que las actualizaciones se aplacen (el dispositivo sigue la rama actual para negocios, CBB y reglas)<br />Si desea obtener información detallada, consulte:<br>[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|Escritorio y Mobile<br>**Descripción:** directiva para aplazar actualizaciones de software durante un máximo de 4 semanas<br />**Tipo de datos:** entero<br />**Values:**<br> **0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br>**1**-**4**: número de semanas durante las que aplazar las actualizaciones de software.<br />Si desea obtener información detallada, consulte:<br>[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|Escritorio y Mobile<br>**Descripción:** directiva para aplazar actualizaciones de funciones durante un máximo de 8 meses<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br>**1**-**8**: número de meses durante los que aplazar actualizaciones de características.<br />Si desea obtener información detallada, consulte:<br>[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|Escritorio y Mobile<br>**Descripción:** permite que un dispositivo deje de recibir actualizaciones durante 5 semanas.<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br>**1**: pausar las actualizaciones (expira transcurridas 5 semanas)|

## &nbsp;&nbsp;&nbsp;Windows Defender

|Nombre y URI de la directiva|Detalles|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: supervisar todos los archivos (valor predeterminado)<br>**1** : supervisar los archivos entrantes<br>**2** : supervisar los archivos salientes|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0** - **90**: representa la cantidad de tiempo que se conservará el malware.<br>**Valor predeterminado:** **0**: se guarda en la carpeta de cuarentena para siempre y no se quita automáticamente|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**1**: examen rápido (valor predeterminado)<br>**2**: examen completo|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0** -todos los días (valor predeterminado)<br>**1**: lunes<br>**2**: martes<br>**3**: miércoles<br>**4**: jueves<br>**5**: viernes<br>**6**: sábado<br>**7**: domingo<br>**8** : ningún examen programado|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: 12:00<br>**60** : 1:00<br>**120**: 2:00 (valor predeterminado)<br>**180** : 3:00<br>**240** : 4:00<br>**300** : 5:00<br>**360** : 6:00<br>**420** : 7:00<br>**480** : 8:00<br>**540** : 9:00<br>**600** : 10:00<br>**660** : 11:00<br>**720** : 12:00<br>**780** : 13:00<br>**840** : 14:00<br>**900** : 15:00<br>**960** : 16:00<br>**1020** : 17:00<br>**1080** : 18:00<br>**1140** : 19:00<br>**1200** : 20:00<br>**1260** : 21:00<br>**1320** : 22:00<br>**1381** : ventana de mantenimiento|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|Solo escritorio<br>**Tipo de datos:** entero<br />**Values:**<br>**0**: 12:00<br>**60** : 1:00<br>**120**: 2:00 (valor predeterminado)<br>**180** : 3:00<br>**240** : 4:00<br>**300** : 5:00<br>**360** : 6:00<br>**420** : 7:00<br>**480** : 8:00<br>**540** : 9:00<br>**600** : 10:00<br>**660** : 11:00<br>**720** : 12:00<br>**780** : 13:00<br>**840** : 14:00<br>**900** : 15:00<br>**960** : 16:00<br>**1020** : 17:00<br>**1080** : 18:00<br>**1140** : 19:00<br>**1200** : 20:00<br>**1260** : 21:00<br>**1320** : 22:00<br>**1380** : 23:00|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0** - **100** (valor predeterminado: **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|Solo escritorio<br />**Tipo de datos:** entero<br>**Valores:** **0**: no permitido (valor predeterminado); **1**: permitido|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido (valor predeterminado); **1**: permitido|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado). También se ejecuta cuando RTP está activado y se establece como permitido|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: no comprobar las firmas en un intervalo<br>**1**: comprobar las firmas cada hora<br>**2**: comprobar las firmas cada 2 horas, etc.<br>**24**: comprobar las firmas cada día<br>**Valor predeterminado:** 8: comprobar las firmas cada 8 horas|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: preguntar siempre (valor predeterminado)<br>**1** : enviar muestras seguras automáticamente<br>**2** : no enviar nunca<br>**3** : enviar todas las muestras automáticamente|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|Solo escritorio<br />**Tipo de datos:** cadena<br />**Values:**<br>*&lt;lista de extensiones separadas por punto y coma&gt;* p. ej. **obj;lib**<br>**Valor predeterminado**: no se excluye ninguna extensión|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|Solo escritorio<br />**Tipo de datos:** cadena<br />**Values:**<br />*&lt;lista de rutas de acceso separadas por punto y coma&gt;*<br />Ejemplo: **c:\test;c:\test1.exe**<br />**Valor predeterminado:** no se excluye ninguna ruta de acceso|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|Solo escritorio<br />**Tipo de datos:** cadena<br />**Values:**<br>*&lt;lista de rutas de acceso separadas por punto y coma&gt;*<br>Ejemplo: **c:\test.exe;c:\test1.exe**<br>**Valor predeterminado:** no se excluye ningún proceso|

## &nbsp;&nbsp;&nbsp;Explorador Edge

|Nombre y URI de la directiva|Detalles|
|---------------|------------|-----------|
|**Permitir explorador**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: exploración desactivada; **1**: exploración activada (valor predeterminado)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no mostrar sugerencias; **1**: mostrar sugerencias (valor predeterminado)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Solo escritorio<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: deshabilitado (abrir sitios de intranet en el explorador Edge, valor predeterminado).<br>**1**: habilitado (abrir sitios de intranet en Internet Explorer).|
|**Permitir No realizar seguimiento**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: deshabilitado (DNT no enviado; valor predeterminado); **1**: habilitado (enviar DNT)|
|**Configurar SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitir; **1**: permitir (valor predeterminado)|
|**Permitir elementos emergentes**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: bloquear elementos emergentes (valor predeterminado); **1**: permitir elementos emergentes|
|**Permitir cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: permitir cookies de todos los sitios web (valor predeterminado)<br>**1**: bloquear solo cookies de terceros<br>**2**: bloquear todas las cookies|
|**Permitir guardar contraseña**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Values:**<br>**0**: el administrador de contraseñas está deshabilitado <br>**1**: el administrador de contraseñas está habilitado (valor predeterminado)|
|**Permitir autorrellenar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: deshabilitado (valor predeterminado); **1**: habilitado|
|**Configurar la lista de sitios de empresa**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Solo escritorio<br />**Tipo de datos:** cadena<br />**Valores:<br>**0**: no configurado; <br>**1**: usar la lista de sitios del modo de empresa de IE si está configurado (valor predeterminado); <br>**2**: especificar la ubicación de la lista de sitios de empresa|

## Configuración general de directivas

Use la **directiva de configuración general** de Microsoft Intune para Windows 10 para configurar las opciones integradas de los dispositivos Windows 10 Escritorio y Windows 10 Mobile inscritos. 

## &nbsp;&nbsp;&nbsp;Contraseña

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Requerir contraseña para desbloquear dispositivos**|-|
|**Tipo de contraseña obligatoria**|Especifica si la contraseña debe ser solo numérica o alfanumérica|
|**Tipo de contraseña requerida** - **Número mínimo de conjuntos de caracteres**|Hay cuatro conjuntos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. Esta configuración especifica cuántos de estos conjuntos deben incluirse en la contraseña.|
|**Longitud mínima de la contraseña**|Solo se aplica a Windows 10 Mobile|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Para los dispositivos que ejecutan Windows 10: si el dispositivo tiene habilitado BitLocker, se pondrá en el modo de recuperación de BitLocker si el inicio de sesión falla el número de veces especificado. Si el dispositivo no tiene habilitado BitLocker, no se aplicará esta configuración.<br>Para los dispositivos que ejecutan Windows 10 Mobile: si el inicio de sesión falla el número de veces especificado, el dispositivo se borrará.|
|**Minutos de inactividad antes de que se apague la pantalla**|Especifica el tiempo durante el que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.|
|**Caducidad de contraseña (días)**|Especifica el período de tiempo tras el que debe cambiarse la contraseña del dispositivo.|
|**Recordar el historial de contraseñas**|Especifica si quiere impedir que el usuario final cree contraseñas usadas anteriormente.|
|**Recordar historial de contraseñas** - **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas que el dispositivo recuerda.|
|**Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**|Si está habilitado, el usuario debe escribir una contraseña para desbloquear el dispositivo. (Windows 10 Mobile solo)|

## &nbsp;&nbsp;&nbsp;Cifrado

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Requerir cifrado en dispositivo móvil**|Habilita el cifrado en dispositivos de destino<br>(Windows 10 Mobile solo)|

## &nbsp;&nbsp;&nbsp;System (Sistema)

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Permitir captura de pantalla**|Permite al usuario capturar la pantalla del dispositivo como una imagen. (Windows 10 Mobile solo)|
|**Permitir cancelar suscripción manualmente**|Permite al usuario eliminar manualmente la cuenta del área de trabajo desde el dispositivo.|
|**Permitir la instalación de certificado raíz manualmente**|Se aplica a Windows 10 Mobile|
|**Permitir que datos de diagnóstico y uso se envíen a Microsoft**|Los valores posibles son:<br><br>**No**: no se envían datos a Microsoft.<br>**Básico**: se envía información limitada a Microsoft<br>**Mejorado**: se envían datos de diagnóstico mejorados a Microsoft<br>**Completo (recomendado)**: envía los mismos datos que **Mejorado**, además de datos adicionales sobre el estado del dispositivo.|


## &nbsp;&nbsp;&nbsp;Cuenta y sincronización

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|---------------------|
|**Permitir cuenta de Microsoft**|Permite al usuario asociar una cuenta de Microsoft con el dispositivo.|
|**Permitir añadir cuentas que no son de Microsoft de forma manual**|Permite al usuario agregar al dispositivo cuentas de correo electrónico que no estén asociadas a una cuenta de Microsoft.|
|**Permitir la sincronización de la configuración de las cuentas de Microsoft**|Permite que la configuración de dispositivo y aplicación asociada a una cuenta de Microsoft se sincronice entre los dispositivos.|

## &nbsp;&nbsp;&nbsp;Microsoft Edge

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Permitir explorador web**|Permite el uso del explorador web de Edge en el dispositivo.<br>(Windows 10 Mobile solo)|
|**Permitir sugerencias de búsqueda en la barra de direcciones**|Permite que el motor de búsqueda sugiera sitios a medida que se escriben las frases de búsqueda.|
|**Permitir enviar tráfico de intranet a Internet Explorer**|Permite a los usuarios abrir sitios web de intranet en Internet Explorer.<br>(Windows 10 Escritorio solo)|
|**Permitir no rastrear**|Configura el explorador Edge para que envíe encabezados Do Not Track a los sitios web que visitan los usuarios.|
|**Habilitar SmartScreen**|-|
|**Permitir Active scripting**|Permite que se ejecuten en el explorador Edge scripts como JavaScript.|
|**Permitir elementos emergentes**|Solo se aplica a Windows 10 Escritorio|
|**Permitir cookies**|-|
|**Permitir autorrellenar**|Permite a los usuarios cambiar la configuración de Autocompletar en el explorador.<br>(Windows 10 Escritorio solo)|
|**Permitir administrador de contraseñas**|Habilita o deshabilita la característica Administrador de contraseñas de Edge.|
|**Ubicación de la lista de sitios de Modo de empresa**|Especifica dónde se encuentra la lista de sitios web que se abrirá en modo de empresa. Los usuarios no pueden editar esta lista.<br>(Windows 10 Escritorio solo)|

## &nbsp;&nbsp;&nbsp;Aplicaciones

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|---------------------|
|**Permitir almacén de aplicaciones**|Solo se aplica a Windows 10 Mobile|



## &nbsp;&nbsp;&nbsp;Móvil

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|---------------------|
|**Permitir itinerancia de datos**|Permite movilidad entre redes al obtener acceso a datos.|
|**Permitir VPN sobre móvil**|Controla si el dispositivo puede tener acceso a las conexiones VPN cuando se conecta a una red móvil.|
|**Permitir itinerancia de VPN sobre móvil**|Controla si el dispositivo puede tener acceso a las conexiones VPN cuando hay itinerancia a una red móvil.|

## &nbsp;&nbsp;&nbsp;Hardware

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Permitir cámara**|-|
|**Permitir almacenamiento extraíble**|Especifica si se pueden usar dispositivos de almacenamiento externo, como una tarjeta SD, con el dispositivo.|
|**Permitir Wi-Fi**|Solo se aplica a Windows 10 Mobile|
|**Permitir compartir Internet**|Permite el uso compartido de una conexión de Internet en el dispositivo.|
|**Permitir la configuración Wi-Fi manual**|Controla si el usuario puede configurar sus propias conexiones Wi-Fi o si solo puede usar conexiones configuradas mediante un perfil Wi-Fi.<br>(Windows 10 Mobile solo)|
|**Permitir la conexión automática a zonas Wi-Fi gratuitas**|Permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente los términos y condiciones para la conexión.|
|**Permitir geolocalización**|Especifica si el dispositivo puede usar información de servicios de ubicación.|
|**Permitir NFC**|Permite que el dispositivo use las funcionalidades de transmisión de datos en proximidad.|
|**Permitir Bluetooth**|-|
|**Permitir modo visible de Bluetooth **|Permite que otros dispositivos habilitados para Bluetooth detecten este dispositivo.|
|**Permitir anuncios de Bluetooth**|Permite que los dispositivos reciban anuncios a través de Bluetooth.|
|**Permitir restablecer teléfono**|Controla si el usuario puede restablecer su dispositivo a la configuración de fábrica.|
|**Permitir conexión USB**|Controla si los dispositivos pueden tener acceso a dispositivos de almacenamiento externo a través de una conexión USB.|
|**Permitir modo antirrobo**|Permite habilitar el modo antirrobo de Windows.|

## &nbsp;&nbsp;&nbsp;Funciones

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|---------------------|
|**Permitir copiar y pegar**|Solo se aplica a Windows 10 Mobile|
|**Permitir grabación de voz**|Solo se aplica a Windows 10 Mobile|
|**Permitir a Cortana**|Habilita o deshabilita el asistente de voz de Cortana.|
|**Permitir notificaciones del centro de actividades**|Habilita o deshabilita notificaciones del centro de actividades en la pantalla de bloqueo del dispositivo.<br>(Windows 10 Mobile solo)|

## &nbsp;&nbsp;&nbsp;Windows Defender

Todos los valores son solo válidos para Windows 10 Escritorio.

|Nombre de la configuración|Información adicional (si es necesario)|
|-|-|
|**Permitir supervisión en tiempo real**|Habilita el análisis en tiempo real de malware, spyware y otro software no deseado.|
|**Permitir supervisión del comportamiento**|Permite a Defender comprobar determinados patrones conocidos de actividad sospechosa en los dispositivos.|
|**Habilitar Sistema de inspección de red**|El Sistema de inspección de red (NIS) ayuda a proteger los dispositivos contra ataques basados en red mediante el uso de firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para detectar y bloquear el tráfico malintencionado.|
|**Analizar todas las descargas**|Controla si Defender analiza todos los archivos descargados de Internet.|
|**Permitir análisis de scripts**|Permite que Defender examine scripts que se usan en Internet Explorer.|
|**Supervisar actividad de archivos y programas**|Habilite esta opción para permitir que Defender supervise la actividad de archivos y programas en los dispositivos.|
|**Días que hay que hacer seguimiento de malware resuelto**|Permite que Defender continúe realizando el seguimiento de malware resuelto durante el número de días especificado para que pueda comprobar de forma manual los dispositivos previamente afectados. Si establece el número de días en **0**, el malware permanece en la carpeta de cuarentena y no se quita automáticamente. |
|**Permitir acceso a la interfaz de usuario de cliente**|Controla si la interfaz de usuario de Windows Defender se oculta a los usuarios finales.<br>Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario final.|
|**Programar un examen rápido diario**|Permite programar un examen rápido que se lleva a cabo diariamente a la hora que seleccione.|
|**Programar un examen del sistema**|Permite programar un examen completo o rápido del sistema que se lleva a cabo periódicamente en el día y la hora seleccionados.|
|**Limitar el uso de la CPU durante un análisis a**|Permite limitar la cantidad de CPU que pueden usar los exámenes (de **1** a **100**)|
|**Examinar archivos de almacenamiento**|Permite que Defender examine archivos almacenados, como archivos Zip o Cab.|
|**Analizar mensajes de correo electrónico**|Permite que Defender analice los mensajes de correo electrónico cuando llegan al dispositivo.|
|**Analizar unidades extraíbles**|Permite que Defender analice unidades extraíbles, como sticks USB.|
|**Examinar unidades de red asignadas**|Permite que Defender examine archivos en unidades de red asignadas.<br>Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.|
|**Examinar archivos abiertos desde carpetas compartidas de red**|Permite que Defender examine archivos en unidades de red compartidas (por ejemplo, aquellas a las que se tiene acceso desde una ruta de acceso UNC).<br>Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.|
|**Intervalo de actualización de firma**|Especifica el intervalo en el que Defender buscará nuevos archivos de firma.|
|**Permitir la protección en la nube**|Permite o bloquea la recepción por parte de Microsoft Active Protection Service de información sobre la actividad de malware de los dispositivos que administra. Esta información se usa para mejorar el servicio en el futuro.|
|**Pedir a los usuarios el envío de muestras**|Controla si los archivos que podrían requerir un análisis posterior por parte de Microsoft para determinar si son malintencionados se envían automáticamente a Microsoft.|
|**Detección de aplicaciones potencialmente no deseadas**|Esta configuración se puede usar para proteger los dispositivos de escritorio de Windows inscritos frente a la ejecución de software que Windows Defender ha clasificado como potencialmente no deseado. Puede protegerse contra la ejecución de estas aplicaciones o puede usar el modo auditoría para informar cuando se instale una aplicación potencialmente no deseada.|
|**Archivos y carpetas que se van a excluir al ejecutar un análisis o al usar la protección en tiempo real**|Agrega uno o varios archivos y carpetas como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluirán en los análisis en tiempo real ni programados.|
|**Extensiones de archivo que se deben excluir al ejecutar un análisis o al utilizar protección en tiempo real**|Agrega una o varias extensiones de archivo como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluirán en los análisis en tiempo real ni programados.|
|**Procesos que se deben excluir al ejecutar un análisis o al utilizar protección en tiempo real**|Agrega uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluirán en los análisis en tiempo real ni programados.| 


## &nbsp;&nbsp;&nbsp;Updates

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|---------------|
|**Permitir actualizaciones automáticas**|Habilite esta configuración para permitir las actualizaciones automáticas. Luego, configure una de las opciones siguientes para controlar el comportamiento de las actualizaciones:<br />**Notificar descarga**<br />**Instalar automáticamente en tiempo de mantenimiento**<br />**Instalar y reiniciar automáticamente en tiempo de mantenimiento**<br />**Instalar y reiniciar automáticamente a la hora programada** **Nota:** cuando esta opción está seleccionada, también puede configurar los valores siguientes: **Eliminar la notificación para el usuario final** y **Definir el día de instalación para las actualizaciones programadas**.<br>(Windows 10 Escritorio solo)|
|**Permitir características de evaluación**|Permite a Microsoft implementar características y configuraciones de la versión preliminar en dispositivos Windows 10. Puede seleccionar permitir que se instale únicamente la configuración o todas las configuraciones y características de la versión preliminar.|

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)





<!--HONumber=Oct16_HO1-->


