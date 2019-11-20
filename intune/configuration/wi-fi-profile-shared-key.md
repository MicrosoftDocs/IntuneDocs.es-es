---
title: Creación de un perfil Wi-Fi con una clave precompartida en Microsoft Intune (Azure) | Microsoft Docs
description: Use un perfil personalizado para crear un perfil de Wi-Fi con una clave precompartida y obtenga el código XML de ejemplo para Windows, Android y perfiles de Wi-Fi basados en EAP, en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02d1311be0943d93f80f2f5a1c3f421d476af1e5
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059825"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key-in-intune"></a>Uso de un perfil de dispositivo personalizado para crear un perfil Wi-Fi con una clave precompartida en Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Las claves precompartidas se suelen usar para autenticar a los usuarios en redes Wi-Fi o en redes LAN inalámbricas. Con Intune, puede crear un perfil de Wi-Fi con una clave precompartida. Para crear el perfil, utilice la característica **Personalizar perfiles de dispositivo** en Intune. En este artículo también se incluyen algunos ejemplos de cómo crear un perfil de Wi-Fi basado en EAP.

Esta característica es compatible con:

- Android
- Windows
- Wi-Fi basado en EAP

> [!IMPORTANT]
> - Si se usa una clave precompartida con Windows 10, se produce un error de corrección en Intune. Cuando esto sucede, el perfil de Wi-Fi se asigna correctamente al dispositivo y el perfil funciona según lo previsto.
> - Si exporta un perfil de Wi-Fi que incluye una clave previamente compartida, asegúrese de que el archivo esté protegido. La clave tiene texto sin formato, por lo que es su responsabilidad protegerla.

## <a name="before-you-begin"></a>Antes de comenzar

- Le resultará más fácil copiar el código de un equipo conectado a esa red, tal como se describe a continuación.
- Puede agregar varias redes y claves si agrega más configuraciones de OMA-URI.
- En iOS, use Apple Configurator en una estación Mac para configurar el perfil.
- La opción de PSK requiere una cadena de 64 dígitos hexadecimales o una frase de contraseña de entre 8 y 63 caracteres ASCII imprimibles. No se admiten algunos caracteres, como el asterisco (*).

## <a name="create-a-custom-profile"></a>Creación de un perfil personalizado

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para la directiva. Asígnele un nombre a las directivas para que pueda identificarlas de manera sencilla más adelante. Por ejemplo, un nombre de directiva válido es **Configuración del perfil Wi-Fi de OMA-URI personalizado para dispositivos Android**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: elija la plataforma.
    - **Tipo de perfil**: seleccione **Personalizado**.

