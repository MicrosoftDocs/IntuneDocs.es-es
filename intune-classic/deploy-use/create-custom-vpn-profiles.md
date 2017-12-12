---
title: Configuraciones personalizadas para perfiles de VPN de Microsoft Intune
description: Utilice las configuraciones personalizadas para crear perfiles de VPN en Intune.
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab235f10c8c91e707c623eca5168ff75de234f32
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="custom-configurations-for-microsoft-intune-vpn-profiles"></a>Configuraciones personalizadas para perfiles de VPN de Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="create-a-custom-configuration"></a>Crear una configuración personalizada
Puede usar directivas de configuración personalizadas de Intune para crear perfiles de VPN para:

* Dispositivos que ejecutan Android 4 y versiones posteriores
* Dispositivos Android for Work
* Dispositivos inscritos que ejecutan Windows 8.1 y versiones posteriores
* Dispositivos que ejecutan Windows Phone 8,1 y versiones posteriores
* Dispositivos inscritos que ejecutan Windows 10 Escritorio
* Dispositivos que ejecutan Windows 10 Mobile

Este tipo de directiva puede ser útil cuando las directivas estándar de VPN de Intune no contienen la configuración que quiere usar.

## <a name="to-create-a-custom-configuration-policy"></a>Para crear una directiva de configuración personalizada:

   1. En la [Consola de administración de Intune](https://manage.microsoft.com), seleccione **Directiva** > **Agregar directiva** > *Expandir plataforma* > **Configuración personalizada** > **Crear directiva**.
   2. Especifique un nombre para la directiva.
   3. En cada opción de configuración del URI que quiere especificar, pulse **Agregar** y proporcione la información que se le solicite. Este podría ser un ejemplo:

   ![Cuadro de diálogo de configuración personalizada de perfil de VPN](./media/Intune_Add_VPN_URI.png)

   4.  Una vez que haya escrito todas las opciones de configuración del URI, elija **Guardar directiva** y, después, impleméntela.

Después, [implemente la directiva](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy) de manera normal.

## <a name="example-uri-settings"></a>Ejemplo de la configuración de URI

Estas opciones de configuración pueden usarse para crear una configuración personalizada para una VPN en una empresa ficticia denominada Contoso.
Para ver los detalles completos de todas las opciones que puede usar, vea [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx).

**VPN de Contoso nativa (IKEv2):**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

**vpn.contoso.com**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

**Ikev2<br />** ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

**SplitTunnel**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

**Eap**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
``` xml
<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
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
            <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </PerformServerValidation>
            <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </AcceptServerName>
         </EapType>
      </Eap>
   </Config>
</EapHostConfig>
```
**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**<br />
True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**<br />
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**<br />
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**<br />
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**<br />
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**<br />
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Si tiene preguntas sobre cómo se deben usar estas opciones o necesita más información sobre lo que hacen, los clientes deben consultar la [documentación del proveedor de servicios de configuración (CSP)](https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx).

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>Valores de URI para una VPN por aplicación de Android en PulseSecure
### <a name="custom-uri-for-package-list"></a>URI PERSONALIZADO PARA LISTA DE PAQUETES
-  Data type = String
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  Value = Lista de paquete separada por delimitador
   - Delimitadores: punto y coma (;), dos puntos (:), coma (,), barra vertical (|)

Ejemplos:
- com.android.chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>URI PERSONALIZADO PARA MODO (OPCIONAL)
- Data Type = String
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> Notas
> - Use el mismo *nombre* que haya asignado al perfil personalizado
> - Valores posibles: *GLOBAL*, *WHITELIST*, *BLACKLIST*
> - El valor predeterminado es *GLOBAL* si no se proporciona ningún valor de PackageList (compatibilidad con versiones anteriores de perfiles de todo el sistema)
> - El valor predeterminado es *WHITELIST* si se proporciona un valor de PackageList


### <a name="see-also"></a>Consulte también
[Conexiones VPN en Microsoft Intune](vpn-connections-in-microsoft-intune.md)
