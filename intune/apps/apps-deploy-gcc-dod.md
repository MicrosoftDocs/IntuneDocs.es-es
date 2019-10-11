---
title: Aplicaciones para entornos GCC High y DoD
titleSuffix: Microsoft Intune
description: Obtenga información sobre las aplicaciones que implican entornos GCC High y DoD mediante el uso de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4d414899b6146afbe2c5ac119193fe0e59aa719b
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71939974"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Implementación de aplicaciones mediante Intune en los entornos GCC High y DoD 

Los administradores de inquilinos pueden usar Microsoft Intune para distribuir aplicaciones a los recursos. Los recursos son los empleados de la empresa, es decir, los usuarios de las aplicaciones. Hay muchos tipos de aplicaciones que se pueden implementar desde Intune en entornos GCC High o DoD. Si un administrador tiene que cargar y distribuir una aplicación Windows destinada a una audiencia de GCC High o DoD personalizada, creada por otros fabricantes o como una aplicación sin conexión descargada de [Microsoft Store para Empresas](https://businessstore.microsoft.com/store), el administrador puede optar por distribuirla como una [aplicación de línea de negocio](apps-add.md#app-types-in-microsoft-intune).  

> [!NOTE]
> En el caso de los entornos comerciales, un administrador de inquilinos puede sincronizar su instancia de Microsoft Store para Empresas con Intune, pero este servicio no está disponible para entornos GCC High y DoD. Los administradores que se encuentren en esta situación deben cargar la aplicación directamente en Intune para implementarla.  

## <a name="add-line-of-business-apps-using-intune"></a>Adición de aplicaciones de línea de negocio con Intune 

Para agregar una aplicación de línea de negocio destinada a un entorno GCC High o DoD mediante Intune, puede seguir las instrucciones de la [aplicación de línea de negocio de Windows](lob-apps-windows.md). Puede implementar primero el Portal de empresa desde Microsoft Store para Empresas. Si decide usar el Portal de empresa, puede instalarlo e implementarlo manualmente. Para obtener más información, vea [Configuración de la aplicación Portal de empresa de Microsoft Intune](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Distribución de aplicaciones sin conexión desde Microsoft Store para Empresas con Intune  

Si necesita [descargar una aplicación con licencia sin conexión](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) desde Microsoft Store para Empresas, siga estos pasos: 

1. Inicie sesión en [Microsoft Store para Empresas](https://businessstore.microsoft.com/).
2. Seleccione **Administrar** > **Configuración**.
3. En **Shopping Experience** (Experiencia de compra), establezca **Show offline apps** (Mostrar aplicaciones sin conexión) en **Activado**.

Cuando vaya a comprar una aplicación, si hay disponible una versión sin conexión, podrá cambiar el tipo de licencia a sin conexión. Una vez que haya obtenido la aplicación, podrá administrarla si selecciona **Administrar** > **Productos y servicios** en [Microsoft Store para Empresas](https://businessstore.microsoft.com/). Además, puede descargar la aplicación y sus dependencias. Después, puede implementar la aplicación descargada (y sus dependencias) en los usuarios con Intune.  

## <a name="syncing-intune-to-the-store-for-business"></a>Sincronización de Intune con Microsoft Store para Empresas 

En un entorno comercial (que no sea de la Administración Pública), un administrador puede sincronizar Intune con Microsoft Store para Empresas. Esta característica no está disponible en los entornos de la Administración Pública. Para obtener más información sobre las diferencias entre Intune en entornos comerciales e Intune para entornos de la Administración Pública, vea [Descripción del servicio Enterprise Mobility + Security para el gobierno de EE. UU.](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description)  

Para sincronizar Intune con su cuenta de Microsoft Store para Empresas, vea [Cómo administrar las aplicaciones adquiridas a través de la Microsoft Store para Empresas con Microsoft Intune](windows-store-for-business.md).  

## <a name="compliance"></a>Cumplimiento 

Revise las declaraciones de privacidad y cumplimiento de las aplicaciones y compárelas con los requisitos de cumplimiento, seguridad y privacidad de su organización al evaluar el uso adecuado de estos servicios.   

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre cómo implementar y asignar aplicaciones, vea [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

 
