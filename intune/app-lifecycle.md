---
title: Información general sobre el ciclo de vida de la aplicación para Microsoft Intune
description: Obtenga información sobre el ciclo de vida de las aplicaciones administradas en Microsoft Intune. El ciclo de vida de la aplicación implica agregar, implementar, configurar, proteger y retirar aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.openlocfilehash: a23f5fb9e05cf9a7fe46456b642aef76b6a79b70
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183118"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Información general sobre el ciclo de vida de la aplicación en Microsoft Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

El ciclo de vida de la aplicación de Microsoft Intune empieza cuando se agrega una aplicación, se extiende a través de otras fases y termina cuando se quita. Al comprender estas fases, tendrá los detalles que necesita para empezar a trabajar con la administración de aplicaciones de Intune.

![El ciclo de vida de la aplicación](./media/app-lifecycle.png "el ciclo de vida de la aplicación de Intune")

## <a name="add"></a>Agregar

El primer paso en la implementación de la aplicación es agregar a Intune las aplicaciones que quiere administrar y asignar. Aunque hay muchos tipos diferentes de aplicaciones con las que puede trabajar, los procedimientos básicos son los mismos. Con Intune puede agregar tipos diferentes de aplicaciones, incluidas aplicaciones escritas internamente (línea de negocio), aplicaciones de la tienda, aplicaciones integradas y aplicaciones en la web. Para obtener más información sobre estos tipos de aplicaciones, consulte [Agregar una aplicación a Microsoft Intune](apps-add.md). 

## <a name="deploy"></a>Implementar

Después de agregar la aplicación a Intune, puede [asignarla a usuarios y dispositivos que administre](apps-deploy.md). Intune facilita este proceso y, después de implementar la aplicación, puede [supervisar que la implementación se haya realizado correctamente](apps-monitor.md) desde Intune en Azure Portal. Además, en algunas tiendas de aplicaciones, como el [App Store de Apple](vpp-apps-ios.md) y la [Tienda de aplicaciones Windows](windows-store-for-business.md), puede comprar licencias de aplicación en masa para la empresa. Intune puede sincronizar datos con estas tiendas para permitirle implementar y realizar un seguimiento del uso de licencias de estos tipos de aplicaciones directamente desde la consola de administración de Intune.

## <a name="configure"></a>Configurar

Como parte del ciclo de vida de la aplicación, periódicamente se publican nuevas versiones de aplicaciones. Intune proporciona herramientas para [actualizar aplicaciones](apps-add.md) que haya implementado en una versión más reciente con facilidad. Además, puede configurar funcionalidad adicional para algunas aplicaciones, como:
- Las [directivas de configuración de aplicaciones iOS](app-configuration-policies-use-ios.md) proporcionan valores para aplicaciones iOS compatibles que se usan cuando se ejecuta la aplicación. Por ejemplo, es posible que una aplicación necesite una configuración de marca concreta o el nombre de un servidor al que se debe conectar.
- Las [directivas de explorador administrado](app-configuration-managed-browser.md) ayudan a configurar los valores del explorador administrado de Intune que reemplaza al explorador de dispositivos predeterminado y que permite restringir los sitios web que pueden visitar los usuarios.

## <a name="protect"></a>Proteger

Intune ofrece muchas maneras de ayudar a proteger los datos de las aplicaciones. Los métodos principales son:
- El [acceso condicional](conditional-access.md), que controla el acceso al correo electrónico y otros servicios en función de las condiciones que especifique. Dichas condiciones incluyen tipos de dispositivos o el cumplimiento de una [directiva de cumplimiento de dispositivos](device-compliance.md) que haya implementado.
- Las [directivas de protección de aplicaciones](app-protection-policy.md) funcionan con aplicaciones individuales para ayudar a proteger los datos empresariales que usan. Por ejemplo, puede restringir la copia de datos entre las aplicaciones no administradas y las aplicaciones que administre o evitar que las aplicaciones se ejecuten en dispositivos con jailbreak o rooting.

## <a name="retire"></a>Retirar

Por último, es probable que las aplicaciones que haya implementado queden obsoletas y tengan que quitarse. Intune facilita la [retirada de aplicaciones del servicio](device-management.md).

## <a name="next-steps"></a>Pasos siguientes:

- Obtenga información sobre la [administración de aplicaciones de Microsoft Intune](app-management.md)