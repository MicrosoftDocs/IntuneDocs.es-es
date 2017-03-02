---
title: "Establecer restricciones de inscripción en Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Azure de Intune: restrinja las inscripciones por plataforma y establezca un límite de inscripciones de dispositivos en Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 56996592febf0be5ab74b158a70404728fe17a4d
ms.lasthandoff: 02/18/2017

---

# <a name="set-enrollment-restrictions"></a>Establecer restricciones de inscripción 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Puede establecer los tipos y el número máximo de dispositivos que permitirá que se inscriban. En la hoja Restricciones de inscripción, puede establecer lo siguiente:

- Las plataformas que se pueden inscribir y si desea bloquear la inscripción de dispositivos de propiedad personal para iOS y Android.

- El número máximo de dispositivos que puede inscribir un usuario.

## <a name="set-device-type-restrictions"></a>Establecer restricciones de tipo de dispositivo

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y, luego, **Restricciones de inscripción**.

3. En **Restricciones de tipo de dispositivo**, seleccione **Predeterminado**.

4. En la hoja **Todos los usuarios**, seleccione **Plataformas**.

5. Para las plataformas que tengan permiso para inscribirse en Intune, seleccione **Permitir**. Para las plataformas a las que quiera impedir la inscripción, seleccione **Bloquear**. En el caso de las plataformas, la opción **Permitir** está establecida de forma predeterminada. 

    >[!NOTE]
    >Esta configuración no se aplica a las inscripciones de Windows que usen el cliente de software de Intune, y tampoco las bloquea. Esta configuración afecta solo a las inscripciones que usen la administración de dispositivos móviles. 

6. Seleccione **Guardar**.

7. Seleccione **Configuraciones de plataforma**.

8. Seleccione si quiere **Permitir** o **Bloquear** la inscripción de dispositivos iOS y Android de propiedad personal.

9. Seleccione **Guardar**.

## <a name="set-device-limit-restrictions"></a>Establecer restricciones de límite de dispositivos

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y, luego, **Restricciones de inscripción**.

3. En **Restricciones de límite de dispositivos**, seleccione **Predeterminado**.

4. En la hoja **Todos los usuarios**, seleccione **Límite de dispositivos**.

5. Seleccione el número máximo de dispositivos que un usuario puede inscribir y haga clic en **Guardar**.

