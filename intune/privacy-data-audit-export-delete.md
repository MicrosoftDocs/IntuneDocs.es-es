---
title: Auditoría, exportación o eliminación de datos personales
description: Obtenga más información sobre cómo auditar, exportar o eliminar datos personales.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 87bd539199ec4f8b43f0679b251bd550cd837651
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041309"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Auditoría, exportación o eliminación de datos personales en Intune

Los administradores de Intune pueden usar los registros de auditoría para realizar un seguimiento de las actividades en torno a los datos personales. Los administradores también pueden exportar y eliminar los datos personales.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>Auditoría de los datos personales

Los registros de auditoría proporcionan a los administradores de inquilinos un registro de las actividades que generan un cambio en Microsoft Intune. Los registros de auditoría están disponibles para muchas tareas de administración y normalmente permiten crear, actualizar (editar), eliminar y asignar acciones. También se pueden revisar las tareas remotas que generan eventos de auditoría. Estos registros de auditoría pueden contener datos personales de los usuarios cuyos dispositivos estén inscritos en Intune.  

Por motivos de seguridad, Intune podrá mantener los registros de auditoría para las acciones de usuario y de dispositivo durante un período de un año. Estos registros se eliminan automáticamente tras el período de retención de un año.

Para revisar los registros de auditoría, vea [Registros de auditoría para actividades de Intune](monitor-audit-logs.md). 

Los administradores no pueden eliminar los registros de auditoría.

Estos eventos de auditoría se conservan durante un año. Los administradores de inquilinos pueden solicitar registros de auditoría mediante [este formulario de solicitud de soporte técnico](https://privacy.microsoft.com/en-US/privacy-questions?).

## <a name="export-personal-data"></a>Exportación de los datos personales

Los administradores pueden exportar los datos personales del usuario final, incluidas las cuentas, los datos del servicio y los registros asociados para cumplir con las solicitudes de derechos del interesado. Depende de usted y de su organización decidir si se debe proporcionar al titular una copia de los datos personales o si existe algún motivo comercial legítimo para retenerlos. Si decide proporcionarlos, puede hacerlo mediante una copia del documento real, una versión redactada adecuadamente o una captura de pantalla de las partes que considere oportuno compartir.

Para exportar datos personales de un usuario, puede usar: 
- la hoja de dispositivos de MDM de Intune para exportar una lista de dispositivos. También puede copiar los datos del dispositivo directamente.
- el [script Export-IntuneData.ps1](https://aka.ms/intunedataexport).

## <a name="delete-end-user-personal-data"></a>Eliminación de los datos personales del usuario final

Hay tres formas de eliminar los datos personales de la administración de Intune:
- Eliminación del usuario de Azure Active Directory
- Restablecimiento de los valores de fábrica del dispositivo
- Eliminación automática del usuario

### <a name="delete-a-user-from-intune"></a>Eliminación de un usuario de Intune

Para eliminar los datos personales de un usuario final de Intune, un administrador debe [eliminar el usuario de Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory.md#delete-users-from-azure-ad). Cuando se elimina el usuario de AAD (eliminación permanente), Intune recibe la señal de eliminación de AAD y, después, comienza a purgar automáticamente todos los datos personales del usuario del servicio de Intune. La información del usuario se eliminará del servicio de Intune en un plazo de 30 días a partir de la acción de eliminación.

### <a name="reset-device-to-factory-settings"></a>Restablecimiento de los valores de fábrica del dispositivo
La restauración de los valores de fábrica permite restaurar todos los datos personales y de empresa, así como las opciones de configuración, a los valores originales de fábrica. Resulta una opción muy útil para proporcionar un dispositivo a otro empleado. Los archivos de usuario, las aplicaciones instaladas y los valores no predeterminados dejan de estar disponibles y se eliminan del servicio de Intune en 30 días tras eliminarlos del dispositivo.

### <a name="user-self-removal-from-intune-management"></a>Eliminación automática de usuarios desde la administración de Intune
Los usuarios pueden quitar sus dispositivos [Android, Apple o Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android.md) personales desde la administración de Intune sin la asistencia del administrador.   

### <a name="retire"></a>Retirar
La acción **Retirar** quita los datos aprovisionados por Intune, como las aplicaciones de empresa, los datos sobre las aplicaciones que administra Intune, la configuración de directivas y los perfiles de correo electrónico que se aprovisionan mediante Intune. Esta acción deja los datos personales del usuario en el dispositivo.

### <a name="delete-a-tenant-from-microsoft-intune"></a>Eliminación de un inquilino de Microsoft Intune

Si un cliente de inquilino de Intune cancela su cuenta de Intune, todos los datos del inquilino se eliminan en los 180 días posteriores al cierre de la cuenta de Intune. Si el inquilino de AAD está asociado a otras suscripciones empresariales de Microsoft (Azure, Office 365), solo se eliminan los datos del cliente de Intune. El recurso de inquilino de AAD se mantiene para su uso en otras suscripciones. Si la cuenta de Intune es la única suscripción asociada al inquilino de AAD, se elimina el inquilino, así como todos los recursos y los datos del cliente.

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>Eliminación de un usuario de un entorno híbrido de administración de dispositivos móviles (MDM)
Si tiene un entorno de MDM híbrido (Intune integrado con Configuration Manager), debe realizar las siguientes acciones en orden para eliminar completamente un usuario y eliminarlo permanentemente del sitio de Active Directory local, Configuration Manager e Intune.

1. Elimine el usuario del sitio de Active Directory (AD) local. Esto impedirá que el usuario se sincronice con Azure AD y que lo detecte la herramienta de detección de Configuration Manager. 
2. Elimine el usuario desde la consola de Configuration Manager para quitar el usuario y los datos asociados de Configuration Manager. En la consola, vaya a **Activos y compatibilidad** > **Usuarios**, y haga clic en el usuario que quiera eliminar y en **Eliminar**.
3. [Eliminar el usuario de AAD](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory.md#delete-users-from-azure-ad), que permite eliminar el usuario y los datos asociados tanto de Azure Active Directory como de Intune al mismo tiempo. Cuando se elimina el usuario de AAD (eliminación permanente), Intune recibe la señal de eliminación de AAD y, después, comienza a purgar automáticamente todos los datos personales del usuario del servicio de Intune. La información del usuario se eliminará del servicio de Intune en un plazo de 30 días a partir de la acción de eliminación.

> [!Important]
>La incorporación de nuevos clientes MDM híbridos está en desuso. Para obtener más información, vea la entrada de blog [Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) (Transición de la administración de dispositivos móviles híbrida a Intune en Azure).

## <a name="next-steps"></a>Pasos siguientes

Obtenga más información sobre cómo [auditar, exportar o eliminar](privacy-data-audit-export-delete.md) datos personales en Intune.
