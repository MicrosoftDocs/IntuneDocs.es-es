---
title: Actualizar aplicaciones
description: "Use la información de este tema para entender cómo actualizar aplicaciones cuando se requiere una versión nueva."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b89b087c13847af06187cf3b6a046b9730a07826
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2018
---
# <a name="update-apps-using-microsoft-intune"></a>Actualizar aplicaciones con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune puede ayudarle a administrar actualizaciones de aplicaciones. Use la información de este tema para entender cómo actualizar aplicaciones cuando se requiere una versión nueva.

## <a name="how-to-update-apps"></a>Actualizar aplicaciones
Cuando se lanza una nueva versión de una aplicación que ha implementado, Intune le permite actualizar e implementar la versión más reciente de la aplicación. Una implementación solo se puede reemplazar por una versión más reciente de la misma aplicación (que tenga el mismo identificador). No se pueden usar las actualizaciones de aplicaciones para actualizar una implementación con un paquete de la aplicación diferente.

### <a name="app-identifiers"></a>Identificadores de aplicación
El identificador de la aplicación es una propiedad que identifica de forma única una aplicación. No puede instalar varias copias de una aplicación con el mismo identificador. A continuación, se proporcionan algunos ejemplos de identificadores de aplicación:

- **iOS** - Identificador de agrupación (por ejemplo: com.microsoft.excel)
- **Android** - Identificador de paquete (por ejemplo: com.microsoft.excel)
- **Windows Phone** - (instalador xap); use el id. del producto (GUID)
- **Windows** - (appx/appxbundle); use el nombre completo del paquete



> [!IMPORTANT]
> Si implementa una aplicación con la acción de implementación **Instalación requerida** y posteriormente cambia la acción de implementación a **Instalación disponible**, las actualizaciones de la aplicación no se instalan automáticamente en los dispositivos que instalaron la aplicación antes de que se realizara el cambio de implementación. Para corregir este problema, puede hacer lo siguiente:
>
> -   Indique al usuario del dispositivo que vaya al Portal de empresa, seleccione la aplicación instalada y, luego, elija **Instalar**.
> -   Cambie la acción de implementación a **Desinstalar**y, una vez desinstalada la aplicación, vuelva a implementar la aplicación con la acción de implementación **Instalación disponible**.

### <a name="to-update-an-app"></a>Para actualizar una aplicación

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Aplicaciones** &gt; **Aplicaciones**.

2.  En la lista **Aplicaciones**, seleccione la aplicación que quiere actualizar y luego **Editar**.

3.  En el asistente **Editar software** , proporcione los detalles nuevos del paquete de la aplicación.

4.  Cuando termine, seleccione **Actualizar**.

Cuando los dispositivos comprueben posteriormente si hay aplicaciones disponibles, la aplicación se actualizará automáticamente a la última versión.
En el caso de las aplicaciones instaladas a partir de un paquete de aplicaciones (aplicaciones de línea de negocio), la aplicación se actualizará automáticamente tanto para las implementaciones obligatorias como las disponibles, siempre y cuando la aplicación tenga el mismo identificador.

En el caso de las aplicaciones implementadas como un vínculo a un almacén, el almacén del que procede la aplicación administra la actualización.