4. En **Configuración**, seleccione **Agregar**. Escriba una nueva configuración de OMA-URI con las siguientes propiedades:

    1. **Nombre**: escriba un nombre para la configuración de OMA-URI.
    2. **Descripción**: especifique una descripción para la configuración de OMA-URI. Esta configuración es opcional pero recomendada.
    3. **OMA-URI**: especifique una de las siguientes opciones:

        - **En Android**: `./Vendor/MSFT/WiFi/Profile/SSID/Settings`
        - **En Windows**: `./Vendor/MSFT/WiFi/Profile/SSID/WlanXml`

        > [!NOTE]
        > Asegúrese de incluir el carácter de punto al principio.

        SSID es el SSID para el que va a crear la directiva. Por ejemplo, si el nombre de la red Wi-Fi es `Hotspot-1`, escriba `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

    4. **Tipo de datos**: Seleccione **Cadena**.

    5. **Valor**: pegue el código XML. Vea los [ejemplos](#android-or-windows-wi-fi-profile-example) de este artículo. Actualice cada valor para que coincida con la configuración de red. En la sección de comentarios del código se incluye información útil.

5. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se muestra en la lista de perfiles. A continuación, [asigne este perfil](../device-profile-assign.md) a los grupos de usuarios. Esta directiva solo se puede asignar a grupos de usuarios.

La siguiente vez que se registre cada dispositivo, se aplicará la directiva y se creará un perfil de Wi-Fi en el dispositivo. A partir de entonces el dispositivo podrá conectarse automáticamente a la red.

## <a name="android-or-windows-wi-fi-profile-example"></a>Ejemplo de perfil de Wi-Fi de Windows o Android

Este es un ejemplo del código XML de un perfil de Wi-Fi de Android o Windows. El ejemplo se proporciona para mostrar un formato correcto y proporcionar más detalles. Es solo un ejemplo y no está pensado como una configuración recomendada para su entorno.

### <a name="what-you-need-to-know"></a>Aspectos que debe saber

- `<protected>false</protected>` debe establecerse en **false**. Si se establece en **true**, podría causar que el dispositivo esperara una contraseña cifrada y luego intentara descifrarla, lo que podría dar lugar a un error de conexión.

- `<hex>53534944</hex>` se debe establecer en el valor hexadecimal de `<name><SSID of wifi profile></name>`. Los dispositivos Windows 10 pueden devolver un falso error `x87D1FDE8 Remediation failed`, pero el dispositivo sigue conteniendo el perfil.

- El archivo XML tiene caracteres especiales, como `&` (Y comercial). Usar caracteres especiales puede impedir que el archivo XML funcione según lo previsto. 

### <a name="example"></a>Ejemplo

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
-->

<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

### <a name="eap-based-wi-fi-profile-example"></a>Ejemplo de perfil de Wi-Fi basado en EAP
En el ejemplo siguiente se incluye el código XML de un perfil de Wi-Fi basado en EAP: El ejemplo se proporciona para mostrar un formato correcto y proporcionar más detalles. Es solo un ejemplo y no está pensado como una configuración recomendada para su entorno.


```xml
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>Crear el archivo XML desde una conexión Wi-Fi existente

También puede crear un archivo XML desde una conexión Wi-Fi existente. En un equipo Windows, siga estos pasos:

1. Cree una carpeta local para los perfiles Wi-Fi exportados, como c:\WiFi.
2. Abra un símbolo del sistema como administrador (haga clic con el botón secundario en `cmd` > **Ejecutar como administrador**).
3. Ejecute `netsh wlan show profiles`. Se muestran los nombres de todos los perfiles.
4. Ejecute `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`. Este comando crea un archivo denominado `Wi-Fi-YourProfileName.xml` en c:\Wifi.

    - Si va a exportar un perfil Wi-Fi que incluye una clave precompartida, agregue `key=clear` al comando:
  
        `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

        `key=clear` exporta la clave en texto sin formato, lo que es necesario para usar correctamente el perfil.

Cuando tenga el archivo XML, copie y pegue la sintaxis XML en la configuración de OMA-URI > **Tipo de datos**. En [Creación de un perfil personalizado](#create-a-custom-profile) (en este artículo) se indican los pasos.

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` incluye también todos los perfiles en formato XML.

## <a name="best-practices"></a>Procedimientos recomendados

- Antes de implementar un perfil de Wi-Fi con PSK, confirme que el dispositivo puede conectarse directamente al punto de conexión.

- Al rotar claves (contraseñas o frases de contraseña), tenga previsto que va a producirse un tiempo de inactividad y, por tanto, planee las implementaciones. Considere la posibilidad de insertar nuevos perfiles de Wi-Fi durante las horas no laborables. Avise igualmente a los usuarios de que la conectividad puede verse afectada.

- Para tener una transición sin problemas, asegúrese de que el dispositivo del usuario final tenga una conexión a Internet alternativa. Por ejemplo, el usuario final puede volver a la red Wi-Fi de invitado (o a alguna otra red Wi-Fi) o disponer de una conexión de telefonía móvil para comunicarse con Intune. Esta conexión adicional permite que el usuario reciba actualizaciones de las directivas cuando se actualice el perfil de red Wi-Fi corporativo en el dispositivo.

## <a name="next-steps"></a>Pasos siguientes

Asegúrese de [asignar el perfil](device-profile-assign.md) y [supervise](device-profile-monitor.md) su estado.
