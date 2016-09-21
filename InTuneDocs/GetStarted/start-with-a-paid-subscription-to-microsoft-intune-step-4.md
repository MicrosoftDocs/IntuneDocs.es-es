---
title: Administrar licencias de Intune | Microsoft Intune
description: "Explica cómo asignar licencias a los usuarios para la suscripción de Intune"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f86fe2710318209a2a4373beea1590c5343cbf4c
ms.openlocfilehash: 08e112bfae9a3655f428d53f68922fd3ff4713b4


---

# Administración de licencias de Intune
Para que los usuarios puedan iniciar sesión para usar el servicio de Intune o inscribir sus dispositivos en la administración, primero debe asignar a cada usuario una licencia a la suscripción de Intune con el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854).

Las organizaciones que usan Microsoft Enterprise Mobility + Seguridad (EMS) podrían tener usuarios que solo requieran servicios de Azure Active Directory Premium o Intune en el paquete de EMS. Puede asignar un servicio o un subconjunto de servicios mediante [cmdlets de PowerShell de Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx). Para obtener más información, consulte [Administración de licencias de Intune con PowerShell](start-with-a-paid-subscription-to-microsoft-intune-step-4-posh.md).

## Cómo se asignan licencias de Intune
Cuando se sincronizan cuentas de usuario desde Active Directory local o se agregan manualmente a la suscripción de servicios en la nube a través del [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), no se asigna automáticamente una licencia de Intune. En su lugar, posteriormente, un administrador de inquilinos Intune debe editar la cuenta de usuario para asignar una licencia al usuario desde el portal de Office 365.

Cuando la suscripción comparte Azure AD con otros servicios en la nube asociados a su suscripción, también tiene acceso a los usuarios agregados a esos servicios. Estos usuarios no tienen una licencia para [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] hasta que le asigne una licencia a cada uno de ellos.

> [!TIP]
> Si la opción de asignar o revocar una licencia de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] está deshabilitada, la suscripción podría incluir opciones de licencias por volumen, como las disponibles al usar [Enterprise Mobility Suite + Seguridad](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx). Para obtener información acerca de cómo asignar o revocar licencias, consulte la documentación de las opciones de licencia.

## Asignar una licencia de usuario de Intune

Utilice el [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para agregar manualmente usuarios basados en la nube y asignar licencias a cuentas de usuarios basadas en la nube y cuentas sincronizadas desde Active Directory local en Azure AD.

1.  Inicie sesión en el [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con sus credenciales de administrador de inquilinos y, a continuación, seleccione **Personas** > **Todos los usuarios**.

2.  Seleccione la cuenta de usuario a la que desee asignar una licencia de usuario de Intune y, a continuación, seleccione **Microsoft Intune** (independiente) o **Enterprise Mobility Suite**.

3.  Ahora, la cuenta de usuario tiene los permisos necesarios para usar el servicio e inscribir dispositivos en administración.

> [!NOTE] Los usuarios aparecerán en la consola una vez que hayan inscrito un dispositivo. 

### Usar PowerShell para administrar de forma selectiva las licencias de usuario de EMS
Las organizaciones que usan Microsoft Enterprise Mobility + Seguridad (anteriormente, Enterprise Mobility Suite) podrían tener usuarios que solo requieran servicios de Azure Active Directory Premium o Intune en el paquete de EMS. Puede asignar un servicio o un subconjunto de servicios mediante [cmdlets de PowerShell de Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

Para asignar licencias de usuario para servicios de EMS de forma selectiva, abra PowerShell como administrador en un equipo con el [Módulo de Active Directory para Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) instalado. Puede instalar PowerShell en un equipo local o en un servidor de ADFS.

Debe crear una nueva definición de SKU de licencia que se aplique solo a los planes de servicio deseados. Para ello, deshabilite los planes que no desee aplicar. Por ejemplo, podría crear una definición de SKU de licencia que no asigne una licencia de Intune. Para ver una lista de servicios disponibles, escriba:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

Puede ejecutar el siguiente comando para excluir el plan de servicio de Intune. Puede utilizar el mismo método para expandir un grupo de seguridad completo o puede usar filtros más granulares.

**Ejemplo 1** Crear un nuevo usuario en la línea de comandos y asignar una licencia de EMS sin habilitar la parte Intune de la licencia:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Comprobar con:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Ejemplo 2** Deshabilitar la parte Intune de la licencia de EMS para un usuario que ya está asignado a una licencia:

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


