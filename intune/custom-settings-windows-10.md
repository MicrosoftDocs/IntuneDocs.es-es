---
title: Configuración personalizada para dispositivos Windows 10 en Microsoft Intune - Azure | Microsoft Docs
description: Configure las opciones personalizadas de OMA-URI en dispositivos que ejecutan Windows 10 mediante un perfil personalizado en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdbb6643a4ee8aace0db22cd7f9189f7ac6445f0
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232833"
---
# <a name="custom-oma-uri-settings-for-windows-10-devices---intune"></a>Configuración personalizada de OMA-URI para dispositivos de Windows 10 - Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use el perfil **personalizado** de Microsoft Intune para Windows 10 y Windows 10 Mobile para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance). Estos valores se usan para controlar las características en los dispositivos. Windows 10 tiene disponibles muchos valores de proveedores de servicios de configuración (CSP), como el [proveedor de servicios de configuración de directivas (CSP de directivas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Si busca una configuración determinada, recuerde que el [perfil de restricción de dispositivos de Windows 10](device-restrictions-windows-10.md) incluye muchas configuraciones que están integradas en Intune y no requiere valores personalizados.

## <a name="configure-custom-settings"></a>Configuración de opciones personalizadas

1. Cree un nuevo perfil de configuración mediante el tipo de perfil **Personalizado**. En [Configuración personalizada del dispositivo](custom-settings-configure.md) se indican los pasos.
2. En **Configuración OMA-URI personalizada**, seleccione **Agregar** para crear una nueva configuración. También puede hacer clic en **Exportar** para crear una lista de todos los valores configurados en un archivo de valores separados por comas (.csv).
3. Para cada configuración de OMA-URI que quiera agregar, escriba la siguiente información:

- **Nombre**: escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.
- **Descripción**: si quiere, escriba una descripción para la configuración.
- **OMA-URI (distingue mayúsculas de minúsculas)**: escriba el OMA-URI para el que quiere proporcionar un valor de configuración.
- **Tipo de datos**: elija una de estas opciones:
  - **Cadena**
  - **Cadena (XML)**
  - **Fecha y hora**
  - **Entero**
  - **Punto flotante**
  - **Booleano**
  - **Base64**
- **Valor**: escriba el valor o el archivo que quiere asociar con la configuración OMA-URI especificada.

4. Cuando termine, seleccione **Aceptar**. En **Crear perfil**, seleccione **Crear**. El perfil se crea y se muestra en la lista de perfiles.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente, la configuración **Connectivity/AllowVPNOverCellular** está habilitada. Este valor permite que un dispositivo Windows 10 abra una conexión VPN cuando se encuentre en una red de telefonía móvil.

![Ejemplo de una directiva personalizada que contiene opciones de VPN](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Buscar las directivas que se pueden configurar

Encontrará una lista completa de todos los proveedores de servicio de configuración (CSP) que Windows 10 admite en la [referencia del proveedor de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference).

No todas las configuraciones son compatibles con todas las versiones de Windows 10. En la [referencia del proveedor de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) se indica qué versiones son compatibles con cada CSP.

Además, Intune no admite todas las configuraciones mostradas. Para saber si Intune admite la configuración que quiere, abra el artículo correspondiente a dicha configuración. La página de cada configuración muestra una operación compatible. Para trabajar con Intune, la configuración debe ser compatible con las operaciones **Add** o **Replace**.
