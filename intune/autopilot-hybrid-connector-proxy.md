---
title: Configuración del proxy para el conector de Intune para Active Directory
description: Se explica cómo configurar el conector de Intune para Active Directory para trabajar con servidores proxy locales existentes.
keywords: ''
author: master11218
ms.author: tanvira
manager: smantri
ms.date: 4/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: ebefba3f912669166e5e077fe15b0b04f4a7b75f
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61490014"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>Trabajar con servidores proxy locales existentes

En este artículo se explica cómo configurar el conector de Intune para Active Directory para trabajar con servidores proxy de salida. Está dirigido a clientes con entornos de red que tienen servidores proxy.

Para más información sobre cómo funcionan los conectores, vea [Understand Azure AD Application Proxy connectors](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-connectors) (Descripción de conectores de Azure AD Application Proxy).

## <a name="bypass-outbound-proxies"></a>Omitir servidores proxy de salida

Los conectores tienen componentes del sistema operativo subyacentes que realizan solicitudes salientes. Estos componentes intentan automáticamente encontrar un servidor proxy en la red mediante Detección automática de proxy web (WPAD).

Los componentes del sistema operativo intentan localizar un servidor proxy mediante una búsqueda DNS para wpad.domainsuffix. Si la búsqueda se resuelve en DNS, se realiza una solicitud HTTP a la dirección IP para wpad.dat. Esta solicitud se convierte en el script de configuración de proxy en su entorno. El conector usa este script para seleccionar un servidor proxy de salida, aunque es posible que el tráfico del conector siga sin pasar porque hay que configurar más valores en el servidor proxy.

Puede configurar el conector para omitir el proxy local para asegurarse de que usa una conectividad directa con los servicios de Azure. Se recomienda hacer esto siempre que lo permita la directiva de red, porque así tendrá una configuración menos que mantener.

Para deshabilitar el uso de proxy de salida para el conector, edite el archivo C:\Archivos de programa\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config y agregue la dirección y el puerto del proxy en la sección que se muestra en este ejemplo de código:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```
Para asegurarse de que el servicio Connector Updater también omite el proxy, realice un cambio similar en C:\Archivos de programa\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

Asegúrese de realizar copias de los archivos originales, en caso de que deba volver a los archivos .config predeterminados.

Una vez que se hayan modificado los archivos de configuración, deberá reiniciar el servicio de conector de Intune. 

1. Abra **services.msc**.
2. Busque y seleccione el **Servicio ODJConnector de Intune**.
3. Seleccione **Reiniciar**.

![Captura de pantalla de reinicio del servicio](media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>Pasos siguientes

[Administrar los dispositivos](device-management.md)