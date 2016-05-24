---
# required metadata

title: Configuraciones personalizadas para perfiles de VPN | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuraciones personalizadas para perfiles de VPN

## Crear una configuración personalizada
Puede usar configuraciones personalizadas para crear perfiles de VPN en Intune. Para crear una configuración personalizada:

   1. En la consola de administración de Intune, seleccione **Directiva** -> **Agregar directiva** -> *<Expand platform>* -> **Configuración personalizada** -> **Crear directiva**..
   2. Indique un nombre para la directiva.
   3. En cada opción de URI, haga clic en **Agregar** y suministre la información que se le pida. Este podría ser un ejemplo:

   ![Cuadro de diálogo de configuración personalizada de perfil de VPN](intune/media/Intune_Add_VPN_URI.png)

   4.  Tras especificar todos los valores de URI, haga clic en **Guardar directiva** y, después, implemente la directiva.

## Implementar una directiva de configuración

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, luego, haga clic en **Administrar implementación**..

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   **Para implementar la directiva**: seleccione uno o más grupos en los que quiera implementar la directiva y haga clic en **Agregar** &gt; **Aceptar**..

    -   **Para cerrar el cuadro de diálogo sin implementarla**: haga clic en **Cancelar**..

Cuando se selecciona una directiva implementada, puede ver más información acerca de la implementación en la parte inferior de la lista de directivas.

##Ejemplo de valores de URI de una configuración personalizada de perfil de VPN
Estas son entradas de ejemplo de valores de URI para crear una configuración personalizada para una VPN en una empresa ficticia denominada Contoso. Para obtener más información, como el tipo de datos de cada entrada, vea [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx) (CSP de VPNv2).

VPN de Contoso nativa (IKEv2):
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
&lt;EapHostConfig xmlns = "http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Escriba xmlns = "http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/tipo&gt;&lt;VendorId xmlns = "http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns = "http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns = "http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns = "http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns = "http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;tipo&gt;13&lt;/tipo&gt;&lt;EapType xmlns = "http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns = "http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns = "http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**
True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Los clientes que tengan preguntas sobre cómo usar estos valores o que necesiten más información sobre qué hacen deben consultar la documentación de CSP correspondiente:
https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx

## Valores de URI para una VPN por aplicación de Android en PulseSecure
### URI PERSONALIZADO PARA LISTA DE PAQUETES 
-  Data type = String
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/<Name>/PackageList 
-  Value = Lista de paquete separada por delimitador
   - Delimitadores: punto y coma (;), dos puntos (:), coma (,), barra vertical (|)

Ejemplos: 
- com.android.chrome
- com.android.chrome;com.android.browser

### URI PERSONALIZADO PARA MODO (OPCIONAL)
- Data Type = String
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode 

> Notas
> - Use el mismo *nombre* que haya asignado al perfil personalizado
> - Valores posibles: *GLOBAL*, *WHITELIST*, *BLACKLIST*
> - El valor predeterminado es *GLOBAL* si no se proporciona ningún valor de PackageList (compatibilidad con versiones anteriores de perfiles de todo el sistema)
> - El valor predeterminado es *WHITELIST* si se proporciona un valor de PackageList


### Consulte también
(Conexiones VPN en Microsoft Intune)[vpn-connections-in-microsoft-intune.md]


<!--HONumber=May16_HO1-->


