---
title: Configuraciones personalizadas para perfiles de VPN de Microsoft Intune | Microsoft Docs
description: Utilice las configuraciones personalizadas para crear perfiles de VPN en Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f2b364b2c57adab33df2a8e6b34c1f30c02988d3
ms.openlocfilehash: 9dbb44981c1525e6137dd8a469b1582731ee9719


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

Después, [implemente la directiva](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy) de manera normal.

## <a name="example-uri-settings"></a>Ejemplo de la configuración de URI

Estas opciones de configuración pueden usarse para crear una configuración personalizada para una VPN en una empresa ficticia denominada Contoso.
Para ver los detalles completos de todas las opciones que puede usar, vea [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx).

VPN de Contoso nativa (IKEv2): ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Type xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Type&gt;13&lt;/Type&gt;&lt;EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal** True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials** 1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address** 10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize** 8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn** true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id** %PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Los clientes que tengan preguntas sobre cómo usar estas opciones de configuración o que necesiten más información sobre lo que hacen, deben consultar la documentación del proveedor de servicios de configuración (CSP) correspondiente: https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx.

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



<!--HONumber=Dec16_HO3-->


