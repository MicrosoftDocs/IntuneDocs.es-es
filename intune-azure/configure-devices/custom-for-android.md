---
title: "Configuración personalizada de Intune para dispositivos Android | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: conozca la configuración que puede usar en un perfil personalizado de Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: 3a80a69a27b540b66fb96e098c0b0f66a0854297


---

# <a name="custom-settings-for-android-devices-in-intune-azure-preview"></a>Configuración personalizada para dispositivos Android en la versión preliminar de Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use el perfil **Personalizado** de Android de Microsoft Intune para implementar la configuración de OMA-URI que se puede usar para controlar características en dispositivos Android. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta capacidad está pensada para que se puedan implementar las opciones de configuración de Android que no se pueden definir con directivas de Intune.

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



<!--HONumber=Feb17_HO1-->


