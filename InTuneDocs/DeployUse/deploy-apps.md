---
title: Implementar aplicaciones | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: e6b995118e66fd146a68b49ce4decdcbd1fe3572
ms.openlocfilehash: a68cb85602bd585539147c7d7d38c0d906f2b1f7


---

# Implementar aplicaciones con Microsoft Intune

En este tema se explican algunos de los conceptos que es preciso conocer para empezar a implementar aplicaciones con Microsoft Intune.


## Acciones de implementación de aplicaciones
Al implementar aplicaciones, puede elegir una de las siguientes acciones de implementación:

-   **Instalación requerida:** la aplicación se instala en el dispositivo sin intervención por parte del usuario final.

    > [!TIP] En los dispositivos iOS que no estén en modo supervisado y en todos los dispositivos Android, el usuario debe aceptar la oferta de la aplicación antes de instalarla.
    > 
    >  Si un usuario final desinstala una aplicación que ha implementado como una instalación necesaria, Intune volverá a instalar automáticamente la aplicación tras el siguiente ciclo de inventario, que normalmente se produce cada 7 días.

-   **Instalación disponible:** la aplicación aparece en el portal de empresa y los usuarios finales pueden solicitar instalarla.

-   **Desinstalar** : la aplicación se desinstala del dispositivo.

-   **No aplicable** : la aplicación no aparece en el portal de empresa y no está instalada en los dispositivos.

#### Saber qué acciones de implementación están disponibles para cada tipo de instalador

|Tipo de instalador|Instalación requerida|Instalación disponible|Desinstalar|No aplicable|
|------------------|--------------------|---------------------|-------------|------------------|
|Paquete de aplicación de Windows (implementado para un grupo de usuarios)|Sí|Sí|Sí|Sí|
|Paquete de aplicación de Windows (se implementa en un grupo de dispositivos)|Sí|No|Sí|Sí|
|Paquete de aplicación para dispositivos móviles (se implementa para un grupo de usuarios)|Sí|Sí|Sí|Sí|
|Paquete de aplicación para dispositivos móviles (se implementa para un grupo de dispositivos)|Sí|No|Sí|Sí|
|Windows Installer (se implementa para un grupo de usuarios)|No|Sí|No|Sí|
|Windows Installer (se implementa para un grupo de dispositivos)|Sí|No|Sí|Sí|
|Vínculo externo (se implementa para un grupo de usuarios)|No|Sí|No|Sí|
|Vínculo externo (se implementa para un grupo de dispositivos)|No|No|No|No|
|Aplicación iOS administrada desde la tienda de aplicaciones (se implementa para un grupo de usuarios)|Sí|Sí|Sí|Sí|
|Aplicación iOS administrada desde la tienda de aplicaciones (se implementa para un grupo de dispositivos)|Sí|No|Sí|Sí|
> [!TIP] Si, al implementar aplicaciones, selecciona grupos tanto de usuarios como de dispositivos, la aplicación solo se puede implementar como una **instalación disponible**.

## Conflictos de implementación
Cuando un dispositivo recibe dos implementaciones, con la misma acción de implementación, se aplican las siguientes reglas:

-   Las implementaciones para un grupo de dispositivos tienen prioridad sobre las implementaciones para un grupo de usuarios. Sin embargo, si una aplicación se implementa para un grupo de usuarios con la acción de implementación **Disponible** y la misma aplicación se implementa también para un grupo de dispositivos con la acción de implementación **No aplicable**, la aplicación estará disponible en el portal de la compañía para que los usuarios la instalen.

-   Una acción de instalación tiene prioridad sobre una de desinstalación.

-   Si un dispositivo recibe una instalación necesaria y disponible, las acciones se combinan (la aplicación es necesaria y disponible; en otras palabras, el usuario final puede instalarla desde el portal de empresa antes de que comience la instalación necesaria).


## Pasos siguientes

Obtenga información sobre cómo [implementar aplicaciones en Microsoft Intune](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Jun16_HO3-->


