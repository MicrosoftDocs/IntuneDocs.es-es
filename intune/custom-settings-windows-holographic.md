---
title: Configuración personalizada de Microsoft Intune para dispositivos Windows Holographic for Business
titlesuffix: ''
description: Obtenga información sobre las opciones de configuración que puede aplicar en un perfil personalizado de Windows Holographic for Business.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 3/6/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b95d891d1dfaecbce182fde4a2221255a7e1eb06
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-holographic-for-business"></a>Configuración de dispositivos personalizada de Microsoft Intune para dispositivos Windows Holographic for Business

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Use el perfil **personalizado** de Microsoft Intune para Windows Holographic for Business para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que se puede usar para controlar las características en los dispositivos. Windows Holographic for Business ofrece muchas opciones de configuración de proveedores de servicios de configuración (CSP). Para obtener una introducción a CSP, consulte [Introducción a los proveedores de servicios de configuración (CSP) para los profesionales de las TI](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Para conocer los CSP específicos admitidos por Windows Holographic, consulte [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP admitidos en Windows Holographic).

Si busca una configuración determinada, recuerde que el [perfil de restricción de dispositivos de Windows Holographic for Business](device-restrictions-windows-holographic.md) incluye muchas configuraciones integradas y no requiere que especifique valores personalizados.

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
2. En **Crear perfil**, elija **Configuración** para agregar uno o varios valores de configuración de OMA-URI.
3. En **Configuración OMA-URI personalizada**, haga clic en **Agregar** para agregar un nuevo valor. También puede hacer clic en **Exportar** para crear una lista de todos los valores configurados en un archivo de valores separados por comas (.csv).
4. Para cada configuración de OMA-URI que quiera agregar, escriba la siguiente información:
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
1. Cuando haya terminado, vuelva a **Crear perfil** y haga clic en **Crear**.
El perfil se crea y aparece en la lista de perfiles.

## <a name="recommended-custom-settings"></a>Configuración personalizada recomendada

La siguiente configuración es útil para dispositivos que ejecuten Windows Holographic for Business:


|Nombre de la configuración|OMA-URI|Tipo de datos  |
|---------|---------|---------|
|[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)|./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Entero<br>0: no permitido<br>1: permitido (valor predeterminado)|
|[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)|./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Entero<br>0: no permitido<br>1: permitido (valor predeterminado)|
|[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)|./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Entero<br>0: no se permite el servicio de actualización <br>1: se permite el servicio de actualización (valor predeterminado).|
|[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)|./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|String<br>URL: el dispositivo busca actualizaciones desde el servidor de WSUS en la URL especificada.<br>No configurado: el dispositivo busca actualizaciones desde Microsoft Update.|
|[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)|./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Entero<br>0: no configurado. El dispositivo instala todas las actualizaciones aplicables.<br>1: el dispositivo solo instala las actualizaciones que son aplicables y que están en la lista Actualizaciones aprobadas. Establezca esta directiva en 1 si el departamento de TI quiere controlar la implementación de actualizaciones en dispositivos, por ejemplo, cuando es necesario realizar pruebas antes de la implementación.|
|[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)|./Vendor/MSFT/Update/ApprovedUpdates<br><br>**Importante**<br>Debe leer y aceptar los CLUF de la actualización en nombre de los usuarios finales. Si no lo hace, es un incumplimiento de las obligaciones legales o contractuales.|Nodo para las aprobaciones de actualización y la aceptación de CLUF en nombre del usuario final.|
[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)|./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br><br>**Importante**<br>El artículo de AppLocker CSP usa ejemplos XML con escape. Para configurar los valores con perfiles personalizados de Intune, debe usar XML sin formato.|String<br>Para obtener más información, vea el artículo de [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp). 

## <a name="how-to-find-the-policies-you-can-configure"></a>Búsqueda de las directivas que puede configurar

Puede encontrar una lista completa de todos los proveedores de servicios de configuración (CSP) que admite Windows Holographic en [CSP admitidos en Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). No todas las configuraciones son compatibles con todas las versiones de Windows Holographic. La tabla del artículo sobre Windows indica las versiones compatibles con cada CSP.

Además, Intune no admite todas las configuraciones que aparecen en el artículo. Para saber si Intune admite la configuración que quiere, abra el artículo correspondiente a dicha configuración. La página de cada configuración muestra una operación compatible. Para trabajar con Intune, la configuración debe ser compatible con las operaciones **Add** o **Replace**.
