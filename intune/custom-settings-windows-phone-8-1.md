---
title: "Configuración personalizada de Intune para dispositivos Windows Phone 8.1"
titleSuffix: Azure portal
description: "Conozca la configuración que puede usar en un perfil personalizado de Windows Phone 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 21c55041-3821-4a62-9f85-855b97dba269
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bbe76f454575d9f09617b12e3811b0c7d5a75ca1
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="custom-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Configuración personalizada para dispositivos Windows Phone 8.1 en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use el perfil **Personalizado** de Windows Phone 8.1 para Microsoft Intune para asignar la configuración OMA-URI que se puede usar para controlar características de dispositivos Windows Phone 8.1. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad tiene como fin permitirle asignar opciones de configuración que no se pueden definir con otras directivas de Intune.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Configuración de directiva personalizada para dispositivos Windows Phone 8.1

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
2. En la hoja **Create Profile** (Crear perfil), elija **Configuración** para agregar uno o varios valores de configuración de OMA-URI.
3. En la hoja **Add Row** (Agregar fila), configure los siguientes valores para cada opción:
    - **Nombre**: escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.
    - **Descripción**: proporcione una descripción que ofrezca información general del valor y otra información relacionada que le ayude a encontrarlo.
    - **OMA-URI**: especifique la configuración OMA-URI para la que quiere suministrar un valor.
    - **Tipo de datos**: seleccione el tipo de datos en el que especificará este valor OMA-URI. Elija entre **Cadena**, **fecha y hora**, **Entero**, **Punto flotante** o **Booleano**.
    - **Valor**: escriba el valor que quiere asociar con la configuración OMA-URI especificada.

4. Haga clic en **Aceptar** cuando haya terminado y luego siga agregando más valores según sea necesario.
