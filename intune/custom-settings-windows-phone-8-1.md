---
title: Configuración personalizada de Microsoft Intune para dispositivos que ejecutan Windows Phone 8.1
titleSuffix: ''
description: Conozca la configuración que puede usar en un perfil personalizado de Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b21464016dff3396b25861af568fa90d8b7a260f
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-phone-81"></a>Configuración de dispositivo personalizada de Microsoft Intune para dispositivos que ejecutan Windows Phone 8.1

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use el perfil **Personalizado** de Windows Phone 8.1 para Microsoft Intune para asignar la configuración OMA-URI que se puede usar para controlar características de dispositivos Windows Phone 8.1. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad tiene como fin permitirle asignar opciones de configuración que no se pueden definir con otras directivas de Intune.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Configuración de directiva personalizada para dispositivos Windows Phone 8.1

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
2. En el panel **Configuración OMA-URI personalizada**, elija **Agregar** para agregar uno o varios valores de OMA-URI.
3. En el panel **Agregar fila**, configure los siguientes valores para cada opción:
    - **Nombre**: escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.
    - **Descripción**: proporcione una descripción que ofrezca información general del valor y otra información relacionada que le ayude a encontrarlo.
    - **OMA-URI**: especifique la configuración OMA-URI para la que quiere suministrar un valor.
    - **Tipo de datos**: seleccione el tipo de datos en el que especificar este valor OMA-URI. Elija entre **Cadena**, **Cadena (XML)**, **Fecha y hora**, **Entero**, **Punto flotante**, **Booleano** o **Base64**.
    - **Valor**: escriba el valor o el archivo que quiere asociar con la configuración OMA-URI especificada.

4. Haga clic en **Aceptar** cuando haya terminado y luego siga agregando más valores según sea necesario.
