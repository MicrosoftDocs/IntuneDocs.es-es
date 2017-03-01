---
title: "Configuración personalizada de Intune para dispositivos Windows Phone 8.1 | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: conozca la configuración que puede usar en un perfil personalizado de Windows Phone 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 21c55041-3821-4a62-9f85-855b97dba269
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: 3656db2d9828dcc16c479ba072de691848fdd23b


---

# <a name="custom-settings-for-windows-phone-81-devices-in-intune-azure-preview"></a>Configuración para dispositivos Windows Phone 8.1 en la versión preliminar de Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use el perfil **Personalizado** de Windows Phone 8.1 para Microsoft Intune para implementar la configuración OMA-URI que se puede usar para controlar características de dispositivos Windows Phone 8.1. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad tiene como fin permitirle implementar opciones de configuración que no se pueden definir con otras directivas de Intune.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Configuración de directiva personalizada para dispositivos Windows Phone 8.1

1. Siga las instrucciones que se indican en [Configuración personalizada de dispositivos de Intune](how-to-configure-custom-settings.md) para comenzar.
2. En la hoja **Create Profile** (Crear perfil), elija **Configuración** para agregar uno o varios valores de configuración de OMA-URI.
3. En la hoja **Add Row** (Agregar fila), configure los siguientes valores para cada opción:
    - **Nombre**: escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.
    - **Descripción**: proporcione una descripción que ofrezca información general del valor y otra información relacionada que le ayude a encontrarlo.
    - **OMA-URI**: especifique la configuración OMA-URI para la que quiere suministrar un valor.
    - **Tipo de datos**: seleccione el tipo de datos en el que especificará este valor OMA-URI. Elija entre **Cadena**, **fecha y hora**, **Entero**, **Punto flotante** o **Booleano**.
    - **Valor**: escriba el valor que quiere asociar con la configuración OMA-URI especificada.

4. Haga clic en **Aceptar** cuando haya terminado y luego siga agregando más valores según sea necesario.



<!--HONumber=Feb17_HO1-->

