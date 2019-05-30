---
title: Uso de informes de Update Compliance para actualizaciones de Windows en Microsoft Intune | Microsoft Docs
description: Use Update Compliance de OMS para ver los datos del informe de Windows Update que implemente con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2b236d01cb5ffcf5a26e71ac0a9b65bb586dcb1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039667"
---
# <a name="intune-compliance-reports-for-updates"></a>Informes de cumplimiento de Intune para las actualizaciones
Al usar Intune para implementar la actualización de Windows en dispositivos Windows 10, vea detalles sobre el cumplimiento de las actualizaciones mediante Intune o una solución gratuita llamada *Update Compliance*, que forma parte de Microsoft Operations Management Suite (OMS).

## <a name="use-intune"></a>Uso de Intune
Para revisar un informe de directivas sobre el estado de implementación para los anillos de actualizaciones de Windows 10 que ha configurado, haga lo siguiente: 
1. Inicie sesión en el [Portal de Azure](https://portal.azure.com/).
2. Elija **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Actualizaciones de software** > **Información general**. Puede ver información general sobre el estado de los círculos de actualizaciones que tenga asignados.
4. Abra uno de los informes siguientes:  

   **Para todos los anillos de implementación**:
   1. En **Actualizaciones de software** > **Anillos de actualización de Windows 10**
   2. En la **sección Supervisar**, elija **Por el estado de implementación del círculo de implementaciones**.  

   **Para anillos de implementación específicos**:  

   1. En **Actualizaciones de software** > **Anillos de actualización de Windows 10**, elija los anillos de implementación que va a revisar.  
   2. En la sección **Supervisar**, elija uno de los siguientes informes para ver información más detallada sobre el círculo de actualizaciones:  
      - **Estado del dispositivo**  
      - **Estado del usuario**  

## <a name="use-update-compliance"></a>Uso de Update Compliance
Puede supervisar los lanzamientos de las actualizaciones de Windows 10 mediante [Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), una solución de Windows Analytics. Update Compliance se ofrece a través de Azure Portal y está disponible de forma gratuita para los dispositivos que cumplen los [requisitos previos](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

Cuando se utiliza esta solución, se implementa un identificador comercial en cualquiera de sus dispositivos Windows 10 administrados con Intune para el que quiera que se informe del cumplimiento de las actualizaciones.  

En la consola de Intune, se usa la configuración OMA-URI de una directiva personalizada para configurar el identificador comercial. Para obtener más información, consulte [Configuración de directivas de Intune para dispositivos Windows 10 en Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

Ruta OMA-URI (distingue mayúsculas de minúsculas) para configurar el identificador comercial: *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*  

Por ejemplo, puede usar los siguientes valores en **Agregar o editar configuración OMA-URI**:
- **Nombre de la configuración**: identificador comercial de Windows Analytics
- **Descripción de la configuración**: configuración del identificador comercial para soluciones de Windows Analytics
- **OMA-URI** (distingue mayúsculas de minúsculas): *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Tipo de datos**: String
- **Valor**: \<Utilizar el GUID que se muestra en la pestaña Telemetría de Windows del área de trabajo de OMS>
 
> [!NOTE]  
> Para obtener más información sobre MS DM Server, vea [DMClient configuration service provider (CSP)]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp) (Proveedor de servicios de configuración (CSP) de DMClient).

## <a name="next-steps"></a>Pasos siguientes
[Administrar las actualizaciones de software en Intune](windows-update-for-business-configure.md)

