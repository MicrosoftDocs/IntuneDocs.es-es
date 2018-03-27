---
title: Exchange Connector para Exchange Online
description: Conecte Intune al servicio de Office 365 Exchange para admitir la administración de dispositivos móviles (MDM) de Exchange ActiveSync.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/29/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 78b4e91fd61bb79c2a3a6d86d5a79c39b320cc5e
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="configure-the-intune-service-to-service-connector-for-exchange-online"></a>Configurar Intune Service to Service Connector para Exchange Online

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use esta información para conectar Microsoft Intune y Exchange Online o el nuevo servicio Exchange Online dedicado. Para determinar si su entorno Exchange Online dedicado es una versión **nueva** o **heredada**, póngase en contacto con su administrador de cuentas. Intune solo admite una conexión de Exchange Connector de cualquier tipo por suscripción.

## <a name="service-to-service-connector-requirements"></a>Requisitos de Service to Service Connector
**Service to Service Connector** solo admite Exchange Online o Exchange Online dedicado y no requiere infraestructura local.

|Requisito|Más información|
|---------------|--------------------|
|Exchange Online configurado y en ejecución|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Entidad de administración de dispositivos móviles| [Configurar Microsoft Intune como la entidad de administración de dispositivos móviles](prerequisites-for-enrollment.md#step-2-set-mdm-authority)|
|Versión de Microsoft Exchange|Exchange Online o el nuevo servicio Exchange Online dedicado|/intune/users-permissions-add
|Sincronización de Active Directory|Para poder usar Intune Connector, debe [configurar la sincronización de Active Directory](/intune/users-permissions-add) de forma que los usuarios locales y los grupos de seguridad estén sincronizados con su instancia de Azure Active Directory.|

### <a name="exchange-cmdlet-requirements"></a>Requisitos del cmdlet de Exchange

Cree una cuenta de usuario de Exchange Online que sea utilizada por Intune Exchange Connector. La cuenta debe tener permiso para usar la consola de administración de Intune y ejecutar en ella los cmdlets de Exchange de Windows PowerShell necesarios que se enumeran a continuación:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Configurar Service to Service Connector

1. Abra la [consola de administración de Microsoft Intune](https://manage.microsoft.com) con una cuenta de usuario con derechos de administrador de Exchange y los permisos de los cmdlets [descritos anteriormente](#exchange-cmdlet-requirements). Para establecer la conexión, Microsoft Intune usa la dirección de correo electrónico del usuario que actualmente ha iniciado sesión.

2.  En el panel de accesos directos del área de trabajo, elija **ADMINISTRACIÓN**>**Administración de dispositivos móviles** > **Microsoft Exchange** > **Configurar conexión de Exchange**.
![Página de configuración de Service to Service Connector](../media/intunesa5cservicetoserviceconnector.png)

3.  En la página **Configurar conexión de Exchange**, haga clic en **Configurar Service to Service Connector**.


Service to Service Connector se configura automáticamente y se sincroniza con el entorno de Exchange Online o el nuevo entorno de Exchange Online dedicado.

## <a name="validate-your-exchange-connection"></a>Validar la conexión de Exchange

Después de haber configurado correctamente Exchange Connector, vaya a la [consola de administración de Microsoft Intune](https://manage.microsoft.com). Elija **Administración**> **Administración de dispositivos móviles** > **Microsoft Exchange**. A continuación, compruebe que los detalles que proporcionó aparecen en **Información de conexión de Exchange**.

También puede comprobar la fecha y la hora del último intento de sincronización correcto.
