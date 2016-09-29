---
title: Administrar licencias de Intune con PowerShell | Microsoft Intune
description: Administrar licencias de Intune con PowerShell
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8f99159079002b9e44dd1ba328b0f2fc079770d8
ms.openlocfilehash: 9a3e28cad00f99035b18182a33c24bcb714cca19


---

# Administrar licencias de Intune con PowerShell
Para que los usuarios puedan iniciar sesión para usar el servicio de Intune o inscribir sus dispositivos en la administración, primero debe asignar a cada usuario una licencia a la suscripción de Intune, tal como se describe en [Administración de licencias de Intune](start-with-a-paid-subscription-to-microsoft-intune-step-4.md). Pero las organizaciones que usan Microsoft Enterprise Mobility + Security podrían tener usuarios que solo requieran servicios de Azure Active Directory Premium o Intune en el paquete de EMS. Puede asignar un servicio o un subconjunto de servicios mediante [cmdlets de PowerShell de Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

Para asignar licencias de usuario para servicios de EMS de forma selectiva, abra PowerShell como administrador en un equipo con el [Módulo de Active Directory para Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) instalado. Puede instalar PowerShell en un equipo local o en un servidor de ADFS.

Debe crear una nueva definición de SKU de licencia que se aplique solo a los planes de servicio deseados. Para ello, deshabilite los planes que no desee aplicar. Por ejemplo, podría crear una definición de SKU de licencia que no asigne una licencia de Intune. Para ver una lista de los servicios disponibles, escriba:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

Puede ejecutar el siguiente comando para excluir el plan de servicio de Intune. Puede utilizar el mismo método para expandir un grupo de seguridad completo o puede usar filtros más específicos.

**Ejemplo 1** Crear un nuevo usuario en la línea de comandos y asignar una licencia de EMS sin habilitar la parte de Intune de la licencia:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Comprobar con:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Ejemplo 2** Deshabilitar la parte de Intune de la licencia de EMS para un usuario que ya está asignado a una licencia:

    Connect-MsolService

    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS

Comprobar con:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

### Pasos siguientes
¡Enhorabuena! Acaba de completar el paso 4 de la *Guía de inicio rápido de Intune*.
>[!div class="step-by-step"]

>[&larr; **Sincronizar usuarios con Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Organizar usuarios y dispositivos** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  



<!--HONumber=Sep16_HO3-->


