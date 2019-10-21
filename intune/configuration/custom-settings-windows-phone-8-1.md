---
title: 'Agregar una configuración personalizada para dispositivos Windows Phone 8.1 en Microsoft Intune: Azure | Microsoft Docs'
titleSuffix: ''
description: Agregue o cree un perfil personalizado para usar la configuración OMA-URI para dispositivos con Windows Phone 8.1 en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1362f6c6453569d1c306cd16397cc9a7f83736e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495350"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Usar una configuración personalizada para dispositivos Windows Phone 8.1 en Intune

Con Microsoft Intune, puede agregar o crear una configuración personalizada para los dispositivos Windows Phone 8.1 mediante "perfiles personalizados". Los perfiles personalizados son una característica de Intune diseñada para agregar una configuración de dispositivo y características que no están integradas Intune.

Los perfiles personalizados de Windows Phone 8.1 usan la configuración OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) para configurar diferentes características. Esta configuración la suelen usar los fabricantes de dispositivos móviles para controlar las características en el dispositivo. [Windows Phone documentación del protocolo MDM de 8,1](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10)) muestra la configuración.

En este artículo se muestra cómo crear un perfil personalizado para dispositivos Windows Phone 8.1. 

## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre para el perfil, como `windows phone custom profile`.
    - **Descripción**: escriba una descripción para el perfil
    - **Plataforma**: elija **Windows Phone 8.1**.
    - **Tipo de perfil**: elija **Personalizado**.

4. En **Configuración OMA-URI personalizada**, seleccione **Agregar**. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.
    - **Descripción**: escriba una descripción con información general sobre la configuración e información relacionada que le ayude a encontrarla.
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

En el ejemplo siguiente, Windows 8.1 dispositivos telefónicos no pueden cambiar las redes móviles cuando viajan fuera del área de cobertura de la portadora.

- **Nombre**: permitir itinerancia de datos móviles
- **Descripción**: habilita o deshabilita la itinerancia de datos móviles
- **OMA-URI** (distingue mayúsculas de minúsculas):./Vendor/msft/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **Tipo de datos:** entero
- **Valor**: 0

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md).

Vea cómo crear un perfil personalizado en [Dispositivos Windows 10](../custom-settings-windows-10.md).
