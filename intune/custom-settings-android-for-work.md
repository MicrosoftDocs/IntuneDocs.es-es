---
title: 'Agregar una configuración personalizada para dispositivos Android Enterprise en Microsoft Intune: Azure | Microsoft Docs'
description: Agregar o crear un perfil personalizado para dispositivos Android Enterprise en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a622264ed7cc091849bacbd02f8ae7bdb33603fe
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983149"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Uso de una configuración personalizada para dispositivos Android Enterprise en Microsoft Intune

Con Microsoft Intune, puede agregar o crear una configuración personalizada para los dispositivos Android Enterprise mediante un "perfil personalizado". Los perfiles personalizados son una característica de Intune diseñada para agregar una configuración de dispositivo y características que no están integradas Intune.

Los perfiles personalizados de Android Enterprise usan la configuración OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) para controlar las características en dispositivos Android. Esta configuración la suelen usar los fabricantes de dispositivos móviles para controlar estas características.

Intune admite un número limitado de perfiles personalizados de Android.

En este artículo se muestra cómo crear un perfil personalizado para dispositivos Android Enterprise. También se proporciona un ejemplo de un perfil personalizado que bloquea las acciones de copiar y pegar.

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre para el perfil, como `android enterprise custom profile`.
    - **Descripción**: escriba una descripción para el perfil.
    - **Plataforma**: seleccione **Android Enterprise**.
    - **Tipo de perfil**: elija **Personalizado**.

4. En **Configuración OMA-URI personalizada**, seleccione **Agregar**. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre único para la configuración OMA-URI, de modo que pueda encontrarla fácilmente.
    - **Descripción**: escriba una descripción con información general sobre la configuración y otros detalles importantes.
    - **OMA-URI**: escriba la configuración OMA-URI que quiere usar.
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

En este ejemplo, creará un perfil personalizado que restringe las acciones de copiar y pegar entre aplicaciones profesionales y aplicaciones personales en dispositivos Android Enterprise.

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre para el perfil, como `android ent block copy paste custom profile`.
    - **Descripción**: escriba una descripción para el perfil
    - **Plataforma**: seleccione **Android Enterprise**.
    - **Tipo de perfil**: elija **Personalizado**.

4. En **Configuración OMA-URI personalizada**, seleccione **Agregar**. Escriba los valores siguientes:

    - **Nombre**: escriba algo parecido a `Block copy and paste`.
    - **Descripción**: escriba algo parecido a `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: escriba `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Tipo de datos**: elija **booleano** para que el valor de esta configuración OMA-URI sea **True** o **False**.
    - **Valor**: elija **True**.

5. Después de especificar la configuración, el entorno debería tener un aspecto similar a la imagen siguiente:

    ![Bloquee las acciones de copiar y pegar para un perfil de trabajo Android.](./media/custom-policy-afw-copy-paste.png)

Cuando asigna este perfil a los dispositivos Android Enterprise que administra, las acciones de copiar y pegar estarán bloqueadas entre las aplicaciones de los perfiles profesional y personal.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md).

Vea cómo [crear el perfil en dispositivos Android](custom-settings-android.md).