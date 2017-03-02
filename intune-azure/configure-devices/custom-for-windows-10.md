---
title: "Configuración personalizada de Intune para dispositivos Windows 10 | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: conozca la configuración que puede usar en un perfil personalizado de Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: bc740d9e43e2937757075bf84735fe611433f6f0
ms.lasthandoff: 02/16/2017


---

# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Configuración personalizada de dispositivos para dispositivos Windows 10 en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

 Use el perfil **personalizado** de Microsoft Intune para Windows 10 y Windows 10 Mobile para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que se puede usar para controlar las características en los dispositivos. Windows 10 ofrece muchas opciones de configuración mediante el [proveedor de servicios de configuración de directivas](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](how-to-configure-custom-settings.md) para comenzar.
2. En la hoja **Create Profile** (Crear perfil), elija **Configuración** para agregar uno o varios valores de configuración de OMA-URI.
3. En la hoja **Configuración OMA-URI personalizada**, haga clic en **Agregar** para agregar un nuevo valor. También puede hacer clic en **Exportar** para crear una lista de todos los valores configurados en un archivo de valores separados por comas (.csv).
4. Para cada configuración de OMA-URI que quiera agregar, escriba la siguiente información. Use la lista de este tema para aprender sobre la configuración que puede usar:
    - **Nombre de la configuración**: escriba un nombre único para la configuración de OMA-URI que le ayude a identificarla en la lista de valores de configuración.
    - **Descripción de la configuración**: si lo desea, escriba una descripción para la configuración.
    - **Tipo de datos**: elija una de estas opciones:
        - **Cadena**
        - **Cadena (XML)**
        - **Fecha y hora**
        - **Entero**
        - **Punto flotante**
        - **Booleano**
    - **OMA-URI (distingue mayúsculas de minúsculas)**: especifique el OMA-URI para el que quiere proporcionar un valor de configuración.
    - **Valor**: especifique el valor que quiere asociar al OMA-URI especificado.
5. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.
El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="example"></a>Ejemplo
En la siguiente captura de pantalla, se ha habilitado el valor **Connectivity/AllowVPNOverCellular**. De esta forma, un dispositivo Windows 10 puede abrir una conexión VPN cuando se encuentra en una red de telefonía móvil.

> ![Ejemplo de una directiva personalizada que contiene opciones de VPN](./media/custom-policy-example.png)


## <a name="policy-settings"></a>Configuraciones de directiva

