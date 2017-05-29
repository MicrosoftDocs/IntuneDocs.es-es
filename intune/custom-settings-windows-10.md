---
title: "Configuración personalizada de Intune para dispositivos Windows 10"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca la configuración que puede usar en un perfil personalizado de Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 52ad4f141c3b2b73a400c69fb9d9beb174bbac64
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Configuración personalizada de dispositivos para dispositivos Windows 10 en Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

 Use el perfil **personalizado** de Microsoft Intune para Windows 10 y Windows 10 Mobile para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que se puede usar para controlar las características en los dispositivos. Windows 10 tiene disponibles muchas opciones de configuración de CSP, por ejemplo, el [proveedor de servicios de configuración de directivas (CSP de directivas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Si busca una configuración determinada, recuerde que el [perfil de restricción de dispositivos de Windows 10](device-restrictions-windows-10.md) incluye muchas configuraciones que están integradas en Intune y no requiere que especifique valores personalizados.

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
5. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.
El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="example"></a>Ejemplo
En la siguiente captura de pantalla, se ha habilitado el valor **Connectivity/AllowVPNOverCellular**. De esta forma, un dispositivo Windows 10 puede abrir una conexión VPN cuando se encuentra en una red de telefonía móvil.

> ![Ejemplo de una directiva personalizada que contiene opciones de VPN](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Búsqueda de las directivas que puede configurar

Encontrará una lista completa de todos los proveedores de servicio de configuración (CSP) que Windows 10 admite en la [referencia del proveedor de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) en la biblioteca de documentación de Windows.

No todas las configuraciones son compatibles con todas las versiones de Windows 10. La tabla en el tema sobre Windows indica las versiones compatibles con cada CSP.

Además, Intune no admite todas las configuraciones que aparecen en el tema. Para saber si Intune admite la configuración que desea, abra el tema correspondiente a dicha configuración. La página de cada configuración muestra una operación compatible. Para trabajar con Intune, la configuración debe ser compatible con las operaciones **Add** o **Replace**.



