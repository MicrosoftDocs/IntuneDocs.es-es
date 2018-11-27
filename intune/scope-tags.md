---
title: Filtrado de directivas con etiquetas de ámbito en Microsoft Intune - Azure | Microsoft Docs
description: Use las etiquetas de ámbito para filtrar los perfiles de configuración por roles específicos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 080205e601b857d4765eb6b97eeeeeb8f4e6fc1b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187164"
---
# <a name="use-scope-tags-to-filter-policies"></a>Uso de etiquetas de ámbito para filtrar directivas

Las etiquetas de ámbito permiten filtrar las directivas mediante etiquetas personalizadas que cree.

Por ejemplo, cree una etiqueta de ámbito denominada "Departamento de ingeniería" y asígnela a los perfiles de configuración relacionados con el departamento de ingeniería. Asigne esa misma etiqueta a un rol de "Administradores de Ingeniería". Solo verán las directivas con la etiqueta "Departamento de ingeniería".

## <a name="to-create-a-scope-tag"></a>Para crear una etiqueta de ámbito

Seleccione **Roles** > **Ámbito (etiquetas)** > **Crear**.

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Para agregar una etiqueta de ámbito a un perfil de configuración

Elija **Configuración del dispositivo** > **Perfiles** > elija un perfil > **Propiedades** > **Ámbito (etiquetas)**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Para asignar una etiqueta de ámbito a un rol

Elija **Roles** > **Todos los roles** > **Administrador de directivas y perfiles** > **Asignaciones** > **Ámbito (etiquetas)**.

## <a name="next-steps"></a>Pasos siguientes

Administre sus [roles](role-based-access-control.md) y [perfiles](device-profile-assign.md).