|Nombre y URI de la directiva|Detalles|
|---------------|------------|-----------|
|**Permitir las actualizaciones automáticas**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Solo escritorio<br>**Tipo de datos:** entero<br />**Valores:** **0** - **5** (valor predeterminado: **1**)|
|**Programar el día de la instalación**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Solo Mobile<br>**Tipo de datos:** entero<br />**Valores**<br>**0**: todos los días (valor predeterminado)<br>**1**: domingo<br>**2**: lunes<br>**3**: martes<br>**4**: miércoles<br>**5**: jueves<br>**6**: viernes<br>**7**: sábado|
|**Programar la hora de la instalación**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: **23** horas (**0** es medianoche) (valor predeterminado: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: el usuario no puede establecer el temporizador de período de gracia de la contraseña y el valor se establece como "siempre"<br>**1**: el usuario puede establecer el temporizador de período de gracia de la contraseña (valor predeterminado)|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: no se permite **usar la conexión Wi-Fi**.<br>**1**: **se permite usar la conexión Wi-Fi** (valor predeterminado)|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|Escritorio y Mobile<br>**Tipo de datos:** entero<br />**Valores:** **0**: No permitir el uso compartido de Internet; **1**: Permitir compartir Internet (valor predeterminado)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: no se permite la conexión Wi-Fi fuera de la MDM aprovisionada.<br>**1**: se permite agregar nuevos SSID de red más allá de los de la MDM aprovisionada (valor predeterminado).|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|Escritorio y Mobile<br>**Tipo de datos:** entero<br />**Valores**<br>**0** : no permitido (valor de Enterprise solo)<br>**1** : limitado<br>**2**: completo (valor predeterminado)<br>**3**: completo e información de diagnóstico|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0** : no permitido<br>**1**: solo configuración (valor predeterminado)<br>**2**: configuración y experimentación|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: no permitir el modo antirrobo<br>**1**: preferencia del usuario (valor predeterminado)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: no se permite la VPN a través de la red de telefonía móvil<br>**1**: la VPN puede usar cualquier conexión, incluida la de la red de telefonía móvil (valor predeterminado)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: no se permite al usuario activar el Bluetooth.<br>**1**: reservado. El usuario puede activar y configurar el Bluetooth (no admitido en Windows Phone 8.1 para MDM, EAS, Windows 10 Escritorio o Windows 10 Mobile)<br>**2**: permitido El usuario puede activar y configurar el Bluetooth (valor predeterminado)|
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
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0** : no permitir<br>El diccionario extendido abierto está desactivado.<br>Un usuario no puede:<br>- Agregar un nuevo diccionario extendido abierto<br />- Agregar un nuevo archivo de configuración de integración de búsqueda<br>- Usar la característica de candidato en la nube<br>- Enviar la palabra registrada del usuario.<br>**1**: permitir<br>El diccionario extendido abierto se puede agregar y usar de forma predeterminada. La función de integración de búsqueda también se puede usar de forma predeterminada.<br>Un usuario puede:<br>Usar la característica de candidato en la nube.|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: el registro de conversión incorrecta está desactivado.<br>**1**: el registro de conversión incorrecta está activado (valor predeterminado).|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: no se filtra ningún carácter (valor predeterminado).<br>**1**: se filtra todo excepto los caracteres Shift JIS.|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br />**0**: no se filtra ningún carácter (valor predeterminado).<br>**1**: se filtra todo excepto los caracteres JIS0208.|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: no se filtra ningún carácter (valor predeterminado).<br>**1**: se filtra todo excepto los caracteres JIS0208 o EUDC.|
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
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0** : filtrado estricto más alto del contenido para adultos<br>**1**: filtrado moderado del contenido para adultos (no se filtrarán los resultados de búsqueda válidos, valor predeterminado)|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**Forzar tamaño inicial**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: permitir al usuario cambiar el tamaño (valor predeterminado)<br>**1**: forzar la pantalla no completa<br>**2**: forzar la pantalla completa|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: no aplazar la actualización (permanecer en la rama actual, CB, valor predeterminado)<br>**1**: habilitar que las actualizaciones se aplacen (el dispositivo sigue la rama actual para negocios, CBB y reglas)<br />Si desea obtener información detallada, consulte:<br>[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|Escritorio y Mobile<br>**Descripción:** directiva para aplazar actualizaciones de software durante un máximo de 4 semanas<br />**Tipo de datos:** entero<br />**Valores**<br> **0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br>**1**-**4**: número de semanas durante las que aplazar las actualizaciones de software.<br />Si desea obtener información detallada, consulte:<br>[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|Escritorio y Mobile<br>**Descripción:** directiva para aplazar actualizaciones de funciones durante un máximo de 8 meses<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br>**1**-**8**: número de meses durante los que aplazar actualizaciones de características.<br />Si desea obtener información detallada, consulte:<br>[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|Escritorio y Mobile<br>**Descripción:** permite que un dispositivo deje de recibir actualizaciones durante 5 semanas.<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br>**1**: pausar las actualizaciones (expira transcurridas 5 semanas)|

## <a name="windows-defender-settings"></a>Configuración de Windows Defender

|Nombre y URI de la directiva|Detalles|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: supervisar todos los archivos (valor predeterminado)<br>**1** : supervisar los archivos entrantes<br>**2** : supervisar los archivos salientes|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0** - **90**: representa la cantidad de tiempo que se conservará el malware.<br>**Valor predeterminado:** **0**: se guarda en la carpeta de cuarentena para siempre y no se quita automáticamente|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**1**: examen rápido (valor predeterminado)<br>**2**: examen completo|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0** -todos los días (valor predeterminado)<br>**1**: lunes<br>**2**: martes<br>**3**: miércoles<br>**4**: jueves<br>**5**: viernes<br>**6**: sábado<br>**7**: domingo<br>**8** : ningún examen programado|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: 12:00<br>**60** : 1:00<br>**120**: 2:00 (valor predeterminado)<br>**180** : 3:00<br>**240** : 4:00<br>**300** : 5:00<br>**360** : 6:00<br>**420** : 7:00<br>**480** : 8:00<br>**540** : 9:00<br>**600** : 10:00<br>**660** : 11:00<br>**720** : 12:00<br>**780** : 13:00<br>**840** : 14:00<br>**900** : 15:00<br>**960** : 16:00<br>**1020** : 17:00<br>**1080** : 18:00<br>**1140** : 19:00<br>**1200** : 20:00<br>**1260** : 21:00<br>**1320** : 22:00<br>**1381** : ventana de mantenimiento|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|Solo escritorio<br>**Tipo de datos:** entero<br />**Valores**<br>**0**: 12:00<br>**60** : 1:00<br>**120**: 2:00 (valor predeterminado)<br>**180** : 3:00<br>**240** : 4:00<br>**300** : 5:00<br>**360** : 6:00<br>**420** : 7:00<br>**480** : 8:00<br>**540** : 9:00<br>**600** : 10:00<br>**660** : 11:00<br>**720** : 12:00<br>**780** : 13:00<br>**840** : 14:00<br>**900** : 15:00<br>**960** : 16:00<br>**1020** : 17:00<br>**1080** : 18:00<br>**1140** : 19:00<br>**1200** : 20:00<br>**1260** : 21:00<br>**1320** : 22:00<br>**1380** : 23:00|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0** - **100** (valor predeterminado: **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|Solo escritorio<br />**Tipo de datos:** entero<br>**Valores:** **0**: no permitido (valor predeterminado); **1**: permitido|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido (valor predeterminado); **1**: permitido|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado). También se ejecuta cuando RTP está activado y se establece como permitido|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: no comprobar las firmas en un intervalo<br>**1**: comprobar las firmas cada hora<br>**2**: comprobar las firmas cada 2 horas, etc.<br>**24**: comprobar las firmas cada día<br>**Valor predeterminado:** 8: comprobar las firmas cada 8 horas|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitido; **1**: permitido (valor predeterminado)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: preguntar siempre (valor predeterminado)<br>**1** : enviar muestras seguras automáticamente<br>**2** : no enviar nunca<br>**3** : enviar todas las muestras automáticamente|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|Solo escritorio<br />**Tipo de datos:** cadena<br />**Valores**<br>*&lt;lista de extensiones separadas por punto y coma&gt;* p. ej. **obj;lib**<br>**Valor predeterminado**: no se excluye ninguna extensión|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|Solo escritorio<br />**Tipo de datos:** cadena<br />**Valores**<br />*&lt;lista de rutas de acceso separadas por punto y coma&gt;*<br />Ejemplo: **c:\test;c:\test1.exe**<br />**Valor predeterminado:** no se excluye ninguna ruta de acceso|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|Solo escritorio<br />**Tipo de datos:** cadena<br />**Valores**<br>*&lt;lista de rutas de acceso separadas por punto y coma&gt;*<br>Ejemplo: **c:\test.exe;c:\test1.exe**<br>**Valor predeterminado:** no se excluye ningún proceso|

## <a name="edge-browser-settings"></a>Configuración del explorador Edge

|Nombre y URI de la directiva|Detalles|
|---------------|------------|-----------|
|**Permitir explorador**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Solo Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: exploración desactivada; **1**: exploración activada (valor predeterminado)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no mostrar sugerencias; **1**: mostrar sugerencias (valor predeterminado)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: deshabilitado (abrir sitios de intranet en el explorador Edge, valor predeterminado).<br>**1**: habilitado (abrir sitios de intranet en Internet Explorer).|
|**Permitir No realizar seguimiento**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: deshabilitado (DNT no enviado; valor predeterminado); **1**: habilitado (enviar DNT)|
|**Configurar SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores:** **0**: no permitir; **1**: permitir (valor predeterminado)|
|**Permitir elementos emergentes**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: bloquear elementos emergentes (valor predeterminado); **1**: permitir elementos emergentes|
|**Permitir cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: permitir cookies de todos los sitios web (valor predeterminado)<br>**1**: bloquear solo cookies de terceros<br>**2**: bloquear todas las cookies|
|**Permitir guardar contraseña**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Escritorio y Mobile<br />**Tipo de datos:** entero<br />**Valores**<br>**0**: el administrador de contraseñas está deshabilitado <br>**1**: el administrador de contraseñas está habilitado (valor predeterminado)|
|**Permitir el autorrelleno**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Solo escritorio<br />**Tipo de datos:** entero<br />**Valores:** **0**: deshabilitado (valor predeterminado); **1**: habilitado|
|**Configurar la lista de sitios de empresa**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Solo escritorio<br />**Tipo de datos:** cadena<br />**Valores:<br>**0**: no configurado; <br>**1**: usar la lista de sitios del modo de empresa de IE si está configurado (valor predeterminado); <br>**2**: especificar la ubicación de la lista de sitios de empresa|

