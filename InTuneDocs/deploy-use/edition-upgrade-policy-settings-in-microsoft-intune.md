---
title: "Configuración de la directiva de actualización de edición de Windows | Microsoft Docs"
description: "Aprenda a actualizar automáticamente dispositivos de Windows 10 a la versión más reciente con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: ae6477866991cec4091ff2790b925b0e464375f9


---

# <a name="windows-edition-upgrade-policy-settings-in-microsoft-intune"></a>Configuración de directivas de actualización de edición de Windows en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

La **directiva de actualización de edición** de Microsoft Intune permite actualizar automáticamente los dispositivos que ejecutan una de las siguientes versiones de Windows 10 a una edición más reciente:
* Windows 10 Escritorio
* Windows 10 Holographic
* Windows 10 Mobile

Las siguientes rutas de acceso de actualización son compatibles:
- De Windows 10 Pro a Windows 10 Enterprise
- De Windows 10 Home a Windows 10 Education
- De Windows 10 Mobile a Windows 10 Mobile Enterprise
- De Windows 10 Holographic Pro a Windows 10 Holographic Enterprise

## <a name="before-you-start"></a>Antes de empezar
Antes de empezar a actualizar dispositivos a la versión más reciente, necesitará uno de los elementos siguientes:
* Una clave de producto válida para instalar la nueva versión de Windows en todos los dispositivos de destino de la directiva (para ediciones de Windows 10 Escritorio). Puede utilizar las claves de las claves de activación múltiple (MAK) o el servidor de administración de claves (KMS).
**o** un archivo de licencia de Microsoft que contenga la información de licencia para instalar la nueva versión de Windows en todos los dispositivos de destino de la directiva (para las ediciones de Windows 10 Mobile y Windows 10 Holographic).
* Los dispositivos de Windows 10 que planee actualizar deben estar inscritos en Microsoft Intune. No puede usar la directiva de actualización de edición con equipos que ejecutan el software cliente de PC de Intune.

## <a name="edition-upgrade-policy-settings"></a>Configuración de la directiva de actualización de edición

|Nombre de la configuración|Detalles|
|-|-|
|**Nombre**|Escriba un nombre para la directiva de actualización de edición.|
|**Descripción**|Si lo desea, escriba una descripción de la directiva que sirva para identificarla en la consola de Intune.
|**Edición a la que actualizar**|En la lista desplegable, seleccione la versión de Windows 10 Escritorio, Windows 10 Holographic o Windows 10 Mobile a la que quiera actualizar los dispositivos de destino.
|**Clave de producto**|Especifique la clave de producto que obtuvo de Microsoft, que se puede usar para actualizar todos los dispositivos de Windows 10 Escritorio de destino.<br>Después de crear una directiva que contenga una clave de producto, no se puede editar la clave de producto más adelante. Esto se debe a que la clave se oculta por motivos de seguridad. Para cambiar la clave de producto, debe escribir toda la clave de nuevo.
|**Archivo de licencia**|Elija **Examinar** para seleccionar el archivo de licencia que obtuvo de Microsoft y que contiene la información de licencia de la edición Windows Holographic o Windows 10 Mobile a la que quiere actualizar los dispositivos de destino.

### <a name="see-also"></a>Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Dec16_HO2-->


