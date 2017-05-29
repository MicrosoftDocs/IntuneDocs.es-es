---
title: "Configuración personalizada de Intune para dispositivos Windows Phone 8.1"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca la configuración que puede usar en un perfil personalizado de Windows Phone 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 21c55041-3821-4a62-9f85-855b97dba269
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 646d0ec4274e068487ad9546ff0b5dabfc815e46
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="custom-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Configuración personalizada para dispositivos Windows Phone 8.1 en Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

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

