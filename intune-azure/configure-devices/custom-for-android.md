---
title: "Configuración personalizada de Intune para dispositivos Android"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca la configuración que puede usar en un perfil personalizado de Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: a9748a0ad6b9bbe10e36ba133ba74edb6aa6e09a
ms.openlocfilehash: 0ac1a6eeca125261f44607bbbb76b04253d5270e
ms.contentlocale: es-es
ms.lasthandoff: 05/05/2017


---

# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Opciones de configuración personalizadas para dispositivos Android en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use el perfil **personalizado** de Android de Microsoft Intune para asignar la configuración de OMA-URI que se puede usar para controlar características en dispositivos Android. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad está pensada para que se puedan asignar las opciones de configuración de Android que no se pueden definir con directivas de Intune.

## <a name="custom-profile-settings-for-android-devices"></a>Configuración personalizada de perfiles para dispositivos Android

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](how-to-configure-custom-settings.md) para comenzar.
2. En la hoja **Create Profile** (Crear perfil), elija **Configuración** para agregar uno o varios valores de configuración de OMA-URI.
3. En la hoja **Editar fila**, configure los siguientes valores para cada opción:
    - **Nombre**: escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.
    - **Descripción**: proporcione una descripción que ofrezca información general del valor y otra información relacionada que le ayude a encontrarlo.
    - **Tipo de datos**: seleccione el tipo de datos en el que especificará este valor OMA-URI. Elija entre **Cadena**, **Cadena (XML)**, **Fecha y hora**, **Entero**, **Punto flotante** o **Booleano**.
    - **OMA-URI**: especifique la configuración OMA-URI para la que quiere suministrar un valor.
    - **Valor**: escriba el valor que quiere asociar con la configuración OMA-URI especificada.
4. Haga clic en **Aceptar** cuando haya terminado y luego siga agregando más valores según sea necesario.

