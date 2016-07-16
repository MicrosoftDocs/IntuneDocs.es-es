---
title: Configurar Microsoft Intune Exchange Connector para Exchange hospedado | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6951ccdb0e37489217ef939f0cbf6fc1133a6d3c
ms.openlocfilehash: 6cfc532cba2f53034c4c3ef0c2df3d6c1e6e7841


---

# Configurar Intune Service to Service Connector para Exchange Online

Use esta información para conectar Microsoft Intune y el servicio Exchange Online hospedado en Office 365.

## Requisitos para Service to Service Connector
**Service to Service Connector** solo admite Exchange hospedado y no requiere infraestructura local.

|Requisito|Más información|
|---------------|--------------------|
|Hosted Exchange configurado y en ejecución|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Entidad de administración de dispositivos móviles| [Configurar Microsoft Intune como la entidad de administración de dispositivos móviles](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Versión de Microsoft Exchange|Debe tener una suscripción a Office 365 con un inquilino de Exchange Server 2013 o posterior. Mientras el inquilino sea de Exchange Server 2013 o posterior, el conector admitirá Exchange Server 2010 en ese mismo entorno.|
|Sincronización de Active Directory|Para poder usar Intune Connector, debe [configurar la sincronización de Active Directory](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) de forma que los usuarios locales y los grupos de seguridad estén sincronizados con su instancia de Azure Active Directory.|

### Requisitos del cmdlet de Exchange

Cree una cuenta de usuario de Exchange Online que sea utilizada por Intune Exchange Connector. La cuenta debe tener permiso para usar la consola de administración de Intune y ejecutar en ella los cmdlets de Exchange de Windows PowerShell necesarios que se enumeran a continuación:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## Configurar Service-to-Service Connector

1. Abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com) con una cuenta de usuario con derechos de administrador de Exchange y los permisos de los cmdlets [anteriores](#exchange-cmdlet-requirements). Para establecer la conexión, Microsoft Intune usa la dirección de correo electrónico del usuario que actualmente ha iniciado sesión.

2.  En el panel de accesos directos del área de trabajo, elija **Administración**, vaya a **Administración de dispositivos móviles** > **Microsoft Exchange** > **Configurar conexión de Exchange**.
![Configurar la página Service to Service Connector](../media/intunesa5cservicetoserviceconnector.png)

3.  En la página **Configurar conexión de Exchange**, haga clic en **Configurar Service to Service Connector**.


Service to Service Connector se configurará automáticamente y se sincronizará con su entorno de Hosted Exchange.

## Validar la conexión de Exchange

Después de configurar correctamente Exchange Connector, vaya a la consola de administración de Intune y seleccione el área de trabajo **Administración**. Después, vaya a **Administración de dispositivos móviles** > **Microsoft Exchange** y compruebe que los detalles que ha facilitado aparecen en **Información de conexión de Exchange**.

También puede comprobar la fecha y la hora del último intento de sincronización correcto.



<!--HONumber=Jun16_HO4-->


