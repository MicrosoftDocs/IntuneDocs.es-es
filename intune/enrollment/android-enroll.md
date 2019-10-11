---
title: Inscribir dispositivos Android en Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo inscribir dispositivos Android en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a9de31ce7a08edcb7dddc6a65a061c1883021e4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723598"
---
# <a name="enroll-android-devices"></a>Inscripción de dispositivos Android

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Como Administrador del servicio Intune, puede inscribir dispositivos Android de las siguientes maneras:
- Android Enterprise (ofrece un conjunto de opciones de inscripción que proporcionan a los usuarios las características más actualizadas y seguras):
    - [**Perfil de trabajo de Android Enterprise**](android-work-profile-enroll.md): Para dispositivos personales que tienen permiso para acceder a datos corporativos. Los administradores pueden administrar las cuentas de trabajo, las aplicaciones y los datos. Los datos personales del dispositivo se mantienen separados de los datos de trabajo y los administradores no tienen control sobre la configuración o los datos personales. 
    - [**Android Enterprise dedicado**](android-kiosk-enroll.md): Para dispositivos de propiedad corporativa de uso único, como señalización digital, impresión de vales o administración de inventario. Los administradores bloquean el uso de un dispositivo para un conjunto limitado de aplicaciones y vínculos web. También impide que los usuarios agreguen otras aplicaciones o lleven a cabo otras acciones en el dispositivo.
    - [**Android Enterprise totalmente administrado**](android-fully-managed-enroll.md): Para dispositivos de propiedad corporativa de usuario único, que se usan exclusivamente para trabajo y no para uso personal. Los administradores pueden administrar todo el dispositivo y aplicar controles de directiva que no están disponibles para perfiles de trabajo. 
- [**Administrador de dispositivos Android**](android-enroll-device-administrator.md), incluidos los dispositivos Samsung Knox Standard y los [dispositivos Zebra](../configuration/android-zebra-mx-overview.md). 

## <a name="prerequisites"></a>Requisitos previos

Para prepararse para administrar dispositivos móviles, debe establecer la entidad de administración de dispositivos móviles (MDM) en **Microsoft Intune**. Para obtener instrucciones, consulte [Set the MDM authority](../fundamentals/mdm-authority-set.md) (Establecimiento de la autoridad de MDM). Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles.

En el caso de los dispositivos fabricados por Zebra Technologies, puede que haya que conceder permisos adicionales en el Portal de empresa según las funcionalidades del dispositivo específico. En el artículo sobre [Mobility Extensions en dispositivos Zebra](../configuration/android-zebra-mx-overview.md) se incluye más información.

En el caso de los dispositivos Samsung Knox Standard, existen [más requisitos previos](android-samsung-knox-mobile-enroll.md).

## <a name="next-steps"></a>Pasos siguientes

- [Configure la inscripción de dispositivos de perfil de trabajo Android Enterprise](android-work-profile-enroll.md)
- [Configuración de la inscripción en Intune de dispositivos dedicados de Android Enterprise](android-kiosk-enroll.md)
- [Configuración de la inscripción en Intune de dispositivos Android Enterprise totalmente administrados](android-fully-managed-enroll.md)
- [Configuración de la inscripción del administrador de dispositivos Android](android-enroll-device-administrator.md)

