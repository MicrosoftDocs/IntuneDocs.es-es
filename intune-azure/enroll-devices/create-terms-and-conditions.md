---
title: "Definir los términos y condiciones en Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: establezca los términos y condiciones que los usuarios ven en el Portal de empresa de Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 07a42cf8fa10d3223129fbb2932217ff90ac365b
ms.lasthandoff: 02/18/2017

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

