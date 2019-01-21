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
ms.openlocfilehash: 0da6861b6c49fc37691b8c6e464a506670643fa3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203338"
---
# <a name="use-scope-tags-to-filter-policies"></a>Uso de etiquetas de ámbito para filtrar directivas

Las etiquetas de ámbito permiten filtrar las directivas mediante etiquetas personalizadas que cree. Puede aplicar etiquetas de ámbito a roles y aplicaciones.

Por ejemplo, cree una etiqueta de ámbito denominada "Departamento de ingeniería" y asígnela a los perfiles de configuración relacionados con el departamento de ingeniería. Asigne esa misma etiqueta a un rol de "Administradores de Ingeniería". Solo verán las directivas con la etiqueta "Departamento de ingeniería".

## <a name="to-create-a-scope-tag"></a>Para crear una etiqueta de ámbito

Seleccione **Roles** > **Ámbito (etiquetas)** > **Crear**.

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Para agregar una etiqueta de ámbito a un perfil de configuración

Elija **Configuración del dispositivo** > **Perfiles** > elija un perfil > **Propiedades** > **Ámbito (etiquetas)**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Para asignar una etiqueta de ámbito a un rol

Elija **Roles** > **Todos los roles** > **Administrador de directivas y perfiles** > **Asignaciones** > **Ámbito (etiquetas)**.

## <a name="to-assign-a-scope-tag-to-an-app"></a>Para asignar una etiqueta de ámbito a una aplicación

Elija **Aplicaciones cliente** > **Aplicaciones** > elija la aplicación > **Propiedades** > **Ámbito (etiquetas)** > **Agregar** > elija las etiquetas > **Seleccionar** > **Aceptar** > **Guardar**.


## <a name="next-steps"></a>Pasos siguientes

Administre sus [roles](role-based-access-control.md) y [perfiles](device-profile-assign.md).

