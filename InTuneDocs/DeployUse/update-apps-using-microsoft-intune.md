---
title: Actualizar aplicaciones | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: 0581d1476fba5bedcdd4446df20f8f92b151f41b
ms.openlocfilehash: 9e5b8f4a467e8e58cc2f8fa495b5f008eee7e35b


---

# Actualizar aplicaciones con Microsoft Intune
Microsoft Intune puede ayudarle a administrar actualizaciones de aplicaciones. Use la información de este tema para entender cómo actualizar aplicaciones cuando se requiere una versión nueva.

## Actualizar aplicaciones
Cuando se lanza una nueva versión de una aplicación que haya implementado, Intune permite actualizar e implementar la versión más reciente de la aplicación. Una implementación solo se puede reemplazar por una versión más reciente de la misma aplicación (con el mismo identificador). No se pueden usar las actualizaciones de aplicaciones para actualizar una implementación con un paquete de la aplicación diferente.

> [!IMPORTANT]
> Si implementa una aplicación con la acción de implementación **Instalación requerida** y posteriormente cambia la acción de implementación a **Instalación disponible**, las actualizaciones de la aplicación no se instalan automáticamente en los dispositivos que instalaron la aplicación antes de que se realizara el cambio de implementación. Para corregir este problema, puede hacer lo siguiente:
> 
> -   Indique al usuario del dispositivo que vaya al portal de empresa, seleccione la aplicación instalada y luego **Instalar**.
> -   Cambie la acción de implementación a **Desinstalar**y, una vez desinstalada la aplicación, vuelva a implementar la aplicación con la acción de implementación **Instalación disponible**.

### Para actualizar una aplicación

1.  En la [consola de administrador de Microsoft Intune](https://manage.microsoft.com), seleccione **Aplicaciones** &gt; **Aplicaciones**.

2.  En la lista **Aplicaciones**, seleccione la aplicación que quiere actualizar y luego **Editar**.

3.  En el asistente **Editar software** , proporcione los detalles nuevos del paquete de la aplicación.

4.  Cuando termine, seleccione **Actualizar**.

Cuando los dispositivos comprueben posteriormente si hay aplicaciones disponibles, la aplicación se actualizará automáticamente a la última versión.
En el caso de las aplicaciones instaladas desde un paquete de aplicaciones (aplicaciones de línea de negocio), la aplicación se actualizará automáticamente tanto para implementaciones obligatorias como disponibles, siempre y cuando la aplicación tenga el mismo identificador.
En el caso de las aplicaciones implementadas como un vínculo a un almacén, el almacén del que procede la aplicación administra la actualización.






<!--HONumber=Jun16_HO3-->


