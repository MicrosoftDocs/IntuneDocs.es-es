---
# required metadata

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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Actualizar aplicaciones con Microsoft Intune
Microsoft Intune puede ayudarle a administrar actualizaciones de aplicaciones. Use la información de este tema para entender cómo actualizar aplicaciones cuando se requiere una versión nueva.

## Actualizar aplicaciones
Cuando se lanza una nueva versión de una aplicación que haya implementado, Intune permite actualizar e implementar la versión más reciente de la aplicación. Una implementación solo se puede reemplazar por una versión más reciente de la misma aplicación (con el mismo identificador). No se pueden usar las actualizaciones de aplicaciones para actualizar una implementación con un paquete de la aplicación diferente.

> [!IMPORTANT]
> Si implementa una aplicación con la acción de implementación **Instalación requerida** y posteriormente cambia la acción de implementación a **Instalación disponible**, las actualizaciones de la aplicación no se instalan automáticamente en los dispositivos que instalaron la aplicación antes de que se realizara el cambio de implementación. Para corregir este problema, puede hacer lo siguiente:
> 
> -   Indique al usuario del dispositivo que vaya al portal de empresa, seleccione la aplicación instalada y haga clic en **Instalar**.
> -   Cambie la acción de implementación a **Desinstalar**y, una vez desinstalada la aplicación, vuelva a implementar la aplicación con la acción de implementación **Instalación disponible**.

### Para actualizar una aplicación

1.  En la [consola de administrador de Microsoft Intune](https://manage.microsoft.com), haga clic en **Aplicaciones** &gt; **Aplicaciones**.

2.  En la lista **Aplicaciones** , seleccione la aplicación que quiera actualizar y, a continuación, haga clic en **Editar**.

3.  En el asistente **Editar software** , proporcione los detalles nuevos del paquete de la aplicación.

4.  Cuando haya terminado haga clic en **Actualizar**.

Cuando los dispositivos comprueben posteriormente si hay aplicaciones disponibles, la aplicación se actualizará automáticamente a la última versión.





<!--HONumber=May16_HO2-->


