---
title: Implementar aplicaciones | Microsoft Intune
description: En este tema se explican los conceptos que es preciso conocer para empezar a implementar aplicaciones con Intune.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c4a760b6362356a6bafa8b6acc69299647a5e0f3
ms.openlocfilehash: 377597aabc03c020060e2851c6fc25e0c780ea51


---

# Implementar aplicaciones con Microsoft Intune

En este tema se explican algunos de los conceptos que es preciso conocer para empezar a implementar aplicaciones con Microsoft Intune.


## Acciones de implementación de aplicaciones
Al implementar aplicaciones, puede elegir una de las siguientes acciones de implementación:

-   **Instalación requerida:** la aplicación se instala en el dispositivo sin intervención por parte del usuario.

    > [!TIP]
    > En los dispositivos iOS que no estén en modo supervisado y en todos los dispositivos Android, el usuario debe aceptar la oferta de la aplicación antes de instalarla.
    >
    >  Si un usuario desinstala una aplicación que ha implementado como una instalación necesaria, Intune volverá a instalar automáticamente la aplicación tras el siguiente ciclo de inventario, que normalmente se produce cada siete días.

-   **Instalación disponible:** la aplicación aparece en el portal de empresa y los usuarios pueden solicitar instalarla.

-   **Desinstalar** : la aplicación se desinstala del dispositivo.

-   **No aplicable**: La aplicación no aparece en el portal de empresa y no está instalada en los dispositivos.

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
> [!TIP]
> Si, al implementar aplicaciones, selecciona grupos tanto de usuarios como de dispositivos, la aplicación solo se puede implementar como una **instalación disponible**.

## Conflictos de implementación
Cuando un dispositivo recibe dos implementaciones, con la misma acción de implementación, se aplican las siguientes reglas:

-   Las implementaciones para un grupo de dispositivos tienen prioridad sobre las implementaciones para un grupo de usuarios. Sin embargo, si una aplicación se implementa para un grupo de usuarios con la acción de implementación **Disponible** y la misma aplicación se implementa también para un grupo de dispositivos con la acción de implementación **No aplicable**, la aplicación estará disponible en el portal de la compañía para que los usuarios la instalen.

-   Una acción de instalación tiene prioridad sobre una de desinstalación.

-   Si un dispositivo recibe una instalación requerida y una instalación disponible, ambas acciones se combinan. En otras palabras, el usuario puede instalar la aplicación disponible desde el portal de empresa antes de que comience la instalación requerida.


## Pasos siguientes

Obtenga información sobre cómo [implementar aplicaciones en Microsoft Intune](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Jul16_HO4-->


