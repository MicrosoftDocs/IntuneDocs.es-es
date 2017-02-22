---
title: "Establecimiento de los términos y condiciones en Microsoft Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: establezca los términos y condiciones que los usuarios ven en el Portal de empresa de Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 694e5ac5eff0e2d39d44d992fe9dcc2262c112ce

---

# <a name="set-terms-and-conditions"></a>Establecimiento de los términos y condiciones 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Puede implementar los términos y condiciones de Intune en los grupos de usuarios para explicar en qué afecta la inscripción, el acceso a los recursos de trabajo y la aplicación Portal de empresa a los dispositivos y los usuarios. Los usuarios deben aceptar los términos y las condiciones para poder usar el portal de empresa a fin de inscribirse y obtener acceso a su trabajo.

Puede crear e implementar varias directivas que contienen diferentes términos y condiciones. También puede generar versiones de los mismos términos y condiciones en distintos idiomas e implementarlas en los grupos correspondientes.

**Para crear términos y condiciones**:

1. En el portal de Azure, elija **More Services** (Más servicios), escriba **Intune** en el cuadro de texto y luego seleccione **Other** (Otros)  > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego **Términos y condiciones**.

3. Seleccione **Crear**.

4. En la hoja **Crear términos y condiciones**, especifique la siguiente información:

   - **Nombre para mostrar**: nombre que se usa en los términos. Los usuarios ven este nombre en la aplicación Portal de empresa.

   - **Descripción**: detalles opcionales que le ayudan a identifican la directiva en el portal de Azure.

5. Seleccione la flecha situada junto a Define terms of use (Definir términos de uso) para abrir la hoja Términos y condiciones y, luego, escriba la siguiente información:

   - **Título**: el título que ven los usuarios en el Portal de empresa.

   - **Resumen de los términos**: texto que explica lo que significa que los usuarios acepten los términos.

   - **Términos y condiciones**: la etiqueta legal que los usuarios ven y deben aceptar o rechazar; por ejemplo, "Acepto los términos y condiciones".

6. Seleccione **Aceptar**.



<!--HONumber=Feb17_HO1-->


