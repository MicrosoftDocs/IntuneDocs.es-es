---
title: Administrar licencias de Intune con PowerShell | Microsoft Docs
description: Administre licencias de Intune con PowerShell.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 6b5ea7323f08ae63ce37adedbf23b9fab31a6f55


---

# <a name="manage-intune-licenses-using-powershell"></a>Administrar licencias de Intune con PowerShell

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Antes de que los usuarios puedan iniciar sesión para usar el servicio de Intune o inscriban sus dispositivos en la administración, primero debe asignar a cada usuario una licencia a su suscripción de Intune, como se describe en [Manage Intune licenses (Administrar licencias de Intune)](start-with-a-paid-subscription-to-microsoft-intune-step-4.md). Pero las organizaciones que usan Microsoft Enterprise Mobility + Security pueden tener usuarios que solo necesiten Azure Active Directory Premium o los servicios de Intune en el paquete de EMS. Puede asignar un servicio o un subconjunto de servicios mediante los [cmdlets de PowerShell de Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

Para asignar licencias de usuario de forma selectiva a los servicios de EMS, abra PowerShell como administrador en un equipo que tenga instalado el [módulo de Azure Active Directory para Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule). Puede instalar PowerShell en un equipo local o en un servidor de ADFS.

Debe crear una nueva definición de SKU de licencia que solo se aplique a los planes de servicio deseados. Para ello, deshabilite los planes que no quiera aplicar. Por ejemplo, podría crear una definición de SKU de licencia que no asigne una licencia de Intune. Para ver una lista con los servicios disponibles, escriba:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

Puede ejecutar el comando siguiente para excluir el plan de servicio Intune. Puede usar el mismo método para realizar una expansión a todo un grupo de seguridad o puede usar filtros más pormenorizados.

**Ejemplo 1** Cree un nuevo usuario en la línea de comandos y asigne una licencia de EMS sin habilitar la parte de Intune de la licencia:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Realice la comprobación con lo siguiente:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Ejemplo 2** Deshabilite la parte de Intune de la licencia de EMS de un usuario que ya tenga asignada una licencia:

    Connect-MsolService

    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS

Realice la comprobación con lo siguiente:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

### <a name="next-steps"></a>Pasos siguientes
Enhorabuena. Acaba de completar el paso 4 de la *Guía de inicio rápido de Intune*.
>[!div class="step-by-step"]

>[&larr; **Sincronizar los usuarios con Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Organizar usuarios y dispositivos** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  



<!--HONumber=Dec16_HO2-->


