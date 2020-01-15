---
title: Introducción a escenarios guiados
titleSuffix: Microsoft Intune
description: Conozca los escenarios guiados de Intune disponibles en el portal de administración de dispositivos de Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b833e5265387637a35bfcdf79f4ae5f37558de61
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839133"
---
# <a name="intune-guided-scenarios-overview"></a>Introducción a los escenarios guiados de Intune 

Un escenario guiado es una serie personalizada de pasos en torno a un caso de uso completo. Los escenarios más habituales se basan en el rol que un administrador, un usuario o un dispositivo desempeñan en la organización. Estos roles suelen requerir una colección de perfiles, opciones, aplicaciones y controles de seguridad cuidadosamente organizados para proporcionar la mejor experiencia de usuario y seguridad.    

Si no está familiarizado con todos los pasos y recursos necesarios para implementar un determinado escenario de Intune, los escenarios guiados pueden servir de punto de partida. En el escenario guiado se ensamblarán directivas, aplicaciones, asignaciones y otras configuraciones de administración de manera automática. Asimismo, puede que en estos escenarios guiados se omitan deliberadamente ciertas opciones que no procedan o que sean poco frecuentes en el escenario en cuestión. 

Los escenarios guiados no son un espacio de administración distinto de los flujos de trabajo de Intune habituales. Estos flujos de trabajo están pensados para usarse junto con los flujos de trabajo existentes de Intune de los perfiles, aplicaciones y directivas. Tras completar un escenario guiado, toda la administración futura del escenario debe realizarse en los menús existentes de las directivas, aplicaciones y perfiles. Un escenario guiado no guarda un tipo de recurso de "escenario guiado" ni realiza un seguimiento de los cambios futuros realizados en los recursos. Todos los recursos creados por un escenario guiado aparecerán en su correspondiente carga de trabajo. Todas las opciones del escenario guiado, incluso las omitidas, estarán disponibles para su edición en los menús existentes.  

## <a name="types-of-guided-scenarios"></a>Tipos de escenarios guiados 

Por motivos de simplicidad, en todos los escenarios guiados se omiten características de ámbito complejas, como las etiquetas de ámbito, los grupos de exclusión y las asignaciones de grupo virtual. Todos los recursos creados en un escenario guiado heredarán todas las etiquetas de ámbito del administrador que complete el escenario. Algunos escenarios ofrecen cierto nivel de personalización de la configuración común para cubrir escenarios que están estrechamente relacionados. En estos escenarios solo se permite la asignación de grupos a grupos de inclusión. En otros escenarios guiados, todo el escenario garantiza una experiencia coherente al no ofrecer ninguna personalización, y se genera automáticamente un nuevo grupo para recibir todas las asignaciones. Una vez completado el escenario guiado, se pueden usar asignaciones más sofisticadas directamente a través de las cargas de trabajo de directivas, aplicaciones y perfiles existentes.  

Los siguientes escenarios son escenarios guiados: 
- Implementar Microsoft Edge para aplicaciones móviles 
- Probar un equipo administrado en la nube
- Proteger Microsoft Office para móviles 

## <a name="guided-scenario-functionality"></a>Funcionalidad de los escenarios guiados 

Los escenarios guiados ofrecen una funcionalidad específica. Los siguientes detalles ayudan a explicar lo que se puede y no se puede hacer mientras se sigue un escenario guiado.

### <a name="launching"></a>Inicio  

Todos los escenarios guiados están disponibles en el **[portal de administración de dispositivos](https://devicemanagement.microsoft.com)**  > **Solución de problemas + soporte técnico** > **Escenarios guiados**. 

El escenario guiado comienza con una introducción en la que se explica el propósito del escenario y los requisitos previos necesarios para completar la configuración. En ese momento, se comprueban sus permisos de administrador para corroborar que tiene todos los privilegios necesarios para completar el escenario.  

Una vez superadas todas las comprobaciones de requisitos previos, el escenario ofrece la configuración adecuada de personalización. El objetivo de los escenarios guiados es que el usuario introduzca únicamente el número mínimo de configuraciones, y en ellos la configuración no habitual o avanzada se oculta hasta que sea necesaria o en función de circunstancias especiales. Cada escenario guiado incluye vínculos a la documentación que proporciona más información detallada. 

Una vez especificados todos los valores obligatorios, el escenario guiado muestra un resumen de los valores especificados y los recursos que el escenario en cuestión requiere. Hasta el momento, no se ha guardado nada a menos que se haya indicado expresamente.

El siguiente paso consiste en implementar el escenario. Con la implementación de un escenario se crean y guardan todos los recursos necesarios y la configuración seleccionada. El tiempo que se tarda en completar una implementación varía según el escenario. Una vez finalizada la implementación, el escenario guiado muestra una lista de los recursos creados con vínculos a la vista de administración de cada recurso, la carga de trabajo normal del recurso y la documentación. 

> [!IMPORTANT]
> La lista que se muestra al final del escenario guiado no se guarda y solo está visible mientras el escenario guiado está abierto.  
Si se produce un error al implementar el escenario, se revertirán todos los cambios. 

### <a name="editing"></a>Edición 

Los escenarios guiados no se pueden usar para editar los recursos existentes. Una vez creados, todos los recursos, grupos y asignaciones se deben editar con las cargas de trabajo existentes.

### <a name="monitoring"></a>monitoring 

Los escenarios guiados no se pueden usar para supervisar los recursos existentes aparte del proceso de creación inicial. Una vez creados, todos los recursos, grupos y asignaciones se deben supervisar con las cargas de trabajo existentes. 

### <a name="retiring"></a>Retirada 

Los escenarios guiados no se pueden usar para retirar recursos existentes, aparte de la limpieza automatizada durante un error en la implementación inicial. Una vez creados, todos los recursos, grupos y asignaciones se deben retirar con las cargas de trabajo existentes. 

### <a name="updating"></a>Actualización

A medida que la tecnología avanza, Intune puede actualizar de vez en cuando un escenario guiado para mejorar la experiencia de usuario, la seguridad u otros aspectos de ese escenario. Esta actualización afectará únicamente a las nuevas implementaciones realizadas en el escenario guiado. Intune no actualizará los recursos existentes que se hayan generado previamente en el escenario guiado para que coincidan con nuevas prácticas recomendadas o recomendaciones.  

## <a name="next-steps"></a>Pasos siguientes

Para empezar a usar Microsoft Intune cuanto antes, recorra los escenarios guiados de Intune. Si no está familiarizado con Intune, configure un inquilino de Intune siguiendo el [inicio rápido de prueba gratuita](free-trial-sign-up.md).
