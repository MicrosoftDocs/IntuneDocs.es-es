---
title: "Configuración personalizada de Intune para dispositivos Windows Holographic for Business"
titlesuffix: Azure portal
description: "Obtenga información sobre las opciones de configuración que puede aplicar en un perfil personalizado de Windows Holographic for Business."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae46aef10ca294637a4d433ce273d3c53e695d64
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="custom-device-settings-for-windows-holographic-for-business-devices-in-microsoft-intune"></a>Configuración de dispositivos personalizada para dispositivos Windows Holographic for Business en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Use el perfil **personalizado** de Microsoft Intune para Windows Holographic for Business para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que se puede usar para controlar las características en los dispositivos. Windows Holographic for Business ofrece muchas opciones de configuración de proveedores de servicios de configuración (CSP). Para obtener una introducción a CSP, consulte [Introducción a los proveedores de servicios de configuración (CSP) para los profesionales de las TI](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Para conocer los CSP específicos admitidos por Windows Holographic, consulte [CSPs supported in Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP admitidos en Windows Holographic).

Si busca una configuración determinada, recuerde que el [perfil de restricción de dispositivos de Windows Holographic for Business](device-restrictions-windows-holographic.md) incluye muchas configuraciones integradas y no requiere que especifique valores personalizados.

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
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
5. Cuando haya terminado, vuelva a la hoja **Crear perfil** y haga clic en **Crear**.
El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="supported-custom-settings"></a>Configuración personalizada admitida

Windows Holographic for Business es compatible con las siguientes opciones de configuración personalizadas:


|Nombre de la configuración|OMA-URI|Tipo de datos  |
|---------|---------|---------|
|AllowFastReconnect     |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Entero (0 - no permitido, 1 - permitido)|
|AllowVPN     |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Entero (0 - no permitido, 1 - permitido)|



## <a name="how-to-find-the-policies-you-can-configure"></a>Búsqueda de las directivas que puede configurar

Puede encontrar una lista completa de todos los proveedores de servicios de configuración (CSP) que admite Windows Holographic en [CSP admitidos en Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens). No todas las configuraciones son compatibles con todas las versiones de Windows Holographic. La tabla en el tema sobre Windows indica las versiones compatibles con cada CSP.

Además, Intune no admite todas las configuraciones que aparecen en el tema. Para saber si Intune admite la configuración que desea, abra el tema correspondiente a dicha configuración. La página de cada configuración muestra una operación compatible. Para trabajar con Intune, la configuración debe ser compatible con las operaciones **Add** o **Replace**.


