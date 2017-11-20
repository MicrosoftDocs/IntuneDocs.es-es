---
title: "Directivas de configuración de aplicaciones de Intune | Microsoft Docs"
titlesuffix: Azure portal
description: "Obtenga información sobre el uso de directivas de configuración de aplicaciones para Intune."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b690f691278d0cc708ed7e586e30aee4ed6e807a
ms.sourcegitcommit: 67c037af31c1f167ec9b4f4baa754631c817e7d1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2017
---
# <a name="app-configuration-policies-for-intune"></a>Directivas de configuración de aplicaciones para Intune

Proporcione valores de configuración cuando los usuarios ejecuten una aplicación para iOS o Android con directivas de configuración de aplicaciones en Microsoft Intune. Por ejemplo, una aplicación puede requerir a los usuarios que especifiquen:

- Un número de puerto personalizado
- Configuración de idioma
- Configuración de seguridad
- Configuración de marca, como un logotipo de empresa

Si los usuarios han especificado esta configuración incorrectamente, puede aumentar la carga del departamento de soporte técnico y ralentizar la adopción de nuevas aplicaciones.

Las directivas de configuración de aplicaciones pueden ayudarle a eliminar estos problemas al permitirle asignar esta configuración a los usuarios en una directiva antes de ejecutar la aplicación. A continuación, la configuración se proporciona de forma automática y los usuarios no tienen que realizar ninguna acción.

No asigne estas directivas directamente a usuarios y dispositivos. Asocie la directiva con una aplicación y, a continuación, asigne la aplicación. La configuración de directiva se usará cada vez que la aplicación la compruebe (normalmente, la primera vez que se ejecuta).

Tiene dos opciones sobre cómo usar las configuraciones de aplicación con Intune:
 - **Dispositivos administrados**  
   El dispositivo se administra mediante Intune como el proveedor de MDM.
 - **Aplicaciones administradas**  
   Una aplicación se administra sin la inscripción de dispositivos.

## <a name="apps-that-support-app-configuration"></a>Aplicaciones que admiten la configuración de aplicaciones

Puede usar las directivas de configuración de aplicaciones en las aplicaciones que lo admitan. Para admitir la configuración de aplicaciones en Intune, las aplicaciones deben haberse escrito con ese fin. Consulte con el proveedor de su aplicación para obtener más información.

Puede preparar las aplicaciones de línea de negocio mediante la incorporación de Intune App SDK en la aplicación o mediante la encapsulación de la aplicación después de que se ha desarrollado. El SDK de aplicaciones de Intune, disponible para iOS y Android, habilita su aplicación para las directivas de protección de aplicaciones de Intune. Su objetivo es minimizar la cantidad de cambios de código que debe realizar el desarrollador de la aplicación. Para obtener más información, vea [Información general del SDK para aplicaciones de Intune](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Compatibilidad de API Graph para la configuración de aplicaciones

Además, puede usar API Graph para realizar tareas de configuración de aplicaciones. Para obtener más información, consulte la [referencia sobre API Graph para la configuración de destino de MAM](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Pasos siguientes

### <a name="managed-devices"></a>Dispositivos administrados

 - Obtenga información sobre cómo usar la configuración de aplicaciones con los dispositivos iOS.  Vea [Agregar directivas de configuración de aplicaciones para dispositivos iOS administrados](app-configuration-policies-use-ios.md).
 - Obtenga información sobre cómo usar la configuración de aplicaciones con los dispositivos Android.  Vea [Agregar directivas de configuración de aplicaciones para dispositivos Android administrados](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Aplicaciones administradas

 - Obtenga información sobre cómo usar la configuración de aplicaciones con aplicaciones administradas. Consulte [Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos](app-configuration-policies-managed-app.md).