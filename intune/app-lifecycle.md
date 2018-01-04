---
title: "Información general sobre el ciclo de vida de la aplicación de Intune"
description: "Obtenga información acerca del ciclo de vida de aplicaciones que administra Intune, desde su incorporación hasta la retirada final."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1e50e3af525be48bf058dd32bfb7b93508d500a3
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="overview-of-the-app-lifecycle"></a>Información general sobre el ciclo de vida de la aplicación

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

El ciclo de vida de la aplicación de Intune empieza cuando se agrega una aplicación, se extiende a través de otras fases y termina cuando se quita.

![El ciclo de vida de la aplicación](./media/app-lifecycle.png "el ciclo de vida de la aplicación de Intune")

## <a name="add"></a>Agregar

El primer paso en la implementación de la aplicación es agregar a Intune las aplicaciones que quiere administrar y asignar. Aunque hay muchos tipos diferentes de aplicaciones con las que puede trabajar, los procedimientos básicos son los mismos. Con Intune, puede agregar aplicaciones para [dispositivos inscritos](apps-add.md) ([portal clásico](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)) y para [equipos con Windows administrados con el software cliente de Intune](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune).

## <a name="deploy"></a>Implementar

Después de agregar la aplicación a Intune, puede [asignarla a usuarios y dispositivos que administre](apps-deploy.md) ([portal clásico](/intune-classic/deploy-use/deploy-apps)). Intune facilita este proceso. Después de implementar la aplicación, puede [supervisar el éxito](apps-monitor.md) ([portal clásico](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune)) de la implementación desde la consola de administración de Intune. Además, en algunas tiendas de aplicaciones, como las de [Apple](vpp-apps-ios.md) ([portal clásico](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)) y [Windows](windows-store-for-business.md) ([portal clásico](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)), puede comprar licencias de aplicación en masa para la empresa. Intune puede sincronizar datos con estas tiendas para permitirle implementar y realizar un seguimiento del uso de licencias de estos tipos de aplicaciones directamente desde la consola de administración de Intune.

## <a name="configure"></a>Configurar

Como parte del ciclo de vida de la aplicación, periódicamente se publican nuevas versiones de aplicaciones. Intune proporciona herramientas para [actualizar aplicaciones](apps-add.md) ([portal clásico](/intune-classic/deploy-use/update-apps-using-microsoft-intune)) que haya implementado en una versión más reciente con facilidad. Además, puede configurar funcionalidad adicional para algunas aplicaciones, como:
- Las [directivas de configuración de aplicaciones iOS](app-configuration-policies-use-ios.md) ([portal clásico](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)) proporcionan valores para aplicaciones iOS compatibles que se usan cuando se ejecuta la aplicación. Por ejemplo, es posible que una aplicación necesite una configuración de marca concreta o el nombre de un servidor al que conectarse.
- Las [directivas de Managed Browser](app-configuration-managed-browser.md) ([portal clásico](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)) ayudan a configurar los valores de Intune Managed Browser que reemplaza al explorador de dispositivos predeterminado y que permite restringir los sitios web que pueden visitar los usuarios.

## <a name="protect"></a>Proteger

Intune ofrece muchas maneras de ayudar a proteger los datos de las aplicaciones. Los métodos principales son:
- El [acceso condicional](conditional-access.md) ([portal clásico](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)) controla el acceso al correo electrónico y otros servicios en función de las condiciones especificadas. Dichas condiciones incluyen tipos de dispositivos o el cumplimiento de una [directiva de cumplimiento de dispositivos](device-compliance.md) ([portal clásico](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)) que haya implementado.
- Las [directivas de protección de aplicaciones](app-protection-policy.md) ([portal clásico](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)) funcionan con aplicaciones individuales para ayudar a proteger los datos empresariales que usan. Por ejemplo, puede restringir la copia de datos entre las aplicaciones no administradas y las aplicaciones que administre o evitar que las aplicaciones se ejecuten en dispositivos con jailbreak o rooting.

## <a name="retire"></a>Retirar

Por último, es probable que las aplicaciones que haya implementado queden obsoletas y tengan que quitarse. Intune facilita la [retirada de aplicaciones del servicio](device-management.md) ([portal clásico](/intune-classic/deploy-use/retire-apps-using-microsoft-intune)).
