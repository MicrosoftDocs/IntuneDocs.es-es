---
title: "Problemas conocidos de la versión preliminar de Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: lea acerca de los problemas conocidos de la versión preliminar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: ec3f87994b19591bda4ec201eac3c839798d634c
ms.lasthandoff: 03/15/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Problemas conocidos de la versión preliminar de Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Use este tema para aprender sobre los problemas conocidos de la versión preliminar de Intune.

Si quiere notificar un error que no aparece aquí, [abra una solicitud de soporte técnico](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

Si quiere solicitar que se agregue una nueva característica a Intune, considere la posibilidad de presentar un informe en nuestro sitio [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

## <a name="administration-and-accounts"></a>Administración y cuentas

- Los administradores globales (también denominados administradores de inquilinos) pueden seguir realizando tareas de administración cotidianas sin una licencia independiente de Intune o Enterprise Mobility Suite (EMS). Sin embargo, si los administradores globales quieren usar el servicio, por ejemplo para inscribir sus dispositivos, un dispositivo de la empresa o para usar el Portal de empresa de Intune, necesitarán una licencia de Intune o EMS igual que cualquier otro usuario.

## <a name="apple-enrollment-profile-migration"></a>Migración de perfiles de inscripción de Apple
- En los próximos meses, Intune permitirá administrar las inscripciones de Apple Configurator y el programa de inscripciones de dispositivos de Apple mediante el nuevo Azure Portal. Si elimina el token del programa de inscripción de dispositivos de Apple y no carga uno actualizado, el original se restaurará en el nuevo Azure Portal como parte del proceso de migración de su cuenta de Intune. Para quitar este token y evitar la inscripción de DEP, simplemente elimine el token en Azure Portal. 

