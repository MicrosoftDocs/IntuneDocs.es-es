---
title: Inscripción del administrador de dispositivos Android en Microsoft Intune
titleSuffix: ''
description: Inscriba dispositivos Android en Intune mediante la inscripción del administrador de dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1dc495e6356a35215943415e03a46496a72bddf1
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071043"
---
# <a name="android-device-administrator-enrollment"></a>Inscripción del administrador de dispositivos Android

El administrador de dispositivos Android (que a veces se conoce como administración de Android "heredada" y publicada con Android 2.2) es una manera de administrar dispositivos Android. Sin embargo, ahora hay una funcionalidad de administración mejorada disponible con [Android Enterprise](https://www.android.com/enterprise/management/) (publicada con Android 5.0). Con el fin de realizar la transición a la administración de dispositivos moderna, más completa y segura, Google va a reducir la compatibilidad con el administrador de dispositivos en las nuevas versiones de Android.

Por lo tanto, para evitar esta funcionalidad reducida, se recomienda dejar de inscribir los nuevos dispositivos con el proceso del administrador de dispositivos que se describe a continuación.

Por las mismas razones, también se recomienda migrar los dispositivos desde la administración del administrador de dispositivos si los dispositivos van a actualizarse a Android 10. 

Para más información sobre la compatibilidad de Intune con el administrador de dispositivos, consulte la [sección de avisos](whats-new.md#decreasing-support-for-android-device-administrator).

Si, a pesar de todo, prefiere que los usuarios inscriban sus dispositivos Android con la administración del administrador de dispositivos, continúe con la siguiente sección.  


> [!Note]  
> Android 10 y versiones posteriores no se admitirán en la administración de dispositivos móviles híbrida (MDM híbrida; Intune administrado con la consola de System Center Configuration Manager) porque la MDM híbrida va a dejar de funcionar a partir del 1 de septiembre de 2019. Si aún usa la MDM híbrida, debe migrar a Intune independiente lo antes posible. Si necesita ayuda para la migración, póngase en contacto con el soporte técnico. Para más información, vea [Move from Hybrid Mobile Device Management to Intune on Azure](https://aka.ms/hybrid_notification) (Pasar de la administración híbrida de dispositivos móviles (MDM) a Intune en Azure).

Para más información sobre las características de Android Enterprise de Google, consulte estos artículos:
- [Guía de Google para la migración desde el administrador de dispositivos a Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentación de Google sobre el plan para dejar de usar la API del administrador de dispositivos](https://developers.google.com/android/work/device-admin-deprecation)


## <a name="set-up-device-administrator-enrollment"></a>Configuración de la inscripción del administrador de dispositivos

De forma predeterminada, Intune permite la inscripción de dispositivos Android con funcionalidades de administrador de dispositivos.

1. Para prepararse para administrar dispositivos móviles, debe establecer la entidad de administración de dispositivos móviles (MDM) en **Microsoft Intune**. Para obtener instrucciones, consulte [Set the MDM authority](mdm-authority-set.md) (Establecimiento de la autoridad de MDM). Este elemento solo se establece una vez, la primera vez que configura Intune para la administración de dispositivos móviles.
2. [Indique a los usuarios cómo deben inscribir sus dispositivos](/intune-user-help/enroll-your-device-in-intune-android).  

Después de que un usuario se haya inscrito, puede empezar a administrar sus dispositivos en Intune, que incluye la [asignación de directivas de cumplimiento de normas](compliance-policy-create-android.md), la [administración de aplicaciones](app-management.md) y mucho más.

Para más información sobre otras tareas de usuario final, vea estos artículos:
- [Recursos sobre la experiencia del usuario final con Microsoft Intune](end-user-educate.md)
- [Uso de un dispositivo Android con Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)


## <a name="block-device-administrator-enrollment"></a>Bloqueo de la inscripción del administrador de dispositivos Android
Para impedir la inscripción de los dispositivos del administrador de dispositivos Android, o solo de aquellos de propiedad personal, consulte [Establecer restricciones de tipo de dispositivo](enrollment-restrictions-set.md).



## <a name="next-steps"></a>Pasos siguientes
- [Asignación de directivas de cumplimiento](compliance-policy-create-android.md)
- [Administración de aplicaciones](app-management.md)