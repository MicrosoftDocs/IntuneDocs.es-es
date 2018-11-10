---
title: 'Agregar una configuración personalizada para dispositivos Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o cree un perfil personalizado para usar la configuración OMA-URI para dispositivos con Windows 10 en Microsoft Intune. Use un perfil personalizado para agregar una configuración personalizada.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78ed923c7502744ccd7f23e341049ce8ee8a8d86
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983217"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>Usar una configuración personalizada para dispositivos Windows 10 en Intune

Con Microsoft Intune, puede agregar o crear una configuración personalizada para los dispositivos Windows 10 mediante "perfiles personalizados". Los perfiles personalizados son una característica de Intune diseñada para agregar una configuración de dispositivo y características que no están integradas Intune.

Los perfiles personalizados de Windows 10 usan la configuración OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) para configurar diferentes características. Esta configuración la suelen usar los fabricantes de dispositivos móviles para controlar las características en el dispositivo. 

Windows 10 tiene disponibles muchos valores de proveedores de servicios de configuración (CSP), como el [proveedor de servicios de configuración de directivas (CSP de directivas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Si busca una configuración determinada, recuerde que el [perfil de restricción de dispositivos de Windows 10](device-restrictions-windows-10.md) incluye muchas configuraciones integradas. Por lo tanto, es posible que no necesite especificar valores personalizados.

En este artículo:

- Se explica cómo crear un perfil personalizado para dispositivos Windows 10
- Se incluye una lista de las configuraciones OMA-URI recomendadas
- Se proporciona un ejemplo de un perfil personalizado que abre una conexión VPN

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre para el perfil, como `windows 10 custom profile`.
    - **Descripción**: escriba una descripción para el perfil
    - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
    - **Tipo de perfil**: elija **Personalizado**.

4. En **Configuración OMA-URI personalizada**, seleccione **Agregar**. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.
    - **Descripción**: escriba una descripción con información general sobre la configuración y otros detalles importantes.
    - **OMA-URI** (distingue mayúsculas de minúsculas): escriba la configuración OMA-URI que quiere usar.
    - **Tipo de datos**: elija el tipo de datos que se usará para esta configuración OMA-URI. Las opciones son:

        - String
        - Cadena (archivo XML)
        - Fecha y hora
        - Integer
        - Punto flotante
        - Boolean
        - Base64 (archivo)

    - **Valor**: escriba el valor de datos que quiere asociar con la configuración OMA-URI especificada. El valor depende del tipo de datos que ha seleccionado. Por ejemplo, si elige **Fecha y hora**, debe seleccionar el valor en un selector de fecha.

    Después de agregar algunos valores de configuración, puede seleccionar **Exportar**. Haga clic en **Exportar** para crear una lista de todos los valores agregados en un archivo de valores separados por comas (.csv).

5. Haga clic en **Aceptar** para guardar los cambios. Continúe agregando más valores según sea necesario.
6. Cuando termine, seleccione **Aceptar** > **Crear** para crear el perfil de Intune. Una vez que se haya completado, el perfil se mostrará en la lista **Configuración del dispositivo - Perfiles**.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, la configuración **Connectivity/AllowVPNOverCellular** está habilitada. Este valor permite que un dispositivo Windows 10 abra una conexión VPN cuando se encuentre en una red de telefonía móvil.

![Ejemplo de una directiva personalizada que contiene opciones de VPN](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Buscar las directivas que se pueden configurar

Encontrará una lista completa de todos los proveedores de servicio de configuración (CSP) que Windows 10 admite en la [referencia del proveedor de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference).

No todas las configuraciones son compatibles con todas las versiones de Windows 10. En la [referencia del proveedor de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) se indica qué versiones son compatibles con cada CSP.

Además, Intune no es compatible con todas las configuraciones que aparecen en la [referencia del proveedor de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference). Para saber si Intune admite la configuración que quiere, abra el artículo correspondiente a dicha configuración. En la página de cada configuración se muestra la operación que admite. Para trabajar con Intune, la configuración debe ser compatible con las operaciones **Add** o **Replace**.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md).
