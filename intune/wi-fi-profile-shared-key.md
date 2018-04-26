---
title: Creación de un perfil de Wi-Fi con una clave precompartida - Microsoft Intune - Azure | Microsoft Docs
description: Use un perfil personalizado para crear un perfil de Wi-Fi con una clave precompartida y obtenga el código XML de ejemplo para Windows, Android y perfiles de Wi-Fi basados en EAP, en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a3b98dad86b7abe5ce330ae99fdf008137cc2b11
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key---intune"></a>Uso de un perfil de dispositivo personalizado para crear un perfil de Wi-Fi con una clave precompartida - Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Normalmente las claves precompartidas se utilizan para autenticar a los usuarios en las redes Wi-Fi o en redes LAN inalámbricas. Con Intune, puede crear un perfil de Wi-Fi con una clave precompartida. Para crear el perfil, utilice la característica **Personalizar perfiles de dispositivo** en Intune. En este artículo también se incluyen algunos ejemplos de cómo crear un perfil de Wi-Fi basado en EAP.

> [!IMPORTANT]
>- Si se usa una clave previamente compartida con Windows 10, se producirá un error de corrección en Intune. Cuando esto sucede, el perfil de Wi-Fi se asigna correctamente al dispositivo y el perfil funciona según lo previsto.
>- Si exporta un perfil de Wi-Fi que incluye una clave previamente compartida, asegúrese de que el archivo esté protegido. La clave tiene texto sin formato, por lo que es su responsabilidad protegerla.

## <a name="before-you-begin"></a>Antes de comenzar

- Le resultará más fácil copiar el código de un equipo conectado a esa red, tal como se describe a continuación.
- En Android, también puede usar la herramienta [Android PSK Generator](http://intunepskgenerator.johnathonb.com/).
- Puede agregar varias redes y claves si agrega más configuraciones de OMA-URI.
- En iOS, use Apple Configurator en una estación Mac para configurar el perfil. O bien, use [iOS PSK Mobile Config Generator](http://intunepskgenerator.johnathonb.com/).

## <a name="create-a-custom-profile"></a>Creación de un perfil personalizado
Puede crear un perfil personalizado con una clave precompartida para Android, Windows o un perfil de Wi-Fi basado en EAP. Para crear el perfil mediante Azure Portal, consulte [Crear un perfil con una configuración personalizada](custom-settings-configure.md). Al crear el perfil de dispositivo, elija **Personalizar** en la plataforma de su dispositivo. No seleccione el perfil de Wi-Fi. Cuando elija la opción de personalizar, asegúrese de: 

1. Introducir un nombre y una descripción del perfil.
2. Agregar una nueva configuración de OMA-URI con las siguientes propiedades: 

   a. Escriba un nombre para esta configuración de red Wi-Fi.

   b. (Opcional) Escriba una descripción de la configuración OMA-URI o deje este campo en blanco.

   c. Establezca el **Tipo de datos** en **String**

   d. **OMA-URI**:

   - **Para Android**: ./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
   - **Para Windows**: ./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

     > [!NOTE]
     > Asegúrese de incluir el carácter de punto al principio.

     SSID es el SSID para el que va a crear la directiva. Por ejemplo, escriba `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

   e. **Campo de valor** es donde se pega el código XML. Vea los ejemplos de este artículo. Actualice cada valor para que coincida con la configuración de red. En la sección de comentarios del código se incluye información útil.
3. Seleccione **Aceptar**, guarde y, luego, asigne la directiva.

    > [!NOTE]
    > Esta directiva solo se puede asignar a grupos de usuarios.

La siguiente vez que se registre cada dispositivo, se aplicará la directiva y se creará un perfil de Wi-Fi en el dispositivo. A partir de entonces el dispositivo podrá conectarse automáticamente a la red.

## <a name="android-or-windows-wi-fi-profile-example"></a>Ejemplo de perfil de Wi-Fi de Windows o Android

Este es un ejemplo del código XML de un perfil de Wi-Fi de Android o Windows. 

> [!IMPORTANT]
>
> `<protected>false</protected>` debe establecerse en **false**. Si se establece en **true**, podría causar que el dispositivo esperara una contraseña cifrada y luego intentara descifrarla, lo que podría dar lugar a un error de conexión.
>
>  `<hex>53534944</hex>` se debe establecer en el valor hexadecimal de `<name><SSID of wifi profile></name>`.
>  Los dispositivos Windows 10 pueden devolver un falso error *0x87D1FDE8 Error de corrección*, pero el dispositivo sigue conteniendo el perfil.

```
<!--
<Name of wifi profile> = Name of profile
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Password to connect to the network
x>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
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
        <keyType>networkKey</keyType>
        <protected>false</protected>
        <keyMaterial>MyPassword</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

## <a name="eap-based-wi-fi-profile-example"></a>Ejemplo de perfil de Wi-Fi basado en EAP
En el ejemplo siguiente se incluye el código XML de un perfil de Wi-Fi basado en EAP:

```
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
También puede crear un archivo XML desde una conexión Wi-Fi existente siguiendo estos pasos: 

1. En un equipo conectado a la red inalámbrica, o que se ha conectado recientemente a ella, abra la carpeta `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}`.

   Es mejor usar un equipo que no se haya conectado a muchas redes inalámbricas. De lo contrario, tendrá que buscar en todos los perfiles hasta encontrar el correcto.

2. Busque el archivo XML que tenga el nombre correcto.
3. Cuando haya encontrado el archivo XML correcto, copie y pegue el código XML en el campo de **datos** de la página de configuración de OMA-URI.

## <a name="best-practices"></a>Procedimientos recomendados
- Antes de implementar un perfil de Wi-Fi con PSK, confirme que el dispositivo puede conectarse directamente al punto de conexión.

- Al girar las claves (contraseñas o frases de contraseña), tenga previsto que va a producirse un tiempo de inactividad y, por tanto, planee las implementaciones en consecuencia. Considere la posibilidad de insertar nuevos perfiles de Wi-Fi durante las horas no laborables. Avise igualmente a los usuarios de que la conectividad pueden verse afectada.

- Para asegurar una transición sin problemas, asegúrese de que el dispositivo del usuario final tiene una conexión a Internet alternativa. Por ejemplo, el usuario final debe poder volver a la red Wi-Fi de invitado (o a alguna otra red Wi-Fi) o disponer de una conexión de telefonía móvil para comunicarse con Intune. Esta conexión adicional permite que el usuario reciba actualizaciones de las directivas cuando se actualice el perfil de red Wi-Fi corporativo en el dispositivo.
