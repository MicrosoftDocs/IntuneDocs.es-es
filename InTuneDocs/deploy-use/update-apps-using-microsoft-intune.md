---
title: Actualizar aplicaciones | Microsoft Intune
description: "Use la información de este tema para entender cómo actualizar aplicaciones cuando se requiere una versión nueva."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: e78642494356038d4dff259ca54030122fd90819


---

# Actualizar aplicaciones con Microsoft Intune
Microsoft Intune puede ayudarle a administrar actualizaciones de aplicaciones. Use la información de este tema para entender cómo actualizar aplicaciones cuando se requiere una versión nueva.

## Actualizar aplicaciones
Cuando se lanza una nueva versión de una aplicación que ha implementado, Intune le permite actualizar e implementar la versión más reciente de la aplicación. Una implementación solo se puede reemplazar por una versión más reciente de la misma aplicación (que tenga el mismo identificador). No se pueden usar las actualizaciones de aplicaciones para actualizar una implementación con un paquete de la aplicación diferente.

### Identificadores de aplicación
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

### Para actualizar una aplicación

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Aplicaciones** &gt; **Aplicaciones**.

2.  En la lista **Aplicaciones**, seleccione la aplicación que quiere actualizar y luego **Editar**.

3.  En el asistente **Editar software** , proporcione los detalles nuevos del paquete de la aplicación.

4.  Cuando termine, seleccione **Actualizar**.

Cuando los dispositivos comprueben posteriormente si hay aplicaciones disponibles, la aplicación se actualizará automáticamente a la última versión.
En el caso de las aplicaciones instaladas desde un paquete de aplicaciones (aplicaciones de línea de negocio), la aplicación se actualizará automáticamente tanto para implementaciones obligatorias como disponibles, siempre y cuando la aplicación tenga el mismo identificador.

En el caso de las aplicaciones implementadas como un vínculo a un almacén, el almacén del que procede la aplicación administra la actualización.



<!--HONumber=Oct16_HO4-->


