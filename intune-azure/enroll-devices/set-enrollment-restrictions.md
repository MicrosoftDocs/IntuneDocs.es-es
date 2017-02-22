---
title: "Configuración de restricciones de inscripción en Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: restrinja las inscripciones por plataforma y establezca un límite de inscripciones de dispositivos en Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 1bdefce35c20ce24b94ee701a2d13b5408f435ce

---

# <a name="set-enrollment-restrictions"></a>Configuración de restricciones de inscripción 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Puede limitar los tipos de dispositivos que tienen permiso para inscribirse en Intune especificando las plataformas permitidas. También puede establecer el número máximo de dispositivos que puede inscribir un usuario.

## <a name="set-device-type-restrictions"></a>Configuración de restricciones de tipo de dispositivo

1. En el portal de Azure, elija **More Services** (Más servicios), escriba **Intune** en el cuadro de texto y luego seleccione **Other** (Otros)  > **Intune**

2. En la hoja de Intune, elija **inscribir dispositivos** y luego elija **Restricciones de inscripción**.

3. En **Restricciones de tipo de dispositivo**, seleccione **Default** (Predeterminada).

4. En la hoja **All Users** (Todos los usuarios), seleccione **Plataformas**.

5. Para las plataformas que tengan permiso para inscribirse en Intune, seleccione **Permitir**. Para las plataformas a las que quiera impedir la inscripción, seleccione **Bloquear**.

6. Seleccione **Guardar**.

7. Seleccione **Configuraciones de plataforma**.

8. Seleccione si quiere permitir o impedir la inscripción de dispositivos iOS de propiedad personal.

9. Seleccione **Guardar**.

## <a name="set-device-limit-restrictions"></a>Configuraciones de restricciones de límite de dispositivo

1. En la hoja de Intune del portal de Azure, elija **Inscribir dispositivos** y luego elija **Restricciones de inscripción**.

2. En **Restricciones de límite de dispositivos**, seleccione **Default** (Predeterminada).

3. En la hoja **All Users** (Todos los usuarios), seleccione **Límite de dispositivos**.

4. Seleccione el número máximo de dispositivos que un usuario puede inscribir y haga clic en **Guardar**.



<!--HONumber=Feb17_HO1-->


