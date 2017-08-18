---
title: "Configuración personalizada de Intune para dispositivos Android"
titleSuffix: Intune on Azure
description: "Conozca la configuración que puede usar en un perfil personalizado de Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45a3a8fe4960cc1bb8c5f2150f57d34d59c08e0a
ms.sourcegitcommit: 1c71fff769ca0097faf46fc2b58b953ff28386e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2017
---
# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Opciones de configuración personalizadas para dispositivos Android en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use el perfil **personalizado** de Android de Microsoft Intune para asignar la configuración de OMA-URI que se puede usar para controlar características en dispositivos Android. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad está pensada para que se puedan asignar las opciones de configuración de Android que no se pueden definir con directivas de Intune.

## <a name="custom-profile-settings-for-android-devices"></a>Configuración personalizada de perfiles para dispositivos Android

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](custom-settings-configure.md) para comenzar.
2. En la hoja **Create Profile** (Crear perfil), elija **Configuración** para agregar uno o varios valores de configuración de OMA-URI.
3. En la hoja **Editar fila**, configure los siguientes valores para cada opción:
    - **Nombre**: escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.
    - **Descripción**: proporcione una descripción que ofrezca información general del valor y otra información relacionada que le ayude a encontrarlo.
    - **Tipo de datos**: seleccione el tipo de datos en el que especificará este valor OMA-URI. Elija entre **Cadena**, **Cadena (XML)**, **Fecha y hora**, **Entero**, **Punto flotante** o **Booleano**.
    - **OMA-URI**: especifique la configuración OMA-URI para la que quiere suministrar un valor.
    - **Valor**: escriba el valor que quiere asociar con la configuración OMA-URI especificada.
4. Haga clic en **Aceptar** cuando haya terminado y luego siga agregando más valores según sea necesario.

## <a name="next-steps"></a>Pasos siguientes

Cuando finalice la configuración, el perfil se creará y aparecerá en la hoja de la lista de perfiles. Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

Para obtener ejemplos de configuraciones personalizadas que puede usar, vea:

- [Uso de un perfil de dispositivo personalizado de Microsoft Intune para crear un perfil de Wi-Fi con una clave precompartida](/intune/wi-fi-profile-shared-key)
- [Uso de un perfil personalizado de Microsoft Intune para crear un perfil de VPN por aplicación para dispositivos Android](/intune/android-pulse-secure-per-app-vpn)
- [Uso de directivas personalizadas para permitir y bloquear aplicaciones para dispositivos Samsung KNOX Standard en Microsoft Intune](/intune/samsung-knox-apps-allow-block)
