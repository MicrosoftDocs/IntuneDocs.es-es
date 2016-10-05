---
title: Exchange Connector para Exchange Online | Microsoft Intune
description: "Conecte Intune al servicio de Office 365 Exchange para admitir la administración de dispositivos móviles (MDM) de Exchange ActiveSync."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: a6438bb3ca21e5c46dca5ebe69266fd9bce9a4b8


---

# Configurar Intune Service to Service Connector para Exchange Online

Use esta información para conectar Microsoft Intune y Exchange Online o el nuevo servicio Exchange Online dedicado. Para determinar si su entorno Exchange Online dedicado es **nuevo** o **heredado**, póngase en contacto con su administrador de cuentas. Intune solo admite una conexión de Exchange Connector de cualquier tipo por suscripción.

## Requisitos para Service to Service Connector
**Service to Service Connector** solo admite Exchange Online o el nuevo Exchange Online dedicado y no requiere infraestructura local.

|Requisito|Más información|
|---------------|--------------------|
|Exchange Online configurado y en ejecución|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Entidad de administración de dispositivos móviles| [Configurar Microsoft Intune como la entidad de administración de dispositivos móviles](prerequisites-for-enrollment.md#set-mobile-device-management-authority)|
|Versión de Microsoft Exchange|Exchange Online o el nuevo servicio Exchange Online dedicado|
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


Service to Service Connector se configura automáticamente y se sincroniza con el entorno de Exchange Online o el nuevo entorno de Exchange Online dedicado.

## Validar la conexión de Exchange

Después de configurar correctamente Exchange Connector, vaya a la [consola de administración de Intune](http://manage.microsoft.com), seleccione **Administración** y vaya a **Administración de dispositivos móviles** > **Microsoft Exchange** y compruebe que los detalles que ha facilitado aparecen en **Información de conexión de Exchange**.

También puede comprobar la fecha y la hora del último intento de sincronización correcto.



<!--HONumber=Sep16_HO4-->


