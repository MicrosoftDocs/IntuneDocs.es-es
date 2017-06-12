---
title: "Preparativos para configurar directivas de protección de aplicaciones para Windows 10 | Microsoft Docs"
description: "Configuración del proveedor de administración de aplicaciones móviles (MAM) en Azure AD"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ebc7cfc8-40b9-47c2-8357-d392ebbb27c8
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c48f9181e8fd740ab080a8620f3873909d0fd0f1
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Preparativos para configurar directivas de protección de aplicaciones para Windows 10

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Antes de crear una directiva de protección de aplicaciones para Windows 10, debe habilitar la administración de aplicaciones móviles (MAM) para Windows 10 configurando el proveedor de MAM en Azure AD. Esta configuración le permite definir el estado de la inscripción al crear una nueva directiva de Windows Information Protection (WIP) con Intune.

> [!NOTE]
> El estado de la inscripción puede ser MAM o administración de dispositivos móviles (MDM).

## <a name="to-configure-the-mam-provider"></a>Para configurar el proveedor de MAM

1.  Vaya a [Azure Portal](https://portal.azure.com/) e inicie sesión con sus credenciales de Intune.

2.  En el menú de la izquierda, elija **Azure Active Directory**.

    ![Configuración de proveedor de MAM](../media/AppManagement/mam-provider-sc-1.png)

3.  Se abre la hoja de **Azure AD**, elija **Movilidad (MDM y MAM)** y, a continuación, haga clic en **Microsoft Intune**.

    ![Movilidad (MDM y MAM)](../media/AppManagement/mam-provider-sc-2.png)

4.  Cuando se abra la hoja de configuración, elija primero **Restaurar las URL de MAM predeterminadas** y luego configure lo siguiente:

    a.  Ámbito de usuario de MAM: puede usar MAM para proteger los datos corporativos en un grupo específico de usuarios que utilizan dispositivos Windows 10 o todos los usuarios.

    b.  URL de los términos de uso de MAM: la dirección URL del extremo de términos de uso del servicio MAM. Se utiliza para mostrar el término del servicio MAM a los usuarios finales.

    c.  URL de detección de MAM: esta es la dirección URL que buscan los dispositivos cuando necesitan aplicar directivas de protección de aplicaciones.

    d.  URL de cumplimiento de MAM:

5.  Una vez configurados estos valores, elija **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

[Create a WIP app protection policy](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune) (Creación de una directiva de protección de aplicaciones de WIP)

