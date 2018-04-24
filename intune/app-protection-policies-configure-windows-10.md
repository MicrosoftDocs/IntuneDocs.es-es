---
title: Preparativos para configurar directivas de protección de aplicaciones para Windows 10
titleSuffix: Microsoft Intune
description: Configuración del proveedor de administración de aplicaciones móviles (MAM) en Azure AD.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16c579bb4eb475bc92260e55f2e47335efc73e03
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Preparativos para configurar directivas de protección de aplicaciones para Windows 10 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Habilite la administración de aplicaciones móviles (MAM) para Windows 10. Para ello, establezca el proveedor de MAM en Azure AD. Establecer un proveedor de MAM en Azure AD permite definir el estado de la inscripción al crear una nueva directiva de Windows Information Protection con Intune. El estado de la inscripción puede ser MAM o administración de dispositivos móviles (MDM).

> [!NOTE]
> Se requiere que los dispositivos con un estado de inscripción de MAM se combinen con Azure AD.

## <a name="to-configure-the-mam-provider"></a>Para configurar el proveedor de MAM

1. Inicie sesión en Azure Portal y seleccione **Azure Active Directory.**

2. Elija **Movilidad (MDM y MAM)** en el grupo **Administrar**.

3. Haga clic en **Microsoft Intune**.

4. Configure los valores en el grupo **Restaurar las URL de MAM predeterminadas** en la hoja **Configurar**.

   **Ámbito de usuario de MAM**  
   Use la inscripción automática de MAM para administrar los datos de la empresa en los dispositivos Windows de sus empleados. La inscripción automática de MAM se configurará para traer sus propios escenarios de dispositivo.<ul><li>**Ninguno**<br>Seleccione si ningún usuario se puede inscribir en MAM.</li><li>**Algunos**<br>Seleccione los grupos de Azure AD que incluyen los usuarios que se inscribirán en MAM.</li><li>**Todos**<br>Seleccione si todos los usuarios se pueden inscribir en MAM.</li></ul>

   **URL de las condiciones de uso de MAM**  
   Microsoft Intune no admite la URL de los términos de uso de MAM. Este cuadro de entrada se debe dejar en blanco para que se apliquen las directivas de protección.

   **URL de detección de MAM**  
   La dirección URL del punto de conexión de la inscripción del servicio MAM. El punto de conexión de inscripción se usa para inscribir dispositivos para administración con el servicio MAM.

   **URL de cumplimiento de MAM**  
   Microsoft Intune no admite la URL de cumplimiento de MAM. Este cuadro de entrada se debe dejar en blanco para que se apliquen las directivas de protección. 

5.  Haga clic en **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

[Create a WIP app protection policy](windows-information-protection-policy-create.md) (Creación de una directiva de protección de aplicaciones de WIP)
