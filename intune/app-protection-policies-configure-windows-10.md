---
title: "Preparativos para configurar directivas de protección de aplicaciones para Windows 10"
titleSuffix: Intune on Azure
description: "Configuración del proveedor de administración de aplicaciones móviles (MAM) en Azure AD"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 6f2f0b610b900bb41a3c2bd7416b6db28434a155
ms.openlocfilehash: bf56d3a80f0d167baa95e9dfdb20d08e02590984
ms.contentlocale: es-es
ms.lasthandoff: 06/13/2017


---

# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Preparativos para configurar directivas de protección de aplicaciones para Windows 10

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Antes de crear una directiva de protección de aplicaciones para Windows 10, debe habilitar la administración de aplicaciones móviles (MAM) para Windows 10 configurando el proveedor de MAM en Azure AD. Esta configuración le permite definir el estado de la inscripción al crear una nueva directiva de Windows Information Protection (WIP) con Intune.

> [!NOTE]
> El estado de la inscripción puede ser MAM o administración de dispositivos móviles (MDM).

## <a name="to-configure-the-mam-provider"></a>Para configurar el proveedor de MAM

1.  Vaya a [Azure Portal](https://portal.azure.com/) e inicie sesión con sus credenciales de Intune.

2.  En el menú de la izquierda, elija **Azure Active Directory**.

    ![Configuración de proveedor de MAM](./media/mam-provider-sc-1.png)

3.  Se abre la hoja de **Azure AD**, elija **Movilidad (MDM y MAM)** y, a continuación, haga clic en **Microsoft Intune**.

    ![Movilidad (MDM y MAM)](./media/mam-provider-sc-1.png)

4.  Cuando se abra la hoja de configuración, elija primero **Restaurar las URL de MAM predeterminadas** y luego configure lo siguiente:

    a.  Ámbito de usuario de MAM: puede usar MAM para proteger los datos corporativos en un grupo específico de usuarios que utilizan dispositivos Windows 10 o todos los usuarios.

    b.  URL de los términos de uso de MAM: la dirección URL del extremo de términos de uso del servicio MAM. Se utiliza para mostrar el término del servicio MAM a los usuarios finales.

    c.  URL de detección de MAM: esta es la dirección URL que buscan los dispositivos cuando necesitan aplicar directivas de protección de aplicaciones.

    d.  URL de cumplimiento de MAM:

5.  Una vez configurados estos valores, elija **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

[Create a WIP app protection policy](windows-information-protection-policy-create.md) (Creación de una directiva de protección de aplicaciones de WIP)

