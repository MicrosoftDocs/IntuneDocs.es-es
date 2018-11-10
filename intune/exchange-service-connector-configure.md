---
title: Intune Exchange Connector para Exchange Online
titleSuffix: ''
description: Conecte Intune al servicio de Office 365 Exchange para admitir la administración de dispositivos móviles (MDM) de Exchange ActiveSync.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6132e77c4f4a86a30a55d436219f0d7e2a49980c
ms.sourcegitcommit: ff6db80cb3638e1eec0a4c8b185649363e9e552e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806330"
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>Configuración de Exchange Service Connector para Intune y Exchange Online
En este artículo se muestra cómo conectar el servicio Microsoft Intune y Exchange Online o el nuevo servicio Exchange Online dedicado. Para determinar si su entorno Exchange Online dedicado es una versión **nueva** o **heredada**, póngase en contacto con su administrador de cuentas.

Con **Service to Service Connector**, puede administrar los dispositivos administrados por Intune y Exchange ActiveSync (EAS) desde una única consola administrativa.  El conector no es necesario para habilitar el acceso condicional para Exchange Online.

## <a name="service-to-service-connector-requirements"></a>Requisitos de Service to Service Connector
**Service to Service Connector** solo admite Exchange Online o Exchange Online dedicado y no requiere infraestructura local. 


|              Requisito               |                                                                                                            Más información                                                                                                            |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange Online configurado y en ejecución |                                                                                 [Exchange Online](https://technet.microsoft.com/library/jj200580.aspx)                                                                                 |
|   Entidad de administración de dispositivos móviles   |                                                       [Configurar Microsoft Intune como la entidad de administración de dispositivos móviles](mdm-authority-set.md)                                                       |
|       Versión de Microsoft Exchange       |                                                                                      Exchange Online o el nuevo servicio Exchange Online dedicado                                                                                      |
|    Sincronización de Active Directory    | Para poder usar Intune Connector, debe [configurar la sincronización de Active Directory](/intune/users-add) de forma que los usuarios locales y los grupos de seguridad estén sincronizados con su instancia de Azure Active Directory. |

### <a name="exchange-cmdlet-requirements"></a>Requisitos del cmdlet de Exchange

Cree una cuenta de usuario de Exchange Online que sea utilizada por Intune Exchange Service Connector. La cuenta debe tener permiso para ejecutar los siguientes cmdlets de Windows PowerShell Exchange necesarios:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Configurar Service to Service Connector

1. Inicie sesión en [Azure Portal](http://portal.azure.com) con una cuenta de usuario con derechos de administración de Exchange y los permisos de los cmdlets [que se describieron anteriormente](#exchange-cmdlet-requirements), y el rol de Administrador global. Para establecer la conexión, Microsoft Intune usa la dirección de correo electrónico del usuario que actualmente ha iniciado sesión.

2. Elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Intune** para abrir el panel de Microsoft Intune. Elija **Acceso condicional** y, en **Configurar**, elija **Exchange Service Connector**.

4.  En la página **Conditional access - Exchange service connector** (Acceso condicional: Exchange Service Connector), elija **Configurar Service to Service Connector**. 
   
     ![Imagen que muestra la selección del vínculo Configurar Service to Service Connector](media/exchange_service_connector.png)

Service to Service Connector se configura automáticamente y se sincroniza con el entorno de Exchange Online o el nuevo entorno de Exchange Online dedicado.

## <a name="validate-your-exchange-connection"></a>Validar la conexión de Exchange

Después de configurar correctamente Exchange Service to Service Connector, valide la información del servidor Exchange Connector en la página **Conditional access - Exchange service connector** (Acceso condicional: Exchange Service Connector).

También puede comprobar el **estado de la conexión** y la fecha y la hora del último intento de sincronización correcto.

 