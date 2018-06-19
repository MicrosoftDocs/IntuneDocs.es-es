---
title: 'Agregar una configuración personalizada para dispositivos Android en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o cree un perfil personalizado para dispositivos Android para crear un perfil de Wi-Fi con una clave precompartida, cree un perfil de VPN por aplicación o bien permita o bloquee aplicaciones para dispositivos Samsung Knox Standard en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0195e138b59fae019fa2bc02aadf211257a65cac
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022057"
---
# <a name="custom-settings-for-android-devices---intune"></a>Configuración personalizada para dispositivos Android: Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Los perfiles personalizados usan la configuración OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) para configurar diferentes características en dispositivos Android. Esta configuración la suelen usar los fabricantes de dispositivos móviles para controlar las características en el dispositivo.

Si usa un perfil personalizado, puede configurar y asignar los siguientes valores de Android. Esta configuración no está integrada en las directivas de Intune:

- [Crear un perfil de Wi-Fi con una clave precompartida](/intune/wi-fi-profile-shared-key)
- [Creación de un perfil de VPN por aplicación](/intune/android-pulse-secure-per-app-vpn)
- [Uso de directivas personalizadas para permitir y bloquear aplicaciones para dispositivos Samsung Knox Standard](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Este tipo de perfil solo puede configurar los valores enumerados. Los dispositivos Android no exponen una lista completa de opciones de OMA-URI que pueda configurar. Si quiere ver más valores, vote por ellos en el [sitio de Uservoice de Intune](https://microsoftintune.uservoice.com/forums/291681-ideas).

## <a name="custom-profile-settings-for-android-devices"></a>Configuración personalizada de perfiles para dispositivos Android

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com). 
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Cree un perfil personalizado con la plataforma Android. En [Configuración personalizada de dispositivos en Microsoft Intune](custom-settings-configure.md) se muestran los pasos.
4. En **Configuración OMA-URI personalizada**, seleccione **Agregar** y, luego, **Agregar fila**.
5. Introduzca las siguientes propiedades:

   - **Nombre**: escriba un nombre único para la configuración OMA-URI para que pueda encontrarla fácilmente.
   - **Descripción**: escriba una descripción que ofrezca información general sobre la configuración y otros detalles importantes.
   - **Tipo de datos**: especifique el tipo de datos que se usará para esta configuración OMA-URI. Elija entre **Cadena**, **Cadena (XML)**, **Fecha y hora**, **Entero**, **Punto flotante** o **Booleano**.
   - **OMA-URI**: especifique el OMA-URI que quiera.
   - **Valor**: escriba el valor que quiere asociar con la configuración OMA-URI especificada.

6. Haga clic en **Aceptar** para guardar los cambios. Continúe agregando más valores según sea necesario.

## <a name="next-steps"></a>Pasos siguientes

Cuando finalice la configuración, se crea el perfil y aparece en la lista. Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).
