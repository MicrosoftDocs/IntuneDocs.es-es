---
title: "Establecimiento de los términos y condiciones en Microsoft Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: establezca los términos y condiciones que los usuarios ven en el Portal de empresa de Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: f7d6ebc9d71a077492ab615a3bc5397e092b1deb
ms.lasthandoff: 02/15/2017

---

# <a name="set-terms-and-conditions"></a>Establecimiento de los términos y condiciones 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Puede implementar los términos y condiciones de Intune en los grupos de usuarios para explicar en qué afecta la inscripción, el acceso a los recursos de trabajo y la aplicación Portal de empresa a los dispositivos y los usuarios. Los usuarios deben aceptar los términos y las condiciones para poder usar el portal de empresa a fin de inscribirse y obtener acceso a su trabajo.

Puede crear e implementar varias directivas que contienen diferentes términos y condiciones. También puede generar versiones de los mismos términos y condiciones en distintos idiomas e implementarlas en los grupos correspondientes.

**Para crear términos y condiciones**:

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

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

