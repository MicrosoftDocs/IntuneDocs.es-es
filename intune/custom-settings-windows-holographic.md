---
title: 'Configuración personalizada para dispositivos Windows Holographic for Business en Microsoft Intune: Azure | Microsoft Docs'
description: Cree un perfil personalizado para usar la configuración de OMA-URI para dispositivos con Windows Holographic for Business en Microsoft Intune. Puede establecer las opciones de los proveedores de servicios de configuración (CSP) de directivas AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates y ApplicationLaunchRestrictions.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/26/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b8ba5078d304c0e9d6b10e4efb868642323c901c
ms.sourcegitcommit: 2795255e89cbe97d0b17383d446cca57c7335016
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2018
ms.locfileid: "47403585"
---
# <a name="custom-device-settings-for-devices-running-windows-holographic-for-business-in-intune"></a>Configuración de dispositivos personalizada para dispositivos con Windows Holographic for Business en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Use el perfil **personalizado** de Microsoft Intune para Windows Holographic for Business para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que se puede usar para controlar las características en los dispositivos. Windows Holographic for Business ofrece muchas opciones de configuración de proveedores de servicios de configuración (CSP). Para obtener una introducción a CSP, consulte [Introducción a los proveedores de servicios de configuración (CSP) para los profesionales de las TI](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Para conocer los CSP específicos admitidos por Windows Holographic, consulte [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP admitidos en Windows Holographic).

Si busca una configuración determinada, recuerde que el [perfil de restricción de dispositivos de Windows Holographic for Business](device-restrictions-windows-holographic.md) incluye muchas configuraciones integradas y no requiere que especifique valores personalizados.

## <a name="create-the-custom-oma-uri-profile"></a>Crear el perfil personalizado de OMA-URI

1. Use las instrucciones de [Configuración de los valores personalizados del dispositivo](custom-settings-configure.md) para comenzar.
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
  - **OMA-URI (distingue mayúsculas de minúsculas)**: escriba el OMA-URI para el que quiere proporcionar un valor de configuración.
  - **Valor**: escriba el valor que quiere asociar con la configuración OMA-URI especificada.
5. Cuando haya terminado, vuelva a **Crear perfil** y haga clic en **Crear**. El perfil se crea y aparece en la lista de perfiles.

## <a name="recommended-custom-settings"></a>Configuración personalizada recomendada

La siguiente configuración es útil para dispositivos que ejecuten Windows Holographic for Business:

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Entero<br/>0: no permitido<br/>1: permitido (valor predeterminado)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Entero<br/>0: no se permite el servicio de actualización <br/>1: se permite el servicio de actualización (valor predeterminado).|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Entero<br/>0: no permitido<br/>1: permitido (valor predeterminado)|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Entero<br/>0: no configurado. El dispositivo instala todas las actualizaciones aplicables.<br/>1: el dispositivo solo instala las actualizaciones que son aplicables y que están en la lista Actualizaciones aprobadas. Establezca esta directiva en 1 si el departamento de TI quiere controlar la implementación de actualizaciones en dispositivos, por ejemplo, cuando es necesario realizar pruebas antes de la implementación.|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Entero 0-23, donde 0 = 12 a.m. y 23 = 11 p.m.<br/>El valor predeterminado es 3.|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|String<br/>URL: el dispositivo busca actualizaciones desde el servidor de WSUS en la URL especificada.<br/>No configurado: el dispositivo busca actualizaciones desde Microsoft Update.|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |---|---|
> |./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br/><br/>**Importante**<br/>Debe leer y aceptar los CLUF de la actualización en nombre de los usuarios finales. Si no lo hace, es un incumplimiento de las obligaciones legales o contractuales.|Nodo para las aprobaciones de actualización y la aceptación de CLUF en nombre del usuario final.<br/><br/>Para más información, consulte [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) (CSP de actualización).|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |----|---|
> |./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br/><br/>**Importante**<br/>El artículo de AppLocker CSP usa ejemplos XML con escape. Para configurar los valores con perfiles personalizados de Intune, debe usar XML sin formato.|String<br/>Para más información, consulte [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp) (CSP de AppLocker).|

### <a name="deletionpolicyhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[DeletionPolicy](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|Entero<br/>0 - eliminar inmediatamente cuando el dispositivo vuelva a un estado sin usuarios activos<br/>1 - eliminar cuando se alcance el umbral de capacidad de almacenamiento (valor predeterminado)<br/>2 - eliminar cuando se alcancen el umbral de capacidad de almacenamiento y el umbral de inactividad de perfil|

### <a name="enableprofilemanagerhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[EnableProfileManager](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager|Boolean<br/>True - habilitar<br/>False - deshabilitar (valor predeterminado)|

### <a name="profileinactivitythresholdhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[ProfileInactivityThreshold](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold|Entero<br/>El valor predeterminado es 30.|


### <a name="storagecapacitystartdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStartDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion|Entero<br/>El valor predeterminado es 25.|

### <a name="storagecapacitystopdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStopDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de datos|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion|Entero<br/>El valor predeterminado es 50.|

## <a name="find-the-policies-you-can-configure"></a>Buscar las directivas que se pueden configurar

Puede encontrar una lista completa de todos los proveedores de servicios de configuración (CSP) que admite Windows Holographic en [CSP admitidos en Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). No todas las configuraciones son compatibles con todas las versiones de Windows Holographic. La tabla del artículo sobre Windows indica las versiones compatibles con cada CSP.

Además, Intune no admite todas las configuraciones que aparecen en el artículo. Para saber si Intune admite la configuración que quiere, abra el artículo correspondiente a dicha configuración. La página de cada configuración muestra una operación compatible. Para trabajar con Intune, la configuración debe ser compatible con las operaciones **Add** o **Replace**.
