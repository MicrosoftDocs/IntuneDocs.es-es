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
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 97d656db3e828ef3377b927395a283fe995bb8a4
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389297"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Usar una configuración personalizada para dispositivos Windows Phone 8.1 en Intune

Con Microsoft Intune, puede agregar o crear una configuración personalizada para los dispositivos Windows Phone 8.1 mediante "perfiles personalizados". Los perfiles personalizados son una característica de Intune diseñada para agregar una configuración de dispositivo y características que no están integradas Intune.

Los perfiles personalizados de Windows Phone 8.1 usan la configuración OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) para configurar diferentes características. Esta configuración la suelen usar los fabricantes de dispositivos móviles para controlar las características en el dispositivo. [Documentación de Windows Phone 8.1 MDM protocol](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10)) se muestra la configuración.

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

En el ejemplo siguiente, los dispositivos de Windows 8.1 phone impedir que cambien las redes celulares cuando viaja fuera del área de cobertura del operador.

- **Nombre**: permitir itinerancia de datos móviles
- **Descripción**: habilita o deshabilita la itinerancia de datos móviles
- **Configuración de OMA-URI** (distingue mayúsculas de minúsculas): ./Vendor/MSFT/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **Tipo de datos:** entero
- **Valor**: 0

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md).

Vea cómo crear un perfil personalizado en [Dispositivos Windows 10](custom-settings-windows-10.md).
