---
# required metadata

title: Configuración de directivas de actualización de edición de Windows en Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuración de directivas de actualización de edición de Windows en Microsoft Intune
La **directiva de actualización de edición** de Microsoft Intune permite actualizar automáticamente los dispositivos que ejecutan una de las siguientes versiones de Windows 10 a una edición más reciente:
* Windows 10 Escritorio
* Windows 10 Holographic

## Antes de empezar
Antes de empezar a actualizar dispositivos a la versión más reciente, necesitará uno de los elementos siguientes:
* Una clave de producto válida para instalar la nueva versión de Windows en todos los dispositivos de destino de la directiva (para ediciones de Windows 10 Escritorio).
* Un archivo de licencia de Microsoft que contenga la información de licencia para instalar la nueva versión de Windows en todos los dispositivos de destino de la directiva (para las ediciones de Windows 10 Mobile y Windows 10 Holographic).
* Los dispositivos de Windows 10 que planee actualizar deben estar inscritos en Microsoft Intune.

## Configuración de la directiva de actualización de edición

|Nombre de la configuración|Detalles|
|-|-|
|**Nombre**|Escriba un nombre para la directiva de actualización de edición.|
|**Descripción**|Si lo desea, escriba una descripción de la directiva que sirva para identificarla en la consola de Intune.
|**Edición a la que actualizar**|En la lista desplegable, seleccione la versión de Windows 10 Escritorio, Windows 10 Holographic o Windows 10 Mobile a la que quiera actualizar los dispositivos de destino.
|**Clave de producto**|Especifique la clave de producto que obtuvo de Microsoft, que se puede usar para actualizar todos los dispositivos de Windows 10 Escritorio de destino.<br>Después de crear una directiva que contenga una clave de producto, no se puede editar la clave de producto más adelante. Esto se debe a que la clave se oculta por motivos de seguridad. Para cambiar la clave de producto, debe volver a escribir toda la clave.
|**Archivo de licencia**|Haga clic en **Examinar** para seleccionar el archivo de licencia que obtuvo de Microsoft, que contiene la información de licencia de la edición Windows Holographic a la que quiere actualizar los dispositivos de destino.

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

<!--HONumber=May16_HO1-->


