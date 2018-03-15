---
title: "Configuración personalizada de Microsoft Intune para dispositivos que ejecutan Windows 10"
titlesuffix: 
description: "Obtenga información sobre los valores personalizados que puede configurar en un perfil personalizado de Windows 10."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 156d37874529b4ae5a8176d7e9a8873cf440c32c
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-10"></a>Configuración de dispositivo personalizada de Microsoft Intune para dispositivos que ejecutan Windows 10 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Use el perfil **personalizado** de Microsoft Intune para Windows 10 y Windows 10 Mobile para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que se puede usar para controlar las características en los dispositivos. Windows 10 tiene disponibles muchos valores de proveedores de servicios de configuración (CSP), por ejemplo, el [proveedor de servicios de configuración de directivas (CSP de directivas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Si busca una configuración determinada, recuerde que el [perfil de restricción de dispositivos de Windows 10](device-restrictions-windows-10.md) incluye muchas configuraciones que están integradas en Intune y no requiere que especifique valores personalizados.

## <a name="configure-custom-settings"></a>Configuración de opciones personalizadas

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
2. En la página **Crear perfil**, elija **Configuración** para agregar uno o varios valores de configuración de OMA-URI.
3. En la página **Configuración OMA-URI personalizada**, haga clic en **Agregar** para agregar un nuevo valor. También puede hacer clic en **Exportar** para crear una lista de todos los valores configurados en un archivo de valores separados por comas (.csv).
4. Para cada configuración de OMA-URI que quiera agregar, escriba la siguiente información. Use la lista de este artículo para obtener información sobre las opciones de configuración que puede usar:
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
5. Cuando haya terminado, vuelva a la página **Crear perfil** y pulse **Crear**.
Se creará el perfil y aparecerá en la página con la lista de perfiles.

## <a name="example"></a>Ejemplo
En la siguiente captura de pantalla, se ha habilitado el valor **Connectivity/AllowVPNOverCellular**. De esta forma, un dispositivo Windows 10 puede abrir una conexión VPN cuando se encuentra en una red de telefonía móvil.

> ![Ejemplo de una directiva personalizada que contiene opciones de VPN](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Búsqueda de las directivas que puede configurar

Encontrará una lista completa de todos los proveedores de servicio de configuración (CSP) que Windows 10 admite en la [referencia del proveedor de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) en la biblioteca de documentación de Windows.

No todas las configuraciones son compatibles con todas las versiones de Windows 10. La tabla del artículo sobre Windows indica las versiones compatibles con cada CSP.

Además, Intune no admite todas las configuraciones que aparecen en el artículo. Para saber si Intune admite la configuración que quiere, abra el artículo correspondiente a dicha configuración. La página de cada configuración muestra una operación compatible. Para trabajar con Intune, la configuración debe ser compatible con las operaciones **Add** o **Replace**.


